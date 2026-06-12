---
title: "Configurando conky"
date: 2008-10-25
forum: Software
---

### Post by ramiro_md on 2008-10-25
Gente, hace unos días kabezon me hizo poner conky en mi pc y realmente me gusto xD...el tema es que quiero poner la temperatura del micro y demás...googleando un poco, encontré el conky de un tipo donde tenía los "termometros" que quiero en mi conky, en su archivo .conklrc había puesto algo así:

${alignc}Temperatures
${alignc}CPU: ${color white}${i2c 9191-0290 temp 2}Â°C$color - MB: ${color white}${i2c 9191-0290 temp 1}Â°C

(su conky es vertical, el mio es paralelo al panel superior de gnome) Toqueteando un poco, y sacandole algunas cosas que no me interesaban lo dejé así:

Temperaturas:cpu:${i2c 9191-0290 temp 2}A°C - mb: ${i2c 9191-0290 temp 1}A°C

Pero cuando ejecuto conky no inicia :O en que le estoy herrando ? que toque que no debería ?..con el código original tampoco arranca...espero me den unaidea =), un saludo !

---

### Post by santiagoward2000 on 2008-10-25
Hola!
Probaste abrirlo desde una terminal a ver si te tira algún error?

---

### Post by ramiro_md on 2008-10-25
Sii santi, me re colgue con eso ! el error está al parecer en que no encuentra un directorio: /sys/bus/i2c/devices/9191-0290/temp2_input.
Cómo puedo saber que directorio corresponden a mi dispositivos ?.

---

### Post by c4d0rn4 on 2008-10-25
la verdad no tengo mucha idea, por ahí es tema que te falta instalar algun paquete que interprete los sensores.

En esta guía ( [http://www.quicktweaks.com/2008/09/27/gmail-weather-beauty-right-on-your-ubuntu-desktop/](http://www.quicktweaks.com/2008/09/27/gmail-weather-beauty-right-on-your-ubuntu-desktop/) ) dice que deben instalarse estos paquetes
# To monitor your hard disk and CPU temperature install lm-sensors and hddtemp
# $sudo apt-get install hddtemp
$sudo apt-get install lm-sensors

---

### Post by ramiro_md on 2008-10-25
> **c4d0rn4 said:**
> la verdad no tengo mucha idea, por ahí es tema que te falta instalar algun paquete que interprete los sensores.

En esta guía ( [http://www.quicktweaks.com/2008/09/27/gmail-weather-beauty-right-on-your-ubuntu-desktop/](http://www.quicktweaks.com/2008/09/27/gmail-weather-beauty-right-on-your-ubuntu-desktop/) ) dice que deben instalarse estos paquetes
# To monitor your hard disk and CPU temperature install lm-sensors and hddtemp
# $sudo apt-get install hddtemp
$sudo apt-get install lm-sensors

Gracias man, aún así no funcionó !...probando y probando le saque el 1 y el 2 que siguen al término "temp" y salió andando, pero marca 0ºC de temp jejeje ya me voy acercando xD

---

### Post by santiagoward2000 on 2008-10-25
La verdad que estoy medio perdido con eso del "i2c 9191-0290". Por lo que leí es un bus de comunicaciones que puede tirar ese tipo de info, como temperatura, pero no tengo ni idea del tema, asíque prefiero no hablar mucho.
Si tu máquina es compatible con acpi podés usar **acpitemp**. Pero mejor que alguien que sepa algo más te explique cómo es el tema este...
Suerte!

---

### Post by chakersito on 2008-10-26
Ramiro, consulta, cuando ejecutas "sensors" que te devuelve el comando? Y para encontrar tus dispositivos fijate en /sys/bus/platform/drivers/

Por ejemplo en mi .conkyrc para la temperatura del micro arme esta linea:

```
CPU Temp: ${execi 2 cat /sys/bus/platform/drivers/w83627hf/w83627hf.656/hwmon/hwmon1/device/temp2_input | cut -c1,2} C
```


Saludos.

Hugo

---

### Post by ramiro_md on 2008-10-26
Chakersito, el comando me devuelve:
```
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +13.0°C                                    
Core0 Temp:   +9.0°C                                    
Core1 Temp:  +10.0°C                                    
Core1 Temp:  +16.0°C 
```
Probé cambiando el "i2c 9191-0290" por el "k8temp-pci-00c3" y nada :S. Con respecto al directorio de los dispositivos, tampoco, nada de nada :S...UN saludo.

---

### Post by chakersito on 2008-10-26
Fijate en este directorio:
/sys/bus/pci/drivers/k8temp/
Tenes que tener ahi adentro una carpeta con el nombre que empieza con "0000" (Ej: 0000:000:18.1)

Saludos.

Hugo

---

### Post by ramiro_md on 2008-10-26
Hugo encontré la carpeta :) el nombre es "0000:000:18.1" y lo reemplaze en la config de conky de esta forma: "${k8temp-pci-0000:000:18.3 temp 1}°C". Cuando inicio conky en vez de aparecerme la temperatura, aparece "${k8temp-pci-0000:000:18.3 temp 1}°C" ¿se entiende? :confused:. Un saludo y gracias.

---

### Post by ramiro_md on 2008-10-26
Ya pude poner la temperatura del micro (${acpitemp})..ahora me gustaría meter la del motherboard y la placa de video, asique voy a seguir leyendo, si alguien sabe como, postee :)

---

### Post by santiagoward2000 on 2008-10-26
Acá tenés las variables que vienen ya definidas en conky:
[http://conky.sourceforge.net/variables.html]("http://conky.sourceforge.net/variables.html")
Pero no encontré una para el mother... Puede que tengas que buscar algún script para eso.

---

### Post by ramiro_md on 2008-10-26
Gracias santi, ya la había visitado esa página, y encontré algunas variables copadas pero no muchas de las que busco. Un saludo.

---

### Post by Bruce M. on 2008-10-27
> **c4d0rn4 said:**
> la verdad no tengo mucha idea, por ahí es tema que te falta instalar algun paquete que interprete los sensores.

En esta guía ( [http://www.quicktweaks.com/2008/09/27/gmail-weather-beauty-right-on-your-ubuntu-desktop/](http://www.quicktweaks.com/2008/09/27/gmail-weather-beauty-right-on-your-ubuntu-desktop/) ) dice que deben instalarse estos paquetes
# To monitor your hard disk and CPU temperature install lm-sensors and hddtemp
# $sudo apt-get install hddtemp
$sudo apt-get install lm-sensors

Si ...con: hddtemp y lm-sensors ... y:

```
bruloo@bruloo:~$ sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +57.0°C                                    

w83627thf-isa-0290
Adapter: ISA adapter
VCore:       +1.39 V  (min =  +0.70 V, max =  +1.87 V)
+12V:       +12.52 V  (min =  +9.18 V, max =  +0.24 V)
+3.3V:       +3.14 V  (min =  +1.47 V, max =  +3.98 V)
+5V:         +4.91 V  (min =  +5.97 V, max =  +4.59 V)
-12V:       -11.87 V  (min = -13.10 V, max = -13.59 V)
V5SB:        +5.03 V  (min =  +1.10 V, max =  +1.96 V)
VBat:        +3.01 V  (min =  +1.01 V, max =  +3.09 V)
fan1:          0 RPM  (min = 168750 RPM, div = 2)
CPU Fan:       0 RPM  (min =   -1 RPM, div = 8)
fan3:       4963 RPM  (min = 9926 RPM, div = 2)
**M/B Temp:    +38.0°C**  (high = +28.0°C, hyst =  +8.0°C)  sensor = thermistor
CPU Temp:    +51.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
temp3:       +21.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
cpu0_vid:   +0.000 V
beep_enable:enabled

bruloo@bruloo:~$ 
```
Con mi datos arriba:
```
${alignr 2}${color4}M/B: ${execpi 8 sensors | grep 'M/B Temp' | cut --characters 15-16 | xargs ~/Conky/scripts/ColorTempMB.sh}°$color
```
y **ColorTempMB.sh**
```
#!/bin/bash
# colorize.sh

COOL=60
WARM=70

if [[ $1 < $COOL ]]
   then echo "\${color7}"$1    # COOL
elif [[ $1 > $WARM ]]
   then echo "\${color9}"$1    # HOT
else echo "\${color8}"$1       # WARM
fi

exit 0
```
ver attached!

> **ramiro_md said:**
> Ya pude poner la temperatura del micro (${acpitemp})..ahora me gustaría meter la del motherboard y la placa de video, asique voy a seguir leyendo, si alguien sabe como, postee :)

Es siempre: 22°C - no se ¡porque!

> **santiagoward2000 said:**
> Acá tenés las variables que vienen ya definidas en conky:
[http://conky.sourceforge.net/variables.html]("http://conky.sourceforge.net/variables.html")
Pero no encontré una para el mother... Puede que tengas que buscar algún script para eso.

Con hddtemp y lm-sensors vas a tener todo que lo necesitas 

Perdone por mi castellano, estoy aprendiendo!
Chimo!
Bruce

---

### Post by santiagoward2000 on 2008-10-27
Hola Bruce!
¿El script **ColorTempMB.sh** hace que cambie el color dependiendo de la temperatura?
MUY BUENO!

---

### Post by Bruce M. on 2008-10-27
> **santiagoward2000 said:**
> Hola Bruce!
¿El script **ColorTempMB.sh** hace que cambie el color dependiendo de la temperatura?
MUY BUENO!

Hola santiagoward2000 - tanto tiempo!

Si ... "lightblue" (cool), "yellow" (warm) y "red" (hot) (en mi caso)

[CENTER][[IMG]http://img528.imageshack.us/img528/392/20oct08et8.th.gif[/IMG]](http://img528.imageshack.us/my.php?image=20oct08et8.gif)[/CENTER]

Lo encontré: Post your .conkyrc files w/ screenshots - No lo escribí.

Tengo mas:

ColorUseNet.sh
ColorUseHDD.sh
ColorUseCPU.sh
ColorTempMB.sh
ColorTempHDD.sh
ColorTempGPU.sh
ColorTempCPU.sh
ColorTempCore.sh
ColorFreeHDD.sh
ColorCapHDD.sh

Los numeros para COOL y WARM cambia por cada uno depende en su equipo

Chimo!
Bruce

---

### Post by santiagoward2000 on 2008-10-27
> **Bruce M. said:**
> Lo encontré: Post your .conkyrc files w/ screenshots - No lo escribí.

Tengo mas:

ColorUseNet.sh
ColorUseHDD.sh
ColorUseCPU.sh
ColorTempMB.sh
ColorTempHDD.sh
ColorTempGPU.sh
ColorTempCPU.sh
ColorTempCore.sh
ColorFreeHDD.sh
ColorCapHDD.sh

Los numeros para COOL y WARM cambia por cada uno depende en su equipo

Chimo!
Bruce

Bruce, ¿podrías poner el link donde están todos esos scripts? Me interesa ver algunos :)

PS: Va mejorando tu castellano! :D

---

### Post by Bruce M. on 2008-10-27
> **santiagoward2000 said:**
> Bruce, ¿podrías poner el link donde están todos esos scripts? Me interesa ver algunos :)

PS: Va mejorando tu castellano! :D

Enserio!  Buen, me alegro!

Todos son iguales excepto los números pero, los links comienzan [aquí]("http://ubuntuforums.org/showpost.php?p=5936990&postcount=3877") ... [y]("http://ubuntuforums.org/showpost.php?p=5936363&postcount=3873") ... [y]("http://ubuntuforums.org/showpost.php?p=5941789&postcount=3896") ... [y estoy pensando]("http://ubuntuforums.org/showpost.php?p=5941846&postcount=3898") ... [y el fin]("http://ubuntuforums.org/showpost.php?p=5941882&postcount=3899")

Entonces, el mismo script, con nombres diferente, y cambiar los números por COOL & WARM.

Mira:
```
${alignc}${color7}<= ${color8}Temperataures ${color9}=>$color
${color4}CPU: ${color5}${execpi 8 sensors | grep 'CPU Temp' | cut --characters 15-16 | xargs **~/Conky/scripts/ColorTempCPU.sh**}°$color${goto 108}${color4}Core: ${execpi 8 sensors | grep 'Core0' | cut --characters 15-16 | xargs **~/Conky/scripts/ColorTempCore.sh**}°$color${alignr 2}${color4}M/B: ${execpi 8 sensors | grep 'M/B Temp' | cut --characters 15-16 | xargs **~/Conky/scripts/ColorTempMB.sh**}°$color
```

Image: [http://ubuntuforums.org/attachment.php?attachmentid=89872&d=1225122037](http://ubuntuforums.org/attachment.php?attachmentid=89872&d=1225122037)

```
COOL=60 # change if required
WARM=70 # change if required
```

Chimo!
Bruce

---

### Post by ramiro_md on 2008-11-09
Tengo un problema al querer "mantener conky por detrás" de todas las ventanas. En el archivo .conkyrc agregué la palabra "above" a una de las líneas quedando algo así: 
"own_window_hints undecorated,sticky,skip_taskbar,skip_pager,above"
La cosa es que funciona, salvo cuando inicia el sistema y carga conky dejandoló por sobre todas las ventanas. Hay algo que no haya especificado en el .conkyrc ?...espero que alguien me de una mano.
Un saludo, y muchas gracias.

---

### Post by santiagoward2000 on 2008-11-09
> **ramiro_md said:**
> Tengo un problema al querer "mantener conky por detrás" de todas las ventanas. En el archivo .conkyrc agregué la palabra "above" a una de las líneas quedando algo así: 
"own_window_hints undecorated,sticky,skip_taskbar,skip_pager,above"
La cosa es que funciona, salvo cuando inicia el sistema y carga conky dejandoló por sobre todas las ventanas. Hay algo que no haya especificado en el .conkyrc ?...espero que alguien me de una mano.
Un saludo, y muchas gracias.

Hola Ramiro!
¿Vos querés que conky quede abajo? Entonces tenés que usar **"below"**. **"above"** lo deja por encima de las otras ventanas.
Saludos!

---

### Post by chakersito on 2008-11-09
> **ramiro_md said:**
> Tengo un problema al querer "mantener conky por detrás" de todas las ventanas. En el archivo .conkyrc agregué la palabra "above" a una de las líneas quedando algo así: 
"own_window_hints undecorated,sticky,skip_taskbar,skip_pager,above"
La cosa es que funciona, salvo cuando inicia el sistema y carga conky dejandoló por sobre todas las ventanas. Hay algo que no haya especificado en el .conkyrc ?...espero que alguien me de una mano.
Un saludo, y muchas gracias.

Mmmm a ver... above = encima... deberías poner bellow (debajo)
```
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below
```

Fijate cambiando la palabra... te debería funcionar.

---

### Post by ramiro_md on 2008-11-09
Tanto como con above y bellow (debí decir que ya estaba así x default, yo cambie luego x above) aca dejo el screen :S. EL screen corresponde a cuando inicia el sistema, repito. Luego cierro conky y vuelvo abrir y ahí si queda como debe (tanto con above como con bellow).

---

### Post by chakersito on 2008-11-09
Podes postear tu conky?

---

### Post by ramiro_md on 2008-11-10
Si, disculpen, lo tendría que haber hecho antes.

```
update_interval 1.0
use_xft yes
xftfont purisia:size=8
alignment top_right
xftalpha 0.8
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,sticky,skip_taskbar,skip_pager,below
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
stippled_borders 0
border_margin 4
border_width 1
default_shade_color grey
default_outline_color black
default_color white
use_spacer none
no_buffers yes
gap_x 5
gap_y 40
uppercase no
color1 F8DF58
minimum_size 200 5
maximum_width 200
 #!/bin/bash
    #
    # requirements: amaroK (!)

    case “$1&#8243; in

    # % progress
    progress)
    stat=`dcop amarok player status`
    if (( $stat == 1 )); then
    expr 100
    else
    curr=`dcop amarok player trackCurrentTime`
    tot=`dcop amarok player trackTotalTime`
    if (( $tot )); then
    expr $curr \* 100 / $tot
    fi
    fi
    ;;
    esac

TEXT
${font purisa:size=10}$alignc GNU/Linux
${font purisa:size=10}$alignc Ubuntu 8.10
${font purisa:size=10}$alignc$nodename
${font purisa:size=10}$alignc Proc: $processes ($running_processes running)
${font purisa:size=10}$alignc Work: $uptime
${font purisa:size=10}$alignc Core 1: ${cpu cpu1}%
${font purisa:size=10}$alignc Core 2: ${cpu cpu2}%
${font purisa:size=10}$alignc Ram: $memperc%
${font purisa:size=10}$alignc Swap: $swapperc%
${font purisa:size=10}$alignc Download: ${downspeed eth0} Kb/s
${font purisa:size=10}$alignc Upload: ${upspeed eth0} Kb/s
${font purisa:size=10}$alignc Escuchando:
${font purisa:size=10}$alignc ${execi 10 dcop amarok player artist}
${font purisa:size=10}$alignc ${execi 10 dcop amarok player title}
```

---

### Post by Bruce M. on 2008-11-10
> **ramiro_md said:**
> Si, disculpen, lo tendría que haber hecho antes.

Como:
```

own_window_hints undecorated,sticky,skip_taskbar,skip_pager

```

---

### Post by ramiro_md on 2008-11-10
Bruce, probe sin especificar below y above. Pero el "problema" persiste. Voy a revisar tu how to, el que tienes en la firma, que según leí está interesante.

---

### Post by c4d0rn4 on 2008-11-10
> **ramiro_md said:**
> Bruce, probe sin especificar below y above. Pero el "problema" persiste. Voy a revisar tu how to, el que tienes en la firma, que según leí está interesante.

como decis que el si se ejecuta después del inicio funciona bien, porque no tratás de iniciarlo con un sleep lo suficientemente largo.

```
sleep 33s && conky
```

medio bestia los 33s pero si anda bien de una, será cuestión de ajustar el tiempo.

---

### Post by ramiro_md on 2008-11-10
GGracias x la data, pero el problema persiste. A lo mejor lo estoy hacinedo mal eso del "sleep", yo lo especifiqué así en el archivo de configuración:
```
#!/bin/bash
sleep 33s && conky
conky -c ~/Conky/conkymain &
#sleep 0 &&
#conky -c ~/Conky/conkyforecast &
```
A lo mejor no es de esta forma je. De todas formas, agradezco los aportes =)

---

### Post by c4d0rn4 on 2008-11-10
> **ramiro_md said:**
> GGracias x la data, pero el problema persiste. A lo mejor lo estoy hacinedo mal eso del "sleep", yo lo especifiqué así en el archivo de configuración:
```
#!/bin/bash
sleep 33s && conky
conky -c ~/Conky/conkymain &
#sleep 0 &&
#conky -c ~/Conky/conkyforecast &
```
A lo mejor no es de esta forma je. De todas formas, agradezco los aportes =)

si usas un archivo sh podés poner

sleep SEGUNDOSs && /carpetas/archivoEjecutable

El sleep fundamentalmente hace que espere un tiempo antes de seguir con el siguiente comando. 

La verdad es un idea que se me ocurre, no suele ser algo atípico usar sleep para ejecutar conky y evitar problemas con programas en el arranque. Fijate en google, conky y sleep

---

### Post by Bruce M. on 2008-11-10
> **c4d0rn4 said:**
> si usas un archivo sh podés poner

sleep SEGUNDOSs && /carpetas/archivoEjecutable

El sleep fundamentalmente hace que espere un tiempo antes de seguir con el siguiente comando. 

La verdad es un idea que se me ocurre, no suele ser algo atípico usar sleep para ejecutar conky y evitar problemas con programas en el arranque. Fijate en google, conky y sleep

Sin **s** --- 33**s** ... como:
```

#!/bin/bash
sleep 10 &&	# 0 good for Xfce - use 10 to 30 for Gnome
conky -c ~/Conky/conkymain &
sleep 10 &&
conky -c ~/Conky/conkyforecast &
```

Chimo!
Bruce

---

### Post by staar on 2008-11-11
tengo el mismo problema que ramiro, probe con below, con above, y sin nada en el conkyrc, uso el script para que se demore la carga y lo mismo, el conky inicia encima, a mi me parece que es cosa del compiz, pero ni idea como arreglarlo...

adjunto mi conkyrc porque es un poco largo...

saludos

---

### Post by chakersito on 2008-11-11
Probaste poner el conky en las Windows Rules de Compiz?

"class=conky"

---

### Post by staar on 2008-11-11
> **chakersito said:**
> Probaste poner el conky en las Windows Rules de Compiz?

"class=conky"

si, ya probe en las windows rules y tambien probe excluirlo en decoracion de ventanas, con class=conky, con class=Conky, y con title=Conky, y con otros, y nada

ahora voy a probar con otro conkyrc a ver si viene por ahi el problema

saludos

---

### Post by staar on 2008-11-11
bueno, logre solucionarlo, al final con el script que lo retarda funciono pero hubo que modificarlo un poquito, tuve que poner 40 segundos de retardo y la linea que inicia conky es diferente, tiene la opcion -d

```
#!/bin/bash
sleep 40 &&
conky -d -c /home/*usuario*/.conkyrc
exit
```

saludos

---

### Post by Bruce M. on 2008-11-11
Por PM, Warper me preguntó:
> Hola Bruce:

¿Podrías poner la configuración de conky de esta captura de pantalla?

[http://ubuntuforums.org/showpost.php?p=6123028&postcount=4400](http://ubuntuforums.org/showpost.php?p=6123028&postcount=4400)

He estado viendo las configuraciones que usas, y me gusta como quedan.

Muchas gracias por anticipado

Bueno: Mi pantalla es: 1280x1024

Para mi conky vas a necesitar:
Fonts: [Zekton]("http://www.dafont.com/search.php?psize=m&q=Zekton"), [OpenLogos]("http://www.dafont.com/search.php?psize=m&q=OpenLogos"), [LCDMono]("http://www.spinwardstars.com/scrfonts/lcdmono.html")

Y, scripts por Kaivalagi:
[LIST=1]
[*][conkyEmail]("http://ubuntuforums.org/showthread.php?t=869771")
[*][conkyForecast]("http://ubuntuforums.org/showthread.php?t=869328"): Lea las instrucciones cuidadosamente
[*][conkyGoogleCalendar]("http://ubuntuforums.org/showthread.php?t=837385")
[/LIST]

y más: por Synaptic: [lm-sensors]("http://ubuntuforums.org/showthread.php?t=2780"), curl, hddtemp, vnstat y más "scripts"

Hay 7 conkys:

**/.startconky**
```
#!/bin/bash
sleep 0 &&	# 0 good for Xfce - use 10 to 30 for Gnome
conky -c ~/Conky/conkymain &
sleep 0 &&
conky -c ~/Conky/conkyforecast &
sleep 0 &&
conky -c ~/Conky/conkyemail &
sleep 0 &&
conky -c ~/Conky/calendar &
sleep 2 &&
conky -c ~/Conky/conkygcal &
sleep 0 &&
conky -c ~/Conky/todo &
sleep 0 &&
conky -c ~/Conky/othersforecast &
```
**conkymain**
```
background no
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_colour lightblue
double_buffer yes
use_spacer left
override_utf8_locale yes
use_xft	yes
font Zekton:size=9
xftfont Zekton:size=9
xftalpha 2.5
update_interval 5.0
uppercase no  # set to yes if you want all text to be in uppercase
stippled_borders 3
border_margin 9
border_width 10
default_outline_color black
default_shade_color black
draw_borders no
draw_outline yes  # amplifies text if yes
draw_shades no  # shadecolor black
default_color white
color0 cyan
color1 lightblue
color2 orange
color3 yellow
color4 wheat
color5 salmon
color6 red
color7 lightblue
color8 yellow
color9 red
alignment bl  # Aligned position on screen: tl, tr, tm, bl, br, bm, ml, mr
gap_x 10
gap_y -200 # -200 for br & 35 for tm
text_buffer_size 512 # use 1024 for the forecast
no_buffers yes  # Subtract file system buffers from used memory?
short_units yes
pad_percents 2

# -------- help ---------------
# Timezone information found in: /usr/share/zoneinfo
# UTC ${utime %H:%M}
# BC: ${tztime Canada/Pacific %H:%M}
# Man: ${tztime Canada/Central %H:%M}
# Ont: ${tztime Canada/Eastern %H:%M}
# Nfld: ${tztime Canada/Newfoundland %H:%M}
# Beijing: ${tztime Asia/Shanghai %H:%M}

#-----------------
#with vnstat first you must create database:
#sudo vnstat -u -i eth0 (change eth0 for your network interface)
#-----------------
#for hddtemp to work in conky:
#sudo chmod u+s /usr/sbin/hddtemp
#-----------------
# Show IF there are files in Trash - ${execi 60 du -sh ~/.local/share/Trash/files/ | awk '{print $1}' | sed '/^4.0K/ d'  | sed 's/$/ of TRASH /'}
# -------- end help ------------

TEXT
${voffset -45}${color7}${font OpenLogos:size=150}v$font$color
${voffset -65}${font Zekton:size=15}${color2}Up time:$color${alignr 2}$uptime_short
${color0}${hr 1}$color
${color2}AMD64:$color${alignc}${font DejaVu Sans Mono:size=9}${freq_dyn_g cpu0}Ghz$font
${alignc}${color7}<= ${color8}Temperataures ${color9}=>$color
${color4}CPU: ${color5}${execpi 8 sensors | grep 'CPU Temp' | cut --characters 15-16 | xargs ~/Conky/scripts/ColorTempCPU.sh}°$color${goto 108}${color4}Core: ${execpi 8 sensors | grep 'Core0' | cut --characters 15-16 | xargs ~/Conky/scripts/ColorTempCore.sh}°$color${alignr 2}${color4}M/B: ${execpi 8 sensors | grep 'M/B Temp' | cut --characters 15-16 | xargs ~/Conky/scripts/ColorTempMB.sh}°$color
${voffset 10}${font DejaVu Sans Mono:size=9}${color2}Process:$color${alignr 2}${color 888888}${cpubar cpu0 14,140}$color
${color4}${voffset -16}${goto 140}$running_processes /$processes${alignr 5}$cpu%$color
${voffset -14}${alignr 2}${color yellow}${cpubar cpu2 14,140}$color
${voffset 5}${color7}Load:		${goto 70}${color3}${loadavg 1}	${goto 140}${loadavg 2}${alignr 5}${loadavg 3}$color
${voffset 5}${color2}RAM:$color${alignr 2}${color 888888}${membar 14,140}$color
${color4}${voffset -16}${goto 140}$mem${alignr 5}$memperc%$color
${voffset -14}${alignr 2}${color yellow}${cpubar cpu3 14,140}$color
${voffset 5}${color7}Buffered:${color3}	${goto 70}${buffers}${alignr 2}${color7}Cached:${color3} ${cached}
${voffset 5}${color2}SWAP:$color${alignr 2}${color 888888}${swapbar 14,140}$color
${color4}${voffset -16}${goto 140}$swap${alignr 5}$swapperc%$font
${voffset -16}${alignr 2}${color yellow}${cpubar cpu4 14,140}$color
${color0}${hr 1}$color
${voffset 5}${color2}HD Info${color7} -$color Free${color7} - Used$color
${voffset 5}${color2}sda: ${color7}<= ${color8}Temp: ${color9}=> ${execpi 8 hddtemp /dev/sda | cut --characters 27-28 | xargs ~/Conky/scripts/ColorTempHDD.sh}°$color
${font DejaVu Sans Mono:size=9}		${goto 25}${color7}Root:$color	${goto 90}${fs_free_perc /}%	${goto 135}${fs_free /}${color2}${alignr 2}${color7}${fs_used /}$color$font
${goto 25}${font DejaVu Sans Mono:size=9}${color7}Home:$color	${goto 90}${fs_free_perc /home/bruloo}%	${goto 135}${fs_free /home/bruloo}${alignr 2}${color7}${fs_used /home/bruloo}$color$font
${voffset 5}${color2}sdb: ${color7}<= ${color8}Temp: ${color9}=> ${execpi 8 hddtemp /dev/sdb | cut --characters 31-32 | xargs ~/Conky/scripts/ColorTempHDD.sh}°$color
${goto 25}${font DejaVu Sans Mono:size=9}${color7}Data:$color	${goto 90}${fs_free_perc /Data}%	${goto 135}${fs_free /Data}${alignr 2}${color7}${fs_used /Data}$color$font
${color0}${hr}$color
${voffset 5}${alignc 2}${color2}IP:  $color${addr eth0}
${color2}Dn:$color${downspeed eth0} k/s ${totaldown eth0}${alignr 2}${color2}Up:$color${upspeed eth0} k/s ${totalup eth0}
${color2}In:  $color${tcp_portmon 1 32767 count}${alignc}${color2}Out:  $color${tcp_portmon 32768 61000 count}${alignr 2}${color2}Total:  $color${tcp_portmon 1 65535 count}
--- As of: 11 Nov. 08 ---
${color2}Today:$color${goto 60}${execi 300 vnstat | grep "today" | awk '{print $2 $3}'}${goto 150}${color2}Today:$color${goto 210}${execi 300 vnstat | grep "today" | awk '{print $5 $6}'}  
${color2}Week:$color${goto 60}${execi 300 vnstat -w | grep "current week" | awk '{print $3 $4}'}${goto 150}${color2}Week:$color${goto 210}${execi 300 vnstat -w | grep "current week" | awk '{print $6 $7}'} 
${color2}Month:$color${goto 60}${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $3 $4}'}${goto 150}${color2}Month:$color${goto 210}${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $6 $7}'}
${color0}${hr}$color
${goto 60}${color9}${font Zekton:size=12}${execi 60 du -sh ~/.local/share/Trash/files/ | awk '{print $1}' | sed '/^4.0K/ d'  | sed 's/$/ of TRASH /'}$font$color
```
**ColorTempHDD.sh**
```
#!/bin/bash
# colorize.sh

COOL=40
WARM=50

if [[ $1 < $COOL ]]
   then echo "\${color7}"$1    # COOL
elif [[ $1 > $WARM ]]
   then echo "\${color9}"$1    # HOT
else echo "\${color8}"$1       # WARM
fi

exit 0
```
**conkyforecast**
```
background no
own_window yes
own_window_type override # normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager # undecorated,below,skip_taskbar,skip_pager
own_window_colour black
double_buffer yes
use_spacer left
override_utf8_locale yes
use_xft	yes
font DejaVu Sans Mono:size=9
xftfont DejaVu Sans Mono:size=9
xftalpha 0.5
update_interval 5.0
uppercase no  # set to yes if you want all text to be in uppercase
stippled_borders 3
border_margin 9
border_width 10
default_outline_color black
default_shade_color black
draw_borders no
draw_outline yes  # amplifies text if yes
draw_shades no  # shadecolor black
default_color white
color0 cyan
color1 lightblue
color2 orange
color3 yellow
color4 wheat
color5 salmon
color6 red
color7 lightblue
color8 yellow
color9 red
alignment br  # Aligned position on screen: tl, tr, tm, bl, br, bm, ml, mr
gap_x -15
gap_y -25 # because of the VOFFSET to get the weather font up to the 2nd day, the negative "gap_y" value brings conky back to the bottom of the screen.
text_buffer_size 6076 # large buffer needed
no_buffers yes  # Subtract file system buffers from used memory?
short_units yes
pad_percents 2

# ${goto 30}${color4}${font Zekton:size=15}Pronóstico de 5 dias$font
# line 25 - start with: ${color4}[--datatype=MP]$color

# Use in template:
#${color8}${goto 50}Norwich${goto 140}Sanford${goto 220}Prague$font$color
#${goto 50}${color8}[--datatype=DW --shortweekday --startday=0]:${color4}[--location=UKXX0103 --datatype=HT --hideunits --hidedegreesymbol]/[--location=UKXX0103 --datatype=LT --hideunits --hidedegreesymbol]${goto 140}${color8}[--datatype=DW --shortweekday --startday=0]:${color4}[--location=USME0356 --datatype=HT --hideunits --hidedegreesymbol]/[--location=USME0356 --datatype=LT --hideunits --hidedegreesymbol]${goto 220}${color8}[--datatype=DW --shortweekday --startday=0]:${color4}[--location=EZXX0012 --datatype=HT --hideunits --hidedegreesymbol]/[--location=EZXX0012 --datatype=LT --hideunits --hidedegreesymbol]
#${goto 50}${color8}Luz:${color4}[--location=UKXX0103 --datatype=DL]${goto 140}${color8}Luz:${color4}[--location=USME0356 --datatype=DL]${goto 220}${color8}Luz:${color4}[--location=EZXX0012 --datatype=DL]

TEXT
${execpi 900 conkyForecast --location=ARBA0009 --template=/home/bruloo/Conky/scripts/myweather.template}
```
**myweather.template**
```
${color4}${font ConkyWeather:size=55}[--datatype=WF]$font$color
${voffset -70}${goto 90}${color7}${font Zekton:size=20}[--datatype=DW --shortweekday --startday=0]:$color [--datatype=HT]
${goto 90}${voffset -10}${font Zekton:size=9}${color7}Sensación térmica: ${color}[--datatype=LT]$font
${goto 15}${voffset 15}${font Zekton:size=10} ${color7}[--datatype=CC]$color$font
${goto 15}${voffset 5}${font ConkyWindN:size=40}${color4}[--datatype=BS]$font
${goto 70}${voffset -45}${color7}Viento: ${color3}[--datatype=WS] ${color7}(${color4}[--datatype=WA]°${color7}) ${color3}[--datatype=WD]
${voffset 5}${goto 70}${color7}Visibilidad:${color3} [--datatype=VI]

${color7}Presión: ${color3}[--datatype=BR] - [--datatype=BD]$color
${color7}Humedad: ${color3}[--datatype=HM]${goto 140}${color7}Precipitación: ${color3}[--datatype=PC]$color
${color7}UV: ${color3}[--datatype=UI] - ${color3}[--datatype=UT]${goto 140}${color7}P. de R.: ${color3}[--datatype=DP]$color$font
${color0}${goto 130}--------------------$color
${goto 130}${color7}[--datatype=DW --shortweekday --startday=1]:${color4}[--datatype=HT --hideunits --hidedegreesymbol --startday=1]/[--datatype=LT --hideunits --hidedegreesymbol --startday=1]${goto 210}${color7}[--datatype=DW --shortweekday --startday=2]:${color4}[--datatype=HT --hideunits --hidedegreesymbol --startday=2]/[--datatype=LT --hideunits --hidedegreesymbol --startday=2]
	${goto 30}${voffset -15}${color3}${font SunNMoon:size=50}n$font$color		${voffset -25}${color3}${font ConkyWeather:size=30}${goto 138}[--datatype=WF --startday=1]${goto 218}[--datatype=WF --startday=2]$font
	${goto 30}${voffset 5}${color0}${font Arrows:size 20}b$font${color3}[--datatype=SR]${goto 130}${color7}Sol:${color4}[--datatype=SR --startday=1]${goto 210}${color7}Sol:${color4}[--datatype=SR --startday=2]
	${goto 30}${color7}Luz:${color3}[--datatype=DL]${goto 130}${color7}   :${color4}[--datatype=SS --startday=1]${goto 210}${color7}   :${color4}[--datatype=SS --startday=2]  
	${goto 30}${color0}${font Arrows:size 20}h$font${color3}[--datatype=SS]${goto 130}${color7}Luz:${color4}[--datatype=DL --startday=1]${goto 210}${color7}Luz:${color4}[--datatype=DL --startday=2]
${color0}${goto 130}--------------------$color
${goto 130}${color7}[--datatype=DW --shortweekday --startday=3]:${color4}[--datatype=HT --hideunits --hidedegreesymbol --startday=3]/[--datatype=LT --hideunits --hidedegreesymbol --startday=3]${goto 210}${color7}[--datatype=DW --shortweekday --startday=4]:${color4}[--datatype=HT --hideunits --hidedegreesymbol --startday=4]/[--datatype=LT --hideunits --hidedegreesymbol --startday=4]
	${goto 30}${color4}${font moon phases:size=50}[--datatype=MF]$font	${voffset -46}${color3}${font ConkyWeather:size=30}${goto 135}[--datatype=WF --startday=3]${goto 215}[--datatype=WF --startday=4]$font$color
${goto 130}${color7}Sol:${color4}[--datatype=SR --startday=3]${goto 210}${color7}Sol:${color4}[--datatype=SR --startday=4]
${goto 130}${color7}   :${color4}[--datatype=SS --startday=3]${goto 210}${color7}   :${color4}[--datatype=SS --startday=4]  
${goto 130}${color7}Luz:${color4}[--datatype=DL --startday=3]${goto 210}${color7}Luz:${color4}[--datatype=DL --startday=4]
${font DejaVu Sans Mono:size=7}${alignc 0}W:[--location=ARBA0009 --datatype=LU] -=- C:[--location=ARBA0009 --datatype=LF]
```
**/.conkyforcast.config**
```
# config settings for conkyForecast.py
CACHE_FOLDERPATH = /home/bruloo/Conky/cache
CONNECTION_TIMEOUT = 5
EXPIRY_MINUTES = 30
TIME_FORMAT = %H:%M
DATE_FORMAT = %Y-%m-%d
LOCALE = es
XOAP_PARTNER_ID = xxxxxxxxxxxx
XOAP_LICENCE_KEY = xxxxxxxxxxxxxxxx
```
**conkyemail**
```
background no
own_window yes
own_window_type override # normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager # undecorated,below,skip_taskbar,skip_pager
own_window_colour black
double_buffer yes
use_spacer left
override_utf8_locale yes
use_xft	yes
font Zekton:size=15
xftfont Zekton:size=15
xftalpha 0.5
update_interval 5.0
uppercase no  # set to yes if you want all text to be in uppercase
stippled_borders 3
border_margin 9
border_width 10
default_outline_color black
default_shade_color black
draw_borders no
draw_outline yes  # amplifies text if yes
draw_shades no  # shadecolor black
default_color white
color0 cyan
color1 lightblue
color2 orange
color3 yellow
color4 wheat
color5 salmon
color6 red
color7 lightblue
color8 yellow
color9 red
alignment tm  # Aligned position on screen: tl, tr, tm, bl, br, bm, ml, mr
gap_x 10
gap_y 35
text_buffer_size 1024 # use 1024 for the forecast
no_buffers yes  # Subtract file system buffers from used memory?
short_units yes
pad_percents 2

# a month calendar - no day names
#${color4}${font LCDMono:size=8}${execpi 60 DKV=`date +%_d`; cal | sed '1d' | sed '1e' | sed '/./!d' | sed 's/^/   /' | sed 's/$/ /' | fold -w 24 | sed -n '/^.\{21\}/p' | sed /" $DKV "/s/" $DKV "/" "'${color6}'"$DKV"'${color4}'" "/}$font$color


TEXT
${alignc}${color7}Hay  ${color3}${execi 60 conkyEmail --servertype=POP --servername=pop3.xxxxxxx.com.ar --username=xxxxx --password=xxxxxxxxxx}  ${color7}E-mail(s)$color
```
**calendar**
```
background no
own_window yes
own_window_type override # normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager # undecorated,below,skip_taskbar,skip_pager
own_window_colour black
double_buffer yes
use_spacer left
override_utf8_locale yes
use_xft	yes
font Zekton:size=8
xftfont Zekton:size=8
xftalpha 2.5
update_interval 5.0
uppercase no  # set to yes if you want all text to be in uppercase
stippled_borders 3
border_margin 9
border_width 10
default_outline_color black
default_shade_color black
draw_borders no
draw_outline yes  # amplifies text if yes
draw_shades no  # shadecolor black
default_color white
color0 cyan
color1 lightblue
color2 orange
color3 yellow
color4 wheat
color5 salmon
color6 red
color7 lightblue
color8 yellow
color9 red
alignment tr  # Aligned position on screen: tl, tr, tm, bl, br, bm, ml, mr
gap_x 10
gap_y 35
text_buffer_size 512 # use 1024 for the forecast
no_buffers yes  # Subtract file system buffers from used memory?
short_units yes
pad_percents 2
# Timezone information found in: /usr/share/zoneinfo


TEXT
${font Zekton:bold:size=12}${color4}${alignc}UTC:$color ${utime %H:%M}
${font Zekton:bold:size=9}${color7}Man: $color${tztime Canada/Central %H:%M}${alignr 2}${color7}Ont: $color${tztime Canada/Eastern %H:%M}$font
${color0}${hr}
${goto 70}${font Zekton:bold:size=9}${color7}Buenos Aires, Argentina$color
${goto 70}${color4}34°20' S${goto 164}58°30' W$color$font
${font LCDMono:size=55}${time %H:%M}$font
${voffset -63}${font Zekton:size=20}${alignr 5}${time %b}$font
${font Zekton:size=20}${alignr 5}${time %y}$font
${color0}${hr 1}$color
${font LCDMono:size=19}${color2}${pre_exec ~/Conky/scripts/calendario.sh semana}
${color 888888}${pre_exec ~/Conky/scripts/calendario.sh pasado}${color2}${pre_exec ~/Conky/scripts/calendario.sh hoy}${color 888888}${pre_exec ~/Conky/scripts/calendario.sh futuro}$font

${color4}${font LCDMono:size=9}${pre_exec cal -3 | cut -c23-44 --complement}
```
**calendario.sh**
```
#! /bin/sh
# written by: jjgomera

#str=`echo '\033[01;32m29'`

# replace the 4 "cal |" with "cal -m |" to have the week start on Monday

DATE=`date | awk -F" " '{print $3}'`

case "$1" in
mes)
cal | head -n1
;;
semana)
cal | head -n2 | tail -n1
;;
pasado)
cal | grep -v '[a-zA-Z]' | grep '[0-9]' | awk -F$DATE ' BEGIN {i=0}
($1 == $0 && i==0) {print $1}($1 != $0 && i==0){i=i+1;print $1}';
;;
hoy)
echo $DATE;
;;
futuro)
cal | grep -v '[a-zA-Z]' | grep '[0-9]' | awk -F$DATE ' BEGIN {i=1}
(i==0) {print $0}($1 != $0 && i==1){i=i-1;print $2}';
;;
esac
```
**conkygcal** - "[Google Calendar]("http://www.google.com/googlecalendar/overview.html")"
```
background no
own_window yes
own_window_type override # normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager # undecorated,below,skip_taskbar,skip_pager
own_window_colour black
double_buffer yes
use_spacer left
override_utf8_locale yes
use_xft	yes
font DejaVu Sans Mono:size=9
xftfont DejaVu Sans Mono:size=9
xftalpha 0.5
update_interval 5.0
uppercase no  # set to yes if you want all text to be in uppercase
stippled_borders 3
border_margin 9
border_width 10
default_outline_color black
default_shade_color black
draw_borders no
draw_outline yes  # amplifies text if yes
draw_shades no  # shadecolor black
default_color white
color0 cyan
color1 lightblue
color2 orange
color3 yellow
color4 wheat
color5 salmon
color6 red
color7 lightblue
color8 yellow
color9 red
alignment tm  # Aligned position on screen: tl, tr, tm, bl, br, bm, ml, mr
gap_x 230
gap_y 35
text_buffer_size 1024 # use 1024 for the forecast
no_buffers yes  # Subtract file system buffers from used memory?
short_units yes
pad_percents 2

TEXT
${font Zekton:size=15}${color7}A g e n d a:$font$color
${voffset 5}${execpi 3600 conkyGoogleCalendar --username=xxxxxxxx@gmail.com --password=xxxxxxxxxxxx --daysahead=5 --limit=15 --timeformat="%H:%M"  --template=/home/bruloo/Conky/scripts/conkyGoogleCalendar.template}
```
**conkyGoogleCalendar.template**
```
${color4}<starttime> ${color7}: ${color0}<title>
```
**todo (ver: Hoy)**
```
background no
own_window yes
own_window_type override # normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager # undecorated,below,skip_taskbar,skip_pager
own_window_colour black
double_buffer yes
use_spacer left
override_utf8_locale yes
use_xft	yes
font Zekton:bold:size=15
xftfont Zekton:bold:size=15
xftalpha 0.5
update_interval 5.0
uppercase no  # set to yes if you want all text to be in uppercase
stippled_borders 3
border_margin 9
border_width 10
default_outline_color black
default_shade_color black
draw_borders no
draw_outline yes  # amplifies text if yes
draw_shades no  # shadecolor black
default_color white
color0 cyan
color1 lightblue
color2 orange
color3 yellow
color4 wheat
color5 salmon
color6 red
color7 yellow
color8 lightblue
color9 red
alignment tm  # Aligned position on screen: tl, tr, tm, bl, br, bm, ml, mr
gap_x -250
gap_y 35
text_buffer_size 1024 # use 1024 for the forecast
no_buffers yes  # Subtract file system buffers from used memory?
short_units yes
pad_percents 2

# a month calendar - no days
#${voffset -0}${color4}${font LCDMono:size=8}${execpi 60 DKV=`date +%_d`; cal | sed '1d' | sed '1e' | sed '/./!d' | sed 's/^/   /' | sed 's/$/ /' | fold -w 24 | sed -n '/^.\{21\}/p' | sed /" $DKV "/s/" $DKV "/" "'${color6}'"$DKV"'${color4}'" "/}$font$color


TEXT
${color2}Hoy$color
${color4}${font DejaVu Sans Mono:size=9}${execi 2 less ~/Documents/todo/todo.txt}$font$color
```
**othersforecast**
```
background no
own_window yes
own_window_type override # normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager # undecorated,below,skip_taskbar,skip_pager
own_window_colour black
double_buffer yes
use_spacer left
override_utf8_locale yes
use_xft	yes
font DejaVu Sans Mono:size=9
xftfont DejaVu Sans Mono:size=9
xftalpha 0.5
update_interval 5.0
uppercase no  # set to yes if you want all text to be in uppercase
stippled_borders 3
border_margin 9
border_width 10
default_outline_color black
default_shade_color black
draw_borders no
draw_outline yes  # amplifies text if yes
draw_shades no  # shadecolor black
default_color white
color0 cyan
color1 lightblue
color2 orange
color3 yellow
color4 wheat
color5 salmon
color6 red
color7 lightblue
color8 yellow
color9 red
alignment br  # Aligned position on screen: tl, tr, tm, bl, br, bm, ml, mr
gap_x 290
gap_y 20 # because of the VOFFSET to get the weather font up to the 2nd day, the negative "gap_y" value brings conky back to the bottom of the screen.
text_buffer_size 6076 # large buffer needed
no_buffers yes  # Subtract file system buffers from used memory?
short_units yes
pad_percents 2

TEXT
${execpi 3600 conkyForecast --template=/home/bruloo/Conky/scripts/others.template}
```
**others.template**
```
${color5}Norwich$color
${color1}Hoy:${color4}[--location=UKXX0103 --datatype=HT --hideunits --hidedegreesymbol]/[--location=UKXX0103 --datatype=LT --hideunits --hidedegreesymbol]
${color1}Luz:${color4}[--location=UKXX0103 --datatype=DL]

${color5}Sanford$color
${color1}Hoy:${color4}[--location=USME0356 --datatype=HT --hideunits --hidedegreesymbol]/[--location=USME0356 --datatype=LT --hideunits --hidedegreesymbol]
${color1}Luz:${color4}[--location=USME0356 --datatype=DL]

${color5}Prague$color
${color1}Hoy:${color4}[--location=EZXX0012 --datatype=HT --hideunits --hidedegreesymbol]/[--location=EZXX0012 --datatype=LT --hideunits --hidedegreesymbol]
${color1}Luz:${color4}[--location=EZXX0012 --datatype=DL]

${color5}Winnipeg$color
${color1}Hoy:${color4}[--location=CAXX0547 --datatype=HT --hideunits --hidedegreesymbol]/[--location=CAXX0547 --datatype=LT --hideunits --hidedegreesymbol]
${color1}Luz:${color4}[--location=CAXX0547 --datatype=DL]

${color5}London$color
${color1}Hoy:${color4}[--location=CAXX0255 --datatype=HT --hideunits --hidedegreesymbol]/[--location=CAXX0255 --datatype=LT --hideunits --hidedegreesymbol]
${color1}Luz:${color4}[--location=CAXX0255 --datatype=DL]
```
Listo!

Espero que te gusta!
Bruce
PD: pardon mi español, estoy aprendiendo.

---

### Post by Warper on 2008-11-12
Gracias Bruce.

Pues sí que me gusta. He hecho algunas modificaciones (he "castellanizado", he puesto aquí, he puesto allá) y me gusta el resultado.

Lo que no he puesto, es el mail, ya que con mi cuenta principal (telefonica.net), me da problemas. Me dice que hay un error en el usuario o el password, y están correctos, lo he comprobado varias veces. Con otra cuenta secundaria, sí ha funcionado a la primera.

Bueno, así es como ha quedado en una primera versión:

---

### Post by c4d0rn4 on 2008-11-12
> **Warper said:**
> Gracias Bruce.

Pues sí que me gusta. He hecho algunas modificaciones (he "castellanizado", he puesto aquí, he puesto allá) y me gusta el resultado.

Lo que no he puesto, es el mail, ya que con mi cuenta principal (telefonica.net), me da problemas. Me dice que hay un error en el usuario o el password, y están correctos, lo he comprobado varias veces. Con otra cuenta secundaria, sí ha funcionado a la primera

Fijate que gmail tiene la opción de levantar correos de cuentas pop. La opción está en settings-> account.

Podés meter varías cuenta y con una sola tener acceso a todas y desde la comodidad de gmail.

---

### Post by equiman on 2008-11-13
> **Bruce M. said:**
> Hola santiagoward2000 - tanto tiempo!

Si ... "lightblue" (cool), "yellow" (warm) y "red" (hot) (en mi caso)

[CENTER][[IMG]http://img528.imageshack.us/img528/392/20oct08et8.th.gif[/IMG]](http://img528.imageshack.us/my.php?image=20oct08et8.gif)[/CENTER]

Lo encontré: Post your .conkyrc files w/ screenshots - No lo escribí.

Tengo mas:

ColorUseNet.sh
ColorUseHDD.sh
ColorUseCPU.sh
ColorTempMB.sh
ColorTempHDD.sh
ColorTempGPU.sh
ColorTempCPU.sh
ColorTempCore.sh
ColorFreeHDD.sh
ColorCapHDD.sh

Los numeros para COOL y WARM cambia por cada uno depende en su equipo

Chimo!
Bruce

He tratado de buscar ejemplos de como aplicar 
ColorUseNet.sh
ColorUseHDD.sh
ColorUseCPU.sh
ColorFreeHDD.sh

Pero no encuentro, podrais poner un ejemplo al menos de uno?

---

### Post by Bruce M. on 2008-11-14
> **equiman said:**
> He tratado de buscar ejemplos de como aplicar 
ColorUseNet.sh
ColorUseHDD.sh
ColorUseCPU.sh
ColorFreeHDD.sh

Pero no encuentro, podrais poner un ejemplo al menos de uno?

Tengo los archivos. No puedo conseguirlos para funcionar correctamente todavía. Cuando trabajan, demostraré un ejemplo.

Enviaré un P.M. para dejarle saber.
Que tengas un buen día.
Bruce

---

### Post by equiman on 2008-11-14
Ok, gracias Bruce, pero si los puedes poner sobre todo la parte de como se utilizan desde Conky podemso ir probando varios hasta que funcione.

---

### Post by Bruce M. on 2008-11-14
> **equiman said:**
> Ok, gracias Bruce, pero si los puedes poner sobre todo la parte de como se utilizan desde Conky podemso ir probando varios hasta que funcione.

```
${color4}CPU: ${color5}**${execpi 8 sensors | grep 'CPU Temp' | cut --characters 15-16 | xargs ~/Conky/scripts/ColorTempCPU.sh}°**$color${goto 108}${color4}Core: **${execpi 8 sensors | grep 'Core0' | cut --characters 15-16 | xargs ~/Conky/scripts/ColorTempCore.sh}°**$color${alignr 2}${color4}M/B: **${execpi 8 sensors | grep 'M/B Temp' | cut --characters 15-16 | xargs ~/Conky/scripts/ColorTempMB.sh}°**$color
```
*ColorTempCPU.sh*
```
#!/bin/bash
# colorize.sh

COOL=60
WARM=70

if [[ $1 < $COOL ]]
   then echo "\${color7}"$1    # COOL
elif [[ $1 > $WARM ]]
   then echo "\${color9}"$1    # HOT
else echo "\${color8}"$1       # WARM
fi

exit 0
```
*ColorTempCore.sh*
```
#!/bin/bash
# colorize.sh

COOL=60
WARM=70

if [[ $1 < $COOL ]]
   then echo "\${color7}"$1    # COOL
elif [[ $1 > $WARM ]]
   then echo "\${color9}"$1    # HOT
else echo "\${color8}"$1       # WARM
fi

exit 0
```
*ColorTempMB.sh*
```
#!/bin/bash
# colorize.sh

COOL=60
WARM=70

if [[ $1 < $COOL ]]
   then echo "\${color7}"$1    # COOL
elif [[ $1 > $WARM ]]
   then echo "\${color9}"$1    # HOT
else echo "\${color8}"$1       # WARM
fi

exit 0
```
Son lo mismos porque estoy buscando la information para mi "mother", "CPU" y "core". Estos (60 y 70) son "safe" temps.

---

### Post by equiman on 2008-11-17
Gracias. Tienes tambien los de HDD Usage?

---

### Post by ramiro_md on 2008-11-17
Gente después de tanto tiempo leyendo conkyrc's pude solucionar el tema del "above" y "below" jeje, en la línea "own_window_type" estaba configurado "override" y lo cambie por "normal".
Por otro lado, el conky queda como levantado del wallpaper, como en relieve, toquetee bastante y todavía no lo puedo dejar plano sobre el escritorio :S, si alguno tiene alguna idea, bienvenido sea.
Un saludo y gracias,

---

### Post by Bruce M. on 2008-11-17
> **equiman said:**
> Gracias. Tienes tambien los de HDD Usage?

Todavía - no :(

Bruce

---

### Post by jjgomera on 2008-11-19
> **ramiro_md said:**
> Gente después de tanto tiempo leyendo conkyrc's pude solucionar el tema del "above" y "below" jeje, en la línea "own_window_type" estaba configurado "override" y lo cambie por "normal".
por pura casualidad, lo suyo sería que lo definiares con la variable:
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

undecorated: sin bordes de ventana
below: lo que tu buscas, siempre debajo de otras ventanas
sticky: en todos los escritorios
skiptaskbar: no aparece en el icono de sistema
skippager: no aparece en la lista de ventanas

> **ramiro_md said:**
> 
Por otro lado, el conky queda como levantado del wallpaper, como en relieve, toquetee bastante y todavía no lo puedo dejar plano sobre el escritorio :S, si alguno tiene alguna idea, bienvenido sea.
Un saludo y gracias,
eso depende más de gestor de ventanas, si estás usando compiz deberás configurarlo en él, levantar una excepción o algo así para que no dibuje efectos sobre las ventanas de conky (no uso compiz como para poder explicarte cómo).
yo que uso xcompmgr me basta con cambiar el valor de la variable own_window_type a desktop

@ bruce M: que alegría verte participando tan fluido en los hilos en español :lolflag:

---

### Post by ramiro_md on 2008-11-19
> **jjgomera said:**
> por pura casualidad, lo suyo sería que lo definiares con la variable:
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

Así lo tuve configurado toda la vida :) Gracias x la data de compiz, voy a ver que onda con eso.

---

### Post by jjgomera on 2008-11-20
> **ramiro_md said:**
> Así lo tuve configurado toda la vida :) Gracias x la data de compiz, voy a ver que onda con eso.
ah, own_window_hints solo funciona cuando own_window es yes, si no se ignora, quizá fuera por eso que no te obedecía

---

### Post by Bruce M. on 2008-11-20
> **jjgomera said:**
> @ bruce M: que alegría verte participando tan fluido en los hilos en español :lolflag:

Estoy practicando mi castellano y ayudando gente al mismo tiempo.
Ahora estoy un poco más cómodo escribiendo y tengo mi "spelling checker" para Español/Argentina ayudándome.

CHIMO!
Bruce

---

### Post by lega on 2008-11-29
tengo un problema con el conky de la captura, como pueden ver en el 3 bloque donde dice Governor no marca nada, si lo lanzo de la terminal me da el siguiente error 
> sh: sensors: not found
cat: /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor: No existe el fichero ó directorio
sh: /home/leonardo/.scripts/cpu_mhz: not found


el script cpu_mhz está en su lugar sin embargo dice que no lo encuentra, no se que puede estar pasando, alguien me puede dar una mano?

---

### Post by Hei Ku on 2008-11-29
Chequeaste los permisos del script, y que tenga permiso de ejecucion?

```

sudo chmod +x <nombre de archivo>

```

---

### Post by lega on 2008-11-29
sip, tiene permisos de ejecución

---

### Post by jjgomera on 2008-11-30
es más facil ayudarte si pones tu conkyrc, o por lo menos la linea del governor, y el script que utilizas

---

### Post by lega on 2008-11-30
Bueno, este es el conky rc de ese script
```
# Use Xft?
use_xft yes
xftfont cure:size=6

# Update interval in seconds
update_interval 1

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window  yes
own_window_transparent no
own_window_type widget
own_window_hints undecorate,sticky,skip_taskbar,skip_pager 

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 280 5

maximum_width 87

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders yes

# Stippled borders?
stippled_borders 0

# border margins
border_margin 5

# border width
border_width 1

# Default colors and also border colors
default_color 303030
#default_shade_color white
#default_outline_color black
own_window_colour 262524

# Text alignment, other possible values are commented
alignment top_left
#alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 20
gap_y 325

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer yes

TEXT
${color 9ACD32}Kernel:${color a4a4a4}${alignr}$kernel
${color 9ACD32}UpTime:${color a4a4a4}${alignr}$uptime

${color 9ACD32}Cpu1:${color a4a4a4}${alignr}${cpu cpu1}% ${color 556B2F}${execi 20 sensors k8temp-pci-00c3 |grep Core0 |awk '{print $3}'}
${color 556B2F}${cpugraph cpu1 20,85 556B2F 9ACD32} 
${color 9ACD32}Cpu2:${color a4a4a4}${alignr}${cpu cpu2}% ${color 556B2F}${execi 20 sensors k8temp-pci-00c3 |grep Core1 |awk '{print $3}'}
${color 556B2F}${cpugraph cpu2 20,85 556B2F 9ACD32} 

${color 9ACD32}Governor:
${color a4a4a4}${execi 5 cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor} ${alignr}${execi 5 ~/.scripts/cpu_mhz}GHz

${color 9ACD32}Gpu:${color a4a4a4}${alignr}${execi 20 nvidia-settings -q GPUCurrentClockFreqs |grep Attribute |awk '{print $4}' |cut -c1-7} ${color 556B2F}${execi 20 nvidia-settings -q gpucoretemp |grep Attribute |awk '{print $4}' |cut -c1-2}°C

${color 9ACD32}Ram:${color a4a4a4}${alignr}$mem
${color 556B2F}${membar 3,85}
```

y este el script

```
#!/bin/awk -f

BEGIN {

	CPU_MHZ_CMD = "cat /proc/cpuinfo |grep MHz"; # CPU MHz
	CPU_MHZ_CMD | getline;
	close(CPU_MHZ_CMD);

	mhz = sprintf("%1.1f", ($4 / 1000));
	print mhz;

      }
```

---

### Post by jjgomera on 2008-11-30
has comprobado que existe este archivo en tu sistema?
/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

también te esta dandos problemas:
sensors k8temp-pci-00c3, parece que tu sistema no lo reconoce, prueba desde una terminal a ver que error te da

el ultimo error sobre el script no sé realmente que está mal

---

### Post by lega on 2008-11-30
gracias me faltaba instalar lm-sensors ahora me muestra la temperatura del procesador, que antes no lo hacía 
> has comprobado que existe este archivo en tu sistema?
/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

Ahora si lo comprobé,y no,no existe... que tengo que instalar?

---

### Post by sbruno on 2008-11-30
> **lega said:**
> gracias me faltaba instalar lm-sensors ahora me muestra la temperatura del procesador, que antes no lo hacía 


Ahora si lo comprobé,y no,no existe... que tengo que instalar?

Si tu cpu soporta frequency scaling y no tenés cargado el módulo, tendrías que hacer que lo cargue.

En mi caso, para un AMD Athlon, tengo que tener cargado el módulo powernow-k8

```
modprobe powernow-k8
```

con eso te tendría que dar algo

```
less /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```

como root podés cambiar el governor con cosas como
```
echo "ondemand" > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```
```
echo "performance" > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```

y ver la frecuencia actual con un script como el que tenés con awk, o
```
grep "cpu MHz" /proc/cpuinfo | cut -d':' -f2
```

Yo tengo que me cargue al inicio ondemand y que esté siempre así. Pero podés instalar cpufreq y ver que onda. Yo nunca lo usé.

Buscá frequency scaling en el foro o en google y vas a encontrar más información.

Por el error en el último script, fijate que te da hacer

```
ls -lh /home/leonardo/.scripts/cpu_mhz
```

si faltan permisos, o no existe.

---

### Post by lega on 2008-11-30
> En mi caso, para un AMD Athlon, tengo que tener cargado el módulo powernow-k8

Code:

modprobe powernow-k8



A mi me sale esto :
```
FATAL: Error inserting powernow_k8 (/lib/modules/2.6.27-9-generic/kernel/arch/x86/kernel/cpu/cpufreq/powernow-k8.ko): Operation not permitted

```
> Por el error en el último script, fijate que te da hacer
```
ls -lh /home/leonardo/.scripts/cpu_mhz
```

me tira esto
```
-rwxr-xr-x 1 leonardo leonardo 185 2008-09-19 08:16 /home/leonardo/.scripts/cpu_mhz

```

gracias despues busco en el foro

---

