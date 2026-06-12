---
title: "No me anda FrostWire"
date: 2009-06-10
forum: Software
---

### Post by leosr on 2009-06-10
Hola.
Desde que instalé Ubuntu Jaunty no me anda FrostWire. Cuando hago click en su respectivo icono del menú, no pasa nada. Ya probé reinstalandolo y sigue sin funcionar. Bajé la última versión y tampoco anda.
Incluso instalé LimeWire, ya que Frostwire está basado en éste, y funciona sin problemas. Pero no me gusta!

Saludos.

---

### Post by luks911 on 2009-06-10
Probá de ejecutarlo en una terminal, para ver si te evuelve algún error.
¿Tenés instalado java, no?
Y por si sirve... [https://help.ubuntu.com/community/FrostWire](https://help.ubuntu.com/community/FrostWire)

---

### Post by leosr on 2009-06-10
> **luks911 said:**
> Probá de ejecutarlo en una terminal, para ver si te evuelve algún error.
¿Tenés instalado java, no?
Y por si sirve... [https://help.ubuntu.com/community/FrostWire](https://help.ubuntu.com/community/FrostWire)
Gracias por tu respuesta!
Parece que tengo una versión de Java que no es compatible con FrostWire.
```
leo@Semprom2600-desktop:~$ frostwire
HOSTNAME IS Semprom2600-desktop
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_13]
Configuring environment...
Loading FrostWire:
CLASSPATH SET TO: :./gettext-commons.jar:./foxtrot.jar:./jflac.jar:./vorbisspi.jar:./httpcore-niossl-4.0-alpha7.jar:./commons-logging.jar:./junit.jar:./onion-common.jar:./icu4j.jar:./lw-all.jar:./jcraft.jar:./commons-codec-1.3.jar:./ProgressTabs.jar:./clink.jar:./guice-1.0.jar:./tritonus.jar:./httpcore-nio-4.0-beta2.jar:./messages.jar:./themes.jar:./jl.jar:./mp3spi.jar:./jogg.jar:./jdic.jar:./jorbis.jar:./FrostWire.jar:./onion-fec.jar:./daap.jar:./looks.jar:./jdic_stub.jar:./forms.jar:./aopalliance.jar:./jaudiotagger.jar:./jmdns.jar:./jython.jar:./log4j.jar:./httpcore-4.0-beta2.jar:./httpclient-4.0-alpha3.jar
Invalid or corrupt jarfile FrostWire.jar


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0_13"
Java(TM) SE Runtime Environment (build 1.6.0_13-b03)
Java HotSpot(TM) Client VM (build 11.3-b02, mixed mode, sharing)

leo@Semprom2600-desktop:~$
```

Cómo instalo esa versión de Java? tengo que quitar la otra?

Salu2

---

### Post by luks911 on 2009-06-10
Parece que la respuesta está en la wiki que te pasé, dice:
```
Simply type in sudo update-alternatives --config java then select the alternative that includes "sun" in the name. 
```

O sea, en una terminal ejecutá

```
sudo update-alternatives --config 
```

poné tu contraseña, y elegí la opción que incluye "sun" en el nombre (no sé a qué opciones se refiere porque ahora no lo puedo reproducir en esta máquina :-S , porque tiene XP). Espero que sirva.

---

### Post by leosr on 2009-06-10
> **luks911 said:**
> Probá de ejecutarlo en una terminal, para ver si te evuelve algún error.
¿Tenés instalado java, no?
Y por si sirve... [https://help.ubuntu.com/community/FrostWire](https://help.ubuntu.com/community/FrostWire)

Como dice en el link, tengo funcionando la versión "sun" de Java.

---

### Post by luks911 on 2009-06-10
> **leosr said:**
> Como dice en el link, tengo funcionando la versión "sun" de Java.

Error mío en el post anterior. Lo que tenés que ejecutar es 

```
sudo update-alternatives --config java 
```
y después seleccionar la opción que ncluye "sun". La diferencia entre lo que necesitás es de versiones, todas son de Sun. 
Perdón por la metida de pata. Y avisá si funciona.

---

### Post by leosr on 2009-06-10
> **luks911 said:**
> Error mío en el post anterior. Lo que tenés que ejecutar es 

```
sudo update-alternatives --config java 
```
y después seleccionar la opción que ncluye "sun". La diferencia entre lo que necesitás es de versiones, todas son de Sun. 
Perdón por la metida de pata. Y avisá si funciona.

En el primer link que me pasaste decia eso y lo hice, pero sigue tirando ese error.

---

### Post by luks911 on 2009-06-10
Mmmmm.... ok
Acá[0] sugieren desisntalar Frostwire, desinstalar sun java 6, instalar el 5 (lo ecnontrás en synaptic), instalar Frostwire y dejás que al ejecutarlo se encargue de actualizar a una versión de java que le sirva.


[0] [https://answers.launchpad.net/ubuntu/+question/72805](https://answers.launchpad.net/ubuntu/+question/72805)

---

### Post by leosr on 2009-06-11
> **luks911 said:**
> Mmmmm.... ok
Acá[0] sugieren desisntalar Frostwire, desinstalar sun java 6, instalar el 5 (lo ecnontrás en synaptic), instalar Frostwire y dejás que al ejecutarlo se encargue de actualizar a una versión de java que le sirva.


[0] [https://answers.launchpad.net/ubuntu/+question/72805](https://answers.launchpad.net/ubuntu/+question/72805)
Pruebo y te cuento...

---

### Post by leosr on 2009-07-01
Les cuento que probé con todo lo que me dijeron y nada. Es más, reinstalé Ubuntu, manteniendo el /home, y sigue sin andar.
Alguna idea?

---

### Post by leosr on 2009-07-02
Lo pude solucionar... parece que no soy el único que tuvo problemas con Frostwire y Jaunty.
En el foro de Frostwire está la solución, creo que al instalarlo como root se arregla.
Dejo el link [http://forum.frostwire.com/viewtopic.php?f=1&t=6241](http://forum.frostwire.com/viewtopic.php?f=1&t=6241)

Saludos y gracias a todos.

---

