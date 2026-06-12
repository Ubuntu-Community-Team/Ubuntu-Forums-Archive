---
title: "Clonar, Virtualizar, Ghost? Necesita Orientación"
date: 2011-07-28
forum: Software
---

### Post by rgambra on 2011-07-28
Buenas a todos, estoy buscando un poco de orientación ya que ando un poco perdido sobre cual es la solución correcta a la que debo orientarme...

Tengo por un lado un Ubuntu donde he configurado un servidor de un erp, con su base de datos, y le instale varias cosas básicas: ssh, vnc, una rutina de back ups etc... 
Esto es a modo generico. 

¿Cual es mi necesidad? La idea mia es generar un "Servidor Generico" con todo lo que necesito instalado, para no perder tiempo cada vez que tengo que preparar un servidor nuevo. Basicamente todos van a llevar el mismo erp y voy a necesitar los mismos programas.

Lo que quisiera es saber cual es la manera de de copiar este servidor en nuevas maquinas (con distinto hardware).

Las 3 opciones que contemplé son clonar los discos, pero seguramente tenga problemas de hard, lo mismo con un ghost. Virtualizar creo que es la opción más viable, pero me gustaría que me cuenten uds desde su experiencia que han hecho en estos casos. Y si han usado Qemu, vmWare o que.

Gracias!

---

### Post by juancarlospaco on 2011-07-29
Para Clonacion: Clonezilla (es avanzado), Redo Backup Live (es amigable).

---

### Post by biale on 2011-07-29
Solo algunas ideas...

Descartaría a Ghost desde el vamos. Clonezilla era un partimage sofisticado con algo de "dd", me pareció mas predecible seguir con tar. Pero igual era una buena opción.

Los problemas comienzan cuando el hardware es muy diferente. En ese caso la virtualización del HW podría ayudar. Ojo que no tengo experiencia en virtualización de servidores.

---

### Post by rgambra on 2011-08-04
Gracias gente, voy a probar con clonezilla a ver si sale lo que quiero hacer :D

---

