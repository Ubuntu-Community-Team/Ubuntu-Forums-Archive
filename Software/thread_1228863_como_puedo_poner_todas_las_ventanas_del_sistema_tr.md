---
title: "como puedo poner todas las ventanas del sistema trasparente?"
date: 2009-08-01
forum: Software
---

### Post by pelaolinux on 2009-08-01
hola amigos del team chile!!! 
hoy les necesito saber como poner las ventanas trasparente en mi sistema, como se llama el programa? y todo eso ... 
bueno y me gustaría saber si con : 1Ghz, 512 de ram y de video 128 mb no me funcionara inestable el sistema con el programa ... 
saludos!

---

### Post by robertor on 2009-08-01
Te refieres a compiz-fusion?
El equipo de mi mamá tiene ubuntu (creo que 8.04, no lo he actualizado por falta de tiempo). Ella tiene un Athlon XP 1800+, 512 de ram y una nvidia 5200 de 128(creo que ese es el modelo...es la que viene despues de la gforce4) y el sistema anda bien.
Para instalar debiera bastarte:
```
sudo apt-get install compiz-fusion
```
Saludos!
Roberto

---

### Post by pelaolinux on 2009-08-01
> **robertor said:**
> Te refieres a compiz-fusion?
El equipo de mi mamá tiene ubuntu (creo que 8.04, no lo he actualizado por falta de tiempo). Ella tiene un Athlon XP 1800+, 512 de ram y una nvidia 5200 de 128(creo que ese es el modelo...es la que viene despues de la gforce4) y el sistema anda bien.
Para instalar debiera bastarte:
```
sudo apt-get install compiz-fusion
```Saludos!
Roberto




lo probare, gracias!!!

---

### Post by augias on 2009-08-02
te recomiendo que tambien bajes "compizconfig-settings-manager"

este paquete instala una aplicacion en tu menu de programas, en preferencias de sistema, que se llama compizconfig, obvio. en mi caso no venia predeterminado con compiz pero es necesario porque es el lugar donde configuras con finos detalles los efectos de escritorio.

---

### Post by aledruetta on 2009-08-04
> **pelaolinux said:**
> hola amigos del team chile!!! 
hoy les necesito saber como poner las ventanas trasparente en mi sistema, como se llama el programa? y todo eso ... 
bueno y me gustaría saber si con : 1Ghz, 512 de ram y de video 128 mb no me funcionara inestable el sistema con el programa ... 
saludos!

Hola pelaolinux,

¿Qué versión de Ubuntu estás usando? Porque si es la 8.10 o la 9.04, Compiz ya está instalado y si tu placa gráfica tiene las características apropiadas, debería estar funcionando. Es sólo ir a Sistema-->Preferencias-->Apariencia-->Efectos visuales y activar el nivel de efectos según la potencia de la tarjeta gráfica.

El otro paquete que te recomendaron, el compizconfig-setting-manager, ese sí hay que instalarlo y te da más libertad para seleccionar qué tipo de efectos querés usar y configurarlos a gusto.

---

### Post by nopersona on 2009-08-04
Bueno, añadiendo una poco más de ayuda al tema, especificamente, vas a compiz>administración de opciones>accesibilidad>opacidad, brillo y saturación. En opacidad creas una entrad nueva que contenga esto

```
Tooltip | Menu Tooltip | Menu | PopupMenu | DropdownMenu
```

Y le das un valor a tu gusto, yo lo tengo en 84. Eso me deja menu, notificaciones y ventanas transparentes. Lo mismo se puede hacer para el brillo y todo lo demás.  También puedes hacer otra con

```
ropdownMenu
```

Saludos.

---

### Post by pelaolinux on 2010-01-05
> **nopersona said:**
> Bueno, añadiendo una poco más de ayuda al tema, especificamente, vas a compiz>administración de opciones>accesibilidad>opacidad, brillo y saturación. En opacidad creas una entrad nueva que contenga esto

```
Tooltip | Menu Tooltip | Menu | PopupMenu | DropdownMenu
```Y le das un valor a tu gusto, yo lo tengo en 84. Eso me deja menu, notificaciones y ventanas transparentes. Lo mismo se puede hacer para el brillo y todo lo demás.  También puedes hacer otra con

```
ropdownMenu
```Saludos.


Muchas gracias por la ayuda me funciono.

---

### Post by _ZeTa on 2010-01-18
> **nopersona said:**
> Bueno, añadiendo una poco más de ayuda al tema, especificamente, vas a compiz>administración de opciones>accesibilidad>opacidad, brillo y saturación. En opacidad creas una entrad nueva que contenga esto

```
Tooltip | Menu Tooltip | Menu | PopupMenu | DropdownMenu
```

Y le das un valor a tu gusto, yo lo tengo en 84. Eso me deja menu, notificaciones y ventanas transparentes. Lo mismo se puede hacer para el brillo y todo lo demás.  También puedes hacer otra con

```
ropdownMenu
```

Saludos.

[Post de la semana]("http://ubuntuforums.org/showthread.php?t=1176055"): [18 de enero 2010]("http://www.ubuntu-cl.org/comunidad/menus-del-sistema-transparentes")

---

### Post by pinguinosaurio on 2010-01-19
Tambien puedes crear otro valor con el nombre "normal" con un valor que tu quieras (sobre 90 es aceptable) con esto haces que todas las ventanas de gnome se vuelva transparente, y cuando digo todo, es todo :)

Si haces un valor con el nombre "dialog" con un valor 84 los cuadros de dialogos se vuelven transparentes.

Para hacer transparente la barra de título: Presionan: ALT+F2
 Escriben: gconf-editor
 van hasta: apps / gwd
 y en donde dice "metacity_theme_active_opacity" y "metacity_theme_shade_opacity" colocamos un valor de "0,5".

---

### Post by pinguinosaurio on 2010-01-19
Tambien puedes hacer que determinadas aplicaciones de Ubuntu sean completamente transparentes, esto se hace agregando una nueva entrada en las opciones de Opacidad, brillo y saturacion de compiz ya mencionada anteriormente, y agregas el siguiente valor:

class=Rhythmbox & !title=Buddy List

luego le das el valor de transparencia (yo le di 80 y se ve muy bien), en ese caso específico he hecho transparente al reproductor Rhythmbox, si quisisera que el reproductor Totem fuese transparente, habria que reemplazar el nombre Rhythmbox por Totem (lo demas se deja tal cual), con lo que quedaría así:

class=[COLOR=Blue]Totem[/COLOR] & !title=Buddy List

Luego le das un valor de transparencia que desees.

Fijate como la primera letra de la aplicacion a hacer transparente está en mayusculas, esto no es una regla exacta, por ejemplo, si quieres hacer transparente la Terminal debes agregar el valor:

class=[COLOR=Blue]terminal[/COLOR] & !title=Buddy List

y le das un valor de transparencia que desees.

Como se puede ver, en este valor, la primera letra de la aplicacion se escribe en minúsculas, es así como, cuando quieras hacer transparente una aplicacion, y no te funciona, prueba a colocar la primera letra de la aplicacion en minusculas (espero se entienda)

---

### Post by pelaolinux on 2010-04-13
> **pinguinosaurio said:**
> Tambien puedes crear otro valor con el nombre "normal" con un valor que tu quieras (sobre 90 es aceptable) con esto haces que todas las ventanas de gnome se vuelva transparente, y cuando digo todo, es todo :)

Si haces un valor con el nombre "dialog" con un valor 84 los cuadros de dialogos se vuelven transparentes.

Para hacer transparente la barra de título: Presionan: ALT+F2
 Escriben: gconf-editor
 van hasta: apps / gwd
 y en donde dice "metacity_theme_active_opacity" y "metacity_theme_shade_opacity" colocamos un valor de "0,5".

Muchísimas gracias... es muy genial el dato que me diste! :lolflag::guitar:

---

