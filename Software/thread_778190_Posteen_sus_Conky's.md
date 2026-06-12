---
title: "Posteen sus Conky's"
date: 2008-05-01
forum: Software
---

### Post by Mauro22 on 2008-05-01
Buenas!!


Despues de 2 dias retocando la configuracion de conky (y viendo que en HH no parpadea) quede como loco!


Creo que me quedo como me gusta y "aprendi" un monton de este "lenguaje".
Gracias a meduza y a internet por los consejos dados.

--Una lastima que los acentos no salgan--

```

background yes
use_xft yes
xftfont DejaVu Serif:size=9
xftalpha 0.5
update_interval 1.0
total_run_times 0
own_window no
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 300 5
maximum_width 350
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color yellow
default_shade_color red
default_outline_color green
alignment top_left
gap_x 12
gap_y 48
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no

TEXT
${color #FFFFFF}
${hr 4}
$alignc Ubuntu Hardy Heron Conky By Darkfire
$alignc $sysname $kernel ($machine)
${hr 4}
${color red}
HARDWARE ${hr 2}
${color white}CPU ${color orange} @${freq_g}MHz   ${cpu cpu0}%  $cpubar
${color white}RAM ${color orange} ($memmax)   $memperc%  ${membar 6}
${color white}Swap ${color orange}($swapmax)   $swapperc%  ${swapbar 6}
${color red}Temperaturas ${hr 1}  
${color white}WesterDigital (160GB) ${color red}$alignr${execi 300 nc localhost 7634 | cut -c31-32 ;} Grados
${color white}Maxtor (80GB) ${color red}$alignr${execi 300 nc localhost 7634 | cut -c61-62 ;} Grados
${color white}GeForce 6200@${execi 20 nvidia-settings -q GPUCurrentClockFreqs | grep "Attribute" | cut -d" " -f6 | tr -s "," "/" | tr -d "."} MHz   ${color red}$alignr${execi 150 nvclock -T |grep "temperature" | grep '[0-9][0-9]' -o} Grados
${color white}AMD Athlon 3200+ 64bits ${color red}$alignr${execi 10 cat /sys/devices/platform/w83627hf.656/temp1_input | cut -c1,2} Grados
${color white}-> AMD Core ${color red}$alignr${execi 10 cat /sys/bus/pci/drivers/k8temp/000*/temp1_input | cut -c1,2} Grados
${color white}Motherboard ${color red}$alignr${execi 10 cat /sys/devices/platform/w83627hf.656/temp2_input | cut -c1,2} Grados
${color white}Ventilador 1  ${color green}$alignr${execi 10 cat /sys/devices/platform/w83627hf.656/fan2_input} RPMs
${color red}Discos ${hr 1}
${color white}/ (Sistema)
${fs_used /}  /  ${color red}${fs_size /}${color orange}${alignr}${fs_bar 5,120 /}
${color white}/home (Datos)
${fs_used /home} / ${color red}${fs_size /home}${color orange}${alignr}${fs_bar 5,120 /home}
${color red}${hr 2}
${color slate grey}
RED ${hr 2}
${exec iwconfig wlan0 | grep "ESSID" | cut -c 25-47}
Velocidad: ${color white}${wireless_bitrate wlan0}   ${alignr}${color slate grey}Fuerza: ${color white}${wireless_link_qual_perc wlan0}%
${color slate grey}IP (interna) $alignr${color white}${addr wlan0}
${color slate grey}IP (externa) $alignr${color white}${execi 600 ~/.conky/wan}
${color slate grey}Bajando a:  ${color white}${downspeed wlan0}KB/s ${alignr}${color slate grey}Subiendo a:  ${color white}${upspeed wlan0}KB/s
${color }${downspeedgraph wlan0 25,125 00ff00 00ff00}${alignr}${upspeedgraph wlan0 25,125 ff0000 ff0000}
${color slate grey}Totales: ${totaldown wlan0} ${alignr} ${totalup wlan0}${color slate grey}
${hr 2}
${color #3399FF}
GMAIL ${hr 2}
${texeci 150 python ~/.conky/gmail.py}
${hr 2}
${color #FFFF00}
MUSICA ${hr 2}
${alignc}Estas escuchando
Artista $alignr ${execi 10 ~/.conky/amarok artist}
Titulo $alignr ${execi 10 ~/.conky/amarok title}
${color orange}${execibar 1 ~/.conky/amarok progress}${color #FFFF00}
Album $alignr ${execi 10 ~/.conky/amarok album}
${hr 2}
${color lightgrey}
FORTUNA ${hr 2}
${execi 120 fortune -s | fold -w50}
${hr 2}
${color #999999}
${hr 2}
$alignc POWERED BY

${font OpenLogos:size=45}v m S t

```

---

### Post by sajnox on 2008-05-01
A mi conky me puede.

Les dejo el mio, y no solo la imagen hay que dejar tambien el .conkyrc



```
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes

# Update interval in seconds
update_interval 1.50

# Minimum size of text area
# minimum_size 180 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
font monospace:size=12
uppercase no # set to yes if you want all text to be in uppercase

# X font when Xft is disabled, you can pick one with program xfontsel
#font 7x12
#font 6x10
#font 7x13
#font 8x13
#font 7x12
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*
#font -artwiz-snap-normal-r-normal-*-*-100-*-*-p-*-iso8859-1

# Use Xft?
use_xft no

# Xft font when Xft is enabled
#xftfont Bitstream Vera Sans Mono:size=8
#xftfont Deja Vu Sans Mono:size=8
xftfont Courier:size=8

# Text alpha when using Xft
#xftalpha 0.8

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color white

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment bottom_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 20
gap_y 15

# stuff after 'TEXT' will be formatted on screen

TEXT
$color
${color white}SISTEMA ${hr 2}$color
$nodename $sysname $kernel on $machine

${color white}CPU ${hr 2}$color
${freq} MHz${alignr}Carga: ${loadavg}
$cpubar
${cpugraph 20 9900ff 0030f0}

${color white}MEMORIA ${hr 2}$color
RAM: Total: $memmax / En uso: $mem / %En uso: $memperc% 
${membar 6}$color 
Swap: Total: $swapmax / En uso: $swap / %En uso: $swapperc%
${swapbar 6}$color

${color white}DISCO ${hr 2}$color
HDA0 : Tamaño: ${fs_size /} / Usado ${fs_used /} / Libre ${fs_free /} ${fs_free_perc /}%
${fs_bar 6 /}$color
HDA1 : Tamaño: ${fs_size /media/hda2} / Usado ${fs_used /media/hda2} / Libre ${fs_free /media/hda2} ${fs_free_perc /media/hda2}%
${fs_bar 6 /media/hda2}$color
Datos : Tamaño: ${fs_size /media/hdb5} / Usado ${fs_used /media/hdb5} / Libre ${fs_free /media/hdb5} ${fs_free_perc /media/hdb5}%
${fs_bar 6 /media/hdb5}

${color white}PROCESOS ${hr 2}$color
Total: ${processes} ${alignr}Corriendo: ${running_processes}
NOMBRE             ID          CPU %       MEM %
${top name 1}   ${top pid 1}     ${top cpu 1}      ${top mem 1}
${top name 2}   ${top pid 2}     ${top cpu 2}      ${top mem 2}
${top name 3}   ${top pid 3}     ${top cpu 3}      ${top mem 3}
${top name 4}   ${top pid 4}     ${top cpu 4}      ${top mem 4}
${top name 5}   ${top pid 5}     ${top cpu 5}      ${top mem 5}

${color white}RED (${addr eth0}) ${hr 2}$color
Recibido: $color${downspeed eth0} kB/s ${alignr}Enviado: ${upspeed eth0} kB/s
${downspeedgraph eth0 25,140 206900 3bc300} ${alignr}${upspeedgraph eth0
25,140 f1d900 d01800}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
Enviando: ${tcp_portmon 32768 61000 count} Recibiendo: ${tcp_portmon 1 
32767 count}${alignr}Total: ${tcp_portmon 1 65535 count}
ENVIANDO ${alignr} SERVICIO REMOTO/PUERTO
${tcp_portmon 32768 61000 rhost 0} ${alignr} ${tcp_portmon 32768 61000 rservice 0}
${tcp_portmon 32768 61000 rhost 1} ${alignr} ${tcp_portmon 32768 61000 rservice 1}
${tcp_portmon 32768 61000 rhost 2} ${alignr} ${tcp_portmon 32768 61000 rservice 2}
${tcp_portmon 32768 61000 rhost 3} ${alignr} ${tcp_portmon 32768 61000 rservice 3}
${tcp_portmon 32768 61000 rhost 4} ${alignr} ${tcp_portmon 32768 61000 rservice 4}
RECIBIENDO ${alignr} SERVICIO LOCAL/PUERTO
${tcp_portmon 1 32767 rhost 0} ${alignr} ${tcp_portmon 1 32767 lservice 0}
${tcp_portmon 1 32767 rhost 1} ${alignr} ${tcp_portmon 1 32767 lservice 1}
${tcp_portmon 1 32767 rhost 2} ${alignr} ${tcp_portmon 1 32767 lservice 2}
${tcp_portmon 1 32767 rhost 3} ${alignr} ${tcp_portmon 1 32767 lservice 3}
${tcp_portmon 1 32767 rhost 4} ${alignr} ${tcp_portmon 1 32767 lservice 4}
${color white}${hr 2}$color

```

---

### Post by totoloco on 2008-05-02
Solo hora, temperatura y calendario.
Los recursos los tengo x Gkrellm.

Adjunto zip q tiene los scripts q usa el conky.

salU

---

### Post by PatoDB on 2008-05-03
Aca esta mi nuevo Conky...

Recien Estrenado... =)

Aun faltan algunos retoques... Quizas le ponga la cancion que esta sonando en el Exaile (si se puede.. :P) Y quiero ver si le puedo poner un reloj grande arriba...Alguien sabe si se puede? y Como?

[IMG]http://img370.imageshack.us/img370/3245/conkyav4.png[/IMG]


```

use_xft yes
xftfont Terminus:size=8
xftalpha 0.8
update_interval 2.0
total_run_times 0
own_window no
double_buffer yes
minimum_size 1000 5
draw_shades yes
draw_outline no
draw_borders no
stippled_borders 8
border_margin 4
border_width 1
default_color white
default_shade_color black
default_outline_color white
alignment top_left
gap_x 575
gap_y 140
no_buffers yes
uppercase no
cpu_avg_samples 2
net_avg_samples 2
override_utf8_locale no
use_spacer yes

TEXT


${offset 240}${color #ffcb48}${color #ffcb48}  Ubuntu Linux 8.04
${offset 240}${color slate grey}UpTime: ${color }$uptime

${offset 240}${color slate grey}CPU:${color } $cpu% ${acpitemp}C
${offset 240}${cpugraph 20,130 000000 ffffff}
${offset 240}${color slate grey}Running:   ${color }$running_processes

${offset 240}${color slate grey}Highest CPU:
${offset 240}${color #ddaa00} ${top name 1}${top_mem cpu 1}
${offset 240}${color lightgrey} ${top name 2}${top cpu 2}
${offset 240}${color lightgrey} ${top name 3}${top cpu 3}
${offset 240}${color lightgrey} ${top name 4}${top cpu 4}

${offset 240}${color slate grey}Highest MEM:
${offset 240}${color #ddaa00} ${top_mem name 1}${top_mem mem 1}
${offset 240}${color lightgrey} ${top_mem name 2}${top_mem mem 2}
${offset 240}${color lightgrey} ${top_mem name 3}${top_mem mem 3}
${offset 240}${color lightgrey} ${top_mem name 4}${top_mem mem 4}

${offset 240}${color slate grey}MEM:  ${color } $memperc% $mem/$memmax
${offset 240}${membar 3,100}
${offset 240}${color slate grey}SWAP: ${color }$swapperc% $swap/$swapmax
${offset 240}${swapbar 3,100}

${offset 240}${color slate grey}HDA4:    ${color }${fs_free /media/disk}/${fs_size /media/disk}
${offset 240}${fs_bar 3,100 /media/disk}

${offset 240}${color slate grey}HOME:  ${color }${fs_free /home}/${fs_size /home}
${offset 240}${fs_bar 3,100 /home}

${offset 240}${color slate grey}NET: 
${offset 240}${color}Up: ${color }${upspeed eth0} k/s
${offset 240}${upspeedgraph eth0 20,130 000000 ffffff}
${offset 240}${color}Down: ${color }${downspeed eth0}k/s${color}
${offset 240}${downspeedgraph eth0 20,130 000000 ffffff}


```

---

### Post by MetallicA15 on 2008-05-03
Perdón por no postear el código, ví esto de "conky" y no sabía de su existencia. Lo bajé y le saqué una foto default:

[[IMG]http://www.uploadfilesystem.com/en/files/08/05/03/tn_3iS24364.jpg[/IMG]](http://www.uploadfilesystem.com/en//viewimage.php?file=files/08/05/03/3iS24364.png)

Lo que si no pude encontrar el archivo de configuración =S.

PD; Soy nuevo en esta gran comunidad =).

---

### Post by Mauro22 on 2008-05-03
El archivo de configuracion se llama .conkyrc (con el punto adelante porque esta oculto)

Y se encuentra en tu home

/home/nombredeusuario/.conkyrc

---

### Post by MetallicA15 on 2008-05-03
No tenía ningún archivo .conkyrc, busqué en /usr/share/doc/conky/examples y descomrpimí y copié el archivo en /Home/usuario, pero cuando le cambio el nombre a ".conkyrc" y ejecuto desde la terminal el programa no se ejecuta =S.... si retiro el .conkyrc y ejecuto nuevamente el programa, funciona de 10.

¿Qué estoy haciendo mal?


***_[COLOR="Red"]EDIT: Ya lo solucioné =)[/COLOR]_***

---

### Post by sergiom99 on 2008-05-03
como hago para arrancar conky?? lo instale con adept y lo hice correr por un momento con sudo conky, pero cerre la consola y se jue!

---

### Post by MeduZa on 2008-05-03
> **sergiom99 said:**
> como hago para arrancar conky?? lo instale con adept y lo hice correr por un momento con sudo conky, pero cerre la consola y se jue!

system > preferences > sessions
apretas add y escribis conky en los 3 casilleros y listo

---

### Post by sergiom99 on 2008-05-03
uso KDE, busque pero no pude encontrar algo equivalente :-(

---

### Post by Hernán-Amaya on 2008-05-03
todavía sigo viendo que poner en mi conky pero encontré esto por ahí les sirve

[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

---

### Post by Hei Ku on 2008-05-03
> **sergiom99 said:**
> uso KDE, busque pero no pude encontrar algo equivalente :-(

Como que no? Y que es SuperKaramba? Instalalo por adept, y despues andate a kde-look.org y en la seccion Karamba te podes empachar de cosas.
Personalmente te recomiendo el Liquid Weather y el AIO (all in one) que permite agregarle plugins de distintas cosas.

Con todo respeto a los gnomeros, KDE le saca el trapo al momento de "tunear" el escritorio.

---

### Post by sergiom99 on 2008-05-04
gracias capo, se fue conky y entro Karamba.
Ahora tengo q ver como hacerlo andar solo.

---

### Post by Hei Ku on 2008-05-04
> **sergiom99 said:**
> gracias capo, se fue conky y entro Karamba.
Ahora tengo q ver como hacerlo andar solo.

Te referis a que arranque solo al iniciar? Fijate que tiene una opcion, y si no, con grabar la sesion actual como predeterminada deberia arrancar solito.

---

### Post by MeduZa on 2008-05-04
> **Hei Ku said:**
> Como que no? Y que es SuperKaramba? Instalalo por adept, y despues andate a kde-look.org y en la seccion Karamba te podes empachar de cosas.
Personalmente te recomiendo el Liquid Weather y el AIO (all in one) que permite agregarle plugins de distintas cosas.

Con todo respeto a los gnomeros, KDE le saca el trapo al momento de "tunear" el escritorio.

es verdad, lo probe y es mucho mas lindo el kde, pero sigo usando Gnome ^_^

---

### Post by sergiom99 on 2008-05-04
> **Hei Ku said:**
> Te referis a que arranque solo al iniciar? Fijate que tiene una opcion, y si no, con grabar la sesion actual como predeterminada deberia arrancar solito.

no, en realidad me cuesta un poquito hacer arrancar al liquid weather, me paso que un par de veces arranca y se cuelga y no termina de cargar.

tenes algun otro para recomendar?

---

### Post by Hei Ku on 2008-05-04
el AIO, que tiene distintos plugins para agregarle cosas, iconos, cambiarle el skin, etc.

---

### Post by sergiom99 on 2008-05-04
lo tengo puesto, pero no puedo hacer que me de bola con el tema de la bateria.
ahora esta asi:
AC directory: "/proc/acpi/ac_adapter/ACAD/"
battery directory: "/proc/acpi/battery/BAT0/"

pero en la solapa de bateria no dice nada de nada!

---

### Post by Hei Ku on 2008-05-04
te fijaste que esos archivos existan?
en la terminal pone:
cat /proc/acpi/ac_adapter/ACAD/
cat /proc/acpi/battery/BAT0/

Yo lo use en su momento con la temperatura de los discos, y anduvo bien despues de cambiar la ruta, porque Ubuntu tiene algunas carpetas distintas al resto de las distros. (heredado de Debian)

---

### Post by sergiom99 on 2008-05-04
si, existen ambas y dentro tienen archivos state, donde dice la carga de la bateria, o si esta enchufada o no.
si en el path pongo xxx/state, en la pantalla del AIO dice "check your paths"

---

### Post by MeduZa on 2008-05-05
holas, despues de un rato de renegar con el conky logre esto que para mi gusto quedo mas o menos como yo queria, detecta mis unidades de disco extraibles (camara, SDs y otras) y tiene todo lo que necesito saber a la vista y en la comodidad del desktop donde no molesta.
Lo bueno es que logre que todo sea dinamico asi si algo cambia no tengo que volver a editar el config, aunque siempre ahi detalles que retocar (Como la F de Memory fan que la puse en minuscula y el % de velocidad del CPU que en ese momento estaba a menos de 50% y aun no se como calcularlo dinamicamente o extraerlo del cpufreq)

Espero les guste y les sirva.

Saludos

---

### Post by PatoDB on 2008-05-05
0.0

Wow Meduza!!!

Te quedo alucinante!!!

Tendria que ponerme las pilas y retocar un poco el mio... :P


Felicitaciones por el trabajo!!! Yo quiero empezar a cambiarle un poco los colores al mio, pero no tengi idea... 

Asi que me voy a fijar en tu archivo haber si puedo encontrar algo de utilidad...

Nuevamente... Excelente trabajo... ^^

---

### Post by MeduZa on 2008-05-05
> **PatoDB said:**
> 0.0

Wow Meduza!!!

Te quedo alucinante!!!

Tendria que ponerme las pilas y retocar un poco el mio... :P


Felicitaciones por el trabajo!!! Yo quiero empezar a cambiarle un poco los colores al mio, pero no tengi idea... 

Asi que me voy a fijar en tu archivo haber si puedo encontrar algo de utilidad...

Nuevamente... Excelente trabajo... ^^

gracias, igualmente mi conky.conf puede volver loco a cualquiera asi que avisa si necesitas una mano.

---

### Post by PatoDB on 2008-05-05
> **MeduZa said:**
> gracias, igualmente mi conky.conf puede volver loco a cualquiera asi que avisa si necesitas una mano.

NO te preocupes, ya perdi la cabeza... :P


No entendi nada de nada... Asi que me rendi, algun dia de estos le colocare iconos y cabiare los colores... Por ahora me resigno hasta nuevo aviso...

Gracias de todas formas... ^^

Exitos!

---

### Post by Thalskarth on 2008-05-06
Bueno, aca dejo mi Conky.

Esta basado en el de PatoDB, con algunas modificaciones que le hice...

```
background yes
use_xft yes
xftfont Terminus:size=9
xftalpha 0.8
update_interval 2.0
total_run_times 0
own_window yes
own_window_type override
own_window_transparent yes
double_buffer yes
minimum_size 1000 5
draw_shades no
draw_outline yes
draw_borders no
stippled_borders 8
border_margin 4
border_width 1
default_color white
default_shade_color white
default_outline_color black
alignment top_left
gap_x 1120
gap_y 160
no_buffers yes
uppercase no
cpu_avg_samples 2
net_avg_samples 2
override_utf8_locale no
use_spacer no

TEXT


${color }${color }  Ubuntu Linux 8.04
${color }UpTime: ${color }$uptime

${color }CPU:${color } $cpu% ${acpitemp}C
${cpugraph 20,130 000000 ffffff}
${color }Running:   ${color }$running_processes

${color }Highest CPU:
${color } ${top name 1}${top_mem cpu 1}
${color } ${top name 2}${top cpu 2}
${color } ${top name 3}${top cpu 3}
${color } ${top name 4}${top cpu 4}

${color }Highest MEM:
${color } ${top_mem name 1}${top_mem mem 1}
${color } ${top_mem name 2}${top_mem mem 2}
${color } ${top_mem name 3}${top_mem mem 3}
${color } ${top_mem name 4}${top_mem mem 4}

${color }MEM: ${color } $memperc%
$mem/$memmax
${membar 3,100}
${color }SWAP: ${color }$swapperc%
$swap/$swapmax
${swapbar 3,100}

${color }ROOT - Libre: ${color }${fs_free_perc /}%
${color }${fs_used /}/${fs_size /}
${fs_bar 3,100 /}

${color }HOME - Libre: ${color }${fs_free_perc /home}%
${color }${fs_used /home}/${fs_size /home}
${fs_bar 3,100 /home}

${color }NET: ${addr eth0}
${color}Up: ${color }${upspeed eth0} k/s
${upspeedgraph eth0 20,130 000000 ffffff}
${color}Down: ${color }${downspeed eth0}k/s${color}
${downspeedgraph eth0 20,130 000000 ffffff}
```

---

### Post by guillermolisi on 2008-05-07
Bueno, como ningun fana de KDE mando algo , aqui va un monitor de sistema, onda conky, pero para Superkaramba.

Monitor = original Perso theme, retocado y ajustado a mi sistema por mi.
Superkaramba 0.42 KDE 3.5.9

Para el que guste, le paso el archivo de configuracion.

[[IMG]http://i261.photobucket.com/albums/ii63/unimix/perso_monitor-1.png[/IMG]]("http://i261.photobucket.com/albums/ii63/unimix/perso_monitor.png")

---

### Post by Mauro22 on 2008-05-08
Muy bueno ese SuperKaramba... no lo conocia.

:guitar:

---

### Post by sebaxxxtian on 2008-05-08
yo tengo problemas con mi conky. antes aparecia en el boot bien pero despues de un tiempo desaparecia. ahora directamente no aparece en el escritorio. hay alguna confg q este mal?

lo dejo posteado. gracias.

background yes
use_xft yes
xftfont DejaVu Serif:size=9
xftalpha 0.5
update_interval 1.0
total_run_times 0
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 300 5
maximum_width 350
draw_shades no
# Create own window instead of using desktop (required in nautilus)
own_window yes


own_window_type root
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager


# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft no

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
# minimum_size 250 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
font arial
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 10

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color 888a74

own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 0

# stuff after 'TEXT' will be formatted on screen
TEXT
$color
${color 33ff00}SYSTEM ${hr 2}$color
$nodename $sysname $kernel on $machine
${color 33ff00}CPU ${hr 2}$color
${freq}MHz   Load: ${loadavg}   
$cpubar
${cpugraph 000000 ff0000}
NAME             PID       CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}
${color 33ff00}MEMORY / DISK ${hr 2}$color
RAM:   $memperc%   ${membar 6}$color
Root:  ${fs_free_perc /}%   ${fs_bar 6 /}$color
${battery} ${acpitempf}F ${wireless_essid ath0}
${color 33ff00}NETWORK (${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph ath0 25,140 000000 ff0000} ${alignr}${upspeedgraph ath0
25,140 000000 ffff00}$color
Total: ${totaldown ath0} ${alignr}Total: ${totalup ath0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

---

### Post by niko_3100 on 2008-05-09
Fijate de sacar la ultima linea donde comienza Inbound borra de ahi a abajo osea estas dos a ver que onda...

Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

Yo borre esas y levanto.

---

### Post by smrdelj on 2008-05-13
Muchachos, instalé la version actual de conky mediante sudo apt-get.

Hice esto para correrlo:

> **MeduZa said:**
> system > preferences > sessions
apretas add y escribis conky en los 3 casilleros y listo

Sin embargo, nada cambió en mi escritorio. Por otro lado, busqué ese tal archivo .conky en mi Carpeta Personal y no lo encontré (o sea, no existe).

Hay un par de conkys de las aqui posteadas que me gustaria probar (por ej la tuya, Meduza), ¿Como tengo que hacer?

En definitiva: ya tengo instalado conky, ¿Cómo lo corro?¿Cómo pruebo las distintas conkys aqui posteadas?

Saludos gracias

---

### Post by pol666 on 2008-05-13
para sirve el compiz? solo para ver el estado de la pc?

---

### Post by faktorqm on 2008-05-13
ammm compiz o conky? compiz es una manejador de ventanas, (si mal no recuerdo) y conky... si, es como un monitor del sistema themeable (configurable a gusto digamos) donde podes ver la red, el espacio, version de kernel, y supongo que salidas de algunos comandos. 
A mi me parece algo absolutamente inutil, tener algo asi ocupando espacio en mi escritorio, y utilizando recursos que podria usar para algo mejor... Aunque veo que mi opinion no es compartida por el resto, lo cual me parece perfecto, yo los miro y digo "que grosso!", y automaticamente paso a otro thread. 
Es como los tatuajes, a mi no me gustan ni me haria uno jamás, pero capaz si los veo hechos en otra persona digo "ahh, mira vos" y ya.
Salu2!

---

### Post by smrdelj on 2008-05-13
Bueno ya me avivé de cómo mostrar el conky..ahora les hago una pregunta: Dónde puedo encontrar una buena guia para crear uno personalizado?

---

### Post by sajnox on 2008-05-13
Aca tenes la pagina oficial de conky: [http://conky.sourceforge.net/](http://conky.sourceforge.net/)

Y aca tenes una lista de todas las variables que le podes agregar: [http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)

Un buen metodo de aprendizaje es el de prueba y error....

---

### Post by smrdelj on 2008-05-13
Muchas gracias, pero la verdad que, como me interesaba algo bien sencillo, me di maña por intuicion editando el Conky de Mauro22 xD

Ahora, lo que no consigo es hacer que el conky se inicie al cargar Ubuntu. Como previamente postié, hice lo señalado por MeduZa, pero no me surte efecto. Ademas, quisiera saber cómo se cierra conky una vez abierto y corriendo.

Gracias, espero su respuesta. Saludos

---

### Post by pol666 on 2008-05-13
> **faktorqm said:**
> ammm compiz o conky? compiz es una manejador de ventanas, (si mal no recuerdo) y conky... si, es como un monitor del sistema themeable (configurable a gusto digamos) donde podes ver la red, el espacio, version de kernel, y supongo que salidas de algunos comandos. 
A mi me parece algo absolutamente inutil, tener algo asi ocupando espacio en mi escritorio, y utilizando recursos que podria usar para algo mejor... Aunque veo que mi opinion no es compartida por el resto, lo cual me parece perfecto, yo los miro y digo "que grosso!", y automaticamente paso a otro thread. 
Es como los tatuajes, a mi no me gustan ni me haria uno jamás, pero capaz si los veo hechos en otra persona digo "ahh, mira



si me equivoque queria decir Conky...Y la verdad no me interesa mucho prefiero usar un Screenlet que me indique la memoria y el espacio que es lo unico que me interesa saber

---

### Post by Air23 on 2008-05-13
Aca va mi Conky
Es bastante sencillo, use como base uno de [http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865) y lo modifique un poco.
```
# set to yes if you want Conky to be forked in the background
background yes

cpu_avg_samples 2
net_avg_samples 2

out_to_console no

# X font when Xft is disabled, you can pick one with program xfontsel
#font 7x12
#font 6x10
#font 7x13
#font 8x13
#font 7x12
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*
#font -artwiz-snap-normal-r-normal-*-*-100-*-*-p-*-iso8859-1

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono:size=9

# Text alpha when using Xft
xftalpha 0.8

#on_bottom yes

# mail spool
mail_spool $MAIL

# Update interval in seconds
update_interval 1
# Create own window instead of using desktop (required in nautilus)
own_window yes
#own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 260 5
maximum_width 250

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders no

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
#default_color white
#default_shade_color white
#default_outline_color white

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
gap_x 15
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text

# Add spaces to keep things from moving about? This only affects certain objects.
use_spacer none

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# none, xmms, bmp, audacious, infopipe (default is none)
#none

# boinc (seti) dir
# seti_dir /opt/seti

# Possible variables to be used:
#
# Variable Arguments Description
# acpiacadapter ACPI ac adapter state.
# acpifan ACPI fan state
# acpitemp ACPI temperature.
# adt746xcpu CPU temperature from therm_adt746x
# adt746xfan Fan speed from therm_adt746x
# battery (num) Remaining capasity in ACPI or APM
# battery. ACPI battery number can be
# given as argument (default is BAT0).
# buffers Amount of memory buffered
# cached Amount of memory cached
# color (color) Change drawing color to color
# cpu CPU usage in percents
# cpubar (height) Bar that shows CPU usage, height is
# bar's height in pixels
# downspeed net Download speed in kilobytes
# downspeedf net Download speed in kilobytes with one
# decimal
# exec shell command Executes a shell command and displays
# the output in torsmo. warning: this
# takes a lot more resources than other
# variables. I'd recommend coding wanted
# behaviour in C and posting a patch .
# execi interval, shell Same as exec but with specific interval.
# command Interval can't be less than
# update_interval in configuration.
# fs_bar (height), (fs) Bar that shows how much space is used on
# a file system. height is the height in
# pixels. fs is any file on that file
# system.
# fs_free (fs) Free space on a file system available
# for users.
# fs_free_perc (fs) Free percentage of space on a file
# system available for users.
# fs_size (fs) File system size
# fs_used (fs) File system used space
# hr (height) Horizontal line, height is the height in
# pixels
# i2c (dev), type, n I2C sensor from sysfs (Linux 2.6). dev
# may be omitted if you have only one I2C
# device. type is either in (or vol)
# meaning voltage, fan meaning fan or temp
# meaning temperature. n is number of the
# sensor. See /sys/bus/i2c/devices/ on
# your local computer.
# kernel Kernel version
# loadavg (1), (2), (3) System load average, 1 is for past 1
# minute, 2 for past 5 minutes and 3 for
# past 15 minutes.
# machine Machine, i686 for example
# mails Mail count in mail spool. You can use
# program like fetchmail to get mails from
# some server using your favourite
# protocol. See also new_mails.
# mem Amount of memory in use
# membar (height) Bar that shows amount of memory in use
# memmax Total amount of memory
# memperc Percentage of memory in use
# new_mails Unread mail count in mail spool.
# nodename Hostname
# outlinecolor (color) Change outline color
# pre_exec shell command Executes a shell command one time before
# torsmo displays anything and puts output
# as text.
# processes Total processes (sleeping and running)
# running_processes Running processes (not sleeping),
# requires Linux 2.6
# shadecolor (color) Change shading color
# stippled_hr (space), Stippled (dashed) horizontal line
# (height)
# swapbar (height) Bar that shows amount of swap in use
# swap Amount of swap in use
# swapmax Total amount of swap
# swapperc Percentage of swap in use
# sysname System name, Linux for example
# time (format) Local time, see man strftime to get more
# information about format
# totaldown net Total download, overflows at 4 GB on
# Linux with 32-bit arch and there doesn't
# seem to be a way to know how many times
# it has already done that before torsmo
# has started.
# totalup net Total upload, this one too, may overflow
# updates Number of updates (for debugging)
# upspeed net Upload speed in kilobytes
# upspeedf net Upload speed in kilobytes with one
# decimal
# uptime Uptime
# uptime_short Uptime in a shorter format
#
# seti_prog Seti@home current progress
# seti_progbar (height) Seti@home current progress bar
# seti_credit Seti@hoome total user credit


# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument
#${font Dungeon:style=Boldixelsize=10}I can change the font as well
#${font Verdana:size=10}as many times as I choose
#${font Perry:size=10}Including UTF-8,
# stuff after 'TEXT' will be formatted on screen
#${font Grunge:size=12}${time %a %b %d}${alignr -25}${time %k:%M}

TEXT
${color #FFFFFF}
$stippled_hr
$nodename
${execi 99999 lsb_release -d -s -c | tr -s "\n" " "}
$kernel on $machine
$stippled_hr
Intel® Core™2 Duo E6600 2.4 GHz

CPU:1  ${cpu cpu1}% ${cpubar cpu1}
CPU:2  ${cpu cpu2}% ${cpubar cpu2}
$stippled_hr
memory:
 ram:  ${alignr}$mem / $memmax
    ${membar 10,200}

 swap: ${alignr}$swap / $swapmax
    ${swapbar 10,200}
$stippled_hr
hard disks:
 root   ${alignr}${fs_used /} / ${fs_size /}
    ${fs_bar 10,200 /}

 home   ${alignr}${fs_used /home} / ${fs_size /home}
    ${fs_bar 10,200 /home}
$stippled_hr
cpu usage: ${alignr}CPU%
 ${top name 1}  ${alignr}${top cpu 1}
 ${top name 2}  ${alignr}${top cpu 2}
 ${top name 3}  ${alignr}${top cpu 3}
 ${top name 4}  ${alignr}${top cpu 4}
 ${top name 5}  ${alignr}${top cpu 5}
 ${top name 6}  ${alignr}${top cpu 6}
 ${top name 7}  ${alignr}${top cpu 7}
$stippled_hr
mem usage: ${alignr}MEM%
 ${top_mem name 1}  ${alignr}${top_mem mem 1}
 ${top_mem name 2}  ${alignr}${top_mem mem 2}
 ${top_mem name 3}  ${alignr}${top_mem mem 3}
 ${top_mem name 4}  ${alignr}${top_mem mem 4}
 ${top_mem name 5}  ${alignr}${top_mem mem 5}
 ${top_mem name 6}  ${alignr}${top_mem mem 6}
 ${top_mem name 7}  ${alignr}${top_mem mem 7}
$stippled_hr
network:
 IP ${addr eth0}
down: ${downspeed eth0} k/s ${alignr}up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,120 000000 000000} $alignr${upspeedgraph eth0 25,120 000000 000000}
${totaldown eth0} $alignr${totalup eth0}
$stippled_hr
```

Aprovecho la oportunidad para hacer dos preguntas:

[LIST=1]
[*]¿Como lo subo para que conky quede mas cerca del panel superior?
[*]En Gutsy usaba esto para mostrar la cancion que estaba escuchando con Exaile
[/LIST]
```
 ${execi 10 exaile --get-title} 
 ${execi 10 exaile --get-artist}
 ${execi 10 exaile --get-album}
```

Pero en Hardy no anda bien (en una de las imagenes adjuntadas se ve la diferencia) y si lo corro desde una terminal sale esto:
```
  File "/usr/share/exaile/xl/dbusinterface.py", line 289, in test
    print iface.get_album()
UnicodeEncodeError: 'ascii' codec can't encode character u'\xf1' in position 15: ordinal not in range(128)

```

¿Alguien sabe como arreglarlo?

---

### Post by niko_3100 on 2008-05-14
La verdad qeu probe screenlets y gdesklets pero sigo estando enamorado del conky es perfecto y eso que no lo tengo taaan informativo como ustedes pero esta barbaro.

---

### Post by PatoDB on 2008-05-14
Wenas!!


Necesito que alguien me diga por favor, como se puede poner una palabra en una letra mayor al resto...


Porque cuando quiero cambiar el tamaño, me cambia el tamaño de todas las letras...

Es posible cambiar el tamaño de una palabra nomas???


Saludos!!!

-------------------------------------

Listo, a modo de prueba y error encontre una posible solucion:

Hice lo siguiente...

```
${font size=10}  UBUNTU 8.04 ${font }
```

Y logre que esa linea se vea mas grande.

No se si esta bien o mal, yo tengo cero de esta programacion.. :P

La cuestion, es que el numero al lado del size, esta de mas, porque ya sea que le ponga 10 - 18 - 36, siempre tiene el mismo tamaño.

Alguna Sugerencia?

---

### Post by sajnox on 2008-05-14
> **smrdelj said:**
> Muchas gracias, pero la verdad que, como me interesaba algo bien sencillo, me di maña por intuicion editando el Conky de Mauro22 xD

Ahora, lo que no consigo es hacer que el conky se inicie al cargar Ubuntu. Como previamente postié, hice lo señalado por MeduZa, pero no me surte efecto. Ademas, quisiera saber cómo se cierra conky una vez abierto y corriendo.

Gracias, espero su respuesta. Saludos

Para que inicie con la maquina tenes que agregarlo en sistema/preferencias/sesiones en donde dice "orden" tiene que ir conky (asi como lo ves en letras minusculas)

Para cerrarlo, lo podes hacer desde el monitor del sistema /sistema/administracion/monitor del sistema y matas el proceso o desde una consola con 

```
sudo kill "numero de proceso de conky"
```

---

### Post by _kAz_ on 2008-05-14
> **smrdelj said:**
> Muchachos, instalé la version actual de conky mediante sudo apt-get.

Hice esto para correrlo:
Sin embargo, nada cambió en mi escritorio. Por otro lado, busqué ese tal archivo .conky en mi Carpeta Personal y no lo encontré (o sea, no existe).

Hay un par de conkys de las aqui posteadas que me gustaria probar (por ej la tuya, Meduza), ¿Como tengo que hacer?

En definitiva: ya tengo instalado conky, ¿Cómo lo corro?¿Cómo pruebo las distintas conkys aqui posteadas?


Venía a pedir lo mismo. Supuestamente tengo Conky... pero es un asco!!!!

Alguien que me/nos de **una mano** y nos diga o pase una guía para más o menos configurarlo y tunearlo así queda más agradable a la vista, y NO ESTO :-&

---

### Post by Air23 on 2008-05-14
> **smrdelj said:**
> Muchas gracias, pero la verdad que, como me interesaba algo bien sencillo, me di maña por intuicion editando el Conky de Mauro22 xD

Ahora, lo que no consigo es hacer que el conky se inicie al cargar Ubuntu. Como previamente postié, hice lo señalado por MeduZa, pero no me surte efecto. Ademas, quisiera saber cómo se cierra conky una vez abierto y corriendo.

Gracias, espero su respuesta. Saludos

Si la memoria no me falla, cuando lo instalas no viene con ningun .conkyrc (es mas ni siquiera un archivo en blanco, sino que no existe). Tenes que haces lo siguiente:
```
sudo gedit ~/.conkyrc
```
Se abre un documento en el cual debes pegar el conkyrc que te gusta, guardas y cerras.
Finalmente desde una terminal ejecutas: conky y listo
Si queres que conky se inicie con tu ubuntu, anda a sistema>preferencias>sesiones, vas a añadir y en la ventana que se abre pone como Nombre Conky (o el que mas te guste) y donde dice orden pones: conky (asi en minusculas).
En [http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html) y [http://conky.sourceforge.net/config_settings.html](http://conky.sourceforge.net/config_settings.html) tenes informacion sobre como configurarlo y en [http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865) hay cientos de conkys para usar como inspiracion (o sencillamente usarlos)

---

### Post by sebaxxxtian on 2008-05-15
yo queria agregar la parte de amarok, asi q se la agregue al que tenia pero no se como setear el conkyrc para que salga lo que estoy escuchando. y me perdi con el dpoc.

alguien me da una mano?

dsps les paso como quedo el mio

---

### Post by sebaxxxtian on 2008-05-15
yo queria agregar la parte de amarok, asi q se la agregue al que tenia pero no se como setear el conkyrc para que salga lo que estoy escuchando. y me perdi con el dpoc.

alguien me da una mano?

dsps les paso como quedo el mio

---

### Post by smrdelj on 2008-05-15
Muchas gracias muchachos por sus respuestas!

Saludos

---

### Post by MeduZa on 2008-05-19
bueno, aca dejo 3 aportes, ya que cambie 3 veces de reproductor en 2 meses xD

barra de % para:

Rhythmbox:
archibo: rhythmbox.sh
```
#!/bin/bash
# barra de % para rhythmbox
x=`rhythmbox-client --no-start --print-playing-format "%td" | tr -d ":" | sed 's#Not playing##'`;
y=`rhythmbox-client --no-start --print-playing-format "%te" | tr -d ":" | sed 's#Not playing##'`;
x=$(($x+0));
y=$(($y+0));
test $x -eq 0 && x=100;
z=$((100000/ $x * $y /1000));
test $z -gt 100 && echo 100 || echo $z;
x=`rhythmbox-client --no-start --print-playing-format "%td" | tr -d ":" | sed 's#Not playing##'`;y=`rhythmbox-client --no-start --print-playing-format "%te" | tr -d ":" | sed 's#Not playing##'`;x=$(($x+0));y=$(($y+0));test $x -eq 0 && x=100;z=$((100000/ $x * $y /1000));test $z -gt 100 && echo 100 || echo $z;
# By meduza
```
codigo en el conf de concky:
> ${if_running rhythmbox}${voffset 7}${font Webdings:regular:size=21}${color #ba55d3}Ø${voffset -7}${font Anklepants:regular:size=11}${color #5da5d3}Music
${voffset -10}${color #ffd700}${hr 1}$font$color
  ${color #ffe7ba}Title: $color${execi 20 rhythmbox-client --no-start --print-playing-format "%tt"}
  ${color #ffe7ba}Album: $color${execi 20 rhythmbox-client --no-start --print-playing-format "%at"}$alignr${color #ffe7ba} CD:$color${execi 20 rhythmbox-client --no-start --print-playing-format "%aN"}
  ${color #ffe7ba}Artist:$color ${execi 20 rhythmbox-client --no-start --print-playing-format "%aa"}$alignr${color #ffe7ba}Track:$color${execi 20 rhythmbox-client --no-start --print-playing-format "%tN"}
  ${color #ffe7ba}Time: ${color #9acd32}${execi 1 rhythmbox-client --no-start --print-playing-format "%te / %td"}$alignr${color #ffe7ba}Year: $color${execi 20 rhythmbox-client --no-start --print-playing-format "%ay"}
  ${color #ba55d3}${execbar sh ~/.conky/rhythmbox.sh}

Banshee:
banshee.sh
```
#!/bin/bash
# barra de % para banshee
y=`banshee --query-position | sed 's#Position: ##'`;
x=`banshee --query-duration | sed 's#Duration: ##'`;
#x=$(($x+0));
#y=$(($y+0));
test $x -eq 0 && x=100;
z=$((100000/ $x * $y /1000));
test $z -gt 100 && echo 100 || echo $z;
# By meduza
```
codigo en el conf de concky:
> ups lo borre sin querer xD pero es facil, solo lo hago a pedido

Exile:
exile.sh
```
#!/bin/bash
# barra de % para exaile
y=`exaile -q | cut -d"[" -f2 | tr -d "]" | head -n 1 | tr -d ":"`;
x=`exaile --get-length | head -n 1 | tr -d ":"`;
#x=$(($x+0));
#y=$(($y+0));
test $x -eq 0 && x=100;
z=$((100000/ $x * $y /1000));
test $z -gt 100 && echo 100 || echo $z;
# By meduza
```
codigo en el conf de concky:
> ${if_running python /usr/lib/exaile/exaile.py}${voffset 7}${font Webdings:regular:size=21}${color #ba55d3}Ø${voffset -7}${font Anklepants:regular:size=11}${color #5da5d3}Music
${voffset -10}${color #ffd700}${hr 1}$font$color
  ${color #ffe7ba}Title: $color${execi 10 exaile --get-title | head -n 1}
  ${color #ffe7ba}Album: $color${execi 10 exaile --get-album | head -n 1}
  ${color #ffe7ba}Artist:$color ${execi 10 exaile --get-artist | head -n 1}
  ${color #ffe7ba}Time: ${color #9acd32}${execi 1 exaile -q | cut -d"[" -f2 | tr -d "]" | head -n 1} / ${execi 1  exaile --get-length | head -n 1}
  ${color #ba55d3}${execbar sh ~/.conky/exaile.sh}
$endif

---

### Post by Thalskarth on 2008-05-19
> **MeduZa said:**
> Exile:
exile.sh
```
#!/bin/bash
# barra de % para exaile
y=`exaile -q | cut -d"[" -f2 | tr -d "]" | head -n 1 | tr -d ":"`;
x=`exaile --get-length | head -n 1 | tr -d ":"`;
#x=$(($x+0));
#y=$(($y+0));
test $x -eq 0 && x=100;
z=$((100000/ $x * $y /1000));
test $z -gt 100 && echo 100 || echo $z;
# By meduza
```
codigo en el conf de concky:

Una duda, el exaile.sh donde debo guardarlo??

---

### Post by Air23 on 2008-05-19
> **Thalskarth said:**
> Una duda, el exaile.sh donde debo guardarlo??

Tenes que guardarlo en ~/.conky (o sea /home/usuario/.conky).

---

### Post by Air23 on 2008-05-19
> **MeduZa said:**
> bueno, aca dejo 3 aportes, ya que cambie 3 veces de reproductor en 2 meses xD

GRACIAS TOTALES (y una pregunta)

Es posible que dentro del conky la parte del exaile (en mi caso) aparezca solo cuando estoy ejecutandolo (al exaile)? Porque si no lo tengo abierto me aparece como salida de los distintos comandos:  /usr/lib/xulrunner-1.9b5/libxpcom.so y queda feo.

Gracias de nuevo

---

### Post by MeduZa on 2008-05-19
> **Air23 said:**
> GRACIAS TOTALES (y una pregunta)

Es posible que dentro del conky la parte del exaile (en mi caso) aparezca solo cuando estoy ejecutandolo (al exaile)? Porque si no lo tengo abierto me aparece como salida de los distintos comandos:  /usr/lib/xulrunner-1.9b5/libxpcom.so y queda feo.

Gracias de nuevo

cerre el exile y tenes razon, siempre queda en memoria, aunque el iconito o el programa no esten abiertos :S
reinicie la pc para ver que pasa y tambien aparece en memoria el exile cuando termina de reiniciar, es como que el conky lo "despertara" pero no era esa la idea.

voy a ver que se puede hacer porque si pongo: ${if_running python exaile} no lo detecta

---

### Post by MeduZa on 2008-05-19
> **Thalskarth said:**
> Una duda, el exaile.sh donde debo guardarlo??

perdon me olvide eso, ese archivo te conviene meterlo en tu home en una carperta que tenes que crear llamada .conky como te dijeron mas arriba, o si te gusta mas, lo podes meter donde se te cante, pero tenes que cambiar el acceso desde el config de conky

---

### Post by Thalskarth on 2008-05-19
> **Air23 said:**
> Tenes que guardarlo en ~/.conky (o sea /home/usuario/.conky).

> **MeduZa said:**
> perdon me olvide eso, ese archivo te conviene meterlo en tu home en una carperta que tenes que crear llamada .conky como te dijeron mas arriba, o si te gusta mas, lo podes meter donde se te cante, pero tenes que cambiar el acceso desde el config de conky


Gracias a ambos por las respuestas

Mañana lo pruebo :)

---

### Post by santiagoward2000 on 2008-05-22
Hola!
Acá pongo el mio. Por fin consegui que me guste como queda. Gracias a Totoloco por los scripts que subio! :)
Saludos!

_EDIT:_
Me acabo de avivar que hay un error en mi conkyrc. El % y la barrita del disco de windows (al lado de WIN) estan bien, pero el espacio libre marca el de la particion de Xubuntu. Si alguien lo usa, fijese de agregar /media/nombre_de_su_particion despues de **"WIN: ${fs_free"** (como no creo que nadie tenga el nombre de mi particion, no vale la pena que suba el nuevo).

---

### Post by valucha on 2008-05-23
[COLOR="DarkOrchid"]Chicos me ayudan a ordenar esto?...

Lo que quiero esque me quede todo horizontal. primero el clima y después la hora alineado a la derecha y que la "barra" osea, el conky sea lo más finito posible...

Tengo varios problemas, no me aparece el solcito/nubecita/etc (el clima en frma de dibujito) por más que tenga la font como corresponda, en un momento aparecía y después dejó de hacerlo, no sé que hago mal... Y por otro lado que no me quedan alineados verticalmente, queda uno bajo el otro...
probé con el voffset, offset, alignr, alignc etc... pero no puedo coordinar todo para que quede alineado y a la derecha...

Desde ya mil gracias..

dejo screenshot y mi conky


> #avoid flicker



double_buffer yes



#own window to run simultanious 2 or more conkys



own_window yes



own_window_type normal



own_window_transparent no



own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager



#borders



draw_borders no



border_margin 0



border_width 3



draw_outline no



default_outline_color 777777



#shades



draw_shades no



#position



gap_x 0



gap_y 10



alignment tm



#behaviour



update_interval 5



#colour



default_color  8f8f8f



#default_shade_color 359748



own_window_colour 262729



#font



use_xft yes



xftfont bauhaus:pixelsize=12



#to prevent window from moving



use_spacer yes



minimum_size 1280 15



#mpd



mpd_host localhost



mpd_port 6600



draw_graph_borders no





TEXT
${voffset 0}${offset 1000}${color white}${font weather:size=50}${execi 300 ~/.scripts/conditions.sh ARRN0116}${color white}${font}${execi 300 ~/.scripts/pogodynka.sh ARBA0009}${offset 10}${color white}${font monospace:size=15}${time %I:%M:%S}
${color ca1a6d} ${hr 3}  [/COLOR]

---

### Post by oktubrer on 2008-05-23
Con respecto al dibujito tendrías que ver la salida del script conditions.sh, proba sacarlo por consola y fijate, debería ser una letra sola dependiendo del estado del clima.

Si no sale nada ya tendrías que ver si está bien el script, si están bien las rutas de los archivos, etc.  Creo que conditions.sh chequea el estado del tiempo que guarda el otro script (pogodynka.sh) en /tmp/clima.txt (no me acuerdo si así era originalmente o si asi lo dejé configurado yo).

---

### Post by santiagoward2000 on 2008-05-23
> **valucha said:**
> [COLOR="DarkOrchid"]Chicos me ayudan a ordenar esto?...

Lo que quiero esque me quede todo horizontal. primero el clima y después la hora alineado a la derecha y que la "barra" osea, el conky sea lo más finito posible...

Tengo varios problemas, no me aparece el solcito/nubecita/etc (el clima en frma de dibujito) por más que tenga la font como corresponda, en un momento aparecía y después dejó de hacerlo, no sé que hago mal... Y por otro lado que no me quedan alineados verticalmente, queda uno bajo el otro...
probé con el voffset, offset, alignr, alignc etc... pero no puedo coordinar todo para que quede alineado y a la derecha...

Desde ya mil gracias..

dejo screenshot y mi conky


 [/COLOR]

Hola Vale,
Según veo, en el clima (la parte que te pone la nubecita) tenés puesto el de Bariloche (ARRN0116) que no siempre anda (lo digo por experiencia). Además, como no sos de acá me imagino que no te debe interesar mucho nuestro clima... JAJA.
Fijate que tu código dice:
```
${execi 300 ~/.scripts/conditions.sh ARRN0116}$
```
Tratá de cambiarlo por
```
${execi 300 ~/.scripts/conditions.sh ARBA0009}$
```
Espero que te sirva!

---

### Post by oktubrer on 2008-05-23
> **MeduZa said:**
> cerre el exile y tenes razon, siempre queda en memoria, aunque el iconito o el programa no esten abiertos :S
reinicie la pc para ver que pasa y tambien aparece en memoria el exile cuando termina de reiniciar, es como que el conky lo "despertara" pero no era esa la idea.

voy a ver que se puede hacer porque si pongo: ${if_running python exaile} no lo detecta

El conky no lo ejecuta, lo que pasa es que el if_running en este caso chequea si hay alguna instancia de python ejecutandosé, puede ser el exaile o cualquier otra cosa aplicación.

---

### Post by Thalskarth on 2008-05-23
> **santiagoward2000 said:**
> Hola!
Acá pongo el mio. Por fin consegui que me guste como queda. Gracias a Totoloco por los scripts que subio! :)
Saludos!

hola, te hago una opregunta

quise usar tu ascrip para la temperatuira, etc...

pero las muestra mal onda "18Äº C".. yo copie el texto de la instruccion desde tu conkyrc sin modificar esa linea...

sabes a que se puede deber que lo vea asi???

---

### Post by andy_91 on 2008-05-23
bueno les dejo lo que va de mi conky hasta ahora va bien salvo por el clima que me aparese una letra en vez e el dibujo de una nube o un sol

bueno es casi la misma que santiagoward2000 pero un poco mas light


bueno se las dejo

---

### Post by valucha on 2008-05-23
> **andy_91 said:**
> bueno les dejo lo que va de mi conky hasta ahora va bien salvo por el clima que me aparese una letra en vez e el dibujo de una nube o un sol

bueno es casi la misma que santiagoward2000 pero un poco mas light


bueno se las dejo

[COLOR="DarkOrchid"]Necesitas la font que utiliza... en ese caso creo que es wheather.tff
bajala de acá: [http://www.dafont.com/font.php?file=weather](http://www.dafont.com/font.php?file=weather)
copiala acá:

sudo nautilus /usr/share/fonts 

y voilà...[/COLOR]

---

### Post by andy_91 on 2008-05-24
gracias ahora si se ven las nubecitas XD

no les pongo como quedo por que es igual nada mas que en lugar de una e aparese las nubes

ahora si puedo decir que me falta encontrar un buen fondo de pantalla y ya termine de tunear mi desktop jeje

---

### Post by MeduZa on 2008-05-24
> **oktubrer said:**
> El conky no lo ejecuta, lo que pasa es que el if_running en este caso chequea si hay alguna instancia de python ejecutandosé, puede ser el exaile o cualquier otra cosa aplicación.

aja pero exaile existe pero no toma el if_running exaile por alguna razon que desconozco, entonces por eso use python + el comando para exaile pero tampoco funco.

se me acaban las ideas :P

como detecto al exaile en memoria?
yo en el system monitor lo veo 2 veces y encima come memoria que da miedo :S 

(la segunda es el conky leyendo datos de el ya me di cuenta)

---

### Post by santiagoward2000 on 2008-05-25
> **Thalskarth said:**
> hola, te hago una opregunta

quise usar tu ascrip para la temperatuira, etc...

pero las muestra mal onda "18Äº C".. yo copie el texto de la instruccion desde tu conkyrc sin modificar esa linea...

sabes a que se puede deber que lo vea asi???

Hmm, la verdad que ni idea. ¿Podes subir tu conkyrc para ver? Si no modificaste el script, me imagino que el error debe estar ahi.

---

### Post by Mauro22 on 2008-05-25
Los simbolos raros, es porque el tipo de letra que estas usando no tiene el caracter que va entre el numero y la C.

---

### Post by Thalskarth on 2008-05-25
> **santiagoward2000 said:**
> Hmm, la verdad que ni idea. ¿Podes subir tu conkyrc para ver? Si no modificaste el script, me imagino que el error debe estar ahi.

Aca mi .conkyrc

```
background yes
use_xft yes
xftfont Terminus:size=9
xftalpha 0.8
update_interval 2.0
total_run_times 0
own_window yes
own_window_type override
own_window_transparent yes
double_buffer yes
minimum_size 1000 5
draw_shades no
draw_outline yes
draw_borders no
stippled_borders 8
border_margin 4
border_width 1
default_color white
default_shade_color white
default_outline_color black
alignment top_left
gap_x 1120
gap_y 160
no_buffers yes
uppercase no
cpu_avg_samples 2
net_avg_samples 2
override_utf8_locale no
use_spacer no

TEXT

TEMP / SEN / HUM%   ${font weather:size=22}${execi 300 ~/.conky/scripts/weather2/conditions.sh ARBA0009}${font} 
${execi 300 ~/.conky/scripts/weather2/pogodynka.sh ARBA0009}


${color }${color }  Ubuntu Linux 8.04
${color }UpTime: ${color }$uptime

${color }CPU:${color } $cpu% ${acpitemp}C
${cpugraph 20,130 000000 ffffff}
${color }Running:   ${color }$running_processes

${color }Highest CPU:
${color } ${top name 1}${top_mem cpu 1}
${color } ${top name 2}${top cpu 2}
${color } ${top name 3}${top cpu 3}
${color } ${top name 4}${top cpu 4}

${color }Highest MEM:
${color } ${top_mem name 1}${top_mem mem 1}
${color } ${top_mem name 2}${top_mem mem 2}
${color } ${top_mem name 3}${top_mem mem 3}
${color } ${top_mem name 4}${top_mem mem 4}

${color }MEM: ${color } $memperc%
$mem/$memmax
${membar 3,100}
${color }SWAP: ${color }$swapperc%
$swap/$swapmax
${swapbar 3,100}

${color }ROOT - Libre: ${color }${fs_free_perc /}%
${color }${fs_used /}/${fs_size /}
${fs_bar 3,100 /}

${color }HOME - Libre: ${color }${fs_free_perc /home}%
${color }${fs_used /home}/${fs_size /home}
${fs_bar 3,100 /home}

${color }NET: ${addr eth0}
${color}Up: ${color }${upspeed eth0} k/s
${upspeedgraph eth0 20,130 000000 ffffff}
${color}Down: ${color }${downspeed eth0}k/s${color}
${downspeedgraph eth0 20,130 000000 ffffff}
```


Si es la letra, como lo modifico??

---

### Post by santiagoward2000 on 2008-05-25
> **Thalskarth said:**
> Aca mi .conkyrc
Si es la letra, como lo modifico??

Y si, debe ser eso, aunque no probre esa letra. Fijate en tu código donde dice:
```
xftfont Terminus:size=9
```
Ahi cambia Terminus por otra.
Saludos

---

### Post by Thalskarth on 2008-05-25
> **santiagoward2000 said:**
> Y si, debe ser eso, aunque no probre esa letra. Fijate en tu código donde dice:
```
xftfont Terminus:size=9
```
Ahi cambia Terminus por otra.
Saludos

probe cambiandolo por Arial, por Bitstraeam Vera, por DejaVu y Verdana.. y pasa lo mismo... que letra puede funcionar??

---

### Post by santiagoward2000 on 2008-05-25
> **Thalskarth said:**
> probe cambiandolo por Arial, por Bitstraeam Vera, por DejaVu y Verdana.. y pasa lo mismo... que letra puede funcionar??

Uhh, me mataste. Yo uso arial y no me pasa... :confused:
Ni idea de que puede ser. Perdona.

---

### Post by Thalskarth on 2008-05-26
> **santiagoward2000 said:**
> Uhh, me mataste. Yo uso arial y no me pasa... :confused:
Ni idea de que puede ser. Perdona.

nah. no es problema... la verdad que entiendo poco de como configurar el conky y seguro hice lio en algun lugar :P

Ahora probé hacver el sentido inverso... o sea, en vez de usar el conkyrc que yo tenia y a ese agregarle lo del clima y calenadrio desde tu conkyrc...

tome el tuyo como base... y modifique hacia lo que era el mio. Y ahora funcino bien :)
o sea, no se porque:confused:, pero al menos anda bian ahora :)

Aca como me quedo, por si alguno le interesa :
```
# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages 
# - netstat connections to your computer
#
# -- Pengo (conky@pengo.us)
#

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes

# Update interval in seconds
update_interval 1.0

#Maximum width of window
maximum_width 160

# Minimum size of text area
# minimum_size 180 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline yes # amplifies text if yes
draw_borders no
font arial:size=10
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, white == #ffffff
default_color white
default_outline_color black

own_window_colour black
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 170

# ${font AvantGarde Bk BT:size=9}${execi 1800 ~/Programas/Conky/scripts/weather/weather.sh ARRN0116}
# stuff after 'TEXT' will be formatted on screen

TEXT
${color white}     ${font monospace:size=18}${time %I:%M:%S}${font}

${alignc}${time %a  %e de %B de %Y}
${alignc} ${font Monospace:size=6}${exec ~/.conky/scripts/calendar.sh}
${hr 1}
     ${font weather:size=120}${execi 300 ~/.conky/scripts/weather2/conditions.sh ARBA0009}${font}
${alignc}TEMP/SENS/HUM%
${alignc}${execi 300 ~/.conky/scripts/weather2/pogodynka.sh ARBA0009}
${hr 1}
${alignc}${color }UpTime: ${color }$uptime
${hr 1}
${color }CPU:${color } $cpu%
${cpugraph 000000 ffffff}
${color }MEM: ${color } $memperc%
$mem/$memmax
${membar}
${color }SWAP: ${color }$swapperc%
$swap/$swapmax
${swapbar}
${hr 1}
${color }ROOT - Libre: ${color }${fs_free_perc /}%
${color }${fs_used /}/${fs_size /}
${fs_bar /}

${color }HOME - Libre: ${color }${fs_free_perc /home}%
${color }${fs_used /home}/${fs_size /home}
${fs_bar /home}
${hr 1}
${color }NET: ${addr eth0}
${color}Up: ${color }${upspeed eth0} k/s
${upspeedgraph eth0 000000 ffffff}
${color}Down: ${color }${downspeed eth0}k/s${color}
${downspeedgraph eth0 000000 ffffff}
```

---

### Post by santiagoward2000 on 2008-05-26
> **Thalskarth said:**
> nah. no es problema... la verdad que entiendo poco de como configurar el conky y seguro hice lio en algun lugar :P

Ahora probé hacver el sentido inverso... o sea, en vez de usar el conkyrc que yo tenia y a ese agregarle lo del clima y calenadrio desde tu conkyrc...

tome el tuyo como base... y modifique hacia lo que era el mio. Y ahora funcino bien :)
o sea, no se porque:confused:, pero al menos anda bian ahora :)

Bueno, me alegro que haya funcionado. Ahora veo que vos habias usado un **xftfont**, y yo solo **font**. Puede que ahi haya estado el problema, pero ni idea de que diferencia hay.
Saludos

---

### Post by Aspergillus on 2008-05-27
dejo el mio, es muy sencillo, me gusta que tenga lo basico y que sea estetico, la fuente utilizada es la "mintsstrong", viene en el pack de fuentes de Artwiz

el .conkyrc

```

background yes

use_xft yes

#fuente ocupada
xftfont Ani Regular:size=7

xftalpha 1
update_interval 5.0
total_run_times 0
own_window yes
own_window_type override
own_window_transparent no
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 200 1
maximum_width 1200
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color white
default_shade_color white
default_outline_color white

#Posicion de conky
#alignment top_left
#alignment top_right
alignment bottom_left
#alignment bottom_right

gap_x 15
gap_y 7
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no

TEXT
${font mintsstrong :style=bold :size=7}${color #777777}Kernel: ${color}${color #bfbfbf}$kernel${color}  |  ${color #777777}Encendido: ${color}${color #bfbfbf}$uptime${color}  |  ${color #777777}Procesos: ${color}${color #bfbfbf}($running_processes Act./Tot. $processes)${color}  |  ${color #777777}Cpu: ${color}${color #bfbfbf}$cpu% ${color #777777}Ram: ${color}${color #bfbfbf}$mem${color} ${color #777777}Swap: ${color}${color #bfbfbf}$swap${color}  |  ${color #777777}Home: ${color}${color #bfbfbf}${fs_free /home} ${color #777777}Local: ${color}${color #bfbfbf}${fs_free /media/hda1} ${color #777777}USB 160GB: ${color}${color #bfbfbf}${fs_free /media/USER Movible 160 GB}${color}  |  ${font mintsstrong :style=regular :size=7}${color #777777}NET: UP ${color }${color #bfbfbf}${upspeed eth0} k/s ${color}${color #777777} DOWN ${color }${color #bfbfbf}${downspeed eth0}k/s ${color}
```

el screenshot

[http://xs127.xs.to/xs127/08223/conky780.jpg](http://xs127.xs.to/xs127/08223/conky780.jpg)

---

### Post by lega on 2008-05-28
Hola, gracias por postear sus conkyrc de hecho el que estoy usando lo saqué de acá, creo que es una mezcla entre el de santiago y el de Thalskarth, el problema que tengo es que me sale muy abajo,parte de los datos se me van de la pantalla, cual sería el parametro que hay que tocar para subirlo un toque? adjunto captura espero que se aprecie lo que digo.
Saludos

---

### Post by jjgomera on 2008-05-28
Con esto eliges la esquina con respecto a la que vas a referenciar el conky:

```
# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
```

Con estos valores valores distancias de esa esquina elegida arriba el conky, tanto en la coordenada x (horizontal) como en la coordenada y (vertical)

```
# Gap between borders of screen and text
gap_x 0
gap_y 0
```

Para subirlo, dependiendo de la esquina puesta arriba, tendrás que aumentar o disminuir el valor de gap_y

---

### Post by lega on 2008-05-28
jjgomera , muchas gracias pero por mas que lo subo hasta el tope no entra todo en la pantalla, la parte de abajo queda afuera, tal vez tocando el tamaño de la fuente en general?, no se...
Posteo mi conky por si alguien ve algo raro, es el mismo que puso Thalskarth creo

Gracias
> UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages 
# - netstat connections to your computer
#
# -- Pengo (conky@pengo.us)
#

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_xft yes

# Update interval in seconds
update_interval 1.0

#Maximum width of window
maximum_width 160

# Minimum size of text area
# minimum_size 180 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline yes # amplifies text if yes
draw_borders no
font arial:size=10
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, white == #ffffff
default_color white
default_outline_color black

own_window_colour black
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 10

# ${font AvantGarde Bk BT:size=9}${execi 1800 ~/Programas/Conky/scripts/weather/weather.sh ARRN0116}
# stuff after 'TEXT' will be formatted on screen

TEXT
${color white}     ${font monospace:size=18}${time %I:%M:%S}${font}

${alignc}${time %a  %e de %B de %Y}
${alignc} ${font Monospace:size=6}${exec ~/.conky/scripts/calendar.sh}
${hr 1}
     ${font weather:size=120}${execi 300 ~/.conky/scripts/weather2/conditions.sh ARBA0009}${font}
${alignc}TEMP/SENS/HUM%
${alignc}${execi 300 ~/.conky/scripts/weather2/pogodynka.sh ARBA0009}
${hr 1}
${alignc}${color }UpTime: ${color }$uptime
${hr 1}
${color }CPU:${color } $cpu%
${cpugraph 000000 ffffff}
${color }MEM: ${color } $memperc%
$mem/$memmax
${membar}
${color }SWAP: ${color }$swapperc%
$swap/$swapmax
${swapbar}
${hr 1}
${color }ROOT - Libre: ${color }${fs_free_perc /}%
${color }${fs_used /}/${fs_size /}
${fs_bar /}

${color }HOME - Libre: ${color }${fs_free_perc /home}%
${color }${fs_used /home}/${fs_size /home}
${fs_bar /home}
${hr 1}
${color }NET: ${addr eth0}
${color}Up: ${color }${upspeed eth0} k/s
${upspeedgraph eth0 000000 ffffff}
${color}Down: ${color }${downspeed eth0}k/s${color}
${downspeedgraph eth0 000000 ffffff}

---

### Post by Thalskarth on 2008-05-28
Hola, si lo usaste sacandolo desde el mio,

fijate en la linea:
```
# Gap between borders of screen and text
gap_x 10
gap_y 170
```

el 170 es la distancia desde el borde superior hasta el conky, yo lo tengo asi abajo debodo a que pongo un relog cairo-clock en el espacio libre. si le pones menos, conky arrannca más arriba

Que resolucion de pantalla usas?? yo uso 1280*1024 y el conky ocupa de alto toda mi pantalla. Si tu resolucion es menor, te va a quedar fuera de pantalla y podes probar cambiando el tamaño de la letra:

```
# Text stuff
draw_outline yes # amplifies text if yes
draw_borders no
font arial:size=10
uppercase no # set to yes if you want all text to be in uppercase
```
mdificando el 10 por otro valor

---

### Post by lega on 2008-05-28
gracias, si lo solucione cambiando la fuente de la parte del tiempo, de todos modos a la noche me fijo bien como queda tocando la fuente general.
Gracias

---

### Post by villa77 on 2008-05-29
Bueno acá les dejo el mío, modifiqué un poco el de valucha y le sumé un par de cositas más :-)
```

# Update interval in seconds
update_interval 1
# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

background yes

# Create own window instead of using desktop (required in nautilus)
own_window  yes
own_window_transparent no
own_window_type root
own_window_hints undecorate,sticky,skip_taskbar,skip_pager 

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 87 0

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders yes

# Stippled borders?
stippled_borders 0

# border margins
border_margin 6

# border width
border_width 1

# Default colors and also border colors
default_color 303030
#default_shade_color white
#default_outline_color black
own_window_colour 262626

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 5
gap_y 30

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
use_xft yes
xftfont Zekton:size=10

Load "dbe"

TEXT
${color D5C7AD}${alignc}DIEGO-DELL
${color D5C7AD}Uptime:$alignr$uptime
${color D5C7AD}${time %A} ${time %e-%m-%g}$alignr${time %H:%M:%S}


${alignr 30}${color D5C7AD}${font weather:size=30}${execi 3600 python ~/.scripts/conkyForecast.py --location=ARDF0127 --datatype=WF}${font} 
${color D5C7AD}${voffset -24} ${execi 3600 python ~/.scripts/conkyForecast.py --location=ARDF0127 --datatype=HT}
${execi 3600 python ~/.scripts/conkyForecast.py --location=ARDF0127 --datatype=CC}  
Viento: ${execi 3600 python ~/.scripts/conkyForecast.py --location=ARDF0127 --datatype=WS}
Dirreccion: ${execi 3600 python ~/.scripts/conkyForecast.py --location=ARDF0127 --datatype=WD}
Humedad: ${execi 3600 python ~/.scripts/conkyForecast.py --location=ARDF0127 --datatype=HM}


${color D5C7AD}Cpu: ${color D5C7AD}$cpu%
${color B1735E}${cpugraph 20,85 3E3629 776241}  ${color D5C7AD}${alignr}Temp:${acpitemp}C


${color D5C7AD}Ram:  ${color D5C7AD}$memperc% ${alignr}$mem/$memmax
${color B1735E}${membar 3,85}


${color D5C7AD}Disco: ${fs_used_perc /}% ${alignr}${fs_used /}/${fs_size /}
${color B1735E}${fs_bar 3,85} ${color D5C7AD}${alignr}Temp:${hddtemp /dev/sda}


${color D5C7AD}NET: ${addr ppp0}
${color D5C7AD}Up: ${color D5C7AD}${upspeed ppp0} Kb/s ${color D5C7AD}${alignr}Down: ${color D5C7AD}${downspeed ppp0} Kb/s
${color B1735E}${upspeedgraph ppp0 20,85 3E3629 776241} ${color B1735E}${alignr}${downspeedgraph ppp0 20,85 3E3629 776241}


${color D5C7AD}Bateria: ${color D5C7AD}$battery
${color B1735E}${battery_bar 3,85}
```

---

### Post by villa77 on 2008-06-01
Una consulta con respecto a mi conky, cuando es de noche me muestra el sol y no la luna. A que se debe?

---

### Post by _kAz_ on 2008-06-01
Gente necesito ayuda, me gustó el conky que viene haciendo furor en este thread, creo que lo copié de lega, pero tengo varios inconvenientes:

1. De movida no tengo los scripts, de donde los saco??? Los tengo que buscar en algun lado o andan por ahí en mi pc??? Calculo que van en la carpeta ~/.conky/scripts/ que debo crear.

2. En el adjunto verán que cuando lo paso hacia la izquierda pierde la transparencia. Alguna sugerencia?

3. No me gusta ver los segundos en el reloj, me pone nervioso :mad: Como puedo sacarselo?

Desde ya gracias.

---

### Post by santiagoward2000 on 2008-06-02
> **_kAz_ said:**
> Gente necesito ayuda, me gustó el conky que viene haciendo furor en este thread, creo que lo copié de lega, pero tengo varios inconvenientes:

1. De movida no tengo los scripts, de donde los saco??? Los tengo que buscar en algun lado o andan por ahí en mi pc??? Calculo que van en la carpeta ~/.conky/scripts/ que debo crear.

2. En el adjunto verán que cuando lo paso hacia la izquierda pierde la transparencia. Alguna sugerencia?

3. No me gusta ver los segundos en el reloj, me pone nervioso :mad: Como puedo sacarselo?

Desde ya gracias.

Hola!

1. Los scripts para el calendario y el clima estan en el archivo que yo subi, que los saqué del [post de totoloco]("http://ubuntuforums.org/showthread.php?p=4862986#post4862986"), fijate si los encontras.

2. Conky no tiene una transparencia verdadera. Lo que hace es copiar la imagen que tengas en el fondo, por eso te tapa el icono. Lo unico que se puede hacer es poner conky en otro lado o mover el icono.

3. Para sacar los segundos, buscá la parte del archivo que dice: ```
${color white} ${font monospace:size=18}${time %I:%M:%S}${font}
``` y sacá el **:%S**.

Saludos

---

### Post by _kAz_ on 2008-06-02
Va queriendo!!!

Lo único que queda es que me aparezca todo el weather y no esa A!!! Los datos aparentemente están bien porque coinciden con el del awn. Le cambie la localidad a ARCA0023 que es la de Cordoba.

Ah y otra cosa... El calendario está un poco torcido, es así o será que le cambie la tipografía???

**EDIT:** me di cuenta de mi impericia y copie la fuente que venia en el zip al archivo de fuentes. La A desaparecio, pero no muestra nada.

**EDIT2:**Ahora aparece algo... pero es un sol, y siendo las 2 de la mañana medio complicado :lol:

---

### Post by santiagoward2000 on 2008-06-02
> **_kAz_ said:**
> Va queriendo!!!

Lo único que queda es que me aparezca todo el weather y no esa A!!! Los datos aparentemente están bien porque coinciden con el del awn. Le cambie la localidad a ARCA0023 que es la de Cordoba.

Ah y otra cosa... El calendario está un poco torcido, es así o será que le cambie la tipografía???

Para que el weather aparezca con el dibujito tenes que usar las letras que vienen en la carpeta font del archivo. Primero tenes que copiar el archivo **wef_____.ttf** a una carpeta **.fonts** en home (si no existe creala). Despues fijate que en el archivo de conky diga:
```
${font weather:size=120}${execi 300 ~/.conky/scripts/weather2/conditions.sh ARCA0023}${font}
``` Obvio, podes cambiar el tamaño al que quieras, pero no el tipo de letra.
Por lo del calendario, si, es la letra tambien. La mayoria de los tipos tienen distintos tamaños para cada letra, por ejemplo, la **m** puede ocupar mas espacios que la **n**, por eso se desalinea. Para que no pasa tenés que usar un tipo de letra que tenga los mismos espacios, por ejemplo la **Monospace**.
Saludos!

_EDIT:_
Ups, llegue medio tarde, veo que arreglaste lo de la A. Y sobre el sol, esta bien. Estas letras no tienen lunas, asique te va a mostrar el sol aunque sea de noche.

_EDIT2:_
Acabo de probar la letra en el Abi, y vi que si hay lunas. Me imagino que habria que modificar el script para que las use, pero eso ya es un poco mucho para mi :(

---

### Post by kdk on 2008-06-02
Hola, alguien me puede decir como instalar el conky y configurarlo???

Gracias!

---

### Post by santiagoward2000 on 2008-06-02
> **kdk said:**
> Hola, alguien me puede decir como instalar el conky y configurarlo???

Gracias!

Hola!
Para instalarlo, abri una consola y tipia:
```
sudo apt-get install conky
```
Para configurarlo, tenes que crear un archivo en tu home:
```
gedit ~/.conkyrc
```
y ahí escribís la configuracion. Te recomiendo que copies alguno de los que estan aca y lo modifiques, es medio complicado armar uno de cero si nunca lo usaste antes.
Cuando ya esté, lo abrís con el comando:
```
conky
```
Saludos!

---

### Post by _kAz_ on 2008-06-02
> **santiagoward2000 said:**
> 
_EDIT2:_
Acabo de probar la letra en el Abi, y vi que si hay lunas. Me imagino que habria que modificar el script para que las use, pero eso ya es un poco mucho para mi :(

Así es... calculo que hay que cambiar el conditions.sh, lo estaba por hacer anoche pero me dio fiaca :lolflag:

Por lo poco que vi me parece que se complica en donde dice "fairy|sunny" o algo así, porque no disocia si es de día o de noche, sólo si esta despejado.

---

### Post by granjerox on 2008-06-03
Hola a todos, me uno a vosotros en el uso de conky. Sabía hace tiempo de sus bondades pero nunca me había puesto. Hoy he estado todo el día enredando y le he dicho adiós a los screenlets y este es el resultado

```
background yes
font Snap.se:size=8
xftfont Snap.se:size=8
use_xft yes
xftalpha 0.1
update_interval 1.0
total_run_times 0
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders no
minimum_size 206 5
maximum_width 206
default_color ffffff
default_shade_color 000000
default_outline_color 000000
alignment top_right
gap_x 6
gap_y 22
no_buffers yes
cpu_avg_samples 2
override_utf8_locale no
uppercase no # set to yes if you want all text to be in uppercase
use_spacer no

TEXT
${voffset 20}${font LCD:style=Bold:pixelsize=30}${alignc}${time %H:%M:%S}${font Snap.se:size=8}

${font Aerial:style=Bold:pixelsize=12}${color #5da5d3}SYSTEM${font Snap.se:size=8} ${color #ffd700}${hr 1 }
${color #ffffff}
Hostname: $alignr$nodename
Kernel: $alignr$kernel
Uptime: $alignr$uptime
Processes: ${alignr}$processes ($running_processes running)
Load: ${alignr}$loadavg

${color #5da5d3}CPU0$color       ${alignc} ${freq}MHz / ${acpitemp}C ${alignr}(${cpu cpu0}%)
${cpubar 4 cpu0}
${color #5da5d3}CPU1$color       ${alignr}(${cpu cpu1}%)
${cpubar 4 cpu1} 
${cpugraph cccccc ffffff}

${color #5da5d3}RAM $color${alignr}$mem / $memmax ($memperc%)
${membar 4}
${color #5da5d3}SWAP $color${alignr}$swap / $swapmax ($swapperc%)
${swapbar 4}

${color #5da5d3}Highest CPU $alignr CPU% MEM%
${color #ffd700}${hr 1}$color
${top name 1}$alignr${top cpu 1}${top mem 1}
${top name 2}$alignr${top cpu 2}${top mem 2}
${top name 3}$alignr${top cpu 3}${top mem 3}
${top name 4}$alignr${top cpu 4}${top mem 4}

${color #5da5d3}Highest MEM $alignr CPU% MEM%
${color #ffd700}${hr 1}$color
${top_mem name 1}$alignr${top_mem cpu 1}${top_mem mem 1}
${top_mem name 2}$alignr${top_mem cpu 2}${top_mem mem 2}
${top_mem name 3}$alignr${top_mem cpu 3}${top_mem mem 3}
${top_mem name 4}$alignr${top_mem cpu 4}${top_mem mem 4}


${font Aerial:style=Bold:pixelsize=12}${color #5da5d3}FILESYSTEM ${font Snap.se:size=8}${color #ffd700}${hr 1 }$color

Root: ${alignr}${fs_free /} / ${fs_size /}
${fs_bar 4 /}
Home: ${alignr}${fs_free /home} / ${fs_size /home}
${fs_bar 4 /home}
Windows: ${alignr}${fs_free /media/windows} / ${fs_size /media/windows}
${fs_bar 4 /media/windows}
Datos: ${alignr}${fs_free /mnt/datos} / ${fs_size /mnt/datos}
${fs_bar 4 /mnt/datos}


${font Aerial:style=Bold:pixelsize=12}${color #5da5d3}NETWORK ${font Snap.se:size=8}${color #ffd700}${hr 1 }$color

Down ${downspeed eth0} k/s ${alignr}Up ${upspeed eth0} k/s
${downspeedgraph eth0 25,107 000000 ff0000} ${alignr}${upspeedgraph eth0 25,107 000000 00ff00}
Total ${totaldown eth0} ${alignr}Total ${totalup eth0}

${font Aerial:style=Bold:pixelsize=12}${color #5da5d3}PRECICCION en 
${execi 3600 python ~/.conky/conkyForecast.py --location=GMXX0063 --datatype=CN}${font Snap.se:size=8}${color #ffd700}${hr 1 }
${alignr 30}${color D5C7AD}${font weather:size=30}${execi 3600 python ~/.conky/conkyForecast.py --location=GMXX0063 --datatype=WF}$font 
${color D5C7AD}${voffset -24} ${execi 3600 python ~/.conky/conkyForecast.py --location=GMXX0063 --datatype=HT}
${execi 3600 python ~/.conky/conkyForecast.py --location=GMXX0063 --datatype=CC}  
Viento: ${execi 3600 python ~/.conky/conkyForecast.py --location=GMXX0063 --datatype=WS}
Dirreccion: ${execi 3600 python ~/.conky/conkyForecast.py --location=GMXX0063 --datatype=WD}
Humedad: ${execi 3600 python ~/.conky/conkyForecast.py --location=GMXX0063 --datatype=HM}

${if_running /bin/bash /usr/local/bin/exaile-bzr}${voffset 7}${font Webdings:regular:size=21}${color #ba55d3}U${voffset 0}${font Anklepants:regular:size=11}${color #5da5d3}  Music
${voffset -5}${color #ffd700}${hr 1}$font$color
${color #ffe7ba}Title: $color${texeci 20 /home/granjerox/Exaile-BZR/exaile --get-title | head -n 1}
${color #ffe7ba}Album: $color${texeci 20 /home/granjerox/Exaile-BZR/exaile --get-album | head -n 1}
${color #ffe7ba}Artist:$color ${texeci 20 /home/granjerox/Exaile-BZR/exaile --get-artist | head -n 1}
$endif 

```Aunque se ve bastante bien, tengo un par de preguntillas.

1º No consigo que no aparezca la parte de exaile abajo del todo cuando exaile está cerrado
```

${if_running /bin/bash /usr/local/bin/exaile-bzr}${voffset 7}${font Webdings:regular:size=21}${color #ba55d3}U${voffset 0}${font Anklepants:regular:size=11}${color #5da5d3}  Music
${voffset -5}${color #ffd700}${hr 1}$font$color
${color #ffe7ba}Title: $color${texeci 20 /home/granjerox/Exaile-BZR/exaile --get-title | head -n 1}
${color #ffe7ba}Album: $color${texeci 20 /home/granjerox/Exaile-BZR/exaile --get-album | head -n 1}
${color #ffe7ba}Artist:$color ${texeci 20 /home/granjerox/Exaile-BZR/exaile --get-artist | head -n 1}

```2º Aun así, cuando está funcionando, cada vez que actualiza la canción, el conky se queda congelado un par de segundos y después vuelve a funcionar bien. Lo noto por el reloj y las gráficas.

3º Esto es una tontería, pero hace un poco feo y es que si os fijais, en la temperatura
sale una "Á" entre el número y el ºC. ¿sabeis porqué?

Saludos a todos y gracias de antemano.

---

### Post by jjgomera on 2008-06-04
1º No conozco exaile, pero lo que debes poner en la variable if_running es el nombre del proceso, cuando este corriendo el programa abre el monitor del sistema y busca el nombre que tiene el exaile

2º Ya tienes la linea correcta en el conky,

double_buffer yes

pero además debes activarlo en el sistema, para ello edita el archivo /etc/X11/xorg.conf y en la Section "Module" añade la linea:
	Load		"dbe"

3º Cambia en el conky la linea a sí
override_utf8_locale no

---

### Post by granjerox on 2008-06-04
Muchas gracias por la ayuda, he hecho las modificaciones que me recomendaste y han
funcionado. Excepto por lo de detectar cuándo el exaile está activo. El problema es que 
está escrito en python de manera que el programa que realmente está en ejecución es 
python, pero evidentemente no es la única instancia de python ya que utilizo otros 
programas escritos en python, sin ir mas lejos algún plugin de awn.

Cuando hago un ```
ps -uax |grep exaile
```esto es lo que obtengo
```
1000      1810  0.0  0.0   4992  1380 ?        S    16:02   0:00 /bin/bash /usr/local/bin/exaile-bzr
1000      1959  3.8  2.9 147424 61660 ?        Sl   16:03   0:37 python -O exaile.py

```Si pongo la primera en el conkyrc ("/bin/bash /usr/local/bin/exaile-bzr") me detecta las 
instancias de bash, si pongo la segunda ("python -O exaile.py") me aparece un error en 
el terminal respecto a "pidof", si pongo exaile o exaile-bzr, no me detecta nada .......

¿alguna sugerencia?

---

### Post by MeduZa on 2008-06-05
> **granjerox said:**
> Muchas gracias por la ayuda, he hecho las modificaciones que me recomendaste y han
funcionado. Excepto por lo de detectar cuándo el exaile está activo. El problema es que 
está escrito en python de manera que el programa que realmente está en ejecución es 
python, pero evidentemente no es la única instancia de python ya que utilizo otros 
programas escritos en python, sin ir mas lejos algún plugin de awn.

Cuando hago un ```
ps -uax |grep exaile
```esto es lo que obtengo
```
1000      1810  0.0  0.0   4992  1380 ?        S    16:02   0:00 /bin/bash /usr/local/bin/exaile-bzr
1000      1959  3.8  2.9 147424 61660 ?        Sl   16:03   0:37 python -O exaile.py

```Si pongo la primera en el conkyrc ("/bin/bash /usr/local/bin/exaile-bzr") me detecta las 
instancias de bash, si pongo la segunda ("python -O exaile.py") me aparece un error en 
el terminal respecto a "pidof", si pongo exaile o exaile-bzr, no me detecta nada .......

¿alguna sugerencia?

pregunte lo mismo varias paginas antes y nunca encontre como detectar el proceso de exaile, simplemente desde conky es imposible!
o detecta a python o detecta otra cosa!

---

### Post by granjerox on 2008-06-05
Se me ha ocurrido una cosa, aunque no se cómo hacerlo. Se trataría de un script latente 
que corriera a la vez que exaile.  Mientras que exaile esté activo, el script debería crear 
un archivo y cuando exaile se cierre, borrar el archivo. De esta manera desde conky se 
podría comprobar si el archivo existe con la variable if_existing.

¿sabeis cómo se haría?

---

### Post by granjerox on 2008-06-05
Me respondo yo mismo :D, problema solucionado

script para comprobar si exaile está corriendo "check_exaile.sh" recordar hacerlo ejecutable.
```
#!/bin/bash

while true
do
    if ps ax | grep -v grep | grep '/bin/bash /usr/local/bin/exaile-bzr' > /dev/null
    then
            touch /tmp/exaile.chk
            sleep 5
    else
            rm /tmp/exaile.chk
        break
    fi

done

```

Debeis modificar grep '/bin/bash /usr/local/bin/exaile-bzr' con lo que os salga  a vosotros. En conkyrc poneis ${if_existing /tmp/exaile.chk} y listo.

---

### Post by Air23 on 2008-07-16
Hola, no me funciona pero me parece que no hay algo que no estoy entendiendo. Ya cree el script (y le di permisos de ejecucion), pero no se a que te referis con esto:
> **granjerox said:**
> Debeis modificar grep '/bin/bash /usr/local/bin/exaile-bzr' con lo que os salga  a vosotros

Ademas en mi .conkyrc tengo que poner ${if_existing /tmp/exaile.chk} y luego que mas?

Muchas gracias

---

### Post by N3RI on 2008-12-02
> **Mauro22 said:**
> Buenas!!
```

${color white}CPU ${color orange} @$**{freq_g}MHz**   ${cpu cpu0}%  $cpubar

```
Sé que es bastante viejo, pero quería comentar que noté que estás usando {freq_g} que te devuelve la frecuencia en GHz, pero le pusiste MHz al costado.

---

### Post by c4d0rn4 on 2008-12-02
.conkyrc

```
use_spacer yes
use_xft yes
xftfont Vera-8
xftalpha 1
update_interval 10.0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_hints below
double_buffer yes
minimum_size 200 5
maximum_width 250
draw_shades no
draw_outline no # amplifies text
draw_borders no
stippled_borders 3
border_margin 5
border_width 6
alignment top_right
gap_x 24
gap_y 24
no_buffers yes
color0 61B7E6
color1 e5e5e5
color2 ff9900
color3 0000ff
color4 white
color5 5896B4

TEXT
$color4 ${font Century Gothic:size=14}perez${font}$alignr ${time %a}${time %e %B %G}|${font OpenLogos:size=14}uJT${font}
${color0} User ${hr 1}
  $color1 ${execi 30 whoami} @ $nodename $alignr $sysname $machine $kernel
   ${execi 1000 cat /proc/cpuinfo | grep 'model name' | sed -e 's/model name.*: //'} $alignr${freq_g} GHz
   uptime $alignr $uptime_short

$color0 System (${execi 1200 ~/scripts/pogodynka.sh})${hr 1} 
  $color1 cpu usage $color $alignr $cpu%
   load $alignr $loadavg
${alignr}$color5${cpugraph cpu0 10,245 e5e5e5 e5e5e5 }

$color0 Processes${tab 44}Cpu %${tab 20}Ram%${alignr}M.Ram   
  $color1${font Sans:size=6}${top name 1}${tab 30 start} ${top cpu 1}${tab 20}${top mem 1}${alignr}${top mem_res 1}
   ${top name 2}${tab 30 start} ${top cpu 2}${tab 20}${top mem 2}${alignr}${top mem_res 2}
   ${top name 3}${tab 30 start} ${top cpu 3}${tab 20}${top mem 3}${alignr}${top mem_res 3}
   ${top name 4}${tab 30 start} ${top cpu 4}${tab 20}${top mem 4}${alignr}${top mem_res 4}
   ${top name 5}${tab 30 start} ${top cpu 5}${tab 20}${top mem 5}${alignr}${top mem_res 5}
$alignr $color0 Running$color1 $running_processes / $processes ${font}
${font}$color0 Top Mem: $color1 ${top_mem name 1} $color0${font Sans:size=6} ${top_mem name 2} ${top_mem name 3}{hr 1}
$alignr $color0 ${font}Used$color1${font Sans:size=6} $memperc% $color0$mem / $memmax ${font}

$color0 Wired ($color2 ${addr eth0}$color0) ${hr 1}
  $color1 down $color2 ${downspeedf eth0} $color1 k/s ${alignr}$color1 up $color3 ${upspeedf eth0} $color1 k/s
   total down: ${totaldown eth0} $alignr total up: ${totalup eth0}
${alignr}$color5${downspeedgraph eth0 10,245 e5e5e5 e5e5e5 }

$color0 File Systems ( ${font weather:size=10}x $font HDD ${execi 1 ~/scripts/hddmonit.sh}°C )${hr 1}
 $color1 home $color4 ${fs_free /} (${fs_free_perc /}%) $color1 free of ${fs_size /}
       ${fs_bar /}
  $color1 win Xp $color4 ${fs_free /media/sda1} (${fs_free_perc /media/sda1}%) $color1 free of ${fs_size /media/sda1}
       ${fs_bar /media/sda1}
  $color1 zero $color4 ${fs_free /media/sda5} (${fs_free_perc /media/sda5}%) $color1 free of ${fs_size /media/sda5}
       ${fs_bar /media/sda5}
${alignr}$color5${diskiograph  10,245 e5e5e5 e5e5e5 }
${if_running rhythmbox}$color0 Listening (${execi 1 rhythmbox-client --print-playing-format "%te / %td"})${hr 1} 
                          $color1${execi 1 rhythmbox-client --print-playing-format "%ta"}$color0${hr 1}
${alignr}${execi 1 rhythmbox-client --print-playing-format "%tt"} ${hr 1}${else}${endif}
```

~/scripts/pogodynka.sh
```
#!/bin/bash
sciezka=~/scripts
kod=ARDF0002
plik=~/weather
 	w3m -dump http://weather.yahoo.com/forecast/"$kod"_c.html | grep -A21 "Current" | sed 's/DEG/°/g' > $plik

	stan=`head -n3 $plik | tail -n1`
	temp=`tail -n1 $plik | awk '{print $1}'`
	tempo=`head -n6 $plik | tail -n1`
	cisn=`head -n8 $plik | tail -n1`
	wiatr=`head -n16 $plik | tail -n1`
	wilg=`head -n10 $plik | tail -n1`
	wsch=`head -n18 $plik | tail -n1`
	zach=`head -n20 $plik | tail -n1`
	if [ `cat "$sciezka"/pogodynka.sh | grep -x "# $stan" | wc -l` -eq 0 ]
	  then
		stanpl=$stan
	  else
		stanpl=`cat "$sciezka"/pogodynka.sh | grep -xA1 "# $stan" | tail -n1 | awk '{print $2,$3,$4,$5,$6,$7}'`
	fi

	echo $temp C  / $zach / $stan
```

[[IMG]http://img352.imageshack.us/img352/5489/conkyhc2.th.png[/IMG]](http://img352.imageshack.us/img352/5489/conkyhc2.png)

---

### Post by feche_mza on 2008-12-03
aca esta mi conky en proceso de construccion, me faltaria algun script para que el viento me muestre una veleta o una flechita con la direccion a donde va.Gracias a LethalBoy y a staar que me inspiraron para poner el script del amarok y al final lo hice andar y ahora tengo la barra de progreso

---

### Post by viper3k on 2008-12-28
> **feche_mza said:**
> aca esta mi conky en proceso de construccion, me faltaria algun script para que el viento me muestre una veleta o una flechita con la direccion a donde va.Gracias a LethalBoy y a staar que me inspiraron para poner el script del amarok y al final lo hice andar y ahora tengo la barra de progreso

me encanto tu conky! que font usastes para escribir "red"?

---

### Post by andy_91 on 2008-12-29
bueno este es el mio, esta basado en este: > **Kabezon said:**
> [kabeconkyrc.tar.gz]("http://ubuntuforums.org/attachment.php?attachmentid=95336&d=1228451024")

Pero le hice algunos cambios a la manera que pude:

```
#Albertronics Conky

double_buffer yes

#own window to run simultanious 2 or more conkys
own_window yes
own_window_type normal
own_window_transparent no
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

#borders

draw_borders no

border_margin 0
border_width 3
draw_outline no
default_outline_color 777777

#shades

draw_shades no

#position
gap_x 0

gap_y 0

alignment bottom_right

#behaviour

update_interval 1

#colour

default_color ffffff

#default_shade_color 359748

own_window_colour 0e1219

#font

use_xft yes

xftfont bauhaus:pixelsize=11

#to prevent window from moving

use_spacer yes

minimum_size 1680 11

#mpd

mpd_host localhost

mpd_port 6600

draw_graph_borders no


TEXT
*************************************************************************************************************${color white} Kernel: $kernel ${color 1793D1}|${color white} CPU: ${cpu}% ${cpubar 6,80 } ${color 1793D1}|${color white} Ram: $memperc% ${membar 6,80} ${color 1793D1}|${color white} Swap:$swapperc% ${swapbar 6,80} ${color 1793D1}|${color white} Sistema de archivos: ${fs_used_perc /}% ${fs_bar 6,80 /} ${color 1793D1}| ${color white}${time %A %x} ${execi 600 python ~/.scripts/conkyForecast.py --location=ARBA0043 --datatype=HT}
```
***************************EDIT****************************************

la k de kernel se ve entera, es que a mi se me corto cuando recorte el conky

---

### Post by viper3k on 2008-12-29
mi conky , no sabia bien como usar al gimp asiq recorte y pegue en un fondo blanco x eso quedaron los bordes blancos =)

```

use_xft yes
xftfont verdana:size=8
alignment top_right
xftalpha 0.8
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
stippled_borders 10
border_margin 4
border_width 1
default_shade_color white
default_outline_color black
use_spacer none
no_buffers yes
uppercase no
color1 F8DF58

#Gmail
#${font FreeSans:size=16}@${font}${execpi 300 python ~/.scripts/gmail_parser.py user password 3}

TEXT
${font Radio Space:size=22}${alignc}Viper3k
${font Radio Space}HORA ${hr 2}
             ${font Radio Space:size=45}${time %H:%M}${font}
${font Radio Space:size=14}${time %A %d %Y}
${font Radio Space}SISTEMA ${hr 2}
${font OpenLogos:size=16}u${font}  Kernel:  ${alignr}${kernel}
${font StyleBats:size=16}A${font}  CPU0: ${cpu cpu0}% ${alignr}${cpugraph 8,60 F78F19 FCC375 cpu0}
${font StyleBats:size=16}A${font}  CPU1: ${cpu cpu1}% ${alignr}${cpugraph 8,60 F78F19 FCC375 cpu1}
${font PizzaDude Bullets:size=14}J${font} RAM:  $memperc% ${alignr}${membar 8,60}
${font PizzaDude Bullets:size=14}L${font} SWAP: $swapperc% ${alignr}${swapbar 8,60}
${font StyleBats:size=16}P${font}  Logeado: ${alignr}${uptime}

${font Radio Space}UNIDAD ${hr 2}
${font PizzaDude Bullets:size=16}m${font} Raiz:
${fs_used /}/${fs_size /} $alignr${fs_bar 8,60 /}

${font Radio Space}WIRED ${hr 2}  
${if_existing /proc/net/route wlan0}    
${font PizzaDude Bullets:size=16}v${font}   Up: ${upspeed wlan0} kb/s $alignr${upspeedgraph wlan0 8,60 F78F19 FCC375}
${font PizzaDude Bullets:size=16}r${font}   Down: ${downspeed wlan0} kb/s $alignr${downspeedgraph wlan0 8,60 F78F19 FCC375}
${font PizzaDude Bullets:size=16}M${font}   Upload: $alignr${totalup wlan0}
${font PizzaDude Bullets:size=16}S${font}   Download: $alignr${totaldown wlan0}
${font PizzaDude Bullets:size=16}Y${font}   Sinal: ${wireless_link_qual wlan0}% $alignr${wireless_link_bar 8,60 wlan0}
${font PizzaDude Bullets:size=16}t${font}   Ip Local: $alignr${addr wlan0}
${font PizzaDude Bullets:size=16}u${font}   Ip Público: $alignr${execi 1 ~/.scripts/ip.sh}

${alignr}${downspeedgraph eth0 10,245 e5e5e5 e5e5e5 }
${else}${if_existing /proc/net/route eth0}
${font PizzaDude Bullets:size=16}v${font}   Up: ${upspeed eth0} kb/s $alignr${upspeedgraph eth0 8,60 F78F19 FCC375}
${font PizzaDude Bullets:size=16}r${font}   Down: ${downspeed eth0} kb/s $alignr${downspeedgraph eth0 8,60 F78F19 FCC375}
${font PizzaDude Bullets:size=16}M${font}   Upload: $alignr${totalup eth0}
${font PizzaDude Bullets:size=16}S${font}   Download: $alignr${totaldown eth0}
${font PizzaDude Bullets:size=16}t${font}   Ip Local: $alignr${addr eth0}
${font PizzaDude Bullets:size=16}u${font}   Ip Público: $alignr${execi 1 ~/.scripts/ip.sh}

${alignr}${downspeedgraph eth0 10,245 e5e5e5 e5e5e5 }
${endif}${else}${if_existing /proc/net/route eth1}
${font PizzaDude Bullets:size=16}v${font}   Up: ${upspeed eth1} kb/s $alignr${upspeedgraph eth1 8,60 F78F19 FCC375}
${font PizzaDude Bullets:size=16}r${font}   Down: ${downspeed eth1} kb/s $alignr${downspeedgraph eth1 8,60 F78F19 FCC375}
${font PizzaDude Bullets:size=16}M${font}   Upload: $alignr${totalup eth1}
${font PizzaDude Bullets:size=16}S${font}   Download: $alignr${totaldown eth1}
${font PizzaDude Bullets:size=16}t${font}   Ip Local: $alignr${addr eth1}
${font PizzaDude Bullets:size=16}u${font}   Ip Público: $alignr${execi 1 ~/.scripts/ip.sh}

${alignr}${downspeedgraph eth0 10,245 e5e5e5 e5e5e5 }
${endif}${else}
${font PizzaDude Bullets:size=16}4${font}   Red indisponible
${endif}

${if_running amarokapp}${font Radio Space}NOW PLAYING ${hr 2}
${alignc}${execi 10 ~/.conky/amarok artist}
${alignc}${execi 10 ~/.conky/amarok title}
${execibar 1 ~/.conky/amarok progress}
${alignc}${execi 10 ~/.conky/amarok album}
${endif}
${font Radio Space}Gmail ${hr 2}
${font FreeSans:size=16}@${font}${execpi 300 python ~/.scripts/gmail_parser.py fran89fran catriel89viper 3}${color}
${font Radio Space}Clima ${hr 2}
${font weather:size=50}${execi 600 ~/.scripts/conditions.sh}${color}${font}${voffset -25}  ${execi 1200 ~/.scripts/pogodynka.sh}


```

saludos:KS

---

### Post by andy_91 on 2008-12-29
¿por que el clima en Fahrenheit?

---

### Post by feche_mza on 2008-12-29
> **viper3k said:**
> me encanto tu conky! que font usastes para escribir "red"?

No se llaman , Futurama Bold Font, originalmente queria ponerle las bauhaus que usa valucha pero no las encontre y termine poniendole estas que ahora me gustan mas :)

---

### Post by jjgomera on 2008-12-29
pues yo pego una captura de mi escritorio completo, ya que casi todo es puro conky

[[IMG]http://img267.imageshack.us/img267/8160/pantallazo4jl0.th.png[/IMG]](http://img267.imageshack.us/img267/8160/pantallazo4jl0.png)

---

### Post by oktubrum on 2008-12-29
> **viper3k said:**
> mi conky , no sabia bien como usar al gimp asiq recorte y pegue en un fondo blanco x eso quedaron los bordes blancos =)

```

...

```

saludos:KS

No se si te avisaron o no, pero en el código me parece que te quedó la clave de gmail, sería bueno que la cambies (o que la edite un moderador) 
=)

Saludos!

---

### Post by exegeses on 2009-05-11
> **santiagoward2000 said:**
> Para que el weather aparezca con el dibujito tenes que usar las letras que vienen en la carpeta font del archivo. Primero tenes que copiar el archivo **wef_____.ttf** a una carpeta **.fonts** en home (si no existe creala). Despues fijate que en el archivo de conky diga:
```
${font weather:size=120}${execi 300 ~/.conky/scripts/weather2/conditions.sh ARCA0023}${font}
```


quise agregar esta línea para que se viese el clima:

```
${font weather:size=120}${execi 1200 /home/exegeses/scripts/conkyscripts/conditions.sh ARBA0009}${font}

```

todo bien, ya lo logré, ahora:::

cómo hago para verlo en español???
para ver los grados veo al lado del número de grados un chirimbolo como una A con sombrerito. ¿cómo lo corrijo?
¿será el charset?  ¿será el utf? ¿será el frío?

desde ya, muchas gracias

saludos

---

### Post by exegeses on 2009-05-11
> **feche_mza said:**
> aca esta mi conky en proceso de construccion, me faltaria algun script para que el viento me muestre una veleta o una flechita con la direccion a donde va.Gracias a LethalBoy y a staar que me inspiraron para poner el script del amarok y al final lo hice andar y ahora tengo la barra de progreso

pasás el script??
gracias

---

### Post by sartrejp on 2009-06-14
Este es mi conky, y acá el .conkyrc
```
background yes
cpu_avg_samples 2
net_avg_samples 2
out_to_console no
use_xft yes
xftfont Bitstream Vera Sans Mono:size=9
xftalpha 0.8
mail_spool $MAIL
update_interval 1
own_window yes
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 280 5
maximum_width 270
draw_shades no
draw_outline no
draw_borders no
stippled_borders no
border_margin 4
border_width 1

alignment top_right
gap_x 7
use_spacer none

no_buffers yes

uppercase no

TEXT
${color #FFFFFF}
$stippled_hr
$nodename
${execi 99999 lsb_release -d -s -c | tr -s "\n" " "}
$kernel on $machine
$stippled_hr
Intel® Core™2 Duo E6600 2.4 GHz
CPU:1  ${cpu cpu1}% ${cpubar cpu1}
CPU:2  ${cpu cpu2}% ${cpubar cpu2}
$stippled_hr
memory:
 ram:  ${alignr}$mem / $memmax
    ${membar 10,200}
 swap: ${alignr}$swap / $swapmax
    ${swapbar 10,200}
$stippled_hr
hard disks:
 root   ${alignr}${fs_used /} / ${fs_size /}
    ${fs_bar 10,200 /}
 home   ${alignr}${fs_used /home} / ${fs_size /home}
    ${fs_bar 10,200 /home}
$stippled_hr
cpu usage: ${alignr}CPU%
 ${top name 1}  ${alignr}${top cpu 1}
 ${top name 2}  ${alignr}${top cpu 2}
 ${top name 3}  ${alignr}${top cpu 3}
 ${top name 4}  ${alignr}${top cpu 4}
$stippled_hr
mem usage: ${alignr}MEM%
 ${top_mem name 1}  ${alignr}${top_mem mem 1}
 ${top_mem name 2}  ${alignr}${top_mem mem 2}
 ${top_mem name 3}  ${alignr}${top_mem mem 3}
 ${top_mem name 4}  ${alignr}${top_mem mem 4}
$stippled_hr
network:
 IP ${addr eth0}
down: ${downspeed eth0} k/s ${alignr}up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,120 000000 000000} $alignr${upspeedgraph eth0 25,120 000000 000000}
${totaldown eth0} $alignr${totalup eth0}
$stippled_hr
${color }WIFI (${addr wlan0}) ${hr 2}$color
Down: $color${downspeed wlan0} k/s ${alignr}Up: ${upspeed wlan0} k/s
${downspeedgraph wlan0 25,140 000000 ff0000} ${alignr}${upspeedgraph wlan0
25,140 000000 00ff00}$color
Total: ${totaldown wlan0} ${alignr}Total: ${totalup wlan0}
```

Alguien sabe como puedo hacer para subirlo un poco (para que no deje tanto espacio arriba) y para agrandarle el tamaño, así llega hasta abajo y no queda cortado?

---

### Post by staar on 2009-06-14
con las opciones ```
gap_x *valor*
gap_y *valor*
``` regulas el espacio hasta el borde de la pantalla, y con ```
minimum_size *ancho* *alto*
``` regulas el tamaño mínimo...

saludos

---

### Post by sartrejp on 2009-06-15
Espectacular, gracias!

---

### Post by Bruce M. on 2009-07-07
Hola gente,

El tiempo para Buenos Aires (y el mundo) con una programa del python: [Conky Weather Forecast Python Script]("http://ubuntuforums.org/showthread.php?t=869328"). (imagen una)

El tiempo para Buenos Aires (y el mundo) con [Desktop Info App With Html Support (gtk-desktop-info)]("http://ubuntuforums.org/showthread.php?p=6366056") (imagen dos)

[Ver mi conky aquí.]("http://conky.linux-hardcore.com/?page_id=297")

NOTA: mi idioma no es castellano, pero ayudaré si puedo. (Santiago - JJ, ayúdame, please) [-o<

Y algo mas, un **.deb** de: [conky_1.7.1.1-1_amd64.deb]("http://conky.linux-hardcore.com/?page_id=1334") hecho por mi, con imágenes: ver uno con mi avatar: [aquí]("http://conky.linux-hardcore.com/")

Que tengas un buen día
Bruce

---

### Post by sitodonosti on 2009-07-26
Hola estoy configurando mi conky y me gustaría saber como habeis puesto para que te aparezcan los mails en el conky, los de gmail. 

especialmente me a gustado el de jjgomera que tiene puesto el asunto del mail si no me equiboco, sabrías como hacerlo?o en su caso como poner gmail sin script¿

Bruce, cómo has puesto los script del tiempo?el de la segunda foto, me he bajado gtk-desktop-info pero nose como arrancarlo...:$
gracias!

p.d.:ya he conseguido que me aparezca gmail aunque ha sido con un script me gustaria saber si se puede hacer sin él

---

### Post by matias_tati on 2009-07-26
> **viper3k said:**
> mi conky , no sabia bien como usar al gimp asiq recorte y pegue en un fondo blanco x eso quedaron los bordes blancos =)

```

use_xft yes
xftfont verdana:size=8
alignment top_right
xftalpha 0.8
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
stippled_borders 10
border_margin 4
border_width 1
default_shade_color white
default_outline_color black
use_spacer none
no_buffers yes
uppercase no
color1 F8DF58

#Gmail
#${font FreeSans:size=16}@${font}${execpi 300 python ~/.scripts/gmail_parser.py user password 3}

TEXT
${font Radio Space:size=22}${alignc}Viper3k
${font Radio Space}HORA ${hr 2}
             ${font Radio Space:size=45}${time %H:%M}${font}
${font Radio Space:size=14}${time %A %d %Y}
${font Radio Space}SISTEMA ${hr 2}
${font OpenLogos:size=16}u${font}  Kernel:  ${alignr}${kernel}
${font StyleBats:size=16}A${font}  CPU0: ${cpu cpu0}% ${alignr}${cpugraph 8,60 F78F19 FCC375 cpu0}
${font StyleBats:size=16}A${font}  CPU1: ${cpu cpu1}% ${alignr}${cpugraph 8,60 F78F19 FCC375 cpu1}
${font PizzaDude Bullets:size=14}J${font} RAM:  $memperc% ${alignr}${membar 8,60}
${font PizzaDude Bullets:size=14}L${font} SWAP: $swapperc% ${alignr}${swapbar 8,60}
${font StyleBats:size=16}P${font}  Logeado: ${alignr}${uptime}

${font Radio Space}UNIDAD ${hr 2}
${font PizzaDude Bullets:size=16}m${font} Raiz:
${fs_used /}/${fs_size /} $alignr${fs_bar 8,60 /}

${font Radio Space}WIRED ${hr 2}  
${if_existing /proc/net/route wlan0}    
${font PizzaDude Bullets:size=16}v${font}   Up: ${upspeed wlan0} kb/s $alignr${upspeedgraph wlan0 8,60 F78F19 FCC375}
${font PizzaDude Bullets:size=16}r${font}   Down: ${downspeed wlan0} kb/s $alignr${downspeedgraph wlan0 8,60 F78F19 FCC375}
${font PizzaDude Bullets:size=16}M${font}   Upload: $alignr${totalup wlan0}
${font PizzaDude Bullets:size=16}S${font}   Download: $alignr${totaldown wlan0}
${font PizzaDude Bullets:size=16}Y${font}   Sinal: ${wireless_link_qual wlan0}% $alignr${wireless_link_bar 8,60 wlan0}
${font PizzaDude Bullets:size=16}t${font}   Ip Local: $alignr${addr wlan0}
${font PizzaDude Bullets:size=16}u${font}   Ip Público: $alignr${execi 1 ~/.scripts/ip.sh}

${alignr}${downspeedgraph eth0 10,245 e5e5e5 e5e5e5 }
${else}${if_existing /proc/net/route eth0}
${font PizzaDude Bullets:size=16}v${font}   Up: ${upspeed eth0} kb/s $alignr${upspeedgraph eth0 8,60 F78F19 FCC375}
${font PizzaDude Bullets:size=16}r${font}   Down: ${downspeed eth0} kb/s $alignr${downspeedgraph eth0 8,60 F78F19 FCC375}
${font PizzaDude Bullets:size=16}M${font}   Upload: $alignr${totalup eth0}
${font PizzaDude Bullets:size=16}S${font}   Download: $alignr${totaldown eth0}
${font PizzaDude Bullets:size=16}t${font}   Ip Local: $alignr${addr eth0}
${font PizzaDude Bullets:size=16}u${font}   Ip Público: $alignr${execi 1 ~/.scripts/ip.sh}

${alignr}${downspeedgraph eth0 10,245 e5e5e5 e5e5e5 }
${endif}${else}${if_existing /proc/net/route eth1}
${font PizzaDude Bullets:size=16}v${font}   Up: ${upspeed eth1} kb/s $alignr${upspeedgraph eth1 8,60 F78F19 FCC375}
${font PizzaDude Bullets:size=16}r${font}   Down: ${downspeed eth1} kb/s $alignr${downspeedgraph eth1 8,60 F78F19 FCC375}
${font PizzaDude Bullets:size=16}M${font}   Upload: $alignr${totalup eth1}
${font PizzaDude Bullets:size=16}S${font}   Download: $alignr${totaldown eth1}
${font PizzaDude Bullets:size=16}t${font}   Ip Local: $alignr${addr eth1}
${font PizzaDude Bullets:size=16}u${font}   Ip Público: $alignr${execi 1 ~/.scripts/ip.sh}

${alignr}${downspeedgraph eth0 10,245 e5e5e5 e5e5e5 }
${endif}${else}
${font PizzaDude Bullets:size=16}4${font}   Red indisponible
${endif}

${if_running amarokapp}${font Radio Space}NOW PLAYING ${hr 2}
${alignc}${execi 10 ~/.conky/amarok artist}
${alignc}${execi 10 ~/.conky/amarok title}
${execibar 1 ~/.conky/amarok progress}
${alignc}${execi 10 ~/.conky/amarok album}
${endif}
${font Radio Space}Gmail ${hr 2}
${font FreeSans:size=16}@${font}${execpi 300 python ~/.scripts/gmail_parser.py fran89fran catriel89viper 3}${color}
${font Radio Space}Clima ${hr 2}
${font weather:size=50}${execi 600 ~/.scripts/conditions.sh}${color}${font}${voffset -25}  ${execi 1200 ~/.scripts/pogodynka.sh}


```saludos:KS

Hola copie el tuyo pero es la primera vez que hago esto me ayudas a configurar los scripts y me gustaria cambiar el color a negro pq mi wallpaper es blanco y se me pierde, ah y donde dice Viper3k me gustaria que dijera mi nombre. PD no se como cortar la imagen

---

### Post by matias_tati on 2009-07-26
....................................

---

### Post by staar on 2009-07-26
> **matias_tati said:**
> Hola copie el tuyo pero es la primera vez que hago esto me ayudas a configurar los scripts y me gustaria cambiar el color a negro pq mi wallpaper es blanco y se me pierde, ah y donde dice Viper3k me gustaria que dijera mi nombre. PD no se como cortar la imagen
para cambiar el color de conky existe la opción 'default_color', simplemente abrís el conkyrc y agregás una línea (las opciones para correr conky, como esta, van antes de la línea que dice TEXT, lo que va después de dicha línea es lo que conky imprime) así ```
default_color black
``` para el negro (también podés poner el código del color)

para cambiar el Viper3k por tu nombre, modificá la primera línea después de TEXT, al final...

veo también que te faltan algunas fuentes para que quede igual, por eso te salen esas letras (es un truco que se suele hacer con conky, como este solo imprime texto, se usan fuentes con símbolos para adornarlo), la variable 'font' permite definir la fuente, fijate que te faltan Radio Space, OpenLogos, StyleBats, PizzaDude Bullets y weather, buscalas por [dafont.com]("http://dafont.com") o con google...

también te faltan los scripts a los que ese conkyrc llama (con la variable execi) ahi no te puedo ayudar porque no se cuales usó Viper3k, pero podés pasarte por [gnome-look.org]("http://gnome-look.org") que ahí hay varios conkyrcs y scripts, con todo lo necesario para usarlos, y desde los que podés partir para modificar el tuyo...

EDIT: otro buen lugar para ver, es este [thread]("http://ubuntuforums.org/showthread.php?t=281865") de la parte internacional del foro, 830 páginas de conky :-D algunos son impresionantes...

saludos

---

### Post by matias_tati on 2009-07-27
Ah buenisimo entonces pruebo eso, me fijo en el thread y espero la ayuda de Viper3k.
Ya cambie el color del texto ahora una pregunta, donde copio las fuentes?

---

### Post by matias_tati on 2009-07-27
Ya esta lo de las fuentes. Me faltaria que Viper3k me tire un salvavidas con los scripts.

---

### Post by matias_tati on 2009-07-27
Y en el terminal no me salen los script que necesito cuando ejecuto el conky? Pq no se de donde sacarlos. Saludos!

---

### Post by staar on 2009-07-27
en el conkyrc te podés fijar, mirando rápido veo uno que se llama ip.sh, otro amarok, otro gmail_parser.py, otro conditions.sh, pero eso no sirve de mucho ya que cada uno puede cambiarle el nombre como quiera al script...

mirando un poco mejor la screenshot me doy cuenta de que ese conky es parecido (y supongo que basado en) a uno muy conocido, que se llama CONKY-colors, que está posteado [acá]("http://www.gnome-look.org/content/show.php/CONKY-colors?content=92328") con todo lo necesario para dejarlo bien...

saludos

---

### Post by matias_tati on 2009-07-27
Y no les puedo cambiar directamente los scripts por otros? Lo que me interesa son las fuentes de este y lo que quiero es que me diga el clima y los mail de gmail ya con esa estoy por ahora. 
PD intente seguir el de conky colors y mori en el intento.

---

### Post by matias_tati on 2009-07-28
Quedo hermoso descarte el otro e instale este siguiendo este [tutorial]("http://www.quicktweaks.com/2008/09/27/gmail-weather-beauty-right-on-your-ubuntu-desktop/") para el que le sirva sobretodo a los mas novatos. Solo me faltaria cambiar los Farenheit por grados. Saludos.

---

### Post by matias_tati on 2009-07-28
Ayuda para pasar a grados Celsius? en el tutorial me pide que reemplaze una linea pero cuando lo hago me queda algo que nada que ver. Gracias.

---

### Post by Fak89 on 2009-07-28
Bueno, aca comparto mi conkyrc..
Esta basado en el diseño default..

La "seccion" de musica es para el reproductor Audacious..

```
use_xft yes
xftfont Liberation Sans:size=8

update_interval 1
total_run_times 0
double_buffer yes
text_buffer_size 2048

own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

minimum_size 185 0
maximum_width 185

default_color white
draw_shades no

color0 white
color1 CCCCCC
color2 white

alignment top_right
gap_x 25
gap_y 75

no_buffers no
net_avg_samples 2

override_utf8_locale yes

no_buffers yes

TEXT
${alignc 45}${color2}${font Arial Black:size=30}${time %H:%M}${font}${color}
${alignc}${time %A %d %Y}


${alignc 45}${font Monospace:size=7.5}${exec ~/.scripts/calendar.sh}${font}


SISTEMA ${hr 2}
${execi 99999 lsb_release -d -s -c | tr -s "\n" " "}
$kernel on $machine
${color0}${font StyleBats:size=16}q${font}${color}   UPTIME: ${alignr}${color2}${uptime}${color}
$stippled_hr
AMD Phenom&#8482; X4 Quad-Core 9950 2.4 GHz
${color0}${font StyleBats:size=16}A${font}${color}   CPU1: ${font Liberation Sans:style=Bold:size=8}${color1}${cpu cpu1}%${color}${font} ${alignr}${color2}${cpubar cpu1 8,60}${color}
${color0}${font StyleBats:size=16}A${font}${color}   CPU2: ${font Liberation Sans:style=Bold:size=8}${color1}${cpu cpu2}%${color}${font} ${alignr}${color2}${cpubar cpu2 8,60}${color}
${color0}${font StyleBats:size=16}A${font}${color}   CPU3: ${font Liberation Sans:style=Bold:size=8}${color1}${cpu cpu3}%${color}${font} ${alignr}${color2}${cpubar cpu3 8,60}${color}
${color0}${font StyleBats:size=16}A${font}${color}   CPU4: ${font Liberation Sans:style=Bold:size=8}${color1}${cpu cpu4}%${color}${font} ${alignr}${color2}${cpubar cpu4 8,60}${color}
$stippled_hr
${color0}${font StyleBats:size=16}g${font}${color}   RAM: ${font Liberation Sans:style=Bold:size=8}${color1}$memperc%${color}${font} ${alignr}${color2}${membar 8,60}${color}
${color0}${font StyleBats:size=16}j${font}${color}   SWAP: ${font Liberation Sans:style=Bold:size=8}${color1}$swapperc%${color}${font} ${alignr}${color2}${swapbar 8,60}${color}
$stippled_hr
${color0}${font Pie charts for maps:size=14}7${font}${color}   HDD: ${font Liberation Sans:style=Bold:size=8}${color1}${diskio}${color} ${alignr}${color2}${diskiograph 8,60}${color}


DISCO ${hr 2}
${font Pie charts for maps:size=14}7${font} ${voffset -5}HOME:
${color0}${font Liberation Sans:style=Bold:size=8}${color1}${fs_free /home}/${fs_size /home}${color}${font} ${alignr}${fs_bar 8,60 /home}
${color0}${font Pie charts for maps:size=14}7${font}${font} ${voffset -5}C:
${color0}${font Liberation Sans:style=Bold:size=8}${color1}${fs_used /media/disk-1}/${fs_size /media/disk-1}${color}${font} ${alignr}${fs_bar 8,60 /media/disk-1}
${color0}${font Pie charts for maps:size=14}7${font}${font} ${voffset -5}D:
${color0}${font Liberation Sans:style=Bold:size=8}${color1}${fs_used /media/disk}/${fs_size /media/disk}${color}${font} ${alignr}${fs_bar 8,60 /media/disk}


NET ${hr 2}
${color0}${font PizzaDude Bullets:size=14}O${font}${color}   UP: ${font Liberation Sans:style=Bold:size=8}${color1}${upspeed eth0} k/s${font}${color}
${color0}${font PizzaDude Bullets:size=14}U${font}${color}   DOWN: ${font Liberation Sans:style=Bold:size=8}${color1}${downspeed eth0} k/s${font}${color}
$stippled_hr
${color0}${font PizzaDude Bullets:size=14}N${font}${color}   UPLOAD: ${font Liberation Sans:style=Bold:size=8}${color1}${totalup eth0}${color}
${color0}${font PizzaDude Bullets:size=14}T${font}${color}   DOWNLOAD: ${font Liberation Sans:style=Bold:size=8}${color1}${totaldown eth0}${color}${font}






MUSICA ${hr 2}
$alignc${color1}${font Liberation Sans:style=Bold:size=8}${exec audtool current-song}${font}
$alignc${color}${exec audtool current-song-output-length}${color1} / ${color}${exec audtool current-song-length}
$stippled_hr
${color}MODE: ${color1}${font Liberation Sans:style=Bold:size=8}${exec audtool playback-status}${color}${font}
${color}REPEAT: ${color1}${font Liberation Sans:style=Bold:size=8}${exec audtool playlist-repeat-status}${color}${font}
${color}SHUFFLE: ${color1}${font Liberation Sans:style=Bold:size=8}${exec audtool playlist-shuffle-status}${color}${font}
${color}SONGS: ${color1}${font Liberation Sans:style=Bold:size=8}${exec audtool playqueue-length}${color}${font}
```

Pd. Si alguien me puede decir como agregar la barra del reproductor de musica (el estado del tema que se esta reproduciendo) se lo agradeceria mucho ya que yo no pude agregarla..

---

### Post by staar on 2009-07-28
según dice ese tutorial, a esta línea ```
w3m -dump http://weather.yahoo.com/forecast/"$kod".html | grep -A21 "Current" | sed 's/DEG/°/g' > $plik
``` la tenés que modificar, dejándola así ```
w3m -dump http://weather.yahoo.com/forecast/"$kod"**_c**.html | grep -A21 "Current" | sed 's/DEG/°/g' > $plik
``` solo le tenés que agregar ese **_c**, cual es el problema?

saludos

---

### Post by matias_tati on 2009-07-29
Si hasta ahi bien pero me sigue quedando la F mira.

---

### Post by matias_tati on 2009-07-29
Dejo el script pogodynka.sh

# # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # #
#                                                            #
# Pogodynka 0.2.2.1                                                    #
#                                                            #
# azhag (azhag@bsd.miki.eu.org)                                                #
#                                                            # 
# # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # #
#                                                            #
# Skrypt pobiera informacje o stanie pogody ze strony weather.yahoo.com dla danego miasta, nastêpnie formatuje je i    #
# wy¶wietla na ekranie. Skrypt mo¿e byæ wykorzystany np. w conky'm, xosd, *message.                    #
#                                                            #
# # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # #
#                                                            #
# Wymagane aplikacje:                                                    #
# w3m - tekstowa przegl±darka www                                            #
#                                                            #
# # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # #
#                                                            # 
# Przed u¿yciem skryptu nale¿y ustaliæ zmienne "sciezka" oraz "kod".                            #
#                                                            #
# Aby ustaliæ kod swojego miasta wejd¿ na stronê [http://weather.yahoo.com/](http://weather.yahoo.com/) i wyszukaj tam swoje miasto. Kodem jest     #
# koñcówka linka z pogod± naszego miasta.                                        #    
#                                                            #
# Przyk³adowe kody:                                                    #
# Warszawa - PLXX0028                                                    #
# Kraków - PLXX0012                                                    #
# Gdañsk - PLXX0005                                                    #
# Szczecin - PLXX0025                                                    #
#                                                            #
# Informacjê jak± wy¶wietla skrypt mo¿na zmieniæ haszuj±c odpowiednie linijki w sekcji "formatowanie informacji        #
# wyj¶ciowej". Mo¿na równie¿ w ³atwy sposób sformatowaæ w³asny wynik u¿ywaj±c dostepnych zmiennych.            #
#                                                            #
# # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # #

#!/bin/bash

# Katalog, w którym znajduje siê skrypt
sciezka=~/scripts

# Kod miasta
kod=ARBA1611

plik=~/weather
# sprawdzenie czy serwer jest dostêpny
#if [ `ping -c1 216.109.126.70 | grep from | wc -l` -eq 0 ]
 # then
    #echo "Serwis niedostêpny"
  #else
    # pobieranie informacji
     w3m -dump http://weather.yahoo.com/forecast/"$kod"_c.html | grep -A21 "Current" | sed 's/DEG/°/g' > $plik

    # ustalenie warto¶ci zmiennych
    stan=`head -n3 $plik | tail -n1`
    temp=`tail -n1 $plik | awk '{print $1}'`
    tempo=`head -n6 $plik | tail -n1`
    cisn=`head -n8 $plik | tail -n1`
    wiatr=`head -n16 $plik | tail -n1`
    wilg=`head -n10 $plik | tail -n1`
    wsch=`head -n18 $plik | tail -n1`
    zach=`head -n20 $plik | tail -n1`
    if [ `cat "$sciezka"/pogodynka.sh | grep -x "# $stan" | wc -l` -eq 0 ]
      then
        stanpl=$stan
      else
        stanpl=`cat "$sciezka"/pogodynka.sh | grep -xA1 "# $stan" | tail -n1 | awk '{print $2,$3,$4,$5,$6,$7}'`
    fi
    
    # formatowanie informacji wyj¶ciowej
    # dostêpne zmienne:
    # $stan        opis stanu po angielsku
    # $stanpl    opis stanu po polsku
    # $temp        temperatura powietrza
    # $tempo    temperatura odczuwalna
    # $cisn        ci¶nienie atmosferyczne
    # $wiatr    kierunek, si³a wiatru
    # $wilg        wilgotno¶æ powietrza
    # $wsch        godzina wschodu s³oñca
    # $zach        godzina zachodu s³oñca
    
    #echo $stan
    #echo $stanpl
    echo $temp F  /  $tempo F
    #echo Cisnienie $cisn hPa
    #echo $wiatr
    #echo Wilgotno¶æ: $wilg
    #echo Wschód S³oñca: $wsch
    #echo Zachód S³oñca: $zach
    #echo $stanpl, $temp C

#fi

# # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # #
#
# T³umaczenia stanów pogody.
# Je¿eli zauwa¿ysz pogodê, której nie ma jeszcze na liscie daj mi znaæ na maila podanego na górze. Z góry dziêkujê.
#
# Sunny
# S³onecznie
# Clear
# Przejrzy¶cie
# Fair
# Pogodnie
# Sunny/Windy
# S³onecznie/Wiatr
# Clear/Windy
# Przejrzy¶cie/Wiatr
# Fair/Windy
# Przejrzy¶cie/Wiatr
# Windy
# Wiatr
#
# Partly Cloudy
# Czê¶ciowo pochmurnie
# Partly Cloudy and Windy
# Czê¶ciowo pochmurnie/Wiatr
# Partly Sunny
# Czê¶ciowo s³onecznie
# Mostly Clear
# Przew. przejrzy¶cie
# Partly Sunny/Windy
# Czê¶ciowo s³onecznie/Wiatr
# Mostly Clear/Windy
# Przew. przejrzy¶cie/Wiatr
# Mostly Sunny
# Przew. p³onecznie
# Mostly Sunny/Windy
# Przew. s³onecznie/Wiatr
# Scattered Clouds
# Rzadkie ob³oki
#
# Cloudy
# Pochmurnie
# Overcast
# Ca³k. zachmurzenie
# Cloudy/Windy
# Pochmurnie/Wiatr
# Overcast/Windy
# Ca³k. zachmurzenie/Wiatr
# Mostly Cloudy/Windy
# Przew. pochmurnie/Wiatr
# Mostly Cloudy
# Przew. pochmurnie
# Am Clouds / Pm Sun
# Ranek pochmurny/S³oneczne popo³udnie
#
# Light Drizzle
# Lekka m¿awka
# Drizzle
# M¿awka
# Light Rain
# Lekki deszcz
# Rain
# Deszcz
# Heavy Rain
# Ulewa
# Light Rain/Fog
# Lekki deszcz/Mg³a
# Rain/Fog
# Deszcz/Mg³a
# Light Drizzle/Windy
# Lekka m¿awka/Wiatr
# Drizzle/Windy
# M¿awka/Wiatr
# Light Rain/Windy
# Lekki deszcz/Wiatr
# Rain/Windy
# Deszcz/Wiatr
# Rain / Wind
# Deszcz/Wiatr
# Heavy Rain/Windy
# Ulewa/Wiatr
# AM Light Rain
# Ranny lekki deszcz
# PM Light Rain
# Popo³udniowy lekki deszcz
# Pm Light Rain
# Popo³udniowy lekki deszcz
# AM Light Rain/Windy
# Ranny lekki deszcz/Wiatr
# PM Light Rain/Windy
# Popo³udniowy lekki deszcz/Wiatr
#
# Rain Shower
# Przelotny deszcz
# Shower
# Przelotna ulewa
# Showers
# Przelotna ulewa
# Heavy Rain Shower
# Mocna ulewa
# Heavy Rain Shower/Windy
# Mocna ulewa/Wiatr
# Light Rain Shower
# Lekka ulewa
# AM Shower
# Poranna ulewa
# AM Showers
# Poranna ulewa
# Am Showers
# Poranna ulewa
# AM Showers / Wind
# Poranna ulewa/Wiatr
# PM Shower
# Popo³udniowa ulewa
# PM Showers / Wind
# Popo³udniowe ulewy/Wiatr
# Few Showers / Wind
# Przelotne deszcze/Wiatr
# Showers / Wind
# Deszcze/Wiatr
# PM Showers
# Popo³udniowe ulewy
# Pm Showers
# Popo³udniowe ulewy
# Scattered Shower
# Rozleg³a ulewa
# Scattered Showers
# Rozleg³e ulewy
# Scatter Showers
# Rozleg³e ulewy
# Rain Shower/Windy
# Przelotny deszcz/Wiatr
# Shower/Windy
# Przelotna ulewa/Wiatr
# Light Rain Shower/Windy
# Lekka ulewa/Wiatr
# AM Shower/Windy
# Poranna ulewa/Wiatr
# PM Shower/Windy
# Popo³udniowa ulewa/Wiatr
# Scattered Shower/Windy
# Rozleg³a ulewa/Wiatr
# Scatter Showers / Wind
# Rozleg³e ulewy/Wiatr
# Few Showers
# Mo¿liwe ulewy
# Few Showers/Windy
# Mo¿liwe ulewy/Wiatr
# Showers in the Vicinity
# Pobliskie ulewy
#
# Light Snow
# Lekki ¶nieg
# Snow
# &#352;nieg
# Snow / Wind
# &#352;nieg/Wiatr
# Heavy Snow
# Mocny ¶nieg
# Light Snow Pellets
# Lekki grad ¶nie¿ny
# Snow Pellets
# Grad ¶nie¿ny
# Light Ice Pellets
# Lekki grad lodowy
# Ice Pellets
# Grad lodowy
# Wintery Weather
# Zimowa pogoda
# Light Freezing Rain
# Lekki zamarzaj±y deszcz
# Freezing Rain
# Zamarzaj±cy deszcz
# Flurries/Windy
# Zamiecie/Wiatr
# Light Flurries/Windy
# Lekkie zamiecie/Wiatr
# Light Snow/Windy
# Lekki ¶nieg/Wiatr
# Light Snow / Wind
# Lekki ¶nieg/Wiatr
# Snow/Windy
# &#352;nieg/Wiatr
# Heavy Snow/Windy
# Mocny ¶nieg/Wiatr
# Light Snow Pellets/Windy
# Lekki grad ¶nie¿ny/Wiatr
# Snow Pellets/Windy
# Grad ¶nie¿ny/Wiatr
# Light Ice Pellets/Windy
# Lekki grad lodowy/Wiatr
# Ice Pellets/Windy
# Grad lodowy/Wiatr
# Light Freezing Rain/Windy
# Lekki zamarzaj±cy deszcz/Wiatr
# Freezing Rain/Windy
# Zamarzaj±cy deszcz/Wiatr
# Wintery Mix
# Miks zimowy
# Light Snow Grains
# Lekkie granulki ¶niegu
# Snow Grains
# Granulki ¶niegu
# Rain/Snow
# &#352;nieg z deszczem
# Rain / Snow Showers
# Deszcz ze ¶niegiem
# Rain / Snow
# Deszcz ze ¶niegiem
# Rain / Thunder
# Deszcz / Burza
# Rain/Show/Windy
# &#352;nieg z deszczem/Wiatr
# Rain / Snow / Wind
# &#352;nieg z deszczem/Wiatr
# Light Rain/Freezing Rain
# Lekki deszcz/Zamarzaj±cy deszcz
# Rain/Freezing Rain
# Deszcz/Zamarzaj±cy deszcz
# Light Rain/Freezing Rain/Windy
# Lekki deszcz/Zamarzaj±cy Deszcz/Wiatr
# Rain/Freezing Rain/Windy
# Deszcz/Zamarzaj±cy deszcz/Wiatr
# AM Snow
# Poranny ¶nieg
# PM Snow
# Popo³udniowy ¶nieg
# AM Light Snow
# Poranny lekki ¶nieg
# PM Light Snow
# Popo³udniowy lekki ¶nieg
# Ice Crystals
# Kryszta³ki lodu
# Ice Crystals/Windy
# Kryszta³ki lodu/Wiatr
# 
# Snow Showers
# Burze ¶nie¿ne
# Snow Shower
# Burza ¶nie¿na
# Heavy Snow Shower
# Mocna burza ¶nie¿na
# Heavy Snow Shower/Windy
# Mocna burza ¶nie¿na/Wiatr
# PM Snow Showers
# Popo³udniowe burze ¶nie¿ne
# AM Snow Showers
# Poranne burze ¶nie¿ne
# Rain/Snow Showers
# Deszcz/Burze ¶nie¿ne
# Snow Showers/Windy
# Burze ¶nie¿ne/Wiatr
# PM Snow Showers/Windy
# Popo³udniowe burze ¶nie¿ne/Wiatr
# AM Snow Showers/Windy
# Poranne burze ¶nie¿ne/Wiatr
# Rain/Snow Showers/Windy
# Deszcz/Burze ¶nie¿ne/Wiatr
# Light Snow Showers
# Lekkie burze ¶nie¿ne
# Light Snow Shower
# Lekka burza ¶nie¿na
# Light Snow Showers/Windy
# Lekkie burze ¶nie¿ne/Wiatr
# Flurries
# Zamiecie
# Light Flurries
# Lekkie zamiecie
# Scattered Flurries
# Rozleg³e zamiecie
# Few Flurries
# Mo¿liwe zamiecie
# Few Flurries/Windy
# Mo¿liwe zamiecie/Wiatr
# Scattered Snow Showers
# Rozleg³e burze ¶nie¿ne
# Scattered Snow Showers/Windy
# Rozleg³e burze ¶nie¿ne/Wiatr
# Few Snow Showers
# Mo¿liwe burze ¶nie¿ne
# Few Snow Showers/Windy
# Mo¿liwe burze ¶nie¿ne/Wiatr
# Freezing Drizzle
# Marzn±ca m¿awka
# Light Freezing Drizzle
# Lekka marzn±ca m¿awka
# Freezing Drizzle/Windy
# Marzn±ca m¿awka/Wiatr
# Light Freezing Drizzle/Windy
# Lekka marzn±ca m¿awka/Wiatr
# Drifting Snow
# Zawieja ¶nie¿na
# 
# Thunderstorms
# Burze
# T-storms
# Burze
# T-Storms
# Burze
# T-Storm
# Burza
# Scattered Thunderstorms
# Rozleg³e burze
# Scattered T-Storms
# Rozleg³e burze
# Thunderstorms/Windy
# Burze/Wiatr
# Scattered Thunderstorms/Windy
# Rozleg³e burze/Wiatr
# Rain/Thunder
# Deszcz/Grzmoty
# Light Thunderstorms/Rain
# Lekkie burze/Deszcz
# Thunderstorms/Rain
# Burze/Deszcz
# Light Rain with Thunder
# Lekki deszcz z grzmotami
# Rain with Thunder
# Deszcz z grzmotami
# Thunder in the Vicinity
# Pobliskie burze
# 
# Fog
# Mg³a
# Haze
# Lekka mg³a
# Mist
# Lekkie zamglenie
# Fog/Windy
# Mg³a/Wiatr
# Haze/Windy
# Lekka Mg³a/Wiatr
# Mist/Windy
# Lekkie zamglenie/Wiatr
# Partial Fog
# Czê¶ciowa mg³a
# Smoke
# Gêsta mg³a
# Foggy
# Mglisto
# AM Fog/PM Sun
# Ranna mg³a/Popo³udniowe s³oñce
# Shallow Fog
# P³ytka mg³a
# 
# Blowing Dust
# Zawieja py³owa
# Blowing Sand
# Zawieja piaskowa
# Duststorm
# Burza piaskowa
# Wind
# Wiatr
# Widespread Dust/Windy
# Rozleg³e zamiecie/Wiatr
# Widespread Dust
# Rozleg³e zamiecie
# Low Drifting Sand
# Zawieja piaskowa
# 
# Data Not Available
# Dane niedostêpne
# N/A
# N/D
# N/a
# N/d

---

### Post by Mauro22 on 2009-07-29
Ahi lo tenes:

#echo $stan
#echo $stanpl
echo $temp F / $tempo F
#echo Cisnienie $cisn hPa
#echo $wiatr


creo que es eso...

---

### Post by sitodonosti on 2009-07-29
alguien sabe como poner el tiempo en conky, especialmente me gusta el de bruce, la segunda foto. he intentado hacerlo y no funciona. me podrías ayudar?

gracias un saludo desde donosti

---

### Post by matias_tati on 2009-07-29
Golazo Mauro22 la otras dudas las voy a ir subiendo despues ya estoy re pesado. gracias!!!!

---

### Post by staar on 2009-07-29
un script en polaco :-P :-D

sitodonosti, la segunda captura de bruce (por lo menos del último post que hizo, no se a cual te referis) no es conky, es gtk-desktop-info...

saludos

---

### Post by sitodonosti on 2009-07-30
si si ya se que es gtk-desktop- info pero esque nose como ponerlo en realidad, sino me equivoco este programa lo que te hace es un script,no?o eso entiendo y claro he conseguido el script pero no consigo que vaya la verda....

---

### Post by Bruce M. on 2009-07-30
> **matias_tati said:**
> Quedo hermoso descarte el otro e instale este siguiendo este [tutorial]("http://www.quicktweaks.com/2008/09/27/gmail-weather-beauty-right-on-your-ubuntu-desktop/") para el que le sirva sobretodo a los mas novatos. Solo me faltaria cambiar los Farenheit por grados. Saludos.

Hola matias,

Cambiar los Farenheit por grados:

Busque esta línea:
```
w3m -dump http://weather.yahoo.com/forecast/"$kod".html | grep -A21 "Current" | sed 's/DEG/°/g' > $plik
```
Substitúyalo por:
```
w3m -dump http://weather.yahoo.com/forecast/"$kod"_c.html | grep -A21 &#8220;Current&#8221; | sed &#8217;s/DEG/°/g&#8217; > $plik
```

La diferencia es: (F) "$kod".html = (C) "$kod"**_c.html**

Que tengas un buen día.
Bruce

---

### Post by Bruce M. on 2009-07-30
> **sitodonosti said:**
> alguien sabe como poner el tiempo en conky, especialmente me gusta el de bruce, la segunda foto. he intentado hacerlo y no funciona. me podrías ayudar?

gracias un saludo desde donosti

Te lo doy: **Buenos Aires, Argentina - gtk-desktop-app**

**ss-gtk.sh** - make executable y launcher (panel o desktop) y/o "autostart"

**Ejemplo:**
```
Name: gtk-weather
Description: 
Icon: sun (attached)
Command: /home/user_name/gtk-desk/ss-gtk.sh
```


**ss-gtk.sh**
```
#!/bin/sh
# click to start, click to stop

# get the pid of the forecast gtk process, if we can...
pid=`ps -C python -f | grep "plugin=forecast" | cut -c10-15`

# do we have a valid pid value for killing :)
if test -z "$pid"
then
	# no pid so starting...
	echo 'starting process'
	# start gtk-desktop weather - Monitor 17" "Res: 1280 x 1024 - Bottom left - See: x= and y=
	gtk-desktop-info --allworkspaces --backgroundblend=40 --backgroundcolour=0,0,0 --backgroundcorner=30 --logfile=/tmp/gtk-desktop-info.log --interval=600 --width=725 --height=245 --x=10 --y=755 --windowmanager=xfce4 --css=/home/bruloo/gtk-desk/my_forecast.css --template=/home/bruloo/gtk-desk/my.template --noheader --plugin=forecast &
else
	# valid pid so killing...
	echo 'killing process'
	kill $pid	
fi
```

**Screen:** 1280x 1024 entonces: x=10 --y=755 = bottom_left
**Estoy usando Xfce entonces:** --windowmanager=xfce4
>   --windowmanager=NAME
  default:[gnome]

 Tell the app which windows manager is in use, options are gnome, kde3, kde4, xfce4

**my.template**
```
<html>
<head></head>
<body>
<!-- --datatype : The data type options are:
	 DW (Day of Week),
	 WF (Weather Font output),
Today:	 LT - Feels Like Temp  - WITHOUT: "--startday=0" [--datatype LT]
Today:	 HT - Current Temp - WITHOUT: "--startday=0" [--datatype HT]
Today:	 LT - Forcasted Low Temp: - WITH: "--startday=0" [-- startday=0 --datatype LT]
Today:	 HT - Forecasted High Temp: - WITH: "--startday=0" [-- startday=0 --datatype HT]
Fore:	 LT - Low Temp - use with --startday=1 to 4 [-- startday=1 --datatype LT]
Fore:	 HT - High Temp - use with --startday=1 to 4 [-- startday=1 --datatype HT]
	 CC (Current Conditions),
	 CC (Conditions Text),
	 PC (Precipitation Chance),
	 HM (Humidity),
	 VI (Visibility),
	 WD (Wind Direction),
	 WA (Wind Angle - in degrees),
	 WS (Wind Speed),
	 WG (Wind Gusts),
	 BF (Bearing Font),
	 BS (Bearing font with Speed),
	 CN (City Name),
	 CO (Country),
	 OB (Observatory),
	 SR (SunRise),
	 SS (SunSet),
	 DL (Hours of DayLight),
	 MP (Moon Phase),
	 MF (Moon Font),
	 BR (Barometer Reading),
	 BD (Barometer Description),
	 UI (UV Index),
	 UT (UV Text),
	 DP (Dew Point),
	 LU (Last Update at weather.com),
	 LF (Last Fetch from weather.com),
	 WM (weather map) -->

<table cellpadding="0" cellspacing="5" border="0">
<tr>
	<td rowspan="3" align="center" valign="top"><img src="[--datatype=WF]" width="100"/></td>
	<td rowspan="3" align="center" class="hoy-cyan">[--datatype=HT --hideunits]</td>
	<td rowspan="3" align="right" valign="center">
<!-- High, Low, ST -->
		<table cellpadding="0" cellspacing="0" border="0">
		<tr>
			<td align="right" class="ml-red">Máx:</td>
		</tr>
		<tr>
			<td align="right" class="ml-cyan">Mín:</td>
		</tr>
		<tr>
			<td align="right" class="ml-green"><br>ST:</td>
		</tr>
		<tr>
			<td align="right" class="ml-wkday">PC:</td>
		</tr>
		</table>
<!-- END: High, Low, ST -->
	</td>
	<td rowspan="3" align="right" valign="middle">
<!-- high, low, st values -->
		<table cellpadding="0" cellspacing="0" border="0">
		<tr>
			<td class="ml-red">[--datatype=HT --startday=0 --hideunits]</td>
		</tr>
		<tr>
			<td class="ml-cyan">[--datatype=LT --startday=0 --hideunits]</td>
		</tr>
		<tr>
			<td class="ml-green"><br>[--datatype=LT --hideunits]</td>
		</tr>
		<tr>
			<td class="ml-wkday">[--datatype=PC --startday=0]</td>
		</tr>
		</table>
<!-- END: high, low, st values -->
	</td>
	<td colspan="3" rowspan="4" align="right" valign="top">
<!-- Todays info text -->	
		<table cellpadding="0" cellspacing="0" border="0" valign="top">
		<tr>
			<td align="right" class="ml-yellow">UV:</td>
		</tr>
		<tr>
			<td align="right" class="ml-yellow"><br>Visibilidad:</td>
		</tr>
		<tr>
			<td align="right" class="ml-yellow"><br>Humedad</td>
		</tr>
		<tr>
			<td align="right" class="ml-yellow"><br>Punto&nbsp;del&nbsp;Rocío:</td>
		</tr>
		<tr>
			<td align="right" class="ml-yellow"><br>Presíon:</td>
		</tr>
		</table>
<!-- END: Todays info text -->	
	</td>
	<td rowspan="4" valign="top">
<!-- Todays info data -->	
		<table cellpadding="0" cellspacing="0" border="0" valign="top" width="80">
		<tr>
			<td class="ml-cyan">[--datatype=UI]&nbsp;~&nbsp;[--datatype=UT]</td>
		</tr>
		<tr>
			<td class="ml-cyan"><br>[--datatype=VI]</td>
		</tr>
		<tr>
			<td class="ml-cyan"><br>[--datatype=HM]</td>
		</tr>
		<tr>
			<td class="ml-cyan"><br>[--datatype=DP]</td>
		</tr>
		<tr>
			<td class="ml-cyan"><br>[--datatype=BR]<br>[--datatype=BD]</td>
		</tr>
		</table>
<!-- END: Todays info data -->
	</td>
	<td colspan="4" align="center" valign="bottom" class="ml-yellow">los próximos días</td>
</tr>
<tr><!-- 4 weekday names -->
	<td align="center" class="ml-wkday">[--datatype=DW --startday=1]</td>
	<td align="center" class="ml-wkday">[--datatype=DW --startday=2]</td>
	<td align="center" class="ml-wkday">[--datatype=DW --startday=3]</td>
	<td align="center" class="ml-wkday">[--datatype=DW --startday=4]</td>
</tr>
<tr>
	<td><!-- Day 1 info -->
		<table cellpadding="0" cellspacing="0" border="0" width="70">
		<tr>
			<td colspan="3" align="center"><img src="[--datatype=WF --startday=1]" width="40"/></td>
		</tr>
		<tr>
			<td align="center" class="ml-red">[--datatype=HT --startday=1 --hideunits]</td>
			<td align="center" class="ml-green">~</td>
			<td align="center" class="ml-cyan">[--datatype=LT --startday=1 --hideunits]</td>
		</tr>
		<tr>
			<td colspan="3" align="center" class="ml-wkday">[--datatype=PC --startday=1]</td>
		</tr>
		</table>
	</td>
	<td><!-- Day 2 info -->
		<table cellpadding="0" cellspacing="0" border="0" width="70">
		<tr>
			<td colspan="3" align="center"><img src="[--datatype=WF --startday=2]" width="40"/></td>
		</tr>
		<tr>
			<td align="center" class="ml-red">[--datatype=HT --startday=2 --hideunits]</td>
			<td align="center" class="ml-green">~</td>
			<td align="center" class="ml-cyan">[--datatype=LT --startday=2 --hideunits]</td>
		</tr>
		<tr>
			<td colspan="3" align="center" class="ml-wkday">[--datatype=PC --startday=2]</td>
		</tr>
		</table>
	</td>
	<td><!-- Day 3 info -->
		<table cellpadding="0" cellspacing="0" border="0" width="70">
		<tr>
			<td colspan="3" align="center"><img src="[--datatype=WF --startday=3]" width="40"/></td>
		</tr>
		<tr>
			<td align="center" class="ml-red">[--datatype=HT --startday=3 --hideunits]</td>
			<td align="center" class="ml-green">~</td>
			<td align="center" class="ml-cyan">[--datatype=LT --startday=3 --hideunits]</td>
		</tr>
		<tr>
			<td colspan="3" align="center" class="ml-wkday">[--datatype=PC --startday=3]</td>
		</tr>
		</table>
	</td>
	<td><!-- Day 4 info -->
		<table cellpadding="0" cellspacing="0" border="0" width="70">
		<tr>
			<td colspan="3" align="center"><img src="[--datatype=WF --startday=4]" width="40"/></td>
		</tr>
		<tr>
			<td align="center" class="ml-red">[--datatype=HT --startday=4 --hideunits]</td>
			<td align="center" class="ml-green">~</td>
			<td align="center" class="ml-cyan">[--datatype=LT --startday=4 --hideunits]</td>
		</tr>
		<tr>
			<td colspan="3" align="center" class="ml-wkday">[--datatype=PC --startday=4]</td>
		</tr>
		</table>
	</td>
</tr>
<tr>
	<td colspan="4" class="hugelight">&nbsp;&nbsp;[--datatype=CC]</td>
	<td colspan="4" class="hugelight">&nbsp;</td>
</tr>
<tr>
	<td rowspan="2" align="center" class="ml-yellow"><img src="[--datatype=BS]" width="50"/><br><br>[--datatype=WD] [--datatype=WS]</td>
	<td colspan="3" rowspan="2" align="center" class="ml-yellow"><img src="[--datatype=MF]" width="50"/><br><br>[--datatype=MP]</td>
	<td colspan="3">
<!-- sunrise - sunset & daylight text -->
		<table cellpadding="0" cellspacing="0" border="0">
		<tr>
			<td align="right" class="ml-sr">Salida&nbsp;del&nbsp;Sol:</td>
		</tr>
		<tr>
			<td align="right" class="md-ss">Puesto del Sol:</td>
		</tr>
		<tr>
			<td align="right" class="ml-daylight"><br>Horas de Luz:</td>
		</tr>
		</table>
<!-- END: sunrise - sunset & daylight text -->
	</td>
	<td align="center">
<!-- Today: sunrise - sunset & daylight values -->
		<table cellpadding="0" cellspacing="0" border="0">
		<tr align="center">
			<td align="right" class="ml-sr">[--datatype=SR]</td>
		</tr>
		<tr>
			<td align="right" class="md-ss">[--datatype=SS]</td>
		</tr>
		<tr>
			<td align="right" class="ml-daylight"><br>[--datatype=DL]</td>
		</tr>
		</table>
<!-- END: Today: sunrise - sunset & daylight values -->
	</td>
	<td align="center">
<!-- Day 1: sunrise - sunset & daylight values -->
		<table cellpadding="0" cellspacing="0" border="0">
		<tr align="center">
			<td align="right" class="ml-sr">[--datatype=SR --startday=1]</td>
		</tr>
		<tr>
			<td align="right" class="md-ss">[--datatype=SS --startday=1]</td>
		</tr>
		<tr>
			<td align="right" class="ml-daylight"><br>[--datatype=DL --startday=1]</td>
		</tr>
		</table>
<!-- END: Day 1: sunrise - sunset & daylight values -->
	</td>
	<td align="center">
<!-- Day 2: sunrise - sunset & daylight values -->
		<table cellpadding="0" cellspacing="0" border="0">
		<tr align="center">
			<td align="right" class="ml-sr">[--datatype=SR --startday=2]</td>
		</tr>
		<tr>
			<td align="right" class="md-ss">[--datatype=SS --startday=2]</td>
		</tr>
		<tr>
			<td align="right" class="ml-daylight"><br>[--datatype=DL --startday=2]</td>
		</tr>
		</table>
<!-- END: Day 2: sunrise - sunset & daylight values -->
	</td>
	<td align="center">
<!-- Day 3: sunrise - sunset & daylight values -->
		<table cellpadding="0" cellspacing="0" border="0">
		<tr align="center">
			<td align="right" class="ml-sr">[--datatype=SR --startday=3]</td>
		</tr>
		<tr>
			<td align="right" class="md-ss">[--datatype=SS --startday=3]</td>
		</tr>
		<tr>
			<td align="right" class="ml-daylight"><br>[--datatype=DL --startday=3]</td>
		</tr>
		</table>
<!-- END: Day 3: sunrise - sunset & daylight values -->
	</td>
	<td align="center">
<!-- Day 4: sunrise - sunset & daylight values -->
		<table cellpadding="0" cellspacing="0" border="0">
		<tr align="center">
			<td align="right" class="ml-sr">[--datatype=SR --startday=4]</td>
		</tr>
		<tr>
			<td align="right" class="md-ss">[--datatype=SS --startday=4]</td>
		</tr>
		<tr>
			<td align="right" class="ml-daylight"><br>[--datatype=DL --startday=4]</td>
		</tr>
		</table>
<!-- END: Day 4: sunrise - sunset & daylight values -->
	</td>
</tr>
<tr>
	<td colspan="5" align="right" valign="bottom" class="smalldark">Last Update: [datatype=LU]</td>
	<td colspan="3" align="right" valign="bottom" class="smalldark">Last Fetch: [datatype=LF]</td>
</tr>
</table>
</body>
</html>

```

**my_forecast.css**
```
body{
  font-family: arial, verdana, "sans-serif";
}

.hoy-cyan {
  color: #A7D4FF;
  font-size: 40px;
  font-weight: bold;
  font-style: italic;
}

.ml-red {
  color: #FF7B7B;
  font-size: 12px;
  font-weight: bold;
}

.ml-cyan {
  color: #A7D4FF;
  font-size: 12px;
  font-weight: bold;
}

.ml-green {
  color: #00FF00;
  font-size: 12px;
  font-weight: bold;
}

.ml-yellow {
  color: #FFFF00;
  font-size: 12px;
  font-weight: bold;
}

.ml-wkday {
  color: #8EEA8E;
  font-size: 12px;
  font-weight: bold;
}

.ml-sr {
  color: #A7D4FF;
  font-size: 12px;
  font-weight: bold;
}

.md-ss {
  color: #DE5F00;
  font-size: 12px;
  font-weight: bold;
}

.ml-daylight {
  color: #FFFFFF;
  font-size: 12px;
  font-weight: bold;
}

.smalllight {
  color: #FFB60D;
  font-size: 10px;
  font-weight: bold;
}

.smalldark {
  color: #EB6500;
  font-size: 10px;
  font-weight: bold;
}

.mediumlight {
  color: #FFB60D;
  font-size: 12px;
  font-weight: bold;
}

.mediumdark {
  color: #EB6500;
  font-size: 12px;
  font-weight: bold;
}

.hoy-temp {
  color: #FFB60D;
  font-size: 22px;
  font-weight: bold;
}

.largelight {
  color: #FFB60D;
  font-size: 16px;
  font-weight: bold;
}

.largedark {
  color: #EB6500;
  font-size: 16px;
  font-weight: bold;
}

.hugelight {
  color: #FFB60D;
  font-size: 22px;
  font-weight: bold;
}

.hugedark {
  color: #EB6500;
  font-size: 22px;
  font-weight: bold;
}

.smalllightitalic {
  color: #FFB60D;
  font-size: 10px;
  font-weight: bold;
  font-style: italic;
}

.smalldarkitalic {
  color: #EB6500;
  font-size: 10px;
  font-weight: bold;
  font-style: italic;
}

.mediumlightitalic {
  color: #FFB60D;
  font-size: 12px;
  font-weight: bold;
  font-style: italic;
}

.mediumdarkitalic {
  color: #EB6500;
  font-size: 12px;
  font-weight: bold;
  font-style: italic;
}

.largelightitalic {
  color: #FFB60D;
  font-size: 16px;
  font-weight: bold;
  font-style: italic;
}

.largedarkitalic {
  color: #EB6500;
  font-size: 16px;
  font-weight: bold;
  font-style: italic;
}

.hugelightitalic {
  color: #A7D4FF;
  font-size: 22px;
  font-weight: bold;
  font-style: italic;
}

.hugedarkitalic {
  color: #EB6500;
  font-size: 22px;
  font-weight: bold;
  font-style: italic;
}

.contenttop{
  color: #EB6500;
  font-size: 12px;
  font-weight: bold;  
  float: left;
  margin: 2px 0 2px 0;
  padding-bottom: 2px;
  width: 100%;
}

.contentleft{
  color: #EB6500;
  font-size: 12px;
  font-weight: bold;  
  float: left;
  margin: 2px 0 2px 0;
  width: 65%;
}

.contentright{
  color: #EB6500;
  font-size: 12px;
  font-weight: bold;  
  float: right;
  margin: 2px 0 2px 0;
  width: 35%;
}

.contentbottom{
  color: #EB6500;
  font-size: 12px;
  font-weight: bold;
  float: right;
  margin: 2px 0 2px 0;
  width: 100%;
}

.current{
  float: left;
  width: 33%;
  margin: 0 0 0 0;
  text-align: center;
}

.current img{
  margin: 10px 0 5px 2px;
}

.moon{
  float: left;
  width: 33%;
  margin: 0 0 0 0;
  text-align: center;
}

.moon img{
  margin: 10px 0 5px 2px;
}

.wind{
  float: left;
  width: 33%;
  margin: 0 0 0 0;
  text-align: center;
}

.wind img{
  margin: 10px 0 5px 2px;
}

.forecast{
  border-top: 2px solid #FFB60D;
  clear: both;
  width: 100%
  margin: 5px 0 2px 0;
  padding: 5px 0 2px 0;
  text-align: center;
}

.day{
  width: 24%;
  float: left;
  text-align: center;
  color: #EB6500;
}

.day img{
  margin: 10px 0 5px 2px;
}

p {
  color: #EB6500;
  font-size: 12px;
  font-weight: bold;  
}
```

Tengo los tres archivos en: ~/gtk-desk

-------------------------
**y conkyForecast:**
-------------------------

```
background no
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_colour black
double_buffer yes
use_spacer left
override_utf8_locale yes
use_xft	yes
font DejaVu Sans Mono:bold:size=9
xftfont DejaVu Sans Mono:bold:size=9
xftalpha 0.5
update_interval 5.0
uppercase no  # set to yes if you want all text to be in uppercase
stippled_borders 0 #3
border_margin 0 #9
border_width 0 #10
default_outline_color black
default_shade_color black
draw_borders no
draw_outline yes  # amplifies text if yes
draw_shades yes  # shadecolor black

default_color DCDCDC #Gainsboro
color0 7FFFD4 #Aquamarine
color1 CD5C5C #IndianRed #00CED1 DarkTurquoise #FFA07A LightSalmon #00FFFF Cyan
color2 FF8C00 #Darkorange #D2691E #Chocolate
color3 7FFF00 #Chartreuse
color4 778899 #LightSlateGrey
color5 FFDEAD #NavajoWhite
color6 00BFFF #DeepSkyBlue
#	colours below used by colorize script
color7 48D1CC #MediumTurquoise
color8 FFFF00 #Yellow
color9 FF0000 #Red

alignment bl  # Aligned position on screen: tl, tr, tm, bl, br, bm, ml, mr
gap_x 5
gap_y -212 # because of the VOFFSET, the negative "gap_y" value brings conky back to the bottom of the screen.
text_buffer_size 2304 # 256 is the minimum
no_buffers yes  # Subtract file system buffers from used memory?
short_units yes
pad_percents 2

# Bs As, Argentina = ARDF0127

TEXT
${execpi 7200 ~/Conky/scripts/invisible_weather.sh}
${voffset -35}${execpi 1800 conkyForecast --location=ARDF0127 --template=/home/bruloo/Conky/scripts/myweather.template}
```

y **myweather.template**

```
${goto 10}${color8}${font ConkyWeather:size=55}[--datatype=WF]${font}${color}
${voffset -70}${goto 90}${color2}${font Zekton:size=20}[--datatype=DW --shortweekday --startday=0]:${color6} [--datatype=HT]
${goto 90}${voffset -10}${font Zekton:bold:size=9}${color2}Sensación térmica: ${color6}[--datatype=LT]${font}
${goto 90}${color2}Mín: ${color6}[--startday=0 --datatype=LT --night] ${color2}Máx: ${color9}[--startday=0 --datatype=HT --night]
${goto 10}${voffset 10}${font Zekton:bold:size=11} ${color7}[--datatype=CC]${color}${font}
${goto 300}${voffset -110}${font ConkyWindN:size=40}${color8}[--datatype=BS]${font}
${goto 380}${voffset -45}${color7}Viento: ${color8}[--datatype=WS] ${color7}(${color8}[--datatype=WA]°${color7}) ${color8}[--datatype=WD]
${voffset 0}${goto 380}${color7}Visibilidad:${color8} [--datatype=VI]
${voffset 0}${goto 380}${color7}P. de R.: ${color8}[--datatype=DP]${color}
${goto 300}${voffset 10}${color7}Presión: ${color8}[--datatype=BR] - [--datatype=BD]${color}
${goto 300}${color7}Humedad: ${color8}[--datatype=HM]  ${color7}UV: ${color8}[--datatype=UI] - ${color8}[--datatype=UT]
${goto 300}${cpubar cpu3 1,300}
${goto 15}${voffset 20}${color8}${font SunNMoon:size=50}n${font}${goto 70}${voffset -38}${font Arrows:size 20}${color3}b${color8}${font}[--datatype=SR]
${goto 75}${color0}Luz: [--datatype=DL]
${goto 70}${font Arrows:size 20}${color1}h${color8}${font}[--datatype=SS]${color}
${goto 170}${voffset -50}${font moon phases:size=40}[--datatype=MF]${font}
${voffset -70}${goto 300}${color2}[--datatype=DW --shortweekday --startday=1]:${color1}[--datatype=HT --hideunits --hidedegreesymbol --startday=1]${color}/${color7}[--datatype=LT --hideunits --hidedegreesymbol --startday=1]${goto 380}${color2}[--datatype=DW --shortweekday --startday=2]:${color1}[--datatype=HT --hideunits --hidedegreesymbol --startday=2]${color}/${color7}[--datatype=LT --hideunits --hidedegreesymbol --startday=2]${goto 460}${color2}[--datatype=DW --shortweekday --startday=3]:${color1}[--datatype=HT --hideunits --hidedegreesymbol --startday=3]${color}/${color7}[--datatype=LT --hideunits --hidedegreesymbol --startday=3]${goto 540}${color2}[--datatype=DW --shortweekday --startday=4]:${color1}[--datatype=HT --hideunits --hidedegreesymbol --startday=4]${color}/${color7}[--datatype=LT --hideunits --hidedegreesymbol --startday=4]
${goto 300}${color8}${font ConkyWeather:size=30}[--datatype=WF --startday=1]${goto 380}[--datatype=WF --startday=2]${goto 460}[--datatype=WF --startday=3]${goto 540}[--datatype=WF --startday=4]${font}${color}
${goto 300}${color7}Sol:${color3}[--datatype=SR --startday=1]${goto 380}${color7}Sol:${color3}[--datatype=SR --startday=2]${goto 460}${color7}Sol:${color3}[--datatype=SR --startday=3]${goto 540}${color7}Sol:${color3}[--datatype=SR --startday=4]
${goto 300}${color7}   :${color1}[--datatype=SS --startday=1]${goto 380}${color7}   :${color1}[--datatype=SS --startday=2]${goto 460}${color7}   :${color1}[--datatype=SS --startday=3]${goto 540}${color7}   :${color1}[--datatype=SS --startday=4]${color}
${goto 15}${font DejaVu Sans Mono:bold:size=7}W:[--datatype=LU] -=- C:[--datatype=LF]${font}${voffset -2}${goto 300}${color7}Luz:${color8}[--datatype=DL --startday=1]${goto 380}${color7}Luz:${color8}[--datatype=DL --startday=2]${goto 460}${color7}Luz:${color8}[--datatype=DL --startday=3]${goto 540}${color7}Luz:${color8}[--datatype=DL --startday=4]${color}
```

Hay más preguntas?

Que tengas un buen día.
Bruce

---

### Post by matias_tati on 2009-07-30
> **Bruce M. said:**
> Hola matias,

Cambiar los Farenheit por grados:

Busque esta línea:
```
w3m -dump http://weather.yahoo.com/forecast/"$kod".html | grep -A21 "Current" | sed 's/DEG/°/g' > $plik
```Substitúyalo por:
```
w3m -dump http://weather.yahoo.com/forecast/"$kod"_c.html | grep -A21 “Current” | sed ’s/DEG/°/g’ > $plik
```La diferencia es: (F) "$kod".html = (C) "$kod"**_c.html**

Que tengas un buen día.
Bruce

Si gracias ya habia logrado solucionarlo. Siempre de noche se ve el sol?

---

### Post by sitodonosti on 2009-07-30
gracias Bruce, me va perfecto ahora solo hace falta algunos retoques,yo nose programar ni nada de scripts entonces me aparece con la temperatura y tal de argentina, los acentos me salen con letras raras y quiero darle mas altura
como podría hacerlo? dejo la imagen nose si me explicado bien

gracias de nuevo

---

### Post by Bruce M. on 2009-08-02
> **sitodonosti said:**
> gracias Bruce, me va perfecto ahora solo hace falta algunos retoques,yo nose programar ni nada de scripts entonces me aparece con la temperatura y tal de argentina, los acentos me salen con letras raras y quiero darle mas altura
como podría hacerlo? dejo la imagen nose si me explicado bien

gracias de nuevo

Metta questa linea prima di TEXT
Put this line before TEXT

```
override_utf8_locale yes
TEXT
```

Abbia un giorno piacevole.
Bruce

---

### Post by sitodonosti on 2009-08-02
nose si me has entendido lo que quiero decir, me refería al conky del tiempo, no en el .conkyrc. Lo que quiero hacer es poner el tiempo de mi ciudad y me aparece el de argentina, además de que las letras con tilde algunas se ven mal. Mi pregunta era si me podrías decir como poner el tiempo de mi ciudad en vez de la de Argentina

---

### Post by matias_tati on 2009-08-02
Hola una duda cuando ejecuto el conky en el terminal me sale lo que dice en la imagen como puedo hacer para cambiarla por mi dir. IP pq en el conky no me muestra nada en up y en down.

---

### Post by Bruce M. on 2009-08-02
> **sitodonosti said:**
> nose si me has entendido lo que quiero decir, me refería al conky del tiempo, no en el .conkyrc. Lo que quiero hacer es poner el tiempo de mi ciudad y me aparece el de argentina, además de que las letras con tilde algunas se ven mal. Mi pregunta era si me podrías decir como poner el tiempo de mi ciudad en vez de la de Argentina

**[COLOR="Red"]Oops![/COLOR]**

[http://xoap.weather.com/search/search?where=Buenos Aires](http://xoap.weather.com/search/search?where=Buenos Aires)

<search ver="3.0">
<loc id="**ARBA0009**" type="1">Buenos Aires, Argentina</loc>
<loc id="BRXX1283" type="1">Buenos Aires, Brazil</loc>
<loc id="**ARDF0127**" type="1">Aeroparque Buenos Aires, Argentina</loc>
<loc id="MXJO0669" type="1">Concepcion De Buenos Aires, Mexico</loc>
<loc id="MXPA1785" type="1">San Nicolas De Buenos Aires, Mexico</loc>
<loc id="ARBA0005" type="1">Balcarce, Argentina</loc>
<loc id="ARBA0008" type="1">Bragado, Argentina</loc>
<loc id="ARBA0010" type="1">Campana, Argentina</loc>
<loc id="ARBA0016" type="1">Chascomus, Argentina</loc>
<loc id="ARBA0019" type="1">Chivilcoy, Argentina</loc>
</search>

[http://xoap.weather.com/search/search?where=Mendoza](http://xoap.weather.com/search/search?where=Mendoza)

<search ver="3.0">
<loc id="**ARMA0056**" type="1">Mendoza, Argentina</loc>
<loc id="MXVZ2131" type="1">Camerino Z Mendoza, Mexico</loc>
<loc id="ARMA0037" type="1">Guaymallen, Argentina</loc>
<loc id="ARMA0052" type="1">Malargue, Argentina</loc>
<loc id="ARMA0106" type="1">Uspallata, Argentina</loc>
<loc id="ARMA1405" type="1">Canalejas, Argentina</loc>
<loc id="ARMA5509" type="1">Perdriel, Argentina</loc>
<loc id="ARMA5515" type="1">Maipu, Argentina</loc>
<loc id="ARMA5529" type="1">Pedregal, Argentina</loc>
<loc id="ARMA5560" type="1">Tunuyan, Argentina</loc>
</search>

Have a nice day.
Bruce

---

### Post by staar on 2009-08-02
> **matias_tati said:**
> Hola una duda cuando ejecuto el conky en el terminal me sale lo que dice en la imagen como puedo hacer para cambiarla por mi dir. IP pq en el conky no me muestra nada en up y en down. posteá tu conkyrc y lo vemos...

saludos

---

### Post by matias_tati on 2009-08-03
Aqui esta..

use_xft yes
xftfont verdana:size=8
alignment top_right
xftalpha 0.8
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
stippled_borders 10
border_margin 4
border_width 1
default_shade_color grey
default_outline_color black
default_color BADCDD
use_spacer none
no_buffers yes
uppercase no
color1 F8DF58


TEXT
 ${color white}${font Radio Space:size=38}${alignc}MATIAS
 ${color white}${font OpenLogos:size=45} u t
${color white}${font weather:size=82}${execi 600 ~/scripts/conditions.sh}${color white}${font}${voffset -25}  ${execi 1200 ~/scripts/pogodynka.sh}

   ${font weather:size=28}x ${font}HDD ${execi 1 ~/scripts/hddmonit.sh}°C 
    
   ${font PizzaDude Bullets:size=16}v${font}   Up: ${upspeed eth1} Kb/s 
   ${font PizzaDude Bullets:size=16}r${font}   Down: ${downspeed eth1} Kb/s 

   ${font PizzaDude Bullets:size=16}M${font}   Upload: ${totalup eth1}
   ${font PizzaDude Bullets:size=16}S${font}   Download: ${totaldown eth1}

   ${color white}${font StyleBats:size=16}A${font}  CPU0: ${cpu cpu0}% ${cpubar cpu0}
   ${font StyleBats:size=16}A${font}  CPU1: ${cpu cpu1}% ${cpubar cpu1}


   ${color white}${font FreeSans:size=16}@${font}${execpi 300 python ~/scripts/gmail_parser.py [email]matiaspedroarroyo@gmail.com[/email] (Mi contraseña) 3}

   ${color white}${font PizzaDude Bullets:size=16}J${font}   $mem / $memmax

   ${font StyleBats:size=18}P${font}  Logeado:  ${uptime_short}


 ${color white}${font Radio Space:size=20}${time %A %d %Y}
    ${color white}${font Radio Space:size=55}${time %H:%M}

---

### Post by staar on 2009-08-03
primero que nada, aclararte que 127.0.0.1 es la ip interna de tu máquina (y de la mía, y de la de la mayoría de la gente) y esos mensajes que salen son del script de gmail, que por lo que veo en la captura, anda bien, no te preocupes...

después, para el tema de que no sale la subida y la bajada de datos, el tema puede pasar porque está mal puesta la interfaz ```

${font PizzaDude Bullets:size=16}v${font} Up: ${upspeed **eth1**} Kb/s 
${font PizzaDude Bullets:size=16}r${font} Down: ${downspeed **eth1**} Kb/s 

${font PizzaDude Bullets:size=16}M${font} Upload: ${totalup **eth1**}
${font PizzaDude Bullets:size=16}S${font} Download: ${totaldown **eth1**}
``` esos *eth1* son la interfaz que está mostrando, podés usar el comando ifconfig (en una terminal) para saber el nombre de todas las interfaces de red que estás corriendo, fijate cual es la correcta y cambiala (eth son las cableadas, wlan las wifi, ppp las dial-up, etc, todas con un número al lado, empezando desde 0 inclusive)

saludos

---

### Post by sitodonosti on 2009-08-03
> **Bruce M. said:**
> **[COLOR="Red"]Oops![/COLOR]**

[http://xoap.weather.com/search/search?where=Buenos](http://xoap.weather.com/search/search?where=Buenos) Aires

<search ver="3.0">
<loc id="**ARBA0009**" type="1">Buenos Aires, Argentina</loc>
<loc id="BRXX1283" type="1">Buenos Aires, Brazil</loc>
<loc id="**ARDF0127**" type="1">Aeroparque Buenos Aires, Argentina</loc>
<loc id="MXJO0669" type="1">Concepcion De Buenos Aires, Mexico</loc>
<loc id="MXPA1785" type="1">San Nicolas De Buenos Aires, Mexico</loc>
<loc id="ARBA0005" type="1">Balcarce, Argentina</loc>
<loc id="ARBA0008" type="1">Bragado, Argentina</loc>
<loc id="ARBA0010" type="1">Campana, Argentina</loc>
<loc id="ARBA0016" type="1">Chascomus, Argentina</loc>
<loc id="ARBA0019" type="1">Chivilcoy, Argentina</loc>
</search>

[http://xoap.weather.com/search/search?where=Mendoza](http://xoap.weather.com/search/search?where=Mendoza)

<search ver="3.0">
<loc id="**ARMA0056**" type="1">Mendoza, Argentina</loc>
<loc id="MXVZ2131" type="1">Camerino Z Mendoza, Mexico</loc>
<loc id="ARMA0037" type="1">Guaymallen, Argentina</loc>
<loc id="ARMA0052" type="1">Malargue, Argentina</loc>
<loc id="ARMA0106" type="1">Uspallata, Argentina</loc>
<loc id="ARMA1405" type="1">Canalejas, Argentina</loc>
<loc id="ARMA5509" type="1">Perdriel, Argentina</loc>
<loc id="ARMA5515" type="1">Maipu, Argentina</loc>
<loc id="ARMA5529" type="1">Pedregal, Argentina</loc>
<loc id="ARMA5560" type="1">Tunuyan, Argentina</loc>
</search>

Have a nice day.
Bruce
mmmm y esto donde se supone que viene?solo tengo tres archivos el my.template, my_forecast.css y ss-gtk.sh

---

### Post by Bruce M. on 2009-08-03
> **sitodonosti said:**
> mmmm y esto donde se supone que viene?solo tengo tres archivos el my.template, my_forecast.css y ss-gtk.sh

Ahhhhhhhhhhhh - OK - siento tonto

```
/usr/share/gtk-desktop-info/config/plugin_forecast.config
```

copie el "plugin_forecast.config" al mismo lugar como el otros gtk archivos; my.template, my_forecast.css y ss-gtk.sh.

y cambie tres líneas:

```

LOCATION = your_city <<<<----- Uno

# Your registered partner id
XOAP_PARTNER_ID =  your_id <<<<<----- dos

# Your registered licence key  <<<<<----- tres
XOAP_LICENCE_KEY = your_key
```

listo!

Bruce

---

### Post by sitodonosti on 2009-08-03
> **Bruce M. said:**
> Ahhhhhhhhhhhh - OK - siento tonto

```
/usr/share/gtk-desktop-info/config/plugin_forecast.config
```

copie el "plugin_forecast.config" al mismo lugar como el otros gtk archivos; my.template, my_forecast.css y ss-gtk.sh.

y cambie tres líneas:

```

LOCATION = your_city <<<<----- Uno

# Your registered partner id
XOAP_PARTNER_ID =  your_id <<<<<----- dos

# Your registered licence key  <<<<<----- tres
XOAP_LICENCE_KEY = your_key
```

listo!

Bruce

vale he hecho lo que me has dicho y e puesto el archivo plugin_forecast.config en la carpeta gtk-desk, pero sigo sin tener el tiempo hay que configurar alguna otra cosa?

tambien he visto que hay un plugin de exaile sabrías como ponerlo?

un saludo

---

### Post by matias_tati on 2009-08-03
> **staar said:**
> primero que nada, aclararte que 127.0.0.1 es la ip interna de tu máquina (y de la mía, y de la de la mayoría de la gente) y esos mensajes que salen son del script de gmail, que por lo que veo en la captura, anda bien, no te preocupes...

después, para el tema de que no sale la subida y la bajada de datos, el tema puede pasar porque está mal puesta la interfaz ```

${font PizzaDude Bullets:size=16}v${font} Up: ${upspeed **eth1**} Kb/s 
${font PizzaDude Bullets:size=16}r${font} Down: ${downspeed **eth1**} Kb/s 

${font PizzaDude Bullets:size=16}M${font} Upload: ${totalup **eth1**}
${font PizzaDude Bullets:size=16}S${font} Download: ${totaldown **eth1**}
``` esos *eth1* son la interfaz que está mostrando, podés usar el comando ifconfig (en una terminal) para saber el nombre de todas las interfaces de red que estás corriendo, fijate cual es la correcta y cambiala (eth son las cableadas, wlan las wifi, ppp las dial-up, etc, todas con un número al lado, empezando desde 0 inclusive)

saludos

Gracias solo tuve que cambiar el 1 por un 0 y listo. Saludos!!!!!

---

### Post by Bruce M. on 2009-08-04
> **sitodonosti said:**
> vale he hecho lo que me has dicho y e puesto el archivo plugin_forecast.config en la carpeta gtk-desk, pero sigo sin tener el tiempo hay que configurar alguna otra cosa?

tambien he visto que hay un plugin de exaile sabrías como ponerlo?

un saludo

Podes mostrarme su ¿conky y "template"?  No necesito su plugin_forecast.config.

No utilizo "exaile". Voy a buscar una respuesta.

Bruce

---

### Post by sitodonosti on 2009-08-04
my.template:

<html>
<head></head>
<body>
<!-- --datatype : The data type options are:
	 DW (Day of Week),
	 WF (Weather Font output),
Today:	 LT - Feels Like Temp  - WITHOUT: "--startday=0" [--datatype LT]
Today:	 HT - Current Temp - WITHOUT: "--startday=0" [--datatype HT]
Today:	 LT - Forcasted Low Temp: - WITH: "--startday=0" [-- startday=0 --datatype LT]
Today:	 HT - Forecasted High Temp: - WITH: "--startday=0" [-- startday=0 --datatype HT]
Fore:	 LT - Low Temp - use with --startday=1 to 4 [-- startday=1 --datatype LT]
Fore:	 HT - High Temp - use with --startday=1 to 4 [-- startday=1 --datatype HT]
	 CC (Current Conditions),
	 CC (Conditions Text),
	 PC (Precipitation Chance),
	 HM (Humidity),
	 VI (Visibility),
	 WD (Wind Direction),
	 WA (Wind Angle - in degrees),
	 WS (Wind Speed),
	 WG (Wind Gusts),
	 BF (Bearing Font),
	 BS (Bearing font with Speed),
	 CN (City Name),
	 CO (Country),
	 OB (Observatory),
	 SR (SunRise),
	 SS (SunSet),
	 DL (Hours of DayLight),
	 MP (Moon Phase),
	 MF (Moon Font),
	 BR (Barometer Reading),
	 BD (Barometer Description),
	 UI (UV Index),
	 UT (UV Text),
	 DP (Dew Point),
	 LU (Last Update at weather.com),
	 LF (Last Fetch from weather.com),
	 WM (weather map) -->

<table cellpadding="0" cellspacing="5" border="0">
<tr>
	<td rowspan="3" align="center" valign="top"><img src="[--datatype=WF]" width="100"/></td>
	<td rowspan="3" align="center" class="hoy-cyan">[--datatype=HT --hideunits]</td>
	<td rowspan="3" align="right" valign="center">
<!-- High, Low, ST -->
		<table cellpadding="0" cellspacing="0" border="0">
		<tr>
			<td align="right" class="ml-red">Máx:</td>
		</tr>
		<tr>
			<td align="right" class="ml-cyan">Mín:</td>
		</tr>
		<tr>
			<td align="right" class="ml-green"><br>ST:</td>
		</tr>
		<tr>
			<td align="right" class="ml-wkday">PC:</td>
		</tr>
		</table>
<!-- END: High, Low, ST -->
	</td>
	<td rowspan="3" align="right" valign="middle">
<!-- high, low, st values -->
		<table cellpadding="0" cellspacing="0" border="0">
		<tr>
			<td class="ml-red">[--datatype=HT --startday=0 --hideunits]</td>
		</tr>
		<tr>
			<td class="ml-cyan">[--datatype=LT --startday=0 --hideunits]</td>
		</tr>
		<tr>
			<td class="ml-green"><br>[--datatype=LT --hideunits]</td>
		</tr>
		<tr>
			<td class="ml-wkday">[--datatype=PC --startday=0]</td>
		</tr>
		</table>
<!-- END: high, low, st values -->
	</td>
	<td colspan="3" rowspan="4" align="right" valign="top">
<!-- Todays info text -->	
		<table cellpadding="0" cellspacing="0" border="0" valign="top">
		<tr>
			<td align="right" class="ml-yellow">UV:</td>
		</tr>
		<tr>
			<td align="right" class="ml-yellow"><br>Visibilidad:</td>
		</tr>
		<tr>
			<td align="right" class="ml-yellow"><br>Humedad</td>
		</tr>
		<tr>
			<td align="right" class="ml-yellow"><br>Punto&nbsp;del&nbsp;Rocío:</td>
		</tr>
		<tr>
			<td align="right" class="ml-yellow"><br>Presíon:</td>
		</tr>
		</table>
<!-- END: Todays info text -->	
	</td>
	<td rowspan="4" valign="top">
<!-- Todays info data -->	
		<table cellpadding="0" cellspacing="0" border="0" valign="top" width="80">
		<tr>
			<td class="ml-cyan">[--datatype=UI]&nbsp;~&nbsp;[--datatype=UT]</td>
		</tr>
		<tr>
			<td class="ml-cyan"><br>[--datatype=VI]</td>
		</tr>
		<tr>
			<td class="ml-cyan"><br>[--datatype=HM]</td>
		</tr>
		<tr>
			<td class="ml-cyan"><br>[--datatype=DP]</td>
		</tr>
		<tr>
			<td class="ml-cyan"><br>[--datatype=BR]<br>[--datatype=BD]</td>
		</tr>
		</table>
<!-- END: Todays info data -->
	</td>
	<td colspan="4" align="center" valign="bottom" class="ml-yellow">los próximos días</td>
</tr>
<tr><!-- 4 weekday names -->
	<td align="center" class="ml-wkday">[--datatype=DW --startday=1]</td>
	<td align="center" class="ml-wkday">[--datatype=DW --startday=2]</td>
	<td align="center" class="ml-wkday">[--datatype=DW --startday=3]</td>
	<td align="center" class="ml-wkday">[--datatype=DW --startday=4]</td>
</tr>
<tr>
	<td><!-- Day 1 info -->
		<table cellpadding="0" cellspacing="0" border="0" width="70">
		<tr>
			<td colspan="3" align="center"><img src="[--datatype=WF --startday=1]" width="40"/></td>
		</tr>
		<tr>
			<td align="center" class="ml-red">[--datatype=HT --startday=1 --hideunits]</td>
			<td align="center" class="ml-green">~</td>
			<td align="center" class="ml-cyan">[--datatype=LT --startday=1 --hideunits]</td>
		</tr>
		<tr>
			<td colspan="3" align="center" class="ml-wkday">[--datatype=PC --startday=1]</td>
		</tr>
		</table>
	</td>
	<td><!-- Day 2 info -->
		<table cellpadding="0" cellspacing="0" border="0" width="70">
		<tr>
			<td colspan="3" align="center"><img src="[--datatype=WF --startday=2]" width="40"/></td>
		</tr>
		<tr>
			<td align="center" class="ml-red">[--datatype=HT --startday=2 --hideunits]</td>
			<td align="center" class="ml-green">~</td>
			<td align="center" class="ml-cyan">[--datatype=LT --startday=2 --hideunits]</td>
		</tr>
		<tr>
			<td colspan="3" align="center" class="ml-wkday">[--datatype=PC --startday=2]</td>
		</tr>
		</table>
	</td>
	<td><!-- Day 3 info -->
		<table cellpadding="0" cellspacing="0" border="0" width="70">
		<tr>
			<td colspan="3" align="center"><img src="[--datatype=WF --startday=3]" width="40"/></td>
		</tr>
		<tr>
			<td align="center" class="ml-red">[--datatype=HT --startday=3 --hideunits]</td>
			<td align="center" class="ml-green">~</td>
			<td align="center" class="ml-cyan">[--datatype=LT --startday=3 --hideunits]</td>
		</tr>
		<tr>
			<td colspan="3" align="center" class="ml-wkday">[--datatype=PC --startday=3]</td>
		</tr>
		</table>
	</td>
	<td><!-- Day 4 info -->
		<table cellpadding="0" cellspacing="0" border="0" width="70">
		<tr>
			<td colspan="3" align="center"><img src="[--datatype=WF --startday=4]" width="40"/></td>
		</tr>
		<tr>
			<td align="center" class="ml-red">[--datatype=HT --startday=4 --hideunits]</td>
			<td align="center" class="ml-green">~</td>
			<td align="center" class="ml-cyan">[--datatype=LT --startday=4 --hideunits]</td>
		</tr>
		<tr>
			<td colspan="3" align="center" class="ml-wkday">[--datatype=PC --startday=4]</td>
		</tr>
		</table>
	</td>
</tr>
<tr>
	<td colspan="4" class="hugelight">&nbsp;&nbsp;[--datatype=CC]</td>
	<td colspan="4" class="hugelight">&nbsp;</td>
</tr>
<tr>
	<td rowspan="2" align="center" class="ml-yellow"><img src="[--datatype=BS]" width="50"/><br><br>[--datatype=WD] [--datatype=WS]</td>
	<td colspan="3" rowspan="2" align="center" class="ml-yellow"><img src="[--datatype=MF]" width="50"/><br><br>[--datatype=MP]</td>
	<td colspan="3">
<!-- sunrise - sunset & daylight text -->
		<table cellpadding="0" cellspacing="0" border="0">
		<tr>
			<td align="right" class="ml-sr">Salida&nbsp;del&nbsp;Sol:</td>
		</tr>
		<tr>
			<td align="right" class="md-ss">Puesto del Sol:</td>
		</tr>
		<tr>
			<td align="right" class="ml-daylight"><br>Horas de Luz:</td>
		</tr>
		</table>
<!-- END: sunrise - sunset & daylight text -->
	</td>
	<td align="center">
<!-- Today: sunrise - sunset & daylight values -->
		<table cellpadding="0" cellspacing="0" border="0">
		<tr align="center">
			<td align="right" class="ml-sr">[--datatype=SR]</td>
		</tr>
		<tr>
			<td align="right" class="md-ss">[--datatype=SS]</td>
		</tr>
		<tr>
			<td align="right" class="ml-daylight"><br>[--datatype=DL]</td>
		</tr>
		</table>
<!-- END: Today: sunrise - sunset & daylight values -->
	</td>
	<td align="center">
<!-- Day 1: sunrise - sunset & daylight values -->
		<table cellpadding="0" cellspacing="0" border="0">
		<tr align="center">
			<td align="right" class="ml-sr">[--datatype=SR --startday=1]</td>
		</tr>
		<tr>
			<td align="right" class="md-ss">[--datatype=SS --startday=1]</td>
		</tr>
		<tr>
			<td align="right" class="ml-daylight"><br>[--datatype=DL --startday=1]</td>
		</tr>
		</table>
<!-- END: Day 1: sunrise - sunset & daylight values -->
	</td>
	<td align="center">
<!-- Day 2: sunrise - sunset & daylight values -->
		<table cellpadding="0" cellspacing="0" border="0">
		<tr align="center">
			<td align="right" class="ml-sr">[--datatype=SR --startday=2]</td>
		</tr>
		<tr>
			<td align="right" class="md-ss">[--datatype=SS --startday=2]</td>
		</tr>
		<tr>
			<td align="right" class="ml-daylight"><br>[--datatype=DL --startday=2]</td>
		</tr>
		</table>
<!-- END: Day 2: sunrise - sunset & daylight values -->
	</td>
	<td align="center">
<!-- Day 3: sunrise - sunset & daylight values -->
		<table cellpadding="0" cellspacing="0" border="0">
		<tr align="center">
			<td align="right" class="ml-sr">[--datatype=SR --startday=3]</td>
		</tr>
		<tr>
			<td align="right" class="md-ss">[--datatype=SS --startday=3]</td>
		</tr>
		<tr>
			<td align="right" class="ml-daylight"><br>[--datatype=DL --startday=3]</td>
		</tr>
		</table>
<!-- END: Day 3: sunrise - sunset & daylight values -->
	</td>
	<td align="center">
<!-- Day 4: sunrise - sunset & daylight values -->
		<table cellpadding="0" cellspacing="0" border="0">
		<tr align="center">
			<td align="right" class="ml-sr">[--datatype=SR --startday=4]</td>
		</tr>
		<tr>
			<td align="right" class="md-ss">[--datatype=SS --startday=4]</td>
		</tr>
		<tr>
			<td align="right" class="ml-daylight"><br>[--datatype=DL --startday=4]</td>
		</tr>
		</table>
<!-- END: Day 4: sunrise - sunset & daylight values -->
	</td>
</tr>
<tr>
	<td colspan="5" align="right" valign="bottom" class="smalldark">Last Update: [datatype=LU]</td>
	<td colspan="3" align="right" valign="bottom" class="smalldark">Last Fetch: [datatype=LF]</td>
</tr>
</table>
</body>
</html>

ss-gtk.sh:
#!/bin/sh
# click to start, click to stop

# get the pid of the forecast gtk process, if we can...
pid=`ps -C python -f | grep "plugin=forecast" | cut -c10-15`

# do we have a valid pid value for killing :)
if test -z "$pid"
then
	# no pid so starting...
	echo 'starting process'
	# start gtk-desktop weather - Monitor 15" "Res: 1280 x 800 - Bottom left - See: x= and y=
	gtk-desktop-info --allworkspaces --backgroundblend=40 --backgroundcolour=0,0,0 --backgroundcorner=30 --logfile=/tmp/gtk-desktop-info.log --interval=600 --width=725 --height=245 --x=10 --y=755 --windowmanager=gnome --css=/home/sito/gtk-desk/my_forecast.css --template=/home/sito/gtk-desk/my.template --noheader --plugin=forecast &
else
	# valid pid so killing...
	echo 'killing process'
	kill $pid	
fi

my_forecast.css:

body{
  font-family: arial, verdana, "sans-serif";
}

.hoy-cyan {
  color: #A7D4FF;
  font-size: 40px;
  font-weight: bold;
  font-style: italic;
}

.ml-red {
  color: #FF7B7B;
  font-size: 12px;
  font-weight: bold;
}

.ml-cyan {
  color: #A7D4FF;
  font-size: 12px;
  font-weight: bold;
}

.ml-green {
  color: #00FF00;
  font-size: 12px;
  font-weight: bold;
}

.ml-yellow {
  color: #FFFF00;
  font-size: 12px;
  font-weight: bold;
}

.ml-wkday {
  color: #8EEA8E;
  font-size: 12px;
  font-weight: bold;
}

.ml-sr {
  color: #A7D4FF;
  font-size: 12px;
  font-weight: bold;
}

.md-ss {
  color: #DE5F00;
  font-size: 12px;
  font-weight: bold;
}

.ml-daylight {
  color: #FFFFFF;
  font-size: 12px;
  font-weight: bold;
}

.smalllight {
  color: #FFB60D;
  font-size: 10px;
  font-weight: bold;
}

.smalldark {
  color: #EB6500;
  font-size: 10px;
  font-weight: bold;
}

.mediumlight {
  color: #FFB60D;
  font-size: 12px;
  font-weight: bold;
}

.mediumdark {
  color: #EB6500;
  font-size: 12px;
  font-weight: bold;
}

.hoy-temp {
  color: #FFB60D;
  font-size: 22px;
  font-weight: bold;
}

.largelight {
  color: #FFB60D;
  font-size: 16px;
  font-weight: bold;
}

.largedark {
  color: #EB6500;
  font-size: 16px;
  font-weight: bold;
}

.hugelight {
  color: #FFB60D;
  font-size: 22px;
  font-weight: bold;
}

.hugedark {
  color: #EB6500;
  font-size: 22px;
  font-weight: bold;
}

.smalllightitalic {
  color: #FFB60D;
  font-size: 10px;
  font-weight: bold;
  font-style: italic;
}

.smalldarkitalic {
  color: #EB6500;
  font-size: 10px;
  font-weight: bold;
  font-style: italic;
}

.mediumlightitalic {
  color: #FFB60D;
  font-size: 12px;
  font-weight: bold;
  font-style: italic;
}

.mediumdarkitalic {
  color: #EB6500;
  font-size: 12px;
  font-weight: bold;
  font-style: italic;
}

.largelightitalic {
  color: #FFB60D;
  font-size: 16px;
  font-weight: bold;
  font-style: italic;
}

.largedarkitalic {
  color: #EB6500;
  font-size: 16px;
  font-weight: bold;
  font-style: italic;
}

.hugelightitalic {
  color: #A7D4FF;
  font-size: 22px;
  font-weight: bold;
  font-style: italic;
}

.hugedarkitalic {
  color: #EB6500;
  font-size: 22px;
  font-weight: bold;
  font-style: italic;
}

.contenttop{
  color: #EB6500;
  font-size: 12px;
  font-weight: bold;  
  float: left;
  margin: 2px 0 2px 0;
  padding-bottom: 2px;
  width: 100%;
}

.contentleft{
  color: #EB6500;
  font-size: 12px;
  font-weight: bold;  
  float: left;
  margin: 2px 0 2px 0;
  width: 65%;
}

.contentright{
  color: #EB6500;
  font-size: 12px;
  font-weight: bold;  
  float: right;
  margin: 2px 0 2px 0;
  width: 35%;
}

.contentbottom{
  color: #EB6500;
  font-size: 12px;
  font-weight: bold;
  float: right;
  margin: 2px 0 2px 0;
  width: 100%;
}

.current{
  float: left;
  width: 33%;
  margin: 0 0 0 0;
  text-align: center;
}

.current img{
  margin: 10px 0 5px 2px;
}

.moon{
  float: left;
  width: 33%;
  margin: 0 0 0 0;
  text-align: center;
}

.moon img{
  margin: 10px 0 5px 2px;
}

.wind{
  float: left;
  width: 33%;
  margin: 0 0 0 0;
  text-align: center;
}

.wind img{
  margin: 10px 0 5px 2px;
}

.forecast{
  border-top: 2px solid #FFB60D;
  clear: both;
  width: 100%
  margin: 5px 0 2px 0;
  padding: 5px 0 2px 0;
  text-align: center;
}

.day{
  width: 24%;
  float: left;
  text-align: center;
  color: #EB6500;
}

.day img{
  margin: 10px 0 5px 2px;
}

p {
  color: #EB6500;
  font-size: 12px;
  font-weight: bold;  
}


nose porque mi conky pero vale!
.conkyrc:
# maintain spacing between certain elements
use_spacer right

# set to yes if you want tormo to be forked in the background
#background yes

use_xft yes

# Xft font when Xft is enabled
#xftfont Vera-8
#xftfont Andale Mono-8
#xftfont Clean-8
#xftfont cubicfive10:pixelsize=8
xftfont Sans-Serif:size=9:pixelsize=11
#xftfont swf!t_v02:pixelsize=11

# Text alpha when using Xft
xftalpha 1
#mail_spool $MAIL

# Update interval in seconds
update_interval 2.0

# Create own window instead of using desktop (required in nautilus) normal desktop or override
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

#own_window_hints below

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 200 5
maximum_width 250

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no # amplifies text

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 3

# border margins
border_margin 5

# border widt5
border_width 6

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey90
default_shade_color black
default_outline_color DarkGrey

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 5
gap_y 50

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no
override_utf8_locale yes
TEXT
${voffset -5}${font openlogos:size=20}${alignr}${color black}G${color white}T${color brown}U${color orange}t${color red}u${voffset -15}
${font DejaVu Sans:size=9}${color red}${execi 99999 lsb_release -d -s -c | tr -s "\n" " "}$kernel  ${color #ddaa00}$machine 
${color black}$nodename${alignr}${color}Tiempo ${color }$uptime
${font Your Keys:regular:18}${color black}W ${font DejaVu Sans:size=9}${color }CARGA DEL SISTEMA ${hr 2}${color }
#nombre procesador y kernel y logo
${voffset -15}${font Areal:regular:size=10}${color #ffd700}Gráfica: ${font Bitstream Charter:bold:size=10}${color #cdc8b1}${execi 20 glxinfo | grep "OpenGL renderer" | cut -c 25-39}$color$font
 2D/3D Clock: ${color #c0ff3e}${execi 20 nvidia-settings -q GPUCurrentClockFreqs | grep "Attribute" | cut -d" " -f6 | tr -s "," "/" | tr -d "."} MHz${color} Temp: ${color #c0ff3e}${execi 20 nvidia-settings -q gpucoretemp | grep "Attribute" | cut -d" " -f6| cut -c -2}&#7506;C
${font Areal:regular:size=10}${color #ffd700}Procesador
${voffset -2}${font DejaVu Sans:bold:size=7}${color #cdc8b1}${execi 99999 cat /proc/cpuinfo|grep "model name" -m1|cut -d":" -f2|cut -d" " -f2- | sed 's#Processor ##'}$font$color
  $color${cpugraph 116,246 000000 ff4500}  
${voffset -118}			       ${cpu}% 
${voffset -16}  ${freq_g 1}GHz${color #c0ff3e} ${execi 5 sensors |grep "Core 0" | cut -c14-16}Cº$alignr ${color #436eee} ${execi 5 sensors |grep "Core 1" | cut -c14-16}Cº $color${freq_g 2}GHz
    ${voffset 10}${color #ffe7ba}CPU      PID                         Top$color
  ${color }${top cpu 1}    ${top pid 1}$alignr$color${top name 1}
  ${color #ffc125}${top cpu 2}    ${top pid 2}$alignr$color${top name 2}
  ${color #eeee00}${top cpu 3}    ${top pid 3}$alignr$color${top name 3}
  ${color #c0ff3e}${top cpu 4}    ${top pid 4}$alignr$color${top name 4}
$alignr${color}$processes procesos  ($running_processes despiertos)
${voffset 10}${color #c0ff3e}${cpu cpu1}%${cpubar cpu1 5,92}  ${color #436eee}${cpu cpu2}%$alignr${cpubar cpu2 5,92}$color
${font Your Keys:regular:18}${color black}U${font }${color }MEMORIA ${hr 2}$(color)
  ${color }${memgraph 100,246 000000 3BB9C4 }
${voffset -100}            $color${memperc}%  ${memmax}/${mem}
      Top 				      Memoria
   ${top_mem mem 1}  ${alignr}${top_mem name 1}
   ${top_mem mem 2}  ${alignr}${top_mem name 2}
   ${top_mem mem 3}  ${alignr}${top_mem name 3}
   ${top_mem mem 4}  ${alignr}${top_mem name 4}
${voffset 17}${font}  ${color 3BB9C4}SWAP:${color} $swapperc% ${alignr}${color 3BB9C4}${swapbar 8,60 3BB9C4}
${color #000000}DISCO DURO ${hr 2}${color}
${color #ddaa00}Temperatura:${alignr}${color lightgrey}${exec nc localhost 7634 | cut -f 4 -d "|"}º C
${color #ddaa00}Raiz$alignr${voffset 1}${color red}${fs_bar 10,205 /}
${voffset -14}               ${color white} ${color lightgrey}${fs_used /} / ${fs_size /} ${fs_free_perc /}%$alignr${fs_type /} 
${color #ddaa00}Home$alignr${voffset 1}${color blue}${fs_bar 10,205 /home/sito}
${voffset -14}               ${color white} ${color lightgrey}${fs_used /home/sito} / ${fs_size /home/sito} ${fs_free_perc /home/sito}%$alignr${fs_type /home/sito} 
${color #ddaa00}XP$alignr${voffset 1}${color green}${fs_bar 10,205 /media/windows}
${voffset -14}                ${color lightgrey}${fs_used /media/windows} / ${fs_size /media/windows} ${fs_free_perc /media/windows}%$alignr${fs_type /media/windows} 
${color #ddaa00}Sito$alignr${voffset 1}${color white}${fs_bar 10,205 /media/sito}
${voffset -14}                ${color lightgrey}${fs_used /media/sito} / ${fs_size /media/sito} ${fs_free_perc /media/sito}%$alignr${fs_type /media/sito} 
${color blue}G${color red}M${color yellow}A${color blue}I${color green}L 
$alignc${color lightgray}${color D7D3C5}${execi 300 python ~/Conky/.scripts/gmail.py}
${color4}${font Terminus:style=Bold:size=14}@ ${font Terminus:style=Bold:size=11}Exaile${font}

---

### Post by Bruce M. on 2009-08-04
> **sitodonosti said:**
> 

my.template:

ss-gtk.sh:

my_forecast.css:

Son los míos, palabra por palabra. No realicé eso!  ):P

> **sitodonosti said:**
> nose porque mi conky pero vale!

Error en mi parte, perdóneme. :oops: Estoy trabajando mucho a [Conky Hardcore!]("http://conky.linux-hardcore.com/")

Bueno, ahora necesito su código de ciudad. Para ver si anda aca.

Si guieres "PM" su código de ciudad.

Chimo!
Bruce

---

### Post by sitodonosti on 2009-08-04
si la copie pensaando que estaba por aki para poner el codigo de la cidudad y a ver si funcionaba bien y veo que si jejeje mi codigo es SPXX0026

ue me quieres preguntar con lo de "pm" de mi ciudad? la hora?¿
bueno además de la ciduad tambien tengo algun otro problema, que no se ve bien todo nose si es por lo de la ciudad o por los acentos que nose ven bien si quieres pongo la imagen.

---

### Post by Bruce M. on 2009-08-04
> **sitodonosti said:**
> si la copie pensaando que estaba por aki para poner el codigo de la cidudad y a ver si funcionaba bien y veo que si jejeje mi codigo es SPXX0026

ue me quieres preguntar con lo de "pm" de mi ciudad? la hora?¿
bueno además de la ciduad tambien tengo algun otro problema, que no se ve bien todo nose si es por lo de la ciudad o por los acentos que nose ven bien si quieres pongo la imagen.

"PM" Private Message (Mensaje privado) "Click" en mi nombre: Bruce M.

OK, otro caso de :redface: para mi, y muy, muy :redface: ](*,)

No puedo ver a veces los árboles ¡para el bosque!

El verdadero plugin_forecast.config está aquí:

```
~/.config/gtk-desktop-info/plugin_forecast.config
```

```
# The location code for weather data.
# Use the following url to determine your location code by city name:
# http://xoap.weather.com/search/search?where=Norwich
LOCATION = ARDF0127
#LOCATION = SPXX0026
```

no olvide el "LOCALE" tambien:

```
# with no setting the default locale of the system is used, if supported.
# If no translation is available then the plugin defaults to english
LOCALE = es
```

> **sitodonosti said:**
> si quieres pongo la imagen.

OK, please show me.

Que tengas un buen día
yo, voy a ocultar mi cara
Bruce :redface:

---

### Post by sitodonosti on 2009-08-04
okay!!ahora el tiempo si es el de mi ciudad pero mira lo que pasa con los acentos y que se corta la imagen alfinal, me imagino que lo que sale con ??? es porque wather channel no tiene información.

---

### Post by Bruce M. on 2009-08-04
> **sitodonosti said:**
> okay!!ahora el tiempo si es el de mi ciudad pero mira lo que pasa con los acentos y que se corta la imagen alfinal, me imagino que lo que sale con ??? es porque wather channel no tiene información.

Bueno - el conseguir mejor

Claro weather.com no tiene ??? (hours of daylight) se calcula en el ".py" programa, y no sé porqué no en su caso, los acentos también.  

Voy a hablar con un amigo: jjgomera.(él es español) 

Saludos.
Bruce

---

### Post by jjgomera on 2009-08-04
> **sitodonosti said:**
> okay!!ahora el tiempo si es el de mi ciudad pero mira lo que pasa con los acentos y que se corta la imagen alfinal, me imagino que lo que sale con ??? es porque wather channel no tiene información.
¿Qué locales tienes en el sistema? Usa el comando locale para comprobarlo y escribe aquí lo que te devuelve

---

### Post by sitodonosti on 2009-08-04
Bueno ya he arreglado lo del tamaño y se ve todo bien, lo unico que faltaria es lo de los acentos y que no se ve lo de la hora de voz

locale:
~$ locale
LANG=es_ES.UTF-8
LC_CTYPE="es_ES.UTF-8"
LC_NUMERIC="es_ES.UTF-8"
LC_TIME="es_ES.UTF-8"
LC_COLLATE="es_ES.UTF-8"
LC_MONETARY="es_ES.UTF-8"
LC_MESSAGES="es_ES.UTF-8"
LC_PAPER="es_ES.UTF-8"
LC_NAME="es_ES.UTF-8"
LC_ADDRESS="es_ES.UTF-8"
LC_TELEPHONE="es_ES.UTF-8"
LC_MEASUREMENT="es_ES.UTF-8"
LC_IDENTIFICATION="es_ES.UTF-8"
LC_ALL=

---

### Post by jjgomera on 2009-08-04
> **Bruce M. said:**
> 

no olvide el "LOCALE" tambien:

```
# with no setting the default locale of the system is used, if supported.
# If no translation is available then the plugin defaults to english
LOCALE = es
```

prueba con:
```
LOCALE=None
```
o
```
LOCALE=es_ES
```

---

### Post by sitodonosti on 2009-08-04
local=es tenia puesto y nada e probado con None y es_Es y sigue igual dejo la imagen 
gracias por la ayuda

---

### Post by jjgomera on 2009-08-04
Pues ahora si que no se que puede ser, te diría que probaras a configurar tus locales a es_ES@euro pero si a bruce le funciona con las normales no se que puede estar pasando.

---

### Post by sitodonosti on 2009-08-04
Por si es de ayuda en el amsn no puedo poner acentos, es decir los acentos me salen así: cami´on en vez de camión pero solo en el amsn nose si sirve de algo...
vy actualizar idiomas aer s isirve de algo nose...




PD: he instalado todo lo de lso idiomas y puesto es_ES y nada sigue igual.. :(

---

### Post by Fak89 on 2009-08-04
alguien tiene idea de como poner la barra de estado del audacious?? porq la variable "audacious_bar" no me la toma..

---

### Post by Bruce M. on 2009-08-04
> **sitodonosti said:**
> Bueno ya he arreglado lo del tamaño y se ve todo bien, lo unico que faltaria es lo de los acentos y que no se ve lo de la hora de voz

locale:
~$ locale
LANG=es_ES.UTF-8
LC_CTYPE="es_ES.UTF-8"
LC_NUMERIC="es_ES.UTF-8"
LC_TIME="es_ES.UTF-8"
LC_COLLATE="es_ES.UTF-8"
LC_MONETARY="es_ES.UTF-8"
LC_MESSAGES="es_ES.UTF-8"
LC_PAPER="es_ES.UTF-8"
LC_NAME="es_ES.UTF-8"
LC_ADDRESS="es_ES.UTF-8"
LC_TELEPHONE="es_ES.UTF-8"
LC_MEASUREMENT="es_ES.UTF-8"
LC_IDENTIFICATION="es_ES.UTF-8"
LC_ALL=

OK probar:

```
LOCALE = 
```

---

### Post by sitodonosti on 2009-08-05
> **Bruce M. said:**
> OK probar:

```
LOCALE = 
```

ya lo hice y sige sin funcionar.... :$

---

### Post by Bruce M. on 2009-08-05
> **sitodonosti said:**
> ya lo hice y sige sin funcionar.... :$

OK, tengo otro idea.

Mire:

gksu gedit /usr/share/gtk-desktop-info/locale/es/LC_MESSAGES/plugin_forecast.po

¿Son los acentos ACEPTABLES en ese archivo?

Hice la traducción con un teclado "Latin-America", 
el código para los acentos es quizá diferente.

Que tengas un buen día.
Bruce

---

### Post by sitodonosti on 2009-08-05
si, yo creo que si porque en el archivo aparece esto:
#: conkyForecast.py:303
msgid "Wed"
msgstr "Mié"

sin embargo me aparece un tocho asi:
#: conkyForecast.py:272
#: conkyForecast.py:291
#: conkyForecast.py:295
#: conkyForecast.py:296
#: conkyForecast.py:515
#: conkyForecast.py:796
#: conkyForecast.py:838
#: conkyForecast.py:839
#: conkyForecast.py:840
#: conkyForecast.py:841
#: conkyForecast.py:842
#: conkyForecast.py:843
#: conkyForecast.py:844
#: conkyForecast.py:845
#: conkyForecast.py:846

y en los demás hay cosas dentro como esto:
#: conkyForecast.py:264
msgid "Hail"
msgstr "Granizo"

#: conkyForecast.py:265
msgid "Sleet"
msgstr "Aguanieve"

#: conkyForecast.py:266
msgid "Dust"
msgstr "Polvo"

#: conkyForecast.py:267
msgid "Fog"
msgstr "Niebla"

#: conkyForecast.py:268
msgid "Haze"
msgstr "Bruma"

#: conkyForecast.py:269
msgid "Smoke"
msgstr "Humo"

#: conkyForecast.py:270
msgid "Blustery"
msgstr "Tempestad"

#: conkyForecast.py:271
msgid "Windy"
msgstr "Ventoso"

---

### Post by Bruce M. on 2009-08-05
> **sitodonosti said:**
> si, yo creo que si porque en el archivo aparece esto:
#: conkyForecast.py:303
msgid "Wed"
msgstr "Mié"

sin embargo me aparece un tocho asi:
#: conkyForecast.py:272
#: conkyForecast.py:291
#: conkyForecast.py:295


Utiliza el mismo **.PO ** archivo como del conkyForecast - No es un problema, él es normal.

¿Cómo están los acentos en ese archivo?

---

### Post by sitodonosti on 2009-08-05
nose lo que me quieres decir con lo de como estan los acentos asique tedejo el archivo

# i18n translation template file for conkyForecast.py
# The msgstr values require defining for the require language, once populated
# pass the file back so it can be compiled and used in the script.
# Copyright (C) 2008 Kaivalagi
# Kaivalagi <m_buck@hotmail.com>, 2008.
#
msgid ""
msgstr ""
"Project-Id-Version: conkyForecast.py 1.0\n"
"POT-Creation-Date: 2008-08-19 19:02+BST\n"
"PO-Revision-Date: 2009-02-02 18:43-0300\n"
"Last-Translator: canuck <b1canuck@gmail.com>\n"
"Language-Team: Kaivalagi <m_buck@hotmail.com>\n"
"MIME-Version: 1.0\n"
"Content-Type: text/plain; charset=utf-8\n"
"Content-Transfer-Encoding: 8bit\n"
"Generated-By: pygettext.py 1.5\n"

#: conkyForecast.py:247
msgid "Tornado"
msgstr "Tornado"

#: conkyForecast.py:248
msgid "Tropical Storm"
msgstr "Tormenta Tropical"

#: conkyForecast.py:249
msgid "Hurricane"
msgstr "Huracán"

#: conkyForecast.py:250
msgid "Severe Thunderstorms"
msgstr "Tormentas Fuertes"

#: conkyForecast.py:251
msgid "Thunderstorms"
msgstr "Tormentas"

#: conkyForecast.py:252
msgid "Mixed Rain and Snow"
msgstr "Lluvia y Nieve Mezclada"

#: conkyForecast.py:253
msgid "Mixed Rain and Sleet"
msgstr "Lluvia y Aguanieve Mezclada"

#: conkyForecast.py:254
msgid "Mixed Precipitation"
msgstr "Aguanieve"

#: conkyForecast.py:255
msgid "Freezing Drizzle"
msgstr "Llovizna Helada"

#: conkyForecast.py:256
msgid "Drizzle"
msgstr "Llovizna"

#: conkyForecast.py:257
msgid "Freezing Rain"
msgstr "Lluvia Engelante"

#: conkyForecast.py:258
msgid "Light Rain"
msgstr "Lluvia Engelante"

#: conkyForecast.py:259
msgid "Rain"
msgstr "Lluvia"

#: conkyForecast.py:260
msgid "Snow Flurries"
msgstr "Nieve Ligera"

#: conkyForecast.py:261
msgid "Light Snow Showers"
msgstr "Nieve Ligera"

#: conkyForecast.py:262
msgid "Drifting Snow"
msgstr "Ventisca de Nieve"

#: conkyForecast.py:263
msgid "Snow"
msgstr "Nieve"

#: conkyForecast.py:264
msgid "Hail"
msgstr "Granizo"

#: conkyForecast.py:265
msgid "Sleet"
msgstr "Aguanieve"

#: conkyForecast.py:266
msgid "Dust"
msgstr "Polvo"

#: conkyForecast.py:267
msgid "Fog"
msgstr "Niebla"

#: conkyForecast.py:268
msgid "Haze"
msgstr "Bruma"

#: conkyForecast.py:269
msgid "Smoke"
msgstr "Humo"

#: conkyForecast.py:270
msgid "Blustery"
msgstr "Tempestad"

#: conkyForecast.py:271
msgid "Windy"
msgstr "Ventoso"

#: conkyForecast.py:272
#: conkyForecast.py:291
#: conkyForecast.py:295
#: conkyForecast.py:296
#: conkyForecast.py:515
#: conkyForecast.py:796
#: conkyForecast.py:838
#: conkyForecast.py:839
#: conkyForecast.py:840
#: conkyForecast.py:841
#: conkyForecast.py:842
#: conkyForecast.py:843
#: conkyForecast.py:844
#: conkyForecast.py:845
#: conkyForecast.py:846
msgid "N/A"
msgstr "N/A"

#: conkyForecast.py:273
msgid "Cloudy"
msgstr "Nublado"

#: conkyForecast.py:274
#: conkyForecast.py:275
msgid "Mostly Cloudy"
msgstr "Nublado"

#: conkyForecast.py:276
#: conkyForecast.py:277
msgid "Partly Cloudy"
msgstr "Parcialmente Nublado"

#: conkyForecast.py:278
#: conkyForecast.py:279
msgid "Clear"
msgstr "Despejado"

#: conkyForecast.py:280
#: conkyForecast.py:281
msgid "Fair"
msgstr "Algo Nublado"

#: conkyForecast.py:282
msgid "Mixed Rain and Hail"
msgstr "Lluvia con Granizo"

#: conkyForecast.py:283
msgid "Hot"
msgstr "Calor"

#: conkyForecast.py:284
#: conkyForecast.py:294
msgid "Isolated Thunderstorms"
msgstr "Tormentas Aisladas"

#: conkyForecast.py:285
msgid "Scattered Thunderstorms"
msgstr "Tormentas Dispersas"

#: conkyForecast.py:286
#: conkyForecast.py:292
msgid "Scattered Showers"
msgstr "Chubascos Dispersos"

#: conkyForecast.py:287
msgid "Heavy Rain"
msgstr "Lluvia Pesada"

#: conkyForecast.py:288
msgid "Scattered Snow Showers"
msgstr "Nevadas Débiles y Dispersas"

#: conkyForecast.py:289
#: conkyForecast.py:290
msgid "Heavy Snow"
msgstr "Nieve Pesada"

#: conkyForecast.py:293
msgid "Snow Showers"
msgstr "Nevadas Dispersas"

#: conkyForecast.py:300
msgid "Now"
msgstr "Ahora"

#: conkyForecast.py:301
msgid "Mon"
msgstr "Lun"

#: conkyForecast.py:302
msgid "Tue"
msgstr "Mar"

#: conkyForecast.py:303
msgid "Wed"
msgstr "Mié"

#: conkyForecast.py:304
msgid "Thu"
msgstr "Jue"

#: conkyForecast.py:305
msgid "Fri"
msgstr "Vie"

#: conkyForecast.py:306
msgid "Sat"
msgstr "Sáb"

#: conkyForecast.py:307
msgid "Sun"
msgstr "Dom"

#: conkyForecast.py:428
msgid "New"
msgstr "Luna Nueva"

#: conkyForecast.py:429
msgid "First Quarter"
msgstr "Cuarto Creciente"

#: conkyForecast.py:430
msgid "Full"
msgstr "Luna Llena"

#: conkyForecast.py:431
msgid "Last Quarter"
msgstr "Cuarto Menguante"

#: conkyForecast.py:432
msgid "Waning Crescent"
msgstr "Luna Menguante"

#: conkyForecast.py:433
msgid "Waning Gibbous"
msgstr "Luna Gibada Menguante"

#: conkyForecast.py:434
msgid "Waxing Crescent"
msgstr "Luna Nueva Visible"

#: conkyForecast.py:435
msgid "Waxing Gibbous"
msgstr "Luna Gibada Creciente"

#: conkyForecast.py:514
msgid "n/a"
msgstr "n/a"

#: conkyForecast.py:516
msgid "Not Available"
msgstr "No Disponible"

#: conkyForecast.py:517
msgid "unknown"
msgstr "desconocido"

#: conkyForecast.py:518
msgid "NONE"
msgstr "NINGUNOS"

#: conkyForecast.py:519
msgid "day"
msgstr "día"

#: conkyForecast.py:520
msgid "night"
msgstr "noche"

#: conkyForecast.py:525
msgid "Extreme"
msgstr "Extremo"

#: conkyForecast.py:526
msgid "Very High"
msgstr "Muy Alto"

#: conkyForecast.py:527
msgid "High"
msgstr "Alto"

#: conkyForecast.py:529
msgid "Low"
msgstr "Bajo"

#: conkyForecast.py:534
msgid "Very Low"
msgstr "Muy Bajo"

#: conkyForecast.py:535
msgid "Moderate"
msgstr "Moderado"

#: conkyForecast.py:536
msgid "rising"
msgstr "en aumento"

#: conkyForecast.py:537
msgid "falling"
msgstr "en descenso"

#: conkyForecast.py:538
msgid "steady"
msgstr "constante"

#: conkyForecast.py:539
msgid "calm"
msgstr "calma"

#: conkyForecast.py:545
msgid "East"
msgstr "Este"

#: conkyForecast.py:546
msgid "East Northeast"
msgstr "Este nordeste"

#: conkyForecast.py:547
msgid "East Southeast"
msgstr "Este sureste"

#: conkyForecast.py:548
msgid "North"
msgstr "Norte"

#: conkyForecast.py:549
msgid "Northeast"
msgstr "Nordeste"

#: conkyForecast.py:550
msgid "North Northeast"
msgstr "Norte nordeste"

#: conkyForecast.py:551
msgid "North Northwest"
msgstr "Norte noroeste"

#: conkyForecast.py:552
msgid "Northwest"
msgstr "Noroeste"

#: conkyForecast.py:553
msgid "South"
msgstr "Sur"

#: conkyForecast.py:554
msgid "Southeast"
msgstr "Sureste"

#: conkyForecast.py:555
msgid "South Southeast"
msgstr "Sur sureste"

#: conkyForecast.py:556
msgid "South Southwest"
msgstr "Sur suroeste"

#: conkyForecast.py:557
msgid "Southwest"
msgstr "Suroeste"

#: conkyForecast.py:558
msgid "variable"
msgstr "variable"

#: conkyForecast.py:559
msgid "West"
msgstr "Oeste"

#: conkyForecast.py:560
msgid "West Northwest"
msgstr "Oeste noroeste"

#: conkyForecast.py:561
msgid "West Southwest"
msgstr "Oeste suroeste"

#: conkyForecast.py:565
msgid "E"
msgstr "E"

#: conkyForecast.py:566
msgid "ENE"
msgstr "ENE"

#: conkyForecast.py:567
msgid "ESE"
msgstr "ESE"

#: conkyForecast.py:568
msgid "N"
msgstr "N"

#: conkyForecast.py:569
msgid "NE"
msgstr "NE"

#: conkyForecast.py:570
msgid "NNE"
msgstr "NNE"

#: conkyForecast.py:571
msgid "NNW"
msgstr "NNO"

#: conkyForecast.py:572
msgid "NW"
msgstr "NO"

#: conkyForecast.py:573
msgid "S"
msgstr "S"

#: conkyForecast.py:574
msgid "SE"
msgstr "SE"

#: conkyForecast.py:575
msgid "SSE"
msgstr "SSE"

#: conkyForecast.py:576
msgid "SSW"
msgstr "SSO"

#: conkyForecast.py:577
msgid "SW"
msgstr "SO"

#: conkyForecast.py:578
msgid "W"
msgstr "O"

#: conkyForecast.py:579
msgid "WNW"
msgstr "ONO"

#: conkyForecast.py:580
msgid "WSW"
msgstr "OSO"

#: conkyForecast.py:584
#: conkyForecast.py:795
msgid "Today"
msgstr "Hoy"

#: conkyForecast.py:585
msgid "Monday"
msgstr "Lunes"

#: conkyForecast.py:586
msgid "Tuesday"
msgstr "Martes"

#: conkyForecast.py:587
msgid "Wednesday"
msgstr "Míercoles"

#: conkyForecast.py:588
msgid "Thursday"
msgstr "Jueves"

#: conkyForecast.py:589
msgid "Friday"
msgstr "Viernes"

#: conkyForecast.py:590
msgid "Saturday"
msgstr "Sábado"

#: conkyForecast.py:591
msgid "Sunday"
msgstr "Domingo"

#: conkyForecast.py:1143
msgid "\302\260C"
msgstr "\302\260C"

#: conkyForecast.py:1144
msgid "kph"
msgstr "km/h"

#: conkyForecast.py:1145
msgid "km"
msgstr "km"

#: conkyForecast.py:1146
msgid "mb"
msgstr "mb"

#: conkyForecast.py:1148
msgid "\302\260F"
msgstr "\302\260F"

#: conkyForecast.py:1149
msgid "mph"
msgstr "mph"

#: conkyForecast.py:1150
msgid "m"
msgstr "m"

#: conkyForecast.py:1151
msgid "in"
msgstr "in"

---

### Post by Bruce M. on 2009-08-05
> **sitodonosti said:**
> nose lo que me quieres decir con lo de como estan los acentos asique tedejo el archivo


```
#: conkyForecast.py:249
msgid "Hurricane"
msgstr "Huracán"

#: conkyForecast.py:288
msgid "Scattered Snow Showers"
msgstr "Nevadas Débiles y Dispersas"

#: conkyForecast.py:303
msgid "Wed"
msgstr "Mié"

#: conkyForecast.py:306
msgid "Sat"
msgstr "Sáb"

#: conkyForecast.py:519
msgid "day"
msgstr "día"
```

Cuando usted abre el archivo en su computadora, ¿hay acentos en las palabras españolas?  ¿O usted ve algo extraño?

Bruce

---

### Post by sitodonosti on 2009-08-05
> **Bruce M. said:**
> [CODE]

Cuando usted abre el archivo en su computadora, ¿hay acentos en las palabras españolas?  ¿O usted ve algo extraño?

Bruce

aaaah! si si que veo como en día sáb y asi si que están

---

### Post by Bruce M. on 2009-08-05
> **sitodonosti said:**
> aaaah! si si que veo como en día sáb y asi si que están

Entonces no es un problema con el "gtk-desktop-info". El problema está con su configuración de la computadora.

---

### Post by sitodonosti on 2009-08-05
y sabrías como se podría solucionarse¿igual es por eso que en amsn me salen los acentos así : cami´on en vez de camión

---

### Post by Bruce M. on 2009-08-05
> **sitodonosti said:**
> y sabrías como se podría solucionarse¿igual es por eso que en amsn me salen los acentos así : cami´on en vez de camión

Ninguna idea. Mi "locale" para mi PC es: Canada.

```
:~$ locale
LANG=en_CA.UTF-8
LC_CTYPE=en_CA.UTF-8
LC_NUMERIC=en_CA.UTF-8
LC_TIME=en_CA.UTF-8
LC_COLLATE=en_CA.UTF-8
LC_MONETARY=en_CA.UTF-8
LC_MESSAGES=en_CA.UTF-8
LC_PAPER=en_CA.UTF-8
LC_NAME=en_CA.UTF-8
LC_ADDRESS=en_CA.UTF-8
LC_TELEPHONE=en_CA.UTF-8
LC_MEASUREMENT=en_CA.UTF-8
LC_IDENTIFICATION=en_CA.UTF-8
LC_ALL=
~$
```

con un teclado de "Latin-America", y todo anda bien.

Extraño no hay foro para España.

Cree un nuevo "thread" aquí en el foro de la Argentina y pida ayuda de su problema.

Buena suerte

Que tengas un buen día.
Bruce

---

### Post by matias_tati on 2009-08-06
> **staar said:**
> primero que nada, aclararte que 127.0.0.1 es la ip interna de tu máquina (y de la mía, y de la de la mayoría de la gente) y esos mensajes que salen son del script de gmail, que por lo que veo en la captura, anda bien, no te preocupes...

después, para el tema de que no sale la subida y la bajada de datos, el tema puede pasar porque está mal puesta la interfaz ```

${font PizzaDude Bullets:size=16}v${font} Up: ${upspeed **eth1**} Kb/s 
${font PizzaDude Bullets:size=16}r${font} Down: ${downspeed **eth1**} Kb/s 

${font PizzaDude Bullets:size=16}M${font} Upload: ${totalup **eth1**}
${font PizzaDude Bullets:size=16}S${font} Download: ${totaldown **eth1**}
``` esos *eth1* son la interfaz que está mostrando, podés usar el comando ifconfig (en una terminal) para saber el nombre de todas las interfaces de red que estás corriendo, fijate cual es la correcta y cambiala (eth son las cableadas, wlan las wifi, ppp las dial-up, etc, todas con un número al lado, empezando desde 0 inclusive)

saludos

Y tenes idea de pq me muestra lo de gmail en amarillo y como lo cambio?

---

### Post by jjgomera on 2009-08-06
> **matias_tati said:**
> Y tenes idea de pq me muestra lo de gmail en amarillo y como lo cambio?

añade un ${color} antes de gmail si quieres usar el color por defecto de tu conky o ${color 000000} para usar un color concreto, en ese caso el 000000 que es el negro

> **sitodonosti said:**
> y sabrías como se podría solucionarse¿igual es por eso que en amsn me salen los acentos así : cami´on en vez de camión
lo del amsn parece más un problema de configuración del teclado, si fuera de codificación te saldría camiÂon o algo así, pero desde luego que es raro que solo te pase con el amsn, o esto con gtk-dektop-info. La pena es que yo no puedo instalar gtk-desktop para comprobar si me funciona bien, me da problemas de dependencias en lenny.

> **Bruce M. said:**
> Extraño no hay foro para España.
Esa es una historia bastante larga, digamos que prefirieron mantenerse en un servidor aparte y morirse poco a poco antes que crear aquí el foro, estában aquí antes de morir [http://www.ubuntu-es.org/](http://www.ubuntu-es.org/)

---

### Post by sitodonosti on 2009-08-07
> **jjgomera said:**
> 
Esa es una historia bastante larga, digamos que prefirieron mantenerse en un servidor aparte y morirse poco a poco antes que crear aquí el foro, estában aquí antes de morir [http://www.ubuntu-es.org/](http://www.ubuntu-es.org/)

han muerto? joe yo que veia soluciones algunas y no me funcionaba, yo pienso que es mejor crear aquí el foro que hay mas gente que te pueda ayudar, la verda es que esi es raro lo del amsn asique igual lo que hago es reinstalar ubuntu con home incluido que tengo muchas cosas que no utilizo y sobran por aki jijiji

un saludo y gracias por la ayuda con conky y gtk-info

---

### Post by Hagen. on 2009-08-09
Hola gente, soy nuevo por estos lados, antiguamente estaba en ubuntu-es pero segun lei mas arriba ese foro no esta mas (cada tanto me abre la pagina). Decidi registrarme aca porq tengo un problema hace tiempo y no encuentro la solucion por ningun lado. Estoy usando conky 1.6.0 con Ubuntu 9.04 64 bits. Arranca al iniciar la sesion todo barbaro, el tema es que despues de un rato, conky deja de refrescarse y se congelan todos los valores, desde la hora hasta el uso de memoria, procesos, uso de los cores y demas. Al cabo de 8 o 9 min vuelve a funcionar bien pero despues vuelve a pasarle lo mismo. Intente ejecutar conky con maxima prioridad pero me pasa exactamente lo mismo. Ya no se que probar. Alguno tuvo el mismo problema? Aca les dejo una copia de mi conkyrc y de paso una captura para que vean como es.

Gracias de antemano.

[html]&#65279;# .conkyrc - Edited from various examples compiled from the web
# by Seba

# --- Window Layout & Options --- #
own_window yes
own_window_colour brown
own_window_transparent yes
own_window_type desktop
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
total_run_times 0
update_interval 0.5
use_spacer right
use_xft yes
alignment top_right
gap_x 10
gap_y 45

# --- Colours, Sizes, Fonts & Margins --- #
update_interval 1.0
maximum_width 250
stippled_borders 3
border_margin 9
border_width 10
default_color #92A2C7

# --- Text --- #
draw_outline no
draw_borders no
font Sans:size=8
uppercase no
draw_shades yes
override_utf8_locale yes

TEXT
${font Sans:size=9}${color  #99CBFF}${hr 2}$color${font Sans:size=8:weight=bold}
${alignc 30}${color #E67B13}${font OpenLogos:size=50}u${font}
${font Sans:size=14:weight=bold}${color #99CBFF}            ${time %H:%M}
${font Sans:size=11:weight=bold}${color #99CBFF}    ${time %A} ${time %e} ${time %B} ${time %G}

${font Sans:size=9:weight=bold}${color  #99CBFF}System Information ${hr 2}$color${font Sans:size=8}
${color  #99CBFF}Computer$color Ubuntu 9.04 ${alignr}${color  #99CBFF} Uptime$color $uptime
${color  #99CBFF}Kernel$color  $kernel ${alignr}${color  #99CBFF}Arch.$color $machine

${font Sans:size=9:weight=bold}${color  #99CBFF}Date ${hr 2}

${color 888888}${font LCDMono:size=12}${execpi 60 DJS=`date +%_d`; cal | sed '1d' | sed '/./!d' | sed 's/$/ /' | fold -w 21 | sed -n '/^.\{21\}/p' | sed 's/^/${alignc} /' | sed /" $DJS "/s/" $DJS "/" "'${color2}'"$DJS"'${color 888888}'" "/}

${font Sans:size=9:weight=bold}${color  #99CBFF}Computer ${hr 2}$color
${font Arial:bold:size=8}${color #ff0000}${execi 99999 cat /proc/cpuinfo | grep "model name" -m1 | cut -d":" -f2 | cut -d" " -f2- | sed 's#Processor ##'}$font$color
${color  #99CBFF}Frequency:$color ${execi 20 sensors |grep "Core0 Temp" | cut -d" " -f4} $font$color$alignr${freq_g 2} GHz ${alignr}${color  #99CBFF}Processes:$color $running_processes/ $processes

${font Sans:size=9:weight=bold}${color  #99CBFF}CPU ${hr 2}$color
${color green}${font}Core 1                              ${color white}${cpu cpu0}%   ${color green}Core 2                         ${color white}${cpu cpu1}%        
${cpugraph cpu0 25,120 000000 ff6600 }  ${cpugraph cpu1 25,120 000000 ff6600 }   
${color green}Core 3                      ${color white}${cpu cpu2}%
${cpugraph cpu2 25,120 000000 ff6600 }

${font Sans:size=9:weight=bold}${color  #99CBFF}5 Process Top ${hr 2}{color} ${font}${alignr}${color green}
Name                                 ${alignr}CPU   ${alignr}RAM  $color
${font}${top name 1}${alignr}${top cpu 1}${alignr }${top mem 1}
${font}${top name 2}${alignr}${top cpu 2}${alignr }${top mem 2}
${font}${top name 3}${alignr}${top cpu 3}${alignr }${top mem 3}
${font}${top name 4}${alignr}${top cpu 4}${alignr }${top mem 4}
${font}${top name 5}${alignr}${top cpu 5}${alignr }${top mem 5}

${font Sans:size=9:weight=bold}${color  #99CBFF}Ram & Swap ${hr 2}$color${font Sans:size=8:weight=bold}
${font}${color #99CBFF}RAM$color  ${memperc}%  ${color  #99CBFF}${membar 3.180}
${font}${color #99CBFF}SWAP$color  ${swapperc}%  ${color  #99CBFF}${swapbar 3.180}

${font Sans:size=9:weight=bold}${color  #99CBFF}Partition ${hr 2}$color${font Sans:size=8:weight=bold}
${font}${color #99CBFF}Root$color  ${fs_free_perc /}%$alignr${fs_free /}/ ${fs_size /}
${color  #99CBFF}${fs_bar 3 /} 
${font}${color #99CBFF}Home$color  ${fs_free_perc /home}%$alignr${fs_free /home}/ ${fs_size /home}
${color  #99CBFF}${fs_bar 3 /home}

${font Sans:size=9}${color  #99CBFF}Public IP: ${execi 1~/.scripts/ip.sh} ${hr 2}$color${font Sans:size=8:weight=bold}
${font Sans:size=9}${color  #99CBFF}Network IP: ${addr eth0} ${hr 2}$color${font Sans:size=8:weight=bold}

${color #99CBFF}Transfer Speed
${font}${color green}Download.$color ${downspeed eth0}&#1050;b/s${alignr}${font}${color red}Upload.$color${alignr} ${upspeed eth0}&#1050;b/s
${downspeedgraph eth0 25,120 000000 00ff00} ${alignr}${upspeedgraph eth0 25,120 000000 ff0000}$color

${font Sans:size=9:weight=bold}${color  #99CBFF}&#1058;raffic ${hr 2}$color${font Sans:size=9}
${color green}Downstream ${alignr}${totaldown eth0} 
${color red}Upstream ${alignr} ${totalup eth0}

${font Sans:size=8:weight=bold}${color  #99CBFF}${hr 2}$color${font Sans:size=8:weight=bold}

[/html]
[[IMG]http://img196.imageshack.us/img196/5980/desktoplmd.th.jpg[/IMG]]("http://img196.imageshack.us/i/desktoplmd.jpg/")[[IMG]http://img196.imageshack.us/i/desktoplmd.jpg/[/IMG]]("http://%5BIMG%5Dhttp://img196.imageshack.us/i/desktoplmd.jpg/%5B/IMG%5D")

---

### Post by staar on 2009-08-09
mmm, tenés dos valores para la opción update_interval, dejá uno, también probá correrlo desde la terminal y posteá los errores que te tira cuando se congela...

saludos

---

### Post by Hagen. on 2009-08-09
> **staar said:**
> mmm, tenés dos valores para la opción update_interval, dejá uno, también probá correrlo desde la terminal y posteá los errores que te tira cuando se congela...

saludos

Muchas gracias por responder. Si, acabo de darme cuenta de los dos valores, ahi le deje uno solo. Estoy probando y te cuento. Justo lo tenia corriendo por terminal, pego aca lo unico que decia.

Conky: /home/seba/.conkyrc: 1: no such configuration: '&#65279;'
Conky: /home/seba/.conkyrc: 25: config file error
Conky: desktop window (14000a7) is subwindow of root window (b1)
Conky: window type - desktop
Conky: drawing to created window (0x4000001)
Conky: drawing to double buffer

---

### Post by Hagen. on 2009-08-09
Me fije esos dos errores que marcaba ahi y vi que la linea 25 correspondia al color asignado para conky, elimine ese valor junto con la fila 1 (no tenia nada, solo un comentario) y sigue pasando lo mismo. Ahora los dos errores desaparecieron de la consola y solo figura lo siguiente:

seba@Magui:~$ conky
Conky: desktop window (14000a7) is subwindow of root window (b1)
Conky: window type - normal
Conky: drawing to created window (0x4400001)
Conky: drawing to double buffer

---

### Post by staar on 2009-08-09
primero que nada una cosa, no hace falta (no estoy seguro si eso está generando problemas, por lo menos sí en la línea 25) que pongas los # al poner los códigos de color, funciona igual poner solo el número...

después verificaría los intervalos con los que corrés algunas cosas, los del calendario y la frecuencia parecen bien, pero el del script de la ip está muy bajo y le falta un espacio...

también podrías aclarar si cuando conky se cuelga estás haciendo algo en particular con la pc...

saludos

---

### Post by matias_tati on 2009-08-09
> **jjgomera said:**
> añade un ${color} antes de gmail si quieres usar el color por defecto de tu conky o ${color 000000} para usar un color concreto, en ese caso el 000000 que es el negro


${color white}${font FreeSans:size=16}@${font}${execpi 300 python ~/scripts/gmail_parser.py [email]matiaspedroarroyo@gmail.com[/email] ------------- 3}

---

### Post by staar on 2009-08-10
> **matias_tati said:**
> ${color white}${font FreeSans:size=16}@${font}${execpi 300 python ~/scripts/gmail_parser.py [email]matiaspedroarroyo@gmail.com[/email] ------------- 3}

si lo usas todo blanco, te conviene cambiar la opción default_color (la tenías en BADCDD, cambiala a white o FFFFFF) y no poner un ${color} en cada línea...

saludos

---

### Post by Hagen. on 2009-08-10
> **staar said:**
> primero que nada una cosa, no hace falta (no estoy seguro si eso está generando problemas, por lo menos sí en la línea 25) que pongas los # al poner los códigos de color, funciona igual poner solo el número...

después verificaría los intervalos con los que corrés algunas cosas, los del calendario y la frecuencia parecen bien, pero el del script de la ip está muy bajo y le falta un espacio...

también podrías aclarar si cuando conky se cuelga estás haciendo algo en particular con la pc...

saludos

Comente la linea 25 y ahora deja de mostrar el error en la consola pero sigue freezandose conky a los pocos minutos. Voy a probar de sacar el modulo de la direccion ip para ver si el script ese esta jodiendo de alguna manera.

Con respecto a si hago algo especifico cuando se congela conky te respondo que no, es indiferente, la pc puede estar sin ejecutar tareas y es lo mismo a que yo este usando alguna aplicacion.

Gracias.

---

### Post by matias_tati on 2009-08-10
> **staar said:**
> si lo usas todo blanco, te conviene cambiar la opción default_color (la tenías en BADCDD, cambiala a white o FFFFFF) y no poner un ${color} en cada línea...

saludos

Y elimino esto ${color white} de cada linea?

---

### Post by staar on 2009-08-10
> **matias_tati said:**
> Y elimino esto ${color white} de cada linea?
si querés lo podés dejar, no afecta, pero sería redundante...

saludos

---

### Post by Hagen. on 2009-08-10
> **staar said:**
> primero que nada una cosa, no hace falta (no estoy seguro si eso está generando problemas, por lo menos sí en la línea 25) que pongas los # al poner los códigos de color, funciona igual poner solo el número...

después verificaría los intervalos con los que corrés algunas cosas, los del calendario y la frecuencia parecen bien, pero el del script de la ip está muy bajo y le falta un espacio...

también podrías aclarar si cuando conky se cuelga estás haciendo algo en particular con la pc...

saludos

Efectivamente era el script de la ip que esstaba mal, lo saque y ahora anda barbaro. Como te diste cuenta q el problema podia venir por ese lado?

[[IMG]http://img249.imageshack.us/img249/7429/conkyi.th.jpg[/IMG]]("http://img249.imageshack.us/i/conkyi.jpg/")

---

### Post by staar on 2009-08-10
porque tuve un problema similar, porque el intervalo me parecía muy bajo (revisar la ip una vez por segundo es como mucho, no?) y porque faltaba un espacio entre el número del intervalo y la ubicación del script :-D:-D

me alegro que se haya solucionado...

saludos

---

### Post by Hagen. on 2009-08-10
> **staar said:**
> porque tuve un problema similar, porque el intervalo me parecía muy bajo (revisar la ip una vez por segundo es como mucho, no?) y porque faltaba un espacio entre el número del intervalo y la ubicación del script :-D:-D

me alegro que se haya solucionado...

saludos

Sos groso! Gracias de nuevo, te debo una, anotala en mi cuenta. :):)

---

### Post by matias_tati on 2009-08-11
Pq mi conky aparece por encima de las ventanas? esto es desde que lo puse desde el arranque desp esta todo igual..
Si lo cierro con killall conky y luego lo abro con conky se ve bien pero en el arranque me lo carga asi.

---

### Post by Hagen. on 2009-08-11
> **matias_tati said:**
> Pq mi conky aparece por encima de las ventanas? esto es desde que lo puse desde el arranque desp esta todo igual..
Si lo cierro con killall conky y luego lo abro con conky se ve bien pero en el arranque me lo carga asi.

Si no me equivoco eso se debe porq no esta especificado que quede siempre debajo. Tenes que tener la siguiente linea al inicio.

own_window_hints undecorated,**below**,sticky,skip_taskbar,skip_pager

Fijate de tener ese below ahi.

---

### Post by matias_tati on 2009-08-11
Me olvide la captura....

---

### Post by Hagen. on 2009-08-11
> **matias_tati said:**
> Me olvide la captura....

Postea el codigo de tu conkyrc.

---

### Post by matias_tati on 2009-08-11
> **Hagen. said:**
> Si no me equivoco eso se debe porq no esta especificado que quede siempre debajo. Tenes que tener la siguiente linea al inicio.

own_window_hints undecorated,**below**,sticky,skip_taskbar,skip_pager

Fijate de tener ese below ahi.

Esta asi..........

---

### Post by jjgomera on 2009-08-11
cambia esta linea:

own_window_type normal

---

### Post by Hagen. on 2009-08-11
> **matias_tati said:**
> Esta asi..........

Cambia donde dice: 

own_window_type override

por

own_window_type normal

---

### Post by matias_tati on 2009-08-11
Y pq es que no se me funde con el fondo? Se ven los bordes.....

---

### Post by staar on 2009-08-11
> **matias_tati said:**
> Y pq es que no se me funde con el fondo? Se ven los bordes.....
tuve un el mismo problema, lo arreglé, pero no me acuerdo bien como :-P

creo que era en las propiedades del efecto 'Decoración de ventanas' en compiz, en la parte de las sombras, cambiar el *any* (o sea que todas las ventanas tengan sombra) por algo como *!(iclass=conky)* para que a las ventanas de conky no les agrege la sombra...

saludos

---

### Post by matias_tati on 2009-08-11
> **staar said:**
> tuve un el mismo problema, lo arreglé, pero no me acuerdo bien como :-P

creo que era en las propiedades del efecto 'Decoración de ventanas' en compiz, en la parte de las sombras, cambiar el *any* (o sea que todas las ventanas tengan sombra) por algo como *!(iclass=conky)* para que a las ventanas de conky no les agrege la sombra...

saludos

Funciono gracias

---

### Post by sitodonosti on 2009-08-14
Holap, oye tengo una pregunta, ¿se pueden poner imagenes en conky?por ejemplo la imagen de un icono?

---

### Post by Bruce M. on 2009-08-14
> **sitodonosti said:**
> Holap, oye tengo una pregunta, ¿se pueden poner imagenes en conky?por ejemplo la imagen de un icono?

Si, con Conky v1.7.1

[Conky v1.7.1 para Ubuntu]("http://www.getdeb.net/search.php?keywords=conky") (Xubu & KDE)

> image
	<path to image> (-p x,y) (-s WxH)

	Renders an image from the path specified using IMLIB2. Takes 2 optional arguments, one being a position, the other an size. Changing the x,y position will move the position of the image, and changing the WxH will scale the image. Example: ${image /home/brenden/cheeseburger.jpg -p 20,20 -s 200x200} will render 'cheeseburger.jpg' at (20,20) scaled to 200x200 pixels. Conky does not make any attempt to adjust the position (or any other formatting) of images, they are just rendered as per the arguments passed. The only reason $image is part of the TEXT section, is to allow for runtime modifications, through $execp $lua_parse, $lua_read_parse, or some other method.

```
${image /home/bruloo/Conky/images/clock.png -p 20,85 -s 64x64}${image /home/bruloo/Conky/images/thermometer_2.png -p 20,455 -s 14x40}${image /home/bruloo/Conky/images/pc-ram.png -p 140,563 -s 121x31}${image /home/bruloo/Conky/images/HdFlagship_Hard_Drive_2.png -p 100,655 -s 104x60}
```

---

### Post by Fistandantilus on 2009-08-14
Como se puede hacer para rellenar un texto con caracteres a la derecha para que siempre tenga un ancho fijo??? 
A lo que voy: 
${top name 1}${alignr}${top cpu 1}${alignr }${top mem 1}

"top mem x" y "top cpu x" tienen una salida #.## en caso de ser menor a 10 y ##.## en caso de ser menor a 100, pero quiero que siempre tengan el formato ##.## ya que cuando uno de los programas q estan en la lista ocupa mas del 10% de la memoria y el resto menos se desalinea la lista.... y no me gusta... :P

la idea es que quede
{nombre1}-------------------------##.##-##.##
{nombre2}-------------------------##.##-##.##
{nombre3}-------------------------##.##-##.##
y no me quede
{nombre1}--------------------------##.##-#.##
{nombre2}-------------------------##.##-##.##
{nombre3}--------------------------##.##-#.##

Saludos!.

---

### Post by Fistandantilus on 2009-08-14
Estoy teniendo el mismo problema que matias_tati pero no lo puedo solucionar... probé varias combinaciones en el focus_prevention del compiz pero no logro sacarle el borde....

además cuando le hago click en el borde que aparece remarcado me lo deja de mostrar pero el proceso sigue en ejecucion... esta relacionado con el mismo problema o es por otra cosa???

---

### Post by matias_tati on 2009-08-15
> **Fistandantilus said:**
> Estoy teniendo el mismo problema que matias_tati pero no lo puedo solucionar... probé varias combinaciones en el focus_prevention del compiz pero no logro sacarle el borde....

además cuando le hago click en el borde que aparece remarcado me lo deja de mostrar pero el proceso sigue en ejecucion... esta relacionado con el mismo problema o es por otra cosa???

Yo hize lo que me dijo Star y se soluciono.

---

### Post by Fistandantilus on 2009-08-15
listo!, lo estaba poniendo en Opciones Generales -> Focus & Raice behaviour  :P

grax matias.

nadie tiene una idea de como hacer que la salida de ${top mem x} tenga siempre el format ##.## ??

---

### Post by matias_tati on 2009-08-27
> **ALEXEX said:**
> te quedo muy bien el conky, lo puedes subir a la page, porfa:P

use_xft yes
xftfont verdana:size=8
alignment top_right
xftalpha 0.8
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
stippled_borders 10
border_margin 4
border_width 1
default_shade_color grey
default_outline_color black
default_color black
use_spacer none
no_buffers yes
uppercase no
color1 F8DF58


TEXT
${font Radio Space:size=38}${alignc}MATIAS
${font OpenLogos:size=45} u t
${font weather:size=82}${execi 600 ~/scripts/conditions.sh}${font}${voffset -25} ${execi 1200 ~/scripts/pogodynka.sh}

${font weather:size=28}x ${font}HDD ${execi 1 ~/scripts/hddmonit.sh}°C 

${font PizzaDude Bullets:size=16}v${font} Up: ${upspeed eth0} Kb/s 
${font PizzaDude Bullets:size=16}r${font} Down: ${downspeed eth0} Kb/s 

${font PizzaDude Bullets:size=16}M${font} Upload: ${totalup eth0}
${font PizzaDude Bullets:size=16}S${font} Download: ${totaldown eth0}

${font StyleBats:size=16}A${font} CPU0: ${cpu cpu0}% ${cpubar cpu0}
${font StyleBats:size=16}A${font} CPU1: ${cpu cpu1}% ${cpubar cpu1}

${font PizzaDude Bullets:size=16}J${font} $mem / $memmax

${font StyleBats:size=18}P${font} Logeado: ${uptime_short}


${font Radio Space:size=20}${time %A %d %Y}
${font Radio Space:size=55}${time %H:%M}

[[img]http://h.imagehost.org/t/0881/screenshot_001.jpg[/img]](http://h.imagehost.org/view/0881/screenshot_001)

---

### Post by matias_tati on 2009-09-04
Como hafo para que el pronostico del clima se vea en español lo debo hacer manualmente? Pq me voy a volver loco.

[[img]http://a.imagehost.org/t/0767/screenshot_001.jpg[/img]](http://a.imagehost.org/view/0767/screenshot_001)

Gracias....

---

### Post by Bruce M. on 2009-09-04
> **matias_tati said:**
> Como hafo para que el pronostico del clima se vea en español lo debo hacer manualmente? Pq me voy a volver loco.

Gracias....

Hay un archivo:  ~/.conkyForecast.config

```
# config settings for conkyForecast.py
CACHE_FOLDERPATH = /home/bruloo/Conky/cache
CONNECTION_TIMEOUT = 5
EXPIRY_MINUTES = 30
TIME_FORMAT = %H:%M
DATE_FORMAT = %Y-%m-%d
LOCALE = es
XOAP_PARTNER_ID = xxxxxxxxx
XOAP_LICENCE_KEY = yyyyyyyyyyyy
MAXIMUM_DAYS_FORECAST = 7
#BASE_XOAP_URL = http://xoap.weather.com/weather/local/<LOCATION>?cc=*&dayf=10&link=xoap&prod=xoap&par=<XOAP_PARTNER_ID>&key=<XOAP_LICENCE_KEY>&unit=m
BASE_XOAP_URL = http://xml.weather.com/weather/local/<LOCATION>?cc=*&unit=m&dayf=10&link=xoap&prod=xoap&par=<XOAP_PARTNER_ID>&key=<XOAP_LICENCE_KEY>&unit=m
```

Podes cambiar: LOCALE = por otro idiomas.

```
LOCALE =    # (default: ingles)
LOCALE = es # español
```

Que tengas un buen día
Bruce

---

### Post by matias_tati on 2009-09-04
> **Bruce M. said:**
> Hay un archivo:  ~/.conkyForecast.config

```
# config settings for conkyForecast.py
CACHE_FOLDERPATH = /home/bruloo/Conky/cache
CONNECTION_TIMEOUT = 5
EXPIRY_MINUTES = 30
TIME_FORMAT = %H:%M
DATE_FORMAT = %Y-%m-%d
LOCALE = es
XOAP_PARTNER_ID = xxxxxxxxx
XOAP_LICENCE_KEY = yyyyyyyyyyyy
MAXIMUM_DAYS_FORECAST = 7
#BASE_XOAP_URL = http://xoap.weather.com/weather/local/<LOCATION>?cc=*&dayf=10&link=xoap&prod=xoap&par=<XOAP_PARTNER_ID>&key=<XOAP_LICENCE_KEY>&unit=m
BASE_XOAP_URL = http://xml.weather.com/weather/local/<LOCATION>?cc=*&unit=m&dayf=10&link=xoap&prod=xoap&par=<XOAP_PARTNER_ID>&key=<XOAP_LICENCE_KEY>&unit=m
```

Podes cambiar: LOCALE = por otro idiomas.

```
LOCALE =    # (default: ingles)
LOCALE = es # español
```

Que tengas un buen día
Bruce

 Lo tengo asi pero
 nada.

---

### Post by Fak89 on 2009-09-04
> **matias_tati said:**
> Como hafo para que el pronostico del clima se vea en español lo debo hacer manualmente? Pq me voy a volver loco.

[[IMG]http://a.imagehost.org/t/0767/screenshot_001.jpg[/IMG]]("http://a.imagehost.org/view/0767/screenshot_001")

Gracias....

Mati, me podrías pasar el codigo de tu almanaque?? se ve muy bonito asi..

---

### Post by matias_tati on 2009-09-04
> **Fak89 said:**
> Mati, me podrías pasar el codigo de tu almanaque?? se ve muy bonito asi..

use_xft yes
xftfont Liberation Sans:size=8

update_interval 1
total_run_times 0
double_buffer yes
text_buffer_size 2048

own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

minimum_size 182 0
maximum_width 182

default_color cccccc
draw_shades no

color0 white
color1 white
color2 white

alignment top_right
gap_x 25
gap_y 40

no_buffers no
net_avg_samples 2

override_utf8_locale yes

no_buffers yes

imlib_cache_size 0

TEXT
${font Liberation Sans:style=Bold:size=8}SISTEMA $stippled_hr${font}
${color0}${font Poky:size=15}S${font}${color}${goto 32}${voffset -8}Kernel:  ${alignr}${color2}${kernel}${color}
${goto 32}Actividad: ${alignr}${color2}${uptime}${color}
${offset 1}${color0}${font Poky:size=16}P${font}${offset -19}${voffset 9}${cpubar cpu0 4,18}${color}${voffset -15}${goto 32}CPU1: ${font Liberation Sans:style=Bold:size=8}${color1}${cpu cpu1}%${color}${font} ${alignr}${color2}${cpugraph cpu1 8,60 white white}${color}
${goto 32}CPU2: ${font Liberation Sans:style=Bold:size=8}${color1}${cpu cpu2}%${color}${font} ${alignr}${color2}${cpugraph cpu2 8,60 white white}${color}
${color0}${font Poky:size=16}M${font}${color}${goto 32}${voffset -7}RAM: ${font Liberation Sans:style=Bold:size=8}${color1}$memperc%${color}${font}
${offset 1}${voffset 3}${color2}${membar 4,18}${color}${goto 32}${voffset -4}U: ${color2}${mem}${color} F: ${color2}${memeasyfree}${color}
${voffset 2}${color0}${font Poky:size=15}a${font}${color}${goto 32}${voffset -10}Procesos: ${color2}${alignr 13}CPU${alignr}RAM${color}
${voffset -1}${goto 42}${color2}${top name 1}${color}${font Liberation Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 1}${alignr }${top mem 1}${color}${font}
${voffset -1}${goto 42}${color2}${top name 2}${color}${font Liberation Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 2}${alignr }${top mem 2}${color}${font}
${voffset -1}${goto 42}${color2}${top name 3}${color}${font Liberation Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 3}${alignr }${top mem 3}${color}${font}
${voffset 4}${font Liberation Sans:style=Bold:size=8}FECHA $stippled_hr${font}
${voffset 20}${alignc 44}${font zoraclockH:size=70}${color2}${execpi 120 ~/.conky/clock.sh hour}${color}${font}
${voffset -90}${alignc 64}${font zoraclockM:size=100}${color2}${execpi 60 ~/.conky/clock.sh minute}${color}${font}
${voffset 26}${alignc}${font Liberation Sans:style=Bold:size=10}${color1}${time %H:%M}${color}${font}${voffset -8}
${voffset 4}${color0}${font Poky:size=13}d${font}${color}${voffset -4}${font Liberation Mono:size=8}${execpi 10800 DJS=`date +%_d`; cal | sed 's/^/${alignc} /' | sed s/" $DJS "/" "'${font Liberation Mono:style=bold:size=8}${color1}'"$DJS"'${color}${font}${font Liberation Mono:size=8}'" "/}${font}${font}
${voffset 4}${font Liberation Sans:style=Bold:size=8}HD $stippled_hr${font}
${execpi 30 ~/.conky/hd_default.py}
${voffset 4}${font Liberation Sans:style=Bold:size=8}CLIMA $stippled_hr${font}
${if_existing /proc/net/route wlan0}
${execpi 10800 ~/.conky/conkyForecast.py --location=ARBA0034 -t ~/.conky/conkyForecast.template}
${else}${if_existing /proc/net/route eth0}
${execpi 10800 ~/.conky/conkyForecast.py --location=ARBA0034 -t ~/.conky/conkyForecast.template}
${endif}${else}${if_existing /proc/net/route ppp0}
${execpi 10800 ~/.conky/conkyForecast.py --location=ARBA0034 -t ~/.conky/conkyForecast.template}
${endif}${else}${voffset 4}${color0}${font PizzaDude Bullets:size=12}4${font}${color}${goto 32}Clima no disponible${endif}${endif}

[[img]http://a.imagehost.org/t/0767/screenshot_001.jpg[/img]](http://a.imagehost.org/view/0767/screenshot_001)


Nadie tiene idea de como poner en español la parte del clima?

---

### Post by Bruce M. on 2009-09-04
> **matias_tati said:**
> Lo tengo asi pero
 nada.

Mostrarme tu ~/.conkyForecast.config (menos KEY y ID) y ~/.conky/conkyForecast.template

Que versión de conkyForecast?
```
0 bruloo@bruloo: ~
Fri Sep 04, 22:52 $ conkyForecast -V
conkyForecast v.2.07
0 bruloo@bruloo: ~
Fri Sep 04, 22:52 $
```

Que tengas un buen día.
Bruce

---

### Post by matias_tati on 2009-09-04
[[img]http://a.imagehost.org/t/0606/PantallazoconkyForecast_config_gedit.jpg[/img]](http://a.imagehost.org/view/0606/PantallazoconkyForecast_config_gedit)

Y siceramente no se que version es. Donde me fijo eso?

---

### Post by Bruce M. on 2009-09-05
> **matias_tati said:**
> [[img]http://a.imagehost.org/t/0606/PantallazoconkyForecast_config_gedit.jpg[/img]](http://a.imagehost.org/view/0606/PantallazoconkyForecast_config_gedit)

Y siceramente no se que version es. Donde me fijo eso?

Terminal:

```
conkyForecast -V
```

---

### Post by matias_tati on 2009-09-05
> **Bruce M. said:**
> Terminal:

```
conkyForecast -V
```

matias@matias-desktop:~$ conkyForecast -V
bash: conkyForecast: orden no encontrada
matias@matias-deskt

---

### Post by Bruce M. on 2009-09-05
> **matias_tati said:**
> matias@matias-desktop:~$ conkyForecast -V
bash: conkyForecast: orden no encontrada
matias@matias-deskt

??? ??? ???  pero vos tenes ~/.conkyforecast.config?

Ponga su ID y KEY en un archivo de texto para mantenerlos seguro

OK, Buscar el nuevo conkyforecast: [Conky Weather Forecast Python Script]("http://ubuntuforums.org/showthread.php?t=869328")

**"Method 1: Using apt"**

Después de que se aumente, cambie sus líneas conky como esto:

```
${voffset 4}${font Liberation Sans:style=Bold:size=8}CLIMA $stippled_hr${font}
${if_existing /proc/net/route wlan0}
${execpi 10800 conkyForecast --location=ARBA0034 -t ~/.conky/conkyForecast.template}
${else}${if_existing /proc/net/route eth0}
${execpi 10800 conkyForecast --location=ARBA0034 -t ~/.conky/conkyForecast.template}
${endif}${else}${if_existing /proc/net/route ppp0}
${execpi 10800 conkyForecast --location=ARBA0034 -t ~/.conky/conkyForecast.template}
```

y uso este para un nuevo ~/.conkyForecast.config

```
# config settings for conkyForecast.py
CACHE_FOLDERPATH = /tmp/
CONNECTION_TIMEOUT = 5
EXPIRY_MINUTES = 30
TIME_FORMAT = %H:%M
DATE_FORMAT = %Y-%m-%d
LOCALE = es
XOAP_PARTNER_ID = xxxxxxxxxxx       #de tuyo
XOAP_LICENCE_KEY = yyyyyyyyyyyyyyy  #de tuyo
MAXIMUM_DAYS_FORECAST = 7
#BASE_XOAP_URL = http://xoap.weather.com/weather/local/<LOCATION>?cc=*&dayf=10&link=xoap&prod=xoap&par=<XOAP_PARTNER_ID>&key=<XOAP_LICENCE_KEY>&unit=m
BASE_XOAP_URL = http://xml.weather.com/weather/local/<LOCATION>?cc=*&unit=m&dayf=10&link=xoap&prod=xoap&par=<XOAP_PARTNER_ID>&key=<XOAP_LICENCE_KEY>&unit=m
```

Bruce

---

### Post by matias_tati on 2009-09-05
Lo intente una vez y no me salio en un rato intento de nuevo...

---

### Post by Mustaine666 on 2009-09-07
> **Hagen. said:**
> Hola gente, soy nuevo por estos lados, antiguamente estaba en ubuntu-es pero segun lei mas arriba ese foro no esta mas (cada tanto me abre la pagina). Decidi registrarme aca porq tengo un problema hace tiempo y no encuentro la solucion por ningun lado. Estoy usando conky 1.6.0 con Ubuntu 9.04 64 bits. Arranca al iniciar la sesion todo barbaro, el tema es que despues de un rato, conky deja de refrescarse y se congelan todos los valores, desde la hora hasta el uso de memoria, procesos, uso de los cores y demas. Al cabo de 8 o 9 min vuelve a funcionar bien pero despues vuelve a pasarle lo mismo. Intente ejecutar conky con maxima prioridad pero me pasa exactamente lo mismo. Ya no se que probar. Alguno tuvo el mismo problema? Aca les dejo una copia de mi conkyrc y de paso una captura para que vean como es.

Gracias de antemano.

[html]&#65279;# .conkyrc - Edited from various examples compiled from the web
# by Seba

# --- Window Layout & Options --- #
own_window yes
own_window_colour brown
own_window_transparent yes
own_window_type desktop
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
total_run_times 0
update_interval 0.5
use_spacer right
use_xft yes
alignment top_right
gap_x 10
gap_y 45

# --- Colours, Sizes, Fonts & Margins --- #
update_interval 1.0
maximum_width 250
stippled_borders 3
border_margin 9
border_width 10
default_color #92A2C7

# --- Text --- #
draw_outline no
draw_borders no
font Sans:size=8
uppercase no
draw_shades yes
override_utf8_locale yes

TEXT
${font Sans:size=9}${color  #99CBFF}${hr 2}$color${font Sans:size=8:weight=bold}
${alignc 30}${color #E67B13}${font OpenLogos:size=50}u${font}
${font Sans:size=14:weight=bold}${color #99CBFF}            ${time %H:%M}
${font Sans:size=11:weight=bold}${color #99CBFF}    ${time %A} ${time %e} ${time %B} ${time %G}

${font Sans:size=9:weight=bold}${color  #99CBFF}System Information ${hr 2}$color${font Sans:size=8}
${color  #99CBFF}Computer$color Ubuntu 9.04 ${alignr}${color  #99CBFF} Uptime$color $uptime
${color  #99CBFF}Kernel$color  $kernel ${alignr}${color  #99CBFF}Arch.$color $machine

${font Sans:size=9:weight=bold}${color  #99CBFF}Date ${hr 2}

${color 888888}${font LCDMono:size=12}${execpi 60 DJS=`date +%_d`; cal | sed '1d' | sed '/./!d' | sed 's/$/ /' | fold -w 21 | sed -n '/^.\{21\}/p' | sed 's/^/${alignc} /' | sed /" $DJS "/s/" $DJS "/" "'${color2}'"$DJS"'${color 888888}'" "/}

${font Sans:size=9:weight=bold}${color  #99CBFF}Computer ${hr 2}$color
${font Arial:bold:size=8}${color #ff0000}${execi 99999 cat /proc/cpuinfo | grep "model name" -m1 | cut -d":" -f2 | cut -d" " -f2- | sed 's#Processor ##'}$font$color
${color  #99CBFF}Frequency:$color ${execi 20 sensors |grep "Core0 Temp" | cut -d" " -f4} $font$color$alignr${freq_g 2} GHz ${alignr}${color  #99CBFF}Processes:$color $running_processes/ $processes

${font Sans:size=9:weight=bold}${color  #99CBFF}CPU ${hr 2}$color
${color green}${font}Core 1                              ${color white}${cpu cpu0}%   ${color green}Core 2                         ${color white}${cpu cpu1}%        
${cpugraph cpu0 25,120 000000 ff6600 }  ${cpugraph cpu1 25,120 000000 ff6600 }   
${color green}Core 3                      ${color white}${cpu cpu2}%
${cpugraph cpu2 25,120 000000 ff6600 }

${font Sans:size=9:weight=bold}${color  #99CBFF}5 Process Top ${hr 2}{color} ${font}${alignr}${color green}
Name                                 ${alignr}CPU   ${alignr}RAM  $color
${font}${top name 1}${alignr}${top cpu 1}${alignr }${top mem 1}
${font}${top name 2}${alignr}${top cpu 2}${alignr }${top mem 2}
${font}${top name 3}${alignr}${top cpu 3}${alignr }${top mem 3}
${font}${top name 4}${alignr}${top cpu 4}${alignr }${top mem 4}
${font}${top name 5}${alignr}${top cpu 5}${alignr }${top mem 5}

${font Sans:size=9:weight=bold}${color  #99CBFF}Ram & Swap ${hr 2}$color${font Sans:size=8:weight=bold}
${font}${color #99CBFF}RAM$color  ${memperc}%  ${color  #99CBFF}${membar 3.180}
${font}${color #99CBFF}SWAP$color  ${swapperc}%  ${color  #99CBFF}${swapbar 3.180}

${font Sans:size=9:weight=bold}${color  #99CBFF}Partition ${hr 2}$color${font Sans:size=8:weight=bold}
${font}${color #99CBFF}Root$color  ${fs_free_perc /}%$alignr${fs_free /}/ ${fs_size /}
${color  #99CBFF}${fs_bar 3 /} 
${font}${color #99CBFF}Home$color  ${fs_free_perc /home}%$alignr${fs_free /home}/ ${fs_size /home}
${color  #99CBFF}${fs_bar 3 /home}

${font Sans:size=9}${color  #99CBFF}Public IP: ${execi 1~/.scripts/ip.sh} ${hr 2}$color${font Sans:size=8:weight=bold}
${font Sans:size=9}${color  #99CBFF}Network IP: ${addr eth0} ${hr 2}$color${font Sans:size=8:weight=bold}

${color #99CBFF}Transfer Speed
${font}${color green}Download.$color ${downspeed eth0}&#1050;b/s${alignr}${font}${color red}Upload.$color${alignr} ${upspeed eth0}&#1050;b/s
${downspeedgraph eth0 25,120 000000 00ff00} ${alignr}${upspeedgraph eth0 25,120 000000 ff0000}$color

${font Sans:size=9:weight=bold}${color  #99CBFF}&#1058;raffic ${hr 2}$color${font Sans:size=9}
${color green}Downstream ${alignr}${totaldown eth0} 
${color red}Upstream ${alignr} ${totalup eth0}

${font Sans:size=8:weight=bold}${color  #99CBFF}${hr 2}$color${font Sans:size=8:weight=bold}

[/html][[IMG]http://img196.imageshack.us/img196/5980/desktoplmd.th.jpg[/IMG]]("http://img196.imageshack.us/i/desktoplmd.jpg/")[[IMG]http://img196.imageshack.us/i/desktoplmd.jpg/[/IMG]]("http://%5BIMG%5Dhttp://img196.imageshack.us/i/desktoplmd.jpg/%5B/IMG%5D")


me gusto mucho este conky.. pero cuando copio el conkyrc. .. y lo intento arrancar .. no arranca! .. 

el mio es.. 

[html]  use_xft yes
xftfont verdana:size=8
alignment top_right
xftalpha 0.8
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
stippled_borders 10
border_margin 4
border_width 1
default_shade_color grey
default_outline_color black
default_color BADCDD
use_spacer none
no_buffers yes
uppercase no
color1 F8DF58
override_utf8_locale yes



TEXT


  
   ${color FFFFFF} TIEMPO ${hr 2}

   ${voffset -10}${alignr 56}${font ConkyWeather:style=Bold:size=40}${execi 600 conkyForecast --location=SPXX0015 --datatype=WF}${font}
   ${voffset -50}${font Weather:size=40}y${font}  ${voffset -20}${font Arial Black:size=26}${execi 600 conkyForecast --location=SPXX0015 --datatype=HT}${font}
       
   ${Color 81F7F3} RED ${hr 2} 
   ${font PizzaDude Bullets:size=16}v${font}   Up: ${upspeed eth1} Kb/s 
   ${font PizzaDude Bullets:size=16}r${font}   Down: ${downspeed eth1} Kb/s 

   ${font PizzaDude Bullets:size=16}M${font}   Upload: ${totalup eth1}
   ${font PizzaDude Bullets:size=16}S${font}   Download: ${totaldown eth1}

   ${voffset 4}${font PizzaDude Bullets:size=14}b${font} IP pública $alignr${execi 3600 curl www.whatismyip.org}
   ${voffset 4}${font PizzaDude Bullets:size=14}a${font} IP local $alignr ${addr eth0}

   ${color FAAC58}SYSTEMA ${hr 2}
   ${font OpenLogos:size=16}u${font}  Kernel:  ${alignr}${kernel}
   ${font StyleBats:size=16}A${font}  CPU: ${cpu cpu1}% ${alignr}${cpubar cpu1 8,60}
   ${font StyleBats:size=16}g${font}  RAM: $memperc%  $mem ${alignr}${membar 8,60}
   ${font Pie charts for maps:size=14}7${font}   ${voffset -5}Home:
   ${voffset 4}${alignc}${fs_free /home}/${fs_size /home} ${alignr}${fs_bar 8,60 /home}
   ${font StyleBats:size=16}j${font}  SWAP: $swapperc% ${alignr}${swapbar 8,60}
   ${font StyleBats:size=16}q${font}  Encendido: ${alignr}${uptime}

   ${color C2E078}PROCESOS ${hr 2}

   CPU $alignr PID CPU% MEM%

   ${top name 1}$alignr${top pid 1}${top cpu 1}${top mem 1}
   ${top name 2}$alignr${top pid 2}${top cpu 2}${top mem 2}
   ${top name 3}$alignr${top pid 3}${top cpu 3}${top mem 3}
   ${top name 4}$alignr${top pid 4}${top cpu 4}${top mem 4}
   ${top name 5}$alignr${top pid 5}${top cpu 5}${top mem 5}

   RAM $alignr PID CPU% MEM%

   ${top_mem name 1}$alignr${top_mem pid 1}${top_mem cpu 1}${top_mem mem 1}
   ${top_mem name 2}$alignr${top_mem pid 2}${top_mem cpu 2}${top_mem mem 2}
   ${top_mem name 3}$alignr${top_mem pid 3}${top_mem cpu 3}${top_mem mem 3}
   ${top_mem name 4}$alignr${top_mem pid 4}${top_mem cpu 4}${top_mem mem 4}
   ${top_mem name 5}$alignr${top_mem pid 5}${top_mem cpu 5}${top_mem mem 5}
   
  
   ${color F8DF58} ${hr 2}
   ${font Radio Space:size=14}${time %A %d %Y}
      ${font Radio Space:size=55}${time %H:%M}
   

[/html]

y se ve asi! .. [[img]http://h.imagehost.org/t/0245/Pantallazo-1.jpg[/img]](http://h.imagehost.org/view/0245/Pantallazo-1) 

algo muy simple!

---

### Post by Bruce M. on 2009-09-08
> **matias_tati said:**
> Lo intente una vez y no me salio en un rato intento de nuevo...

Borre su archivo existente de ~/.conky/conkyForecast.py

Dé un nuevo nombre a ~/.conkyforecast.config = ~/.conkyforecast.config-bak

Comience otra vez con el archivo: **conkyforecast_2.05_all.deb**

Después de él está instalado, copie el "conkyforecast.config" a ~/.conkyforecast.config

```
sudo cp /usr/share/conkyforecast/conkyForecast.config
 ~/.conkyForecast.config
```

y copie su ID y KEY de su viejo archivo: ~/.conkyforecast.config-bak y no olvide: **LOCALE = es**

**[COLOR="Red"]NO COPIE conkyforecast.py a otra localización.[/COLOR]**

Cambie las tres líneas:
```
${execpi 10800 ~/.conky/conkyForecast.py --location=ARBA0034 -t ~/.conky/conkyForecast.template}
```
a
```
${execpi 10800 conkyForecast --location=ARBA0034 --template=/home/matias/.conky/conkyForecast.template}
```
si su nombre de usuario es: /home/matias/

Que tengas un buen día
Bruce

---

### Post by Mustaine666 on 2009-09-14
en que formato estan los colores.. osea de donde puedo sacar los codigos de los colores! .. gracias!

---

### Post by Bruce M. on 2009-09-14
> **Mustaine666 said:**
> en que formato estan los colores.. osea de donde puedo sacar los codigos de los colores! .. gracias!

¿Como esto?

```
#F0F8FF  AliceBlue
#FAEBD7  AntiqueWhite
#00FFFF  Aqua
#7FFFD4  Aquamarine
#F0FFFF  Azure
#F5F5DC  Beige
#FFE4C4  Bisque
#000000  Black
#FFEBCD  BlanchedAlmond
#0000FF  Blue
#8A2BE2  BlueViolet
#A52A2A  Brown
#DEB887  BurlyWood
#5F9EA0  CadetBlue
#7FFF00  Chartreuse
#D2691E  Chocolate
#FF7F50  Coral
#6495ED  CornflowerBlue
#FFF8DC  Cornsilk
#DC143C  Crimson
#00FFFF  Cyan
#00008B  DarkBlue
#008B8B  DarkCyan
#B8860B  DarkGoldenRod
#A9A9A9  DarkGray
#A9A9A9  DarkGrey
#006400  DarkGreen
#BDB76B  DarkKhaki
#8B008B  DarkMagenta
#556B2F  DarkOliveGreen
#FF8C00  Darkorange
#9932CC  DarkOrchid
#8B0000  DarkRed
#E9967A  DarkSalmon
#8FBC8F  DarkSeaGreen
#483D8B  DarkSlateBlue
#2F4F4F  DarkSlateGray
#2F4F4F  DarkSlateGrey
#00CED1  DarkTurquoise
#9400D3  DarkViolet
#FF1493  DeepPink
#00BFFF  DeepSkyBlue
#696969  DimGray
#696969  DimGrey
#1E90FF  DodgerBlue
#B22222  FireBrick
#FFFAF0  FloralWhite
#228B22  ForestGreen
#FF00FF  Fuchsia
#DCDCDC  Gainsboro
#F8F8FF  GhostWhite
#FFD700  Gold
#DAA520  GoldenRod
#808080  Gray
#808080  Grey
#008000  Green
#ADFF2F  GreenYellow
#F0FFF0  HoneyDew
#FF69B4  HotPink
#CD5C5C  IndianRed
#4B0082  Indigo
#FFFFF0  Ivory
#F0E68C  Khaki
#E6E6FA  Lavender
#FFF0F5  LavenderBlush
#7CFC00  LawnGreen
#FFFACD  LemonChiffon
#ADD8E6  LightBlue
#F08080  LightCoral
#E0FFFF  LightCyan
#FAFAD2  LightGoldenRodYellow
#D3D3D3  LightGray
#D3D3D3  LightGrey
#90EE90  LightGreen
#FFB6C1  LightPink
#FFA07A  LightSalmon
#20B2AA  LightSeaGreen
#87CEFA  LightSkyBlue
#778899  LightSlateGray
#778899  LightSlateGrey
#B0C4DE  LightSteelBlue
#FFFFE0  LightYellow
#00FF00  Lime
#32CD32  LimeGreen
#FAF0E6  Linen
#FF00FF  Magenta
#800000  Maroon
#66CDAA  MediumAquaMarine
#0000CD  MediumBlue
#BA55D3  MediumOrchid
#9370D8  MediumPurple
#3CB371  MediumSeaGreen
#7B68EE  MediumSlateBlue
#00FA9A  MediumSpringGreen
#48D1CC  MediumTurquoise
#C71585  MediumVioletRed
#191970  MidnightBlue
#F5FFFA  MintCream
#FFE4E1  MistyRose
#FFE4B5  Moccasin
#FFDEAD  NavajoWhite
#000080  Navy
#FDF5E6  OldLace
#808000  Olive
#6B8E23  OliveDrab
#FFA500  Orange
#FF4500  OrangeRed
#DA70D6  Orchid
#EEE8AA  PaleGoldenRod
#98FB98  PaleGreen
#AFEEEE  PaleTurquoise
#D87093  PaleVioletRed
#FFEFD5  PapayaWhip
#FFDAB9  PeachPuff
#CD853F  Peru
#FFC0CB  Pink
#DDA0DD  Plum
#B0E0E6  PowderBlue
#800080  Purple
#FF0000  Red
#BC8F8F  RosyBrown
#4169E1  RoyalBlue
#8B4513  SaddleBrown
#FA8072  Salmon
#F4A460  SandyBrown
#2E8B57  SeaGreen
#FFF5EE  SeaShell
#A0522D  Sienna
#C0C0C0  Silver
#87CEEB  SkyBlue
#6A5ACD  SlateBlue
#708090  SlateGray
#708090  SlateGrey
#FFFAFA  Snow
#00FF7F  SpringGreen
#4682B4  SteelBlue
#D2B48C  Tan
#008080  Teal
#D8BFD8  Thistle
#FF6347  Tomato
#40E0D0  Turquoise
#EE82EE  Violet
#F5DEB3  Wheat
#FFFFFF  White
#F5F5F5  WhiteSmoke
#FFFF00  Yellow
#9ACD32  YellowGreen
```

Usted puede utilizar el "name" , en inglés, o el código.

Que tengas un buen día
Bruce

---

### Post by Bruce M. on 2009-09-14
Hay un nuevo **conkyForecast v2.09** por Conky 1.7.1 = **images!!**

[Conky Weather Forecast Python Script]("http://ubuntuforums.org/showthread.php?t=869328")

CHIMO!
Bruce

---

### Post by Mustaine666 on 2009-09-15
che muchisimas gracias bruce.. cuando termine el mio.. se los presento

---

### Post by Mustaine666 on 2009-09-15
Existe la forma de poner en el conky.. lo que estas escuchando en el Amarok? .. existe otro reproductor mas bueno?

---

### Post by ALEXEX on 2009-09-15
> **Bruce M. said:**
> Hay un nuevo **conkyForecast v2.09** por Conky 1.7.1 = **images!!**
 
[Conky Weather Forecast Python Script]("http://ubuntuforums.org/showthread.php?t=869328")
 
CHIMO!
Bruce
 
 
esta espectacular tu conky, te llevas mis respetos man :lolflag:

---

### Post by Mustaine666 on 2009-09-15
[SIZE=5][COLOR=Red]Me quedo horrible.. no me gusta como me quedo pero bueno.. [/COLOR][/SIZE]

```
use_xft yes
xftfont verdana:size=8
alignment top_right
xftalpha 0.8
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
stippled_borders 10
border_margin 4
border_width 1
default_shade_color grey
default_outline_color black
default_color White
use_spacer none
no_buffers yes
uppercase no
color1 F8DF58
override_utf8_locale yes
# Gap between borders of screen and text
gap_x 8
gap_y 15


TEXT

   ${font Sans:size=9:weight=bold} ${color #FF0000} TIEMPO ${hr 2} $color $font

   ${voffset -10}${alignr 56}${font ConkyWeather:style=Bold:size=40}${execi 600 conkyForecast --location=SPXX0015 --datatype=WF}${font}
   ${voffset -50}${font Weather:size=40}y${font}  ${voffset -20}${font Arial Black:size=26}${execi 600 conkyForecast --location=SPXX0015 --datatype=HT}${font}

${color #F5F5F5} ${font size=12} ${time %a, }   ${time %e %B %G}  $alignc $font
${color #FFFFFF} ${font size=12} ${time %Z,    } ${time %H:%M:%S}  $font


   ${font Sans:size=9:weight=bold} ${color #FF0000}  NET: (${addr eth1}) ${hr 2} $font
   ${color #FF0000}Up: ${color }${upspeed eth0} k/b
   ${upspeedgraph eth1 25,140 206900 3bc300}
   ${color #FF0000}Down: ${color }${downspeed eth1}k/b${color}
   ${downspeedgraph eth0 25,140 f1d900 d01800}
   ${color #FF0000} Upload: ${color}   $alignr${totalup eth1}
   ${color #FF0000} Download: ${color}    $alignr${totaldown eth1}

   
   ${font Sans:size=9:weight=bold}${color  #FF0000}Informacion del Sistema ${hr 2}$color${font Sans:size=8}
   ${color  #FF0000}Computer$color Ubuntu 9.04 ${alignr}${color  #FF0000} Uptime$color $uptime
   ${color  #FF0000}Kernel$color  $kernel ${alignr}${color  #FF0000}Arch.$color $machine
   ${color  white}${font StyleBats:size=16}A${font}  CPU: ${cpu cpu1}% ${alignr}${cpubar cpu1 8,60}${color}
   ${color  white}${font StyleBats:size=16}g${font}  RAM: $memperc%  $mem ${alignr}${membar 8,60}${color}
   ${color  white}${font Pie charts for maps:size=14}7${font}   ${voffset -5}Home:${color}
   ${color  white}${voffset 4}${alignc}${fs_free /home}/${fs_size /home} ${alignr}${fs_bar 8,60 /home}${color}
   ${color  white}${font StyleBats:size=16}j${font}  SWAP: $swapperc% ${alignr}${swapbar 8,60}${color}
   

   ${font Sans:size=9:weight=bold} ${color #FF0000}PROCESOS ${hr 2} $font
   ${color #FF0000}CPU $alignr PID CPU% MEM% $color
   ${top name 1}$alignr${top pid 1}${top cpu 1}${top mem 1}
   ${top name 2}$alignr${top pid 2}${top cpu 2}${top mem 2}
   ${top name 3}$alignr${top pid 3}${top cpu 3}${top mem 3}
 
   ${font Sans:size=9:weight=bold} ${color #FF0000}RAM $alignr PID CPU% MEM% $color $font
   ${top_mem name 1}$alignr${top_mem pid 1}${top_mem cpu 1}${top_mem mem 1}
   ${top_mem name 2}$alignr${top_mem pid 2}${top_mem cpu 2}${top_mem mem 2}
   ${top_mem name 3}$alignr${top_mem pid 3}${top_mem cpu 3}${top_mem mem 3}
  




```


[[img]http://a.imagehost.org/t/0961/Pantallazo.jpg[/img]](http://a.imagehost.org/view/0961/Pantallazo)


yo quiero hacer que aparezca lo q reproduzco en el amarok en el conky.. como hago?

---

### Post by matias_tati on 2009-09-15
> **Mustaine666 said:**
> [SIZE=5][COLOR=Red]Me quedo horrible.. no me gusta como me quedo pero bueno.. [/COLOR][/SIZE]

```
use_xft yes
xftfont verdana:size=8
alignment top_right
xftalpha 0.8
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
stippled_borders 10
border_margin 4
border_width 1
default_shade_color grey
default_outline_color black
default_color White
use_spacer none
no_buffers yes
uppercase no
color1 F8DF58
override_utf8_locale yes
# Gap between borders of screen and text
gap_x 8
gap_y 15


TEXT

   ${font Sans:size=9:weight=bold} ${color #FF0000} TIEMPO ${hr 2} $color $font

   ${voffset -10}${alignr 56}${font ConkyWeather:style=Bold:size=40}${execi 600 conkyForecast --location=SPXX0015 --datatype=WF}${font}
   ${voffset -50}${font Weather:size=40}y${font}  ${voffset -20}${font Arial Black:size=26}${execi 600 conkyForecast --location=SPXX0015 --datatype=HT}${font}

${color #F5F5F5} ${font size=12} ${time %a, }   ${time %e %B %G}  $alignc $font
${color #FFFFFF} ${font size=12} ${time %Z,    } ${time %H:%M:%S}  $font


   ${font Sans:size=9:weight=bold} ${color #FF0000}  NET: (${addr eth1}) ${hr 2} $font
   ${color #FF0000}Up: ${color }${upspeed eth0} k/b
   ${upspeedgraph eth1 25,140 206900 3bc300}
   ${color #FF0000}Down: ${color }${downspeed eth1}k/b${color}
   ${downspeedgraph eth0 25,140 f1d900 d01800}
   ${color #FF0000} Upload: ${color}   $alignr${totalup eth1}
   ${color #FF0000} Download: ${color}    $alignr${totaldown eth1}

   
   ${font Sans:size=9:weight=bold}${color  #FF0000}Informacion del Sistema ${hr 2}$color${font Sans:size=8}
   ${color  #FF0000}Computer$color Ubuntu 9.04 ${alignr}${color  #FF0000} Uptime$color $uptime
   ${color  #FF0000}Kernel$color  $kernel ${alignr}${color  #FF0000}Arch.$color $machine
   ${color  white}${font StyleBats:size=16}A${font}  CPU: ${cpu cpu1}% ${alignr}${cpubar cpu1 8,60}${color}
   ${color  white}${font StyleBats:size=16}g${font}  RAM: $memperc%  $mem ${alignr}${membar 8,60}${color}
   ${color  white}${font Pie charts for maps:size=14}7${font}   ${voffset -5}Home:${color}
   ${color  white}${voffset 4}${alignc}${fs_free /home}/${fs_size /home} ${alignr}${fs_bar 8,60 /home}${color}
   ${color  white}${font StyleBats:size=16}j${font}  SWAP: $swapperc% ${alignr}${swapbar 8,60}${color}
   

   ${font Sans:size=9:weight=bold} ${color #FF0000}PROCESOS ${hr 2} $font
   ${color #FF0000}CPU $alignr PID CPU% MEM% $color
   ${top name 1}$alignr${top pid 1}${top cpu 1}${top mem 1}
   ${top name 2}$alignr${top pid 2}${top cpu 2}${top mem 2}
   ${top name 3}$alignr${top pid 3}${top cpu 3}${top mem 3}
 
   ${font Sans:size=9:weight=bold} ${color #FF0000}RAM $alignr PID CPU% MEM% $color $font
   ${top_mem name 1}$alignr${top_mem pid 1}${top_mem cpu 1}${top_mem mem 1}
   ${top_mem name 2}$alignr${top_mem pid 2}${top_mem cpu 2}${top_mem mem 2}
   ${top_mem name 3}$alignr${top_mem pid 3}${top_mem cpu 3}${top_mem mem 3}
  




```


[[img]http://a.imagehost.org/t/0961/Pantallazo.jpg[/img]](http://a.imagehost.org/view/0961/Pantallazo)


yo quiero hacer que aparezca lo q reproduzco en el amarok en el conky.. como hago?

[http://facusdelacruz.wordpress.com/2008/06/18/script-para-conky-amarok/](http://facusdelacruz.wordpress.com/2008/06/18/script-para-conky-amarok/)
Y con respecto al reproductor yo uso Songbird creo que es muchisimo mejor y se adapta mejor a gnome. Saludos!!

---

### Post by Mustaine666 on 2009-09-15
gracias.. ahora voy a probar el songbird

---

### Post by Bruce M. on 2009-09-15
> **Mustaine666 said:**
> Existe la forma de poner en el conky.. lo que estas escuchando en el Amarok? .. existe otro reproductor mas bueno?

Hola Mustaine666

[Conky Exaile Python Script]("http://ubuntuforums.org/showthread.php?t=926041")

[Conky Rhythmbox Python Script]("http://ubuntuforums.org/showthread.php?t=928168")

y/o

[Conky Banshee Python Script]("http://ubuntuforums.org/showthread.php?p=7683570")

CHIMO!
Bruce

---

### Post by Bruce M. on 2009-09-15
> **ALEXEX said:**
> esta espectacular tu conky, te llevas mis respetos man :lolflag:

GRACIAS!

[Encuéntrelos aquí]("http://conky.linux-hardcore.com/?page_id=2487")

Es solamente [uno de cuatro]("http://conky.linux-hardcore.com/?page_id=2305").

Que tengas un buen día
Bruce

---

### Post by por100pre1 on 2009-09-16
> **Mustaine666 said:**
> [SIZE=5][COLOR=Red]Me quedo horrible.. no me gusta como me quedo pero bueno.. [/COLOR][/SIZE]
[[img]http://a.imagehost.org/t/0961/Pantallazo.jpg[/img]](http://a.imagehost.org/view/0961/Pantallazo)

Creo que te quedo muy bien...

---

### Post by Bruce M. on 2009-09-16
> **por100pre1 said:**
> creo que te quedo muy bien...

+1

---

### Post by guillermolisi on 2009-09-16
> **Mustaine666 said:**
> mal no me quedo pero es como que no estoy orgulloso..

otra cosa.. no pude instalar el songbird.. alguno me ayuda?
Mensaje totalmente Off Topic, va en thread aparte.

---

### Post by Mustaine666 on 2009-10-03
vamos a revivir un poco esto..necesitaria si alguien me ayuda a instalar este script

[http://ubuntuforums.org/showthread.php?p=6099901](http://ubuntuforums.org/showthread.php?p=6099901) 

que es pidgin en el conky .. como se hace? .. digamos que mucho no entiendo

---

### Post by cianca on 2009-10-03
Aca posteo el mio...

Conky1, arriba a la derecha...

```


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
own_window no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 283 134
maximum_width 283

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
default_color black
default_shade_color white
default_outline_color black

# own window options
own_window		yes
own_window_transparent	yes
own_window_type		override
own_window_hints	undecorated,below,sticky,skip_taskbar,skip_pager

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 
gap_y 24

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

TEXT
${image /home/cianca/.conky/DSTRY/mail-and-other-w.png -p 0,0 -s 283x134}${offset 98}${voffset 0}${font cure:size=6}${color #000000}Culture Is Your O.S.
${offset 9}${voffset -4}Userpanel
${offset 9}${voffset 12}${font cure:size=6}${color #000000}* Mail: ${color #00B7FF}${execi 300 python ~/.scripts/gmail.py}
${offset 9}${voffset 10}${font cure:size=6}${color #000000}* IP: ${color #00B7FF}${execi 180 wget -O - http://ip.tupeux.com | tail}
${offset 9}${voffset 10}${font cure:size=6}${color #000000}* CPU: ${color #00B7FF}${cpubar 3,100}  ${cpu}%
${offset 9}${voffset 10}${font cure:size=6}${color #000000}* Down: ${color #00B7FF}${downspeed eth0}KB/s ${color #000000}Up: ${color #00B7FF}${upspeed eth0}KB/s
${offset 35}${voffset 15}${font cure:size=6}${color #000000}$conky_build_arch
```


Y el de abajo a la izquierda...

```


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
own_window no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 284 60
maximum_width 284

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
default_color black
default_shade_color white
default_outline_color black

# own window options
own_window		yes
own_window_transparent	yes
own_window_type		override
own_window_hints	undecorated,below,sticky,skip_taskbar,skip_pager
window_type		desktop

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 0	
gap_y 0

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

#Para el arte de tapa de banshee
imlib_cache_size 15

TEXT
${image /home/cianca/.conky/DSTRY/music-w.png -p 0,13 -s 200x51}${offset 8}${voffset 14}${color #00B7FF}${font cure:size=6}Playing:${alignr 86}${execi 1 conkyBanshee  -m 10 --datatype=AL}
${offset 8}${voffset 15}${color #444444}${font cure:size=6}${execi 1 conkyBanshee -m 25 --datatype=AR} - ${execi 1 conkyBanshee --datatype=TI}
${execi 1 cp "`conkyBanshee --datatype=CA | sed -e 's/\\\//g'`" /home/cianca/.album/image.jpg}
${image /home/cianca/.album/image.jpg -p 200,13 -s 51x51}
${image /home/cianca/.conky/DSTRY/CA-w.png -p 131,13 }
```


[[IMG]http://img183.imageshack.us/img183/131/11009.th.png[/IMG]](http://img183.imageshack.us/i/11009.png/)


Si alguien quiere las imágenes, avisenme y las subo

---

### Post by Mustaine666 on 2009-10-03
tengo un problema.. no me andan los graficos de la coneccion de internet! .. 


[[img]http://a.imagehost.org/t/0891/proba.jpg[/img]](http://a.imagehost.org/view/0891/proba) 

... 

y este es el conky.. 

```
use_xft yes
xftfont verdana:size=8
alignment top_right
xftalpha 0.8
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
stippled_borders 10
border_margin 4
border_width 1
default_shade_color grey
default_outline_color black
default_color White
use_spacer none
no_buffers yes
uppercase no
color1 F8DF58
override_utf8_locale yes
# Gap between borders of screen and text
gap_x 8
gap_y 15


TEXT

   ${font Sans:size=9:weight=bold} ${color #FF0000} TIEMPO ${hr 2} $color $font

   ${voffset -10}${alignr 56}${font ConkyWeather:style=Bold:size=40}${execi 600 conkyForecast --location=SPXX0015 --datatype=WF}${font}
   ${voffset -50}${font Weather:size=40}y${font}  ${voffset -20}${font Arial Black:size=26}${execi 600 conkyForecast --location=SPXX0015 --datatype=HT}${font}

${color #F5F5F5} ${font size=12} ${time %a, }   ${time %e %B %G}  $alignc $font
${color #FFFFFF} ${font size=12} ${time %Z,    } ${time %H:%M:%S}  $font


   ${font Sans:size=9:weight=bold} ${color #FF0000}  NET: (${addr eth1}) ${hr 2} $font
   ${color #FF0000}Up: ${color }${upspeed eth1} k/b
   ${upspeedgraph eth1 25,140 206900 3bc300}
   ${color #FF0000}Down: ${color }${downspeed eth1}k/b${color}
   ${downspeedgraph eth1 25,140 f1d900 d01800}
   ${color #FF0000} Upload: ${color}   $alignr${totalup eth1}
   ${color #FF0000} Download: ${color}    $alignr${totaldown eth1}

   
   ${font Sans:size=9:weight=bold}${color  #FF0000}Informacion del Sistema ${hr 2}$color${font Sans:size=8}
   ${color  #FF0000}Computer$color Ubuntu 9.04 ${alignr}${color  #FF0000} Uptime$color $uptime
   ${color  #FF0000}Kernel$color  $kernel ${alignr}${color  #FF0000}Arch.$color $machine
   ${color  white}${font StyleBats:size=16}A${font}  CPU: ${cpu cpu1}% ${alignr}${cpubar cpu1 8,60}${color}
   ${color  white}${font StyleBats:size=16}g${font}  RAM: $memperc%  $mem ${alignr}${membar 8,60}${color}
   ${color  white}${font Pie charts for maps:size=14}7${font}   ${voffset -5}Home:${color}
   ${color  white}${voffset 4}${alignc}${fs_free /home}/${fs_size /home} ${alignr}${fs_bar 8,60 /home}${color}
   

   ${font Sans:size=9:weight=bold} ${color #FF0000}PROCESOS ${hr 2} $font
   ${color #FF0000}CPU $alignr PID CPU% MEM% $color
   ${top name 1}$alignr${top pid 1}${top cpu 1}${top mem 1}
   ${top name 2}$alignr${top pid 2}${top cpu 2}${top mem 2}
   ${top name 3}$alignr${top pid 3}${top cpu 3}${top mem 3}

  
```

---

### Post by Mustaine666 on 2009-10-03
> **cianca said:**
> Aca posteo el mio...

Conky1, arriba a la derecha...

```


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
own_window no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 283 134
maximum_width 283

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
default_color black
default_shade_color white
default_outline_color black

# own window options
own_window        yes
own_window_transparent    yes
own_window_type        override
own_window_hints    undecorated,below,sticky,skip_taskbar,skip_pager

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 
gap_y 24

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

TEXT
${image /home/cianca/.conky/DSTRY/mail-and-other-w.png -p 0,0 -s 283x134}${offset 98}${voffset 0}${font cure:size=6}${color #000000}Culture Is Your O.S.
${offset 9}${voffset -4}Userpanel
${offset 9}${voffset 12}${font cure:size=6}${color #000000}* Mail: ${color #00B7FF}${execi 300 python ~/.scripts/gmail.py}
${offset 9}${voffset 10}${font cure:size=6}${color #000000}* IP: ${color #00B7FF}${execi 180 wget -O - http://ip.tupeux.com | tail}
${offset 9}${voffset 10}${font cure:size=6}${color #000000}* CPU: ${color #00B7FF}${cpubar 3,100}  ${cpu}%
${offset 9}${voffset 10}${font cure:size=6}${color #000000}* Down: ${color #00B7FF}${downspeed eth0}KB/s ${color #000000}Up: ${color #00B7FF}${upspeed eth0}KB/s
${offset 35}${voffset 15}${font cure:size=6}${color #000000}$conky_build_arch
```
Y el de abajo a la izquierda...

```


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
own_window no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 284 60
maximum_width 284

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
default_color black
default_shade_color white
default_outline_color black

# own window options
own_window        yes
own_window_transparent    yes
own_window_type        override
own_window_hints    undecorated,below,sticky,skip_taskbar,skip_pager
window_type        desktop

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 0    
gap_y 0

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

#Para el arte de tapa de banshee
imlib_cache_size 15

TEXT
${image /home/cianca/.conky/DSTRY/music-w.png -p 0,13 -s 200x51}${offset 8}${voffset 14}${color #00B7FF}${font cure:size=6}Playing:${alignr 86}${execi 1 conkyBanshee  -m 10 --datatype=AL}
${offset 8}${voffset 15}${color #444444}${font cure:size=6}${execi 1 conkyBanshee -m 25 --datatype=AR} - ${execi 1 conkyBanshee --datatype=TI}
${execi 1 cp "`conkyBanshee --datatype=CA | sed -e 's/\\\//g'`" /home/cianca/.album/image.jpg}
${image /home/cianca/.album/image.jpg -p 200,13 -s 51x51}
${image /home/cianca/.conky/DSTRY/CA-w.png -p 131,13 }
```
[[IMG]http://img183.imageshack.us/img183/131/11009.th.png[/IMG]]("http://img183.imageshack.us/i/11009.png/")


Si alguien quiere las imágenes, avisenme y las subo


me gusta mucho tus conkys.. pero no los pude hacer andar! .. 

me gusta el fondo que tiene!

---

### Post by staar on 2009-10-03
OJO, para que ande conky con imágenes se necesita la última versión, no se cual tendrás instalada, si es la de los repos oficiales no anda, necesitás actualizarla...

saludos

---

### Post by cianca on 2009-10-03
> **Mustaine666 said:**
> me gusta mucho tus conkys.. pero no los pude hacer andar! .. 

me gusta el fondo que tiene!



Acá estan los fondos del conky, los ponés donde quieras y despues cambias las rutas en los archivos de conky, fijate que siempre que diga "/home/cianca/..." tenés que cambiarlo por /home/<tu usuario>/...
Lo de la música funciona con el banshee, debe ser fácil modificarlo para otros reproductores.
El script para los mails lo tenes que copiar a /home/<tu user>/.scripts, y ponerle los datos de tu cuenta.

Fijate si podes, si no, avisá!

Saludos


Edito: seguramente es lo que dice staar, yo soy nuevo en todo esto y es la única versión que use, no sabía que no funciona en las versiones anteriores.

---

### Post by guillermolisi on 2009-10-04
Los post que hablaban sobre la instalacion de Conky 1.7.2 y los problemas para exponer la interface de red correcta estan [aqui]("http://ubuntuforums.org/showthread.php?t=1282891")

---

### Post by matias_tati on 2009-10-24
Actualice a la version conky 1.7.2 y se comporta extraño en ralidad tengo estos inconvenientes. Se Refracta el wall y me aparece mas arriba asi que la primer linea la tapa el panel superior

use_xft yes
xftfont Liberation Sans:size=8

update_interval 1
total_run_times 0
double_buffer yes
text_buffer_size 2048

own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

minimum_size 182 0
maximum_width 182

default_color cccccc
draw_shades no

color0 white
color1 1D4C61
color2 white

alignment top_right
gap_x 25
gap_y 40

no_buffers no
net_avg_samples 2

override_utf8_locale yes

no_buffers yes

imlib_cache_size 0

TEXT
${font Liberation Sans:style=Bold:size=8}SISTEMA $stippled_hr${font}
${color0}${font Poky:size=15}S${font}${color}${goto 32}${voffset -8}Kernel:  ${alignr}${color2}${kernel}${color}
${goto 32}Actividad: ${alignr}${color2}${uptime}${color}
${offset 1}${color0}${font Poky:size=16}P${font}${offset -19}${voffset 9}${cpubar cpu0 4,18}${color}${voffset -15}${goto 32}CPU1: ${font Liberation Sans:style=Bold:size=8}${color1}${cpu cpu1}%${color}${font} ${alignr}${color2}${cpugraph cpu1 8,60 204A87 3465A4}${color}
${goto 32}CPU2: ${font Liberation Sans:style=Bold:size=8}${color1}${cpu cpu2}%${color}${font} ${alignr}${color2}${cpugraph cpu2 8,60 204A87 3465A4}${color}
${color0}${font Poky:size=16}M${font}${color}${goto 32}${voffset -7}RAM: ${font Liberation Sans:style=Bold:size=8}${color1}$memperc%${color}${font}
${offset 1}${voffset 3}${color2}${membar 4,18}${color}${goto 32}${voffset -4}U: ${color2}${mem}${color} F: ${color2}${memeasyfree}${color}
${voffset 2}${color0}${font Poky:size=15}a${font}${color}${goto 32}${voffset -10}Procesos: ${color2}${alignr 13}CPU${alignr}RAM${color}
${voffset -1}${goto 42}${color2}${top name 1}${color}${font Liberation Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 1}${alignr }${top mem 1}${color}${font}
${voffset -1}${goto 42}${color2}${top name 2}${color}${font Liberation Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 2}${alignr }${top mem 2}${color}${font}
${voffset -1}${goto 42}${color2}${top name 3}${color}${font Liberation Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 3}${alignr }${top mem 3}${color}${font}
${voffset 2}${color0}${font Poky:size=14}s${font}${color}${voffset -8}${goto 32}SWAP: ${font Liberation Sans:style=Bold:size=8}${color1}${swapperc}%${color}${font}
${voffset 4}${offset 1}${color2}${swapbar 4,18}${color}${voffset -4}${goto 32}F: ${color2}$swapmax${color} U: ${color2}$swap${color}
${voffset 4}${font Liberation Sans:style=Bold:size=8}FECHA $stippled_hr${font}
${voffset 10}${alignc 55}${font aClock:style=_Hour:size=90}${color2}${execi 120 python ~/.conky/conkyClock_h.py}${color}${font}
${voffset -98}${alignc 55}${font aClock:style=_Min:size=90}${color2}${execi 60 python ~/.conky/conkyClock_m.py}${color}${font}
${voffset 12}${alignc}${font Liberation Sans:style=Bold:size=10}${color1}${time %H:%M}${color}${font}${voffset -8}
${voffset 4}${color0}${font Poky:size=13}d${font}${color}${voffset -4}${font Liberation Mono:size=8}${execpi 10800 DJS=`date +%_d`; cal | sed 's/^/${alignc} /' | sed s/" $DJS "/" "'${font Liberation Mono:style=bold:size=8}${color1}'"$DJS"'${color}${font}${font Liberation Mono:size=8}'" "/}${font}${font}
${voffset 4}${font Liberation Sans:style=Bold:size=8}HD $stippled_hr${font}
${execpi 30 ~/.conky/hd_default.py}
${voffset 4}${font Liberation Sans:style=Bold:size=8}RED $stippled_hr${font}
${if_existing /proc/net/route wlan0}
${voffset -13}${color0}${font VariShapes Solid:size=14}q${font}${color}${goto 32}${voffset -6}Envío: ${font Liberation Sans:style=Bold:size=8}${color1}${upspeed wlan0}${color}${font} ${alignr}${color2}${upspeedgraph wlan0 8,60 204A87 3465A4}${color}
${goto 32}Total: ${color2}${totalup wlan0}${color}
${voffset -2}${color0}${font VariShapes Solid:size=14}Q${font}${color}${goto 32}${voffset -6}Recibo: ${font Liberation Sans:style=Bold:size=8}${color1}${downspeed wlan0}${color}${font} ${alignr}${color2}${downspeedgraph wlan0 8,60 204A87 3465A4}${color}
${goto 32}Total: ${color2}${totaldown wlan0}${color}
${voffset -2}${color0}${font Poky:size=14}Y${font}${color}${goto 32} ${voffset -2}Señal: ${font Liberation Sans:style=Bold:size=8}${color1}${wireless_link_qual wlan0}%${color}${font} ${alignr}${color2}${wireless_link_bar 8,60 wlan0}${color}
${voffset 4}${color0}${font Poky:size=13}w${font}${color}${goto 32}${voffset -8}Ip Local: ${alignr}${color2}${addr wlan0}${color}
${goto 32}Ip Pública: ${alignr}${color2}${execi 10800 ~/.conky/ip.sh}${color}
${else}${if_existing /proc/net/route eth0}
${voffset -13}${color0}${font VariShapes Solid:size=14}q${font}${color}${goto 32}${voffset -6}Envío: ${font Liberation Sans:style=Bold:size=8}${color1}${upspeed eth0}${color}${font} ${alignr}${color2}${upspeedgraph eth0 8,60 204A87 3465A4}${color}
${goto 32}Total: ${color2}${totalup eth0}${color}
${voffset -2}${color0}${font VariShapes Solid:size=14}Q${font}${color}${goto 32}${voffset -6}Recibo: ${font Liberation Sans:style=Bold:size=8}${color1}${downspeed eth0}${color}${font} ${alignr}${color2}${downspeedgraph eth0 8,60 204A87 3465A4}${color}
${goto 32}Total: ${color2}${totaldown eth0}${color}
${voffset -2}${color0}${font Poky:size=13}w${font}${color}${goto 32}${voffset -4}Ip Local: ${alignr}${color2}${addr eth0}${color}
${goto 32}Ip Pública: ${alignr}${color2}${execi 10800 ~/.conky/ip.sh}${color}
${endif}${else}${if_existing /proc/net/route ppp0}
${voffset -13}${color0}${font VariShapes Solid:size=14}q${font}${color}${goto 32}${voffset -6}Envío: ${font Liberation Sans:style=Bold:size=8}${color1}${upspeed ppp0}${color}${font} ${alignr}${color2}${upspeedgraph ppp0 8,60 204A87 3465A4}${color}
${goto 32}Total: ${color2}${totalup ppp0}${color}
${voffset -2}${color0}${font VariShapes Solid:size=14}Q${font}${color}${goto 32}${voffset -6}Recibo: ${font Liberation Sans:style=Bold:size=8}${color1}${downspeed ppp0}${color}${font} ${alignr}${color2}${downspeedgraph ppp0 8,60 204A87 3465A4}${color}
${goto 32}Total: ${color2}${totaldown ppp0}${color}
${voffset -2}${color0}${font Poky:size=13}w${font}${color}${goto 32}${voffset -4}Ip Local: ${alignr}${color2}${addr ppp0}${color}
${endif}${else}${voffset 4}${color0}${font PizzaDude Bullets:size=12}4${font}${color}${goto 32}Red no disponible${endif}${endif}
${voffset -8}${font Liberation Sans:style=Bold:size=8}CLIMA $stippled_hr${font}
${if_existing /proc/net/route wlan0}
${execpi 10800 ~/.conky/conkyForecast.py --location=ARBA0034 -t ~/.conky/conkyForecast.template}
${else}${if_existing /proc/net/route eth0}
${execpi 10800 ~/.conky/conkyForecast.py --location=ARBA0034 -t ~/.conky/conkyForecast.template}
${endif}${else}${if_existing /proc/net/route ppp0}
${execpi 10800 ~/.conky/conkyForecast.py --location=ARBA0034 -t ~/.conky/conkyForecast.template}
${endif}${else}${voffset 4}${color0}${font PizzaDude Bullets:size=12}4${font}${color}${goto 32}Clima no disponible${endif}${endif}

Gracias...

---

### Post by Bruce M. on 2009-10-24
> **matias_tati said:**
> Actualice a la version conky 1.7.2 y se comporta extraño en ralidad tengo estos inconvenientes. Se Refracta el wall y me aparece mas arriba asi que la primer linea la tapa el panel superior

Hola matias,

Probar:
**own_window [SIZE="5"][COLOR="DarkRed"]no[/COLOR][/SIZE]**

Tenes:
```
no_buffers no <<-- porque "no" aca
net_avg_samples 2

override_utf8_locale yes

no_buffers yes <<-- ¿y "si" aca?
```

mejor = "yes"

Que tengas un buen día!
Bruce

---

### Post by matias_tati on 2009-10-24
> **Bruce M. said:**
> Hola matias,

Probar:
**own_window [SIZE="5"][COLOR="DarkRed"]no[/COLOR][/SIZE]**

Tenes:
```
no_buffers no <<-- porque "no" aca
net_avg_samples 2

override_utf8_locale yes

no_buffers yes <<-- ¿y "si" aca?
```

mejor = "yes"

Que tengas un buen día!
Bruce

No funciono. Gracias.

---

### Post by matias_tati on 2009-10-26
Agradeceria un poco de ayuda. Saludos!

---

### Post by Bruce M. on 2009-10-26
> **matias_tati said:**
> No funciono. Gracias.

Hmmmmmm... Tenía el mismo problema - que lo fijó.

dame 2 horas de máximo. (17:03 ahora)

---

### Post by Bruce M. on 2009-10-26
> **matias_tati said:**
> Agradeceria un poco de ayuda. Saludos!

Hola Matias,

Dos cosas:

**1.** **Linea 50:** ***${colo r}*** = ***${color}***

**2:** Compiz?

Remove the shadow by adding
Quite la sombra agregando
```
(any) & !(name=Conky)
```
under window decoration in compiz settings manager
bajo "window decoration" en "compiz settings manager"

CHIMO!
Bruce

---

### Post by matias_tati on 2009-10-27
Claro pero mi problema no es la sombra del conky eso ya lo habia solucionado, sino que el wallpaper se refracta algo asi como cuando metes una cuchara dentrao de un vaso con agua y lo miras de afuera. 
Quizas con otra captura quede mas claro:

Si intentan seguir la linea del pasto azul justo a la altura del conky tiene un corrimiento.

[[img]http://a.imagehost.org/t/0841/Pantallazo.jpg[/img]](http://a.imagehost.org/view/0841/Pantallazo)

---

### Post by Bruce M. on 2009-10-27
> **matias_tati said:**
> Claro pero mi problema no es la sombra del conky eso ya lo habia solucionado, sino que el wallpaper se refracta algo asi como cuando metes una cuchara dentrao de un vaso con agua y lo miras de afuera. 
Quizas con otra captura quede mas claro:

Si intentan seguir la linea del pasto azul justo a la altura del conky tiene un corrimiento.

Si, lo mismo problema que yo y lo fijé con:

```
background no
own_window no
# own_window_type override
# own_window_transparent yes
# own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
# own_window_class conky
```

Conky está dibujando un fondo, de que es porqué usted ve la línea.

Espero que esto ayude.

Que tengas un buen día.
Bruce

---

### Post by Bruce M. on 2009-10-27
Tengo un conky nuevo - como siempre!

Todo los archivos estan [aca]("http://conky.linux-hardcore.com/?page_id=3459").

Que tengas un buen día.
Bruce

---

### Post by matias_tati on 2009-10-27
La cura fue peor que la enfermedad.

[[img]http://a.imagehost.org/t/0734/Pantallazo.jpg[/img]](http://a.imagehost.org/view/0734/Pantallazo)

use_xft yes
xftfont Liberation Sans:size=8

update_interval 1
total_run_times 0
double_buffer yes
text_buffer_size 2048

background no
own_window no
# own_window_type override
# own_window_transparent yes
# own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
# own_window_class conky

minimum_size 182 0
maximum_width 182

default_color cccccc
draw_shades no

color0 white
color1 3465A4
color2 white

alignment top_right
gap_x 25
gap_y 40

no_buffers no
net_avg_samples 2

override_utf8_locale yes

no_buffers yes

imlib_cache_size 0

TEXT
${font Liberation Sans:style=Bold:size=8}SISTEMA $stippled_hr${font}
${color0}${font Poky:size=15}S${font}${color}${goto 32}${voffset -8}Kernel:  ${alignr}${color2}${kernel}${color}
${goto 32}Actividad: ${alignr}${color2}${uptime}${color}
${offset 1}${color0}${font Poky:size=16}P${font}${offset -19}${voffset 9}${cpubar cpu0 4,18}${color}${voffset -15}${goto 32}CPU1: ${font Liberation Sans:style=Bold:size=8}${color1}${cpu cpu1}%${color}${font} ${alignr}${color2}${cpugraph cpu1 8,60 204A87 3465A4}${color}
${goto 32}CPU2: ${font Liberation Sans:style=Bold:size=8}${color1}${cpu cpu2}%${color}${font} ${alignr}${color2}${cpugraph cpu2 8,60 204A87 3465A4}${color}
${color0}${font Poky:size=16}M${font}${color}${goto 32}${voffset -7}RAM: ${font Liberation Sans:style=Bold:size=8}${color1}$memperc%${color}${font}
${offset 1}${voffset 3}${color2}${membar 4,18}${color}${goto 32}${voffset -4}U: ${color2}${mem}${color} F: ${color2}${memeasyfree}${color}
${voffset 2}${color0}${font Poky:size=15}a${font}${color}${goto 32}${voffset -10}Procesos: ${color2}${alignr 13}CPU${alignr}RAM${color}
${voffset -1}${goto 42}${color2}${top name 1}${color}${font Liberation Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 1}${alignr }${top mem 1}${color}${font}
${voffset -1}${goto 42}${color2}${top name 2}${color}${font Liberation Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 2}${alignr }${top mem 2}${color}${font}
${voffset -1}${goto 42}${color2}${top name 3}${color}${font Liberation Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 3}${alignr }${top mem 3}${color}${font}
${voffset -1}${goto 42}${color2}${top name 4}${color}${font Liberation Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 4}${alignr }${top mem 4}${color}${font}
${voffset 4}${font Liberation Sans:style=Bold:size=8}FECHA $stippled_hr${font}
${voffset 10}${alignc 55}${font aClock:style=_Hour:size=90}${color2}${execi 120 python ~/.conky/conkyClock_h.py}${color}${font}
${voffset -98}${alignc 55}${font aClock:style=_Min:size=90}${color2}${execi 60 python ~/.conky/conkyClock_m.py}${color}${font}
${voffset 12}${alignc}${font Liberation Sans:style=Bold:size=10}${color1}${time %H:%M}${color}${font}${voffset -8}
${voffset 4}${color0}${font Poky:size=13}d${font}${color}${voffset -4}${font Liberation Mono:size=8}${execpi 10800 DJS=`date +%_d`; cal | sed 's/^/${alignc} /' | sed s/" $DJS "/" "'${font Liberation Mono:style=bold:size=8}${color1}'"$DJS"'${color}${font}${font Liberation Mono:size=8}'" "/}${font}${font}
${voffset 4}${font Liberation Sans:style=Bold:size=8}HD $stippled_hr${font}
${execpi 30 ~/.conky/hd_default.py}
${voffset 4}${font Liberation Sans:style=Bold:size=8}RED $stippled_hr${font}
${if_existing /proc/net/route wlan0}
${voffset -13}${color0}${font VariShapes Solid:size=14}q${font}${color}${goto 32}${voffset -6}Envío: ${font Liberation Sans:style=Bold:size=8}${color1}${upspeed wlan0}${color}${font} ${alignr}${color2}${upspeedgraph wlan0 8,60 204A87 3465A4}${color}
${goto 32}Total: ${color2}${totalup wlan0}${color}
${voffset -2}${color0}${font VariShapes Solid:size=14}Q${font}${color}${goto 32}${voffset -6}Recibo: ${font Liberation Sans:style=Bold:size=8}${color1}${downspeed wlan0}${color}${font} ${alignr}${color2}${downspeedgraph wlan0 8,60 204A87 3465A4}${color}
${goto 32}Total: ${color2}${totaldown wlan0}${color}
${voffset -2}${color0}${font Poky:size=14}Y${font}${color}${goto 32} ${voffset -2}Señal: ${font Liberation Sans:style=Bold:size=8}${color1}${wireless_link_qual wlan0}%${color}${font} ${alignr}${color2}${wireless_link_bar 8,60 wlan0}${color}
${voffset 4}${color0}${font Poky:size=13}w${font}${color}${goto 32}${voffset -8}Ip Local: ${alignr}${color2}${addr wlan0}${color}
${goto 32}Ip Pública: ${alignr}${color2}${execi 10800 ~/.conky/ip.sh}${color}
${else}${if_existing /proc/net/route eth0}
${voffset -13}${color0}${font VariShapes Solid:size=14}q${font}${color}${goto 32}${voffset -6}Envío: ${font Liberation Sans:style=Bold:size=8}${color1}${upspeed eth0}${color}${font} ${alignr}${color2}${upspeedgraph eth0 8,60 204A87 3465A4}${color}
${goto 32}Total: ${color2}${totalup eth0}${color}
${voffset -2}${color0}${font VariShapes Solid:size=14}Q${font}${color}${goto 32}${voffset -6}Recibo: ${font Liberation Sans:style=Bold:size=8}${color1}${downspeed eth0}${color}${font} ${alignr}${color2}${downspeedgraph eth0 8,60 204A87 3465A4}${color}
${goto 32}Total: ${color2}${totaldown eth0}${color}
${voffset -2}${color0}${font Poky:size=13}w${font}${color}${goto 32}${voffset -4}Ip Local: ${alignr}${color2}${addr eth0}${color}
${goto 32}Ip Pública: ${alignr}${color2}${execi 10800 ~/.conky/ip.sh}${color}
${endif}${else}${if_existing /proc/net/route ppp0}
${voffset -13}${color0}${font VariShapes Solid:size=14}q${font}${color}${goto 32}${voffset -6}Envío: ${font Liberation Sans:style=Bold:size=8}${color1}${upspeed ppp0}${color}${font} ${alignr}${color2}${upspeedgraph ppp0 8,60 204A87 3465A4}${color}
${goto 32}Total: ${color2}${totalup ppp0}${color}
${voffset -2}${color0}${font VariShapes Solid:size=14}Q${font}${color}${goto 32}${voffset -6}Recibo: ${font Liberation Sans:style=Bold:size=8}${color1}${downspeed ppp0}${color}${font} ${alignr}${color2}${downspeedgraph ppp0 8,60 204A87 3465A4}${color}
${goto 32}Total: ${color2}${totaldown ppp0}${color}
${voffset -2}${color0}${font Poky:size=13}w${font}${color}${goto 32}${voffset -4}Ip Local: ${alignr}${color2}${addr ppp0}${color}
${endif}${else}${voffset 4}${color0}${font PizzaDude Bullets:size=12}4${font}${color}${goto 32}Red no disponible${endif}${endif}
${voffset -8}${font Liberation Sans:style=Bold:size=8}CLIMA $stippled_hr${font}
${if_existing /proc/net/route wlan0}
${execpi 10800 ~/.conky/conkyForecast.py --location=ARBA0034 -t ~/.conky/conkyForecast.template}
${else}${if_existing /proc/net/route eth0}
${execpi 10800 ~/.conky/conkyForecast.py --location=ARBA0034 -t ~/.conky/conkyForecast.template}
${endif}${else}${if_existing /proc/net/route ppp0}
${execpi 10800 ~/.conky/conkyForecast.py --location=ARBA0034 -t ~/.conky/conkyForecast.template}
${endif}${else}${voffset 4}${color0}${font PizzaDude Bullets:size=12}4${font}${color}${goto 32}Clima no disponible${endif}${endif}

---

### Post by Bruce M. on 2009-10-27
> **matias_tati said:**
> La cura fue peor que la enfermedad.

Oh NO!!!!

Probar este:
Estoy usando JJ sin "composite" sin compiz

```
background no
own_window no
# own_window_type override
# own_window_transparent yes
# own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
# own_window_class conky
use_xft yes
#xftfont DejaVu Sans Mono:bold:size=8
xftfont Liberation Sans:size=8
xftalpha 1.0
override_utf8_locale yes
update_interval 1
total_run_times 0
double_buffer yes
no_buffers yes
cpu_avg_samples 2
net_avg_samples 2
use_spacer none
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
alignment tr
uppercase no
imlib_cache_size 0
# minimum_size 1280 1024 # minimum_size width & height
gap_x 25 # left-right
gap_y 40 # up-down
border_inner_margin 0
border_outer_margin 0

# Colors
#default_color DCDCDC #Gainsboro
#color0 FFD700 #Gold  #7FFFD4 #Aquamarine
#color1 FFA07A #LightSalmon
#color2 FF8C00 #Darkorange

color0 white
color1 3465A4
color2 white

color3 7FFF00 #Chartreuse
color4 778899 #LightSlateGrey
color5 FFDEAD #NavajoWhite
color6 00BFFF #DeepSkyBlue
#	colours below used by colorize script
color7 48D1CC #MediumTurquoise
color8 FFFF00 #Yellow
color9 FF0000 #Red
text_buffer_size 6144 # 256 is the minimum
short_units yes
pad_percents 2

imlib_cache_size 0

# WARNING: Change name and passwords on e-mail code if posting!!

# — Lua Load — #
lua_load ~/Conky/scripts/clock_lua.lua
lua_draw_hook_pre clock_rings


TEXT
```

Esto es lo que utilizo - y anda muy bien

---

### Post by guillermolisi on 2009-10-31
Seleccione los ultimos posts porque ya se habian ido del tema del thread, asi que con ellos abri [uno nuevo]("http://ubuntuforums.org/showthread.php?t=1308500") en la seccion software.

---

### Post by santiagoward2000 on 2009-11-08
Hola gente!
Desde que actualice a Karmic me dejo de andar el Adesklets SystemMonitor, y como no tenia ganas de ponerme a ver por que, me puse a tratar de imitarlo con Conky. Tuve que hacer un par de scripts para las barritas (8 para las barras y otros 8 para que cambien de color en caso de que un parametro suba mucho). Es la primera vez que hago algo asi, por lo que seguramente les hace falta una pulida, pero quede bastante contento con el resultado. Igual, si alguno se anima a usarlos, seguramente van a tener que cambiar algo (sobre todo en los downspeed y upspeed, que son muy improvisados).
Adjunto un tar con los scripts, el **.conkyrc** y todas las imagenes que usa para las barritas, fondo e iconos.
Saludos!

_EDIT:_
Si alguien lo bajo y probo mis scripts, seguro se dio cuenta que era complicadisimo ajustarles la posicion, ya que se desarmaba todo. Estuve trabajando en eso, y creo que logre arreglarlo un poco (ahora solo hay que cambiar los valores de **x** e **y** en cada script, pero sigue siendo medio complicado ajustar despues el texto que va abajo). Ademas, se me dio por juntar las barritas de memoria y swap en mi conkyrc. Adjunto las modificaciones.
Saludos de nuevo!

_OTRO EDIT MAS:_
Estuve jugando con esto un poco mas, y le agregue a los scripts de downspeed y upseed una parte que calcula la velocidad maxima de la conexion. Ya no hay que cambiarla manualmente en cada script, solo dejarlo correr un rato mientras estan conectados. El unico problema es que, en caso de de cambiar la conexion por una mas lenta, hay que resetear los archivos **maxdown** y **maxup** manualmente, volviendo el valor a **1**, para que vuelva a calcularla (tengo un script armado que hace esto, pero no se como hacer para que se corra automaticamente cada vez que se conecta a una red).
Ya me canse de saludar :D

---

### Post by sitodonosti on 2009-12-18
Hola, a ver si me podeis ayudar. Encontré un script para poner google calendar en conky, la cosa es que no se muy bien como fundiona, me aparece solo la información dle tiempo que tengo. Pongo de de dónde saqué el script, ademas quiero poner dos conkys diferentes y eso nose como hacer, me podeis ayudar¿
La direccion es esta: [http://ubuntuforums.org/showthread.php?t=837385](http://ubuntuforums.org/showthread.php?t=837385)

me baje todo pero nose como hacerlo funcionar una ayudita por favor?

gracias y un saludo

---

### Post by Bruce M. on 2009-12-18
> **sitodonosti said:**
> Hola, a ver si me podeis ayudar. Encontré un script para poner google calendar en conky, la cosa es que no se muy bien como fundiona, me aparece solo la información dle tiempo que tengo. Pongo de de dónde saqué el script, ademas quiero poner dos conkys diferentes y eso nose como hacer, me podeis ayudar¿
La direccion es esta: [http://ubuntuforums.org/showthread.php?t=837385](http://ubuntuforums.org/showthread.php?t=837385)

me baje todo pero nose como hacerlo funcionar una ayudita por favor?

gracias y un saludo

${execi 1800 conkyGoogleCalendar ...options...} y los opciones: [http://conky.linux-hardcore.com/?page_id=853](http://conky.linux-hardcore.com/?page_id=853) - en ingles.

Y para dos conkys:

```
#!/bin/sh
# click to start, click to stop
 
if pidof conky | grep [0-9] > /dev/null
then
exec killall conky
else
sleep 30  # sleep not required for xfce on startup - 30 or more for others
conky -c ~/Conky/conkymain &amp;
conky -c ~/Conky/conkytext &amp;
exit
fi
```

*~/Conky/conkymain* = **/home/user/path/to/conky_file**

Bruce

---

### Post by sitodonosti on 2009-12-18
hola bruce he conseguido que vaya este conky gracias, pero sigo teniendo problemas, por así llamarlos, el caso esque solo me aparecen dos notas que tengo en google calendar cuando en el día de hoy tengo unas 7 o así...
Además nose como hacer para agrandar hacia abajo la ventana estado mirando en conky pero nose realmente cual es... :$

En cuanto a los dos conky's como hago eso, osea creo por ejemplo conky_main, pero los diferentes conkys cómo los llamo?dónde los guardo?Cómo hago para que funcione?

un saludo y gracias

PD: Agrego una foto de como se ve y así a ver si me explico con lo que kiero decir de agrandar hacia abajo jiijji

Pongo dos fotos una es el conky que tengo y la otra el google calendar que son las dos que quiero juntar en el conky_main

---

### Post by Bruce M. on 2009-12-18
Hola sitodonosti

Tenes dos conkys ahora, ¿cómo se llaman y dónde están?

¿conky_main? = ~/conky/conky_main si o no?
y el otro?

Mostrar los archivos de conky y "templates". Quitar la información  personal: correo electrónico "contraseñas", etc, etc

Hay muchas maneras de comenzar dos conkys. Esto es lo que uso:
Crear:
~/Conky
y
~/Conky/scripts

Poner los dos archivos de conky en ~/Conky commo:
~/Conky/el_tiempo
~/Conky/google_cal

y en ~/Conky/scripts este archivo: **ssc.sh**
```
#!/bin/sh
# click to start, click to stop
if pidof conky | grep [0-9] > /dev/null
then
  exec killall conky
else

sleep 30  # sleep no se requiere para el arranque de Xfce - 30 o más para los demás
conky -c ~/Conky/el_tiempo &
conky -c ~/Conky/google_cal &
  exit
fi
```
y hacerlo ejecutable - en la terminal
```
cd Conky/scripts
sudo chmod +x ssc.sh
```

Ahora poner **ssc.sh** en "autostart" y crear un "launcher" (icono en el "panel") por **ssc.sh**

Bruce

---

### Post by sartrejp on 2009-12-19
descubrí cairo-dock (seguro que ya todos lo conocía), pero me encantó y me pude deshacer de los paneles, por lo que decidí colocar conky en forma horizontal. El resultado es el siguiente:

---

### Post by sitodonosti on 2009-12-24
Hola Bruce ya siento no haber contestado antes, pero estado ocupado con trabajos en la universidad y presentaciones y demás. Gracias por la ayuda ya he conseguido lo de los dons conkys. En cuanto al de google calendar esto es lo que me has pedido:
conky:
# conky configuration
# edited by kaivalagi

# set to yes if you want Conky to be forked in the background
background no

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono:size=9

# Text alpha when using Xft
xftalpha 0.8

# Update interval in seconds
update_interval 5.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 300 
maximum_width 500

# Draw shades?
draw_shades yes

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
border_width 1

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
#alignment top_left
# maintain spacing between certain elements
use_spacer right

# set to yes if you want tormo to be forked in the background
#background yes

use_xft yes

# Xft font when Xft is enabled
#xftfont Vera-8
#xftfont Andale Mono-8
#xftfont Clean-8
#xftfont cubicfive10:pixelsize=8
xftfont Sans-Serif:size=9:pixelsize=11
#xftfont swf!t_v02:pixelsize=11

# Text alpha when using Xft
xftalpha 1
#mail_spool $MAIL

#own_window_hints below

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 400
gap_y 575

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no
override_utf8_locale yes
TEXT
${color blue}C${color red}A${color yellow}L${color blue}E${color green}N${color blue}D${color red}A${color yellow}R
${color1}${font}${execpi 1800 conkyGoogleCalendar --username=sito.otis@googlemail.com --password=72497521 --daysahead=7 --limit=10 --template=/usr/share/conkygooglecalendar/example/conkyGoogleCalendar.template}

Template(/usr/share/conkygooglecalendar/example):
${color3}Title: ${color1}[title]
${color3}Start Time: ${color1}[starttime]
#${color3}End Time: ${color1}[endtime]
#${color3}Location: ${color1}[location]
#${color3}Description: ${color1}[description]
#${color3}Who: ${color1}[who]

conkyGoogleCalendar.py(/usr/share/conkygooglecalendar):
#!/usr/bin/python
# -*- coding: utf-8 -*-
###############################################################################
# conkyGoogleCalendar.py is a simple python script to output google calendar
# event details in conky.
#
# Author: Kaivalagi
# Created: 22/06/2008
# Modifications:
#    22/06/2008    Modified to sort events earliest starttime first
#    23/06/2008    Modified to only display current events (--daysahead option) that start after now
#    23/06/2008    Added --indent option to add spaces to the front of each line that is output (excludes template output)
#    24/06/2008    Added who is attending (email addresses) to the output of each event, added a <who> parameter for the template, and added a --nowho option to hide the data (excludes template output)
#    24/06/2008    Fixed up template output using regex, to remove unnecessary blank lines where no data exists
#    19/07/2008    Output "No Events..." if non found, rather than nothing at all.
#    19/07/2008    Fix for all day events where time is shown. Catered for 12:00:00 AM (%r formatted time) so it is no longer displayed.
#    21/07/2008    Updated date time formatting, datetime now formatted using Day + locale.D_FMT + locale.T_FMT_AMPM, date only uses Day + locale.D_FMT. In my locale this results in the format "15/02/2007 13:00:00 pm", for US users the day and month will be switched :)
#    02/07/2008    Added --dateformat option. If used this overrides the default date formatting. The values to use are standard formatting strings e.g. Weekday=%a, Day=%d, Month=%m, Year=%y. For an output like "Thu 15/10/2008" you would require --dateformat="%a %d/%m/%y", to have no date you would require --dateformat=""
#    03/08/2008    Updated the restriction of text width to include location and who as well as description, also renamed MAX_DESCRIPTION_LENGTH to be called MAX_WIDTH
#    25/08/2008    Events now get ignored when their end date is not effective anymore, rather than the start date
#    25/08/2008    Changed default for --daysahead from 1 to 7, and up'ed the default for the end date parameter of date ranged output, now up to the year 2020
#    26/08/2008    Updated the template handling code to cope better with missing data
#    05/09/2008    Refactored code and added better info and error logging
#    05/09/2008    Added regex removal of trailing email address on who list, so "someone@abc.net" becomes "someone"
#    05/09/2008    Added --connectiontimeout option, default timeout of 10 seconds when not set
#    05/09/2008    Added further error handling for gdata orientated functions
#    08/09/2008    Changed default time format locale used for output, now 24hr clock based to hopefully support all language locales
#    08/09/2008    Added timeformat option to allow changing the default time formatting of output, this does no support a blank setting
#    02/10/2008    Updated script to remove the whole line from a template based output where no data is available for the required output, this will mean all template output should be on new lines, but enables conky based formatting in the template when using execp or execpi
#    06/10/2008    Updated script to work properly without a template, now --nowho option works
#    13/10/2008    Updated script to bring back event data for ALL calendars available, not just the default one
#    13/10/2008    Added --requestCalendarNames option to pick and choose which calendars event data should be returned, e.g. --requestCalendarNames="cal1;cal2;other cal". If not set all calendar events are returned
#    27/10/2008    Updated to require a deliberate new line in any custom template for blank line separators between event output, so that output can have no blank lines if required. Templates may require updating!
#    04/11/2008    Added utf-8 encoding to output
#    10/11/2008    Added --errorlog and --infolog options to log data to a file
#    15/11/2008    Now loading the template file in unicode mode to allow for the extended character set
#    18/11/2008    Changed option tags from <...> to [...], so <title> now needs to be [title] in the template to work
#    06/01/2009    Removed .encode("utf-8") from internal return to fix unicode output?...it works...
#    01/03/2009    Exposed width setting for line lengths, --maxwidth will set maximum lengths for output lines (default 40 as before)
#    15/04/2009    Updated to handle overridden calendar names when using the --requestCalendarNames option to limit output
#    16/04/2009    Removed excess imports statements
#    16/04/2009    Changed the default connection timeout from 10 to 30 seconds
#    16/04/2009    Calendars detailed in the --requestCalendarNames option now HAVE to match the exact name (not case sensitive though)
#                  e.g. -r "Diary" will no longer mean a calendar called "SchoolDiary" is output, to output it -r "SchoolDiary" is necessary.
#    18/05/2009    Updated to expand ~ based template paths
#    27/06/2009    Updated to make safe the output, replacing "${exec" text with "$e!noexec!", to stop unwanted conky execution

from datetime import datetime, date, timedelta
from optparse import OptionParser
from xml.dom import minidom
import socket
import gdata.calendar.service
import sys
import locale
import re
import textwrap
import urllib
import codecs
import traceback
import os

class CalendarData:

    def __init__(self, title):
        self.title = title

class CalendarEventData:

    def __init__(self, title, starttime, endtime, location, description, who=None):
        self.title = title
        self.starttime = starttime
        self.endtime = endtime
        self.location = location
        self.description = description
        self.who = who

    def __cmp__(self, other):
        return cmp(self.starttime, other.starttime)

    def __str__(self):
        return str(self.starttime)

class CommandLineParser:

    parser = None

    def __init__(self):

        self.parser = OptionParser()
        self.parser.add_option("-u","--username", dest="username", type="string", metavar="USERNAME", help=u"Username for login into Google Calendar, this will normally be your gmail account")
        self.parser.add_option("-p","--password",dest="password", type="string", metavar="PASSWORD", help=u"Password for login")
        self.parser.add_option("-r","--requestCalendarNames",dest="requestedCalendars", type="string", metavar="TEXT", help=u"Define a list of calendars to request event data for, calendar names should be separated by semi-colons \";\". For example --requestCalendarNames=\"cal1;cal2;other cal\" If not set all calendar data will be returned.")
        self.parser.add_option("-d","--daysahead",dest="daysahead", default=7, type="int", metavar="NUMBER", help=u"[default: %default] Define the number of days ahead you wish to retrieve calendar entries for, starting from today.")
        self.parser.add_option("-s","--startdate",dest="startdate", type="string", metavar="DATE", help=u"Define the start date to retrieve calendar events. In the form '2007-12-01'")
        self.parser.add_option("-e","--enddate",dest="enddate", type="string", metavar="DATE", help=u"Define the end date to retrieve calendar events, must be supplied if --startdate supplied. In the form '2007-12-01'")
        self.parser.add_option("-a","--allevents",dest="allevents", default=False, action="store_true", help=u"Retrieve all calendar events")
        self.parser.add_option("-w","--wordsearch",dest="wordsearch", type="string", metavar="TEXT", help=u"Define the text to search calendar entries with.")
        self.parser.add_option("-l","--limit",dest="limit", default=0, type="int", metavar="NUMBER", help=u"[default: %default] Define the maximum number of calendar events to display, zero means no limit.")
        self.parser.add_option("-t","--template",dest="template", type="string", metavar="FILE", help=u"Template file determining the format for each event. Use the following placeholders: [title], [starttime], [endtime], [location], [description], [who]. Ensure only one placeholder per line, as the whole line is removed if no data for that placeholder exists.")
        self.parser.add_option("-f","--dateformat",dest="dateformat", default=None, type="string", metavar="\"DATEFORMAT\"", help=u"If used this overrides the default date formatting. The values to use are standard formatting strings e.g. Weekday=%a, Day=%d, Month=%m, Year=%y. For an output like \"Thu 15/10/2008\" you would require --dateformat=\"%a %d/%m/%y\", to have no date you would require --dateformat=\"\"")
        self.parser.add_option("-F","--timeformat",dest="timeformat", default=None, type="string", metavar="\"TIMEFORMAT\"", help=u"If used this overrides the default time formatting. The values to use are standard formatting strings e.g. Hours (12hr)=%l, Hours (24hr)=%H, Minutes=%M, Seconds=%S, AM/PM=%P. For an output like \"05:22 PM\" you would require --timeformat=\"%l:%M %P\", --timeformat=\"\" is not supported, default locale settings are used")
        self.parser.add_option("-i","--indent",dest="indent", default=0, type="int", metavar="NUMBER", help=u"[default: %default] Define the number of spaces to indent the output (excludes template based output)")
        self.parser.add_option("-m","--maxwidth",dest="maxwidth", default=40, type="int", metavar="NUMBER", help=u"[default: %default] Define the number of characters to output per line")
        self.parser.add_option("-n","--nowho",dest="nowho", default=False, action="store_true", help=u"Hides who is attending the events (excludes template based output)")
        self.parser.add_option("-c","--connectiontimeout",dest="connectiontimeout", type="int", default=30, metavar="NUMBER", help=u"[default: %default] Define the number of seconds before a connection timeout can occur.")
        self.parser.add_option("-v","--verbose",dest="verbose", default=False, action="store_true", help=u"Request verbose output, no a good idea when running through conky!")
        self.parser.add_option("-V", "--version", dest="version", default=False, action="store_true", help=u"Displays the version of the script.")
        self.parser.add_option("--errorlogfile", dest="errorlogfile", type="string", metavar="FILE", help=u"If a filepath is set, the script appends errors to the filepath.")
        self.parser.add_option("--infologfile", dest="infologfile", type="string", metavar="FILE", help=u"If a filepath is set, the script appends info to the filepath.")

    def parse_args(self):
        (options, args) = self.parser.parse_args()
        return (options, args)

    def print_help(self):
        return self.parser.print_help()

class GoogleCalendarInfo:

    dateformat=""
    timeformat=""
    options = None

    requestedCalendars = []
    requiredCalendars = []
    feedPrefix    = 'http://www.google.com/calendar/feeds/'
    ACCESS_ALL         = 'all'      # non-google access level
    ACCESS_DEFAULT     = 'default'  # non-google access level
    ACCESS_NONE        = 'none'
    ACCESS_OWNER       = 'owner'
    ACCESS_EDITOR      = 'editor'
    ACCESS_CONTRIBUTOR = 'contributor'
    ACCESS_READ        = 'read'
    ACCESS_FREEBUSY    = 'freebusy'

    ################ GOOGLE CALENDAR FUNCTIONS ################################
    def __init__(self, options):

        try:
            # store options for use throughout the class
            self.options = options

            self.logInfo("Initialising google calendar connection...")

            socket.setdefaulttimeout(self.options.connectiontimeout)

            self.cal_client = gdata.calendar.service.CalendarService()
            self.cal_client.email = self.options.username
            self.cal_client.password = self.options.password
            self.cal_client.source = 'conkyGoogleCalendar'
            self.cal_client.ProgrammaticLogin()

            # load the format for date and time to use
            self.getDatetimeFormat(self.options.dateformat, self.options.timeformat)

            # prepare calendar list to use for event retrieval
            self.getCalendarList()

        except Exception,e:
            self.logError("GoogleCalendarEngine Initialisation:Unexpected error:" + traceback.format_exc())

    def getCalendarList(self):

        self.logInfo("Preparing google calendar list...")

        # prepare calendar list to retrieve
        if self.options.requestedCalendars != None:
            self.requestedCalendars = self.options.requestedCalendars.split(";")

        # get the list of calendars from google
        calendars = self.cal_client.GetAllCalendarsFeed()

        order = { self.ACCESS_OWNER       : 1,
                  self.ACCESS_EDITOR      : 2,
                  self.ACCESS_CONTRIBUTOR : 3,
                  self.ACCESS_READ        : 4,
                  self.ACCESS_FREEBUSY    : 5,
                  self.ACCESS_NONE        : 6 }

        calendars.entry.sort(lambda x, y:
                                cmp(order[x.access_level.value],
                                    order[y.access_level.value]))

        # clear the list
        self.requiredCalendars = []

        for cal in calendars.entry:

            cal.gcalcli_altLink = cal.GetAlternateLink().href
            match = re.match('^' + self.feedPrefix + '(.*?)/(.*?)/(.*)$',cal.gcalcli_altLink)
            cal.username    = urllib.unquote(match.group(1))
            cal.visibility  = urllib.unquote(match.group(2))
            cal.projection  = urllib.unquote(match.group(3))

            if len(self.requestedCalendars):

                # get the calendar name, updating it if an override is found
                calendarName = cal.title.text
                doc = minidom.parseString(str(cal))
                overrideName = doc.getElementsByTagNameNS(u'http://schemas.google.com/gCal/2005', 'overridename')
                if len(overrideName) > 0:
                    calendarName = overrideName[0].getAttribute("value")

                for rc in self.requestedCalendars:
                    if rc.lower() == calendarName.lower():
                        self.requiredCalendars.append(cal)
            else:
                self.requiredCalendars.append(cal)


    def getOwnedCalendars(self):

        try:

            self.logInfo("Fetching owned calendars...")

            feed = self.cal_client.GetOwnCalendarsFeed()

            calendarDataList = []

            for mycalendar in zip(xrange(len(feed.entry)), feed.entry):
                calendarData = CalendarData(mycalendar.title.text)
                calendarDataList.append(calendarData)

            return calendarDataList

        except Exception,e:
            self.logError("getOwnedCalendars:Unexpected error:" + traceback.format_exc())
            return []

    def getAllEvents(self):

        try:

            self.logInfo("Fetching all event data...")

            calendarDataEventList = []

            for cal in self.requiredCalendars:
                query = gdata.calendar.service.CalendarEventQuery(cal.username, cal.visibility, cal.projection)
                feed = self.cal_client.CalendarQuery(query)
                now = datetime.now()
                for i, event in zip(xrange(len(feed.entry)), feed.entry):
                    for j, when in zip(xrange(len(event.when)), event.when):
                        for k, where in zip(xrange(len(event.where)), event.where):
                            # if the event's end time is after now then add it!
                            if self.getDateFromWhen(when.end_time) > now:
                                whoList = []
                                for l, who in zip(xrange(len(event.who)), event.who):
                                    whoList.append(who.email)
                                if len(whoList) == 0:
                                    whoList = None
                                calendarDataEvent = CalendarEventData(event.title.text, when.start_time, when.end_time, where.value_string, event.content.text, whoList)
                                calendarDataEventList.append(calendarDataEvent)

            return calendarDataEventList

        except Exception,e:
            self.logError("getAllEvents:Unexpected error:" + traceback.format_exc())
            return []

    def getTextQueryEvents(self, text_query='Project'):

        try:

            self.logInfo("Fetching text queried event data using text query of \"%s\"..."%text_query)

            calendarDataEventList = []

            for cal in self.requiredCalendars:

                query = gdata.calendar.service.CalendarEventQuery(cal.username, cal.visibility, cal.projection, text_query)
                query.orderby = 'starttime'
                query.singleevents = 'true'
                feed = self.cal_client.CalendarQuery(query)
                now = datetime.now()
                for i, event in zip(xrange(len(feed.entry)), feed.entry):
                    for j, when in zip(xrange(len(event.when)), event.when):
                        for k, where in zip(xrange(len(event.where)), event.where):
                            # if the event's end time is after now then add it!
                            if self.getDateFromWhen(when.end_time) > now:
                                whoList = []
                                for l, who in zip(xrange(len(event.who)), event.who):
                                    whoList.append(who.email)
                                if len(whoList) == 0:
                                    whoList = None
                                calendarDataEvent = CalendarEventData(event.title.text, when.start_time, when.end_time, where.value_string, event.content.text, whoList)
                                calendarDataEventList.append(calendarDataEvent)

            return calendarDataEventList

        except Exception,e:
            self.logError("getTextQueryEvents:Unexpected error:" + traceback.format_exc())
            return []

    def getDateRangedEvents(self, start_date='2007-01-01', end_date='2020-01-01'):

        try:

            self.logInfo("Fetching date ranged event data for dates between %s and %s..."%(start_date,end_date))

            calendarDataEventList = []

            for cal in self.requiredCalendars:

                query = gdata.calendar.service.CalendarEventQuery(cal.username, cal.visibility, cal.projection)
                query.start_min = start_date
                query.start_max = end_date
                query.orderby = 'starttime'
                query.singleevents = 'true'
                feed = self.cal_client.CalendarQuery(query)
                for i, event in zip(xrange(len(feed.entry)), feed.entry):
                    for j, when in zip(xrange(len(event.when)), event.when):
                        for k, where in zip(xrange(len(event.where)), event.where):
                            whoList = []
                            for l, who in zip(xrange(len(event.who)), event.who):
                                whoList.append(who.email)
                            if len(whoList) == 0:
                                whoList = None
                            calendarDataEvent = CalendarEventData(event.title.text, when.start_time, when.end_time, where.value_string, event.content.text, whoList)
                            calendarDataEventList.append(calendarDataEvent)

            return calendarDataEventList

        except Exception,e:
            self.logError("getDateRangedEvents:Unexpected error:" + traceback.format_exc())
            return []

    def getFutureEvents(self, days_ahead=7):

        try:

            self.logInfo("Fetching future event data, for the next %s days..."%days_ahead)

            calendarDataEventList = []

            for cal in self.requiredCalendars:

                query = gdata.calendar.service.CalendarEventQuery(cal.username, cal.visibility, cal.projection)
                query.start_min = str(date.today())
                query.start_max = str(date.today()+timedelta(days=days_ahead))
                query.orderby = 'starttime'
                query.singleevents = 'true'
                feed = self.cal_client.CalendarQuery(query)
                now = datetime.now()
                for i, event in zip(xrange(len(feed.entry)), feed.entry):
                    for j, when in zip(xrange(len(event.when)), event.when):
                        for k, where in zip(xrange(len(event.where)), event.where):
                            # if the event's end time is after now then add it!
                            if self.getDateFromWhen(when.end_time) > now:
                                whoList = []
                                for l, who in zip(xrange(len(event.who)), event.who):
                                    whoList.append(who.email)
                                if len(whoList) == 0:
                                    whoList = None
                                calendarDataEvent = CalendarEventData(event.title.text, when.start_time, when.end_time, where.value_string, event.content.text, whoList)
                                calendarDataEventList.append(calendarDataEvent)

            return calendarDataEventList

        except Exception,e:
            self.logError("getFutureEvents:Unexpected error:" + traceback.format_exc())
            return []

    def getOutputFromTemplate(self, template, title, starttime, endtime, location, description, who):

        try:

            output = template

            if title == None or title.strip() == "":
                output = self.removeLineByString(output,"[title]")
            else:
                output = output.replace("[title]",title)

            if location == None or location.strip() == "":
                output = self.removeLineByString(output,"[location]")
            else:
                output = output.replace("[location]",location)

            if description == None or description.strip() == "":
                output = self.removeLineByString(output,"[description]")
            else:
                output = output.replace("[description]",description)

            if who == None or who.strip() == "":
                output = self.removeLineByString(output,"[who]")
            else:
                #output = output.replace("[who]",";".join(who))
                output = output.replace("[who]",who)

            output = output.replace("[starttime]",starttime)
            output = output.replace("[endtime]",endtime)

            # get rid of any excess crlf's and add just one
            #output = output.rstrip(" \n")
            #output = output + "\n"

            return output

        except Exception,e:
            self.logError("getOutputFromTemplate:Unexpected error:" + traceback.format_exc())
            return ""

    def getDatetimeFormat(self,dateformat=None,timeformat=None):

        try:

            # get locale defaults for output
            locale.setlocale(locale.LC_ALL,'')

            # format date based on format setting
            if dateformat == None:
                self.dateformat = "%a "+locale.nl_langinfo(locale.D_FMT)
            elif dateformat == "":
                self.dateformat = ""
            else:
                self.dateformat = dateformat

            # format time based on format setting
            if timeformat == None or timeformat == "":
                self.timeformat = locale.nl_langinfo(locale.T_FMT)
            else:
                self.timeformat = timeformat

        except Exception,e:
            self.logError("getDatetimeFormat:Unexpected error:" + traceback.format_exc())

    def getDateFromWhen(self,when, stringformat=False):

        try:

            # is this a datetime or just date field
            if len(when) > 10:
                dateandtime = True
            else:
                dateandtime = False

            # convert to datetime field
            if dateandtime == True:
                whendatetime = datetime.strptime(when[0:19], "%Y-%m-%dT%H:%M:%S")
            else:
                whendatetime = datetime.strptime(when[0:10], "%Y-%m-%d")

            # if string formatting required, format to a string using locale
            if stringformat == True:
                if dateandtime == True:
                    if self.dateformat == "":
                        whendatetime = whendatetime.strftime(self.timeformat)
                    else:
                        whendatetime = whendatetime.strftime(self.dateformat + " " + self.timeformat)
                else:
                    if self.dateformat == "": # if no formating but only required to show date we need then revert to default!
                        whendatetime = whendatetime.strftime(locale.nl_langinfo(locale.D_FMT))
                    else:
                        whendatetime = whendatetime.strftime(self.dateformat)

                # remove excess space between date and time if necessary
                whendatetime = whendatetime.replace("  "," ")

            return whendatetime

        except Exception,e:
            self.logError("getDateFromWhen:Unexpected error:" + traceback.format_exc)

    def writeOutput(self):

        try:

            ################ GOOGLE CALENDAR DATA RETRIEVAL #########################

            # determine the required query and run it
            if self.options.wordsearch != None:
                calendarEventDataList = self.getTextQueryEvents(self.options.wordsearch)
            elif self.options.startdate != None:
                if self.options.enddate != None:
                    calendarEventDataList = self.getDateRangedEvents(self.options.startdate,self.options.enddate)
                else:
                    print >> sys.stdout, "--startdate provided with no --enddate."
                    self.parser.print_help()
            elif self.options.allevents == True:
                calendarEventDataList = self.getAllEvents()
            else:
                calendarEventDataList = self.getFutureEvents(self.options.daysahead)

            ################ PREPARE FOR OUTPUT ##############################

            self.logInfo("Processing output...")

            if self.options.template == None:
                # get the indent spacing sorted out
                if self.options.indent > 0:
                    indent = self.getSpaces(self.options.indent)
                else:
                    indent = ""

                # create default template
                template = indent+"Title: [title]\n" + indent + "Start Time: [starttime]\n" + indent + "End Time: [endtime]\n" + indent + "Location: [location]\n" + indent + "Description: [description]\n" + indent + "Who: [who]\n"
            else:
                # load the template file contents
                try:
                    fileinput = codecs.open(os.path.expanduser(self.options.template), encoding='utf-8')
                    template = fileinput.read()
                    fileinput.close()
                    # lose the final "\n" which should always be there...
                    template = template[0:len(template)-1]
                except:
                    self.logError("Template file no found!")
                    sys.exit(2)

            ################ PROCESS OUTPUT #########################################
            calendarEventCount = 0
            calendarEventDataList.sort()

            if len(calendarEventDataList) > 0:
                # walk through the calendar events
                for calendarEventData in calendarEventDataList:

                    # keep a tally of events output, if past the limit then exit
                    if self.options.limit <> 0:
                        calendarEventCount = calendarEventCount+1
                        if calendarEventCount > self.options.limit:
                            sys.exit()

                    # collect calendar event data and format as we go
                    title = calendarEventData.title
                    starttime = self.getDateFromWhen(calendarEventData.starttime, True)
                    endtime = self.getDateFromWhen(calendarEventData.endtime, True)

                    location = calendarEventData.location
                    if location <> None:
                        #location = self.getWrappedText(location, self.options.maxwidth, indent)
                        if len(location) > self.options.maxwidth:
                            location = location[0:self.options.maxwidth].replace("\n","")+"..."

                    description = calendarEventData.description
                    if description <> None:
                        #description = self.getWrappedText(description, self.options.maxwidth, indent)
                        if len(description) > self.options.maxwidth:
                            description = description[0:self.options.maxwidth].replace("\n","")+"..."

                    who = calendarEventData.who
                    if who != None:
                        if self.options.nowho == True:
                            who = None
                        else:
                            who = ";".join(who)+";"
                            who = re.sub("@.*?;",", ",who).rstrip(", ")
                            if len(who) > self.options.maxwidth:
                                who = who[0:self.options.maxwidth]+"..."
                                #who = ";".join(who).replace(";",", ")
                                #who = self.getWrappedText(who, self.options.maxwidth, indent)

                    # output event data using the template
                    output = self.getOutputFromTemplate(template, title, starttime, endtime, location, description, who)

                    output = self.getMadeSafeOutput(output)
                    print output #.encode("utf-8")

            else:
                print "No Events..."

        except Exception,e:
            self.logError("writeOutput:Unexpected error:" + traceback.format_exc())

    def removeLineByString(self,lines,string):

        # define list from multiple lines, to allow remove function
        lineslist = lines.split("\n")
        lineslistchanged = False

        for line in lineslist:
            if line.find(string) <> -1:
                lineslist.remove(line)
                lineslistchanged = True
                break

        if lineslistchanged == True:
            # rebuild lines string from updated list
            lines = "\n".join(lineslist)

        return lines

    def getSpaces(self,spaces):
        string = ""
        for i in range(0, spaces+1):
            string = string + " "
        return string

    def getWrappedText(self,text,width=40,indent=0):
        if len(text) > width:
            indentspace = "".ljust(indent)
            wrappedtext=""
            for line in textwrap.wrap(text,width=(width-indent),expand_tabs=False,replace_whitespace=False):
                wrappedtext = wrappedtext + line + "\n" + indentspace
            return wrappedtext.rstrip("\n ")
        else:
            return text

    def logInfo(self, text):
        if self.options.verbose == True:
            print >> sys.stdout, "INFO: " + text

        if self.options.infologfile != None:
            datetimestamp = datetime.now().strftime("%Y-%m-%d %H:%M:%S")
            fileoutput = open(self.options.infologfile, "ab")
            fileoutput.write(datetimestamp+" INFO: "+text+"\n")
            fileoutput.close()

    def logError(self, text):
        print >> sys.stderr, "ERROR: " + text

        if self.options.errorlogfile != None:
            datetimestamp = datetime.now().strftime("%Y-%m-%d %H:%M:%S")
            fileoutput = open(self.options.errorlogfile, "ab")
            fileoutput.write(datetimestamp+" ERROR: "+text+"\n")
            fileoutput.close()

    def getMadeSafeOutput(self, text):
        return text.replace("${exec","${!noexec!")

def main():
    """Runs the conkyGoogleCalendar application with the provided username and
    and password values.  Authentication credentials are required."""

    ################ COMMAND LINE ARGUMENTS #################################
    parser = CommandLineParser()
    (options, args) = parser.parse_args()

    if options.version == True:

        print >> sys.stdout,"conkyGoogleCalendar v.2.06"

    else:

        if options.username == None or options.password == None:
            print >> sys.stdout, "A username and/or password was not given!"
            sys.exit(2)

        if options.verbose == True:
            print >> sys.stdout, "*** INITIAL OPTIONS:"
            print >> sys.stdout, "    username:",options.username
            print >> sys.stdout, "    password:",options.password
            print >> sys.stdout, "    daysahead:",options.daysahead
            print >> sys.stdout, "    startdate:",options.startdate
            print >> sys.stdout, "    enddate:",options.enddate
            print >> sys.stdout, "    allevents:",options.allevents
            print >> sys.stdout, "    wordsearch:",options.wordsearch
            print >> sys.stdout, "    limit:",options.limit
            print >> sys.stdout, "    template:",options.template
            print >> sys.stdout, "    dateformat:",options.dateformat
            print >> sys.stdout, "    indent:",options.indent
            print >> sys.stdout, "    nowho:",options.nowho
            print >> sys.stdout, "    verbose:",options.verbose
            print >> sys.stdout, "    errorlogfile:",options.errorlogfile
            print >> sys.stdout, "    infologfile:",options.infologfile

        googlecalendarinfo = GoogleCalendarInfo(options)
        googlecalendarinfo.writeOutput()

if __name__ == '__main__':
    main()
    sys.exit()


Esto es lo que he creido que puede ser lo mas importante hay una archivo mas conkyGoogleCalendar.pyc
Necesitas algo más?
Ahora a ver si consigo que que el title y start vayan mas para arriba ji

un saludo[ATTACH]141029[/ATTACH]

---

### Post by leonardomdq on 2009-12-25
Mi conky con algunas cosas que pulir, por ejemplo la temperatura es lo unico que no pude hacer funcionar...alguna idea?

**.conkyrc**

> 
use_xft yes
xftfont verdana:size=8
alignment top_right
xftalpha 0.8
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
stippled_borders 10
border_margin 4
border_width 1
default_shade_color grey
default_outline_color black
default_color BADCDD
use_spacer none
no_buffers yes
uppercase no
color1 F8DF58



TEXT
 ${color 6694B2}${font OpenLogos:size=45} u t
${color BADCDD}${font weather:size=82}${execi 600 ~/scripts/conditions.sh}${color}${font}${voffset -25}  ${execi 1200 ~/scripts/pogodynka.sh}

   ${font weather:size=28}x ${font}HDD ${execi 1 ~/scripts/hddmonit.sh}°C 
    
   ${font PizzaDude Bullets:size=16}v${font}   Up: ${upspeed eth0} Kb/s 
   ${font PizzaDude Bullets:size=16}r${font}   Down: ${downspeed eth0} Kb/s 

   ${font PizzaDude Bullets:size=16}M${font}   Upload: ${totalup eth0}
   ${font PizzaDude Bullets:size=16}S${font}   Download: ${totaldown eth0}

   ${color ffffff}${font StyleBats:size=16}A${font}  CPU0: ${cpu cpu0}% ${cpubar cpu0}
   ${font StyleBats:size=16}A${font}  CPU1: ${cpu cpu1}% ${cpubar cpu1}

   ${color F8DF58}${font StyleBats:size=16}8${font}  Battery: ${battery_percent}% ${battery_bar}

   ${color F8DF58}${font FreeSans:size=16}@${font}${execpi 300 python ~/scripts/gmail_parser.py [EMAIL="leo.mdp@gmail.com"]leo.mdp@gmail.com[/EMAIL] (mi contraseña) 3}

   ${color C2E078}${font PizzaDude Bullets:size=16}J${font}   $mem / $memmax

   ${font StyleBats:size=18}P${font}  Work:  ${uptime_short}


 ${font Radio Space:size=14}${time %A %d %Y}
      ${font Radio Space:size=55}${time %H:%M}

**script** **pogodynka.sh**

> 
# # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # #
# #
# Pogodynka 0.2.2.1 #
# #
# azhag (azhag@bsd.miki.eu.org) #
# #
# # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # #
# #
# Skrypt pobiera informacje o stanie pogody ze strony weather.yahoo.com dla danego miasta, nastêpnie formatuje je i #
# wy¶wietla na ekranie. Skrypt mo¿e byæ wykorzystany np. w conky'm, xosd, *message. #
# #
# # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # #
# #
# Wymagane aplikacje: #
# w3m - tekstowa przegl±darka www #
# #
# # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # #
# #
# Przed u¿yciem skryptu nale¿y ustaliæ zmienne "sciezka" oraz "kod". #
# #
# Aby ustaliæ kod swojego miasta wejd¿ na stronê [http://weather.yahoo.com/](http://weather.yahoo.com/) i wyszukaj tam swoje miasto. Kodem jest #
# koñcówka linka z pogod± naszego miasta. #
# #
# Przyk³adowe kody: #
# Warszawa - PLXX0028 #
# Kraków - PLXX0012 #
# Gdañsk - PLXX0005 #
# Szczecin - PLXX0025 #
# #
# Informacjê jak± wy¶wietla skrypt mo¿na zmieniæ haszuj±c odpowiednie linijki w sekcji "formatowanie informacji #
# wyj¶ciowej". Mo¿na równie¿ w ³atwy sposób sformatowaæ w³asny wynik u¿ywaj±c dostepnych zmiennych. #
# #
# # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # #

#!/bin/bash

# Katalog, w którym znajduje siê skrypt
sciezka=~/scripts

# Kod miasta
kod=ARBA0054

plik=~/weather
# sprawdzenie czy serwer jest dostêpny
#if [ `ping -c1 216.109.126.70 | grep from | wc -l` -eq 0 ]
# then
#echo "Serwis niedostêpny"
#else
# pobieranie informacji
w3m -dump http://weather.yahoo.com/forecast/"$kod"_c.html | grep -A21 "Current" | sed 's/DEG/°/g' > $plik

# ustalenie warto¶ci zmiennych
stan=`head -n3 $plik | tail -n1`
temp=`tail -n1 $plik | awk '{print $1}'`
tempo=`head -n6 $plik | tail -n1`
cisn=`head -n8 $plik | tail -n1`
wiatr=`head -n16 $plik | tail -n1`
wilg=`head -n10 $plik | tail -n1`
wsch=`head -n18 $plik | tail -n1`
zach=`head -n20 $plik | tail -n1`
if [ `cat "$sciezka"/pogodynka.sh | grep -x "# $stan" | wc -l` -eq 0 ]
then
stanpl=$stan
else
stanpl=`cat "$sciezka"/pogodynka.sh | grep -xA1 "# $stan" | tail -n1 | awk '{print $2,$3,$4,$5,$6,$7}'`
fi

# formatowanie informacji wyj¶ciowej
# dostêpne zmienne:
# $stan opis stanu po angielsku
# $stanpl opis stanu po polsku
# $temp temperatura powietrza
# $tempo temperatura odczuwalna
# $cisn ci¶nienie atmosferyczne
# $wiatr kierunek, si³a wiatru
# $wilg wilgotno¶æ powietrza
# $wsch godzina wschodu s³oñca
# $zach godzina zachodu s³oñca

#echo $stan
#echo $stanpl
echo $temp C / $tempo C
#echo Cisnienie $cisn hPa
#echo $wiatr
#echo Wilgotno¶æ: $wilg
#echo Wschód S³oñca: $wsch
#echo Zachód S³oñca: $zach
#echo $stanpl, $temp C

#fi

# # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # #
#
# T³umaczenia stanów pogody.
# Je¿eli zauwa¿ysz pogodê, której nie ma jeszcze na liscie daj mi znaæ na maila podanego na górze. Z góry dziêkujê.
#
# Sunny
# S³onecznie
# Clear
# Przejrzy¶cie
# Fair
# Pogodnie
# Sunny/Windy
# S³onecznie/Wiatr
# Clear/Windy
# Przejrzy¶cie/Wiatr
# Fair/Windy
# Przejrzy¶cie/Wiatr
# Windy
# Wiatr
#
# Partly Cloudy
# Czê¶ciowo pochmurnie
# Partly Cloudy and Windy
# Czê¶ciowo pochmurnie/Wiatr
# Partly Sunny
# Czê¶ciowo s³onecznie
# Mostly Clear
# Przew. przejrzy¶cie
# Partly Sunny/Windy
# Czê¶ciowo s³onecznie/Wiatr
# Mostly Clear/Windy
# Przew. przejrzy¶cie/Wiatr
# Mostly Sunny
# Przew. p³onecznie
# Mostly Sunny/Windy
# Przew. s³onecznie/Wiatr
# Scattered Clouds
# Rzadkie ob³oki
#
# Cloudy
# Pochmurnie
# Overcast
# Ca³k. zachmurzenie
# Cloudy/Windy
# Pochmurnie/Wiatr
# Overcast/Windy
# Ca³k. zachmurzenie/Wiatr
# Mostly Cloudy/Windy
# Przew. pochmurnie/Wiatr
# Mostly Cloudy
# Przew. pochmurnie
# Am Clouds / Pm Sun
# Ranek pochmurny/S³oneczne popo³udnie
#
# Light Drizzle
# Lekka m¿awka
# Drizzle
# M¿awka
# Light Rain
# Lekki deszcz
# Rain
# Deszcz
# Heavy Rain
# Ulewa
# Light Rain/Fog
# Lekki deszcz/Mg³a
# Rain/Fog
# Deszcz/Mg³a
# Light Drizzle/Windy
# Lekka m¿awka/Wiatr
# Drizzle/Windy
# M¿awka/Wiatr
# Light Rain/Windy
# Lekki deszcz/Wiatr
# Rain/Windy
# Deszcz/Wiatr
# Rain / Wind
# Deszcz/Wiatr
# Heavy Rain/Windy
# Ulewa/Wiatr
# AM Light Rain
# Ranny lekki deszcz
# PM Light Rain
# Popo³udniowy lekki deszcz
# Pm Light Rain
# Popo³udniowy lekki deszcz
# AM Light Rain/Windy
# Ranny lekki deszcz/Wiatr
# PM Light Rain/Windy
# Popo³udniowy lekki deszcz/Wiatr
#
# Rain Shower
# Przelotny deszcz
# Shower
# Przelotna ulewa
# Showers
# Przelotna ulewa
# Heavy Rain Shower
# Mocna ulewa
# Heavy Rain Shower/Windy
# Mocna ulewa/Wiatr
# Light Rain Shower
# Lekka ulewa
# AM Shower
# Poranna ulewa
# AM Showers
# Poranna ulewa
# Am Showers
# Poranna ulewa
# AM Showers / Wind
# Poranna ulewa/Wiatr
# PM Shower
# Popo³udniowa ulewa
# PM Showers / Wind
# Popo³udniowe ulewy/Wiatr
# Few Showers / Wind
# Przelotne deszcze/Wiatr
# Showers / Wind
# Deszcze/Wiatr
# PM Showers
# Popo³udniowe ulewy
# Pm Showers
# Popo³udniowe ulewy
# Scattered Shower
# Rozleg³a ulewa
# Scattered Showers
# Rozleg³e ulewy
# Scatter Showers
# Rozleg³e ulewy
# Rain Shower/Windy
# Przelotny deszcz/Wiatr
# Shower/Windy
# Przelotna ulewa/Wiatr
# Light Rain Shower/Windy
# Lekka ulewa/Wiatr
# AM Shower/Windy
# Poranna ulewa/Wiatr
# PM Shower/Windy
# Popo³udniowa ulewa/Wiatr
# Scattered Shower/Windy
# Rozleg³a ulewa/Wiatr
# Scatter Showers / Wind
# Rozleg³e ulewy/Wiatr
# Few Showers
# Mo¿liwe ulewy
# Few Showers/Windy
# Mo¿liwe ulewy/Wiatr
# Showers in the Vicinity
# Pobliskie ulewy
#
# Light Snow
# Lekki ¶nieg
# Snow
# Šnieg
# Snow / Wind
# Šnieg/Wiatr
# Heavy Snow
# Mocny ¶nieg
# Light Snow Pellets
# Lekki grad ¶nie¿ny
# Snow Pellets
# Grad ¶nie¿ny
# Light Ice Pellets
# Lekki grad lodowy
# Ice Pellets
# Grad lodowy
# Wintery Weather
# Zimowa pogoda
# Light Freezing Rain
# Lekki zamarzaj±y deszcz
# Freezing Rain
# Zamarzaj±cy deszcz
# Flurries/Windy
# Zamiecie/Wiatr
# Light Flurries/Windy
# Lekkie zamiecie/Wiatr
# Light Snow/Windy
# Lekki ¶nieg/Wiatr
# Light Snow / Wind
# Lekki ¶nieg/Wiatr
# Snow/Windy
# Šnieg/Wiatr
# Heavy Snow/Windy
# Mocny ¶nieg/Wiatr
# Light Snow Pellets/Windy
# Lekki grad ¶nie¿ny/Wiatr
# Snow Pellets/Windy
# Grad ¶nie¿ny/Wiatr
# Light Ice Pellets/Windy
# Lekki grad lodowy/Wiatr
# Ice Pellets/Windy
# Grad lodowy/Wiatr
# Light Freezing Rain/Windy
# Lekki zamarzaj±cy deszcz/Wiatr
# Freezing Rain/Windy
# Zamarzaj±cy deszcz/Wiatr
# Wintery Mix
# Miks zimowy
# Light Snow Grains
# Lekkie granulki ¶niegu
# Snow Grains
# Granulki ¶niegu
# Rain/Snow
# Šnieg z deszczem
# Rain / Snow Showers
# Deszcz ze ¶niegiem
# Rain / Snow
# Deszcz ze ¶niegiem
# Rain / Thunder
# Deszcz / Burza
# Rain/Show/Windy
# Šnieg z deszczem/Wiatr
# Rain / Snow / Wind
# Šnieg z deszczem/Wiatr
# Light Rain/Freezing Rain
# Lekki deszcz/Zamarzaj±cy deszcz
# Rain/Freezing Rain
# Deszcz/Zamarzaj±cy deszcz
# Light Rain/Freezing Rain/Windy
# Lekki deszcz/Zamarzaj±cy Deszcz/Wiatr
# Rain/Freezing Rain/Windy
# Deszcz/Zamarzaj±cy deszcz/Wiatr
# AM Snow
# Poranny ¶nieg
# PM Snow
# Popo³udniowy ¶nieg
# AM Light Snow
# Poranny lekki ¶nieg
# PM Light Snow
# Popo³udniowy lekki ¶nieg
# Ice Crystals
# Kryszta³ki lodu
# Ice Crystals/Windy
# Kryszta³ki lodu/Wiatr
#
# Snow Showers
# Burze ¶nie¿ne
# Snow Shower
# Burza ¶nie¿na
# Heavy Snow Shower
# Mocna burza ¶nie¿na
# Heavy Snow Shower/Windy
# Mocna burza ¶nie¿na/Wiatr
# PM Snow Showers
# Popo³udniowe burze ¶nie¿ne
# AM Snow Showers
# Poranne burze ¶nie¿ne
# Rain/Snow Showers
# Deszcz/Burze ¶nie¿ne
# Snow Showers/Windy
# Burze ¶nie¿ne/Wiatr
# PM Snow Showers/Windy
# Popo³udniowe burze ¶nie¿ne/Wiatr
# AM Snow Showers/Windy
# Poranne burze ¶nie¿ne/Wiatr
# Rain/Snow Showers/Windy
# Deszcz/Burze ¶nie¿ne/Wiatr
# Light Snow Showers
# Lekkie burze ¶nie¿ne
# Light Snow Shower
# Lekka burza ¶nie¿na
# Light Snow Showers/Windy
# Lekkie burze ¶nie¿ne/Wiatr
# Flurries
# Zamiecie
# Light Flurries
# Lekkie zamiecie
# Scattered Flurries
# Rozleg³e zamiecie
# Few Flurries
# Mo¿liwe zamiecie
# Few Flurries/Windy
# Mo¿liwe zamiecie/Wiatr
# Scattered Snow Showers
# Rozleg³e burze ¶nie¿ne
# Scattered Snow Showers/Windy
# Rozleg³e burze ¶nie¿ne/Wiatr
# Few Snow Showers
# Mo¿liwe burze ¶nie¿ne
# Few Snow Showers/Windy
# Mo¿liwe burze ¶nie¿ne/Wiatr
# Freezing Drizzle
# Marzn±ca m¿awka
# Light Freezing Drizzle
# Lekka marzn±ca m¿awka
# Freezing Drizzle/Windy
# Marzn±ca m¿awka/Wiatr
# Light Freezing Drizzle/Windy
# Lekka marzn±ca m¿awka/Wiatr
# Drifting Snow
# Zawieja ¶nie¿na
#
# Thunderstorms
# Burze
# T-storms
# Burze
# T-Storms
# Burze
# T-Storm
# Burza
# Scattered Thunderstorms
# Rozleg³e burze
# Scattered T-Storms
# Rozleg³e burze
# Thunderstorms/Windy
# Burze/Wiatr
# Scattered Thunderstorms/Windy
# Rozleg³e burze/Wiatr
# Rain/Thunder
# Deszcz/Grzmoty
# Light Thunderstorms/Rain
# Lekkie burze/Deszcz
# Thunderstorms/Rain
# Burze/Deszcz
# Light Rain with Thunder
# Lekki deszcz z grzmotami
# Rain with Thunder
# Deszcz z grzmotami
# Thunder in the Vicinity
# Pobliskie burze
#
# Fog
# Mg³a
# Haze
# Lekka mg³a
# Mist
# Lekkie zamglenie
# Fog/Windy
# Mg³a/Wiatr
# Haze/Windy
# Lekka Mg³a/Wiatr
# Mist/Windy
# Lekkie zamglenie/Wiatr
# Partial Fog
# Czê¶ciowa mg³a
# Smoke
# Gêsta mg³a
# Foggy
# Mglisto
# AM Fog/PM Sun
# Ranna mg³a/Popo³udniowe s³oñce
# Shallow Fog
# P³ytka mg³a
#
# Blowing Dust
# Zawieja py³owa
# Blowing Sand
# Zawieja piaskowa
# Duststorm
# Burza piaskowa
# Wind
# Wiatr
# Widespread Dust/Windy
# Rozleg³e zamiecie/Wiatr
# Widespread Dust
# Rozleg³e zamiecie
# Low Drifting Sand
# Zawieja piaskowa
#
# Data Not Available
# Dane niedostêpne
# N/A
# N/D
# N/a
# N/d


---

### Post by leonardomdq on 2010-01-04
Alguien que me de una mano con el conky? solo me falta configurar la temperatura pero no hay caso.
Es otro conky pero estoy usando los mismo script para el clima que el conky del mensaje anterior.

saludos

---

### Post by Bruce M. on 2010-01-04
> **leonardomdq said:**
> Alguien que me de una mano con el conky? solo me falta configurar la temperatura pero no hay caso.
Es otro conky pero estoy usando los mismo script para el clima que el conky del mensaje anterior.

saludos

¿Quieres algo como esto en castellano para Mar del Plata?

[[IMG]http://conky.linux-hardcore.com/wp-content/uploads/2009/11/WeatherBox-300x240.png[/IMG]]("http://conky.linux-hardcore.com/wp-content/uploads/2009/11/WeatherBox.png")

Esto es para Buenos Aires.  [Obtener ConkyForecast desde aquí]("http://ubuntuforums.org/showpost.php?p=5452132&postcount=1")

El código de Mar del Plata es ARBA0054

Después de instalar conkyForecast copiar esto en: ~/.conkyForecast
```
# config settings for conkyForecast.py
CACHE_FOLDERPATH = /tmp/
CONNECTION_TIMEOUT = 5
EXPIRY_MINUTES = 30
TIME_FORMAT = %H:%M
DATE_FORMAT = %Y-%m-%d
LOCALE = es # español
XOAP_PARTNER_ID = 
XOAP_LICENCE_KEY = 
MAXIMUM_DAYS_FORECAST = 7
#BASE_XOAP_URL = http://xoap.weather.com/weather/local/<LOCATION>?cc=*&dayf=10&link=xoap&prod=xoap&par=<XOAP_PARTNER_ID>&key=<XOAP_LICENCE_KEY>&unit=m
BASE_XOAP_URL = http://xml.weather.com/weather/local/<LOCATION>?cc=*&dayf=10&link=xoap&prod=xoap&par=<XOAP_PARTNER_ID>&key=<XOAP_LICENCE_KEY>&unit=m
```

en esta página - "Sign Up!": [http://www.weather.com/services/xmloap.html](http://www.weather.com/services/xmloap.html)

Usted recibirá XOAP_PARTNER_ID y XOAP_LICENCE_KEY por email.
Póngalos en el archivo anterior.

**Conky:**
```
background no
own_window yes
own_window_type normal
own_window_transparent no
own_window_hints skip_taskbar,skip_pager
own_window_title WeatherBox
use_xft yes
#xftfont terminus:bold:size=8
xftfont DejaVu Sans Mono:bold:size=8
xftalpha 1.0 #0.2
override_utf8_locale yes
update_interval 3500
total_run_times 0
double_buffer yes
no_buffers yes
cpu_avg_samples 2
net_avg_samples 2
use_spacer none
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
alignment tl
uppercase no
imlib_cache_size 0
gap_x 270 # left-right
gap_y 90 # up-down
border_inner_margin 5
border_outer_margin 0

# Colors
default_color DCDCDC #Gainsboro
color0 FFD700 #Gold  #7FFFD4 #Aquamarine
color1 FFA07A #LightSalmon #CD5C5C IndianRed #00CED1 DarkTurquoise #00FFFF Cyan
color2 FF8C00 #Darkorange
color3 7FFF00 #Chartreuse
color4 778899 #LightSlateGrey
color5 FFDEAD #NavajoWhite
color6 00BFFF #DeepSkyBlue
#	colours below used by colorize script
color7 48D1CC #MediumTurquoise
color8 FFFF00 #Yellow
color9 FF0000 #Red
text_buffer_size 6144 # 256 is the minimum
short_units yes
pad_percents 2

imlib_cache_size 0

# maximum_width 1280 
minimum_size 0 0 

TEXT
${execpi 3600 conkyForecast --location=ARBA0054 --template=/home/bruloo/Conky/scripts/OB_Weather.template}${font}
```


**OB_Weather.template**
```
${goto 120}${voffset -0}${color2}${font Zekton:size=20}${color6}[--datatype=HT]${font}${image [--datatype=WI] -p 0,0 -s 90x90}
${goto 120}${voffset -0}${color2}Sensación térmica: ${color6}[--datatype=LT --night]${image [--datatype=WI --startday=1] -p 480,025 -s 50x50}${image [--datatype=WI --startday=2] -p 580,025 -s 50x50}${image [--datatype=WI --startday=3] -p 680,025 -s 50x50}
${goto 120}${color2}Mín: ${color6}[--startday=0 --datatype=LT --night] ${color2}Máx: ${color9}[--startday=0 --datatype=HT --night]${image [--datatype=WI --startday=4] -p 380,105 -s 50x50}${image [--datatype=WI --startday=5] -p 480,105 -s 50x50}${image [--datatype=WI --startday=6] -p 580,105 -s 50x50}${image [--datatype=WI --startday=7] -p 680,105 -s 50x50}
${goto 120}${voffset 0}${font Zekton:bold:size=11} ${color7}[--datatype=CC]${color}${font}${image [--datatype=MI] -p 015,100 -s 55x55}${image [--datatype=BI] -p 380,00 -s 45x45}
${goto 480}${voffset -75}${color2}[--datatype=DW --shortweekday --startday=1]:${color1}[--datatype=HT --hideunits --hidedegreesymbol --startday=1]${color}/${color7}[--datatype=LT --hideunits --hidedegreesymbol --startday=1]${goto 580}${color2}[--datatype=DW --shortweekday --startday=2]:${color1}[--datatype=HT --hideunits --hidedegreesymbol --startday=2]${color}/${color7}[--datatype=LT --hideunits --hidedegreesymbol --startday=2]${goto 680}${color2}[--datatype=DW --shortweekday --startday=3]:${color1}[--datatype=HT --hideunits --hidedegreesymbol --startday=3]${color}/${color7}[--datatype=LT --hideunits --hidedegreesymbol --startday=3]
${goto 120}${voffset 70}${color7}Visibilidad:${color8} [--datatype=VI]
${goto 120}${voffset 3}${color7}P. de R.: ${color8}[--datatype=DP]${color}
${goto 120}${voffset 3}${color7}Humedad: ${color8}[--datatype=HM]  ${color7}UV: ${color8}[--datatype=UI] - ${color8}[--datatype=UT]
${goto 120}${voffset 3}${color7}Presión: ${color8}[--datatype=BR] - [--datatype=BD]${color}
${goto 380}${voffset -100}${color7}(${color8}[--datatype=WA]°${color7}) ${color8}[--datatype=WD]
${goto 380} ${color8}[--datatype=WS]
${voffset 05}${color8}${goto 380}${cpubar cpu3 1,370}${color}
${goto 380}${color2}[--datatype=DW --shortweekday --startday=4]:${color1}[--datatype=HT --hideunits --hidedegreesymbol --startday=4]${color}/${color7}[--datatype=LT --hideunits --hidedegreesymbol --startday=4]${goto 480}${color2}[--datatype=DW --shortweekday --startday=5]:${color1}[--datatype=HT --hideunits --hidedegreesymbol --startday=5]${color}/${color7}[--datatype=LT --hideunits --hidedegreesymbol --startday=5]${goto 580}${color2}[--datatype=DW --shortweekday --startday=6]:${color1}[--datatype=HT --hideunits --hidedegreesymbol --startday=6]${color}/${color7}[--datatype=LT --hideunits --hidedegreesymbol --startday=6]${goto 680}${color2}[--datatype=DW --shortweekday --startday=7]:${color1}[--datatype=HT --hideunits --hidedegreesymbol --startday=7]${color}/${color7}[--datatype=LT --hideunits --hidedegreesymbol --startday=7]
${goto 120}${voffset 45}Sol: ${font Arrows:size 20}${color3}b${goto 200}${color1}h${color}${font}
${voffset -14}${goto 165}${color8}[--datatype=SR]${goto 220}[--datatype=SS]${color}
${goto 120}${color7}Horas de Luz: ${color8}[--datatype=DL]${color}${alignr 10}${color4}W:[--datatype=LU] -=- C:[--datatype=LF]${color}

```

Se ha cambiado el uso Mar del Plata Argentina.

Que tengas Un buen día
Bruce y [Traductor Google]("http://translate.google.com/#en|es|Google%20Translate")

---

### Post by Bruce M. on 2010-01-04
> **sitodonosti said:**
> Hola Bruce ya siento no haber contestado antes, pero estado ocupado con trabajos en la universidad y presentaciones y demás. Gracias por la ayuda ya he conseguido lo de los dons conkys. En cuanto al de google calendar esto es lo que me has pedido:


Esto es lo que he creido que puede ser lo mas importante hay una archivo mas conkyGoogleCalendar.pyc
Necesitas algo más?
Ahora a ver si consigo que que el title y start vayan mas para arriba ji

un saludo[ATTACH]141029[/ATTACH]

Ohhhhhh, no es bueno! Yo no uso Google Calendar ni el programa. Así que no puedo ayudarle.

Que tengas un buen día.
Bruce y [Traductor Google]("http://translate.google.com/#en|es|")

---

### Post by leonardomdq on 2010-01-04
Muchas gracias Bruce por la respuesta y por tu conky que me pasaste.

En este que estoy configurando ahora me falta que me aparezca la temperatura y lo raro que es de noche y aparece un sol de color negro, te dejo una captura que me estara faltando?

_[[IMG]http://img130.imageshack.us/img130/3341/pantallazovr.th.png[/IMG]]("http://img130.imageshack.us/i/pantallazovr.png/")_

Conky 
```

#!/usr/bin/conky -d -c
##    .conkyrc configuration
alignment top_right
background yes
border_margin 5
border_width 5
cpu_avg_samples 2
default_color black
double_buffer yes
draw_borders no
draw_graph_borders no
draw_outline no
draw_shades no
gap_x 5
gap_y 40
max_specials 1024
max_user_text 10000
maximum_width 180
minimum_size 850
net_avg_samples 2
no_buffers yes
override_utf8_locale yes
own_window yes
own_window_default_color
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_transparent yes
own_window_type override     ## normal
pad_percents 2            # to co nizej, miejsc po przecinku
short_units yes            # krotka wersja podawania wielkosci dyskow np. 612.21M/3.80G
stippled_borders 3
text_buffer_size 8000
total_run_times 0
update_interval 1.0
uppercase no
use_spacer right
use_xft yes
xftalpha 0.75
xftfont sans:size=7
default_color black

TEXT
${color}${font OpenLogos:size=40} u t
${color}${goto 10}${font DejaVu Sans Mono:size=44}${time %H}${font DejaVu Sans Mono:size=20}${voffset -25}'${time %M}${font DejaVu Sans Mono:size=8}${voffset -12}${time %S}
${color}${goto 85}${voffset 10}${font :size=8}${time %A}
${color}${goto 85}${voffset 1}${font :size=8}${time %d %B %Y}
${color}${font RsbillsDng:size=14}O${font}${font DejaVu Sans Mono:size=8}${execpi 3600 DJS=`date +%_d`; cal -m | sed '1d' | sed '/./!d' | sed 's/$/                     /' | fold -w 21 | sed -n '/^.\{21\}/p' | sed 's/^/${alignc} /' | sed /" $DJS "/s/" $DJS "/" "'${color}'"$DJS"'${color}'" "/}${font}

${voffset -20}${color}${font led:size=9}WEATHER ${font}$hr
${color}${font weather:size=70}${execi 600 ~/.conky/conditions.sh}${color}${font}${voffset -25} ${execi 1200 ~/.conky/pogodynka.sh}

${font weather:size=28}x ${font}HDD ${execi 1 ~/.conky/hddmonit.sh}°C


${voffset -20}${color}${font led:size=9}SISTEMA ${font}$hr
${color}${sysname} Kernel: ${alignr}$kernel
${color}Conky:${alignr}${conky_version}


${voffset -10}${color}${font led:size=9}CPU ${font}$hr
${color}Core 1:  ${cpu cpu1}% $alignr ${freq_g (1)} GHz / ${exec sensors | grep "Core 0" | cut --bytes=14-21}
${color}Core 2:  ${cpu cpu2}% $alignr ${freq_g (2)} GHz / ${exec sensors | grep "Core 1" | cut --bytes=14-21}

${voffset -7}${color}${font}NAME ${goto 90}PID${goto 120}CPU% ${alignr}MEM%
${color}${font :size=6}${goto 9}${top name 1}${goto 85}${top pid 1}${goto 120}${top cpu 1}${goto 156}${top mem 1}
${color}${font :size=6}${goto 9}${top name 2}${goto 85}${top pid 2}${goto 120}${top cpu 2}${goto 156}${top mem 2}
${color}${font :size=6}${goto 9}${top name 3}${goto 85}${top pid 3}${goto 120}${top cpu 3}${goto 156}${top mem 3}


${voffset -6}${color}${font led:size=9}MEMORIA / HDD / USB ${font}$hr
${color}ram: ${mem} / ${memmax} ${alignr} ${memperc}%
${color}swap: ${swap} / ${swapmax} ${alignr} ${swapperc}%
${color}root: ${fs_used /} / ${fs_size /} ${alignr} ${fs_used_perc /}%
${color}home: ${fs_used /home} / ${fs_size /home} ${alignr} ${fs_used_perc /home}%
${color}${voffset -12}${execpi 5 ~/.conky/usb_nowe.sh}


${voffset -10}${color}${font led:size=9}NETWORK ${font}$hr
${color}gateway IP: ${alignr}${gw_ip}
${color}local IP: $alignr${addr eth0}
${color}public IP: $alignr${execi 60 ~/.conky/ip.sh}

${voffset 5}${color}${goto 10}${font pizzadude bullets:size=16}S${font}${color}${voffset -12}${goto 40}Down: ${downspeed eth0}kb/s ${color}
${goto 40}Day: ${totaldown eth0}${voffset -12}${alignr}${downspeedgraph eth0 25,50 64574e 64574e}
${voffset -13}${goto 40}Month: ${execi 300 vnstat -m | grep "`date +"'%y"`" | tail -1 | awk '{print $3 $4}'}

${goto 10}${font pizzadude bullets:size=16}M${font}$color${voffset -12}${goto 40}Up: ${upspeed eth0}kb/s${color}
${goto 40}Day: ${totalup eth0}${voffset -12}${alignr}${upspeedgraph eth0 25,50 64574e 64574e}
${voffset -13}${goto 40}Month: ${execi 300 vnstat -m | grep "`date +"'%y"`" | tail -1 | awk '{print $6 $7}'}

${color}${if_mpd_playing}${font led:size=9}MPD ${font}${mpd_status} $hr
${color}${alignc}${mpd_artist} - "${mpd_title}"
${color}${alignc}${mpd_album}
${color}${alignc}${mpd_bar 3,150}
${color}${alignc}${mpd_elapsed}/${mpd_length}${endif}

```conkyforecast.config (/home/leonardo/conkyforecast.config)
```

# config settings for conkyForecast.py
CACHE_FOLDERPATH = /tmp/
CONNECTION_TIMEOUT = 5
EXPIRY_MINUTES = 30
TIME_FORMAT = %H:%M
DATE_FORMAT = %Y-%m-%d
LOCALE = ARBA0054
XOAP_PARTNER_ID = XXXXXXXXXXX
XOAP_LICENCE_KEY = XXXXXXXXXXX
MAXIMUM_DAYS_FORECAST = 7
#BASE_XOAP_URL = http://xoap.weather.com/weather/local/<LOCATION>?cc=*&dayf=10&link=xoap&prod=xoap&par=<XOAP_PARTNER_ID>&key=<XOAP_LICENCE_KEY>&unit=m
BASE_XOAP_URL = http://xml.weather.com/weather/local/<LOCATION>?cc=*&dayf=10&link=xoap&prod=xoap&par=<XOAP_PARTNER_ID>&key=<XOAP_PARTNER_ID>&unit=m

```

Despues tengo en el directorio /scripts los siguientes scripts

- Conditions.sh
- Pagodinka.sh

-ConkyForecast.py
```

#!/usr/bin/python
# -*- coding: utf-8 -*-
###############################################################################
# conkyForecast.py is a (not so) simple (anymore) python script to gather 
# details of the current weather for use in conky.
#
#  Author: Kaivalagi
# Created: 13/04/2008
# Modifications:
#    14/04/2008    Allow day ranges for forecast data
#    14/04/2008    Check for connectivity to xoap service
#    18/04/2008    Allow the setting of spaces for ranged output
#    18/04/2008    Allow Night and Day forecast output
#    18/04/2008    Support locale for condition code text "CC" option, awaiting spanish language translation
#    18/04/2008    Use pickling for class data rather than opening xml, this bypasses the need to interrogate cached data
#    19/04/2008    Added spanish condition text - Thanks Bruce M
#    19/04/2008    Added isnumeric check on all numeric output with units suffix
#    19/04/2008    Altered pickle file naming to include location code
#    19/04/2008    Added spanish week days conversion via locale
#    20/04/2008    Added decent command argument parser
#    20/04/2008    Added --shortweekday option, if given the day of week data type is shortened to 3 characters
#    21/04/2008    Fixed locale options for forecast output
#    21/04/2008    Added --template option to allow custom output using a single exec call :)
#    21/04/2008    Added --hideunits option to remove, for example, mph and C from output
#    23/04/2008    Removed --imperial option from template, this MUST be set as a standard option on the script call and not used in the template file. 
#    23/04/2008    Readded --imperial option to template, enabling metric or imperial values per datatype. Note when using templates command line option will not work.
#    23/04/2008    Added output notifying user if the location given is bad
#    24/04/2008    Added handling for no connectivity, will revert to cached data now (erroring if no cache exists). Tests by trying to open xoap.weather.com
#    24/04/2008    Fixed Celsius to fahrenheit conversion
#    06/05/2008    Updated url used after webservice was updated
#    09/05/2008    Consolidated current condition and forecast data fetch into one call
#    09/05/2008    Added Sunrise and sunset to datatypes, these are specific to both current conditions and forecast data
#    09/05/2008    Added moon phase, barometer reading and barometer description to datatypes, these are only specific to current conditions and so are N/A in forecasted output
#    09/05/2008    Added unit conversions for barometer from mb to inches (imperial)
#    09/05/2008  Updated spanish condition text - Thanks Bruce M
#    10/05/2008  Added french locale data - Thanks benpaka
#    12/05/2008  Added new BF (bearing font) datatype to provide an arrow character (use with Arrow.ttf font) instead of NSEW output from WD (wind direction)
#    12/05/2008  Updated WD output to be locale specific, currently supports default english and spanish - Thanks Bruce M
#    18/05/2008    Added new MF (moon font) datatype to provide a moon font character (characters incorrect and no dedicated font yet).
#    21/05/2008    For current conditions the --datatype=LT option now displays "feels like" temperature rather than the current temperature
#    28/05/2008    Arrows reported to be pointing in the wrong direction. Correction provided by jjgomera
#    03/06/2008    Updated MF function, added days #26, #27, #28 nad #29 to complete the cycle. Corrections provided by Bruce M/uboops/HippyRandall
#    15/06/2008    Added new UI (UV index), UT (UV text), DP (dew point) datatypes
#    18/06/2008    Updated DP (dew point) output to convert to imperial units when required - thanks HippyRandall
#    18/06/2008    Added Spanish and French translations for UV text - Thanks Bruce M.
#    18/06/2008    Fixed incorrect WSW bearing text translation for Spanish and French - thanks Bruce M. 
#    18/06/2008    Updated to now use users own registration details from weather.com, visit http://www.weather.com/services/xmloap.html to register and obtain the PAR and KEY codes
#    06/07/2008    Added check for invalid licence key error in returned xml and now display "*** ERROR: Invalid License Key ***" in output if found...
#    27/07/2008    Updated help text to include bearing font in list of datatypes
#    28/07/2008    Added --beaufont option to convert wind speeds to the beaufort scale, works in templates too
#    28/07/2008    Updated sunrise and sunset times to be output in 24 hour format to save space
#    29/07/2008    24 hour clock now works, units removed for beaufort and --beaufont renamed to --beaufort :)
#    30/07/2008    Updated beaufort calculation to round up or down accordingly to the nearest whole number
#    02/08/2008    Fixed spacing error, default spacing of 1 for ranged output, --space=3 will now give 3 spaces rather than 4.
#    08/08/2008    Updated weather font conditions list to not use black background weather fonts
#    08/08/2008    Added and translate bulgarian locale data from stanko<dot>metodiev<at>gmail<dot>com, aka stancho
#    15/08/2008    Fixed issue with datatype=BF, when N/A is returned for current conditions wind direction, it is now correctly converted to a space
#    16/08/2008    Fixed issue with template output when template file has no space and new line at the end
#    16/08/2008    Added --hidedegreesymbol option to remove the symbol from temperature output, only valid if used as well as --hideunits
#    16/08/2008    Updated connectivity check so it only happens when necessary, also added a timeout option, defaulting to 5 seconds
#    16/08/2008    Added Czech locale "cs" translations - thanks Nite
#    16/08/2008    Tidied up non conky specific output, if there is an error or not only the verbose option will display it
#    16/08/2008    Added --datatype=LU (last updated), it provides the date and time when the last update of weather data occurred
#    17/08/2008    Fix to correct datetime function error
#    17/08/2008    Added Dutch locale "nl" translations - thanks El_Belgicano
#    17/08/2008    Updated error handling and set max startday/endday limit rules in code
#    17/08/2008    Refactored the xoap service handling and caching fallback for issues
#    17/08/2008    Added config data file handling
#    18/08/2008    Updated script to handle languages using the gettext (i18n) functions, seperate locale ".mo" will now be required
#    19/08/2008    Updated conditions_text to match xoap sdk and updated translation options in code
#    20/08/2008    Now using last update field from weather data rather than cache datetime, as this is when the weather data was recorded
#    20/08/2008    config now loaded from ~/.conkyForecast.config
#    28/08/2008    Major rewrite by nite (small changes to this by Kaivalagi)
#                  important functionality changes:
#                      - moved all cached data into one class per location, which gets pickled into one cache file ".conkyForecast-LOCATION.pkl". Because of that, only one option,
#                        CACHE_FOLDERPATH replaced the previous 3 options for specifying the destination cache folder.
#                      - changed DATETIME_FORMAT config option to DATE_FORMAT, which is used only for formatting dates. For times, TIME_FORMAT is used.
#                      - added the following new datatypes:
#                          - LF - Last Fetch. Displays date and time of the last fetching of weather data from the server
#                          - WA - Wind Angle. Displays wind direction as a number
#                          - OB - OBservatory. Displays the name of the observatory from which the weather data for given location originate.
#                          - VI - VIsibility. Displays visibility. As of now, only metric units are supported, because I'm not sure of all possible values
#                                 this can have, so far I only got "Unlimited", 8.0 and 10.0 (in kilometers) but in case of fog this could change to meters?
#                                 If converted to imperial, these numbers are not so "pretty", but it seems weather.com does it this way.
#                                 For 10.km the imperial value from weather.com was 6.2mi.
#                          - CO - COuntry. Previous CN (City Name) is now split into 2 strings (the format was "City, Country")
#                      - some datatypes' value was modified:
#                          - LF and LU both display timestamp in format "DATE_FORMAT TIME_FORMAT". New option --minuteshide was introduced, which hides certain
#                            parts of the timestamp if it is "recent enough" (not older than the minutes specified). Proper description is in the OptionParser help.
#                          - CN now only displays City Name, country is displayed in the CO datatype.
#                      - template parsing was rewritten from scratch and should now be a bit more effective and handle any kind of syntax error gracefully
#                      - added a new option --enableerrors which will in case of an error replace the regular output with the error description
#                        not usable in a template, in case of a template replaces the whole template text with the error description
#                        (useful for testing with templates etc.., but also in conky for displaying an error with internet connection for example)
#                      - errors are now printed to stderr, so they always appear in console but not in conky (only through --enableerrors)
#    31/08/2008    When barometric reading (BR) outputted in imperial (inches) it is given 2 decimal places
#    31/08/2008    Changed pickle import to cPickle because of better performance
#    31/08/2008    Added KeyError exception handler to getOutputText(), in case an unexpected word appears in the weather xml and is used as index to
#                  WeatherText dictionary (like a Wind Bearing text is used as an index for Bearing Font)
#    31/08/2008    Added a "VAR" key to the Bearing Font dictionary in WeatherText
#    31/09/2008    Fixed mixed up current and feels_like temp in current conditions
#    01/09/2008    Shortweekday option missed from getDatatypeFromSet function
#    01/09/2008    Strip out local time from last update before converting datetime for output
#    01/09/2008    Added version option to script which only outputs the version number of the script and exits
#    02/09/2008    Used regex to extract the datetime and timezone (if applicable) from the lastupdate text
#    02/09/2008    VI (visibility) is now converted to miles if --imperial option used
#    02/09/2008    Updated convert function to provide decimal place functionality and used for VI and BR output
#    03/09/2008    Replaced weather.ttf with ConkyWeather.oft and updated WF output to suit, we now have day and night based font output! - thanks Stancho
#    14/09/2008    Updated script to be python 2.4 compliant, file open function not reliant on with operator now
#    14/09/2008    Updated script to be python 2.4 compliant, this time for datetime conversions....hopefully
#    20/09/2008    Added new datatype BS (Bearing font with Speed) for the new direction font which displays different arrows for different wind speeds:
#                      Beafort scale 1-3: Small arrow
#                      Beafort scale 4-6: Bigger arrow
#                      Beafort scale 7-9: Big arrow
#                      Beafort scale 10-12: Very big arrow
#    27/09/2008    Added --centeredwidth option, if used the output will be centered in a string of the set width, padded out with spaces, if the output width is greater than the setting it will have no effect
#    02/10/2008    Updated script to now use "[" and "]" as template brackets rather than "{" and "}" so that the execp/execpi conky command can be used, this enables the use of $font, $color options in the template which conky will then make adjustments for in the output!
#    04/10/2008    Added DL (Daylight) datatype which returns the difference in hours and minutes between sunrise and sunset
#    04/10/2008    Updated to load template file in unicode mode, so we can work with all characters
#    05/10/2008       Added the possibility to set the location inside a template. To achive this, the script now loads different locations into a dictionary whenever a new location is needed.
#    05/10/2008       The command line options now set default values for corresponding options of template items
#    05/10/2008       Modified the error handling a bit (because of the locations etc..). --enableerrors can be used inside a template and after it prints the errors it clears them (so that errors don't get printed many times in a long template).
#    05/10/2008       Changed the output of DL datatype to HH:MM
#    24/10/2008    Updated daylight output to always provide correct output, now using delta.seconds -> hours/minutes string
#    10/11/2008    Added --errorlog and --infolog options to log data to a file, and removed unnecessary --enableerrors option

#    16/11/2008    Updated translation code to fallback to english if no translation found for locale requested
#    17/11/2008    Added unused text arrays to aid the translation process, all translatable text will now be picked up by pygettext - thanks foppeh
import sys, os, socket, urllib2, gettext, locale, re, codecs

from optparse import OptionParser
from xml.dom import minidom
from datetime import datetime, timedelta
import time

# cPickle is a pickle class implemented in C - so its faster
# in case its not available, use regular pickle
try:
    import cPickle as pickle
except ImportError:
    import pickle

# default to standard locale translation
domain = __file__.replace(os.path.dirname (__file__) + "/", "").replace(".py", "")
localedirectory = os.path.dirname(os.path.abspath(__file__)) + "/locale"
gettext.bindtextdomain(domain, localedirectory)
gettext.textdomain(domain)
gettext.install(domain)

class CommandLineParser:

    parser = None

    def __init__(self):

        self.parser = OptionParser()
        self.parser.add_option("-l", "--location", dest="location", default="UKXX0103", type="string", metavar="CODE", help=u"location code for weather data [default: %default],Use the following url to determine your location code by city name: http://xoap.weather.com/search/search?where=Norwich")
        self.parser.add_option("-d", "--datatype", dest="datatype", default="HT", type="string", metavar="DATATYPE", help=u"[default: %default] The data type options are: DW (Day of Week), WF (Weather Font output), LT (Forecast:Low Temp,Current:Feels Like Temp), HT (Forecast:High Temp,Current:Current Temp), CC (Current Conditions), CT (Conditions Text), PC (Precipitation Chance), HM (Humidity), VI (Visibility), WD (Wind Direction), WA (Wind Angle - in degrees), WS (Wind Speed), WG (Wind Gusts), BF (Bearing Font), BS (Bearing font with Speed), CN (City Name), CO (Country), OB (Observatory), SR (SunRise), SS (SunSet), DL (DayLight), MP (Moon Phase), MF (Moon Font), BR (Barometer Reading), BD (Barometer Description), UI (UV Index), UT (UV Text), DP (Dew Point), LU (Last Update at weather.com), LF (Last Fetch from weather.com). Not applicable at command line when using templates.")
        self.parser.add_option("-s", "--startday", dest="startday", type="int", metavar="NUMBER", help=u"define the starting day number, if omitted current conditions are output. Not applicable at command line when using templates.")
        self.parser.add_option("-e", "--endday", dest="endday", type="int", metavar="NUMBER", help=u"define the ending day number, if omitted only starting day data is output. Not applicable at command line when using templates.")
        self.parser.add_option("-S", "--spaces", dest="spaces", type="int", default=1, metavar="NUMBER", help=u"[default: %default] Define the number of spaces between ranged output. Not applicable at command line when using templates.")
        self.parser.add_option("-t", "--template", dest="template", type="string", metavar="FILE", help=u"define a template file to generate output in one call. A displayable item in the file is in the form [--datatype=HT --startday=1]. The following are possible options within each item: --location,--datatype,--startday,--endday,--night,--shortweekday,--imperial,--beaufort,--hideunits,--hidedegreesymbol,--spaces,--minuteshide. Note that the short forms of the options are not supported! If any of these options is set from the commandline, it sets the default value of the option for all template items.")
        self.parser.add_option("-L", "--locale", dest="locale", type="string", help=u"override the system locale for language output (en=english, es=spanish, fr=french, bg=bulgarian, cs=czech, more to come)")
        self.parser.add_option("-i", "--imperial", dest="imperial", default=False, action="store_true", help=u"request imperial units, if omitted output is in metric.")
        self.parser.add_option("-b", "--beaufort", dest="beaufort", default=False, action="store_true", help=u"request beaufort scale for wind speeds, if omitted output is either metric/imperial.")
        self.parser.add_option("-n", "--night", dest="night", default=False, action="store_true", help=u"switch output to night data, if omitted day output will be output.")
        self.parser.add_option("-w", "--shortweekday", dest="shortweekday", default=False, action="store_true", help=u"Shorten the day of week data type to 3 characters.")
        self.parser.add_option("-u", "--hideunits", dest="hideunits", default=False, action="store_true", help=u"Hide units such as mph or C, degree symbols (°) are still shown.")
        self.parser.add_option("-x", "--hidedegreesymbol", dest="hidedegreesymbol", default=False, action="store_true", help=u"Hide the degree symbol used with temperature output, this is only valid if used in conjunction with --hideunits.")
        self.parser.add_option("-m", "--minuteshide", dest="minuteshide", type="int", metavar="NUMBER", help=u"Works only with LU and LF. If present, hides the date part of the LU or LF timestamp if the day of the timestamp is today. The time part is also hidden, if the timestamp is older than minutes specified in this argument. If set to 0, the time part is always shown. If set to -1, the value EXPIRY_MINUTES from the config file is used.")
        self.parser.add_option("-c", "--centeredwidth", dest="centeredwidth", type="int", metavar="WIDTH", help=u"If used the output will be centered in a string of the set width, padded out with spaces, if the output width is greater than the setting it will have no effect")
        self.parser.add_option("-r", "--refetch", dest="refetch", default=False, action="store_true", help=u"Fetch data regardless of data expiry.")
        self.parser.add_option("-v", "--verbose", dest="verbose", default=False, action="store_true", help=u"Request verbose output, not a good idea when running through conky!")
        self.parser.add_option("-V", "--version", dest="version", default=False, action="store_true", help=u"Displays the version of the script.")
        self.parser.add_option("--errorlogfile", dest="errorlogfile", type="string", metavar="FILE", help=u"If a filepath is set, the script appends errors to the filepath.")
        self.parser.add_option("--infologfile", dest="infologfile", type="string", metavar="FILE", help=u"If a filepath is set, the script appends info to the filepath.")                

    def parse_args(self):
        (options, args) = self.parser.parse_args()
        return (options, args)

    def print_help(self):
        return self.parser.print_help()
    
    
class ForecastConfig:
    CACHE_FOLDERPATH = "/tmp/"
    CONNECTION_TIMEOUT = 5
    EXPIRY_MINUTES = 30
    TIME_FORMAT = "%H:%M"
    DATE_FORMAT = "%Y-%m-%d"
    LOCALE = "es # español" # with no setting the default locale of the system is used
    XOAP_PARTNER_ID = "XXXXXXXXX" # need config with correct partner id
    XOAP_LICENCE_KEY = "XXXXXXXXXX" # need config with correct licence key


class ForecastDataset:
    def __init__(self, last_update, day_of_week, low, high, condition_code, condition_text, precip, humidity, wind_dir, wind_dir_numeric, wind_speed, wind_gusts, sunrise, sunset, moon_phase, moon_icon, bar_read, bar_desc, uv_index, uv_text, dew_point, observatory, visibility, city, country):
        self.last_update = last_update
        self.day_of_week = day_of_week
        self.low = low
        self.high = high
        self.condition_code = condition_code
        self.condition_text = condition_text
        self.precip = precip
        self.humidity = humidity
        self.wind_dir = wind_dir
        self.wind_dir_numeric = wind_dir_numeric
        self.wind_speed = wind_speed
        self.wind_gusts = wind_gusts
        self.sunrise = sunrise
        self.sunset = sunset
        self.moon_phase = moon_phase
        self.moon_icon = moon_icon        
        self.bar_read = bar_read
        self.bar_desc = bar_desc
        self.uv_index = uv_index
        self.uv_text = uv_text
        self.dew_point = dew_point
        self.observatory = observatory
        self.visibility = visibility
        self.city = city
        self.country = country

class ForecastLocation:
    timestamp = None
    
    def __init__(self, current, day, night):
        self.current = current
        self.day = day
        self.night = night
        self.timestamp = datetime.today()
        
    def outdated(self, mins):
        if datetime.today() > self.timestamp + timedelta(minutes=mins):
            return True
        else:
            return False

# start ignoring translations required at runtime
def _(text): return text

class ForecastText:

    # translatable dictionaries
    conditions_text = {
        "0": _(u"Tornado"),
        "1": _(u"Tropical Storm"),
        "2": _(u"Hurricane"),
        "3": _(u"Severe Thunderstorms"),
        "4": _(u"Thunderstorms"),
        "5": _(u"Mixed Rain and Snow"),
        "6": _(u"Mixed Rain and Sleet"),
        "7": _(u"Mixed Precipitation"),
        "8": _(u"Freezing Drizzle"),
        "9": _(u"Drizzle"),
        "10": _(u"Freezing Rain"),
        "11": _(u"Light Rain"),
        "12": _(u"Rain"),
        "13": _(u"Snow Flurries"),
        "14": _(u"Light Snow Showers"),
        "15": _(u"Drifting Snow"),
        "16": _(u"Snow"),
        "17": _(u"Hail"),
        "18": _(u"Sleet"),
        "19": _(u"Dust"),
        "20": _(u"Fog"),
        "21": _(u"Haze"),
        "22": _(u"Smoke"),
        "23": _(u"Blustery"),
        "24": _(u"Windy"),
        "25": _(u"N/A"),
        "26": _(u"Cloudy"),
        "27": _(u"Przewaznie pochmurnie"),
        "28": _(u"Przewaznie pochmurnie"),
        "29": _(u"Czesciowo pochmurnie"),
        "30": _(u"Czesciowo pochmurnie"),
        "31": _(u"Clear"),
        "32": _(u"Clear"),
        "33": _(u"Fair"),
        "34": _(u"Fair"),
        "35": _(u"Mixed Rain and Hail"),
        "36": _(u"Hot"),
        "37": _(u"Isolated Thunderstorms"),
        "38": _(u"Scattered Thunderstorms"),
        "39": _(u"Scattered Showers"),
        "40": _(u"Heavy Rain"),
        "41": _(u"Scattered Snow Showers"),
        "42": _(u"Heavy Snow"),
        "43": _(u"Heavy Snow"),
        "44": _(u"N/A"),
        "45": _(u"Scattered Showers"),
        "46": _(u"Snow Showers"),
        "47": _(u"Isolated Thunderstorms"),
        "na": _(u"N/A"),
        "-": _(u"N/A")
    }

    day_of_week_short = {
        "Today": _(u"Now"),
        "Monday": _(u"Mon"),
        "Tuesday": _(u"Tue"),
        "Wednesday": _(u"Wed"),
        "Thursday": _(u"Thu"),
        "Friday": _(u"Fri"),
        "Saturday": _(u"Sat"),
        "Sunday": _(u"Sun")
    }

    # font based character sets, untranslatable

    # ConkyWeather.ttf based output
    conditions_weather_font = {
        "0": u"1", #Tornado
        "1": u"2", #Tropical Storm
        "2": u"3", #Hurricane
        "3": u"n", #Severe Thunderstorms
        "4": u"m", #Thunderstorms
        "5": u"x", #Mixed Rain and Snow
        "6": u"x", #Mixed Rain and Sleet
        "7": u"y", #Mixed Precipitation
        "8": u"s", #Freezing Drizzle
        "9": u"h", #Drizzle
        "10": u"t", #Freezing Rain
        "11": u"h", #Light Rain
        "12": u"i", #Rain
        "13": u"p", #Snow Flurries
        "14": u"p", #Light Snow Showers
        "15": u"8", #Drifting Snow
        "16": u"q", #Snow
        "17": u"u", #Hail
        "18": u"w", #Sleet
        "19": u"7", #Dust
        "20": u"0", #Fog
        "21": u"9", #Haze
        "22": u"4", #Smoke
        "23": u"6", #Blustery 
        "24": u"6", #Windy
        "25": u"-", #N/A
        "26": u"f", #Cloudy
        "27": u"D", #Mostly Cloudy - night
        "28": u"d", #Mostly Cloudy - day
        "29": u"C", #Partly Cloudy - night
        "30": u"c", #Partly Cloudy - day
        "31": u"A", #Clear - night
        "32": u"a", #Clear - day
        "33": u"B", #Fair - night
        "34": u"b", #Fair - day
        "35": u"v", #Mixed Rain and Hail
        "36": u"5", #Hot
        "37": u"k", #Isolated Thunderstorms - day
        "38": u"k", #Scattered Thunderstorms - day
        "39": u"g", #Scattered Showers - day
        "40": u"j", #Heavy Rain
        "41": u"o", #Scattered Snow Showers - day
        "42": u"r", #Heavy Snow
        "43": u"r", #Heavy Snow
        "44": u"-", #N/A
        "45": u"G", #Scattered Showers - night
        "46": u"O", #Scattered Snow Showers - night
        "47": u"K", #Isolated Thunderstorms - night
        "na": u"-", #N/A
        "-": u"-" #N/A
    }

    conditions_moon_font = {
        "0": u"1",
        "1": u"N",
        "2": u"O",
        "3": u"P",
        "4": u"Q",
        "5": u"R",
        "6": u"S",
        "7": u"T",
        "8": u"U",
        "9": u"V",
        "10": u"W",
        "11": u"X",
        "12": u"Y",
        "13": u"Z",
        "14": u"0",
        "15": u"0",
        "16": u"A",
        "17": u"B",
        "18": u"C",
        "19": u"D",
        "20": u"E",
        "21": u"F",
        "22": u"G",
        "23": u"H",
        "24": u"I",
        "25": u"J",
        "26": u"K",
        "27": u"L",
        "28": u"M",
        "29": u"1",
        "N/A": u"",
        "na": u"",
        "-": u""
    }

    # this now returns ascii code
    bearing_arrow_font = {
        "S": 0x31,
        "SSW": 0x32,
        "SW": 0x33,
        "WSW": 0x34,
        "W": 0x35,
        "WNW": 0x36,
        "NW": 0x37,
        "NNW": 0x38,
        "N": 0x39,
        "NNE": 0x3a,
        "NE": 0x3b,
        "ENE": 0x3c,
        "E": 0x3d,
        "ESE": 0x3e,
        "SE": 0x3f,
        "SSE": 0x40,
    }

    # New translatable strings
    # foppeh >> These arrays are here so they get translated even if they
    #           are not used in the code. 
    
    # first all about moon phases
    moon_phase = {    
    "New": _(u"New"),
    "First Quarter": _(u"First Quarter"),
    "Full": _(u"Full"),
    "Last Quarter": _(u"Last Quarter"),
    "Waning Cresent": _(u"Waning Cresent"),
    "Waning Gibbous": _(u"Waning Gibbous"),
    "Waxing Cresent": _(u"Waxing Cresent"),
    "Waxing Gibbous": _(u"Waxing Gibbous")
    }
    
    # foppeh >> Something is going on with these string. I don't know if they are valid.
    #           The weird thing is they are in lower case and the XML seems to spit
    #           text with too many Uppercase. So I don't know if strings presented here
    #           will ever be a valid output from weather.com. Yet I stored them here for
    #           future reference (and because of the French translation).
    
    # all about weather conditions
    # 'blowing dust'                 => 'tempête de sable',
    # 'blowing snow'                 => 'tempête de neige',
    # 'blowing snow and windy'       => 'blizzard',
    # 'clear'                        => 'clair     ',
    # 'cloudy'                       => 'nuageux',
    # 'cloudy and windy'             => 'nuageux et venteux',
    # 'drizzle'                      => 'bruine',
    # 'drifting snow'                => 'accumulation de neige',
    # 'fair'                         => 'clair',
    # 'fair and windy'               => 'clair et venteux',
    # 'fog'                          => 'brouillard',
    # 'haze'                         => 'smog',
    # 'heavy drizzle'                => 'bruine intense',
    # 'heavy rain'                   => 'pluie intense',
    # 'heavy rain and windy'         => 'pluie intense et venteux',
    # 'heavy snow'                   => 'neige intense',
    # 'heavy snow and windy'         => 'neige intense et venteux',
    # 'heavy t-storm'                => 'orage électrique intense',
    # 'light drizzle'                => 'faible bruine',
    # 'light drizzle and windy'      => 'bruine légère  et venteux',
    # 'light freezing drizzle'       => 'bruine légère verglassante',
    # 'light freezing rain'          => 'faible pluie verglassante',
    # 'light rain'                   => 'faible pluie',
    # 'light rain shower'            => 'faible averse de pluie',
    # 'light rain and fog'           => 'faible pluie et brouillard',
    # 'light rain and freezing rain' => 'pluie faible et pluie erglassante',
    # 'light rain with thunder'      => 'faible pluie avec tonnerre',
    # 'light rain and windy'         => 'faible pluie et venteux',
    # 'light snow'                   => 'faible neige',
    # 'light snow shower'            => 'faible averse de neige',
    # 'light snow and sleet'         => 'leichter Schneefall und Schneeregen',
    # 'light snow and windy'         => 'leichter Schneefall und windig',
    # 'mist'                         => 'brume',
    # 'mostly cloudy'                => 'nuageux avec éclaircies',
    # 'mostly cloudy and windy'      => 'venteux et nuageux avec éclaircies',
    # 'partial fog'                  => 'partiellement brumeux',
    # 'partly cloudy'                => 'partiellement nuageux',
    # 'partly cloudy and windy'      => 'partiellement nuageux et venteux',
    # 'patches of fog'               => 'partielles de brouillard',
    # 'rain'                         => 'pluvieux',
    # 'rain and sleet'               => 'pluie et grésil',
    # 'rain and snow'                => 'pluie et neige',
    # 'rain shower'                  => 'averse de pluie',
    # 'rain and fog'                 => 'pluie et brouillard',
    # 'rain and windy'               => 'pluvieux et venteux',
    # 'sand'                         => 'sable',
    # 'shallow fog'                  => 'brouillard mince',
    # 'showers in the vicinity'      => 'averses à proximité',
    # 'sleet'                        => 'grésil',
    # 'smoke'                        => 'fumée',
    # 'snow'                         => 'neige',
    # 'snow and fog'                 => 'neige et brouillard',
    # 'snow and freezing rain'       => 'neige et pluie verglassante',
    # 'snow grains'                  => 'neige intermittante',
    # 'snow showers'                 => 'averse de neige',
    # 'snow and windy and fog'       => 'neige, brouillard et venteux',
    # 'squalls and windy'            => 'vent et grésil',
    # 'sunny'                        => 'ensoleillé',
    # 'sunny and windy'              => 'ensoleillé et venteux',
    # 't-storm'                      => 'Orage Électrique',
    # 'thunder'                      => 'tonnerre',
    # 'thunder in the vicinity'      => 'tonnerre aux alentours',
    # 'unknown precip'               => 'précipitation inconnue',
    # 'widespread dust'              => 'vents de poussière',
    # 'wintry mix'                   => 'conditions hivernales variables',

    
    # some general things...
    general = {
     "n/a": _(u"n/a"),
    'N/A': _(u"N/A"),
    'Not Available': _(u"Not Available"),
    'unknown': _(u"unknown"),
    'NONE': _(u"NONE"),
    'day': _(u"day"),
    'night': _(u"night")
    }
    
    # UV index ...
    UV_index = {
    "Extreme": _(u"Extreme"),
    "Very high": _(u"Very High"),
    "High": _(u"High"),
    "Moderate": (u"Moderate"),
    "Low": _(u"Low")
    }
    
    # tendencies used for barometric pressure
    bar_pressure = {
    "Very Low": _(u"Very Low"),
    "Moderate": _(u"Moderate"),
    "rising": _(u"rising"),
    "falling": _(u"falling"),
    "steady": _(u"steady"),
    "calm": _(u"calm")
    }


    # wind directions long
    wind_directions_long = {
    "East": _(u"East"),
    "East Northeast": _(u"East Northeast"),
    "East Southeast": _(u"East Southeast"),
    "North": _(u"North"),
    "Northeast": _(u"Northeast"),
    "North Northeast": _(u"North Northeast"),
    "North Northwest": _(u"North Northwest"),
    "Northwest": _(u"Northwest"),
    "South": _(u"South"),
    "Souteast": _(u"Southeast"),
    "South Southeast": _(u"South Southeast"),
    "South Southwest": _(u"South Southwest"),
    "Southwest": _(u"Southwest"),
    "variable": _(u"variable"),
    "West": _(u"West"),
    "West Northwest": _(u"West Northwest"),
    "West Southwest": _(u"West Southwest")
    }
    
    wind_directions_short = {
    "E": _(u"E"),
    "ENE": _(u"ENE"),
    "ESE": _(u"ESE"),
    "N": _(u"N"),
    "NE": _(u"NE"),
    "NNE": _(u"NNE"),
    "NNW": _(u"NNW"),
    "NW": _(u"NW"),
    "S": _(u"S"),
    "SE": _(u"SE"),
    "SSE": _(u"SSE"),
    "SSW": _(u"SSW"),
    "SW": _(u"SW"),
    "W": _(u"W"),
    "WNW": _(u"WNW"),
    "WSW": _(u"WSW")
    }

    days_of_week = {
    "Today": _(u"Today"),
    "Monday": _(u"Monday"),
    "Tuesday":_(u"Tuesday"),
    "Wednesday":_(u"Wednesday"),
    "Thursday": _(u"Thursday"),
    "Friday": _(u"Friday"),
    "Saturday": _(u"Saturday"),
    "Sunday": _(u"Sunday")
    }
    
# end ignoring translations
del _

class ForecastInfo:
    
    # design time variables
    options = None
    config = None
    forecast_data = {}
    # a list of locations for which an attempt was made to load them
    # locations in this list are not loaded again (if there was an error,
    # this makes sure it doesn't reapeat over and over)
    loaded_locations = []
    error = ""
    errorfound = False
    
    # design time settings
    CONFIG_FILENAME = ".conkyForecast.config"
    CACHE_FILENAME_TEMPLATE = ".conkyForecast-LOCATION.cache"
    MAX_DAY_NUMBER = 4

    def __init__(self, options):

        self.options = options
                                         
        self.loadConfigData()
        
        # setup timeout for connections
        # TODO: seems like this doesn't work in all cases..
        socket.setdefaulttimeout(self.config.CONNECTION_TIMEOUT)
        
        # set the locale
        if self.options.locale == None:
            if self.config.LOCALE == "":
                self.options.locale = locale.getdefaultlocale()[0][0:2]
            else:
                self.options.locale = self.config.LOCALE

        self.logInfo("Locale set to " + self.options.locale)
        
        # if not the default "en" locale, configure the i18n language translation    
        if self.options.locale != "en":

            self.logInfo("Looking for translation file for '%s' under %s" % (self.options.locale, localedirectory))
            
            if gettext.find(domain, localedirectory, languages=[self.options.locale]) != None:
                self.logInfo("Translation file found for '%s'" % self.options.locale)
                
                try:
                    trans = gettext.translation(domain, localedirectory, languages=[self.options.locale])
                    trans.install(unicode=True)
                    self.logInfo("Translation installed for '%s'" % self.options.locale)
                    
                except Exception, e:
                    self.logError("Unable to load translation for '%s' %s" % (self.options.locale, e.__str__()))
            else:
                self.logInfo("Translation file not found for '%s', defaulting to 'en'" % self.options.locale)
                self.options.locale = "en"
                
    def loadConfigData(self):
        try:         
            # load .conkyForecast.config from home directory of the user
            configfilepath = os.path.join(os.path.expanduser('~'), self.CONFIG_FILENAME)
                                          
            if os.path.exists(configfilepath):
                
                self.config = ForecastConfig()
                
                #load the file
                fileinput = open(configfilepath)
                lines = fileinput.read().split("\n")
                fileinput.close() 

                for line in lines:
                    line = line.strip()
                    if len(line) > 0 and line[0:1] != "#": # ignore commented lines or empty ones
    
                        name = line.split("=")[0].strip().upper() # config setting name on the left of =
                        value = line.split("=")[1].split("#")[0].strip() # config value on the right of = (minus any trailing comments)
                        
                        if len(value) > 0:
                            if name == "CACHE_FOLDERPATH":
                                self.config.CACHE_FOLDERPATH = value
                            elif name == "CONNECTION_TIMEOUT":
                                try: # NITE: removed the isNumeric() check in favor of this..its more effective and lets the user know something is wrong
                                    self.config.CONNECTION_TIMEOUT = int(value)
                                except:
                                    self.logError("Invalid value of config option CONNECTION_TIMEOUT: " + value)
                            elif name == "EXPIRY_MINUTES":
                                try:
                                    self.config.EXPIRY_MINUTES = int(value)
                                except:
                                    self.logError("Invalid value of config option EXPIRY_MINUTES: " + value)
                            elif name == "TIME_FORMAT":
                                self.config.TIME_FORMAT = value
                            elif name == "DATE_FORMAT":
                                self.config.DATE_FORMAT = value                                    
                            elif name == "LOCALE":
                                self.config.LOCALE = value
                            elif name == "XOAP_PARTNER_ID":
                                self.config.XOAP_PARTNER_ID = value
                            elif name == "XOAP_LICENCE_KEY":
                                self.config.XOAP_LICENCE_KEY = value
                            else:
                                self.logError("Unknown option in config file: " + name)

                if self.options.verbose == True:
                    print >> sys.stdout,"*** CONFIG OPTIONS:"
                    print >> sys.stdout,"    CACHE_FOLDERPATH:", self.config.CACHE_FOLDERPATH
                    print >> sys.stdout,"    CONNECTION_TIMEOUT:", self.config.CONNECTION_TIMEOUT
                    print >> sys.stdout,"    EXPIRY_MINUTES:", self.config.EXPIRY_MINUTES
                    print >> sys.stdout,"    TIME_FORMAT:", self.config.TIME_FORMAT
                    print >> sys.stdout,"    DATE_FORMAT:", self.config.DATE_FORMAT                
                    print >> sys.stdout,"    LOCALE:", self.config.LOCALE
                    print >> sys.stdout,"    XOAP_PARTNER_ID:", self.config.XOAP_PARTNER_ID
                    print >> sys.stdout,"    XOAP_LICENCE_KEY:", self.config.XOAP_LICENCE_KEY
                    
            else:
                self.logError("Config data file %s not found, using defaults (Registration info is needed though)" % configfilepath)

        except Exception, e:
            self.logError("Error while loading config data, using defaults (Registration info is needed though): " + e.__str__())


    def checkAndLoad(self, location):

        # if the location was not loaded before (or attempted to load)
        if not location in self.loaded_locations:
            # add it to the list so it doesn't get loaded again (or attempted to load)
            self.loaded_locations.append(location)

            # define CACHE_FILEPATH based on cache folder and location code
            CACHE_FILEPATH = os.path.join(self.config.CACHE_FOLDERPATH, self.CACHE_FILENAME_TEMPLATE.replace("LOCATION", location))

            if not self.forecast_data.has_key(location):
                if os.path.exists(CACHE_FILEPATH):
                    try:
                        self.logInfo("Loading cache file " + CACHE_FILEPATH)
                        file = open(CACHE_FILEPATH, 'rb')
                        self.forecast_data[location] = pickle.load(file)
                        file.close()
                    except Exception, e:
                        self.logError("Unable to read the cache file %s: %s" % (CACHE_FILEPATH, e.__str__()))

            # check the data in the dictionary and update if outdated
            # if there was an update, store the new data in the cache file
            if self.checkAndUpdate(location) == True:
                try:
                    self.logInfo("Saving updated cache file " + CACHE_FILEPATH)
                    file = open(CACHE_FILEPATH, 'wb')
                    pickle.dump(self.forecast_data[location], file)
                    file.close()
                except Exception, e:
                    self.logError("Unable to save cache file %s: %s" % (CACHE_FILEPATH, e.__str__()))

        # if the location is still not in cache, print an error and return false to writeOutput()
        if self.forecast_data.has_key(location):
            return True
        else:
            self.logError("Location %s is not in cache." % self.options.location) 
            return False

    def checkAndUpdate(self, location):
        # if the location is outdated or the refetch is forced..
        if not self.forecast_data.has_key(location) or \
           self.forecast_data[location].outdated(self.config.EXPIRY_MINUTES) or \
           self.options.refetch == True:

            # obtain current conditions data from xoap service
            try:
                url = "http://xoap.weather.com/weather/local/" + location + "?cc=*&dayf=8&link=xoap&prod=xoap&par=" + self.config.XOAP_PARTNER_ID + "&key=" + self.config.XOAP_LICENCE_KEY + "&unit=m"
        
                self.logInfo("Fetching weather data from " + url)

                usock = urllib2.urlopen(url)
                xml = usock.read()
                usock.close()
                
            except Exception, e:
                self.logError("Server connection error: " + e.__str__())
            
            else:
                # interrogate weather data
                try:
                    # parse the XML
                    self.weatherxmldoc = minidom.parseString(xml)
                                    
                    weather_n = self.weatherxmldoc.documentElement
                    
                    # check for an error and raise an exception
                    if len(weather_n.getElementsByTagName('err')) > 0:
                        raise Exception, self.getText(weather_n, 'err')
                    
                    #head_n = self.getChild(weather_n, 'head')
                    #visibility_unit = self.getText(head_n, 'ud')
                    
                    location_n = self.getChild(weather_n, 'loc')
                    city, country = self.getText(location_n, 'dnam').split(',')
                    country = country.strip()
                    
                    # current conditions data
                    day_of_week = _(u"Today")
                    precip = _(u"N/A")
                    sunrise = self.getText(location_n, 'sunr')
                    sunset = self.getText(location_n, 'suns')

                    current_condition_n = self.getChild(weather_n, 'cc')
                    last_update = self.getText(current_condition_n, 'lsup')
                    observatory = self.getText(current_condition_n, 'obst')
                    # remove the ", country" from the string (the string is in form "location_name, country")
                    observatory = observatory[:observatory.rfind(',')]
                    current_desc = self.getText(current_condition_n, 't')
                    current_code = self.getText(current_condition_n, 'icon')
                    current_temp = self.getText(current_condition_n, 'tmp')
                    current_temp_feels = self.getText(current_condition_n, 'flik')
                    
                    bar_n = self.getChild(current_condition_n, 'bar')
                    bar_read = self.getText(bar_n, 'r')
                    bar_desc = self.getText(bar_n, 'd')
                    
                    wind_n = self.getChild(current_condition_n, 'wind')
                    wind_speed = self.getText(wind_n, 's')
                    wind_gusts = self.getText(wind_n, 'gust')
                    wind_direction_numeric = self.getText(wind_n, 'd')
                    wind_direction = self.getText(wind_n, 't')
                    
                    humidity = self.getText(current_condition_n, 'hmid')
                    visibility = self.getText(current_condition_n, 'vis')
                    #if self.isNumeric(visibility):
                    #    visibility = visibility + visibility_unit
                    
                    uv_n = self.getChild(current_condition_n, 'uv')
                    uv_index = self.getText(uv_n, 'i')
                    uv_text = self.getText(uv_n, 't')
                    
                    dew_point = self.getText(current_condition_n, 'dewp')
                    
                    moon_n = self.getChild(current_condition_n, 'moon')
                    moon_icon = self.getText(moon_n, 'icon')
                    moon_phase = self.getText(moon_n, 't')
                    
                    current_forecast_data = ForecastDataset(last_update, day_of_week, current_temp_feels, current_temp, current_code, current_desc, precip, humidity, wind_direction, wind_direction_numeric, wind_speed, wind_gusts, sunrise, sunset, moon_phase, moon_icon, bar_read, bar_desc, uv_index, uv_text, dew_point, observatory, visibility, city, country)
    
                    # collect forecast data
                    observatory = _(u"N/A")
                    bar_read = _(u"N/A")
                    bar_desc = _(u"N/A")
                    visibility = _(u"N/A")
                    uv_index = _(u"N/A")
                    uv_text = _(u"N/A")
                    dew_point = _(u"N/A")
                    moon_phase = _(u"N/A")
                    moon_icon = _(u"N/A")
                    
                    forecast_n = self.getChild(weather_n, 'dayf')
                    last_update = self.getText(forecast_n, 'lsup')
                    
                    day_nodes = forecast_n.getElementsByTagName('day')
                    
                    day_forecast_data_list = []
                    night_forecast_data_list = []
        
                    for day in day_nodes:
                        day_of_week = day.getAttribute('t')

                        high_temp = self.getText(day, 'hi')
                        low_temp = self.getText(day, 'low')
                        sunrise = self.getText(day, 'sunr')
                        sunset = self.getText(day, 'suns')
    
                        # day forecast specific data
                        daytime_n = self.getChild(day, 'part')
                        condition_code = self.getText(daytime_n, 'icon')
                        condition = self.getText(daytime_n, 't')

                        wind_n = self.getChild(daytime_n, 'wind')
                        wind_speed = self.getText(wind_n, 's')
                        wind_gusts = self.getText(wind_n, 'gust')
                        wind_direction_numeric = self.getText(wind_n, 'd')
                        wind_direction = self.getText(wind_n, 't')
                        
                        precip = self.getText(daytime_n, 'ppcp')
                        humidity = self.getText(daytime_n, 'hmid')
                        
                        day_forecast_data = ForecastDataset(last_update, day_of_week, low_temp, high_temp, condition_code, condition, precip, humidity, wind_direction, wind_direction_numeric, wind_speed, wind_gusts, sunrise, sunset, moon_phase, moon_icon, bar_read, bar_desc, uv_index, uv_text, dew_point, observatory, visibility, city, country)
                        day_forecast_data_list.append(day_forecast_data)
    
                        # night forecast specific data
                        daytime_n = self.getChild(day, 'part', 1)
                        condition_code = self.getText(daytime_n, 'icon')
                        condition = self.getText(daytime_n, 't')

                        wind_n = self.getChild(daytime_n, 'wind')
                        wind_speed = self.getText(wind_n, 's')
                        wind_gusts = self.getText(wind_n, 'gust')
                        wind_direction_numeric = self.getText(wind_n, 'd')
                        wind_direction = self.getText(wind_n, 't')
                        
                        precip = self.getText(daytime_n, 'ppcp')
                        humidity = self.getText(daytime_n, 'hmid')
                        
                        night_forecast_data = ForecastDataset(last_update, day_of_week, low_temp, high_temp, condition_code, condition, precip, humidity, wind_direction, wind_direction_numeric, wind_speed, wind_gusts, sunrise, sunset, moon_phase, moon_icon, bar_read, bar_desc, uv_index, uv_text, dew_point, observatory, visibility, city, country)
                        night_forecast_data_list.append(night_forecast_data)
                        
                    self.forecast_data[location] = ForecastLocation(current_forecast_data, day_forecast_data_list, night_forecast_data_list)
                    
                    return True
            
                except Exception, e:
                    self.logError("Error reading weather data: " + e.__str__())

    def getTimestampOutput(self, timestamp, minuteshide):            
        # minuteshide:
        # None = disabled
        # -1 = hide days and use config.EXPIRY_MINUTES
        # 0 = hide days and always show hours
        
        output = u""
        
        today = datetime.today()
        days = today.day - timestamp.day
        if days or minuteshide == None:
            output += timestamp.strftime(self.config.DATE_FORMAT)
        
        if minuteshide == -1:
            minuteshide = self.config.EXPIRY_MINUTES
            
        delta = today - timestamp
        if days or minuteshide == None or minuteshide == 0 or delta.seconds > minuteshide * 60:
            if (len(output) > 0):
                output += " "
            output += timestamp.strftime(self.config.TIME_FORMAT)
        
        return output


    def getDatatypeFromSet(self, location, datatype, set, shortweekday, imperial, beaufort, tempunit, speedunit, distanceunit, pressureunit, minuteshide, centeredwidth):
        output = u""

        try:
            if datatype == "LU":
                datetext, timezone = re.match(r"(\d{1,2}/\d{1,2}/\d{2} \d{1,2}:\d{2} [A|P]M)\s(\w*\s*\w*)",set.last_update).groups()
                if datetext != None:
                    #output = self.getTimestampOutput(datetime.strptime(datetext, "%m/%d/%y %I:%M %p"), minuteshide)
                    
                    # python 2.4 compliant
                    output = self.getTimestampOutput(datetime(*(time.strptime(datetext, "%m/%d/%y %I:%M %p"))[0:6]), minuteshide)
                    if timezone != None and timezone != "Local Time" and len(output) > 0:
                        output = output + " " + timezone
                else:
                    output = set.last_update.strip()
                    self.logError("Unable to extract the Last update date from the dataset")
            elif datatype == "LF":
                output = self.getTimestampOutput(self.forecast_data[location].timestamp, minuteshide)
            elif datatype == "DW":
                if shortweekday == True:
                    output = _(ForecastText.day_of_week_short[set.day_of_week])
                else:
                    output = _(set.day_of_week)
            elif datatype == "WF":
                output = ForecastText.conditions_weather_font[set.condition_code]
            elif datatype == "LT":
                if self.isNumeric(set.low) == True:
                    if imperial == True:
                        string = self.convertCelsiusToFahrenheit(set.low)
                    else:
                        string = set.low
                    string = string + tempunit
                else:
                    string = _(set.low)
                output = string
            elif datatype == "HT":
                if self.isNumeric(set.high) == True:
                    if imperial == True:
                        string = self.convertCelsiusToFahrenheit(set.high)
                    else:
                        string = set.high
                    string = string + tempunit
                else:
                    string = _(set.high)
                output = string
            elif datatype == "CC":
                output = _(ForecastText.conditions_text[set.condition_code])
            elif datatype == "CT":
                output = _(set.condition_text)
            elif datatype == "PC":
                if self.isNumeric(set.precip) == True:
                    string = set.precip + u"%"
                else:
                    string = _(set.precip)
                output = string
            elif datatype == "HM":
                if self.isNumeric(set.humidity) == True:
                    string = set.humidity + u"%"
                else:
                    string = _(set.humidity)
                output = string
            elif datatype == "WD":
                output = _(set.wind_dir)
            elif datatype == "BF":
                if set.wind_speed == "calm":
                    output = chr(0x25)
                else:
                    if (set.wind_dir == "VAR"):
                        output = chr(0x22) # 2nd level var arrow
                    else:
                        try:
                            # for the old datatype, add 0x10, that makes the output in the A-P range,
                            # which is the 2nd level arrow
                            output = chr(ForecastText.bearing_arrow_font[set.wind_dir] + 0x10)
                        except KeyError:
                            # if the value wasn't found in ForecastText.bearing_arrow_font, use space
                            output = "-"
            elif datatype == "BS":
                if set.wind_speed == "calm":
                    output = chr(0x25)
                elif self.isNumeric(set.wind_speed) == True:
                    if (set.wind_dir == "VAR"):
                        output = chr(0x21 + self.getWindLevel(set.wind_speed))
                    else:
                        try:
                            output = chr(ForecastText.bearing_arrow_font[set.wind_dir] + self.getWindLevel(set.wind_speed) * 0x10)
                        except KeyError:
                            # if the value wasn't found in ForecastText.bearing_arrow_font, use N/A
                            output = "-"
                else:
                    try:
                        # if the speed is not "calm" but also not a number, add 0x10
                        # that makes the output in the A-P range, the 2nd level arrow
                        output = chr(ForecastText.bearing_arrow_font[set.wind_dir] + 0x10)
                    except KeyError:
                        # if the value wasn't found in ForecastText.bearing_arrow_font, use N/A
                        output = "-"
            elif datatype == "WA":
                output = _(set.wind_dir_numeric)
            elif datatype == "WS":
                if self.isNumeric(set.wind_speed) == True:
                    if beaufort == True:
                        string = self.convertKPHtoBeaufort(set.wind_speed)
                    elif imperial == True:
                        string = self.convertKilometresToMiles(set.wind_speed)
                    else:
                        string = set.wind_speed
                    string = string + speedunit
                else:
                    string = _(set.wind_speed)
                output = string
            elif datatype == "WG":
                if self.isNumeric(set.wind_gusts) == True:
                    if beaufort == True:
                        string = self.convertKPHtoBeaufort(set.wind_gusts)
                    elif imperial == True:
                        string = self.convertKilometresToMiles(set.wind_gusts)
                    else:
                        string = set.wind_gusts
                    string = string + speedunit
                else:
                    string = _(set.wind_gusts) # need to define translations
                output = string
            elif datatype == "SR":
                #srtime = datetime.strptime(set.sunrise, "%I:%M %p")
                #output = srtime.strftime(self.config.TIME_FORMAT)

                # python 2.4 compliant
                srtime = datetime(*(time.strptime(set.sunrise, "%I:%M %p"))[0:6])
                output = srtime.strftime(self.config.TIME_FORMAT)    
                                
            elif datatype == "SS":
                #sstime = datetime.strptime(set.sunset, "%I:%M %p")
                #output = sstime.strftime(self.config.TIME_FORMAT)
                
                # python 2.4 compliant
                sstime = datetime(*(time.strptime(set.sunset, "%I:%M %p"))[0:6])
                output = sstime.strftime(self.config.TIME_FORMAT)
            elif datatype == "DL":
                srtime = datetime(*(time.strptime(set.sunrise, "%I:%M %p"))[0:6])
                sstime = datetime(*(time.strptime(set.sunset, "%I:%M %p"))[0:6])
                delta = sstime - srtime              
                output = self.getHoursMinutesStringFromSeconds(delta.seconds)
            elif datatype == "MP":
                output = _(set.moon_phase) # need to define translations
            elif datatype == "MF":
                output = ForecastText.conditions_moon_font[set.moon_icon]                        
            elif datatype == "BR":
                if self.isNumeric(set.bar_read) == True:
                    if imperial == True:
                        string = self.convertMillibarsToInches(set.bar_read,2)
                    else:
                        string = set.bar_read
                    string = string + pressureunit
                else:
                    string = _(set.bar_read)
                output = string
            elif datatype == "BD":
                output = _(set.bar_desc) # need to define translations
            elif datatype == "UI":
                output = _(set.uv_index)
            elif datatype == "UT":
                output = _(set.uv_text)
            elif datatype == "DP":
                if self.isNumeric(set.dew_point) == True:
                    if imperial == True:
                        string = self.convertCelsiusToFahrenheit(set.dew_point)
                    else:
                        string = set.dew_point
                    string = string + tempunit
                else:
                    string = _(set.dew_point)
                output = string
            elif datatype == "OB":
                output = set.observatory
            elif datatype == "VI":
                if self.isNumeric(set.visibility) == True:
                    if imperial == True:
                        string = self.convertKilometresToMiles(set.visibility,1)
                    else:
                        string = set.visibility
                    string = string + distanceunit
                else:
                    string = _(set.visibility)
                output = string            
            elif datatype == "CN":
                output = set.city
            elif datatype == "CO":
                output = set.country
            else:
                self.logError("Unknown datatype requested: " + datatype)

        except KeyError, e:
            self.logError("Unknown value %s encountered for datatype '%s'! Please report this!" % (e.__str__(), datatype))
        
        # center the text if requested
        if self.isNumeric(centeredwidth) == True:
            output = output.center(int(centeredwidth))    
                            
        return output


    def getDatasetOutput(self, location, datatype, startday, endday, night, shortweekday, imperial, beaufort, hideunits, hidedegreesymbol, spaces, minuteshide, centeredwidth):

        output = u""
        # Check if the location is loaded, if not, load it. If it can't be loaded, there was an error
        if not self.checkAndLoad(location):
            self.logError("Failed to load the location cache")
            return output

        # define current units for output
        if hideunits == False:
            if imperial == False:
                tempunit = _(u"°C")
                speedunit = _(u"kph")
                distanceunit = _(u"km")
                pressureunit = _(u"mb")
            else:
                tempunit = _(u"°F")
                speedunit = _(u"mph")
                distanceunit = _(u"m")
                pressureunit = _(u"in")
                
            # override speed units if beaufort selected
            if beaufort == True:
                speedunit = u""
        else:
            # remove degree symbol if not required
            if hidedegreesymbol == False:
                tempunit = u"°"
            else:
                tempunit = u""
                
            speedunit = u""
            distanceunit = u""
            pressureunit = u""

        if startday == None:
            output += self.getDatatypeFromSet(location, datatype, self.forecast_data[location].current, shortweekday, imperial, beaufort, tempunit, speedunit, distanceunit, pressureunit, minuteshide, centeredwidth)
        else: # forecast data

            # ensure startday and enday are within the forecast limit
            
            if startday < 0:
                startday = 0
                self.logError("--startday set beyond forecast limit, reset to minimum of 0")
            elif startday > self.MAX_DAY_NUMBER:
                startday = self.MAX_DAY_NUMBER
                self.logError("--startday set beyond forecast limit, reset to maximum of " + self.MAX_DAY_NUMBER)
                
            if endday == None: # if no endday was set use startday
                endday = startday
            elif endday < 0:
                endday = 0
                self.logError("--endday set beyond forecast limit, reset to minimum of 0")
            elif endday > self.MAX_DAY_NUMBER:
                endday = self.MAX_DAY_NUMBER
                self.logError("--endday set beyond forecast limit, reset to maximum of " + self.MAX_DAY_NUMBER)
                
            for daynumber in range(startday, endday + 1):
                
                if night == True:
                    output += self.getDatatypeFromSet(location, datatype, self.forecast_data[location].night[daynumber], shortweekday, imperial, beaufort, tempunit, speedunit, distanceunit, pressureunit, minuteshide, centeredwidth)
                else:
                    output += self.getDatatypeFromSet(location, datatype, self.forecast_data[location].day[daynumber], shortweekday, imperial, beaufort, tempunit, speedunit, distanceunit, pressureunit, minuteshide, centeredwidth)
                    
                if daynumber != endday:
                    output += self.getSpaces(spaces)

        return output

    def getTemplateItemOutput(self, template_text):
        
        # keys to template data
        LOCATION_KEY = "location"
        DATATYPE_KEY = "datatype"
        STARTDAY_KEY = "startday"
        ENDDAY_KEY = "endday"
        NIGHT_KEY = "night"
        SHORTWEEKDAY_KEY = "shortweekday"
        IMPERIAL_KEY = "imperial"
        BEAUFORT_KEY = "beaufort"
        HIDEUNITS_KEY = "hideunits"
        HIDEDEGREESYMBOL_KEY = "hidedegreesymbol"
        SPACES_KEY = "spaces"
        MINUTESHIDE_KEY = "minuteshide"
        CENTEREDWIDTH_KEY = "centeredwidth"
        
        location = self.options.location
        datatype = self.options.datatype
        startday = self.options.startday
        endday = self.options.endday
        night = self.options.night
        shortweekday = self.options.shortweekday
        imperial = self.options.imperial
        beaufort = self.options.beaufort
        hideunits = self.options.hideunits
        hidedegreesymbol = self.options.hidedegreesymbol
        spaces = self.options.spaces
        minuteshide = self.options.minuteshide
        centeredwidth = self.options.centeredwidth
        
        for option in template_text.split('--'):
            if len(option) == 0 or option.isspace():
                continue
            
            # not using split here...it can't assign both key and value in one call, this should be faster
            x = option.find('=')
            if (x != -1):
                key = option[:x].strip()
                value = option[x + 1:].strip()
                if value == "":
                    value = None
            else:
                key = option.strip()
                value = None
            
            try:
                if key == LOCATION_KEY:
                    location = value
                elif key == DATATYPE_KEY:
                    datatype = value
                elif key == STARTDAY_KEY:
                    startday = int(value)
                elif key == ENDDAY_KEY:
                    endday = int(value)
                elif key == NIGHT_KEY:
                    night = True
                elif key == SHORTWEEKDAY_KEY:
                    shortweekday = True
                elif key == IMPERIAL_KEY:
                    imperial = True
                elif key == BEAUFORT_KEY:
                    beaufort = True
                elif key == HIDEUNITS_KEY:
                    hideunits = True
                elif key == HIDEDEGREESYMBOL_KEY:
                    hidedegreesymbol = True
                elif key == SPACES_KEY:
                    spaces = int(value)
                elif key == MINUTESHIDE_KEY:
                    if value != None:
                        minuteshide = int(value)
                    else:
                        minuteshide = -1
                elif key == CENTEREDWIDTH_KEY:
                    centeredwidth = value
                else:
                    self.logError("Unknown template option: " + option)

            except (TypeError, ValueError):
                self.logError("Cannot convert option argument to number: " + option)
                return u""
                
        if datatype != None:
            return self.getDatasetOutput(location, datatype, startday, endday, night, shortweekday, imperial, beaufort, hideunits, hidedegreesymbol, spaces, minuteshide, centeredwidth)
        else:
            self.logError("Template item does not have datatype defined")
            return u""

    def getOutputFromTemplate(self, template):
        output = u""
        end = False
        a = 0
        
        # a and b are indexes in the template string
        # moving from left to right the string is processed
        # b is index of the opening bracket and a of the closing bracket
        # everything between b and a is a template that needs to be parsed
        while not end:
            b = template.find('[', a)
            
            if b == -1:
                b = len(template)
                end = True
            
            # if there is something between a and b, append it straight to output
            if b > a:
                output += template[a : b]
                # check for the escape char (if we are not at the end)
                if template[b - 1] == '\\' and not end:
                    # if its there, replace it by the bracket
                    output = output[:-1] + '['
                    # skip the bracket in the input string and continue from the beginning
                    a = b + 1
                    continue
                    
            if end:
                break
            
            a = template.find(']', b)
            
            if a == -1:
                self.logError("Missing terminal bracket (]) for a template item")
                return u""
            
            # if there is some template text...
            if a > b + 1:
                output += self.getTemplateItemOutput(template[b + 1 : a])
            
            a = a + 1

        return output

    def writeOutput(self):
        if self.options.template != None:
            #load the file
            try:
                fileinput = codecs.open(self.options.template, encoding='utf-8')
                template = fileinput.read()
                fileinput.close()
            except Exception, e:
                self.logError("Error loading template file: " + e.__str__())
            else:
                output = self.getOutputFromTemplate(template)
        else:
            output = self.getDatasetOutput(self.options.location, self.options.datatype, self.options.startday, self.options.endday, self.options.night, self.options.shortweekday, self.options.imperial, self.options.beaufort, self.options.hideunits, self.options.hidedegreesymbol, self.options.spaces, self.options.minuteshide, self.options.centeredwidth)
            
        print output.encode("utf-8")

    def logInfo(self, text):
        if self.options.verbose == True:
            print >> sys.stdout, "INFO: " + text

        if self.options.infologfile != None:
            datetimestamp = datetime.now().strftime("%Y-%m-%d %H:%M:%S") 
            fileoutput = open(self.options.infologfile, "ab")
            fileoutput.write(datetimestamp+" INFO: "+text+"\n")
            fileoutput.close()
            
    def logError(self, text):
        print >> sys.stderr, "ERROR: " + text
        
        if self.options.errorlogfile != None:
            datetimestamp = datetime.now().strftime("%Y-%m-%d %H:%M:%S") 
            fileoutput = open(self.options.errorlogfile, "ab")
            fileoutput.write(datetimestamp+" ERROR: "+text+"\n")
            fileoutput.close()

    def getText(self, parentNode, name):
        try:
            node = parentNode.getElementsByTagName(name)[0]
        except IndexError:
            raise Exception, "Data element <%s> not present under <%s>" % (name, parentNode.tagName)

        rc = ""
        for child in node.childNodes:
            if child.nodeType == child.TEXT_NODE:
                rc = rc + child.data
        return rc
    
    def getChild(self, parentNode, name, index = 0):
        try:
            return parentNode.getElementsByTagName(name)[index]
        except IndexError:
            raise Exception, "Data element <%s> is not present under <%s> (index %i)" % (name, parentNode.tagName, index)

    def getSpaces(self, spaces=1):
        string = u""
        for dummy in range(0, spaces):
            string = string + u" "
        return string

    def isNumeric(self, string):
        try:
            dummy = float(string)
            return True
        except:
            return False

    def convertCelsiusToFahrenheit(self, temp, dp=0):
        value = ((float(temp) * 9.0) / 5.0) + 32
        if dp == 0:
            return str(int(round(value,dp))) # lose the dp
        else:
            return str(round(value,dp))

    def convertKilometresToMiles(self, dist, dp=0):
        value = float(dist) * 0.621371192
        if dp == 0:
            return str(int(round(value,dp))) # lose the dp
        else:
            return str(round(value,dp))

    def convertKPHtoBeaufort(self, kph, dp=0):
        value = pow(float(kph) * 0.332270069, 2.0 / 3.0)
        if dp == 0:
            return str(int(round(value,dp))) # lose the dp
        else:
            return str(round(value,dp))
        
    def convertMillibarsToInches(self,mb,dp=0):
        value = float(mb)/33.8582
        if dp == 0:
            return str(int(round(value,dp))) # lose the dp
        else:
            return str(round(value,dp))
    
    def getWindLevel(self, speed):
        beaufort = self.convertKPHtoBeaufort(speed)
        if beaufort < 4:
            return 0
        elif beaufort < 7:
            return 1
        elif beaufort < 10:
            return 2
        else:
            return 3

    def getHoursMinutesStringFromSeconds(self,seconds):
        time = int(seconds)
        hours, time = divmod(time, 60*60)
        minutes, seconds = divmod(time, 60)
        output = str(hours).rjust(2,"0") + ":" + str(minutes).rjust(2,"0")
        return output
    
def main():

    parser = CommandLineParser()
    (options, args) = parser.parse_args()

    if options.version == True:
        
        print >> sys.stdout,"conkyForecast v.2.01"
        
    else:
        
        if options.verbose == True:
            print >> sys.stdout, "*** INITIAL OPTIONS:"
            print >> sys.stdout, "    location:", options.location
            print >> sys.stdout, "    datatype:", options.datatype
            print >> sys.stdout, "    start day:", options.startday
            print >> sys.stdout, "    end day:", options.endday
            print >> sys.stdout, "    spaces:", options.spaces
            print >> sys.stdout, "    template:", options.template
            print >> sys.stdout, "    locale:", options.locale
            print >> sys.stdout, "    imperial:", options.imperial
            print >> sys.stdout, "    beaufort:", options.beaufort
            print >> sys.stdout, "    night:", options.night
            print >> sys.stdout, "    shortweekday:", options.shortweekday
            print >> sys.stdout, "    hideunits:", options.hideunits
            print >> sys.stdout, "    hidedegreesymbol:", options.hidedegreesymbol
            print >> sys.stdout, "    minuteshide:", options.minuteshide
            print >> sys.stdout, "    centeredwidth:", options.centeredwidth
            print >> sys.stdout, "    refetch:", options.refetch
            print >> sys.stdout, "    verbose:", options.verbose
            print >> sys.stdout, "    errorlogfile:",options.errorlogfile
            print >> sys.stdout, "    infologfile:",options.infologfile        
    
        forecastinfo = ForecastInfo(options)
        forecastinfo.writeOutput()

if __name__ == '__main__':
    main()
    sys.exit()
    

```Conditions.sh
```

#!/bin/bash

#Czyta dane z pliku
cnd=$(cat ~/weather)

#Ustawia czcionk&#281; obrazkow&#261;, odpowiadaj&#261;c&#261; aktualnej pogoda.  
if echo "$cnd" | grep -E -i -q 'partly cloudy'; then
    echo 'c'
elif echo "$cnd" | grep -E -i -q 'fair|sunny'; then
    echo 'A'
elif echo "$cnd" | grep -E -i -q 'cloudy'; then
    echo 'e'
elif echo "$cnd" | grep -E -i -q 'storm|thunder'; then
    echo 'i'
elif echo "$cnd" | grep -E -i -q 'snow'; then
    echo 'k'
elif echo "$cnd" | grep -E -i -q 'rain'; then
    echo 'h'
elif echo "$cnd" | grep -E -i -q 'shower'; then
    echo 'g'
fi

```- conkyForecast.template
```

${voffset -10}${alignr 56}${color2}${font ConkyWeather:style=Bold:size=40}[--datatype=WF]${font}${color}
${voffset -50}${color2}${font Weather:size=40}y${font}${color2}  ${voffset -38}${color2}${font Arial Black:size=26}[--datatype=HT]${font}${color}
${voffset 2}
${voffset 0}${goto 13}[--datatype=DW --startday=1 --shortweekday] ${goto 59}[--datatype=DW --startday=2 --shortweekday] ${goto 105}[--datatype=DW --startday=3 --shortweekday] ${goto 150}[--datatype=DW --startday=4 --shortweekday]
${voffset 0}${color2}${font ConkyWeather:size=28}[--datatype=WF --startday=1 --endday=4 --spaces=1]${font}${color}
${voffset 0}${goto 8}[--datatype=HT --startday=1 --hideunits --centeredwidth=3]/[--datatype=LT --startday=1 --hideunits --centeredwidth=3] ${goto 53}[--datatype=HT --startday=2 --hideunits --centeredwidth=3]/[--datatype=LT --startday=2 --hideunits --centeredwidth=3] ${goto 98}[--datatype=HT --startday=3 --hideunits --centeredwidth=3]/[--datatype=LT --startday=3 --hideunits --centeredwidth=3] ${goto 145}[--datatype=HT --startday=4 --hideunits --centeredwidth=3]/[--datatype=LT --startday=4 --hideunits --centeredwidth=3]
${voffset -10}

```Pagodinka.sh
```

# # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # #
#                                                            #
# Pogodynka 0.2.2.1                                                    #
#                                                            #
# azhag (azhag@bsd.miki.eu.org)                                                #
#                                                            # 
# # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # #
#                                                            #
# Skrypt pobiera informacje o stanie pogody ze strony weather.yahoo.com dla danego miasta, nastêpnie formatuje je i    #
# wy¶wietla na ekranie. Skrypt mo¿e byæ wykorzystany np. w conky'm, xosd, *message.                    #
#                                                            #
# # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # #
#                                                            #
# Wymagane aplikacje:                                                    #
# w3m - tekstowa przegl±darka www                                            #
#                                                            #
# # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # #
#                                                            # 
# Przed u¿yciem skryptu nale¿y ustaliæ zmienne "sciezka" oraz "kod".                            #
#                                                            #
# Aby ustaliæ kod swojego miasta wejd¿ na stronê http://weather.yahoo.com/ i wyszukaj tam swoje miasto. Kodem jest     #
# koñcówka linka z pogod± naszego miasta.                                        #    
#                                                            #
# Przyk³adowe kody:                                                    #
# Warszawa - PLXX0028                                                    #
# Kraków - PLXX0012                                                    #
# Gdañsk - PLXX0005                                                    #
# Szczecin - PLXX0025                                                    #
#                                                            #
# Informacjê jak± wy¶wietla skrypt mo¿na zmieniæ haszuj±c odpowiednie linijki w sekcji "formatowanie informacji        #
# wyj¶ciowej". Mo¿na równie¿ w ³atwy sposób sformatowaæ w³asny wynik u¿ywaj±c dostepnych zmiennych.            #
#                                                            #
# # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # #

#!/bin/bash

# Katalog, w którym znajduje siê skrypt
sciezka=~./conky

# Kod miasta
kod=ARBA0054

plik=~/weather
# sprawdzenie czy serwer jest dostêpny
#if [ `ping -c1 216.109.126.70 | grep from | wc -l` -eq 0 ]
 # then
    #echo "Serwis niedostêpny"
  #else
    # pobieranie informacji
     w3m -dump http://weather.yahoo.com/forecast/"$kod"_c.html | grep -A21 "Current" | sed 's/DEG/°/g' > $plik

    # ustalenie warto¶ci zmiennych
    stan=`head -n3 $plik | tail -n1`
    temp=`tail -n1 $plik | awk '{print $1}'`
    tempo=`head -n6 $plik | tail -n1`
    cisn=`head -n8 $plik | tail -n1`
    wiatr=`head -n16 $plik | tail -n1`
    wilg=`head -n10 $plik | tail -n1`
    wsch=`head -n18 $plik | tail -n1`
    zach=`head -n20 $plik | tail -n1`
    if [ `cat "$sciezka"/pogodynka.sh | grep -x "# $stan" | wc -l` -eq 0 ]
      then
        stanpl=$stan
      else
        stanpl=`cat "$sciezka"/pogodynka.sh | grep -xA1 "# $stan" | tail -n1 | awk '{print $2,$3,$4,$5,$6,$7}'`
    fi
    
    # formatowanie informacji wyj¶ciowej
    # dostêpne zmienne:
    # $stan        opis stanu po angielsku
    # $stanpl    opis stanu po polsku
    # $temp        temperatura powietrza
    # $tempo    temperatura odczuwalna
    # $cisn        ci¶nienie atmosferyczne
    # $wiatr    kierunek, si³a wiatru
    # $wilg        wilgotno¶æ powietrza
    # $wsch        godzina wschodu s³oñca
    # $zach        godzina zachodu s³oñca
    
    #echo $stan
    #echo $stanpl
    echo $temp C  /  $tempo C
    #echo Cisnienie $cisn hPa
    #echo $wiatr
    #echo Wilgotno¶æ: $wilg
    #echo Wschód S³oñca: $wsch
    #echo Zachód S³oñca: $zach
    #echo $stanpl, $temp C

#fi

# # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # #
#
# T³umaczenia stanów pogody.
# Je¿eli zauwa¿ysz pogodê, której nie ma jeszcze na liscie daj mi znaæ na maila podanego na górze. Z góry dziêkujê.
#
# Sunny
# S³onecznie
# Clear
# Przejrzy¶cie
# Fair
# Pogodnie
# Sunny/Windy
# S³onecznie/Wiatr
# Clear/Windy
# Przejrzy¶cie/Wiatr
# Fair/Windy
# Przejrzy¶cie/Wiatr
# Windy
# Wiatr
#
# Partly Cloudy
# Czê¶ciowo pochmurnie
# Partly Cloudy and Windy
# Czê¶ciowo pochmurnie/Wiatr
# Partly Sunny
# Czê¶ciowo s³onecznie
# Mostly Clear
# Przew. przejrzy¶cie
# Partly Sunny/Windy
# Czê¶ciowo s³onecznie/Wiatr
# Mostly Clear/Windy
# Przew. przejrzy¶cie/Wiatr
# Mostly Sunny
# Przew. p³onecznie
# Mostly Sunny/Windy
# Przew. s³onecznie/Wiatr
# Scattered Clouds
# Rzadkie ob³oki
#
# Cloudy
# Pochmurnie
# Overcast
# Ca³k. zachmurzenie
# Cloudy/Windy
# Pochmurnie/Wiatr
# Overcast/Windy
# Ca³k. zachmurzenie/Wiatr
# Mostly Cloudy/Windy
# Przew. pochmurnie/Wiatr
# Mostly Cloudy
# Przew. pochmurnie
# Am Clouds / Pm Sun
# Ranek pochmurny/S³oneczne popo³udnie
#
# Light Drizzle
# Lekka m¿awka
# Drizzle
# M¿awka
# Light Rain
# Lekki deszcz
# Rain
# Deszcz
# Heavy Rain
# Ulewa
# Light Rain/Fog
# Lekki deszcz/Mg³a
# Rain/Fog
# Deszcz/Mg³a
# Light Drizzle/Windy
# Lekka m¿awka/Wiatr
# Drizzle/Windy
# M¿awka/Wiatr
# Light Rain/Windy
# Lekki deszcz/Wiatr
# Rain/Windy
# Deszcz/Wiatr
# Rain / Wind
# Deszcz/Wiatr
# Heavy Rain/Windy
# Ulewa/Wiatr
# AM Light Rain
# Ranny lekki deszcz
# PM Light Rain
# Popo³udniowy lekki deszcz
# Pm Light Rain
# Popo³udniowy lekki deszcz
# AM Light Rain/Windy
# Ranny lekki deszcz/Wiatr
# PM Light Rain/Windy
# Popo³udniowy lekki deszcz/Wiatr
#
# Rain Shower
# Przelotny deszcz
# Shower
# Przelotna ulewa
# Showers
# Przelotna ulewa
# Heavy Rain Shower
# Mocna ulewa
# Heavy Rain Shower/Windy
# Mocna ulewa/Wiatr
# Light Rain Shower
# Lekka ulewa
# AM Shower
# Poranna ulewa
# AM Showers
# Poranna ulewa
# Am Showers
# Poranna ulewa
# AM Showers / Wind
# Poranna ulewa/Wiatr
# PM Shower
# Popo³udniowa ulewa
# PM Showers / Wind
# Popo³udniowe ulewy/Wiatr
# Few Showers / Wind
# Przelotne deszcze/Wiatr
# Showers / Wind
# Deszcze/Wiatr
# PM Showers
# Popo³udniowe ulewy
# Pm Showers
# Popo³udniowe ulewy
# Scattered Shower
# Rozleg³a ulewa
# Scattered Showers
# Rozleg³e ulewy
# Scatter Showers
# Rozleg³e ulewy
# Rain Shower/Windy
# Przelotny deszcz/Wiatr
# Shower/Windy
# Przelotna ulewa/Wiatr
# Light Rain Shower/Windy
# Lekka ulewa/Wiatr
# AM Shower/Windy
# Poranna ulewa/Wiatr
# PM Shower/Windy
# Popo³udniowa ulewa/Wiatr
# Scattered Shower/Windy
# Rozleg³a ulewa/Wiatr
# Scatter Showers / Wind
# Rozleg³e ulewy/Wiatr
# Few Showers
# Mo¿liwe ulewy
# Few Showers/Windy
# Mo¿liwe ulewy/Wiatr
# Showers in the Vicinity
# Pobliskie ulewy
#
# Light Snow
# Lekki ¶nieg
# Snow
# &#352;nieg
# Snow / Wind
# &#352;nieg/Wiatr
# Heavy Snow
# Mocny ¶nieg
# Light Snow Pellets
# Lekki grad ¶nie¿ny
# Snow Pellets
# Grad ¶nie¿ny
# Light Ice Pellets
# Lekki grad lodowy
# Ice Pellets
# Grad lodowy
# Wintery Weather
# Zimowa pogoda
# Light Freezing Rain
# Lekki zamarzaj±y deszcz
# Freezing Rain
# Zamarzaj±cy deszcz
# Flurries/Windy
# Zamiecie/Wiatr
# Light Flurries/Windy
# Lekkie zamiecie/Wiatr
# Light Snow/Windy
# Lekki ¶nieg/Wiatr
# Light Snow / Wind
# Lekki ¶nieg/Wiatr
# Snow/Windy
# &#352;nieg/Wiatr
# Heavy Snow/Windy
# Mocny ¶nieg/Wiatr
# Light Snow Pellets/Windy
# Lekki grad ¶nie¿ny/Wiatr
# Snow Pellets/Windy
# Grad ¶nie¿ny/Wiatr
# Light Ice Pellets/Windy
# Lekki grad lodowy/Wiatr
# Ice Pellets/Windy
# Grad lodowy/Wiatr
# Light Freezing Rain/Windy
# Lekki zamarzaj±cy deszcz/Wiatr
# Freezing Rain/Windy
# Zamarzaj±cy deszcz/Wiatr
# Wintery Mix
# Miks zimowy
# Light Snow Grains
# Lekkie granulki ¶niegu
# Snow Grains
# Granulki ¶niegu
# Rain/Snow
# &#352;nieg z deszczem
# Rain / Snow Showers
# Deszcz ze ¶niegiem
# Rain / Snow
# Deszcz ze ¶niegiem
# Rain / Thunder
# Deszcz / Burza
# Rain/Show/Windy
# &#352;nieg z deszczem/Wiatr
# Rain / Snow / Wind
# &#352;nieg z deszczem/Wiatr
# Light Rain/Freezing Rain
# Lekki deszcz/Zamarzaj±cy deszcz
# Rain/Freezing Rain
# Deszcz/Zamarzaj±cy deszcz
# Light Rain/Freezing Rain/Windy
# Lekki deszcz/Zamarzaj±cy Deszcz/Wiatr
# Rain/Freezing Rain/Windy
# Deszcz/Zamarzaj±cy deszcz/Wiatr
# AM Snow
# Poranny ¶nieg
# PM Snow
# Popo³udniowy ¶nieg
# AM Light Snow
# Poranny lekki ¶nieg
# PM Light Snow
# Popo³udniowy lekki ¶nieg
# Ice Crystals
# Kryszta³ki lodu
# Ice Crystals/Windy
# Kryszta³ki lodu/Wiatr
# 
# Snow Showers
# Burze ¶nie¿ne
# Snow Shower
# Burza ¶nie¿na
# Heavy Snow Shower
# Mocna burza ¶nie¿na
# Heavy Snow Shower/Windy
# Mocna burza ¶nie¿na/Wiatr
# PM Snow Showers
# Popo³udniowe burze ¶nie¿ne
# AM Snow Showers
# Poranne burze ¶nie¿ne
# Rain/Snow Showers
# Deszcz/Burze ¶nie¿ne
# Snow Showers/Windy
# Burze ¶nie¿ne/Wiatr
# PM Snow Showers/Windy
# Popo³udniowe burze ¶nie¿ne/Wiatr
# AM Snow Showers/Windy
# Poranne burze ¶nie¿ne/Wiatr
# Rain/Snow Showers/Windy
# Deszcz/Burze ¶nie¿ne/Wiatr
# Light Snow Showers
# Lekkie burze ¶nie¿ne
# Light Snow Shower
# Lekka burza ¶nie¿na
# Light Snow Showers/Windy
# Lekkie burze ¶nie¿ne/Wiatr
# Flurries
# Zamiecie
# Light Flurries
# Lekkie zamiecie
# Scattered Flurries
# Rozleg³e zamiecie
# Few Flurries
# Mo¿liwe zamiecie
# Few Flurries/Windy
# Mo¿liwe zamiecie/Wiatr
# Scattered Snow Showers
# Rozleg³e burze ¶nie¿ne
# Scattered Snow Showers/Windy
# Rozleg³e burze ¶nie¿ne/Wiatr
# Few Snow Showers
# Mo¿liwe burze ¶nie¿ne
# Few Snow Showers/Windy
# Mo¿liwe burze ¶nie¿ne/Wiatr
# Freezing Drizzle
# Marzn±ca m¿awka
# Light Freezing Drizzle
# Lekka marzn±ca m¿awka
# Freezing Drizzle/Windy
# Marzn±ca m¿awka/Wiatr
# Light Freezing Drizzle/Windy
# Lekka marzn±ca m¿awka/Wiatr
# Drifting Snow
# Zawieja ¶nie¿na
# 
# Thunderstorms
# Burze
# T-storms
# Burze
# T-Storms
# Burze
# T-Storm
# Burza
# Scattered Thunderstorms
# Rozleg³e burze
# Scattered T-Storms
# Rozleg³e burze
# Thunderstorms/Windy
# Burze/Wiatr
# Scattered Thunderstorms/Windy
# Rozleg³e burze/Wiatr
# Rain/Thunder
# Deszcz/Grzmoty
# Light Thunderstorms/Rain
# Lekkie burze/Deszcz
# Thunderstorms/Rain
# Burze/Deszcz
# Light Rain with Thunder
# Lekki deszcz z grzmotami
# Rain with Thunder
# Deszcz z grzmotami
# Thunder in the Vicinity
# Pobliskie burze
# 
# Fog
# Mg³a
# Haze
# Lekka mg³a
# Mist
# Lekkie zamglenie
# Fog/Windy
# Mg³a/Wiatr
# Haze/Windy
# Lekka Mg³a/Wiatr
# Mist/Windy
# Lekkie zamglenie/Wiatr
# Partial Fog
# Czê¶ciowa mg³a
# Smoke
# Gêsta mg³a
# Foggy
# Mglisto
# AM Fog/PM Sun
# Ranna mg³a/Popo³udniowe s³oñce
# Shallow Fog
# P³ytka mg³a
# 
# Blowing Dust
# Zawieja py³owa
# Blowing Sand
# Zawieja piaskowa
# Duststorm
# Burza piaskowa
# Wind
# Wiatr
# Widespread Dust/Windy
# Rozleg³e zamiecie/Wiatr
# Widespread Dust
# Rozleg³e zamiecie
# Low Drifting Sand
# Zawieja piaskowa
# 
# Data Not Available
# Dane niedostêpne
# N/A
# N/D
# N/a
# N/d


```

---

### Post by Bruce M. on 2010-01-04
> **leonardomdq said:**
> Muchas gracias Bruce por la respuesta y por tu conky que me pasaste.

En este que estoy configurando ahora me falta que me aparezca la temperatura y lo raro que es de noche y aparece un sol de color negro, te dejo una captura que me estara faltando?

```

.
.
.
default_color black
.
.
.
.
.
TEXT
.
.
.
.
.
.
.
.
${voffset -20}${color}${font led:size=9}WEATHER ${font}$hr
${color}${font weather:size=70}
.
.
.
.
.
.
.
.
.
```

Sí, normal, está utilizando el color negro con una "weather font"

El sol significa: cielos despejados

Voy a arreglar el código de mañana

Buenos noches
Bruce

---

### Post by leonardomdq on 2010-01-04
Lo extraño que sigue sin decirme la temperatura al lado del dibujo del sol.

Saludos y gracias Bruce

---

### Post by Bruce M. on 2010-01-05
> **leonardomdq said:**
> Lo extraño que sigue sin decirme la temperatura al lado del dibujo del sol.

Saludos y gracias Bruce

Estoy trabajando con su conky ahora, me dan menos de 90 minutos, y yo te tengo aquí.

51 munutos.

Conky:
```
#!/usr/bin/conky -d -c
##    .conkyrc configuration
alignment top_right
background yes
border_margin 5
border_width 5
cpu_avg_samples 2
default_color black
double_buffer yes
draw_borders no
draw_graph_borders no
draw_outline no
draw_shades no
gap_x 5
gap_y 40
max_specials 1024
max_user_text 10000
maximum_width 180
minimum_size 850
net_avg_samples 2
no_buffers yes
override_utf8_locale yes
own_window yes
own_window_default_color
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_transparent yes
own_window_type override     ## normal
pad_percents 2            # to co nizej, miejsc po przecinku
short_units yes            # krotka wersja podawania wielkosci dyskow np. 612.21M/3.80G
stippled_borders 3
text_buffer_size 8000
total_run_times 0
update_interval 1.0
uppercase no
use_spacer right
use_xft yes
xftalpha 0.75
xftfont sans:size=7
default_color black

TEXT
${color}${font OpenLogos:size=40} u t
${color}${goto 10}${font DejaVu Sans Mono:size=44}${time %H}${font DejaVu Sans Mono:size=20}${voffset -25}'${time %M}${font DejaVu Sans Mono:size=8}${voffset -12}${time %S}
${color}${goto 85}${voffset 10}${font :size=8}${time %A}
${color}${goto 85}${voffset 1}${font :size=8}${time %d %B %Y}
${color}${font RsbillsDng:size=14}O${font}${font DejaVu Sans Mono:size=8}${execpi 3600 DJS=`date +%_d`; cal -m | sed '1d' | sed '/./!d' | sed 's/$/                     /' | fold -w 21 | sed -n '/^.\{21\}/p' | sed 's/^/${alignc} /' | sed /" $DJS "/s/" $DJS "/" "'${color}'"$DJS"'${color}'" "/}${font}

${voffset -20}${color}${font led:size=9}WEATHER ${font}$hr
${color}${execpi 3600 conkyForecast --location=ARBA0054 --template=/home/bruloo/Conky/Test/leonardo/leonardo.template}
${font weather:size=28}x ${font}HDD #${execi 1 ~/.conky/hddmonit.sh}°C${font}


${voffset -20}${color}${font led:size=9}SISTEMA ${font}$hr
${color}${sysname} Kernel: ${alignr}$kernel
${color}Conky:${alignr}${conky_version}


${voffset -10}${color}${font led:size=9}CPU ${font}$hr
${color}Core 1:  ${cpu cpu1}% $alignr ${freq_g (1)} GHz / ${exec sensors | grep "Core 0" | cut --bytes=14-21}
#${color}Core 2:  ${cpu cpu2}% $alignr ${freq_g (2)} GHz / ${exec sensors | grep "Core 1" | cut --bytes=14-21}

${voffset -7}${color}${font}NAME ${goto 90}PID${goto 120}CPU% ${alignr}MEM%
${color}${font :size=6}${goto 9}${top name 1}${goto 85}${top pid 1}${goto 120}${top cpu 1}${goto 156}${top mem 1}
${color}${font :size=6}${goto 9}${top name 2}${goto 85}${top pid 2}${goto 120}${top cpu 2}${goto 156}${top mem 2}
${color}${font :size=6}${goto 9}${top name 3}${goto 85}${top pid 3}${goto 120}${top cpu 3}${goto 156}${top mem 3}


${voffset -6}${color}${font led:size=9}MEMORIA / HDD / USB ${font}$hr
${color}ram: ${mem} / ${memmax} ${alignr} ${memperc}%
${color}swap: ${swap} / ${swapmax} ${alignr} ${swapperc}%
${color}root: ${fs_used /} / ${fs_size /} ${alignr} ${fs_used_perc /}%
${color}home: ${fs_used /home} / ${fs_size /home} ${alignr} ${fs_used_perc /home}%
${color}${voffset -12}??#${execpi 5 ~/.conky/usb_nowe.sh}


${voffset -10}${color}${font led:size=9}NETWORK ${font}$hr
${color}gateway IP: ${alignr}${gw_ip}
${color}local IP: $alignr${addr eth0}
${color}public IP: $alignr${execi 60 ~/.conky/ip.sh}

${voffset 5}${color}${goto 10}${font pizzadude bullets:size=16}S${font}${color}${voffset -12}${goto 40}Down: ${downspeed eth0}kb/s ${color}
${goto 40}Day: ${totaldown eth0}${voffset -12}${alignr}${downspeedgraph eth0 25,50 64574e 64574e}
${voffset -13}${goto 40}Month: ${execi 300 vnstat -m | grep "`date +"'%y"`" | tail -1 | awk '{print $3 $4}'}

${goto 10}${font pizzadude bullets:size=16}M${font}$color${voffset -12}${goto 40}Up: ${upspeed eth0}kb/s${color}
${goto 40}Day: ${totalup eth0}${voffset -12}${alignr}${upspeedgraph eth0 25,50 64574e 64574e}
${voffset -13}${goto 40}Month: ${execi 300 vnstat -m | grep "`date +"'%y"`" | tail -1 | awk '{print $6 $7}'}

${color}${if_mpd_playing}${font led:size=9}MPD ${font}${mpd_status} $hr
${color}${alignc}${mpd_artist} - "${mpd_title}"
${color}${alignc}${mpd_album}
${color}${alignc}${mpd_bar 3,150}
${color}${alignc}${mpd_elapsed}/${mpd_length}${endif}
```

**leonardo.template**
```
${goto 120}${font Zekton:size=20}[--datatype=HT]${font}${image [--datatype=WI] -p 0,220 -s 90x90}
${goto 120} ST: [--datatype=LT --night]
${goto 120}Mín: [--startday=0 --datatype=LT --night]
${goto 120}Máx: [--startday=0 --datatype=HT --night]
${font Zekton:size=10}[--datatype=CC]${font}
```

**[COLOR="Red"]OjO[/COLOR]** con:  ${color}${execpi 3600 conkyForecast --location=ARBA0054 --template=***/home/bruloo/Conky/Test/leonardo/leonardo.template***}

asegúrese de cambiar la ubicación.


**[COLOR="Red"]OjO[/COLOR]** con este: conkyforecast.config (/home/leonardo/conkyforecast.config)

es: /home/leonardo/**[COLOR="Red"][SIZE="5"].[/SIZE][/COLOR]**conkyforecast.config) = oculto **y tambien:**

> DATE_FORMAT = %Y-%m-%d
LOCALE = ARBA0054 **[COLOR="Red"]<<-- error[/COLOR]**
XOAP_PARTNER_ID = XXXXXXXXXXX
XOAP_LICENCE_KEY = XXXXXXXXXXX

> DATE_FORMAT = %Y-%m-%d
LOCALE = es
XOAP_PARTNER_ID = XXXXXXXXXXX
XOAP_LICENCE_KEY = XXXXXXXXXXX

"LOCALE" es para la salida de idioma - es = español

Con este conky y leonardo.template no es necesario:
- Conditions.sh
- Pagodinka.sh

Que tengas un buen día
Bruce

---

### Post by leonardomdq on 2010-01-05
Muchas gracias Bruce!!! quedo barbaro :D

Bruce hay una cosa que no pude corregir, donde va la linea de gmail me muestra en color blanco los emails recibidos y el color default es negro :confused:
```

${color}Gmail:${alignr}${execpi 300 python ~/scripts/gmail_parser.py xxxxxxx xxxxxxx 3}

```

Quiero agregarle abajo del todo el script de Rhythmbox con la guitarra, dejo un conky con el ejemplo para asi se entiende lo que quiero agregar
[IMG]http://i46.tinypic.com/2pov24m.png[/IMG]

---

### Post by Bruce M. on 2010-01-05
> **leonardomdq said:**
> Muchas gracias Bruce!!! quedo barbaro :D

Bruce hay una cosa que no pude corregir, donde va la linea de gmail me muestra en color blanco los emails recibidos y el color default es negro :confused:
```

${color}Gmail:${alignr}${execpi 300 python ~/scripts/gmail_parser.py xxxxxxx xxxxxxx 3}

```

Quiero agregarle abajo del todo el script de Rhythmbox con la guitarra, dejo un conky con el ejemplo para asi se entiende lo que quiero agregar
[IMG]http://i46.tinypic.com/2pov24m.png[/IMG]

Bueno muéstrame **gmail_parser.py** es probable que haya un código de color en el archivo.

También quite todos los $(color) de conky, si quieres que todo sea negro no es necesario.

También la imagen debe elevarse un poco en **leonardo.template** de esta parte de la línea:
```
${image [--datatype=WI] -p 0,220 -s 90x90}
```
prueba con 200 o 190
```
${image [--datatype=WI] -p 0,200 -s 90x90}
```
```
${image [--datatype=WI] -p 0,190 -s 90x90}
```

¿Porque? algunas imágenes muestran más abajo en la pantalla: la niebla, por ejemplo.


Bueno: Rhythmbox - Yo no lo uso (tenemos un equipo de música), pero el programa está aquí: [Conky Rhythmbox Python Script]("http://ubuntuforums.org/showthread.php?t=928168"). Voy a ayudar en todo lo que puedo, pero no hago promesas. :guitar:

¿Tenes un imagine de una guitarra?

Que tengas un buen día
Bruce

---

### Post by Bruce M. on 2010-01-05
**[SIZE="5"]@ leonardomdq[/SIZE]**

:guitar: :guitar:
Bruce

---

### Post by leonardomdq on 2010-01-05
Este es **gmail_parser.py**
```

## check-gmail.py -- A command line util to check GMail -*- Python -*-
## modified to display mailbox summary for conky

# ======================================================================
# Copyright (C) 2006 Baishampayan Ghose <b.ghose@ubuntu.com>
# Modified 2008 Hunter Loftis <hbloftis@uncc.edu>
# Time-stamp: Mon Jul 31, 2006 20:45+0530
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License version 2 as
# published by the Free Software Foundation.
# ======================================================================

import sys
import urllib             # For BasicHTTPAuthentication
import feedparser         # For parsing the feed
from textwrap import wrap

_URL = "https://mail.google.com/gmail/feed/atom"

uname = sys.argv[1]
password = sys.argv[2]
maxlen = sys.argv[3]

urllib.FancyURLopener.prompt_user_passwd = lambda self, host, realm: (uname, password)
    
def auth():
    '''The method to do HTTPBasicAuthentication'''
    opener = urllib.FancyURLopener()
    f = opener.open(_URL)
    feed = f.read()
    return feed


def readmail(feed, maxlen):
    '''Parse the Atom feed and print a summary'''
    atom = feedparser.parse(feed)
    print '${color1} %s new email(s)\n' % (len(atom.entries))
    for i in range(min(len(atom.entries), maxlen)):
        print '          ${color2}%s' % atom.entries[i].title
#uncomment the following line if you want to show the name of the sender
#        print '          ${color2}%s' % atom.entries[i].author
    if len(atom.entries) > maxlen:
        print ' ${color}more...'

if __name__ == "__main__":
    f = auth()  # Do auth and then get the feed
    readmail(f, int(maxlen)) # Let the feed be chewed by feedparser

```

Bruce ya arregle la imagen del weather, era que le habia bajado el tamano de las fonts de 7 a 6.
La guitarra son unas fonts que se llaman **KR Katlings Eleven**

[[img]http://f.imagehost.org/t/0870/Pantallazo_8.jpg[/img]](http://f.imagehost.org/view/0870/Pantallazo_8)

---

### Post by Bruce M. on 2010-01-05
> **leonardomdq said:**
> Este es **gmail_parser.py**

Bruce ya arregle la imagen del weather, era que le habia bajado el tamano de las fonts de 7 a 6.
La guitarra son unas fonts que se llaman **KR Katlings Eleven**

Oooooooo bueno! Una nuevo font, gracias

[[img]http://f.imagehost.org/t/0870/Pantallazo_8.jpg[/img]](http://f.imagehost.org/view/0870/Pantallazo_8)

MIRA--->>> **#        print '          ${color2}%s' % atom**

El nuevo **gmail_parser.py** para vos solo: sin ${color}

```

## check-gmail.py -- A command line util to check GMail -*- Python -*-
## modified to display mailbox summary for conky

# ======================================================================
# Copyright (C) 2006 Baishampayan Ghose <b.ghose@ubuntu.com>
# Modified 2008 Hunter Loftis <hbloftis@uncc.edu>
# Time-stamp: Mon Jul 31, 2006 20:45+0530
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License version 2 as
# published by the Free Software Foundation.
# ======================================================================

import sys
import urllib             # For BasicHTTPAuthentication
import feedparser         # For parsing the feed
from textwrap import wrap

_URL = "https://mail.google.com/gmail/feed/atom"

uname = sys.argv[1]
password = sys.argv[2]
maxlen = sys.argv[3]

urllib.FancyURLopener.prompt_user_passwd = lambda self, host, realm: (uname, password)
    
def auth():
    '''The method to do HTTPBasicAuthentication'''
    opener = urllib.FancyURLopener()
    f = opener.open(_URL)
    feed = f.read()
    return feed


def readmail(feed, maxlen):
    '''Parse the Atom feed and print a summary'''
    atom = feedparser.parse(feed)
    print ' %s new email(s)\n' % (len(atom.entries))
    for i in range(min(len(atom.entries), maxlen)):
        print '          %s' % atom.entries[i].title
#uncomment the following line if you want to show the name of the sender
#        print '          %s' % atom.entries[i].author
    if len(atom.entries) > maxlen:
        print ' more...'

if __name__ == "__main__":
    f = auth()  # Do auth and then get the feed
    readmail(f, int(maxlen)) # Let the feed be chewed by feedparser

```

Que tengas un buen día
Bruce

---

### Post by leonardomdq on 2010-01-05
Mil gracias Bruce, solucionado lo del gmail_parser.py.

Saludos y gracias nuevamente.

---

### Post by Bruce M. on 2010-01-05
> **leonardomdq said:**
> Mil gracias Bruce, solucionado lo del gmail_parser.py.

Saludos y gracias nuevamente.

De nada.

Buenos noches.
Bruce

---

### Post by leonardomdq on 2010-01-11
Hola Bruce,  de la nada desaparecio de mi conky el conkyforecast
¿que podra ser?

Dejo una captura asi se entiendo lo que paso:
[[img]http://g.imagehost.org/t/0596/Pantallazo.jpg[/img]](http://g.imagehost.org/view/0596/Pantallazo)

Saludos

---

### Post by Bruce M. on 2010-01-11
> **leonardomdq said:**
> Hola Bruce,  de la nada desaparecio de mi conky el conkyforecast
¿que podra ser?

Dejo una captura asi se entiendo lo que paso:
[[img]http://g.imagehost.org/t/0596/Pantallazo.jpg[/img]](http://g.imagehost.org/view/0596/Pantallazo)

Saludos

OH OH!!!!

Todo bien aquí ...

muéstrame el archivo: ~/.conkyForecast.config - sin este información personal:

[B]XOAP_PARTNER_ID = xxxxxxxxxx
XOAP_LICENCE_KEY = xxxxxxxxxxxxx[/B]

muéstrame la línea de conky para el clima, como:
```
${execpi 3600 conkyForecast --location=ARDF0127 --template=/home/bruloo/Conky/scripts/OB_Weather.template}${font}
```

y el template.

Que tengas un buen día.
Bruce

---

### Post by leonardomdq on 2010-01-11
Listo Bruce lo solucione reinstalando conkyforecast y salio andando conky nuevamente.

Muchas gracias.

---

### Post by Bruce M. on 2010-01-11
> **leonardomdq said:**
> Listo Bruce lo solucione reinstalando conkyforecast y salio andando conky nuevamente.

Muchas gracias.

:KS:KS:KS:KS:KS

Perfecto!

---

### Post by leonardomdq on 2010-01-11
> **Bruce M. said:**
> :KS:KS:KS:KS:KS

Perfecto!
Me olvide de consultarte algo, quiero que salgan los dias, lunes, martes, miercoles etc etc arriba del calendario, como seria la linea a agregar?

saludos

---

### Post by Bruce M. on 2010-01-11
> **leonardomdq said:**
> Me olvide de consultarte algo, quiero que salgan los dias, lunes, martes, miercoles etc etc arriba del calendario, como seria la linea a agregar?

saludos

Tengo esto:

```
TEXT
${font OpenLogos:size=40} u t
${goto 10}${font DejaVu Sans Mono:size=44}${time %H}${font DejaVu Sans Mono:size=20}${voffset -25}'${time %M}${font DejaVu Sans Mono:size=8}${voffset -12}${time %S}
${goto 85}${voffset 10}${font :size=8}${time %A}
${goto 85}${voffset 1}${font :size=8}${time %d %B %Y}
${font RsbillsDng:size=14}O${font}${font DejaVu Sans Mono:size=8}${execpi 3600 DJS=`date +%_d`; cal -m | sed '1d' | sed '/./!d' | sed 's/$/                     /' | fold -w 21 | sed -n '/^.\{21\}/p' | sed 's/^/${alignc} /' | sed /" $DJS "/s/" $DJS "/" "'${color}'"$DJS"'${color}'" "/}${font}
- - - - -
${goto 40}${font DejaVu Sans Mono:size=8}Do Lu Ma Mi Ju Vi Sa
${voffset 2}${color4}${execpi 60 DJS=`date +%_d`; cal | sed '2d' | sed '1d'  | sed '/./!d' | sed 's/$/                     /' | fold -w 21 | sed -n '/^.\{21\}/p' | sed 's/^/${goto 30} /' | sed /" $DJS "/s/" $DJS "/" "'${color2}'"$DJS"'${color4}'" "/}${font}
- - - - -
```

Que tengas un buen día
Bruce

---

### Post by leonardomdq on 2010-01-11
Quedo buenisimo asi , muchas gracias nuevamente :KS

Saludos Bruce :P

---

### Post by leosr on 2010-01-15
Hola.
Necesito ayuda con Conky-colors, lo instalé siguiente este tutorial: [http://www.lavidalinux.com.ar/2009/12/tutorial-de-instalacion-conky-colors.html](http://www.lavidalinux.com.ar/2009/12/tutorial-de-instalacion-conky-colors.html)
En el pantallazo se vé cómo quedó después de la instalación. A ver si alguien me ayuda con la confirguración... quiero que tenga lo siguiente: nombre de la PC, kernel, tipo de cpu, uso de cpu (barra), tiempo de uso, ram disponible, swap disponible, espacio en HD, uso de red y el clima.
este es el contenido actual de archivo conkyrc:
```
use_xft yes
xftfont Liberation Sans:size=8
override_utf8_locale yes

text_buffer_size 2048
update_interval 1
total_run_times 0
double_buffer yes
no_buffers yes
net_avg_samples 1
cpu_avg_samples 1

own_window_class Conky
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

default_color cccccc
draw_shades no

color0 white
color1 E07A1F
color2 white

alignment top_right
gap_x 25
gap_y 40
minimum_size 182 0
maximum_width 182

default_bar_size 60 8

imlib_cache_size 0

TEXT
${font Liberation Sans:style=Bold:size=8}SYSTEM $stippled_hr${font}
${color0}${font Poky:size=15}S${font}${color}${goto 32}${voffset -8}Kernel:  ${alignr}${color2}${kernel}${color}
${goto 32}Uptime: ${alignr}${color2}${uptime}${color}
${offset 1}${color0}${font Poky:size=16}P${font}${offset -19}${voffset 9}${cpubar cpu0 4,18}${color}${voffset -16}${goto 32}CPU1: ${font Liberation Sans:style=Bold:size=8}${color1}${cpu cpu1}%${color}${font} ${alignr}${color2}${cpugraph cpu1 8,60 CE5C00 E07A1F}${color}
${color0}${font Poky:size=16}M${font}${color}${goto 32}${voffset -7}RAM: ${font Liberation Sans:style=Bold:size=8}${color1}$memperc%${color}${font}
${offset 1}${voffset 2}${color2}${membar 4,18}${color}${goto 32}${voffset -2}F: ${color2}${memeasyfree}${color} U: ${color2}${mem}${color}
${voffset 4}${font Liberation Sans:style=Bold:size=8}DATE $stippled_hr${font}
${voffset -10}${alignc 46}${color2}${font Arial Black:size=30}${time %H:%M}${font}${color}
${alignc}${time %d %B %Y}
```
y es te es unoque tenía antes de Conky-colorsy  que saque del foro y que yo modifiqué:
```
background yes
cpu_avg_samples 2
net_avg_samples 2
out_to_console no
use_xft yes
xftfont Bitstream Vera Sans Mono:size=9
xftalpha 0.8
mail_spool $MAIL
update_interval 1
own_window yes
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 280 5
maximum_width 220
draw_shades no
draw_outline no
draw_borders no
stippled_borders no
border_margin 4
border_width 1

alignment top_right
gap_x 7
gap y 200
use_spacer none

no_buffers yes

uppercase no

TEXT
${color #FFFFFF}
Sistema ${hr 2}
$nodename
${execi 99999 lsb_release -d -s -c | tr -s "\n" " "}
$kernel on $machine
$stippled_hr
AMD Sempron 2600+ 1.6 GHz
${font StyleBats:size=14}A${font} CPU1: ${cpu cpu1}% ${cpubar cpu1}
${font StyleBats:size=14}q${font} Tiempo uso: ${alignr}${uptime}
$stippled_hr
memory:
 ram:  ${alignr}$mem / $memmax
    ${membar 10,200}
 swap: ${alignr}$swap / $swapmax
    ${swapbar 10,200}
$stippled_hr
hard disks:
 root   ${alignr}${fs_used /} / ${fs_size /}
    ${fs_bar 10,200 /}
 home   ${alignr}${fs_used /home} / ${fs_size /home}
    ${fs_bar 10,200 /home}
Procesos ${hr 2}
cpu usage: ${alignr}CPU%
 ${top name 1}  ${alignr}${top cpu 1}
 ${top name 2}  ${alignr}${top cpu 2}
 ${top name 3}  ${alignr}${top cpu 3}
 ${top name 4}  ${alignr}${top cpu 4}
$stippled_hr
mem usage: ${alignr}MEM%
 ${top_mem name 1}  ${alignr}${top_mem mem 1}
 ${top_mem name 2}  ${alignr}${top_mem mem 2}
 ${top_mem name 3}  ${alignr}${top_mem mem 3}
 ${top_mem name 4}  ${alignr}${top_mem mem 4}
Red ${hr 2}
IP ${addr eth0}
${font PizzaDude Bullets:size=14}M${font} Upload: ${totalup eth0} k/s
${font PizzaDude Bullets:size=14}S${font} Download: ${totaldown eth0} k/s
Total:
${font PizzaDude Bullets:size=12}M${font} ${totaldown eth0} $alignr${font PizzaDude Bullets:size=12}S${font} ${totalup eth0}
$stippled_hr
${color FFFFFF} TIEMPO ${hr 2}

${voffset -10}${alignr 56}${font ConkyWeather:style=Bold:size=40}${execi 600 conkyForecast --location=SPXX0015 --datatype=WF}${font}
${voffset -50}${font Weather:size=40}y${font}  ${voffset -20}${font Arial Black:size=26}${execi 600 conkyForecast --location=SPXX0015 --datatype=HT}${font}
       
```
No lo quiero de muchos colores, uno o dos. Y tal vez el clima a todo color. Con mi primer Conky venía bien hasta que le puse lo del clima, no me quedó bien.
Mi monitor es un CRT de 17" 1024x768.

Gracias.

PD: me gusta como le quedó a leonardomdq pero lo quiero sin la fecha y sin lo que está escuchado.

---

### Post by Bruce M. on 2010-01-15
> **leonardomdq said:**
> Quedo buenisimo asi , muchas gracias nuevamente :KS

Saludos Bruce :P

Estoy usando uno mas liviano hoy.  :)

Con el tiempo en una ventana, que puede abrir y cerrar

Que tengas un buen día
Bruce

---

### Post by Rob3rt0 on 2010-01-17
El Mio. :)

[[IMG]http://img138.imageshack.us/img138/3532/seleccin004.png[/IMG]]("http://img138.imageshack.us/my.php?image=seleccin004.png")

> **leonardomdq said:**
> Alguien que me de una mano con el conky? solo me falta configurar la temperatura pero no hay caso.
Es otro conky pero estoy usando los mismo script para el clima que el conky del mensaje anterior.
[http://ubuntuforums.org/attachment.php?attachmentid=142450&d=1262640665](http://ubuntuforums.org/attachment.php?attachmentid=142450&d=1262640665)
saludos

Leonardo cómo pusiste esos iconos de abajo así? Eso es Docky verdad ?
Qué tema y que font's son las que usas ? Pasame el Wallpaper por favor :)
Y cómo pusiste el icono del pinguino arriba?

Y aquí : [http://ubuntuforums.org/attachment.php?attachmentid=143346&d=1263251422](http://ubuntuforums.org/attachment.php?attachmentid=143346&d=1263251422)
Cómo pusiste esas letras abajo? Y podrías pasarme ese wallpaper también, me quedé embelezado con tu escritorio. @_@

---

### Post by sitodonosti on 2010-02-01
> **Bruce M. said:**
> Estoy usando uno mas liviano hoy.  :)

Con el tiempo en una ventana, que puede abrir y cerrar

Que tengas un buen día
Bruce

Bruce como has puesto es conkyforecast? e intentado buscarlo en conkyhardcore pero no lo encontrado, podrias decirme como ponerlo?
un saludo

---

### Post by Bruce M. on 2010-02-01
> **sitodonosti said:**
> Bruce como has puesto es conkyforecast? e intentado buscarlo en conkyhardcore pero no lo encontrado, podrias decirme como ponerlo?
un saludo

Hola sitodonosti, todo bien?

Es en Conky Hardcore!, buscar esta imagen en [esa página.]("http://conky.linux-hardcore.com/?page_id=3651")

[CENTER][[IMG]http://conky.linux-hardcore.com/wp-content/uploads/2009/11/On_Boot-up-300x240.png[/IMG]]("http://conky.linux-hardcore.com/wp-content/uploads/2009/11/On_Boot-up.png")[/CENTER]

Cuando inicio mi equipo que es lo que parece.

Que tengas un buen día
Bruce

---

### Post by juancho_777 on 2010-02-01
hola!!!
por lo que anduve leyendo Conky es solo para Gnome.. no es cierto?
perdon por la ignorancia, pero si lo que dije antes es cierto, conocen algo similar a Conky para KDE?
o si se puede instalar Conky en KDE como hacerlo.

perdon x salirme un poco del tema.
Gracias!!:D

---

### Post by Bruce M. on 2010-02-01
> **juancho_777 said:**
> hola!!!
por lo que anduve leyendo Conky es solo para Gnome.. no es cierto?

Es para Linux, GNOME, Xfce, KDE or sin DE y con WM: OpenBox, FluxBox, Awesome o WindowMaker etc. etc.  Estoy usando OpenBox solo!

> **juancho_777 said:**
> 
perdon por la ignorancia, pero si lo que dije antes es cierto, conocen algo similar a Conky para KDE?
o si se puede instalar Conky en KDE como hacerlo.

perdon x salirme un poco del tema.
Gracias!!:D

[Install Conky]("http://conky.linux-hardcore.com/?page_id=1289")

[Conky Hardcore!]("http://conky.linux-hardcore.com/?page_id=1473") y un Conky para KDE: [Crinos512]("http://conky.linux-hardcore.com/?page_id=764")

Que tengas un buen día
Bruce

---

### Post by juancho_777 on 2010-02-01
muchas gracias capo!!!!
en unos días estaré subiendo mi conky entonces :)

EDIT:

Bruce, tengo un problema... configure todo mi conky tal como indica el Conky para KDE que me pasaste, pero luego de configurar todo al poner en terminal:
> conky -c /home/Conky/conkymain

obtengo este error como resultado
> Conky: forked to background, pid is 22197               
juancho_777@juancho777:~$                               
Conky: desktop window (1c00144) is subwindow of root window (109)
Conky: window type - normal
Conky: drawing to created window (0x4800001)
Conky: drawing to double buffer
sh: /home/Conky/conkyparts/conkytemplate.sh: Permission denied
sh: /home/Conky/conkyparts/conkyheader.sh: Permission denied
sh: /home/Conky/conkyparts/conkycalender.sh: Permission denied
sh: /home/Conky/conkyparts/conkycore.sh: Permission denied
sh: /home/Conky/conkyparts/conkymemory.sh: Permission denied
sh: /home/Conky/conkyparts/conkydevices.sh: Permission denied
sh: /home/Conky/conkyparts/conkycore.sh: Permission denied
sh: /home/Conky/conkyparts/conkymemory.sh: Permission denied
sh: /home/Conky/conkyparts/conkydevices.sh: Permission denied
sh: /home/Conky/conkyparts/conkycore.sh: Permission denied
sh: /home/Conky/conkyparts/conkymemory.sh: Permission denied
sh: /home/Conky/conkyparts/conkydevices.sh: Permission denied
sh: /home/Conky/conkyparts/conkycore.sh: Permission denied
sh: /home/Conky/conkyparts/conkymemory.sh: Permission denied
sh: /home/Conky/conkyparts/conkydevices.sh: Permission denied
sh: /home/Conky/conkyparts/conkycore.sh: Permission denied
sh: /home/Conky/conkyparts/conkymemory.sh: Permission denied


y repite ese error hasta que cierro el terminal, y muestra en el escritorio un rectangulo negro sin nada mas.
como lo puedo solucionar? ya le di permisos de lectura/escritura a toda la carpeta /home/Conky 
ya no se que hacer.

Gracias!

---

### Post by el_eternauta on 2010-02-22
[I]${voffset 10}${offset 1}${font Tahoma:14}Exaile
${font Tahoma:Italic:size=8}${execi 10 exaile --get-title}
${voffset 3}${offset 14}${font Tahoma:size=9}${execi 10 exaile --get-artist} 
${font Tahoma:Italic:size=8}Duracion: ${execi 10 exaile --get-length}[/I]

Tengo esos comandos para Exaile en Conky y están funcionando bien. La preguntas es: ¿qué debo hacer para que Conky me dibuje la barra de progreso de las canciones de Exaile?

PD: No se si tendrá algo que ver pero uso Exaile 0.3.1b y Karmic Koala! Saludos!

PD2: ¿Alguien conoce algún tutorial para principiantes que enseñe como instalar esto?: 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=122960&d=1248969783[/IMG]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=122964&d=1248970645[/IMG]

Muchas gracias por las respuestas!

---

### Post by cevastian on 2010-03-14
bueno, siendo las 2.30 de la mañana de un domingo lluvioso por mis pagos voy a postear como quedó mi conky, me llevó 2 días dejarlo así, seré muy lento? xD
**.conkyrc**
```
background yes
use_xft yes
xftfont Arial:size=10
xftalpha 0.5
update_interval 1.0
total_run_times 0
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
minimum_size 180 5
maximum_width 180
default_color black
default_shade_color black
default_outline_color black
alignment top_right
gap_x 5
gap_y 200
no_buffers yes
cpu_avg_samples 2
override_utf8_locale yes
use_spacer none
draw_graph_borders yes
uppercase none

TEXT
${color 783b02}${font weather:size=48} ${execi 600 ~/.conky/scripts/clima.sh}$color ${alignc}${font Teen:size=26}${voffset -10}${execi 1200 ~/.conky/scripts/temperatura.sh}$font

${font DejaVu Sans Mono}${voffset 7}${color 8B0000}${execi 60 ~/.conky/scripts/calendario.sh mes}

${color ffffff}${execi 60 ~/.conky/scripts/calendario.sh semana}
${color 000000}${execi 60 ~/.conky/scripts/calendario.sh pasado}${color red}${execi 60 ~/.conky/scripts/calendario.sh hoy}${color 000000}${execi 60 ~/.conky/scripts/calendario.sh futuro}$font


${font Teen:size=15}SISTEMA ${hr 1}$font
${font OpenLogos:size=20}${color 0000ff}J  $color${font Teen:size=12}${voffset -5}kernel: $alignr$kernel${font Arial:size=16}
${font StyleBats:size=16}${color 00ff00}A $color${font Teen:size=12}${voffset -5}cpu: ${cpu cpu1}%${alignr}${voffset 0}${cpubar cpu1 8,80}$voffset${font Arial:size=16}
${font StyleBats:size=16}${color ff0000}O $color${font Teen:size=12}${voffset -5}encendido: $alignr$uptime
${membar 18}
${voffset -25}${color 783b02}${font Teen:size=16}$alignr${offset -2}ram $memperc%$color$font
${swapbar 18}
${voffset -25}${color 783b02}${font Teen:size=16}$alignr${offset -2}swap $swapperc%$color$font


${font Teen:size=15}HD ${hr 1}$font
${font Teen:size=12}home: ${font Teen:size=10}$alignr${fs_free /home/sebas/} / ${fs_size /home/sebas/}
${fs_bar 8 /home/sebas/}
${font Teen:size=12}archivos: ${font Teen:size=10}$alignr${fs_free /home/sebas/archivos/} / ${fs_size /home/sebas/archivos/}
${fs_bar 8 /home/sebas/archivos/}


${font Teen:size=15}RED ${hr 1}$font
${font PizzaDude Bullets:size=16}${color ff0000}r${font Teen:size=13}${offset 10}$color${downspeedf eth0}KB/s$alignr${totaldown eth0}${font Arial:size=13}
${font PizzaDude Bullets:size=16}${color 00ff00}v${font Teen:size=13}${offset 10}$color${upspeedf eth0}KB/s$alignr${totalup eth0}$font
```y la captura correspondiente

[IMG]http://img534.imageshack.us/img534/6005/pantallaconky.jpg[/IMG]

agrego además los scripts que usé para el calendario, el clima y la temperatura

**calendario** "calendario.sh" (fuente [http://linexiando.blogspot.com/2009/02/calendario-en-conky.html](http://linexiando.blogspot.com/2009/02/calendario-en-conky.html))
```
#! /bin/sh
 
DATE=`date | awk -F" " '{print $3}'`
 
case "$1" in
mes)
cal | head -n1
;;
semana)
cal | head -n2 | tail -n1
;;
pasado)
cal | grep -v '[a-zA-Z]' | grep '[0-9]' | awk -F$DATE ' BEGIN {i=0}
($1 == $0 && i==0) {print $1}($1 != $0 && i==0){i=i+1;print $1}';
;;
hoy)
echo $DATE;
;;
futuro)
cal | grep -v '[a-zA-Z]' | grep '[0-9]' | awk -F$DATE ' BEGIN {i=1}
(i==0) {print $0}($1 != $0 && i==1){i=i-1;print $2}';
;;
esac
```**clima** "clima.sh"
```
#!/bin/bash
# tomado del script conditions.sh y modificado a mi gusto
# código correspodiente a la ciudad, en mi caso corrientes capital
cod=ARCS0025
# dirección de donde leer y obtención del clima (yahoo.com.ar)
# dirección modificada para argentina y parámetros de búsqueda cambiados acorde
cnd=$(w3m -dump http://weather.yahoo.com/forecast/"$cod".html | grep -A21 "Current")
if echo "$cnd" | grep -E -i -q 'partly cloudy'; then
    echo 'c'
elif echo "$cnd" | grep -E -i -q 'fair|sunny'; then
    echo 'A'
elif echo "$cnd" | grep -E -i -q 'cloudy'; then
    echo 'e'
elif echo "$cnd" | grep -E -i -q 'storm|thunder'; then
    echo 'i'
elif echo "$cnd" | grep -E -i -q 'snow'; then
    echo 'k'
elif echo "$cnd" | grep -E -i -q 'rain'; then
    echo 'h'
elif echo "$cnd" | grep -E -i -q 'shower'; then
    echo 'g'
fi
```**temperatura** "temperatura.sh"
```
#!/bin/bash
# tomado del script pogodynka.sh y modificado a mi gusto muestra la temperatura en Celcius
# código correspodiente a la ciudad, en mi caso corrientes capital
cod=ARCS0025
# creamos archivo temporal, hay que tenerlo creado previamente en el disco en esa ubicación
archivo=~/.conky/weather
# dirección de donde leer y obtención de la temperatura (yahoo.com.ar)
# dirección modificada para argentina de modo que la temperatura la muestra en C
w3m -dump http://ar.weather.yahoo.com/forecast/"$cod".html | grep -A21 "Condiciones" | sed 's/DEG/°/g' > $archivo
temp=`tail -n3 $archivo | awk '{print $1}'`
echo $temp
```las fuentes me dio fiaca subirlas, además me muero de sueño :o
saludos a todos

por si alguno quiere saber mi distro es debian lenny con icewm que tiene   tema modificado por mí desde otro que tomé como base para evitar  muchas cosas que no utilizo

P/D: si alguien sabe como hacer para cambiar el inicio de semana del  calendario al día domingo que me tire un cable porque no logro dar con  eso

---

