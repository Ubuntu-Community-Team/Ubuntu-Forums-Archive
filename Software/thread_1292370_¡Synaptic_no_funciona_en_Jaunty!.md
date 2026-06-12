---
title: "¡Synaptic no funciona en Jaunty!"
date: 2009-10-15
forum: Software
---

### Post by edelcid on 2009-10-15
Hola, buen día, que tal!
A ver si a alguien le pasó:
Tenía Ubuntu Hardy Heron (8.04) y quise actualizarlo. El mismo día, según las instrucciones, actualicé primero a la versión 8.10 y luego a la 9.04, que es la que tengo ahora.
Después de eso, algo se rompió, porque la conexión ADSL Speedy se sesconfiguró, y me costó un montón dejarla como estaba. Después, vino lo peor:
El Gestor de actualizaciones me marca las actualizaciones disponibles y, cuando le tildo que actualice, descarga y luego me muestra un cuadro de diálobo con el siguiente error:
                      [SIZE=2]--error no se pudo efectuar un "fork" de Pty--[/SIZE]
Entonces pruebo con la Terminal.
La abro y de inmediato aparece:
         [SIZE=2] --Ha ocurrido un error al crear el proceso hijo para esta terminal--[/SIZE]
Y queda inhabilitada.
Pruebo con Synaptic, y me da el error del "fork".
En el toqueteo, borré el Virtualbox, que lo uso para trabajar.
No puedo reinstalar los paquetes de Synaptic desde el CD porque me salta el error.
He buscado por todos lados, y lo único que encontré sobre el "Fork del pty" fue una traducción de una lista de errores.
¿Dónde estará el error?
¿Qué comando puedo usar desde la pantalla negra de Ctrl+Alt+F2 o Alt+F2? Es lo único que puedo utilizar.
Llevo varios días con este problema, y ya estoy a punto de agotamiento.
Espero que alguien sepa algo.
Un abrazo a todos.-

---

### Post by Sef on 2009-10-15
Moved to Argentina Loco.

---

### Post by SLA_leandrin on 2009-10-15
Probaste en la consola con

sudo apt-get update && sudo apt-get upgrade

Fijate, a ver que pasa, y si te da un error ahí, pegalo aquí así podemos ayudarte mejor.

---

### Post by guillermolisi on 2009-10-15
> **Sef said:**
> Moved to Argentina Loco.
Thank you Sef !

---

### Post by edelcid on 2009-10-17
No puedo abrir la Terminal porque me da el error que comenté del proceso hijo, y probé desde el modo texto cuando pulso Ctrl+Alt+F2, y descarga los paquetes, pero dice que es imposible actualizar. No recuerdo exactamente el mensaje porque ahora no estoy frente a la Pc del problema (es del trabajo, y ahora estoy en casa).
El problema apareció cuando se actualizó a Jaunty desde la versión anterior. Hice las actualizaciones desde Hardy en forma secuencial desde el Gestor de Actualizaciones, a medida que aparecia la notificación en su ventana. Lo hacía directamente presionado el botón "Instalar actualizaciones".

---

### Post by edelcid on 2009-10-19
La pregunta puntual es: si hay forma de, una vez que arranca desde el Live CD, ejecutar algún comando que me permita reinstalar synaptic o el gestor de actualizaciones, SIN que reinstale todo Ubuntu, ya que formatea todo.:confused:

---

### Post by edelcid on 2009-10-27
Al final: lo que tuve que hacer fue reinstalar Ubuntu desde el Live CD, en una partición limpia. Ahora estoy migrando documentos. :(

---

