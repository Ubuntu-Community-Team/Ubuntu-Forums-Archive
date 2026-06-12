---
title: "VNC en ubuntu"
date: 2008-06-26
forum: Software
---

### Post by Simbiosys on 2008-06-26
Buenas!! tengo ubuntu 8.04 y el asunto es que el cliente de terminal server, cuando eligo el protoloco. VNC.. no me lo permite como en la version 7.10, ya que aparece como GRISADO... (ver adjunto 1)

por otro lado, encontre la herramienta "Visor de escritorios remotos" que es  un cliente de VNC, pero la verdad es que no me funciona bien, anda lento... y el mouse no puedo verlo (el teclado tampoco funciona!) así que estoy clavado y necesito usar esta herramienta...

muchas gracias!!!!!!!!!!!!!!

---

### Post by sergiom99 on 2008-06-26
Para usar VNC lo mejor que encontre es usar el Uvncviewer.exe con Wine.
Yo lo uso para acceder a servidores Win con UVnc.

---

### Post by Simbiosys on 2008-06-26
Estoy bajandolo para probar, lo que sucede es que me gusta poder mantener toda la estructura "normal" de la distribucion y tratar de no incorporar cosas por afuera, para manejar todo por repositorios... me llamo la atencion el hecho de tener "grisado" el protoloco vnc...

Gracias sergio.

---

### Post by sergiom99 on 2008-06-26
yo en su momento tuve tu misma intencion y no encontre un cliente para Uvnc en linux. con solo el exe del viewer lo puedo hacer sin problemas y asi estoy acostumbrado porque siempre lo usaba en Win$

---

### Post by vk-cdg on 2008-06-26
Te cuento nuestro caso en el trabajo. Nosotros usamos Ultr@VNC mas un plugIn que encripta la conexión entre el cliente y el servidor. Este plugIn es free también, se llama DSM PlugIn. 
La cosa es que no encontré un cliente para Linux que soportara este esquema hasta que me decidí a emular con Wine el cliente de Windows.

Los resultados son satisfactorios, Anda todo, incluso el plugIn de encriptación, así que dale tranquilo que no vas a tener prolbemas.

---

### Post by sergiom99 on 2008-06-26
sip, es lo mismo que hago yo. con el exe y el archivito del plugin en WinE funciona barbaro.

---

### Post by Mister X on 2008-06-26
> ...lo que sucede es que me gusta poder mantener toda la estructura "normal" de la distribucion y tratar de no incorporar cosas por afuera, para manejar todo por repositorios

Coincido plenamente.

El protocolo VNC es abierto y de ninguna manera necesitas de un virus (programa de windo$, jaja) para conectarte. Fijate que tal vez te falte instalar algun cliente VNC, busca en synaptic, yo tengo instalado los paquetes vnc-common, xvnc4viewer y xvncviewer, me funciona perfecto desde consola y desde el lanzador grafico tambien.

saludos

---

### Post by jonafischer on 2008-06-26
yo uso los visores VNC de gnome vino (server) y vinagre(viewer) y funcionan baastante bien, igualmente lo probe en una red LAN que anda mas rapido, el mouse se movia y todo!... Si no lo que hago es conectarme a la maq de mi trabajo que corre Debian Etch 4.0 por ssh, montando el sistema de archivos con sshfs. Para ssh (para mi es mucho mejor que VNC) uso ssh -X user@host_ip, que te permite usar las aplicaciones graficas. Y si se pone lento, uso la consola, navego por internet para bajar archivos con links2 que tiene javascript. Dejense de joder con programas de guindouse, usen los de linux que andan mas rapido y mejor...

---

### Post by vk-cdg on 2008-06-26
> **jonafischer said:**
> ...Dejense de joder con programas de guindouse, usen los de linux que andan mas rapido y mejor...

Si lográs que alguno de los clientes de VNC de linux levante el plugIn de encriptación (requisito en mi trabajo) dejo de usar el emulado con wine inmediatamente.
Imaginate que di vuelta media internet para ver si había algo, ya que hasta que no lograra hacer andar eso no podía instalar ubuntu en el trabajo.

---

### Post by sergiom99 on 2008-06-26
estoy probando el xvnc4viewer y me conecto al equipo XP remoto pero no tengo ninguna barra de herramientas ni nada. no puedo mandar el crl+alt+del para loguearme!

**EDIT:**
de casualidad puse
```
 sergio@kubuntu:~$ xvnc4viewer --help 
```
y salió... la ayuda (duh!) y me enteré que con F8 aparece el menú del programa.
Pero es mucho mas lento que usar el otro con WinE!

---

### Post by Mister X on 2008-06-27
> **sergiom99 said:**
> estoy probando el xvnc4viewer y me conecto al equipo XP remoto pero no tengo ninguna barra de herramientas ni nada. no puedo mandar el crl+alt+del para loguearme!

**EDIT:**
de casualidad puse
```
 sergio@kubuntu:~$ xvnc4viewer --help 
```
y salió... la ayuda (duh!) y me enteré que con F8 aparece el menú del programa.
Pero es mucho mas lento que usar el otro con WinE!

fijate con F8 en opciones y probá con otro tipo de encoding (no me acuerdo cual), se acelera muchisimo

---

