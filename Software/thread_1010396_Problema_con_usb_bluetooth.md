---
title: "Problema con usb bluetooth"
date: 2008-12-13
forum: Software
---

### Post by Mauro22 on 2008-12-13
Hola!!


Tengo el cerebro frito de buscar tanta info sobre esto y no lo arreglo...

Objetivo: Quiero mandar un archivo PC -> Celular

Problema: Da error, el BT lo reconoce pero no conecta

Observaciones: 

De Celular -> PC todo joya!
Ya instale todo lo que tenga que ver con bluez bluetooth bluegnome etc etc 
LLegue al punto que -supongo- es asi:

gnome-obex-send    <--- Sirve para enviar. No lo tengo!! 
gnome-obex-server   <--- Sirve para recibir. Este esta!!



El usb es generico pero andaba lo mas bien en hardy




Ubuntu 8.10 Gnome


Tenkiu ):P

---

### Post by andy_91 on 2008-12-13
es un bug de ubuntu 8.10. A mi me pasaba lo mismo, pero tampoco podia enviar cosas al pc.

Me cambie a ubuntu Hardy Heron y ahora anda sin problemas

---

### Post by Hei Ku on 2008-12-13
Reportaron el bug en Launchpad o saben si ya esta reportado?

---

### Post by Mauro22 on 2008-12-13
> **andy_91 said:**
> es un bug de ubuntu 8.10. A mi me pasaba lo mismo, pero tampoco podia enviar cosas al pc.

Me cambie a ubuntu Hardy Heron y ahora anda sin problemas


Que mal.... :(


[quote=Hei Ku]Reportaron el bug en Launchpad o saben si ya esta reportado? 	[/quote]

No se como se hace o donde me tengo que fijar?



Grax

---

### Post by Hei Ku on 2008-12-13
Aca estan los bugs de Ubuntu, te podes fijar si esta reportado.

[https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/)

---

### Post by andy_91 on 2008-12-13
aca estan todos los de bluetooth

[bug bluetooth]("https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=bluetooth&orderby=-importance&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=")

I can't speaking english very well

---

### Post by whac on 2008-12-14
english please?

en ingles, por favor?

---

### Post by andy_91 on 2008-12-14
> **whac said:**
> english please?

en ingles, por favor?


no entendi, que fue lo que le editaron al post :confused:
 es que lo vi recien ahora y no me cierra

creo que me confundi cuando puse 

I can't speaking english very well

seria mas bien I can't reading english very well

---

### Post by Hei Ku on 2008-12-14
lenguaje inapropiado para este foro. :lolflag:

---

### Post by andy_91 on 2008-12-14
con lenguage te referis a idioma o a exprecion :confused:

---

### Post by Hei Ku on 2008-12-14
buena pregunta. ;)

Recuerdas si habia un bug reportado sobre el problema con el bluetooth que tiene Mauro?

---

### Post by andy_91 on 2008-12-14
recuerdo que hay uno que es alrreve, pero me parese que no esta ese

[https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/283064](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/283064)


ahi habla un poco de todo, pero como esta en ingles no se decir bien si el problema esta ahi

---

### Post by faktorqm on 2008-12-15
fijate si te sive esto: [http://ahorcandoeltiempo.blogspot.com/2007/07/bluetooth-en-ubuntu.html](http://ahorcandoeltiempo.blogspot.com/2007/07/bluetooth-en-ubuntu.html)

yo diria de mandarle gas al paquete de una, no importa si es hardy o intrepid, mientras cumpla las depndencias. salu2!

---

### Post by Mauro22 on 2008-12-15
Alguien me podria pasar el gnome-obex-send... porque ningun paquete lo tiene... por ahi de una de esas anda...


):P

---

### Post by faktorqm on 2008-12-15
Che y no sera el nuevo paquete obex-data-server? mira esto:

```
faktorqm@the-edge:~$ aptitude search obex
p   cobex                                                                                      - Connector for mobile devices                                                                        
p   gnome-vfs-obexftp                                                                          - GNOME VFS module for OBEX FTP                                                                       
p   libobexftp-dev                                                                             - object exchange file transfer library                                                               
v   libopenobex-dev                                                                            -                                                                                                     
i   libopenobex1                                                                               - OBEX protocol library                                                                               
p   libopenobex1-dev                                                                           - OBEX protocol library - development files                                                           
i   obex-data-server                                                                           - D-Bus service for OBEX client and server side functionality                                         
p   obexfs                                                                                     - mount filesystem of ObexFTP capable devices                                                         
p   obexftp                                                                                    - file transfer utility for devices that use the OBEX protocol                                        
p   obexpushd                                                                                  - program for receiving files via Bluetooth or IRDA                                                   
p   obextool                                                                                   - graphical frontend for obexftp written in TCL/TK                                                    
p   openobex-apps                                                                              - Applications for OpenOBEX                                                                           
faktorqm@the-edge:~$ 

```

yo tengo instalado y si bien no tengo ningun dispositivo bt puedo ejecutar hcitool como dice el blog que te pase. Revisa eso, salu2!

---

### Post by Mauro22 on 2008-12-15
Por lo que entiendo el server es para recibir y buscar...


el send es para enviar.

---

