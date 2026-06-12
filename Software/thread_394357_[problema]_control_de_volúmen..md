---
title: "[problema] control de volúmen."
date: 2007-03-26
forum: Software
---

### Post by valucha on 2007-03-26
[COLOR="DarkOrchid"]Buenas noches...

Tengo un problema con el control del volúmen. Si trato de subirlo o bajarlo desde el ícono en la barra no pasa nada, estuve investigando por ahi pero no encontré ninguna solución. Tengo instalado el Alsa en la versión más reciente....

También tengo un teclado Genius con las teclas para subir/bajar el volúmen, cuando las toco me aparece el cartel que me indicaría que estoy modificando el volúmen, sin embargo no pasa nada.

Espero su respuesta y pido perdones por preguntar mucho y aportar poco, pero es que soy novata en esto :)[/COLOR]

---

### Post by Tinchio on 2007-03-27
proba con el comando "alsamixer" desde ahi podes ajustar el volumen de todos los controles, en una de esas...

---

### Post by felipelerena on 2007-03-27
tenes que ir a "sonido" y ahi configurar bien cual es la placa de sonido

---

### Post by valucha on 2007-03-27
[COLOR="DarkOrchid"]Miren... ejecuté el Alsamixer...
y me di cuenta que cuando subo y bajo el volumen, se modifica el "master", sin embargo eso no es lo que modifica el volumen de mi parlante, sino que es el headphone...
Traté de c ambiar la fichita de lugar y si la pongo en otro lugar directamente no se escucha...

Ahora lo que pude hacer fue desde el ícono en el panel, seleccionar el "headphone" y por lo menos puedo subir el volumen desde ahi, pero cuando toco el botón del teclado me sube y baja el volúmen del "master" pero no del headphone que es dond eestaría conectado mi parlante...

¿existe alguna forma de configurarlo? osea, de poner el headphone como predeterminado..?

Ahhh, configuré mi teclado Genius, pero igual no hay caso :(... y si pongo en " combinaciones de teclas" los botones de mi teclado me sigue bajando y subiendo el volumen del "master"[/COLOR]

---

### Post by felipelerena on 2007-03-27
si, como te dije (y no me diste bola) eso lo configuras en "sonido" en las preferencias

---

### Post by valucha on 2007-03-27
[COLOR="DarkOrchid"]No sé que es lo que tengo que cambiar, ya vi eso pero de ninguna manera se arregla mi problema :([/COLOR]

---

### Post by clasificado on 2007-03-27
> "sonido" en las preferencias

¿Porqué te ponés un screenshot de que se tendria que tocar?

Yo que tengo kubuntu estoy por acá de oído nomás :D

---

### Post by felipelerena on 2007-03-27
si, perdon por no poner screenshot, es que en el laburo no puedo hacer tanto...
ahi selecciona maestro

---

### Post by valucha on 2007-03-27
[COLOR="DarkOrchid"]Mmmmm.. yo veo la mitad :s[/COLOR]

---

### Post by valucha on 2007-03-27
[img]http://img353.imageshack.us/img353/5449/pantallazopreferenciasdrs6.png[/img]

---

### Post by felipelerena on 2007-03-27
eh...
eh...
eh...
mmm...
eh...
suerte, jajaja.

ni idea de por que no te aparece eso
eh...
no se que decirte, despues agregame al messenger si queres y lo charlamos y te pregunto bien todo.
bah, como quieras,

---

### Post by valucha on 2007-03-28
[COLOR="DarkOrchid"]Jajajajajajajajajajajajaj


xD...

bueno charlamos por MSN... 

Nadie más sabe :(?[/COLOR]

---

### Post by strugart on 2007-03-28
Tratando de entender (me quede medio en el camino pero hago un esfuerzo) supongo por lo que me dijiste que tenes un headphone y unos parlantes... si ambos andan no anda bien la placa si al contrario anda un solo...bueno es obvio lo que voy a decir. 

NOTA: Pude haber flasheado mal si es así obvien el post y si quieren avisen así me desflahseo ajajja

PD:  Perdón por colgarme un par de dias (aprovecho el post, estuve con varias cosas asi que no pude estar con ustedes)

---

### Post by valucha on 2007-03-28
[COLOR="DarkOrchid"]nonon, yo escucho desde parlantes... el sonido sale y todo perfecto...
Cuando toco el control del volumen que tiene mi teclado, el volumen no se modifica...

Y descubrí ejecutando el alsamixer en la terminal... que mi teclado modifica el "master" y parece que po ahi "no sale el sonido", sino que sale por "headphones" no sé por qué, pero cuando modifico los valores de "headphone" si que se modifica el voklumen que sale de mis par[/COLOR]lantes...

---

### Post by jpmorelli on 2007-03-31
Si haces clik con el botón derecho sobre el iconito del parlante al lado de la hora podés ir a las preferencias y elegir cual es el canal maestro que es modificado. Si te toma los headphones como canal master de sonido eso lamentablemente debe ser por como es detectada tu placa por el kernel, ya ahi no se como se cambiaría.

---

### Post by Maximiliano on 2008-01-12
A mi me pasó lo mismo, no podía controlar el sonido ni desde el ícono de la barra, ni con el teclado genuis.

Se resuelve muy facil:

1) Para controlar el volumen desde el ícono del volumen, hacer click derecho, seleccionar preferencias y ahi seleccionar PCM

2) Para controlar el volumen desde el teclado, ir a Sistema/Preferencias/Sonido, y allí seleccionar PCM dónde dice Pistas predeterminadas del mezclador.


Saludos.

---

### Post by valucha on 2008-01-12
> **Maximiliano said:**
> A mi me pasó lo mismo, no podía controlar el sonido ni desde el ícono de la barra, ni con el teclado genuis.

Se resuelve muy facil:

1) Para controlar el volumen desde el ícono del volumen, hacer click derecho, seleccionar preferencias y ahi seleccionar PCM

2) Para controlar el volumen desde el teclado, ir a Sistema/Preferencias/Sonido, y allí seleccionar PCM dónde dice Pistas predeterminadas del mezclador.


Saludos.

[COLOR="DarkOrchid"]A mi el tema se me arregió con feisty.. :)[/COLOR]

---

### Post by User21 on 2008-01-14
Lo he visto en algunas laptops: la principal salida de sonido es Headphones, no importa las vueltas que le des... Desde la instalación se pone asi, y no hay forma; debe ser una cuestion del hardware.

---

### Post by donmatas on 2009-08-01
tengo el mismo problema (con 8.04)

el control de volumen principal no modifica el volumen de algunas aplicaciones (como ryhtmbox) pero sí de otras (tothem)

algunas ideas?

salud
DM

---

### Post by guillermolisi on 2009-08-01
> **donmatas said:**
> tengo el mismo problema (con 8.04)

el control de volumen principal no modifica el volumen de algunas aplicaciones (como ryhtmbox) pero sí de otras (tothem)

algunas ideas?

salud
DM
Posiblemente esas aplicaciones administren el control de volumen en canales diferentes y si uno intenta subirlo  bajarlo siempre con el mismo pareceria que con algunos funciona y con otros no.

Mi recomendacion es visualizar todos los controles del mixer de audio e ir probando con cada aplicacion para determinar cual es el control que administra su nivel de sonido.
De paso verificas que no tengas canales a usar que esten silenciados.

---

### Post by donmatas on 2009-08-01
gracias guille

adjunto mi control de volumen. Entiendo que tengo habilitados todo los output... adjunto imagen de las preferencias de mi control

salud
DM

---

