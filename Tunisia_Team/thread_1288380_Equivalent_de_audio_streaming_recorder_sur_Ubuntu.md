---
title: "Equivalent de audio streaming recorder sur Ubuntu"
date: 2009-10-11
forum: Tunisia Team
---

### Post by wael_k on 2009-10-11
Bonjour,

Je suis à la recherche d'un logiciel ou peux etre une extension de firefox (j'ai bien cherché mais en vain) qui me permet d'extraire des sons à partir d'une video en streaming, une radio ...
Un exemple de logiciel sous Windows c'est : Audio Streaming Recorder...

Merci [IMG]http://forum.ubuntu-fr.org/img/smilies/smile.png[/IMG]


[http://tunisiangeeks.wordpress.com](http://tunisiangeeks.wordpress.com)

---

### Post by Neo31 on 2009-10-12
Salut,
Il y a un plugin de firefox qui s'appel DownloadHelper.
Sinon pour les Radio tu pe utiliser un outil console qui s'appel StreamRipper, il permet d'enregistrer la radio et servir comme serveur local, (tu pe enregistrer et écouteur sans doubler l'utilisation de la bande passante)
J'espère que c'est suffisant comme informations, je suis pas pour plus de détails en cas de besoin.
Bonne chance.

Edit :
desole, une petite rectification, DownloadHelper c'est pour télécharger de l'audio ou de la video, mais ce n'est pas pour extraire l'audio depuis une video, de brouille toi pour faire ça. Ce n'est pas difficile a faire (essaye les logiciel de montage video par exemple si tu trouve pas une solution plus facile).

---

### Post by wael_k on 2009-10-18
Merci à toi,
J'avais compri que ce n'était pas vraiment simple de l'extraire sur Ubuntu :(
Ceci dit je ne vais pas repasser sur windows mais je vais essayer de trouver un moyen pas très dure (sans passer par des logiciels de montage ...)
Si un jour je trouve une solution je la posterais :) !
thanx

---

### Post by Neo31 on 2009-10-22
Salut Wael,


[LIST]
[*].
[/LIST]
Je n'avais pas accès a Internet la semaine dernière et je n'ai lu ton message que hier soir.  
Maintenant que j'ai un peu de temps voila une solution complète :
1. Téléchargement des videos avec le plugin de Firefox DownloadHelper
2. Extraction du son avec AVIDemux


[LIST]
[*].
[/LIST]
   Appartement tu n'aime pas les logiciels de montage video, mais c'est très simple a utiliser avidemux spécialement est simple et facile a utiliser. Donc voila comment faire (je m'excuser d'écrire les noms des options et menus en anglais parce que j'utilise un système anglais a 100% donc a toi de traduire)


[LIST]
[*].
[/LIST]
    Commençant par télécharger le plugin de téléchargement des videos. Pour ceci ouvre Firefox et fait ça : Tools > add-ons > get addons (outils > modules complémentaires > ???) puis écrit  DownloadHelper pour chercher le plugin et clic sur Add to firefox (ajouter a firefox). Voila il ne reste plus que de redémarrer firfox et tu verra la petite icône [[IMG]http://www.image-share.com/upload/76/166.png[/IMG]]("http://www.image-share.com/") qui sera animée quand le plugin détecte une video à télécharger.


[LIST]
[*].
[/LIST]
    On passe maintenant à télécharger avidemux. La je doit vous dire que j'utilise fedora et que je vais écrire comment j'ai fait sur fedora donc assure toi que tu fait la même chose avec la bonne méthode pour ubuntu.
On commence par ouvrir le terminal et exécuter la commande d'installation de avidemux avec les privilèges root.
pour ceci j'ai utiliser cette commande sur fedora :
```
 su -c 'yum install avidemux avidemux-plugins'
```je pense que l'équivalent sur ubuntu est :
```
 sudo apt-get install avidemux avidemux-plugins
```Voila donc, tout est prêt.


[LIST]
[*].
[/LIST]
    Après avoir télécharger une video avec DownloadHelper voila comment en extraire l'audio :
1. Ouvrir avidemux
2. File > open (fichier > ouvrir)
3. Sélectionne la video (avidemux support plusieurs formats, même le format flv)
4. Sélectionne le format de l'audio désirée (voir l'image ci-dessou). ceci est possible a travers la petite liste dans la catégorie Audio a gauche (la liste est juste au-dessus du bouton configure - configurer)
5. Menu Audio > save (audio > enregistrer) (voir l'image ci-dessou)
6. Écrit le nom du fichier audio sans oublier de taper la bonne extension a la fin du nom.
et voila on y ai. c'est peut être une longue explication mais croie moi, c'est très facile a faire.
[[IMG]http://www.image-share.com/upload/76/167m.png[/IMG]]("http://www.image-share.com/image.php?img=76/167.png")


[LIST]
[*].
[/LIST]
    Bonne chance, et n'oublie pas de nous informer si tout ete bien passer.
Be free, be GNU/Linux ;)
Neo31

---

### Post by omrisaber on 2009-10-23
Très bien expliqué Neo .. Bravo !
Je vous félicites :)

---

### Post by Neo31 on 2009-10-23
Merci omrisaber. Mais c'est toujours rien parce que je doit beaucoup a la communauté GNU/Linux.
J'espère aussi que ça évolue plus rapidement en Tunisie :) Donc je fait de mon mieux :)

---

