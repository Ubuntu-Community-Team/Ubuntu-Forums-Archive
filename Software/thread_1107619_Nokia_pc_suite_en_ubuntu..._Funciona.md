---
title: "Nokia pc suite en ubuntu... Funciona?"
date: 2009-03-26
forum: Software
---

### Post by leonardo83 on 2009-03-26
Buenas, queria saber si alguien pudo hacer funcionar el Nokia PC Suite en Ubuntu y como lo lograron, yo tengo el nokia 6020 y quiese instalar los archivos del cd mediante wine y se instalo despues de mucho esfuerzo, pero no anda bien, las ventanas se me ven negras(?) y algunas opciones no me responden (?), por ejemplo no puedo eleguir el telefono a usar y me dice que esta desconectado y no puedo hacer nada :(

Necesito saber si alguine lo pudo hacer funcionar, no quiero recurrir a virtualizar win xp para instalar esto
Saludos!

---

### Post by pablo.s on 2009-03-27
La respuesta es... NO

Saludos.

---

### Post by Juanxho on 2009-03-27
> **leonardo83 said:**
> Buenas, queria saber si alguien pudo hacer funcionar el Nokia PC Suite en Ubuntu y como lo lograron, yo tengo el nokia 6020 y quiese instalar los archivos del cd mediante wine y se instalo despues de mucho esfuerzo, pero no anda bien, las ventanas se me ven negras(?) y algunas opciones no me responden (?), por ejemplo no puedo eleguir el telefono a usar y me dice que esta desconectado y no puedo hacer nada :(

Necesito saber si alguine lo pudo hacer funcionar, no quiero recurrir a virtualizar win xp para instalar esto
Saludos!

Efecvtivamente la respuesta es NO, pero con tantos programas para administrar teléfonos no creo que tengas mayores problemas. Algunos de esos programas (descargables desde synaptic) son:


[LIST]
[*]Phone Manager   [COLOR=Red][http://live.gnome.org/PhoneManager](http://live.gnome.org/PhoneManager)[/COLOR]
[*]KMobileTools       [COLOR=Red][http://kmobiletools.berlios.de/](http://kmobiletools.berlios.de/)[/COLOR]
[*]Wammu             [COLOR=Red][http://wammu.eu/](http://wammu.eu/)[/COLOR]
[*]Xgnokii              [COLOR=Red][http://gnokii.org](http://gnokii.org)[/COLOR]
[*]gMobileMedia [COLOR=Red]     [http://gmobilebrowser.sourceforge.net/](http://gmobilebrowser.sourceforge.net/)[/COLOR]
[/LIST]
Te pongo las paginas de cada una de las aplicaciones para que veas antes de instalarlas, pero a todas las encuentras directamente en synaptic. Mira [COLOR=Red][aquí]("http://es.wikipedia.org/wiki/Synaptic")[/COLOR] para saber más acerca de Synaptic.

Espero que tengas suerte.

---

### Post by z37a on 2009-03-28
> **Juanxho said:**
> Efecvtivamente la respuesta es NO, pero con tantos programas para administrar teléfonos no creo que tengas mayores problemas. Algunos de esos programas (descargables desde synaptic) son:


[LIST]
[*]Phone Manager   [COLOR=Red][http://live.gnome.org/PhoneManager](http://live.gnome.org/PhoneManager)[/COLOR]
[*]KMobileTools       [COLOR=Red][http://kmobiletools.berlios.de/](http://kmobiletools.berlios.de/)[/COLOR]
[*]Wammu             [COLOR=Red][http://wammu.eu/](http://wammu.eu/)[/COLOR]
[*]Xgnokii              [COLOR=Red][http://gnokii.org](http://gnokii.org)[/COLOR]
[*]gMobileMedia [COLOR=Red]     [http://gmobilebrowser.sourceforge.net/](http://gmobilebrowser.sourceforge.net/)[/COLOR]
[/LIST]
Te pongo las paginas de cada una de las aplicaciones para que veas antes de instalarlas, pero a todas las encuentras directamente en synaptic. Mira [COLOR=Red][aquí]("http://es.wikipedia.org/wiki/Synaptic")[/COLOR] para saber más acerca de Synaptic.

Espero que tengas suerte.

Ya que leo este post, cual recomiendan para un N95, y un nokia 6300? hay alguno en especial que funcione mejor o algo pro el estilo?

---

### Post by leonardo83 on 2009-03-28
si si, pero pasa que creo que ninguno de esos programas puede manejar imagenes, por ejemplo como el wammu, todo bien con los mensajes de texto pero no me deja bajar o usar las fotos que saque con el celu, y creo que los demas tampoco, no trabajan el tema de graficos como para pasarlos a la pc como lo tiene el pc suite :(

---

### Post by Shiddo on 2009-03-28
El nokia pc suite no funciona, coma ya te dijeron; pero en general hay problemas de conexion con intrepid y los cel nokia (me paso con un 6131 q no lo detectaba; al igual q la disquetera). Y se soluciona facil, remplazando unos rules.
Hace un backup de los archivos, por si las dudas
Remplazar 60-persistent-storage.rules y 40-permissions.rules en /etc/udev/rules.d/

[http://www.mediafire.com/download.php?zomzmlozmyq]("http://www.mediafire.com/download.php?zomzmlozmyq")
[http://www.mediafire.com/download.php?hygzlvrjmnm]("http://www.mediafire.com/download.php?hygzlvrjmnm")

Espero q te sirva. Saludos:P

---

### Post by guillermolisi on 2009-03-28
> **leonardo83 said:**
> si si, pero pasa que creo que ninguno de esos programas puede manejar imagenes, por ejemplo como el wammu, todo bien con los mensajes de texto pero no me deja bajar o usar las fotos que saque con el celu, y creo que los demas tampoco, no trabajan el tema de graficos como para pasarlos a la pc como lo tiene el pc suite :(
Para pasar archivos entre el telefono y la PC uso Bluetooth y las funcionalidades del Obex server (a traves de Kbluetooth). El telefono se convierte en un pendrive y lo navegas con cualquier file manager que te guste y tengas a mano (Konqueror/Dolphin en mi caso). Y no necesito el cable de datos ya que inclusive tambien funciona con Wammu y Kmobiletools que son los que uso (antes con un Nokia 6131 y ahora con un N73)

---

### Post by NickCis on 2009-03-30
Este es la info que da wine acerca de la compatibilidad con el Nokia Pc Suite (por cierto, es pesima, pero bueno,) [http://appdb.winehq.org/objectManager.php?sClass=version&iId=13360](http://appdb.winehq.org/objectManager.php?sClass=version&iId=13360) .

Yo tengo un Nokia 5610 Xpress Music, tengo que pasar musica y todo eso, usandolo estilo Pen drive, lo demas no anda sobre Linux.

Voy a mandarle un mail a los de nokia para ver que me responden. Les recomiendo que hagan lo mismo, supongo que si muchos lo hacemos se van a dar cuenta que hay una parte significativa de sus clientes que usan Linux y algun programa haran. Es muy poco probable, pero bue, es una esperanza. xD

Saludos.

---

### Post by infernus92 on 2009-03-30
en definitiva... el PC Suite de Nokia es una ******... yo lo usaba desde window$ con un 3200 y jamas anduvo bien ni asi...

---

