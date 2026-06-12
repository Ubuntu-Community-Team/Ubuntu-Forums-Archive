---
title: "Papelera de reciclaje tilda Ubuntu"
date: 2009-05-24
forum: Software
---

### Post by aledruetta on 2009-05-24
Hola Comunidad!

Ayer comenzó a suceder (o mejor dicho, ayer percibí que esto estaba sucediendo) algo extraño con mi Ubuntu Jaunty. Cuando vacío la papelera se tilda el sistema. Queda congelado, no puedo hacer nada más, ni mover el puntero del mouse.

Acontece si borro un archivo grande, una película, por ejemplo, pero también si se trata de un archivo de unos pocos kb.

Cuando pasa esto, tengo que apagar la portátil y volver a encenderla. Cuando vuelve a cargar el sistema, llega hasta un 80% más o menos y se tilda otra vez. Recién la segunda vez que apago y inicio, se carga el sistema.

No tengo idea de a qué otro suceso lo puedo vincular como para saber cuál puede ser el origen del problema.

¿Alguien tiene idea de qué puede estar causando esto?

Saludos y muchas gracias,
Alejandro.

---

### Post by pablo.s on 2009-05-24
Que FS estás utilizando?

---

### Post by juancarlospaco on 2009-05-24
Cerra todos los programas, abri una Terminal, copia y pega esto en la Terminal y dale ENTER:
[B]
sudo rm --verbose --force --recursive $HOME/.local/share/Trash/files/[/B]

---

### Post by aledruetta on 2009-05-25
Perdón, Pablo, disculpa mi ignorancia, qué es FS?

---

### Post by aledruetta on 2009-05-25
Juan Carlos,

Apliqué el comando y vació la papelera sin que se tilde el sistema. Pregunto:

1.- a partir de ahora tengo que seguir ese procedimiento siempre, o puedo volver al habitual de "vaciar papelera".

2.- además de la carpeta "file", observé que hay otras dos: "expunged" e "info" ¿esas no se tocan?

Saludos y muchas gracias,
Alejandro.

---

### Post by Hernán-Amaya on 2009-05-25
FS = File System 

te esta preguntado cual FS tenés yo uso Ext4 y anda de lujo.

---

### Post by guillermolisi on 2009-05-25
> **aledruetta said:**
> Juan Carlos,

Apliqué el comando y vació la papelera sin que se tilde el sistema. Pregunto:

1.- a partir de ahora tengo que seguir ese procedimiento siempre, o puedo volver al habitual de "vaciar papelera".

2.- además de la carpeta "file", observé que hay otras dos: "expunged" e "info" ¿esas no se tocan?

Saludos y muchas gracias,
Alejandro.
En principio y si despues de llevar a cabo el procedimiento que te aconsejaron funciona bien y estable, no haria falta que lo repitas.
La situacion por la que pasaste no es normal, algo habia en o con la papelera que producia ese problema.
Dentro de ese directorio siempre habra un par de archivos que son necesarios para su funcionamiento:
```
guille@guillermo:~$ ls -al /home/guille/.local/share/Trash
total 16
drwx------ 4 guille guille 4096 2007-11-03 16:17 .
drwx------ 9 guille guille 4096 2009-05-09 23:07 ..
drwx------ 2 guille guille 4096 2009-01-15 22:42 files
drwx------ 2 guille guille 4096 2009-01-15 22:42 info
```

---

### Post by aledruetta on 2009-05-25
Pablo,

El sistema de archivos que estoy usando es Ext4. Tengo un disco con dos particiones (/ y swap) y Ubuntu Jaunty únicamente.

---

### Post by guillermolisi on 2009-05-25
> **aledruetta said:**
> Pablo,

El sistema de archivos que estoy usando es Ext4. Tengo un disco con dos particiones (/ y swap) y Ubuntu Jaunty únicamente.
Tene especial atencion a las acciones que llevas adelante entre los consejos que se dan aqui y los que recibis de otras partes, como el Chile Team :D, ya que los de un lado no saben que aconsejan del otro y sos vos el que debe actuar con discrecion al respecto (ya que sos el que concentra toda la informacion, salvo quienes tambien lean el foro del otro team).

---

### Post by aledruetta on 2009-05-25
> **guillermolisi said:**
> Tene especial atencion a las acciones que llevas adelante entre los consejos que se dan aqui y los que recibis de otras partes, como el Chile Team :D, ya que los de un lado no saben que aconsejan del otro y sos vos el que debe actuar con discrecion al respecto (ya que sos el que concentra toda la informacion, salvo quienes tambien lean el foro del otro team).

Sí, Guillermo, entiendo, voy tratando de dar toda la información que se me ocurre que sea útil, y completando con lo que me piden en cada lugar. De todos modos, si soluciono el problema, postearé la solución en ambas comunidades para que quede a disposición de todos. Creo que de eso se trata esto de compartir el conocimiento ¿no? Y, ya que estamos, creo que es una muy buena práctica leer los post de ubuntu-ar y ubuntu-cl. Ubuntu, como lo humano, no tiene fronteras.

Saludos y muchas gracias,
Alejandro.

---

