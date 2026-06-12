---
title: "[SOLVED] Open Office 3 y el Sonido"
date: 2008-12-16
forum: Software
---

### Post by NickCis on 2008-12-16
Estoy usando Open Office 3, con Ubuntu 8.04, encuentro un problema en el Impress (lo que vendria a ser el powerpoint). Lo que pasa es que no emite ningun tipo de sonido. Me mandan archivos *.pps por email, que estan probados en otra maquina con Windows, tienen sonido, aca no me andan.
Ademas, si intento en la galeria escuchar alguno de los sonidos que vienen con el Open Office, tampoco andan.

Como puedo solucionar esto?.

Por lo que busque, es algo relacionado con el java, el java que tengo, creo que es el 6 (no se bien donde fijarme) y es el que viene solo o se instala con las Ubuntu Restricted (creo que es una de estas dos, por que nunca instale el java, sino que aparecio solo).

Saludos.

---

### Post by Hei Ku on 2008-12-17
Sabés si en otras aplicaciones java tenés sonido? O probaste de deshabilitar java en el OpenOffice? A veces traía problemas.

---

### Post by NickCis on 2008-12-17
Deshabilitando el java en el open office, me dice que lo tengo que habilitar para escuchar sonido.
Y no se como fijarme para saber si el sonido Java anda.
Por lo que vi por google, es que tengo que instalar el JMF, Java Media Framework y el Mp3 Plugin.

Algun sabe de esto?

Saludos.

Edit: Probe siguiendo estas instrucciones ( [http://comunidad.molinux.info/index.php/A%F1adir_soporte_de_sonido_a_OpenOffice](http://comunidad.molinux.info/index.php/A%F1adir_soporte_de_sonido_a_OpenOffice) ) (y volviuendo a instalar el Java) pero sigue sin andar.

---

### Post by NickCis on 2008-12-19
Nadie, tiene idea de como solucionarlo?
Saludos.

---

### Post by Hei Ku on 2008-12-20
que paquetes de java tenes instalado?

---

### Post by NickCis on 2008-12-20
Decidi volver al Openoffice que viene con el Ubuntu, y el problema del sonido se soluciono.

Use el comando: "sudo apt-get install openoffice.org", el cual me desinstale el Open Office 3 y me instalo el 2. Y este problema desaparecio...

Saludos.

---

