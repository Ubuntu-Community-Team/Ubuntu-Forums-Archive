---
title: "Icono control volumen -Desaparecido en Lucid"
date: 2010-05-01
forum: Software
---

### Post by prostata on 2010-05-01
Hola, pues acabo de hacer una instalación limpia, del nuevo Lucid, y de momento todo va bien excepto que ha desaparecido el icono del control de volumen, y lo que es peor en añadir al panel no veo tampoco el icono...he buscado por google pero no encuentro solución. ¿alguno sabe cómo añadir este icono al panel y que funcione, claro...???

Saludos

---

### Post by fonte on 2010-05-01
Tengo el mismo problema.

---

### Post by leonardomdq on 2010-05-01
Se posan sobre el panel y van a añadir al panel y buscan "Miniaplicacion de indicadores" y luego añadir.

Saludos.

---

### Post by kanamor on 2010-05-01
> **leonardomdq said:**
> Se posan sobre el panel y van a añadir al panel y buscan "Miniaplicacion de indicadores" y luego añadir.

Saludos.


Gracias leonardomdq

---

### Post by fonte on 2010-05-02
¡Gracias! ¡Ahora entiendo lo que me paso!
Lo elimine al querer quitar el icono de "Chat, Configurar correo..., Difusión"

¿Hay alguna forma de dejar solo el icono de volumen?

---

### Post by leonardomdq on 2010-05-02
> **fonte said:**
> ¡Gracias! ¡Ahora entiendo lo que me paso!
Lo elimine al querer quitar el icono de "Chat, Configurar correo..., Difusión"

¿Hay alguna forma de dejar solo el icono de volumen?
Trate de hacer lo mismo en su momento pero no pude quitarlo.

---

### Post by juancarlospaco on 2010-05-02
*volumen y red estan pegados por ahora, para evitar que se desordenen...*

---

### Post by hictio on 2010-05-02
> **juancarlospaco said:**
> *volumen y red estan pegados por ahora, para evitar que se desordenen...*

Que buena desición!
Puede que sea un control freak, pero me molestaba bastante que los íconos del área de notificación se volvieran locos luego de un reboot.

---

### Post by diegodelcele on 2010-05-02
Gracias leonardomdq

---

### Post by alfplayer on 2010-05-02
Para quitar el ícono del sobre:

```
sudo apt-get remove indicator-messages
```(no lo probé, por favor confirmen si funciona)

---

### Post by fonte on 2010-05-02
> **alfplayer said:**
> Para quitar el ícono del sobre:

```
sudo apt-get remove indicator-messages
```(no lo probé, por favor confirmen si funciona)

Lo acabo de probar. 
¡funciona perfecto!

---

### Post by leonardomdq on 2010-05-02
> **alfplayer said:**
> Para quitar el ícono del sobre:

```
sudo apt-get remove indicator-messages
```(no lo probé, por favor confirmen si funciona)
Gracias alfplayer :D
Confirmado quita el icono de indicador de mensajes.

[[IMG]http://img693.imageshack.us/img693/3636/pantallazoat.png[/IMG]]("http://img693.imageshack.us/i/pantallazoat.png/")

---

### Post by prostata on 2010-05-03
Muchas gracias, funcionó correctamente, pero ahora me desapareció el icono de apagar, cambio sesión, reiniciar...¿cómo ponerlo de nuevo..???

siento como que las actualizaciones no están suficientemente probadas, o que algunas cosas que funcionan bien las cambien sin mucho sentido, por ejemplo al abrir una terminal con sudo nautilus, y hacer lo que debo hacer a la hora de cerrar siempre manda el mensaje de que no se puede cerrar porque está haciendose una operación, en fin debe ser el principio

Saludos

---

### Post by leonardomdq on 2010-05-03
> **prostata said:**
> Muchas gracias, funcionó correctamente, pero ahora me desapareció el icono de apagar, cambio sesión, reiniciar...¿cómo ponerlo de nuevo..???

siento como que las actualizaciones no están suficientemente probadas, o que algunas cosas que funcionan bien las cambien sin mucho sentido, por ejemplo al abrir una terminal con sudo nautilus, y hacer lo que debo hacer a la hora de cerrar siempre manda el mensaje de que no se puede cerrar porque está haciendose una operación, en fin debe ser el principio

Saludos
Para restaurar el indicador de sesión es el mismo procedimiento, boton derecho sobre el panel superior -> añadir al panel -> Minipalicación de indicadores de sesión -> Añadir 

Saludos

---

