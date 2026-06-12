---
title: "Velocidad de bajada disminuida"
date: 2009-02-25
forum: Software
---

### Post by sirkurt on 2009-02-25
Desde que me pase a ubuntu llegue a notar que mi velocidad de bajada es muy inferior a la que realmente por banda ancha y la cual funcionaba bien en windows, para que se den una idea tengo 1 mega y medio y con gestores y sin estar uzando ninguna aplicacion que necesite internet estoy bajando a una velocidad promedio de 40k.....

A alguien mas le paso? alguna sugerencia?

---

### Post by luks911 on 2009-02-25
Mmmmm.... si en efecto estás seguro de que hay una diferencia con respecto a la velocidad de bajada en Windows, es decir que no se trata de un problema de tu ISP, por ejemplo, podrías revisar el driver de la placa con la que te conectás. 

¿Es wifi o cableada? ¿Qué drivers usa? Y en una terminal ejecutá lspci (si es pci) o lsusb (si es usb) y pegá el resultado para ver qué placa es.

---

### Post by sirkurt on 2009-02-25
bueno es una red cableada y esta conectada a un router si necesitas algo mas de info decime te dejo el resultado del codigo 


[HTML].00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP61 SMU (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT (rev a1)[/HTML]

---

### Post by luks911 on 2009-02-25
Tratándose de esa placa, descarto la posibilidad de que se trate de un tema de drivers. 
Hacé la prueba de velocidad de acá [http://www.speedtest.net/](http://www.speedtest.net/) a ver qué pasa. Si todavía lo tenés, hacela también en Windows y repetila varias veces para ver si hay cambios.
Además podés probar el applet netspeed, que te muestra la velocidad de todo el tráfico de la red. Esto porque, en una de esas, cuando estabas bajando ubuntu buscaba actualizaciones, por ejemplo, y eso afectaba la descarga.

---

### Post by sirkurt on 2009-02-25
[[IMG]http://www.speedtest.net/result/418488566.png[/IMG]](http://www.speedtest.net)

ahi estan los resultados y parece estar todo bien.... no puede ser algo de configuracion de ubuntu?....

con el Jdownloader almenos de noche hasta las 10 de la mañana descarga perfecto, pero los otros gestores nunca suben de 50

---

### Post by pol666 on 2009-02-25
Leo bien o estas bajando a mas 1mb eso es muchisimo o estoy medio dormido. Es casi a un doble de loq ue bajo yo  :|

---

### Post by sirkurt on 2009-02-25
si el problema es justamente que en pocos casos baja a esa velocidad.....
y solamente me pasa en ubuntu

---

### Post by luks911 on 2009-02-26
Cierto, la prueba da bien. No soy experto, pero no creo que haya algo de Ubuntu que lo provoque. ¿Bajando con qué programas tenés el problema? 
Si no, quedan dos posibles culpables, creo: el ISP o el lugar desde donde descargas.

---

