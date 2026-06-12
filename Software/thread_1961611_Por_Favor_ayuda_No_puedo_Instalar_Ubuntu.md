---
title: "Por Favor ayuda No puedo Instalar Ubuntu"
date: 2012-04-19
forum: Software
---

### Post by mhistral5 on 2012-04-19
Hola compañeros, 

acudo a su ayuda tengo ubuntu en CD y quise instalarlo en mi pc, tengo un sistema XP, sin embargo cuando voy al CD y hago clic en el ejecutabl "Wubi", y despues de que empieza a instalar en mitad del proceso se detiene y me dice que hubo un error y me la ruta de un archivo log, habro el archivo log y me muestra lo siguiente 

copio un fragmento de la ultima parte 


> 
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 202, in copy_file
IOError: [Errno 22] Invalid argument
04-20 15:17 DEBUG  TaskList: # Cancelling tasklist
04-20 15:17 DEBUG  TaskList: New task check_iso
04-20 15:17 ERROR  root: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 205, in run_cd_menu
  File "\lib\wubi\application.py", line 120, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 202, in copy_file
IOError: [Errno 22] Invalid argument
04-20 15:17 ERROR  TaskList: 'WindowsBackend' object has no attribute 'iso_path'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 579, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 565, in use_iso
AttributeError: 'WindowsBackend' object has no attribute 'iso_path'
04-20 15:17 DEBUG  TaskList: # Cancelling tasklist
04-20 15:17 DEBUG  TaskList: # Finished tasklist




me pasa cada vez que quiero instalar Ubuntu, por favor diganme que es lo que debo hacer, desde ya muchas gracias

---

### Post by mhistral5 on 2012-04-19
esta es mi maquina por si sirve de algo

> 

Computadora:
      Tipo de computadora                               Equipo multiprocesador ACPI
      Sistema operativo                                 Microsoft Windows XP Professional
      Service Pack del sistema operativo                Service Pack 3
      Internet Explorer                                 8.0.6001.18702 (IE 8.0)
         
    Motherboard:
      Tipo de CPU                                       DualCore Intel Core 2 Duo E4300, 1800 MHz (9 x 200)
      Nombre del motherboard                            Biostar 945GZ Micro 775 SE  (3 PCI, 1 PCI-E x16, 2 DDR2 DIMM, Audio, Video, LAN)
      Chipset del motherboard                           Intel Lakeport-G i945GZ
      Memoria del sistema                               1015 MB  (DDR2-533 DDR2 SDRAM)
      DIMM1: NovaTech Solutions NA2D001G37D             1 GB DDR2-533 DDR2 SDRAM  (4-4-5-12 @ 266 MHz)  (3-4-5-12 @ 266 MHz)
      Tipo de BIOS                                      Award (01/23/07)
      Puerto de comunicación                            Puerto de comunicaciones (COM1)
      Puerto de comunicación                            Puerto de impresora (LPT1)

  

    Multimedia:
      Placa de sonido                                   Realtek ALC862 @ Intel 82801GB ICH7 - High Definition Audio Controller [A-1]

    Almacenamiento:
      Controlador IDE                                   Intel(R) 82801G (ICH7 Family) Ultra ATA Storage Controllers - 27DF
      Controlador IDE                                   Intel(R) 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller - 27C0
      Disco rígido                                      Generic USB CF Reader USB Device
      Disco rígido                                      Generic USB MS Reader USB Device
      Disco rígido                                      Generic USB SD Reader USB Device
      Disco rígido                                      Generic USB SM Reader USB Device
      Disco rígido                                      WDC WD3200AAKS-00L9A0  (298 GB, IDE)
      Disco óptico                                      HL-DT-ST DVD-RAM GSA-H54N  (DVD+R9:10x, DVD-R9:10x, DVD+RW:18x/8x, DVD-RW:18x/6x, DVD-RAM:12x, DVD-ROM:16x, CD:48x/32x/48x DVD+RW/DVD-RW/DVD-RAM)
      Estado SMART de los discos rígidos                OK

    Particiones:
      C: (NTFS)                                         90577 MB (85073 MB libre)
      D: (NTFS)                                         209.6 GB (11.1 GB libre)
      Tamaño total                                      298.1 GB (94.2 GB libre)

   
    
      Módem                                             Smart Link 56K Voice Modem

    Periféricos:
      Controlador USB1                                  Intel 82801GB ICH7 - USB Universal Host Controller [A-1]
      Controlador USB1                                  Intel 82801GB ICH7 - USB Universal Host Controller [A-1]
      Controlador USB1                                  Intel 82801GB ICH7 - USB Universal Host Controller [A-1]
      Controlador USB1                                  Intel 82801GB ICH7 - USB Universal Host Controller [A-1]
      Controlador USB2                                  Intel 82801GB ICH7 - Enhanced USB2 Controller [A-1]
      Dispositivo USB                                   Dispositivo de almacenamiento masivo USB
      Dispositivo USB                                   Pirelli - Discus™ Modem

    DMI:
      DMI Fabricante del BIOS                           Phoenix Technologies, LTD
      DMI Versión del BIOS                              6.00 PG
      DMI Fabricante del sistema                        Biostar
      DMI Nombre del sistema                            945GZ Micro 775 SE
      DMI Versión del sistema                           
      DMI Número de serie del sistema                   
      DMI UUID del sistema                              001921D9-A42CFFFF-FFFFFFFF-FFFFFFFF
      DMI Fabricante del motherboard                    Biostar
      DMI Nombre del motherboard                        945GZ Micro 775 SE
      DMI Versión del motherboard                       
      DMI Número de serie del motherboard               
      DMI Fabricante del chasis                         Biostar
      DMI Versión del chasis                            
      DMI Número de serie del chasis                    
      DMI Identificador del chasis                      
      DMI Tipo de chasis                                Desktop Case
      DMI Sockets de memoria Total / Libres             4 / 3






---

### Post by albandy on 2012-04-19
Descarga wubi de esta dirección y ejecútalo.

[http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)

De todas formas, es importante que la máquina donde estés instalando Ubuntu a través de wubi tenga conexión a internet.

---

### Post by guillermolisi on 2012-04-19
Siempre pero siempre, sea con Wubi o condoble inicio (Dual boot) es recomendable defragmentar las particiones que tenga el disco y que esten utilizadas por Windows.

Que version de Ubuntu estas queriendo instalar ?
Por que con Wubi ? No podes hacer espacio en el disco rigido para instalar Ubuntu sin necesidad de que este corriendo Windows ?

---

### Post by mhistral5 on 2012-04-19
> Descarga wubi de esta dirección y ejecútalo.

[http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)

De todas formas, es importante que la máquina donde estés instalando Ubuntu a través de wubi tenga conexión a internet. ya lo baje y me volvio a pasar lo mismo, gracias de todos modos, se ve que el problema no es el ejecutable



> Siempre pero siempre, sea con Wubi o condoble inicio (Dual boot) es  recomendable defragmentar las particiones que tenga el disco y que esten  utilizadas por Windows.

Que version de Ubuntu estas queriendo instalar ?
Por que con Wubi ? No podes hacer espacio en el disco rigido para instalar Ubuntu sin necesidad de que este corriendo Windows ?     

gracias por el consejo pero ya desfrgamente el disco dos veces y me sigue saliendo ese problema, entre a otro foro donde me recomiendan que lo instale en el disco duro completo en vez de compartido con el window, ( quiero instalar la ultima version que baje de la pagina oficial de Ubuntu), pero tambien lo realice desde la bios o sea reinicie la maquina y quise instalarlo en el disco c, pero tampoco se puede se queda la pantalla rosada y mas nada, nose ES TAN DIFICIL INSTALAR UN SISTEMA OPERATIVO COMO LINUX'¿?????????????????????????



NO TE ENTENDI ESA PARTE DE "HACER ESPACIO EN EL DISCO RIGIDO PARA INSTALAR UBUNTU SIN NECESIDAD DE QUE ESTE CORRIENDO WINDOW"


COMO TENDRIA QUE HACER??????? 


GRACIAS DESDE Ya................. debo ser el unico tipo en el mundo que no puede instalar Linux en una simple computadora

---

### Post by guillermolisi on 2012-04-20
Para saber si hay alguna cuestion a resolver con el hardware, primero iniciar la maquina desde el CD/pendrive en modo Live, es decir, sin instalar Ubuntu.

Si todo funciona bien, entonces se puede encarar una instalacion.
Si hay algun componente, audio, red inalambrica, video, etc., que no funcione adecuadamente, hay que ver de que se trata porque eso condiciona los pasos a realizar durante o despues de haber instalado.

La instalacion de Ubuntu utilizando Wubi no es una instalacion limpia porque es como que Ubuntu queda inserto, como una aplicacion mas de Windows. A eso me referia cuando hice el comentario sobre instalar Ubuntu sin necesidad de que este corriendo Windows.

Para ello, ademas de defragmentar, el asistente de la instalacion te brinda tres opciones de las cuales una de ellas es instalar Ubuntu "al lado" de Windows.

Este tipo de instalacion requiere que el particionador del disco rigido reduzca el tamaño de una particion (si no hay espacio libre) o marque una nueva particion (si hay espacio libre disponible a tal efecto) para instalar ahi Ubuntu y luego elegir si se inicia la PC con uno u otro sistema operativo (esto es dual boot).

Esta operacion a veces requiere de una minima intervencion del usuario, por lo menos para decidir que alternativa debe seguir el instalador, cuanto espacio se quiere lograr para Ubuntu o en que particion del disco instalarlo.

Verifica que en modo Live funcione todo bien y despues vemos como seguimos.

---

