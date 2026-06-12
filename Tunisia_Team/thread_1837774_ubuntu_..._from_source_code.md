---
title: "ubuntu ... from source code"
date: 2011-09-02
forum: Tunisia Team
---

### Post by micronet on 2011-09-02
bonjour,

l'une des distributions qui assure l'utilisation des logiciels open-source d'une manière optimale est sans doute Gentoo. Le problème de cette distribution est qu'elle est difficile à installer et à utiliser, surtout pour ceux qui sont habitués à la facilité d'ubuntu. j'ai donc pensé à utiliser ubuntu d'une maniere semblable à celle de gentoo, c.a.d. installer les application à partir de leurs codes source et éviter les packages pré-compilés.

voila, j'ai cherché sur le net et j'ai trouvé cette solution:
sudo apt-get build-dep <package>
sudo apt-get -b source <package>

le problème avec cette solution est qu'elle n'assure que la compilation du package, mais toutes les dépendances sont installé normalement(binaire pré-compilé, on n'a rien fait donc).

y a t il une méthode assez simple qui permet de tout auto-compiler sur ma machine?

merci d'avance

---

