---
title: "no se conecta a la red inalambrica"
date: 2009-09-26
forum: Software
---

### Post by Leandro17 on 2009-09-26
primero les explico como es la red...

con mi pc de mesa con winxp sp3 e internet de arnet (atravez del modem usb huawei mt810) le paso conexion y archivos a travez de una red ad-hoc inalambrica a mi notebook comapq cq50-111la que tiene ubuntu 9.04 (y vista starter en otra particion)..

hasta hace unos dias todo andaba bien, ambas se conectaban y la notebook desde ubuntu tenia todo el acceso permitido por la pc, luego por otros motivos tuve que volver a configurar la red y desde ahi ubuntu no se conecta... detecta la red pero no se conecta, a cada rato me pide la contraseña y siempre la pongo bien y no se conecta... probe con una red sin cifrado y tampoco se conecta... que problema sería?

pareciera que es problema de winxp, pero desde la particion de vista puedo conectarme (eso si, no tengo internet, pero eso fue un problema de siempre desde esa particion)...

que me suguieren??


saludos...

---

### Post by emiliano_raso on 2009-09-26
Estas usando gnome-network-manager? Es decir, la aplicacion en el area de notificacion para conectarse a la red que te viene por defecto cuando instalas?

Si es asi, entonces probá conectarla por cable de red a la notebook. Tiene que funcionar. Si funciona y se conecta, instalá WICD.
Está en el Añadir y Quitar.
Funciona mejor. Hay redes que el gnome-power-manager no procesa bien. Pôrque? No se :-S

Espero que te sirva.

---

### Post by Leandro17 on 2009-09-26
> **emiliano_raso said:**
> Estas usando gnome-network-manager? Es decir, la aplicacion en el area de notificacion para conectarse a la red que te viene por defecto cuando instalas?

Si es asi, entonces probá conectarla por cable de red a la notebook. Tiene que funcionar. Si funciona y se conecta, instalá WICD.
Está en el Añadir y Quitar.
Funciona mejor. Hay redes que el gnome-power-manager no procesa bien. Pôrque? No se :-S

Espero que te sirva.

si estoy usando gnome-network-manager...  cable no tengo, asi que voy a probar bajandome el wicd...  gracias

como lo instalo sin internet?

---

### Post by emiliano_raso on 2009-09-27
Primero desinstalá el network manager de Gnome.
1) Abri una consola
2) ```
sudo aptitude remove network-manager
```
3) ```
sudo aptitude purge network-manager
```

Si te conseguis el .deb de WICD lo ejecutas como un .exe clasico de Windows.
Si lo queres instalar por consola (porque sos re heavy re jodido) haces lo siguiente:

1) Abris una consola

2) Te metes en el directorio donde tenes el .deb (suponiendo que lo tenes en el escritorio, ya que apenas abris una consola te ubica en tu HOME, entonces tiras el siguiente comando)
```
cd Escritorio
```

3) ```
sudo dpkg -i nombre_del_archivo.deb
```

Listo. Ahi se instala. Seguramente te preguntará por s/n algo. Decí que si.
Despues lo agregas a las aplicaciones al inicio si no se agregó solo en Sistema/Administracio/Aplicaciones al inicio.


Desde aca te bajas del .deb
Bajalo con otra maquina en la que tengas internet y pasateló a la otra con un pendrive o lo que sea.
[http://sourceforge.net/projects/wicd/files/wicd-stable/wicd%201.3.1/wicd_1.3.1-all.deb/download](http://sourceforge.net/projects/wicd/files/wicd-stable/wicd%201.3.1/wicd_1.3.1-all.deb/download)

---

### Post by Hei Ku on 2009-09-27
El Wicd ya esta en los repositorios de la 9.04.

---

### Post by Leandro17 on 2009-09-27
gracias ya tengo instalado el wicd, pero sigue sin conectarse... ya deberia estar suponiendo que es problema de win

---

### Post by emiliano_raso on 2009-09-27
> **Hei Ku said:**
> El Wicd ya esta en los repositorios de la 9.04.

Si lo se, pero no tiene internet. :-P

---

### Post by NickCis on 2009-09-27
Medio Offtopic: Puede ser que te reconosca menos fuerza de señal wifi con Ubuntu?. Por que en una pc que tiene una placa wifi (una encore pci, me parece), estando en widnows me dice maxima, y en ubuntu me da como mucho 20% =S. O es el chamullo de windows?.

Saludos.
P.D.: el router wifi, es uno qe te da speedy qe es modem tmb, ese qe se parece a un porta retratos xD,,, y toy usando el gnome-network manager (el q viene por defecto).

---

### Post by Leandro17 on 2009-09-28
> **NickCis said:**
> Medio Offtopic: Puede ser que te reconosca menos fuerza de señal wifi con Ubuntu?. Por que en una pc que tiene una placa wifi (una encore pci, me parece), estando en widnows me dice maxima, y en ubuntu me da como mucho 20% =S. O es el chamullo de windows?.

Saludos.
P.D.: el router wifi, es uno qe te da speedy qe es modem tmb, ese qe se parece a un porta retratos xD,,, y toy usando el gnome-network manager (el q viene por defecto).

si en vista me reconoce un poco mas de señal y ademas el indicador se pone en azul... mi modem es de arnet y por desgracia no es router...


sigo sin poder conectarme, se queda validando la autenticacion... puede ser que algun controlador de la tarjeta esta fallando? como puedo comprobarlo...

---

### Post by Leandro17 on 2009-09-28
Perdon por el doble post, pero ahora estoy conectado desde la notebook con ubuntu, pero desde el liveusb que tengo, y conectado con el network.manager... esto me clarifico algunas cosas, y supongo que a ustedes tambien... supongo que es algun controlador o configuracion de la placa que esta mal, pero cual y como puedo saberlo y solucionarlo

---

### Post by emiliano_raso on 2009-09-28
Copiá y pegá lo que te diga este comando:
```
lspci
```

---

### Post by Leandro17 on 2009-09-29
eso es lo que me dejo el lspci

```

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

```

emm.. parece que esta bien no?

---

### Post by Leandro17 on 2009-09-30
Puedo reinstalar ubuntu en la misma particion... podria ser una solucion?

---

### Post by Leandro17 on 2009-10-01
Buscando en interent encontre esto [https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo) y puse en parctica en la parte que dice Avoiding password nagging... lastima que es para una version anteerior, ademas ahora en la pantalla de inicio de sesion de ubuntu me dice error en ... ehmm algo ahí... la cuestion es que ya esta puesto el password, y debe ser por las cosas que instale siguiendo esa guia, bueno, ahora no puedo iniciar sesion..._ yo creo que la solucion más facil es formatear toda esa particion e instalar ubuntu nuevamente_, total hace un mes que vengo usando y muchas cosas no lo he puesto, pero bueno, yo creo que en ubuntu no es tan facil, mas teniendo en cuenta que _en otra particion tengo vista_ y no quiero perderlo... entonces como puedo hacer?... la verdad esto me esta quemando el coco y como lo dije en otra parte deberia estar estudiando derecho porque mañana tengo dos parciales #-o

---

### Post by guillermolisi on 2009-10-01
> **Leandro17 said:**
> Buscando en interent encontre esto [https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo) y puse en parctica en la parte que dice Avoiding password nagging... lastima que es para una version anteerior, ademas ahora en la pantalla de inicio de sesion de ubuntu me dice error en ... ehmm algo ahí... la cuestion es que ya esta puesto el password, y debe ser por las cosas que instale siguiendo esa guia, bueno, ahora no puedo iniciar sesion..._ yo creo que la solucion más facil es formatear toda esa particion e instalar ubuntu nuevamente_, total hace un mes que vengo usando y muchas cosas no lo he puesto, pero bueno, yo creo que en ubuntu no es tan facil, mas teniendo en cuenta que _en otra particion tengo vista_ y no quiero perderlo... entonces como puedo hacer?... la verdad esto me esta quemando el coco y como lo dije en otra parte deberia estar estudiando derecho porque mañana tengo dos parciales #-o
Las prioridades las administras vos, ni nosotros ni Ubuntu.

Hay miles de personas satisfechas con Ubuntu en el mundo y digo miles para ser conservador.

Aprender, familiarizarse con cosas nuevas lleva su tiempo. Pensa en tu carrera universitaria y fijate cuanto dura para que tengas un ejemplo.

Muchos de los problemas que se presentan tienen que ver con desconocimiento y meter la mano sin saber que se esta haciendo realmente (á la Windows).

---

### Post by Leandro17 on 2009-10-01
> **guillermolisi said:**
> Las prioridades las administras vos, ni nosotros ni Ubuntu.

Hay miles de personas satisfechas con Ubuntu en el mundo y digo miles para ser conservador.

Aprender, familiarizarse con cosas nuevas lleva su tiempo. Pensa en tu carrera universitaria y fijate cuanto dura para que tengas un ejemplo.

Muchos de los problemas que se presentan tienen que ver con desconocimiento y meter la mano sin saber que se esta haciendo realmente (á la Windows).

No digo que estoy insatisfecho con ubuntu, es más considero que es un sistema operativo mucho mas rapido e intuitivo que vista, lo que pasa es que yo no soy el unico que usa la notebook, y mas alla de que mi hermano, el otro que usa la portatil, no tiene problemas al usar ubuntu, me pidieron que deje la particion de vista por cualquier cosa...

Lo que pasa es que la notebook en un 99% la usamos para entrar en internet, y como no tiene acceso estoy tratando, generalmente de manera erronea, solucionar el problema y a veces me pongo nervioso al no encontrar documentacion y uso más tiempo para tratar de solucionarlo, lo que me resta horas de estudio...

Paradojicamente el error no devino en un desconocimiento (bahh eso creo), ya que luego de reconfigurar algo en la pc servidor la notebook no se pudo conectar más, y mas extraño aún es que desde el liveusb se conecta.. y puedo afirmar que no meti mano en la notebook anteriormente al problema...

Volviendo al tema, yo creo que la solución más fácil sería formatear la particion de ubuntu e instalarlo nuevamente, pero tengo entendido que hay una parte de grub que no hay que tocar o hay que modificarlo, cosa que no sé... por eso pido ayuda...

---

### Post by Leandro17 on 2009-10-02
pueden ponerlo como solucionado... una vez reinstalado el sistema, todo va de 10...

gracias emiliano por la ayuda

---

