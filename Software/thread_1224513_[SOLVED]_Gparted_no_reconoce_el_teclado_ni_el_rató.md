---
title: "[SOLVED] Gparted no reconoce el teclado ni el ratón"
date: 2009-07-27
forum: Software
---

### Post by prostata on 2009-07-27
Usando en otro equipo WXP quiero particionar para instalar Ubuntu, siempre he usado para esos menesteres el Gparted sin problema alguno, pero en ese otro equipo cuando aparece la pantalla de gparted este no me rreconoce ni el ratón ni el teclado con lo cual me inhabilita la operación....qué puedo hacer me estoy volviendo loco, llevo todo el día sin éxito...

Saludos


WXP
AMD 1600MH
RAM 1Gb
Nvidia 120 Mb
Teclado y ratón normalitos...normalitos

---

### Post by Mauro22 on 2009-07-27
Usas el Gparted como??


El livecd de gparted propiamente dicho

o 

El gparted que viene dentro del LiveCD de ubuntu?

---

### Post by prostata on 2009-07-28
> **Mauro22 said:**
> Usas el Gparted como??


El livecd de gparted propiamente dicho

o 

El gparted que viene dentro del LiveCD de ubuntu?

Uso el gparted-live-0.4.5-5.iso y finalmente está solucionado mi esposa ya va con Ubuntu....pero..siempre un pero...ahora cuando el Grub se inicia de forma que pueda seleccionar con qué SO quiere trabajar el teclado sigue sin estar operativo de forma que obligatoriamente arranca Ubuntu. Una vez dentro de Ubuntu tanto el teclado como el ratón si son perfectamente operativos...qué puedo hacer..??

Gracias

---

### Post by Mauro22 on 2009-07-28
Lo unico que se me ocurren es que sea teclado USB o Inalambrico... cualquiera de los 2, el grub no lo toma.

---

### Post by prostata on 2009-07-28
Pues en mi ordenador el teclado es USB y funciona correctamente, de modo que.....:(

Saludos

---

### Post by alfplayer on 2009-07-28
Hay hardware que no tiene soporte, pero en muchos casos (especialmente con hardware moderno) debería funcionar bien con teclados inalámbricos y USB.

---

### Post by Mauro22 on 2009-07-28
Pero durante el booteo no hay drivers USB... por eso no anda la seleccion, mientras que cuando carga el SO, sí!

---

### Post by prostata on 2009-07-28
Perdón me precipité, el teclado de mi ordenador no es USB, es el conector de forma cilíndrica tradicional, de esos pequeñitos con varios "pins", (conectores??) de hace ya unos cuantos años no es tampoco un RS2...el de mi esposa si es USB, aunque le he puesto un acople como el mío de salida USB a entrada al "acople" y tampoco funciona luego de reseteda la máquina...

saludos

---

### Post by alfplayer on 2009-07-28
Por la descripción puede ser PS/2, antes estaban los de puerto serie RS-232.

---

### Post by prostata on 2009-07-28
> **alfplayer said:**
> Por la descripción puede ser PS/2, antes estaban los de puerto serie RS-232.


Cierto es un PS/2, de tanto intento se me bloquea la mente, si es un PS/2, pero ni así funciona..

---

### Post by alfplayer on 2009-07-28
Algo que se me ocurre intentar (aunque es difícil que funcione) es seguir probando si las teclas responden al final del tiempo de espera del menú de grub (30 segundos?), por si por alguna razón hay algo que tarda mucho en iniciarse.

Algunos datos que pueden ser importantes es si funciona cuando inicia la pc (por ejemplo en la configuración del bios), y si funciona un teclado USB conectado directamente sin adaptador.

Puede ser un problema del bios, que se solucione actualizando el bios.

---

### Post by prostata on 2009-07-29
Pues efectivamente Todo se debía al teclado USB después de mil pruebas y de poner mi teclado en la máquina de mi esposa y ver que funcionaba a la primera el Grub me fuí a la tienda de abajo y por 4.5 Euros compre un teclado genuino PS/2 y todo funciona de lujo, así que muchas gracias a todos por vuestros aportes...

Saludos

---

