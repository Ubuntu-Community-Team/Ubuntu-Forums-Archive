---
title: "Consulta compiz (lo más seguro consultonta)"
date: 2008-10-21
forum: Software
---

### Post by chulelinux on 2008-10-21
Hola gente, Tengo compiz configurado en hardy pero para que cargue cada vez que reinicio o prendo la máquina tengo que reload window manager en el icono de compiz para que cargue.
No pude encontrar como solucionarlo para que cargue directamente sin hacer nada. Disculpen pero no encontré la info en los foros...
Slds

---

### Post by Hernán-Amaya on 2008-10-21
probá instalando compiz-fusion-icon creo que era así el paquete no estoy en mi casa.

---

### Post by santiagoward2000 on 2008-10-21
> **Hernán-Amaya said:**
> probá instalando compiz-fusion-icon creo que era así el paquete no estoy en mi casa.

Por lo que veo, ya tiene el fusion-icon instalado:

> **chulelinux said:**
> tengo que reload window manager en el icono de compiz para que cargue.

Ya que estoy, me sumo al pedido, jeje. A mí me pasa lo mismo (por alguna razón me pasa en Gnome, pero no en Xfce), aunque no le doy mucha bola.
Una solución medio casera sería agregar ```
compiz --replace
``` a la lista de StartUp programs, pero me parece raro que el fusion-icon no lo haga solo.
Saludos!

---

### Post by hictio on 2008-10-21
Que desktop environmet estas usando? KDE?
Hiciste un updgrade de alguna version anterior de Ubuntu a Hardy, o instalaste Compiz directamente en esta version?

Aca hay info de como automatizar el arranque:

[Need to "reload window manager" each time I start X]("http://forum.compiz-fusion.org/showthread.php?t=9904")

Con el paquete que dice Hernán-Amaya, yo instale Compiz en Hardy, y no tuve ese problema, si tenia el problema que no re-emplazaba el window manager por Beryl, pero es un segundo de arreglar.

---

### Post by hictio on 2008-10-21
santiagoward2000,

Que raro eso, yo lo que tuve que hacer para que en Compiz usara el window manager Emerald, y dejara de usar metacity, es en:

"System -> Preferences -> Advanced Desktop Effects Settings -> Effects -> Window decorations"

en en el box de 'Command', puse 'emerald --replace' sin comillas, y claro, uso Emerald.

---

### Post by santiagoward2000 on 2008-10-21
> **hictio said:**
> Aca hay info de como automatizar el arranque:

[Need to "reload window manager" each time I start X]("http://forum.compiz-fusion.org/showthread.php?t=9904")

Por lo que entiendo (creo que tiene el mismo problemita que yo) es que el fusion-icon ya está puesto para que arranque solo (como dice en ese foro), pero por alguna razón no arranca Compiz, solo aparece el ícono en el panel. Entonces tiene que hacer click en la opción **Reload Window Manager** del ícono.

---

### Post by chulelinux on 2008-10-22
Disculpen que no pude contestar antes y gracias por las respuestas... Tengo instalado hardy con el entorno de gnome. Tengo instalado el compiz icon. Me anda perfecto todo pero siempre tengo que apretar reload para que me anden los efectos de escritorio. Tengo marcado el window decorator en efectos. La verdad que no me muestra ningún error ni nada, solo el detalle de tener que apretar que recargue para que arranque. Como Window decorator uso GTK pero es lo mismo si marco y uso emerald. No hice ningún upgrade ni nada y tengo todo instalado de 0 desde hace un mes y no le encontré la vuelta. Ya lo reinstalé de vuelta varias veces por eso pensé que era un detalle de configuración que se me escapaba.

---

### Post by eldanyel on 2009-11-04
Me pasa lo mismo, tengo configurado para que se inicie fusion-icon al inicio pero cada vez que arranco el sistema tengo que darle a "reload window manager" en el fusion-icon para ver el compiz. A parte de eso, el compiz funciona perfectamente.

Lo raro es que solo me pasa en el portátil

---

### Post by santiagoward2000 on 2009-11-04
> **eldanyel said:**
> Me pasa lo mismo, tengo configurado para que se inicie fusion-icon al inicio pero cada vez que arranco el sistema tengo que darle a "reload window manager" en el fusion-icon para ver el compiz. A parte de eso, el compiz funciona perfectamente.

Lo raro es que solo me pasa en el portátil

Hola!
¿Qué parámetro tiene el comando de **fusion-icon** que agregaste para que arranque? El lanzador que está en el menú aparece con el comando:
```
fusion-icon --no-start
```
Si está así probá sacarle el **--no-start**.
Si no, podés probar agregarle la opción: **--force-compiz**.
Saludos!

---

### Post by josecuervo86 on 2009-11-04
Gente, por ahi al instalar fusion-icon se produce un conflicto con compiz y no abre. A mi me pasaba lo mismo y la solución fue sacar a fusion-icon del start. Luego de eso compiz salio andando solito.

---

### Post by eldanyel on 2009-11-05
> **santiagoward2000 said:**
> Hola!
¿Qué parámetro tiene el comando de **fusion-icon** que agregaste para que arranque? El lanzador que está en el menú aparece con el comando:
```
fusion-icon --no-start
```Si está así probá sacarle el **--no-start**.
Si no, podés probar agregarle la opción: **--force-compiz**.
Saludos!
Gracias por la respuesta. Aunque yo lo tenía configurado sin parametros he probado tu propuesta y de todos modos no funciona.

JoseCuervo tiene razón, por lo visto el fusion-icon hace de las suyas. Lo he quitado del inicio, he vuelto a activar los efectos en sistema>preferencias>apariencia y he activado el emerald con el fusion-icon. Ahora todo funciona correctamente. 

Gracias a ambos!

---

