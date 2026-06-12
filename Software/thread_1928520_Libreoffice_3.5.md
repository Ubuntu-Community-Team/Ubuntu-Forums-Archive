---
title: "Libreoffice 3.5"
date: 2012-02-20
forum: Software
---

### Post by rojojuan on 2012-02-20
Tengo el siguiente problema:
Estoy usando Ubuntu 10,04.
Tengo instalada la versión 3-4-5 de Libreoffice. Actualicé a la versión 3-5 y encuentro que cuando quiero guardar una plantilla de Writer me aparece el mensaje “template ya existe” y no me deja incorporarla o modificarla.
Aclaro que desinstalé previamente la versión 3-4-5 con el comando “apt-get purge libreoffice*,*”
Por lo que dije mas arriba tuve que volver a la versión 3-4-5.
En otro equipo que tenía openoffice y lo reemplace por Libreoffice no tuve problema alguno.
¿Se tratará de un problema de rutas?

---

### Post by euzkoarima on 2012-02-21
Según leí por ahí, en la versión 3.5 cambiaron donde se guarda el profile de tu usuario.
Parece que hasta 3.4 era en /home/tu-usuario/.libreoffice/3/user (3 puede ser otro número)
CREO, x lo que leí, que ahora está en /home/tu-usuario/.config/libreoffice/3/user
Si es asi, parece que hay que probar (obviamente, después de haber hecho backup por las dudas) primero de borrar el viejo profile.
Si eso no funcionan, también recomiendan borrar o cambiar el nombre del archivo registrymodifications.xcu que está en el profile.

Saludos,
Eduardo

---

### Post by rojojuan on 2012-02-21
Muchas gracias por la pronta respuesta. Lo pruebo y comento después.
Recién ví que fue reportado como bug en [http://ask.libreoffice.org/question/240/error-creating-new-documenttemplates-already-exist](http://ask.libreoffice.org/question/240/error-creating-new-documenttemplates-already-exist)


> **euzkoarima said:**
> Según leí por ahí, en la versión 3.5 cambiaron donde se guarda el profile de tu usuario.
Parece que hasta 3.4 era en /home/tu-usuario/.libreoffice/3/user (3 puede ser otro número)
CREO, x lo que leí, que ahora está en /home/tu-usuario/.config/libreoffice/3/user
Si es asi, parece que hay que probar (obviamente, después de haber hecho backup por las dudas) primero de borrar el viejo profile.
Si eso no funcionan, también recomiendan borrar o cambiar el nombre del archivo registrymodifications.xcu que está en el profile.

Saludos,
Eduardo

---

### Post by philpinch on 2012-02-28
Sorry, no hablo espanol.

template ya existe or templates already exist whenever you try to do anything involving a
Template. This includes opening an existing document based on a template.

You just have to rename $HOME/.config/libreoffice/3/user/registrymodifications.xcu to ~/.config/libreoffice/3/user/registrymodifications.xcu.old

Hope it will help.

---

### Post by rojojuan on 2012-03-01
Muchas gracias a Euzkoarima y a Philpinch.
Seguí sus instrucciones y todo puedo guardar las plantillas correctamente.
Todo funciona bien hasta ahora.

---

