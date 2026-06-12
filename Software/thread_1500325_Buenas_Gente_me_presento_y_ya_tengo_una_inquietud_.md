---
title: "Buenas Gente me presento y ya tengo una inquietud jajajaj"
date: 2010-06-03
forum: Software
---

### Post by JolyRecords on 2010-06-03
Hola gente como va?, les comento que soy nuevo en el foro y con Ubuntu (ahora la version mas reciente) estoy tratando de no tropezar esta vez, ya que la anterior me dió algun que otro dolor de cabeza, obviamente por lo noob que soy con Linux...

Mi primera inquietud es la siguiente, entre a youtube, instale lo que faltaba para poder ver videos flash (creo que el plugin oficial de adobe) y todo bien, salvo cuando quiero ver algun video a pantalla completa en HD (720p) porque pasa esto?... si bien mi compu tiene un chip nfoce, (integrado) en Win7 veo perfectamente los videos hd de youtube...

que puede pasar???

Les mando un abrazo, y gracias a todos

Jolyrecords

---

### Post by eliux on 2010-06-03
Te comento, tenes Ubuntu 32 o 64 bits?
 Para el caso de Ubuntu si es que es de 64 bits, olvidalo anda sacandolo y pone el de 32 porque te va a dar un dolor de cabeza. Pero si necesitas tener si o si de 64 podes seguir estos pasos para solucionar el tema del flashplayer [http://ubuntuforums.org/showthread.php?t=1486793](http://ubuntuforums.org/showthread.php?t=1486793)

Si es de 32 bits fijate en sistema-->administracion-->controladores del hardware si te aparece algun hardware restringido porque tiene codigo privativo, si es asi, dale a activar y habilitar. Deberia de funcionar.

Espero tus noticias!:P

---

### Post by alfplayer on 2010-06-03
Antes, Flash en linux era más lento que en windows. No se actualmente, pero puede seguir siendo cierto.

---

### Post by hictio on 2010-06-03
> **alfplayer said:**
> Antes, Flash en linux era más lento que en windows. No se actualmente, pero puede seguir siendo cierto.

Yo lo noto muchísimo más lento en Linux. Y no sólo lento en si, sino que en Linux el performance es realmente abismal.
Lo que hago si puedo es bajar el contenido Flash o copiarlo del cache del Firefox y reproducirlo con VLC o Movie Player (los que se pueden reproducir).

---

### Post by alfplayer on 2010-06-03
> **hictio said:**
> Yo lo noto muchísimo más lento en Linux. Y no sólo lento en si, sino que en Linux el performance es realmente abismal.
Lo que hago si puedo es bajar el contenido Flash o copiarlo del cache del Firefox y reproducirlo con VLC o Movie Player (los que se pueden reproducir).

Y con Flash 10.1 con aceleración por hardware en windows la diferencia de velocidad probablemente es mucho mayor.

---

### Post by eliux on 2010-06-04
Particularmente yo tuve el problema del firefox con flash pero con ubuntu en 64 bits, cuando me pase a 32 bits el flash funciono perfectamente, otra opcion es probar el GOOGLE CHROME comparando CHROME y FIREFOX en el uso de aplicaciones flash y animaciones, chrome tiene una marcada venaja sobre firefox.

Fijate! Saludos!

---

### Post by santiagoward2000 on 2010-06-04
> **eliux said:**
> Particularmente yo tuve el problema del firefox con flash pero con ubuntu en 64 bits, cuando me pase a 32 bits el flash funciono perfectamente

Hola!
El problema con 64 bits es que Adobe no había armado paquete para amd64 de la versión actual. Si lo instalás desde los repositorios de Ubuntu, con el paquete **flashplugin-installer**, Ubuntu te instala la versión de 32 bits, y hace que corra con un programa llamado **nspluginwrapper**.
Ahora Adobe armó una compilación de Flash para amd64, que a mí me solucionó varios problemas. Si querés probarlo, hay que desinstalar **flashplugin-installer** y **nspluginwrapper**, agregás el PPA de Flash: [https://launchpad.net/~sevenmachines/+archive/flash]("https://launchpad.net/~sevenmachines/+archive/flash")
y después instalás **flashplugin64-installer**.
Saludos!

---

