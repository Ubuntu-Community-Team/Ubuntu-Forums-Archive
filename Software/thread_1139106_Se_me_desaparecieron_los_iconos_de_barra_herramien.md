---
title: "Se me desaparecieron los iconos de barra herramientas superior"
date: 2009-04-26
forum: Software
---

### Post by leonardomdq on 2009-04-26
Hola a todos, el problema que tengo es que se me desaparecio el icono desplegable de la barra de tareas superior donde esta conexiones inalambricas, VPN, conexion cableada y demas, creo que lo elimine sin querer.
Hay manera de restaurarlo?? porque reinicie pensando que apareceria de nuevo pero no.
Estoy usando Intrepid.

Desde ya muchas gracias

---

### Post by sajnox on 2009-04-26
Click derecho en donde estaba y elegi "agregar al panel" y despues seleccionas "Area de Notificacion"

Eso te lo deberia solucionar

---

### Post by leonardomdq on 2009-04-26
Listo!! muchas gracias por ayuda

---

### Post by abelardo.baldizon on 2009-06-01
Hola 
Yo tengo el mismo problema con la barra de menu en ubuntu 9.04. Accidentalmente la quite queriendo hacerle algunas modificaciones como agregar la papelera. bueno el asunto es que ahora no me aparece para nada. Ya trate de arreglar el problema con el boton derecho del mouse pero no me da la opción de agregar nada. Otra cosa que hice es que cambie el escritorio del que esta disenado para notebooks (ya que yo uso una notebook) al escritorio clasico de ubuntu. Cuando hice ese cambio me volvio a aparecer la barra pero al encender la siguiente vez la compu ya no estaba. Ahora tengo el gran problema de que no puedo acceder a ningun programa. solo a los archivos que estan en el escritorio. es realmente una desgracia. Tal vez me pueden ayudar. Se los agradeceria enormemente. 
Saludos 
Abelardo

---

### Post by pablo.s on 2009-06-01
> **abelardo.baldizon said:**
> Cuando hice ese cambio me volvio a aparecer la barra pero al encender la siguiente vez la compu ya no estaba. 

En una terminal escribí:

**[COLOR=DarkGreen]gnome-panel[/COLOR]**

y va a aparecer. Luego en
Sistema -Preferencias -
Aplicaciones de inicio
tenés que chequear
Gnome Panel

---

### Post by Brath-ga on 2009-06-04
> **pablo.s said:**
> En una terminal escribí:

**[COLOR=DarkGreen]gnome-panel[/COLOR]**

y va a aparecer. Luego en
Sistema -Preferencias -
Aplicaciones de inicio
tenés que chequear
Gnome Panel

A mi me acaban de desaparecer los paneles superior e inferior, con lo cual no puedo acceder a los menús y aprovechar tu ayuda.

No borré nada, fué al arrancar en el día de hoy.

---

### Post by Hei Ku on 2009-06-04
Apretá Alt+F2 y escribi: gnome-panel

---

### Post by Brath-ga on 2009-06-05
Gracias por el intento Hei-Ku, pero es que alt-f2 no me funciona tampoco.
Puedo entrar en un terminal, pero tendría que saber a que subdirectorio tengo que dirigirme, pues en home no me funciona lo de gnome-panel.

---

### Post by Hei Ku on 2009-06-05
Como que no te funciona lo de gnome-panel?
Desde adentro de gnome, abri una terminal y escribi gnome-panel

Si no te anda, postea el error.

Y el Alt+F2 te tiene que andar, o tienes un error mucho mas severo que simplemente un panel faltante.

---

### Post by staar on 2009-06-05
Hei Ku el Alt+F2 en Gnome es parte de gnome-panel, por eso no anda...

saludos

---

### Post by pablo.s on 2009-06-05
> **Brath-ga said:**
> Puedo entrar en un terminal, pero tendría que saber a que subdirectorio tengo que dirigirme, pues en home no me funciona lo de gnome-panel.

gnome-panel esta situado
en /usr/bin pero desde
/home se puede acceder.
Verifica si por un error
no se desinstalo, efectuando
una busqueda desde Synaptic.
En la terminal escribe:

[COLOR="DarkGreen"]**sudo Synaptic**[/COLOR]

y busca si esta instalado
gnome-panel.

---

