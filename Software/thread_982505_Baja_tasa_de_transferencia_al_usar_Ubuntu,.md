---
title: "Baja tasa de transferencia al usar Ubuntu,"
date: 2008-11-14
forum: Software
---

### Post by Just64 on 2008-11-14
Estoy actualizando de 8.04 a 8.10 y lo esta haciendo a una tasa de tasa de descarga q llega con suerte a los 40kb/s, mientras q en WinXp mi tasa normal es de 120+kb/s. No solo es la actualizacion,tmb los torrents, las descargas directas, en general es..
Q puedo hacer?

---

### Post by aregnando on 2008-11-14
Hola Just64, un dato que saqué de alguno de tantos tutos que hay me sirvió de mucho para acelerar las descargas de actualizaciones.
Tenés que ir a Sistema>Administracion>Origenes del software, una vez ahí en la pestaña Software de Ubuntu vas a la opción Descargar desde, la abris y pones Otro, y presionas el botón Seleccionar el mejor servidor a lo cual el sistema hará un testeo de los diferentes servidores y te va a permitir seleccionar el que te brinda mayor velocidad de descarga.
Espero que te haya sido de ayuda.
Saludos.

---

### Post by luks911 on 2008-11-14
> **Just64 said:**
> Estoy actualizando de 8.04 a 8.10 y lo esta haciendo a una tasa de tasa de descarga q llega con suerte a los 40kb/s, mientras q en WinXp mi tasa normal es de 120+kb/s. No solo es la actualizacion,tmb los torrents, las descargas directas, en general es..
Q puedo hacer?

Buenas, 
Un par de preguntas: ¿con 8.04 la transferencia también era más lenta que en el XP? ¿Con qué hardware te conectás (placa de red, placa wifi)? Porque se me ocurre que puede ser un tema de drivers, capaz que con cambiarlos se arregla. De paso: ¿instalaste o compilaste algún driver para ese hard o Ubuntu te lo detectó sin que hagas nada?

Para ver el hard:

```
lspci | grep net
```

si es una placa pci

```
lsusb | grep net
```

si es una placa usb, alguna wifi por ejemplo. Ejecutalos y pegá acá el resultado. (El grep lo que hace es filtrar los datos para que te muestre los que tengan, en este caso, la palabra "net". Es para achicar el resultado.)

saludos

---

### Post by Just64 on 2008-11-14
Aregnando: Ahora pruevo, pero el tema es q en caso de q eso llegara a funcionar, no me arreglaria todas las otras aplicaciones como torrents, descarga directa, etc.

luks911: En este momento tengo 8.04, estoy trando de actualizar, y lo hace a 40-50Kb/s. Tengo la pc conectada a traves de placa de red.
(En estos momentos tengo 2 pcs en casa q las conecte con un switch, ovbiamente con el modem ruteado, x lo q las PC se me conectan de manera instantantea, ya sea en Xp o 8.04. Antes de hacer esto nunca me habia podido conectar a inet dsd 8.04 configurando la coneccion manualmente, pero igualmente no tomaria esto en cuenta xq posiblente lo alla echo mal yo, ya q soy muy noob en Ubu.)

---

### Post by Zootropo on 2008-11-15
Prueba a desactivar IPv6

[http://www.guia-ubuntu.org/index.php?title=Deshabilitar_IPV6](http://www.guia-ubuntu.org/index.php?title=Deshabilitar_IPV6)

---

### Post by luks911 on 2008-11-15
> **Just64 said:**
> luks911: En este momento tengo 8.04, estoy trando de actualizar, y lo hace a 40-50Kb/s. Tengo la pc conectada a traves de placa de red.
(En estos momentos tengo 2 pcs en casa q las conecte con un switch, ovbiamente con el modem ruteado, x lo q las PC se me conectan de manera instantantea, ya sea en Xp o 8.04. Antes de hacer esto nunca me habia podido conectar a inet dsd 8.04 configurando la coneccion manualmente, pero igualmente no tomaria esto en cuenta xq posiblente lo alla echo mal yo, ya q soy muy noob en Ubu.)

Cuando hablo de hard me refiero a la placa de red o wifi de la PC, más allá de que la conexión sea manual o a un router. Lo planteo porque leyendo en Ubuntu-es vi de algunos casos de placas con chip Realtek que si bien son detectadas por Ubuntu y se conectaban, tenían problemas de velocidad que se solucionaban instalando otros dirvers.

Saludos

---

### Post by majatu on 2008-11-18
A mi me es de bajar extremadamente lento las actualizaciones durante el dia (servidor para argentina), voy a ver si de alguna de estas formas ayuda un poco, porque intente pero me tengo que poner a actualizar de noche/madrugada para que baje a una velocidad respetable.

Saludos

---

### Post by guillermolisi on 2008-11-19
> **majatu said:**
> A mi me es de bajar extremadamente lento las actualizaciones durante el dia (servidor para argentina), voy a ver si de alguna de estas formas ayuda un poco, porque intente pero me tengo que poner a actualizar de noche/madrugada para que baje a una velocidad respetable.

Saludos

En general, es bastante frecuente que con los repositorios de Argentina se logren tasas de transferencia mas bajas que con los de Brasil.

Prueben con Brasil para poder comparar y despues deciden cual usar.

---

### Post by santiagoward2000 on 2008-11-21
> **guillermolisi said:**
> En general, es bastante frecuente que con los repositorios de Argentina se logren tasas de transferencia mas bajas que con los de Brasil.

Prueben con Brasil para poder comparar y despues deciden cual usar.

Una pregunta: ¿Cuáles son los repositorios de Argentina? En mi lista de servers no aparece.

---

