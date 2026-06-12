---
title: "Gestor de actualizaciones"
date: 2009-12-25
forum: Software
---

### Post by EGKaltenmeier on 2009-12-25
Inicié el gestor de actualizaciones, y en determinado momento, antes de terminar de descargarlas todas, me distraje y por error cancelé la descarga. Entonces intenté iniciarlo nuevamente, pero el gestor no respondía. Decidí reiniciar la máquina y una vez hecho ello, intenté comenzar a descargar las actualizaciones nuevamente, pero en ese momento apareció el siguiente mensaje de error:
 “Se ha producido un error. Se han proporcionado los siguientes detalles.
 E: dpkg se interrumpió, debe ejecutar manualmente «sudo dpkg --configure -a» para corregir el problema.  
 E: _cache->open() failed, please report.”.
 Desearía saber cuál fue el problema y su causa, cómo ejecuto manualmente dicha operación, y cómo soluciono el problema. Agradecería que me respondan a mi correo electrónico, que es [EMAIL="egkaltenmeier@hotmail.com"]egkaltenmeier@hotmail.com[/EMAIL]

---

### Post by guillermolisi on 2009-12-25
> **EGKaltenmeier said:**
> Inicié el gestor de actualizaciones, y en determinado momento, antes de terminar de descargarlas todas, me distraje y por error cancelé la descarga. Entonces intenté iniciarlo nuevamente, pero el gestor no respondía. Decidí reiniciar la máquina y una vez hecho ello, intenté comenzar a descargar las actualizaciones nuevamente, pero en ese momento apareció el siguiente mensaje de error:
 “Se ha producido un error. Se han proporcionado los siguientes detalles.
 E: dpkg se interrumpió, debe ejecutar manualmente «sudo dpkg --configure -a» para corregir el problema.  
 E: _cache->open() failed, please report.”.
 Desearía saber cuál fue el problema y su causa, cómo ejecuto manualmente dicha operación, y cómo soluciono el problema. Agradecería que me respondan a mi correo electrónico, que es [EMAIL="egkaltenmeier@hotmail.com"]egkaltenmeier@hotmail.com[/EMAIL]
La solucion esta en el mensaje que citas.

Tenes que abrir una consola/terminal y ahi ejecutar ```
sudo dpkg --configure -a
```

El problema fuiste vos al interrumpir la descarga/actualizacion ya que el cache de paquetes quedo corrupto.

Ejecuta la recomendacion y comenta como te fue.

PS: Una virtud de este foro es que las consultas y sus respuestas queden al alcance de cualquiera que tenga un problema similar. De esta forma se logra un muy bune base de conocimientos a la cual cualquiera puede recurrir ante problemas, cosa que no sucede cuando se responde tal como solicitas.

---

### Post by EGKaltenmeier on 2009-12-29
Gracias Guillermo. Antes que nada, debo decir que soy completamente novato en lo que a cvomputación refiere, y por eso mientras que voy aprendiendo voy cometiendo errores. Justamente, una de las cosas que preguntaba es como lo ejecuto, y de acuerdo a lo que me decís, cómo abro una consola o terminal. 
Comparto la filosofía del foro, solo dejé mi correo porque en estas fechas me resultaba más conveniente concentrar las respuestas en la casilla de correo, no era otro el objetivo.
Gracias y feliz año.

---

### Post by FB91 on 2009-12-29
Para abrir una terminal andá a **Aplicaciones - Accesorios - Terminal**

ó bien, presioná Alt + F2 y escribí gnome-terminal

---

### Post by EGKaltenmeier on 2009-12-31
Gracias, explorando un poco había encontrado la forma. Como recuperé el gestor me dí cuenta que había hecho lo correcto. Gracias y hasta pronto.

---

