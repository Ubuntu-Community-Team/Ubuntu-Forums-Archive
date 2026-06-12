---
title: "Problemas con el Openoffice 3.1"
date: 2009-05-25
forum: Software
---

### Post by mano negra on 2009-05-25
Buenas,
  Les cuento con soy muy nuevo en Linux. Vengo de años de Windows.
  Mi problema es el siguiente: tengo instalado el Ubuntu 8.10. Tuve que formatear la máquina y lo instalé nuevamente. Como viene con el openoffice 2.4, lo actualicé el y justo se había lanzado el 3.1. Yo venía trabajando con el 3.0.
  La cuestión es que la versión que tengo instalada no se compara con la 3.0: la noto incompleta, los documentos que realizados con anterioridad me los habre con otra configuración o les falta cosas, cada vez que quiero abrir un archivo no me aparece la opción para buscar la ruta. Además de que está en inglés, aunque por lo que tengo entendido todavía no salieron los paquetes para pasarlo a español. 
   La instalación la hice desde el Synaptic, teniendo en cuenta, antes de actualizar los repositarios, de añadir la clave GPG para openoffice.
   Mis preguntas son:
- ¿Me está faltando instalar cosas?
- ¿Existe alguna posibilidad, si es desde los repositorios mejor, de poder instalar el openoffice 3.0?
Gracias.

---

### Post by pablo.s on 2009-05-25
> **mano negra said:**
> Mis preguntas son:
- ¿Me está faltando instalar cosas?
- ¿Existe alguna posibilidad, si es desde los repositorios mejor, de poder instalar el openoffice 3.0?
Gracias.

Hola: Existe la posibilidad de instalar
la nueva versión de OpenOffice. Un
camino es instalarlo desde los 
repositorios de Jaunty. No la recomiendo.
(Por una cuestión de sanidad del
sistema, no se si se comprende)
El camino que te va a ser más útil va a
ser desinstalar el 2.4, luego bajar el
OpenOffice 3.1 desde [el sitio oficial]("http://es.openoffice.org/") y
proceder a la instalación.
Conste que no tengo idea si hace las
entradas en los menús, pero instala
el programa en español y bien completo.

---

### Post by mano negra on 2009-05-25
> **pablo.s said:**
> 
El camino que te va a ser más útil va a
ser desinstalar el 2.4, luego bajar el
OpenOffice 3.1 desde [el sitio oficial]("http://es.openoffice.org/") y
proceder a la instalación.


  Desinstalar el 2.4 lo hice antes de poner el 3.1. 
Ahora bien, ya me lo bajé desde el sitio oficial pero no se bien como se instala. O mejor dicho, cuáles de los archivos contenidos en el .tar.gz tengo que utilizar y si luego tengo que instalar paquetes extra. Tengo entendido que en principio son los .deb, pero hay uno solo nada más.

Gracias.

---

### Post by Kleist on 2009-05-25
> **mano negra said:**
> Desinstalar el 2.4 lo hice antes de poner el 3.1. 
Ahora bien, ya me lo bajé desde el sitio oficial pero no se bien como se instala. O mejor dicho, cuáles de los archivos contenidos en el .tar.gz tengo que utilizar y si luego tengo que instalar paquetes extra. Tengo entendido que en principio son los .deb, pero hay uno solo nada más.

Gracias.

Debes de bajar el paquete .deb de esta pagina. Aqui esta la version en español. 


[http://download.openoffice.org/other.html#en-US](http://download.openoffice.org/other.html#en-US)

Para instalarlo, aquí esta una buena guía, en inglés. Si tiene poblema para entender, te puedo poner una traduccion.

[http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04](http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04)
;)

---

### Post by gmunioz on 2009-05-25
Hola man...:

Si quieres tener el Openoffice 3.1 integrado a Ubuntu y en español:

1- Desinstala desde Synaptic, de a uno todos los paquetes de Openoffice,

que no te pidan desinstalar paquetes ajenos al ooo, tales como

ubuntu-desktop  o los paquetes de idiomas, en ese caso desmárcalo y 

déjalo instalado a ese paquete conflictivo.

2- Agrega luego estos repositorios al listado de repositorios de synaptic

```
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main

deb-src http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
```

Recarga y luego cierra Synaptic

3- Baja de este link el archivo comprimido que contiene los archivos de

idioma español de ooo 3.1 en formato .deb 

```
http://www.mediafire.com/?cytyycym2b0
```

Descomprime el archivo e instala los .deb desde Nautilus con Gdebi

4- Abre nuevamente Synaptic e instala Openoffice 3.1

Este Openoffice de Ubuntu, como el de Debian, es un fork del original

depende de go-oo, que incorpora un sinnumero de funcionalidades 

descartadas por Sun en el original. Para instalar el original que has

descargado, debes colocar todos los .deb en un directorio e instalarlos

con la orden sudo dpkg *.deb, te aparecerá en el menu, pero no estará

integrado a Ubuntu y se instalara en /opt

Saludos

---

### Post by mano negra on 2009-05-25
Hice todo como índico gmunioz y no tuve ningún problema. Lo único si ya son detalles: por un lado, y me pasaba antes, no se me instaló el ícono general de openoffice y no puedo cambiar el estilo en la configuración (más que nada los íconos).
  Saludos y gracias ya por lo anterior.
  Después si me pueden decir ésto último buenísimo.

---

