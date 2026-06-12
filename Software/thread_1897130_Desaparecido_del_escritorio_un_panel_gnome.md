---
title: "Desaparecido del escritorio un panel gnome"
date: 2011-12-18
forum: Software
---

### Post by mecdem on 2011-12-18
Equipo: Toshiba Satellite A105-S4384
Sistema: Ubuntu 10.04 (32 bits)
______

Hola amigos.

Ha desaparecido un panel del escritorio. No el principal, sino uno opcional que tenía con muchos íconos ordenados en "cajones".
______

Por si sirve el dato: durante un inicio del sistema, al llegar a mostrar el escritorio, sorpresivamente el equipo se apagó. Al reiniciarlo, el panel opcional había desaparecido. No así el que contiene la barra de sistema, el ícono del menú, etc. Ese panel principal permanece OK, con la particularidad de que, después del episodio del "apagón" inesperado, al cliquear botón derecho sobre el ícono del menú, estaba desaparecida la opción "editar menús". Esto lo he solucionado eliminando ese ícono y volviendo a añadirlo con botón derecho sobre el panel > añadir al panel.
______

El subdirectorio con los íconos que estaban en el menú desaparecido está en miusuario > .gnome2 > panel2.d > default > launchers

[IMG]https://lh4.googleusercontent.com/-YP9fd9hrxV0/Tu4xsTTsLdI/AAAAAAAAB-k/d0o90IpRpsM/h120/Launchers.png[/IMG]

Si me dirijo a ese directorio y cliqueo sobre los íconos, todos funcionan perfectamente.

¿Es posible recuperar el panel perdido y conectarlo con ese directorio?
______

En una [consulta anterior]("http://ubuntuforums.org/showthread.php?t=1421364&highlight=gnome+panel") por la desaparición del panel principal, tavomazzei me dio la solución con una línea de comando, *rm -rf .gnome .gnome2 .gconf .gconfd .metacity*, que en ese caso funcionó, pero no sé si es válida para el panel opcional.

Agradezco desde ya la respuesta.
Cordial saludo.

MEC

---

### Post by hictio on 2011-12-19
> 
En una consulta anterior por la desaparición del panel principal, tavomazzei me dio la solución con una línea de comando, rm -rf .gnome .gnome2 .gconf .gconfd .metacity, que en ese caso funcionó, pero no sé si es válida para el panel opcional.


Ejecutar ese comando no te va a restituir todo la configuración que hiciste en los Paneles, ese comando lo resetea al los defaults de instalación de Ubuntu.

---

### Post by mecdem on 2011-12-19
> **hictio said:**
> Ejecutar ese comando no te va a restituir todo la configuración que hiciste en los Paneles, ese comando lo resetea al los defaults de instalación de Ubuntu.

Es lo que sospeché.
Gracias por tu respuesta, hictio
______

Entonces mantengo la pregunta:

¿Es posible recuperar el panel perdido -o abrir uno nuevo- y conectarlo con el directorio que contiene todos los accesos directos configurados por el usuario?

Desde mi ignorancia de no-informática, se me ocurre que si cuando al panel se le añaden accesos directos y con ellos se va formando el directorio "Launchers", debe de haber alguna línea de comando que cada vez que se abre le dice al panel "tomá los datos de .../Launchers".

Lo que intento es no volver a añadir y configurar, uno por uno, los alrededor de 60 accesos directos; y contar con la herramienta, si existe, para subsanar el desaguisado si volviera a ocurrir.

Muchas gracias.
 
MEC

---

### Post by mecdem on 2012-01-03
> **mecdem said:**
> ...mantengo la pregunta:
¿Es posible recuperar el panel perdido -o abrir uno nuevo- y conectarlo con el directorio que contiene todos los accesos directos configurados por el usuario?


Separé y repetí la pregunta de la entrada anterior porque quizás -ubicada casi al principio del texto- no quedó claro que mi interrogante sigue en pie.

Gracias. Saludos.
MEC

---

