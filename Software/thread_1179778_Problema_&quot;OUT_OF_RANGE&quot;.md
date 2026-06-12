---
title: "Problema &quot;OUT OF RANGE&quot;"
date: 2009-06-06
forum: Software
---

### Post by pablocerg on 2009-06-06
Buenas, el año pasado intente instalar ubuntu 8.04 y se me dio el problema que al iniciar el live o la instalación se me apagaba el monitor y salia "OUT OF RANGE". Busque ayuda, no la encontré.

Cuando me enteré que salió ubuntu 9.04 me dio ganas de volver a probar aver si tenía algún arreglo... Me sucedió lo mismo, entonces bajé el instalador alternativo (texto), con este pude instalarlo, pero cuando reinició y estaba iniciando me paso el mismo problema.

Ahora quisiera saber si alguien tiene una solución, mi placa de video es GeForce 8400GS

Si necesitan algún otro dato avisenme.

Un saludo

---

### Post by staar on 2009-06-06
claro que tiene solución, y es muy simple, pero necesitaríamos saber el modelo de tu monitor para poder ayudarte...

saludos

---

### Post by pablocerg on 2009-06-06
> **staar said:**
> claro que tiene solución, y es muy simple, pero necesitaríamos saber el modelo de tu monitor para poder ayudarte...

saludos

Muchas gracias por responder rápido, lo aprecio.
Bueno por everest encontre estos datos (No tengo idea, me enchufaron este monitor dentro de una promoción)


Propiedades del monitor	
Nombre del monitor:	Monitor Plug and Play [NoDB]
Identificación del monitor:	HPC1998
Fecha de fabricación:	Semana 42 / 2004
Número de serie:	144252512782
Tamaño de visión máximo:	36 cm x 27 cm (17.7")
Ratio de aspecto de la imagen:	4:3
Frecuencia horizontal:	30 - 98 KHz
Frecuencia vertical:	50 - 160 Hz
Gamma:	2.60
Gestión del modo DPMS:	Standby, Suspend, Active-Off

Si necesitas algún otro dato avisame, voy a hacer lo posible por encontrar los papeles

---

### Post by staar on 2009-06-06
bien, esos datos son los que quería, ahora iniciá ubuntu, al terminar de cargar, cuando te queda en 'Out of Range' apretá Ctrl + Alt + F1 para cambiarte a una consola, ahí te logueas con tu usuario (al tipear tu pass, no se muestra nada en pantalla, no te asustes, es el comportamiento normal, por seguridad, igual está escribiendo) después ponés ```
sudo nano /etc/X11/xorg.conf
``` para editar el archivo de configuración del servidor gráfico, andá hasta la sección Monitor y dejala exactamente así ```

Section "Monitor"
Identifier "Configured Monitor"
HorizSync 30.0 - 98.0
VertRefresh 50.0 - 160.0
EndSection
``` guardá con Ctrl + o, Enter, salí de nano con Ctrl + x, reiniciá con ```
sudo reboot
``` y contá si funcionó...

saludos

---

### Post by pablocerg on 2009-06-06
Gracias, pero me quedo una duda, si quiero iniciar el live cd también puedo hacer eso?

---

### Post by guisheca on 2009-06-06
Con el live-cd no lo vas a poder hacer lamentablemente. Porque los pasos que te indicaron implican a edición de archivos de sistema. Al ser un CD, los datos son de "sólo lectura" y no lo vas a poder modificar.

---

### Post by pablocerg on 2009-06-06
> **guisheca said:**
> Con el live-cd no lo vas a poder hacer lamentablemente. Porque los pasos que te indicaron implican a edición de archivos de sistema. Al ser un CD, los datos son de "sólo lectura" y no lo vas a poder modificar.

Entonces la única opción que tengo es instalar el alternativo?

Edito:
Y si lo instalo dentro de windows con el cd de ubuntu?
Porque por el momento voy a usar los 2 so

---

### Post by pablocerg on 2009-06-06
Disculpen que levante el post, necesito la respuesta por favor.

gracias

---

### Post by Hei Ku on 2009-06-06
Cualquiera de las dos opciones te permite hacer doble boot. Personalmente, me inclino por el alternate, pero la instalacion desde dentro de Windows, con Wubi, es mas facil.

---

### Post by jo4kkin on 2012-05-29
yo acabo de instalar ubuntu 12.04 en mi pc y me aparece el mensaje de out of range mi monitor es LG 

Display Devices
---------------
          Card name: NVIDIA GeForce 6150SE nForce 430 (Microsoft Corporation - WDDM)
       Manufacturer: NVIDIA
          Chip type: GeForce 6150SE nForce 430
           DAC type: Integrated RAMDAC
         Device Key: Enum\PCI\VEN_10DE&DEV_03D0&SUBSYS_D0001458&REV_A2
     Display Memory: 793 MB
   Dedicated Memory: 57 MB
      Shared Memory: 735 MB
       Current Mode: 1600 x 900 (32 bit) (60Hz)
       Monitor Name: Monitor PnP genérico
      Monitor Model: W2043
         Monitor Id: GSM4E9D
        Native Mode: 1600 x 900(p) (60.000Hz)
        Output Type: HD15
        Driver Name: nvd3dumx.dll,nvd3dum,nvwgf2umx.dll, nvwgf2um


GRACIAS DE ANTEMANO  :)

---

### Post by gmunioz on 2012-06-08
Prueba crear el archivo como te indican con los datos de tu monitor.
ModelName "LG W2043" 
HorizSync 30.0 - 83.0 
VertRefresh 56.0 - 75.0

---

