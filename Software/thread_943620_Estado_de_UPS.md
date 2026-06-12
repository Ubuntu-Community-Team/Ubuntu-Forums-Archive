---
title: "Estado de UPS"
date: 2008-10-10
forum: Software
---

### Post by MeduZa on 2008-10-10
Hola, estoy trabajando en un proyecto y necesito saber como hace el Power manager para conseguir la inforacion sobre la bateria o el USP, estuve buscando en internet y no consigo nada.
buscando en el sistema encontre esto:
/acpi$ ls
ac_adapter  battery  dsdt                 event  fan   power_resource  sleep         video
alarm       button   embedded_controller  fadt   info  processor       thermal_zone  wakeup
pero ahi no hay nada, o esta vacio el directorio o obtengo un permiso denegado cosa que es inutil ya que mi programa correria con permisos de usuario.
para que entiendan mejor de lo que hablo dejo unas capturas
captura1: el estado normal, te dice que hay un UPS y que esta xxx% cargado (en este caso 100%) pero podria decir cargando 80%
captura2: (le pegue una desenchufada a la pc) me dice que paso (cable de energia desenchufado)

¿alguien sabe de donde saco esa informacion?

---

### Post by Mauro22 on 2008-10-10
Te tiro lo que fui encontrando:

[http://www.basicallytech.com/blog/index.php?/archives/110-Colour-coded-battery-charge-level-and-status-in-your-bash-prompt.html](http://www.basicallytech.com/blog/index.php?/archives/110-Colour-coded-battery-charge-level-and-status-in-your-bash-prompt.html)

[http://www.go2linux.org/laptop-battery-status-with-linux-console-command-acpi](http://www.go2linux.org/laptop-battery-status-with-linux-console-command-acpi)

[http://ubuntuforums.org/showthread.php?t=932329](http://ubuntuforums.org/showthread.php?t=932329)

PDF: [http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/pdf/Battery-Powered.pdf](http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/pdf/Battery-Powered.pdf)

Y:

```

                          I generally have a simple prompt, since I'm not interested in flashy colours. I do like to keep track of the battery status on my laptop though, so I wrote this bash function to do so: 
                                                  # DeeK's funky function to calculate battery status.
                        readbatt() {
                          capacity=`awk '/last full capacity:/ { print $4 }' /proc/acpi/battery/BAT0/info`
                          remaining=`awk '/remaining capacity:/ { print $3 }' /proc/acpi/battery/BAT0/state`
                          charging=`awk '/charging state:/ { print $3 }' /proc/acpi/battery/BAT0/state`
                          test "$remaining" == "" && return
                          test "$capacity" == "" && echo "BattErr" && return
                          test "$charging" == "charged" && return
                          if test "$remaining" -le "$capacity"; then
                            echo "[$((remaining*100/capacity))%]:";
                          #else echo "[battery full]:"
                          fi
                        }
                                                  Just add this to the end of your .bashrc file, and put the string `readbatt` somewhere into your PS1 var. Include the backticks! 
                          If you want a battery full message, uncomment the 'else' line. I generally prefer to see nothing if the battery is full, hence why I've commented it out. 
                          I'm sure someone will find this as useful as I have. It's a good reminder for those times that I've accidentally left the power unplugged from the laptop. 


```

Sacado de: [http://technocrat.net/d/2007/6/11/21373](http://technocrat.net/d/2007/6/11/21373)






Saludos!! y espero que te sirva

---

### Post by MeduZa on 2008-10-10
Gracias por responder, si eso tambien lo vi pero en el /proc/acpi/ no tengo nada:
> meduza@Xenoid:/proc/acpi$ ls -R
.:
ac_adapter  button               event  info            sleep         wakeup
alarm       dsdt                 fadt   power_resource  thermal_zone
battery     embedded_controller  fan    processor       video

./ac_adapter:

./battery:

./button:
power

./button/power:
PWRB  PWRF

./button/power/PWRB:
info

./button/power/PWRF:
info

./embedded_controller:

./fan:
FAN

./fan/FAN:
state

./power_resource:

./processor:
CPU0  CPU1

./processor/CPU0:
info  limit  power  throttling

./processor/CPU1:
info  limit  power  throttling

./thermal_zone:
THRM

./thermal_zone/THRM:
cooling_mode  polling_frequency  state  temperature  trip_points

./video:

es mas la mayoria de las cosas dentro de acpi o no dicen nada o no me dejan entrar, lo que me lleva a la conclusion que ahi no es donde tengo que mirar y que ahi tampoco mira el medidor ese, o sea un UPS no es una "bateria" sino otra cosa y no se donde encontrarla U_U

PD: me olvide decir que mi pc NO ES LAPTOP es DESKTOP con UPS.

---

### Post by Mauro22 on 2008-10-10
Y algo onda asi 

sudo ls -R / | grep battery 

:confused::confused:


Eso te tendria que tirar todo lo que sea battery dentro de /

---

### Post by MeduZa on 2008-10-10
> **Mauro22 said:**
> Y algo onda asi 

sudo ls -R / | grep battery 

:confused::confused:


Eso te tendria que tirar todo lo que sea battery dentro de /

estoy buscando, pero nada :S

mira lo que dice lsusb -v:
> 
Bus 001 Device 002: ID 0764:0501 Cyber Power System, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x0764 Cyber Power System, Inc.
  idProduct          0x0501 
  bcdDevice            0.01
  iManufacturer           3 
  iProduct                1 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower               50mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode           33 US
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     346
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
cannot read device status, Operation not permitted (1)

con sudo device status solo dice self powered -.-

---

### Post by Mauro22 on 2008-10-10
Probaste con lshal ?


Te va a convenir volcarlo a un archivo para leerlo porque se hace largo

```
lshal > lshal.txt
```


En /sys/class/power_supply no tenes BAT0 o algo asi?

---

### Post by MeduZa on 2008-10-10
> **Mauro22 said:**
> Probaste con lshal ?


Te va a convenir volcarlo a un archivo para leerlo porque se hace largo

```
lshal > lshal.txt
```


En /sys/class/power_supply no tenes BAT0 o algo asi?

ahi vi valores que parece ser eso!!

ahora si, yo busque por hal pero no sabia que buscar :(

mira la salida:
udi = '/org/freedesktop/Hal/devices/usb_device_764_501_noserial_if0_hiddev'
  battery.charge_level.current = 100  (0x64)  (int)
  battery.charge_level.design = 100  (0x64)  (int)
  battery.charge_level.last_full = 100  (0x64)  (int)
  battery.charge_level.percentage = 100  (0x64)  (int)
  battery.charge_level.unit = 'percent'  (string)
  battery.is_rechargeable = true  (bool)
  [COLOR="Red"]battery.model = 'UPS AE550'  (string)
  battery.present = true  (bool)
  battery.rechargeable.is_charging = false  (bool)
  battery.rechargeable.is_discharging = false  (bool)[/COLOR]
  battery.remaining_time = 690  (0x2b2)  (int)[/COLOR] < esto son segundos
  battery.reporting.current = 100  (0x64)  (int)
  battery.reporting.design = 100  (0x64)  (int)
  battery.reporting.last_full = 100  (0x64)  (int)
  battery.reporting.percentage = 100  (0x64)  (int)
  battery.reporting.technology = 'PbAcid'  (string)
  battery.reporting.unit = 'percent'  (string)
  battery.serial = 'AEB5101.G1X'  (string)
  battery.technology = 'unknown'  (string)
  battery.type = 'ups'  (string)
  battery.vendor = 'CPS'  (string)
  hiddev.application_pages = {'Power
    [21:54:38] Device Page'} (string list)
  hiddev.device = '/dev/usb/hiddev0'  (string)
  hiddev.product = 'CPS UPS AE550'  (string)
  info.addons = {'hald-addon-hid-ups'} (string list)
[COLOR="Red"]  info.capabilities = {'hiddev', 'battery'} (string list)
  info.category = 'hiddev'  (string)[/COLOR]
  info.parent = '/org/freedesktop/Hal/devices/usb_device_764_501_noserial_if0'  (string)
  info.product = 'CPS UPS AE550'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_764_501_noserial_if0_hiddev'  (string)
  linux.device_file = '/dev/usb/hiddev0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.0/usb1/1-7/1-7:1.0/usb/hiddev0'  (string)

creo que con eso estaria echo de momento ahora me toca investigar como lo diferencio en diferentes sistemas :P
calculo que lo voy a acceder por dbus a esos valores. no me gusta parcear.
gracias!!

---

### Post by MeduZa on 2008-10-10
fui a la otra pc y no es tan dificil diferenciarlo, por cada sistema de baterias te tira una informacion diferente asi que creo que el tema ahora vendria por que tanto me quiero matar en leer la informacion xD

gracias !

---

### Post by Mauro22 on 2008-10-11
Ahi ya tenes todo

battery.charge_level.current = 100  (0x64)  (int)
  battery.charge_level.percentage = 100  (0x64)  (int)
  battery.charge_level.unit = 'percent'  (string)
  battery.is_rechargeable = true  (bool)

current level
percentage
y la booleana si esta recargando o no

---

### Post by MeduZa on 2008-10-11
> **Mauro22 said:**
> Ahi ya tenes todo

battery.charge_level.current = 100  (0x64)  (int)
  battery.charge_level.percentage = 100  (0x64)  (int)
  battery.charge_level.unit = 'percent'  (string)
  battery.is_rechargeable = true  (bool)

current level
percentage
y la booleana si esta recargando o no

si y si se esta descargando o no, me fije en la otra pc y me toma las 2 baterias, es increible hasta sabe de que estan echas las baterias xD
esta es de acido y la de la laptop es de li ion.

---

