---
title: "compartir internet sin ruoter y sin firestarter"
date: 2009-05-29
forum: Software
---

### Post by granjero on 2009-05-29
buenas... ya hice todo lo que pude con mi problema, me gustaría saber que opinan...

tengo dos pcs.

**pcjm** con ubuntu 8.04 Mi pc de cabecera.
AMD athlon 64 X 2 5200
2gb ram
360gb HD
nvidia 8600gt
2 placas de red:
 eth0: configuracion automática de DHCP
 eth2: ip fija: ip:10.0.0.1
                mascara: 255.0.0.0
 

**pcvieja** ahora tiene ubuntu 9.04 pero tenia xubuntu 8.04 es con la que me divierto experimentando.
AMD duron 1300 
512mb ram
20gb con el SO
80gb con un bakup de musica y fotos y peliculas
eth0: 10.0.0.2
mascara: 255.0.0.0

la cuestión es que están conectadas con un cable de red cruzado. 
lo que quiero es que pcvieja pueda tener internet para instalarle software para ver las pcs del laburo podrían funcionar con ubuntu.

probé de todo. active el ufw y le di el comando para que todo el trafico de 10.0.0.2 pase por el puerto 80 y el 22 y no anduvo.

trate con esto que me lo dijo un muchacho español en el chat de freenode

```

modprobe iptable_nat 
iptables -t nat -A POSTROUTING -s 10.0.0.2 -o eth0 -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/ip_forward
```

esto fue lo que hizo que con xubuntu ande internet en pcvieja

tambien segui este tutorial [https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)

no quiero comprar un switcher ni un router porque no quiero ni un enchufe mas y ademas con xubuntu despues de lo que me dijo el chico español tuve internet, pero cuando acualice a ubuntu 9.04 se acabo la internet.


gracias de antemano

---

### Post by juancarlospaco on 2009-05-30
pcvieja ubuntu 9.04 
AMD duron 1300
512mb ram
20gb con el SO
80gb con un bakup de musica y fotos y peliculas
eth0: 10.0.0.2
mascara: 255.0.0.0
Default Gateway: 10.0.0.1
DNS: DNS de Arnet aqui*(o algun otro de internet)*

---

### Post by NickCis on 2009-05-30
Usa esta guia: [http://ubuntuforums.org/showthread.php?p=6060607#post6060607](http://ubuntuforums.org/showthread.php?p=6060607#post6060607)

Esta en ingles, pero se entiende perfectamente.

Saludos.

---

### Post by guillermolisi on 2009-05-30
> **granjero said:**
> 
```

modprobe iptable_nat 
iptables -t nat -A POSTROUTING -s 10.0.0.2 -o eth0 -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/ip_forward
```esto fue lo que hizo que con xubuntu ande internet en pcvieja

tambien segui este tutorial [https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)

no quiero comprar un switcher ni un router porque no quiero ni un enchufe mas y ademas con xubuntu despues de lo que me dijo el chico español tuve internet, pero cuando acualice a ubuntu 9.04 se acabo la internet.


gracias de antemano
Despues de la actualizacion, repetiste ese scripting para iptables ?

---

### Post by granjero on 2009-05-31
si guillermo, lo repetí, lo que pasa ahora es que la internet funciona a veces si y a veces no...

me resulta rarísimo...

y no se por que es...

salud!

---

### Post by guillermolisi on 2009-05-31
> **granjero said:**
> si guillermo, lo repetí, lo que pasa ahora es que la internet funciona a veces si y a veces no...

me resulta rarísimo...

y no se por que es...

salud!
Disculpa la pregunta pero cuando decis que la conexion a Internet a veces funciona y a veces no te referis a ambas maquinas o solo a la que esta en red via el cable cruzado ?

Si funciona en las dos PCs en forma irregular el problema esta fuera de las maquinas, esta entre la PC con las dos placas e Internet (supongo que no debe ser esto ultimo ya que antes decis que andaba estable).

Hay algo mas que hayas hecho y no recordas ?

Si haces un tracert (traceroute) a una IP publica, por ejemplo los DNS o Google, que te muestra ?

---

### Post by granjero on 2009-06-03
guillermo, lo que pasa es que la máquina conectada con el cable cruzado (pcvieja) es la que tiene a veces si y a vece no internet.

lo que me dí cuenta es que para que le ande internet tengo que ejecutar siempre estas líneas. en la pc que funcionaria a la manera de server...

```
modprobe iptable_nat 
iptables -t nat -A POSTROUTING -s 10.0.0.2 -o eth0 -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/ip_forward
```

para que eso ande siempre las tengo que agregar en el rc.local?

gracias...

---

### Post by fmsismo on 2009-06-03
Podes agregarlo en el rc.local, así cada vez que prendes el servidor o lo reinicias esas instrucciones son ejecutadas.

---

### Post by staar on 2009-06-03
fijate esto [http://www.tutoriales-ubuntu.com/archives/restaurar-las-iptables-en-ubuntu-automaticamente]("http://www.tutoriales-ubuntu.com/archives/restaurar-las-iptables-en-ubuntu-automaticamente")

saludos

---

### Post by granjero on 2009-06-04
muchas gracias gente!

---

