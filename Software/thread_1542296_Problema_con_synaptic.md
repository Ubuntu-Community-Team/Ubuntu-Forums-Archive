---
title: "Problema con synaptic"
date: 2010-07-30
forum: Software
---

### Post by Simbiosys on 2010-07-30
Buenas!
A ver si pueden ayudarme, intenté hacer una búsqueda en el foro para ver si alguien ya tuvo este inconveniente y algo encontré, inconvenientes parecidos pero mis pruebas en base a lo encontrado no fueron satisfactorias y no quiero hacer lío dado que si toco algo seguro termino rompiendo más.

Cuando abro el gestor de actualizaciones me sale el siguiente error: 

```
W: Error de GPG: http://packages.medibuntu.org lucid Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 2EBC26B60C5A2783
```

Entonces, de acuerdo a lo que leí en el foro (problemas similares) ejecuté el siguiente comando: 

```
gpg --recv-keys --keyserver wwwkeys.eu.pgp.net 2EBC26B60C5A2783
```

Y el resultado fue:

```
gpg: /home/nahuel/.gnupg: directorio creado
gpg: creado un nuevo archivo de configuración `/home/nahuel/.gnupg/gpg.conf'
gpg: AVISO: las opciones en `/home/nahuel/.gnupg/gpg.conf' no están aún activas en esta ejecución
gpg: anillo Â«/home/nahuel/.gnupg/secring.gpgÂ» creado
gpg: anillo Â«/home/nahuel/.gnupg/pubring.gpgÂ» creado
gpg: solicitando clave 0C5A2783 de hkp servidor wwwkeys.eu.pgp.net
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no se han encontrados datos OpenPGP válidos
gpg: Cantidad total procesada: 0
```

Recalco el **HTTP fetch error 7: couldn't connect to host** y aclaro que ese momento tenía internet y todo andaba bien.

También entré a medibuntu y corroboré que funcione, pero el error sigue y no se como solucionarlo.

Además, ¿Que se supone que creó si al final no pudo conectarse? ¿Borro esos archivos?

Para que sepan tengo instalado Ubuntu 10.04 y mi computadora es una Dell Inspiron 1525.

Desde ya muchas gracias, saludos.
Nahuel

---

### Post by atari130xe on 2010-07-30
Para Medibuntu yo hice algo mucho mas simple: Ubuntu Tweak, simplemente elegís el PPA de Medibuntu y Ubuntu Tweak por sí solo hace todo el trabajo, valída las claves GPC e instala el repositorio que en mi caso funciona perfecto.
saludos

---

### Post by guillermolisi on 2010-07-30
Antes de llevar a cabo la recomendacion de Atari130xe, borra el repositorio y claves relacionadas con Medibuntu de la lista de origenes de software/repositorios (Synaptic).

---

### Post by Simbiosys on 2010-08-02
Hola!

No instalé el Ubuntu Tweak, solucioné el problema borrado los repositorios de medibuntu desde la configuración del synaptic y luego siguiendo las instrucciones desde la ([página de medibuntu]("https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repository").

Gracias a todos por el aporte. La macana me la mandé siguiendo las instrucciones de howtoforge a perfect dekstop. Parece que en la guía se morfaron el tema de las llaves gpg de medibuntu... (o me las morfé yo).

Siguiendo la guía de medibuntu funciona todo perfecto.

Muchas gracias.
Saludos, Nahuel.-:)

---

