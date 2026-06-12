---
title: "problema internet móvil ubuntu netbook remix"
date: 2011-02-22
forum: Software
---

### Post by exsimio on 2011-02-22
Ok, déjenme partir con que soy un principiante en todo esto de la computación y todavía me da susto abrir la terminal sin que sea copiar y pegar. 

Bueno, ya que eso se entiende, tengo un netbook Samsung, con Ubuntu Netbook Remix y recientemente contraté un servicio de internet móvil Claro con un módem ZTE, y donde salen todas las conexiones a internet me reconoce el módem, trato de activarlo, pero me aparece sin conexión.

Me imagino que falta configurar algo o algún programa, ¿alguien sabe? ¿o a alguien le pasa lo mismo?

Saludos.

---

### Post by tio lucas on 2011-03-09
hace poco estuve usando la banda ancha móvil de entel, y en ubuntu hay asistentes para configurar la conexión. Una vez que configuré la conexión, indicando el proveedor, el asistente completó los datos correspondientes y eso fue todo.

---

### Post by mgalvezb on 2011-03-10
Revisa si tu modem esta activado. Usualmente los chips se activan por sistema. El mio, un Vomitar, lo active desde Linux y 0 drama, pues segui las indicaciones en pantalla.

Previamente intente pedir ayuda a Vomitar... pero me dijeron que no dan Soporte para Linux... genial respuesta... no les parece?.

m.

---

### Post by asterix77 on 2011-03-11
Escribe en la terminal lo siguiente para ver que te arroja:

$lsusb

Lo anterior es para ver si ubuntu te lo está reconociendo como unidad de almacenamiento (si es que posee una que es lo más lógico), o como módem.

En caso de que no te lo detecte como modem, debes instalar el paquete usb-modeswithch.

$sudo apt-get install usb-modeswitch

y luego iniciar el asistente de conexión de banda ancha del network-manager, es decir, click derecho en el ícono------>Editar las conexiones----->Banda Ancha Móvil----->Añadir, y aquí simplemente seguir las instrucciones.

Luego para conectarse haz click de nuevo en el icono pero en el lado izquierdo, y debiera aparecer tu conexión.

Espero que te sirva, saludos

---

