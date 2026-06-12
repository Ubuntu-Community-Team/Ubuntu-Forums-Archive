---
title: "[SOLUCIONADO] libnotify de pidgin no funciona"
date: 2009-05-21
forum: Software
---

### Post by 3nG3ndR0 on 2009-05-21
hola removí pidgin e instale la nueva versión, pero no me muestra los avisos en la notificaciones. me fije que removio el pidgin-libnotify y lo instale de nuevo, pero lo activo en los complemento y aun asi no funciona.

como dejarlo como antes.

---

### Post by Patriciologico on 2009-05-21
Creo que usas Jaunty, si es asi, pidgin notifica por medio de notify osd (el nuevo notificador integrado) pidgin-libnotify usa notification-daemon el cual es incompatible con notify osd. (visto desde synaptic, en propiedades de los paquetes aludidos)

De todos modos para reinstalarlo nuevamente usa
```
sudo aptitude purge pidgin
```

y luego instalalo desde el repositorio oficial.

Saludos!

---

### Post by 3nG3ndR0 on 2009-05-21
> **Patriciologico said:**
> Creo que usas Jaunty, si es asi, pidgin notifica por medio de notify osd (el nuevo notificador integrado) pidgin-libnotify usa notification-daemon el cual es incompatible con notify osd. (visto desde synaptic, en propiedades de los paquetes aludidos)

De todos modos para reinstalarlo nuevamente usa
```
sudo aptitude purge pidgin
```y luego instalalo desde el repositorio oficial.

Saludos!

lo hice y después instale pidgin pero esta igual. Me di cuenta que antes al lado del reloj, salia un icono de un sobre o carta, y ahí estaba el pidgin y ahora no esta. No recuerdo el nombre.

---

### Post by moreback on 2009-05-21
Tengo la impresión que notify-osd necesita que estén activados los efectos de compiz.

---

### Post by Patriciologico on 2009-05-22
> **3nG3ndR0 said:**
> lo hice y después instale pidgin pero esta igual. Me di cuenta que antes al lado del reloj, salia un icono de un sobre o carta, y ahí estaba el pidgin y ahora no esta. No recuerdo el nombre.

En la mañana bien temprano hice pruebas con los Ubunteros Lecaros y Pagondel, para buscarte una solucion, ya que me llamo la atencion y no encontraba informacion. De esas pruebas deduje lo que antes te escribi, y ahora acabo de comprobar que el complemento pidgin-libnotify activa el icono de sobre y como dice moreback notify-osd necesita que estén activados los efectos de compiz.

Lamento no poder ayudarte mas por el momento, pero estaré pendiente.

---

### Post by moreback on 2009-05-22
> **3nG3ndR0 said:**
> lo hice y después instale pidgin pero esta igual. Me di cuenta que antes al lado del reloj, salia un icono de un sobre o carta, y ahí estaba el pidgin y ahora no esta. No recuerdo el nombre.
Ese es un applet del panel, el cual puedes volver a hacer aparecer haciendo clic derecho sobre el panel, seleccionando **Añadir al panel...** y después seleccionar **Aplicación Indicador** de la lista que aparece.

Respecto a lo del notify-osd, debo rectificar que igual funciona sin los efectos de Compiz, la diferencia es que al poner el mouse encima de la notificación, ésta desaparece si no tienes los efectos activados, pero se pone transparente cuando sí lo están.

PD: me acabo de acordar que con Metacity también se pueden activar los efectos aunque no uses compiz, tienes que abrir el **Editor de configuración **(gconf-editor) y luego ir a la clave **/apps/metacity/general** y marcar la clave **compositing_manager**. En una de esas te funciona con esto.

---

### Post by rodrigovb-cl on 2009-05-22
> **moreback said:**
> Tengo la impresión que notify-osd necesita que estén activados los efectos de compiz.

Para nada, yo no uso compiz y me funcionan las notificaciones, incluidas las de Pidgin, probablemente con compiz activado la cosa es más "bonitas" pero no por eso más efectivas.

---

### Post by aolivares on 2009-05-22
Solo un dato para quienes están respondiendo este tema, el amigo dice que instaló una versión nueva de pidgin... vendrá de ahí el problema??

---

### Post by Patriciologico on 2009-05-23
> **rodrigovb-cl said:**
> Para nada, yo no uso compiz y me funcionan las notificaciones, incluidas las de Pidgin, probablemente con compiz activado la cosa es más "bonitas" pero no por eso más efectivas.

Pero hablamos de dos notificadores distintos el bonito usa una librería y el tradicional otra ¿a ti te funciona el bonito con y sin efecto? pues ami solo con efectos.

Lo que menciona aolivares es importante, por que yo cambie repositorios y ahora gwibber aunque me notifica por notify osd, no se integra al indicator-applet (icono de sobre)

Por eso le recomendé a 3nG3ndR0 que si reinstalaba lo hiciera con las versiones soportadas por canonical.

Saludos!

---

### Post by rodrigovb-cl on 2009-05-23
> **Patriciologico said:**
> Pero hablamos de dos notificadores distintos el bonito usa una librería y el tradicional otra ¿a ti te funciona el bonito con y sin efecto? pues ami solo con efectos.
Saludos!

Ni idea... ¿screenshot de la bonita?

---

### Post by Patriciologico on 2009-05-23
[IMG]http://farm4.static.flickr.com/3341/3337637925_ae4116e16d_o.png[/IMG]

---

### Post by Patriciologico on 2009-06-25
> **aolivares said:**
> Solo un dato para quienes están respondiendo este tema, el amigo dice que instaló una versión nueva de pidgin... vendrá de ahí el problema??

Para dar por solucionado este tema. notify-osd, funciona con o sin efectos. Libnotify (por ejemplo en Exaile) actibva notify-osd, por lo tanto si estan relacionados (al contrario de lo que yo pensaba en un comienzo)

Y como dice olivares, las versiones mas modernas de las aplicaciones (por ejemplo repositorio individual o Getdeb) no todas tienen buena integración con notify-osd, que es el caso aqui de Pidgin o Gwibber.

Saludos!

---

### Post by Sortega on 2009-06-25
> **Patriciologico said:**
>  Y como dice olivares, las versiones mas modernas de las aplicaciones (por ejemplo repositorio individual o Getdeb) no todas tienen buena integración con notify-osd, que es el caso aqui de Pidgin o Gwibber.

Yo tengo instalado la ultima version de pidgin y no e tenido problemas con notify-osd

Saludos

---

### Post by Patriciologico on 2009-06-25
Entonces no esta solucionado

 ¿exactamente cual es la ultima que tu tienes de que repositorio? Proposed? getdeb? daily? u otro?

---

### Post by Sortega on 2009-06-25
> **Patriciologico said:**
> ¿exactamente cual es la ultima que tu tienes de que repositorio? Proposed? getdeb? daily? u otro?

Tengo instalado pidgin 2.5.7, descargado desde getdeb, pero de forma directa no mediante el repositorio

---

### Post by 3nG3ndR0 on 2009-06-26
> **Sortega said:**
> Tengo instalado pidgin 2.5.7, descargado desde getdeb, pero de forma directa no mediante el repositorio

Ya lo solucione. Al actualizar primero borre el pidgin antiguo y me borro pidgin-libnotify e pidgin-otr los instale y funciono.

dato: no funciono a la primera borre el contenido de ~/.purple volvió a la normalidad.

---

