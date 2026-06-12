---
title: "Mis efectos de escritorio murieron"
date: 2009-06-29
forum: Software
---

### Post by Fisaulerod on 2009-06-29
Hola, resulta que ahora estaba ahí en mi Ubuntu y de repente noto que desaparecieron los bordes de las ventanas y todo se puso feo...a fin de cuentas, compiz dejo de funcionar. Luego traté de activar los efectos y me dice que no se puede activar los efectos de escritorio. ¿Qué pasó?, antes me funcionaba a la perfección.
Cuando pasó eso sólo estaba tratando de instalar Simcity 3000 en Linux (el nativo), que no funcionó. Pero en el instante mismo que se desactivo compiz yo no estaba haciendo nada.
¿Qué puedo hacer?, gracias de antemano.

---

### Post by moreback on 2009-06-30
Se puede haber muerto el Compiz, ejecútalo con Alt+F2 y escribe **compiz --replace**.

---

### Post by Fisaulerod on 2009-06-30
Hice eso y funcionó, volvió compiz. Pero debo hacer eso cada vez que reinicio, ya que al prender el pc de nuevo otra vez esta todo desconfigurado y feo :S

---

### Post by moreback on 2009-06-30
A mi me pasó algo similar y lo arregle usando **Sistema -> Preferencias -> Aplicaciones al inicio**. Ahí me fui a la pestaña **Opciones** y marqué la única opción que sale: **Recordar automáticamente las aplicaciones en ejecución al salir de la sesión**.

Ojo que tienes que dejar sólo las aplicaciones que quieras al inicio y de ahí desloguearte y loguearte nuevamente.

Saludos.

---

### Post by nopersona on 2009-07-01
> **moreback said:**
> A mi me pasó algo similar y lo arregle usando **Sistema -> Preferencias -> Aplicaciones al inicio**. Ahí me fui a la pestaña **Opciones** y marqué la única opción que sale: **Recordar automáticamente las aplicaciones en ejecución al salir de la sesión**.

Ojo que tienes que dejar sólo las aplicaciones que quieras al inicio y de ahí desloguearte y loguearte nuevamente.

Saludos.


Yo implementé una más fácil, ya que tuve problemas con la configuración de compiz, conky, screenlets y cairo-dock al inicio, ya que compiz no guardaba la configuración y al iniciarse aquellas aplicaciones, erraban en el composite, por ende, todo se veía horrible. 
 
La solución fue demorar el incio de cada proceso con un sencillo script, dándole la partida a compiz, sería algo así:

```
sudo gedit /usr/bin/inicio-compiz
```

Agregar:

```
#!/bin/bash
sleep 5 && fusion-icon;
```

El sleep depende de la carga de tu escritorio, en mi caso es de 3 a 5 segundos. 

Después le otorgas los permisos

```
sudo chmod a+x /usr/bin/inicio-compiz
```

Y por último lo agregas al inicio: Preferencias> Aplicaciones al inicio> inicio-compiz


Luego vas tirando lo que quieras que se inicie, sin problemas. De ahí hago un temita para explicarlo mejor.

Saludos!

---

### Post by Fisaulerod on 2009-07-01
gracias :P

---

### Post by Carlos C on 2009-07-01
> **Fisaulerod said:**
> gracias :P
¿Solucionado?

---

