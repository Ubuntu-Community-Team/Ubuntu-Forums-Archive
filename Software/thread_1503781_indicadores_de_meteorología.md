---
title: "indicadores de meteorología"
date: 2010-06-07
forum: Software
---

### Post by drazhe on 2010-06-07
Existe alguna forma de cambiar el origen de la información de meteorología de Ubuntu 10.04? se que epor default baja esa información del sitio weather.com o.net y me gustaría cambiarlo por el del servicio meteorológico nacional, ya que en estos momentos weather me dice que tengo neblina espesa y afuera hay un sol radiante que raja la tierra.. jejeje

---

### Post by hictio on 2010-06-07
Lamentablemente, no te sabría decir de dónde saca la info.. Yo también vi que a veces hay diferencia entre el clima "real" y el de Applet del Panel.
Ahora, lo que vi, es que casi siempre el problema se debe a un delay en los updates periódicos que hace para mantener el reporte lo más "fresco" posible.
Yo lo que hice fue deshabilitar la función del clima propia del Applet "Clock", y luego agregar al Panel el Applet Weather Report, con el cual se puede especificar cada cuánto tiempo querés hacer un update de la info.

---

### Post by drazhe on 2010-06-07
> **hictio said:**
> Lamentablemente, no te sabría decir de dónde saca la info.. Yo también vi que a veces hay diferencia entre el clima "real" y el de Applet del Panel.
Ahora, lo que vi, es que casi siempre el problema se debe a un delay en los updates periódicos que hace para mantener el reporte lo más "fresco" posible.
Yo lo que hice fue deshabilitar la función del clima propia del Applet "Clock", y luego agregar al Panel el Applet Weather Report, con el cual se puede especificar cada cuánto tiempo querés hacer un update de la info.

eso es lo que hice, y aún así, me decía que habia niebla espesa y afuera había un sol rajante... jejeje, pero no solo eso, sino que fue apenas encendí la computadora, este aplet bajo la información del sitio que mencione weather.com y en la temperatura coincidía con el SMN pero en la descripción, le habia pifiado muchísimo.. jejejeje

---

### Post by kornykyano on 2010-06-07
Pero esa información no es para el día siguiente?

---

### Post by hictio on 2010-06-07
No ninguno de estos dos Applets muestra el pronóstico, sino las condiciones actuales, o actuales al momento del último update.
El Applet de "Weather Report" tiene una opción para mostrarte mapas, tomados de Weather.com; pero para Bs. As. por lo menos, no funcionan.

---

### Post by el_eternauta on 2010-06-09
A mi me interesaria poder agregar mi ciudad pero no se que archivo editar. En el applet de AWN 0.4.0 pongo mi ciudad y listo, clima para toda la semana, pero me interesa mucho poder poner eso en el panel de Ubuntu, así ya no tengo que usar AWN o Conky. No se si me expliqué.

---

### Post by hictio on 2010-06-09
Por lo que veo, toma la info de los aeropuertos:

[img]http://img202.imageshack.us/img202/6362/seleccionciudades.png[/img]

Pero, al margen de eso, no veo ninguno en La Rioja? :(

---

### Post by el_eternauta on 2010-06-09
> **hictio said:**
> Por lo que veo, toma la info de los aeropuertos:

[img]http://img202.imageshack.us/img202/6362/seleccionciudades.png[/img]

Pero, al margen de eso, no veo ninguno en La Rioja? :(

Ese es el tema hictio, no sale y tampoco me deja agregarla desde ahí por lo que pensé que tal vez editando algún archivo y agregando la clave de mi ciudad me lo tomaría, no se. Pero tampoco encuentro el archivo a editar. En Conky y AWN 0.4.0 puedo tener el clima pero ahí nunca pude y es la que más me interesa. :S

---

