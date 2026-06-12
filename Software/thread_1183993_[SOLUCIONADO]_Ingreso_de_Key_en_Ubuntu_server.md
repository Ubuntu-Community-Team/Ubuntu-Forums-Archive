---
title: "[SOLUCIONADO] Ingreso de Key en Ubuntu server"
date: 2009-06-10
forum: Software
---

### Post by flakojaime on 2009-06-10
HOla.

He tenido problemas para ingresar  el key a los servidores de Ubuntu

[B]gpg: error del servidor de claves
gpg: envío al servidor de claves fallido: Error del servidor de claves[/B]

Alguien sabe si esta caido el servidor?

Gracias!

---

### Post by pagondel on 2009-06-11
Hay varios servidores, si con el que probaste estaba caido, prueba con otro, por ejemplo: [http://pgp.mit.edu/](http://pgp.mit.edu/)
Saludos!

---

### Post by flakojaime on 2009-06-11
HOla, 

No hay problema que ingrese el key de la firma del codigo de conducta en esa direccion?



saludos

---

### Post by pagondel on 2009-06-11
no flakojaime no hay problema... cada cierto tmp todos los servidores de keys gpg se sincronizan ;)

---

### Post by flakojaime on 2009-06-12
HOla.

Como se ingresa el key en esa pagina?


gracias

---

### Post by pagondel on 2009-06-12
```
gpg --keyserver pgp.mit.edu --send-keys $GPGKEY
```

---

### Post by flakojaime on 2009-06-13
Ok, gracias!...


key ingresada

---

### Post by Carlos C on 2009-06-13
Título editado y thread movido al subforo adecuado.

---

