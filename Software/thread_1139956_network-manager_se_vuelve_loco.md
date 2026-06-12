---
title: "network-manager se vuelve loco"
date: 2009-04-27
forum: Software
---

### Post by Brath-ga on 2009-04-27
Hola a todos.

Después de instalar la 9.04 desde 0 en 2 ordenadores sin problemas, el tercero se me resiste.

El problema es que tiene una conexión directa por cable y cada vez que arranca me indica un ath diferente, es decir si está en ath1 en la siguiente aparece ath2 y así consecutivamente.

Tengo editado el /etc/network/interfaces para que arranque desde ath0. ero no soluciono el problema.

Como podría obligarlo a que no busque más conexiones ?

---

### Post by Apipote on 2009-04-27
Network manager a mi me resulta inestable desde Hardy. 
Es un misterio que luego de actualizar desaparece de la barra de tareas, y no funciona. Y sigue en Jaunty
He leido en launchpad a varios que se quejan de lo mismo.

Probá wicd que está en los repositorios. A mi me resulta mucho mejor.

Slds

---

### Post by Brath-ga on 2009-04-27
Pero wicd no es para redes inalambricas solo?

Yo necesito para redes almbricas.

Corigeme si me equivoco.

---

### Post by rubioo on 2009-04-27
Hola brath, wicd funciona también para redes cableadas.
 Para instalarlo, si estas usando Jaunty
 
 ```

 sudo aptitude install wicd
 
```

 Si usas intrepid tenes que agregar el repositorio

 ```

 deb http://apt.wicd.net  intrepid  extras
 
```

 Y por ultimo

 ```

 wget -q http://apt.wicd.net/wicd.gpg -O- | sudo apt-key add -
 
```

 Y a instalar.

  
  Saludos

---

### Post by staar on 2009-04-27
> **rubioo said:**
> Hola brath, wicd funciona también para redes cableadas.
 Para instalarlo, si estas usando Jaunty
 
 ```

 sudo aptitude install wicd
 
```

 Si usas intrepid tenes que agregar el repositorio

 ```

 deb http://apt.wicd.net  intrepid  extras
 
```

 Y por ultimo

 ```

 wget -q http://apt.wicd.net/wicd.gpg -O- | sudo apt-key add -
 
```

 Y a instalar.

  
  Saludos

OJO, que hay que desinstalar network-manager antes de instalar wicd!!...

otra cosa, network-manager necesita, según me acuerdo, que el archivo /etc/interfaces esté limpio, después lo gestiona él mismo...

y si, nm es de los programas con mas bugs en ubuntu :-P :-D...

saludos

---

### Post by Brath-ga on 2009-05-05
Por lo visto parece que el problema viene de que el la 9.04 no me reconoce bien la tarjeta de red (propia de la placa. Es una Geforce), entonces nunca encuentra la eth0 y cada vez que reinicio no me da conectado porque tiene activa ethn+1.

---

### Post by Hei Ku on 2009-05-05
Podes postear el resultado de lspci para la placa Ethernet?
Lo que hay que hacer es agregar una regla para que no te tome la placa como una distinta cada vez.

---

### Post by Brath-ga on 2009-05-06
El resultado de lspci es este.

xoan@xoan-lmeh:~$ lspci | grep Ethernet
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)

---

### Post by Brath-ga on 2009-05-08
Estuve investigando un poco y el caso es que cada vez que reinicio se me modifica el fichero /etc/udev/rules.d/70-persistent-net.rules añadiendo una linea a mayores con la eth aumentada en 1 unidad.
Como puedo fijarla ?

---

### Post by Hei Ku on 2009-05-08
Poné esto, a ver qué tira:
```

lsmod | grep eth

```

Despues, vas a tener que modificar el archivo /etc/udev/rules.d/70-persistent-net.rules, sacando las lineas que tiene y poniendo:

```

SUBSYSTEM=="net", DRIVERS=="<nombre del driver>", NAME="eth0" 

```

donde nombre del driver es el modulo que te tiró en el comando anterior.

---

### Post by Brath-ga on 2009-05-12
```
xoan@xoan-lmeh:~$ lsmod | grep eth
forcedeth              61712  0 

```

¿ Como sería el apartado DRIVERS=="6712"  ?

Te pego parte del 70-persistent-net.rules que me aparece ahora

Fíjate como cambia ATTR{address}

```
PCI device 0x10de:0x03ef (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:00:6c:15:49:ee", ATTR{type}=="1", KERNEL=="eth*", NAME="e$

# PCI device 0x10de:0x03ef (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:00:6c:88:be:91", ATTR{type}=="1", KERNEL=="eth*", NAME="e$

# PCI device 0x10de:0x03ef (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:00:6c:d8:40:81", ATTR{type}=="1", KERNEL=="eth*", NAME="e$


```

---

### Post by Hei Ku on 2009-05-12
en drivers tenes que poner forcedeth, como la hw address te cambia cada vez, entonces la rule deberia quedarte asi.

```

SUBSYSTEM=="net", DRIVERS=="forcedeth", NAME="eth0"

```

---

### Post by Brath-ga on 2009-05-12
Gracias Hei-Ku

Funciona estupendamente.

---

### Post by juancarlospaco on 2009-05-12
[Wicd]("apt:/wicd")

*Que queres con esa cosa hecha por Red Hat, es muy caprichosa a veces...* :(

---

### Post by Brath-ga on 2009-05-13
Seguí vuestras indicaciones e instalé el wicd, pero el problema persistía. La solución definitiva vino dada por Hei-ku.

Ahora funciona perfectamente. aunque perdí el icono de conexión en la parte alta del panel. Pero funciona.

---

