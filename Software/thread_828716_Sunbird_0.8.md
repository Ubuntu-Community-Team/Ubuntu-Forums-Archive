---
title: "Sunbird 0.8"
date: 2008-06-14
forum: Software
---

### Post by Applelnx on 2008-06-14
Como el sunbird mas nuevo no estaba en los repositorios quise instalarlo manualmente. Me baje el paquete, lo compile a un .deb con un scrpti que habia pasado sajnox y lo instale. El problema es que el sunbird no me aparece en ningun menu. Cuando ejecuto el comando sunbird me dice que no lo encuentra.

Les dejo una screen del synaptic a ver si les dice algo ... :s

[[IMG]http://img505.imageshack.us/img505/7638/sunbirdxx2.th.png[/IMG]](http://img505.imageshack.us/my.php?image=sunbirdxx2.png)

---

### Post by _kAz_ on 2008-06-14
A mi me paso exactamente lo mismo pero con el Songbird, supuestamente lo tengo instalado en la máquina, pero desde que lo puse lo pude ver únicamente esa vez y nada más, después desapareció sin dejar rastros :(

---

### Post by clasificado on 2008-06-14
y si le dan un 
```
whereis nombredelprograma
```
?

---

### Post by Thalskarth on 2008-06-15
> **_kAz_ said:**
> A mi me paso exactamente lo mismo pero con el Songbird, supuestamente lo tengo instalado en la máquina, pero desde que lo puse lo pude ver únicamente esa vez y nada más, después desapareció sin dejar rastros :(

Con el songbird... no hace falta instalarlo.
O sea, bajate el archivo comprimido de la página... lo descomprimis... y dentro de esa carpeta, hay un archivo llamado "songbird"... lo ejecutas (doble click).. y listo. ahi arranca el songbird sin dramas...

---

### Post by Applelnx on 2008-06-17
Hola de nuevo. En contre una guia donde explicaba como instalar el sunbird 0.7 y lo probe para el 0.8:

# Download Sunbird 0.7 from here.
# Run these commands in your terminal:

```
sudo tar zxvf sunbird-0.7.en-US.linux-i686.tar.gz -C /opt/
sudo chown -R root:root /opt/sunbird/
sudo chmod -R 755 /opt/sunbird/
```

# Create GNOME menu item:
```

sudo gedit /usr/share/applications/sunbird.desktop
```

Then add:

```
[Desktop Entry]
Encoding=UTF-8
Name=Sunbird
Comment=Calendar application
Exec=/opt/sunbird/sunbird
Icon=/opt/sunbird/icons/mozicon128.png
Terminal=false
Type=Application
Categories=Application;Network;
StartupNotify=true
```

Pero no funciono :(
Alguien tiene idea de lo que hice y como volver atras :confused:

---

### Post by faktorqm on 2008-06-17
y... ahi lo instalaste digamos, y luego hiciste una entrada en el menu (de todas maneras eso mejor se hace desde el menu principal en sistema -> administracion)
Lo que pasa es que eso ya esta preocmpilado, vos lo tenes que compilar, si ya lo compilaste, proba con ejecutar /usr/bin/nombre_del_programa a ver que pasa desde una consola. Probaste el whereis? locate tambien podes usar. Tambien find. Si no decime y me lo instalo yo, lo hago andar y te aviso como se hace. Salu2!

---

### Post by Applelnx on 2008-06-21
Quedo instalado en opt/sunbird

Cuando trato de ejecutar el binario del sunbird me dice:
```

./sunbird-bin: error while loading shared libraries: libmozjs.so: cannot open shared object file: No such file or directory
```

:confused::confused:

---

### Post by Hei Ku on 2008-06-21
te fijaste si existe esa libreria?

whereis libmozjs.so

---

### Post by Applelnx on 2008-06-22
> **Hei Ku said:**
> te fijaste si existe esa libreria?

whereis libmozjs.so

No existe. Me fije en synaptic si habia algun paquete con ese nombre pero no, hay otros parecidos.

libmozjd0d
libmozjd0d-dbg
libmozjd0d-dev

Son de Mozilla SpiderMonkey

---

### Post by Hei Ku on 2008-06-22
proba de instalarte el paquete libmozjs0d, a ver que pasa.

---

### Post by Applelnx on 2008-06-22
> **Hei Ku said:**
> proba de instalarte el paquete libmozjs0d, a ver que pasa.

No pasa nada, sigue sin encontrarlo :s

---

### Post by Hei Ku on 2008-06-22
sabes lo que son los symbolic links?
podes probar de crear uno en la carpeta del sunbird a la carpeta donde quedo instalado el libmozjs.

si no sabes, pone cuales son las dos carpetas, y te decimos como hacerlo.

---

### Post by Applelnx on 2008-06-23
No, la verdad que me mataron. El libmozjsz0d no lo encuentro. Mejor espero a que lo suban al repositorio y listo :$

---

