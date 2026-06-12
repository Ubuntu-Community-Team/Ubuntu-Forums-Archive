---
title: "Desinstalar aplicaciones"
date: 2009-02-20
forum: Software
---

### Post by JUTGtgRB7z on 2009-02-20
La pregunta que tengo para hacerles es si hay alguna manera de desinstalar aplicaciones que fueron instaladas a partir de paquetes .deb y no desde los repositorios.  Gracias, espero sus respuestas.

---

### Post by sajnox on 2009-02-20
Si instalaste un paquete deb podes desinstalarlo con synaptic (no hay diferencia con el repositorio)

---

### Post by josecuervo86 on 2009-02-20
Si no desde terminal

$ sudo apt-get remove -purge *nombredelaaplicacion*

---

### Post by JUTGtgRB7z on 2009-02-21
> **sajnox said:**
> Si instalaste un paquete deb podes desinstalarlo con synaptic (no hay diferencia con el repositorio)
Específicamente la aplicacion de que se trataba era Cedega. En Synaptic no me aparecia, la pude desinstalar usando sudo dpkg -r cedega ¿Cual es la diferencia con apt-get y con aptitude? ¿Se trata de un problema específico esto? Porque busqué varias veces en Synaptic y no estaba.

---

### Post by sajnox on 2009-02-21
Hasta donde yo se Synaptic es un front-end de aptitude, seguramente alguien nos podra explicar un poco mejor

Saludos

---

