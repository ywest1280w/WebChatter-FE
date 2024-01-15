<script>
	import Nested from './Nested.svelte';
	let name = 'svelte';
	let src = '/image.gif';
	let string = `this string contains some <Strong>HTML!!</Strong>`
	let count = 0
	$: doubled = count * 2;
	$: {
		console.log(`the count is ${count}`);
		console.log(`this will also be logged whenever count changes`);
	}
	$: if(count >= 10){
		alert(`count is dangerously high!!`);
		count = 0;
	}
	function increment(){
		count += 1;
	}
</script>
<h1>hello {name.toUpperCase()}</h1>
<!-- svelte-ignore a11y-missing-attribute -->
<img src={src} alt="{name} dances">
<p>this is a paragraph</p>
<Nested/>
<p>{@html string}</p>
<button on:click={increment}>
Clicked {count}
{count === 1 ? 'time' : "times"}
</button>
<p>{count} doubled is {doubled}</p>
<style>
	p {
		color: goldenrod;
		font-family: 'Courier New', Courier, monospace;
		font-size: 2em;
	}
</style>