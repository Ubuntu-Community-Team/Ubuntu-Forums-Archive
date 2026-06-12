---
title: "Problemas instalando XP"
date: 2008-09-12
forum: Software
---

### Post by SLA_leandrin on 2008-09-12
Hola a todos.

La situación es la siguiente; 

- Tengo que instalar (no quiero, tengo) winchorg Xp en mi notebook porque lamentablemente no puedo correr ciertos programas específicos en Ubuntu. 

- Mi notebook está actualmente usando SOLO Ubuntu 8.04, y el disco está particionado de la siguiente manera; 
   
    * /dev/sda1 montado en /home con sistema de archivos ext3 (80.64 Gib)
    * /dev/sda2 monetado en / sist. ext3 con 10.28 Gib
    * /dev/sda3 de 20.87, en fat32 ---> destinado a Windows.

    * Tenía una partición SWAP pero la eliminé porque el instalado de XP me decía que tenía "muchas" particiones :lolflag: y no me dejaba seguir el proceso.

- Cuando booteo con el CD del XP, arranca la famosa pantalla azul, le pido que me lo instale en la partición /dev/sda3 (Que el instalador reconoce como la partición C) y copia los archivos como para bootear y todo bien hasta ahí.

- Al reiniciar la máquina no arranca nada, me dice directamente "DISK ERROR" y no anda ni para atrás ni adelante. Sólo me queda entonces bootear con el live CD de ubuntu para reinstalar el Grub. 

- Este proceso ha sido probado con dos CDs diferentes del XP así que descarto que sea ese el problema... 

Alguno tiene para tirarme una punta???

Gracias!!

---

### Post by zeroadrenaline on 2008-09-12
Mira, si te metes en gedit, edita los flags, y ponele boot a la particion 3.
Por otro lado, yo no hubiera sacado el swap, leete algo de particiones extendidas, la idea es que podes tener Swap, Lin Win, y dentro de una particon extendida agregar la particion de tu Home, y una para datos de win si queres tener tus datos win mas asegurados.
Insisto leete algo sobre particiones extendidas, esa es la solucion a la cantidad de particiones.
Tene en cuenta que probablemente cuando instales win, te borre grub del mbr, con lo que tendrias que reinstalarlo desde live cd, quisas ese sea el motivo de tu problema, que el mbr esta descajetado.
Busca en google, yo encontre esto, no se si es exactamente lo que nececitas, pero te puede dar una idea, [http://grupos.pucp.edu.pe/archivos/linux/linux.200508/0013.html](http://grupos.pucp.edu.pe/archivos/linux/linux.200508/0013.html)
El problema esta en el mbr creo yo!.
Reinstalate un grub con el live cd de lin, y fijate que onda.
Siempre es mejor instalar Ubuntu sobre win, quew Win sobre Lin, win parece que tiene una politica invasiva, es decir, llego y me quedo con todo, no es amigable con los nativos, Como los antiguos colonizadores, que actitud mas arcaica no creen?.

---

