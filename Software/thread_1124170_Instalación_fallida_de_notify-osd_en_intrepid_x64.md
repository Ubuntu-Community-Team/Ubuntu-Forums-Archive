---
title: "Instalación fallida de notify-osd en intrepid x64"
date: 2009-04-13
forum: Software
---

### Post by warmaster on 2009-04-13
Les cuento que estuve tratando de instalar el sistema de notificaciones del jaunty en intrepid en mi ubuntu 8.10 x64 con Aurora Engine y me tira los errores que detallo al final.

Seguí los pasos especificados en los siguientes blogs:
[http://www.genbeta.com/linux/instala-el-nuevo-sistema-de-notificaciones-de-ubuntu-jaunty-jackalope](http://www.genbeta.com/linux/instala-el-nuevo-sistema-de-notificaciones-de-ubuntu-jaunty-jackalope)

[http://blog.alexrybicki.com/2009/02/how-to-install-notify-osd-in-intrepid.html](http://blog.alexrybicki.com/2009/02/how-to-install-notify-osd-in-intrepid.html)

Mi pregunta es, me pasa esto por que tengo el Aurora engine o por que no instalé bien notify-osd ?

En caso de haberlo instalado mal, hay algún log que registre mis operaciones infradotadas ?

Desde ya muchas gracias por la buena onda y sean pacientes que soy bastante nuevo, viva linux !

Fede

A continuación la lista de errores:

federico@fede-escritorio:~/Documentos$ killall notification-daemon ;  /home/federico/Documentos/Archivos\ de\ Programa/notify/notify-osd/src/notify-osd
notification-daemon: ningún proceso eliminado
/home/federico/.themes/Aurora Leopard BSM/gtk-2.0/gtkrc:260: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.
/home/federico/.themes/Aurora Leopard BSM/gtk-2.0/gtkrc:261: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/federico/.themes/Aurora Leopard BSM/gtk-2.0/gtkrc:262: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/federico/.themes/Aurora Leopard BSM/gtk-2.0/gtkrc:447: error: invalid string constant "panel-buttons", expected valid string constant
** (notify-osd:15838): DEBUG: [2009-04-13T04:48:29-00:00, Notificación de correo, id:0, icon:stock_mail] Nuevo mensaje
Buzón: [email]federicomenoyo@gmail.com[/email]
De: me <federicomenoyo@gmail.com>
Asunto: pop

** (notify-osd:15838): DEBUG: notification request turned into a dialog box, because it contains at least one action callback (mail-open: "Abrir")

---

### Post by Hei Ku on 2009-04-13
Yo probaria con un tema default, a ver si asi anda.

PS: Movido a Software

---

