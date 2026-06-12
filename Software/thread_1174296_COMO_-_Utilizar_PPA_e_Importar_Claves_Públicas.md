---
title: "COMO - Utilizar PPA e Importar Claves Públicas"
date: 2009-05-30
forum: Software
---

### Post by pablo.s on 2009-05-30
Esta es una traducción de la página de Launchpad
en la que se explica el uso correcto de un PPA (Archivo
Personal de Paquetes). Le extraje la parte que es más
útil para los usuarios.

[COLOR=#000000][FONT=Droid Serif, serif][SIZE=2]**Instalar y desinstalar programas de un PPA es**[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Droid Serif, serif][SIZE=2][B] tan fácil 
cómo instalar programas del archivo[/B][/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Droid Serif, serif][SIZE=2][B] primario de Ubuntu. 
Esto lo convierte en una[/B][/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Droid Serif, serif][SIZE=2][B] manera ideal de distribuir 
versiones beta,[/B][/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Droid Serif, serif][SIZE=2][B] compilaciones diarias y otras versiones 
de su[/B][/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Droid Serif, serif][SIZE=2]** programa para testear, sin tener que pedir a**[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Droid Serif, serif][SIZE=2][B] tus 
testers que compilen desde el código fuente.[/B][/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Droid Serif, serif][SIZE=2]**Los paquetes que publicas en tu PPA se mantendrán**[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Droid Serif, serif][SIZE=2][B] allí 
hasta que tú los elimines, sean reemplazados[/B][/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Droid Serif, serif][SIZE=2][B] por otro 
paquete que subas o la versión de[/B][/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Droid Serif, serif][SIZE=2][B] Ubuntu ante cuál los 
hayas compilado se haya[/B][/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Droid Serif, serif][SIZE=2]** vuelto obsoleta.**[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Droid Serif, serif][SIZE=2]**Los PPA trabajan como archivos normales de**[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Droid Serif, serif][SIZE=2][B] Ubuntu. 
Puedes instalar programas de la forma[/B][/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Droid Serif, serif][SIZE=2][B] habitual 
&#8211;por ejemplo, a través de apt-get o synaptic--[/B][/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Droid Serif, serif][SIZE=2][B] y cuando
sea que haya una actualización Ubuntu te[/B][/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Droid Serif, serif][SIZE=2][B] informará que 
la instales.[/B][/SIZE][/FONT][/COLOR]
  **[COLOR=#000000][B][FONT=Droid Serif, serif][SIZE=2]Para instalar paquetes de un PPA, tienes que  [/SIZE][/FONT]**[/COLOR][/B][B][COLOR=#000000][B][FONT=Droid Serif, serif][SIZE=2]informarle a 
Ubuntu dónde encontrarlo. Esto lo[/SIZE][/FONT][/B][/COLOR][/B][COLOR=#000000][B][FONT=Droid Serif, serif][SIZE=2] haces informandole de
la URL del PPA, la cuál puedes[/SIZE][/FONT][/B][/COLOR][COLOR=#000000][B][FONT=Droid Serif, serif][SIZE=2] encontrar en la página de 
resumen del PPA.[/SIZE][/FONT][/B][/COLOR]
 [COLOR=#000000][B][FONT=Droid Serif, serif][SIZE=2]
Por ejemplo, observemos el [PPA del Equipo de Pruebas]("https://launchpad.net/%7Eawn-testing/+archive")[/SIZE][/FONT][/B][/COLOR][COLOR=#000000][B][FONT=Droid Serif, serif][SIZE=2][ de AWN]("https://launchpad.net/%7Eawn-testing/+archive"). 
Si estás utilizando la más reciente versión de[/SIZE][/FONT][/B][/COLOR][COLOR=#000000][B][FONT=Droid Serif, serif][SIZE=2] desarrollo de Ubuntu,
todo lo que necesitas es copiar[/SIZE][/FONT][/B][/COLOR][COLOR=#000000][B][FONT=Droid Serif, serif][SIZE=2] esas lineas de la sección 
apt sources.list de la página.[/SIZE][/FONT][/B][/COLOR][COLOR=#000000]**[FONT=Droid Serif, serif][SIZE=2] Por ejemplo:[/SIZE][/FONT]**[/COLOR]
 ```
[COLOR=#000000][FONT=Droid Serif, serif][SIZE=2]**deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) jaunty main**[/SIZE][/FONT][/COLOR] 
[COLOR=#000000][FONT=Droid Serif, serif][SIZE=2]**deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) jaunty main**[/SIZE][/FONT][/COLOR]
```[B][COLOR=#000000][B][FONT=Droid Serif, serif][SIZE=2] 

Si, como mucha gente, estás utilizando otra versión[/SIZE][/FONT][/B][/COLOR][/B][COLOR=#000000][B][FONT=Droid Serif, serif][SIZE=2] de Ubuntu
--digamos, la versión estable más reciente--,[/SIZE][/FONT][/B][/COLOR][COLOR=#000000][B][FONT=Droid Serif, serif][SIZE=2] entonces necesitas
seleccionar la versión de la lista con[/SIZE][/FONT][/B][/COLOR][COLOR=#000000][B][FONT=Droid Serif, serif][SIZE=2] solapa. 
Esto automaticamente actualiza las URL que[/SIZE][/FONT][/B][/COLOR][COLOR=#000000]**[FONT=Droid Serif, serif][SIZE=2] necesitas copiar.[/SIZE][/FONT]**[/COLOR]
  [COLOR=#000000]**[FONT=Droid Serif, serif][SIZE=2]Cada PPA tiene su propia y única clave que es usada para[/SIZE][/FONT]**[/COLOR][COLOR=#000000][B][FONT=Droid Serif, serif][SIZE=2] firmar 
a los paquetes de ese archivo. Esto te deja saber que:[/SIZE][/FONT][/B][/COLOR]
 [COLOR=#000000][B][FONT=Droid Serif, serif][SIZE=2]
 * Los paquetes que estás descargando no han sido [/SIZE][/FONT][/B][/COLOR][COLOR=#000000]**[FONT=Droid Serif, serif][SIZE=2]alterados[/SIZE][/FONT]**[/COLOR][COLOR=#000000][B][FONT=Droid Serif, serif][SIZE=2] 
desde que Launchpad los compiló.[/SIZE][/FONT][/B][/COLOR]  
[COLOR=#000000]**[FONT=Droid Serif, serif][SIZE=2] * Estás descargando del PPA que querías.[/SIZE][/FONT]**[/COLOR] 

    [SIZE=3][COLOR=DarkGreen][I][B][FONT=Droid Serif, serif]Importante: Los paquetes que instalas de un PPA corren 
bajo tu propio riesgo. Ubuntu, Launchpad y Canonical 
no soportan estos paquetes. Tienes que asegurarte que 
confias plenamente en el empaquetador del PPA antes 
de instalar sus programas. [/FONT][/B][/I][/COLOR][/SIZE] 
 [COLOR=#000000][B][FONT=Droid Serif, serif][SIZE=2]
Hasta que no añades la clave del PPA a tu sistema, te aparecerán[/SIZE][/FONT][/B][/COLOR]
 [COLOR=#000000]**[FONT=Droid Serif, serif][SIZE=2]advertencias de que estás descargando de una fuente no confiable.[/SIZE][/FONT]**[/COLOR]
 [COLOR=#000000]**[FONT=Droid Serif, serif][SIZE=2]Si confías en el empaquetador del PPA, añade la clave a tu[/SIZE][/FONT]**[/COLOR][COLOR=#000000]**[FONT=Droid Serif, serif][SIZE=2] sistema.[/SIZE][/FONT]**[/COLOR]
 [COLOR=#000000]**[FONT=Droid Serif, serif][SIZE=2]La manera más sencilla de añadir la clave del PPA a tu sistema[/SIZE][/FONT]**[/COLOR]
 [COLOR=#000000]**[FONT=Droid Serif, serif][SIZE=2]es mirar nuestro [screencast]("http://www.youtube.com/watch?v=UUZOQsNo_ws"). Esto es lo que te cuenta:[/SIZE][/FONT]**[/COLOR]
 [COLOR=#000000][B][FONT=Droid Serif, serif][SIZE=2]
Paso 1: Visita la página de resúmen del PPA en Launchpad.[/SIZE][/FONT][/B][/COLOR]
 [COLOR=#000000]**[FONT=Droid Serif, serif][SIZE=2]Volvamos a la del [Equipo de Pruebas de AWN]("https://launchpad.net/%7Eawn-testing/+archive") que miramos[/SIZE][/FONT]**[/COLOR][COLOR=#000000]**[FONT=Droid Serif, serif][SIZE=2] antes.[/SIZE][/FONT]**[/COLOR]
 [COLOR=#000000][B][FONT=Droid Serif, serif][SIZE=2]
Paso 2: Cliquea en la huella de la clave en la página de resúmen.[/SIZE][/FONT][/B][/COLOR]
 [COLOR=#000000][B][FONT=Droid Serif, serif][SIZE=2]Vas a encontrar algo como esto:
[COLOR=Blue]B0BE17C2A0C914F086B7B8327D2C7A23BF810CD5[/COLOR].[/SIZE][/FONT][/B][/COLOR]
 [COLOR=#000000][B][FONT=Droid Serif, serif][SIZE=2]
Paso 3: Esto te va a llevar a la página de la clave en el servidor[/SIZE][/FONT][/B][/COLOR]
 [COLOR=#000000]**[FONT=Droid Serif, serif][SIZE=2]de claves de Ubuntu. Cliquea en la ID, la que es algo como esto: [/SIZE][/FONT]**[/COLOR] 
 [COLOR=Blue]**[FONT=Droid Serif, serif][SIZE=2]BF810CD5[/SIZE][/FONT]**[/COLOR]
 [COLOR=#000000][B][FONT=Droid Serif, serif][SIZE=2]
Paso 4: Copia la clave pública, que se asemeja a esto:[/SIZE][/FONT][/B][/COLOR]
 [COLOR=#000000][FONT=Droid Serif, serif][SIZE=2]-----BEGIN PGP PUBLIC KEY BLOCK-----[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Droid Serif, serif][SIZE=2]Version: SKS 1.0.10[/SIZE][/FONT][/COLOR]  [COLOR=#000000][FONT=Droid Serif, serif][SIZE=2]mI0ESXS1/wEEALis4to4JdgrkdRunmSTfB2tYRq99Cdcgdh9up4HzAf1yTZ
U1EtmETPP1Uy2[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Droid Serif, serif][SIZE=2]vnAFf/cCunL5VRywNJB3QOxiHdvNlijbdsa0H/fT/ulq+A4iDljUEfsaJug+dAB5uEJE0BzZ[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Droid Serif, serif][SIZE=2]agRjgLbFvRYtsKf3BwZizbo4XtWSAm3JSjZCGZKTABEBAAG0
IkxhdW5jaHBhZCBQUEEgZm9y[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Droid Serif, serif][SIZE=2]IEF3biBUZXN0aW5nIFRlYW2
IRgQQEQIABgUCSXqnWgAKCRBBf7ZCSCH+JPZMAJ4xW7gbpuA+[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Droid Serif, serif][SIZE=2]yedehvDQWdJHHUgseQCgy6NOmAyXqRKrIXWERkXw6h9Ts
RuItgQTAQIAIAUCSXS1/wIbAwYL[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Droid Serif, serif][SIZE=2]CQgHAwIEFQIIAwQWAgMB
Ah4BAheAAAoJEH0seiO/gQzVpSID/0FXxTSLtxPHrT7IE9eif5qJ[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Droid Serif, serif][SIZE=2]vjOjzcmOCXe9/3G0ctV8IfYHx0VynddjxgTqJ9WuEjMLVHRgXvK1
Rw1XMlik+MeyyHrr9EWQ[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Droid Serif, serif][SIZE=2]DUFbUs+Yc2usRyZY8pVe2Uwy2x7lF
si6VBfo0k9jVsu1l1qBU9BhANJDUTHjR15aPYiUJiZa[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Droid Serif, serif][SIZE=2]13CZ[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Droid Serif, serif][SIZE=2]=a6Gh[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Droid Serif, serif][SIZE=2]**-----END PGP PUBLIC KEY BLOCK-----**[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Droid Serif, serif][SIZE=2][B]

Paso 5: Pega la clave pública en un editor de texto y guardala.[/B][/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Droid Serif, serif][SIZE=2][B]

Paso 6: Abre el menú Sistema &#8594; Administración &#8594; Fuentes de[/B][/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Droid Serif, serif][SIZE=2][B]
Software y cliquea en la solapa Autentificación.[/B][/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Droid Serif, serif][SIZE=2][B]

Paso 7: Cliquea en Importar Clave Pública, selecciona la clave[/B][/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Droid Serif, serif][SIZE=2][B]que
habias guardado previamente y listo!


[/B][/SIZE][/FONT][/COLOR]```
[COLOR=#000000][FONT=Droid Serif, serif][SIZE=2][B][COLOR=DarkGreen][SIZE=4][COLOR=Silver]ACTUALIZACION 5 de Junio[/COLOR][/SIZE]

[/COLOR][/B][COLOR=Black]Dominic Evans ha realizado un script llamado 
"launchpad update" que busca todas las claves 
de los PPA por nosotros.
Hay que [descargarlo]("http://bazaar.launchpad.net/%7Eoldman/%2Bjunk/launchpad-update/download/head%3A/launchpadupdate-20090603123623-qo8gcw2k08v3dib8-1/launchpad-update"), darle permisos de ejecución
(chmod 755) y ejecutarlo.[/COLOR][/SIZE][/FONT][/COLOR]
```[COLOR=#000000][FONT=Droid Serif, serif][SIZE=2][COLOR=Black] 

[/COLOR][/SIZE][/FONT][/COLOR]```
[COLOR=#000000][FONT=Droid Serif, serif][SIZE=2][B][COLOR=DarkGreen][SIZE=4]ACTUALIZACION 17 de Octubre[/SIZE]

[/COLOR][/B][COLOR=Black]A partir de la versión Karmic Koala 9.10 hay un
comando nuevo llamado [/COLOR][/SIZE][/FONT][/COLOR]**add-apt-repository** que[COLOR=#000000][FONT=Droid Serif, serif][SIZE=2][COLOR=Black]
añade el PPA y la clave pública del PPA de forma
automática. Su modo de uso es
[/COLOR][/SIZE][/FONT][/COLOR][COLOR=DarkGreen]**sudo add-apt-repository ppa:nombre-del-ppa**[/COLOR][COLOR=#000000][FONT=Droid Serif, serif][SIZE=2][COLOR=Black].[/COLOR][/SIZE][/FONT][/COLOR]
```[COLOR=#000000][FONT=Droid Serif, serif][SIZE=2][COLOR=Black] 
[/COLOR][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Droid Serif, serif][SIZE=2][COLOR=Black] 
[/COLOR][/SIZE][/FONT][/COLOR]

---

