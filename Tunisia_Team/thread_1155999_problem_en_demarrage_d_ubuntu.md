---
title: "problem en demarrage d ubuntu"
date: 2009-05-11
forum: Tunisia Team
---

### Post by dark of angel on 2009-05-11
j ai ubuntu 8.10 et a laide de gestionnaire de mise ajours jai  aller vers ubuntu9.04 en téléchargent 675 fichiers sur 1086 demandes et pour certain raison j ai arreter l ordinateur apres l annulation la continuation de mis e ajours
alors en redémarrant l ordinateur autre fois j ai le symbole de ubuntu 9.04 en train de telechargent (cherchant les fichiers pour démarrer ) mais cet recherche reste longtemps et en fin une fenêtre noir est ouvrit en disant que 
"/dev/disk/by-uuid/71f3fe62 ...est missing" alors  dans cette situation je  ne peux pas ouvrir mon pc bloquant dans cet etat qui se repete a chaque demarrage (cest  une boucle)

!!!!!!!…¿,,¿c est koi la solution( cest quel code a taper)b et merci de me comprendrequ est ce qu il passe a ce misere pc

---

### Post by Nizarus on 2009-05-11
ton message d'erreur indique qu'il y a un problème pour trouver ton disque ou un fichier de ton disque. Peux tu nous donner le message d'erreur complet ?

---

### Post by dark of angel on 2009-05-11
> **Nizarus said:**
> ton message d'erreur indique qu'il y a un problème pour trouver ton disque ou un fichier de ton disque. Peux tu nous donner le message d'erreur complet ?
thnx for ur caring 
le problem est lorsque la translation de ubuntu 8.10 vers ubuntu9.04 et suite de l interruption de telechargement certain fichiers un message "vouler vous remplacer certain fichiers ou conserver certain fichier( je ne les rappelles plus) ma reponse est de la changer  (apparament: dou vient le problem)
le message d erreur complet est
"/dev/disk/by-uuid/71f3fe62-ff56-4186-b805-18811bc-544ae"

---

### Post by Nizarus on 2009-05-13
donc apparemment l'un de tes disques (ou partitions) n'est plus reconnu :/
il faut peut être faire une installation fr&#265;he de ubuntu !!

---

### Post by hanen105 on 2009-05-13
Salut dark of angel,

En fait, t'aurais pu essayer la comparaison entre l'uuid marqué dans ton menu.lst avec celui référençant réellement ta partition bootable (qui doivent coincider, mais pas après cette fausse manoeuvre dont t'as fais qui a arrété le processus de mise à jour des dépendances système pour tenir en compte la nouvelle version du kernel)

- (Ctrl + Alt + F4) tu seras redirigé en mode console

- tu tapes  [COLOR="Red"]blkid[/COLOR]  (tu peux faire [COLOR="Red"]man blkid[/COLOR] avant pour comprendre ce qui ce se passera :)

- tu prends note de l'uuid de ta partition bootable 

- tu vérifies si c'est le même que celui marqué sur ton menu.lst en tapant par ex:    [COLOR="Red"]vi /boot/grub/menu.lst[/COLOR]
(çà dépend de l'emplacement de ton /boot monté à part: [COLOR="Yellow"][COLOR="Lime"]/media/boot[/COLOR][/COLOR] ou simplement en dessous de ton / racine: [COLOR="Lime"]/boot[/COLOR])

---

### Post by dark of angel on 2009-05-14
> **hanen105 said:**
> Salut dark of angel,

En fait, t'aurais pu essayer la comparaison entre l'uuid marqué dans ton menu.lst avec celui référençant réellement ta partition bootable (qui doivent coincider, mais pas après cette fausse manoeuvre dont t'as fais qui a arrété le processus de mise à jour des dépendances système pour tenir en compte la nouvelle version du kernel)

- (Ctrl + Alt + F4) tu seras redirigé en mode console

- tu tapes  [COLOR="Red"]blkid[/COLOR]  (tu peux faire [COLOR="Red"]man blkid[/COLOR] avant pour comprendre ce qui ce se passera :)

- tu prends note de l'uuid de ta partition bootable 

- tu vérifies si c'est le même que celui marqué sur ton menu.lst en tapant par ex:    [COLOR="Red"]vi /boot/grub/menu.lst[/COLOR]
(çà dépend de l'emplacement de ton /boot monté à part: [COLOR="Yellow"][COLOR="Lime"]/media/boot[/COLOR][/COLOR] ou simplement en dessous de ton / racine: [COLOR="Lime"]/boot[/COLOR])
merci b1 
 ca marche en tapant ces commandes

---

