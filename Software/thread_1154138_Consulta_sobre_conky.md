---
title: "Consulta sobre conky"
date: 2009-05-09
forum: Software
---

### Post by exegeses on 2009-05-09
> **andy_91 said:**
> se llama conky

para instalarlo tenes que ejecutar en un terminal

```
sudo apt-get install conky
```

y para ponerlo asi como el mio te dejo la configuracion:

```
#Albertronics Conky

double_buffer yes

#own window to run simultanious 2 or more conkys
own_window yes
own_window_type normal
own_window_transparent yes
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
gap_x -660

gap_y 749

alignment bottom_right

#behaviour

update_interval 1

#colour

default_color ffffff

#default_shade_color 359748

own_window_colour 0e1219

#font

use_xft yes

xftfont bauhaus:pixelsize=14
#to prevent window from moving

use_spacer yes

minimum_size 1680 11

#mpd

mpd_host localhost

mpd_port 6600

draw_graph_borders no


TEXT
${color white}${time %A %x %R} ${color AAAAAA}| ${color white} CPU: ${cpu}% ${cpubar 6,80 } ${color AAAAAA}|${color white} Ram: $memperc% ${membar 6,80} ${color AAAAAA}|${color white} Swap:$swapperc% ${swapbar 6,80} ${color AAAAAA}|${color white} Sistema de archivos: ${fs_used_perc /}% ${fs_bar 6,80 /}
```

ese texto lo pegas en un archivo de texto y lo guardas como **.conkyrc** en tu home

por ultimo agregas conky a los programas al inicio de la secion(eso varia segun el entorno grafico)



gracias por la config.
ahora, ¿hay algún tutorial / guía de los parámetros para configurar el conky?
así configuro y posteo mi desk
desde ya, muchas gracias
saludos

---

### Post by Hei Ku on 2009-05-09
Movido fuera del thread de escritorios. Ese ya es demasiado largo de por sí. 

Si buscas en este foro tenes un monton de info sobre Conky, ejemplos y todo.

---

### Post by Jorgel on 2009-05-11
Saludos, para no empezar un nuevo tema: Instalo conky pero me da este error

```
jorge@ubuntu:~$ conky
Conky: /home/jorge/.conkyrc: 23: no such configuration: 'wm_class_name'
Conky: can't open '/sys/bus/i2c/devices/0-002d/temp2_input': No such file or directory
please check your device or remove this var from Conky
```

No tengo la menor idea de que estoy haciendo mal.

Busco en my home y no veo el archivo conky por ningun lado :confused:

---

### Post by pablo.s on 2009-05-11
> **Jorgel said:**
> 

```
jorge@ubuntu:~$ conky
Conky: /home/jorge/.conkyrc: 23: no such configuration: 'wm_class_name'
Conky: can't open '/sys/bus/i2c/devices/0-002d/temp2_input': No such file or directory
please check your device or remove this var from Conky
```  

Te dice que hay una linea invalida en
.conkyrc que debes borrar.

> **Jorgel said:**
> Busco en my home y no veo el archivo conky por ningun lado :confused:
El archivo conkyrc es el encargado
de mantener la configuración de
Conky. Por ende es un archivo oculto.
Si hace&#347; **[COLOR=DarkGreen]ls -a[/COLOR]** en una terminal en tu
/home lo vas a ver listado.
Para editarlo escribí **[COLOR=DarkGreen]gedit .conkyrc[/COLOR]**

---

### Post by Jorgel on 2009-05-11
Gracias Pablo, pude hacer que arrancara con tu ayuda, luego trabajo con el conky mas, cuando aprenda bien a "customizarlo".

---

