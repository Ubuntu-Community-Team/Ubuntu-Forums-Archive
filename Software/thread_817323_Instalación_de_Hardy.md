---
title: "Instalación de Hardy"
date: 2008-06-03
forum: Software
---

### Post by Vero1 on 2008-06-03
Hola,

Estoy queriendo instalar Hardy pero me han dicho que convenía hacer primero un backup de mi home.

Lo que quisiera me aclaren si es necesario pasar el backup a un CD o es suficiente grabarlo en algun otro lugar del disco, por ejemplo en Documentos nada mas.

Muchas gracias y saludos.

---

### Post by vk-cdg on 2008-06-03
Vero, no conozco la estructura de tu disco, pero al menos en la mía, la carpeta documentos está dentro del /home, así que no, no alcanzaría.

Por otro lado, el tema del backup tiene que ver con resguardar tu información por si algo llega a pasar con tus particiones al momento de instalar (lo que sea). Esto generalmente ocurre por factores humanos, es decir una metida de pata. En esos casos, toda la partición puede perderse, con lo que ello implica. Por eso la idea es "sacar" los documentos del disco. Quiero decir, hacer una copia de todo lo que te duela perder, en otro lugar que no sea el disco.

Mas allá de la instalación de una nueva versión, siempre es recomendable hacer backup periodicamente. Hace poco mas de 2 meses me tocó perder 90Gb de archivos de fotos y videos y lo lamenté bastante! En este caso fue porque el disco dijo BASTA!

---

### Post by pol666 on 2008-06-03
que feo es hacer backup en CD o DVD

lo mejor es tener un disco externo. pero yo no tengo :(

---

### Post by Vero1 on 2008-06-03
Hola vk-cdg y pol666,

pol, yo tampoco tengo :)

vk, en mi caso yo no tengo un / y un /home aparte. Todo lo tengo en /.


Realmente no tengo nada importante en el disco, ni fotos ni videos por los que muera:)

Hasta ahora he hecho upgrade de Feisty a Gutsy sin perder nada. Claro que pudo ser suerte. En cuanto al disco, es prácticamente nuevo o no tiene que ver con que en cualquier momento diga basta?

Creés que pueda intentar hacer un backup de mi Carpeta Personal que es donde está lo que me interesa y lo guarde en Documentos para tener algun resguardo o es lo mismo no hacer nada?

Gracias

---

### Post by vk-cdg on 2008-06-03
Que el disco sea nuevo, no tiene nada que ver. El mio tenía menos de 6 meses :(.
Por suerte, estaba en garantía así que mas que $1 para ir y $1 para volver...:)

Bien, yendo a tu disco si no separaste el / y el /home, entonces tu estructura está así

/
 /home
     /Vero1
          /Documentos

A menos que la carpeta documentos a la que te refieras, sea de tu disco de Windows o de otra partición. Lo que quise decirte antes, es que la carpeta documentos que vos ves en Nautilus, está dentro de tu home, que está dentro del disco donde vas a instalar ubuntu. 
En este caso es peor, ya que ubuntu te va a formatear (si hacés un clean install) todo el / y con ello el /home y todo lo que tenga adentro.
Ahora, si hacés una actualización desde la web, probablemente no pase nada, pero.... cada cual sabe cuanto quiere a sus datos.
Tené en cuenta que adentro de tu /home está la configuración y los mails del Evolution (o Thunderbird) así que eso si debe ser importante.

---

### Post by lega on 2008-06-03
Vero, podes independizar el home y moverlo una vez instalado Hardy, te dejo un tutorial muy bien explicado, yo lo hice cuando pasé de Feisty a Gutsy y me anduvo de 10 [http://tuxpepino.wordpress.com/2007/09/18/independizando-el-home/](http://tuxpepino.wordpress.com/2007/09/18/independizando-el-home/)

Saludos

---

### Post by pol666 on 2008-06-03
yo tambien tengo la /home en particion separada pero igual ahpra quiero borrar TODo y voy a tener que hacer backup U_U

---

