---
title: "Como instalar OFFICE 2007 CON WINE??"
date: 2009-06-10
forum: Software
---

### Post by ceskai on 2009-06-10
Que tal amigos..!

Quería saber si alguien me puede ayudar con la instalación de office 2007. La verdad necesito instalar para trabajar en mi tesis, tengo xp tb , pero es una lata tener que trabajar en win xp.!  .. y lamentablemente en openoffice se me desconfigura todo ..! 

Se podra instalar con wine..!??? 

Bueno ojaa alguien me ayudara..! 
Saludos...

---

### Post by 3nG3ndR0 on 2009-06-10
hay muchos [tutoriales]("http://ubuntulife.wordpress.com/2008/09/26/instalando-office-2007-en-ubuntu-804/") en la red, pero de la manera que mejor me funciono fue con crossover-pro

---

### Post by moreback on 2009-06-10
Si en OpenOffice se te desconfigura todo es probable que no estés usando los poderosos estilos (párrafos, titulos, secciones, etc.) para escribir tu texto. Aparte de dejar más ordenado tu texto, te permite cambiar de fuentes y cosas así de manera más facil.

---

### Post by Iced_R on 2009-06-10
No le temas a OpenOffice, es una herramienta poderosísima que incluso hace valer hongo a Office xDDD. Y si no te acostumbras a OpenOffice, hay muchos otros programas de ofimática, como la suite de KDE, la de GNOME, Abiword, etc.

Atrévete al cambio!

Saludos.

---

### Post by AlvaroV on 2009-06-10
> **ceskai said:**
> Que tal amigos..!

Quería saber si alguien me puede ayudar con la instalación de office 2007. La verdad necesito instalar para trabajar en mi tesis, tengo xp tb , pero es una lata tener que trabajar en win xp.!  .. y lamentablemente en openoffice se me desconfigura todo ..! 

Se podra instalar con wine..!??? 

Bueno ojaa alguien me ayudara..! 
Saludos...

Me sumo yo utilizo exclusivamente openoffice y también he tenido que trabajar tesis e investigaciones de variado tipo y no tengo ningún problema, aún más lo instale en los PC del resto de mi familia y ni se han enterado que no es el office de windows:D.

Atrevase a cambiar!!

---

### Post by nopersona on 2009-06-11
> **AlvaroV said:**
> Me sumo yo utilizo exclusivamente openoffice y también he tenido que trabajar tesis e investigaciones de variado tipo y no tengo ningún problema, aún más lo instale en los PC del resto de mi familia y ni se han enterado que no es el office de windows:D.

Atrevase a cambiar!!


Haciendo mi tesis con OpenOffice 3.1 y ningún problema :p

---

### Post by CdK1 on 2009-06-11
Es mucho más recomendable una herramienta nativa que otra que no lo es... además una de las grandes herramientas de Linux es OpenOffice..., si se te desconfigura, borra su directorio y correlo de nuevo...

---

### Post by ceskai on 2009-06-15
Lo que pasa que cuando mando la tesis a corrección, los cambios devueltos no me los reconoce openoffice, y la verdad se me desconfigura mucho ,sobre todo en los pie, encabezado de paginas. Por ende se desconfigura el archivo por completo.  Nada más que por la tesis quiero instalar office. 

En unos de los tutoriales que me dejaron posteado, tengo una duda ... cuando llego al siguiente paso , 

**es hora de insertar el CD de Microsoft Office 7, o de montar la imagen iso del mismo. Para montar el CD, puedes ejecutar desde la consola un comando del estilo:** $ sudo mount -t iso9660 -o loop -o unhide /media/Descargas/Office2007Espanyol.iso /media/iso


yo tengo un cd de office , pero no se como montarlo a traves de la consola .. .. 

Saludos .

---

### Post by Carlos C on 2009-06-15
si quieres una aplicación gráfica para montar imágenes ISO puedes usar Gmount-iso. Lo encuentras en los repositorios.
Para montar desde el terminal escribes:
```
sudo mount -t iso9660 -o loop <nombre_archivo.iso> <punto_de_montaje>
```

---

### Post by ceskai on 2009-06-16
Carlos gracias por tu respuesta.  haber si entiendo 

Si tengo un iso del office en escritorio que se llama Office2007.iso, la forma seria esta?

sudo mount -t iso9660 -o loop Office2007.iso> <punto_de_montaje>
Y el punto de montaje cual seria ???  "/"  "Home" ?, si me puede ayudar con eso .. 
Gracias

---

### Post by augias on 2009-06-16
el punto de montaje es la carpeta donde encontraras el "CD". lo puedes montar donde tu quieras mientras haya una carpeta para contener los archivos del .iso. 

personalmente, y creo que es el comportamiento recomendado para ubuntu, hago el directorio para montaje en /media. esto ademas porque nautilus exhibe las cosas montadas en /media (por ej los usb) en tu escritorio.

para crear un directorio en media vas a necesitar ser super user. entras a /media por la consola con "cd /media" y luego creas la carpeta: "sudo mkdir Office2007" y finalmente el comando que te dio carlos. sudo mount -t iso9660 -o loop /home/usuario/Escritorio/Office2007.iso /media/Office2007


suerte con tu tesis! estoy en las mismas pero firme con openoffice.

---

### Post by Carlos C on 2009-06-16
> **augias said:**
> el punto de montaje es la carpeta donde encontraras el "cd". Lo puedes montar donde tu quieras mientras haya una carpeta para contener los archivos del .iso. 

Personalmente, y creo que es el comportamiento recomendado para ubuntu, hago el directorio para montaje en /media. Esto ademas porque nautilus exhibe las cosas montadas en /media (por ej los usb) en tu escritorio.

Para crear un directorio en media vas a necesitar ser super user. Entras a /media por la consola con "cd /media" y luego creas la carpeta: "sudo mkdir office2007" y finalmente el comando que te dio carlos. Sudo mount -t iso9660 -o loop /home/usuario/escritorio/office2007.iso /media/office2007


suerte con tu tesis! Estoy en las mismas pero firme con openoffice.

+1

---

### Post by ceskai on 2009-06-16
mm... Me sale que ocurrio un error en la instalcion ... 
LO que hice fue lo siguiente . 

Luego de seguir los pasos del siguiente tutorial ;[FONT=monospace]
**[http://ubuntulife.wordpress.com/2008/09/26/instalando-office-2007-en-ubuntu-804/](http://ubuntulife.wordpress.com/2008/09/26/instalando-office-2007-en-ubuntu-804/)**[/FONT]
Llegue a la parte del montaje, donde monte la imagen con el programa que me recomendo carlos. Monte la imegen en el directorio que  me dijo "augias" ( /media/Office2007) , luego le di al siguietne comando para comenzar la instalacion (wine ./setup.exe) y me sale una ventana con el siguiente mensaje. 

***el programa de instalcion no se completo correctamente.Sentimos los incovenientes ocasionados. Error al instalar, el programa de instalacion no pudo completarse***

La verdad segui los pasos tal cual estan descritos en el tutorial, pero no me resulta...

---

### Post by AlvaroV on 2009-06-17
> **ceskai said:**
> mm... Me sale que ocurrio un error en la instalcion ... 
LO que hice fue lo siguiente . 

(...)
***el programa de instalcion no se completo correctamente.Sentimos los incovenientes ocasionados. Error al instalar, el programa de instalacion no pudo completarse***

La verdad segui los pasos tal cual estan descritos en el tutorial, pero no me resulta...

Yo se en que va a terminar este thread: ** "ceskai" va decir "bueno es una pena yo quería utilizar software libre pero como quiero hacer mi tesis con office xp tendre que volver a windows".**

Entiendo que este es un foro para dar soporte a herramientas del software libre, por lo cual tengo mis dudas con respecto hasta donde llegar ayudando a usar aplicaciones privativas. Ubuntu no fue hecho para usar MS Office, sino Open Office u otra herramienta que algún desarrollador cree pensando en usarla en Linux.

Sí "ceskai" esta convencido, como parece estarlo, de las bondades extremas de MS Office o la urgencia  de finalizar su tesis lo obliga, yo le aconsejo entonces que mientras hace su tesis use Windows (previo pago de las licencias como corresponde) y luego que termine, seriamente comience de cero a cambiarse al software libre.

Es mi opinión.

---

### Post by Patriciologico on 2009-06-17
Ya que estamos dando opiniones :p Dependiendo de las caracteristicas de su "Nave" podria usar una maquina virtual en modo fluido, no es necesario reiniciar solo para correr word. En mi caso tuve un problema similar al de él y como no tengo windows en otra partición, use Virtualbox.

Saludos!

---

### Post by enano on 2009-06-22
Hola:

Para instalar Ms Office 2007 debes usar una versión un poco "antigua" de wine, cualquiera entre la 1.1.10 y la 1.1.15 (yo use esa última), desde la versión 1.1.16 en adelante se hicieron algunas regresiones en el código y la instalación del Office no se ejecuta correctamente.
En mi caso probé todas las versiones desde la actual hasta la 1.1.15 en la que como te decía la instalación funcionó perfectamente sin necesidad de instalar nada más. si tienes dudas mándame un PM y vemos como puedo ayudarte. Despúes de instalado word excel y Power corren con cualquier versión superior.

Saludos

---

