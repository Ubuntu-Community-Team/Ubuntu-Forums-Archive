---
title: "Gmail Drive"
date: 2009-01-20
forum: Software
---

### Post by emiliano_raso on 2009-01-20
Alguien sabe como instalarlo en linux?

Encontre en internet que hay que instalar lo siguiente:
> sudo aptitude install gmailfs

Y luego montarlo modificando segun los datos personales con este comando:
> sudo mount -t gmailfs /usr/local/bin/gmailfs.py /DIRECTORIODEMONTAJE -o username=NOMBREDEUSUARIO,password=CONTRASEÑA,fsname=zOlRRa

Pero me dice lo siguiente y no hace nada:
> Ignored option :rw
fuse: bad mount point `/media/gmail': No such file or directory
Traceback (most recent call last):
  File "/sbin/mount.gmailfs", line 166, in <module>
    main(mountpoint, namedOptions, useEncfs)
  File "/sbin/mount.gmailfs", line 92, in main
    gmailfs.main(mountpoint, namedOptions)
  File "/usr/lib/python2.5/site-packages/gmailfs.py", line 1180, in main
    server.main()
  File "/usr/lib/python2.5/site-packages/fuse.py", line 713, in main
    main(**d)
fuse.FuseError: filesystem initialization failed



Alguien sabe que pasa? U otra forma de instalarlo mas facilmente?
Desde ya gracias.

NOTA: Tengo Ubuntu Intrepid Ibex 8.10 en una notebook Acer Aspire 5710-4900

---

### Post by guillermolisi on 2009-01-20
> **emiliano_raso said:**
> Alguien sabe como instalarlo en linux?

Encontre en internet que hay que instalar lo siguiente:


Y luego montarlo modificando segun los datos personales con este comando:


Pero me dice lo siguiente y no hace nada:


Alguien sabe que pasa? U otra forma de instalarlo mas facilmente?
Desde ya gracias.

NOTA: Tengo Ubuntu Intrepid Ibex 8.10 en una notebook Acer Aspire 5710-4900
Buscando esto en Google encontre algo que podria darte una pista:

[http://www.linuxforums.org/forum/debian-linux-help/44852-gmail-drive-linux.html](http://www.linuxforums.org/forum/debian-linux-help/44852-gmail-drive-linux.html)

Si pones "gmail drive linux" en Google veras cantidad de sugerencias, comentarios y casos relacionados con el tema.

---

### Post by emiliano_raso on 2009-01-21
Gracias por responder.

Y si si... ya busque en google a morir, pero la mayoria no funcionan.
Ese link que me pasaste es uno de los que probe y no funcionaron xD

---

### Post by guillermolisi on 2009-01-21
> **emiliano_raso said:**
> Gracias por responder.

Y si si... ya busque en google a morir, pero la mayoria no funcionan.
Ese link que me pasaste es uno de los que probe y no funcionaron xD

Mira, hace un tiempo atras, un año mas o menos, quise usar esta facilidad en una maquina con WinXP y nunca anduvo. Indagando un poco creo haber leido que este servicio lo habian desactivado, cosa que contradice aparentemente a las opiniones que aparecen en los resultados de una busqueda en Google.

El asunto es que nunca lo pude hacer andar, asi que lo desestime.

---

### Post by sergiom99 on 2009-01-21
en XP (viene pre-instalado con WinUE) funciona bien.
Jamas puede hacerlo andar en Ubuntu. Es mucho mas complicado porque hay que tocarlo en fstab y nunca me quedo bien.

---

### Post by emiliano_raso on 2009-01-22
Yo instale WIndows UE en la otra maquina y lo vi (no sabia que existia) y tampoco lo pude hacer andar xD Aunqe  no le dedique mucho tiempo siendo sinceros...

Segui buscando en internet pero sigo encontrando siempre lo mismo y nadie uqe haya logrado hacerlo mas que el OP

---

### Post by guillermolisi on 2009-01-22
[respuesta_off_topic]
WinUE no trae Gmail drive preinstalado, es una opcion que se selecciona o deselecciona en tiempo de instalacion de los agregados que esta distribucion tiene.
[/respuesta_off_topic]

Bueno, casualmente fue con WinUE 7 que hice una de las pruebas (la anterior fue con un WinXP Pro) y nunca funciono. A raiz de ello investigue via Google y lei que lo habian desactivado.

---

### Post by emiliano_raso on 2009-01-23
Ha! Descativaron Gmail Drive?
Dato interesante xD Jajaja...

Gracias por la informacion :-P

---

### Post by guillermolisi on 2009-01-25
> **emiliano_raso said:**
> Ha! Descativaron Gmail Drive?
Dato interesante xD Jajaja...

Gracias por la informacion :-P
Trata de confirmar eso ya que he visto cantidad de comentarios en Internet, mas o menos recientes, que hablan como si funcionara (en realidad la gran mayoria solo dice como hacer para configurar el Gmail Drive, nada mas). Para mi, por lo que recuerdo que lei despues de haberme quemado las pestañas tratando de hacerlo funcionar, no esta mas disponible.

---

### Post by sergiom99 on 2009-01-27
Les confirmo que en XP sigue funcionando, con la última versión [1]
Recién subí 3 archivos de 15Mb cada uno.
Suerte!

[1] [http://www.viksoe.dk/code/gmail.htm](http://www.viksoe.dk/code/gmail.htm)

---

### Post by fencer on 2009-01-27
> **emiliano_raso said:**
> Gracias por responder.

Y si si... ya busque en google a morir, pero la mayoria no funcionan.
Ese link que me pasaste es uno de los que probe y no funcionaron xD

Lo hice funcionar pero el unico problema es que al montarlo con el sudo solo me dejaba entrar como root en el drive, asi que lo desmonté... estoy buscando la manera de que funcione como un drive normal

---

### Post by alcarraz on 2010-11-12
Please tell us how you did it. Share your knowledge.

thanks

Andrés

---

### Post by mama21mama on 2010-11-12
gmail drive seria como el que viene en ubuntu como se llama?
ptm olvide su nombre :confused:

---

### Post by sys.adm.og on 2010-11-13
> **fencer said:**
> Lo hice funcionar pero el unico problema es que al montarlo con el sudo solo me dejaba entrar como root en el drive, asi que lo desmonté... estoy buscando la manera de que funcione como un drive normal

Lo montas desde el fstab? Si es asi con umask=0777 en la linea donde montas lo solucionas!
Saludos

---

