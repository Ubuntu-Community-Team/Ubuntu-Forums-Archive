---
title: "No puedo escribir en sistema de archivos"
date: 2009-08-11
forum: Software
---

### Post by Z!ro on 2009-08-11
Primero perdo si poste en un lugar que no corresponde...
bueno volviendo al tema por el que creo este post, no puedo escribie en la particion en la que instale Ubuntu (Sistema de archivos), no permite crear, modificar ni eliminar archivos. ademas cuando algun programa treata de crear un temporal no puede

[IMG]http://fotos.subefotos.com/79e5346727cec6fd9458b9a02974105ao.png[/IMG]

si alguien me ayuda se lo agradesere, mientras estoy tratando de arreglerlo o configurarlo no se exactamente cuna es el preblema y si es un problema

PD: alguien me explicaria como hacer un Spoiler en este foro

---

### Post by josecuervo86 on 2009-08-11
Hoa Z!ro, primero que nada estaria bueno que explicaras cual es la tarea que intentas realizar, ya que nos da mas pistas de que puede pasar. Intuyo que estas tratando de modificar algo sin permisos de usuario.

---

### Post by Z!ro on 2009-08-11
ok entiendo... cuando ejecuto cualquier aplicacio me aparese que no se puede crear algun archivo...
no se como explicarlo, EJ: trato de cambiar el skin del AMSN pero no puedo pegar una carpeta dentro de la carpeta de Skins del Amsn ni crear, otra cosa no me deja cambiar el escritorio (si no explique bien) tengo Gnome y no puedo canviar a KDE cuando lo trato de iniciar me dice que no puede estar mal instalado (ya desistale y reinstale los paquetes) o que puede que no tenga espasio suficiente (el espacio me sobra tengo 28G libres) solo puedo modificar el contenido de las carpetas perosnales...
eso es lo que me pasa agrandes rasgos

---

### Post by josecuervo86 on 2009-08-11
Claro, es que justamente sin permisos de usuario, solo podes modificar los archivos personales, nada mas. Para modificar el sistema de archivos (lease; lo que no es la carpeta personal) necesitas permisos de usuario. La forma mas facil de hacer esto es abrir una terminal y poner:

```
sudo nautilus
```

Esto te abre un navegador de archivos, pero con permisos de root, que te permite modificar cualquier archivo del sistema. Pero ojo, tene cuidado que tocas!!

---

### Post by Z!ro on 2009-08-12
muchas gracia, aunque e podido modificar los archivos dentro del directorio Raiz, no e podido poner KDE como queria, i sigo teniendo problemas con los temporales de los programas...
en fin e cambiado a kubuntu
donde es:

```
sudo konqueror
```para el navegador com privilejios (si no Hubieras puesto el nautilus nunca lo hubiera buscado)

te agradesco mucho

---

### Post by josecuervo86 on 2009-08-12
Una forma de probar KDE seria mediante la instalación del desktop de kubuntu. El comando seria:

```
sudo apt-get install kubuntu-desktop
```

Eso te instala el escritorio KDE de kubuntu, pero te aviso que los menus te quedan hechos una chanchada, porque te agrega las aplicaciones de KDE a los menus de Gnome.
Una vez instalado podrias acceder desde la ventana de inicio de sesión.

---

