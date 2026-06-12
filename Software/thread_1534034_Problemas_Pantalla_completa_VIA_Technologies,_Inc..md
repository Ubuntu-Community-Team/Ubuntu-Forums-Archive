---
title: "Problemas Pantalla completa VIA Technologies, Inc. KM400/KN400/P4M800"
date: 2010-07-18
forum: Software
---

### Post by Cholon on 2010-07-18
Cuando pongo algun video en pantalla completa se pone la pantalla blanca y no se ve nada

---

### Post by Patriciologico on 2010-07-19
Hola Cholon,

Te recomiendo des mas información sobre el problema, tu equipo y la distribución que usas o si tienes otros problemas graficos (puede que solo la salida de video sea el problema, o haya un conflicto con compiz)

Puedes usar [Huuf]("http://ubuntuforums.org/showthread.php?t=1410952") para generar reportes de tu equipo.

o usar estos comandos

```
lspci
``````
lshw
```

Ademas puedes agregar que salida de video estas usando

```
gstreamer-properties
```

Es relevante saber con que reproductor te sucede, pues no todos usan gstreamer, (VLC, mplayer, Xine, etc, tienen salidas independientes)

Saludos.

---

### Post by Cholon on 2010-07-19
ocupo ubuntu 10.04, hasta el momento no tengo otros problemas, y me pasa en paginas como youtube 

con lspci me sale la siguiente informacion

00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] (rev 01)

con lshw me sale

WARNING: you should run this program as super-user.
montecinos                
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1015MiB
     *-cpu
          product: AMD Athlon(tm) XP 2200+
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 6.8.1
          size: 1800MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 256KiB
     *-pci
          description: Host bridge
          product: VT8378 [KM400/A] Chipset Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-via latency=8
          resources: irq:0 memory:d0000000-d7ffffff(prefetchable)
        *-pci
             description: PCI bridge
             product: VT8237/VX700 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master cap_list
             resources: memory:dc000000-ddffffff memory:d8000000-dbffffff(prefetchable)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: KM400/KN400/P4M800 [S3 UniChrome]
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list
                configuration: latency=32 mingnt=2
                resources: memory:d8000000-dbffffff(prefetchable) memory:dc000000-dcffffff memory:dd000000-dd00ffff(prefetchable)
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:21 ioport:d000(size=32)
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:21 ioport:d400(size=32)
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:21 ioport:d800(size=32)
        *-usb:3
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: 82
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:21 memory:de000000-de0000ff
        *-isa
             description: ISA bridge
             product: VT8235 ISA Bridge
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 11.1
             bus info: pci@0000:00:11.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=pata_via latency=32
             resources: irq:20 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:dc00(size=16)
        *-multimedia
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@0000:00:11.5
             version: 50
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: driver=VIA 82xx Audio latency=0
             resources: irq:22 ioport:e000(size=256)
        *-communication
             description: Communication controller
             product: AC'97 Modem Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.6
             bus info: pci@0000:00:11.6
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: driver=VIA 82xx Modem latency=0
             resources: irq:22 ioport:e400(size=256)
        *-network
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 74
             serial: 00:0c:76:34:4b:4a
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 ip=200.86.203.41 latency=32 maxlatency=8 mingnt=3 multicast=yes
             resources: irq:23 ioport:e800(size=256) memory:de001000-de0010ff

y con gstreamer-properties me dice :

video 
Salida predeterminada
Complemento: autodetectar
dispositivo: no soportado
pipeline: autovideosink

de antes te agradesco por responderme y tratar de ayudar:p

---

### Post by Carlos C on 2010-07-19
Las tarjetas VIA no tienen buen desempeño en linux. En este mismo foro existe más de una discusión al respecto:

[http://ubuntuforums.org/showthread.php?t=1164426&highlight=driver](http://ubuntuforums.org/showthread.php?t=1164426&highlight=driver)

[http://ubuntuforums.org/showthread.php?t=1211580&highlight=driver](http://ubuntuforums.org/showthread.php?t=1211580&highlight=driver)

[http://ubuntuforums.org/showthread.php?t=1470204](http://ubuntuforums.org/showthread.php?t=1470204)

Te recomiendo que leas estos thread con la esperanza de obtener el mejor rendimiento de tu tarjeta, pero debes tener en mente que nunca alcanzará el nivel de rendimiento de otras marcas.

---

