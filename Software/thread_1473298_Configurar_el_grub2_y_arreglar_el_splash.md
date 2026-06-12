---
title: "Configurar el grub2 y arreglar el splash"
date: 2010-05-05
forum: Software
---

### Post by santi1703 on 2010-05-05
buenas...regien me regristro en el foro a leechear informacion muajajajaj (6)

nah en serio...soy usuario a medio tiempo d ubuntu (deberia serlo a tiempo completo pero los juegos me pueden)

instale hace un par d dias lucid lynx, y al kerer alindarlo mande moco al editar el grub y ahora me tira error cuando kiero updatear

sudo update-grub2
/etc/default/grub: 28: Syntax error: EOF in backquote substitution

eso me dice doña consola, a pesar d k deshice todos los cambios k habia hecho, y k por cierto no backupee :S

lo k pretendia hacer era poner grubs animadosm y por otro lado corregir el splash k pierde resolucion al instalar los drivers privativos d la vga (una ati 4870x2 en mi caso)

si, se k explike todo enredado, si kieren algun dato pregunteme :P y k uso mucho lenguaje sms pero si alguno se esmera en desencriptarlo y tirarme alguna idea estare muy agradecido =D

saludos

---

### Post by alfplayer on 2010-05-05
Hola. Voy a tratar de ayudarte.

Al parecer hay un error en la línea 28 de /etc/default/grub. Verificá que realmente vuelvas ese archivo a su estado original.

Se recomienda que no escribas español incorrecto (por ejemplo con "lenguaje sms").

---

### Post by santi1703 on 2010-05-05
> **alfplayer said:**
> Hola. Voy a tratar de ayudarte.

Al parecer hay un error en la línea 28 de /etc/default/grub. Verificá que realmente vuelvas ese archivo a su estado original.

Se recomienda que no escribas español incorrecto (por ejemplo con "lenguaje sms").

vos podras cotejar si mi /etc/default/grub esta igual k el tuyo?? en el proximo post lo pego aca, puede ser??

gracias

---

### Post by alfplayer on 2010-05-06
En la web se encuentran muchas, por ejemplo:

[https://wiki.ubuntu.com/Grub2#grub (/etc/default/grub)]("https://wiki.ubuntu.com/Grub2#grub (/etc/default/grub)")

También está en el paquete "grub-pc":

sudo gnome-open /var/cache/apt/archives/grub-pc*

En la pestaña de archivos incluídos está en usr/share/grub/default/grub.

---

### Post by Rodrigo6375 on 2010-05-12
Tengo un problema con el GRUB:

Acabo de actualizar de 9.10 a 10.04 y en la parte donde me dice que elija en que partición instalarlo, me equivoqué. :(

Luego de terminar y reiniciar, me devuelve una linea de comando que menciona que no encuentra no se que del GRUB.

Alguien sabe como puedo arreglar esto desde la linea de comando, o de alguna otra forma? :confused:

No quiero perder los contenidos de las carpetas de Ubuntu ni una unstalación de WinXP que conservo por temas laborales.

Muchas Gracias

---

### Post by alfplayer on 2010-05-12
> **Rodrigo6375 said:**
> Tengo un problema con el GRUB:

Acabo de actualizar de 9.10 a 10.04 y en la parte donde me dice que elija en que partición instalarlo, me equivoqué. :(

Luego de terminar y reiniciar, me devuelve una linea de comando que menciona que no encuentra no se que del GRUB.

Alguien sabe como puedo arreglar esto desde la linea de comando, o de alguna otra forma? :confused:

No quiero perder los contenidos de las carpetas de Ubuntu ni una unstalación de WinXP que conservo por temas laborales.

Muchas Gracias

Podés buscar información en la web o en este foro sobre cómo recuperar grub, o abrir otro tema nuevo.

---

### Post by Rodrigo6375 on 2010-05-13
Lo he resuelto utilizando el [Super GRUB2 Disk 1.30]("http://www.supergrubdisk.org/forum/index.php?topic=438.0").

Muy sencillo:
[LIST]
[*]se quema un CD con el (*) [ISO del super GRUB2]("http://www.supergrubdisk.org/index.php?pid=5")
[*]Se arranca la PC con ese Disco
[*]Se elige entre las opciones, Buscar
[*]Aparece el arranque recuperado.
[*]Listo!
[/LIST]

(*)También se puede bajar a un [USB]("http://www.supergrubdisk.org/index.php?pid=7") o a un [FLOPPY]("http://www.supergrubdisk.org/index.php?pid=6")


> **Rodrigo6375 said:**
> Tengo un problema con el GRUB:

Acabo de actualizar de 9.10 a 10.04 y en la parte donde me dice que elija en que partición instalarlo, me equivoqué. :(

Luego de terminar y reiniciar, me devuelve una linea de comando que menciona que no encuentra no se que del GRUB.

Alguien sabe como puedo arreglar esto desde la linea de comando, o de alguna otra forma? :confused:

No quiero perder los contenidos de las carpetas de Ubuntu ni una unstalación de WinXP que conservo por temas laborales.

Muchas Gracias

---

