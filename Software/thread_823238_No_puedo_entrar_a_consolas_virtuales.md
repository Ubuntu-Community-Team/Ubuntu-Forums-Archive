---
title: "No puedo entrar a consolas virtuales"
date: 2008-06-09
forum: Software
---

### Post by EnriqueK on 2008-06-09
Tengo Ubuntu 8.04 y resulta que le puse una gráfica Nvidia , instalé los controladores restrigidos que propociona Ubuntu y no funciona adecuadamente, concretamente se bloquea el sistema por un tiempo cuando ejecuto programas gráficos como ser el Blender e inclusive con el salvapantallas, por eso decidí instalar el último Driver que provee Nvidia , para poder instalarlo debo usar la consola, matar las X y prceder a compilar, pero tengo un problema, no puedo matar las X, tira un pantallazo de colores raros y se bloquea, la única forma de poder hacerlo es entrando por Recovery Mode, pero ahora tengo otro problema necesito poder conectarme a Internet por mi módem telefónico y para eso requiero abrir otro terminal, probé con Ctrl+Alt+F2....F6 y ninguno funciona, aclaro que tampoco puedo entra a estas consolas virtuales desde Gnome (se bloquea de igual forma que antes), probé todas las alternativas que leí en cuanto foro tengo conocimiento y nada, en concreto quisiera saber si hay alguna otra forma de abrir al menos una consola virtual adicional.
Estaba pensado si conecto el monitor a la salida de la gráfica integrada , que es una Intel y nunca me dio problemas y allí si creo que puedo abrir consolas virtuales, no se como será  si no causará mas problemas.

---

### Post by faktorqm on 2008-06-09
Arranca el x con cualquier driver que ande. Despues lee aca: [http://ubuntuforums.org/showthread.php?t=809714&page=2](http://ubuntuforums.org/showthread.php?t=809714&page=2) Salu2!!

---

### Post by EnriqueK on 2008-06-09
Gracias, pero ya había probado con el EnvyNG ,  te baja los mismos controladores que te provee Ubuntu en "controladores restringidos", en resúmen todo sigue igual.
Después de publicar este hilo me decidí a arrancar el equipo con la gráfica integrada, allí si pude entrar a las consolas virtuales, procedí a copmpilar el último driver provisto por Nvidia, pero no pude lograrlo por que me indica que ellos no cuentan con un módulo del kernel precompilado y que yo debo hacerlo manualmente, el asunto es que cuando reinicié el equipo ya no contaba con gráfica, así que recurrí a instalar una imagen de restauración creada previamente con el Acronis True Image, asi que sigo en las mismas, curioso que no tengan módulo de kernel precompilado para Ubuntu, siendo que esta distro debe ser por lejos la mas usada, supongo que habrá que esperar o tendré que compilar el módulo del kernel y eso si que no tengo la mas mínima idea de como hacerlo.

---

### Post by faktorqm on 2008-06-09
Bueno, el envy entre otras cosas eso lo hace automaticamente. Que placa de video tenés? no lo ponés en ningun lado....... me da la sensacion de que tenes alguna placa nvidia "vieja", estilo gforce 4, o algo de eso, y le estas poniendo el ultimo driver cuando no esta soportado. En la pagina de nvidia te dice que versiones del drivers soportan tal o cual placa. Salu2!!

---

### Post by EnriqueK on 2008-06-09
Mi gráfica es GForce 6200, para ranuras AGP, pero me Mother es una Asrock , por lo que en vez de ser AGP es AGI , no se cual será la diferencia pero en Xp funciona bien.

---

### Post by faktorqm on 2008-06-10
uhhh mira que tengo años en computación/informática y jamás había visto  semejante.... AGI significa Asrock Graphics Interface (interfaz de gráficos Asrock). Esta tramoya lo que hace es darle soporte AGP a un mother que nativamente no lo soporta por chipset, como no le pueden dar soporte a AGP 100% inventaron eso que funciona SOLO con una lista de placas de video conocidas.
Hagamos una cosa, postea la salida de los comandos "lspci" y "lshw" a ver como te esta "viendo" ubuntu y de ahi vemos que podemos hacer. Salu2!!

---

### Post by EnriqueK on 2008-06-10
> **faktorqm said:**
> 
Hagamos una cosa, postea la salida de los comandos "lspci" y "lshw" a ver como te esta "viendo" ubuntu y de ahi vemos que podemos hacer. Salu2!!

Aquí va lo que pedís, pero antes te comento que por fin pude compilar el último driver propietario de Nvidia , pero todo sigue igual, no noto mejora alguna.
Aquí se ve la presencia de dos cotroladore de video uno Intel y otro Nvidia, no se, tal vez la solución venga en eliminar el módulo Intel y dejar solo el de Nvidia, todo esto es nuevo para mi.
enrique@enrique-desktop:~$ lshw
(Solo la parte que puede interesar)

*-pci 
         description: Host bridge
          product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display
             description: Display controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=i810_smbus latency=0 module=i2c_i810
 *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 82
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master

*-display
                description: VGA compatible controller
                product: NV44A [GeForce 6200]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                version: a1
                width: 32 bits
                clock: 66MHz
                capabilities: vga_controller bus_master cap_list
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia




enrique@enrique-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 Display controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
03:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)
03:04.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
03:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by EnriqueK on 2008-06-11
Tema solucionado, el problema era causado por la tarjeta madre ASROCK , para arreglar el problema basta con poner en lista negra a la gráfica Intel mediante los siguientes comandos 

 sudo gedit  /etc/modprobe.d/blacklist
Añadir al final del fichero esto:
 blacklist intel_agp

---

