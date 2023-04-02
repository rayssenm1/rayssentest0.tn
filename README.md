<!DOCTYPE html>
<html>
<head>
	<title>Exemple de code pour une zone de saisie de texte</title>
	<link rel="stylesheet" type="text/css" href="style.css">
</head>
<body>
	<div class="container">
		<h1>Mon application</h1>
		<form>
			<label for="inputText">Texte à ajouter :</label>
			<input type="text" id="inputText">
			<button type="button" onclick="ajouterTexte()">Ajouter</button>
		</form>
		<table>
			<thead>
				<tr>
					<th>Texte ajouté</th>
					<th>Actions</th>
				</tr>
			</thead>
			<tbody id="tableBody">
			</tbody>
		</table>
	</div>

	<script>
    let tableBody = document.getElementById("tableBody");

function ajouterTexte() {
	let inputText = document.getElementById("inputText");
	let texte = inputText.value.trim();
	if (texte !== "") {
		ajouterLigne(texte);
		inputText.value = "";
	}
}

function ajouterLigne(texte) {
	let tr = document.createElement("tr");

	let tdTexte = document.createElement("td");
	tdTexte.innerText = texte;

	let tdActions = document.createElement("td");
	let btnModifier = document.createElement("button");
	btnModifier.innerText = "Modifier";
	btnModifier.addEventListener("click", function() {
		modifierLigne(tr, texte);
	});

	let btnSupprimer = document.createElement("button");
	btnSupprimer.innerText = "Supprimer";
	btnSupprimer.addEventListener("click", function() {
		cacherLigne(tr);
	});

	tdActions.appendChild(btnModifier);
	tdActions.appendChild(btnSupprimer);

	tr.appendChild(tdTexte);
	tr.appendChild(tdActions);

	tableBody.appendChild(tr);
}

function modifierLigne(tr, texte) {
	let nouveauTexte = prompt("Nouveau texte :", texte);
	if (nouveauTexte !== null) {
		tr.childNodes[0].innerText = nouveauTexte;
	}
}

function cacherLigne(tr) {
	tr.classList.add("hide");
}

  </script>
</body>
</html>
