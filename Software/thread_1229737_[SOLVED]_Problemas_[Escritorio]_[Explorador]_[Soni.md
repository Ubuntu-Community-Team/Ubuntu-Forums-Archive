---
title: "[SOLVED] Problemas: [Escritorio] [Explorador] [Sonido] - Gnome"
date: 2009-08-02
forum: Software
---

### Post by demian86 on 2009-08-02
Damas y Caballeros, en el dia de la fecha les traigo 3 inconvenientes que tengo y no encontre forma de solucionarlos.

1º Me voy al panel superior --> Lugares --> Ej; Carpeta personal

Y me salta el error de 

> 
No se puede abrir el lugar «file:///home/demian»
No hay ninguna aplicación registrada para manejar este archivo
2º Escritorio totalmente bloqueado.

Menu contextual no aparece, por mas que apreta el boton derecho del mouse con un taladro percutor, no va ni con la gotita.
Lanzadores, todos los lanzadores que tenia en el escritorio desaparecieron.
Intento enviar accesos al escritorio y me los rebota.

Utilize San Google y encontre la forma de entrar al editor de Gnome, revise en Show Desktop y revise, auqnue tengo poco conocimiento del ingles verifique y todo esta en orden.

Aclarar, los paneles superior e inferior funcional con total normalidad

3º y ultimo problema, pero estaba vez la macana me la mande yo

como placa de sonido On-Board tengo un Via 8235 codec VT1617a, que seguramente desde synaptic abre borrado los controladores. me he quedado sin sonido y cuando voy a la opcion de control de volumen me salta el siguiente error.

> 
Falló al iniciar el control de volumen: Ha ocurrido un error al ejecutar el proceso hijo «gnome-volume-control» (No existe el fichero ó directorio)
Como instalo nuevamente los controladores ?

Desde antemano muchas gracias al que me pueda dar una solucion.

---

### Post by staar on 2009-08-02
1 y 2 son el mismo problema, algo está haciendo que nautilus (el programa que es navegador de archivos y el que maneja el escritorio) se cierre, hacé una cosa, abrí una Terminal y corré ```
killall nautilus
``` para cerrar la instancia actual del programa, después poné ```
nautilus
``` en la misma terminal, y tratá de abrir de nuevo tu carpeta personal, si se cierra de nuevo, en la terminal vas a tener los mensajes de error que largó nautilus antes de morir, copialos y pegalos acá para que te podamos ayudar mejor...

el 3 no es un problema de drivers, la mayoría de los drivers de sonido están en el kernel y no se pueden desinstalar desde synaptic sin desinstalar el kernel (con lo que te quedarías sin sistema), el problema es con el programa gnome-volume-control (el control de volumen del entorno de escritorio gnome) que, por alguna razón, no lo encuentra, no recordás haberlo desinstalado? si es así, reinstalalo, si no, también podés correr ```
alsamixer
``` en una terminal, es otro control de volumen, pero de consola, y ahí setear el volumen que quieras...

saludos

---

### Post by demian86 on 2009-08-02
[B]Bueno, resuelta que sin darme cuenta desinstale nautilus.


Tratando de instalar nautilus nuevamente me presento otro problema en las dependencias.

Ya que nautilus depende de gvfs-backends y este mismo depende de gvfs.

Resulta que tenia instalado gvfs [1.2.2-0ubuntu2], y no me permitia instalar gvfs-bakends [1.2.2-0ubuntu1].

Asi que me dispuse a desistalar gvfs.

Y luego de desistalarlo, instale nuevamente nautilus y asunto resuelto.

Proximo paso, recuperar el sonido.

Pronto edito haber como me fue con eso

Gracias
[/B]

---

### Post by staar on 2009-08-02
y porqué desinstalaste nautilus? tené cuidado con lo que desinstalás, porque podés romper todo...

saludos

---

### Post by demian86 on 2009-08-02
[B]Bueno, es que no sepo, no sabo y no se.

[COLOR=Red]Nunca llegaras a ser perfecto sin cometer ningun error[/COLOR], asi me decia un vecino que ya fallecio.

Sobre el sonido, ni pa adelante ni para atras.

Si instalo  el Mezclador Gnome Alsa tengo el control del volumen activado, junto con los del Mic y toda la bolada, pero igual sigo sin sonido.

U.U[/B]

---

### Post by Hei Ku on 2009-08-02
pone en una terminal: alsamixer

y fijate que todos los volumnes esten al tope

---

### Post by demian86 on 2009-08-02
[B]Estan todos subido o.O

No me va a ganar esta madakaca   :F

Edito

desinstale todos los Alsa desde sinaptyc y los volvi a instalar y ahora funciona sin ningun problema

Creo que tendre que llamar a Alcoholicos Anonimos, quien tiene el numero asi llamo.

Staar, muchisimas gracias nuevamente

Hei Ku, gracias a vos tambien.

Cada vez me gusta mas esto, me gusta calentarme con las cosas, se hace mas entretenido.

Problema solucionado, si quieren cierrenlo
[/B]

---

