---
title: "Virtual Box 2 y la red"
date: 2008-11-15
forum: Software
---

### Post by z37a on 2008-11-15
Gente, una consulta, estoy usando VirtualBox2, si lo se no es libre, pero es gratis y anda bien!!!, pero tengo un problema, logre configurar el bridge mal, siguiendo varias guías, mi problema esta en que funciona todo bien pro ~36 horas, luego la red palma y no tengo acceso a internet, si a la red(lo mas raro) desde mi pc, tiro un network restart y listo red de nuevo, peor se vuelve muy molesto. Me podrían recomendar alguna guía en donde sepan que funcione si o si el VBox con red en bridge?

PD: Uso Hardy de 64 en una pc e Intrepid de 32 en la laptop(que todavía no le configure nada del VBox)

---

### Post by c4d0rn4 on 2008-11-15
se que tal vez no es la mejor respuesta, pero si todo anda bien, por qué no le configura un cron? y que cada x tiempo haga el trabajo sucio por ti.

edit: o era anacron el que era por tiempo ? ... mmmm

---

### Post by z37a on 2008-11-16
> **c4d0rn4 said:**
> se que tal vez no es la mejor respuesta, pero si todo anda bien, por qué no le configura un cron? y que cada x tiempo haga el trabajo sucio por ti.

edit: o era anacron el que era por tiempo ? ... mmmm

Seria una solución, peor en realidad quiero tener un uptime mayor de la red, o sea no quiero que me falle la red. Pero igual no había pensado esa y es una buena opción para evitar la intercaccion con el usuario

---

### Post by guillermolisi on 2008-11-17
No se si entiendo bien el problema.

Tenes un host que corre una VM con Vbox 2 en modo bridge, cierto ?.

Las dos se quedan sin acceso a Internet o solo la VM ?
Que estas corriendo en el host y que en la VM ?
Podes mostrar como estan configuradas las placas de red de cada maquina ?
Que tipo de conexion a Internet estas usando ?

---

### Post by ariel on 2008-11-17
> **z37a said:**
> Gente, una consulta, estoy usando VirtualBox2, si lo se no es libre, pero es gratis y anda bien!!!, pero tengo un problema, logre configurar el bridge mal, siguiendo varias guías, mi problema esta en que funciona todo bien pro ~36 horas, luego la red palma y no tengo acceso a internet, si a la red(lo mas raro) desde mi pc, tiro un network restart y listo red de nuevo, peor se vuelve muy molesto. Me podrían recomendar alguna guía en donde sepan que funcione si o si el VBox con red en bridge?

PD: Uso Hardy de 64 en una pc e Intrepid de 32 en la laptop(que todavía no le configure nada del VBox)

Yo uso bridge & host-based NAT con virtualbox. Esto es lo que uso, capaz que te sirve para darte una idea:

```

    - Host Interface Networking (workaround to VBox's buggy NAT implementation)
        - Edit /etc/network/interfaces and add the following - follow instructions
        # vbox host interface networks
        #   run once: sudo apt-get install uml-utilities  #this is required for tunctl
        #             needs: echo 1 > /proc/sys/net/ipv4/ip_forward
        #             (persistently: editing the /etc/sysctl.conf; and uncomment: net.ipv4.ip_forward = 1)
        #             needs: change TUN device permissions (see note)
        #             do *not* do: sudo VBoxAddIF vbox0 <user> (has problems bringing up the ip config of vbox0; I use tunctl instead)
        # config in the virtual machine settings:
        #   settings > network > 
        #      Adapter type: Intel Pro 1000/MT desktop (if using the intel driver)
        #      Attached to: Host Interface
        #      Host interface settings / Interface name: vbox0
        # config in guest:
        #   static ip address: 172.16.254.2, def gw: 172.16.254.1; DNS: manually set to same as host dns
        #   remember to disable netbios over tcp
        # to reload config: /etc/init.d/networking restart
        # in the below, customize: -u username (e.g. ariel); -o interface-name (e.g. ath0)
        auto vbox0
        iface vbox0 inet static
             address 172.16.254.1
             netmask 255.255.255.0
             pre-up /usr/sbin/tunctl -u ariel -t vbox0 >/dev/null
             up iptables -t nat -A POSTROUTING -o ath0 -j MASQUERADE
             down iptables -t nat -D POSTROUTING -o ath0 -j MASQUERADE
             post-down /usr/sbin/tunctl -d vbox0 >/dev/null
    - TUN device permissions
      - to change it for the current session only: sudo sudo chmod 0666 /dev/net/tun
      - permanent change: edit /etc/udev/rules.d/60-vboxdrv.rules
      - add the line:
        - KERNEL=="tun", OWNER="root", GROUP="vboxusers", MODE="0660"


```

---

### Post by Applelnx on 2008-11-18
Pregunta fuera de tema que me surgio cuando leia el 1er post:

Libre = cualquiera lo puede modificar
Gratis = que no te cobran ????????????

Saludos

---

### Post by sajnox on 2008-11-18
> **Applelnx said:**
> Pregunta fuera de tema que me surgio cuando leia el 1er post:

Libre = cualquiera lo puede modificar
Gratis = que no te cobran ????????????

Saludos

Basicamente si,

Pero tenes que tener en cuenta que la libertad se divide en cuatro categorias, te dejo un link [0] con mas informacion

Ejemplos de programas gratuitos y cerrados son: Opera, flash, y seguro que viene Leo y nos da una lista un poco mas larga

(0) [http://www.gnu.org/philosophy/free-sw.es.html](http://www.gnu.org/philosophy/free-sw.es.html)

---

### Post by z37a on 2008-11-20
> **guillermolisi said:**
> No se si entiendo bien el problema.

Tenes un host que corre una VM con Vbox 2 en modo bridge, cierto ?.

Las dos se quedan sin acceso a Internet o solo la VM ?
Que estas corriendo en el host y que en la VM ?
Podes mostrar como estan configuradas las placas de red de cada maquina ?
Que tipo de conexion a Internet estas usando ?

Ambas sin internet, la física y la virtual que corra adentro, lo raro es que si tiro un ping o accedo a una pc de la red entro, es como si se perdiera la puerta de enlace, peor si tiro ping a esta me responde, es como si no la usara, tiro un restart al servicio de red y listo andando!

Aca les dejo una copia de mi interfaces:

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
#address 192.168.2.2
#netmask 255.255.255.0
#gateway 192.168.2.1

auto tap0
iface tap0 inet manual
up ifconfig $IFACE 0.0.0.0 up
down ifconfig $IFACE down
tunctl_user z37a

#auto tap1
#iface tap1 inet manual
#up ifconfig $IFACE 0.0.0.0 up
#down ifconfig $IFACE down
#tunctl_user usuario

auto br0
iface br0 inet static
address 192.168.2.2
netmask 255.255.255.0
gateway 192.168.2.1
bridge_ports all tap0
```

Lo que me gustaría saber es si alguno tiene una guía paso a paso para configurar el modo bridge que hallan testeado y funcione bien. En unos días esa pc se formatea, pero no pro que no quiera corregir ni nada si no pro que reemplazo los hdds por 1 solo(je voy a usar mis 2 hdds actuales para armarme un file server, p2p server, etc.. hogareño con ubuntu server jejeje)

---

