---
title: "Detalles estéticos &quot;finos&quot;"
date: 2008-08-22
forum: Software
---

### Post by vk-cdg on 2008-08-22
Debido a que terminé con la configuración grande de Ubuntu en la notebook, ahora me puse con los detalles finos (cosas no funcionales) y hay varias cosas que no se hacer o que no se si se pueden hacer.

Por ejemplo encontré [este]("http://120linux.com/aspecto-reloj-ubuntu/") artículo en un blog donde muestran como personalizar la vista del reloj del system tray, algo que me pareció "simpático".

Una cosa con la que estoy luchando es con el usplash, ya que el mismo se muestra por default en 640 x 480. 
En la desktop con el startup manager lo pude poner en 1024 x 768 y se ve de primera pero en la notebook (wide) cuando lo pongo en otra resolución que no sea 640 x 480 o no se ve o se ve grande, pixelado y deformado. Alguno lo cambió de los que tienen monitores widescreen?

Otra de las cosas que cambié fue la pantalla de lokeo cuando una sesión está iniciada (Bloquear Pantalla), pero de las opciones que encontré en gnome-look no me termina de convencer ninguna. Hay alguna otra en otro lado?

La última (por ahora). No logro hacer que al entrar en mi sesión, el emesene (que se carga solo) lo haga cerrado en el system tray (como lo hace el de MS) o en su defecto minimizado. No solo lo hace abierto sino que en cada inicio aparece en un lugar diferente de la pantalla sin patron aparente.

Eso es todo por ahora.

---

### Post by sherwoodinc on 2008-08-22
Hola! Este es mi "first post" :) 

Con respecto a tu primer pregunta, en el LCD de mi desktop (1680x1050) sólo pude poner resoluciones no-wide (4:3) para el splash, a pesar de que probé a mano con varias en el grub. Creo que eso depende de la placa de video y del soporte VESA que tenga, mi placa es una Nvidia 8800 y teóricamente tiene el soporte, pero igual no la hice andar en resoluciones wide (obvio que en el X anda).
Así que hoy día está en 1280x1024 y aunque no se ve "feo" se nota que el splash está un poco más aplastado.
Si alguien con nvidia lo pudo hacer, estaría agradecido de recibir noticias :)

Acerca del emesene, si el programa no tiene opción de arrancar minimizado, tendrías que recurrir a algún programa (o comando shell) que te lo minimize en el arranque, estoy seguro que algo así se puede lograr.

---

### Post by valucha on 2008-08-22
[COLOR="DarkOrchid"]Muuuuuuuuuuuuuuuy bueno lo del reloj :)...
De donde saco todos los comandos posibles??... porque por ejemplo, yo no quiero que la fecha sea smaller, sino que la hora sea bigger... y si pongo big, o bigger no me da bola...
gracias :)[/COLOR]

---

### Post by lega on 2008-08-22
me gustó el cambio de aspecto del reloj, ya lo hice :)gracias

---

### Post by lega on 2008-08-22
según dicen en los comments del blog > Para saber las opciones de los campos % pueden consultar
man strftime

---

### Post by vk-cdg on 2008-08-22
> **valucha said:**
> [COLOR="DarkOrchid"]Muuuuuuuuuuuuuuuy bueno lo del reloj :)...
De donde saco todos los comandos posibles??... porque por ejemplo, yo no quiero que la fecha sea smaller, sino que la hora sea bigger... y si pongo big, o bigger no me da bola...
gracias :)[/COLOR]

Soy bastante novatoide todavía. En el blog algo decía, pero no lo consulté. Me suena a que son tags de HTM eso, pero no estoy seguro.

---

### Post by vk-cdg on 2008-08-22
> **lega said:**
> según dicen en los comments del blog

Gracias Lega, aclaraste la duda de Valu

---

### Post by santiagoward2000 on 2008-08-22
> **vk-cdg said:**
> Por ejemplo encontré [este]("http://120linux.com/aspecto-reloj-ubuntu/") artículo en un blog donde muestran como personalizar la vista del reloj del system tray, algo que me pareció "simpático".

Muy bueno! Gracias :)

> **vk-cdg said:**
> La última (por ahora). No logro hacer que al entrar en mi sesión, el emesene (que se carga solo) lo haga cerrado en el system tray (como lo hace el de MS) o en su defecto minimizado. No solo lo hace abierto sino que en cada inicio aparece en un lugar diferente de la pantalla sin patron aparente.

Acerca de esto, podés probar con el **devilspie** para que empiece minimizado. Acá te dejo un tuto bastante bueno que encontré (es medio viejo, ahora podes instalarlo directamente desde los repositorios):
[http://www.ubuntu-es.org/index.php?q=node/15810]("http://www.ubuntu-es.org/index.php?q=node/15810")
También podés usarlo para definir la posicion en la que aparece, el tamaño de la ventana, si aparece o no en la taskbar, con o sin bordes de ventanas...
Suerte!

---

### Post by santiagoward2000 on 2008-08-22
> **valucha said:**
> [COLOR="DarkOrchid"]Muuuuuuuuuuuuuuuy bueno lo del reloj :)...
De donde saco todos los comandos posibles??... porque por ejemplo, yo no quiero que la fecha sea smaller, sino que la hora sea bigger... y si pongo big, o bigger no me da bola...
gracias :)[/COLOR]

Ahh, no encuentro una lista con eso de los tamaños, pero para que sea grande probá con **large** o **larger**.
Saludos!

---

### Post by luchardi on 2008-08-25
En intrepid no esta dentro de applet el clock ....

Alguien lo probo en intrepid?

---

