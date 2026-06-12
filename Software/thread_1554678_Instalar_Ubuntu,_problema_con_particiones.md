---
title: "Instalar Ubuntu, problema con particiones"
date: 2010-08-17
forum: Software
---

### Post by marcelopatagonia on 2010-08-17
Estimados:

Hola a todos. Necesito ayuda, por favor, para instalar Ubuntu 10.4.

 Tengo una notebook con un disco duro de 160 gb. Tengo instalado Windows 7, con una particion mas para archivos y backup de ese sistema. Como lo muestra la siguiente imagen (Live CD):

[IMG]http://img185.imageshack.us/img185/4913/pantallazoy.png[/IMG]


Estoy partiendo de cero, por lo que les pido con toda amabilidad, si me pueden indicar exactamente què particiones debo hacer, o cuàles cosas hacer, segùn sus indicaciones para que me quede instalado Ubuntu, y con el tiempo pueda dejar definitivamente Windows, o en su defecto achicar lo mas posible el uso de tal.

Y me preguntaba si es posible ordenar las particiones que no estàn asignadas en una sola, y no como ven ahì, separadas.

Muchìsimas gracias de antemano.

Saludos, Marcelo.

EDIT: Disculpen por favor, si este no es el lugar adecuado. Caì aquì por casualidad buscando ayuda. Gracias nuevamente.

---

### Post by marcelopatagonia on 2010-08-17
He encontrado información, pero no logro entenderla. No comprendo qué formato darle a las particiones de Ubuntu, y qué partición va dentro de cuál (swap, etc), y qué puedo hacer con ese espacio no asignado mas pequeño.

---

### Post by marcelopatagonia on 2010-08-17
[IMG]http://img831.imageshack.us/img831/7763/screenshotzm.png[/IMG]  Asi seria correcta la particion?  Cuando intento aplicarla, me indica error al mover o achicar la particion donde se encuentra Windows instalado.   Alguna solucion?

---

### Post by alfplayer on 2010-08-17
Hola.

Es mejor intentar evitar redimensionar particiones y sistemas de archivos, por eso recomiendo crear particiones de linux solo ocupando el espacio no asignado que aparece en la primer imagen.

La segunda partición NTFS (la que está al final) aparece como de 53.89 GB en la primer captura, y en la segunda captura aparce como de menor tamaño. Eso sería porque GParted está preparado para que las particiones de linux tomen demasiado espacio, ocupando espacio de la partición NTFS.

Una partición raíz de 10 GB se puede llenar rápidamente por ser demasiado pequeña. Si la idea es instalar ubuntu para probarlo, te recomiendo crear solo dos particiones en ese espacio no asignado: una para swap (para que funcione hibernar el tamaño debe ser mayor o igual al tamaño de memoria RAM), y otra raíz.

Espero que ayude.

---

