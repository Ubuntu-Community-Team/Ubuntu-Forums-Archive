---
title: "Usuarios de Debian denme una mano."
date: 2008-10-09
forum: Software
---

### Post by ramiro_md on 2008-10-09
Gente, bueno posteo esto acá porque el foro de debian-ar.org no estaba disponible.
La cuestión es que instale debian etch en una partición. Los temas fundamentales de mi port son los siguientes:
1) Cómo actualizo de kde 3.5 a 4.1 ?
2) Cómo obtener las fuentes de win, como "comic sans"...es la que uso en emesene :)
3) Cuando quiero acceder a la partición de ubuntu desde "equipo" me tira el siguiente error: "hal-storage-
fixed-mount refused uid 1000".
Bueno por ahora eso solo jejej.Gracias. Un saludo.

---

### Post by leo_rockway on 2008-10-09
> **ramiro_md said:**
> 
1) Cómo actualizo de kde 3.5 a 4.1 ?

En Etch no se puede. Etch es estable, KDE4.x no.
EDIT: podés intentar instalar el backport de Lenny, pero probablemente tengas problemas de dependencias.

> **ramiro_md said:**
> 
2) Cómo obtener las fuentes de win, como "comic sans"...es la que uso en emesene :)

Me imagino que en non-free, pero no estoy seguro porque no uso non-free.

---

### Post by ramiro_md on 2008-10-09
Okas, gracias leo por la info. Un saludo

---

### Post by leo_rockway on 2008-10-09
Te dejo el enlace a los backports de KDE4 para Lenny [0]. Igualmente cabe aclarar que si no estás en un entorno de producción estricto entonces Lenny es suficientemente estable y es muy recomendable migrar. Y si estás en un entorno de producción estricto o en un servidor... entonces no instales KDE4, jaja.
KDE4 está cada día mejor, pero para un entorno que necesita estabilidad a cualquier costo no es recomendable.

[0] [http://kde4.debian.net/](http://kde4.debian.net/)

---

### Post by Vera_ on 2008-10-10
> 2) Cómo obtener las fuentes de win, como "comic sans"...es la que uso en emesene 
Yo uso Ubuntu, y para alguans fuentes que necesito existe un paquete que se llama *msttcorefonts*. Vienen las siguientes fuentes:

    * Arial
    * Andale Mono
    * Comic Sans MS
    * Courier New
    * Georgia
    * Impact
    * Verdana
    * Times New Roman
    * Trebuchet MS
    * Webdings

Para instalarlo, en la consola de Debian pones el siguiente comando:
```
apt-get install msttcorefonts
```
Durante la instalación te sale como una especie de acuerdo, lo aceptas y listo. ;)

Un saludo,
Vera.

---

### Post by ramiro_md on 2008-10-10
Leo, entonces voy a ver si cambio a Leny xq la uso como pc de escritorio nomás. Y estoy usando para probar :)
Vera, ese paquete no está en debian :S ya lo intenté instalar x synaptic y aptitude.

---

### Post by EnriqueK on 2008-10-10
Nunca usé Debian, pero en Ubuntu cuando quiero tener una fuente .ttf de Windows, simplemente la copio a la carpeta fonts, tendrías que ver donde ubica Debian esa carpeta, ahora Ubuntu la ubica en /usr/share , seguramente para que esté disponible para todos los usuarios, antes la tenía como carpeta oculta dentro del directorio del usuario.
Resumiendo, si a esas fuentes las tenés en Ubuntu, las copiás y las llevás a la carpeta fonts de Debian.

---

### Post by pol666 on 2008-10-10
yo uso Testing pero generalmente mezclo repositorios con sid.

no tuve problemas de dependencias, para nada. 100% estable

---

### Post by ramiro_md on 2008-10-10
BUeno muchachiiios, el tema de las fuentes lo solcuioné copiando la carpeta /usr/share/fonts/truetypes/msttcorefonts de ubuntu a debian.
Y lo de las particones "ubuntu" y "datos" lo colucionè a medias, porque pude montar tranquilamente la partcion ext3 de ubuntu pero no asì la de datos (ntfs). Cuando quiero entrar con konqueror a la ntfs me dice "no se pudo entrar a la carpeta /mnt/datos".
Bueno un saludoo !!.

---

### Post by ramiro_md on 2008-10-10
Solucioné el tema de la particon ntfs. Le di "chmod -R 777 /mnt/datos" y ya puedo navegar tranquilo x el disco, reproducir mp3 ver fotos. Lo unico es que no em deja modificar nada. Me estoy comiendo algun parametro en el chmod ?. Un saludo.

---

### Post by sebastianabate on 2008-10-12
Pegá el contenido de tu /etc/fstab, para ver con qué opciones se está montando tu partición NTFS.

Básicamente si el type es ntfs lo vas a poder usar como solo lectura únicamente, si es ntfs-3g podés usarlo como lectura/escritura. No sé si en Debian viene por defecto ntfs-3g, en ubuntu sí.

---

