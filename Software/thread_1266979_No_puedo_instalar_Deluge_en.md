---
title: "No puedo instalar Deluge en"
date: 2009-09-15
forum: Software
---

### Post by te veo on 2009-09-15
Hola amigos, me llamo Martin y estoy teniendo mis primeras experiencia en Ubuntu.

El mes pasado borre todos los repositorios predeterminados por obviamente ser un Newbie en Ubuntu y no hubo forma de restaurarlos asi que empece a agregarlos manualmente.

Asi llego a la instalacion de la ultima version de Deluge, no he podido encontrar ningun repositorio de Python y cuando doy a instalar deluge-core en Synaptic me salta la siguiente dependencia insastifecha:

[IMG]http://i28.tinypic.com/2q3vn2s.jpg[/IMG]

Como no tengo repositorios de Python instalados no puedo resolver esa dependencia. 

Puede parecer una pelotudez esto pero soy un total newbie en ubuntu-linux.




Tengo esta distro

Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.1
Release:	8.04
Codename:	hardy



Un saludo ):P

---

### Post by euzkoarima on 2009-09-15
Me parece que el problema viene de lo que comentás, que borrastes los repositorios y los volviste a agregar a mano. Ahí debió quedar algo mal.

Por lo pronto te diría que abras una consola (Aplicaciones -> Accesorios -> Terminal), ejecutes este comando
```
cat /etc/apt/sources.list
```
y copies aca la salida.

Saludos,
Eduardo

---

