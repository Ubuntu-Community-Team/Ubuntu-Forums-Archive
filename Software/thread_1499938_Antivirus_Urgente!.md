---
title: "Antivirus Urgente!"
date: 2010-06-02
forum: Software
---

### Post by manaxchan on 2010-06-02
Hola, necesito instalar con urgencia un antivirus en las computadores del ciber cafe que manejo. Se que es muy dificil que un virus se cole en una de ellas, pero una cliente ya me trajo uno y se envia automaticamente por emesene =/.
Podrían por favor recomendarme uno y decirme como instalarlo?
Muchas gracias.

---

### Post by ubuntu27 on 2010-06-02
Antivirus para Windows? 

Te recomiendo que instales [Avast! Antivirus]("http://www.avast.com/free-antivirus-download"), es gratuito y funciona bien ^^

[http://www.avast.com/free-antivirus-download](http://www.avast.com/free-antivirus-download)


**EDIT:** Oh, ok. Para Linux? Usa [Clam Antivirus]("http://www.clamav.net"). Esta en el repositorio. Busca "clam" en Gestor de Paquetes Synaptic

---

### Post by capcabgue on 2010-06-02
> **manaxchan said:**
> Hola, necesito instalar con urgencia un antivirus en las computadores del ciber cafe que manejo. Se que es muy dificil que un virus se cole en una de ellas, pero una cliente ya me trajo uno y se envia automaticamente por emesene =/.
Podrían por favor recomendarme uno y decirme como instalarlo?
Muchas gracias.
Hola manaxchan:
Podrías dar a conocer un poco mejor las características de tu ciber.
Suponiendo quet tienes Ubuntu, puedes instalar avg (hay una versión especial para linux) en el momento de chequear los archivos lo debes hacer por consola (revisa el manual de avg para ver los parametros que debes incluir).
Bueno si no te gusta avg también te recomiendo avast, si quieres saber como instalarlo aqui te dejop un link:
[B][http://www.exaquo.com/instalar-avast-antivirus-en-ubuntu-gutsy/](http://www.exaquo.com/instalar-avast-antivirus-en-ubuntu-gutsy/)

Suerte
[/B]

---

### Post by asterix77 on 2010-06-02
Yo he instalado el avast que posee una versión para sistemas basados en debian.
Acá dejo un link donde hay un tutorial de como instalarlo.

En dicha página indican como se instala en un sistema de 64 bit; si es para sistemas de 32 bit, solo hay que modificar el paso n°4, quedando de la siguiente forma.

sudo dpkg -i  avast4workstation_1.3.0-2_i386.deb


[http://www.tecnohispanos.com/principal/2010/01/25/como-instalar-avast-4-para-linux-en-ubuntu-9-10/](http://www.tecnohispanos.com/principal/2010/01/25/como-instalar-avast-4-para-linux-en-ubuntu-9-10/)

Saludos

---

### Post by manaxchan on 2010-06-04
Ok, muchas gracias. Seguire todos sus consejos y luego les cuento como me fue.
Con respecto al ciber... bueno lo tenemos al día de hoy con Ubuntu 10.04 se que es un poco arriesgado, ya que es demasiado nuevo, pero al día de hoy andamos bastante bien con el
Además usamos control de ciber y la impresora anda genial.
Solo me queda resolver el tema del antivirus.
Gracias.

---

### Post by manaxchan on 2010-06-04
Chicos les cuento que tengo el problema de que el sistema es 32 bits, y la librería de Avast es para 64 bits... estuve buscando de donde bajarlo, ya que tampoco me deja instalar el paquete ia32libs desde la terminal =/.
Ojala puedan ayudarme.
Gracias

---

### Post by asterix77 on 2010-06-07
No entiendo tu problema.

¿quieres instalar avast en máquinas de 32 ó 64 bits? 

**y la librería de Avast es para 64 bits...**  Hasta donde sé Avast está disponible solo para arquitecturas 32 bits, por lo que no creo que venga Avast con librerias de 64.

**ya que tampoco me deja instalar el paquete ia32-libs desde la terminal  =/.**

El paquete ia32-libs está en los repositorios oficiales de ubuntu, por lo que no entiendo porqué no te deja instalarlo, solo debes ejecutar en la terminal

#sudo apt-get install ia32-libs

...y listo


Saludos

---

### Post by ubuntu27 on 2010-06-08
> **manaxchan said:**
>  un cliente ya me trajo uno y se envia automaticamente por emesene =/.
P

Yo sospecho que tu makina no esta infectada por un virus o otro malware. Mas bien como el esta usando emsene es muy posible que los amigos de tu cliente (contactos en emesene) son los que estan infectados y le envian archivos e textos automaticamente al cliente. 

Esto es normal cuando una interactua con amigos que usan Windows y el protocolo MSN o MSN Live.

---

### Post by manaxchan on 2010-06-08
> **asterix77 said:**
> No entiendo tu problema.
 
¿quieres instalar avast en máquinas de 32 ó 64 bits? 
 
**y la librería de Avast es para 64 bits...** Hasta donde sé Avast está disponible solo para arquitecturas 32 bits, por lo que no creo que venga Avast con librerias de 64.
 
**ya que tampoco me deja instalar el paquete ia32-libs desde la terminal =/.**
 
El paquete ia32-libs está en los repositorios oficiales de ubuntu, por lo que no entiendo porqué no te deja instalarlo, solo debes ejecutar en la terminal
 
#sudo apt-get install ia32-libs
 
...y listo
 
 
Saludos
 
Bueno mis maquinas son de 32 bits, mejor les agregare los errores que me lanza al hacerlo por la terminal. Porque no me deja instalarlos u.u.
No creo que influya que tengo ubuntu 10.04 cierto?

---

### Post by asterix77 on 2010-06-08
Bueno, si tus máquinas son de 32 bits, solo debes instalar el paquete deb solamente, ya que el resto que aparece en el link es para aquellos que tienen arquitecturas de 64 bit.

Busca la carpeta donde tengas el archivo avast...deb, dale doble click para que empiece la instalación y listo. Si faltan depedencias, automáticamente se descargarán. El acceso por defecto queda en Aplicaciones -------->Accesorios -------->Avast.


Saludos

PD: No tiene nada que ver que la versión sea la 10.04, yo lo tengo instalado tanto en mi notebook (64 bit), como en mi pc de escritorio (32 bit), ambos con 10.04

---

### Post by RafaelG on 2010-06-10
> **manaxchan said:**
> bueno lo tenemos al día de hoy con Ubuntu 10.04 se que es un poco arriesgado, ya que es demasiado nuevo


Disculpa,

Que tiene de arriesgada la Version 10.4 LTS? 

Podrias entregar mas antecedentes del virus que tuviste con esta version, alcansaste a crear algun Thread en forum o Launchpad con referencia a este virus! como lo resolviste?

Por otro lado los usuarios del cyber ingresan como super user o como usuario con restriciones?

---

