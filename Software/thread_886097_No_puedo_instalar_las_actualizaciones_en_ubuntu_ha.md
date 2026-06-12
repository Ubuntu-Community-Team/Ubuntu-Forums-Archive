---
title: "No puedo instalar las actualizaciones en ubuntu hardy!!!"
date: 2008-08-10
forum: Software
---

### Post by darkarcangel_sam on 2008-08-10
bien e aqui mis problemas:


recien antier me instale el ubuntu 8.04.1 hardy heron pormedio de wubi
desde windows , mi problema mas reciente es:

me sale el mensaje de q hay actualizaciones q contiene 93 archibos
(les debo las capturas)

bueno cuando le doy actualizar nomas se queda hai y no hace nada , ni me pide contraseña ni nada , he intentado un millon de opsiones y ninguno soluciona mi problema

mi coneccion a internet es de 56 k/s 

y en varios foros he leido q puede ser x la coneccion

y pues nada , no paso de ahi , 

nesecito saber si alguien me puede ayudar en este problema

se q a este foro solo vengo con problemas pero espero y algundia poder ayudar a los demas , mientras tansolo soy un novato q tiene 2 dias de usar ubuntu

y si alguien me puede ayudar c lo agradecere 

de antemano gracias

---

### Post by Hei Ku on 2008-08-10
que pasa si desde la consola pones:

primero:
```

sudo apt-get update

```

despues:
```

sudo apt-get dist-upgrade

```

---

### Post by darkarcangel_sam on 2008-08-10
sale lo siguiente :


dark@dark-desktop:~$ sudo apt-get update
sudo: unable to resolve host dark-desktop
[sudo] password for dark: 
Obj [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) hardy Release.gpg
Obj [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) hardy/main Translation-es
Obj [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) hardy/restricted Translation-es
Obj [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) hardy/universe Translation-es
Obj [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) hardy/multiverse Translation-es
Obj [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) hardy-updates/main Translation-es
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) hardy-updates/restricted Translation-es
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) hardy-updates/universe Translation-es
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) hardy-updates/multiverse Translation-es
Obj [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) hardy Release
Obj [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) hardy-updates Release
Obj [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) hardy/main Packages
Obj [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) hardy/restricted Packages
Obj [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) hardy/main Sources
Obj [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) hardy/restricted Sources
Obj [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) hardy/universe Packages
Obj [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) hardy/universe Sources
Obj [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) hardy/multiverse Packages
Obj [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) hardy/multiverse Sources
Obj [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) hardy-updates/main Packages
Obj [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) hardy-updates/restricted Packages
Obj [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) hardy-updates/main Sources
Obj [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) hardy-updates/restricted Sources
Obj [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) hardy-updates/universe Packages
Obj [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) hardy-updates/universe Sources
Obj [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) hardy-updates/multiverse Packages
Obj [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) hardy-updates/multiverse Sources
Leyendo lista de paquetes... Hecho
dark@dark-desktop:~$

---

### Post by darkarcangel_sam on 2008-08-10
y depues esto :


dark@dark-desktop:~$ sudo apt-get dist-upgrade
sudo: unable to resolve host dark-desktop
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Tal vez quiera ejecutar `apt-get -f install' para corregirlo.
Los siguientes paquetes tienen dependencias incumplidas:
  w32codecs: Depende: libstdc++5 (>= 1:3.3.4-1) pero no está instalado
E: Dependencias incumplidas. Pruebe de nuevo usando -f.

---

### Post by darkarcangel_sam on 2008-08-10
nesicito las actualizaciones , ayudenme x favor , de antemano gracis

---

### Post by fenT1 on 2008-08-10
saludos,

no creo que sea de mucha ayuda esta respuesta pero deberias instalarlo en la pc por completo conjunto con windows no te arrepentiras. a mi me funciona en todos los sentidos.

---

### Post by darkarcangel_sam on 2008-08-10
gracias fenT1 pero solo lo estoy probando y no es q no quiera en ubuntu , es lo q mas deseo , cambirme de S.O. pero ps tomare encuenta tu consejo en un furuto no muy lejano

pero gracias

---

### Post by fenT1 on 2008-08-10
que disfrutes, y espero que tu experiencia con linux sea una buena. en ocasiones es un poco frustrante.

---

### Post by Hei Ku on 2008-08-10
A diferencia de windows, acá los errores sirven:

> 
Tal vez quiera ejecutar `apt-get -f install' para corregirlo.


poné:
```

sudo apt-get -f install

```

y decime que te tira. Si sale todo bien, volve a probar con el segundo comando.

---

