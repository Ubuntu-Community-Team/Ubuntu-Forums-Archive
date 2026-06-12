---
title: "Borre libc6 y se me rompio Ubuntu! AYUDA!"
date: 2011-09-15
forum: Software
---

### Post by leonardo83 on 2011-09-15
Buenas compañeros, voy a ser claro: mi novia tiene en la pc instalado Ubuntu Jaunty (algo viejo pero por lo que usa esta bien).
Queria probar instalar el chat de audio/video en gmail y entonces se bajo el paquete de gmail, pero le daba errores de dependencia, mas precisamente porque no satisfacia la dependencia de libc6 (>=2.11)
Lo que hizo fue buscarlo en synaptic y no lo podia actualizar, entonces vaya a saber porque se le ocurrio borrarlo y reinstalarlo.
La macana es que mientras se desisntalaba la pantalla le quedo en gris, como que no tiene escritorio con un par de iconos locos (me conto esto por sms porque yo no estaba con ella, sino en mi casa hablandole por chat)
Lo urgente es: hay alguna forma de solucionarlo? Por favor tirenme una ayuda porque no se que es eso que borro si es tan vital que es como si hubiese borrado la carpeta system32 de win o algo asi :S
Se puede reinstalar? como? hay alguna manera de volver atras de alguna manera el sistema como un punto de restauracion o similar?
Agradecere cualquier ayuda por favos, muchas gracias :(

Adrian

---

### Post by gmunioz on 2011-09-16
Glibc es la biblioteca estándar de lenguaje C de GNU. En los sistemas Linux se instala con el nombre de libc6. Esta biblioteca de C, proporciona y define las llamadas al sistema y otras funciones básicas, es utilizada por casi todos los programas. Eliminaste el sistema nervioso de la distribución a cada versión de Debian/Ubuntu le corresponde una versión de libc6 no upgradable ni downgradable.
Intenta con un live-cd hacer un chroot del sistema instalado y reinstalar la biblioteca original de la distribución, es lo único que se me ocurre viable.

---

### Post by leonardo83 on 2011-09-16
Uuuuuh LPM!!! :( no pense era tan j****o, bueno voy a tratar de hacer eso que me decis, pero me lo podrias explicar paso a paso? pasa que no soy muy experto en esto. El cd de Jaunty lo tengo, booteo desde ahi y elijo consola? como sigo?

Desde ya te agradezco la ayuda saludos!

---

### Post by juancarlospaco on 2011-09-16
Sugiero un Upgrade de la version del SO . . .

---

### Post by gmunioz on 2011-09-16
chroot
Una vez en la terminal, de la sesión live, ejecutar:
sudo su
fdisk -l
[I](esto te mostrará como se llama la partición / del disco
supongamos sea /dev/sda1)[/I]
mkdir /mnt/ubuntu
chmod -Rf 777 /mnt/ubuntu
mount /dev/sda1 /mnt/ubuntu
mkdir /mnt/ubuntu/dev
chmod -Rf 777 /mnt/ubuntu/dev
mount --bind /dev/ /mnt/ubuntu/dev
chroot /mnt/ubuntu
*(a partir de ahora estarias trabajando en el sistema del disco)*
apt-get update
apt-get install libc6
umount /mnt/ubuntu/dev
umount /mnt/ubuntu
reboot

---

### Post by EnriqueK on 2011-09-16
Los repos de esa versión están inactivos, por lo que antes de hacer lo anterior, debés cambiar la sources,list tanto en la sesión LiveCd como el de la instalada por el siguiente.
    deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) jaunty main restricted universe multiverse
    deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) jaunty main restricted universe multiverse

    deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) jaunty-updates main restricted universe multiverse
    deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) jaunty-updates main restricted universe multiverse

    deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) jaunty-security main restricted universe multiverse
    deb-src [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) jaunty-security main restricted universe multiverse

    deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
    deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

---

### Post by mama21mama on 2011-09-17
Otra opcion es bajar el paquete en deb [http://packages.ubuntu.com/natty/libc6](http://packages.ubuntu.com/natty/libc6)

entrar en modo live, y extrar el deb.

Primero extraemos lo que hay en el deb

```
ar p *.deb data.tar.gz | tar zx
```

ahora copiamos en el lugar correcto

```
mv -f etc/ lib/ usr/ /
```

Eso debería andar también

Saludos

[Fuente]("http://www.skamasle.com/como-desempaquetar-un-deb-y-rpm-extraer-contenido-descomprimir/")

---

### Post by EnriqueK on 2011-09-17
Creo que la expresión
mv -f etc/ lib/ usr/ /
va a agregar los elementos en la / del LiveCD, estimo que debería ser algo así
sudo mv -f etc/ lib/ usr/ /media/carperta_de_montaje_de_instalació_de_Ubuntu

---

