---
title: "[Aporte] Instalar fuente 'TAHOMA NEGRITA'"
date: 2009-08-14
forum: Software
---

### Post by rafaelca on 2009-08-14
Bueno aquí copio y pego algo que me gusto y sirvio.

Tanto en Ubuntu y sus derivados, como en ArchLinux, siempre es necesario instalar un paquete de fuentes luego de la instalación normal, para que las Webs se visualicen correctamente (o al menos como el diseñador web la diseñó).

El problema que existe con estos paquetes de fuentes, es que no incluyen todas las fuentes normalmente usadas en la web, y que por ende estas se dibujan mal en la pantalla.

La fuente que, a mi parecer, es la que más hace falta es Tahoma Bold (Tahoma Negrita), tal como se indica en los correspondientes reportes de bugs de [Ubuntu]("https://bugs.launchpad.net/ubuntu/+source/msttcorefonts/+bug/50529") y [ArchLinux]("http://bugs.archlinux.org/task/12547").

Como se puede ver en esos reportes, el bug no será solucionado próximamente. Por ello, elaboré aquí una miniguía sobre como solucionar este problema.

Los pasos a seguir son:

1) Obtener la fuente correspondiente
La pueden obtener de [este enlace]("http://www.webpagepublicity.com/free-fonts/t/Tahoma%20Bold.ttf"), o del directorio Windows/Fonts de alguna instalación de Windows (el archivo se llama tahomabd.ttf)

2) Copiarla al directorio correspondiente.
En el caso de querer disponer de la fuente sólo para un usuario, debes copiar el archivo en la carpeta /home/usuario/.fonts/ (Si no existe, deben crearla). En caso de querer disponer de ella para todo el sistema, debes copiar el archivo a /usr/share/fonts

3) Refrescar la caché de fuentes.
Esto lo hacemos ingresando en una consola como root (o con sudo) y ejecutando el comando
fc-cache -vf

Esperamos un momento y listo. Todas las aplicaciones que abramos desde este momento, usarán la fuente Tahoma bold correcta. 

**Y LO HICE ASÍ:**

Baje el archivo y cree en mi usuario "home/tu_usuario/.fonts". Cree la carpeta .fonts ya que no me venia.Pero si te viene perfecto :D

Luego copie y pege la fuente ahí.

Me diriji a "Aplicaciones->Accesorios->Terminal"

Copie y pege: fc-cache -vf

Y luego en "Sistema->Preferencias->Apariencia" cambie la fonts...

Ojala te sirva :D

***FUENTE PRINCIPAL:*** [http://blog.tolaware.com.ar/2009/02/tahoma-negrita-en-linux.html](http://blog.tolaware.com.ar/2009/02/tahoma-negrita-en-linux.html)

---

