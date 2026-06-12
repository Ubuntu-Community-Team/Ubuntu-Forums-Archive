---
title: "¿Dónde se hospeda Grub?"
date: 2009-07-03
forum: Software
---

### Post by pablocerg on 2009-07-03
Hola a todos, les explico porque quiero saber donde se hospeda grub, tengo una particion C donde esta windows y otra en ext3 para Ubuntu (más otra para mis archivos personales, musica, fotos, etc). Y necesito saber donde esta grub, por si yo formateo la particion donde esta ubuntu voy a tener problemas para iniciar windows despues (sin formatear C) o que tengo que hacer.

Un saludo

---

### Post by sergiom99 on 2009-07-03
hasta donde yo se, que tengo un esquema parecido al tuyo, no pasaria nada, porque el GRUB esta en la primer porcion del disco.
Yo formatee la particion de Ubuntu un par de veces y no paso nada con la de XP ni con el GRUB.
Creo que lo podes corroborar mirando el archivo con el menu de arranque:
```
 $ sudo cat /boot/grub/menu.lst |more
```

Suerte!

---

### Post by juancarlospaco on 2009-07-03
**/boot/grub/**

---

### Post by gmunioz on 2009-07-03
Hola pab...:

Todo disco rígido tiene un sector 0 llamado Master Boot Record (MBR)

Este es el sector de arranque del disco rígido y en él se aloja un

programa encargado de pasar el control, en secuencia de arranque, al 

sector cero de la partición que contiene el sistema operativo 

seleccionado.

Es decir, toda partición primaria o extendida tiene su sector 0, también 

llamado sector de arranque de la partición. En este sector se aloja, a su

vez, un programa encargado de arrancar el sistema operativo instalado en

dicha partición. En ocasiones este programa es una parte o etapa del 

gestor instalado en el MBR.

La ejecución de GRUB está dividida en dos etapas. Cada etapa es una fase

de ejecución de GRUB.

Etapa 1: la BIOS carga el GRUB en memoria, desde el MBR, donde se aloja

la primera y pequeña parte del GRUB.

Etapa 2: se visualiza el menú de GRUB para seleccionar el sistema

operativo a iniciar y carga en memoria el núcleo de dicho sistema. 

A partir de este momento es el núcleo el que se encarga de continuar la 

secuencia de arranque.

En esta etapa el GRUB se utilizan los archivos restantes de él, que 

se alojan en /boot/grub/

En ocasiones, cuando es necesario existe una etapa intermedia (etapa 1.5)

que sirve de puente entre las etapas 1 y 2, el archivo de esta etapa 1.5 

tambien esta alojado en /boot/grub.

---

### Post by pablocerg on 2009-07-03
Muchas gracias por las respuestas, pero entonces si formateo la partición de ubuntu, para iniciar mi otro sistema operativo va a arrancar con grub o va a iniciar automaticamente como antes?

---

### Post by clasificado on 2009-07-04
me parece que vas a tener problemitas

porque /boot/grub está en tu partición de ubuntu

y el grub necesita de esa carpeta para leer el menu.lst y mostrarte las opciones

tengo entendido que el grub está en dos mitades: la del master boot record que es el grub en si mismo, que no es una partición pero tampoco da el funcionamiento completo, y la del /boot/grub que le da la mitad de la configuración.

creo que sin esa carpeta, te deja en la linea de comando de grub para que pongas a mano de donde tiene que bootear, ya que no puede leer las opciones del menu.lst

no es nada que el live cd no te ayude a resolver, ya que podes formatear y volver a poner todo en su lugar teniendo la seguridad que con el livecd tenés una pc funcionando todo el tiempo

es por eso que muchos dejan una partición muy pequeña (algunos megas nomás) como primera partición para el /boot

clasificado

---

### Post by pablocerg on 2009-07-04
Voy a tener que formatear todo entonces, porque no puedo iniciar de LiveCD porque tengo los problemas con el monitor que solo puedo instalar ubuntu con el alternativo

---

### Post by juancarlospaco on 2009-07-04
modo grafico seguro ?
podes hacerlo desde linea de comandos...

---

