---
title: "Bug Raro en Firefox"
date: 2008-12-11
forum: Software
---

### Post by pol666 on 2008-12-11
hola sucede que el firefox 3.04 sobre Ubuntu Intrepid bajo KDE4.1 se me cierra repentinamente, generalmente cuando copio algo en la barra de direcciones, aunque tambien en otras ocaciones, por ejemplo ahora escribiendo este mensaje :P.


La consola me dice esto 
> 

The program 'firefox' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 27938 error_code 2 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

---

### Post by sajnox on 2008-12-11
Reporte el bug amigo mio, reportelo!!

[https://developer.mozilla.org/en/Crash_reporting](https://developer.mozilla.org/en/Crash_reporting)

---

### Post by pol666 on 2008-12-11
Gracias, pero resuleta cuando voy a la barra de direcciones al about firefox tambien se cierra U_U

Alguien podria reportar mi bug?

---

### Post by majatu on 2008-12-12
> **pol666 said:**
> Gracias, pero resuleta cuando voy a la barra de direcciones al about firefox tambien se cierra U_U

Alguien podria reportar mi bug?

Me pide el Branch del Firefox, cual tenes? me da a elegir **1.9**, **1.9.1** y **1.9.2**

Complete todo asi:

[LINK]("http://crash-stats.mozilla.com/?do_query=1&product=Firefox&branch=1.9.2&version=Firefox%3A3.0.4&platform=linux&query_search=signature&query_type=contains&query=The%2Bprogram%2B%27firefox%27%2Breceived%2Ban%2BX%2BWindow%2BSystem%2Berror.%2BThis%2Bprobably%2Breflects%2Ba%2Bbug%2Bin%2Bthe%2Bprogram.%2BThe%2Berror%2Bwas%2B%27BadValue%2B(integer%2Bparameter%2Bout%2Bof%2Brange%2Bfor%2Boperation)%27.%2B(Details%3A%2Bserial%2B27938%2Berror_code%2B2%2Brequest_code%2B53%2Bminor_code%2B0)%2B(Note%2Bto%2Bprogrammers%3A%2Bnormally%2C%2BX%2Berrors%2Bare%2Breported%2Basynchronously%3B%2Bthat%2Bis%2C%2Byou%2Bwill%2Breceive%2Bthe%2Berror%2Ba%2Bwhile%2Bafter%2Bcausing%2Bit.%2BTo%2Bdebug%2Byour%2Bprogram%2C%2Brun%2Bit%2Bwith%2Bthe%2B--sync%2Bcommand%2Bline%2Boption%2Bto%2Bchange%2Bthis%2Bbehavior.%2BYou%2Bcan%2Bthen%2Bget%2Ba%2Bmeaningful%2Bbacktrace%2Bfrom%2Byour%2Bdebugger%2Bif%2Byou%2Bbreak%2Bon%2Bthe%2Bgdk_x_error()%2Bfunction.)%2B&date=now&range_value=1&range_unit=weeks")

Estará bien hecho el reporte?


Saludos!

---

### Post by pol666 on 2008-12-12
Gracias majatu, Justamente me iba a fijar eso por que no sabia que era, aparentemente cuadno voy al about se cierra y no puedo ver que dice.


Oh, Desde Gnome lo pude hacer creo que el branch es 1.9.04 puede ser?

---

### Post by Hei Ku on 2008-12-13
Es 3.0.4

```

Package: firefox
Priority: optional
Section: web
Installed-Size: 120
Maintainer: Alexander Sack <asac@ubuntu.com>
Architecture: all
Source: firefox-3.0
Version: 3.0.4+nobinonly-0ubuntu0.8.04.1
Depends: firefox-3.0
Filename: pool/main/f/firefox-3.0/firefox_3.0.4+nobinonly-0ubuntu0.8.04.1_all.deb

```

---

