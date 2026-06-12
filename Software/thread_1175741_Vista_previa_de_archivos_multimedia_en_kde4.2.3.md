---
title: "Vista previa de archivos multimedia en kde4.2.3"
date: 2009-06-01
forum: Software
---

### Post by guisheca on 2009-06-01
Que tal comunidad, siguiendo en mi camino como nuevo (y creo que ya permanente) usuario de kde hay una cosa que todavía no pude solucionar. Y es el tema de las vistas previas de los archivos multimedia, como por ejemplo, los videos.
En gnome cuando habro una carpeta que contiene videos en ves de aparecer el ícono correspondiente al archivo de video aparece un "frame" al azar del contenido de dicho archivo. Esto me resulta muy útil porque descargo muchos videos desde lugares como youtube y todos tienen nombres del tipo FXHJGD574, etc. Es decir, es imposible identificarlos por el nombre. En gnome en seguida me daba cuenta de cual era cual debido a que contaba con las vistas previas, pero en kde 4.2.3 no se como habilitar esa característica.
Espero alguien sepa algo. Por cierto, ya investigue y el encargado de hacer esto en gnome es totem y uno de sus complementos. Instalé totem en kde y habilité ese complemento pero no funcionó.
Saludos y gracias.

---

### Post by pablo.s on 2009-06-01
sudo apt-get install mplayerthumbs ffmpegthumbnailer

---

### Post by guisheca on 2009-06-01
> **pablo.s said:**
> sudo apt-get install mplayerthumbs ffmpegthumbnailer

Sos groso sabelo!!

Muchas gracias!

---

### Post by guisheca on 2009-06-01
Haaa canté victoria antes de tiempo. Muchos de los videos no pueden previsualizarse, simplemente porque el mplayer no los reconoce y no los puede reproducir.
Voy a ver que puedo instalar para que lo haga, tal ves en los repositorios de medibuntu este la respuesta, ya que tengo instalado tanto kubuntu-restricted-extras como ubuntu-restricted-extras.
Saludos y gracias nuevamente por mostarme el camino.

---

### Post by guisheca on 2009-06-02
Bueno gente, despues de mucho batallar, logré que todo funcione a la perfección. Pero solamente cuando instalé el mplayer que viene en los repositorios de medibuntu pude obtener vistas previas de todo.
Ahora bien, con el mplayer de medibuntu no podía reproducirlo todo, no se porque, pero me tomé el trabajo de compilar las fuentes obtenidas vía SVN siguiendo [este tuto]("http://ubuntuforums.org/showpost.php?p=6455106&postcount=1"), y ahora si, el mplayer es lo mas :-).
Saludos y gracias.

---

### Post by pol666 on 2009-06-02
Tambien puede depender mcuho de KDE, para KDE4.3 se tiene preparado la vista previa en carpetas y en otros archivos :)

---

### Post by pablo.s on 2009-06-02
> **guisheca said:**
> me tomé el trabajo de compilar las fuentes obtenidas vía SVN siguiendo [este tuto]("http://ubuntuforums.org/showpost.php?p=6455106&postcount=1"), y ahora si, el mplayer es lo mas :-).
Saludos y gracias.

Sos grosso, guisheca, sabelo.
Ayer a la noche me hice el
mismo laburito pero para
OpenSolaris. Media hora
después encontré 
un repositorio...

---

