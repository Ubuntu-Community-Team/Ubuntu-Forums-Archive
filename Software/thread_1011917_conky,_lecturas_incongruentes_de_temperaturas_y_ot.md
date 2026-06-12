---
title: "conky, lecturas incongruentes de temperaturas y otros malestares"
date: 2008-12-15
forum: Software
---

### Post by granjero on 2008-12-15
buenas gente, les comento lo que me pasó... hace una semana más o menos en dos ocasiones distintas separadas por más o menos 2 días mi pc se reinició tirando luego un error de temperatura durante el booteo... en el bios en la sección "harware monitor" decía que el CPU estaba a 102ºC lo cual me pareció una locura. 

abrí el gabinete y toque el disipador del cpu  y estaba calentito pero no quemaba al tacto...

leyendo y leyendo vi que para monitorear las temp del cpu recomendaban usar conky.
con un poco de tiempo y toqueteo logre armarme mi conky...
aca se los dejo...


>     background yes
    use_xft yes
    xftfont AlMateen:size=10
    xftalpha 0.5
    update_interval 1
    total_run_times 0
    own_window yes
    own_window_hints skip_taskbar
    own_window_type normal
    own_window_transparent no
    double_buffer yes
    draw_shades no
    draw_outline yes
    draw_borders no
    draw_graph_borders no
    default_color white
    no_buffers yes
    uppercase no
    cpu_avg_samples 1
    override_utf8_locale no

# $alignc direccion IP: ${addr eth0}

TEXT 
$alignc}chip AMD Athlon(tm)64x2 Dual-core 5200+
$alignc}placa madre Asus M3A
$alignc}RAM 2gb
$alignc}Video Nvidia 8600gt
$alignc $sysname 
$alignc $kernel
$alignc $machine
$alignc fecha: ${time %d/%m/%Y}
$alignc hora: ${time %H horas %M minutos %S segundos} 
$alignc velocidad de descarga: ${downspeed eth0} KB/s
$alignc velocidad de subida: ${upspeed eth0} KB/s
$alignc uso del cpu1: ${cpu cpu0}%  
$alignc uso del cpu2: ${cpu cpu1}%

$alignc TEMPERATURAS bizarras

$alignc k8temp-pci-00c3 
$alignc /sys/bus/pci/drivers/k8temp/0000:00:18.3

$alignc temp1_input: ${execi 1 cat /sys/bus/pci/drivers/k8temp/0000:00:18.3/temp1_input | cut -c1,2} C  
$alignc temp2_input: ${execi 1 cat /sys/bus/pci/drivers/k8temp/0000:00:18.3/temp2_input | cut -c1,2} C  
$alignc temp3_input: ${execi 1 cat /sys/bus/pci/drivers/k8temp/0000:00:18.3/temp3_input | cut -c1,2} C  
$alignc temp4_input: ${execi 1 cat /sys/bus/pci/drivers/k8temp/0000:00:18.3/temp4_input | cut -c1,2} C

$alignc it8716-isa-0e80 /
$alignc sys/bus/platform/drivers/it87/it87.3712

$alignc temp1_input: ${execi 1 cat /sys/bus/platform/drivers/it87/it87.3712/temp1_input | cut -c1,2} C
$alignc temp2_input: ${execi 1 cat /sys/bus/platform/drivers/it87/it87.3712/temp2_input | cut -c1,2} C
$alignc temp3_input: ${execi 1 cat /sys/bus/platform/drivers/it87/it87.3712/temp3_input | cut -c1,2} C
 


mi tema es el siguiente... no se todavía a que corresponden las temperaturas que estoy viendo de los sensores **k8temp-pci-00c3** e **it8716-isa-0e80** o sea cuál es el del chip, cuál de la placa madre y cuál de la placa de viedo....

y también por que las temperaturas que marca oscilan tan rápido entre los 90ºC y los 10ºC no hay material que se banque esas fluctuaciones constantes....

también tuve lecturas de -1ºC (?)

no sé que hacer. la pc esta en garantía hasta el 7/1/09 o sea que quiero detectar que es lo que falla antes de esa fecha para que me cambien la parte defectuosa si es que hay alguna....


les dejo también unas capturas del conky... en las capturas se ve como varia de 90º a 14º en 4 segundos y otras barbarides...

no hay una especie de youtube pero que levante formato .ogg así capturo la ventana con el deskrecorder y ven realmente los cambios bruscos entre temperaturas muy elevadas y temepraturas bajas?


les agradezco su tiempo!

salud!

---

### Post by chakersito on 2008-12-15
Si ejecutas en consola: ```
sensors
```

Que te te aparece?

---

### Post by granjero on 2008-12-15
chakersito, la salida de sensors que me olvide de poner en el otro post



> jm@pcjm:~$ sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +13.0°C                                    
Core0 Temp:   +4.0°C                                    
Core1 Temp:  +23.0°C                                    
Core1 Temp:   +5.0°C                                    

it8716-isa-0e80
Adapter: ISA adapter
VCore:       +1.33 V  (min =  +0.00 V, max =  +4.08 V)
VDDR:        +3.36 V  (min =  +0.00 V, max =  +4.08 V)
+3.3V:       +0.00 V  (min =  +0.00 V, max =  +4.08 V)
+5V:         +5.05 V  (min =  +0.00 V, max =  +6.85 V)
+12V:       +12.22 V  (min =  +0.00 V, max = +16.32 V)
in5:         +0.00 V  (min =  +0.00 V, max =  +4.08 V)
in6:         +0.00 V  (min =  +0.00 V, max =  +4.08 V)
5VSB:        +6.85 V  (min =  +0.00 V, max =  +6.85 V)
VBat:        +3.31 V
fan1:       3229 RPM  (min =    0 RPM)
fan2:          0 RPM  (min =    0 RPM)
fan3:          0 RPM  (min =    0 RPM)
temp1:       +48.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = thermal diode
temp2:       +31.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = transistor
temp3:       +25.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = transistor
cpu0_vid:   +1.550 V



salud!

---

### Post by MeduZa on 2008-12-16
tengo el mismo chip que vos para los sensores y ahi que acerle ajustes, yo encontre los ajustes de mi motherboard en la pagina de lm-sensors fijate si consegis la tuya o en google, necesotas en sensors.conf para las correcciones de los sensores.

---

### Post by granjero on 2008-12-16
perdón pero no entendí meduza....

gracias igual...

---

### Post by granjero on 2008-12-22
up


salud!

---

### Post by Hei Ku on 2008-12-22
Fijate en esta pagina si aparece algo especifico para tu mother. Quizas tengas que hacerle algun ajuste al lm-sensors

[http://www.lm-sensors.org/wiki/Configurations](http://www.lm-sensors.org/wiki/Configurations)

---

