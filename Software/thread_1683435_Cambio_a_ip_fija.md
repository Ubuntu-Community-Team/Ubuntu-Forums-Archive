---
title: "Cambio a ip fija"
date: 2011-02-07
forum: Software
---

### Post by c3959 on 2011-02-07
gente:
necesito cambiar una red a una ip fija, pero no logro que esto pase... el gestor de red no lo soluciona. espero sus repuestas


saludos!"

---

### Post by Elkan76 on 2011-02-07
Hola,
Pues bien, respecto a este problema no das mucha información.
Si tu equipo es cliente de la red, este no resuelve solo su IP, el que realiza la asignación, es el router (por lo común), por lo tanto, es este equipo al que se debe deshabilitar DHCP.
Saludos.

---

### Post by magicdrums on 2011-02-07
Puedes porfavor mostar tu ifconfig y el archivo interface?

> $cat /etc/network/interfaces

---

### Post by c3959 on 2011-02-11
les cuento... tengo un dlink dir-600, que permite en modo dhcp intervalos de ips de 99-199, osea puedo ponerles a pcs ipc fijas desde 2 a 98, por lo cual tengo el interfaces del pc de la siguiente forma:

auto eth0
iface eth0 inet sstatic
address 192.168.0.22
netmask 255.255.255.0
gateway 192.168.0.2

auto lo
iface lo inet loopback


creo que algo me falta en la configuracion de eth0... pero no entiendo que es lo que está faltando o que esta mal usado


espero sus respuestas

saludos!"

---

### Post by c3959 on 2011-02-11
lo solucione al tratar de entrar en la configuracion del router... error torpe =P
resulta que cambie la ip del router en algun momento (ni idea cuando) por 192.168.0.9... entonces mi gateway estaba mala, la reemplaze por la del router y ya está corriendo todo, pense que era error de la ip pero no era error de mi router


gracias por su respuesta y sorry por el doble post


saludos!"

---

