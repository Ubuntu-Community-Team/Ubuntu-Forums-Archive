---
title: "Problemas con Conky"
date: 2009-10-27
forum: Software
---

### Post by matias_tati on 2009-10-27
El tema esta asi:
Tuve antes un problema que era que el conky se veia delante de las ventanas en el inicio. Lo solucionaba cambiando esta linea:
own_window_type override por own_window_type normal
y todos contentos, pero ahora teniendolo asi me pasa este problema que se refracta el wallpaper.
Si lo dejo asi own_window_type override en el inicio me queda delante de las ventanas y con sombra pero si lo cierro con killall conky y le doy conky de nuevo funciona bien pero es engorroso hacer esto cada vez qyue cierre sesion.
Pasamos en limpio:

own_window_type override me queda detras de las ventanas en el inicio y con sombra

own_window_type normal me queda el wallpaper refractado y se me corre arriba un poco.

Con own_window no: se me desparrame mi conky por toda la pantalla.

Que estara pasando?

---

### Post by Bruce M. on 2009-10-28
> **matias_tati said:**
> Que estara pasando?

La verdad: No tengo ninguna idea

Una pregunta: Estas usando 
[LIST]
[*]compositor o
[*]COMPIZ
[/LIST]

Encontraré una respuesta en otro foro.

CHIMO!
Bruce

---

### Post by matias_tati on 2009-10-28
> **Bruce M. said:**
> La verdad: No tengo ninguna idea

Una pregunta: Estas usando 
[LIST]
[*]compositor o
[*]COMPIZ
[/LIST]

Encontraré una respuesta en otro foro.

CHIMO!
Bruce

Uso compiz. En la version anterior esto no me pasaba ahora 1.7.2 me pasa.
Gracias.

---

### Post by Bruce M. on 2009-10-29
> **matias_tati said:**
> Uso compiz. En la version anterior esto no me pasaba ahora 1.7.2 me pasa.
Gracias.

Bueno, dame uno o dos días.

CHIMO!
Bruce

---

### Post by matias_tati on 2009-10-29
> **Bruce M. said:**
> Bueno, dame uno o dos días.

CHIMO!
Bruce

Ok gracias.

---

### Post by matias_tati on 2009-10-31
Acabo de descubrirqui si quito el conky de aplicaciones al inicio y lo ejecuto manualmente cuando ya cargo Ubuntu corre sin problemas
No se podra hacer un script que m ejecute onky unas vez trascurrido cierto tiempo para no hacerlo manualmente??

---

### Post by josecuervo86 on 2009-10-31
[OT]Esto ya esta para sticky no piensan?[/OT]

---

### Post by staar on 2009-10-31
> **matias_tati said:**
> Acabo de descubrirqui si quito el conky de aplicaciones al inicio y lo ejecuto manualmente cuando ya cargo Ubuntu corre sin problemas
No se podra hacer un script que m ejecute onky unas vez trascurrido cierto tiempo para no hacerlo manualmente??

si, se puede, y de hecho es muy común hacerlo, sobre todo cuando se usa conky con compiz, el script puede ser algo así ```

!#/bin/bash
sleep 10 &&
conky
``` lo guardás, le das permisos de ejecución, lo ponés en las aplicaciones al inicio, y tendría que andar...

si te sigue pasando lo mismo, podés probar aumentando el tiempo del *sleep*...

saludos

---

### Post by matias_tati on 2009-10-31
> **staar said:**
> si, se puede, y de hecho es muy común hacerlo, sobre todo cuando se usa conky con compiz, el script puede ser algo así ```

!#/bin/bash
sleep 10 &&
conky
``` lo guardás, le das permisos de ejecución, lo ponés en las aplicaciones al inicio, y tendría que andar...

si te sigue pasando lo mismo, podés probar aumentando el tiempo del *sleep*...

saludos

Como lo nombro? Quiero saber si esty haciendolo bien. Le pongo cualquier nombre .sh?
Y le doy permisos de ejecucion?

---

### Post by Mauro22 on 2009-10-31
Guarda con el OT..


Nombralo de la forma que quieras con o sin sh (acá las extensiones no significan mucho... es puro paradigma windosero; ((algunas)) )


> chmod +x archivo.sh

Con eso le das permiso

lo moves a bin:
> 
sudo mv archivo.sh /usr/bin


y despues solo haciendo:

> archivo.sh

desde la consola, se abre :D

---

### Post by matias_tati on 2009-10-31
Perfecto lo hize siguiendo este tutorial por si a alguien mas le pasa.
[http://www.ubuntu-es.org/index.php?q=node/103184](http://www.ubuntu-es.org/index.php?q=node/103184)

Lo que si note que cuando reinicio no lo toma pero si cierro sesion si, sera cuestion de jugar con el tiempo de espera. 

[[img]http://a.imagehost.org/t/0805/Pantallazo.jpg[/img]](http://a.imagehost.org/view/0805/Pantallazo)

---

### Post by edipotrebol on 2010-02-10
Muy buenas.
Me acabo de dar de alta en el foro. Había entrado muchas veces a mirar cosas pero nunca había participado (sólo como lector), pero el encontrar la solución a conky me ha hecho ingresar. Tenía los mismos problemas de ejecución al inicio de conky y es que se ejecutaba y terminaba casi al mismo tiempo. Ejecutándolo con un pequeño retraso, problema resuelto. Muchísimas gracias.

---

### Post by juanuni on 2010-10-04
> **matias_tati said:**
> Link al conky agregado!!!
tengo un problemilla con conky....lo que pasa es que al encender la pc, conky se superpone a cualquier  ventana abierta, lo que me trae problemas dado que oculta los botones de  max, min, cerrar, digamos q parcialmente lo soluciono, al cambiar la  línea:

own_window_type        override

por 

own_window_type        underride

y luego volverlo a 

own_window_type        override

De ese modo, recien puedo tener las ventanas abiertas por encima de  conky, digamos que eso puede no molestarme a mi, pero si seria una gran  molestia para los dema miembros de mi familia que usan la pc cuando no  estoy en casa, dado que ellos no saben como configurar conky, y no creo q  tengan paciencia para querer aprender :razz:, bueno, espero que puedas tener alguna sugerencia. 

Me olvidaba decir que cuando hago  "own_window_type        underride",  la barra de conky se pone en una posicion que no deseo y es muy  frustante lidiar en esa opcion pues no se ajusta como  deseo....agardecere alguna sugerencia a mi problema..........XP

---

### Post by matias_tati on 2010-10-04
> **juanuni said:**
> tengo un problemilla con conky....lo que pasa es que al encender la pc, conky se superpone a cualquier  ventana abierta, lo que me trae problemas dado que oculta los botones de  max, min, cerrar, digamos q parcialmente lo soluciono, al cambiar la  línea:

own_window_type        override

por 

own_window_type        underride

y luego volverlo a 

own_window_type        override

De ese modo, recien puedo tener las ventanas abiertas por encima de  conky, digamos que eso puede no molestarme a mi, pero si seria una gran  molestia para los dema miembros de mi familia que usan la pc cuando no  estoy en casa, dado que ellos no saben como configurar conky, y no creo q  tengan paciencia para querer aprender :razz:, bueno, espero que puedas tener alguna sugerencia. 

Me olvidaba decir que cuando hago  "own_window_type        underride",  la barra de conky se pone en una posicion que no deseo y es muy  frustante lidiar en esa opcion pues no se ajusta como  deseo....agardecere alguna sugerencia a mi problema..........XP

Que pasa si cuando inicias con el conky funcionando le das un
```
killall conky
```

Y luego

```
conky
```

En la terminal?

---

### Post by Nano.uy on 2010-10-05
A mi me pasa algo diferente que no he logrado solucionar en mucho tiempo que llevo intentándolo. 

El tema es con own_window_type. 

Para poder tener transparencia debería colocar desktop. El problema es que al elegir desktop cuando doy un clic en el escritorio el conky desaparece y no vuelve mas. 

Si lo dejo override no me toma las transparencias. 

Alguien ha escuchado de algún problema de estos? 

Actualmente estoy con ArchLinux y tanto en este con KDE así como en Ubuntu con Gnome y compiz tenia el mismo problema. 

Puede ser que sea un problema de la ATI pero la veo difícil para que sea ese problema. 

Si alguien tiene alguna idea se lo agradezco.

Saludos.

---

### Post by matias_tati on 2010-10-05
> **Nano.uy said:**
> A mi me pasa algo diferente que no he logrado solucionar en mucho tiempo que llevo intentándolo. 

El tema es con own_window_type. 

Para poder tener transparencia debería colocar desktop. El problema es que al elegir desktop cuando doy un clic en el escritorio el conky desaparece y no vuelve mas. 

Si lo dejo override no me toma las transparencias. 

Alguien ha escuchado de algún problema de estos? 

Actualmente estoy con ArchLinux y tanto en este con KDE así como en Ubuntu con Gnome y compiz tenia el mismo problema. 

Puede ser que sea un problema de la ATI pero la veo difícil para que sea ese problema. 

Si alguien tiene alguna idea se lo agradezco.

Saludos.

Te hago la misma pregunta que al anterior

---

### Post by Nano.uy on 2010-10-05
Aca no hay cambios. 

Es mas, lo hago constantemente cuando pruebo otras configuraciones obtenidas en la web. 

Mato el conky y pruebo y nada. 

Siempre lo mismo. 

Lo raro es que siempre me anduvo, hasta alguna actualización que se me fue al c****o. Ni me preguntes cual actualización porque le perdí la pista pero seguro esta relacionado al kernel por que en el arch presenta el mismo problema. 

Otra cosa que me dejo de funcionar fueron los condicionales para la red, if_existing
Andaba al pelo y de un momento a otro no funcionó mas. Lo palie poniéndole un cat (if_existing cat /proc/net/route eth1) pero obvio, que queda colgado leyendo siempre /proc/net/route. 

No se que fue lo que pasó pero perdí esas dos cosas, la transparencia y el if_existing

Obs. cuando me refiero a transparencia me refiero a usar la opción own_window_argb_value 

Saludos y gracias por tu interés.

---

### Post by matias_tati on 2010-10-06
> **Nano.uy said:**
> Aca no hay cambios. 

Es mas, lo hago constantemente cuando pruebo otras configuraciones obtenidas en la web. 

Mato el conky y pruebo y nada. 

Siempre lo mismo. 

Lo raro es que siempre me anduvo, hasta alguna actualización que se me fue al c****o. Ni me preguntes cual actualización porque le perdí la pista pero seguro esta relacionado al kernel por que en el arch presenta el mismo problema. 

Otra cosa que me dejo de funcionar fueron los condicionales para la red, if_existing
Andaba al pelo y de un momento a otro no funcionó mas. Lo palie poniéndole un cat (if_existing cat /proc/net/route eth1) pero obvio, que queda colgado leyendo siempre /proc/net/route. 

No se que fue lo que pasó pero perdí esas dos cosas, la transparencia y el if_existing

Obs. cuando me refiero a transparencia me refiero a usar la opción own_window_argb_value 

Saludos y gracias por tu interés.

Usas un script o solo pones la orden conky en aplicaciones al inicio?

---

### Post by Nano.uy on 2010-10-06
En Ubuntu usaba script con un sleep de 60. 

En arch lo largo sin script. No existe diferencia entre las dos formas por aca.

---

### Post by matias_tati on 2010-10-06
> **Nano.uy said:**
> En Ubuntu usaba script con un sleep de 60. 

En arch lo largo sin script. No existe diferencia entre las dos formas por aca.

Probaste usar el script en Arch?

---

### Post by juanuni on 2010-10-07
> **matias_tati said:**
> Que pasa si cuando inicias con el conky funcionando le das un
```
killall conky
```

Y luego

```
conky
```

En la terminal?
pues pasa que si se arregla, pero ese no es el punto, el punto es que al encender la maquina ocurre el problema, se supone que no deberia presentar nigun problema cuando la pc se enciende !!!, a eso iba mi pregunta !!!

---

### Post by matias_tati on 2010-10-08
> **juanuni said:**
> pues pasa que si se arregla, pero ese no es el punto, el punto es que al encender la maquina ocurre el problema, se supone que no deberia presentar nigun problema cuando la pc se enciende !!!, a eso iba mi pregunta !!!

Bueno che estas re ansioso!!! Por algo te lo pregunto. Y contestame la ultima y te digo la solucion.
Como haces para que se inicie?
Pones la orden conky en aplicaciones al inicio?
Te cuento mas o menos como es la cosa si conky se inicia al mismo tiempo que Nautilus eso genera una interaccion entre ambas aplicaciones que hace que suceda este inconveniente. Al principio del post tenes la solucion sino podria ser mas especifico por aca y guiarte. Avisame.

---

### Post by Nano.uy on 2010-10-09
> **matias_tati said:**
> Probaste usar el script en Arch?

Acabo de hacerlo y no hubo diferencias.

---

### Post by juanuni on 2010-10-10
> **matias_tati said:**
> Bueno che estas re ansioso!!! Por algo te lo pregunto. Y contestame la ultima y te digo la solucion.
Como haces para que se inicie?
Pones la orden conky en aplicaciones al inicio?
Te cuento mas o menos como es la cosa si conky se inicia al mismo tiempo que Nautilus eso genera una interaccion entre ambas aplicaciones que hace que suceda este inconveniente. Al principio del post tenes la solucion sino podria ser mas especifico por aca y guiarte. Avisame.
uso un script, digamos que basicamente es el conky q me pasaste :p !!!!

---

### Post by matias_tati on 2010-10-11
> **juanuni said:**
> uso un script, digamos que basicamente es el conky q me pasaste :p !!!!

Bueno por lo que leo que igual no me queda claro asumo que para que se inicie conky vos pones en aplicaciones al inicio la orden conky para que inicie cada vez que encendes tu pc.

Primero quita esa orden, la vamos a sustituir por otra. Lo que hayas modificado en el conkyrc volve a ponerlo como estaba no deberia darte problemas, hablo de las lineas que cambiaste como me mencionaste antes.

A esta linea me refiero:

```
own_window_type override
```


Ahora vamos a crear un script para que en cada inicio conky se lance con un retraso de 20 segundos, muy util tambien si queres iniciar varios conkys.

En la terminal dale

```
sudo gedit /usr/bin/inicio-conky
```

Copia esto tal cual y guardalo.

```
#!/bin/bash
sleep 20 && conky;
```

Le damos permisos de ejecuccion

```
sudo chmod a+x /usr/bin/inicio-conky
```

Y ahora en sistema: Sistema > Preferencias > Sesiones > &#8220;Programas al Inicio&#8221;

Añadis la orden 

```
inicio-conky
```

Donde dice orden.

Enjoy!!!

---

### Post by juanuni on 2010-10-14
> **matias_tati said:**
> Bueno por lo que leo que igual no me queda claro asumo que para que se inicie conky vos pones en aplicaciones al inicio la orden conky para que inicie cada vez que encendes tu pc.

Primero quita esa orden, la vamos a sustituir por otra. Lo que hayas modificado en el conkyrc volve a ponerlo como estaba no deberia darte problemas, hablo de las lineas que cambiaste como me mencionaste antes.

A esta linea me refiero:

```
own_window_type override
```


Ahora vamos a crear un script para que en cada inicio conky se lance con un retraso de 20 segundos, muy util tambien si queres iniciar varios conkys.

En la terminal dale

```
sudo gedit /usr/bin/inicio-conky
```

Copia esto tal cual y guardalo.

```
#!/bin/bash
sleep 20 && conky;
```

Le damos permisos de ejecuccion

```
sudo chmod a+x /usr/bin/inicio-conky
```

Y ahora en sistema: Sistema > Preferencias > Sesiones > &#8220;Programas al Inicio&#8221;

Añadis la orden 

```
inicio-conky
```

Donde dice orden.

Enjoy!!!
pues, bueno, la verdad debi ser mas especifico y decir que NO estaba puesto como aplicaciones al inicio, sino que ya tenia ese archivo inicio-conky, solo que en lugar de 20 segundos de retraso, tenia 15, tambien tenia permisos, pero creo q era d un modo un pokito diferente, mas q nada en la parte de "a+x", bueno esperare tu respuesta !!!

---

### Post by matias_tati on 2010-10-15
> **juanuni said:**
> pues, bueno, la verdad debi ser mas especifico y decir que NO estaba puesto como aplicaciones al inicio, sino que ya tenia ese archivo inicio-conky, solo que en lugar de 20 segundos de retraso, tenia 15, tambien tenia permisos, pero creo q era d un modo un pokito diferente, mas q nada en la parte de "a+x", bueno esperare tu respuesta !!!

Si no es eso no se me ocurre que puede ser. Porque si haces killall conky y desp conky y se arregla el script deberia hacer el mismo efecto. Como si en cada inicio vos esperaras un rato y dieras conky en la terminal. Revisa bien los pasos del script, a veces un error minimo te puede traer muchos dolores de cabeza te lo digo por experiencia.

---

### Post by juanuni on 2010-10-18
> **matias_tati said:**
> Si no es eso no se me ocurre que puede ser. Porque si haces killall conky y desp conky y se arregla el script deberia hacer el mismo efecto. Como si en cada inicio vos esperaras un rato y dieras conky en la terminal. Revisa bien los pasos del script, a veces un error minimo te puede traer muchos dolores de cabeza te lo digo por experiencia.
Gracias man por el tiempo dedicado, al parecer el problema era el tiempo d espera, poniendo 20, todo se solucionó !!!

---

### Post by juanuni on 2011-04-08
Hola, no se si deba escribir esto en este hilo, pero bueno ahi va, ante todo, debo agradecerte por todo el tiempo prestado en resolver los problemas que podamos tener con conky, verás, tengo varios archivos en el escritorio, y algunos de los iconos en el escritorio son tapados (aparecen debajo) del conky, a pesar de que éste está transparente mostrando el fondo de pantalla. Me gustaría enviarte alguna imagen pero no recuerdo como hacerlo dado que hace mucho no posteo. Hay algo que se pueda hacer para que el conky no haga eso? (te dire que tengo el panel superior comprimido y toda la info del conky está al mismo nivel que el panel superior pero en los lados). El problema se presenta el parte superior de la pantalla por debajo del panel superior. te agradeceré alguna respuesta

---

### Post by juanuni on 2011-04-08
> **matias_tati said:**
> Si no es eso no se me ocurre que puede ser. Porque si haces killall conky y desp conky y se arregla el script deberia hacer el mismo efecto. Como si en cada inicio vos esperaras un rato y dieras conky en la terminal. Revisa bien los pasos del script, a veces un error minimo te puede traer muchos dolores de cabeza te lo digo por experiencia.


Hola, no se si deba escribir esto en este hilo, pero bueno ahi va, ante  todo, debo agradecerte por todo el tiempo prestado en resolver los  problemas que podamos tener con conky, verás, tengo varios archivos en  el escritorio, y algunos de los iconos en el escritorio son tapados  (aparecen debajo) del conky, a pesar de que éste está transparente  mostrando el fondo de pantalla. Me gustaría enviarte alguna imagen pero  no recuerdo como hacerlo dado que hace mucho no posteo. Hay algo que se  pueda hacer para que el conky no haga eso? (te dire que tengo el panel  superior comprimido y toda la info del conky está al mismo nivel que el  panel superior pero en los lados). El problema se presenta el parte  superior de la pantalla por debajo del panel superior. te agradeceré  alguna respuesta

---

### Post by juanuni on 2011-04-08
Bueno ahi esta la imagen....

---

### Post by matias_tati on 2011-04-11
> **juanuni said:**
> Bueno ahi esta la imagen....

Eso es porque Conky esta "barriendo" mas espacio del que necesita para ejecutarse. Copia aca el .conkyrc. Asi lo vemos.

---

### Post by juanuni on 2011-04-16
> **matias_tati said:**
> Eso es porque Conky esta "barriendo" mas espacio del que necesita para ejecutarse. Copia aca el .conkyrc. Asi lo vemos.

Hola gracias, sospecho donde está el problema pero dado que conoces más de conky prefiero que me des un diagnóstico, ahi va la configuración de mi conky



> 
# Conky configuration
# Edited by Izobalax 2009

# set to yes if you want Conky to be forked in the background
background no

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Terminus:size=9

# Text alpha when using Xft
xftalpha 0.8

# Update interval in seconds
update_interval 1.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 1400 50
maximum_width 1400

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no
draw_graph_borders yes

# Stippled borders?
stippled_borders 0

# border margins
border_margin 0

# border width
border_width 0

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color white

# own window options
own_window		yes
own_window_transparent	yes
own_window_type		override
own_window_hints	undecorated,below,sticky,skip_taskbar,skip_pager

# Text alignment, other possible values are commented
alignment top_left
#alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 0
gap_y 0

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase none

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer no

# — Lua Load — #
lua_load ~/.scripts/rings.lua
lua_draw_hook_pre ring_stats

TEXT
#${image /home/juan/.scripts/conky.png -p 0,0 -s 1024x70}
#${offset 946}${voffset 18}${font droid sans:size=8}${color #C0C0C0}${time %H:%M}
${offset 5}${voffset 5}${font Santana:size=10}${color #C0C0C0}GMail - ${font Santana:size=13}${execi 300 python ~/.scripts/gmail.py} 
${offset 868}${voffset -28}${font 20thfont:size=9}${color #C0C0C0}CPU${offset 18}${voffset 0}${font 20thfont:size=9}${color #C0C0C0}RAM${offset -845}${voffset 0}${font 20thfont:size=9}${color #C0C0C0}HDD
#${offset 25}${voffset 0}${font 20thfont:size=10}${color #C0C0C0}VOL
#${offset 130}${voffset -7}${font 20thfont:size=10}${font}${execi 20 #hddtemp /dev/sda | cut -c28-32}
${offset 130}${voffset -10}${font weather:size=20}x${font}${voffset -7} ${execi 10 ~/.scripts/hddmonit.sh} C
#${font weather:size=22}${execi 100 ~/.scripts/conditions.sh}${font}#${voffset -15}  ${execi 100 ~/.scripts/pogodynka.sh}
${offset 965}${voffset -20}${font 20thfont:size=10}${color #C0C0C0}${sysname}${offset -60}${voffset 20}${font OpenLogos:size=14}${color #C0C0C0}u${offset 5}${voffset -6}${font 20thfont:size=8}${pre_exec lsb_release -c -s} ${pre_exec lsb_release -r -s}


---

### Post by juanuni on 2011-04-16
> **matias_tati said:**
> Eso es porque Conky esta "barriendo" mas espacio del que necesita para ejecutarse. Copia aca el .conkyrc. Asi lo vemos.

Olvide decirte que tengo resolución de pantalla de 1024x768, y como podrás apreciar, la imagen que tenías en el conky, está desactivada, pero aún con la imagen de fondo en el conky activada, tenía el mismo problema.

---

