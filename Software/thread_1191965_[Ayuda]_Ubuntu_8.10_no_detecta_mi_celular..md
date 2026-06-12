---
title: "[Ayuda] Ubuntu 8.10 no detecta mi celular."
date: 2009-06-19
forum: Software
---

### Post by BootSafe on 2009-06-19
Bueno primero empiezo diciendo hola ... y pidiendo disculpas por si este tema ya fue tratado o esta mal ubicado, (la verdad no entendi mucho este foro jaja[Re animal xD]) 
Bueno paso al problema, la cosa es que tenia ubuntu 8.04 y ayer pase a 8.10, el gran detalle es que no lee la memoria de mi nokia 6131, osea conecto el cable usb y todo, pero no aparece nunca (modo almacenamiento de datos del 6131), encambio si lo pongo en "modo predeteerminado" y abro el Wanmu si lo detecta, pero no me sirve. porque no puedo pasar musica o cosas asi a la memoria.
Alguno tiene la solucion??
desde ayer estoy buscando en google y encontre un par de soluciones pero ninguna me sirvio :( encima vivo pasandole musica al celular, y no tira nada pasarme a winbugs cada vez que quiera un tema.

Saludos y gracias.

---

### Post by josecuervo86 on 2009-06-19
Para tener un poco mas de certeza, conecta el celular y depues en una terminal pone

```
lsusb
```

Y pega el resultado aca

---

### Post by BootSafe on 2009-06-19
Gracias por contestar :)
el resultado que me da la terminal es:
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0c45:612a Microdia PC Camera (SN9C110)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by guillermolisi on 2009-06-20
> **BootSafe said:**
> Gracias por contestar :)
el resultado que me da la terminal es:
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0c45:612a Microdia PC Camera (SN9C110)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Cuando ejecutaste lsusb tenias el celular conectado ?

Solo se ve que reconoce una webcam con chipset microdia.

---

### Post by BootSafe on 2009-06-20
sisi lo tenia conectado :S, y el celular detecto que estaba conectado y lo puse en modo "almacenamiento de datos", y la camara web esta pero en otro puerto usb

---

### Post by rodolfojavier1982 on 2009-06-21
Puede que sea una solucion un poco alejada de lo que buscas, pero te va a servir.
Lo que podes hacer es comprar un adaptador de microSD a USB, te lo deberia leer directamente como cualquier Pendrive, estan como 15 pesos por Mercado L. Es lo que yo hago para pasar cosas a la memoria de la camara digital y del celular. 

Saludos...

---

