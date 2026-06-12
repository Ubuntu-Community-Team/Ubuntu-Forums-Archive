---
title: "¿Lxde?"
date: 2009-03-05
forum: Software
---

### Post by erdosain9 on 2009-03-05
Hola a todos.  quería saber si alguien conoce algo sobre esto de lxde... no tengo una super máquina... ubuntu hardy va bien... pero quería saber si esto del LXDE podría hacer que fuera más rápido y que cosas cambiarían...
un saludo y gracias

---

### Post by NickCis on 2009-03-05
Mira, Lxde, es un escritorio como Gnome, Kde y Xfce. Usa como window manager a Openbox, tiene una barra propia Lxdepanel que parte del pearpanel (me parece), y su gestor de archivos es PcmanFm.

Usa, muy pocos recursos, y el escritorio no es tan feo. En un principio, creo qe no vas a tener transpariencias y cosas asi.

Esta el pagina de Lxde: [http://www.lxde.org/](http://www.lxde.org/)

Y viene con estos programas:
```

Components

PCManFM
    The ultimate fast and robust file manager. It provides tabbed file browsing and desktop icons with low system resource usage.
LXPanel
    Feature-rich yet user-friendly desktop panel providing most crucial functions you expect from a desktop panel. Configuration is done through a graphic user interface.
LXSession
    Standard-compliant X11 session manager with shutdown/reboot/suspend supports via HAL and gdm (LXSession Lite is a stripped-down lightweight version without X11 session management support, and it's more stable).
LXSession Edit
    The standard session edit manager, with ability to turn on disabled applications in LXDE.
LXAppearance
    LXAppearance is a new feature-rich GTK+ theme switcher able to change GTK+ themes, icon themes, and fonts used by applications.
LXLauncher
    LXLauncher enables the desktop to have topic oriented desktops.
Openbox
    Lightweight, standard-compliant, and highly-configurable window manager (adapted by LXDE. We suggest using this as default window manager.). This can be replaced by any other window manager like icewm, fluxbox, metacity, ...etc.
GPicView
    A very simple, fast, and lightweight image viewer featuring immediate startup.
Leafpad
    Lightweight and simple text editor adapted by LXDE. (We suggest using this as default text editor.).
LXDE Common
    LXDE Common is the default settings configuration file for integrating the different components of LXDE. LXDE Common manages the system behavior and functions to integrate icons and artwork.
LXTerminal
    Desktop-independent VTE-based terminal emulator for LXDE without any unnecessary dependency (All instances share the same process to reduce memory usage).
XArchiver
    Lightweight, fast, and desktop-independent gtk+-based file archiver (adapted by LXDE. We suggest using this as as default archiver).
LXRandR
    Monitor configuring tool. You can plug in another screen into LXDE or choose to use a big screen projector. Local screen and extenal screen can be used at the same time. LXRandR configures the screen solution automatically. 
LXNM
    Lightweight network connection manager. LXNM is a helper daemon for LXDE supporting wireless connections (Linux-only).
LXMusic
    The minimalist XMMS2-based music player.
GtkNetCat
    Graphic User Interface for netcat. Netcat provides system functions as a computer networking utility for reading from and writing to network connections on either TCP or UDP. 
```

Saludos.

---

### Post by totolinux on 2009-03-05
Hola mirá lo uso en un pentium II en la maquina de mi hijo lo instale desde los repositorios en ubuntu 8.04 y va mas rapido que gnome ademas PcmanFm esta muy copado y es rápido, aparece todo preconfigurado y  tuneadito con fondos de pantalla propios y muy organizado el menú. yo conforme. saludos

---

### Post by erdosain9 on 2009-03-05
Muchas gracias por contestar... lo instalé siguiendo esta página:

[http://arbolcharyou.es/2008/06/30/instalar-entorno-lxde-desde-repositorios/](http://arbolcharyou.es/2008/06/30/instalar-entorno-lxde-desde-repositorios/)

Me ha gustado pero quiero tener la posibilidad de regresar a lo anterior... cómo se hace para volver... pensé que se podía elegir uno u otro sistema... cómo hago para volver a lo anterior o para convertir esto en una opción a elegir (si es posible).

Saludos y gracias

---

### Post by erdosain9 on 2009-03-05
mmm... perdón por preguntar al ****... ya vi como se hace: Ctrl + Alt + retroceso.  Ahí en opciones elegir sesión y luego Gnome...
Pero no conocía las otra opciones... podrían explicármelas (no quiero tocar y tal vez provocar algún error).

Gracias...

---

### Post by guillermolisi on 2009-03-06
> **erdosain9 said:**
> mmm... perdón por preguntar al ****... ya vi como se hace: Ctrl + Alt + retroceso.  Ahí en opciones elegir sesión y luego Gnome...
Pero no conocía las otra opciones... podrían explicármelas (no quiero tocar y tal vez provocar algún error).

Gracias...
En realidad cuando tecleas Ctrl+Alt+Backspace estas reiniciando el servidor X que permite el funcionamiento del escritorio grafico.

Algo equivalente pero menos rustico (y mas seguro) es cerrar la sesion que tenes abierta con LXDE y luego proceder con la eleccion del escritorio grafico que tengas instalado y gustes usar para una nueva sesion de usuario.

---

### Post by sloggerkhan on 2009-03-06
Me gusta lxde. Creo que es mas sencilla user y configurar de fluxbox y tambien usa menos recursos de xfce.

(No hablo mucho espanol, soy de Estados Unidos.)

---

### Post by pol666 on 2009-03-06
Esta bueno, pero me parece que le falta una tostadita para ser considerado como escritorio.

---

### Post by erdosain9 on 2009-03-06
Muchas gracias por aclararme... veré entonces de hacer la forma más segura.

---

### Post by emiliano_raso on 2009-05-14
Acabo de instalar LXDE y me gustaría saber como configurarlo y customizarlo bien, porque no encuentro donde estan los archivos de configuracion o al menos las aplicaciones en el menu que me permitan modificarlo.

Pude cambiarle el wallpaper, el tema gtk y los iconos, pero no mas que eso. Despues el panel, las aplicaciones de inicio y esas cosas no encuentro donde modificarlas.

EDIT: Ya encontre como configurar las aplicaciones de inicio:
```
sudo gedit /etc/xdg/lxsession/LXDE/autostart
```

Ahi agregamos a la lista con un @ delante las aplicaciones que querramos, por ejemplo, yo le agregué el gvtray y me quedó asi el archivo:
```
@lxde-settings
@xscreensaver -no-splash
@lxpanel --profile LXDE
@pcmanfm -d
@gvtray
```

Igual sigo sin saber todavia como editar los paneles y demas.

---

### Post by staar on 2009-05-15
openbox tiene dos programitas propios, el obconf y el obmenu (creo que los nombres indican bastante bien para que son :-P), instalalos...

lo que no puedas personalizar ahí, está en alguno de los archivos de /home/*usuario*/.config/openbox/ (en el rc generalmente)...

saludos

---

### Post by emiliano_raso on 2009-05-15
> **staar said:**
> openbox tiene dos programitas propios, el obconf y el obmenu (creo que los nombres indican bastante bien para que son :-P), instalalos...

lo que no puedas personalizar ahí, está en alguno de los archivos de /home/*usuario*/.config/openbox/ (en el rc generalmente)...

saludos

Estaba hablando de LXDE :-P
O estoy yo confundido y el windows manager de lxde es open box?

---

### Post by staar on 2009-05-15
si si, el window manager de LXDE es nada menos que Openbox...

saludos

---

### Post by emiliano_raso on 2009-05-15
> **staar said:**
> si si, el window manager de LXDE es nada menos que Openbox...

saludos

Ah genial. Gracias. Ahora estoy entendiendo mas facil las cosas xD

---

### Post by emiliano_raso on 2009-05-15
> **staar said:**
> openbox tiene dos programitas propios, el obconf y el obmenu (creo que los nombres indican bastante bien para que son :-P), instalalos...

lo que no puedas personalizar ahí, está en alguno de los archivos de /home/*usuario*/.config/openbox/ (en el rc generalmente)...

saludos

"obconf" permite cambiar el borde de ventana y algunas cosas mas, pero no permite cambiar la apariencia del panel.

Y sigo sin encontrar algo que me permita sacar todos los iconos del escritorio XD Tengo el icono del home ahi y no hay opcion que me deje sacarlo, como /apps/nautilus/desktop en gconf-editor

---

### Post by staar on 2009-05-15
de nada, fijate en la carpeta .config de tu home, ahí deben estar las carpetas con las configuraciones de las aplicaciones de lxde (estoy 80% seguro de que lxpanel estaba ahí :-P :-D)...

para los iconos del escritorio fijate en el pcmanfm (el navegador de archivos), creo que es el que se ocupa de eso...

saludos

---

### Post by emiliano_raso on 2009-05-15
> **staar said:**
> de nada, fijate en la carpeta .config de tu home, ahí deben estar las carpetas con las configuraciones de las aplicaciones de lxde (estoy 80% seguro de que lxpanel estaba ahí :-P :-D)...

para los iconos del escritorio fijate en el pcmanfm (el navegador de archivos), creo que es el que se ocupa de eso...

saludos

Ahi me fijo...

GENIAL LO DE ESCUCHAR EL DISCO DURO XD JAJAJA XD

EDIT: Encontre el archivo. Muy lindo... pero como le cambio el aspecto? xD

---

### Post by staar on 2009-05-15
tenés instalado todos los componentes de LXDE? [http://wiki.lxde.org/en/Main_Page]("http://wiki.lxde.org/en/Main_Page")

hay una gui para configurar el panel, la buscaste por el menú? click derecho sobre el panel :-P?

saludos

---

### Post by emiliano_raso on 2009-05-15
> **staar said:**
> tenés instalado todos los componentes de LXDE? [http://wiki.lxde.org/en/Main_Page]("http://wiki.lxde.org/en/Main_Page")

hay una gui para configurar el panel, la buscaste por el menú? click derecho sobre el panel :-P?

saludos

OH DIOS! BOTON DERECHO SOBRE EL PANEL! Y LISTO!

Ves? A veces las cosas son mas simples de lo que parecen... Eso es porque despues de instalar ArchLinux si minimo no uso 12 comandos para hacer algo, siento que me estoy equivocando xD jajaja

---

### Post by staar on 2009-05-15
JAJAJAAA, ya me parecía...

naa, arch es SIMPLE :-D, una vez que lo tenés andando, va como piña, casi ni necesita retoques, solo algún pacman -Syu cada tanto...

saludos

---

### Post by guillermolisi on 2009-05-15
> **emiliano_raso said:**
> Ah genial. Gracias. Ahora estoy entendiendo mas facil las cosas xD
Casualmente a este tipo de caracteristicas me referia cuando te di el ejemplo en el otro thread sobre escritorios graficos y gestores de ventanas.

LXDE incluye un gestor de ventanas, OpenBox, pero OpenBox no incluye un LXDE.

---

