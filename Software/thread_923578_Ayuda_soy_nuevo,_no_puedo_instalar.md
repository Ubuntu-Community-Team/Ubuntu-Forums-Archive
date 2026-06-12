---
title: "Ayuda soy nuevo, no puedo instalar"
date: 2008-09-18
forum: Software
---

### Post by franko71ar on 2008-09-18
hola amigos

quiero instalar ubuntu 8.04.1 Server amd64, lo quiero montar sobre  virtual pc 2007 y me tira el siguiente mensaje 

"This kernel requires an x 86-64 CPU, but only detected an i1586CPU. Unable to boot - please use a kernel appropriate for your CPU.

tengo un msi K9N6GM con un AMD Athlon 64 Dual Core 4400 a 2.3 mhz

como puedo solucionarlo

Gracias

---

### Post by lmc.bkp on 2008-09-18
Tu máquina virtual emula un procesador de 32 bits, no de 64. Probá con una iso que tenga un kernel para 32 bits.

---

### Post by franko71ar on 2008-09-19
Gracias Imc.bkp por tu aporte, bajé la misma versión pero para 32 bit y cuando la corro con el virtual después de unos cuantos minutos aparece esto

[145836-130909] isapnp: checksun for device 1 is not valid (0x89)
[145836-139882] isapnp:checksum for device 2 is not valid (0xbe]

Puede ser algun problema del virtual, que otro programa de este tipo puedo usar ?

Gracias

---

### Post by phxnd on 2008-09-22
por que lo usas sobre una maquina virtual? queres seguir teniendo W$ sin ningun cambio?

---

### Post by franko71ar on 2008-09-22
Entonces amigo phxnd no puedo usar una maquina virtual con ubuntu, mi objetivo es poder ver y estudiarlo antes de instalar definitivamente en mi pc
Gracias

---

### Post by VitaLiNux on 2008-09-22
franko71ar,
Una pregunta: tu Virtual PC es compatible con tu procesador? Yo nunca lo he usado, el que si te puedo recomendar es Sun xVM Virtualbox(Googlea eso :popcorn: ), ese si te va a funcionar bien, puedes emular Ubuntu a la perfeccion con ese emulador. O tambien tienes otra alternativa, prueba con Wubi (Googlea eso tambien :popcorn: ), que seguro ya lo tienes incluido en la imagen de disco que te descargaste. El Wubi es para instalar Ubuntu como si fuera un programa de Win$$$
 Saludos y buena suerte!!

P.D.: No te des por vencido!:)
P.P.D.: La solucion mas rapida es con Wubi, no tienes que emular Ubuntu. Para mayor info, busca "Wubi" en Google.

---

### Post by sajnox on 2008-09-22
Es cierto wubi es la forma mas facil de empezar y probar Ubuntu con todas sus funciones.

[http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by zeroadrenaline on 2008-09-22
No se pueden quejar, hace un tiempito vi esto de wubi, y la verdad, cada vez son mas las formas que les da el software libre para que no haya excusas.

---

### Post by leo_rockway on 2008-09-23
> **zeroadrenaline said:**
> No se pueden quejar, hace un tiempito vi esto de wubi, y la verdad, cada vez son mas las formas que les da el software libre para que no haya excusas.

Debian tiene un instalador desde Window$, aunque el sistema no se instala como un programa.

La página [0] tiene un videito que muestra como funciona. La verdad que esto también está piola.

[0] [http://goodbye-microsoft.com/](http://goodbye-microsoft.com/)

---

