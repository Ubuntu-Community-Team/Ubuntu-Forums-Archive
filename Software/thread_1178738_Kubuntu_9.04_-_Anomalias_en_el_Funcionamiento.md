---
title: "Kubuntu 9.04 - Anomalias en el Funcionamiento"
date: 2009-06-04
forum: Software
---

### Post by NickCis on 2009-06-04
Hola, tengo un (varios) problema con Kubuntu 9.04. Instale hace mas o menos un mes y todo andaba barbaro. Pero, hoy a la noche prendo la pc, y el primer problema es que no entra en el entorno grafico, se queda como si no tuviese el login manager.
Despues de tener que iniciar, y usar el comando startx. Abro el amarok, y este me dice que hay problemas con la placa de sonido entonces no se usara, yo pense WTF?!,,, bue me quede sin sonido.

Lo ultimo que pudo aver causado el problema fue actualizar los programas, pero despues de actualizarlos pude reiniciar sin ningun problema, asi que no se.

Adjunto la salida del comando lspci:
```
newpc@newpc-desktop:~$ lspci
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev f3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev f2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev f3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:06.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
05:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 LE] (rev a1)
newpc@newpc-desktop:~$

```

Mi /etc/apt/sources.list (por si algun programa actualizado causo el problema):

```
newpc@newpc-desktop:~$ cat /etc/apt/sources.list                                
# deb cdrom:[Kubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted                                                               
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to       
# newer versions of the distribution.                                           

deb http://ar.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://ar.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.                                                
deb http://ar.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://ar.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any  
## review or updates from the Ubuntu security team.                        
deb http://ar.archive.ubuntu.com/ubuntu/ jaunty universe                   
deb-src http://ar.archive.ubuntu.com/ubuntu/ jaunty universe               
deb http://ar.archive.ubuntu.com/ubuntu/ jaunty-updates universe           
deb-src http://ar.archive.ubuntu.com/ubuntu/ jaunty-updates universe       

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in      
## multiverse WILL NOT receive any review or updates from the Ubuntu        
## security team.                                                           
deb http://ar.archive.ubuntu.com/ubuntu/ jaunty multiverse                  
deb-src http://ar.archive.ubuntu.com/ubuntu/ jaunty multiverse              
deb http://ar.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://ar.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ar.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://ar.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb http://ppa.launchpad.net/monoxide0184/ppa/ubuntu intrepid main
deb-src http://ppa.launchpad.net/monoxide0184/ppa/ubuntu intrepid main
deb http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu jaunty main
deb http://ppa.launchpad.net/kow/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/kow/ppa/ubuntu jaunty main
deb http://wine.budgetdedicated.com/apt jaunty main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope"

newpc@newpc-desktop:~$

```

Alguna ayuda?.
Saludos.

Edit: estoy usando los drivers privativos de Nvidia (los 180), pero no tengo ningun problema con el video, puedo usar los efectos del kwin sin problema...

Si ejecuto aplay en consola:
```
newpc@newpc-desktop:~$ aplay
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No existe el fichero ó directorio
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No existe el fichero ó directorio
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No existe el fichero ó directorio
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No existe el fichero ó directorio
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM default
aplay: main:590: error al abrir audio: No existe el fichero ó directorio
newpc@newpc-desktop:~$
```

---

### Post by staar on 2009-06-04
mmm tenés el ppa de kubuntu ahí, se te actualizó a KDE 4.2.4? no hubo errores en la actualización? que paquetes se actualizaron? ```
sudo cat /var/log/dpkg.log | grep \ installed | awk {'print $5'} | xargs 
```

saludos

---

### Post by NickCis on 2009-06-04
```
newpc@newpc-desktop:~$ sudo cat /var/log/dpkg.log | grep \ installed | awk {'print $5'} | xargs
[sudo] password for newpc:
man-db shared-mime-info kdelibs5-data kdebase-runtime-data-common kdebase-runtime-data kde-icons-oxygen libakonadiprivate1 kdepimlibs-data kdebase-workspace-data ksysguardd cron libkonq5-templates kdeplasma-addons-data kdelibs-bin kdelibs5 libplasma3 kdebase-runtime-bin-kde4 kdebase-runtime kdebase-workspace-libs4+5 libkdecorations4 libkwineffects1 kde-window-manager kdepimlibs5 kdebase-workspace-bin klipper ksysguard systemsettings kdebase-workspace kdm python-kde4 python-plasma libkdepim4 ktimetracker kdepim-kresources libkleo4 libkpgp4 libksieve4 libmimelib4 kmail kaddressbook libkholidays4 korganizer kontact knotes kdepim-wizards akregator ark libkonq5 dolphin dragonplayer kate kde-printer-applet kdebase-bin kdebase-plasma libkcddb4 kdemultimedia-kio-plugins kdepasswd kdepim-strigi-plugins libkexiv2-7 kdeplasma-addons kfind khelpcenter4 kmag kmix kmousetool konqueror-nsplugins konsole kopete krdc krfb ksystemlog kuser kwalletmanager system-config-printer-kde libkipi6 gwenview kamera kde-zeroconf kdegraphics-strigi-plugins ksnapshot libokularcore1 okular okular-extra-backends kdebase-data konqueror libc6 vlc-plugin-esd vlc man-db man-db libvlccore0 libvlc2 libx264-67 vlc-nox vlc mozilla-plugin-vlc libc6 man-db foomatic-db-engine libsqlite3-0 mysql-common libmysqlclient15off vlc-data evolution-documentation-en libc6 shared-mime-info man-db kdepimlibs-data ksysguardd kdebase-runtime-data-common cups-common libcups2 kdebase-workspace-data kde-icons-oxygen kdebase-runtime-data libkonq5-templates ufw kdelibs5-data libcupsimage2 cups cups-client cups-bsd kdelibs-bin kdelibs5 libplasma3 kdepimlibs5 kdebase-runtime-bin-kde4 kdebase-runtime libkholidays4 libkleo4 libkpgp4 kdebase-workspace-libs4+5 ark ksysguard libkdecorations4 libkdepim4 kdm akregator ktimetracker kdebase-workspace-bin libksieve4 klipper libmimelib4 libkwineffects1 systemsettings kde-window-manager kdebase-workspace python-kde4 libkonq5 kdepim-kresources kaddressbook kmail korganizer python-plasma kontact knotes kdepim-wizards libc6 man-db shared-mime-info dolphin dragonplayer kate kde-printer-applet kdebase-plasma libkcddb4 kdemultimedia-kio-plugins kdepasswd kdepim-strigi-plugins libkexiv2-7 kdeplasma-addons-data kdeplasma-addons kfind khelpcenter4 kmag kmix kmousetool konqueror-nsplugins konsole kopete krdc krfb ksystemlog kuser kwalletmanager system-config-printer-kde cupsys libkipi6 gwenview kamera kde-zeroconf kdegraphics-strigi-plugins ksnapshot libokularcore1 okular okular-extra-backends kdebase-data kdebase-bin konqueror libc6 cupsys cupsys timidity-interfaces-extra tk8.4 tcl8.4 timidity man-db libc6 cupsys
newpc@newpc-desktop:~$

```

MMM, si puede ser que se actualizo, el unico problema que tuve, fue cuando estaba actualizando (y yo seguia usando la Pc), se tildo completamente, pero no podia ni cambiar de tty (eso de control alt F1 o f2). Reinicie, hice eso de dkpg -reconfigure -a (como te dice que hagas) y todo continuo andando perfectamente. Ahi no me paso esto, cuando prendi la pc.

Algun log que se pueda consultar sobre por que no entra al gestor de ventanas (tengo que cambiar de TTy, conectar y ejecutar startx por mi cuenta...)?.

Saludos y muchas gracias.

---

### Post by juancarlospaco on 2009-06-04
**[sudo apt-get install ubuntu-desktop]("apt:/ubuntu-desktop")**

---

### Post by staar on 2009-06-04
> **juancarlospaco said:**
> **[sudo apt-get install ubuntu-desktop]("apt:/ubuntu-desktop")**

será [sudo apt-get install kubuntu-desktop]("apt:/kubuntu-desktop"), es Kubuntu, por las dudas, previamente comentá la línea del ppa de kubuntu en el sources.list, para que se instale la versión de los repos oficiales (después, si querés, actualizá de nuevo con el ppa)...

ese tildada y el reinicio forzado deben haber roto algo, un tip para la proxima vez, una forma de reiniciar al colgarse el sistema (mejor que directamente del botón de reset) es apretar Alt + ImprPant (la tecla al lado de F12 y Bloq Despl) y luego, manteniendo el Alt, ir oprimiendo, de a una, las teclas R, E, I, S, U, y B (REISUB), es una característica del kernel que permite un reinicio forzado menos dañino...

saludos

---

### Post by NickCis on 2009-06-05
Saque la linea del /etc/apt/sources.list, hice un sudo apt-get update y dsp reinstale kubuntu-desktop (sudo apt-get install --reinstall kubuntu-desktop). Y se solucionaron los problemas, lo unico que me pasa es que ahora abre el menu del kdm y me pide usuario y contraseña. Como hago para que entre al un usuario directamente?.

Hoy mas a la noche actualizo, y veo que pasa, ahora no tengo tiempo...

Saludos y muchas gracias.

---

### Post by staar on 2009-06-05
para el inicio automático, en Preferencias del sistema (como root, con sudo systemsettings) > Avanzado > Gestor de acceso > Comodidad...

saludos

---

### Post by guillermolisi on 2009-06-05
> **NickCis said:**
> Saque la linea del /etc/apt/sources.list, hice un sudo apt-get update y dsp reinstale kubuntu-desktop (sudo apt-get install --reinstall kubuntu-desktop). Y se solucionaron los problemas, lo unico que me pasa es que ahora abre el menu del kdm y me pide usuario y contraseña. Como hago para que entre al un usuario directamente?.

Hoy mas a la noche actualizo, y veo que pasa, ahora no tengo tiempo...

Saludos y muchas gracias.
Previendo algun mensaje de error que pudiera aparecer por un bug en el paquete de KDE 4.2.2, 4.2.3 y 4.2.4, documentado en Launchpad, donde el modulo kdebase-runtime no se actualiza porque intenta actualizar kdesudo que esta incluido en el paqeute de actualizacion, mi recomendacion para terminar el proceso (y siempre que resulte el error) es:
```
sudo apt-get update
sudo dpkg -i --force-overwrite /var/cache/apt/archives/kdebase-runtime_4%3a4.2.4-0ubuntu1~jaunty1~ppa2_i386.deb
```

Lo probe en una de las maquinas que tengo, luego de haber intentado actualizar desde 4.2.1 a 4.2.2, 4.2.3 y 4.2.4, y funciono perfecto.

---

### Post by NickCis on 2009-06-06
Usando este comando:

sudo dpkg -i --force-overwrite /var/cache/apt/archives/kdebase-runtime_4%3a4.2.4-0ubuntu1~jaunty1~ppa2_i386.deb



Me dice que el paquete no existe.

Intente actualizar (agregando el ppa de kubuntu de vuelta), pero parece que nunca desactualizo, que siempre estoy en la misma vercion nueva :S, no entiendo... Como puedo saber con que vercion de Kde estoy?.



Bueno ahora al problema, parece que cuando habre kate con sudo, "sudo kate" desde konsole, me tira este error:

"Could not start ksmerver. Check your installation." (adjunto foto). Al darle Ok, muere Kde, llevandome al KDM.
 Lo mas raro, es que si no le doy OK, puedo seguir usando la Pc sin ningun error visible :S...
Supuse que era un problema de kde, por lo que hice un reinstall de kubuntu-desktop, pero sigo con el mismo problema.



Alguna idea de como solucionar esto?.



Saludos.

P.D.: no sabia que actualizar KDE, me iba a traer tantos problemas :S...

Edit: ahora me di cuenta que abriendo casi cualquier programa con sudo me pasa este extraño error, probe con dolphin y un par mas y siempre el mismo error, alguna idea?.

---

### Post by staar on 2009-06-06
ese error es un bug, que aparece cada tanto entre versiones de KDE4, y en algunas instalaciones si, y en otras no, en mi arch con kdemod me pasa, una solución es usar dbus-launch, por ejemplo ```
sudo dbus-launch kate
```

y el comando que te pasó guillermo tiene un error de tipeo, además de que la versión que hay actualmente en el ppa es otra, sería así ```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/kdebase-runtime_4.2.85-0ubuntu1~jaunty1~ppa8_i386.deb
```

saludos

---

### Post by NickCis on 2009-06-06
Ahi me funciono el comando: sudo dpkg -i --force-overwrite /var/cache/apt/archives/kdebase-runtime_4%3a4.2.4-0ubuntu1~jaunty1~ppa2_i386.deb
Pero igual, sigue con ese raro problema, por ahora me anda el sonido y todo eso, no me puedo quejar. (la vercion de los repos es la 4.2.4 [https://launchpad.net/~kubuntu-ppa/+archive/ppa?field.name_filter=&field.status_filter=published&field.series_filter=jaunty](https://launchpad.net/~kubuntu-ppa/+archive/ppa?field.name_filter=&field.status_filter=published&field.series_filter=jaunty) )

Y si, efectivamente, se jodio a actualizar a kde 4.2.4 supongo que en el futuro lo arreglaran :P.
Por el momento tendre que vivir con un xmessage (esa ventanita de error, qe mientras no le de ok anda todo bien xD).

Saludos y gracias :P

---

### Post by guillermolisi on 2009-06-06
> **staar said:**
> ese error es un bug, que aparece cada tanto entre versiones de KDE4, y en algunas instalaciones si, y en otras no, en mi arch con kdemod me pasa, una solución es usar dbus-launch, por ejemplo ```
sudo dbus-launch kate
```y el comando que te pasó guillermo tiene un error de tipeo, además de que la versión que hay actualmente en el ppa es otra, sería así ```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/kdebase-runtime_4.2.85-0ubuntu1~jaunty1~ppa8_i386.deb
```saludos
No no ... lo revise varias veces, tanto que lo escribi en papel para volverlo a revisar y, como dije, lo probe antes de informarlo. De hecho tambien le funciono a varios de esa forma.

---

### Post by Hei Ku on 2009-06-06
se puede hacer lo mismo con apt-get, usando el nombre del paquete.

sudo apt-get --force-overwrite install kdebase-runtime

---

### Post by NickCis on 2009-06-06
> **Hei Ku said:**
> se puede hacer lo mismo con apt-get, usando el nombre del paquete.

sudo apt-get --force-overwrite install kdebase-runtime

```
newpc@newpc-desktop:~$ sudo apt-get --force-overwrite install kdebase-runtime
E: No se entiende la opción de línea de órdenes --force-overwrite
newpc@newpc-desktop:~$
```

Puede ser algo que este mal escrito?

Saludos.

---

### Post by staar on 2009-06-06
--force-overwrite es opción de dpkg al parecer, encontré esta ```
sudo apt-get install kdebase-runtime -o DPkg::options::="--force-overwrite"
``` funciona? que raro, tanto lio para algo tan simple como sobreescribir archivos de otro paquete...

saludos

---

### Post by NickCis on 2009-06-06
Nono, no funciona, no instala nada.
Baje el deb del ppa a mano y lo instale con el dpkg y la opcion "--force-overwrite", ya lo solucione.

Muchas gracias!!

---

