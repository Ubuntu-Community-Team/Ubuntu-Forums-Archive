---
title: "virtualizar un sistema operativo ya instalado con virtualbox"
date: 2011-07-09
forum: Software
---

### Post by asterix77 on 2011-07-09
¿Alguien sabe si es posible virtualizar un sistema operativo ya instalado con virtualbox?

He buscado en google pero no he encontrado nada. Lo que pretendo hacer es instalar virtualbox en lucid, y virtualizar windows 7 que ya está instalado.


Desde ya gracias y saludos

---

### Post by gmunioz on 2011-07-09
Si se puede, pero es de riesgo.

Si bien hace muchos años que no uso Windows, recuerdo que en general cuando inicia reescribe la información de configuración de los drivers con respecto al hardware sobre el que corre. 
Esto determina que al iniciar el sistema en Virtualbox la información de los drivers será sobrescrita con las del hardware que simula Virtualbox. 
Si es que piensas utilizar el sistema instalado además de virtualizado como dualboot, deberias hacer un respaldo del perfil de hardware. 

a) Se debe crear una imagen de la partición, ejecutando:

sudo chmod 666 /dev/sdax
Se da permisos de ejecución a la partición

VBoxManage internalcommands createrawvmdk -filename $HOME/.VirtualBox/winxp.vmdk -rawdisk /dev/sdax -relative -register


$HOME/.VirtualBox/winxp.vmdk
Es el directorio y el nombre de la imagen a guardar.

/dev/sdax
Es la partición física del disco a virtualizar.

register
Registra el disco como un disco virtual.

Asi se crea algo similar a un enlace al disco físico, no una copia de este.

b)Crear la maquina virtual, con la opción Usar un disco duro existente y elegir para ello el disco creado.

---

### Post by asterix77 on 2011-07-12
Gracias por tu respuesta gmunioz

La verdad es que me pasaron un notebook en la empresa donde trabajo, después de 5 años de estar en ella. Durante esos 5 años usé un notebook mío el cual tiene ubuntu, y no me resigno a dejar de usar ubuntu por windows, de ahí la pregunta; pero si hay riezgo, creo que lo mejor será que desista, no vaya a ser que estropee el equipo.

Otra alternativa que se me ocurre, es comprar un disco externo e instalar en el ubuntu. Lo complicado es que debo conectarme al dominio de la red a través de windows, y eso significaría bootear cada vez que lo quiera hacer.

Saludos

---

