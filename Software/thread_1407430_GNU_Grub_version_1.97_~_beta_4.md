---
title: "GNU Grub version 1.97 ~ beta 4"
date: 2010-02-15
forum: Software
---

### Post by RafaelG on 2010-02-15
Hola a todos los companeros Ubunteros, despues de un tiempo logre convenser a un amigo que instale ubuntu a modo de prueba desde windows ya que mi amigo piensa que ubuntu es algo demaciado complicado y dificil pero de tanto insistir logre convercerlo que intente a modo prueba, Todo andaba bien hasta que carge las actualizaciones y me produjo el siguiente bug que no pude saber como resolver. Por lo que tuve leyendo  entiendo que fue un bug de una actualizacion que realize relacionada a GNU Grub Version 1.97

GNU Grub version 1.97 ~ beta 4
[minimal bash-like editing is supported, for the first word, tab list possible command completions.anywhere else tab lists possible device/file completions.]
Sh:grub>

despues de googliar y googliar pude llegar a este post que creo es util para poder resolver el bug. les dejo la pagina 

[http://ubuntuforums.org/showthread.php?t=1398113](http://ubuntuforums.org/showthread.php?t=1398113) 

Me gustaria saber cual es la actualizacion que esta probocando este conflicto?
agradeciendo ante mano su opiniones y soluciones alternativas a este conflicto.

---

### Post by Carlos C on 2010-02-15
Parece ser un bug de grub2. Tienes que descargar el archivo "wubildr" y reemplazar el que ya tienes. Puedes entender mejor lo que te digo en este enlace:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

Saludos.

---

### Post by RafaelG on 2010-02-15
> **Carlos C said:**
> . Tienes que descargar el archivo "wubildr" y reemplazar el que ya tienes.

Esta solucion es mas Easy, gracias Carlos.
saludos...

---

