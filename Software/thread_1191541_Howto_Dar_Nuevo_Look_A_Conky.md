---
title: "Howto: Dar Nuevo Look A Conky"
date: 2009-06-19
forum: Software
---

### Post by nopersona on 2009-06-19
Tema migrado del antiguo foro. Ahora hay un paquete en gnome-look que viene casi listo para ensamblar, a gusto de cada uno. De todas formas, siempre es bueno saber cómo se hacen y se configuran las cosas ;)

Bueno, principalmente lo que haremos será darle otro look a conky, usando una par de scripts y unas cuantas fuentes.

Para dudas sobre la  instalación y la configuración básica de Conky, favor leer este otro tema

[http://ubuntuforums.org/showthread.php?p=7482408#post7482408](http://ubuntuforums.org/showthread.php?p=7482408#post7482408)


Cuando terminemos tendremos algo asi

[[img]http://s1.subirimagenes.com/imagenes/previo/thump_1763483conky.jpg[/img]](http://www.subirimagenes.com/imagen-de-conky-1763483.html)


**1.- Las Fuentes**

Para agregar esos simbolos al costado izquierdo, simplemente basta con poner las fuentes adecuadas, en este caso;

A) Weather
B) PizzaDude Bullets

Ambas las pueden encontrar en cualquier página de Fuentes 

[http://www.dafont.com/](http://www.dafont.com/)

Luego las copian a su directorio de fonts.


**2.- Los Scripts**

Para el clima usaremos:

A) pogodynka (trabaja mejor que weather para el clima, lo único malo es que está en polaco)
B) conditions

[http://www.mediafire.com/?dorbeym2oy3](http://www.mediafire.com/?dorbeym2oy3)

La gracia de esto es que las tipografías cambiarán según el clima (Excepto de noche, que saldrá indistintamente un sol, ya que el script trabaja con "despejado", no diferenciando el día de la noche, cosa de [http://weather.yahoo.com](http://weather.yahoo.com)) 

La temperatura de la CPU la pueden agregar con acpi. Revisen las configuraciones de Conky en su página. 

[http://conky.sourceforge.net/screenshots.html](http://conky.sourceforge.net/screenshots.html)


Si tienen problemas con la codificación de los caracteres (letras extrañas como: H&&%RKO=&, etc) agregen esta línea a .conkyrc


```
# Force UTF8? nota el suporte UTF8 requiere XFT
override_utf8_locale yes 
```


**3.- Trabajando**

En su home hacen una directorio de nombre .skrypty, en donde guardarán y descomprimirán los scripts.

Luego, con cualquier editor de texto, abren pogodynka.sh y editan lo siguiente:

**A) **

# Kod miasta
kod=CIXX0007

Este es el código de su ciudad, por defecto está el mío, Concepción.

**B)**

        echo el_nombre_de_su_ciudad:  $stan
    #echo $stanpl
    echo  Temperatura: $temp C
    #echo Temp. odczuwalna: $tempo C
    #echo Ci¶nienie: $cisn hPa
    #echo Wiatr: $wiatr
    #echo Wilgotno¶æ: $wilg
    #echo Wschód S³oñca: $wsch
    #echo Zachód S³oñca: $zach
    #echo $stanpl, $temp C

Aquí deben descasillar las variabales que desean para mostrar, en mi caso tengo el nombre de la ciudad y la temperatura.

Ahora sólo resta inciar Conky con los parámetros correctos.

[http://www.mediafire.com/?box418nx2nt](http://www.mediafire.com/?box418nx2nt)


Ojo, para  no tener problemas cuando se dibuje el escritorio al inicio, simplemente demoramos la carga de Conky con un script:


```
sudo gedit /usr/bin/inicio-conky
```

Y agregan:

#!/bin/bash
 sleep 25 && conky;

(pueden cambiar el valor de 25 a otro que se acomode al tiempo de carga de su escritorio) 

Después le dan los permisos

```
sudo chmod a+x /usr/bin/inicio-conky
```

Por último lo agregan a los programas de inicio. Preferencias -> Sesiones-> inicio-conky

Con esto ya se soluciona la convivencia entre Conky y Nautilus en el escritorio.


Lo demás queda a su criterio, las posibilidades visuales son infinitas.

Provecho.

[[img]http://s1.subirimagenes.com/imagenes/previo/thump_1799209Pantallazo.png[/img]](http://www.subirimagenes.com/imagen-de-Pantallazo-1799209.html)


P.S.: No olvidar cambiar la ruta y el nombre de su usuario en .conkyrc, así como la temperatura de SU hardware.

---

### Post by Martin Fierro on 2009-07-16
Hola Nopersona,

sugiero que en lugar de incluir el script inico-conky dentro del /usr/bin, el usuario puede simplemente agregar el comando " sleep 20 && conky " a la entrada que realice en Sistema >> Preferencias >> Aplicaciones de Inicio. De esta manera, el usuario estará configurando la aplicación en su espacio de disco, minimizando la posibilidad de cometer errores sobre el sistema operativo.
Saludos.

---

