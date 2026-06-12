---
title: "Problemas con ISO de LUBUNTU, ¿Alguién sabe como grabarlo?"
date: 2010-08-20
forum: Software
---

### Post by Arlekin85 on 2010-08-20
Hola a todos, soy nuevo y tengo un problema con el ISO de Lubuntu. 
Necesitaba un sistema operativo para un Pentium 2 de 198 de RAM, y me recomendaron LUBUNTU. Lo bajé de la página oficial (Lubuntu.net), quemé la imagen en un CD pero no me funciona como disco de arranque. En Windows me aparece que este es el contenido del CD
[IMG]http://relatosdeunchascon.bligoo.com/media/users/0/33935/images/public/1201/Dibujo.JPG[/IMG]

¿Está bien el contenido? porque no tiene autoarranque como el disco de UBUNTU (que al ponerlo en el lector windows me tiraba al tiro la ventana de UBUNTU) Lo grabé más de una vez y no funciona. Incluso con el programa Daimon que crea una unidad de discos virtual para leer imágenes no funciona el autoarranque...

Alguién me puede asesorar?

Muchas Gracias

---

### Post by Carlos C on 2010-08-23
Hola. Por favor, antes de volver a publicar en el foro recuerda hacerlo en el subforo adecuado:

[http://ubuntuforums.org/showthread.php?t=1319475](http://ubuntuforums.org/showthread.php?t=1319475)

Respecto a tu duda, cuando he instalado Lubuntu me ha bastado con quemar la imagen en un cd y luego iniciar el sistema desde el disco. Verifica que el orden de booteo de tu equipo sea el correcto. En general es algo que puedes modificar desde el BIOS.

Saludos.

---

### Post by Arlekin85 on 2010-08-23
> **Carlos C said:**
> Hola. Por favor, antes de volver a publicar en el foro recuerda hacerlo en el subforo adecuado:

[http://ubuntuforums.org/showthread.php?t=1319475](http://ubuntuforums.org/showthread.php?t=1319475)

Respecto a tu duda, cuando he instalado Lubuntu me ha bastado con quemar la imagen en un cd y luego iniciar el sistema desde el disco. Verifica que el orden de booteo de tu equipo sea el correcto. En general es algo que puedes modificar desde el BIOS.

Saludos.

Gracias por tu respuesta y por tu corrección, no sabia donde publicarlo.

El booteo se hace desde el CD, pero no funciona. Pensaba que le faltaban archivos al CD ya que el de Ubuntu trae otros elementos y además se puede visualizar desde Windows, pero este no...

---

### Post by JC Cheloven on 2010-08-24
En mi .ISO hay además una carpeta de nombre [BOOT] (con los corchetes incluidos), pero a lo mejor es que win2 no te la enseña por tener caracteres raros. 

Has comprobado el md5sum de la imagen que te has bajado, y del propio disco que has tostado? Parece que se te ha grabado mal. Si es ése el problema, prueba a bajarlo otra vez, o a grabarlo con una velocidad menor.

---

### Post by Arlekin85 on 2010-08-25
> **JC Cheloven said:**
> En mi .ISO hay además una carpeta de nombre [BOOT] (con los corchetes incluidos), pero a lo mejor es que win2 no te la enseña por tener caracteres raros. 

Has comprobado el md5sum de la imagen que te has bajado, y del propio disco que has tostado? Parece que se te ha grabado mal. Si es ése el problema, prueba a bajarlo otra vez, o a grabarlo con una velocidad menor.

Gracias por tu respuesta. La verdad, lo he grabado como 3 veces a velocidad mínima pero no funciona. Incluso he grabado una imagen en mi PC y después lo he leído con una unidad de discos virtual, para evitar errores de grabado porque el CD esté malo o algo así.

No he hecho eso del md5sum, pero averiguaré que es y cómo se hace y postearé mi resultado. ;)

---

### Post by JC Cheloven on 2010-08-25
md5 crea un número largo ("suma de control") a partir de los contenidos del cd. La probabilidad de que dos discos de diferente contenido tengan la misma suma de control, es ínfima. Si ya has tostado a velocidad lenta el cd, es de suponer que la grabación es correcta. Falta por comprobar que se ha bajado bien de internet. Para ello usa el comando md5sum desde terminal:

```
yo@mipc:~$ cd /media/sitio/donde/tengo/la/ISO

yo@mipc:/media/sitio/donde/tengo/la/ISO$ md5sum lubuntu-10.04.iso

``` 
(los paths que pongo son de ejemplo, evidentemente). Pasado un rato, te aparece un número hexadecimal largo en el terminal. Es la suma de control, que tienes que comparar con la verdadera. Normalmente en el propio sitio web de la descarga te viene el md5sum verdadero para que lo compares, pero ahora mismo veo que no es el caso de lubuntu (o no lo encuentro), así que te dejo mi md5sum. Si no han cambiado la imagen, tendría que ser igual al tuyo:
386a227968cbabc89e1a23b95035160e  lubuntu-10.04.iso

EDIT: efectivamente, es que no lo encontraba yo. Están todos aquí, [http://people.ubuntu.com/~gilir/md5sum.txt](http://people.ubuntu.com/~gilir/md5sum.txt)

Saludos
JC

---

