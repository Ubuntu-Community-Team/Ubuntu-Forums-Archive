---
title: "Ayuda! Automatizar iptables"
date: 2009-06-26
forum: Software
---

### Post by Spity on 2009-06-26
Hola!
Cada vez que inicio mi Ubuntu tengo que abrir una consola y como root tipear lo siguiente para poder compartir mi conexion con las PCs de mi casa (que tienen winxp).

echo 1 > /proc/sys/net/ipv4/ip_forward 
 
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE

iptables -t nat -A POSTROUTING -o eth2 -j MASQUERADE

La pregunta es si hay alguna manera de hacerlo automaticamente?

---

### Post by Mauro22 on 2009-06-26
Podes hacer un script pero te va a pedir la contraseña de root...


Hace falta ser root para modificar iptables?


EDIT: Porque no quedan guardados esos puertos? es raro que los tengas que hacer cada vez que inicias.

---

### Post by gmunioz on 2009-06-26
Hola spi.....:

1- Creas un archivo de texto, con un título para ser

originales, autoiptables

2- Pones en su interior estas líneas

```
#!/bin/sh

# Script para automatizar iptables

echo 1 > /proc/sys/net/ipv4/ip_forward

iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE

iptables -t nat -A POSTROUTING -o eth2 -j MASQUERADE

```
3- Lo guardas. 


4- Lo copias a /etc/init.d/, ejecutando en consola

```
sudo cp autoiptables /etc/init.d/autoiptables
```

5- Le das permisos de ejecución, ejecutando en consola

```
sudo chmod +x /etc/init.d/autoiptables
```

6- Creas los enlaces para su ejecución en el inicio del sistema:

```
sudo ln -s /etc/init.d/autoiptables /etc/rc2.d/S99autoiptables

sudo ln -s /etc/init.d/autoiptables /etc/rc3.d/S99autoiptables

sudo ln -s /etc/init.d/autoiptables /etc/rc4.d/S99autoiptables

sudo ln -s /etc/init.d/autoiptables /etc/rc5.d/S99autoiptables

```

7- Reinicias y tendrían que estar funcionando tus configuraciones.

---

### Post by Spity on 2009-06-26
Muchas gracias. Es justo lo que estaba buscando. :)

---

