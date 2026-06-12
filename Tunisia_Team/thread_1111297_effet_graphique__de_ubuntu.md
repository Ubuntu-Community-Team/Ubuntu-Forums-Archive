---
title: "effet graphique  de ubuntu"
date: 2009-03-30
forum: Tunisia Team
---

### Post by dark of angel on 2009-03-30
bj depuis  l installation de   ubuntu8.10 jai confronter plusieurs poblemes et hamdoulilah certain je peut les manipuler et les autre je prend laide de ce precieux forum:
en exploitant j ai trouver que certain effet visuelle comme 2d et 3d sont inaccessible soit pour la mediocre de ma carte gra ou les paquets necessaire  pour ca  dans ce cas je veut savoir ces paquets necessaire a telecharger 
merci pour l aide "nje7 mtawasel"

---

### Post by alaya.zied on 2009-03-31
je pense que tu a une carte graphique dont le pilote n'est pas open source.
pour pouvoir accéder aux effets graphiques, tu doit installé le pilote propriètaire de ta carte.
Dans ce cas, voivi ce qu'il faut faire:
1-Connecte toi sur internet
2-va dans System -> Administration -> Hardware drivers
3- normalement, il detctera ta carte.  clique sur le drivers et choisi Activate

Ubuntu va chercher le driver sur internet, le télécharge puis l'installe :)

---

### Post by fballem on 2009-03-31
D'abord, je vous en prie de m'excuse le français - c'est vraiment ma deuxième langue.

Est-ce-que vous donnez plus des reseignment détailés de votre carte graphique, nous pourrons vous aider mieux.

Merci,

---

### Post by omrisaber on 2009-03-31
Alors vous avez l'une des deux cas :
-soit vous n'avez pas activé les effets (clic droit sur le bureau -> changer l'arriere plan -> onglet "effet" -> effets max)
-soit vous n'avez pas activé la prise en charge du driver propriétaire de votre carte graphique comme a dit zied :
> Dans ce cas, voivi ce qu'il faut faire:
1-Connecte toi sur internet
2-va dans System -> Administration -> Hardware drivers
3- normalement, il detctera ta carte. clique sur le drivers et choisi Activate
Si la couleur du bouton est rouge, vous devez l'activer ;)

PS: vous pouvez vous rendre sur le gestionnaire de paquet "synaptic" et chercher s'il y a des paquets "compiz" manquant et l'installer.

---

### Post by dark of angel on 2009-04-01
le problem est que le gestionnaire de peripherique ne dectecte aucun pilote 
pour plus maider c est ma carte mere de reference 661FX-MREV:1.0
merci pour laide

---

### Post by alaya.zied on 2009-04-02
Bonjour dark of angel,
stp tape la commande suivante dans un terminal:
```
lspci
```
puis copie coller ce que te donne.

ça nous permettra de savoir , entre autre, la ref de ta carte graphique.

---

### Post by RachedTN on 2009-04-02
Bonjour Dark of angel 
Je récapitule les nfos que tu dois nous fournir pour pouvoir t'aider :
résultat de commande : lspci
résultat de commande : cat /proc/cpuinfo
type de carte graphique
taille de RAM
marque de votre PC : assemblé ou bien de marque comme : Siemens ..
Nous attendons votre réponse :)
@+

---

### Post by dark of angel on 2009-04-02
la caracteristique demes cartes sont :


00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
00:0a.0 Ethernet controller: Hangzhou Silan Microelectronics Co., Ltd. RTL8139D [Realtek] PCI 10/100BaseTX ethernet adaptor (rev 01)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
nb: meme j ai cherche les pilote convenable et je ne trouve pas 
merci d avance
(ram 736
versus p4

---

### Post by MaWaLe on 2009-04-02
@Rached : tu as demandé une masse d'info qui dépasse de loin le nécessaire pour orienter notre ami

Sinon : avant de commencer à aller vers la détection d'un éventuel problème, il faut commencer simple : 
-Tu fais un clic droit sur un emplacement vide de ton écran
- Tu choisis la dernière option : changer l'arrière plan de ton bureau
- Dans la fenêtre qui s'ouvre, tu choisis le dernier onglet : Effets visuels
- Tu choisis le troisième (dernier) radio-button : EXTRA

si le tout se passe bien c'est que tu n'as pas à priori besoin de pilote spécifique pour ta carte (pour les nVidia et ATI il te demande d'activer le pilote proprio si ce n'est pas déjà fait)

Là tu vas constater que plusieurs effets s'ajouternt à ton brueau


Maintenant pour avoir plus d'effets, il faut installer Compiz-Fusion

Par ailleurs, j'attire ton attention que l'objectif n'est pas de faire joli puisque compiz ralenti l'ordinateur surtout si ce dernier ne dispose pas assez de puissance et de RAM.

Une autre remarque : pourquoi tu as 736 de RAM. Il est toujours conseillé d'avoir une RAM qui est égale à une puissance de 2 et non pas un multiple de deux.

---

### Post by dark of angel on 2009-04-02
merci  pour les conseil 
j ai fais le test comme tu as dit mais il m affiche " Les effets visuels n'ont pas pu être activés" pour la RAM:(256+512)

---

### Post by omrisaber on 2009-04-02
Salam..
Pour bénéficier des effets de bureau, il faut que l'accélération 3D soit opérationnelle.
Que donne la commande :
> glxinfo | grep -i direct
si c'est : "direct rendering: Yes" donc pas de problème hard !

---

### Post by MaWaLe on 2009-04-03
> **dark of angel said:**
> merci  pour les conseil 
j ai fais le test comme tu as dit mais il m affiche " Les effets visuels n'ont pas pu être activés" pour la RAM:(256+512)

suite à ce message, tu peux être sûr à 80% que ta carte graphique nécessite des pilotes "third party" donc il faut les activer.
Dans ce cas ru cliques sur Système>Administration>Pilotes de Périphériques

Tu es sensé alors voir les périphériques nécessitant un pilote tierce partie apparaitre. De même je te conseille d'aller vérifier la compatibilité de ta carte avec Linux en général (Vérifier les HAL)


Pour la RAM, j'ai bien compris que tu as une 512+256 mais l'idéal (ce qui est toujorus conseillé) c'est d'avoir des barrettes mémoires jumelles (même taille et voir même marque aussi).

---

### Post by RachedTN on 2009-04-03
@ MaWale : je n'ai pas demandé une masse d'info qui dépasse de loin ce qui est demandé, j'explique pour toi, déjà tu connais tout ça, et pour les autres :
* commande : lspci   : pour voir si ubuntu reconaisse ou pas la carte graphique
résultat : 01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
=> ubuntu reconaisse la carte :)

*commande : cat /proc/cpuinfo : pour voir le type de processeur : si c'est un P II ou P I alors c'est inutile d'essayer ce type d'effets ;)

*type de carte graphique : pour faire une petite recherche sur google et voir s'il y'a un thread similaire qui a été traité avant, et aussi en cas ou lspci ne retourne pas de résultat à propos de la carte graphique.

taille de RAM : c'est évidente cette question 

marque de votre PC : assemblé ou bien de marque comme : Siemens ..  : si le PC st de marque, alors c'est fort probable que quelqu'un a rencontré le même problème, donc il y'aura certainement une info sur le net.

Sinon, dark angel, tu peux essayer de retirer la RAM de 256, et essayer si ça marche ou pas, si ça marche : tu peux essayer de changer ta RAM 256 avec une de 512 + un peu d'argent, si ça marche pas, inutile d'acheter une de 512 car ça ne vas pas régler le pb.

---

### Post by dark of angel on 2009-04-03
> **omrisaber said:**
> Salam..
Pour bénéficier des effets de bureau, il faut que l'accélération 3D soit opérationnelle.
Que donne la commande :

si c'est : "direct rendering: Yes" donc pas de problème hard !

[oui cest yes ]

---

### Post by dark of angel on 2009-04-03
apparemment il n y a pas de driver de sis sur ubuntu 8.10 pour la carte graphique ou la carte son

---

### Post by Charly64 on 2009-05-23
bonjour  à tous

J'ai un problème un peu semblable.  

root@phantom-laptop:~# lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
00:1f.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 04)


root@phantom-laptop:~# cat /proc/cpuinfo 
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Pentium(R) Dual  CPU  T2390  @ 1.86GHz
stepping    : 13
cpu MHz        : 800.000
cache size    : 1024 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm
bogomips    : 3733.80
clflush size    : 64
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Pentium(R) Dual  CPU  T2390  @ 1.86GHz
stepping    : 13
cpu MHz        : 800.000
cache size    : 1024 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm
bogomips    : 3733.45
clflush size    : 64
power management:

En réalité je pense qu'il s'agit de mes pilotes graphiques qui sont pas installés. j'arrive pas à les trouver non plus et ce forum est mon dernier recours. Mon affichage est très archaique 
Merci pour vos futures réponses.

---

### Post by dark of angel on 2009-05-24
pour la mienne 
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 3
model name	: Intel(R) Pentium(R) 4 CPU 2.40GHz
stepping	: 3
cpu MHz		: 2405.598
cache size	: 1024 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc up pebs bts pni dtes64 monitor ds_cpl cid
bogomips	: 4811.19
clflush size	: 64
power management:
< desole mon pote mais sis c'est de la misère

---

