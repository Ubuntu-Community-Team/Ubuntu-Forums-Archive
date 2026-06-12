---
title: "apt-get and dpkg problems"
date: 2006-08-25
forum: Repositories &amp; Backports
---

### Post by FonskarWild on 2006-08-25
Hi,

I have had a lot of problems since i installed dapper but this forum fortunately got me out of trouble execpt for one thing.
Since the first day whaen i want to install a package with synaptic or apt-get or even remove a packet it works but i have such messages and the new packet is added at the end of the list:
```
Paramétrage de libdvdread3 (0.9.4-5.1) ...
/var/lib/dpkg/info/libdvdread3.postinst: line 41: ldconfig : commande introuvable
dpkg : erreur de traitement de libdvdread3 (--configure) :
 le sous-processus post-installation script a retourné une erreur de sortie d'état 127
Paramétrage de libssl0.9.7 (0.9.7g-5ubuntu1) ...
/var/lib/dpkg/info/libssl0.9.7.postinst: line 141: ldconfig : commande introuvable
dpkg : erreur de traitement de libssl0.9.7 (--configure) :
 le sous-processus post-installation script a retourné une erreur de sortie d'état 127
Paramétrage de liba52-0.7.4 (0.7.4-1) ...
/var/lib/dpkg/info/liba52-0.7.4.postinst: line 5: ldconfig : commande introuvable
dpkg : erreur de traitement de liba52-0.7.4 (--configure) :
 le sous-processus post-installation script a retourné une erreur de sortie d'état 127
Paramétrage de libungif4g (4.1.4-1) ...
/var/lib/dpkg/info/libungif4g.postinst: line 5: ldconfig : commande introuvable
dpkg : erreur de traitement de libungif4g (--configure) :
 le sous-processus post-installation script a retourné une erreur de sortie d'état 127
Paramétrage de libdrm2 (2.0.2+cvs20060824) ...
/var/lib/dpkg/info/libdrm2.postinst: line 5: ldconfig : commande introuvable
dpkg : erreur de traitement de libdrm2 (--configure) :
 le sous-processus post-installation script a retourné une erreur de sortie d'état 127
Paramétrage de libgsm1 (1.0.10-13) ...
/var/lib/dpkg/info/libgsm1.postinst: line 4: ldconfig : commande introuvable
dpkg : erreur de traitement de libgsm1 (--configure) :
 le sous-processus post-installation script a retourné une erreur de sortie d'état 127
Paramétrage de libsdl-image1.2 (1.2.4-1) ...
/var/lib/dpkg/info/libsdl-image1.2.postinst: line 5: ldconfig : commande introuvable
dpkg : erreur de traitement de libsdl-image1.2 (--configure) :
 le sous-processus post-installation script a retourné une erreur de sortie d'état 127
Paramétrage de libmpcdec3 (1.2.2-1) ...
/var/lib/dpkg/info/libmpcdec3.postinst: line 5: ldconfig : commande introuvable
dpkg : erreur de traitement de libmpcdec3 (--configure) :
 le sous-processus post-installation script a retourné une erreur de sortie d'état 127
dpkg : des problèmes de dépendances empêchent la configuration de gstreamer0.10-plugins-ugly :
 gstreamer0.10-plugins-ugly dépend de liba52-0.7.4 ; cependant :
  Paquet liba52-0.7.4 n'est pas encore configuré.
 gstreamer0.10-plugins-ugly dépend de libdvdread3 ; cependant :
  Paquet libdvdread3 n'est pas encore configuré.
dpkg : erreur de traitement de gstreamer0.10-plugins-ugly (--configure) :
 problèmes de dépendances - laissé non configuré
Paramétrage de gftp-text (2.0.18-11ubuntu1) ...
/var/lib/dpkg/info/gftp-text.postinst: line 8: update-alternatives : commande introuvable
dpkg : erreur de traitement de gftp-text (--configure) :
 le sous-processus post-installation script a retourné une erreur de sortie d'état 127
Paramétrage de wifi-radar (1.9.6-0ubuntu4) ...
/var/lib/dpkg/info/wifi-radar.postinst: line 18: update-rc.d : commande introuvable
dpkg : erreur de traitement de wifi-radar (--configure) :
 le sous-processus post-installation script a retourné une erreur de sortie d'état 127
Paramétrage de libxosd2 (2.2.14-1.2ubuntu2) ...
/var/lib/dpkg/info/libxosd2.postinst: line 5: ldconfig : commande introuvable
dpkg : erreur de traitement de libxosd2 (--configure) :
 le sous-processus post-installation script a retourné une erreur de sortie d'état 127
Paramétrage de libpoppler1 (0.5.3-0ubuntu1) ...
/var/lib/dpkg/info/libpoppler1.postinst: line 5: ldconfig : commande introuvable
dpkg : erreur de traitement de libpoppler1 (--configure) :
 le sous-processus post-installation script a retourné une erreur de sortie d'état 127
Paramétrage de libdvdcss2 (1.2.9-1plf4) ...
/var/lib/dpkg/info/libdvdcss2.postinst: line 5: ldconfig : commande introuvable
dpkg : erreur de traitement de libdvdcss2 (--configure) :
 le sous-processus post-installation script a retourné une erreur de sortie d'état 127
dpkg : des problèmes de dépendances empêchent la configuration de mencoder :
 mencoder dépend de libdvdread3 ; cependant :
  Paquet libdvdread3 n'est pas encore configuré.
 mencoder dépend de libmpcdec3 ; cependant :
  Paquet libmpcdec3 n'est pas encore configuré.
 mencoder dépend de libungif4g (>= 4.1.3) ; cependant :
  Paquet libungif4g n'est pas encore configuré.
dpkg : erreur de traitement de mencoder (--configure) :
 problèmes de dépendances - laissé non configuré
dpkg : des problèmes de dépendances empêchent la configuration de poppler-utils :
 poppler-utils dépend de libpoppler1 (>= 0.5.1) ; cependant :
  Paquet libpoppler1 n'est pas encore configuré.
dpkg : erreur de traitement de poppler-utils (--configure) :
 problèmes de dépendances - laissé non configuré
dpkg : des problèmes de dépendances empêchent la configuration de tcltls :
 tcltls dépend de libssl0.9.7 ; cependant :
  Paquet libssl0.9.7 n'est pas encore configuré.
dpkg : erreur de traitement de tcltls (--configure) :
 problèmes de dépendances - laissé non configuré
Paramétrage de nasm (0.98.38-1.2) ...
/var/lib/dpkg/info/nasm.postinst: line 10: install-info : commande introuvable
dpkg : erreur de traitement de nasm (--configure) :
 le sous-processus post-installation script a retourné une erreur de sortie d'état 127
Paramétrage de libdc1394-13 (1.1.0-3) ...
/var/lib/dpkg/info/libdc1394-13.postinst: line 5: ldconfig : commande introuvable
dpkg : erreur de traitement de libdc1394-13 (--configure) :
 le sous-processus post-installation script a retourné une erreur de sortie d'état 127
Paramétrage de libaa1-dev (1.4p5-30) ...
/var/lib/dpkg/info/libaa1-dev.postinst: line 5: install-info : commande introuvable
dpkg : erreur de traitement de libaa1-dev (--configure) :
 le sous-processus post-installation script a retourné une erreur de sortie d'état 127
Paramétrage de libartsc0 (1.5.2-0ubuntu1) ...
/var/lib/dpkg/info/libartsc0.postinst: line 5: ldconfig : commande introuvable
dpkg : erreur de traitement de libartsc0 (--configure) :
 le sous-processus post-installation script a retourné une erreur de sortie d'état 127
Paramétrage de libtar (1.2.11-4) ...
/var/lib/dpkg/info/libtar.postinst: line 5: ldconfig : commande introuvable
dpkg : erreur de traitement de libtar (--configure) :
 le sous-processus post-installation script a retourné une erreur de sortie d'état 127
Paramétrage de libdvdnav4 (0.1.9-3) ...
/var/lib/dpkg/info/libdvdnav4.postinst: line 5: ldconfig : commande introuvable
dpkg : erreur de traitement de libdvdnav4 (--configure) :
 le sous-processus post-installation script a retourné une erreur de sortie d'état 127
dpkg : des problèmes de dépendances empêchent la configuration de vlc :
 vlc dépend de liba52-0.7.4 ; cependant :
  Paquet liba52-0.7.4 n'est pas encore configuré.
 vlc dépend de libdc1394-13 ; cependant :
  Paquet libdc1394-13 n'est pas encore configuré.
 vlc dépend de libdvdnav4 (>= 0.1.9) ; cependant :
  Paquet libdvdnav4 n'est pas encore configuré.
 vlc dépend de libdvdread3 ; cependant :
  Paquet libdvdread3 n'est pas encore configuré.
 vlc dépend de libgsm1 (>= 1.0.10) ; cependant :
  Paquet libgsm1 n'est pas encore configuré.
 vlc dépend de libmpcdec3 ; cependant :
  Paquet libmpcdec3 n'est pas encore configuré.
 vlc dépend de libsdl-image1.2 (>= 1.2.3) ; cependant :
  Paquet libsdl-image1.2 n'est pas encore configuré.
 vlc dépend de libtar ; cependant :
  Paquet libtar n'est pas encore configuré.
dpkg : erreur de traitement de vlc (--configure) :
 problèmes de dépendances - laissé non configuré
dpkg : des problèmes de dépendances empêchent la configuration de mplayer :
 mplayer dépend de libartsc0 (>= 1.5.2-0) ; cependant :
  Paquet libartsc0 n'est pas encore configuré.
 mplayer dépend de libdvdread3 ; cependant :
  Paquet libdvdread3 n'est pas encore configuré.
 mplayer dépend de libmpcdec3 ; cependant :
  Paquet libmpcdec3 n'est pas encore configuré.
 mplayer dépend de libungif4g (>= 4.1.3) ; cependant :
  Paquet libungif4g n'est pas encore configuré.
dpkg : erreur de traitement de mplayer (--configure) :
 problèmes de dépendances - laissé non configuré
Paramétrage de libmpeg2-4 (0.4.0b-4ubuntu1) ...
/var/lib/dpkg/info/libmpeg2-4.postinst: line 5: ldconfig : commande introuvable
dpkg : erreur de traitement de libmpeg2-4 (--configure) :
 le sous-processus post-installation script a retourné une erreur de sortie d'état 127
Paramétrage de libiso9660-4 (0.76-1ubuntu1) ...
/var/lib/dpkg/info/libiso9660-4.postinst: line 5: ldconfig : commande introuvable
dpkg : erreur de traitement de libiso9660-4 (--configure) :
 le sous-processus post-installation script a retourné une erreur de sortie d'état 127
Paramétrage de libglitz1 (0.5.6-0ubuntu1) ...
/var/lib/dpkg/info/libglitz1.postinst: line 5: ldconfig : commande introuvable
dpkg : erreur de traitement de libglitz1 (--configure) :
 le sous-processus post-installation script a retourné une erreur de sortie d'état 127
Paramétrage de libdvbpsi4 (0.1.5-1) ...
/var/lib/dpkg/info/libdvbpsi4.postinst: line 5: ldconfig : commande introuvable
dpkg : erreur de traitement de libdvbpsi4 (--configure) :
 le sous-processus post-installation script a retourné une erreur de sortie d'état 127
Paramétrage de libgii0 (0.9.1-0.1ubuntu1) ...
/var/lib/dpkg/info/libgii0.postinst: line 21: ldconfig : commande introuvable
dpkg : erreur de traitement de libgii0 (--configure) :
 le sous-processus post-installation script a retourné une erreur de sortie d'état 127
Paramétrage de libmad0 (0.15.1b-2.1) ...
/var/lib/dpkg/info/libmad0.postinst: line 5: ldconfig : commande introuvable
dpkg : erreur de traitement de libmad0 (--configure) :
 le sous-processus post-installation script a retourné une erreur de sortie d'état 127
dpkg : des problèmes de dépendances empêchent la configuration de libggi2 :
 libggi2 dépend de libgii0 (>= 1:0.9.1-0.1ubuntu1) ; cependant :
  Paquet libgii0 n'est pas encore configuré.
dpkg : erreur de traitement de libggi2 (--configure) :
 problèmes de dépendances - laissé non configuré
dpkg : des problèmes de dépendances empêchent la configuration de gftp :
 gftp dépend de gftp-text (= 2.0.18-11ubuntu1) ; cependant :
  Paquet gftp-text n'est pas encore configuré.
dpkg : erreur de traitement de gftp (--configure) :
 problèmes de dépendances - laissé non configuré
Paramétrage de libmodplug0c2 (0.7-5) ...
/var/lib/dpkg/info/libmodplug0c2.postinst: line 5: ldconfig : commande introuvable
dpkg : erreur de traitement de libmodplug0c2 (--configure) :
 le sous-processus post-installation script a retourné une erreur de sortie d'état 127
Paramétrage de libid3tag0 (0.15.1b-8) ...
/var/lib/dpkg/info/libid3tag0.postinst: line 5: ldconfig : commande introuvable
dpkg : erreur de traitement de libid3tag0 (--configure) :
 le sous-processus post-installation script a retourné une erreur de sortie d'état 127
dpkg : des problèmes de dépendances empêchent la configuration de libsdl1.2-dev :
 libsdl1.2-dev dépend de libaa1-dev ; cependant :
  Paquet libaa1-dev n'est pas encore configuré.
dpkg : erreur de traitement de libsdl1.2-dev (--configure) :
 problèmes de dépendances - laissé non configuré
dpkg : des problèmes de dépendances empêchent la configuration de libcairo2 :
 libcairo2 dépend de libglitz1 (>= 0.5.1+cvs20060213) ; cependant :
  Paquet libglitz1 n'est pas encore configuré.
dpkg : erreur de traitement de libcairo2 (--configure) :
 problèmes de dépendances - laissé non configuré
dpkg : des problèmes de dépendances empêchent la configuration de libgl1-mesa :
 libgl1-mesa dépend de libdrm2 ; cependant :
  Paquet libdrm2 n'est pas encore configuré.
dpkg : erreur de traitement de libgl1-mesa (--configure) :
 problèmes de dépendances - laissé non configuré
dpkg : des problèmes de dépendances empêchent la configuration de mesa-utils :
 mesa-utils dépend de libgl1-mesa | libgl1 ; cependant :
  Paquet libgl1-mesa n'est pas encore configuré.
  Paquet libgl1 n'est pas installé.
  Paquet libgl1-mesa qui fournit libgl1 n'est pas encore configuré.
dpkg : erreur de traitement de mesa-utils (--configure) :
 problèmes de dépendances - laissé non configuré
dpkg : des problèmes de dépendances empêchent la configuration de libglitz-glx1 :
 libglitz-glx1 dépend de libgl1-mesa | libgl1 ; cependant :
  Paquet libgl1-mesa n'est pas encore configuré.
  Paquet libgl1 n'est pas installé.
  Paquet libgl1-mesa qui fournit libgl1 n'est pas encore configuré.
 libglitz-glx1 dépend de libglitz1 (>= 0.5.1+cvs20060213) ; cependant :
  Paquet libglitz1 n'est pas encore configuré.
dpkg : erreur de traitement de libglitz-glx1 (--configure) :
 problèmes de dépendances - laissé non configuré
dpkg : des problèmes de dépendances empêchent la configuration de mplayer-686 :
 mplayer-686 dépend de mplayer ; cependant :
  Paquet mplayer n'est pas encore configuré.
dpkg : erreur de traitement de mplayer-686 (--configure) :
 problèmes de dépendances - laissé non configuré
dpkg : des problèmes de dépendances empêchent la configuration de libgl1-mesa-dev :
 libgl1-mesa-dev dépend de libgl1-mesa (= 6.5.1+cvs20060824) ; cependant :
  Paquet libgl1-mesa n'est pas encore configuré.
dpkg : erreur de traitement de libgl1-mesa-dev (--configure) :
 problèmes de dépendances - laissé non configuré
dpkg : des problèmes de dépendances empêchent la configuration de libwxgtk2.6-0 :
 libwxgtk2.6-0 dépend de libcairo2 (>= 1.0.2) ; cependant :
  Paquet libcairo2 n'est pas encore configuré.
 libwxgtk2.6-0 dépend de libgl1-mesa | libgl1 ; cependant :
  Paquet libgl1-mesa n'est pas encore configuré.
  Paquet libgl1 n'est pas installé.
  Paquet libgl1-mesa qui fournit libgl1 n'est pas encore configuré.
dpkg : erreur de traitement de libwxgtk2.6-0 (--configure) :
 problèmes de dépendances - laissé non configuré
dpkg : des problèmes de dépendances empêchent la configuration de libartsc0-dev :
 libartsc0-dev dépend de libartsc0 (= 1.5.2-0ubuntu1) ; cependant :
  Paquet libartsc0 n'est pas encore configuré.
dpkg : erreur de traitement de libartsc0-dev (--configure) :
 problèmes de dépendances - laissé non configuré
dpkg : des problèmes de dépendances empêchent la configuration de libglu1-mesa :
 libglu1-mesa dépend de libgl1-mesa | libgl1 ; cependant :
  Paquet libgl1-mesa n'est pas encore configuré.
  Paquet libgl1 n'est pas installé.
  Paquet libgl1-mesa qui fournit libgl1 n'est pas encore configuré.
dpkg : erreur de traitement de libglu1-mesa (--configure) :
 problèmes de dépendances - laissé non configuré
dpkg : des problèmes de dépendances empêchent la configuration de libpoppler1-glib :
 libpoppler1-glib dépend de libcairo2 (>= 1.0.2-2) ; cependant :
  Paquet libcairo2 n'est pas encore configuré.
 libpoppler1-glib dépend de libpoppler1 (>= 0.5.1) ; cependant :
  Paquet libpoppler1 n'est pas encore configuré.
 libpoppler1-glib dépend de libpoppler1 (= 0.5.3-0ubuntu1) ; cependant :
  Paquet libpoppler1 n'est pas encore configuré.
dpkg : erreur de traitement de libpoppler1-glib (--configure) :
 problèmes de dépendances - laissé non configuré
dpkg : des problèmes de dépendances empêchent la configuration de vlc-plugin-alsa :
 vlc-plugin-alsa dépend de vlc (= 0.8.5.final.1-0ubuntu2) ; cependant :
  Paquet vlc n'est pas encore configuré.
dpkg : erreur de traitement de vlc-plugin-alsa (--configure) :
 problèmes de dépendances - laissé non configuré
dpkg : des problèmes de dépendances empêchent la configuration de xserver-xgl :
 xserver-xgl dépend de libgl1-mesa | libgl1 ; cependant :
  Paquet libgl1-mesa n'est pas encore configuré.
  Paquet libgl1 n'est pas installé.
  Paquet libgl1-mesa qui fournit libgl1 n'est pas encore configuré.
 xserver-xgl dépend de libglitz-glx1 ; cependant :
  Paquet libglitz-glx1 n'est pas encore configuré.
 xserver-xgl dépend de libglitz1 (>= 0.5.1+cvs20060213) ; cependant :
  Paquet libglitz1 n'est pas encore configuré.
dpkg : erreur de traitement de xserver-xgl (--configure) :
 problèmes de dépendances - laissé non configuré
dpkg : des problèmes de dépendances empêchent la configuration de compiz-core :
 compiz-core dépend de libcairo2 ; cependant :
  Paquet libcairo2 n'est pas encore configuré.
 compiz-core dépend de libgl1-mesa ; cependant :
  Paquet libgl1-mesa n'est pas encore configuré.
dpkg : erreur de traitement de compiz-core (--configure) :
 problèmes de dépendances - laissé non configuré
dpkg : des problèmes de dépendances empêchent la configuration de libvcdinfo0 :
 libvcdinfo0 dépend de libiso9660-4 ; cependant :
  Paquet libiso9660-4 n'est pas encore configuré.
dpkg : erreur de traitement de libvcdinfo0 (--configure) :
 problèmes de dépendances - laissé non configuré
dpkg : des problèmes de dépendances empêchent la configuration de libglu1-mesa-dev :
 libglu1-mesa-dev dépend de libglu1-mesa (= 6.5.1+cvs20060824) ; cependant :
  Paquet libglu1-mesa n'est pas encore configuré.
 libglu1-mesa-dev dépend de libgl1-mesa-dev | libgl-dev ; cependant :
  Paquet libgl1-mesa-dev n'est pas encore configuré.
  Paquet libgl-dev n'est pas installé.
  Paquet libgl1-mesa-dev qui fournit libgl-dev n'est pas encore configuré.
dpkg : erreur de traitement de libglu1-mesa-dev (--configure) :
 problèmes de dépendances - laissé non configuré
dpkg : trop d'erreurs, arrêt
Des erreurs ont été rencontrées pendant l'exécution :
 libdvdread3
 libssl0.9.7
 liba52-0.7.4
 libungif4g
 libdrm2
 libgsm1
 libsdl-image1.2
 libmpcdec3
 gstreamer0.10-plugins-ugly
 gftp-text
 wifi-radar
 libxosd2
 libpoppler1
 libdvdcss2
 mencoder
 poppler-utils
 tcltls
 nasm
 libdc1394-13
 libaa1-dev
 libartsc0
 libtar
 libdvdnav4
 vlc
 mplayer
 libmpeg2-4
 libiso9660-4
 libglitz1
 libdvbpsi4
 libgii0
 libmad0
 libggi2
 gftp
 libmodplug0c2
 libid3tag0
 libsdl1.2-dev
 libcairo2
 libgl1-mesa
 mesa-utils
 libglitz-glx1
 mplayer-686
 libgl1-mesa-dev
 libwxgtk2.6-0
 libartsc0-dev
 libglu1-mesa
 libpoppler1-glib
 vlc-plugin-alsa
 xserver-xgl
 compiz-core
 libvcdinfo0
 libglu1-mesa-dev
L'exécution a été arrêtée car il y avait trop d'erreurs.

```

---

### Post by vavoem on 2006-08-25
Try apt-get install -f <package name> 
it might fix it

---

