---
title: "Maple11 - Interfaz gráfica toda gris..."
date: 2008-10-03
forum: Software
---

### Post by carlosgim on 2008-10-03
Hola a todos, soy nuevo en el foro, tengo el siguiente pronblema: :(

[LIST=1]
[*]Instale el programa desde un archivo .bin en el root.
[*]Trate de ejecutar y no funcionó. Creí que  tenía que ver con el lugar de instalación.
[*]Instalé nuevamente el programa, pero esta vez en mi usuario: carlos
[*]Intenté ejecutar y nuevamente no funcionó.
[/LIST]

Ahora voy a detallar que es lo que no funcionó. El programa instalado muestra una pantalla toda gris, pero el programa esta funcionando, lo sé por que al pasar el mouse se activan los menues. Bueno espero se entienda lo que acabo de relatar. Disculpen si no.

Muchas gracias de antemano.

Atte. CarlosGim

---

### Post by juanman on 2008-10-04
Nunca lo usé, pero he leido q Maple suele dar problemas... Proba ejecutandolo desde consola y pega acá si tira errores... Estas usando compiz? Que version de java? (para averiguar, en consola: java -version) Y que drivers de video?

Hay alternativas libres mas faciles de instalar y con mejor soporte en Ubuntu, como Maxima, SAGE, Axiom o Scilab...

---

### Post by carlosgim on 2008-10-07
Bueno ejecuto el programa y luego:
```

Locking assertion failure. Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [xcb767c767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb767c8cbi]
#2 /usr/lib/libX11.so.6(_Reply+0xfd) [0xb09e81bd]

```
Bueno y luego sigue todo el codigo, el problema es que no se como copiarlo desde consola. 
Respecto a la version de java, ejecute lo que me dijiste pero aparece
```
bash: java-version: orden no encontrada
```:confused:
Se agradece la paciencia.

Saludos

---

### Post by WanderingKnight on 2008-10-07
El comando es:

```
java -version
```

no java-version (nótese el espacio). Eso significa que estás ejecutando el comando "java" y tirándole la opción "version", que te tira la versión de Java que tenés instalada.

---

### Post by Mister X on 2008-10-07
Es un programa hecho en java?
A mi me paso siempre con el AquaDataStudio, para usarlo tenia que deshabilitar Compiz sino veia todo gris.
Lo pude solucionar hace poco, lo que hice fue borrar la carpeta jre (el runtime de java)  que está dentro del directorio de instalacion del programa, de esa manera fuerzo al programa a usar el runtime de java que tiene instalado Ubuntu, que en mi caso anda joya.

---

