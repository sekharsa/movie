<style>
/* .zoom {
	overflow: hidden;
}
.zoom img {
	transition: transform 0.7s;
}
.zoom:hover img {
	transform: scale(1.035);
} */
.trans {
	transition: width 0.3s;
	overflow: hidden;
	justify-content: start;
	padding-left: 2px;
}
.trans:hover {
	width: 130px;
	padding-left: 0px;
	justify-content: center;
}
</style>

<script>
import { lazyload } from './../actions/lazyload'
import { currency } from './util'
import { CDN_URL } from '$lib/config'
export let product = {}

let show
function showitems() {
	show = true
}
function hideitems() {
	show = false
}
</script>

<div
	class="group w-1/2 flex-shrink-0 border text-gray-800 hover:bg-white hover:shadow-md sm:mx-2 sm:mb-2 sm:w-52  sm:border-0 md:mx-4 md:mb-4"
	on:mouseenter="{showitems}"
	on:mouseleave="{hideitems}">
	<a href="{'/' + product._source?.slug + '?id=' + product?._id}" class="block overflow-hidden ">
		<div class="">
			<img
				use:lazyload
				src="{`${product._source?.img && product._source?.img[0]}?tr=w-3,h-3`}"
				alt="{product._source?.name}"
				data-src="{`${product._source?.img && product._source?.img[0]}`}"
				class="h-72 w-full bg-black object-cover  object-top " />
		</div>

		<div class="p-4 ">
			{#if show}
				<!-- For view above 640px start -->

				<div class="-mt-12 hidden sm:block">
					<!-- View smilar button start-->
					<a href="{`/search?brand=${product.brandName}`}" class="flex justify-end">
						<div
							class="trans flex h-7 w-7 items-center rounded-full border border-primary-500 bg-white text-primary-500">
							<svg
								xmlns="http://www.w3.org/2000/svg"
								class="h-5 w-5 flex-shrink-0"
								fill="none"
								viewBox="0 0 24 24"
								stroke="currentColor">
								<path
									stroke-linecap="round"
									stroke-linejoin="round"
									stroke-width="2"
									d="M7 21a4 4 0 01-4-4V5a2 2 0 012-2h4a2 2 0 012 2v12a4 4 0 01-4 4zm0 0h12a2 2 0 002-2v-4a2 2 0 00-2-2h-2.343M11 7.343l1.657-1.657a2 2 0 012.828 0l2.829 2.829a2 2 0 010 2.828l-8.486 8.485M7 17h.01"
								></path>
							</svg>
							<span class="whitespace-nowrap text-xs ps-2">View similar</span>
						</div>
					</a>
					<!-- View smilar button end-->
					<!-- Wishlist start-->
					<button
						class="mt-3.5 flex w-full items-center justify-center  space-x-2 border border-gray-300 py-1 focus:outline-none ">
						<svg
							xmlns="http://www.w3.org/2000/svg"
							class="h-5 w-5 text-gray-500 "
							fill="none"
							viewBox="0 0 24 24"
							stroke="currentColor">
							<path
								stroke-linecap="round"
								stroke-linejoin="round"
								stroke-width="1.5"
								d="M4.318 6.318a4.5 4.5 0 000 6.364L12 20.364l7.682-7.682a4.5 4.5 0 00-6.364-6.364L12 7.636l-1.318-1.318a4.5 4.5 0 00-6.364 0z"
							></path>
						</svg><span class="text-sm font-semibold ">WISHLIST</span>
					</button>
					<!-- Wishlist end-->
					<!-- Size chart start-->
					<div class="mt-1.5 flex items-baseline justify-start">
						<h5 class="mr-1 text-sm">Sizes:</h5>
						<h6 class="flex items-baseline space-x-1 text-xs font-medium text-gray-500 ">
							{#if product?.variants?.length}
								{#each product?.variants as v, i}
									<div>{v.size}</div>
								{/each}
							{/if}
						</h6>
					</div>
					<!-- Size chart end-->
				</div>
				<!-- For view above 640px end -->

				<!-- For view below 640px start -->

				<div class="sm:hidden">
					<div class="flex items-center justify-between">
						<h4 class="mb-1.5 font-semibold">
							{#if product._source?.brandName}
								{product._source?.brandName}
							{:else}
								_
							{/if}
						</h4>

						<div class="sm:hidden">
							<svg
								xmlns="http://www.w3.org/2000/svg"
								class="h-5 w-5"
								fill="none"
								viewBox="0 0 24 24"
								stroke="currentColor">
								<path
									stroke-linecap="round"
									stroke-linejoin="round"
									stroke-width="2"
									d="M4.318 6.318a4.5 4.5 0 000 6.364L12 20.364l7.682-7.682a4.5 4.5 0 00-6.364-6.364L12 7.636l-1.318-1.318a4.5 4.5 0 00-6.364 0z"
								></path>
							</svg>
						</div>
					</div>

					<h5
						href="{'/' + product._source?.slug + '?id=' + product._id}"
						class="overflow-hidden overflow-ellipsis whitespace-nowrap text-sm font-medium">
						{#if product._source?.name}
							{product._source?.name}
						{:else}
							_
						{/if}
					</h5>
				</div>

				<!-- For view below 640px end -->
			{:else}
				<div>
					<div class="flex items-center justify-between">
						<h4 class="font-semibold mb-1.5">
							{#if product._source?.brandName}
								{product._source?.brandName}
							{:else}
								_
							{/if}
						</h4>

						<div class="sm:hidden">
							<svg
								xmlns="http://www.w3.org/2000/svg"
								class="h-5 w-5"
								fill="none"
								viewBox="0 0 24 24"
								stroke="currentColor">
								<path
									stroke-linecap="round"
									stroke-linejoin="round"
									stroke-width="2"
									d="M4.318 6.318a4.5 4.5 0 000 6.364L12 20.364l7.682-7.682a4.5 4.5 0 00-6.364-6.364L12 7.636l-1.318-1.318a4.5 4.5 0 00-6.364 0z"
								></path>
							</svg>
						</div>
					</div>

					<h5
						href="{'/' + product._source?.slug + '?id=' + product._id}"
						class="text-sm font-medium overflow-hidden whitespace-nowrap overflow-ellipsis">
						{#if product._source?.name}
							{product._source?.name}
						{:else}
							_
						{/if}
					</h5>
				</div>
			{/if}

			<div class="mt-2.5 mb-1.5 flex flex-wrap items-baseline justify-start leading-4 ">
				<h6 class="mr-1 whitespace-nowrap text-xs font-semibold sm:text-sm ">
					{currency(product._source?.price)}
				</h6>

				<h6 class="mr-1 whitespace-nowrap text-xs text-gray-500 line-through">
					{currency(product._source?.mrp)}
				</h6>

				{#if Math.floor(100 - (product._source?.price * 100) / product._source?.mrp) > 0}
					<div class="text-primary-800 mr-1 whitespace-nowrap text-xs">
						<h6 class="hidden sm:block">
							( {Math.round((product._source?.price * 100) / product._source?.mrp)}% off )
						</h6>

						<h6 class="sm:hidden">
							{Math.round((product._source?.price * 100) / product._source?.mrp)}% off
						</h6>
					</div>
				{/if}

				{#if product._source?.stock < 1}
					<div class="text-xs text-red-500">Out of stock</div>
				{/if}
			</div>
		</div>
	</a>
</div>
