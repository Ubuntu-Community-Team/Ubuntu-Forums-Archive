---
title: "Thunderbird Compartido entre 2 pc"
date: 2009-01-22
forum: Software
---

### Post by NickCis on 2009-01-22
Lo que quiero hacer es tener instalado el Thunderbird en una pc (llamemosla server, que esta conectada a internet, compartiendola y tambien comparte carpetas) y que otra pc (llamemosla nodo), pueda ejecutar ese thunderbird y tenga toda la misma configuracion y mails que el server.

El "server", es un ubuntu 8.04 que tiene el Thunderbird instalado.
El "nodo", es un ubuntu 8.04 (instalacion minima, Openbox como WM, PcmanFM como Fm), que no tiene el THunderbird.

Digo el Thunderbird por que es el programa que estoy usando, pero si es mas facil con otro programa me da lo mismo.

Saludos.

---

### Post by Hei Ku on 2009-01-22
Y... yo usaria un servidor de correo, ya que eso es lo que estas buscando. Y algunos vienen con opcion de webmail, IMAP4 o POP3.

Opciones tenes a montones, pero el Thunderbird no esta incluida. O al menos a mi me parece la herramienta incorrecta para el trabajo.

---

### Post by sergiom99 on 2009-01-22
O intentar correr el Thunderbird Portable con wine, que es una version del TB que esta "autocontenida" en una sola carpeta y la podes correr donde sea.
No estoy seguro si puede correr con Wine.
Lo bajas en portableapps.com.

---

### Post by NickCis on 2009-01-22
Ok, voy a probar eso,,, el problema que me da el thunderbird emulado con el wine, es que no puedo abrir los adjuntos directamente del programa, osea, cuando me abre la ventana de descargar o abrir, si le pongo abrir no me figura el Open Office.

P.D.: no hay otra forma?, el thunderbird no se puede configurar para que guarde la configuracion en otra carpeta? (asi le pongo que sea la carpeta compartida x red y listo...)

---

### Post by sergiom99 on 2009-01-22
> **NickCis said:**
> 
P.D.: no hay otra forma?, el thunderbird no se puede configurar para que guarde la configuracion en otra carpeta? (asi le pongo que sea la carpeta compartida x red y listo...)

Seguramente en algun lado podras decir donde guardar el profile. Pero te aconsejo averiguarlo en la documentacion o wiki de TB, que ahi lo van a tener mas claro.

---

### Post by guillermolisi on 2009-01-23
Conozco gente que ha hecho algo parecido pero compartiendo el perfil de TB entre Ubuntu y la particion NTFS de Windows, en la misma maquina.

Uno de ellos usaba TB bajo Windows y luego instalo Ubuntu en otra particion. Para no tener dos mbox distintos, apunto la configuracion de TB al directorio que ya tenia en Win y, segun el, funciono perfecto.

---

### Post by NickCis on 2009-01-23
Listo, ya lo solucione.

Desde la pc que esta de "Cliente", instale el thunderbir normalmente.
Despues desde consola abri "thunderbird -ProfileManager", teniendo la carpeta de la configuracion del thunderbird compartida (en el "server"), cree un nuevo usuario y diciendole al programa que use la misma carpeta para guardar la configuracion y listo :P.

Saludos.

Edit: Quise ponerlo como solved pero no me aparece la opcion en "Thread Tools",,,

---

