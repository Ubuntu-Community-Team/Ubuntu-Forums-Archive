---
title: "problema con mi HD externo"
date: 2010-03-07
forum: Software
---

### Post by shini-kire on 2010-03-07
mi problema que no me monta el disco pero me lo reconose :/ pero no esta en /media mire aqui pegue mi sudo fdisk -l

```
Disco /dev/sda: 80.0 GB, 80026361856 bytes
255 cabezas, 63 sectores/pista, 9729 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x04ed04ec

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extendida
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disco /dev/sdc: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x3a093a09

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdc1               1       19457   156288321   83  Linux
```

uso ubuntu karmic koala 9.10 y uso 2 navegadores de archivos nautilus y dolphin antes el anutilus me lo montaba pero despues dejo de aparecer mi disco externo y me lo mostraba el dolphin pero ahora no aparece en niuno :( porfavor help!!

---

### Post by shini-kire on 2010-03-08
REsuelto: pasos

1 paso:
```
"sudo mkdir /media/virtual"
```

2 paso:

```
"sudo chmod 777 /media/virtual"
```

3 paso:

```
 sudo mount -t sistema_de_archivo /dev/sdb1 /media/virtual -o defaults
```

4 Paso:

```
 ls /media/vistual 
```

-----------------------------------------------------------------

5 Paso:

```
"sudo umount /media/virtual"
``` Para desmontar y desconectar el Dico externo

y deveria ver los datos ahi. Sacada la info en :

Fuente: [http://www.plurk.com/shnk3](http://www.plurk.com/shnk3)

---

### Post by cool2k on 2010-03-08
:)

---

### Post by Carlos C on 2010-03-08
Muevo el post y lo doy como resuelto. Por favor recuerda leer [aquí]("http://ubuntuforums.org/showthread.php?t=1319475") antes de volver a publicar.

Gracias por decir como lo solucionaste.

Saludos!

---

### Post by shini-kire on 2010-03-08
> **Carlos C said:**
> Muevo el post y lo doy como resuelto. Por favor recuerda leer [aquí]("http://ubuntuforums.org/showthread.php?t=1319475") antes de volver a publicar.

Gracias por decir como lo solucionaste.

Saludos!

no problem, somos una comunidad tenemos que ayudarnos o no? ;)

y gracias por avisarme no me fije el subforo 

saludso!

---

### Post by shini-kire on 2010-03-08
> **Carlos C said:**
> Muevo el post y lo doy como resuelto. Por favor recuerda leer [aquí]("http://ubuntuforums.org/showthread.php?t=1319475") antes de volver a publicar.

Gracias por decir como lo solucionaste.

Saludos!

no problem, somos una comunidad tenemos que ayudarnos o no? ;)

y gracias por avisarme no me fije el subforo 

saludso!

---

