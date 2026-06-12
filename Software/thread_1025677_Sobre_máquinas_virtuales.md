---
title: "Sobre máquinas virtuales"
date: 2008-12-30
forum: Software
---

### Post by Josecanalla on 2008-12-30
Hola, monté una máquina virtual con el VirtualBox, y quisiera saber si podés agarrarte un virus usando Windows virtual.

---

### Post by rodolfojavier1982 on 2008-12-30
Y como que poder podés, obviamente el Virus te va a afectar a tu Windows ahora 
Windows Virtual+With Virus Edition, pero no te va a afectar el Linux, ya que no esta hecho para Linux.
No te asustes, a lo sumo deberas eliminar la imagen de Windows y crearte una nueva...

---

### Post by Mister X on 2008-12-30
solo un virus virtual:-\"

---

### Post by sebastianabate on 2008-12-30
> **rodolfojavier1982 said:**
> Y como que poder podés, obviamente el Virus te va a afectar a tu Windows ahora 
Windows Virtual+With Virus Edition, pero no te va a afectar el Linux, ya que no esta hecho para Linux.
No te asustes, a lo sumo deberas eliminar la imagen de Windows y crearte una nueva...

Bueno, en realidad no es tan simple la cosa, porque si bien tenés razón en que una máquina virtual no puede afectar al host de forma directa, sí lo puede hacer si esta máquina virtual tiene acceso a los archivos del host, como por ejemplo a través de las "shared folders" que ofrece Virtual Box, o si en tu host Linux tenés configurado SAMBA para compartir archivos con el guest Windows, y este tiene mapeada alguna unidad por cualquiera de estos medios. En este escenario el virus del guest podría borrar archivos que están en el host por estos medios.

Es por esto que yo nunca habilito a un guest Windows para que pueda escribir en alguna carpeta compartida del host; únicamente las configuro en modo solo lectura y listo.

Para resumir, una máquina virtual tiene que manejarse como una máquina real; si está aislada completamente del resto de tus máquinas (reales o virtuales), podés quedarte tranquilo, pero si está en red de alguna forma con alguna otra máquina y no tenés antivirus, sos carne de cañón.

Por lo menos esa es mi visión.

---

### Post by Josecanalla on 2009-01-02
Ajá, ahí vamos entendiendo. Yo la máquina virtual la tengo solamente para utilizar diversos programas que no hubo forma de correr en Linux. Entonces a lo mejor ni siquiera le habilito la conexión de red a internety listo.

---

### Post by z37a on 2009-01-04
> **Josecanalla said:**
> Ajá, ahí vamos entendiendo. Yo la máquina virtual la tengo solamente para utilizar diversos programas que no hubo forma de correr en Linux. Entonces a lo mejor ni siquiera le habilito la conexión de red a internety listo.

Exactamente, o sea la maquina virtual no es mas que nada que OTRA pc, podes hasta instalarle un virus a propósito para ver como afecta a un windows, que a tu sistema principal no le va a pasar nada, ya que es otro.

---

