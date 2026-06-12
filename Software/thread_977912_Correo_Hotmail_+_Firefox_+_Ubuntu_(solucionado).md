---
title: "Correo Hotmail + Firefox + Ubuntu (solucionado)"
date: 2008-11-10
forum: Software
---

### Post by pabloatilio on 2008-11-10
Si tienen problemas para poder escribir nuevos correos en una cuenta de hotmail, ahora que el servicio cambió el diseño de la página, lo que tienen que hacer  desde ubuntu + firefox, es lo siguiente :

1) abrir el navegador firefox
2) escribir en la barra de direcciones : about:config (enter)
3) aceptar la advertencia que se les presentará
4) buscar el valor general.useragent.vendor 
5) borrar el valor que tiene ("ubuntu")
6) reiniciar el navegador

Lísto !! , ahora funciona, que RARO que sólo pase con ubuntu no ??


fuente: [http://www.geekets.com/2008/11/07/como-poder-escribir-correos-hotmail-firefox-ubuntu-kubuntu-810/](http://www.geekets.com/2008/11/07/como-poder-escribir-correos-hotmail-firefox-ubuntu-kubuntu-810/)

Saludos !!

PabloA

---

### Post by sergiom99 on 2008-11-10
cuando lo cambio, cierro y reinicio firefox, al volver a abrir me aparece de vuelta el mismo valor!
que otra forma de hacerlo hay?

---

### Post by ramiro_md on 2008-11-10
Yo lo solucioné así jeje:
[https://www.google.com/accounts/NewAccount?continue=http%3A%2F%2Fwww.google.com.ar%2F&hl=es](https://www.google.com/accounts/NewAccount?continue=http%3A%2F%2Fwww.google.com.ar%2F&hl=es)

---

### Post by granjero on 2008-11-12
a mi me pasa lo mismo que a sergiom99 cuando lo borro y vuelve a aparecer el valor... 

alguno tiene una explicación...

gracias!

---

### Post by pabloatilio on 2008-11-13
> **granjero said:**
> a mi me pasa lo mismo que a sergiom99 cuando lo borro y vuelve a aparecer el valor... 

alguno tiene una explicación...

gracias!

Hola amigos, subí la solución porque la probé y me funcionó perfecto, lo hice en 3 computadoras y en todas igual. ¿tendrá que ver en como borran la clave?, bueno, antes puse la info tal cual la encontré, para respetar la fuente, pero por si sirve de algo, les  explico detalladamente como lo hago yo:

1) en la barra de direcciones de firefox pongo "about:config" sin comillas y (enter)

2) acepto la advertencia de que puedo cancelar la garantía (click en botón "seré cuidadoso...")

3) pongo en la barra de arriba , la que dice a la izquierda "filtro", la palabra "ubuntu". A medida que voy escribiendo la palaba me filtra las posibles entradas que estoy buscando.

4) cuando encuentro "general.useragent.vendor" le hago doble click a esa entrada y me aparece una ventana con el valor para editar, lo borro y clickeo en "aceptar"

5) reinicio y listo.


Como dije antes, hice la corrección en 3 equipos sin problemas, ¿a alguien SI le funcionó esta solución?,  parece medio para lelos la explicación que agregué pero es para ver si por ahi se dan cuenta que paso hacen distinto y les sirve, nose de que otra forma poder ayudarlos.
Espero puedan solucionarlo, saludos a todos.

Pablo A

---

### Post by sergiom99 on 2008-11-13
Gracias Pablo, lo estoy haciendo igual! :'( 
pero no me aparece nunca el punto 4 y al reiniciar FF el valor esta de nuevo en 'Ubuntu'.
Aclaro que no uso FF3 sino el 2.0.1x

---

### Post by granjero on 2008-11-13
gracias pabloatilio por la explicación, yo tengo firefox 3 y cada vez que reinicio el firefox la bendita linea reaparece.

en un momento lo que hice fue después de modificar la entrada ubuntu poner ctrl+s y se guardo un archivo "about:config.xul" en el escritorio. anduvo joya hasta que el archivo me molesto la vista en el escritorio y lo borré y volvió el condenado valor ubuntu.

entonces repetí la operación guardando el archivo en .mozilla que esta en home. y no funciono. pensé en guardarlo de nuevo en el escritorio y ocultarlo pero tampoco funcionó la segunda vez que se guardo el .xul en el escritorio.

me recomendaron instalar el agent swithcer pero tampoco funciona.

me recomedaron instalar el firefox 3.1bno se cuanto. "mindfield" y tampoco funciona.

se que una solución es mandar a la ****** la cuenta de hotmail pero tiene tantos años y me llegan tantas cosas que no quiero que llegeuen a mi gmail que me gustaría poder solucionar el problemita...

otra cosa que note medio bizarra es que de tanto tocar mi usuario perdió los privilegios sobre la partición "sistema de archivios" ahora tiene un candado...  pero eso me parece que no debe ser muy difícil de solucionar...

salud y gracias por la buena onda.

---

### Post by c4d0rn4 on 2008-11-13
granjero

te doy una solución, que creo es casi 99,9% efectiva, pero es a lo BP (Bestia Peluda)

Crea un usuario nuevo en linux, logeate, y fijate si te da problema. Si anda te pasas a ese usuario y borras el viejo, si no anda borras el nuevo ajja xD.

Dale lo mismo privilegios al usuario nuevo que al que tenés ahora.

---

### Post by pabloatilio on 2008-11-14
> **granjero said:**
> 
se que una solución es mandar a la ****** la cuenta de hotmail pero tiene tantos años y me llegan tantas cosas que no quiero que llegeuen a mi gmail que me gustaría poder solucionar el problemita...



La verdad que con lo que hicierion estos de M$, dan ganas de eso, yo también por tener una cuenta de taaaanntosssss años con estos tipos no puedo dejar de usarla, aunque de a poco voy migrando de servicio.

Y con respecto a los que no pueden solucionarlo, no se que decirles, a mi me resulto tan fácil como les expliqué anteriormente, ¡y en 3 equipos distintos!. Supongo que habrá que ir a alguna configuración más profunda del asunto y ahi ya no me dá el cuero para ayudar, ojalá encuentren la solución.

Saludos

Pablo A

---

### Post by SLA_leandrin on 2008-11-14
> **ramiro_md said:**
> Yo lo solucioné así jeje:
[https://www.google.com/accounts/NewAccount?continue=http%3A%2F%2Fwww.google.com.ar%2F&hl=es](https://www.google.com/accounts/NewAccount?continue=http%3A%2F%2Fwww.google.com.ar%2F&hl=es)

Ramiro, pusiste mal el link...

Por otro lado, cambiar el vendor en el firefox no me parece una "solución"

---

### Post by sergiom99 on 2008-11-15
> **SLA_leandrin said:**
> 
Por otro lado, cambiar el vendor en el firefox no me parece una "solución"

es cierto, es un "ugly fix" pero de cualquier manera, queremos hacerlo funcionar y ya.

como diria Cartman "Iran/Irak..."

---

