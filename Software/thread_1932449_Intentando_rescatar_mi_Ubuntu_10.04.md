---
title: "Intentando rescatar mi Ubuntu 10.04"
date: 2012-02-27
forum: Software
---

### Post by marcelo_bur on 2012-02-27
Hola. Con la intención de llegar a solucionar el problema que comenté en [http://ubuntuforums.org/showthread.php?t=1842155](http://ubuntuforums.org/showthread.php?t=1842155) he grabado un cd con System Rescue. Si alguien puede aconsejarme sobre cual de las herramientas que trae es la más adecuada, ya que mis conocimientos son limitados, lo agradeceré mucho.
Saludos

---

### Post by marcelo_bur on 2012-03-02
Subiendo el tema, para que sea más visible...

---

### Post by marcelo_bur on 2012-03-04
Hola. Me pasé un par de horas intentando salvar el sistema con System Rescue. No se si es porque no hay forma o porque no se lo suficiente de como usar las herramientas, pero no conseguí nada. No hay forma de acceder a la partición que no arranca, o sea donde está Ubuntu. Seguí otros procedimientos que encontré buscando en Google el mismo problema, pero nada.
Mi último intento será formatear o borrar la partición.
Pero tampoco estoy muy seguro de como hacer eso, GParted me marca tres particiones que corresponden a Ubuntu: dev/sda2 como ext. 4 y dos particiones extendidas, sda3 y sda5.
Lo que quiero saber seguramente es muy simple para alguno de ustedes. ¿Cual es la mejor opción para luego intentar reinstalar Ubuntu 10.04, ELIMINAR o FORMATEAR la partición?? Y por último ¿Ya se trate de una u otra opción, deberé hacerlo en las tres particiones que mencioné o al aplicarla a sda2 automáticamente desapareceran las otras dos??
Les agradecería me respondan a esta duda, pues ya quiero volver a tener mi Ubuntu.
Gracias.

---

### Post by euzkoarima on 2012-03-05
Si vas a reinstalar podes formatear esas particiones, o borrarlas y particionar distinto, eso según tu criterio.

Si no va a cambiarles el tamaño, yo seleccionaría particionado manual en el instalador y le digo que partición usar y que punto de montaje usar (root, home y swap sería lo lógico). También le daría que formatee antes de instalar (las particiones que le indicaste).

Saludos,
Eduardo

---

### Post by marcelo_bur on 2012-03-06
Gracias por responder.
Ya intenté hacer una instalación y que formatee lo existente, pero el instaladar se queda colgado en el segundo paso, por lo que supongo que primero deberé formatear, o borrar, con Gparted.
Saludos

---

### Post by marcelo_bur on 2012-03-14
Listo, ya conseguí que alguien me explique bien como proceder con las particiones y la reistalación.
Saludos

---

