---
title: "Panel principal gnome: desaparecido"
date: 2010-03-04
forum: Software
---

### Post by mecdem on 2010-03-04
Hola, amigos.

Sin que pueda explicarles cómo ocurrió, el panel principal gnome desapareció.

No sé si estoy usando la denominación correcta: por si, aclaro que me refiero al panel donde aparecen los íconos de sistema:
menú principal, papelera, gestión de energía, conexión a redes, preferencias de teclado, etc.

Varios de esos elementos podrían reponerse en un nuevo panel (lo he intentado). Pero el desaparecido no parece ser un panel común: cuando ejecuto programas como basket, klipper, knotes, osmo, y otros, éstos ponen su ícono en ese panel donde quedan en forma permanente. Cosa que no ocurre en un panel común.

He mirado por Sistema - Preferencias - Aplicaciones al inicio, comparándolo con el similar de una netbook con sus paneles configurados igual que en la notebook perdidosa. Pero no encuentro nada diferente, ni nada que me oriente.

¿Cómo se recupera ese panel?
Gracias anticipadas. Saludos.

MECDEM

---

### Post by mecdem on 2010-03-04
Subo la captura de un par de mensajes que aparecen cuando inicio Ubuntu (9.04). Creo que tienen que ver con la consulta.


[IMG]http://lh5.ggpht.com/_NjZr7Ovpr9k/S4_ngpibAvI/AAAAAAAABbA/6fyXCWJBhwo/s128/Pantallazo-Error.png[/IMG]

[IMG]http://lh6.ggpht.com/_NjZr7Ovpr9k/S4_ngzd_ZiI/AAAAAAAABbE/q7QOJoEWwoU/s128/Pantallazo-Error-1.png[/IMG]

---

### Post by tavomazzei on 2010-03-05
Hola para reiniciar los paneles al escritorio gnome por defecto tenes que abrir un terminal y poner este comando:
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
reinicias y tenes los paneles como cuando recien instalaste ubuntu.Si tenes un tema personalizado te sujiero que lo guardes antes asi lo volves a poner.
Espero haberte ayudado suerte
Me olvidaba,para saber si tenes algun paquete dañado pones este comando:
dpkg --configure -a
si es asi actualizar tu distribucion:
aptitude dist-upgrade
solo ejecutas los dos ultimos comandos si el primero no funciono

---

### Post by mecdem on 2010-03-06
¡¡¡Funcionó, tavomazzei!!!
Muchas gracias.

Me quedan algunas duditas.
La instrucción "rm -rf .gnome .gnome2 .gconf .gconfd .metacity" me estaba indicando que iba a eliminar esos directorios. Hice copia de ellos.

En particular .gnome2 tiene dentro un subdirectorio panel2.d donde lo que hay allí parecen ser los muchos iconitos que tenía en mis paneles.

La pregunta es:
[INDENT]¿se puede copiar ese contenido al nuevo .gnome2?[/INDENT]
[INDENT]¿o puede haber ahí algo que haya causado la desaparición del panel principal gnome?[/INDENT]

Esta pregunta es por curiosidad, nomás. Si responderla te pudiera requerir más de 30 segundos... déjala correr. No tengo problema en generar nuevamente los íconos, previa recuperación del cubo-compiz, pero esto sé hacerlo... espero 8-[

Muchísimas gracias por tu ayuda, tan rápida y eficaz.
Un abrazo.

---

