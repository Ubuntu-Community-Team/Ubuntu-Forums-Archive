---
title: "Como configurar mi red y el tiempo en conky"
date: 2008-11-29
forum: Software
---

### Post by LethalBoy on 2008-11-29
Buenas tardes a todos soy nuevo en el mundo de Ubuntu y pues estoy bregando con conky y pues vi uno que me gusto mucho en el post de como se ve tu escritorio, pero necesito configurar la red para q aparezca bien y el tiempo.

aqui tienen uno screenshot de como se ve mi conky ahora mismo:

[http://i34.tinypic.com/2vn3ukn.png](http://i34.tinypic.com/2vn3ukn.png)


Se supone que se vea asi: o sea la conexion, el tiempo, lo de amarok, etc.

[http://i36.tinypic.com/inadf9.jpg](http://i36.tinypic.com/inadf9.jpg)


Espero q me puedan ayudar xD

Este es el conkyrc

> # Use Xft?
use_xft yes
xftfont Sansation:size=9
xftalpha 0.8
text_buffer_size 2048

# Update interval in seconds
update_interval 1

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_type override
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
background yes

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 200 0
maximum_width 225

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 0

# border margins
border_margin 5

# border width
border_width 1

# Default colors and also border colors
default_color white
#default_shade_color black
#default_outline_color white
own_window_colour white

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 25
gap_y 55

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer none


TEXT
${alignr 170}${font DIST Yolks Emoticons:size=100}8${font}

SYSTEM ${hr 2}
${font OpenLogos:size=16}t${font}  Kernel:  ${alignr}${kernel}
${font StyleBats:size=16}A${font} CPU: ${cpu cpu0}% ${alignr}${cpubar 8,60 cpu0}
${font StyleBats:size=16}g${font} RAM:  $memperc% ${alignr}${membar 8,60}
${font StyleBats:size=16}j${font} SWAP: $swapperc% ${alignr}${swapbar 8,60}
${font StyleBats:size=16}q${font} Activity: ${alignr}${uptime}

DATE ${hr 2}
${alignr 125}${font SVI Basic Manual:style=Bold:size=32}${time %H:%M}${font}
${alignc}${time %A %d %B %Y}

HD ${hr 2}
${font PizzaDude Bullets:size=14}g${font} Home:
${fs_free /home}/${fs_size /home} $alignr${fs_bar 285 /home}

NETWORK ${hr 2}
${if_existing /proc/net/route ppp0}
${voffset -6}${font PizzaDude Bullets:size=14}v${font} Up: ${upspeed ppp0} kb/s  $alignr${upspeedgraph ppp0 8,60 789E2D A7CC5C}
${voffset 4}${font PizzaDude Bullets:size=14}r${font} Down: ${downspeed ppp0} kb/s  $alignr${downspeedgraph ppp0 8,60 789E2D A7CC5C}
${voffset 4}${font PizzaDude Bullets:size=14}N${font} Total Up: $alignr${totalup ppp0}
${voffset 4}${font PizzaDude Bullets:size=14}T${font} Total Down: $alignr${totaldown ppp0}
${voffset 4}${font PizzaDude Bullets:size=14}b${font} Public Ip: $alignr${execi 1 ~/.scripts/ip.sh}
${endif}${else}
${font PizzaDude Bullets:size=14}4${font}   Network Not Available
${endif}
TIME ${hr 2}
${if_existing /proc/net/route ppp0}
${voffset -14}${alignr 72}${font ConkyWeather:size=46}${execi 1800 conkyForecast --location=USPR0003--datatype=WF}${font}
${voffset -52}${font Sansation:size=26}${execi 1800 conkyForecast --location=USPR0003 --datatype=HT}${font}
${voffset 0}Condition: ${alignr}${execi 1800 conkyForecast --location=USPR0003 --datatype=CC}
${voffset 0}Wind: ${alignr}${execi 1800 conkyForecast --location=USPR0003 --datatype=WS}
${voffset 0}Humidity: ${alignr}${execi 1800 conkyForecast --location=USPR0003 --datatype=HM}
${endif}${else}
${font PizzaDude Bullets:size=14}4${font}   Time Not Available
${endif}${if_running amarokapp}
MUSIC ${hr 2}
${font Rock Star 2.0:size=14}m${font}${offset 10}${font Sansation:size=12}${execi 10 ~/.scripts/amarok title}
${font Rock Star 2.0:size=14}B${font}${offset 15}${execi 10 ~/.scripts/amarok artist}
${font Rock Star 2.0:size=14}K${font}${offset 17}${execi 10 ~/.scripts/amarok album} (${execi 10 ~/.scripts/amarok year})
${endif}

---

### Post by staar on 2008-11-29
me alegro que te haya gustado mi conky :D, vas a tener q cambiarle algunas cositas para que te ande bien

bueno vamos por partes...

en la parte de los discos donde tenes asi
```
{fs_bar 285 /home}
```
tiene que estar asi
```
{fs_bar 8,60 /home}
```

la parte de la red es mas facil todavia, reemplaza todos los "ppp0" por "eth0" (o "eth1", o "wlan0", o la interfaz que tengas conectada a internet), esto pasa por que yo me conecto por modem (ppp) y no por la placa de red (eth) o placa inalambrica (wlan)

en la parte del clima, lo mismo, cambia el "ppp0"

en la parte del amarok esta linea
```
${if_running amarokapp}
```
indica que lo restante se muestra solo si el amarok esta abierto, y en la captura lo tenes cerrado :P :D

acordate de poner los scripts en la carpeta oculta .scripts en tu home, y las fuentes en .fonts

saludos

---

### Post by feche_mza on 2008-11-29
para el amarok lo podes hacer sin ningún script con dcop que seguro lo tenes instalado para el complemento del emesene que te muestra lo que estas escuchando tenes que poner:> ${exec dcop amarok player title}y vas reemplazando por el nombre del artista y el disco asi:> ${exec dcop amarok player artist}
${exec dcop amarok player album}eso si en este caso es impresindible que le mandes al principio de todo el > ${if_running amarokapp}por que de lo contrario se te cuelga conki cuando no tenes abierto el amarok
lo mismo con la ip publica podes mandarle > ${addr eth0}en lugar de el execi para ejecutar el script

---

### Post by staar on 2008-11-29
lo tuve un tiempo asi, pero me consumia muchos mas recursos que con el script, asi que lo saque, creo recordar que la pagina del manual del conky decia algo de esto...

saludos

---

### Post by LethalBoy on 2008-11-29
staar, hize lo que me pedistes pero cuando reemplazo los ''ppp0'' por ''eth0'' corro el conky y no me sale nada en la pantalla!! ahora, si pongo los ppp0 pues el conky me corre pero en red me sale red no disponible. Q puedo hacer y a q se debe esto

---

### Post by staar on 2008-11-30
> **LethalBoy said:**
> staar, hize lo que me pedistes pero cuando reemplazo los ''ppp0'' por ''eth0'' corro el conky y no me sale nada en la pantalla!! ahora, si pongo los ppp0 pues el conky me corre pero en red me sale red no disponible. Q puedo hacer y a q se debe esto

mmm...en esta parte
```
${voffset 4}${font PizzaDude Bullets:size=14}b${font} Public Ip: $alignr${execi 1 ~/.scripts/ip.sh}
[COLOR="Red"]**${endif}**[/COLOR]${else}
${font PizzaDude Bullets:size=14}4${font} Network Not Available
```
borra ese ${endif}, me parece que es  ese el error (que tambien estaba en mi conkyrc :D)

saludos

---

### Post by LethalBoy on 2008-11-30
gracias staar ahora si me funciono!! ahora una pregunta, como puedo hacer para que aparezca lo q escucho en el amarok y en emesene?  ya que cuando escucho una cancion donde sale lo de musica en el conky se keda asi -> {}

Que debo hacer? ya que el script del amarok lo tengo :(

---

### Post by sergiom99 on 2008-11-30
a mi me pasa lo mismo,pero solo cuando reemplazo el ppp0 de la parte del clima.
Con la parte de red quedo perfecto.

Otra cosa, se le puede dar transparencia al fondo? para que no quede negro solido.

Gracias!

---

### Post by feche_mza on 2008-11-30
tenes que instalar [COLOR="DarkGreen"]**python-dcop**[/COLOR] buscalo por synaptic

---

### Post by sergiom99 on 2008-11-30
> **feche_mza said:**
> tenes que instalar [COLOR="DarkGreen"]**python-dcop**[/COLOR] buscalo por synaptic

Lo instale, pero cuando cambio el ppp0 en la parte del tiempo a eth1, me tira este error al arrancar:

```

sergio@kubuntu:~$ conky
Conky: $else: no matching $if_*
Conky: $endif: no matching $if_*
Conky: forked to background, pid is 18403
Conky: desktop window (1400010) is subwindow of root window (1a6)
Conky: window type - override
Conky: drawing to created window (a00001)
Conky: drawing to double buffer
Conky: you don't need that many fonts, sorry.

```

EDIT: 
ya lo encontre! sobra un [COLOR="Red"]endif[/COLOR] tambien en la parte del Clima, igual que con la red.

---

### Post by staar on 2008-11-30
> como hago para eliminar tanto espacio entre el logo y el texto? no me doy cuenta...

con la variable ${voffset *valor*} regulas la altura, ponela al comienzo de la linea, el valor puede ser negativo o positivo ;)

saludos

---

### Post by feche_mza on 2008-11-30
> **sergiom99 said:**
> Lo instale, pero cuando cambio el ppp0 en la parte del tiempo a eth1, me tira este error al arrancar:


sergio lo de python-dcop era en respuesta a este mensaje > **LethalBoy said:**
> gracias staar ahora si me funciono!! ahora una pregunta, como puedo hacer para que aparezca lo q escucho en el amarok y en emesene?  ya que cuando escucho una cancion donde sale lo de musica en el conky se keda asi -> {}

Que debo hacer? ya que el script del amarok lo tengo :(
no me di cuenta de citarlo cuando lo puse, es para que muestre lo que estas escuchando en el emesene y en el conky.Para ver como viene la mano con tu problema pone la configuracion de tu conky porfa

---

### Post by sergiom99 on 2008-11-30
gracias feche, ya lo arregle, hay unos endif de mas en el conkyrc original.

---

### Post by LethalBoy on 2008-11-30
> **feche_mza said:**
> tenes que instalar [COLOR="DarkGreen"]**python-dcop**[/COLOR] buscalo por synaptic

ya lo tengo instalado!! pero cuando pongo alguna cancion me sale lo mismo en el conky o sea en el area donde dice musica en mi escritorio sale lo mismo o sea {}

alguien q me pueda ayudar :s

aki tienen screenshot:

[http://i33.tinypic.com/2lddfu9.jpg](http://i33.tinypic.com/2lddfu9.jpg)

---

### Post by sergiom99 on 2008-11-30
eso me pasa cuando las tags de la cancion estan vacias. Probalo con algun mp3 que tenga completos los tags de titulo, artista y album.
Ademas necesitas darle permisos de ejecucion al script de amarok.sh

---

### Post by feche_mza on 2008-12-01
> **LethalBoy said:**
> ya lo tengo instalado!! pero cuando pongo alguna cancion me sale lo mismo en el conky o sea en el area donde dice musica en mi escritorio sale lo mismo o sea {}

alguien q me pueda ayudar :s
proba poniendo esto > 
${exec dcop amarok player title}
${exec dcop amarok player artist} 
${exec dcop amarok player album}

 en lugar del script para el amarok, es verdad lo que dice staar consume mas recursos pero fue la unica forma de hacerlo andar (en mi caso) por que el script nunca me ando

---

### Post by LethalBoy on 2008-12-02
Gracias a todos!! por haberme ayudado jeje pero tengo 2 preguntsa alguien sabe como se puede cambiar la temperatura del conky a grados farenheit? y como puedo cambiar la hora del conky a formato de 12h

---

### Post by staar on 2008-12-02
> **LethalBoy said:**
> Gracias a todos!! por haberme ayudado jeje pero tengo 2 preguntsa alguien sabe como se puede cambiar la temperatura del conky a grados farenheit? y como puedo cambiar la hora del conky a formato de 12h

de nada ;)... para cambiar la temperartura fijate [[COLOR="Blue"]ACA[/COLOR]]("http://ubuntuforums.org/showthread.php?t=869328"), es el post original del conkyforecast (el script del clima), creo q tenes q agregar un -imperial por ahi :)
para la hora, se usa el formato strftime, la documentacion la encontras [[COLOR="#0000ff"]ACA[/COLOR]]("http://docs.python.org/lib/module-time.html"), tendrias q cambiar el %H por %I... ;)

saludos

---

### Post by Aguchob on 2008-12-05
```
# Use Xft?
use_xft yes
xftfont Sansation:size=9
xftalpha 0.8
text_buffer_size 2048

# Update interval in seconds
update_interval 1

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_type override
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
background yes

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 200 0
maximum_width 225

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 0

# border margins
border_margin 5

# border width
border_width 1

# Default colors and also border colors
default_color white
#default_shade_color black
#default_outline_color white
own_window_colour white

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 25
gap_y 55

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

# Add spaces to keep things from moving about? This only affects certain objects.
use_spacer none


TEXT
${alignr 170}${font DIST Yolks Emoticons:size=100}8${font}

${color red}Sistema ${hr 2}$color
${font OpenLogos:size=16}t${font} Kernel: ${alignr}${kernel}
${font StyleBats:size=16}A${font} CPU: ${cpu cpu0}% ${alignr}${cpubar 8,60 cpu0}
${font StyleBats:size=16}g${font} RAM: $memperc% ${alignr}${membar 8,60}
${font StyleBats:size=16}j${font} SWAP: $swapperc% ${alignr}${swapbar 8,60}
${font StyleBats:size=16}q${font} Actividad: ${alignr}${uptime}

FECHA ${hr 2}
${alignr 125}${font SVI Basic Manual:style=Bold:size=32}${time %H:%M}${font}
${alignc}${time %A %d %B %Y}

${color red}ADMINISTRACION DE DISCOS ${hr 2}$color
${font PizzaDude Bullets:size=14}g${font} Home:
${fs_free /home}/${fs_size /home} $alignr${fs_bar 8,60 /home}
${font PizzaDude Bullets:size=14}g${font} Windows XP:
${fs_free /home}/${fs_size /home} $alignr${fs_bar 8,60 /home}



${color red}REDES ${hr 2}$color
${if_existing /proc/net/route eth1}
${voffset -6}${font PizzaDude Bullets:size=14}O${font}   Vel. Subida: ${upspeed eth1} kb/s ${alignr}${upspeedgraph eth1 8,60 F57900 FCAF3E}
${voffset 4}${font PizzaDude Bullets:size=14}U${font}   Vel. Bajada: ${downspeed eth1} kb/s ${alignr}${downspeedgraph eth1 8,60 F57900 FCAF3E}
${voffset 4}${font PizzaDude Bullets:size=14}N${font}   Subido: ${alignr}${totalup eth1}
${color4}${voffset 4}${font PizzaDude Bullets:size=14}T${font}   Bajado: ${alignr}${totaldown eth1}
${voffset 4}${font PizzaDude Bullets:size=14}a${font}   Ip Local: ${alignr}${addr eth1}
${voffset 4}${font PizzaDude Bullets:size=14}b${font}   Ip Publica: ${alignr}${execi 1 ~/.scripts/ip.sh}
${else}
${font PizzaDude Bullets:size=14}4${font} Red No Disponible
${endif}

${color red}CLIMA ${hr 2}$color
${if_existing /proc/net/route eth1}
${voffset -14}${alignr 72}${font ConkyWeather:size=46}${execi 1800 conkyForecast --location=ARCA0023 --datatype=WF}${font}
${voffset -52}${font Sansation:size=26}${execi 1800 conkyForecast --location=ARCA0023 --datatype=HT}${font}

${voffset 0}Condicion: ${alignr}${execi 1800 conkyForecast --location=ARCA0023 --datatype=CC}
${voffset 0}Viento: ${alignr}${execi 1800 conkyForecast --location=ARCA0023 --datatype=WS}
${voffset 0}Humedad: ${alignr}${execi 1800 conkyForecast --location=ARCA0023 --datatype=HM}
${else}
${font PizzaDude Bullets:size=14}4${font} Tiempo No Disponible
${endif}${if_running amarokapp}
${color red}MUSICA ${hr 2}$color
${font Rock Star 2.0:size=14}m${font}${offset 10}${font Sansation:size=12}${execi 10 ~/.scripts/amarok.sh title}
${font Rock Star 2.0:size=14}B${font}${offset 15}${execi 10 ~/.scripts/amarok.sh artist}
${font Rock Star 2.0:size=14}K${font}${offset 17}${execi 10 ~/.scripts/amarok.sh album} (${execi 10 ~/.scripts/amarok.sh year})
${endif} 
```


Hola gente como andan bueno me cope con esto del conky y me gusto como lo tenian ordenado uds asi q me puse a chusmear de paso tb me puse a traducirlo y ya esta todo en castellano jejejeje lo unico que me resta es agregar una linea sobre mi particion de windows que nose como seria y queria preguntar 

${font PizzaDude Bullets:size=14}g${font} Windows XP:
${fs_free /home}/${fs_size /home} $alignr${fs_bar 8,60 /home}


q tengo q poner??? donde dice home para q me tome la particion de windows

---

### Post by Aguchob on 2008-12-05
hola chicos como andan bueno ya pude configurar todo despues de tanto probar y renegar jajajajaj.. ahora les dejo como deje mi conky

```
# Use Xft?
use_xft yes
xftfont Sansation:size=9
xftalpha 0.8
text_buffer_size 2048

# Update interval in seconds
update_interval 1

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_type override
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
background yes

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 200 0
maximum_width 225

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 0

# border margins
border_margin 5

# border width
border_width 1

# Default colors and also border colors
default_color white
#default_shade_color black
#default_outline_color white
own_window_colour white

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 25
gap_y 55

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

# Add spaces to keep things from moving about? This only affects certain objects.
use_spacer none


TEXT
${alignr 170}${font DIST Yolks Emoticons:size=100}8${font}

${color red}Sistema ${hr 2}$color
${font OpenLogos:size=16}t${font} Kernel: ${alignr}${kernel}
${font StyleBats:size=16}A${font} CPU: ${cpu cpu0}% ${alignr}${cpubar 8,60 cpu0}
${font StyleBats:size=16}g${font} RAM: $memperc% ${alignr}${membar 8,60}
${font StyleBats:size=16}j${font} SWAP: $swapperc% ${alignr}${swapbar 8,60}
${font StyleBats:size=16}q${font} Actividad: ${alignr}${uptime}

FECHA ${hr 2}
${alignr 125}${font SVI Basic Manual:style=Bold:size=32}${time %H:%M}${font}
${alignc}${time %A %d %B %Y}

${color red}ADMINISTRACION DE DISCOS ${hr 2}$color
${font PizzaDude Bullets:size=14}g${font} Home:
${fs_free /home}/${fs_size /home} $alignr${fs_bar 8,60 /home}
${font PizzaDude Bullets:size=14}g${font} Windows XP:
${fs_free /media/disk}/${fs_size /media/disk} $alignr${fs_bar 8,60 /media/disk}
${font PizzaDude Bullets:size=14}g${font} ROOT:
${fs_free_perc /}%   ${fs_bar 6 /}$color



${color red}REDES ${hr 2}$color
${if_existing /proc/net/route eth1}
${voffset -6}${font PizzaDude Bullets:size=14}O${font}   Vel. Subida: ${upspeed eth1} kb/s ${alignr}${upspeedgraph eth1 8,60 F57900 FCAF3E}
${voffset 4}${font PizzaDude Bullets:size=14}U${font}   Vel. Bajada: ${downspeed eth1} kb/s ${alignr}${downspeedgraph eth1 8,60 F57900 FCAF3E}
${voffset 4}${font PizzaDude Bullets:size=14}N${font}   Subido: ${alignr}${totalup eth1}
${color4}${voffset 4}${font PizzaDude Bullets:size=14}T${font}   Bajado: ${alignr}${totaldown eth1}
${voffset 4}${font PizzaDude Bullets:size=14}a${font}   Ip Local: ${alignr}${addr eth1}
${voffset 4}${font PizzaDude Bullets:size=14}b${font}   Ip Publica: ${alignr}${execi 1 ~/.scripts/ip.sh}
${else}
${font PizzaDude Bullets:size=14}4${font} Red No Disponible
${endif}

${color red}CLIMA ${hr 2}$color
${if_existing /proc/net/route eth1}
${voffset -14}${alignr 72}${font ConkyWeather:size=46}${execi 1800 conkyForecast --location=ARCA0023 --datatype=WF}${font}
${voffset -52}${font Sansation:size=26}${execi 1800 conkyForecast --location=ARCA0023 --datatype=HT}${font}

${voffset 0}Condicion: ${alignr}${execi 1800 conkyForecast --location=ARCA0023 --datatype=CC}
${voffset 0}Viento: ${alignr}${execi 1800 conkyForecast --location=ARCA0023 --datatype=WS}
${voffset 0}Humedad: ${alignr}${execi 1800 conkyForecast --location=ARCA0023 --datatype=HM}
${else}
${font PizzaDude Bullets:size=14}4${font} Tiempo No Disponible
${endif}${if_running amarokapp}
${color red}MUSICA ${hr 2}$color
${font Rock Star 2.0:size=14}m${font}${offset 10}${font Sansation:size=12}${execi 10 ~/.scripts/amarok.sh title}
${font Rock Star 2.0:size=14}B${font}${offset 15}${execi 10 ~/.scripts/amarok.sh artist}
${font Rock Star 2.0:size=14}K${font}${offset 17}${execi 10 ~/.scripts/amarok.sh album} (${execi 10 ~/.scripts/amarok.sh year})
${endif}

```

un comentario para los q no podian hacer andar el amarok ... bueno es re facil... solo tiene que poner el script en la carpeta .script de conky y luego boton derecho propiedades y poner ejecutar como programa jejej...

luego de eso se van al conky y si se fijan bien bien bien dice amarok.. no "amarok.sh" por eso es q les robota en la terminal..a algunos y les da el error si queiren pueden copiar mi conky que se basa en estos ya puestos felicitaciones al autor y que de paso esta traducido, corregido el tema del amarok y añadi root y particon XP en mi caso aca des paso les dejo la imagen 
 
[IMG]http://img205.imageshack.us/img205/2776/pantallazomo1.png[/IMG]

---

### Post by sergiom99 on 2008-12-05
> **Aguchob said:**
> 
${font PizzaDude Bullets:size=14}g${font} Windows XP:
${fs_free /home}/${fs_size /home} $alignr${fs_bar 8,60 /home}


q tengo q poner??? donde dice home para q me tome la particion de windows

supongamos que tu particion sea /media/windows, eso es lo que tenes que poner.
si la estas viendo desde ubuntu, en todo caso posteanos la salida del comando 'df -h' (sin las comillas) y vemos donde la esta montando.

---

### Post by Aguchob on 2008-12-05
```
Conky: forked to background, pid is 7421
agustin@agustin-desktop:~$ 
Conky: desktop window (e000b6) is subwindow of root window (8b)
Conky: window type - override
Conky: drawing to created window (4600001)
Conky: drawing to double buffer

```


Es esto normal en conky sobre todo donde dice forked to backgorund, pid is... porq antes no me decia eso nose porq me empezo a salir ahora..

que significa que sea forked al fondo de pantalla??

---

### Post by Hei Ku on 2008-12-05
forked to background, quiere decir que pasa a ejecutarse en segundo plano, sin necesidad de tener una terminal abierta. Con un comportamiento mas similar al de un servicio, que al de un programa que tenes abierto todo el tiempo. Nada mas que eso.

---

### Post by nabi_gudy8a on 2010-08-29
PORFAAA ayudenme... intento poner lo del clima en el conky y no logro nada...

pueden decirme qué cosas tengo que tener instaladas o donde debo tener guardados los archivos???

quiero que esto...
```

${color red}CLIMA ${hr 2}$color
${if_existing /proc/net/route eth1}
${voffset -14}${alignr 72}${font ConkyWeather:size=46}${execi 1800 conkyForecast --location=ARCA0023 --datatype=WF}${font}
${voffset -52}${font Sansation:size=26}${execi 1800 conkyForecast --location=ARCA0023 --datatype=HT}${font}

${voffset 0}Condicion: ${alignr}${execi 1800 conkyForecast --location=ARCA0023 --datatype=CC}
${voffset 0}Viento: ${alignr}${execi 1800 conkyForecast --location=ARCA0023 --datatype=WS}
${voffset 0}Humedad: ${alignr}${execi 1800 conkyForecast --location=ARCA0023 --datatype=HM}
${else}
${font PizzaDude Bullets:size=14}4${font} Tiempo No Disponible
${endif}
```

me ande...

PORFAAA, AYUDENMEEEE!!!

---

