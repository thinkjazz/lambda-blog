<script>
	import ContactCard from './ContactCard.svelte';
	let name = "Bo";
	let title ="";
	let image ="";
	let age = 30;
	let description ="";


	$: uppercaseName = name.toUpperCase();

	$: console.log(name);
	$: if (name === "Boris") {
		console.log("It runs!");
		age = 31;
	}

	function incrementAge() {
		age += 1;
	}

	function changeName() {
		name = "Boris";
	}

	function nameInput(event) {
		const enteredValue = event.target.value;
		name = enteredValue;
	}
</script>

<main>
	<h1>Hello {uppercaseName}, my age is {age}!</h1>
	<button on:click={incrementAge}>Change Age</button>
	<!-- <button on:click="{changeName}">Change Name</button> -->
	<!-- <input type="text" value={name} on:input={nameInput} /> -->
	<input type="text" bind:value={name} />
	<input type="text" bind:value={title} />
	<input type="text" bind:value={image} />
	<textarea bind:value={description} rows="5"></textarea>



	<ContactCard
			userName={name}
			jobTitle={title}
			description={description}
			userImage={image}/>

</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>