---
title: "Lucid Lynx RC no arranca (Live CD)"
date: 2010-04-23
forum: Software
---

### Post by atari130xe on 2010-04-23
Vuelvo a al foro para ver si alguno de uds. tiene el mismo inconveniente con Lucid Lynx.

En modo Live arrancando "normalmente" sencillamente no funciona en una CPU con la siguiente configuracion:

> Motherboard: Biostar PM890-M7 - 1.5MB RAM 160GB HD - Intel Celeron 420 1.6Mhz Processor Video Via Chrome integrado
• Processor:
Supports Intel Pentium 4 processor ,Celeron D, Pentium D, and Core 2 Duo processor in LGA 775 package.
1066MHz system interface speed.
Supports Hyper-Threading Technology.
• Chipset:
VIA P4M890 VIA8237R+
• Memory:
Support 2 Single Channel DDR2
Support DDR2 533/400 Mhz
Maximum memory capacity is 4GB
RAM Support 256/512/1GB/2GB
• Slots:
2 x PCI Slot
1 x PCI-Express x 1 Slot
1 x PCI-Express x 16 Slot
• IDE:
2 x EIDE channels (up to 4 devices)
Ultra DMA 33/66/100/133 Bus Master Modes
• I/O:
1 x CD-In Connector
1 x VGA , 1 x Serial Port
2 x IDE Devices Connector
1 x RJ-45 LAN Jack
2 x Serial ATA Connectors
8 x USB 2.0 Ports (4 x Rear USB 2.0 , 4 x Front USB 2.0 )
1 x Floppy
1 x Lin-out/Lin-in/Mic-In
1 x PS/2 mouse, 1 x PS/2 keyboard
1 x S/PDIF Out Connector
• SATA:
Integrated in South Bridge VT8237R+
Support RAID 0 / 1 functions.
Data transfer rates up to 150MB/s
• Video:
VIA UniChrome Pro
• Audio:
Realtek ALC658-6Channel AC 97 2.3 CODEC
• LAN:
Realtek RTL8201CL PHY
--- Integrated 10/100 transceiver 

Luego de no menos de 5 minutos en los cuales la bandeja de CD ROM gira como loca leyendo info e imagino tratando de identificar el hardware de la PC, (con la pantalla totalmente en color negro) se escucha el sonido de inicio de Ubuntu y luego (sin entrar al escritorio) aparece GDM pidiendo usuario y contraseña cuando no deberia (no está instalado). Probé con usuario: ubuntu password: ubuntu y nada, probre con root root y tampoco. Entre otras cosas por lo que logro interpretar parece ser que se inicia Ubiquity directamente en el proceso de booteo porque entre otras cosas aparece una cartel con una advertencia como esta: "el instalador debe cerrarse" ( :confused: ), en la versión anterior (beta 2) e iniciando en modo verbose lo último que aparece antes de "freezarse" es lo siguiente:
```
Begin: Running /scripts/init-bottom ...
Done:
init: ureadahead-other main process (1089) terminated with status 4
init: ureadahead-other main process (1090) terminated with status 4
* setting sensors limits                                        (OK)
```

y ahí quedaba.

No probé con la versión alternate deberia bajar la imagen y quemarla en un CD, pero sería muy interesante para mi saber si a otros les pasa lo mismo.

gracias como siempre.

PD: No está demás aclarar que revisé la ISO (MD5 checksum) antes de quemarla en un CD (Hice 2 copias en diferentes Grabadoras por si acaso)

---

### Post by santiagoward2000 on 2010-04-23
> **atari130xe said:**
> No probé con la versión alternate deberia bajar la imagen y quemarla en un CD, pero sería muy interesante para mi saber si a otros les pasa lo mismo.

Hola!
No es exactamente lo mismo, pero también estoy teniendo problemas para entrar al LiveCD de Lucid RC. En mi desktop se queda un rato en el upslash, y después me apaga el monitor, como si no mandara señal la placa de video (tengo una GeForce 9400 GT).
No sé que será.
Saludos!

_EDIT:_
Acabo de probarlo en mi laptop que tiene una GeForce 8400 GS y me pasa lo mismo :(

---

### Post by atari130xe on 2010-04-23
Si Santiago, es muy raro todo, acabo de instalarlo en mi PC y fué todo relativamente bien. Ahora en la PC en cuestión fué un total desastre ni siquiera pude instalar el paquete de idiomas, se bloqueaba (no sé porqué) así que a esa PC estoy viendo de instalarle PCLinuxOS 2010 (no me simpatiza mucho porque utiliza .rpm) o Mepis 8.5 que está basado en Debian, ambos en Modo Live CD funcionan muy bién ahora que pasó con Lucid ni idea, se que no hay caso específicamente con esa configuración.
Aclaro que logré pasar del GDM (Usuario Ubuntu y luego enter o sea password en blanco).

---

