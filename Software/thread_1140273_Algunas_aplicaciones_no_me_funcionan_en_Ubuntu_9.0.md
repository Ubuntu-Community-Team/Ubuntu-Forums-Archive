---
title: "Algunas aplicaciones no me funcionan en Ubuntu 9.04"
date: 2009-04-27
forum: Software
---

### Post by EnriqueK on 2009-04-27
Instalé de cero Ubuntu 9.04 64 bits y aunque no he chequeado todas las aplicaciones, sin embargo he notado que algunas no me funcionan, entre ellas menciono a **alarm-clock**, al ejecutar esta aplicacion se me congela el sistema, otra es el **startupmanager**, directamente no hace nada o sea el programa arranca pero no es capaz de hacer alguna modificación en el grub. Lo que he notado es que al menos estas dos aplicaciones tienen en común es que depende de python o estás escritos en python.

---

### Post by pablo.s on 2009-04-27
Reportá los bugs a Launchpad, no acá !

---

### Post by sajnox on 2009-04-27
> **pablo.s said:**
> Reportá los bugs a Launchpad, no acá !

Lo cortez no quita lo valiente y te recuerdo dos reglas de oro para el foro

1) No critiques, explica!!! 
2) Si no vas a aportar nada, guarda silencio

Aca (0) tenes una traduccion de una muy buena guia para reportar bugs, ahora instalo el startupmanager para ver si tengo el mismo problema y lo reportamos.

Por otro lado si tenes la sospecha de que un programa tiene un bug siempre es prudente ejecutarlo desde la terminal que explica mejor lo que va pasando.

Y para ponernos un poco mas finos si vemos en la parte superior del foro hay un cartel verde y deja a un link aca (1)


Saludos,

(0) [http://ubuntuforums.org/showthread.php?t=1017604&highlight=como+reportar+bugs](http://ubuntuforums.org/showthread.php?t=1017604&highlight=como+reportar+bugs)
(1) [http://mdzlog.alcor.net/2009/03/31/please-dont-report-ubuntu-bugs-directly-to-launchpad/](http://mdzlog.alcor.net/2009/03/31/please-dont-report-ubuntu-bugs-directly-to-launchpad/)

---

### Post by DrKenobi on 2009-04-27
A mi no me anda/deja instalar el FileZilla, eso es un bug a reportar?

---

### Post by pablo.s on 2009-04-27
Que error te da? Si bajás el paquete
de un PPA? Por ejemplo este:

[COLOR=Green]**[https://launchpad.net/~frasten/+archive/ppa](https://launchpad.net/~frasten/+archive/ppa)**[/COLOR]
o
**[COLOR=Green]https://launchpad.net/~debfx/+archive/ppa[/COLOR]**

---

### Post by DrKenobi on 2009-04-27
> **pablo.s said:**
> Que error te da? Si bajás el paquete
de un PPA? Por ejemplo este:

[COLOR=Green]**[https://launchpad.net/~frasten/+archive/ppa](https://launchpad.net/~frasten/+archive/ppa)**[/COLOR]
o
**[COLOR=Green]https://launchpad.net/~debfx/+archive/ppa[/COLOR]**

Me da "error" cuando intenato instalarlo con el Add/Remove. Ahi te dejo una captura de la pantalla.

---

### Post by pablo.s on 2009-04-27
Ese error me da a pensar que 
estas usando:

a) Ubuntu 64 bits
b) PowerPC
c) SPARC ???

---

### Post by DrKenobi on 2009-04-28
> **pablo.s said:**
> Ese error me da a pensar que 
estas usando:

a) Ubuntu 64 bits
b) PowerPC
c) SPARC ???

Nop, estoy usando Xubuntu i386
En 8.10 no tenia problemas, pero cuando pase a 9.04 no me dejo instalarlo
Igual ahora estoy usando Gigolo, que ya viene instalado con Xubuntu y anda muy bien
Raro....pero...

---

### Post by KaKuS on 2009-04-28
> **EnriqueK said:**
> Instalé de cero Ubuntu 9.04 64 bits y aunque no he chequeado todas las aplicaciones, sin embargo he notado que algunas no me funcionan, entre ellas menciono a **alarm-clock**, al ejecutar esta aplicación se me congela el sistema, otra es el **startupmanager**, directamente no hace nada o sea el programa arranca pero no es capaz de hacer alguna modificación en el grub. Lo que he notado es que al menos estas dos aplicaciones tienen en común es que depende de python o estás escritos en python.

A mi tampoco me funciono el startupmanager la primera vez, al abrir la ventana me tiro a la consola de inicio y me reinicio el X. Como no me pareció importante lo deje así, hoy al ver tu mensaje lo tire desde la consola y anduvo de 10. Te diria que pruebes desde la consola "sudo startupmanager" y fijate.

El otro paquete no lo conozco pero lo instalo y te aviso.

---

### Post by EnriqueK on 2009-04-28
Gracias,  el startupmanager funciona, seguramente el problema se corrigió luego de alguna actualizaxión, aunque el alarm-clock sigue dando problemas de bloquear el sistema.
Al final lo que no llego a enteder es el por que alguanas aplicaciones que en anteriores versiones del SO funcionan. bien, dejan de hacerlo con las mas nuevas, personalmente pienso que es por el uso de dependencias compartidas que  no siempre se ajustan adecuadamente a todas las aplicaciones que hacen uso de ellas.

---

### Post by Hei Ku on 2009-04-29
> **EnriqueK said:**
> Gracias,  el startupmanager funciona, seguramente el problema se corrigió luego de alguna actualizaxión, aunque el alarm-clock sigue dando problemas de bloquear el sistema.
Al final lo que no llego a enteder es el por que alguanas aplicaciones que en anteriores versiones del SO funcionan. bien, dejan de hacerlo con las mas nuevas, personalmente pienso que es por el uso de dependencias compartidas que  no siempre se ajustan adecuadamente a todas las aplicaciones que hacen uso de ellas.

Versiones nuevas del programa, bugs en las nuevas versiones, el empaquetador se distrajo y metio mal los dedos. Suceden miles de cosas a lo largo de la creacion de una version que pueden provocar problemas. Igualmente, hay otros programas como el Filezilla, pero nativos de windows. El primero que se me viene a la cabeza es Konqueror, que para estos casos es buenisimo.

---

