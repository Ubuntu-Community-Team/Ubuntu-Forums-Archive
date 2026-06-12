---
title: "Problema al instalar Ubuntu 12.04"
date: 2012-06-25
forum: Software
---

### Post by serwwweb on 2012-06-25
Hola amigos, estoy teniendo un problema que no puedo resolver al querer instalar **Ubuntu 12.04** en una Netbook **MSI X320**.
Tanto al bootear desde Live como al querer directamente instalar me tira el siguiente error:
**mmc0: controller never released inhibit bit (s)** y luego queda la pantalla negra.
Probe varias distribuciones: **fedora, mint y opensuse** (todas en sus ultimas versiones), que dieron el mismo resultado que ubuntu. Las unicas que logre bootear fueron **Puppy y PCLinuxOS** tambien en sus ultimas versiones y **Ubuntu 10.04**, que tambien funciono, pero que al actualizar a 12.04 produjo el mismo problema.
Me gustaria saber si alguien me puede ayudar, ya que busque mucho en google y lei muchos posts relacionados (aunque no iguales a mi problema) pero sin suerte.
Al parecer hay varios problemas relacionados con el hardware de esta maquina, y parece ser que el kernel no soporta bien a esta.
Precisamente parece ser que el problema puede ser el **lector de memoria SD/SDHC/MMC**, como el controlador sata, que es un **sis 3531**, o el **chipset Intel® US15W (Poulsbo)** con **video Intel GMA 500** que tantos problemas trajeron.
Acudo a ustedes como ultimo recurso antes de deshacerme de la maquina, que por cierto es muy comoda para trabajar.
Desde ya les agradezco aunque sea haber leido.

---

### Post by serwwweb on 2012-06-26
Para quien le interese o lo necesite, estoy teniendo ciertos avances.
Ya pude bootear y llegar al escritorio en una sesion live, y despues instalar y configurar el sistema poniendo en la lista negra el controlador "sdhci" "mmc" y el "psb_gfx". Solo me falta ver la manera de instalar el driver de video sin que me quede la pantalla negra al inicio y asi tener aceleracion.

---

### Post by dirty fingers on 2012-07-10
No tengo una solución a tu problema pero si una pregunta.
¿Si con otros linux te funciona el equipo porque le pones tantas ganas a **Ubuntu 12.04** ?

---

### Post by serwwweb on 2012-07-11
> **dirty fingers said:**
> No tengo una solución a tu problema pero si una pregunta.
¿Si con otros linux te funciona el equipo porque le pones tantas ganas a **Ubuntu 12.04** ?

En realidad no es que me funciona con otras distros de linux. Solo logre bootear algunas sin tener que modificar nada en el arranque.
Con todas tengo problemas con el maldito chipset Poulsbo y la placa de video Intel GMA500, pero eso es un problema de drivers para un chip berreta y que no se siguio desarrollando como deberia.
En fin, te cuento que logre hacer funcionar Ubuntu 12.04 con gnome en modo fallback con la resolucion nativa de la maquina pero la aceleracion grafica deja mucho que desear.
Quiero aclarar que no es problema unico en linux, sino tambien en windows.
En fin, ya estoy pensando en deshacerme de la maquinita.
Agradezco tu posteo.
Saludos

---

### Post by rojojuan on 2012-07-11
Yo probaría con ubuntu 12.04 alternate.
Tuve problemas con una máquina vieja y así lo pude instalar.

---

