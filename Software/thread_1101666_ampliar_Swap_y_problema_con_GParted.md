---
title: "ampliar Swap y problema con GParted"
date: 2009-03-20
forum: Software
---

### Post by leosr on 2009-03-20
Hola.
Hace unos meses le agregué 1gb de ram a mi PC, ahora tiene 1,5 gb. Por lo tanto también tiene 512 mb de swap, mi pregunta es si es necesario ampliar la partición swap. Tengo instalado Intrepid.
Algunas veces se llena la swap, aclaro que la mitad de la ram la uso con VirtualBox, y la máquina se pone muy lenta cuando abro varios programas, en especial Firefox.
Cuando quiero ver las particiones con GParted me dice que el sda esta sin asignar y no muestra ninguna de las particiones.
Las particiones serian:
partición 1: win xp
partición 2: /
partición 3: home
partición 4: swap

Adjunto pantallazo de GParted.

Saludos.

---

### Post by euzkoarima on 2009-03-20
En general para la swap se recomienda la mitad de la memoria ram instalada, hasta un máximo de 2Gb (o sea, nunca poner más de 2Gb de swap).

Con 512 estás casi en la mitad, no creo que "haga falta" pero si tenes lugar para agrandarla un poco, dale.

Igual con 1.5 Gb y la mitad para VB, es lógico que la memoria se llene, y se pone lenta por tener que hacer swap contra el disco.

Saludos,
Eduardo

---

### Post by leosr on 2009-03-23
Gracias!
Alguna idea de por qué no me muestra las pariciones el GParted?

Salu2

---

### Post by fmsismo on 2009-03-23
> **leosr said:**
> Hola.
Hace unos meses le agregué 1gb de ram a mi PC, ahora tiene 1,5 gb. Por lo tanto también tiene 512 mb de swap, mi pregunta es si es necesario ampliar la partición swap. Tengo instalado Intrepid.
Algunas veces se llena la swap, aclaro que la mitad de la ram la uso con VirtualBox, y la máquina se pone muy lenta cuando abro varios programas, en especial Firefox.
Cuando quiero ver las particiones con GParted me dice que el sda esta sin asignar y no muestra ninguna de las particiones.
Las particiones serian:
partición 1: win xp
partición 2: /
partición 3: home
partición 4: swap

Adjunto pantallazo de GParted.

Saludos.

Si queres hibernar el equipo debes tener al menos el mismo tamaño (apaga el equipo y grava todo lo que tenes en memoria en la swap, para restaurarlo cuando prendes el sistema).

Si necesitas esta utilidad (es una notebook) y no tenes ganas de estar franeleando con las particiones, podes crear un archivo y formatearlo como swap, editar el fstab y usas eso.  No es TAN performante como una swap propiamente dicha, pero no deberías estar volcando mucho a swap a no ser que estes haciendo cosas extrañas.

La regla que yo uso es:
  Si el equipo tiene menos de 1gb de ram le asigno el doble de swap.
  Si tiene entre 1gb a 4gb le pongo 2gb o el mismo tamaño que la memoria.
  Si tiene más de 4 le pongo 4gb o la 1/2 de la memoria (el mayor valor).

Si es una notebook, siempre trato que tenga el mismo valor o más (uso las dos primeras reglas).

Saludos

---

### Post by leosr on 2009-03-27
Gracias!
Igual, prefiero ampliar la swap, si es que logro que ande bien el GParted!

Sigue sin mostrarme las particiones, será algún problema de permisos o algo por el estilo? Se ejecuta como root. Además probé desde el live cd y pasa lo mismo.
Alguien tiene idea de por qué pasa esto?

Saludos...

---

### Post by gatoyfelpudo on 2009-10-30
leosr: tengo un problema muy similar al que vos describís ¿conseguiste averiguar por qué el gparted te mostraba todo el disco como "sin asignar"? A mí me pasa lo mismo, tanto con el LiveCd del Ubuntu como con el Gparted LiveCd

---

### Post by leosr on 2009-11-03
> **gatoyfelpudo said:**
> leosr: tengo un problema muy similar al que vos describís ¿conseguiste averiguar por qué el gparted te mostraba todo el disco como "sin asignar"? A mí me pasa lo mismo, tanto con el LiveCd del Ubuntu como con el Gparted LiveCd

Hola.
La única solución que encontré fue hacer una instalación limpia. El problema creo que surgió cuando estaba probando otras distribuciones, entre ellas Debian. Creí que el disco 1 era un LiveCD e inicié sin darme cuenta la instalación, la que cancelé al darme cuenta, de ahí en más GParted no me reconoció las particiones.

Más no te puedo ayudar... suerte!

---

