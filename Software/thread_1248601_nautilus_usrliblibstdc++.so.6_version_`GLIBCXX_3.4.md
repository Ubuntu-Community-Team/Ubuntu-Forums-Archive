---
title: "nautilus: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.9' not found"
date: 2009-08-24
forum: Software
---

### Post by JaM0N on 2009-08-24
Buenas tardes, éste es mi primer post en éste foro, si me he equivocado por favor enseñenme :D

Resulta que por algún motivo (aún no se como sucedió) no funciona ni el nautilus ni apt-get y, por el error, ninguna otra aplicación que utilize el libstdc++.so.6

busqué y busqué y no logro hacer andar esto

Algunos intentos infructuosos:
> 
$ ldconfig -p |grep libstdc++

         libstdc++.so.6 (libc6) => /usr/lib/libstdc++.so.6
         libstdc++.so.6 (libc6) => /usr/local/lib/libstdc++.so.6
$ diff /usr/lib/libstdc++.so.6 /usr/local/lib/libstdc++.so.6
   Binary files /usr/lib/libstdc++.so.6 and /usr/local/lib/libstdc++.so.6
differ
The two files are different which means there are two different versions gcc
in the system? I found a gcc directory under /usr/local

Then : $ cat /etc/ld.so.conf.d/libc.conf
# libc default configuration
/usr/local/lib

I added /usr/lib to the file and then run :
$sudo ldconfigno hace ninguna diferencia

```
export LD_LIBRARY_PATH=/usr/lib/:${LD_LIBRARY_PATH}
```no parece hacer nada

```
ln -s libstdc++.so.6.0.9 /usr/local/lib/libstdc++.so.6
```crea el symlink pero de ahi en mas es todo igual (de hecho el symlink siempre estuvo)

```
root@gaspar-desktop:/usr/lib# ls libstd*
libstdc++.so.5  libstdc++.so.5.0.7  libstdc++.so.6  libstdc++.so.6.0.9

``````
root@gaspar-desktop:/usr/lib# cat /etc/ld.so.conf.d/*
# Multiarch support
/lib/i486-linux-gnu
/usr/lib/i486-linux-gnu
# libc default configuration
# /usr/local/lib
/usr/lib
# libc default configuration
# /usr/local/lib

```ESTO ESTÁ RARITO

```
root@gaspar-desktop:/usr/lib# cat /etc/ld.so.conf.d/libc.conf
# libc default configuration
# /usr/local/lib
/usr/lib

```eso lo modifiqué yo para provar... si descomento y borro /usr/bin todo sigue igual

Bueno... espero que alguien pueda ayudarme... sin apt-get no se como hacer para arreglar esto :(

---

### Post by JaM0N on 2009-08-24
BUMP

Vamos por favor alguien!

Todavia no puedo iniciar nautilus, alguien tiene que saber de que se trata esto :'(

---

### Post by Hei Ku on 2009-08-24
Lo que no contas es que hiciste antes de esto.
De hecho lo estas corriendo como root, lo que ya me resulta raro. Tuviste que habilitar explicitamente, algo que no se recomienda.

Y los BUMP son uno por dia como máximo, no cada 7 horas.

---

### Post by JaM0N on 2009-08-24
Perdón por el bump

Antes de eso estaba instalando programas de cnc y provandolos, pero instale varios (ya ni recuerdo bien cuáles), el último fue el [camvox]("http://camvox.sourceforge.net") y antes el [sagcad]("http://sagcad.sourceforge.jp/").

Con respecto a lo de root fué porque primero lo hize como usuario y luego al no poder solucionarlo intenté nuevamente como root (quien sabe... "en una de esas").

Pongo los links de donde saqué la información:

[http://ubuntuforums.org/showthread.php?t=941309](http://ubuntuforums.org/showthread.php?t=941309) [ éste parece tener el mismo problema que yo, pero haciendo lo que hizo él no se arregla. ¿Talvez tenga que hacer un paso intermedio? ]
[http://www.murga-linux.com/puppy/viewtopic.php?t=31007&sid=4705cf40664ff68faae047c574161852](http://www.murga-linux.com/puppy/viewtopic.php?t=31007&sid=4705cf40664ff68faae047c574161852) [ éste tiene otro problema, pero es con la misma libreria ]
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=914618](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=914618) [ figura como solucionado, pero hago lo mismo y no resulta ]

Gracias

---

### Post by Hei Ku on 2009-08-24
Postea el error exacto que te tira

---

### Post by JaM0N on 2009-08-24
```
gaspar@gaspar-desktop:/media/disk/www/CAD$ nautilus
nautilus: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.9' not found (required by /usr/lib/libexempi.so.3)
gaspar@gaspar-desktop:/media/disk/www/CAD$ apt-get
apt-get: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.9' not found (required by apt-get)
apt-get: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.9' not found (required by /usr/lib/libapt-pkg-libc6.7-6.so.4.6)
gaspar@gaspar-desktop:/media/disk/www/CAD$ synaptic 
synaptic: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.9' not found (required by synaptic)
synaptic: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.9' not found (required by /usr/lib/libapt-pkg-libc6.7-6.so.4.6)
synaptic: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.9' not found (required by /usr/lib/libapt-inst-libc6.7-6.so.1.1)

```

Ese es el error cuando quiero correr nautilus (1), apt-get (2) o synaptic (3)

---

### Post by Hei Ku on 2009-08-24
En este punto, ni idea. Probaste mas de lo que se me hubiera ocurrido a mi.

---

### Post by josecuervo86 on 2009-08-24
Por lo que encontre en Google, has hecho todo lo que hicieron aquellos a los que le sucedio exactamente lo mismo. Lo raro es que a ellos si les funciono :???:

---

### Post by JaM0N on 2009-08-24
Y si en lugar que use las librerias  libstdc++.so.6 hago que utilize las  libstdc++.so.5? eso se podria??? luego así con el apt-get podría reinstalar o verificar dependencias o lo que fuere. Que opinan?

---

### Post by Hei Ku on 2009-08-24
No, probablemente no funcione.

Es de los pocos en los que te recomendaria reinstalar, si es una opcion. Y nunca mas tocar las bibliotecas a mano. Para eso esta el apt-get :D

---

### Post by JaM0N on 2009-08-24
Bueno :( y cual seria otra opción? o el procedimiento para reinstalar (no soy un gurú de compilar, pero voy a hacer lo mejor que pueda)

Cabe destacar que no fui yo quien se cargó las librerias, fue algun desliz de uno de esos programas. Tambien cabe destacar que agradezco mucho su ayuda :D

---

### Post by JaM0N on 2009-08-24
Por si es de ayuda:

```
gaspar@gaspar-desktop:/media/disk/www/CAD$ sudo ldconfig -p | grep stdc
    libstdc++.so.6 (libc6) => /usr/lib/libstdc++.so.6
    libstdc++.so.5 (libc6) => /usr/lib/libstdc++.so.5
```

---

### Post by JaM0N on 2009-08-24
Perdón por la seguidilla de posts, pero es que estoy averiguando y posteo cosas que puedan ser de utilidad.

Aparentemente el problema es en realidad que no tengo esta biblioteca actualizada, como que me falta la ultima version (el GLIBCXX_3.4.9 que pide cada vez que ejecuto nautilus y que es requerida por libexempi.so.3)
```
gaspar@gaspar-desktop:/media/disk/www/CAD$ strings /usr/lib/libstdc++.so.6.0.9 | grep GLIBCXX
GLIBCXX_3.4
GLIBCXX_3.4.1
GLIBCXX_3.4.2
GLIBCXX_3.4.3
GLIBCXX_3.4.4
GLIBCXX_3.4.5
GLIBCXX_3.4.6
GLIBCXX_3.4.7
GLIBCXX_3.4.8
GLIBCXX_FORCE_NEW
gaspar@gaspar-desktop:/media/disk/www/CAD$ nautilus
nautilus: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.9' not found (required by /usr/lib/libexempi.so.3)

```

:'(

---

### Post by josecuervo86 on 2009-08-24
Probaste con este: [http://ubuntuforums.org/showthread.php?t=808045](http://ubuntuforums.org/showthread.php?t=808045)

---

### Post by JaM0N on 2009-08-24
Si, acabo de intentar pero no logro ningún resultado (ni positivo ni negativo)

Ahora estoy pensando en recompilar el gcc pero no se... me da cosita :$... necesito un empujon, como tengo que ejecutar el configure y no se.... la verdad que todo lo que compile hasta ahora fueron zandeses...

Ya me descarge el gcc_4.4.1 ... pero me parece que voy a tirar la toalla...
Creo que es una viktory para Don Bash ...
Cuando tenga tiempo reinstalo ubuntu :( por primera vez en 2 años consecutivos y continuos de pruebas y errores; de meter mano, romperla y arreglarla; de instalar, desinstalar y reinstalar; es impresionante que haya durado tanto...

[SIZE=3]**10** Estrellas sobre 5 para [B]GNU/Linux :guitar:
[/B][/SIZE]

---

