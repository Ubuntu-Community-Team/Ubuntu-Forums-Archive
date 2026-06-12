---
title: "Respaldar datos de Evolution"
date: 2011-10-25
forum: Software
---

### Post by Vero1 on 2011-10-25
Hola a todos,

Debido a los problemas que me ocasiona Evolution, entre los cuales se encuentra la imposibilidad de hacer Backup porque me sale una ventana donde dice que no está soportado, que se freeza cuando quiero poner la contraseña que me pide, que no quiere enviar los mails pero sí recibe, que no tiene mbox porque el paquete del applet está roto y no sé cómo arreglarlo porque mi aviso a Launchpad no tuvo eco, etc etc etc. estoy pensando en volver a Ubuntu 11.04 que no tenía estos problemas.

Además, prefiero el escritorio de Gnome porque Unity no me resulta práctico para nada y me marea.

Aparte, no puedo correr Synaptic por un bug que es de conocimiento público pero que no se soluciona. Prefiero Synaptic al Centro de Soft, a pesar de lo bonito que se vé...

Quisiera me dijeran cómo hacer el Backup de Evolution para no perder correo, como me pasó con el mes de Octubre de la Bandeja de Entrada que lisa y llanamente desapareció al hacer upgrade.

Espero por favor me indiquen qué debo hacer.

Desde ya muchas gracias y saludos.

---

### Post by granjero on 2011-10-25
hola vero, encontré esto espero que te sirva...

en una terminal desberías escribir los siguientes comandos:

```
$gconftool-2 --shutdown
$evolution --force-shutdown
$cd
$tar -cvzf evolution-backup.tar.gz .evolution .gconf/apps/evolution .gnome2_private/Evolution
```

Eso según dice la guía hace el backup que hace evolution solito. 

de esa página saque la info que te cuento.
[http://embraceubuntu.com/2005/12/03/how-to-backup-evolution/](http://embraceubuntu.com/2005/12/03/how-to-backup-evolution/)

---

### Post by guillermolisi on 2011-10-26
> **granjero said:**
> hola vero, encontré esto espero que te sirva...

en una terminal desberías escribir los siguientes comandos:

```
$gconftool-2 --shutdown
$evolution --force-shutdown
$cd
$tar -cvzf evolution-backup.tar.gz .evolution .gconf/apps/evolution .gnome2_private/Evolution
```

Eso según dice la guía hace el backup que hace evolution solito. 

de esa página saque la info que te cuento.
[http://embraceubuntu.com/2005/12/03/how-to-backup-evolution/](http://embraceubuntu.com/2005/12/03/how-to-backup-evolution/)
Esa es la mitad de la receta :)

La otra mitad, no menos importante, es como restituis ese backup.
Y mas importante aun es si despues de restituido seguis contando con todo el contenido original en la nueva instalacion (sino, para que me sirve el backup ?)

En teoria y sin haber usado Evolution, salvo para ver como es, deberias reemplazar .evolution de la nueva instalacion con el contenido de la copia de respaldo, ingresando en una terminal/consola ```
cd; tar -xvz evolution-backup.tar.gz
```

Lo que no se es si con la restitucion se reemplaza algun archivo propio de Evolution que se ha modificado con algun cambio de version y eso hace que deje de funcionar como se espera.

Por eso me gusta mucho mas Thunderbird. Mas simple, mas eficiente.

---

### Post by hictio on 2011-10-26
Vero1, yo vengo usando el propio Evolution para hacer los backups sin problemas desde 7.04.
Y para hacer el restore, también el propio Evolution con: File > Restore.
Ningún problema, de hecho, muchas veces uso este "sistema", para pasar un snapshot de mi Evolution de una máquina a otra.
Cómo es el mensaje de error que te da cuando querés hacer un backup?

---

### Post by EnriqueK on 2011-10-26
En entrada usé Thunderbird por que me permitía sincronizar mis mensajes con otro que tenía cuando usaba Xp  en otra partición.
Mi recomendación es que luego de realizar el respaldo uses Thunderbird e importas todo, es muy simple y por si fuera poco, Thunderbird pasó a ser el que se instala por defecto a partir de Ubuntu 11.10, deben haber buenas razones para ello

---

### Post by hictio on 2011-10-26
> **EnriqueK said:**
> En entrada usé Thunderbird por que me permitía sincronizar mis mensajes con otro que tenía cuando usaba Xp  en otra partición.
Mi recomendación es que luego de realizar el respaldo uses Thunderbird e importas todo, es muy simple y por si fuera poco, Thunderbird pasó a ser el que se instala por defecto a partir de Ubuntu 11.10, deben haber buenas razones para ello

El problema con Thunderbird es no tiene incorporada una agenda, TODOs, Notas, etc. En cambio Evolution incluye todo por default (y es muchísimo mejor que el Outlook ;) )

---

### Post by EnriqueK on 2011-10-26
El tema del calendario no es algo que me interese, pero Thunderbird al igual que Firefox, se maneja con complementos y basta hacer una búsqueda para poder elegir entre varios, por ejemplo tenés para sincronizar con Google Calendar, hay calendarios propios y hasta tenés uno llamado " Evolution Mirror"
 Además Evolution es producto de Gnome y este anda a los tumbos con su Gnome3 , no termina de aterrizar , por lo que a Evolution no le debe estar dando mucha importancia. Por algo Ubuntu cambió de gestor de correos por defecto

---

### Post by Vero1 on 2011-10-26
Hola a todos,

Muchas gracias a todos por contestar.

Haré lo que dicen Granjero y Guillermo Lisi.

A Hictio le contesto que cuando quiero hacer backup me dice que no se pudo mostrar el contenido de la carpeta. Operación no soportada.Lo mismo dice cuando quiero restaurar.

A Enrique K le digo que desinstalé Thunderbird porque no me gustó. Tal vez porque estoy demasiado acostumbrada a Evolution :-) 

Volveré. saludos.

---

### Post by guillermolisi on 2011-10-26
> **hictio said:**
> El problema con Thunderbird es no tiene incorporada una agenda, TODOs, Notas, etc. En cambio Evolution incluye todo por default (y es muchísimo mejor que el Outlook ;) )
Como dijo Enriquek, con TB tengo todo lo que hace mucho tenia con Outlook pero mucho mejor. Incluso permite servicios en la nube como Google Calendar (podes tener varios y configurados de distinta forma).
Las cosas cambian, algunas evolucionan favorablemente, asi que a no quedarse con fotografias viejas :)

---

### Post by granjero on 2011-10-26
Yo estoy probando 11.10 con gnome3, mi tema fue pasar los mails viejos de evolution a TB de un plumazo, sin horas de google de por medio... Me instalé Evolution y cargue mis viejos correos en dos clicks. Es así de fácil pasarlos a TB?

En algún lugar me perdí un botón mágico? 

Salud!

---

### Post by hictio on 2011-10-26
> **guillermolisi said:**
> Como dijo Enriquek, con TB tengo todo lo que hace mucho tenia con Outlook pero mucho mejor. Incluso permite servicios en la nube como Google Calendar (podes tener varios y configurados de distinta forma).
Las cosas cambian, algunas evolucionan favorablemente, asi que a no quedarse con fotografias viejas :)

Puede ser, Evolution también tiene soporte para Google Calendar y Contacts a través de Evolution ;)

---

### Post by Vero1 on 2011-10-28
Hola, cómo están?

Bueno, en lo que respecta a Synaptic, solucionado. Alguien me ayudó en el Foro de Ubuntu-es. Para que sepan, si a alguien le pasa lo mismo, hay que ir a Sistema-Acceso Universal y desactivar Lector de Pantalla.

Evolution tambien está semi arreglado por haber entrado en modo de recuperación, que parece que solucionó algunos de los problemas. Por lo menos ya puedo enviar correo.

En cuanto a backup, sigue tirando error pero me dijeron que no hiciera caso de la ventanita y efectivamente comenzó a hacer backup pero de mas de 2000 mensajes... lo aborté. Pienso que son todos los mensajes no eliminados que tengo en algun lugar.

Si alguien me puede indicar cómo  hacer backup de las carpetas por separado, lo voy a agradecer.

saludos

---

