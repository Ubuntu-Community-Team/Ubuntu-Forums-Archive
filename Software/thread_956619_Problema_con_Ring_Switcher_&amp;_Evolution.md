---
title: "Problema con Ring Switcher &amp; Evolution"
date: 2008-10-23
forum: Software
---

### Post by hictio on 2008-10-23
Hola,
Alguien usa el [Ring Switcher]("http://wiki.compiz-fusion.org/Plugins/Switcher#head-a9c4d9e83d592ecc84041865d75adba90e59ed03") de Compiz con Evolution?
Tengo un problema bastante molesto con el calendario y los eventos, cuando creo algun evento en el calendario de Evolution (y no importa si las notificaciones estan apagadas, como las tengo en todos los casos), la proxima vez que uso el Ring Switcher para pasar a otra ventana, ademas de las ventanas abiertas, sale una nueva por cada evento del calendario.

Esas ventanitas nuevas no hacen nada, si selecciono alguna, no pasa nada, y si vuelvo a usar el Ring Switcher, ya no estan.

A alguien le pasa esto?

[[IMG]http://img124.imageshack.us/img124/6488/wtfvd2.th.jpg[/IMG]](http://img124.imageshack.us/my.php?image=wtfvd2.jpg)

Muchas gracias.

---

### Post by Hei Ku on 2008-10-23
> **hictio said:**
> Hola,
Alguien usa el [Ring Switcher]("http://wiki.compiz-fusion.org/Plugins/Switcher#head-a9c4d9e83d592ecc84041865d75adba90e59ed03") de Compiz con Evolution?
Tengo un problema bastante molesto con el calendario y los eventos, cuando creo algun evento en el calendario de Evolution (y no importa si las notificaciones estan apagadas, como las tengo en todos los casos), la proxima vez que uso el Ring Switcher para pasar a otra ventana, ademas de las ventanas abiertas, sale una nueva por cada evento del calendario.

Esas ventanitas nuevas no hacen nada, si selecciono alguna, no pasa nada, y si vuelvo a usar el Ring Switcher, ya no estan.

A alguien le pasa esto?

[[IMG]http://img124.imageshack.us/img124/6488/wtfvd2.th.jpg[/IMG]](http://img124.imageshack.us/my.php?image=wtfvd2.jpg)

Muchas gracias.

La verdad es que ni idea cómo solucionar eso. Creo que tiene una opción para evitar qué ventanas entran en el ring switcher.

Pero, podés subir ese wallpaper? Te quedó buenisimo el efecto!!! :D

---

### Post by santiagoward2000 on 2008-10-23
Hola!
Como dijo Hei Ku, se puede decir qué ventanas querés que aparezcan en el ring y cuáles no. Para eso abrís compizconfig-settings-manager, vas a Ring Switcher, y en la pestaña Misc. Options, donde dice Ring Windows agregá al final:
```
 | !(title=alarms)
```
Contanos si eso lo arregla.
Saludos!

---

### Post by hictio on 2008-10-23
No se que decirte del wallpaper :) ... [Este es el link directo](http://img124.imageshack.us/img124/6488/wtfvd2.jpg), la calidad es una m*erda, creo yo, para un wallpaper de los monitores gigantes de hoy en dia... Abri Evolution, create unas dos docenas de eventos fantasma, y lo vas a tenes fato en casa... Los iconos de las Alarms benditas -y de cualquier app minimizado para el caso- se ve como el c*lo porque usa el icono default que aparece minimizado en el Window List del Panel.

> 
| !(title=alarms)


Muchas gracias, excelente idea! Pero no lo esta arreglando, probe tanto con 'alarms' como con 'Alarms' por si es case sensitive.
No probe con un reinit de X, ni reboot; en un rato la rebooteo y posteo si hay novedades.

---

### Post by santiagoward2000 on 2008-10-24
No sé si te toma estos cambios así nomás o tenés que reiniciar Compiz (si tenés el fusion-icon podés reiniciarlo fácil, si no podés usar un ```
compiz --replace
``` y listo).
Si igual no te lo tomó, podrías probar con un **name** en lugar del **title**, pero no estoy seguro que el nombre sea **alarms**.
Si no, la que creo que es la posta (pero no lo probé con este tipo de cartelitos) es: abrís una terminal y escribís:
```
xprop WM_CLASS
``` y enter. El cursor se va a poner como un +. Hacés click en el cartelito y te tendría que aparecer el class de la ventana. Después ponés:
```
 | !(class=lo que te aparece en la terminal)
```
Contanos como te fue!
Suerte!

---

### Post by hictio on 2008-10-24
Al final rebootee anoche, pero no lo soluciono; estoy con:
```

| !(title=alarms) 

```

Setteado, mas tarde pruebo las otras alternativas, lo que si descubri es que las ventanitas molestas de "Alarm" aparecen solo cuando la ventana de Evolution esta minimizada.
Es decir, si la ventana de Evolution NO esta minimizada, y se usa el Ring Switcher, no aparecen las ventanitas de "Alarm" listadas, aunque ud. no lo crea.

---

### Post by santiagoward2000 on 2008-10-25
> **hictio said:**
> Al final rebootee anoche, pero no lo soluciono; estoy con:
```

| !(title=alarms) 

```

Setteado, mas tarde pruebo las otras alternativas, lo que si descubri es que las ventanitas molestas de "Alarm" aparecen solo cuando la ventana de Evolution esta minimizada.
Es decir, si la ventana de Evolution NO esta minimizada, y se usa el Ring Switcher, no aparecen las ventanitas de "Alarm" listadas, aunque ud. no lo crea.

Que loco eso! Solo para probar... ¿si desactivás la opción **Show Minimized** sigue pasando? Está en la etiqueta de **Misc.Options** de las opciones del **Ring Switcher**.
Suerte!

---

### Post by hictio on 2008-10-25
Con el 'Show minimized' desactivado no aparecen, el problema es que pierde bastante utilidad al no circular por las ventanas minimizadas... En fin.

Y encontre otra ventanita, muy chiquita, que se ve cuando esta habilitado el 'Show minimized', el titulo es "Add signature script", es minima, casi no se ve, me parece que es el icono -sin escalar- que se ve en el las que se llaman "Alarms".

Y lo otro, este problema/ bug, lo que sea, afecta a todos los metodos de circular las ventanas de Compiz, por lo menos los que tengo instalados: "Application Switcher", "Ring Switcher" (doh!) & "Shift Switcher".
Sin embargo, usando "Application Switcher" la ventanita minima "Add signature script" no la veo.

Si alguien usa Evolution, tiene Compiz, y usa Hardy, (plain vanilla con todos los updates al dia) y pudiera probar si le pasa lo mismo, seria ideal.

[URL=http://img406.imageshack.us/my.php?image=rsfckupsu6.png]
[IMG]http://img406.imageshack.us/img406/5097/rsfckupsu6.th.png[/IMG]
[/URL]

---

