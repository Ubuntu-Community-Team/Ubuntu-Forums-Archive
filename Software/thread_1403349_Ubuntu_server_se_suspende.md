---
title: "Ubuntu server se suspende"
date: 2010-02-10
forum: Software
---

### Post by santiago79 on 2010-02-10
Hola gente estoy haciendo un gateway con ubuntu server, mi duda es la siguiente cuando estoy trabajando via SSH con desde un windows xp llega a un momento que el putty me beta y ya descubrí porque es, es porque ubuntu server se suspende y apaga el monitor al hacer eso el putty no funciona
alguien sabe como hacer para desabilitar eso?
cual es el proceso que hace que apague el monitor y el me bete del ssh?
YA QUE ESTE UBUNTU VA A TRABAJAR SIN TECLADO NI MOUSE NI MONITOR SOLO VIA SSH.
MUCHAS GRACIAS DE ANTEMANO

---

### Post by guillermolisi on 2010-02-10
> **santiago79 said:**
> Hola gente estoy haciendo un gateway con ubuntu server, mi duda es la siguiente cuando estoy trabajando via SSH con desde un windows xp llega a un momento que el putty me beta y ya descubrí porque es, es porque ubuntu server se suspende y apaga el monitor al hacer eso el putty no funciona
alguien sabe como hacer para desabilitar eso?
cual es el proceso que hace que apague el monitor y el me bete del ssh?
YA QUE ESTE UBUNTU VA A TRABAJAR SIN TECLADO NI MOUSE NI MONITOR SOLO VIA SSH.
MUCHAS GRACIAS DE ANTEMANO
Revisa las opciones de administracion de energia del BIOS y de Ubuntu.
Particularmente las relacionadas con el procesador ya que las referidas al monitor deberian ser inocuas para trabajar vis SSH (los servers que uso trabajan tal como lo planteas vos y nunca tuve ese problema. Uso 8.04 Server)

---

### Post by santiago79 on 2010-02-10
y como reviso las de ubuntu porque no uso tengo entorno grafico en este server

---

### Post by guillermolisi on 2010-02-10
> **santiago79 said:**
> y como reviso las de ubuntu porque no uso tengo entorno grafico en este server
Ah, cierto, entonces lo mas probable es que no tengas gnome-power-manager con lo cual solo deberian actuar las opciones del BIOS. En ningun server tuve que configurar algo de software por este tema, solo revisar las opciones de administracion de energia en el BIOS ya que se supone el server esta pensado para servicio continuo (el ahorro de energia concreto viene por otro lado en estos casos).

---

### Post by santiago79 on 2010-02-10
mira en el setup el ahorro de energía estaba desabilitado yo lo active y le pude todas las opciones desactivado (apagar monitor discos duros etc) y pasa lo mismo

---

### Post by juancarlospaco on 2010-02-10
**noapic nolapic noapm **

agregar parametros del kernel al **/boot/grub/grub.cfg**

---

### Post by alfplayer on 2010-02-10
> **juancarlospaco said:**
> **noapic nolapic noapm **

agregar parametros del kernel al **/boot/grub/grub.cfg**

Con versiones de Ubuntu o Ubuntu Server anteriores a la 9.10 estaría usando la primera versión de grub, el archivo que habría que modificar para agregar esas opciones es menu.lst.

---

### Post by guillermolisi on 2010-02-10
Para usar esas opciones a nivel de Grub tiene que haber algo particular de la motherboard/chipset.

En mi caso ningun server esta usando esas modificaciones (placas Intel, Asus, Abit) con 8.04.

---

### Post by santiago79 on 2010-02-11
aparentemente se soluciono activando el ahorro de energia y desactivando todas las opciones del ahorro solo falta testear bastante tiempo que no pase, por ahora solo se apaga el monitor y no me beta del ssh asi que re bien estoy a la espectativa a ver que pasa, muchas gracias por la ayuda gente

---

### Post by guillermolisi on 2010-02-11
Conta como siguio el tema asi lo marcamos como SOLVED si fue todo bien.

---

