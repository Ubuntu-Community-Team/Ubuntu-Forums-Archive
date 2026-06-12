---
title: "Problema GRUB: Imposible iniciar Windows XP"
date: 2009-10-30
forum: Software
---

### Post by fedeavila on 2009-10-30
[FONT="monospace"]Hace mucho que no tenía problemas con Ubuntu :D

Instalé Karmic de cero junto a Windows XP y estuve un par días disfrutándolo (bastante contento) hasta que se me dio por iniciar con Windows XP y veo que se pone la pantalla en negro con una linita que titila sin fin.

Googleé y encontré info, un par de post's con problemas similares pero no me animo a intentar resolverlo sin antes consultarlo x aquí.

Desde Ubuntu sí puedo acceder a la partición con Windows XP de forma totalmente normal. Ejecuté el comando update-grub y detecta, me dice "Windows XP found at..." pero cuando lo elijo del menú del GRUB se queda marmota.

Otra cosa, necesito cambiar la contraseña y no me permite desde **[COLOR="Navy"]Sistema/Preferencias/Acerca de mi[/COLOR]** se queda con el relojito pensando y no se modifica nunca :? (sucede lo mismo desde **[COLOR="Navy"]Usuarios y grupos[/COLOR]**)

Gracias


----
No quiero quedar tan negativo y aprovecho para decir que hace unos días me quejaba porque con la RC de Karmic no podía usar la multifunción y ahora **Sí** (a excepción del escáner) :mrgreen: [/FONT]

---

### Post by Mauro22 on 2009-10-30
Para lo de la contraseña usa: passwd

> NAME
       passwd - change user password

SYNOPSIS
       passwd [options] [LOGIN]

DESCRIPTION
       The passwd command changes passwords for user accounts. A normal user
       may only change the password for his/her own account, while the
       superuser may change the password for any account.  passwd also changes
       the account or associated password validity period.

   Password Changes
       The user is first prompted for his/her old password, if one is present.
       This password is then encrypted and compared against the stored
       password. The user has only one chance to enter the correct password.
       The superuser is permitted to bypass this step so that forgotten
       passwords may be changed.


Lo del grub ni idea... 100% linux aca...

---

### Post by fedeavila on 2009-10-30
> **Mauro22 said:**
> Para lo de la contraseña usa: passwd




Lo del grub ni idea... 100% linux aca...

hey gracias x responder rápido
la contraseña ya la pude cambiar
simplemente intenté repetidas veces :-?

en fin...

---

### Post by fedeavila on 2009-11-03
bueno, doy por resuelto el post ya que lamentablemente tuve que optar por formatear la partición con winxp y reinstalar el grub 2

---

### Post by guillermolisi on 2009-11-03
> **fedeavila said:**
> bueno, doy por resuelto el post ya que lamentablemente tuve que optar por formatear la partición con winxp y reinstalar el grub 2
En realidad no esta resuelto porque la opcion de formatear y volver a instalar no es una solucion en si misma sino una ultima alternativa que siempre esta presente. Aun asi, haciendo todo eso, podrias continuar con el mismo problema (y ahi es donde volves a la edad del lapiz y el papel).

Asi que le quito el tag y lo dejo abierto por si alguien tiene una solucion que aportar.

---

### Post by fedeavila on 2009-11-03
jajaj no entiendo, era necesario hacer eso o simplemente jugar con los threads? el problema ya no lo tengo más  [y no tiene más info que la de cambiar una simple password] lo digo más que nada para que no haya hilos abiertos sin sentido :-?
 todo bien, à bientôt! 
 [offtopic]

---

