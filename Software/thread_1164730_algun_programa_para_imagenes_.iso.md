---
title: "algun programa para imagenes .iso?"
date: 2009-05-19
forum: Software
---

### Post by soujiro_valk on 2009-05-19
hola
eso, que programa me recomiendan para gestionar los .iso?

nos vemos

---

### Post by moreback on 2009-05-19
Ubuntu ya viene con **Brasero** para quemar las .iso y creo que el mismo **Gestor de archivadores** te permite mirar dentro de estos archivos.

---

### Post by pagondel on 2009-05-19
Hola Soujiro!

```
sudo aptitude install gmountiso
```

Saludos! 8)

---

### Post by Patriciologico on 2009-05-19
```
sudo aptitude install gmountiso
```

;) me gane un beans

Saludos!

---

### Post by 3nG3ndR0 on 2009-05-20
yo uso un scripts para nautilus que es muy bueno, solo click derecho en la iso seleccionamos el scripts MountISO y listo, para desmontar es o mismo pero con la unidad montada, si te interesa

en el terminal:

```
$ gedit ~/.gnome2/nautilus-scripts/MountISO
```agregar

```
#!/bin/bash
#script via TheeMahn
sudo umount /media/ISO
for I in `echo $*`
do
  foo=`gksudo -u root -k -m "enter your password for root terminal
access" /bin/echo "got r00t?"`
sudo mkdir /media/ISO
sudo mount -o loop -t iso9660 $I /media/ISO
done
```

---

### Post by rodrigovb-cl on 2009-05-20
Y como vamos dejar afuera una solución para consola:

```
sudo mount -t iso9660 -o loop archivo.iso /directorio/de/montaje
```


Y ya que estamos, **para montar NRG:**

```
mount -t iso9660 -o loop,offset=307200 imagen.nrg /directorio/de/montaje
```


**BIN y CUE**

Instalar bchunk para convertilos primero a iso

```
sudo apt-get install bchunk
```

Convertir a ISO

```
bchunk archivo.bin archivo.cue nuevonombre.iso
```

Y hacerlo como ya dijimos.


**Para montar IMG **

Instalamos ccd2iso

```
sudo apt-get install ccd2iso
```

Pasamos a ISO:

```
ccd2iso imagen.img imagen.iso
```

Y ya saben el resto.

Saludos,

---

### Post by CarlosRuiz on 2009-05-20
Holap:

Te recomiendo K3B... es increiblemente bueno:
**sudo apt-get install k3b**

Saludooos :p

---

