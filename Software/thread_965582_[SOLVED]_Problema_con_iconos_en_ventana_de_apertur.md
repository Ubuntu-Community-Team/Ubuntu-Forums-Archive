---
title: "[SOLVED] Problema con iconos en ventana de apertura de archivos"
date: 2008-10-31
forum: Software
---

### Post by serwwweb on 2008-10-31
Hola, los saludo a todos y agradezco de antemano su ayuda. Mi problema es el siguiente, como bien dice el titulo del post, mi problema es que tengo mis iconos personalizados con un tema que baje de gnome-look.org, y se ven realmente bien en todo el entorno de escritorio, salvo cuando quiero abrir un archivo desde una aplicacion en la que abre una ventana para navegar hasta el que uno quiere. El problema precisamente es que en esta ventana de seleccion (o no se como llamarla) me muestra los iconos basicos de gnome.
Soy relativamente nuevo en linux, llevo un año usandolo, especificamente ubuntu, y he aprendido muchisimo, pero esto nunca me habia pasado. Si alguien sabe como solucionarlo desde ya muchas gracias. Espero haber sido claro.
PD: Una cosa que me olvidaba es que los iconos los tengo en la carpeta de root, y me pasa con cualquier tema de iconos. Saludos.

---

### Post by Mauro22 on 2008-10-31
No se si te referis a esto:

> 
Que root se "vea" como el usuario:

sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
sudo ln -s ~/.fonts /root/.fonts


---

### Post by serwwweb on 2008-11-01
> **Mauro22 said:**
> No se si te referis a esto:
No, haciendo un link simbolico a las carpetas de iconos y demas no lo soluciono, ya que tengo el mismo problema aun si instalo los temas de iconos en mi carpeta de usuario. Como dije el problema de los iconos es solamente en las ventanas de apertura de archivos desde una aplicacion, lo demas esta todo ok. Es raro porque nunca me habia pasado en un añode usar ubuntu. No es una calamidad pero por algun motivo me molesta...
Gracias por tu respuesta!

---

### Post by lega on 2008-11-01
Hola, alguna vez me paso eso, tengo un archivito en la pc con pequeños tips ;) sobre este tema tengo anotado lo siguiente:

> Para que tome los iconos pequeños de las carpetas
 cd ~/.icons/[COLOR="Red"]iconpack[/COLOR]/scalable/places/
 ln -s gnome-fs-directory.png folder.png
 ln -s gnome-fs-directory.png gtk-directory.png


Donde dice [COLOR="Red"]iconpack[/COLOR] va el nombre de tus iconos, espero te sirva

Saludos

---

### Post by serwwweb on 2008-11-01
Excelente lega, me soluciono el problema. Muchas gracias!=D>

---

