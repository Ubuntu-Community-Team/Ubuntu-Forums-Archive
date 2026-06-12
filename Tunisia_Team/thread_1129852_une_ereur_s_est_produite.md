---
title: "une ereur s est produite"
date: 2009-04-19
forum: Tunisia Team
---

### Post by dark of angel on 2009-04-19
"W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: Les signatures suivantes n'ont pas pu être vérifiées car la clé publique n'est pas disponible*: NO_PUBKEY 60487016493B3065"
lorsque je fais le mise ajours ce message est apparut , je comprend que j ai télécharger une mise ajours n est pas authentifiée encore mais pourquoi s est produit cette 'faute ' et comment la corrige .

---

### Post by Nizarus on 2009-04-19
ce n'est pas une erreur mais plutôt un avertissement. Apparemment tu as ajouté un dépôt tierce partie sans que tu ajoute la clé d'authentification.
Il est recommandé d'ajouter cette clé.

---

### Post by RachedTN on 2009-04-20
Comme a dis nizarus ,lors de l'ajout d'un dépot tierce partie au fichier sources.list, il est aussi récommandé que tu ajoute son clé, par exemple : 
wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -
donc essaye de voir dequel dépot s'agit il et ajoute son clé :)

---

