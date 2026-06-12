---
title: "Problemas en la consola :-("
date: 2009-01-01
forum: Software
---

### Post by Cristiandley on 2009-01-01
Hola que tal, Soy Cristian y tengo 16 años. Hace mas de 3 años uso Linux...no como sistema principal pero me gusta entrar casi siempre para descubrir y aprender mas.
 Hace un tiempo instale ubuntu 8.04 (Lo descargue como en junio del '08 pero lo instale 1 sola vez y lo borre). Ahora volvi a instalar, ya que estoy en pleno verano. Y he encontrado juegos magnificos para correr bajo linux, como el American Army y el Savage. Me descargue los dos juegos (La version 1 y 2 del Savage también), pero vi que no es lo mismo que instalarlo en WindozZzZz.... Vi que hay que usar la consola, y la verdad...he probado con mil y una combinaciones jeje.
 porbe con:
 
$ sudo sh xxxxx_xxxx.bin
$ sudo ./xxxxx_xxxx.bin
 
y en una web econtre que habia que utilizar esta (para savage 2)

chmod +x Savage2Install-1.5.0-i686.bin
./Savage2Install-1.5.0-i686.bin

Pero la verdad que me canseee. Ya no se mas que hacer.... siempre me salta lo mismo, miren:

cristian@cristian-desktop:~$ sudo chmod +x Savage2Install-1.5.0-i686.bin
chmod: no se puede acceder a «Savage2Install-1.5.0-i686.bin»: No existe el fichero ó directorio
cristian@cristian-desktop:~$ chmod +x Savage2Install-1.5.0-i686.bin
chmod: no se puede acceder a «Savage2Install-1.5.0-i686.bin»: No existe el fichero ó directorio
cristian@cristian-desktop:~$ $ sudo sh savage_linux.sh
bash: $: orden no encontrada
cristian@cristian-desktop:~$ sh./Savage2Install-1.5.0-i686.bin
bash: sh./Savage2Install-1.5.0-i686.bin: No existe el fichero ó directorio
cristian@cristian-desktop:~$ sh./Svage2Install-1.5.0-i686.run
bash: sh./Svage2Install-1.5.0-i686.run: No existe el fichero ó directorio
cristian@cristian-desktop:~$ chmod +x Savage2install-1.5.0-i686.bin
chmod: no se puede acceder a «Savage2install-1.5.0-i686.bin»: No existe el fichero ó directorio
cristian@cristian-desktop:~$ 

Bueno, gracias por la ayuda que pueda recibir de antemano y un FELIZ AÑO NUEVO PARA TODOS.

Atte. Cristian D. L.

---

### Post by Hei Ku on 2009-01-01
Simplemente te dice que no encuentra ese archivo. 
Seguro que esta en tu escritorio? 
Seguro que es el mismo nombre, y no por ejemplo todo en minusculas?

---

### Post by Cristiandley on 2009-01-01
si :S esta en mi escritorio. Hasta he tratado de moverlo a otras carpetas a ver si me lo lee...o que...
 Pero es algo muy raro, o soy muy novato...o me anda mal la consola.

 Yo ingrsé todos los comando que hay por la red y que he encontrado. Lo extraño es que los de instalacion siempre me sale eso...
O me pide mi clave de usuario y luego, salta el error de que no se puede ejecutar

EDITO: Probe en ponerlo en minuscula, pero nada. Verifique todo.. :( :( :( pero nada

---

### Post by Hei Ku on 2009-01-01
Probá de hacer lo siguiente. Escribí "sudo chmod +x Sav" y después apretá Tab. Debería completar el nombre. O hacer un beep, en cuyo caso apretá Tab otra vez. Posteá lo que te salga.

---

### Post by Hei Ku on 2009-01-01
Probá de hacer lo siguiente. Escribí "sudo chmod +x Sav" y después apretá Tab. Debería completar el nombre. O hacer un beep, en cuyo caso apretá Tab otra vez. Posteá lo que te salga.

---

### Post by Cristiandley on 2009-01-01
Gracias por responder :)

SI, mira, lo hice. Puse lo que me dijiste y aprete TAB pero no sucedio nada, ni un BEEP :(  Y probe de darle Enter y ahi salio error...era de suponerse por que no tenia el nombre completo. (si quiera se completo el nombre)

Terminal

cristian@cristian-desktop:~$ sudo chmod +x Sav
chmod: no se puede acceder a «Sav»: No existe el fichero ó directorio
cristian@cristian-desktop:~$ 
cristian@cristian-desktop:~$

---

### Post by Hei Ku on 2009-01-01
Seguro que el archivo está ahí? 
Donde lo bajaste? En tu escritorio, como hace el Firefox? 
Porque el comando lo estas ejecutando en tu home, que NO es la misma carpeta de tu escritorio. Es como Mis Documentos y Escritorio en Windows, dos cosas diferentes.

---

### Post by Cristiandley on 2009-01-01
Mira ahi pongo una imagen, si, lo baje desde firefox y esta en el escritorio el archivo.

Por eso me llama la atencion... Lo mismo me pasa con el AMerican's Army y el Savage 1.. 

Aca te dejo una imagen, te confirmo que lo tengo en el escritorio de Ubuntu.

[[IMG]http://img231.imageshack.us/img231/4543/pantallazofw8.png[/IMG]](http://imageshack.us)


Es algo demasiado extraño...yo penaba hasta ayer que pudiese ser un Bug en mi sistema quizas...

---

### Post by luks911 on 2009-01-01
Entonces es lo que te decía Hei-Ku, el archivo está en tu escritorio pero vos estás ejecutando los comandos en tu home.
Abrí una terminal y hacé
```
cd Escritorio
```
y después sí ejecutás los comandos.

PD: te odié por poner esa imagen, de ese tamaño, en ese lugar. :lolflag:

---

### Post by luks911 on 2009-01-01
Editado: se duplicó el post.

---

### Post by Cristiandley on 2009-01-01
Ahhh mira ahi te entendi...o sea el Home no es el escritorio encontes.

A donde tengo que llevar ese archivo ?

Disculpa las molestias

---

### Post by luks911 on 2009-01-01
Todo bien. Podés moverlo a tu home o dejarlo donde está. Eso depende de vos.
Pero si lo dejás donde está, antes de ejecutar comandos para modificar sus permisos o lo que sea que lo afecte tenés que moverte hacia donde está el achivo. En este caso, como te decía,
```
cd Escritorio
``` respetando la mayúscula.
Otro comando que puede ser útil en estos casos es 
```
ls
``` similar al dir en win y que va a listar el contenido de la carpeta en la que estás. Para ver sus opciones
```
ls --help
```
¿Te dice que no encuentra el archivo? Ejecutás ls y lo buscás en el listado, aunque si te dice que no está, no está, je.

---

### Post by Cristiandley on 2009-01-01
Jeje, si seré.....

Muchas gracias che ! A los 2 10000 gracias jejeje

Saludos y suerte

Atte. Cristian

EDITO: Ahi me lo instalo, aunque ahora el juego se abre y se cierra jejej

---

### Post by Hei Ku on 2009-01-01
> **Cristiandley said:**
> Mira ahi pongo una imagen, si, lo baje desde firefox y esta en el escritorio el archivo.

Por eso me llama la atencion... Lo mismo me pasa con el AMerican's Army y el Savage 1.. 

Es algo demasiado extraño...yo penaba hasta ayer que pudiese ser un Bug en mi sistema quizas...

No, simplemente estas buscando el archivo en el lugar equivocado. PBKAC.

---

