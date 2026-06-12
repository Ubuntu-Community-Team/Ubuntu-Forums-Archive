---
title: "Cómo configurar gnome-panel"
date: 2009-10-12
forum: Software
---

### Post by sitodonosti on 2009-10-12
Hola, hoy he decidido cambiar la apariencia de mi escritorio, y por supuesto esto incluye los paneles de gnome, el caso esque he puesto para que los paneles se escondan pero solo que para mi gusto tardan mucho en aparecer, sabeis donde se podria cambiar eso para que aparezca antes en vez de esperar 1 segundo a que salga que salga justo al pasar por la barra?si esque se puede claro, nose si me expicado bien, he intentado explicarlo de la mejor forma


un saludo

---

### Post by pablo.s on 2009-10-12
En una terminal escribe:

```
gconf-editor
```


luego vas en el arbol de la
izquierda a apps -> panel ->
global y buscas la opción a la
derecha que dice 
panel_hide_delay y la modificas
a 50. Luego modificas la opción
que dice panel_show_delay y
tambien le das 50.

---

### Post by sitodonosti on 2009-10-12
gracias pablo pero e peusto 50 y 50 y sigue la misma velocidad, tengo que renicniar sesion para que surja efecto o asi? tambien me e fijado que pone panel-animation-speed y pone medium, eso tiene algo que ver?

---

### Post by pablo.s on 2009-10-12
> **sitodonosti said:**
> tambien me e fijado que pone panel-animation-speed y pone medium, eso tiene algo que ver?

Si, perdón, tienes que cambiar
el valor panel_animation_speed
a panel-speed-high.
Fijate si hay diferencia.

---

### Post by sitodonosti on 2009-10-12
pues realmente no noto gran diferencia incluso poniendo en vez de 50, 5. Por supuesto cambiando la velocidad a high, ver si reiniciando o asi sino nuse...no e tocado nada más...

un saludo

---

### Post by sitodonosti on 2009-10-14
sigue a la misma velocidad no noto nigun cambio, help me pablo pleas!!ejjeje

un saludiko

---

### Post by ramiro_md on 2009-10-14
Buenas..configurá la velocidad que te quepa y ejecutá en una consola:
```
sudo killall gnome-panel
```
Después de matar el proceso de los paneles, estos se reiniciarán y puede que los cambios que "aplicaste" surgan efecto.
Un saludo y suerte !

---

### Post by sitodonosti on 2009-10-19
Gracias e cambiado ya todo, igual va mas rápido que antes pero segun mi ojo va mas o menos parecido, gracias por la ayuda y un saludo desde donosti

---

