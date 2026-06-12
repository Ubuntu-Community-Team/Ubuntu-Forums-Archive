---
title: "Virtual machine has terminated unexpectedly during startup"
date: 2009-05-11
forum: Tunisia Team
---

### Post by dark of angel on 2009-05-11
apres l installation de virtual box puis preparer la partie avirtualiser et suivant une coupure surpris de la tension de courant (partie steg) en redemmarant le virtual ne marche plus et ce message apparaisse :
 
"The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Re-setup the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu or Fedora should install the DKMS package at first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary."

alors comment faire pour conserver le travaille enregistrer &  faire marcher le virtualbox

---

### Post by omrisaber on 2009-05-11
> **dark of angel said:**
> 
"The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Re-setup the kernel module by executing

'/etc/init.d/vboxdrv setup'


Vous tapez tout simplement la commande indiquée ;) (normalement il y aura une recompilation du noyau pour la prise en charge de la virtualisation)

---

### Post by alaya.zied on 2009-05-12
c'est quelle version de Virtualbox tu utilise ?
je me rappelle qu'avec l'ancien version OSE il faut installer le driver (c'est le vboxdrv).

si non une recherche dans ton synatptic de vboxdrv, ça te donne quoi dans les paquets trouver ?

---

### Post by dark of angel on 2009-05-12
> **alaya.zied said:**
> c'est quelle version de Virtualbox tu utilise ?
je me rappelle qu'avec l'ancien version OSE il faut installer le driver (c'est le vboxdrv).

si non une recherche dans ton synatptic de vboxdrv, ça te donne quoi dans les paquets trouver ?

la recherche ne te donne rien comme paquet 
le seul paquet simulant est vboxgtk ?

---

### Post by dark of angel on 2009-05-12
> **omrisaber said:**
> Vous tapez tout simplement la commande indiquée ;) (normalement il y aura une recompilation du noyau pour la prise en charge de la virtualisation)

la repose de taper dans une console est
 *Usage: /etc/init.d/vboxdrv {start|stop|restart|status}
?

---

### Post by omrisaber on 2009-05-12
> **dark of angel said:**
> la repose de taper dans une console est
 *Usage: /etc/init.d/vboxdrv {start|stop|restart|status}
?

Bon , l'usage c'est :
```
/etc/init.d/vboxdrv start
```
--> pour démarrer le driver de VirtualBox, si ça génère un message d'erreur (normalement il vous dit de recompiler le noyau) alors là, comme a dit zied, tu réinstalles le paquet du driver "vboxdrv", et ensuite il va vous recompiler automatiquement le kernel ;)

---

### Post by MaWaLe on 2009-05-14
ce que je te propose c'est de désinstaller carrément les paquets en place de vbox (actuellement tu dois avoir le vboxgtk (linterface graphique de vBox) et les paquets de vbox OSE.
ensuite tu réinstalles et je te conseille d'ailleurs d'installer la PUEL.
ensuite il faut ajouter ton compte au groupe vboxsuers et à la fin tu relances juste ta session (sans avoir à redémarrer la machine).

---

