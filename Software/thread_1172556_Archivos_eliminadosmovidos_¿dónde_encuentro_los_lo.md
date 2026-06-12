---
title: "Archivos eliminados/movidos ¿dónde encuentro los logs?"
date: 2009-05-28
forum: Software
---

### Post by telefono on 2009-05-28
Buenos días, les cuento que ante-ayer, por algún curioso motivo de la existencia me han desaparecido miles de fotos viejas. Si, toda mi infancia desapareció. Eran dos carpetas, dentro de un disco NTFS montado desde mi XUBUNTU 9.04

Luego de investigar por internet, utilicé el Photorec quien me ayudó a recuperar varias de esas imagenes.

Ahora bien, siempre me quedó la intriga de ¿qué pasó con esos archivos? ¿cómo desaparecieron las dos carpetas magicamente? Cabe destacar, que hace meses no utilizo windows (ni siquiera lo booteo), por lo cual descarto cualquier posibilidad de virus. Más que nada, me aferro a la posibilidad, que alguien al querer ver las fotos, haya movido/eliminado las dos carpetas sin querer, aunque me parece raro.

Por lo cual, y he aquí mi pregunta, ¿dónde se encuentran los Logs de los archivos movidos/eliminados? Si estos no existen, ¿existe algún log de las transacciones NTFS de parte del fuse? ¿El nautilus maneja esa clase de Logs?

Desde ya, muchas gracias,

y saludos a todos! ; )

---

### Post by Mauro22 on 2009-05-28
Lo del log no lo sé.

Pero en la web oficial, dentro de los FAQs:

```
Missing, disappeared files or directories?
or 
Why can't I see all filenames with national characters?
or 
Why do I get "Skipping unrepresentable filename (inode XXXXX) ..." messages?
If the top directory is completely empty then it's very probably that the NTFS volume is not mounted. 

If only some files are missing then please upgrade to at least NTFS-3G 2009.1.1 which has full, built-in Unicode UTF-8 conversion support. 

If you use Mac OS X or FreeBSD and have at least one very long filename with national characters and the filename length translates into more than 255 UTF-8 bytes (higher chance with Korean and Greek languages) than Mac OS X and FreeBSD will not show any files in the directory.
```


```
Archivos o directorios perdidos, faltantes?
o
[...]

Si la raiz esta vacia, es porque el volumen no se montó.

Si algunos archivos se perdieron, por favor actualice a la ultima version (2009.1.1), la cual tiene soporte para la conversion Unicode UTF-8
[...]
```


Lo unico que se me ocurre, es que los archivos tenian nombres invalidos?? segun eso... xD

---

### Post by telefono on 2009-05-28
Gracias por responder, **Mauro22**, 

desgraciadamente no es mi problema, ya que solía ver la carpeta correctamente desde mi ubuntu. Además, desde Windows la carpeta no aparece más. Por lo que deduzco esta fue movida/eliminada accidentalmente. 

Intenté de todos modos buscarla con el clásico Find, sin lograrlo.

Por lo cual, y tras haber recuperado varios archivos con el Photorec, lo único que me resta hacer es averiguar el por qué del suceso. 
Por ello he acudido aquí, a ver si alguien sabe dónde se guardan los logs de las transacciones de archivos, particularmente las realizadas través del NTFS.

Otra duda: ¿El nautilus maneja un log de las acciones de los usuarios?

Pd: Hasta ahora, lo único que he podido hayar es un log del bash. Pero allí no hay respuesta para mi cuestión.

Desde ya gracias,

Atte.

---

### Post by pablo.s on 2009-05-28
Suena que querés
averiguar QUIEN te
borró las carpetas,
no QUE te borró las
carpetas...
¿Estoy en lo cierto?

---

### Post by telefono on 2009-05-28
Jajaja, no para nada; sólo me gustaría ver en 'papel' qué es lo que pasó con los archivos xDD

---

### Post by guisheca on 2009-05-29
Veras, voy a sonar un poco (o mucho) extremista con lo que te voy a decir, pero yo no pongo nada de valor en una partición NTFS o cualquiera que sea de M$ no me fio de nada de lo que ellos hagan. Igual esto no sirve ahora ya que lo que se perdio hay que tratar de recuperarlo.
El [testdisc]("http://www.cgsecurity.org/wiki/TestDisk") (que es lo que usa el photorec si mal no me acuerdo) me salvó una ves, igual te recomiendo que no hagas operaciones de escritura en ese disco hasta que hayamos agotado las posibilidades de recuperar algo. El testdisk esta en los repositorios, y hay que usarlo con mucho cuidado porque podes romper todo para siempre. Igual, se supone que el photorec es un testdisk específicamente para fotos asi que no se.
Lo unico que te aconsejo es que, si tenés algo mas de valor en esa partición, lo saque de ahí a una partición como la gente o a un medio de almacenamiento optico, etc.
Saludos.

---

### Post by telefono on 2009-05-29
Hola** guisheca**, si tampoco yo estoy de acuerdo en utilizar NTFS, sucede que aún no tuve tiempo de migrar completamente. Gracias por los consejos, sin embargo ya utilicé exitosamente el Photorec, y recuperé si bien no la mayoría, casi todo lo más importante. 

Gente, ¿Alguno sabe si hay logs o no? Estamos en linux, yo estimo que debe haber... pero...

Gracias : D

---

### Post by Hei Ku on 2009-05-29
no, probablemente a traves de AppArmor puedas activarlos, pero no hay logs de ese tipo de cosas. Archivos se crean y borran todo el tiempo, salvo que tengas una razon en particular, es un desperdicio de recursos loguear eso.

---

### Post by telefono on 2009-05-31
Gracias :)

---

### Post by infernus92 on 2009-05-31
esto seguramente se les ocurrio a muchos ya... y me van a tratar de o algo parecido...
pero no puede ser que este oculto a tu usuario por alguna extraña razon??

se me ocurre q podrias poner en la carpeta donde deberia estar la(s) carpeta(s) con las fotos 

```
sudo ls -a
```

o

```
sudo ls -A
```

para ver si en realidad esta pero no se muestra...

Saludos

PD: aunque con el find creo que deberia haberlo mostrado...

---

