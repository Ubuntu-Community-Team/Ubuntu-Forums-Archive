---
title: "Desaparecen los bordes de ventanas con compiz"
date: 2011-01-20
forum: Software
---

### Post by electric_dragon on 2011-01-20
Hola hace mucho intenté instalar compiz para lograr tener los efectos de escritorio en mi ubuntu pero desaparecieron los bordes y se me hizo un lío bárbaro, hace poco actualicé ubuntu y vuelvo a la carga.
Una de las causas puede ser que no tengo tarjeta de video? voy a Sistemas->Administración->Controladores Adicionales y me salta el cartel "No se están usando controladores privativos en este sistema" y no me aparece ninguna lista para instalar alguno.
Como soy nuevo mucho de esto no entiendo, acá les dejo mis datos 


00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
00:1f.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)
03:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
03:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
03:00.3 System peripheral: JMicron Technology Corp. MS Host Controller

Saludos, gracias de antemano.

---

### Post by guillermolisi on 2011-01-20
Esta es tu placa de video:> 01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)

Hasta donde tengo entendido, esa placa no posee aceleracion grafica, caracteristica necesaria para que Compiz funcione adecuadamente.

El asunto de los bordes es porque cuando cargas Compiz, Emerald (el decorador de ventanas) es reemplazado. Como COmpiz no puede funcionar por no tener una placa de video adecuada, te quedas sin los efectos de escritorio y sin Emerald (luego sin los bordes).

---

### Post by granjero on 2011-01-20
a mi en mi laptop a veces no me carga el decorador de ventanas al iniciar.

al principio cerraba y abría la sesión. Ahora instalé "compiz fusion icon" y con ese podés recargar con un solo click el decorador.

salud!

---

