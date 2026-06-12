---
title: "Regresar a un estado anterior"
date: 2009-09-16
forum: Software
---

### Post by krakc on 2009-09-16
Hola

bueno les cuento que mate mi ubuntu, ¿como lo hice?, asi:

estaba instalando la ultima version de cedega 7 y me tiraba un error que nesecita python2.4-dbus y entonces lo que hice fue instalar las ultimas versiones de python (2.5 y 2.6) como no me funciono bien eso decidi ir a synaptic y desinstalar todas las versiones de python y reinstalar las 2.4.... y ocurrio la tragedia, sin darme cuenta (no lei) le di si a todo y me desinstalo todo... TODOOOO

no tengo red, no tengo firefox, no tengo ktorrent no tengo terminal, no tengo nada de nada (quedaron pocas cosas) simplemente elimino todo (como el 90% de las cosas que se instalan cuando se instala ubuntu)

asi que lo que quiero es recobrar mi ubuntu a un estado anterior (por ejemplo ayer) ... nunca he creado un backup o algo asi, alguna solucion o ya me toco formatear???

hay alguna manera de decirle a ubuntu que me instale lo que desinstalo ??? ( y que me perdone que no lo vuelvo a hacer jajajaja)
:lolflag:

PD: estoy desde el live CD....

PD2: ayudaa.......

---

### Post by Hei Ku on 2009-09-16
Te quedó al menos el apt? Si es así, podes probar de darle sudo apt-get install ubuntu-desktop, agregando el cd mientras no tengas red.

Eso siempre que tengas al menos el apt-get

Si no, reinstala porque igual es como si empezaras de vuelta.

Ah, y no, no tenes undo.

---

### Post by staar on 2009-09-16
pregunta, podés acceder a una consola virtual y loguearte? decís que no tenés red, como hacés para conectarte normalmente? porque podrías configurar la conexión desde la consola, y usar apt pra volver a instalar todo (previo recuperar una lista de lo que desinstalaste)

saludos

---

### Post by krakc on 2009-09-16
> **staar said:**
> pregunta, podés acceder a una consola virtual y loguearte? decís que no tenés red, como hacés para conectarte normalmente? porque podrías configurar la conexión desde la consola, y usar apt pra volver a instalar todo (previo recuperar una lista de lo que desinstalaste)

saludos

si puedo loguearme desde la consola negra, perdi todo el entorno grafico, creo que se desintalo todo gnome.

no tengo red tambien se desinstalo, para poder entrar a internet estoy usando el live cd

como configuro la red desde la consola o donde recupero la lista de lo que desinstale???

gracias.

---

### Post by Hei Ku on 2009-09-16
podes usar el apt-get e instalar lo que puedas desde el live cd. Con eso deberias recuperar la red y el desktop. Pero tenes que fijarte que el apt-get todavia este ahi

---

### Post by josecuervo86 on 2009-09-16
A mi me paso algo parecido hace muchisimo (cuando recién empezaba), desinstale todo el entorno gráfico queriendo eliminar samba (?). Lo resolvi con lo primero que se me vino en mente:

```
sudo apt-get install gnome
```

---

### Post by gmunioz on 2009-09-16
Hola kra......:

1- Si puedes iniciar en consola, no todo esta

perdido. GnuLinux ¡¡es la consola!! lo demás

es agregado.

2- Ejecuta en la consola

```
sudo su

dhclient
```

si se conecta la red

```
apt-get update

apt-get upgrade

apt-get install ubuntu-desktop
```

si no se conecta la red, es raro pero

no imposible

nano /etc/apt/sources.list

Comenta todas las líneas con almohadilla (#)

menos la que hace referencia la cdrom, que si tiene

almohadilla se la sacas.

guardas el archivo

introduces el cd

ejecutas

```
apt-get update

apt-get upgrade

apt-get install ubuntu-desktop
```

---

### Post by juancarlospaco on 2009-09-16
Suerte!,
lo ironico es que se puede hacer **sudo aptitude install apt-get**

---

