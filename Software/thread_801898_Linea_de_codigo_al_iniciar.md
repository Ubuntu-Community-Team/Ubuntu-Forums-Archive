---
title: "Linea de codigo al iniciar"
date: 2008-05-21
forum: Software
---

### Post by Applelnx on 2008-05-21
Hola de nuevo, queria saber si era posible agregar una linea en algun archivo para que al iniciarse ubuntu se cargue

```

sudo rmmod bttv
sudo modprobe bttv card=151
```

No se si es posible ni como hacerlo

Agradezco que se tomen el tiempo para leer :D

Saludos

---

### Post by Hei Ku on 2008-05-21
En principio, eso deberia ir al /etc/modules me parece.
Uno a la parte de blacklist y el otro para cargar. 
Como son modulos de kernel, hay otras maneras de cargarlos que no sean mediante un script.

---

### Post by faktorqm on 2008-05-21
no! a la blacklist no por que el necesita bajar el bttw, pero volver a levantar el mismo pero pasandole parametros. 
Lo que tenes que hacer como bien te dijo Hei Ku, es editar el archivo /etc/modules e ir a la linea donde dice bttw y agregarle el card=151 al lado, y reiniciar. Ahi te queda para siempre. Salu2!!

---

### Post by Applelnx on 2008-05-21
Esto es lo unico que dice mi /etc/modules

```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
```

tengo que agregar una linea que diga "bttv card=151" ?

---

### Post by User21 on 2008-05-21
Y Deberia quedarte asi:
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
bttv card=151
``` Guardás el archivo y listo. Si con eso te funciona, perfecto. Sino, deberías agregar también tuner y radio. Por ejemplo:
bttv card=151 tuner=2 radio=1
De mas esta decir que tenés que tener permisos de administrador, eh ?

---

### Post by Applelnx on 2008-05-21
No funciono :s

La verdad que el numero de tuner y radio no lo tengo, porque poninedo solo card=151 podia usar todo.

tendre que poner algo de rmmod? No entiendo bien para que es cada comando pero creo que rmmod saca el modulo y modprobe lo carga (?)

---

### Post by osensei on 2008-05-21
Probá de hacer lo siguiente:

1) En el archivo /etc/modprobe.d/blacklist agregá la siguiente línea:
```
blacklist bttv
```

2) En el archivo /etc/modules agregá esta línea:
```
bttv card=151
```

Según lo que leí, este último paso ya lo hiciste, pero lo aclaro por las dudas.

Contame cómo te fue.

Saludos!

---

### Post by Applelnx on 2008-05-21
Perfecto, ahi funciono. Gracias a todos :D

---

### Post by faktorqm on 2008-05-21
aammm por que a la blacklist y luego al modules? definitivamente hay algo que no entiendo. Salu2!

---

### Post by Mister X on 2008-05-21
> **faktorqm said:**
> aammm por que a la blacklist y luego al modules? definitivamente hay algo que no entiendo. Salu2!

Los modulos en blacklist evita que los carge al inicio, no quiere decir que despues no los puedas cargar.
Este modulo necesitaba un parametro, al iniciar el sistema lo cargaba sin el parametro, si lo agregaba en modules con el parametro, el modulo ya estaba cargado de por si en el arranque, por lo que no lo cargaba.
Al agregarlo en blaklist, evita que lo carge el sistema autometicamente, pero  despues lo carga "forzado" en modules con el parametro.

Hice un poco de lio con la explicacion, jaja, si se entiende es por casualidad:)

---

### Post by euzkoarima on 2008-05-21
Che, gracias, de esto no sabía nada y me quedo claro.

---

### Post by faktorqm on 2008-05-22
Ahh ok, o sea que es re trucho eso de la blacklist. Yo te entendi, pero es como una lista donde figura todo lo que no queres que arranque al inicio, pero no te impide cargar el modulo luego. Ahora bien, no era mas facil modificar la linea donde se cargaba originalmente y agregarle el parametro? pregunta inmediata: en que archivo figuran los modulos que se cargan en el inicio del sistema y no los del /etc/modules? o son los mismos? pero si fueran los mismos modificandolo deberia cargar con parametros.... :(

---

