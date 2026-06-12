---
title: "Configuracion de pantalla y actualizaciones"
date: 2011-06-23
forum: Software
---

### Post by ignacioguevara on 2011-06-23
Hola a todos:
tengo este problema.
Actualmente me encuentro utilizando Ubuntu 9.10 en la oficina. y ya que no hay mas soporte pense en actualizar a versiones mas nuevas. Pero con el problema que me encontre es que ene stas la resolucion de pantalla no sale de 800x600, cuando ahora estoy usando 1024 x 768 (4:3).
Mas abajo les dejo los reportes que consegui via consola con lspci y xrandr.
Como podran ver el controlador VGA es un Intel 82456G/GL y en 9.10 puedo utilizar hasta 4 resoluciones distintas. Pero en 10.04 y en 11.04 (probe con los 2, en 10.10 todavia no porque perdi el cd y lo estoy bajando otra vez) la resolucion no sale de 800 x 600. De hecho cuando actualiza a 10.04 via actualizacion via internet (de la cual volvi a 9.10, pero reinstalando todo) tuve el problema adicional al de la resolucion de que no podia ver el cursor, este estaba funcionando pero no se veia hasta que intentaba cambiar la resolucion de pantalla llendo a Sistema / Preferencias / Pantalla.
Otra cosa que me pasa ahora es que estando justamente alli la aplicacion me informa que estoy utilizando un monitor HP de 14 pulgadas, lo cual es cierto porque uso un HP 5500. Pero esta informacion no la obtengo en las otras versiones de la distribucion. Para mas datos el informe de lspci en 10.04 y en 11.04 informa "00:02 default compatible controler"  en ves de "00:00 VGA ..."

ignacio@ignacio-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
**[COLOR=Black]00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)[/COLOR]**
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
03:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
ignacio@ignacio-desktop:~$ 

ignacio@ignacio-desktop:~$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 2048 x 2048
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 265mm x 199mm
   800x600        85.1 +   75.0  
   1024x768       60.0* 
   640x480        75.0     60.0  
   720x400        70.1  


Espero que me puedan ayudar.
un saludo


ignacio

---

### Post by gmunioz on 2011-06-23
Prueba activando los repositorios ppa para intel.
[https://launchpad.net/~glasen/+archive/intel-driver](https://launchpad.net/~glasen/+archive/intel-driver)
E instalando los drivers y sus bibliotecas.

---

