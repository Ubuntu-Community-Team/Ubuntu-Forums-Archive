---
title: "[SOLVED] Conky y Rhythmbox."
date: 2008-01-04
forum: Software
---

### Post by valucha on 2008-01-04
[COLOR="DarkOrchid"]Hola chicos... ando tratando de configurar mi conky y tengo un problema ya que yo uso el Rhythmbox y conky no tiene comandos para poner el álbum, artista, y canción.

Encontré en ubuntu-fr ([http://forum.ubuntu-fr.org/viewtopic.php?pid=1430931](http://forum.ubuntu-fr.org/viewtopic.php?pid=1430931))  la posible solución pero me quedé en el medio por falta de conocimiento en el tema...

En el último post dice que tengo que colocar esta linea > rhythmbox-client --print-playing peeero con alguna forma de que me lo "ejecute" el conky... Porque si la coloco asi nomás aparece el texto no la función.
Probé lo de rhythmbox-client --print-playing en la consola y me dice qué artista y qué canción escucho tal como yo quiero. Entonces solo sería cuestión de que me ayuden a armarlo.


Por si es necesario, he aquí mi configuración del conky:
> use_xft yes
xftfont Dejavu Sans:size=8
xftalpha 0.8
# Alineación del texto
  alignment top_right
# Separación de los bordes del escritorio
  gap_x 10
  gap_y 30
double_buffer yes
TEXT

${font weather:size=42}${execi 600 ~/scripts/conditions.sh}${font}${voffset -10}  ${execi 1200 ~/scripts/pogodynka.sh}





    ${font weather:size=28}x ${font}HDD ${execi 1 ~/scripts/hddmonit.sh} °C
    ${font weather:size=28}z ${font}CPU ${i2c temp 1} °C 
    ${font weather:size=28}y ${font}FSB ${i2c temp 1} °C



    
   ${font PizzaDude Bullets:size=16}v${font}   Up. ${upspeed eth0} Kb/s 
   ${font PizzaDude Bullets:size=16}r${font}   Dow. ${downspeed eth0} Kb/s 



 
   ${font StyleBats:size=18}A${font}   CPU:  ${cpu}
   $cpubar

   ${font PizzaDude Bullets:size=16}J${font}   $mem / $memperc %
   $membar


   ${font StyleBats:size=18}P${font}   Work:  ${uptime_short}
   ${font StyleBats:size=18}4${font}   ${time %A %d %B}


[http://img153.imageshack.us/img153/9378/conkyhw5.png](http://img153.imageshack.us/img153/9378/conkyhw5.png) 
mil gracias desde ya :) [/COLOR]

---

### Post by jorgito on 2008-01-04
Hola Valucha, 

Proba con 

${exec rhythmbox-client --print-playing}

Yo habia hecho algo parecido para mostrar la temperatura que sacaba de un archivo, poniendo 

${exec cat *** NOMBRE DEL ARCHIVO ***}

Espero que sirva.

Saludos.

---

### Post by valucha on 2008-01-04
[COLOR="DarkOrchid"]Miiiiiiil gracias funcionó...[/COLOR]

---

### Post by vk-cdg on 2008-01-04
A ver como quedó?

Queremos ver.. queremos ver... queremos ver!!!

---

### Post by valucha on 2008-01-04
[COLOR="DarkOrchid"]EL problema es que ahora cada vez que se inicia Conky se me inicia el rhythmbox.. alguoen sabe como hacer que no suceda??!


pD: ahi va la imágen :) igualmente le falta un ícono decente con forma de nota musica, es ue no encontré la font adecuada todavía

PD2: ahi la encontré :) .. va queriendo. [IMG]http://img149.imageshack.us/img149/3982/pantallazo1aw0.png[/IMG][/COLOR]

---

### Post by jorgito on 2008-01-08
Valucha, 

Yo no sabia que hacia el comando que posteaste, supuse que solo mandaba a la consola el nombre del artista.

Si conseguis que el rhythmbox mande a un archivo el nombre podes usar el cat. Habria que ver como corcho se hace para que te borre el artista anterior cuando cambia de pista, pero eso se lo dejo a alguno que sepa.

Saludos

---

### Post by lavaramano on 2008-01-10
${exec rhythmbox-client --print-playing --no-start}

fijate que con --print-playing-format podes poner mas pelotudeces, como la duracion del tema y el disco y giladitas de ese tipo.

---

### Post by facundocorradini on 2008-01-11
Valucha:

Un día de estos te voy a dar acceso a mi máquina para que me pongas un skin tan bueno como los que solés mostrar... que impresionante!!

Que los skins de Hardy los haga valucha!!!

---

### Post by valucha on 2008-01-11
[COLOR="DarkOrchid"]Mil gracias lavaramano :)... voy a ver mñas variables para completar mi conky. ¿Sabés de alguna pág en la que lo puedo encontrar?, sino no importa, lo busco con Mr Google...

Facundocorradini: No sos el primero que me lo dice jajaja, me parece que lo voy a hacer y voy a empezar a cobrar para eso... nah, mentira, pero de hecho hice un blog y todo, pero me gustaría hacer algo más que combinar temas que hace la gente... como hacer mis propios temas, y para ello me va bastante tiempo y ahora no lo estoy teniendo...
Gracias por tu elogio..[/COLOR]

---

### Post by User21 on 2008-01-11
Esos super themes que te mandás... Sos soltera??? 
:lolflag:

---

### Post by markp1989 on 2008-05-01
does any one mind telling me how you got the icons next to the text in that conky?

---

### Post by sajnox on 2008-05-01
Markp,

Please note that you are posting in the Argentinean Forum, our language is spanish. Although everyone is welcome to post here, we encourage everyone to do it in Spanish.

For this time I will translate your post.

"does any one mind telling me how you got the icons next to the text in that conky?

A alguien le molestaria decirme como consiguieron esos iconos al lado del texto en ese conky?"

---

### Post by valucha on 2008-05-02
[COLOR="DarkOrchid"]Son fonts con símbolos, tales como, OpenLogos, Pizzadude, weather, etc...[/COLOR]

---

### Post by MeduZa on 2008-05-02
valucha hice una barra de % de tema, con soporte para radios, para rhythmbox en conky si te interes ;)

---

### Post by valucha on 2008-05-02
> **MeduZa said:**
> valucha hice una barra de % de tema, con soporte para radios, para rhythmbox en conky si te interes ;)

[COLOR="DarkOrchid"]Si me interesa :O![/COLOR]

---

### Post by MeduZa on 2008-05-03
> **valucha said:**
> [COLOR="DarkOrchid"]Si me interesa :O![/COLOR]

bueno aca esta :)

ya sabes tiras el sh en algun lado le das permisos de ejecucion y la usas con:
  ${execbar sh /donde lo hayas poesto/rhythmboxbar.sh}

saludos espero te sirva y te guste ;)

---

### Post by valucha on 2008-05-03
[COLOR="DarkOrchid"]GRacias!!:)[/COLOR]

---

### Post by t0ken on 2009-03-28
oye aprovechando de la ayuda me puse a ver ese comando en mi conky y si funciona y pone la musica solo que cuando cierro el reproductor lo vuelbe a abrir y lo vuelbo a cerrar y lo vuelbe a abrir no se que se deba :S

---

### Post by t0ken on 2009-03-28
aprovechando de la ayuda puse ese comando en mi conky y funciono solo que cuando cierro el reporoductor se vuelbe a abrir nos e que se deba :(

---

### Post by t0ken on 2009-03-28
que fuete es la guitarra!

---

### Post by exegeses on 2009-05-13
> **MeduZa said:**
> bueno aca esta :)

ya sabes tiras el sh en algun lado le das permisos de ejecucion y la usas con:
  ${execbar sh /donde lo hayas poesto/rhythmboxbar.sh}

saludos espero te sirva y te guste ;)

Meduza:

probé el script y me tira el siguiente mensaje:

```
/home/exegeses/scripts/conkyscripts/rhythmboxbar.sh: 6: arithmetic expression: expecting EOF: "038+0"
/home/exegeses/scripts/conkyscripts/rhythmboxbar.sh: 6: arithmetic expression: expecting EOF: "038+0"
/home/exegeses/scripts/conkyscripts/rhythmboxbar.sh: 6: arithmetic expression: expecting EOF: "039+0"
/home/exegeses/scripts/conkyscripts/rhythmboxbar.sh: 11: arithmetic expression: expecting EOF: "048+0"
/home/exegeses/scripts/conkyscripts/rhythmboxbar.sh: 6: arithmetic expression: expecting EOF: "049+0"
```

debe ser una pavada, pero ni idea. alguna idea de cómo arreglarlo?
tks

---

### Post by WooS on 2010-06-07
Alguien me puede decir por favor si se puede hacer que el conky muestre la imagen del album del tema q se esta reproduciendo???
Me quedo algo asi y quiero agregar eso pero no tengo idea como, nisiquiera se si se puede =S
Espero su pronta rta ya que me urge terminar esto =)

Añado imagen y el script que modifique
[http://www.4shared.com/file/VCeHJvru/conkyrc.html]("http://www.4shared.com/file/VCeHJvru/conkyrc.html")
[IMG]http://i50.tinypic.com/2ppngno.png[/IMG]
[IMG]http://i49.tinypic.com/289l75z.png[/IMG]

Como ven abajo a la derecha se ve en todo momento lo q escucho si esta abierto el Rhythmbox pero me gustaria hacer eso que les conte
Saludos

---

