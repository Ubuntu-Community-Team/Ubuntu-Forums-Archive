---
title: "Todos mis videos se ven con colores frios"
date: 2009-04-09
forum: Software
---

### Post by rubioo on 2009-04-09
Hola, tengo el problema de que todos los vídeos que tengo en mi PC se ven así(los de youtube, etc. se ven perfectos). Esto sucede aunque los habrá con totem o con vlc. Aclaro que estoy usando gstreamer. 
 Este problema creo que empezó cuando instale libdvdcss2 para poder ver un dvd. Porque antes veía todos los vídeos 10 puntos.
 
 Les dejo unas capturas de pantalla:


       Saludos y espero que puedan ayudarme...

---

### Post by pablo.s on 2009-04-09
Mirá, vos estás usando el programa este
f.lux que varia la coloración de la pantalla.

1) Sin ser doctor, te puedo diagnosticar
un caso de persistencia retiniana. ¿Que es
esto? La coloración que proyecta tu monitor
es cálida. Tu ojo se acostumbra a este 
fenómeno y le dice al cerebro que esto es
normal.Si después ves la televisión y no 
tiene esa coloración, te parece todo frío.

2)libdvdcss2 te libera las zonas y las
protecciones de anticopia, como te expliqué
en otro hilo. No está relacionado con la
coloración ni la temperatura de color que
por ejemplo, f.lux provoca.

Espero que te aclare el panorama.
Saludos.


ACTUALIZO: Al margen de la persistencia 
retiniana, instalá VLC y comprobá si
sigue pasando lo mismo. Está en los
repositorios de Medibuntu.

---

### Post by rubioo on 2009-04-09
Hola pablo, antes que nada gracias por la respuesta.
 Me olvidé de aclarar que no estaba ejecutando f.lux

 1) No entendí mucho lo que me dijiste, pero si ahora que estoy usando la pc me pongo a ver tv se ve normal, si veo videos de youtube se ven normales, si reinicio mi pc y entro a windows el mismo video que en ubuntu se ve con colores frios, se ve como se tiene que ver.

 2) Ya me parecía que no tenía nada que ver  con ibdvdcss2


 Ya tenía instalado vlc y se ve igual de frío

 Nota: la remera del cantante en la foto es de color rojo :S

---

### Post by pablo.s on 2009-04-09
Ahora que lo analizo, mas que colores
frios, pareciera que es negativo lo que
muestra (como el negativo de una foto).

Vamos a ir descartando factores:

1) ¿Los drivers de la placa de video son
especificos (ATI/ NVidia) o son los de
XOrg?

2) ¿Te hace el mismo efecto cuando ves
una foto o gráfico?

---

### Post by rubioo on 2009-04-09
Mmmm, si creo que es como negativo.

  1) Uso drivers Nvidia, la version creo que era 180(luego confirmo esto), ayer se actualizaron.

  2) No. Veo fotos, y todo lo demas normal. Lo unico que hasta ahora se ve asi, son los videos que tengo en mi compu.

---

### Post by Mauro22 on 2009-04-09
Es es negativo...


Mirá hay un plugin de Compiz que capaz activaste (me paso ayer)

Si en una ventana apretas Super (tecla win) + M (o N) se pone en negativo y viceversa...


M lo invierte, es decir todo a negativo menos la ventana actual y al reves.
N es solo la ventana activa.


Ahi te dejo dos caps, una con ese efecto y la otra no.


Desactiva compiz a ver que onda!!


):P

---

### Post by pablo.s on 2009-04-09
¿Pasa lo mismo si está Compiz
desactivado?

EDIT: Lei el mensaje de Mauro22
cuando ya habia posteado.

Lo que estoy pensando acerca de
Compiz da para un post aparte.

---

### Post by staar on 2009-04-09
probaste con mplayer o con xine?, el vlc, que salida de video esta usando, xvideo?

saludos

---

### Post by rubioo on 2009-04-09
> Es es negativo...


Mirá hay un plugin de Compiz que capaz activaste (me paso ayer)

Si en una ventana apretas Super (tecla win) + M (o N) se pone en negativo y viceversa...


M lo invierte, es decir todo a negativo menos la ventana actual y al reves.
N es solo la ventana activa.


Ahi te dejo dos caps, una con ese efecto y la otra no.


Desactiva compiz a ver que onda!!

 El plugin de compiz estaba activado, pero no era eso. Dejo las capturas con y sin el efecto activado.


> probaste con mplayer o con xine?, el vlc, que salida de video esta usando, xvideo?

saludos 

 Gracias! poniendo en la salida de vídeo x11 se ve de 10 :)
 Puedo hacer que se vea así en totem? o pruebo xine y mplayer?


       Saludos y Gracias a todos!

---

### Post by staar on 2009-04-09
el problema es que x11 no usa la aceleración de la placa, y te puede traer problemas...
probá instalando mplayer y SMPlayer, que es un frontend que te deja configurar un montón de cosas (ojo, es en Qt4), entre las que está la salida de video, y te ofrece dos tipos especiales de xv especifícamente para NVidia (xv es la salida de video más recomendada casi siempre)...

saludos

---

### Post by rubioo on 2009-04-09
Muchas gracias starr, me gusto bastante el mplayer. Creo que voy a tener que despedirme de totem...

      Saludetes

---

