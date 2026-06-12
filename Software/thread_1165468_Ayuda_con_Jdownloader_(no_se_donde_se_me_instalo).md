---
title: "Ayuda con Jdownloader (no se donde se me instalo)"
date: 2009-05-20
forum: Software
---

### Post by elvis77 on 2009-05-20
Hola amigos, baje el programa "Jdownloader" que permite bajar varios links de rapidshare y demas sitios como ese. Me bajo una carpeta .jar, en la explicacion solo decia que habia que abrirla haciendo click derecho sobre el archivo y clickeando en "abrir con sun java 6 runtime". Hice eso y se instalo lo mas bien. El tema es que no se donde, porque una vez que cerre el programa no me aparece en ninguna de las categorias de la seccion "aplicaciones".
Alguno de ustedes podra decirme donde pudo haber guardado el programa y como encontrarlo?
Tambien me baje el "Frostwire" y tiene el mismo sistema para instalarlo y no lo instale para no seguir metiendo cosas quien sabe donde... 
Por lo general venia instalando cosas que las encontraba usando el  "añadir y quitar" de la seccion "Aplicaciones" pero estas no estaban ahi... Alguna recomendacion? Soy nuevo...

Elvis

---

### Post by sergiom99 on 2009-05-20
yo lo hacia ejecutando este comando en una consola.
```
java -jar /home/tuusuario/Jdownloader/JDownloader.jar 
```

Esto supone que lo guardaste en una carpeta Jdownloader en el home de tu usuario.

Suerte.

---

### Post by elvis77 on 2009-05-20
Que es una consola?
Tene en cuenta que soy nuevo nuevo... Donde pongo eso?

---

### Post by Mauro22 on 2009-05-20
):P


Te recomiendo Tucan [0]. Anda muchisimo mejor que JDownloader, consume menos y es nativo de linux :D


Es un deb, lo bajas, doble clic y listo. Lo tenes en el menú.



[0] [http://www.getdeb.net/app/Tucan](http://www.getdeb.net/app/Tucan)

---

### Post by elvis77 on 2009-05-20
Ok, barbaro, ahi lo estoy instalando... El tema es que me gustaria desinsatalar el JDownloader donde sea que lo haya instalado... Recien encontre una carpeta llamada JD en el equivalente a "Mis documentos"... Pero no se si borrando esa carpeta se desinstala el programa... Alguien me orienta?

---

### Post by Mauro22 on 2009-05-20
JDownloader no se instalar (bah en realidad se "instala" dentro de la misma carpeta de donde lo descomprimiste)


Vos bajaste JDownloader.rar, lo descomprimis, te queda la carpeta JDownloader... eso es todo. No hay otra cosa salvo esa carpeta. Borrala o dejala por si no te gusta Tucan.


En la carpeta JDownlader vas a ver un archivo: JDownloader.jar, ese dale clic derecho abrir con Java runtime y listo (la primera vez se "instala" en realidad se configura y la segunda en adelante lo podes usar). Pero para mi es inestable y consume mucha ram.


:popcorn:

---

### Post by rubioo on 2009-05-20
Para poder ejecutar el JDownloader, podes hacerlo desde la consola.
 Vas a Aplicaciones > Accesorios > Terminal. Y se abre una ventanita (la consola), luego tenes que escribir esto:

 ```
java -jar /home/tuusuario/Jdownloader/JDownloader.jar
```

 donde "tuusuario" es tu nombre de usuario.
 Sino, para que quede en el menú, vas a:
 Sistema > Preferencias > Menú Principal. Y ahí agregas un nuevo elemento
 (yo por ejemplo lo tengo al jdownloader en internet). Para ponerlo ahí
 en la parte izquierda vas a Internet, haces click en nuevo elemento y pones
 Tipo: Aplicacion, Nombre: JDownloader (por ejemplo), comando "java -jar /home/tuusuario/Jdownloader/JDownloader.jar" (sin las comillas) y listo.

          Saludos

---

### Post by guillermolisi on 2009-05-21
Aqui tenes un tutorial sobre como instalar JDownloader [http://ubuntu-ar.org/node/210](http://ubuntu-ar.org/node/210)

---

### Post by JOSAAX on 2010-04-24
HOLA, se me instalo el jdownloader en la carpeta usr/share , intente borrarla oara instalarlo de nuevo, pero n o me deja, es q ue cuando empieza la descarga me dice que no puede escribir en esa carpeta, y nose ya que hacer, quiero desinstalarlo para poder hacerlo de nuevo , cambiando la carpeta de instalacion para ver si asi rula, por favor decirme como lo desinstalo, gracias.

---

### Post by EGKaltenmeier on 2010-04-24
Hola gente. Intenté descargar el JD para Kubuntu (si tengo que ir a otro foro diganme a cual porque el que frecuento es este -tengo Win7, Ubuntu 9.10 y Kubuntu 9.10 en la notebook-) desde la página oficial de JD usando el Kubuntu, pero me descarga una aplicación .exe y no lo instala. De dónde lo descargo?

---

### Post by guillermolisi on 2010-04-24
> **EGKaltenmeier said:**
> Hola gente. Intenté descargar el JD para Kubuntu (si tengo que ir a otro foro diganme a cual porque el que frecuento es este -tengo Win7, Ubuntu 9.10 y Kubuntu 9.10 en la notebook-) desde la página oficial de JD usando el Kubuntu, pero me descarga una aplicación .exe y no lo instala. De dónde lo descargo?
Ya leiste el tutorial al que hago referencia en el post #8 de este thread ?

Edit: Podes complementarlo con [esto otro]("http://www.tobauntu.com.ar/2010/04/25/instalar-jdownloader-en-dos-pasos/")

---

