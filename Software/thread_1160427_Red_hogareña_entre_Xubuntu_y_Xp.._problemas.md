---
title: "Red hogareña entre Xubuntu y Xp.. problemas"
date: 2009-05-15
forum: Software
---

### Post by harryscode on 2009-05-15
Hola, de no haber visto más que screenshots de ubuntu, decidí el día que salio Ubuntu 9.04 instalarle a una pobre viejita el Xubuntu 9.04. Es decir, no tengo ni idea de linux. Pero estoy más que contento con el cambio. La cuestión es la siguiente. Quise ponerlas en red, tengo un SmartAX MT882, la Xp conectada con USB al modem y la Xubuntu con el cable de red al modem. Después de investigar, leer y demás, logré ponerlas en red. Desde Xp puedo ver la carpeta compartida que tengo en Xubuntu, pude compartir la impresora que esta conectada a la última pero no puedo ver desde Xubuntu la conexión de red a Xp. No encuentro el lugar donde diga Sitios de Red o algo parecido. Todo el proceso de configuración de red lo hice con el Samba. No se si pueden ayudarme para ver como puedo hacer para ver los archivos de la Xp desde Xubuntu o que me falta hacer para verlos.
Desde ya muchas gracias.

---

### Post by guillermolisi on 2009-05-15
> **harryscode said:**
> Hola, de no haber visto más que screenshots de ubuntu, decidí el día que salio Ubuntu 9.04 instalarle a una pobre viejita el Xubuntu 9.04. Es decir, no tengo ni idea de linux. Pero estoy más que contento con el cambio. La cuestión es la siguiente. Quise ponerlas en red, tengo un SmartAX MT882, la Xp conectada con USB al modem y la Xubuntu con el cable de red al modem. Después de investigar, leer y demás, logré ponerlas en red. Desde Xp puedo ver la carpeta compartida que tengo en Xubuntu, pude compartir la impresora que esta conectada a la última pero no puedo ver desde Xubuntu la conexión de red a Xp. No encuentro el lugar donde diga Sitios de Red o algo parecido. Todo el proceso de configuración de red lo hice con el Samba. No se si pueden ayudarme para ver como puedo hacer para ver los archivos de la Xp desde Xubuntu o que me falta hacer para verlos.
Desde ya muchas gracias.
En Windows tenes que compartir algun recurso, un disco, un directorio/carpeta, una impresora, algo que tenga que publicar en la red para que Xubuntu la vea.

Mis Sitios de Red de Windows deberia estar por lo menos en Panel de Control si no lo ves en el escritorio (eso se puede configurar para que se vea).

---

### Post by harryscode on 2009-05-15
> **guillermolisi said:**
> En Windows tenes que compartir algun recurso, un disco, un directorio/carpeta, una impresora, algo que tenga que publicar en la red para que Xubuntu la vea.

Mis Sitios de Red de Windows deberia estar por lo menos en Panel de Control si no lo ves en el escritorio (eso se puede configurar para que se vea).

Gracias por la respuesta. Tengo una carpeta en Xp compartida y una carpeta en Xubuntu compartida.. En Xp puedo ver esa carpeta pero no así en Xubuntu. Y a lo que me refería con mis sitios de red (creo que entendi eso) no era en Xp sino en Xubuntu, no encuentro ningun lugar donde fijarme si hay una red o no. No se si me explico. No encuentro el equivalente a mis sitios de red en Xubuntu. Probe con Carpetas compartidas del menu Sistemas, Visor de Escritorios remotos del menu Red, en el escritorio tampoco aparece una red o algo así. No se que datos necesitan saber para poder darme una mano. Gracias de todos modos.

---

### Post by milovan1971 on 2009-05-15
Podes solucionar eso facil (sin tener que usar el terminal si no te gusta) con nautilus... pero no lo tenes disponible en xubuntu. nautilus es el manejador de archivos de gnome, el escritorio de ubuntu. 
Podes instalarlo desde Aplicaciones>Sistema>Gestor de paquetes synaptic
Pone tu clave, busca "nautilus" en Busqueda rapida, y selecciona para instalar  "nautilus" (gestor de archivos) y "nautilus-share" (extension para compartir carpetas por samba). 
Y asi lo haces con la terminal: $ sudo apt-get install nautilus nautilus-share

Una vez que este instalado, escribi "nautilus --no-desktop" en la terminal (o mejor, create un lanzador en el escritorio de Xfce), se abre nautilus, vas a Archivo>Conectar con el servidor....
te aparece una ventanita donde podes elegir Tipo de servicio: pones Compartido por windows.... y en Servidor pone el nombre del equipo windows (la identidad de red)... y listo! te aparecen las carpetas compartidas!
Avisa si te funciono.

---

### Post by ADICTOALMAXIMO on 2009-05-16
Yo quiero lo mismo pero entre ubuntu y xp (y ubuntu y ubuntu) si alguien tiene un link gracias

---

### Post by Hei Ku on 2009-05-16
> **ADICTOALMAXIMO said:**
> Yo quiero lo mismo pero entre ubuntu y xp (y ubuntu y ubuntu) si alguien tiene un link gracias

Si lees atentamente, podes ver que la solucion propuesta usa Nautilius que es el explorador de Ubuntu, asi que te sirve para Ubuntu.

---

### Post by harryscode on 2009-05-16
> **milovan1971 said:**
> Podes solucionar eso facil (sin tener que usar el terminal si no te gusta) con nautilus... pero no lo tenes disponible en xubuntu. nautilus es el manejador de archivos de gnome, el escritorio de ubuntu. 
Podes instalarlo desde Aplicaciones>Sistema>Gestor de paquetes synaptic
Pone tu clave, busca "nautilus" en Busqueda rapida, y selecciona para instalar  "nautilus" (gestor de archivos) y "nautilus-share" (extension para compartir carpetas por samba). 
Y asi lo haces con la terminal: $ sudo apt-get install nautilus nautilus-share

Una vez que este instalado, escribi "nautilus --no-desktop" en la terminal (o mejor, create un lanzador en el escritorio de Xfce), se abre nautilus, vas a Archivo>Conectar con el servidor....
te aparece una ventanita donde podes elegir Tipo de servicio: pones Compartido por windows.... y en Servidor pone el nombre del equipo windows (la identidad de red)... y listo! te aparecen las carpetas compartidas!
Avisa si te funciono.

De lujo milovan.. muchas gracias.. todo funciona perfecto. Quede medio descolgado con el lanzador en el escritorio (no tengo mucho tiempo usando linux ubuntu) pero investigando lo pude hacer. Una cosa más que se aprende. Muchas Gracias.

Cada vez más fundamentalista de Ubuntu.

---

### Post by ADICTOALMAXIMO on 2009-05-16
PERDON NO ME HABIA FIJADO

GRAcias

---

### Post by milovan1971 on 2009-05-16
> **harryscode said:**
> De lujo milovan.. muchas gracias.. todo funciona perfecto. Quede medio descolgado con el lanzador en el escritorio (no tengo mucho tiempo usando linux ubuntu) pero investigando lo pude hacer. Una cosa más que se aprende. Muchas Gracias.

Cada vez más fundamentalista de Ubuntu.

Me alegro que haya funcionado. Yo tambien soy medio nuevo... pero avido de aprender!
Suerte!

---

