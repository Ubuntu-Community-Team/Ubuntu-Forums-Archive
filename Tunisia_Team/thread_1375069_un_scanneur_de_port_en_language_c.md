---
title: "un scanneur de port en language c"
date: 2010-01-07
forum: Tunisia Team
---

### Post by dark of angel on 2010-01-07
salut a tous
 j'ai 2 question :
1-comment programmer en c sous ubuntu 9.04(compilateur simple du c)
2- j'ai fuis l'internet et j'ai pas trouver sous [c]  un  code qui permet de scanner les ports actifs   et donner l'application corespondante achaque ports
 et merci

---

### Post by alaya.zied on 2010-01-08
Bonjour 
pour installer le compilateur:
sudo apt-get install build-essential

ceci te permettra d'avoir le compilateur en mode commande. si tu veux avoir un interface graphique, le plus simple que je connais est Geany. Une fois installé, tu écris ton code, save it with .c extention, build with F9 and excute with F5.

Attention, à chaque modification il faut refaire le build, si non il exécute le dernier programme.

---

### Post by SalahTr on 2010-01-08
Bonjour,
> **dark of angel said:**
> 
1-comment programmer en c sous ubuntu 9.04(compilateur simple du c)

Le compilateur** C** sous le linux est [GCC]("http://fr.wikipedia.org/wiki/GNU_Compiler_Collection"). 
Voici un exemple de code source en** C**:
```
[COLOR="DarkOrchid"]#include[/COLOR] [COLOR="Magenta"]<stdio.h>[/COLOR]
[COLOR="Green"]void[/COLOR] main ([COLOR="#008000"]int[/COLOR] argc, [COLOR="#008000"]char[/COLOR] *argv[])
{
	printf([COLOR="#ff00ff"]"Hello World"[/COLOR]);
}
```
Pour compiler exécutes :
```
gcc HelloWorld.c
```
Si le source ne contient pas d'erreurs la compilation produit un exécutable nommé **a.out**. La commande qui permet de lancer l'exécutable est la suivante : 
```
./a.out
```
Si tu veux changer le nom de l'exécutable, utilises l'option** -o** 
```
gcc HelloWorld.c -o HelloWorld [COLOR="Blue"]*#Le fichier exécutable sera nommé HelloWorld*[/COLOR]
```
> **dark of angel said:**
> 
2- j'ai fuis l'internet et j'ai pas trouver sous [c]  un  code qui permet de scanner les ports actifs
J'ai un code source permettant cela (dans mon PC à la maison), je te l'enverrai ce soir
> **dark of angel said:**
> 
donner l'application corespondante achaque ports
Consultes [la liste des ports logiciels]("http://fr.wikipedia.org/wiki/Liste_des_ports_logiciels")

---

### Post by SalahTr on 2010-01-08
Voici le code source

---

