---
title: "Diccionario - Ubuntu"
date: 2009-05-02
forum: Software
---

### Post by erdosain9 on 2009-05-02
La aplicación que se encuentra en Oficina (creo que antes estaba en Accesorios) llamada "Diccionario"... nunca me sirvió... es decir busco una palabra en castellano y nada... (ya le cambié a diccionario a castellano en preferencias) y nada al buscar una palabra tilda... luego de un tiempo dice:
"Error al obtener la definición. Falló la búsqueda del host «es.dict.org»: Error desconocido"

y si pongo el diccionario en inglés eso no sucede!!! por qué? qué debo hacer?
Saludos... gracias...

---

### Post by Mauro22 on 2009-05-02
Recien lo probé y funciona bien.


Abrilo desde la consola para ver el error que tira.

---

### Post by sergiom99 on 2009-05-02
empecemos por el principio. tenes conexion a internet?

---

### Post by erdosain9 on 2009-05-02
ey! si! tengo internet...

---

### Post by luks911 on 2009-05-02
Tenía el mismo error. Renombrá o borrá la carpeta /home/tu_usuario/.gnome2/gnome-dictionary
A mí me sirvió.
De todos, modos no encuentra palabras en español, sí en ingles, por ejemplo.

---

### Post by Mauro22 on 2009-05-02
El servidor que tengo yo es:

dict.org

Puerto: 2628

Y funciona en ambos sentidos.

---

### Post by GGsalas on 2009-05-03
> **Mauro22 said:**
> El servidor que tengo yo es:

dict.org

Puerto: 2628

Y funciona en ambos sentidos.

A mi nunca me funcionó. Yo tengo los mismos datos que vos y el error que me da es: 
```
Error al obtener la definición

Falló la búsqueda del host «es.dict.org»: Error desconocido
```

En la consola no aparece ningún error

---

### Post by Mauro22 on 2009-05-03
Hola!!


Hice:

```
mauro@mauro-acer:~$ ping es.dict.org
ping: unknown host es.dict.org
```


despues hice:

```
mauro@mauro-acer:~$ ping dict.org
PING dict.org (216.93.242.2) 56(84) bytes of data.
64 bytes from miranda.org (216.93.242.2): icmp_seq=1 ttl=49 time=197 ms
64 bytes from miranda.org (216.93.242.2): icmp_seq=2 ttl=49 time=201 ms
64 bytes from miranda.org (216.93.242.2): icmp_seq=3 ttl=49 time=194 ms
64 bytes from miranda.org (216.93.242.2): icmp_seq=4 ttl=49 time=200 ms
64 bytes from miranda.org (216.93.242.2): icmp_seq=5 ttl=49 time=207 ms
64 bytes from miranda.org (216.93.242.2): icmp_seq=6 ttl=49 time=210 ms
^C
--- dict.org ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5504ms
rtt min/avg/max/mdev = 194.795/201.905/210.140/5.297 ms

```

Ese si contesta, es mas contesta miranda.org, es mas si vas a [http://dict.org](http://dict.org) te abre la pagina del diccionario.

Cambiar es.dict.org por el ip 216.93.242.2 a ver que onda!

---

### Post by Hei Ku on 2009-05-03
Por casualidad no tenes un firewall que tenga filtrada la salida de paquetes, no?

---

### Post by GGsalas on 2009-05-03
> **Hei Ku said:**
> Por casualidad no tenes un firewall que tenga filtrada la salida de paquetes, no?

Por mi parte, nunca instalé un firewall. Creo que Ubuntu 8.10 no trae ninguno activado.

---

### Post by Mauro22 on 2009-05-03
Todo kernel trae iptables pero sin configurar demaciado, si concientemente no tocaste nada, deberia andar jeje...

Probaste con la ip? o por lo menos si podes entrar a la web?

---

### Post by GGsalas on 2009-05-03
Si! :D
Cambié dict.org por el ip 216.93.242.2 y funciona como traductor.

Ya que estoy pregunto: ¿Cómo puedo poner un diccionario en español, por ejemplo el de le RAE (real academia española)?

---

### Post by juanmatias on 2010-05-13
Al parecer los diccionarios en español en internet no funcionan muy  bien que digamos.
 

Encontré un proyecto que pone a disposición un diccionario en  español, empaquetado en DEB, para que corra como servidor local... no es  lo más completo, pero creo que está bueno para el uso diario.
 

El paquete está en [http://sourceforge.net/projects/dict-es/](http://sourceforge.net/projects/dict-es/)
 

Y para instalarlo, en el diccionario hacés:
 

En Editar » Preferencias. Pulsar en Añadir, cubrir los datos como  sigue:
       Descripción: Diccionario local (o lo que quieras)
       Transporte: Servidor de diccionario
       Servidor: 127,0,0,1
       Puerto: 2628

---

### Post by alfplayer on 2010-05-14
Se puede usar Lemurae que es un programa para acceder al diccionario de la RAE. No hay paquete para 10.04 pero se puede instalar el de 9.10 y después instalar las dependencias no instaladas con "*apt-get -f install*".

---

