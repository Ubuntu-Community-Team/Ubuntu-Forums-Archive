---
title: "Como hacer que usuarios no pueden reiniciar?"
date: 2008-08-27
forum: Software
---

### Post by Thalskarth on 2008-08-27
Buenas...

Vuelvo a molestrar con otro tema sobre los privilegios de usuario.
No se si esto es posible siquiera, pero me gustaria configurar una cuenta de usuario y quitarle privilegios para que no puede reiniciar ni apagar el equipo.

El tema es con la cuenta de mi hermano, yo uso mi propia cuenta y suelo a veces dejar algun arhicvo abierto, bloqueo mi sesion y le dejo la PC... el suele loguearse con la cuenta de el, y luego--- no se porque tiene la mania de siempre reiniciarla o apagarla... perdiendo yo todo lo que estuviese abierto en mi cuenta, ya que ubuntu se reinicia sin siquiera avisar que mi cuenta esta aún abierta.

Ya lo he ****** a ******** y le he dicho que deje de hacerlo, pero sigue igual...

Entonces, me gustaria saber si puedo quitarle los permisos a su usuario asi no puede reiniciar la PC directamente... o sino al menos algo para que si quiere reiniciarla, avise de mi cuenta y no se... pida mi contraseña o algo como similar  como para habilitar el reinicio... 
Que no se pase por alto mi cuenta... digamos

es algo posible eso???

Desde ya, como siemrpe, muchas gracias

---

### Post by rober-mpp on 2008-08-28
Probablemente se puedan setear permisos por grupo al ejecutable. El problema es que no tengo idea si la UI de gnome usa el comando shutdown.
Si lo usa, tendrias que averiguar que grupo tiene seteado, agregarte a ese grupo y sacarlo a tu hno, y haciendo chmod 770 <path>shutdown creo que deberia andar

Saludos

---

### Post by Thalskarth on 2008-08-29
> **rober-mpp said:**
> Probablemente se puedan setear permisos por grupo al ejecutable. El problema es que no tengo idea si la UI de gnome usa el comando shutdown.
Si lo usa, tendrias que averiguar que grupo tiene seteado, agregarte a ese grupo y sacarlo a tu hno, y haciendo chmod 770 <path>shutdown creo que deberia andar

Saludos

Hola, gracias por el dato.... pero si no es molestia, podrías decirme mas o menos como hacerlo? no soy muy ducho en linux todavia (estoy en el largo camino del aprendizaje :P)... y no se como se hace eso de los grupos...

Gracias

---

### Post by Hei Ku on 2008-08-29
hay 2 comandos que se usan para apagar la maquina: /sbin/poweroff y /sbin/reboot

KDE tiene un control de accesos que entre otras permite configurar si todos los usuarios pueden apagar la maquina o no. Gnome debería tener algo similar, quizas a traves del modo kiosk. De hecho, seguro que lo tiene porque Gnome fue el que empezo la especificacion de kiosk.

Pero quizas despues quitaron la opcion. :p

---

### Post by rober-mpp on 2008-08-29
Esta es una buena guia para aprender de los permisos en linux:

[http://wiki.linuxquestions.org/wiki/Chmod](http://wiki.linuxquestions.org/wiki/Chmod)

Lo que tenes que hacer son dos cosas:

1) sacar al otro usuario del grupo root (si es que lo esta). esto lo podes hacer con la utilidad grafica del gnome o kde. Probablemente tengas que crear algun otro grupo para meter a ese usuario.
2) Fijarte que los permisos del ejecutable para apagar la maquina ( /sbin/poweroff, /sbin/reboot, o shutdown ) no permitan a usuarios fuera del grupo ejecutar el archivo. 

En cuanto a lo del kiosk, no tengo ni la mas palida idea :( , lo que si se es que yo la maquina la apago por consola con:

shutdown -h now

Suerte!!

---

### Post by faktorqm on 2008-08-29
sistema -> adminsitracion -> autorizaciones. en la pantalla de la izquierda buscas la seccion que dice "power management" y ahi anidado esta la opcion "shut down the system". Ahi tenes para jugar bastante, pero tene cuidado, no te saques permisos a vos mismo con los permisos implicitos, por que sino vas a ir a apagar y no vas a poder y vas a tener que apagar como root. Salu2!!

---

### Post by Thalskarth on 2008-08-29
Gracias por la ayuda, pero no logro hacerlo...

Probando con el sistema que me dijo rober-mmp, por consola si pongo reboot pide el password sino no funciona... pero si hace click en sistema/salir... reiniciar el sistema se reinicia sin dramas.


Y con el de faktorqm, realmente nunca pude lograr diferencia de nada... o sea, configure para que pida autoricacion, lepuse todo no, le puse bloquear usuario... pero nunca cambio nada, desde el boton de salir... reiniciar, la maquina seimpre se reinicio sin mas, ni siquiera pedia autorizacion ni nada...
estoy fallando en algo?

---

### Post by rober-mpp on 2008-08-29
No es mi intencion ofender, y si, es una pregunta tonta, pero la tengo que hacer.
Una vez que haces los cambios con tu usario/root, te cambias al otro usuario para probarlos ? o lo seguis probando desde el tuyo ?

Saludos

---

### Post by Thalskarth on 2008-08-29
> **rober-mpp said:**
> No es mi intencion ofender, y si, es una pregunta tonta, pero la tengo que hacer.
Una vez que haces los cambios con tu usario/root, te cambias al otro usuario para probarlos ? o lo seguis probando desde el tuyo ?

Saludos

No ofende, esta bien que lo preguntes...:)

Lo hice desde el otro usuario. Como decia, si se usa el comando reboot desde consola, si pide el pass o directamente dice que no esta permitido y no deja reiniciar. Pero haciendo click en el boton salir... /reiniciar sigue funcionando sin dramas. no se porque por un medio si y por otro no. Y mi hermano, usa la pc sin saber casi nada, asi que se maneja todo por el botoncito de salir, creo que nunca abrio una consola :P

---

### Post by rober-mpp on 2008-08-29
Che y no se puede sacar el boton de apagar del menu ? como una solucion a corto plazo...
Disculpen que no pruebe nada pero estoy en el laburo con win2.

Saludos

---

### Post by Thalskarth on 2008-08-29
> **rober-mpp said:**
> Che y no se puede sacar el boton de apagar del menu ? como una solucion a corto plazo...
Disculpen que no pruebe nada pero estoy en el laburo con win2.

Saludos
no por favor, al contrario... gracias por ayudarme tanto...

te comento, probé con esa solucion. pero el boton esta en el panel (ya lo quite), figura en el menu sistema (no se como quitarlo)... y si apretas ctrl+alt+del sale el cartel mismo que cuando se clickea en el boton...
Aparte sacando el boton, tambien desaparece la opcion para cerrar sesión...

pero bueno, voy a seguir probando y mientras voy a usar esta solucion y empezaré a enseñarle "amablemente" a mi hermano

---

### Post by gmunioz on 2008-08-29
Hola tha...:
Pudes probar con:

Para deshabilitar el reinicio y apagado en Linux

1) Edita el archivo /etc/X11/gdm/gdm.conf
sudo gedit /etc/X11/gdm/gdm.con
Añade la línea
SystemMenu = false.

2) Deshabilita el botón de apagado
sudo chmod 000 /etc/acpi/powerbtn.sh

3) Edita el archivo /etc/inittab
sudo gedit /etc/inittab
Cambia la línea referida a CTRL-ALT-DEL a
#Trap CTRL-ALT-DELETE
ca::ctrlaltdel:/bin/echo “ctrl-alt-supr desactivado”

4)Permite únicamente al administrador el acceso a halt
sudo  chgrp admin /sbin/halt /sbin/shutdown
sudo chmod 550 /sbin/halt /sbin/shutdown

5) Para apagar el sistema deberás utilizar la orden
sudo halt

Saludos
Gabriel.
**Solo doy soporte para Ubuntu** - *6666* - **Más malo que el diablo**

---

### Post by Thalskarth on 2008-08-30
> **gmunioz said:**
> Hola tha...:
Pudes probar con:

Para deshabilitar el reinicio y apagado en Linux

1) Edita el archivo /etc/X11/gdm/gdm.conf
sudo gedit /etc/X11/gdm/gdm.con
Añade la línea
SystemMenu = false.
perdona, pero no existe la carpeta /etc/X11/gdm y tampoco el archivo gdm.conf...

Los creo???


PD: perdon que sea tan complicado :P

---

### Post by WanderingKnight on 2008-08-30
> perdona, pero no existe la carpeta /etc/X11/gdm y tampoco el archivo gdm.conf...

Ehm, estás seguro? Usás GNOME? Yo uso KDE pero tengo un backup de /etc/* de cuando tenía GNOME y la carpeta /etc/X11/gdm está ahí... Si tenés KDE la carpeta es /etc/kde3/kdm/.

Cualquier cosa tirá

```
sudo updatedb
locate gdm
```

y posteá lo que sale.

---

### Post by Thalskarth on 2008-08-30
> **WanderingKnight said:**
> Ehm, estás seguro? Usás GNOME? Yo uso KDE pero tengo un backup de /etc/* de cuando tenía GNOME y la carpeta /etc/X11/gdm está ahí... Si tenés KDE la carpeta es /etc/kde3/kdm/.

Cualquier cosa tirá

```
sudo updatedb
locate gdm
```

y posteá lo que sale.

Al hacer eso, me devolvio esto:
```
/etc/gdm
/etc/gdm/Init
/etc/gdm/PostLogin
/etc/gdm/PostSession
/etc/gdm/PreSession
/etc/gdm/XKeepsCrashing
/etc/gdm/Xsession
/etc/gdm/failsafeBlacklist
/etc/gdm/failsafeDexconf
/etc/gdm/failsafeXServer
/etc/gdm/failsafeXinit
/etc/gdm/gdm.conf
/etc/gdm/gdm.conf-custom
/etc/gdm/gdmprefetchlist
/etc/gdm/locale.conf
/etc/gdm/modules
/etc/gdm/Init/Default
/etc/gdm/PostLogin/Default
/etc/gdm/PostLogin/Default.sample
/etc/gdm/PostSession/Default
/etc/gdm/PreSession/Default
/etc/gdm/modules/AccessDwellMouseEvents
/etc/gdm/modules/AccessKeyMouseEvents
/etc/gdm/modules/factory-AccessDwellMouseEvents
/etc/gdm/modules/factory-AccessKeyMouseEvents
/etc/init.d/gdm
/etc/pam.d/gdm
/etc/pam.d/gdm-autologin
/etc/rc0.d/K01gdm
/etc/rc1.d/K01gdm
/etc/rc2.d/S30gdm
/etc/rc3.d/S30gdm
/etc/rc4.d/S30gdm
/etc/rc5.d/S30gdm
/etc/rc6.d/K01gdm
/home/thalskarth/.icons/ALLGREY/scalable/apps/gdm-setup.svg
/home/thalskarth/.icons/ALLGREY/scalable/apps/gdm-xnest.svg
/home/thalskarth/.icons/ALLGREY/scalable/apps/gdm.svg
/home/thalskarth/.icons/Feel-of-Japan/128x128/apps/gdm-setup.png
/home/thalskarth/.icons/Feel-of-Japan/128x128/apps/gdm-xnest.png
/home/thalskarth/.icons/Feel-of-Japan/128x128/apps/gdm.png
/home/thalskarth/.icons/Feel-of-Japan/128x128/apps/gdmsetup.png
/home/thalskarth/.icons/MacUltimate_Leopard/scalable/apps/gdm-setup.png
/home/thalskarth/.icons/MacUltimate_Leopard/scalable/apps/gdm.png
/home/thalskarth/.icons/MacUltimate_Leopard/scalable/apps/gdmsetup.png
/home/thalskarth/.icons/buuf1.04/128x128/apps/gdm-setup.png
/home/thalskarth/.icons/buuf1.04/128x128/apps/gdm-xnest.png
/home/thalskarth/.icons/buuf1.04/128x128/apps/gdm.png
/home/thalskarth/.icons/buuf1.04/128x128/apps/gdmsetup.png
/usr/bin/gdm-dmx-reconnect-proxy
/usr/bin/gdm-signal
/usr/bin/gdmXnest
/usr/bin/gdmXnestchooser
/usr/bin/gdmdynamic
/usr/bin/gdmflexiserver
/usr/bin/gdmphotosetup
/usr/bin/gdmthemetester
/usr/lib/gdm
/usr/lib/gdmplay
/usr/lib/deskbar-applet/modules-2.20-compatible/gdmactions.py
/usr/lib/deskbar-applet/modules-2.20-compatible/gdmactions.pyc
/usr/lib/gdm/gdm-ssh-session
/usr/lib/gdm/gdmaskpass
/usr/lib/gdm/gdmchooser
/usr/lib/gdm/gdmgreeter
/usr/lib/gdm/gdmlogin
/usr/lib/gdm/gdmopen
/usr/lib/gdm/gdmprefetch
/usr/lib/gdm/gdmtranslate
/usr/lib/python2.4/site-packages/deskbar/handlers/gdmclient
/usr/lib/python2.4/site-packages/deskbar/handlers/gdmclient/_gdmclient.so
/usr/lib/python2.5/site-packages/ubuntu_gdm_themes-0.29.egg-info
/usr/lib/python2.5/site-packages/deskbar/handlers/gdmclient
/usr/lib/python2.5/site-packages/deskbar/handlers/gdmclient/__init__.py
/usr/lib/python2.5/site-packages/deskbar/handlers/gdmclient/__init__.pyc
/usr/lib/python2.5/site-packages/deskbar/handlers/gdmclient/_gdmclient.so
/usr/sbin/gdm
/usr/sbin/gdmsetup
/usr/share/gdm
/usr/share/app-install/desktop/gdmap.desktop
/usr/share/app-install/icons/gdmap_icon.png
/usr/share/applications/gdmflexiserver-xnest.desktop
/usr/share/applications/gdmflexiserver.desktop
/usr/share/applications/gdmphotosetup.desktop
/usr/share/applications/gdmsetup.desktop
/usr/share/doc/gdm
/usr/share/doc/ubuntu-gdm-themes
/usr/share/doc/gdm/AUTHORS.gz
/usr/share/doc/gdm/NEWS.gz
/usr/share/doc/gdm/README.Debian
/usr/share/doc/gdm/README.gz
/usr/share/doc/gdm/README.install.gz
/usr/share/doc/gdm/TODO
/usr/share/doc/gdm/changelog.Debian.gz
/usr/share/doc/gdm/changelog.gz
/usr/share/doc/gdm/copyright
/usr/share/doc/ubuntu-gdm-themes/AUTHORS
/usr/share/doc/ubuntu-gdm-themes/changelog.gz
/usr/share/doc/ubuntu-gdm-themes/copyright
/usr/share/gdm/BuiltInSessions
/usr/share/gdm/gdmXnestWrapper
/usr/share/gdm/gdmchooser.glade
/usr/share/gdm/gdmphotosetup.glade
/usr/share/gdm/gdmsetup.glade
/usr/share/gdm/themes
/usr/share/gdm/BuiltInSessions/default.desktop
/usr/share/gdm/themes/Doe-GDM
/usr/share/gdm/themes/Human
/usr/share/gdm/themes/HumanCircle
/usr/share/gdm/themes/HumanList
/usr/share/gdm/themes/circles
/usr/share/gdm/themes/happygnome
/usr/share/gdm/themes/happygnome-list
/usr/share/gdm/themes/Doe-GDM/AvioGDM.xml
/usr/share/gdm/themes/Doe-GDM/AvioGDM.xml~
/usr/share/gdm/themes/Doe-GDM/GdmGreeterTheme.desktop
/usr/share/gdm/themes/Doe-GDM/background.jpg
/usr/share/gdm/themes/Doe-GDM/chooser-active.png
/usr/share/gdm/themes/Doe-GDM/chooser-prelight.png
/usr/share/gdm/themes/Doe-GDM/chooser.png
/usr/share/gdm/themes/Doe-GDM/disconnect-active.png
/usr/share/gdm/themes/Doe-GDM/disconnect-prelight.png
/usr/share/gdm/themes/Doe-GDM/disconnect.png
/usr/share/gdm/themes/Doe-GDM/halt-active.png
/usr/share/gdm/themes/Doe-GDM/halt-prelight.png
/usr/share/gdm/themes/Doe-GDM/halt.png
/usr/share/gdm/themes/Doe-GDM/innerbackground.png
/usr/share/gdm/themes/Doe-GDM/language-active.png
/usr/share/gdm/themes/Doe-GDM/language-prelight.png
/usr/share/gdm/themes/Doe-GDM/language.png
/usr/share/gdm/themes/Doe-GDM/line.png
/usr/share/gdm/themes/Doe-GDM/quit-active.png
/usr/share/gdm/themes/Doe-GDM/quit-prelight.png
/usr/share/gdm/themes/Doe-GDM/quit.png
/usr/share/gdm/themes/Doe-GDM/reboot-active.png
/usr/share/gdm/themes/Doe-GDM/reboot-prelight.png
/usr/share/gdm/themes/Doe-GDM/reboot.png
/usr/share/gdm/themes/Doe-GDM/screenshot.png
/usr/share/gdm/themes/Doe-GDM/selection-active.png
/usr/share/gdm/themes/Doe-GDM/selection-prelight.png
/usr/share/gdm/themes/Doe-GDM/selection.png
/usr/share/gdm/themes/Doe-GDM/session-active.png
/usr/share/gdm/themes/Doe-GDM/session-prelight.png
/usr/share/gdm/themes/Doe-GDM/session.png
/usr/share/gdm/themes/Doe-GDM/suspend-active.png
/usr/share/gdm/themes/Doe-GDM/suspend-prelight.png
/usr/share/gdm/themes/Doe-GDM/suspend.png
/usr/share/gdm/themes/Doe-GDM/system-active.png
/usr/share/gdm/themes/Doe-GDM/system-prelight.png
/usr/share/gdm/themes/Doe-GDM/system.png
/usr/share/gdm/themes/Human/GdmGreeterTheme.desktop
/usr/share/gdm/themes/Human/Human.xml
/usr/share/gdm/themes/Human/background.png
/usr/share/gdm/themes/Human/bottom_bar.svg
/usr/share/gdm/themes/Human/boundingbox.svg
/usr/share/gdm/themes/Human/gtk-2.0
/usr/share/gdm/themes/Human/icon-language-active.png
/usr/share/gdm/themes/Human/icon-language-prelight.png
/usr/share/gdm/themes/Human/icon-language.png
/usr/share/gdm/themes/Human/icon-reboot-active.png
/usr/share/gdm/themes/Human/icon-reboot-prelight.png
/usr/share/gdm/themes/Human/icon-reboot.png
/usr/share/gdm/themes/Human/icon-session-active.png
/usr/share/gdm/themes/Human/icon-session-prelight.png
/usr/share/gdm/themes/Human/icon-session.png
/usr/share/gdm/themes/Human/icon-shutdown-active.png
/usr/share/gdm/themes/Human/icon-shutdown-prelight.png
/usr/share/gdm/themes/Human/icon-shutdown.png
/usr/share/gdm/themes/Human/screenshot.png
/usr/share/gdm/themes/Human/ubuntu.png
/usr/share/gdm/themes/Human/userentry.svg
/usr/share/gdm/themes/Human/gtk-2.0/gtkrc
/usr/share/gdm/themes/HumanCircle/GdmGreeterTheme.desktop
/usr/share/gdm/themes/HumanCircle/HumanCircle.xml
/usr/share/gdm/themes/HumanCircle/circle.png
/usr/share/gdm/themes/HumanCircle/icon-language-active.png
/usr/share/gdm/themes/HumanCircle/icon-language-prelight.png
/usr/share/gdm/themes/HumanCircle/icon-language.png
/usr/share/gdm/themes/HumanCircle/icon-reboot-active.png
/usr/share/gdm/themes/HumanCircle/icon-reboot-prelight.png
/usr/share/gdm/themes/HumanCircle/icon-reboot.png
/usr/share/gdm/themes/HumanCircle/icon-session-active.png
/usr/share/gdm/themes/HumanCircle/icon-session-prelight.png
/usr/share/gdm/themes/HumanCircle/icon-session.png
/usr/share/gdm/themes/HumanCircle/icon-shutdown-active.png
/usr/share/gdm/themes/HumanCircle/icon-shutdown-prelight.png
/usr/share/gdm/themes/HumanCircle/icon-shutdown.png
/usr/share/gdm/themes/HumanCircle/screenshot.png
/usr/share/gdm/themes/HumanList/GdmGreeterTheme.desktop
/usr/share/gdm/themes/HumanList/HumanList.xml
/usr/share/gdm/themes/HumanList/background.png
/usr/share/gdm/themes/HumanList/bottom_bar.svg
/usr/share/gdm/themes/HumanList/boundingbox-0-0.png
/usr/share/gdm/themes/HumanList/boundingbox-0-1.png
/usr/share/gdm/themes/HumanList/boundingbox-0-2.png
/usr/share/gdm/themes/HumanList/boundingbox-bottom.png
/usr/share/gdm/themes/HumanList/boundingbox-middle.png
/usr/share/gdm/themes/HumanList/boundingbox-top.png
/usr/share/gdm/themes/HumanList/boundingbox.png
/usr/share/gdm/themes/HumanList/boundingbox.svg
/usr/share/gdm/themes/HumanList/entry-0-0.png
/usr/share/gdm/themes/HumanList/entry-0-1.png
/usr/share/gdm/themes/HumanList/entry-0-2.png
/usr/share/gdm/themes/HumanList/entry-1-0.png
/usr/share/gdm/themes/HumanList/entry-1-1.png
/usr/share/gdm/themes/HumanList/entry-1-2.png
/usr/share/gdm/themes/HumanList/entry-2-0.png
/usr/share/gdm/themes/HumanList/entry-2-1.png
/usr/share/gdm/themes/HumanList/entry-2-2.png
/usr/share/gdm/themes/HumanList/gtk-2.0
/usr/share/gdm/themes/HumanList/icon-language-active.png
/usr/share/gdm/themes/HumanList/icon-language-prelight.png
/usr/share/gdm/themes/HumanList/icon-language.png
/usr/share/gdm/themes/HumanList/icon-reboot-active.png
/usr/share/gdm/themes/HumanList/icon-reboot-prelight.png
/usr/share/gdm/themes/HumanList/icon-reboot.png
/usr/share/gdm/themes/HumanList/icon-session-active.png
/usr/share/gdm/themes/HumanList/icon-session-prelight.png
/usr/share/gdm/themes/HumanList/icon-session.png
/usr/share/gdm/themes/HumanList/icon-shutdown-active.png
/usr/share/gdm/themes/HumanList/icon-shutdown-prelight.png
/usr/share/gdm/themes/HumanList/icon-shutdown.png
/usr/share/gdm/themes/HumanList/screenshot.png
/usr/share/gdm/themes/HumanList/ubuntu.png
/usr/share/gdm/themes/HumanList/userentry.svg
/usr/share/gdm/themes/HumanList/userlist-bottom.png
/usr/share/gdm/themes/HumanList/userlist-middle.png
/usr/share/gdm/themes/HumanList/userlist-top.png
/usr/share/gdm/themes/HumanList/gtk-2.0/gtkrc
/usr/share/gdm/themes/circles/GdmGreeterTheme.desktop
/usr/share/gdm/themes/circles/background.svg
/usr/share/gdm/themes/circles/circles.xml
/usr/share/gdm/themes/circles/flower.png
/usr/share/gdm/themes/circles/screenshot.png
/usr/share/gdm/themes/happygnome/GdmGreeterTheme.desktop
/usr/share/gdm/themes/happygnome/background.svg
/usr/share/gdm/themes/happygnome/gnome-logo.svg
/usr/share/gdm/themes/happygnome/happygnome.xml
/usr/share/gdm/themes/happygnome/screenshot.png
/usr/share/gdm/themes/happygnome-list/GdmGreeterTheme.desktop
/usr/share/gdm/themes/happygnome-list/background.svg
/usr/share/gdm/themes/happygnome-list/gnome-logo.svg
/usr/share/gdm/themes/happygnome-list/happygnome-list.xml
/usr/share/gdm/themes/happygnome-list/screenshot.png
/usr/share/gnome/help/gdm
/usr/share/gnome/help/gdm/C
/usr/share/gnome/help/gdm/de
/usr/share/gnome/help/gdm/en_GB
/usr/share/gnome/help/gdm/es
/usr/share/gnome/help/gdm/fr
/usr/share/gnome/help/gdm/ko
/usr/share/gnome/help/gdm/oc
/usr/share/gnome/help/gdm/sv
/usr/share/gnome/help/gdm/uk
/usr/share/gnome/help/gdm/C/gdm.xml
/usr/share/gnome/help/gdm/C/legal.xml
/usr/share/gnome/help/gdm/de/gdm.xml
/usr/share/gnome/help/gdm/en_GB/gdm.xml
/usr/share/gnome/help/gdm/es/gdm.xml
/usr/share/gnome/help/gdm/fr/gdm.xml
/usr/share/gnome/help/gdm/ko/gdm.xml
/usr/share/gnome/help/gdm/oc/gdm.xml
/usr/share/gnome/help/gdm/sv/gdm.xml
/usr/share/gnome/help/gdm/uk/gdm.xml
/usr/share/icons/Feel-of-Japan/128x128/apps/gdm-setup.png
/usr/share/icons/Feel-of-Japan/128x128/apps/gdm-xnest.png
/usr/share/icons/Feel-of-Japan/128x128/apps/gdm.png
/usr/share/icons/Feel-of-Japan/128x128/apps/gdmsetup.png
/usr/share/icons/GartoonRedux/16x16/apps/gdm-login-photo.png
/usr/share/icons/GartoonRedux/16x16/apps/gdm-setup.png
/usr/share/icons/GartoonRedux/16x16/apps/gdm-xnest.png
/usr/share/icons/GartoonRedux/16x16/apps/gdm.png
/usr/share/icons/GartoonRedux/16x16/apps/gdmflexiserver.png
/usr/share/icons/GartoonRedux/16x16/apps/gdmsetup.png
/usr/share/icons/GartoonRedux/22x22/apps/gdm-login-photo.png
/usr/share/icons/GartoonRedux/22x22/apps/gdm-setup.png
/usr/share/icons/GartoonRedux/22x22/apps/gdm-xnest.png
/usr/share/icons/GartoonRedux/22x22/apps/gdm.png
/usr/share/icons/GartoonRedux/22x22/apps/gdmflexiserver.png
/usr/share/icons/GartoonRedux/22x22/apps/gdmsetup.png
/usr/share/icons/GartoonRedux/24x24/apps/gdm-login-photo.png
/usr/share/icons/GartoonRedux/24x24/apps/gdm-setup.png
/usr/share/icons/GartoonRedux/24x24/apps/gdm-xnest.png
/usr/share/icons/GartoonRedux/24x24/apps/gdm.png
/usr/share/icons/GartoonRedux/24x24/apps/gdmflexiserver.png
/usr/share/icons/GartoonRedux/24x24/apps/gdmsetup.png
/usr/share/icons/GartoonRedux/32x32/apps/gdm-login-photo.png
/usr/share/icons/GartoonRedux/32x32/apps/gdm-setup.png
/usr/share/icons/GartoonRedux/32x32/apps/gdm-xnest.png
/usr/share/icons/GartoonRedux/32x32/apps/gdm.png
/usr/share/icons/GartoonRedux/32x32/apps/gdmflexiserver.png
/usr/share/icons/GartoonRedux/32x32/apps/gdmsetup.png
/usr/share/icons/GartoonRedux/scalable/apps/gdm-login-photo.svg
/usr/share/icons/GartoonRedux/scalable/apps/gdm-setup.svg
/usr/share/icons/GartoonRedux/scalable/apps/gdm-xnest.svg
/usr/share/icons/GartoonRedux/scalable/apps/gdm.svg
/usr/share/icons/GartoonRedux/scalable/apps/gdmflexiserver.svg
/usr/share/icons/GartoonRedux/scalable/apps/gdmsetup.svg
/usr/share/icons/HighContrastLargePrintInverse/48x48/apps/gdm-setup.png
/usr/share/icons/HighContrastLargePrintInverse/48x48/apps/gdm-xnest.png
/usr/share/icons/HighContrastLargePrintInverse/48x48/apps/gdm.png
/usr/share/icons/MacUltimate_Leopard/scalable/apps/gdm-setup.png
/usr/share/icons/MacUltimate_Leopard/scalable/apps/gdm.png
/usr/share/icons/MacUltimate_Leopard/scalable/apps/gdmsetup.png
/usr/share/icons/Tangerine/16x16/apps/gdm-setup.png
/usr/share/icons/Tangerine/22x22/apps/gdm-setup.png
/usr/share/icons/Tangerine/24x24/apps/gdm-setup.png
/usr/share/icons/Tangerine/32x32/apps/gdm-setup.png
/usr/share/icons/gnome/24x24/apps/gdm.png
/usr/share/icons/gnome/48x48/apps/gdm.png
/usr/share/icons/hicolor/16x16/apps/gdm-xnest.png
/usr/share/icons/hicolor/16x16/apps/gdmflexiserver.png
/usr/share/icons/hicolor/16x16/apps/gdmsetup.png
/usr/share/icons/hicolor/22x22/apps/gdmflexiserver.png
/usr/share/icons/hicolor/22x22/apps/gdmsetup.png
/usr/share/icons/hicolor/24x24/apps/gdmflexiserver.png
/usr/share/icons/hicolor/24x24/apps/gdmsetup.png
/usr/share/icons/hicolor/32x32/apps/gdm-xnest.png
/usr/share/icons/hicolor/32x32/apps/gdmflexiserver.png
/usr/share/icons/hicolor/32x32/apps/gdmsetup.png
/usr/share/icons/hicolor/48x48/apps/gdm-login-photo.png
/usr/share/icons/hicolor/48x48/apps/gdm-xnest.png
/usr/share/icons/hicolor/48x48/apps/gdm.png
/usr/share/icons/hicolor/48x48/apps/gdmflexiserver.png
/usr/share/icons/hicolor/48x48/apps/gdmsetup.png
/usr/share/icons/hicolor/scalable/apps/gdmflexiserver.svg
/usr/share/icons/hicolor/scalable/apps/gdmsetup.svg
/usr/share/locale-langpack/en_AU/LC_MESSAGES/gdm.mo
/usr/share/locale-langpack/en_CA/LC_MESSAGES/gdm.mo
/usr/share/locale-langpack/en_GB/LC_MESSAGES/gdm.mo
/usr/share/locale-langpack/es/LC_MESSAGES/gdm.mo
/usr/share/locale-langpack/es/LC_MESSAGES/ubuntu-gdm-themes.mo
/usr/share/man/man1/gdm.1.gz
/usr/share/man/man1/gdmflexiserver.1.gz
/usr/share/man/man8/gdm.8.gz
/usr/share/man/man8/gdmchooser.8.gz
/usr/share/man/man8/gdmlogin.8.gz
/usr/share/menu/gdm
/usr/share/omf/gdm
/usr/share/omf/gdm/gdm-C.omf
/usr/share/omf/gdm/gdm-de.omf
/usr/share/omf/gdm/gdm-en_GB.omf
/usr/share/omf/gdm/gdm-es.omf
/usr/share/omf/gdm/gdm-fr.omf
/usr/share/omf/gdm/gdm-ko.omf
/usr/share/omf/gdm/gdm-oc.omf
/usr/share/omf/gdm/gdm-sv.omf
/usr/share/omf/gdm/gdm-uk.omf
/usr/share/pixmaps/gdm-foot-logo.png
/usr/share/pixmaps/gdm.xpm
/usr/share/pixmaps/gdmDebianLogo.xpm
/usr/share/pyshared/deskbar/handlers/gdmclient
/usr/share/pyshared/deskbar/handlers/gdmclient/__init__.py
/usr/share/python-support/gnome-orca/orca/scripts/gdmlogin.py
/var/lib/gdm
/var/lib/dpkg/info/gdm.conffiles
/var/lib/dpkg/info/gdm.config
/var/lib/dpkg/info/gdm.list
/var/lib/dpkg/info/gdm.md5sums
/var/lib/dpkg/info/gdm.postinst
/var/lib/dpkg/info/gdm.postrm
/var/lib/dpkg/info/gdm.preinst
/var/lib/dpkg/info/gdm.prerm
/var/lib/dpkg/info/gdm.templates
/var/lib/dpkg/info/ubuntu-gdm-themes.list
/var/lib/dpkg/info/ubuntu-gdm-themes.md5sums
/var/lib/python-support/python2.5/orca/scripts/gdmlogin.py
/var/lib/python-support/python2.5/orca/scripts/gdmlogin.pyc
/var/log/gdm
/var/log/gdm/:0.log
/var/log/gdm/:0.log.1
/var/log/gdm/:0.log.2
/var/log/gdm/:0.log.3
/var/log/gdm/:0.log.4
/var/log/gdm/:20.log
/var/log/gdm/:20.log.1
/var/log/gdm/:20.log.2
/var/log/gdm/:20.log.3
/var/log/gdm/:20.log.4
/var/log/gdm/:21.log
/var/log/gdm/:21.log.1
/var/log/gdm/:21.log.2

```

Con lo que asumo que debo editar el archivo /etc/gdm/gdm.conf en vez de el /etc/X11/gdm/gdm.conf que decia en el otro post... Será que se cambio de lugar en hardy o algo asi??


Nuevamente, gracias a todos por la ayuda :)

---

### Post by gmunioz on 2008-08-30
Hola tha...:
Recuerda a find....
Si estas usando Hardy, gdm se volvió importante y ahora el archivo está en:
/etc/gdm/gdm.conf
control-alt-delete está en
/etc/event.d/
Saludos
Gabriel.
**Solo doy soporte para Ubuntu** -* 6666* - **Más malo que el diablo**

---

### Post by Thalskarth on 2008-08-30
> **gmunioz said:**
> Hola tha...:
Recuerda a find....
Si estas usando Hardy, gdm se volvió importante y ahora el archivo está en:
/etc/gdm/gdm.conf
control-alt-delete está en
/etc/event.d/
Saludos
Gabriel.
**Solo doy soporte para Ubuntu** -* 6666* - **Más malo que el diablo**

Si, he probado con esto y ha funcioando de 10!!...

mil gracias a todos por su ayuda. Ahora nadie puede apagar/reiniciar el equipo porque si.

Gracias :)

---

### Post by villa77 on 2008-09-01
Perdón que te desanime, pero cómo que nadie puede apagar/reiniciar el equipo porque si?
Con el botón de reboot/apagado del cpu te la apagan/reinician. Porque ya es a nivel hardware.
Pero ahí lo tenés que matar a tu hermano, porque ya te lo está haciendo a propósito :p

---

### Post by Thalskarth on 2008-09-01
> **villa77 said:**
> Perdón que te desanime, pero cómo que nadie puede apagar/reiniciar el equipo porque si?
Con el botón de reboot/apagado del cpu te la apagan/reinician. Porque ya es a nivel hardware.
Pero ahí lo tenés que matar a tu hermano, porque ya te lo está haciendo a propósito :p

jajaja... no es drama.. soy conciente de eso... solo espero que mi hermano no :lolflag:


nah, en si... mi gabinete no tiene boton reset.y si aprieta el bton de apagado, primero le sale en ubuntu el cartel con las opciones de 'cerrar sesion', 'bloquear pantalla' y 'cambiar usuario'
y tiene que mantenerlo presionado un ratito para que realmente se apague. Espero que no lo descubra :)

---

### Post by faktorqm on 2008-09-02
y claro si desconecta el cable de alimentacion tambien lo va a hacer... muy buenos todos los consejos. yo sabia como hacer para bloquear el sysrq para que no hagan REISUB justamente y no encuentro en que archivo lo tengo anotado... tengo un archivo con todas las notas de seguridad pero esa no la encuentro... lo del boton de apagado tambien lo podes configurar desde el bios, pero creo que nada mas para decirle si queres que apague o que suspenda, no se si las nuevas te dejan deshabilitarlo. y si te dejan, tampoco estoy seguro de que resistan los famosos 5 segundos, por que qde alguna manera la pc la tenes que apagar algun dia... Salu2!

---

