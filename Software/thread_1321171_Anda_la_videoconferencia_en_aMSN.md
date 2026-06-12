---
title: "Anda la videoconferencia en aMSN?"
date: 2009-11-09
forum: Software
---

### Post by losoollenos on 2009-11-09
Hola cómo andan tod@s.....
Bueno pensé que en Karmic final ya funcionaría la videoconferencia con aMSN, pero sigue el problema con el dichoso farsight2. Sigo el enlace a la página de aMSN donde explica la solución para instalarlo, pero ya de movida tengo problemas de dependencias, no se si a alguno ya le pasó sino las copio.
Agradecería si alguien ya conoce cómo solucionar esto y pudo lograr tener videoconferencia con aMSN, me tire una mano. Lo peor que en el xp si anda la videoconferencia en aMSN.
También podría ser otro programa, pero hasta ahora los que probé no vienen con ésta función.

Muchas gracias y un abrazo para tod@s

---

### Post by deafters on 2009-11-10
Hola, yo uso karmic y para instalar el amsn 0.98 lo que tuve que hacer es desinstalar el que tenia ( busque en synaptic todo lo que fuera amsn y lo desinstale completamente, eliminando toda configuración guardada), luego agregue este repositorio:
deb [http://ppa.launchpad.net/amsn-daily/ppa/ubuntu](http://ppa.launchpad.net/amsn-daily/ppa/ubuntu) karmic main
actualice (sudo apt-get update) y luego instale ( sudo apt-get install amsn) aceptando todos los paquetes sugeridos y listo, 
espero te sirva

---

### Post by losoollenos on 2009-11-10
Gracias deafters por tu aporte !!!
Instalando desde el repo que me indicás, si te funciona la videoconferencia?, porque instalarlo pude desde sinaptic, pero tengo el problema que comento.
Una cosita que no comenté, es que existe la carpeta "farsight2" en /usr/lib, sin embargo amsn dice que falta.......

Un abrazo

---

### Post by losoollenos on 2009-11-10
Bueno, no pude esperar tu respuesta jejeje.....
Ya lo probé y anda!!!!! por fin.....
Ya no se cómo agradecer en este foro, millón de gracias che.

Un abrazo !!!

---

### Post by losoollenos on 2009-11-10
No encuentro como poner "SOLVED"

saludos

---

### Post by rubioo on 2009-11-10
Tenes que editar el primer post y poner esto:

[[img]http://i.imagehost.org/t/0559/asd.jpg[/img]](http://i.imagehost.org/view/0559/asd)

---

### Post by losoollenos on 2009-11-10
OK, no lo había buscado por ahi jeje

saludos

---

### Post by deafters on 2009-11-11
hola disculpas por la tardanza, genial que lo pudieras solucionar.
saludos cordiales

---

