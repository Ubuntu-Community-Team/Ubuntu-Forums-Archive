---
title: "HOW TO: Install and configure lm-sensors"
date: 2004-10-31
forum: Tutorials
---

### Post by emperor on 2004-10-31
Howto Install and Configure lm-sensors
     ========================
     
     1. I**nstall lm-sensors** using apt-get or the Synaptic GUI.
     
     sudo apt-get install lm-sensors
     
     
     2. **Run the mkdev.sh script** in the lm-sensors source. It is extacted below:
     
     a. Copy the script file below to a text editor and save it to a file named mkdev.sh.
     
     #!/bin/bash
     
     # Here you can set several defaults.
     
     # The number of devices to create (max: 256)
     NUMBER=32
     
     # The owner and group of the devices
     OUSER=root
     OGROUP=root
     # The mode of the devices
     MODE=600
     
     # This script doesn't need to be run if devfs is used
     if [ -r /proc/mounts ] ; then
         if grep -q "/dev devfs" /proc/mounts ; then
             echo "You do not need to run this script as your system uses devfs."
             exit;
         fi
     fi
     
     i=0;
     
     while [ $i -lt $NUMBER ] ; do
         echo /dev/i2c-$i
         mknod -m $MODE /dev/i2c-$i c 89 $i || exit
         chown "$OUSER:$OGROUP" /dev/i2c-$i || exit
         i=$[$i + 1]
     done
     #end of file
     
     b. Make the file executable:
     
     chmod 755 mkdev.sh
     
     c. Run mkdev.sh from the current directory
     
     sudo ./mkdev.sh
     
     
   3. Now** run sensors-detect** and answer YES to all YES/no questions. I generally use the ISA bus rather than the SMBus bus, your choice to this question!. At the end of the detection phase, a list of modules that needs to be loaded will displayed. You will need to write these down or print the list for the next steps.
     
     sudo sensors-detect
     
     Below is an example of results from sensors-detect:
     #******************************************************************************
     To make the sensors modules behave correctly, add these lines to
     /etc/modules:
     
     #----cut here----
     # I2C adapter drivers
     i2c-viapro
     i2c-isa
     # I2C chip drivers
     eeprom
     it87
     #----cut here----
     
     Then, run /etc/init.d/module-init-tools
     
     To make the sensors modules behave correctly, add these lines to
     /etc/modprobe.d/local and run update-modules:
     
     #----cut here----
     # I2C module options
     alias char-major-89 i2c-dev
     #----cut here----
     #********************************************************************************
     
  
     4. In this example, we [b]add the modules in reverse order (order is critical!) in "/etc/modules".
  [/b]    
     #************************************************************************ 
     # /etc/modules: kernel modules to load at boot time.
     #
     # This file should contain the names of kernel modules that are
     # to be loaded at boot time, one per line.  Comments begin with
     # a "#", and everything on the line after them are ignored.
     
     psmouse
     mousedev
     ide-cd
     ide-disk
     ide-generic
     lp
     
     #For lm-sensors, i2c modules
     it87
     i2c-viapro
     i2c-isa
     
     #end of file!
     #*****************************************************************
     
     
 4. I found that there was no "/etc/modprobe.d/local" and that "alias char-major-89 i2c-dev" was already listed in "/etc/modprobe.d/aliases". So, nothing to do here.
     
     
     5.Now** load the modules manually using modprobe and update the dependencies.**
     
     sudo modprobe i2c-sensor
     sudo modprobe i2c-viapro
     sudo modprobe i2c-isa
     sudo modprobe it87
     
     sudo depmod -a           <may not be needed!>
     sudo update-modules      <may not be needed!>
     
     
     6. Now [b]test the sensor output using the lm-sensors utility "sensors".
 [/b]      
     sensors
     
     *******************************************************************
     it87-isa-0290
     Adapter: ISA adapter
     VCore 1:   +1.57 V  (min =  +1.42 V, max =  +1.57 V)   ALARM
     VCore 2:   +2.66 V  (min =  +2.40 V, max =  +2.61 V)   ALARM
     +3.3V:     +6.59 V  (min =  +3.14 V, max =  +3.46 V)   ALARM
     +5V:       +5.11 V  (min =  +4.76 V, max =  +5.24 V)
     +12V:     +11.78 V  (min = +11.39 V, max = +12.61 V)
     -12V:     -19.14 V  (min = -12.63 V, max = -11.41 V)   ALARM
     -5V:       +0.77 V  (min =  -5.26 V, max =  -4.77 V)   ALARM
     Stdby:     +5.00 V  (min =  +4.76 V, max =  +5.24 V)
     VBat:      +3.12 V
     fan1:     3668 RPM  (min =    0 RPM, div = :cool:
     fan2:        0 RPM  (min =  664 RPM, div = :cool:          ALARM
     fan3:        0 RPM  (min = 2657 RPM, div = 2)          ALARM
     M/B Temp:    +39°C  (low  =   +15°C, high =   +40°C)   sensor = thermistor
     CPU Temp:    +36°C  (low  =   +15°C, high =   +45°C)   sensor = thermistor
     Temp3:       +96°C  (low  =   +15°C, high =   +45°C)   sensor = diode
     **********************************************************************
     
     7. **Reboot** Ubuntu and the sensors should now be detected during the boot process properly!
     
   8. The **sensor output may be tweaked by editing the "/etc/sensors.conf" file**. It is possible to correct inacurate scaling too. For details check "man sensors.conf.

---

### Post by jgaynor on 2005-01-16
EXCELLENT howto man - I had been struggling with this using the debian method but this worked without issue.  Thanks again!

---

### Post by Tichondrius on 2005-01-17
Works great, I was looking for something like this for overclocking...
But I did not understand what you said about the reverse order in /etc/modules. What exactly should be reversed ?

BTW, if you want a graphical output, try installing the "xsensors" package which uses lm-sensors.

---

### Post by Rule on 2005-01-17
Well I gess I got it working for once but when I type in "sensors" mine comes out differant from your  :confused:  

```
eeprom-i2c-0-51
Adapter: SiS96x SMBus adapter at 0x0c00
Memory type:            DDR SDRAM DIMM
Memory size (MB):       256

eeprom-i2c-0-50
Adapter: SiS96x SMBus adapter at 0x0c00
Memory type:            DDR SDRAM DIMM
Memory size (MB):       256
```

---

### Post by woifi on 2005-01-17
[QUOTE=Rule]Well I gess I got it working for once but when I type in "sensors" mine comes out differant from your  :confused:  

```
eeprom-i2c-0-51
Adapter: SiS96x SMBus adapter at 0x0c00
Memory type:            DDR SDRAM DIMM
Memory size (MB):       256

eeprom-i2c-0-50
Adapter: SiS96x SMBus adapter at 0x0c00
Memory type:            DDR SDRAM DIMM
Memory size (MB):       256
```[/QUOTE]
 is this your full output? if yes, something went wrong ;)

it should look like this:
```
woifi@homer:~ $ sensors
Philips PAL_BG -i2c-2-61
Adapter: bt878 #0 [sw]

MSP3410D-i2c-2-40
Adapter: bt878 #0 [sw]

eeprom-i2c-2-50
Adapter: bt878 #0 [sw]
Unknown EEPROM type (0)

w83627hf-isa-0290
Adapter: ISA adapter
VCore 1:   +1.74 V  (min =  +1.76 V, max =  +1.94 V)       ALARM
VCore 2:   +1.25 V  (min =  +1.76 V, max =  +1.94 V)
+3.3V:     +3.22 V  (min =  +3.14 V, max =  +3.47 V)
+5V:       +4.87 V  (min =  +4.76 V, max =  +5.24 V)
+12V:     +12.71 V  (min = +10.82 V, max = +13.19 V)
-12V:     -12.77 V  (min = -13.18 V, max = -10.80 V)
-5V:       -5.55 V  (min =  -5.25 V, max =  -4.75 V)
V5SB:      +5.51 V  (min =  +4.76 V, max =  +5.24 V)
VBat:      +3.17 V  (min =  +2.40 V, max =  +3.60 V)
fan1:        0 RPM  (min = 3199 RPM, div = 2)
fan2:        0 RPM  (min = 3040 RPM, div = 2)
fan3:        0 RPM  (min = 13500 RPM, div = 2)
temp1:       +25°C  (high =   +15°C, hyst =    -3°C)   sensor = thermistor 
temp2:     +32.5°C  (high =   +80°C, hyst =   +75°C)   sensor = thermistor 
temp3:     -46.0°C  (high =   +80°C, hyst =   +75°C)   sensor = thermistor 
vid:      +1.850 V
alarms:   Chassis intrusion detection                      ALARM
beep_enable:
          Sound alarm disabled

eeprom-i2c-0-51
Adapter: SMBus Via Pro adapter at 0400
Memory type:            DDR SDRAM DIMM
Memory size (MB):       256

eeprom-i2c-0-50
Adapter: SMBus Via Pro adapter at 0400
Memory type:            DDR SDRAM DIMM
Memory size (MB):       256
```

hth

woifi

---

### Post by Rule on 2005-01-17
well I did see some failures :(  maybe thats why, i'm on an Averatec 6100 laptop. I also noticed in my bios it doesnt even tell me the temps :twisted:  :-s

EDIT: when I try to run sensors-dectect and hit enter a few time I get

```
 Sorry, no chips were detected.
 Either your sensors are not supported, or they are
 connected to an I2C bus adapter that we do not support.
 See doc/FAQ, doc/lm_sensors-FAQ.html, or
 http://www2.lm-sensors.nu/~lm78/cvs/lm_sensors2/doc/lm_sensors-FAQ.html
 (FAQ #4.24.3) for further information.
 If you find out what chips are on your board, see
 http://secure.netroedge.com/~lm78/newdrivers.html for driver status.
``` 

also I attatched some of the errors I got before

---

### Post by barbarian on 2005-01-17
[I]eeprom-i2c-0-51
Adapter: SiS96x SMBus adapter at 0x0c00
Memory type:            DDR SDRAM DIMM
Memory size (MB):       256

eeprom-i2c-0-50
Adapter: SiS96x SMBus adapter at 0x0c00
Memory type:            DDR SDRAM DIMM
Memory size (MB):       256[/I]


The same output for me..

[B][I]Adapter: SMBus Via Pro adapter at 5000
Memory type:            DDR SDRAM DIMM
Memory size (MB):       256

eeprom-i2c-0-50
Adapter: SMBus Via Pro adapter at 5000
Memory type:            DDR SDRAM DIMM
Memory size (MB):       256
[/I][/B]

---

### Post by barbarian on 2005-01-18
Noob qestion, but could You notice which place should I put mkdev.sh? usr/share/lmsensors?

---

### Post by emperor on 2005-01-18
[QUOTE=barbarian]Noob qestion, but could You notice which place should I put mkdev.sh? usr/share/lmsensors?[/QUOTE]
 
 You are just going to run the "mkdev.sh" file once, prior to executing sensors-detect.
 
 I put the script file in a sub-directory in my home directory. However, for permanent storage, it can be put almost anywhere you have prev's.

---

### Post by barbarian on 2005-01-19
Ok, thanx, I'll give a try once more..

---

### Post by *aLeX* on 2005-01-19
Hi all!!

I had the same problem... than I tried to swap order in which modules were loaded and now it seems ok even if I get values only from the via module!

This is my output: (some values are a bit strange)

```

via686a-isa-6000
Adapter: ISA adapter
CPU core:  +3.10 V  (min =  +3.07 V, max =  +3.00 V)   ALARM
+2.5V:     +0.06 V  (min =  +3.08 V, max =  +3.10 V)   ALARM
I/O:       +3.33 V  (min =  +4.01 V, max =  +3.82 V)   ALARM
+5V:       +3.27 V  (min =  +3.08 V, max =  +6.44 V)   
+12V:      +7.93 V  (min = +11.77 V, max = +13.68 V)   ALARM
CPU Fan:     0 RPM  (min =    0 RPM, div = 2)          
P/S Fan:     0 RPM  (min =    0 RPM, div = 2)          
SYS Temp:  +23.9°C  (high =  +146°C, hyst =  +146°C)   
CPU Temp:  +23.9°C  (high =  +141°C, hyst =  +146°C)   
SBr Temp:  +24.9°C  (high =   +20°C, hyst =   +34°C)   ALARM

```

and thi is the order in which i loaded the modules:

```

modprobe via686a
modprobe eeprom 
modprobe i2c-viapro
modprobe i2c-isa   

```

---

### Post by emperor on 2005-01-19
[QUOTE=*aLeX*]Hi all!!
  
 I had the same problem... than I tried to swap order in which modules were loaded and now it seems ok even if I get values only from the via module!
  
  This is my output: (some values are a bit strange)[/QUOTE]
  The values that are display are calculate from the raw sensor data and sometime the formula needs to be corrected. See **"/etc/sensors.conf"**.

---

### Post by *aLeX* on 2005-01-20
Thank you.. so now i try to trim them!

---

### Post by barbarian on 2005-01-20
Finaly I'v got it, here's my output:
$ sensors
lm90-i2c-0-4c
Adapter: SMBus Via Pro adapter at 5000
M/B Temp:    +46°C  (low  =    +0°C, high =   +70°C)
CPU Temp:  +50.6°C  (low  =  +0.0°C, high = +70.0°C)
M/B Crit:    +95°C  (hyst =   +85°C)
CPU Crit:    +95°C  (hyst =   +85°C)

---

### Post by kiwigander on 2005-02-28
Thank you Emperor!  Step-by-step instructions that 1) even I could follow and 2) gave a successful outcome on the first try.

---

### Post by RastaMahata on 2005-02-28
well this doesnt work on my nforce2 chipset :(

it told me this:

```

To make the sensors modules behave correctly, add these lines to
/etc/modules:

#----cut here----
# I2C adapter drivers
i2c-nforce2
i2c-nforce2
i2c-isa
# I2C chip drivers
eeprom
w83627hf
#----cut here----

Then, run /etc/init.d/module-init-tools


To make the sensors modules behave correctly, add these lines to
/etc/modprobe.d/local and run update-modules:

#----cut here----
# I2C module options
alias char-major-89 i2c-dev
#----cut here----

```

so I did it, but I get to this point:

```

$ sudo modprobe w83627hf
FATAL: Error inserting w83627hf (/lib/modules/2.6.8.1-5-k7/kernel/drivers/i2c/chips/w83627hf.ko): No such device

```

what can I do? I'm a warty user.

---

### Post by rosslaird on 2005-03-01
It doesn't work on my nforce chipset either -- but I have NEVER been able to get lm-sensors to work with my board in over two years of trying. I think it's an nforce-specific problem.

---

### Post by RastaMahata on 2005-03-01
I got it! Just googling and reading the whole output of sensors-detect, I was able to install lm-sensors in my nforce2 chipset! Here's how I did it:

You can see here something fishy:
```
Probing for `Winbond W83627HF'
  Trying address 0x0290... Success!
    (confidence 8, driver `w83781d')
```

Anyway, I found out that w83627hf is not the right module needed for the nforce2 chipset! The right one is the driver suggested below, the w83781d.

So, here's the correct output needed:
```
# I2C adapter drivers
i2c-nforce2
i2c-nforce2
i2c-isa
# I2C chip drivers
eeprom
w83781d
```

copy that to /etc/modules

then issue these commands:
```
$ sudo modprobe i2c-isa
$ sudo modprobe i2c-nforce2
$ sudo modprobe w83781d
$ sudo modprobe eeprom
$ sudo /etc/init.d/module-init-tools
$ sudo update-modules
```

Then just run this:
```
$ sensors
```

And it should give you something like this:
```
w83627hf-isa-0290
Adapter: ISA adapter
VCore 1:   +1.47 V  (min =  +1.14 V, max =  +1.55 V)
VCore 2:   +1.54 V  (min =  +1.14 V, max =  +1.55 V)       ALARM
+3.3V:     +3.33 V  (min =  +2.82 V, max =  +3.79 V)
+5V:       +5.05 V  (min =  +0.00 V, max =  +0.00 V)       ALARM
+12V:     +12.22 V  (min =  +0.00 V, max =  +0.00 V)       ALARM
-12V:     -12.53 V  (min = -14.91 V, max = -14.91 V)       ALARM
-5V:       -5.35 V  (min =  -7.71 V, max =  -7.71 V)       ALARM
V5SB:      +5.43 V  (min =  +0.43 V, max =  +0.00 V)       ALARM
VBat:      +3.04 V  (min =  +0.00 V, max =  +0.00 V)       ALARM
fan1:        0 RPM  (min =   -1 RPM, div = 2)              ALARM
fan2:     3994 RPM  (min =   -1 RPM, div = 2)              ALARM
fan3:        0 RPM  (min = 3245 RPM, div = 4)              ALARM
temp1:       +34°C  (high =    +0°C, hyst =    +0°C)   sensor = thermistor   ALARM
temp2:     +36.5°C  (high =   +53°C, hyst =   +48°C)   sensor = thermistor 
temp3:     +37.0°C  (high =   +53°C, hyst =   +48°C)   sensor = thermistor 
vid:      +1.350 V
alarms:
beep_enable:
          Sound alarm disabled

eeprom-i2c-0-51
Adapter: SMBus nForce2 adapter at 5000
Memory type:            DDR SDRAM DIMM
Memory size (MB):       256
```

Although I'm not sure if that eeprom is right in there..  and all those "alarm" messages too

---

### Post by Cyberkef on 2005-03-03
[QUOTE=emperor]...
     
c. Run mkdev.sh from the current directory

sudo ./mkdev.sh

...[/QUOTE]
I got stuck here #-o 

```
cyberkef@CyberTrax2000:~/Desktop $ dir
mkdev.sh                            proxy.txt~
mkdev.sh~                           Share\ 120GB.desktop~
mplayer~
cyberkef@CyberTrax2000:~/Desktop $ sudo ./mkdev.sh
sudo: unable to exec ./mkdev.sh: No such file or directory
```

The chmod is 755.

Hm, I don't see why he doesn't find the file, it is there! In the Desktop directory!
Even in another directory I have the same error :confused:

---

### Post by rosslaird on 2005-03-05
Thanks, RastaMahata. Your instructions worked perfectly for me. I can now properly monitor my box, which is designed for silence and sits away in a drawer. I can't hear it, can't see it, and have had until now no input about what's going on inside of it. Now I know.

Cheers.

Ross

---

### Post by RastaMahata on 2005-03-05
[QUOTE=rosslaird]Thanks, RastaMahata. Your instructions worked perfectly for me. I can now properly monitor my box, which is designed for silence and sits away in a drawer. I can't hear it, can't see it, and have had until now no input about what's going on inside of it. Now I know.

Cheers.

Ross[/QUOTE]
 no problem :P

---

### Post by fackamato on 2005-03-07
How about a howto for the program that comes with lm-sensors - fancontrol? ;)

Sure many users who use Speedfan in windows wants some software to control their fans. :D

---

### Post by mario8723 on 2005-03-17
Some help here please...I get to the point where I have to modify the  /etc/modprobe.d/local but I can't find it; doesn't seem to exist...Any suggestions would be most welcome!

I know I must be close, because I can run system apps from gdesklets now, where previously I couldn't. The only thing it doesn't seem to show is the temps...

---

### Post by fackamato on 2005-03-17
[QUOTE=mario8723]Some help here please...I get to the point where I have to modify the  /etc/modprobe.d/local but I can't find it; doesn't seem to exist...Any suggestions would be most welcome![/QUOTE]

Don't you mean /etc/modules ? (where you put modules that should automatically load on boot)

---

### Post by mario8723 on 2005-03-17
I don't have that either. I do have modutils, but I'm looking in the /etc/ folder right now and I don't have modules. Did I do something wrong?

---

### Post by Hurky on 2005-04-05
Hi, I get this error trying to install lmsensors... What am I doing wrong?

```
sudo apt-get install lm-sensors
Reading Package Lists... Done
Building Dependency Tree... Done
Package lm-sensors is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package lm-sensors has no installation candidate
```

---

### Post by jr_G-man on 2005-04-12
Worked great for me on my KT400-based board.  Thanks.

---

### Post by kuleali on 2005-04-12
thanks!

---

### Post by jodsalz on 2005-05-18
I used this howto and installed the right modules correctly, but when doing "sensors" I only can read "no sensors detected"... Any ideas? Use this thread: [http://ubuntuforums.org/showthread.php?p=177493](http://ubuntuforums.org/showthread.php?p=177493)

Thanks!

---

### Post by fackamato on 2005-05-18
[QUOTE=jodsalz]I used this howto and installed the right modules correctly, but when doing "sensors" I only can read "no sensors detected"... Any ideas? Use this thread: [http://ubuntuforums.org/showthread.php?p=177493](http://ubuntuforums.org/showthread.php?p=177493)

Thanks![/QUOTE]

Didn't sensors-detect find anything?

---

### Post by jodsalz on 2005-05-18
[QUOTE=fackamato]Didn't sensors-detect find anything?[/QUOTE]

Well, thats the problem! sensors-detect DID find something, and I loaded the proposed modules. Please take a look: [http://ubuntuforums.org/showthread.php?p=177493](http://ubuntuforums.org/showthread.php?p=177493)

---

### Post by simple on 2005-06-12
[QUOTE=Rule]well I did see some failures :(  maybe thats why, i'm on an Averatec 6100 laptop. I also noticed in my bios it doesnt even tell me the temps :twisted:  :-s

EDIT: when I try to run sensors-dectect and hit enter a few time I get

```
 Sorry, no chips were detected.
 Either your sensors are not supported, or they are
 connected to an I2C bus adapter that we do not support.
 See doc/FAQ, doc/lm_sensors-FAQ.html, or
 http://www2.lm-sensors.nu/~lm78/cvs/lm_sensors2/doc/lm_sensors-FAQ.html
 (FAQ #4.24.3) for further information.
 If you find out what chips are on your board, see
 http://secure.netroedge.com/~lm78/newdrivers.html for driver status.
``` 

also I attatched some of the errors I got before[/QUOTE]
 i get this too not using sudo first.. my mobo's spec [asus goldfish mobo](http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&lang=en&cc=us&product=449732&dlc=en&docname=c00300046)
with sudo i get > Driver `eeprom' (should be inserted):
  Detects correctly:
  * Bus `SMBus I801 adapter at 0400' (Algorithm unavailable)
    Busdriver `i2c-i801', I2C address 0x50
    Chip `SPD EEPROM' (confidence: 8)
  * Bus `SMBus I801 adapter at 0400' (Algorithm unavailable)
    Busdriver `i2c-i801', I2C address 0x52
    Chip `SPD EEPROM' (confidence: 8)
 will this get me to like.. tell temp and stuff?

---

### Post by simple on 2005-06-12
simple@elemental:~$ sensors
eeprom-i2c-0-52
Adapter: SMBus I801 adapter at 0400
Memory type:            DDR SDRAM DIMM
Memory size (MB):       256

eeprom-i2c-0-50
Adapter: SMBus I801 adapter at 0400
Memory type:            DDR SDRAM DIMM
Memory size (MB):       256

simple@elemental:~$

must've have something the same as Rule.. if something went wrong, it's not my fault.. though because i did it exactally.. except i got now.. 

```
simple@elemental:~$ sudo /etc/init.d/module-init-tools
 * Calculating module dependencies...                                    [ ok ]
 * Loading modules...       
``` 
 To make the sensors modules behave correctly, add these lines to
/etc/modprobe.d/local and run update-modules:

#----cut here----
# I2C module options
alias char-major-89 i2c-dev
#----cut here----
#************************************************* *******************************

was i supposed to see that? i never saw anything like that.

---

### Post by simple on 2005-06-12
i guess if you could take a quick look at the attachment, my chip isn't compatible ?
[pc spec](http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&lang=en&cc=us&product=449732&dlc=en&docname=c00280721)

---

### Post by electrosoccertux on 2005-06-18
Hey, thank you so much for this guide.

---

### Post by icecube76 on 2005-06-22
i have hp pavilion ze4900 
and thats what i get 
root@vega:/home/abdulsalam # sudo sensors-detect

This program will help you determine which I2C/SMBus modules you need to
load to use lm_sensors most effectively. You need to have i2c and
lm_sensors installed before running this program.
Also, you need to be `root', or at least have access to the /dev/i2c-*
files, for most things.
If you have patched your kernel and have some drivers built in, you can
safely answer NO if asked to load some modules. In this case, things may
seem a bit confusing, but they will still work.

It is generally safe and recommended to accept the default answers to all
questions, unless you know what you're doing.

 IF THIS IS AN IBM THINKPAD, PRESS CTRL-C NOW!
 IBM Thinkpads have a severely broken i2c/SMBus implementation, just scanning
 the bus will break your Thinkpad forever!
 If this is a non-Thinkpad IBM, we still suggest you press CTRL+C. We have
 had users reporting system breakage on other IBM systems as well.

 We can start with probing for (PCI) I2C or SMBus adapters.
 You do not need any special privileges for this.
 Do you want to probe now? (YES/no): no

As you skipped adapter detection, we will only scan already loaded
adapter modules.
If you have undetectable or unsupported adapters, you can have them
scanned by manually loading the modules before running this script.

 To continue, we need module `i2c-dev' to be loaded.
 If it is built-in into your kernel, you can safely skip this.
i2c-dev is already loaded.

 We are now going to do the adapter probings. Some adapters may hang halfway
 through; we can't really help that. Also, some chips will be double detected;
 we choose the one with the highest confidence value in that case.
 If you found that the adapter hung after probing a certain address, you can
 specify that address to remain unprobed. That often
 includes address 0x69 (clock chip).

Next adapter: SMBus I801 adapter at 1880
Do you want to scan it? (YES/no/selectively): yes
Client found at address 0x30
Client at address 0x50 can not be probed - unload all client drivers first!
Client at address 0x51 can not be probed - unload all client drivers first!
Client found at address 0x69

Some chips are also accessible through the ISA bus. ISA probes are
typically a bit more dangerous, as we have to write to I/O ports to do
this. This is usually safe though.

Do you want to scan the ISA bus? (YES/no): no

Some Super I/O chips may also contain sensors. Super I/O probes are
typically a bit more dangerous, as we have to write to I/O ports to do
this. This is usually safe though.

Do you want to scan for Super I/O sensors? (YES/no): no

 Sorry, no chips were detected.
 Either your sensors are not supported, or they are
 connected to an I2C bus adapter that we do not support.
 See doc/FAQ, doc/lm_sensors-FAQ.html, or
 [http://www2.lm-sensors.nu/~lm78/cvs/lm_sensors2/doc/lm_sensors-FAQ.html](http://www2.lm-sensors.nu/~lm78/cvs/lm_sensors2/doc/lm_sensors-FAQ.html)
 (FAQ #4.24.3) for further information.
 If you find out what chips are on your board, see
 [http://secure.netroedge.com/~lm78/newdrivers.html](http://secure.netroedge.com/~lm78/newdrivers.html) for driver status.
root@vega:/home/abdulsalam # sensors
eeprom-i2c-0-51
Adapter: SMBus I801 adapter at 1880
Memory type:            DDR SDRAM DIMM
Memory size (MB):       256

eeprom-i2c-0-50
Adapter: SMBus I801 adapter at 1880
Memory type:            DDR SDRAM DIMM
Memory size (MB):       256

any help

---

### Post by aragorn2909 on 2005-06-25
Perhaps someone can help me here.  I've gone through the steps here, but my actual cpu temp is not displayed

```
it8712-isa-0290
Adapter: ISA adapter
VCore 1:   +1.79 V  (min =  +1.42 V, max =  +1.57 V)   ALARM
VCore 2:   +0.00 V  (min =  +2.40 V, max =  +2.61 V)   ALARM
+3.3V:     +6.56 V  (min =  +3.14 V, max =  +3.46 V)   ALARM
+5V:       +4.92 V  (min =  +4.76 V, max =  +5.24 V)
+12V:     +12.48 V  (min = +11.39 V, max = +12.61 V)   ALARM
-12V:     -27.36 V  (min = -12.63 V, max = -11.41 V)   ALARM
-5V:      -13.64 V  (min =  -5.26 V, max =  -4.77 V)   ALARM
Stdby:     +5.00 V  (min =  +4.76 V, max =  +5.24 V)
VBat:      +4.08 V
fan1:     4245 RPM  (min =    0 RPM, div = 2)
fan2:        0 RPM  (min = 2657 RPM, div = 2)          ALARM
fan3:        0 RPM  (min = 2657 RPM, div = 2)          ALARM
M/B Temp:    +52°C  (low  =   +15°C, high =   +40°C)   sensor = thermistor
CPU Temp:    +34°C  (low  =   +15°C, high =   +45°C)   sensor = thermistor
Temp3:        -1°C  (low  =   +15°C, high =   +45°C)   sensor = disabled

eeprom-i2c-0-50
Adapter: SMBus Via Pro adapter at e800
Memory type:            DDR SDRAM DIMM
Memory size (MB):       512
```

How to enable "temp3" sensor?

---

### Post by DonVla on 2005-06-30
great howto, 

worked directly.

thank you!!!!


vlad

---

### Post by otherdave on 2005-07-10
First off, this was awesome. I first looked at it and said "What? Scripts and stuff? Forget this..." and went off to do something else. I came back to it and actually READ through it and said "Oh this is nothing!" and it worked correctly for me the FIRST TIME. Excellent instructions.

Second off: Like some others here, I'm using an NForce 2 motherboard (Epox 8rDA+ or something). Does anyone know what the temp sensors map to? T1 is low (I'm guessing ambient temperature), t2 is high (cpu probably) and t3 is about 10 degrees (F) lower than t2 so I'm guessing it's either another chip or the mobo temp? Not sure. I can crack the case open and check the fan settings, but I'm not sure about the temperature sensors. Any ideas?

Thanks again for a simple and well-written guide.

---

### Post by Beire on 2005-07-18
[QUOTE=otherdave]First off, this was awesome. I first looked at it and said "What? Scripts and stuff? Forget this..." and went off to do something else. I came back to it and actually READ through it and said "Oh this is nothing!" and it worked correctly for me the FIRST TIME. Excellent instructions.

Second off: Like some others here, I'm using an NForce 2 motherboard (Epox 8rDA+ or something). Does anyone know what the temp sensors map to? T1 is low (I'm guessing ambient temperature), t2 is high (cpu probably) and t3 is about 10 degrees (F) lower than t2 so I'm guessing it's either another chip or the mobo temp? Not sure. I can crack the case open and check the fan settings, but I'm not sure about the temperature sensors. Any ideas?

Thanks again for a simple and well-written guide.[/QUOTE]
 are the the sensors that gdesklets use ?

all worked fine here , great how-to !

Is there also a sensor for the cpu-load ?

---

### Post by Stormy Eyes on 2005-07-21
Thanks for the HOWTO, **Emperor**. Now I've got the CPU temperature module in Enlightenment 0.17 on Hoary working.

---

### Post by RJARRRPCGP on 2005-07-29
After I install **xsensors** and then ran it, why this?

rjarrrpcgp@ubuntu:~$ sudo -s
root@ubuntu:~# xsensors
Sensor 'it8712' not supported by xsensors!


Is the hardware monitoring chip really rare?  ](*,)

But, this is with Hoary! (I wished that they moved the lm-sensors topic to another forum)

---

### Post by umdzig on 2005-07-29
I have a dell inspiron 8600. All i get when i try to use lm sensors is it says no sensors detected. Can someone tell me what driver i am supposed to use so i can get this to work correctly?

---

### Post by WTF_Shelley on 2005-07-30
I get some weird results
```

Adapter: SMBus Via Pro adapter at 5000
+5V:       +4.87 V  (min =  +6.71 V, max =  +0.00 V)
VTT:       +1.33 V  (min =  +2.55 V, max =  +0.00 V)
+3.3V:     +2.54 V  (min =  +3.68 V, max =  +0.00 V)
+Vcore:    +0.16 V  (min =  +3.02 V, max =  +2.81 V)
+12V:     +12.57 V  (min = +12.82 V, max = +11.75 V)
-12V:     -11.14 V  (min =  -9.60 V, max = -11.74 V)
-5V:       -4.41 V  (min =  -3.64 V, max =  -2.61 V)
fan1:     10546 RPM  (min = 5335 RPM, div = 1)          ALARM
fan2:     5769 RPM  (min =    0 RPM, div = 1)
temp:     -128.00°C (hot: limit =  -1°C, hyst =  -1°C)
:                  (os:  limit =  +0°C, hyst =  -1°C)
alarms:   Board temperature input (LM75)               ALARM

```

please help me :|

Fixed i just had to reorganize the module order

---

### Post by f1dave on 2005-07-31
Sorry for listing yet another strange problem, but i set everything up, it worked beautifully and i got a lovely output of results when running sensors from console... But then upon rebooting I got a "fail" when the sensors tried to load- something about no limits set? And now i run sensors and get no output again! :S

Any ideas?

---

### Post by ankitrohatgi on 2005-08-13
I installed lm-sensors by apt-get install lm-sensors. It's working fine, but I get the following error at the boot up:

i2c_adapter i2c-0: Error: command never completed

(in 10 consecutive lines)

Please help.

Thanks,
Ankit

---

### Post by antoniost on 2005-08-14
I have almost done everything.
This is my output from "sensors-detect"

To make the sensors modules behave correctly, add these lines to
/etc/modules:

#----cut here----
# I2C adapter drivers
i2c-isa
# I2C chip drivers
w83627hf
#----cut here----

When i run "sensors"  , i take :

antonios@homepc:~$ sensors
eeprom-i2c-0-52
Adapter: SMBus I801 adapter at 0400
Memory type:            DDR SDRAM DIMM
Memory size (MB):       512


What must i put in /etc/modules  and in what order ,to make this thing work ?
What about with the "modprobe orders"  ? What is the correct sequence for this ?

Thanks , anyway.

---

### Post by GreyFox503 on 2005-08-14
I already have lm-sensors installed, but just a quick suggestion:  add a brief description at the beginning of the HOWTO that describes what the heck lm-sensors is.  If you didn't know what you're talking about, its not obvious, especially to a newbie.

---

### Post by bjweeks on 2005-08-14
Has anybody got lm-sensors to work on a Asus A8N-Sli

---

### Post by Slugger on 2005-08-14
[QUOTE=bjweeks]Has anybody got lm-sensors to work on a Asus A8N-Sli[/QUOTE]
 I havent gotten Im-sensors to work on a Asus A8N-Sli but maybe someone else has?

---

### Post by N8MAN1068 on 2005-08-23
couldn't get this to work on a Dell Latitude C840, even though commands like
acpi -t show cpu temps

---

### Post by floflooo on 2005-09-08
[QUOTE=N8MAN1068]couldn't get this to work on a Dell Latitude C840, even though commands like
acpi -t show cpu temps[/QUOTE]
 Same here for a Dell Latitude D600. I've tried the howto and the program sensors-detect didn't find any sensor.
I have done a bunch of research before posting and it's crazy that nobody can make lm_sensor work on Dell Laptops. :(

---

### Post by redmoon on 2005-09-14
i have a question (ubuntu noob)

after i run sensors-detect, i am asked if i want the module results to be added to the /etc/modules file automatically...should i answer 'yes' to this question, and if so, does that mean i dont have to add the modules in 'reverse' manually as the HOWTO says? I also don't really understand what you mean by add the modules in reverse either... could you shed some light please? I only ask because I am getting funny results.

Cheers.

---

### Post by kemosabe79 on 2005-09-28
Nice Howto! This is the first time Ive been able to get this to work on my n-Force2 chipset. Thanks alot!:)

---

### Post by John.Michael.Kane on 2005-09-28
this is the responce i get using acpi-t on a acer travelmate 290 centrino notebook. so what note books use lm- sensors
Battery 1: charged, 100%
No support for device type: thermal

---

### Post by casper_2095 on 2005-10-02
The script in the first step of this how-to creates a bunch of entries /dev/i2c-___

What? Why?

I ask because I skipped this on my Hoary + ASUS A8V Deluxe and it seems to be working (mods i2c-viapro + i2c-isa + w83627hf) but now I'm afraid I'm missing out on something. :rolleyes: 

Is this in the [english language] wiki anywhere?

---

### Post by floyd27 on 2005-10-12
Hi.
Just would like to know what in the conf. file I would have to change to get the right valuse to appear.
The current values are way off and i would like to set them.
I kow its a divider or multiplyer proble.

Its just that file is hudge and im not sure which ones to change..
These are what needs to be set..
m/b temp
cpu temp
fan speeds..
thanx

---

### Post by Unit #134679 on 2005-10-12
Great How To!

---

### Post by arunsub on 2005-10-15
I tried this in Breezy. I got the following errors:
sudo ./mkdev.sh
/dev/i2c-0
mknod: `/dev/i2c-0': File exists

$sensors-detect
 Sorry, no chips were detected.
 Either your sensors are not supported, or they are
 connected to an I2C bus adapter that we do not support.
 See doc/FAQ, doc/lm_sensors-FAQ.html, or
 [http://www2.lm-sensors.nu/~lm78/cvs/lm_sensors2/doc/lm_sensors-FAQ.html](http://www2.lm-sensors.nu/~lm78/cvs/lm_sensors2/doc/lm_sensors-FAQ.html)
 (FAQ #4.24.3) for further information.
 If you find out what chips are on your board, see
 [http://secure.netroedge.com/~lm78/newdrivers.html](http://secure.netroedge.com/~lm78/newdrivers.html) for driver status.

It worked fine in Hoary, but not in Breezy. I know it's hoary tips and tricks, but won't it work in breezy?

Edit: everything worked fine after i used sudo.

---

### Post by angrykeyboarder on 2005-10-16
All this for some little displays on my desktop.  Not worth it.  I'll wait a few years till it get's simpler.

And to think I thiought all I had to do was install lm_sensors to get that other stuff working....

---

### Post by Skatox on 2005-10-17
It doesn't work for me in Breezy, too.

---

### Post by JimmyJazz on 2005-10-18
no work for me in breezy HP pavilion zt3000

---

### Post by tschackomuizi on 2005-10-19
oke: i installed lm_sensors in breezy 5.10 on a A2K Asus Motherboard. this is a nforce3 board. should also work on nforce2 ones
the sensors work. i didn't use the how-to exactly.

starting with root all commands:

$: synaptic 
=> search for "lm_sensors" and install the package "wmtemp". this also
installs lm_sensors and all dependencies.

then detect your motherboard sensors with:

$: /usr/sbin/sensors-detect

type "YES" in each test. i got everything failed in "ISA" mode. so
In the end i choose "smbus". It will write some new lines in /etc/modules.

you can look in $: vim /etc/modules and see the added lines. 
now you must load all of these added modules separately

$: modprobe XXXX

after that, if you type now the command $: sensors you get fine output.


my question is now... how can i change the fanspeed manually? i want to let the fanspeed rotate at a specific speed, as i know from "speedfan" in windows, where it worked. yes, not exactly the RPM, but ti change the % how fast it is rotating. ACPI is supported in my motherboard, powernow, also working and activated.  which steps do i have to do for the manual control of the fanspeed?

---

### Post by yesplease on 2005-10-22
Thanks for your helpfull notes Tschackomuizi, I used them for a MSI  K8N Neo2 plat. motherboard,  nforce3. I got this output from sensors:

w83627thf-isa-0290
Adapter: ISA adapter
VCore:     +1.09 V  (min =  +1.93 V, max =  +1.93 V)
+12V:     +12.40 V  (min = +10.82 V, max = +13.19 V)
+3.3V:     +3.12 V  (min =  +3.14 V, max =  +3.47 V)       ALARM
+5V:       +4.93 V  (min =  +4.75 V, max =  +5.25 V)
-12V:     -14.91 V  (min = -10.80 V, max = -13.18 V)
V5SB:      +5.03 V  (min =  +4.76 V, max =  +5.24 V)
VBat:      +2.59 V  (min =  +2.40 V, max =  +3.60 V)
fan1:     5075 RPM  (min = 5232 RPM, div = 2)
CPU Fan:  3391 RPM  (min =   -1 RPM, div = 2)
fan3:        0 RPM  (min = 675000 RPM, div = 2)
M/B Temp:    +27&#176;C  (high =   +16&#176;C, hyst =    +0&#176;C)   sensor = thermistor 
CPU Temp:  +34.5&#176;C  (high =   +80&#176;C, hyst =   +75&#176;C)   sensor = diode
temp3:     +27.5&#176;C  (high =   +80&#176;C, hyst =   +75&#176;C)   sensor = thermistor 
vid:      +0.000 V  (VRM Version 9.0)
alarms:   Chassis intrusion detection                      ALARM
beep_enable:
          Sound alarm disabled

eeprom-i2c-0-51
Adapter: SMBus nForce2 adapter at 4c00
Memory type:            DDR SDRAM DIMM
Memory size (MB):       512

eeprom-i2c-0-50
Adapter: SMBus nForce2 adapter at 4c00
Memory type:            DDR SDRAM DIMM
Memory size (MB):       512

Not exactly what I expected because I chose SMbus output over ISA in sensors-detect, and the i2c drivers are for SMbus. Still most values are from isa.
The min and max values are sometimes strange, but it is a start.

Thanks again.

---

### Post by Klunk on 2005-10-24
I installed lm-sensors and ran sensors-detect (on breezy) and I am getting some strange results.

```
w83782d-i2c-0-2d
Adapter: SMBus AMD756 adapter at 50e0
VCore 1:   +1.76 V  (min =  +1.66 V, max =  +1.82 V)
VCore 2:   +2.48 V  (min =  +1.66 V, max =  +1.82 V)
+3.3V:     +3.31 V  (min =  +3.14 V, max =  +3.46 V)
+5V:       +4.95 V  (min =  +4.73 V, max =  +5.24 V)
+12V:     +12.28 V  (min = +10.82 V, max = +13.19 V)
-12V:     -11.95 V  (min = -13.18 V, max = -10.88 V)
-5V:       -5.00 V  (min =  -5.25 V, max =  -4.75 V)
V5SB:      +5.11 V  (min =  +4.73 V, max =  +5.24 V)
VBat:      +3.22 V  (min =  +2.40 V, max =  +3.60 V)
fan1:        0 RPM  (min = 2657 RPM, div = 2)
fan2:        0 RPM  (min = 2657 RPM, div = 2)
fan3:        0 RPM  (min =  664 RPM, div = 8)
temp1:       +34&#176;C  (high =    +0&#176;C, hyst =    +0&#176;C)   sensor = thermistor 
temp2:     +58.0&#176;C  (high =   +90&#176;C, hyst =   +88&#176;C)   sensor = thermistor 
temp3:    +127.5&#176;C  (high =   +80&#176;C, hyst =   +75&#176;C)   sensor = diode   ALARM
vid:      +1.750 V  (VRM Version 9.0)
alarms:   Chassis intrusion detection                      ALARM
beep_enable:
          Sound alarm disabled

eeprom-i2c-0-52
Adapter: SMBus AMD756 adapter at 50e0
Memory type:            SDR SDRAM DIMM
Memory size (MB):       256

eeprom-i2c-0-50
Adapter: SMBus AMD756 adapter at 50e0
Memory type:            SDR SDRAM DIMM
Memory size (MB):       256


```

My setup in an Gigabit GA-71XE4 motherboard with an Athlon 1GHz processor.

Clearly there must be something wrong wth the temperatures being displayed, and I don't understand why the fans are not showing any rpm.

Has anyone got any pointers for me?

EDIT - I found that temp3 is not used for AMD processors. It does not appear in my BIOS and I have no sensor for this, hence the strange results. I have ignored this in my sensors.conf. I still have one question though, my BIOS reports fan speeds and yet lm_sensors does not, does anyone have any idea why I am not getting anything for the fans?

---

### Post by dudus on 2005-11-17
[QUOTE=RJARRRPCGP]After I install **xsensors** and then ran it, why this?

rjarrrpcgp@ubuntu:~$ sudo -s
root@ubuntu:~# xsensors
Sensor 'it8712' not supported by xsensors!


Is the hardware monitoring chip really rare?  ](*,)

But, this is with Hoary! (I wished that they moved the lm-sensors topic to another forum)[/QUOTE]

It seems that the new versions supports it :

[http://www.linuxhardware.org/xsensors/CHANGELOG](http://www.linuxhardware.org/xsensors/CHANGELOG)

---

### Post by dudus on 2005-11-17
I've got some odd results from the sensor thing. Some values seems out f range, I think I should  tweek this in the conf file. The temp3 is disabled and I can't figure out how to enable it.

When I use xsensors, it says that my chip isn't supported (it8712). My verssion of xsensors is 0.46. In the developer website I read that xsensors 0.47 supports my chip. But this verssion hasn't made into the repos yet.

Not sure If I should install the package since I don't fell confartable installing something that isn't even in the backports.

> $sensors
it8712-isa-0290
Adapter: ISA adapter
VCore 1:   +1.76 V  (min =  +1.42 V, max =  +1.57 V)   ALARM
VCore 2:   +0.00 V  (min =  +2.40 V, max =  +2.61 V)   ALARM
+3.3V:     +6.72 V  (min =  +3.14 V, max =  +3.46 V)   ALARM
+5V:       +4.95 V  (min =  +4.76 V, max =  +5.24 V)
+12V:     +12.48 V  (min = +11.39 V, max = +12.61 V)   ALARM
-12V:     -27.36 V  (min = -12.63 V, max = -11.41 V)   ALARM
-5V:      -13.64 V  (min =  -5.26 V, max =  -4.77 V)   ALARM
Stdby:     +5.08 V  (min =  +4.76 V, max =  +5.24 V)
VBat:      +4.08 V
fan1:     3040 RPM  (min =    0 RPM, div = 2)
fan2:     2689 RPM  (min = 2657 RPM, div = 2)
fan3:        0 RPM  (min = 2657 RPM, div = 2)          ALARM
M/B Temp:    +48°C  (low  =   +15°C, high =   +40°C)   sensor = thermistor
CPU Temp:    +37°C  (low  =   +15°C, high =   +45°C)   sensor = thermistor
Temp3:        -1°C  (low  =   +15°C, high =   +45°C)   sensor = disabled


---

### Post by crag277 on 2005-11-22
First of all, great guide!  Everything works, except the version of lm_sensors that installs through apt-get is 2.9.1, and the version that contains the driver for my sensors (SMSC 47M15x/192) is 2.9.2.  Therefore, when I run sensors-detect it detects everything just fine, but simply says there is no driver for my hardware.  I have tried manually installing version 2.9.2, but I get nothing but errors.  Is there an easier way to maybe just install the module I need for this chip even though the rest of the package is version 2.9.1? Any ideas?

-Eric

---

### Post by crag277 on 2005-11-22
nevermind.  I checked more carefully this time, and the driver I need doesn't exist yet.  Looks like I need to wait.

---

### Post by Cuppa-Chino on 2005-11-23
hi thx for the guide, got mine to work nearly straight off the bat...

where can I mod the limits - my VCore show too high, my MOBO temp is always alarmed: 
```
w83627thf-isa-0290
Adapter: ISA adapter
VCore:     +1.60 V  (min =  +1.45 V, max =  +1.60 V)       ALARM
+12V:     +12.10 V  (min = +10.82 V, max = +13.19 V)
+3.3V:     +3.31 V  (min =  +3.14 V, max =  +3.47 V)
+5V:       +4.99 V  (min =  +4.75 V, max =  +5.25 V)
-12V:     -14.91 V  (min = -10.80 V, max = -13.18 V)
V5SB:      +4.97 V  (min =  +4.76 V, max =  +5.24 V)
VBat:      +0.00 V  (min =  +2.40 V, max =  +3.60 V)
fan1:        0 RPM  (min = 135000 RPM, div = 2)
CPU Fan:     0 RPM  (min =   -1 RPM, div = 2)
fan3:     1599 RPM  (min = 84375 RPM, div = 4)
M/B Temp:    +38°C  (high =   +33°C, hyst =    +0°C)   sensor = thermistor 
CPU Temp:  +30.5°C  (high =   +80°C, hyst =   +75°C)   sensor = thermistor 
temp3:     -48.0°C  (high =   +80°C, hyst =   +75°C)   sensor = thermistor 
vid:      +1.525 V  (VRM Version 9.0)
alarms:
beep_enable:
          Sound alarm enabled


```
but I am okay with for instance the MOBO temp.

also where is conf file for xsensors as my display a lot about the sensors that have 0 readings above?

thanks

---

### Post by Arandomcow5 on 2005-11-28
Excellant guide, thanks a lot

I needed this to test my processor temperatures (i over clocked my processor 30%, so now its running at 3.9GHz) I wanted to make sure that it was running acceptably, and it is, yay!

---

### Post by Cuppa-Chino on 2005-11-29
hi just thought I would "*bump*" my question wrt to the configuration of 

also where is conf file for xsensors as my display a lot about the sensors that have 0 readings above?

thanks

---

### Post by juantxorena on 2006-01-01
Here's my sensors-detect result: ```
#----cut here----
# I2C adapter drivers
i2c-nforce2
# I2C chip drivers
# Warning: the required module smbus-arp is not currently installed on your system.
# For status of 2.6 kernel ports see http://secure.netroedge.com/~lm78/supported.html
# If driver is built-in to the kernel, or unavailable, comment out the following line.
smbus-arp
#----cut here---- 
``` I've just compiled a new kernel, and I can't found anything related to smbus-arp. My motherboard is an ASUS A7N8X-E Deluxe, with a nForce2 chipset.
Any help?

---

### Post by Trev0r269 on 2006-02-10
i got the daunting msg, "No Sensors Found!" , but everything seemed to work ok. 

there was a prompt to add the needed lined to /etc/modules, and i chose yes. i didnt havent to add anything myself like the guide implied. maybe something went wrong here? also, i see /etc/modules but i cant cd into it. i get told it is not a directory.

---

### Post by lleberg on 2006-02-27
well, i think it worked.. But i have a small... error i think.

```
lleberg@margit:~$ sensors
it8712-isa-0290
Adapter: ISA adapter
VCore 1:   +1.09 V  (min =  +1.42 V, max =  +1.57 V)   ALARM
VCore 2:   +2.58 V  (min =  +2.40 V, max =  +2.61 V)
+3.3V:     +6.78 V  (min =  +3.14 V, max =  +3.46 V)   ALARM
+5V:       +4.27 V  (min =  +4.76 V, max =  +5.24 V)   ALARM
+12V:     +12.29 V  (min = +11.39 V, max = +12.61 V)
-12V:      -1.83 V  (min = -12.63 V, max = -11.41 V)   ALARM
-5V:       -5.26 V  (min =  -5.26 V, max =  -4.77 V)   ALARM
Stdby:     +2.63 V  (min =  +4.76 V, max =  +5.24 V)   ALARM
VBat:      +4.08 V
fan1:     3183 RPM  (min =    0 RPM, div = 8)
fan2:     1371 RPM  (min =  664 RPM, div = 8)
fan3:        0 RPM  (min =  664 RPM, div = 8)          ALARM
M/B Temp:    +25°C  (low  =   +15°C, high =   +40°C)   sensor = thermistor
CPU Temp:    +28°C  (low  =   +15°C, high =   +45°C)   sensor = thermistor
Temp3:       +69°C  (low  =   +15°C, high =   +45°C)   sensor = thermistor   ALARM
```

Sure, i'm running my amd64 at 28 degrees C! Right!
And where are temp3 measured? Shouldn't the cpu hotter than the others?

Edit: uh, is this a warty-howto?
Did i just do something.. stupid? :D

---

### Post by Trev0r269 on 2006-03-06
For step 2

Where is the lm-sensors source? 

I'm very new, and I'm trying hard to get this right.

---

### Post by henriquemaia on 2006-03-06
Worked flawlessly. Thanks a lot!

:KS

---

### Post by MaX on 2006-03-10
[QUOTE=Trev0r269]For step 2

Where is the lm-sensors source? 

I'm very new, and I'm trying hard to get this right.[/QUOTE]
You just copy the text begining with "#!/bin/bash" and ending with "#end of file"
 Into it's own file mkdev.sh and you make that runnable (rightclick select properties and run).
Then run the file.

---

### Post by negatron on 2006-03-22
Just a few questions with the installation, because I haven't got lm-sensors (or any other sensor program) working.

1. #sudo mbmon -dA
gives me the following:
SMBus[IntelPIIX4(440BX/MX)] found, but No HWM available on it!!

Does that mean that there are no sensors on my motherboard or have I just made something wrong? It also tells that mbmon needs "setuid root", whatever that means (running as sudo gives the same).

2. #sudo sensors-detect
No chips detected... That makes me think that maybe there just isn't any sensors on my mobo. :-| 

I've tried to run the script mentioned in the how to but still all I got is nothing.  So is there a way to make things work or am I just wasting time here? Could really use some help, I can't sleep with this problem ;)
And I am somewhat a n00b with Linux, so please be gentle...

---

### Post by fackamato on 2006-03-22
[QUOTE=negatron]Just a few questions with the installation, because I haven't got lm-sensors (or any other sensor program) working.

1. #sudo mbmon -dA
gives me the following:
SMBus[IntelPIIX4(440BX/MX)] found, but No HWM available on it!!

Does that mean that there are no sensors on my motherboard or have I just made something wrong? It also tells that mbmon needs "setuid root", whatever that means (running as sudo gives the same).

2. #sudo sensors-detect
No chips detected... That makes me think that maybe there just isn't any sensors on my mobo. :-| 

I've tried to run the script mentioned in the how to but still all I got is nothing.  So is there a way to make things work or am I just wasting time here? Could really use some help, I can't sleep with this problem ;)
And I am somewhat a n00b with Linux, so please be gentle...[/QUOTE]


Doesn't seem like your sensor chips is/are supported yet, or you don't have any. What motherboard/BIOS are you using?

---

### Post by jtp51 on 2006-03-26
So, stating the obvious:

# Generated by sensors-detect on Sat Mar 25 11:54:08 2006
# I2C adapter drivers
i2c-isa
# I2C chip drivers
# no driver for SMSC 47M15x/192 Super IO Fan Sensors yet

I guess my machine is too new to have lm-sensors work correctly?

MSI MS-7184 motherboard.
AMD Athlon 64 X2 3800+ processor.
Northbridge: ATI RS482 and Southbridge: ATI SB400 chipset.
1 GB Ramm

How often are drivers released?

Thanks,

---

### Post by mitjab on 2006-03-27
how to enable sound alarm

alarms:
beep_enable:
Sound alarm disabled

---

### Post by WelterPelter on 2006-03-30
I used this guide (for 64-bit Dapper) and it worked fine, until the reboot stage. Now sensors-detect can't find anything again!

---

### Post by henriquemaia on 2006-03-31
On my new system, an AMD64 dapper, sensors are not detected, unfortunately. Does anyone on amd64 have any ideas how to get this working?

---

### Post by WelterPelter on 2006-04-06
Tonight I downloaded the unofficial AMD-64 version of lm-sensors from debian [here]("http://packages.debian.org/stable/utils/lm-sensors").
After I installed it, Dapper's update thingy told me there was a new version available, which I installed. 
Then I went back through the sensor setup shown at the top of this thread.
Voila! $sensors:

w83627ehf-isa-0290
Adapter: ISA adapter
Case Fan:    0 RPM  (min = 1205 RPM, div = 32)
CPU Fan:  3183 RPM  (min = 1704 RPM, div = 8)
fan3:        0 RPM  (min =    0 RPM, div = 32)
fan4:        0 RPM  (min =    0 RPM, div = 4)
Sys Temp:    +27°C  (high =   +45°C, hyst =   +40°C)
CPU Temp:  +33.0°C  (high = +45.0°C, hyst = +40.0°C)
temp3:     -48.0°C  (high = +127.0°C, hyst = +127.0°C)
:cool::D

---

### Post by JackandJohn on 2006-05-07
Ok, I have a fun one:

I installed all the good stuff; works like a charm:

```
it8712-isa-0290
Adapter: ISA adapter
VCore 1:   +1.39 V  (min =  +1.42 V, max =  +1.57 V)   ALARM
VCore 2:   +2.58 V  (min =  +2.40 V, max =  +2.61 V)
+3.3V:     +6.62 V  (min =  +3.14 V, max =  +3.46 V)   ALARM
+5V:       +4.87 V  (min =  +4.76 V, max =  +5.24 V)
+12V:     +12.29 V  (min = +11.39 V, max = +12.61 V)
-12V:     -11.77 V  (min = -12.63 V, max = -11.41 V)   ALARM
-5V:       -1.86 V  (min =  -5.26 V, max =  -4.77 V)   ALARM
Stdby:     +2.10 V  (min =  +4.76 V, max =  +5.24 V)   ALARM
VBat:      +4.08 V
fan1:     4560 RPM  (min =    0 RPM, div = 8)
fan2:        0 RPM  (min = 3013 RPM, div = 8)
fan3:     1638 RPM  (min = 3013 RPM, div = 8)          ALARM
M/B Temp:    +25°C  (low  =   +15°C, high =   +40°C)   sensor = thermistor
CPU Temp:    +35°C  (low  =   +15°C, high =   +45°C)   sensor = thermistor
Temp3:        +3°C  (low  =   +15°C, high =   +45°C)   sensor = diode

```

NOW, problem is when the cpu modules load:

```
#----cut here for sensor probing----
# I2C adapter drivers
# modprobe unknown adapter bt878 #0 [sw]
it87
eeprom
i2c-isa
i2c-nforce2
# I2C chip drivers
#----cut here----

``` (reversed as per the howto)

I get my mobo speaker beeping at me CONSTANTLY.
Like, one continuous beep that starts when the module is loaded (not sure which one, but one of the above), and does not end until I power down.

Un-usable.


Any help is appreicated; possibly disabling the alarm? or even disable linux's access to that speaker altogether (less than optimal)

Thanks!

---

### Post by seanUSXIII on 2006-05-19
I use lm_sensors on dapper beta 2, and it only detects my cpu and case fans. It won't detect the CPU temp or case temp or anything like that. Speedfan can detect them just fine under windows. Is there any other program that maybe can control fan speeds automatically like speedfan?

---

### Post by CameronCalver on 2006-05-20
hey a noob question on the very first post oyou said mkdev.sh where is that script exactly?

---

### Post by Keith_Beef on 2006-05-31
[QUOTE=juantxorena]Here's my sensors-detect result: ```
#----cut here----
# I2C adapter drivers
i2c-nforce2
# I2C chip drivers
# Warning: the required module smbus-arp is not currently installed on your system.
# For status of 2.6 kernel ports see http://secure.netroedge.com/~lm78/supported.html
# If driver is built-in to the kernel, or unavailable, comment out the following line.
smbus-arp
#----cut here---- 
``` I've just compiled a new kernel, and I can't found anything related to smbus-arp. My motherboard is an ASUS A7N8X-E Deluxe, with a nForce2 chipset.
Any help?[/QUOTE]

I have the same mainboard, and I believe I had lm-sensors working on it with Mandrake 10.2, then Mandriva, both with 2.6 series kernels. I don't remember having any problems getting the sensors to work.

What is this smbus-arp module?

(A while ago, I had lm-sensors working with mandrake on an Abit BP6.)

Beef.

---

### Post by angrykeyboarder on 2006-05-31
Am I the only one that thinks step 1 is almost useless since it doesn't include steps 2-8?

Why do they bother with an installation program that doesn't configure anything?

Is it really worth all this for some geeky stuff on your desktop?

I lost complete interest in any sensors desktop stuff after seeing what a PITA this required package is.

Well at least you won't ever find yourself entering "sudo dpkg-reconfigure lm-sensors"

---

### Post by keithjr on 2006-06-11
Well, if anybody is interested, I got vt1211 to actually work for Dapper and display a sensor readout.  If anybody needs to know, PM me It doesn't help that the driver wasn't even included in the kernel even as high as 2.6.16.  It's useless, though.  The temp readout comes out completely wrong.  The default equation in their vt1211 chip section always comes out with a negative number, and I'd have to take some spreadsheet data to try to find the linear equation to convert the raw data because a simple scaling factor (+x, -x) won't do it.  Which means constantly restarting my system to read the correct values in the bios setup... yikes.  Oh, and every value generates and alarm for Proc. temp, even if it is below the temp_high value, which somehow changes every time I change the calculate statement for the associated temperature.  what the heck??

the people who make lm-sensors really need to get their act together.  A week of work to get to this point and then have to give up is depressing.

---

### Post by Evil Dax on 2006-06-12
I've upgraded from 5.10 to 6.06 this weekend, and now my fancontrol is stopped.
Sensors are OK:
```

w83627hf-isa-0290
Adapter: ISA adapter
VCore 1:   +1.62 V  (min =  +1.57 V, max =  +1.73 V)
VCore 2:   +2.62 V  (min =  +1.57 V, max =  +1.73 V)       ALARM
+3.3V:     +3.30 V  (min =  +3.14 V, max =  +3.47 V)
+5V:       +4.95 V  (min =  +4.76 V, max =  +5.24 V)
+12V:     +11.86 V  (min = +10.82 V, max = +13.19 V)
-12V:     -12.36 V  (min = -13.18 V, max = -10.80 V)
-5V:       -5.00 V  (min =  -5.25 V, max =  -4.75 V)
V5SB:      +5.46 V  (min =  +4.76 V, max =  +5.24 V)       ALARM
VBat:      +3.49 V  (min =  +2.40 V, max =  +3.60 V)
fan1:     2265 RPM  (min =    0 RPM, div = 4)
fan2:     4891 RPM  (min = 337500 RPM, div = 4)              ALARM
fan3:     5720 RPM  (min = 2836 RPM, div = 4)
temp1:       +47°C  (high =   +85°C, hyst =  +125°C)   sensor = thermistor 
temp2:     +58.0°C  (high =   +90°C, hyst =   +85°C)   sensor = thermistor      (beep)
temp3:     -48.0°C  (high =   +90°C, hyst =   +85°C)   sensor = thermistor 
vid:      +1.650 V  (VRM Version 9.0)
alarms:
beep_enable:
          Sound alarm enabled

```
But, when I run fancontrol:
```

Loading configuration from /etc/fancontrol ...

Common settings:
  INTERVAL=5

Settings for 2-0290/pwm2:
  Depends on 2-0290/temp1_input
  Controls 2-0290/fan1_input
  MINTEMP=40
  MAXTEMP=70
  MINSTART=50
  MINSTOP=50

Settings for 2-0290/pwm1:
  Depends on 2-0290/temp1_input
  Controls 2-0290/fan1_input
  MINTEMP=40
  MAXTEMP=70
  MINSTART=50
  MINSTOP=50

Settings for 9191-0290/pwm2:
  Depends on 9191-0290/temp1_input
  Controls 9191-0290/fan2_input
  MINTEMP=0
  MAXTEMP=70
  MINSTART=150
  MINSTOP=100

Settings for 9191-0290/pwm1:
  Depends on 9191-0290/temp1_input
  Controls 9191-0290/fan1_input
  MINTEMP=0
  MAXTEMP=70
  MINSTART=150
  MINSTOP=100

Enabling PWM on fans...
Starting automatic fan control...
cat: 2-0290/temp1_input: No such file or directory
Error reading temperature from /sys/bus/i2c/devices/2-0290/temp1_input
Aborting, restoring fans...
/usr/sbin/fancontrol: line 123: 2-0290/pwm2: No such file or directory
/usr/sbin/fancontrol: line 123: 2-0290/pwm1: No such file or directory
Verify fans have returned to full speed

```


Can anybody see what I've got wrong here?

---

### Post by maddbaron on 2006-06-12
ok this is wayyy over my head lol can someone break it down please?

i installed this program from synaptic when i boot it fails to start.

what do i type in terminal to set it all up?

---

### Post by BoomAM on 2006-06-13
Same as above.
The 'guide' isnt the best segmented and isnt the clearest as to whats ment to go in files and whats 'chat'. Good atempt though.
But regardless, im having nothing but problems.

Hows about a simplifed/clear guide for us n00bs? :)

---

### Post by mdecandia on 2006-06-16
Hi All,
I've installed Ubuntu 6.06 on Hp nx8220. I have some problem with sensors. 
I followed this how-to [https://wiki.ubuntu.com/SensorInstallHowto?highlight=%28sensors%29](https://wiki.ubuntu.com/SensorInstallHowto?highlight=%28sensors%29) 

and sensors-detect have found this sensors:

-------------------------------------------------------------------------
ds1621-i2c-1-4f
Adapter: SMBus stub driver
temp:      +0.00°C  (low  =  +0.0°C, high =  +0.0°C)

ds1621-i2c-1-4e
Adapter: SMBus stub driver
temp:      +0.00°C  (low  =  +0.0°C, high =  +0.0°C)

ds1621-i2c-1-4d
Adapter: SMBus stub driver
temp:      +0.00°C  (low  =  +0.0°C, high =  +0.0°C)

ds1621-i2c-1-4c
Adapter: SMBus stub driver
temp:      +0.00°C  (low  =  +0.0°C, high =  +0.0°C)

lm92-i2c-1-4b
Adapter: SMBus stub driver
CPU Temp: +0.0000°C (high = +0.0000°C, low = +0.0000°C, crit = +0.0000°C, hyst = +0.0000°C)

lm92-i2c-1-4a
Adapter: SMBus stub driver
CPU Temp: +0.0000°C (high = +0.0000°C, low = +0.0000°C, crit = +0.0000°C, hyst = +0.0000°C)

lm92-i2c-1-49
Adapter: SMBus stub driver
CPU Temp: +0.0000°C (high = +0.0000°C, low = +0.0000°C, crit = +0.0000°C, hyst = +0.0000°C)

lm92-i2c-1-48
Adapter: SMBus stub driver
CPU Temp: +0.0000°C (high = +0.0000°C, low = +0.0000°C, crit = +0.0000°C, hyst = +0.0000°C)
-------------------------------------------------------------------------


As you can see the problem is that all sensors gives 0 and also limits are null.
Do you have this problem? Any Idea?

Thanks 
Michele De Candia

---

### Post by BoomAM on 2006-06-16
I followed the above guide as well, but im getting different problems.
I copyed that data into a txt file, saved it as mkdev.sh, saved it in home.
Ran 'chmod 755 mkdev.sh' from terminal.
Then ran './mkdev.sh'
It then chucked out a loat of '/dev.i2c-number' things, from 0-31.
I then did 'sensors-detect', said yes to the first question, and then it just errors saying 'no chips were detected'.

Ideas?

##EDIT##
I tryed doing 'sudo sensors-detect' and got a series of Y/N questions, as the guide says, i answered yes to them all, but now i just get the same as i got before, an error.

Heres what i do in terminal:
```
boomam@boomam-laptop:~$ chmod 755 mkdev.sh
boomam@boomam-laptop:~$ ./mkdev.sh
/dev/i2c-0
mknod: `/dev/i2c-0': Permission denied
boomam@boomam-laptop:~$ sudo ./mkdev.sh
/dev/i2c-0
/dev/i2c-1
/dev/i2c-2
/dev/i2c-3
/dev/i2c-4
/dev/i2c-5
/dev/i2c-6
/dev/i2c-7
/dev/i2c-8
/dev/i2c-9
/dev/i2c-10
/dev/i2c-11
/dev/i2c-12
/dev/i2c-13
/dev/i2c-14
/dev/i2c-15
/dev/i2c-16
/dev/i2c-17
/dev/i2c-18
/dev/i2c-19
/dev/i2c-20
/dev/i2c-21
/dev/i2c-22
/dev/i2c-23
/dev/i2c-24
/dev/i2c-25
/dev/i2c-26
/dev/i2c-27
/dev/i2c-28
/dev/i2c-29
/dev/i2c-30
/dev/i2c-31
boomam@boomam-laptop:~$ sudo sensors-detect
# sensors-detect revision 1.393 (2005/08/30 18:51:18)

This program will help you determine which I2C/SMBus modules you need to
load to use lm_sensors most effectively. You need to have i2c and
lm_sensors installed before running this program.
Also, you need to be `root', or at least have access to the /dev/i2c-*
files, for most things.
If you have patched your kernel and have some drivers built in, you can
safely answer NO if asked to load some modules. In this case, things may
seem a bit confusing, but they will still work.

It is generally safe and recommended to accept the default answers to all
questions, unless you know what you're doing.

 We can start with probing for (PCI) I2C or SMBus adapters.
 You do not need any special privileges for this.
 Do you want to probe now? (YES/no): y
Probing for PCI bus adapters...
Use driver `i2c-i801' for device 00:1f.3: Intel 82801FB ICH6
Probe succesfully concluded.

We will now try to load each adapter module in turn.
Module `i2c-i801' already loaded.
If you have undetectable or unsupported adapters, you can have them
scanned by manually loading the modules before running this script.

 To continue, we need module `i2c-dev' to be loaded.
 If it is built-in into your kernel, you can safely skip this.
i2c-dev is already loaded.

 We are now going to do the adapter probings. Some adapters may hang halfway
 through; we can't really help that. Also, some chips will be double detected;
 we choose the one with the highest confidence value in that case.
 If you found that the adapter hung after probing a certain address, you can
 specify that address to remain unprobed. That often
 includes address 0x69 (clock chip).

Next adapter: SMBus I801 adapter at 18a0
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x08
Client found at address 0x44
Probing for `Maxim MAX6633/MAX6634/MAX6635'... Failed!
Client found at address 0x5c

Some chips are also accessible through the ISA bus. ISA probes are
typically a bit more dangerous, as we have to write to I/O ports to do
this. This is usually safe though.

Do you want to scan the ISA bus? (YES/no): y
Probing for `National Semiconductor LM78'
  Trying address 0x0290... Failed!
Probing for `National Semiconductor LM78-J'
  Trying address 0x0290... Failed!
Probing for `National Semiconductor LM79'
  Trying address 0x0290... Failed!
Probing for `Winbond W83781D'
  Trying address 0x0290... Failed!
Probing for `Winbond W83782D'
  Trying address 0x0290... Failed!
Probing for `Winbond W83627HF'
  Trying address 0x0290... Failed!
Probing for `Winbond W83627EHF'
  Trying address 0x0290... Failed!
Probing for `Winbond W83697HF'
  Trying address 0x0290... Failed!
Probing for `Silicon Integrated Systems SIS5595'
  Trying general detect... Failed!
Probing for `VIA Technologies VT82C686 Integrated Sensors'
  Trying general detect... Failed!
Probing for `VIA Technologies VT8231 Integrated Sensors'
  Trying general detect... Failed!
Probing for `ITE IT8712F'
  Trying address 0x0290... Failed!
Probing for `ITE IT8705F / SiS 950'
  Trying address 0x0290... Failed!
Probing for `IPMI BMC KCS'
  Trying address 0x0ca0... Failed!
Probing for `IPMI BMC SMIC'
  Trying address 0x0ca8... Failed!

Some Super I/O chips may also contain sensors. Super I/O probes are
typically a bit more dangerous, as we have to write to I/O ports to do
this. This is usually safe though.

Do you want to scan for Super I/O sensors? (YES/no): y
Probing for `ITE 8702F Super IO Sensors'
  Failed! (skipping family)
Probing for `Nat. Semi. PC87351 Super IO Fan Sensors'
  Failed! (skipping family)
Probing for `SMSC 47B27x Super IO Fan Sensors'
  Failed! (skipping family)
Probing for `VT1211 Super IO Sensors'
  Failed! (skipping family)
Probing for `Winbond W83627EHF/EHG Super IO Sensors'
  Failed! (skipping family)

Do you want to scan for secondary Super I/O sensors? (YES/no): y
Probing for `ITE 8702F Super IO Sensors'
  Failed! (skipping family)
Probing for `Nat. Semi. PC87351 Super IO Fan Sensors'
  Failed! (skipping family)
Probing for `SMSC 47B27x Super IO Fan Sensors'
  Failed! (skipping family)
Probing for `VT1211 Super IO Sensors'
  Failed! (skipping family)
Probing for `Winbond W83627EHF/EHG Super IO Sensors'
  Failed! (skipping family)

 Sorry, no chips were detected.
 Either your sensors are not supported, or they are
 connected to an I2C bus adapter that we do not support.
 See doc/FAQ, doc/lm_sensors-FAQ.html, or
 http://www2.lm-sensors.nu/~lm78/cvs/lm_sensors2/doc/lm_sensors-FAQ.html
 (FAQ #4.24.3) for further information.
 If you find out what chips are on your board, see
 http://secure.netroedge.com/~lm78/newdrivers.html for driver status.
boomam@boomam-laptop:~$
```

---

### Post by digitalkarabao on 2006-06-16
lm-sensors is installed but whenever i run sensors-detect and answers yes to the questions..i receive the log below.

i was able to run lm-sensors unser breezy before.

```

auric@digitalpenguin:~$ su
Password:
root@digitalpenguin:/home/auric# sensors-detect
# sensors-detect revision 1.393 (2005/08/30 18:51:1

This program will help you determine which I2C/SMBus modules you need to
load to use lm_sensors most effectively. You need to have i2c and
lm_sensors installed before running this program.
Also, you need to be `root', or at least have access to the /dev/i2c-*
files, for most things.
If you have patched your kernel and have some drivers built in, you can
safely answer NO if asked to load some modules. In this case, things may
seem a bit confusing, but they will still work.

It is generally safe and recommended to accept the default answers to all
questions, unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
You do not need any special privileges for this.
Do you want to probe now? (YES/no):
Probing for PCI bus adapters...
Use driver `i2c-sis96x' for device 00:02.1: Silicon Integrated Systems SMBus Controller
Probe succesfully concluded.

We will now try to load each adapter module in turn.
Module `i2c-sis96x' already loaded.
If you have undetectable or unsupported adapters, you can have them
scanned by manually loading the modules before running this script.

To continue, we need module `i2c-dev' to be loaded.
If it is built-in into your kernel, you can safely skip this.
i2c-dev is already loaded.

We are now going to do the adapter probings. Some adapters may hang halfway
through; we can't really help that. Also, some chips will be double detected;
we choose the one with the highest confidence value in that case.
If you found that the adapter hung after probing a certain address, you can
specify that address to remain unprobed. That often
includes address 0x69 (clock chip).

Next adapter: SiS96x SMBus adapter at 0x0c00
Do you want to scan it? (YES/no/selectively):
Client found at address 0x08
Client found at address 0x10
Client found at address 0x30
Client found at address 0x31
Client at address 0x50 can not be probed - unload all client drivers first!
Client at address 0x51 can not be probed - unload all client drivers first!

Some chips are also accessible through the ISA bus. ISA probes are
typically a bit more dangerous, as we have to write to I/O ports to do
this. This is usually safe though.

Do you want to scan the ISA bus? (YES/no):
Probing for `National Semiconductor LM78'
Trying address 0x0290... Failed!
Probing for `National Semiconductor LM78-J'
Trying address 0x0290... Failed!
Probing for `National Semiconductor LM79'
Trying address 0x0290... Failed!
Probing for `Winbond W83781D'
Trying address 0x0290... Failed!
Probing for `Winbond W83782D'
Trying address 0x0290... Failed!
Probing for `Winbond W83627HF'
Trying address 0x0290... Failed!
Probing for `Winbond W83627EHF'
Trying address 0x0290... Failed!
Probing for `Winbond W83697HF'
Trying address 0x0290... Failed!
Probing for `Silicon Integrated Systems SIS5595'
Trying general detect... Failed!
Probing for `VIA Technologies VT82C686 Integrated Sensors'
Trying general detect... Failed!
Probing for `VIA Technologies VT8231 Integrated Sensors'
Trying general detect... Failed!
Probing for `ITE IT8712F'
Trying address 0x0290... Failed!
Probing for `ITE IT8705F / SiS 950'
Trying address 0x0290... Failed!
Probing for `IPMI BMC KCS'
Trying address 0x0ca0... Failed!
Probing for `IPMI BMC SMIC'
Trying address 0x0ca8... Failed!

Some Super I/O chips may also contain sensors. Super I/O probes are
typically a bit more dangerous, as we have to write to I/O ports to do
this. This is usually safe though.

Do you want to scan for Super I/O sensors? (YES/no):
Probing for `ITE 8702F Super IO Sensors'
Failed! (0xea11)
Probing for `ITE 8705F Super IO Sensors'
Failed! (0xea11)
Probing for `ITE 8712F Super IO Sensors'
Failed! (0xea11)
Probing for `Nat. Semi. PC87351 Super IO Fan Sensors'
Failed! (0xea)
Probing for `Nat. Semi. PC87360 Super IO Fan Sensors'
Failed! (0xea)
Probing for `Nat. Semi. PC87363 Super IO Fan Sensors'
Failed! (0xea)
Probing for `Nat. Semi. PC87364 Super IO Fan Sensors'
Failed! (0xea)
Probing for `Nat. Semi. PC87365 Super IO Fan Sensors'
Failed! (0xea)
Probing for `Nat. Semi. PC87365 Super IO Voltage Sensors'
Failed! (0xea)
Probing for `Nat. Semi. PC87365 Super IO Thermal Sensors'
Failed! (0xea)
Probing for `Nat. Semi. PC87366 Super IO Fan Sensors'
Failed! (0xea)
Probing for `Nat. Semi. PC87366 Super IO Voltage Sensors'
Failed! (0xea)
Probing for `Nat. Semi. PC87366 Super IO Thermal Sensors'
Failed! (0xea)
Probing for `Nat. Semi. PC87372 Super IO Fan Sensors'
Failed! (0xea)
Probing for `Nat. Semi. PC87373 Super IO Fan Sensors'
Failed! (0xea)
Probing for `Nat. Semi. PC87591 Super IO'
Failed! (0xea)
Probing for `Nat. Semi. PC87371 Super IO'
Failed! (0xea)
Probing for `Nat. Semi. PC97371 Super IO'
Failed! (0xea)
Probing for `Nat. Semi. PC8739x Super IO'
Success... (no hardware monitoring capabilities)
Probing for `Nat. Semi. PC8741x Super IO'
Failed! (0xea)
Probing for `Nat. Semi. PCPC87427 Super IO'
Failed! (0xea)
Probing for `SMSC 47B27x Super IO Fan Sensors'
Failed! (0xea)
Probing for `SMSC 47M10x/13x Super IO Fan Sensors'
Failed! (0xea)
Probing for `SMSC 47M14x Super IO Fan Sensors'
Failed! (0xea)
Probing for `SMSC 47M15x/192 Super IO Fan Sensors'
Failed! (0xea)
Probing for `SMSC 47S42x Super IO Fan Sensors'
Failed! (0xea)
Probing for `SMSC 47S45x Super IO Fan Sensors'
Failed! (0xea)
Probing for `SMSC 47M172 Super IO'
Failed! (0xea)
Probing for `SMSC LPC47B397-NC Super IO'
Failed! (0xea)
Probing for `VT1211 Super IO Sensors'
Failed! (0xea)
Probing for `Winbond W83627HF Super IO Sensors'
Failed! (0xea)
Probing for `Winbond W83627THF Super IO Sensors'
Failed! (0xea)
Probing for `Winbond W83637HF Super IO Sensors'
Failed! (0xea)
Probing for `Winbond W83687THF Super IO Sensors'
Failed! (0xea)
Probing for `Winbond W83697HF Super IO Sensors'
Failed! (0xea)
Probing for `Winbond W83697SF/UF Super IO PWM'
Failed! (0xea)
Probing for `Winbond W83L517D Super IO'
Failed! (0xea)
Probing for `Winbond W83627EHF/EHG Super IO Sensors'
Failed! (0xea11)

Do you want to scan for secondary Super I/O sensors? (YES/no):
Probing for `ITE 8702F Super IO Sensors'
Failed! (0xec11)
Probing for `ITE 8705F Super IO Sensors'
Failed! (0xec11)
Probing for `ITE 8712F Super IO Sensors'
Failed! (0xec11)
Probing for `Nat. Semi. PC87351 Super IO Fan Sensors'
Failed! (0xec)
Probing for `Nat. Semi. PC87360 Super IO Fan Sensors'
Failed! (0xec)
Probing for `Nat. Semi. PC87363 Super IO Fan Sensors'
Failed! (0xec)
Probing for `Nat. Semi. PC87364 Super IO Fan Sensors'
Failed! (0xec)
Probing for `Nat. Semi. PC87365 Super IO Fan Sensors'
Failed! (0xec)
Probing for `Nat. Semi. PC87365 Super IO Voltage Sensors'
Failed! (0xec)
Probing for `Nat. Semi. PC87365 Super IO Thermal Sensors'
Failed! (0xec)
Probing for `Nat. Semi. PC87366 Super IO Fan Sensors'
Failed! (0xec)
Probing for `Nat. Semi. PC87366 Super IO Voltage Sensors'
Failed! (0xec)
Probing for `Nat. Semi. PC87366 Super IO Thermal Sensors'
Failed! (0xec)
Probing for `Nat. Semi. PC87372 Super IO Fan Sensors'
Failed! (0xec)
Probing for `Nat. Semi. PC87373 Super IO Fan Sensors'
Failed! (0xec)
Probing for `Nat. Semi. PC87591 Super IO'
Success... but not activated
Probing for `Nat. Semi. PC87371 Super IO'
Failed! (0xec)
Probing for `Nat. Semi. PC97371 Super IO'
Failed! (0xec)
Probing for `Nat. Semi. PC8739x Super IO'
Failed! (0xec)
Probing for `Nat. Semi. PC8741x Super IO'
Failed! (0xec)
Probing for `Nat. Semi. PCPC87427 Super IO'
Failed! (0xec)
Probing for `SMSC 47B27x Super IO Fan Sensors'
Failed! (0xec)
Probing for `SMSC 47M10x/13x Super IO Fan Sensors'
Failed! (0xec)
Probing for `SMSC 47M14x Super IO Fan Sensors'
Failed! (0xec)
Probing for `SMSC 47M15x/192 Super IO Fan Sensors'
Failed! (0xec)
Probing for `SMSC 47S42x Super IO Fan Sensors'
Failed! (0xec)
Probing for `SMSC 47S45x Super IO Fan Sensors'
Failed! (0xec)
Probing for `SMSC 47M172 Super IO'
Failed! (0xec)
Probing for `SMSC LPC47B397-NC Super IO'
Failed! (0xec)
Probing for `VT1211 Super IO Sensors'
Failed! (0xec)
Probing for `Winbond W83627HF Super IO Sensors'
Failed! (0xec)
Probing for `Winbond W83627THF Super IO Sensors'
Failed! (0xec)
Probing for `Winbond W83637HF Super IO Sensors'
Failed! (0xec)
Probing for `Winbond W83687THF Super IO Sensors'
Failed! (0xec)
Probing for `Winbond W83697HF Super IO Sensors'
Failed! (0xec)
Probing for `Winbond W83697SF/UF Super IO PWM'
Failed! (0xec)
Probing for `Winbond W83L517D Super IO'
Failed! (0xec)
Probing for `Winbond W83627EHF/EHG Super IO Sensors'
Failed! (0xec11)

Sorry, no chips were detected.
Either your sensors are not supported, or they are
connected to an I2C bus adapter that we do not support.
```

help guys. this is the only bump i hit after installing dapper. everything is working fine.

---

### Post by BoomAM on 2006-06-16
Ive done some searching around and aparentely theres rumors that the lm-sensors software isnt recommended for laptops, especially Thinkpads. Because they dont use sensors in the traditional sence, they access them via ACPI.
Can anyone confirm that:?:

---

### Post by Trev0r269 on 2006-07-01
2. Run the mkdev.sh script in the lm-sensors source

Where is the lm-sensors source?

---

### Post by eldaria on 2006-07-05
[http://www.lm-sensors.org/](http://www.lm-sensors.org/)

---

### Post by cblanquer on 2006-07-09
Hi,

Regarding "smbus-arp" I think it is a bug or a bad explanation form "lm-sensors".
Unless I made a mistake, it is loaded under "i2c-core", i.e. execute "sudo modprobe i2c-core" to get it loaded.

I did so and then the message regarding smbus-arp did not figure anymore and additional data were available.

(If I am wrong pease post)

---

### Post by cblanquer on 2006-07-09
Juantxorena,

Check my later on the thread - I guess it is a part of "i2c-core".

---

### Post by theturner on 2006-07-13
A seemingly simple question: What does "SBr Temp" mean? I couldn't find anything about it on the lm-sensors home page...

---

### Post by ExMachina on 2006-08-12
A few questions..

This is wokring for me.

exmachina@ExMachina:~$ sensors
No sensors found!
exmachina@ExMachina:~$ sudo sensors
Password:
No sensors found!
exmachina@ExMachina:~$

is there a gui for this?
my laptop temp is usally 130 but can get up to 155.. kinda worries me

---

### Post by atze76 on 2006-08-13
I have managed to install lm-sensors on my laptop (running kubuntu dapper). After I have followed the steps described in this how-to and rebooted my system, the cpu utilization increased to almost 100%. Most of the cpu time is consumed by kacpid. I didn't have this problem before.
Now I have uninstalled the whole lm-sensors package (using synaptic) but one of the how-to steps must have left a permanent modification, which causes kacpid to use 100% cpu time.
Even the whole boot process is slow now, it take 5-10 times longer. I had to disable acpi (kernel parameter: acpi=off) in order to be able to boot faster.
Can anyone imagine, which step has to be undone to avoid this freaky behaviour of kacpid.

---

### Post by mark_v_torres on 2006-08-15
I had the same problem. And the strange thing is, it also happens when I boot to Windows. I tried resetting to the default BIOS settings and that seemed to fix the issue.

---

### Post by LKRaider on 2006-08-22
For everyone using lm-sensors on Gnome, install the **sensors-applet** package.
It will place the sensors info on your Gnome panel and allow you to configure alarm levels and so on.

[Screenshot of sensors-applet here on my pc](http://lkraider.eipper.com.br/files/pub/sensors-applet.jpg)

Very handy :)

---

### Post by Cuppa-Chino on 2006-08-22
> **LKRaider said:**
> For everyone using lm-sensors on Gnome, install the **sensors-applet** package.
It will place the sensors info on your Gnome panel and allow you to configure alarm levels and so on.
Very handy :)

[INDENT]*embarrassing... how do I start them????*[/INDENT]

Found it! [http://www.ubuntuforums.org/archive/index.php/t-92504.html]("http://www.ubuntuforums.org/archive/index.php/t-92504.html")

---

### Post by mordox on 2006-08-25
I have intel 845GVSR board and i have recently installed Ubuntu 6.06LTS

I tried to configure lm-sensors as explained above. I tried the following

rivo@Xcc:~$ sudo sensors-detect
Password:
No i2c device files found. Use prog/mkdev/mkdev.sh to create them.
rivo@Xcc:~$ cd Desktop/
rivo@Xcc:~/Desktop$ chmod 755 mkdev.sh
rivo@Xcc:~/Desktop$ sudo ./mkdev.sh
/dev/i2c-0
/dev/i2c-1
/dev/i2c-2
/dev/i2c-3
/dev/i2c-4
/dev/i2c-5
/dev/i2c-6
/dev/i2c-7
/dev/i2c-8
/dev/i2c-9
/dev/i2c-10
/dev/i2c-11
/dev/i2c-12
/dev/i2c-13
/dev/i2c-14
/dev/i2c-15
/dev/i2c-16
/dev/i2c-17
/dev/i2c-18
/dev/i2c-19
/dev/i2c-20
/dev/i2c-21
/dev/i2c-22
/dev/i2c-23
/dev/i2c-24
/dev/i2c-25
/dev/i2c-26
/dev/i2c-27
/dev/i2c-28
/dev/i2c-29
/dev/i2c-30
/dev/i2c-31
rivo@Xcc:~/Desktop$ sudo sensors-detect
# sensors-detect revision 1.393 (2005/08/30 18:51:18)

This program will help you determine which I2C/SMBus modules you need to
load to use lm_sensors most effectively. You need to have i2c and
lm_sensors installed before running this program.
Also, you need to be `root', or at least have access to the /dev/i2c-*
files, for most things.
If you have patched your kernel and have some drivers built in, you can
safely answer NO if asked to load some modules. In this case, things may
seem a bit confusing, but they will still work.

It is generally safe and recommended to accept the default answers to all
questions, unless you know what you're doing.

 We can start with probing for (PCI) I2C or SMBus adapters.
 You do not need any special privileges for this.
 Do you want to probe now? (YES/no): y
Probing for PCI bus adapters...
Use driver `i2c-i801' for device 00:1f.3: Intel 82801DB ICH4
Probe succesfully concluded.

We will now try to load each adapter module in turn.
Load `i2c-i801' (say NO if built into your kernel)? (YES/no): n
If you have undetectable or unsupported adapters, you can have them
scanned by manually loading the modules before running this script.

 To continue, we need module `i2c-dev' to be loaded.
 If it is built-in into your kernel, you can safely skip this.
 i2c-dev is not loaded. Do you want to load it now? (YES/no): y
 Module loaded succesfully.

 We are now going to do the adapter probings. Some adapters may hang halfway
 through; we can't really help that. Also, some chips will be double detected;
 we choose the one with the highest confidence value in that case.
 If you found that the adapter hung after probing a certain address, you can
 specify that address to remain unprobed. That often
 includes address 0x69 (clock chip).

Next adapter: I810/I815 DDC Adapter
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x37
Client found at address 0x50
Probing for `SPD EEPROM'... Success!
    (confidence 1, driver `eeprom')
Probing for `DDC monitor'... Success!
    (confidence 8, driver `eeprom'), other addresses: 0x51 0x52 0x53 0x54 0x55 0 x56 0x57
Probing for `Maxim MAX6900'... Failed!
Client found at address 0x51
Probing for `SPD EEPROM'... Success!
    (confidence 1, driver `eeprom')
Client found at address 0x52
Probing for `SPD EEPROM'... Success!
    (confidence 1, driver `eeprom')
Client found at address 0x53
Probing for `SPD EEPROM'... Success!
    (confidence 1, driver `eeprom')
Client found at address 0x54
Probing for `SPD EEPROM'... Success!
    (confidence 1, driver `eeprom')
Client found at address 0x55
Probing for `SPD EEPROM'... Success!
    (confidence 1, driver `eeprom')
Client found at address 0x56
Probing for `SPD EEPROM'... Success!
    (confidence 1, driver `eeprom')
Client found at address 0x57
Probing for `SPD EEPROM'... Success!
    (confidence 1, driver `eeprom')
Probing for `Sony Vaio EEPROM'... Failed!

Next adapter: I810/I815 I2C Adapter
Do you want to scan it? (YES/no/selectively): y

Some chips are also accessible through the ISA bus. ISA probes are
typically a bit more dangerous, as we have to write to I/O ports to do
this. This is usually safe though.

Do you want to scan the ISA bus? (YES/no): y
Probing for `National Semiconductor LM78'
  Trying address 0x0290... Failed!
Probing for `National Semiconductor LM78-J'
  Trying address 0x0290... Failed!
Probing for `National Semiconductor LM79'
  Trying address 0x0290... Failed!
Probing for `Winbond W83781D'
  Trying address 0x0290... Failed!
Probing for `Winbond W83782D'
  Trying address 0x0290... Failed!
Probing for `Winbond W83627HF'
  Trying address 0x0290... Failed!
Probing for `Winbond W83627EHF'
  Trying address 0x0290... Failed!
Probing for `Winbond W83697HF'
  Trying address 0x0290... Failed!
Probing for `Silicon Integrated Systems SIS5595'
  Trying general detect... Failed!
Probing for `VIA Technologies VT82C686 Integrated Sensors'
  Trying general detect... Failed!
Probing for `VIA Technologies VT8231 Integrated Sensors'
  Trying general detect... Failed!
Probing for `ITE IT8712F'
  Trying address 0x0290... Failed!
Probing for `ITE IT8705F / SiS 950'
  Trying address 0x0290... Failed!
Probing for `IPMI BMC KCS'
  Trying address 0x0ca0... Failed!
Probing for `IPMI BMC SMIC'
  Trying address 0x0ca8... Failed!

Some Super I/O chips may also contain sensors. Super I/O probes are
typically a bit more dangerous, as we have to write to I/O ports to do
this. This is usually safe though.

Do you want to scan for Super I/O sensors? (YES/no): y
Probing for `ITE 8702F Super IO Sensors'
  Failed! (0x1404)
Probing for `ITE 8705F Super IO Sensors'
  Failed! (0x1404)
Probing for `ITE 8712F Super IO Sensors'
  Failed! (0x1404)
Probing for `Nat. Semi. PC87351 Super IO Fan Sensors'
  Failed! (0x14)
Probing for `Nat. Semi. PC87360 Super IO Fan Sensors'
  Failed! (0x14)
Probing for `Nat. Semi. PC87363 Super IO Fan Sensors'
  Failed! (0x14)
Probing for `Nat. Semi. PC87364 Super IO Fan Sensors'
  Failed! (0x14)
Probing for `Nat. Semi. PC87365 Super IO Fan Sensors'
  Failed! (0x14)
Probing for `Nat. Semi. PC87365 Super IO Voltage Sensors'
  Failed! (0x14)
Probing for `Nat. Semi. PC87365 Super IO Thermal Sensors'
  Failed! (0x14)
Probing for `Nat. Semi. PC87366 Super IO Fan Sensors'
  Failed! (0x14)
Probing for `Nat. Semi. PC87366 Super IO Voltage Sensors'
  Failed! (0x14)
Probing for `Nat. Semi. PC87366 Super IO Thermal Sensors'
  Failed! (0x14)
Probing for `Nat. Semi. PC87372 Super IO Fan Sensors'
  Failed! (0x14)
Probing for `Nat. Semi. PC87373 Super IO Fan Sensors'
  Failed! (0x14)
Probing for `Nat. Semi. PC87591 Super IO'
  Failed! (0x14)
Probing for `Nat. Semi. PC87371 Super IO'
  Failed! (0x14)
Probing for `Nat. Semi. PC97371 Super IO'
  Failed! (0x14)
Probing for `Nat. Semi. PC8739x Super IO'
  Failed! (0x14)
Probing for `Nat. Semi. PC8741x Super IO'
  Failed! (0x14)
Probing for `Nat. Semi. PCPC87427 Super IO'
  Failed! (0x14)
Probing for `SMSC 47B27x Super IO Fan Sensors'
  Failed! (0x14)
Probing for `SMSC 47M10x/13x Super IO Fan Sensors'
  Failed! (0x14)
Probing for `SMSC 47M14x Super IO Fan Sensors'
  Failed! (0x14)
Probing for `SMSC 47M15x/192 Super IO Fan Sensors'
  Failed! (0x14)
Probing for `SMSC 47S42x Super IO Fan Sensors'
  Failed! (0x14)
Probing for `SMSC 47S45x Super IO Fan Sensors'
  Failed! (0x14)
Probing for `SMSC 47M172 Super IO'
  Success... (no hardware monitoring capabilities)
Probing for `SMSC LPC47B397-NC Super IO'
  Failed! (0x14)
Probing for `VT1211 Super IO Sensors'
  Failed! (skipping family)
Probing for `Winbond W83627EHF/EHG Super IO Sensors'
  Failed! (skipping family)

Do you want to scan for secondary Super I/O sensors? (YES/no): y
Probing for `ITE 8702F Super IO Sensors'
  Failed! (skipping family)
Probing for `Nat. Semi. PC87351 Super IO Fan Sensors'
  Failed! (skipping family)
Probing for `SMSC 47B27x Super IO Fan Sensors'
  Failed! (skipping family)
Probing for `VT1211 Super IO Sensors'
  Failed! (skipping family)
Probing for `Winbond W83627EHF/EHG Super IO Sensors'
  Failed! (skipping family)

 Now follows a summary of the probes I have just done.
 Just press ENTER to continue:

Driver `eeprom' (should be inserted):
  Detects correctly:
  * Bus `I810/I815 DDC Adapter'
    Busdriver `i2c-i810', I2C address 0x50 (and 0x51 0x52 0x53 0x54 0x55 0x56 0x 57)
    Chip `DDC monitor' (confidence: 8)


 I will now generate the commands needed to load the I2C modules.
 Sometimes, a chip is available both through the ISA bus and an I2C bus.
 ISA bus access is faster, but you need to load an additional driver module
 for it. If you have the choice, do you want to use the ISA bus or the
 I2C/SMBus (ISA/smbus)? smbus

To make the sensors modules behave correctly, add these lines to
/etc/modules:

#----cut here----
# I2C adapter drivers
i2c-i810
# I2C chip drivers
eeprom
#----cut here----

Do you want to add these lines to /etc/modules automatically? (yes/NO)y
rivo@Xcc:~/Desktop$ sudo /etc/init.d/module-init-tools
 * Loading manual drivers...                                             [ ok ]
rivo@Xcc:~/Desktop$ sudo modprobe i2c-i810
rivo@Xcc:~/Desktop$ sudo modprobe eeprom
rivo@Xcc:~/Desktop$ sudo modprobe i2c-i810 eeprom
rivo@Xcc:~/Desktop$ sensors
No sensors found!
rivo@Xcc:~/Desktop$ sudo depmod -a i2c-i810 eeprom
rivo@Xcc:~/Desktop$ sudo update-modules






I even tried reversing the order in which sensors-detect adds the modules but to no avail.
My /etc/modules

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse




# Generated by sensors-detect on Fri Aug 25 13:20:58 2006
# I2C chip drivers
eeprom
# I2C adapter drivers
i2c-i810



Can anyone help plz! :confused:

---

### Post by Sfac on 2006-09-03
Installed lmsensors..all fine. but i cant see my cpu temp or fan speed. These are the sensors found:

# I2C adapter drivers
i2c-viapro
i2c-isa
# I2C chip drivers
eeprom
w83627hf

and this is the sensors list:

w83627hf-isa-0290
Adapter: ISA adapter
VCore 1:   +4.08 V  (min =  +4.08 V, max =  +4.08 V)       ALARM  (beep)
VCore 2:   +4.08 V  (min =  +4.08 V, max =  +4.08 V)       ALARM  (beep)
+3.3V:     +4.08 V  (min =  +4.08 V, max =  +4.08 V)       ALARM  (beep)
+5V:       +6.85 V  (min =  +6.85 V, max =  +6.85 V)       ALARM  (beep)
+12V:     +15.50 V  (min = +15.50 V, max = +15.50 V)       ALARM  (beep)
-12V:      +6.06 V  (min =  +6.06 V, max =  +6.06 V)       ALARM  (beep)
-5V:       +5.10 V  (min =  +5.10 V, max =  +5.10 V)       ALARM  (beep)
V5SB:      +6.85 V  (min =  +6.85 V, max =  +6.85 V)       ALARM  (beep)
VBat:      +4.08 V  (min =  +4.08 V, max =  +4.08 V)       ALARM  (beep)
fan1:        0 RPM  (min =    0 RPM, div = 128)              ALARM  (beep)
fan2:        0 RPM  (min =    0 RPM, div = 128)              ALARM  (beep)
fan3:        0 RPM  (min =    0 RPM, div = 128)              ALARM  (beep)
temp1:        -1°C  (high =    -1°C, hyst =    -1°C)   sensor = diode   ALARM (beep)
temp2:      +0.0°C  (high =    +0°C, hyst =    +0°C)   sensor = diode   ALARM (beep)
temp3:      +0.0°C  (high =    +0°C, hyst =    +0°C)   sensor = diode   ALARM (beep)
vid:      +0.000 V  (VRM Version 2.4)
alarms:   Chassis intrusion detection                      ALARM
beep_enable:
          Sound alarm enabled

How can i turn on the temp sensors?

---

### Post by Sfac on 2006-09-03
Forgot to say..mobo is a ABIT KV8-MAX3 VIA K8T800.
Thanks

---

### Post by detectiveinspekta on 2006-09-07
I have a nforce2 motherboard with a amd 2500+

```

jonathan@booya:~/Documents$ sensors
w83627hf-isa-0290
Adapter: ISA adapter
VCore 1:   +1.63 V  (min =  +1.44 V, max =  +1.86 V)
VCore 2:   +4.08 V  (min =  +1.44 V, max =  +1.86 V)       ALARM
+3.3V:     +3.23 V  (min =  +2.82 V, max =  +3.79 V)
+5V:       +4.87 V  (min =  +3.71 V, max =  +0.13 V)       ALARM
+12V:     +11.86 V  (min =  +1.40 V, max =  +0.97 V)       ALARM
-12V:     -11.95 V  (min = -13.59 V, max =  -4.22 V)
-5V:       +3.49 V  (min =  +3.34 V, max =  -7.56 V)       ALARM
V5SB:      +5.46 V  (min =  +0.27 V, max =  +0.97 V)       ALARM
VBat:      +1.47 V  (min =  +0.05 V, max =  +0.77 V)       ALARM
fan1:        0 RPM  (min =  803 RPM, div = 8)              ALARM
fan2:        0 RPM  (min = 2109 RPM, div = 8)              ALARM
fan3:        0 RPM  (min =  897 RPM, div = 8)              ALARM
temp1:       +26°C  (high =    +2°C, hyst =    +0°C)   sensor = thermistor   ALARM 
temp2:     +28.5°C  (high =  +100°C, hyst =   +95°C)   sensor = thermistor 
temp3:     +22.0°C  (high =  +100°C, hyst =   +95°C)   sensor = thermistor 
vid:      +1.650 V  (VRM Version 9.0)
alarms:   Chassis intrusion detection                      ALARM
beep_enable:
          Sound alarm enabled

lm90-i2c-0-4c
Adapter: SMBus nForce2 adapter at 5000
M/B Temp:    +28°C  (low  =    +0°C, high =   +70°C)
CPU Temp:  +29.0°C  (low  =  +0.0°C, high = +70.0°C)
M/B Crit:    +85°C  (hyst =   +75°C)
CPU Crit:    +75°C  (hyst =   +65°C)

```
which is the acual temperature measurment on the CPU? I am water cooled but according to bios the CPU temp core is ~45 deg

---

### Post by maddbaron on 2006-09-19
I tried get this error after following the instructions on this page:
[http://www.debian-administration.org/articles/327](http://www.debian-administration.org/articles/327)


>  sensors-detect
# sensors-detect revision 1.393 (2005/08/30 18:51:18)

This program will help you determine which I2C/SMBus modules you need to
load to use lm_sensors most effectively. You need to have i2c and
lm_sensors installed before running this program.
Also, you need to be `root', or at least have access to the /dev/i2c-*
files, for most things.
If you have patched your kernel and have some drivers built in, you can
safely answer NO if asked to load some modules. In this case, things may
seem a bit confusing, but they will still work.

It is generally safe and recommended to accept the default answers to all
questions, unless you know what you're doing.

 We can start with probing for (PCI) I2C or SMBus adapters.
 You do not need any special privileges for this.
 Do you want to probe now? (YES/no): Yes
Probing for PCI bus adapters...
Use driver `i2c-sis96x' for device 00:02.1: Silicon Integrated Systems SMBus Controller
Probe succesfully concluded.

As you are not root, we can't load adapter modules. We will only scan
already loaded adapters.
If you have undetectable or unsupported adapters, you can have them
scanned by manually loading the modules before running this script.

 To continue, we need module `i2c-dev' to be loaded.
 If it is built-in into your kernel, you can safely skip this.
i2c-dev is already loaded.

 We are now going to do the adapter probings. Some adapters may hang halfway
 through; we can't really help that. Also, some chips will be double detected;
 we choose the one with the highest confidence value in that case.
 If you found that the adapter hung after probing a certain address, you can
 specify that address to remain unprobed. That often
 includes address 0x69 (clock chip).

Next adapter: SiS96x SMBus adapter at 0x8100
Do you want to scan it? (YES/no/selectively): YES
Can't open /dev/i2c-0

Some chips are also accessible through the ISA bus. ISA probes are
typically a bit more dangerous, as we have to write to I/O ports to do
this. This is usually safe though.

As you are not root, we shall skip this step.

Some Super I/O chips may also contain sensors. Super I/O probes are
typically a bit more dangerous, as we have to write to I/O ports to do
this. This is usually safe though.

As you are not root, we shall skip this step.

 Sorry, no chips were detected.
 Either your sensors are not supported, or they are
 connected to an I2C bus adapter that we do not support.
 See doc/FAQ, doc/lm_sensors-FAQ.html, or
 [http://www2.lm-sensors.nu/~lm78/cvs/lm_sensors2/doc/lm_sensors-FAQ.html](http://www2.lm-sensors.nu/~lm78/cvs/lm_sensors2/doc/lm_sensors-FAQ.html)
 (FAQ #4.24.3) for further information.
 If you find out what chips are on your board, see
 [http://secure.netroedge.com/~lm78/newdrivers.html](http://secure.netroedge.com/~lm78/newdrivers.html) for driver status.


What do I do? Help Please.

---

### Post by ac4000 on 2006-10-01
emperor:  *Amazing* how-to; thanks!

maddbaron:  You should probably run:```
sudo sensors-detect
```

---

### Post by ant1060 on 2006-10-09
Hi!
Thanks for this HOWTO.... but I am struggling with one of the last steps. Everything goes fine until I try and modprobe the i2c sensor when I receive this message
FATAL : Module i2c_sensor not found.
Two things are strange : one is that I enter it as i2c-sensor (but it replies as i2c_sensor with an underscore).... and the second is that earlier on in the process I received confirmation that the i2c sensor was installed correctly : 

To continue, we need module 'i2c-dev' to eb loaded. If it is built-in into your kernel, you can safely skip this. i2c-dev is not loaded. Do you want to load it now? (YES/NO) : YES Module loaded succesfully.

What am I doing wrong?
Thanks for

---

### Post by asmweb on 2006-10-18
I have the same problem it seems not to find the i2c-sensor, how come?

---

### Post by JayTee on 2006-10-19
Thanks for an excellent how-to. I've got this running although I'm not sure about two things. The two things I'm not sure about are 1.) the Vcore settings and why it's in alarm and 2.) my cpu temp reports 35 celsius but when I do a quick restart and check the hw monitor in BIOS it reports between 45 and 47 celsius while the motherboard temp and remote temp are within 1 degree celsius or match the temp reported by sensors.

 Here's the output when I run the sensors command.

> lm85-i2c-0-2e
Adapter: SMBus I801 adapter at 2000
V1.5:       +1.55 V  (min =  +1.42 V, max =  +1.58 V)   
VCore:      +1.20 V  (min =  +1.76 V, max =  +1.95 V)   ALARM
V3.3:       +3.33 V  (min =  +3.13 V, max =  +3.47 V)   
V5:        +5.16 V  (min =  +4.74 V, max =  +5.26 V)   
V12:      +12.19 V  (min = +11.38 V, max = +12.62 V)   
CPU_Fan:   3827 RPM  (min = 1400 RPM)                     
fan2:         0 RPM  (min =    0 RPM)                     
fan3:         0 RPM  (min =    0 RPM)                     
fan4:      2282 RPM  (min =    0 RPM)                     
CPU:         +35°C  (low  =   +10°C, high =   +50°C)       
Board:       +28°C  (low  =   +10°C, high =   +35°C)      
Remote:      +30°C  (low  =   +10°C, high =   +35°C)       
CPU_PWM:   255
Fan2_PWM:   76
Fan3_PWM:   76
vid:      +1.850 V  (VRM Version 9.1)


Here is the section of /etc/sensors.conf that pertains to my motherboard.


> # Sample configuration for the Intel S845WD1-E
# courtesy of Marcus Schopen
#
chip "lm85c-*" "adm1027-*" "adt7463-*" "lm85-*" "lm85b-*"

   set temp1_max 55

# Voltage inputs
   label in0   "V1.5"      # AGP on Intel S845WD1-E
   label in1   "VCore"
   label in2   "V3.3"
   label in3   "V5"
   label in4   "V12"

# Temperature inputs
   label temp1  "CPU"
   label temp2  "Board"
   label temp3  "Remote"

# Fan inputs
   label fan1   "CPU_Fan"
#   label fan2   "Fan2"
#   label fan3   "Fan3"
#   label fan4   "Fan4"

# PWM Outputs
   label pwm1   "CPU_PWM"
   label pwm2   "Fan2_PWM"
   label pwm3   "Fan3_PWM"

# Voltage scaling is done on-chip.  No 'compute' directive
# should be necessary.  If in0 has external scaling set
# it here.

#   compute in0  @ * 2.5,   @ / 2.5

# Adjust fans speeds for actual pulses per rev
#   compute fan1  @ * 2,  @ / 2    # 1 pulse per rev
#   set fan1_ppr  1                # ADM1027 or ADT7463
#   compute fan2  @ / 2,  @ * 2    # 4 pulse per rev
#   set fan2_ppr  4                # ADM1027 or ADT7463

# Ignore fans you (or your motherboard) don't have
#   ignore fan2
#   ignore fan3
#   ignore fan4

# Set VRM version
   set vrm  9.1   # Pentium 4

# Set voltage limits
   set in0_min  1.5 * 0.95
   set in0_max  1.5 * 1.05
   set in1_min  vid * 0.95
   set in1_max  vid * 1.05
   set in2_min  3.3 * 0.95
   set in2_max  3.3 * 1.05
   set in3_min  5.0 * 0.95
   set in3_max  5.0 * 1.05
   set in4_min   12 * 0.95
   set in4_max   12 * 1.05

# Set Fan limits
   set fan1_min 1400
   set fan4_min 1800
# Set Temp Limits
   set temp1_min 10
   set temp1_max 55
   set temp2_min 10
   set temp2_max 35
   set temp3_min 10
   set temp3_max 35

How can I adjust the temperature monitoring for the CPU to be more accurate and should I bother with adjusting the Vcore limits?
Any advice would be appreciated. I've also attached a full copy of my sensors.conf file to this post.

---

### Post by asmweb on 2006-10-20
Well I've been looking a lot of forums and no one explain what is the i2c-sensor module and moreover where to find it! Any help, would appreciate it!

---

### Post by mmajk on 2006-10-21
Ubuntu dapper has 'old' version of lm-sensors, 2.9.something. The latest release is 2.10.something. You can download it from [http://lm-sensors.org/wiki/Download](http://lm-sensors.org/wiki/Download).

As stated on the lm-sensors.org, you don't need the i2c package, since it's allready in the kernel.

Just download the lm-sensors package, READ THE DOCUMENTATION (there are some issues one needs to understand, it's well explained), run the mkdev.sh (from the prog directory in the lm-sensors package), and go with the sensors-detect. Should work fine now.

---

### Post by Tamale on 2006-10-25
I followed all the instructions, and after answering "y" to all of the questions I got "Sorry, no chips were detected" on my new core 2 duo nc8430 laptop..

any ideas?

---

### Post by Tamale on 2006-10-25
after answering "yes" to all of the questions I too got "Sorry, no chips were found" on my new core 2 duo nc8430 laptop...

any ideas?

---

### Post by raven65az on 2006-10-27
did all steps..and alas "No sensors detected"
I am on a Toshiba Satellite A-65 Notebook.
Giving up on the project, but some other Toshiba users might find the info useful.
Scott

---

### Post by maddbaron on 2006-10-27
Does this work with Edgy? I didn't work for me in Dapper so I am going to retry it in Edgy...will this work maybe?

---

### Post by Peepsalot on 2006-10-31
I have an Asus A7N8X-E motherboard and cannot figure out how to configure lm-sensors.

I tried following the tutorial and ended up putting this in my /etc/modules:
```

sensor modules
i2c-core
i2c-nforce2
asb100
eeprom
ds1621

```
But it won't boot when this is placed in there.  I don't know how to troubleshoot from here.  Any suggestions?

---

### Post by devilbush on 2006-11-10
Excellent HOWTO, thank you!

---

### Post by Peepsalot on 2006-11-10
I actually found the solution to my problems today.  Removed eeprom from the list of modules and it all works.

---

### Post by Jongi on 2006-11-12
What does temp3 measure?

---

### Post by raul_ on 2006-11-20
less than 10 minutes for the whole process. Congratulations :)

---

### Post by Prajna on 2006-11-25
I've just set up Dapper for the first time and have managed to get everything working nicely.  I must say, I'm very impressed with it all.  I have even managed to set up VNC and XDMCP from a windows box without too much bother but I am struggling to get lm_sensors to work.

The problem seems to be that I have a Fintek f71805f chip, which is not supported by the lm_sensors package installed by Synaptic.

I downloaded the latest sensors-detect and ran it, which has identified the problem.  The essential output is:
> #----cut here----
# I2C adapter drivers
modprobe i2c-viapro
modprobe i2c-isa
# Chip drivers
modprobe eeprom
# Warning: the required module f71805f is not currently installed
# on your system. For status of 2.6 kernel ports check
# [http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices). If driver is built
# into the kernel, or unavailable, comment out the following line.
modprobe f71805f
# sleep 2 # optional
/usr/local/bin/sensors -s # recommended
#----cut here----

If someone could help me with finding and installing the f71805f module then I think I could get it working. I am a complete n00b with ubuntu and pretty rusty on unix/linux in general.

Thanks

---

### Post by Prajna on 2006-11-29
I got my sensors working great with the f71805f support in Edgy.  Sadly, during the upgrade I somehow managed to wipe out a very fast and reliable Xvnc setup, meaning I have had to revert to a sluggish Xwindows setup using cygwin (whilst I figure out how to set up FreeNX on Edgy).](*,) 

Oh well, you win some and you lose some.  At least I have got some very pretty temps and fan speeds in my panel!

---

### Post by scotte on 2006-11-30
I finally got my sensors working again in edgy, and hopefully this tip helps others who had sensors working fine in dapper, but are no longer working with edgy. This particular issue is not directly related to anything done in Ubuntu.

For the background, I've got an intel 801 based motherboard on this particular box, and everything was working just fine with my former Gentoo install. Likewise, all was good when I installed Ubuntu dapper. After the upgrade to edgy, sensors stopped working. I tried compiling the latest lm-sensors, but that didn't help either.

A key piece of information is that dapper was on kernel 2.6.15 and edgy uses 2.6.17. With some research and perusal of drivers/pci/quirks.c, there are a number of systems where the SMBus is hidden by default (see asus_hides_smbus in quirks.c).

At any rate, I discovered there was a patch applied to quirks.c in 2.6.16 which effectively disables unhiding the SMBus when ACPI_SLEEP is enabled.

**My solution was to build a custom kernel without ACPI_SLEEP support.** I'm now running 2.6.19, but this should work equally well for 2.6.17 or .18.

Here's the supporting documentation:
[http://bugzilla.kernel.org/show_bug.cgi?id=6449](http://bugzilla.kernel.org/show_bug.cgi?id=6449)
[http://www.kernel.org/git/?p=linux/kernel/git/stable/linux-2.6.16.y.git;a=blobdiff;h=0693c23831bb923c12866737891e40863fab66b5;hp=dda6099903c18adc8636d89683ddc02a9a17b32a;hb=a9cacd682ed7c031fa05b1d1367a3b3221813932;f=drivers/pci/quirks.c](http://www.kernel.org/git/?p=linux/kernel/git/stable/linux-2.6.16.y.git;a=blobdiff;h=0693c23831bb923c12866737891e40863fab66b5;hp=dda6099903c18adc8636d89683ddc02a9a17b32a;hb=a9cacd682ed7c031fa05b1d1367a3b3221813932;f=drivers/pci/quirks.c)
[http://www.kernel.org/git/?p=linux/kernel/git/stable/linux-2.6.16.y.git;a=commit;h=a9cacd682ed7c031fa05b1d1367a3b3221813932](http://www.kernel.org/git/?p=linux/kernel/git/stable/linux-2.6.16.y.git;a=commit;h=a9cacd682ed7c031fa05b1d1367a3b3221813932)

Hope this helps!

---

### Post by Sonic Reducer on 2006-12-02
so i got an interesting error:
```
w83627ehf-isa-0290
Adapter: ISA adapter
Case Fan:    0 RPM  (min = 1318 RPM, div = 128)
CPU Fan:     0 RPM  (min =   76 RPM, div = 128)
fan3:     2393 RPM  (min = 2636 RPM, div = 4)
fan4:        0 RPM  (min = 7670 RPM, div = 8)
Sys Temp:    +27°C  (high =  -111°C, hyst =  -124°C)
CPU Temp:  +27.5°C  (high = +80.0°C, hyst = +75.0°C)
temp3:     +27.5°C  (high = +80.0°C, hyst = +75.0°C)
```

and when i turn down the CPU fanspeed with the Zalman FanMate potentiometer thingy that came with the CNPS7700:

```
w83627ehf-isa-0290
Adapter: ISA adapter
Case Fan:    0 RPM  (min = 1318 RPM, div = 128)
CPU Fan:     0 RPM  (min =   76 RPM, div = 128)
fan3:     1339 RPM  (min = 2636 RPM, div = 4)
fan4:        0 RPM  (min = 7670 RPM, div = 16)
Sys Temp:    +27°C  (high =  -111°C, hyst =  -124°C)
CPU Temp:  +28.0°C  (high = +80.0°C, hyst = +75.0°C)
temp3:     +28.0°C  (high = +80.0°C, hyst = +75.0°C)
```

my CPU fan comes up as "fan3" how can i fix this?

---

### Post by Peepsalot on 2006-12-03
> **Sonic Reducer said:**
> my CPU fan comes up as "fan3" how can i fix this?
Your motherboard probably expects the CPU fan to be plugged into a different spot than the one you are using.  Try another.

---

### Post by froped on 2006-12-03
I'm running edgy and followed the initial setup. I get the following error when I run sensors:

[I]
Can't access procfs/sysfs file
Unable to find i2c bus information;
For 2.6 kernels, make sure you have mounted sysfs and libsensors
was compiled with sysfs support!
For older kernels, make sure you have done 'modprobe i2c-proc'!
[/I]

The sensors where discovered and the modules loaded. *mount* shows that sysfs is mounted and i have libsensors installed. Any ideas?

---

### Post by Corbelius on 2006-12-03
> **froped said:**
> I'm running edgy and followed the initial setup. I get the following error when I run sensors:

[I]
Can't access procfs/sysfs file
Unable to find i2c bus information;
For 2.6 kernels, make sure you have mounted sysfs and libsensors
was compiled with sysfs support!
For older kernels, make sure you have done 'modprobe i2c-proc'!
[/I]

The sensors where discovered and the modules loaded. *mount* shows that sysfs is mounted and i have libsensors installed. Any ideas?

What kernel linux you have?

---

### Post by bluevoodoo1 on 2006-12-03
> **froped said:**
> I'm running edgy and followed the initial setup. I get the following error when I run sensors:

[I]
Can't access procfs/sysfs file
Unable to find i2c bus information;
For 2.6 kernels, make sure you have mounted sysfs and libsensors
was compiled with sysfs support!
For older kernels, make sure you have done 'modprobe i2c-proc'!
[/I]

The sensors where discovered and the modules loaded. *mount* shows that sysfs is mounted and i have libsensors installed. Any ideas?

I have the same problem.

---

### Post by three_sixteen on 2006-12-11
> **Corbelius said:**
> What kernel linux you have?

I'm having the same problem - kernel version 2.6.17-10-386

Trying to run it on a Dell XPS m1210

#----cut here----
# I2C adapter drivers
# modprobe unknown adapter NVIDIA I2C Device
# modprobe unknown adapter NVIDIA I2C Device
# modprobe unknown adapter NVIDIA I2C Device
# I2C chip drivers
eeprom
#----cut here----

---

### Post by maschnitz on 2006-12-16
> [I]Can't access procfs/sysfs file
Unable to find i2c bus information;
For 2.6 kernels, make sure you have mounted sysfs and libsensors was compiled with sysfs support!
For older kernels, make sure you have done 'modprobe i2c-proc'![/I]

I am also receiving this error.  I did a little research.  Here's what I learned.

In my case, this is caused by my current kernel not supporting my I/O chip.  For the record, I am running an Asus M2NPV-VM, which has an NForce 430 chipset (MCP 50).  Apparently the I/O chip in question is the IT8716F.  I'm running under a 2.6.18 kernel I compiled.

[This comprehensive list]("http://www.lm-sensors.org/wiki/Devices") shows what is and isn't supported in lm_sensors.  But it is mapped by specific I/O chip name, not chipset name nor motherboard name.  (In my case, it's the IT8716F). So you'll need to know that, too.   Googling around is your best bet.  It helps to do Google searches for your particular motherboard, or, better, your particular chipset, and "lm_sensors".  Check your motherboard manual or motherboard box for the chipset.  It lead me to [this very relevant kernel developers' discussion]("http://lists.lm-sensors.org/pipermail/lm-sensors/2006-August/017352.html") on my motherboard's chipset.   I imagine it's possible to learn this by reading the labels on the chips on your motherboard.

It's likely you'll have to do a kernel patch or reinstallation.  I haven't done this yet, but I've done one in the past.   [This HOW TO]("http://ubuntuforums.org/showthread.php?t=217657") was very helpful.

And, finally, I learned that sometimes, your chips simply aren't supported yet.  Especially if your chipset is brand new.

---

### Post by satandole666 on 2006-12-16
> **bluevoodoo1 said:**
> I have the same problem.

Add me to the list too.

Just made the cold-turkey switch from Windows to Ubuntu.  Wiped my entire HD clean and installed last night.

Being an avid overclocker I'd kill for monitoring software right now.

Hardware is:

Opty165
DFI Lanparty nForce4 UT 

After about 45 minutes of googling, reading guides, and tr ying solutions nothing has worked.  

I did, however, discover that if I did modprobe on the other detected sensors I got these results:

> To make the sensors modules behave correctly, add these lines to
/etc/modules:

#----cut here----
# I2C adapter drivers
i2c-nforce2
i2c-isa
# I2C chip drivers
eeprom
it87
#----cut here----

Do you want to add these lines to /etc/modules automatically? (yes/NO)y

sudo modprobe i2c-sensor
FATAL: Module i2c_sensor not found.
 sudo modprobe i2c-nforce2
 sudo modprobe i2c-isa
sudo modprobe eeprom
sudo modprobe it87
sudo depmod -a
sudo update-modules
sensors
it8712-isa-0290
Adapter: ISA adapter
VCore 1:   +1.49 V  (min =  +0.00 V, max =  +4.08 V)   
VCore 2:   +1.47 V  (min =  +1.28 V, max =  +1.68 V)   
+3.3V:     +3.33 V  (min =  +2.78 V, max =  +3.78 V)   
+5V:       +4.97 V  (min =  +4.49 V, max =  +5.48 V)   
+12V:     +11.84 V  (min =  +9.98 V, max = +13.95 V)   
-12V:     -13.62 V  (min = -22.94 V, max = -17.05 V)   ALARM
-5V:       -1.38 V  (min =  -9.14 V, max =  -7.75 V)   ALARM
Stdby:     +5.05 V  (min =  +4.49 V, max =  +5.48 V)   
VBat:      +3.09 V
fan1:        0 RPM  (min =  811 RPM, div = 8)          
fan2:        0 RPM  (min =  811 RPM, div = 8)          
fan3:     6490 RPM  (min =  811 RPM, div = 8)          
M/B Temp:    +20°C  (low  =  +127°C, high =   +63°C)   sensor = diode   
CPU Temp:    +25°C  (low  =  +127°C, high =   +63°C)   sensor = thermistor   
Temp3:       +36°C  (low  =  +127°C, high =   +63°C)   sensor = thermistor   


Seems to be a success.  All I did was ignore the error.  :-k   I'm going to install a gui for this and see how it works.  Anyway, I hope this helps someone.

P.S.  And yes, I'm going to look into my -12V and -5V readings...if that's true it "might" be the reason I am limited to 2700mhz on my Opty165.

---

### Post by SuperMike on 2006-12-16
I had to look up what 'lm-sensors' did. For the uninformed like me, it's to look at fan, temperature, and things like that on your PC or server.

---

### Post by satandole666 on 2006-12-17
Just as a follow up to my above post, GkrellM works perfect.  My advice to anyone who gets that error is to continue modprobing and finish the install per this guide.  Everything works and there are no problems.  I'm still curious but it doesn't bother me that much.

---

### Post by Andyreas on 2006-12-22
Argh. A lot of people get the same problem:  ((Sorry, no chips were detected. )) when u run sensors detect (even with sudo). The fun thing is that i've got an HP NX8220 and in another post in this thread a guy got another answer. Why? Really there must be someone that has an answer to this problem. What i can understand there is alot of people having this problem. Is it just that simple that our laptops isn't supported yet even thou i've had mine for a long time, 8 months...

---

### Post by jczucco on 2007-01-12
> **scotte said:**
> I finally got my sensors working again in edgy, and hopefully this tip helps others who had sensors working fine in dapper, but are no longer working with edgy. This particular issue is not directly related to anything done in Ubuntu.

For the background, I've got an intel 801 based motherboard on this particular box, and everything was working just fine with my former Gentoo install. Likewise, all was good when I installed Ubuntu dapper. After the upgrade to edgy, sensors stopped working. I tried compiling the latest lm-sensors, but that didn't help either.

A key piece of information is that dapper was on kernel 2.6.15 and edgy uses 2.6.17. With some research and perusal of drivers/pci/quirks.c, there are a number of systems where the SMBus is hidden by default (see asus_hides_smbus in quirks.c).

At any rate, I discovered there was a patch applied to quirks.c in 2.6.16 which effectively disables unhiding the SMBus when ACPI_SLEEP is enabled.

**My solution was to build a custom kernel without ACPI_SLEEP support.** I'm now running 2.6.19, but this should work equally well for 2.6.17 or .18.

Here's the supporting documentation:
[http://bugzilla.kernel.org/show_bug.cgi?id=6449](http://bugzilla.kernel.org/show_bug.cgi?id=6449)
[http://www.kernel.org/git/?p=linux/kernel/git/stable/linux-2.6.16.y.git;a=blobdiff;h=0693c23831bb923c12866737891e40863fab66b5;hp=dda6099903c18adc8636d89683ddc02a9a17b32a;hb=a9cacd682ed7c031fa05b1d1367a3b3221813932;f=drivers/pci/quirks.c](http://www.kernel.org/git/?p=linux/kernel/git/stable/linux-2.6.16.y.git;a=blobdiff;h=0693c23831bb923c12866737891e40863fab66b5;hp=dda6099903c18adc8636d89683ddc02a9a17b32a;hb=a9cacd682ed7c031fa05b1d1367a3b3221813932;f=drivers/pci/quirks.c)
[http://www.kernel.org/git/?p=linux/kernel/git/stable/linux-2.6.16.y.git;a=commit;h=a9cacd682ed7c031fa05b1d1367a3b3221813932](http://www.kernel.org/git/?p=linux/kernel/git/stable/linux-2.6.16.y.git;a=commit;h=a9cacd682ed7c031fa05b1d1367a3b3221813932)

Hope this helps!

Thanks for the tip! I will try this. Can you post your kernel .config ?

---

### Post by jczucco on 2007-01-12
.

---

### Post by sputnik2012 on 2007-02-04
I'm using the 2.6.19.2 kernel, which doesn't have i2c-sensors as a module.

loaded  modules are as follows

> # Generated by sensors-detect on Fri Feb  2 22:36:27 2007
it87
# I2C adapter drivers
i2c-nforce2
i2c-isa
# I2C chip drivers
eeprom
# Warning: the required module it87 is not currently installed on your system.
# For status of 2.6 kernel ports see [http://secure.netroedge.com/~lm78/supported](http://secure.netroedge.com/~lm78/supported)
.html
# If driver is built-in to the kernel, or unavailable, comment out the following
 line.


When I run sensors -s I get the following output:
> root@rob-desktop:/home/rob# sensors -s
it8712-isa-0d00: Can't access procfs/sysfs file for writing;
Run as root?


I had a feeling sysfs was deprecated in favour of udev, but my /sys folder is there.  I have built and rub mkdev.sh.

When I  run sensors and I get the following output:
> it8712-isa-0d00
Adapter: ISA adapter
VCore 1:   +1.65 V  (min =  +1.42 V, max =  +1.57 V)   ALARM
VCore 2:   +1.57 V  (min =  +2.40 V, max =  +2.61 V)   ALARM
+3.3V:     +2.58 V  (min =  +3.14 V, max =  +3.47 V)   ALARM
+5V:       +2.47 V  (min =  +4.76 V, max =  +5.24 V)   ALARM
+12V:     +13.12 V  (min = +11.39 V, max = +12.61 V)   ALARM
-12V:      -5.02 V  (min = -12.63 V, max = -11.41 V)   ALARM
-5V:       -1.24 V  (min =  -5.26 V, max =  -4.77 V)   ALARM
Stdby:     +5.05 V  (min =  +4.76 V, max =  +5.24 V)   
VBat:      +4.08 V
fan1:     4299 RPM  (min =    0 RPM, div = 2)          
fan2:     2109 RPM  (min = 2986 RPM, div = 4)          ALARM
ERROR: Can't get FAN3 data!
M/B Temp:    +51°C  (low  =   +15°C, high =   +40°C)   sensor = diode   
CPU Temp:     -1°C  (low  =   +15°C, high =   +45°C)   sensor = disabled   
Temp3:        -1°C  (low  =   +15°C, high =   +45°C)   sensor = disabled   


How do I enable the CPU and Temp3 sensors?

Thanks,
       Rob.

---

### Post by scotte on 2007-02-09
> **jczucco said:**
> Thanks for the tip! I will try this. Can you post your kernel .config ?

All I did was copy /boot/config-2.6.17-10-generic to the new kernel .config, did a "make oldconfig", disabled ACPI_SLEEP, then proceeded normally from there...

---

### Post by SebMKd on 2007-02-21
Great HowTo! =D> 
Even simpler than expected as the Sensor detect install the modules automatically!

---

### Post by morganGDFP on 2007-02-25
i can't quite get it to work..
I followed the howto and running sensors works after I have loaded the modules manually using sudo modprobe..

but I can't get them to load automatically during boot.
I think I need to be root to load some of the modules, and that's why they don't load properly..

these are the modules I need to load in order to get lm-sensors to work.

```
#----cut here----
# I2C adapter drivers
# modprobe unknown adapter NVIDIA i2c adapter 0 at 1:00.0
# modprobe unknown adapter NVIDIA i2c adapter 1 at 1:00.0
# modprobe unknown adapter NVIDIA i2c adapter 2 at 1:00.0
i2c-sis96x
i2c-isa
# I2C chip drivers
eeprom
w83627hf
#----cut here----

```
they are also added to my /etc/modules file.
but after boot up sensors does not work and I get this error message:

```
morgan@morgan-desktop:~$ sensors
Can't access procfs/sysfs file
Unable to find i2c bus information;
For 2.6 kernels, make sure you have mounted sysfs and libsensors
was compiled with sysfs support!
For older kernels, make sure you have done 'modprobe i2c-proc'!

```
if I then run sudo modprobe on all the modules listed above it works..
if I run modprobe without sudo one of them tells me that I am not allowed to do that..(sorry, I don't remember which one it is)

So, my guess is that I need to load those modules during boot but I need to have sudo rights in order to do that..
Is there a way to do that or is there a completely different way to get lm-sensors to work
thank you in advance.

---

### Post by emperor on 2007-02-27
Since Dapper, I have found that sensors-detect can automaticly make all the changes required to your system. For example, on Ubuntu 6.06.1 you can see below where sensors-detect did the following:

#/etc/modules:
# Generated by sensors-detect on Fri Feb  3 11:24:54 2006
# I2C adapter drivers
i2c-i801
i2c-isa
# I2C chip drivers
eeprom
w83627hf

e.p.

---

### Post by morganGDFP on 2007-02-27
yes it does make the changes and adds the modules in /etc/modules but I still have to run them "manually" after each reboot in order for the "sensors" command to work..
Anyone know why this is?

---

### Post by emperor on 2007-02-27
> **morganGDFP said:**
> yes it does make the changes and adds the modules in /etc/modules but I still have to run them "manually" after each reboot in order for the "sensors" command to work..
Anyone know why this is?

Run "dmesg" and see if there are any messages related to the modprobe attempts related to "/etc/modules" during boot.  

dmesg |less

Use page-down to examine the messages.

I would try running the following commands after manually inserting the modules using modprobe:

     sudo depmod -a 
     sudo update-modules

---

### Post by rookieone on 2007-03-01
> **morganGDFP said:**
> i can't quite get it to work..

```
morgan@morgan-desktop:~$ sensors
Can't access procfs/sysfs file
Unable to find i2c bus information;
For 2.6 kernels, make sure you have mounted sysfs and libsensors
was compiled with sysfs support!
For older kernels, make sure you have done 'modprobe i2c-proc'!

```


I have the same problem on Kubuntu 6.10 on an Nvida Nforce 430MCP board (Asus M2NPV-VM with an Athlon 64 X2 3800+).
I installed lm-sensors with apt, ran the .sh, then sensors detect which added the modules to my /etc/modules.
I get the same error when I try to run "sudo sensors -s" or just "sensors"

---

### Post by bravemosquito on 2007-03-01
This is my case:

```

root@xxxx:/xxx/x# modprobe i2c-sensor
FATAL: Module i2c_sensor not found.

```

Did I miss something? My mobo is ASRock NForce4 MCP 410/430 with on-board vcard

Edit: Nevermind, after reboot measuring works now, but not at full - no hdd temp, constant cpu-fan speed (3183rpm)

---

### Post by Icarosaurus on 2007-03-01
I finally made it work with my **ABIT AN7** Motherboard.
Just go to the thread: [http://www.ubuntuforums.org/showthread.php?p=2231651#post2231651]("http://www.ubuntuforums.org/showthread.php?p=2231651#post2231651")

---

### Post by xfile087 on 2007-03-05
Hi guys - I don't know if this has been posted anywhere in this thread but here it anyway. I tried the tutorial many times and it just wouldn't detect sensors for my Asus M2NPV-MX so I downloaded the latest version of lm-sensors and followed the rest of the tutorial and it works perfectly!!

So download and install the latest version:- 

[INDENT]sudo apt-get install flex bison libsysfs-dev

wget [http://dl.lm-sensors.org/lm-sensors/releases/lm_sensors-2.10.2.tar.gz](http://dl.lm-sensors.org/lm-sensors/releases/lm_sensors-2.10.2.tar.gz)

tar -zxf lm_sensors-2.10.2.tar.gz

cd lm_sensors-2.10.2

make user

su

make user_install

[/INDENT]

and then follow the rest of the tutorial and it works perfectly.

---

### Post by captin_moor on 2007-03-06
Hi there guys and girls, first time user long time listener here :). I user Redhat at work and have previously been an avide Xp user. Well I am glad that phase is over. Die MS die. Anyway what I require is someone to hold my hand to get this lm_sensor working. I would really love to get this to work if possible. 

I have followed the HOWTO: pretty much to the letter but I still get:

To make the sensors modules behave correctly, add these lines to
/etc/modules.conf:

#----cut here----
# I2C module options
alias char-major-89 i2c-dev
#----cut here----

To load everything that is needed, add this to some /etc/rc* file:

#----cut here----
# I2C adapter drivers
modprobe i2c-i801
# Chip drivers
modprobe eeprom
# sleep 2 # optional
/usr/local/bin/sensors -s # recommended
#----cut here----

If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones! You really
should try these commands right now to make sure everything is
working properly. Monitoring programs won't work until the needed
modules are loaded.

Do you want to overwrite /etc/sysconfig/lm_sensors? (YES/no):

ubuntu>/home/captin/backup>cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse

# Generated by sensors-detect on Tue Apr  3 13:21:47 2007

# I2C module options
alias char-major-89 i2c-dev

#For lm-sensors, i2c modules
i2c-i801
eeprom
/usr/local/bin/sensors -s

ubuntu>/home/captin/backup>sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
ubuntu>/home/captin/backup>

I have gone through and run the sensor-detect and it has located items, I have placed these in what I believe to be the correct dirs but still get the same message. 

Can you let me know what you need to help me out and i will re post. 

Thanks for all your help guys and if there is anything that you can help with, I will be eternally in your debit.

---

### Post by scotte on 2007-03-06
captin_moor, since it looks like you have an i801 based system, you may be interested in my comments regarding ACPI_SLEEP on one of the previous pages of this thread...

---

### Post by captin_moor on 2007-03-07
Hey Scotte, thank man I appreciate the help. But I think that this is a bit out of my league at this moment in time. I will need to do some serious google research to catch up to this stage my man. I appreciate the lead though. If I have any question I will let you know. Thanks, Tim :)

---

### Post by bravemosquito on 2007-03-09
In my Gnome panel there isn't Hard Drive Temperature. When I want to check it I must type **hddtemp /dev/hda**

How can I put it back? There are only CPU temp, SYS temp and other unknown value: **temp3 28'C**. I haven't another pc component with built in temp sensor. Only CPU, NorthBridge and HDD :confused:

---

### Post by wikki on 2007-03-16
I believe that I've followed the instructions correctly.  Seems pretty simple.  However when I run sensors I get the following message.

Can't access procfs/sysfs file
Unable to find i2c bus information;
For 2.6 kernels, make sure you have mounted sysfs and libsensors
was compiled with sysfs support!
For older kernels, make sure you have done 'modprobe i2c-proc'!

---

### Post by Pugwash on 2007-03-16
I just noticed that I get an error during boot that goes something like this : "setting sensor limits .. failed" . Is it related to this? I'm quite sure I've not seen such an error during boot before.

---

### Post by zipeppe on 2007-03-17
Hi guys,

**lm-sensors** doesn't work for me :( 

My Laptop is the **ASUS A6JA-Q002** equipped with an Analog Device ADT7463 sensor.

Everything works using **SpeedFan** under Windows XP, but it seems there are no way to handle the ADT7463 with Ubuntu (feisty 7.04 herd 5, kernel 2.6.20-11-generic).

With **SpeedFan** I can set FAN#1 to a wanted speed (50-70% because of a new HDD 7200 rpm installed), I can monitor CPU and HDD TEMP, and I got the following informations:

```

14/02/2007 22.26.49 - START OF DMI HEADER
14/02/2007 22.26.49 - Anchor String=_SM_
14/02/2007 22.26.49 - Entry Point Length=31
14/02/2007 22.26.49 - SMBIOS Major Version=2
14/02/2007 22.26.49 - SMBIOS Minor Version=3
14/02/2007 22.26.49 - Maximum Structure Size=182
14/02/2007 22.26.49 - Entry Point Revision=0
14/02/2007 22.26.49 - Intermediate Anchor String=_DMI_
14/02/2007 22.26.49 - Intermediate Checksum=152
14/02/2007 22.26.49 - Structure Table Length=1474
14/02/2007 22.26.49 - Structure Table Address=$000FC4F0
14/02/2007 22.26.49 - Number of SMBIOS Structures=35
14/02/2007 22.26.49 - SMBIOS BCD Revision=$23
14/02/2007 14/02/2007 22.26.49 - DMI tables properly parsed
14/02/2007 22.26.49 -  -> MB Manufacturer <ASUSTeK Computer Inc.>
14/02/2007 22.26.49 -  -> MB Model <A6J>
14/02/2007 22.26.49 -  -> MB Version <1.0>
14/02/2007 22.26.49 -  -> MB Serial <BSN12345678901234567>

14/02/2007 22.26.49 - UGURU found ASUSTeK Computer Inc. A6J
14/02/2007 22.26.49 - End of UGURU detection

14/02/2007 22.26.49 - About to probe ACPI
14/02/2007 22.26.50 - FOUND ACPI at $0000

- About to read first samples from ADT7463@$2E(onSMBusIntel@$400)
14/02/2007 22.26.50 -   ...temperatures
14/02/2007 22.26.50 -   ...fans
14/02/2007 22.26.50 -   ...pwms
14/02/2007 22.26.51 -   ...volts

- About to read first samples from HTE721010G9AT00MPD0Q7Y0H0TW7L
14/02/2007 22.26.51 -   ...temperatures
14/02/2007 22.26.51 -   ...fans
14/02/2007 22.26.51 -   ...pwms
14/02/2007 22.26.51 -   ...volts

- About to read first samples from ACPI
14/02/2007 22.26.51 -   ...temperatures
14/02/2007 22.26.51 -   ...fans
14/02/2007 22.26.51 -   ...pwms
14/02/2007 22.26.51 -   ...volts

xxx version 2.01

xxx Link UniqueID=ISA@$290

Name=ISA

Address=$290

xxx end



xxx Link UniqueID=PCI@$0

Name=PCI

Address=$0

xxx end



xxx Link UniqueID=SMBusIntel@$400

Name=SMBus

Address=$400

xxx end



xxx Link UniqueID=SMART@$0

Name=SMART

Address=$0

xxx end



xxx Sensor UniqueID=ADT7463@$2E(onSMBusIntel@$400)

Name=**ADT7463**

UsedBUS=**Intel SMBus**

Address=$2E

Link=SMBus

StickyProps=1

Property=13 |PWM 1 mode| set to |Manually controlled|

xxx end



xxx Sensor UniqueID=HTE721010G9AT00MPD0Q7Y0H0TW7L

Name=HD0 (100,0GB)

UsedBUS=SMART

Address=$0

Link=SMART

StickyProps=0

xxx end



xxx Sensor UniqueID=ACPI

Name=ACPI

UsedBUS=ISA

Address=$0

Link=ISA

StickyProps=0

xxx end



xxx the end



xxx Pwm 1 from ADT7463@$2E(onSMBusIntel@$400)

name=Speed01

active=true

min=55

max=100

variate=false

xxx end



xxx Pwm 2 from ADT7463@$2E(onSMBusIntel@$400)

name=Speed02

active=true

min=0

max=100

variate=false

xxx end



xxx Pwm 3 from ADT7463@$2E(onSMBusIntel@$400)

name=Speed03

active=true

min=0

max=100

variate=false

xxx end



xxx Temp 1 from ADT7463@$2E(onSMBusIntel@$400)

name=CPU

active=true

wanted=40

warning=50

offset=0

intray=true

UsedPwms=3

pwm=1 from ADT7463@$2E(onSMBusIntel@$400)

pwm=2 from ADT7463@$2E(onSMBusIntel@$400)

pwm=3 from ADT7463@$2E(onSMBusIntel@$400)

logged=false

xxx end



xxx Temp 2 from ADT7463@$2E(onSMBusIntel@$400)

name=Local

active=true

wanted=40

warning=50

offset=0

intray=false

UsedPwms=3

pwm=1 from ADT7463@$2E(onSMBusIntel@$400)

pwm=2 from ADT7463@$2E(onSMBusIntel@$400)

pwm=3 from ADT7463@$2E(onSMBusIntel@$400)

logged=false

xxx end



xxx Temp 3 from ADT7463@$2E(onSMBusIntel@$400)

name=Remote 2

active=true

wanted=40

warning=50

offset=0

intray=false

UsedPwms=3

pwm=1 from ADT7463@$2E(onSMBusIntel@$400)

pwm=2 from ADT7463@$2E(onSMBusIntel@$400)

pwm=3 from ADT7463@$2E(onSMBusIntel@$400)

logged=false

xxx end



xxx Temp 1 from HTE721010G9AT00MPD0Q7Y0H0TW7L

name=HD0

active=true

wanted=40

warning=50

offset=0

intray=false

UsedPwms=3

pwm=1 from ADT7463@$2E(onSMBusIntel@$400)

pwm=2 from ADT7463@$2E(onSMBusIntel@$400)

pwm=3 from ADT7463@$2E(onSMBusIntel@$400)

logged=false

xxx end



xxx Temp 1 from ACPI

name=Temp1

active=true

wanted=40

warning=50

offset=0

intray=false

UsedPwms=3

pwm=1 from ADT7463@$2E(onSMBusIntel@$400)

pwm=2 from ADT7463@$2E(onSMBusIntel@$400)

pwm=3 from ADT7463@$2E(onSMBusIntel@$400)

logged=false

xxx end



xxx Fan 1 from ADT7463@$2E(onSMBusIntel@$400)

name=Fan1

active=true

logged=false

xxx end



xxx Fan 2 from ADT7463@$2E(onSMBusIntel@$400)

name=Fan2

active=true

logged=false

xxx end



xxx Fan 3 from ADT7463@$2E(onSMBusIntel@$400)

name=Fan3

active=true

logged=false

xxx end



xxx Fan 4 from ADT7463@$2E(onSMBusIntel@$400)

name=Fan4

active=true

logged=false

xxx end



xxx Volt 1 from ADT7463@$2E(onSMBusIntel@$400)

name=+2.5V

active=true

logged=false

xxx end



xxx Volt 2 from ADT7463@$2E(onSMBusIntel@$400)

name=Vcore

active=true

logged=false

xxx end



xxx Volt 3 from ADT7463@$2E(onSMBusIntel@$400)

name=+3.3V

active=true

logged=false

xxx end



xxx Volt 4 from ADT7463@$2E(onSMBusIntel@$400)

name=+5V

active=true

logged=false

xxx end



xxx Volt 5 from ADT7463@$2E(onSMBusIntel@$400)

name=+12V

active=true

logged=false

xxx end

```

The problem is the sensor **NOT DETECTED** by **sensors-detect** command:
> sudo sensors-detect

```

# sensors-detect revision 4171 (2006-09-24 03:37:01 -0700)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): Yes
Probing for PCI bus adapters...
Sorry, no known PCI bus adapters found.

We will now try to load each adapter module in turn.
If you have undetectable or unsupported adapters, you can have them
scanned by manually loading the modules before running this script.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!
Do you want to scan the ISA I/O ports? (YES/no): Yes
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM78-J' at 0x290...     No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No
Probing for `Winbond W83627HF' at 0x290...                  No
Probing for `Silicon Integrated Systems SIS5595'...         No
Probing for `VIA VT82C686 Integrated Sensors'...            No
Probing for `VIA VT8231 Integrated Sensors'...              No
Probing for `AMD K8 thermal sensors'...                     No
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some Super I/O chips may also contain sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): Yes
Probing for Super-I/O at 0x2e/0x2f
Trying family `ITE'...                                      No
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Probing for Super-I/O at 0x4e/0x4f
Trying family `ITE'...                                      No
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No

Sorry, no sensors were detected.
Either your sensors are not supported, or they are connected town an
I2C or SMBus adapter that is not supported. See doc/FAQ,
doc/lm_sensors-FAQ.html or http://www.lm-sensors.org/wiki/FAQ
(FAQ #4.24.3) for further information.
If you find out what chips are on your board, check
http://www.lm-sensors.org/wiki/Devices for driver status.


```

Another thing make me puzzled: **i2c_dev , i2c_ec** and **i2c_core** modules are correctly loaded; nevertheless there are no i2c bus populated as shown:

> ls /proc/bus
**input  pccard  pci  usb**

:confused: :confused: 

Could anyone help me on this? The temp is going hot and I cannot use the laptop under Linux for more than one hour...

Cheers,
ZpP

---

### Post by emperor on 2007-03-17
The sensor chip, ADT7463, has been supported a long time by the lm85 driver. However the bus chipset should be checked.
[http://lm-sensors.org/wiki/Devices](http://lm-sensors.org/wiki/Devices)

---

### Post by bazar on 2007-03-21
> **wikki said:**
> I believe that I've followed the instructions correctly.  Seems pretty simple.  However when I run sensors I get the following message.

Can't access procfs/sysfs file
Unable to find i2c bus information;
For 2.6 kernels, make sure you have mounted sysfs and libsensors
was compiled with sysfs support!
For older kernels, make sure you have done 'modprobe i2c-proc'!


I have the exact same error message happen to me.
Does anyone have a solution for this?

---

### Post by t341 on 2007-03-21
I also came up with the   "Can't access procfs/sysfs file Unable to 
find i2c bus information; For 2.6 kernels, make sure you have mounted 
sysfs and libsensors was compiled with sysfs support!"   error after using 
the instructions in this thread and the ones at ubuntuguide.org.

Would it be at all possible to revise the instructions to include such
steps?

---

### Post by greenfrog on 2007-03-29
I have a laptop with the NVIDIA chipset for my AMD64 CPU.
Anyone had a luck getting the sensors  working.
I can only get the CPU temp working.

Thanks :confused:

---

### Post by DerArzt on 2007-03-31
I realize that i need to tweak some stuff in the conf file, but I don't know what are reasonable values. I get all sorts of alarms . 
[HTML]
it8712-isa-0290
Adapter: ISA adapter
VCore 1:   +1.41 V  (min =  +1.42 V, max =  +1.57 V)   ALARM
VCore 2:   +2.58 V  (min =  +2.40 V, max =  +2.61 V)   
+3.3V:     +3.25 V  (min =  +3.14 V, max =  +3.47 V)   
+5V:       +4.19 V  (min =  +4.76 V, max =  +5.24 V)   ALARM
+12V:     +12.10 V  (min = +11.39 V, max = +12.61 V)   
-12V:     -16.07 V  (min = -12.63 V, max = -11.41 V)   ALARM
-5V:       -8.10 V  (min =  -5.26 V, max =  -4.77 V)   ALARM
Stdby:     +3.09 V  (min =  +4.76 V, max =  +5.24 V)   ALARM
VBat:      +4.08 V
fan1:     2636 RPM  (min =    0 RPM, div = 8)          
fan2:        0 RPM  (min = 3013 RPM, div = 8)          ALARM
fan3:     2556 RPM  (min = 3013 RPM, div = 8)          ALARM
M/B Temp:    +25°C  (low  =   +15°C, high =   +40°C)   sensor = thermistor   
CPU Temp:    +25°C  (low  =   +15°C, high =   +45°C)   sensor = thermistor   
Temp3:       +35°C  (low  =   +15°C, high =   +45°C)   sensor = diode   

[/HTML]

Any help will be greatly appreciated

---

### Post by counterpoint on 2007-04-03
> **maschnitz said:**
> In my case, this is caused by my current kernel not supporting my I/O chip.  For the record, I am running an Asus M2NPV-VM, which has an NForce 430 chipset (MCP 50).  Apparently the I/O chip in question is the IT8716F.  I'm running under a 2.6.18 kernel I compiled.

My new Linux PC is also built on the Asus M2NPV-VM, Mostly seems to be going well so far. But as a Linux beginner, I'd be delighted if someone could post step by step instructions for getting CPU temperature monitoring going,

---

### Post by zipeppe on 2007-04-15
> **emperor said:**
> The sensor chip, ADT7463, has been supported a long time by the lm85 driver. However the bus chipset should be checked.
[http://lm-sensors.org/wiki/Devices](http://lm-sensors.org/wiki/Devices)

What do you mean, please?

Could you give to me some more information? I don't know how to do  it..

Tnx

---

### Post by Tanker Bob on 2007-04-16
Does anyone have a DEB of version 2.10.3 or know where I can get it?  The repository version doesn't work with my MB (MSI P6N SLI Platinum) and the tar file won't compile for me.  Thanks!

---

### Post by PhotoJoe on 2007-04-18
Excellent tutorial! XSensor did not work at all for me using the Add/Remove programs GUI route.  I got an icon in System Tools that did *nothing*! Now it works great!

Here's the question I still have - lmsensors was installed (verified by Synaptic) and the program appeared as 'sleeping' in System Monitor before I even attempted this....so what was missing?  This utility always worked (and still does) in the BIOS.

My guess is the 2 drivers I needed were not in the GUI package(s).....

---

### Post by saltydog on 2007-04-18
This is my output to the sensors command:

```

w83627ehf-isa-0290
Adapter: ISA adapter
Case Fan:    0 RPM  (min = 1240 RPM, div = 64)
CPU Fan:  1896 RPM  (min = 1704 RPM, div = 8)
fan3:        0 RPM  (min = 10546 RPM, div = 64)
fan4:        0 RPM  (min = 1171 RPM, div = 128)
Sys Temp:    +33°C  (high =   +45°C, hyst =   +40°C)  
CPU Temp:  +28.5°C  (high = +45.0°C, hyst = +40.0°C)  
temp3:     +33.0°C  (high = +80.0°C, hyst = +75.0°C) 

```


What is temp3??

---

### Post by bravemosquito on 2007-04-18
> **saltydog said:**
> What is temp3??

Yeah, I'm asking the same question :-k

---

### Post by saltydog on 2007-04-18
Running pwmconfig I got this message:

/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed

I have Dapper, so the patch on pwmconfig is applied. What should I do to have fan control? The fan is  a 3-wire model.

---

### Post by Pkirkham on 2007-04-20
Although the rest of this topic is quite antique it seems the most appropriate place to put this question.

I'm trying to use cacti to monitor sensors. I have installed net-snmp, lm-sensors etc.

If I type sensors at the CLI I get the correct sensor info back but using snmpwalk etc there are no sensor MIBs.

It would appear that I need to recompile net-snmp to include the MIBs but when I use the ./configure in the net-snmp install I get
[B]configure: error: asked to use lm_sensors but I couldn't find sensors/sensors.h
[/B]
I've looked in the Ubuntu Dapper headers but sensors.h isn't there.

**Where is sensors.h? **

I do hate having to recompile stuff to get it to work which for me is a bane of Linux but that's the way it is I suppose, like it or lump it!

Any advice would be appreciated, including a better plcae to post this.
Thanks,
Pete

---

### Post by nss0000 on 2007-04-25
CPT:

I'm running DAPPERx64 on an ASUS-M2N/AMD5400+ ... LM-Sensors has NEVER worked for me. Ultimately all I get is the error "no sensors found". Must be the NV430 chipset is still unsupported.

nss
*******

---

### Post by Chupa on 2007-05-02
Sensors don't work for me :( Don't know what the matter is. There is all I do:

> root@chupa-desktop:/home/chupa# apt-get install lm-sensors
lm-sensors is already the newest version.

root@chupa-desktop:/home/chupa# ./mkdev.sh
/dev/i2c-0
mknod: `/dev/i2c-0': File exists

root@chupa-desktop:/home/chupa# sensors-detect
# sensors-detect revision 4171 (2006-09-24 03:37:01 -0700)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): y
Probing for PCI bus adapters...
Use driver `i2c-i801' for device 0000:00:1f.3: Intel ICH8

We will now try to load each adapter module in turn.
Module `i2c-i801' already loaded.
If you have undetectable or unsupported adapters, you can have them
scanned by manually loading the modules before running this script.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Next adapter: SMBus I801 adapter at 0400
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x08
Client found at address 0x30
Client found at address 0x50
Handled by driver `eeprom' (already loaded), chip type `eeprom'
Client found at address 0x69

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!
Do you want to scan the ISA I/O ports? (YES/no): y
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM78-J' at 0x290...     No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No
Probing for `Winbond W83627HF' at 0x290...                  No
Probing for `Silicon Integrated Systems SIS5595'...         No
Probing for `VIA VT82C686 Integrated Sensors'...            No
Probing for `VIA VT8231 Integrated Sensors'...              No
Probing for `AMD K8 thermal sensors'...                     No
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some Super I/O chips may also contain sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): y
Probing for Super-I/O at 0x2e/0x2f
Trying family `ITE'...                                      Yes
Found unknown chip with ID 0xa023
    (logical device B has address 0x290, could be sensors)
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       Yes
Found `Winbond W83627DHG Super IO Sensors'                  Success!
    (address 0x290, driver `w83627ehf')
Probing for Super-I/O at 0x4e/0x4f
Trying family `ITE'...                                      No
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No

Now follows a summary of the probes I have just done.
Just press ENTER to continue:

Driver `eeprom' (should be inserted):
  Detects correctly:
  * Bus `SMBus I801 adapter at 0400'
    Busdriver `i2c-i801', I2C address 0x50
    Chip `eeprom' (confidence: 6)

  EEPROMs are *NOT* sensors! They are data storage chips commonly
  found on memory modules (SPD), in monitors (EDID), or in some
  laptops, for example.

Driver `w83627ehf' (should be inserted):
  Detects correctly:
  * ISA bus address 0x0290 (Busdriver `i2c-isa')
    Chip `Winbond W83627DHG Super IO Sensors' (confidence: 9)

I will now generate the commands needed to load the required modules.
Just press ENTER to continue:

To make the sensors modules behave correctly, add these lines to
/etc/modules:

#----cut here----
# I2C adapter drivers
i2c-i801
# Chip drivers
eeprom
w83627ehf
#----cut here----

Do you want to add these lines to /etc/modules automatically? (yes/NO)y

root@chupa-desktop:/home/chupa# /etc/init.d/module-init-tools
 * Loading kernel modules...                                                                                                                                                        * Loading manual drivers...                                             [ OK ]

root@chupa-desktop:/home/chupa# nano /etc/modprobe.d/local
root@chupa-desktop:/home/chupa# update-modules

root@chupa-desktop:/home/chupa# modprobe i2c-sensor
FATAL: Module i2c_sensor not found.

root@chupa-desktop:/home/chupa# modprobe i2c-viapro
FATAL: Module i2c_viapro not found.

root@chupa-desktop:/home/chupa# modprobe i2c-isa

root@chupa-desktop:/home/chupa# modprobe it87
FATAL: Error inserting it87 (/lib/modules/2.6.21-custom/kernel/drivers/hwmon/it8                                                                                                   7.ko): No such device

root@chupa-desktop:/home/chupa# depmod -a
root@chupa-desktop:/home/chupa# update-modules

root@chupa-desktop:/home/chupa# sensors
w83627dhg-isa-0290
Adapter: ISA adapter

ASUS P5B-E motherboard, Core 2 Duo E6300, ASUS Radeon X1650XT.

---

### Post by Tanker Bob on 2007-05-02
They don't work on my MSI P6N SLI Platinum motherboard with the NVIDIA nForce 850i chipset either.

---

### Post by Chupa on 2007-05-03
Hmm, GKrellm shows all the sensors correctly but sensons command gives only:
root@chupa-desktop:/home/chupa# sensors
w83627dhg-isa-0290
Adapter: ISA adapter
Why?

---

### Post by Reinhardt on 2007-05-03
> **Chupa said:**
> Sensors don't work for me :( Don't know what the matter is. There is all I do:



ASUS P5B-E motherboard, Core 2 Duo E6300, ASUS Radeon X1650XT.

The reason is that the Asus P5B line uses the `Winbond W83627DHG Super IO' chip.   The w83627EHG driver included with Feisty's 2.6.20-15 kernel is an  older version of the driver which lacks DHG support.  The new 2.6.21 kernel includes proper support - the updated driver wasn't complete until mid February, which was too late to be included in Feisty.   I am not going to risk all the incompatibilities/breaking things by installing the .21 kernel, maybe we will get lucky and someone will release a patch to make the new driver work with the older kernel?

---

### Post by Chupa on 2007-05-04
> **Reinhardt said:**
> The reason is that the Asus P5B line uses the `Winbond W83627DHG Super IO' chip.   The w83627EHG driver included with Feisty's 2.6.20-15 kernel is an  older version of the driver which lacks DHG support.  The new 2.6.21 kernel includes proper support - the updated driver wasn't complete until mid February, which was too late to be included in Feisty.   I am not going to risk all the incompatibilities/breaking things by installing the .21 kernel, maybe we will get lucky and someone will release a patch to make the new driver work with the older kernel?

I have 2.6.21 kernel installed. The quest is why sensors are shown in gkrellm and not shown in sensors?

---

### Post by gosh3t0 on 2007-05-05
Im.. newbie. I have ubuntu edgy for a week. I tried this howto... but... something isn't right . Look what i've done ,and help me if you can. I've installed lm-sensor ... make the script executable and typed sensors-detect 
gosh3t0@gosh3t0-desktop:~$ sudo sensors-detect
# sensors-detect revision 4348 (2007-03-18 02:45:21 -0700)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): y
Probing for PCI bus adapters...
Use driver `i2c-nforce2' for device 0000:00:01.1: nVidia Corporation nForce4 SMBus (MCP)

We will now try to load each adapter module in turn.
Module `i2c-nforce2' already loaded.
If you have undetectable or unsupported adapters, you can have them
scanned by manually loading the modules before running this script.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Next adapter: NVIDIA i2c adapter 2 at 5:00.0 (i2c-4)
Do you want to scan it? (YES/no/selectively): y

Next adapter: NVIDIA i2c adapter 1 at 5:00.0 (i2c-3)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Success!
    (confidence 8, driver `eeprom'), other addresses: 0x51 0x52 0x53 0x54 0x55 0x56 0x57
Probing for `Maxim MAX6900'...                              No

Next adapter: NVIDIA i2c adapter 0 at 5:00.0 (i2c-2)
Do you want to scan it? (YES/no/selectively): y

Next adapter: SMBus nForce2 adapter at f400 (i2c-1)
Do you want to scan it? (YES/no/selectively): y

Next adapter: SMBus nForce2 adapter at f800 (i2c-0)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x50
Handled by driver `eeprom' (already loaded), chip type `eeprom'

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!
Do you want to scan the ISA I/O ports? (YES/no): y
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM78-J' at 0x290...     No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No
Probing for `Silicon Integrated Systems SIS5595'...         No
Probing for `VIA VT82C686 Integrated Sensors'...            No
Probing for `VIA VT8231 Integrated Sensors'...              No
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some Super I/O chips may also contain sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): y
Probing for Super-I/O at 0x2e/0x2f
Trying family `ITE'...                                      No
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Probing for Super-I/O at 0x4e/0x4f
Trying family `ITE'...                                      No
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       Yes
Found `Fintek F71872F/FG Super IO Sensors'                  Success!
    (address 0x295, driver `f71805f')

Some CPUs or memory controllers may also contain embedded sensors.
Do you want to scan for them? (YES/no): y
AMD K8 thermal sensors...                                   Success!
    (driver `k8temp')
Intel Core family thermal sensor...                         No
Intel AMB FB-DIMM thermal sensor...                         No

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `eeprom' (should be inserted):
  Detects correctly:
  * Bus `NVIDIA i2c adapter 1 at 5:00.0'
    Busdriver `UNKNOWN', I2C address 0x50 (and 0x51 0x52 0x53 0x54 0x55 0x56 0x57)
    Chip `EDID EEPROM' (confidence: 8)
  * Bus `SMBus nForce2 adapter at f800'
    Busdriver `i2c-nforce2', I2C address 0x50
    Chip `eeprom' (confidence: 6)

  EEPROMs are *NOT* sensors! They are data storage chips commonly
  found on memory modules (SPD), in monitors (EDID), or in some
  laptops, for example.

Driver `f71805f' (should be inserted):
  Detects correctly:
  * ISA bus, address 0x295 (Busdriver `i2c-isa')
    Chip `Fintek F71872F/FG Super IO Sensors' (confidence: 9)

Driver `k8temp' (should be inserted):
  Detects correctly:
  * Chip `AMD K8 thermal sensors' (confidence: 9)

I will now generate the commands needed to load the required modules.
Just press ENTER to continue: 

To make the sensors modules behave correctly, add these lines to
/etc/modules.conf:

#----cut here----
# I2C module options
alias char-major-89 i2c-dev
#----cut here----

To load everything that is needed, add this to some /etc/rc* file:

#----cut here----
# I2C adapter drivers
# modprobe unknown adapter NVIDIA i2c adapter 0 at 5:00.0
# modprobe unknown adapter NVIDIA i2c adapter 1 at 5:00.0
# modprobe unknown adapter NVIDIA i2c adapter 2 at 5:00.0
modprobe i2c-nforce2
modprobe i2c-isa
# Chip drivers
modprobe eeprom
modprobe f71805f
# Warning: the required module k8temp is not currently installed
# on your system. For status of 2.6 kernel ports check
# [http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices). If driver is built
# into the kernel, or unavailable, comment out the following line.
modprobe k8temp
# sleep 2 # optional
/usr/local/bin/sensors -s # recommended
#----cut here----

If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones! You really
should try these commands right now to make sure everything is
working properly. Monitoring programs won't work until the needed
modules are loaded.

Do you want to overwrite /etc/sysconfig/lm_sensors? (YES/no): y
Copy prog/init/lm_sensors.init to /etc/init.d/lm_sensors
for initialization at boot time.
gosh3t0@gosh3t0-desktop:~$ sudo gedit /etc/modules
gosh3t0@gosh3t0-desktop:~$ /etc/init.d/module-init-tools
open: Permission denied
 * Loading manual drivers...                                                    open: Permission denied
                                                                         [ ok ]
gosh3t0@gosh3t0-desktop:~$ sudo /etc/init.d/module-init-tools
 * Loading manual drivers...                                             [ ok ] 
gosh3t0@gosh3t0-desktop:~$ sudo modprobe i2c-sensor
FATAL: Module i2c_sensor not found.
gosh3t0@gosh3t0-desktop:~$ sudo modprobe i2c-viapro
gosh3t0@gosh3t0-desktop:~$ sudo modprobe i2c-isa
gosh3t0@gosh3t0-desktop:~$ sudo modprobe it87
gosh3t0@gosh3t0-desktop:~$ sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
gosh3t0@gosh3t0-desktop:~$

---

### Post by jegrcek on 2007-05-09
Hi
i was folloving the guide on ubntuguide, but lm-sensors dont detect any sensors. What could be wrong?

```
jegrcek@ubuntu:~$ sudo /etc/init.d/module-init-tools
Password:
 * Loading kernel modules...                                                     * Loading manual drivers...                                             [ OK ] 
jegrcek@ubuntu:~$ sudo sensors -s
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
jegrcek@ubuntu:~$ sudo sensors-detect
# sensors-detect revision 4171 (2006-09-24 03:37:01 -0700)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): y
Probing for PCI bus adapters...
Use driver `i2c-i801' for device 0000:00:1f.3: Intel ICH8

We will now try to load each adapter module in turn.
Module `i2c-i801' already loaded.
If you have undetectable or unsupported adapters, you can have them
scanned by manually loading the modules before running this script.

To continue, we need module `i2c-dev' to be loaded.
Do you want to load `i2c-dev' now? (YES/no): y
Module loaded successfully.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Next adapter: NVIDIA i2c adapter 2 at 1:00.0
Do you want to scan it? (YES/no/selectively): y

Next adapter: NVIDIA i2c adapter 1 at 1:00.0
Do you want to scan it? (YES/no/selectively): y

Next adapter: NVIDIA i2c adapter 0 at 1:00.0
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x37
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Success!
    (confidence 1, driver `eeprom')
Probing for `EDID EEPROM'...                                Success!
    (confidence 8, driver `eeprom'), other addresses: 0x51 0x52 0x53 0x54 0x55 0x56 0x57
Probing for `Maxim MAX6900'...                              No

Next adapter: SMBus I801 adapter at 0400
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x08
Client found at address 0x22
Probing for `National Semiconductor LM78'...                No
Probing for `National Semiconductor LM78-J'...              No
Probing for `National Semiconductor LM79'...                No
Probing for `Winbond W83781D'...                            No
Probing for `Winbond W83782D'...                            No
Probing for `Winbond W83627HF'...                           No
Client found at address 0x30
Client found at address 0x50
Handled by driver `eeprom' (already loaded), chip type `eeprom'
Client found at address 0x69

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!
Do you want to scan the ISA I/O ports? (YES/no): y
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM78-J' at 0x290...     No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No
Probing for `Winbond W83627HF' at 0x290...                  No
Probing for `Silicon Integrated Systems SIS5595'...         No
Probing for `VIA VT82C686 Integrated Sensors'...            No
Probing for `VIA VT8231 Integrated Sensors'...              No
Probing for `AMD K8 thermal sensors'...                     No
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some Super I/O chips may also contain sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): y
Probing for Super-I/O at 0x2e/0x2f
Trying family `ITE'...                                      Yes
Found unknown chip with ID 0xa023
    (logical device B has address 0x290, could be sensors)
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       Yes
Found `Winbond W83627DHG Super IO Sensors'                  Success!
    (address 0x290, driver `w83627ehf')
Probing for Super-I/O at 0x4e/0x4f
Trying family `ITE'...                                      No
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `eeprom' (should be inserted):
  Detects correctly:
  * Bus `NVIDIA i2c adapter 0 at 1:00.0'
    Busdriver `UNKNOWN', I2C address 0x50 (and 0x51 0x52 0x53 0x54 0x55 0x56 0x57)
    Chip `EDID EEPROM' (confidence: 8)
  * Bus `SMBus I801 adapter at 0400'
    Busdriver `i2c-i801', I2C address 0x50
    Chip `eeprom' (confidence: 6)

  EEPROMs are *NOT* sensors! They are data storage chips commonly
  found on memory modules (SPD), in monitors (EDID), or in some
  laptops, for example.

Driver `w83627ehf' (should be inserted):
  Detects correctly:
  * ISA bus address 0x0290 (Busdriver `i2c-isa')
    Chip `Winbond W83627DHG Super IO Sensors' (confidence: 9)

I will now generate the commands needed to load the required modules.
Just press ENTER to continue: 

To make the sensors modules behave correctly, add these lines to
/etc/modules:

#----cut here----
# I2C adapter drivers
# modprobe unknown adapter NVIDIA i2c adapter 0 at 1:00.0
# modprobe unknown adapter NVIDIA i2c adapter 1 at 1:00.0
# modprobe unknown adapter NVIDIA i2c adapter 2 at 1:00.0
i2c-i801
# Chip drivers
eeprom
w83627ehf
#----cut here----


Do you want to add these lines to /etc/modules automatically? (yes/NO)y
jegrcek@ubuntu:~$ sudo /etc/init.d/module-init-tools
 * Loading kernel modules...                                                     * Loading manual drivers...                                             [ OK ] 
jegrcek@ubuntu:~$ sudo sensors -s
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
jegrcek@ubuntu:~$ sudo sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.

```

---

### Post by mrazster on 2007-05-09
Just did this on my *DFI NF4 Ultra-D* ...and it works flawlessly, modules load perfectly everytime on reboot.

Thnx...a bunch.

---

### Post by h0bbe on 2007-05-12
I've followed both the HOW TO above an this one [http://news.softpedia.com/news/How-to-Install-lm-sensors-on-Ubuntu-47205.shtml](http://news.softpedia.com/news/How-to-Install-lm-sensors-on-Ubuntu-47205.shtml). But still don't get it working. My /etc/modules file looks like this:

> # Generated by sensors-detect on Thu May 10 21:27:12 2007
# I2C adapter drivers
i2c-ali1535
# Chip drivers
eeprom

Does this mean anything I don't understand? There is no "2c-isa" as in the both HOW TO:s.

Please help me!

---

### Post by bambit on 2007-05-15
I'm running Feisty on a Toshiba Satellite Pro M10 and this is what I get after sensors-detect:

# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
#----cut here----
# I2C adapter drivers
# modprobe unknown adapter NVIDIA i2c adapter 0 at 1:00.0
# modprobe unknown adapter NVIDIA i2c adapter 1 at 1:00.0
# modprobe unknown adapter NVIDIA i2c adapter 2 at 1:00.0
# Chip drivers
# no driver for Smart Battery Charger yet
# Warning: the required module smartbatt is not currently installed
# on your system. For status of 2.6 kernel ports check
# [http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices). If driver is built
# into the kernel, or unavailable, comment out the following line.
smartbatt
#----cut here----

and then when I run sensors I get:

No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.

I'm stumped and don't know what to do next. Please help.

---

### Post by leona on 2007-05-20
Hi, can someone help me out here.
This used to work for me, I had an Asus A8V VIA board, now I've upgraded to an Asus M2N-E boad NForce, and now non of the sensors are detected.
I reran the scripts, ran Sensor-detect, installed the required Kernal moduals, but alas when I do 'sensors' I get No Sensors Found, 
What can I do to fix this?

---

### Post by Browser_ice on 2007-05-22
When I got to "**3. Now run sensors-detect**", I replied YES to the first 2-3 questions and then the whole graphic screwed up completly and I couldn't do anything else. I had to reboot completly. I'm typing on another PC cause I didn't know if I screwed up my Ubuntu or not.

Prior to this, I had installed xsensors, ksensors and hddtemp.

This is on an PC at the office. ITs an desktop IBM NetVista.



This is following a thread I did about [this PC being extreamly slow after being left ON for a while]("http://ubuntuforums.org/showthread.php?t=447277").

---

### Post by zipeppe on 2007-05-31
No way for me:(:(
lm-sensors doesn't work on my laptop ASUS A6J.
"no sensor detected" as shown:

> 
massimo@A6Ja:~$ sudo sensors-detect
# sensors-detect revision 4171 (2006-09-24 03:37:01 -0700)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): 
Probing for PCI bus adapters...
Sorry, no known PCI bus adapters found.

We will now try to load each adapter module in turn.
If you have undetectable or unsupported adapters, you can have them
scanned by manually loading the modules before running this script.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!
Do you want to scan the ISA I/O ports? (YES/no): 
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM78-J' at 0x290...     No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No
Probing for `Winbond W83627HF' at 0x290...                  No
Probing for `Silicon Integrated Systems SIS5595'...         No
Probing for `VIA VT82C686 Integrated Sensors'...            No
Probing for `VIA VT8231 Integrated Sensors'...              No
Probing for `AMD K8 thermal sensors'...                     No
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some Super I/O chips may also contain sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): 
Probing for Super-I/O at 0x2e/0x2f
Trying family `ITE'...                                      No
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Probing for Super-I/O at 0x4e/0x4f
Trying family `ITE'...                                      No
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No

Sorry, **no sensors were detected**.
Either your sensors are not supported, or they are connected to an
I2C or SMBus adapter that is not supported. See doc/FAQ,
doc/lm_sensors-FAQ.html or [http://www.lm-sensors.org/wiki/FAQ](http://www.lm-sensors.org/wiki/FAQ)
(FAQ #4.24.3) for further information.
If you find out what chips are on your board, check
[http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) for driver status.


Please, could you help me?
Everything works fine with SpeedFan and Windows XP.

I am using ubuntu 7.04 x86
ZPP

---

### Post by kwaanens on 2007-06-01
I have an MSI s262 notebook. I tried running sensors-detect, checking if there was some modules that could be loaded, that isn't already. When rebooting, the computer hangs at the very start. I hold the start/stop button and shut the computer down. Now, when I restart, BIOS doesn't start. The power and wireless lights show up, and stay that way. HDD-light flashes once, then stops.
I did this twice. Both times with the same result. I got a little worried, since I had no idea what to do. So I ended up with the longshot of removing the battery, and putting it back. Then my computer starts.

Does anyone have an idea what to do? (For now, the solution is: never commit changes from sensors-detect...)
If anyone else is using the s262, what BIOS do you use? There's an update that I did not install, and I'm wondering if it's worth the bother (it's an update to get Vista going, and I'm mono-booting Feisty, so does it matter to me?)
Also the CPU temperature seems a bit high (stable at +/- 50 degrees C). Mind you, this is a 12,1 inch, so there's not much room inside, so hw is crowded, I guess that might account for some.

- Ketil

---

### Post by belikralj on 2007-06-06
I have also installed lm-sensors and got the mkdev.sh script as per the howto, but sensors-detect doesn't detect anything. Why? I have Ubuntu Dapper (32bit) installed on my athlon64. I also have both Feisty and Slackware (32bit) on this system and only Feisty (which is 64bit install) detects something and still it doesn't work. I'm guessing by what I see that it has something to do with the kernel (32bit of 64bit), I mean it still doesn't work on my 64bit Feisty but at least it detects something. So can anyone halp me with this? I'll make sure to look at what the problem is in Feisty cause I can't exactly remember of the top of my head what it was.

Thanx

---

### Post by libos on 2007-06-10
> **leona said:**
> Hi, can someone help me out here.
This used to work for me, I had an Asus A8V VIA board, now I've upgraded to an Asus M2N-E boad NForce, and now non of the sensors are detected.
I reran the scripts, ran Sensor-detect, installed the required Kernal moduals, but alas when I do 'sensors' I get No Sensors Found, 
What can I do to fix this?

Not sure what went wrong to yours, but i got mine working :)
[http://bsling.blogspot.com/2007/06/hardware-health-monitoring-on-asus-m2n.html](http://bsling.blogspot.com/2007/06/hardware-health-monitoring-on-asus-m2n.html)

---

### Post by AmericanAqualung on 2007-06-22
Ok, so I got this up and running but have a few questions still.  First, I get three sets of output (shown below) for my AMD opteron board with 4 dual core processors (its part of a linux cluster).  Which do I use?  The top two give reasonable values, but disagree and the third is nonsense (neg. temps).  Also, shouldn't I be able to get either 4 or 8 temps for each cpu/core?  And I understand that temp 1 is m/b,  temp2 is cpu, but what is temp3? case?  Thanks a lot.

```
adm1026-i2c-1-2d
Adapter: SMBus nForce2 adapter at 4c40
in0:       +0.00 V  (min =  +0.00 V, max =  +2.99 V)   ALARM
in1:       +0.00 V  (min =  +2.25 V, max =  +2.75 V)   ALARM
in2:       +0.00 V  (min =  +2.25 V, max =  +2.75 V)   ALARM
in3:       +0.00 V  (min =  +2.25 V, max =  +2.75 V)   ALARM
in4:       +0.00 V  (min =  +0.00 V, max =  +2.99 V)   ALARM
in5:       +0.00 V  (min =  +0.00 V, max =  +2.99 V)   ALARM
in6:       +0.00 V  (min =  +0.00 V, max =  +2.49 V)   ALARM
in7:       +1.36 V  (min =  +1.02 V, max =  +1.68 V)
in8:       +0.00 V  (min =  +0.00 V, max =  +2.49 V)
in9:       +0.35 V  (min =  +0.00 V, max =  +0.76 V)
in10:      +3.08 V  (min =  +2.97 V, max =  +3.64 V)
in11:      +3.42 V  (min =  +0.00 V, max =  +4.42 V)
in12:      +3.38 V  (min =  +2.97 V, max =  +3.64 V)
in13:      +3.36 V  (min =  +4.50 V, max =  +5.49 V)   ALARM
in14:      +1.35 V  (min =  +1.02 V, max =  +1.68 V)
in15:      +0.00 V  (min = +10.81 V, max = +13.19 V)   ALARM
in16:      +0.19 V  (min = -13.18 V, max = -10.80 V)   ALARM
ERROR: Can't get FAN0 data!
fan1:        0 RPM  (min =  712 RPM, div = 8)   ALARM
fan2:        0 RPM  (min =  712 RPM, div = 8)
fan3:     6250 RPM  (min =  712 RPM, div = 8)
fan4:     6250 RPM  (min =  712 RPM, div = 8)   ALARM
fan5:        0 RPM  (min =  712 RPM, div = 8)   ALARM
fan6:        0 RPM  (min =  712 RPM, div = 8)   ALARM
fan7:        0 RPM  (min =  712 RPM, div = 8)   ALARM
temp1:       +51°C  (low  =    +0°C, high =   +80°C)
temp2:       +40°C  (low  =    +0°C, high =   +78°C)
temp3:       +36°C  (low  =    +0°C, high =   +78°C)
vid:      +0.975 V  (VRM Version 2.4)

adm1026-i2c-1-2c
Adapter: SMBus nForce2 adapter at 4c40
in0:       +2.62 V  (min =  +0.00 V, max =  +2.99 V)
in1:       +1.22 V  (min =  +2.25 V, max =  +2.75 V)   ALARM
in2:       +2.65 V  (min =  +2.25 V, max =  +2.75 V)
in3:       +1.50 V  (min =  +2.25 V, max =  +2.75 V)   ALARM
in4:       +0.00 V  (min =  +0.00 V, max =  +2.99 V)   ALARM
in5:       +0.00 V  (min =  +0.00 V, max =  +2.99 V)   ALARM
in6:       +0.00 V  (min =  +0.00 V, max =  +2.49 V)   ALARM
in7:       +1.34 V  (min =  +1.02 V, max =  +1.68 V)
in8:       +0.00 V  (min =  +0.00 V, max =  +2.49 V)
in9:       +0.75 V  (min =  +0.00 V, max =  +0.76 V)
in10:      +3.12 V  (min =  +2.97 V, max =  +3.64 V)
in11:      +3.42 V  (min =  +2.97 V, max =  +3.64 V)
in12:      +3.38 V  (min =  +2.97 V, max =  +3.64 V)
in13:      +5.10 V  (min =  +4.50 V, max =  +5.49 V)
in14:      +1.34 V  (min =  +1.02 V, max =  +1.68 V)
in15:     +12.19 V  (min = +10.81 V, max = +13.19 V)
in16:     -12.03 V  (min = -13.18 V, max = -10.80 V)
ERROR: Can't get FAN0 data!
fan1:        0 RPM  (min =  712 RPM, div = 8)   ALARM
fan2:        0 RPM  (min =  712 RPM, div = 8)   ALARM
fan3:        0 RPM  (min =  712 RPM, div = 8)
fan4:     6250 RPM  (min =  712 RPM, div = 8)   ALARM
fan5:        0 RPM  (min =  712 RPM, div = 8)   ALARM
fan6:        0 RPM  (min =  712 RPM, div = 8)   ALARM
fan7:        0 RPM  (min =  712 RPM, div = 8)   ALARM
temp1:       +45°C  (low  =    +0°C, high =   +80°C)
temp2:       +47°C  (low  =    +0°C, high =   +78°C)
temp3:       +77°C  (low  =    +0°C, high =   +78°C)
vid:      +0.975 V  (VRM Version 2.4)

w83627hf-isa-0290
Adapter: ISA adapter
VCore 1:   +3.14 V  (min =  +0.00 V, max =  +0.00 V)       ALARM
VCore 2:   +3.10 V  (min =  +0.00 V, max =  +0.00 V)       ALARM
+3.3V:     +3.12 V  (min =  +3.14 V, max =  +3.47 V)       ALARM
+5V:       +5.30 V  (min =  +4.76 V, max =  +5.24 V)       ALARM
+12V:     +11.86 V  (min = +10.82 V, max = +13.19 V)
-12V:      +0.72 V  (min = -13.18 V, max = -10.80 V)       ALARM
-5V:       +2.09 V  (min =  -5.25 V, max =  -4.75 V)       ALARM
V5SB:      +5.67 V  (min =  +4.76 V, max =  +5.24 V)       ALARM
VBat:      +0.00 V  (min =  +2.40 V, max =  +3.60 V)       ALARM
fan1:        0 RPM  (min =    0 RPM, div = 2)
fan2:        0 RPM  (min =    0 RPM, div = 2)
fan3:        0 RPM  (min = 5720 RPM, div = 2)              ALARM
temp1:       -15°C  (high =    -1°C, hyst =    -1°C)   sensor = thermistor
temp2:     -17.0°C  (high =   +80°C, hyst =   +75°C)   sensor = thermistor
temp3:     -16.5°C  (high =   +80°C, hyst =   +75°C)   sensor = thermistor
vid:      +0.000 V  (VRM Version 2.4)
alarms:
beep_enable:
          Sound alarm enabled

```

---

### Post by divdude on 2007-06-22
In my laptop I worked it like this.
First i ran sensors-detect
and ran
lsmod(list all loaded modules)

This is my list:
.
.
.
.
usbcore               134280  3 ehci_hcd,uhci_hcd
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit

you can see thermal and processor modules are loaded

After that i ran
cat proc/acpi/thermal_zone/THRM/temperature 
temperature:             47 C

which i think is cpu temperature.
you can run
cat /proc/acpi/thermal and TAB to get options

---

### Post by libos on 2007-06-22
> **AmericanAqualung said:**
> Ok, so I got this up and running but have a few questions still.  First, I get three sets of output (shown below) for my AMD opteron board with 4 dual core processors (its part of a linux cluster).  Which do I use?  The top two give reasonable values, but disagree and the third is nonsense (neg. temps).  Also, shouldn't I be able to get either 4 or 8 temps for each cpu/core?  And I understand that temp 1 is m/b,  temp2 is cpu, but what is temp3? case?  Thanks a lot.

```
adm1026-i2c-1-2d
Adapter: SMBus nForce2 adapter at 4c40
in0:       +0.00 V  (min =  +0.00 V, max =  +2.99 V)   ALARM
in1:       +0.00 V  (min =  +2.25 V, max =  +2.75 V)   ALARM
in2:       +0.00 V  (min =  +2.25 V, max =  +2.75 V)   ALARM
in3:       +0.00 V  (min =  +2.25 V, max =  +2.75 V)   ALARM
in4:       +0.00 V  (min =  +0.00 V, max =  +2.99 V)   ALARM
in5:       +0.00 V  (min =  +0.00 V, max =  +2.99 V)   ALARM
in6:       +0.00 V  (min =  +0.00 V, max =  +2.49 V)   ALARM
in7:       +1.36 V  (min =  +1.02 V, max =  +1.68 V)
in8:       +0.00 V  (min =  +0.00 V, max =  +2.49 V)
in9:       +0.35 V  (min =  +0.00 V, max =  +0.76 V)
in10:      +3.08 V  (min =  +2.97 V, max =  +3.64 V)
in11:      +3.42 V  (min =  +0.00 V, max =  +4.42 V)
in12:      +3.38 V  (min =  +2.97 V, max =  +3.64 V)
in13:      +3.36 V  (min =  +4.50 V, max =  +5.49 V)   ALARM
in14:      +1.35 V  (min =  +1.02 V, max =  +1.68 V)
in15:      +0.00 V  (min = +10.81 V, max = +13.19 V)   ALARM
in16:      +0.19 V  (min = -13.18 V, max = -10.80 V)   ALARM
ERROR: Can't get FAN0 data!
fan1:        0 RPM  (min =  712 RPM, div = 8)   ALARM
fan2:        0 RPM  (min =  712 RPM, div = 8)
fan3:     6250 RPM  (min =  712 RPM, div = 8)
fan4:     6250 RPM  (min =  712 RPM, div = 8)   ALARM
fan5:        0 RPM  (min =  712 RPM, div = 8)   ALARM
fan6:        0 RPM  (min =  712 RPM, div = 8)   ALARM
fan7:        0 RPM  (min =  712 RPM, div = 8)   ALARM
temp1:       +51°C  (low  =    +0°C, high =   +80°C)
temp2:       +40°C  (low  =    +0°C, high =   +78°C)
temp3:       +36°C  (low  =    +0°C, high =   +78°C)
vid:      +0.975 V  (VRM Version 2.4)

adm1026-i2c-1-2c
Adapter: SMBus nForce2 adapter at 4c40
in0:       +2.62 V  (min =  +0.00 V, max =  +2.99 V)
in1:       +1.22 V  (min =  +2.25 V, max =  +2.75 V)   ALARM
in2:       +2.65 V  (min =  +2.25 V, max =  +2.75 V)
in3:       +1.50 V  (min =  +2.25 V, max =  +2.75 V)   ALARM
in4:       +0.00 V  (min =  +0.00 V, max =  +2.99 V)   ALARM
in5:       +0.00 V  (min =  +0.00 V, max =  +2.99 V)   ALARM
in6:       +0.00 V  (min =  +0.00 V, max =  +2.49 V)   ALARM
in7:       +1.34 V  (min =  +1.02 V, max =  +1.68 V)
in8:       +0.00 V  (min =  +0.00 V, max =  +2.49 V)
in9:       +0.75 V  (min =  +0.00 V, max =  +0.76 V)
in10:      +3.12 V  (min =  +2.97 V, max =  +3.64 V)
in11:      +3.42 V  (min =  +2.97 V, max =  +3.64 V)
in12:      +3.38 V  (min =  +2.97 V, max =  +3.64 V)
in13:      +5.10 V  (min =  +4.50 V, max =  +5.49 V)
in14:      +1.34 V  (min =  +1.02 V, max =  +1.68 V)
in15:     +12.19 V  (min = +10.81 V, max = +13.19 V)
in16:     -12.03 V  (min = -13.18 V, max = -10.80 V)
ERROR: Can't get FAN0 data!
fan1:        0 RPM  (min =  712 RPM, div = 8)   ALARM
fan2:        0 RPM  (min =  712 RPM, div = 8)   ALARM
fan3:        0 RPM  (min =  712 RPM, div = 8)
fan4:     6250 RPM  (min =  712 RPM, div = 8)   ALARM
fan5:        0 RPM  (min =  712 RPM, div = 8)   ALARM
fan6:        0 RPM  (min =  712 RPM, div = 8)   ALARM
fan7:        0 RPM  (min =  712 RPM, div = 8)   ALARM
temp1:       +45°C  (low  =    +0°C, high =   +80°C)
temp2:       +47°C  (low  =    +0°C, high =   +78°C)
temp3:       +77°C  (low  =    +0°C, high =   +78°C)
vid:      +0.975 V  (VRM Version 2.4)

w83627hf-isa-0290
Adapter: ISA adapter
VCore 1:   +3.14 V  (min =  +0.00 V, max =  +0.00 V)       ALARM
VCore 2:   +3.10 V  (min =  +0.00 V, max =  +0.00 V)       ALARM
+3.3V:     +3.12 V  (min =  +3.14 V, max =  +3.47 V)       ALARM
+5V:       +5.30 V  (min =  +4.76 V, max =  +5.24 V)       ALARM
+12V:     +11.86 V  (min = +10.82 V, max = +13.19 V)
-12V:      +0.72 V  (min = -13.18 V, max = -10.80 V)       ALARM
-5V:       +2.09 V  (min =  -5.25 V, max =  -4.75 V)       ALARM
V5SB:      +5.67 V  (min =  +4.76 V, max =  +5.24 V)       ALARM
VBat:      +0.00 V  (min =  +2.40 V, max =  +3.60 V)       ALARM
fan1:        0 RPM  (min =    0 RPM, div = 2)
fan2:        0 RPM  (min =    0 RPM, div = 2)
fan3:        0 RPM  (min = 5720 RPM, div = 2)              ALARM
temp1:       -15°C  (high =    -1°C, hyst =    -1°C)   sensor = thermistor
temp2:     -17.0°C  (high =   +80°C, hyst =   +75°C)   sensor = thermistor
temp3:     -16.5°C  (high =   +80°C, hyst =   +75°C)   sensor = thermistor
vid:      +0.000 V  (VRM Version 2.4)
alarms:
beep_enable:
          Sound alarm enabled

```

Aqualung,

My CPU core temps comes from k8temp module. Not sure you have the module loaded.
Mine looks like this:
----------------------------------
k8temp-pci-00c3
Adapter: PCI adapter
Algorithm: PCI algorithm
Core0 Temp:
             +27°C
Core1 Temp:
             +33°C
----------------------------------

As for the temp3, according to lm-sensors documentation, most of the time the temp3 sensor is disconnected but thats depend on your motherboard. If you dont need it, well just disable it from /etc/sensors.conf file.

[http://www.lm-sensors.org/wiki/iwizard/WrongTemps](http://www.lm-sensors.org/wiki/iwizard/WrongTemps)
[http://www.lm-sensors.org/browser/lm-sensors/trunk/doc/chips/SUMMARY](http://www.lm-sensors.org/browser/lm-sensors/trunk/doc/chips/SUMMARY)

You can find lots more info from the site and also the sensors.conf file

I hope this helps.

---

### Post by Gossie on 2007-06-27
Hi,

Would somebody please look at my temperatures? 


My mobo is a Asus A8N-E, and I have the "Q-fan control" in the Bios enabled (called "Cool 'n' Quiet").
I use Feisty Fawn. My CPU is a AMD Athlon64 3800+ . [edit] There is one big noisy fan in the back, and according to the BIOS I have a CPU fan (going around 3000 rpm) and a thing called chip fan (going around 5000 rpm). So fan1 must be the CPU fan and I apparantly have a chip fan. But the BIOS also mentions a CHA1, chassis fan, going at 0 rpm - so even the bios doesn't 'hear' this propeller. [/edit]

Also, is 127 something to worry about?

In de sensors.conf file, I tried putting the sensors in 'diode' (as suggested on [http://www.lm-sensors.org/wiki/iwizard/WrongTemps]("http://www.lm-sensors.org/wiki/iwizard/WrongTemps")). But that gave the same results. Furthermore, I didn't want to change the formulas in the sensors.conf, because I don't know much about hardware.

Here's my output from 'sensors' and also I give the contents of my /etc/modules 

Thanks for helping!
Gossie


```

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:
             +37°C

it8712-isa-0290
Adapter: ISA adapter
VCore 1:   +1.33 V  (min =  +0.00 V, max =  +3.82 V)   
VCore 2:   +0.00 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
+3.3V:     +3.30 V  (min =  +0.00 V, max =  +4.08 V)   
+5V:       +4.84 V  (min =  +0.00 V, max =  +6.85 V)   
+12V:     +11.84 V  (min =  +0.00 V, max = +16.32 V)   
-12V:      -5.15 V  (min = -27.36 V, max =  +3.93 V)   
-5V:      -13.64 V  (min = -13.64 V, max =  +4.03 V)   ALARM
Stdby:     +4.81 V  (min =  +0.00 V, max =  +6.85 V)   
VBat:      +3.07 V
fan1:     1250 RPM  (min =  811 RPM, div = 8)          
fan2:        0 RPM  (min =    0 RPM, div = 8)          
fan3:     5443 RPM  (min =    0 RPM, div = 8)          
M/B Temp:    +36°C  (low  =    -1°C, high =  +127°C)   sensor = thermistor   
CPU Temp:    +28°C  (low  =    -1°C, high =  +127°C)   sensor = thermistor   
Temp3:       +27°C  (low  =    -1°C, high =  +127°C)   sensor = thermistor   
vid:      +0.875 V

```

```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.


lp


# Generated by sensors-detect on Wed Jun 27 09:13:10 2007 (put them in reverse order as suggested in HOWTO on Ubuntuforums
# Chip drivers
it87
k8temp
eeprom
# I2C adapter drivers
i2c-nforce2

```

Finally, this might be something edgy
```

nijlpaard@haai:~$ sudo modprobe i2c-sensors
FATAL: Module i2c_sensors not found.

```

PS: With Q-fan control (from the mobo bios), the fan1 speed decreases to 900 - 1000 rpm, but I get a bios warning at boot.

---

### Post by libos on 2007-06-27
Hi Gossie,

I guess your fan3 is probably your chasis fan. If you have enable the Q-fan control for chasis fans (there are 2 types of Q-fan control for my MOBO - M2N-E which is the CPU and the MOBO), there is 3 Q-fan control profiles to choose from. Silent,Optimum and Performance. Silent will give you the lowest fan speed possible; optimum will try to balance your temperature and fan speed; and at last the performance profile will give you highest fan speed possible. So check out your bios settings. I am just sharing base on my MOBO.

I got the same issue as your where your MOBO complains about your low CPU fan speed. There are 2 ways (at least what i have found, and any suggestions would be appreciated) to workaround this, first is to disable the alarm and second is to disable the quick boot setting. 

Hope this helps.

---

### Post by Gossie on 2007-06-27
Hi Libos,

Thanks for your advise! After I tried all the things I will mention next, my most important question is, off course, is anybody frightened by my 127? (See my post, two steps above.) 
Would it be wise to uninstall lm-sensors, delete the modules in /etc/modules/  and reset the BIOS settings to default?

I had the idea that I was going to use fancontrol, and I found the HOWTO by 'remmelt': [http://ubuntuforums.org/showthread.php?t=42737]("http://ubuntuforums.org/showthread.php?t=42737"). But, allas, when I want to try the fans with pwmconfig, there is no complete result.

On [http://www.almico.com/forumvotes.php?id=6608177]("http://www.almico.com/forumvotes.php?id=6608177") (as kindly suggested when running pwmconfig) I read that [COLOR="DarkRed"]a lot of people with an Asus A8N-E Motherboard cannot control the fans exept the CPU fan[/COLOR]. There is one post that says: "Got it to work on CPU fan by setting PWM1 mode to Software controlled under the Advanced tab." But that option is not in my BIOS (maybe it needs an upgrade...). I disabled "Cool 'n' Quiet". Still, pwmconfig is not working properly (same as with cool&quiet enabled).

Like you suggested, Libos, :popcorn:, I switched off the CHA1 (chassis fan) warning AND I disabled Quick boot. Then the CPU fan is  sometimes going easier: 1100 rpm. 
But the chassis fan is still constant at 5400 rpm. In the BIOS, it says CHA1 is 0 rpm but lm-sensors says fan3 is 5400.  And I still had the pwmconfig problems...

When I disable "Q-fan control", I just get "There are no pwm-capable sensor modules installed". 
"Cool 'n' Quiet" disabled or enabled had no effect on pwm-config, with "Q fan controller" on or off. With Q-fan control enabled, I get the results underneath.

Thanks, 
   Gossie

```

~$ sudo pwmconfig
Password:
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.

We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.

Found the following PWM controls:
   9191-0290/pwm1
   9191-0290/pwm2
   9191-0290/pwm3

Found the following fan sensors:
   9191-0290/fan1_input     current speed: 1562 RPM
   9191-0290/fan2_input     current speed: 0 ... skipping!
   9191-0290/fan3_input     current speed: 5443 RPM

Warning!!! This program will stop your fans, one at a time,
for approximately 5 seconds each!!!
This may cause your processor temperature to rise!!!
If you do not want to do this hit control-C now!!!
Hit return to continue: 

Testing pwm control 9191-0290/pwm1 ...
  9191-0290/fan1_input ... speed was 1562 now 0
    It appears that fan 9191-0290/fan1_input
    is controlled by pwm 9191-0290/pwm1
Would you like to generate a detailed correlation (y)? y
    PWM 255 FAN 3183
    PWM 240 FAN 3125
    PWM 225 FAN 2860
    PWM 210 FAN 2678
    PWM 195 FAN 2481
    PWM 180 FAN 2280
    PWM 165 FAN 2057
    PWM 150 FAN 1854
    PWM 135 FAN 1622
    PWM 120 FAN 1406
    PWM 105 FAN 1155
    PWM 90 FAN 942
    PWM 75 FAN 680
    PWM 60 FAN 0
    Fan Stopped at PWM = 60

  9191-0290/fan3_input ... speed was 5443 now 5273
    no correlation

Testing pwm control 9191-0290/pwm2 ...
  9191-0290/fan1_input ... speed was 1562 now 3245
    no correlation
  9191-0290/fan3_input ... speed was 5443 now 5443
    no correlation

No correlations were detected.
There is either no fan connected to the output of 9191-0290/pwm2,
or the connected fan has no rpm-signal connected to one of
the tested fan sensors. (Note: not all motherboards have
the pwm outputs connected to the fan connectors,
check out the hardware database on http://www.almico.com/forumindex.php)

[COLOR="DarkRed"]Did you see/hear a fan stopping during the above test (n)? y[/COLOR]

Testing pwm control 9191-0290/pwm3 ...
  9191-0290/fan1_input ... speed was 1562 now 3245
    no correlation
  9191-0290/fan3_input ... speed was 5443 now 5273
    no correlation

No correlations were detected.
There is either no fan connected to the output of 9191-0290/pwm3,
or the connected fan has no rpm-signal connected to one of
the tested fan sensors. (Note: not all motherboards have
the pwm outputs connected to the fan connectors,
check out the hardware database on http://www.almico.com/forumindex.php)

[COLOR="DarkRed"]Did you see/hear a fan stopping during the above test (n)? n[/COLOR]

Testing is complete.
Please verify that all fans have returned to their normal speed.

The fancontrol script can automatically respond to temperature changes
of your system by changing fanspeeds.
Do you want to set up its configuration file now (y)? y
What should be the path to your fancontrol config file (/etc/fancontrol)? y
Loading configuration from /etc/fancontrol ...

Select fan output to configure, or other action:
1) 9191-0290/pwm2      3) Change INTERVAL     5) Save and quit
2) 9191-0290/pwm1      4) Just quit           6) Show configuration
select (1-n): 6

Common Settings:
INTERVAL=10

Settings of 9191-0290/pwm2:
  Depends on 
  Controls 9191-0290/fan1_input
  MINTEMP=
  MAXTEMP=
  MINSTART=
  MINSTOP=

Settings of 9191-0290/pwm1:
  Depends on 
  Controls 9191-0290/fan1_input
  MINTEMP=
  MAXTEMP=
  MINSTART=
  MINSTOP=

select (1-n): 3

Current interval is 10 seconds.
Enter the interval at which fancontrol should update PWM values (in s):5
select (1-n): 2

Current temperature readings are as follows:
9191-0290/temp1_input   38
9191-0290/temp2_input   30
9191-0290/temp3_input   27

Select a temperature sensor as source for 9191-0290/pwm1:
1) 9191-0290/temp1_input
2) 9191-0290/temp2_input
3) 9191-0290/temp3_input
4) None (Do not affect this PWM output)
select (1-n): 4
select (1-n): 4

~$ 


```

This is what my BIOS says about the settings, rpm's and temparatures. These settings give the same output for the sensors as I posted earlier today.

[LIST]
[*]Cool 'n' Quiet      enabled
[*]Q fan controller  enabled
[*]Quick boot           disabled

[*]CPU Temperature  38  C
[*]M/B Temperature  30  C

[*]CPU Fan Speed    3183 RPM
[*]CHA1 Fan Speed      0 RPM
[*]Chip Fan Speed   5192 RPM

[*]CPU Target Temperature   72  C

[*]CPU Fan Speed warning   800 RPM
[*]CHA1 Fan Speed warning  Disabled
[*]CHIP Fan Speed warning  Enabled
[/LIST]

---

### Post by asmweb on 2007-06-29
Hi there,

well i'm still suffering with the lm-sensors, I did follow[this guide]("https://help.ubuntu.com/community/SensorInstallHowto"). It did go ahead all ok and here is what my /etc/module file is

# Generated by sensors-detect on Fri Jun 29 11:41:21 2007
# I2C adapter drivers
# modprobe unknown adapter NVIDIA i2c adapter 0 at 1:00.0
# modprobe unknown adapter NVIDIA i2c adapter 1 at 1:00.0
# modprobe unknown adapter NVIDIA i2c adapter 2 at 1:00.0
i2c-i801
# Chip drivers
eeprom

after that I did 
modprobe  i2c-i801
modprobe eeprom

and my modprobe -L conferms that...

did the reboot too but still when I type  sensors I get this:

No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.

How come? 

I got an Dell Latitude D620 computer...

any help would be appreciated

---

### Post by Gossie on 2007-06-29
> **libos said:**
>  (there are 2 types of Q-fan control for my MOBO - M2N-E which is the CPU and the MOBO), there is 3 Q-fan control profiles to choose from. Silent,Optimum and Performance. 


Hi Libos,

There is only one choise in my BIOS: Q fan controller enabled or disabled. I cannot control the Chassis fan, and a lot of other people who have the same mobo, Asus A8N-E, have the same problem. 

In your blog ([http://bsling.blogspot.com/2007/06/hardware-health-monitoring-on-asus-m2n.html]("http://bsling.blogspot.com/2007/06/hardware-health-monitoring-on-asus-m2n.html")) I saw you have also 127 degrees Celcius as high temp, according to your 'sensors' (lm-sensors) ouput. And then you have read some specifications about your hardware and then you changed the min. and max. temperature. Cool.

Do you get your chassis fan under control with pwmconfig? Did you install fancontrol?

Bye,
Gossie

---

### Post by libos on 2007-07-01
Hi Gossie,

The +127C is probably the high limit for the lm-sensors monitoring. Probably can be set in the sensors.conf but i am not so sure. I am using the sensors applet to monitor my temperatures.

I have just setup the pwmconfig and it works like charm :)
[http://bsling.blogspot.com/2007/06/fancontrol.html](http://bsling.blogspot.com/2007/06/fancontrol.html)

---

### Post by Rich1386 on 2007-07-19
I tried following the instructions, but on the reboot, grub selected ubuntu fine, but the screen went dead.  I tried undoing as much of the stuff as I could, including uninstalling lm-sensors, but nothing.  In recovery mode, I used to get some message about sensors failing while booting.  Don't get it after I tried fixing it.

---

### Post by adub on 2007-07-25
Sorry, no chips were detected.
 Either your sensors are not supported, or they are
 connected to an I2C bus adapter that we do not support.
 See doc/FAQ, doc/lm_sensors-FAQ.html, or
 [http://www2.lm-sensors.nu/~lm78/cvs/lm_sensors2/doc/lm_sensors-FAQ.html](http://www2.lm-sensors.nu/~lm78/cvs/lm_sensors2/doc/lm_sensors-FAQ.html)
 (FAQ #4.24.3) for further information.
 If you find out what chips are on your board, see
 [http://secure.netroedge.com/~lm78/newdrivers.html](http://secure.netroedge.com/~lm78/newdrivers.html) for driver status.


I got to sensors-detect and answered yes to all the questions and i get the following output at the end.

i tried going to the websites but they require a password

---

### Post by adub on 2007-07-25
I have the below motherboard

MSI P6N SLI Platinum motherboard with the NVIDIA nForce 850i chipset

I had seen mention that others were having difficulty with this particular board in getting lm-sensors to work

I am still working on this but i feel I am on the right path


I2C/SMBUS BUS DRIVERS - STATUS
nVidia 	 MCP51, MCP55 	 yes 	 i2c-nforce2 	 2.10.1 	 2.6.18

SENSOR CHIP DRIVERS - STATUS
Fintek 	 F71882FG/F71883FG 	 yes 	 	 	 

according to the above the device list indicates for my motherboard lm-sensors has been working since 2.10.1   with kernel version 2.6.18.   for the sensor chip drivers i heard that someone has this working with this motherboard, but they did not post a howto.  I had seen browsing the web.

my problem is i can not find the driver to download to install anywhere.  I also am thinking i need to update my kernel to have the i2c-nforce2 support.

# uname -a
Linux adub-desktop 2.6.17-12-generic #2 SMP Mon Jul 16 19:37:58 UTC 2007 i686 GNU/Linux

it appears i need to update kernel for i2c-nforce2 support for my particular bus drivers "i think"
although lspci list them but i think for them to work with lmsensors then maybe the update is needed

now on the fintek driver i have no clue rebuild kernel  100% clueless

---

### Post by gtstephenson on 2007-07-29
I did just fine till I had to plug the sensors in.

Any suggestions?

Tom S.

root@Toms_Laptop:/etc# modprobe i2c-sensor
FATAL: Module i2c_sensor not found.

---

### Post by mr4thjuly on 2007-08-08
This is an excellent How to.  I just wanted to ask which one is the Harddrive temperature. I know that I have a hard drive temperature sensor but I don't see and output for it, or maybe one of them is the Hard drive temperature but I just don't know it yet.
Thanks in advance.

---

### Post by Pathfinder_ on 2007-08-18
lm-senors worked flawlessly on my desktop now when I try to get them working on my laptop(dell latitude c640) i get the following:

```
# sensors-detect revision 4171 (2006-09-24 03:37:01 -0700)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): y
Probing for PCI bus adapters...
Sorry, no known PCI bus adapters found.

We will now try to load each adapter module in turn.
If you have undetectable or unsupported adapters, you can have them
scanned by manually loading the modules before running this script.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!
Do you want to scan the ISA I/O ports? (YES/no): y
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM78-J' at 0x290...     No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No
Probing for `Winbond W83627HF' at 0x290...                  No
Probing for `Silicon Integrated Systems SIS5595'...         No
Probing for `VIA VT82C686 Integrated Sensors'...            No
Probing for `VIA VT8231 Integrated Sensors'...              No
Probing for `AMD K8 thermal sensors'...                     No
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some Super I/O chips may also contain sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): y
Probing for Super-I/O at 0x2e/0x2f
Trying family `ITE'...                                      Yes
Found unknown chip with ID 0x0e01
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     Yes
Found unknown chip with ID 0x0e01
Trying family `VIA/Winbond/Fintek'...                       No
Probing for Super-I/O at 0x4e/0x4f
Trying family `ITE'...                                      No
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No

Sorry, no sensors were detected.
Either your sensors are not supported, or they are connected to an
I2C or SMBus adapter that is not supported. See doc/FAQ,
doc/lm_sensors-FAQ.html or http://www.lm-sensors.org/wiki/FAQ
(FAQ #4.24.3) for further information.
If you find out what chips are on your board, check
http://www.lm-sensors.org/wiki/Devices for driver status.

```

Can anyone help me get this working on my laptop?

---

### Post by nauj27 on 2007-08-29
> **umdzig said:**
> I have a dell inspiron 8600. All i get when i try to use lm sensors is it says no sensors detected. Can someone tell me what driver i am supposed to use so i can get this to work correctly?

Install i8kutils and sensors-applet. Make sure to load i8k kernel module and you are ready.

---

### Post by leona on 2007-08-29
> **leona said:**
> Hi, can someone help me out here.
This used to work for me, I had an Asus A8V VIA board, now I've upgraded to an Asus M2N-E boad NForce, and now non of the sensors are detected.
I reran the scripts, ran Sensor-detect, installed the required Kernal moduals, but alas when I do 'sensors' I get No Sensors Found, 
What can I do to fix this?
nterestingly upgrading to 7.04 Fiesty Fixed this problem for me, I now have Temps and Fans, yippy! v-happy now.

---

### Post by Psykedelic on 2007-10-18
Hi!
I have some problems with ls-sensors...
I have the P4B motherboard, so the SMBus is hidden and therefore lm-sensors-detect can't find anything...

I've read about the patch for 2.4-kernels, but i'm running 2.6.
I don't know if I understood this matter correctly, but is it so that I have to edit and recompile the kernel with the quirks.c part changed?
I'm an absolute beginner with linux, so I will not attempt to do this...

My second quesition is if anybody knows if there will be support for the P4B motherboard in upcoming kernels?

---

### Post by Yes on 2007-10-24
They work fine for me, but how would I find the sensors for the CPU temp?  So that it would just display the CPU temp, and nothing else?

---

### Post by Icarosaurus on 2007-10-26
Try hardware sensors monitor applet in the desktop panel.
You can install it from synaptic if you don't find it in "add to panel" applets.

---

### Post by PurposeOfReason on 2007-10-27
Which one is more accurate for my CPU? I have a core 0, core 1, and CPU Temp. I like that last because it is lowest. :)

```

shawn@Reasons:~$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +40°C  (high =  +100°C)                   

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +36°C  (high =  +100°C)                   

w83627dhg-isa-0290
Adapter: ISA adapter
VCore:     +1.16 V  (min =  +0.00 V, max =  +1.74 V) 
in1:      +12.46 V  (min =  +1.69 V, max =  +0.53 V) ALARM
AVCC:      +3.22 V  (min =  +1.58 V, max =  +0.26 V) ALARM
3VCC:      +3.20 V  (min =  +0.64 V, max =  +2.05 V) ALARM
in4:       +0.74 V  (min =  +0.26 V, max =  +0.89 V) 
in5:       +1.62 V  (min =  +0.59 V, max =  +0.51 V) ALARM
in6:       +2.20 V  (min =  +2.05 V, max =  +4.22 V) 
VSB:       +3.22 V  (min =  +2.72 V, max =  +2.19 V) ALARM
VBAT:      +2.05 V  (min =  +1.54 V, max =  +0.51 V) ALARM
Case Fan: 2445 RPM  (min = 3879 RPM, div = 4) ALARM
CPU Fan:     0 RPM  (min =  458 RPM, div = 128) ALARM
Aux Fan:     0 RPM  (min = 3515 RPM, div = 128) ALARM
fan4:        0 RPM  (min = 10546 RPM, div = 128) ALARM
fan5:        0 RPM  (min = 10546 RPM, div = 128) ALARM
Sys Temp:    +31°C  (high =   +33°C, hyst =    +0°C)   ALARM
CPU Temp:  +33.0°C  (high = +80.0°C, hyst = +75.0°C)  
AUX Temp: +124.5°C  (high = +80.0°C, hyst = +75.0°C)   ALARM

shawn@Reasons:~$ 

```

All that fans (minus one) are at 0 because I use a fan controller.

---

### Post by Sonic Reducer on 2007-10-28
$acpitemp always says 32F in conky, what is the name of my CPU sensor?

heres my output of **sensors**
```
ryan@ryan-desktop:~$ sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:
             +31°C

w83627ehf-isa-0290
Adapter: ISA adapter
VCore:     +1.17 V  (min =  +0.00 V, max =  +1.74 V) 
in1:      +12.20 V  (min =  +4.49 V, max =  +1.69 V) ALARM
AVCC:      +3.22 V  (min =  +0.02 V, max =  +2.66 V) ALARM
3VCC:      +3.22 V  (min =  +2.51 V, max =  +0.46 V) ALARM
in4:       +2.04 V  (min =  +1.13 V, max =  +1.90 V) ALARM
in5:       +1.61 V  (min =  +0.02 V, max =  +0.16 V) ALARM
in6:       +5.17 V  (min =  +1.00 V, max =  +0.18 V) ALARM
VSB:       +3.22 V  (min =  +2.83 V, max =  +0.26 V) ALARM
VBAT:      +0.66 V  (min =  +3.78 V, max =  +0.18 V) ALARM
in9:       +1.54 V  (min =  +0.14 V, max =  +0.06 V) ALARM
Case Fan:    0 RPM  (min =  263 RPM, div = 128) ALARM
CPU Fan:     0 RPM  (min =   76 RPM, div = 128) ALARM
Aux Fan:  2327 RPM  (min = 2636 RPM, div = 4) ALARM
fan5:        0 RPM  (min = 24107 RPM, div = 8) ALARM
Sys Temp:    +30°C  (high =  -111°C, hyst =  -124°C)   ALARM
CPU Temp:  +25.5°C  (high = +80.0°C, hyst = +75.0°C)  
AUX Temp:  +25.5°C  (high = +80.0°C, hyst = +75.0°C)  
```

i thought it would be k8temp but that does not work, what am i doing wrong here?

---

### Post by ahunor on 2007-11-07
Hi there

Getting lm-sensors to work has never meant tourble, but now, as I'm on my Toshiba A200-14D laptop, it's driving me crazy...I can get readings only from the CPU.

sensors-detect says that I only need two modules, one for the cpu ( which is ok ), and 'smartbatt'...which would take care of the battery ( and, as sensors-detect says my nvidia GPU too ? ).

In the nvidia control panel I can see the temp of my card...nowhere else.

The Question : Where, in the kernel source could I find the smartbatt hw sensor support setting ?

thanks.

---

### Post by moving fusion on 2007-11-21
Hi,

This is a post about w83627dhg (w83627ehf).

I have got it working on 7.10 kernel 2.6.23 (no support in kubuntu stock kernel so i thought might as well get the latest) [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu).

I was also using the version of lm-sensors via apt-get this didn't work even though sensors-detect etc was detecting the hardware.

I have just installed lm_sensors-3.0.0-rc3 with some issues with deps but sorted out easily enough.

I have a ASUS Maximus Formula mobo with Q6600:

~$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +37.0°C  (crit = +100.0°C)

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +36.0°C  (crit = +100.0°C)

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +34.0°C  (crit = +100.0°C)

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +34.0°C  (crit = +100.0°C)

w83627dhg-isa-0290
Adapter: ISA adapter
VCore:       +1.32 V  (min =  +0.00 V, max =  +1.74 V)
in1:        +11.35 V  (min =  +0.84 V, max =  +4.70 V)   ALARM
AVCC:        +3.18 V  (min =  +0.34 V, max =  +2.21 V)   ALARM
3VCC:        +3.18 V  (min =  +1.23 V, max =  +1.04 V)   ALARM
in4:         +1.53 V  (min =  +1.02 V, max =  +0.29 V)   ALARM
in5:         +1.76 V  (min =  +0.02 V, max =  +0.38 V)   ALARM
in6:         +5.02 V  (min =  +5.15 V, max =  +1.66 V)   ALARM
VSB:         +3.18 V  (min =  +2.05 V, max =  +2.30 V)   ALARM
VBAT:        +3.18 V  (min =  +2.34 V, max =  +2.05 V)   ALARM
Case Fan:      0 RPM  (min =  319 RPM, div = 128)  ALARM
CPU Fan:    2789 RPM  (min = 2986 RPM, div = 2)  ALARM
Aux Fan:    1917 RPM  (min =  216 RPM, div = 32)
fan5:       2109 RPM  (min =  180 RPM, div = 32)
Sys Temp:    +30.0°C  (high = +97.0°C, hyst =  +0.0°C)  sensor = thermistor
CPU Temp:    +28.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
AUX Temp:     +7.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor

if anyone needs more info i will be happy to help.

---

### Post by jludeman on 2007-12-01
Thanks for the how to. Worked great on my system.

A little off topic but how do I get this info onto the destop. I searched the forums and this thread for how to show this in conky. No luck. The conky man page does not help either.

Is there another desktop app that will show the cpu temp?

Or do I just have to type sensors in a terminal once in a while?

---

### Post by jludeman on 2007-12-02
Never mind. I gave up on conky altogether. I'm now using Gkrellm which works fine with lm sensors and is easy to set up.

---

### Post by thealmightyone on 2007-12-04
A slight problem with lm-sensors.

When I run sensors-detect, I am told no sensors were detected. I am hoping that I did not install lm-sensors correctly, or this script didn't run correctly, rather than my motherboard is not supported.

Should I get this output when I run the script:

> andy@andy-laptop:~$ sudo ./mkdev.sh
/dev/i2c-0
mknod: `/dev/i2c-0': File exists


---

### Post by MortenE on 2007-12-06
I only get this output:

```
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +32°C  (high =  +100°C)                   

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +35°C  (high =  +100°C)    
```

In windows I get readings of fan, gpu temp, chip temp and hard drive temp aswell.. What could be the problem? I have a Dell XPS M1330.

---

### Post by glósóli on 2007-12-07
that first post of November _2004_ is still updated and valid?

I don't want to engage myself in something outdated, just to discover after endelssly errors that that howto was quite old!

I'm on Ubuntu 7.10...

thank you!

---

### Post by Rafa.Supr on 2007-12-10
I only had to install lm-sensors with synaptic, after that run the command sensors-detect and a reboot. It worked like a charm!

---

### Post by Gourgi on 2007-12-11
> **Rafa.Supr said:**
> I only had to install lm-sensors with synaptic, after that run the command sensors-detect and a reboot. It worked like a charm!
i tried that and k8temp loaded but the other module it didnl't
so i followed the guide and everthing seems ok now (w83627hf module loaded fine :) )
so the guide is valid for me 
time to reboot know!

---

### Post by OffHand on 2007-12-12
> **glósóli said:**
> that first post of November _2004_ is still updated and valid?

I don't want to engage myself in something outdated, just to discover after endelssly errors that that howto was quite old!

I'm on Ubuntu 7.10...

thank you!

Still works...

---

### Post by tmcmulli on 2007-12-13
Not sure if anyone answered you...  try the i2c variable... (${i2c tempf 2})

That should get you your CPU...

> **Sonic Reducer said:**
> $acpitemp always says 32F in conky, what is the name of my CPU sensor?

heres my output of **sensors**
```
ryan@ryan-desktop:~$ sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:
             +31°C

w83627ehf-isa-0290
Adapter: ISA adapter
VCore:     +1.17 V  (min =  +0.00 V, max =  +1.74 V) 
in1:      +12.20 V  (min =  +4.49 V, max =  +1.69 V) ALARM
AVCC:      +3.22 V  (min =  +0.02 V, max =  +2.66 V) ALARM
3VCC:      +3.22 V  (min =  +2.51 V, max =  +0.46 V) ALARM
in4:       +2.04 V  (min =  +1.13 V, max =  +1.90 V) ALARM
in5:       +1.61 V  (min =  +0.02 V, max =  +0.16 V) ALARM
in6:       +5.17 V  (min =  +1.00 V, max =  +0.18 V) ALARM
VSB:       +3.22 V  (min =  +2.83 V, max =  +0.26 V) ALARM
VBAT:      +0.66 V  (min =  +3.78 V, max =  +0.18 V) ALARM
in9:       +1.54 V  (min =  +0.14 V, max =  +0.06 V) ALARM
Case Fan:    0 RPM  (min =  263 RPM, div = 128) ALARM
CPU Fan:     0 RPM  (min =   76 RPM, div = 128) ALARM
Aux Fan:  2327 RPM  (min = 2636 RPM, div = 4) ALARM
fan5:        0 RPM  (min = 24107 RPM, div = 8) ALARM
Sys Temp:    +30°C  (high =  -111°C, hyst =  -124°C)   ALARM
CPU Temp:  +25.5°C  (high = +80.0°C, hyst = +75.0°C)  
AUX Temp:  +25.5°C  (high = +80.0°C, hyst = +75.0°C)  
```

i thought it would be k8temp but that does not work, what am i doing wrong here?

---

### Post by DirtDart on 2007-12-30
Guide still works like a charm!

To be honest, I didn't realize that the 1st post was 3+ years old until AFTER I followed it (nice attention to detail, huh?), but it worked without any problems.


Thanks again for posting this guide.

---

### Post by mysticmatrix on 2008-01-01
Worked for me in Gutsy...
But my Intel DG965RY reported sensors only for the CPU temp... Hmnn that's odd :confused:

---

### Post by mackid on 2008-01-05
Hi,

The guide worked for me, but I don't know which temperatures are my CPU! I have an Athlon 64 X2 4000, socket AM2, and an MSI motherboard.

I'm running Ubuntu 7.10:
```
$ uname -a
Linux hostname 2.6.22-14-generic #1 SMP Tue Dec 18 05:28:27 UTC 2007 x86_64 GNU/Linux
```

Here's the output from sensors:
```

$ sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:
             +34°C
Core0 Temp:
             +23°C
Core1 Temp:
             +28°C
Core1 Temp:
             +25°C

w83627ehf-isa-0290
Adapter: ISA adapter
VCore:     +1.30 V  (min =  +0.00 V, max =  +1.74 V) 
in1:      +12.51 V  (min = +13.46 V, max = +11.77 V) ALARM
AVCC:      +3.30 V  (min =  +3.12 V, max =  +2.61 V) ALARM
3VCC:      +3.30 V  (min =  +4.08 V, max =  +4.03 V) ALARM
in4:       +2.04 V  (min =  +0.98 V, max =  +1.98 V) ALARM
in5:       +1.61 V  (min =  +1.53 V, max =  +1.35 V) ALARM
in6:       +5.09 V  (min =  +6.07 V, max =  +4.48 V) ALARM
VSB:       +3.30 V  (min =  +3.82 V, max =  +3.04 V) ALARM
VBAT:      +3.22 V  (min =  +1.57 V, max =  +1.92 V) ALARM
in9:       +1.61 V  (min =  +1.94 V, max =  +1.34 V) ALARM
Case Fan:    0 RPM  (min =    0 RPM, div = 128)
CPU Fan:  1730 RPM  (min = 5532 RPM, div = 4) ALARM
Aux Fan:     0 RPM  (min = 3515 RPM, div = 128) ALARM
fan5:        0 RPM  (min =    0 RPM, div = 128)
Sys Temp:    +33°C  (high =   -71°C, hyst =  +122°C)  
CPU Temp:  +49.0°C  (high = +100.0°C, hyst = +95.0°C)  
AUX Temp:  +51.0°C  (high = +100.0°C, hyst = +95.0°C) 
```

The core temps seem a lot lower than the CPU Temp, and the temps for the same core differ by a lot as well (34C and 23C, same core!?) Which is correct? Could someone inform me? Thanks a lot.

---

### Post by dcstar on 2008-01-05
> **mackid said:**
> Hi,

The guide worked for me, but I don't know which temperatures are my CPU! I have an Athlon 64 X2 4000, socket AM2, and an MSI motherboard.
........
Here's the output from sensors:
```

$ sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:
             +34°C
Core0 Temp:
             +23°C
Core1 Temp:
             +28°C
Core1 Temp:
             +25°C
......... 
```

The core temps seem a lot lower than the CPU Temp, and the temps for the same core differ by a lot as well (34C and 23C, same core!?) Which is correct? Could someone inform me? Thanks a lot.

I have just installed the same CPU on an Asus MB (replacing a Sempron 3400 which seemed to report temps ok) and have similar weird core temps.

Doing a web search seems to show this as a known problem, and it may be fixed in the new lm-sensors 3.0 package - we will just have to wait for the Ubuntu/Debian developers to start using this new package.

---

### Post by Epic Plecostomus on 2008-01-09
Got my sensors up and running... what choices do i have as far as graphical output for Im-sensors?   Xsensor is nice but I would prefer somthing I can minimze to a bar and set my own alarm bands for.

---

### Post by dcstar on 2008-01-10
> **dcstar said:**
> I have just installed the same CPU on an Asus MB (replacing a Sempron 3400 which seemed to report temps ok) and have similar weird core temps.

Doing a web search seems to show this as a known problem, and it may be fixed in the new lm-sensors 3.0 package - we will just have to wait for the Ubuntu/Debian developers to start using this new package.

I have just done some more research and found that the "Brisbane" core AMD X2 CPUs have a known problem with the accuracy of the temperature diodes (as reported by k8temp). These are the later 65W CPUs, the earlier 89W versions apparently report ok.

It looks like those of us with the Brisbane core CPUs will have to disregard the k8temp data, and find alternative reporting (from the motherboard).

---

### Post by SanskritFritz on 2008-01-29
> **emperor said:**
> Howto Install and Configure lm-sensors
Thank you **emperor** it worked out of the box! Great how-to!

---

### Post by a-converted-sparky on 2008-01-30
Hi peeps (i am a newbie)

I have got to stage  3. and ran
sudo sensors-detect

i have copied the output:

# Chip drivers
coretemp

but i do not have a directory/file for
/etc/modules

the insturction says to "To make the sensors modules behave correctly, add these lines to /etc/modules"  ...

any ideas?

I can do the next part:Then, run /etc/init.d/module-init-tools - thats fine

---

### Post by Nikos.Alexandris on 2008-01-31
I have a Samsung R20, Intel dual core duo 2 GHz.. but no luck with fancontrol. I get information only about temperature... which is really high always and the "coolers" run like crazy non-stop!

Anything I miss?

$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +69°C  (high =  +100°C)                   

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +69°C  (high =  +100°C)

---

### Post by Vadi on 2008-01-31
I found the Hardinfo ([http://getdeb.net/search.php?keywords=hardinfo](http://getdeb.net/search.php?keywords=hardinfo)) program to be a lot more useful. Provides the sensors data plus a ton of more things about your comp, all in one nice program.

---

### Post by Bruce M. on 2008-03-01
> **emperor said:**
> Howto Install and Configure lm-sensors

Since there is no "Thank You" button here:

[CENTER][B][SIZE="5"]Thank You[/SIZE]
for this post/thread[/B][/CENTER]

---

### Post by DasCrushinator on 2008-03-01
> **Bruce M. said:**
> Since there is no "Thank You" button here:

[CENTER][B][SIZE="5"]Thank You[/SIZE]
for this post/thread[/B][/CENTER]

Button next to Quote button.

---

### Post by Bruce M. on 2008-03-01
> **DasCrushinator said:**
> Button next to Quote button.

I know, but it doesn't show up until **Post #227 on Page 23** in this thread.

There isn't one on **Post #1** to thank ***emperor*** for the original HowTo.

So: :guitar: "I diiiiid iiiiiT .... myyyyyy wayyyyyy" :guitar:

---

### Post by DasCrushinator on 2008-03-01
> **Bruce M. said:**
> I know, but it doesn't show up until **Post #227 on Page 23** in this thread.

There isn't one on **Post #1** to thank ***emperor*** for the original HowTo.

So: :guitar: "I diiiiid iiiiiT .... myyyyyy wayyyyyy" :guitar:

lol

Didn't even check until just now, sorry :)

---

### Post by Bruce M. on 2008-03-01
> **DasCrushinator said:**
> lol

Didn't even check until just now, sorry :)

No need to be.
Besides a "personal" Thank You is always nicer. It means that someone took the time to type it in.

---

### Post by Miroku on 2008-03-01
so i got to this stage after sensors-detect:

```
To make the sensors modules behave correctly, add these lines to
/etc/modules:

#----cut here----
# I2C adapter drivers
# modprobe unknown adapter NVIDIA i2c adapter 
# modprobe unknown adapter NVIDIA i2c adapter 
# modprobe unknown adapter NVIDIA i2c adapter 
# Chip drivers
# Warning: the required module smartbatt is not currently installed
# on your system. For status of 2.6 kernel ports check
# http://www.lm-sensors.org/wiki/Devices. If driver is built
# into the kernel, or unavailable, comment out the following line.
smartbatt
it87
coretemp
#----cut here----


Do you want to add these lines to /etc/modules automatically? (yes/NO)
```

i chose NO and now i need some further clarification please. thx.

---

### Post by bulldog on 2008-03-02
Better choose Yes instead,or add the lines manually.

---

### Post by andymadonna on 2008-03-16
Hi I have a Sony Vaio and the fans used to be controlled in windows so that they would slow down after startup. I was able to get the sensors and fans detected, but how do I slow down the fans? Or get them controlled depending on temperature. This is just a kitchen computer for internet surfing, so it probably doesn't need the fans to ever run this high. But right now its just so loud.

```

michelle@michelle-desktop:~$ sensors
w83627hf-isa-0290
Adapter: ISA adapter
VCore 1:   +1.71 V  (min =  +1.65 V, max =  +2.05 V)              
VCore 2:   +0.00 V  (min =  +1.65 V, max =  +2.05 V)       ALARM  
+3.3V:     +3.26 V  (min =  +2.82 V, max =  +3.79 V)              
+5V:       +5.11 V  (min =  +5.83 V, max =  +6.32 V)       ALARM  
+12V:     +11.73 V  (min = +10.64 V, max =  +7.54 V)       ALARM  
-12V:     -12.03 V  (min =  +0.72 V, max =  -4.88 V)       ALARM  
-5V:       +3.54 V  (min =  +4.90 V, max =  +4.50 V)       ALARM  
V5SB:      +5.54 V  (min =  +5.56 V, max =  +5.97 V)       ALARM  
VBat:      +3.87 V  (min =  +3.01 V, max =  +4.03 V)              
fan1:     3835 RPM  (min = 2947 RPM, div = 2)                     
fan2:     1985 RPM  (min = 3708 RPM, div = 4)              ALARM  
fan3:        0 RPM  (min =    0 RPM, div = 2)                     
temp1:       -48°C  (high =   -69°C, hyst =   -11°C)   sensor = thermistor           
temp2:     +46.5°C  (high =   +80°C, hyst =   +75°C)   sensor = diode           
temp3:     +41.0°C  (high =   +80°C, hyst =   +75°C)   sensor = thermistor           
vid:      +1.750 V  (VRM Version 9.0)
alarms:   
beep_enable:
          Sound alarm enabled


```

Any help thanks!

---

### Post by libos on 2008-03-16
Hi andymadonna,

I wrote these in my blog to remind me of how i configure my fancontrol with the lmsensors. I hope this could help you with it.

[http://bsling.blogspot.com/search?q=fan+control](http://bsling.blogspot.com/search?q=fan+control)

---

### Post by Kiri on 2008-03-27
Only a couple of sensors seems to have got detected:

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +63.0°C  (crit = +100.0°C)                  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +67.0°C  (crit = +100.0°C)                  



Shouldnt I have more?

---

### Post by Jugix on 2008-04-09
Nice HOWTO! Now I can seriously overclock my CPU with linux because I know core temps now. TY! :popcorn:
```
w83627dhg-isa-0290
Adapter: ISA adapter
VCore:       +1.34 V  (min =  +0.00 V, max =  +1.74 V)   
in1:         +6.07 V  (min =  +8.98 V, max =  +8.40 V)   ALARM
AVCC:        +3.25 V  (min =  +3.55 V, max =  +1.10 V)   ALARM
3VCC:        +3.25 V  (min =  +2.86 V, max =  +0.27 V)   ALARM
in4:         +1.24 V  (min =  +1.87 V, max =  +0.58 V)   ALARM
in5:         +1.34 V  (min =  +1.38 V, max =  +1.54 V)   ALARM
in6:         +5.02 V  (min =  +2.87 V, max =  +0.15 V)   ALARM
VSB:         +3.22 V  (min =  +2.59 V, max =  +2.13 V)   ALARM
VBAT:        +3.18 V  (min =  +2.32 V, max =  +2.40 V)   ALARM
Case Fan:      0 RPM  (min =  340 RPM, div = 128)  ALARM
CPU Fan:    2721 RPM  (min =  332 RPM, div = 16)
Aux Fan:       0 RPM  (min =  340 RPM, div = 128)  ALARM
fan4:          0 RPM  (min =  340 RPM, div = 128)  ALARM
fan5:          0 RPM  (min = 1318 RPM, div = 128)  ALARM
Sys Temp:    +38.0°C  (high = +13.0°C, hyst = +38.0°C)  ALARM  sensor = thermistor
CPU Temp:    +67.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
AUX Temp:    +54.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +66.0°C  (crit = +85.0°C)                  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +68.0°C  (crit = +85.0°C)     
``````
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Pentium(R) Dual  CPU  E2180  @ 2.00GHz
stepping	: 13
cpu MHz		: 3560.000
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 7125.21
clflush size	: 64

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Pentium(R) Dual  CPU  E2180  @ 2.00GHz
stepping	: 13
cpu MHz		: 3560.000
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 7120.44
clflush size	: 64

```:guitar:

---

### Post by abetterlie on 2008-04-13
great writeup, thanks a million. 
up and running and temperature sensoring in minutes.

---

### Post by SR_ELPIRATA on 2008-04-20
WOW, I was wondering why x-sensors wasnt working. Installed lm-sensors easily though steps 3 to 5 were done by the system automatically, which was pretty nice. I did all this because I wanted to get GKrellM working that specific area and it did, but after doing it noticed that I could add these sensors to my panels easily and it looks 'clean', so I dont know, I think Im going to stick with these instead of GKrellM (but Im not going to uninstall them neither).

ELP

---

### Post by slick_nick on 2008-04-30
Seems like it's gotten a lot easier to get sensors up and running since this thread was started; I don't think anyone has given a new how-to so I will. Thanks to the folks in this thread [ [http://ubuntuforums.org/showthread.php?t=671015](http://ubuntuforums.org/showthread.php?t=671015) ] I got it working quickly taking the following steps:

1. Open a terminal and do the ol' *sudo apt-get install* and install *lm-sensors* and *sensors-applet*.  
2. After the install, run *sudo sensors-detect* and say Yes to everything. 
3. Restart your computer. 
4. Right-click the bar at the top of the screen and select Add to Panel. Find Hardware Sensors Monitor and click Add.


You can also type "sensors" into the terminal and get a readout like this:
slick@maritimus:~$ sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:   +9.0°C                                    
Core0 Temp:   +0.0°C                                    
Core1 Temp:  +12.0°C                                    
Core1 Temp:  +10.0°C                                    

it8718-isa-0228
Adapter: ISA adapter
in0:         +1.31 V  (min =  +0.00 V, max =  +4.08 V)
in1:         +2.10 V  (min =  +0.00 V, max =  +4.08 V)
in2:         +3.31 V  (min =  +0.00 V, max =  +4.08 V)
in3:         +2.94 V  (min =  +0.00 V, max =  +4.08 V)
in4:         +3.02 V  (min =  +0.00 V, max =  +4.08 V)
in5:         +3.18 V  (min =  +0.00 V, max =  +4.08 V)
in6:         +4.08 V  (min =  +0.00 V, max =  +4.08 V)
in7:         +0.00 V  (min =  +0.00 V, max =  +4.08 V)
in8:         +3.07 V
fan1:       2710 RPM  (min =    0 RPM)
fan2:          0 RPM  (min =    0 RPM)
fan3:          0 RPM  (min =    0 RPM)
fan5:          0 RPM  (min =    0 RPM)
temp1:       +32.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = transistor
temp2:       +36.0°C  (low  = +127.0°C, high = +70.0°C)  sensor = thermal diode
**temp3:       +80.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = transistor**
cpu0_vid:   +1.550 V


A couple people asked this a while ago in this thread, and didn't get an answer as far as I saw, so I'll ask again: Anyone know what temp3 is?!?

---

### Post by wnelson on 2008-05-01
If you look in /etc/sensors.conf you will find all of the chip set definitions. Most temp3 are ignored. Just browse that file and find out.


k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp: +9.0°C
Core0 Temp: +0.0°C
Core1 Temp: +12.0°C
Core1 Temp: +10.0°C

it8718-isa-0228          --------> it8718 is the chip set for you computer
Adapter: ISA adapter
in0: +1.31 V (min = +0.00 V, max = +4.08 V)
in1: +2.10 V (min = +0.00 V, max = +4.08 V)
in2: +3.31 V (min = +0.00 V, max = +4.08 V)
in3: +2.94 V (min = +0.00 V, max = +4.08 V)
in4: +3.02 V (min = +0.00 V, max = +4.08 V)
in5: +3.18 V (min = +0.00 V, max = +4.08 V)
in6: +4.08 V (min = +0.00 V, max = +4.08 V)
in7: +0.00 V (min = +0.00 V, max = +4.08 V)
in8: +3.07 V
fan1: 2710 RPM (min = 0 RPM)
fan2: 0 RPM (min = 0 RPM)
fan3: 0 RPM (min = 0 RPM)
fan5: 0 RPM (min = 0 RPM)
temp1: +32.0°C (low = +127.0°C, high = +127.0°C) sensor = transistor
temp2: +36.0°C (low = +127.0°C, high = +70.0°C) sensor = thermal diode
temp3: +80.0°C (low = +127.0°C, high = +127.0°C) sensor = transistor
cpu0_vid: +1.550 V

Walt
Tacoma, WA

---

### Post by deh1963 on 2008-05-01
Has anyone tried installing the latest version of lm-sensors (3.0.1) from the lm-sensors.org website?  I checked in Package Manager and I have version 1:3.0.0-4ubuntu installed.

I ran through sensors-detect and had few signals detected.  Makes me wonder if I'm missing something.

---

### Post by slick_nick on 2008-05-02
deh1963, good job noticing that...my sensors seem to be working fine/detecting with the older ubuntu version , but I might go head and try the latest version tomorrow if I get the time :)

---

### Post by Nameless_one on 2008-05-14
Hello. I installed lm-sensors following this howto (actually the updated info from page 24). I am trying to read my graphics card's temperature. My sensors output is this:

```
 $ sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:
             +40°C
Core1 Temp:
             +40°C

w83627ehf-isa-0290
Adapter: ISA adapter
VCore:     +1.42 V  (min =  +0.00 V, max =  +1.74 V) 
in1:       +9.40 V  (min = +10.08 V, max =  +6.71 V) ALARM
AVCC:      +3.36 V  (min =  +1.97 V, max =  +4.05 V) 
3VCC:      +3.39 V  (min =  +0.45 V, max =  +4.02 V) 
in4:       +1.71 V  (min =  +1.90 V, max =  +0.68 V) ALARM
in5:       +1.72 V  (min =  +1.78 V, max =  +0.57 V) ALARM
in6:       +5.68 V  (min =  +3.23 V, max =  +4.84 V) ALARM
VSB:       +3.36 V  (min =  +3.82 V, max =  +2.90 V) ALARM
VBAT:      +0.00 V  (min =  +3.98 V, max =  +3.50 V) ALARM
in9:       +1.54 V  (min =  +2.04 V, max =  +2.04 V) ALARM
Case Fan: 2250 RPM  (min = 2909 RPM, div = 8) ALARM
CPU Fan:  3013 RPM  (min =  975 RPM, div = 8)
Aux Fan:     0 RPM  (min = 1506 RPM, div = 128) ALARM
fan5:        0 RPM  (min =    0 RPM, div = 128)
Sys Temp:    +31°C  (high =   +47°C, hyst =    -1°C)  
CPU Temp:  +39.0°C  (high = +80.0°C, hyst = +75.0°C)  
AUX Temp:  +39.0°C  (high = +80.0°C, hyst = +75.0°C)  

```

Does anyone know whether any of these metrics corresponds to my GPU?

---

### Post by dtrapp on 2008-05-14
This is also a noob question
Can you tell me where the mkdev.sh file is - I installed lm-sensors but cannot find the file.

---

### Post by Nameless_one on 2008-05-17
If you are running gutsy or later, I believe you don't need to run the mkdev.sh script. Check [here](https://help.ubuntu.com/community/SensorInstallHowto).

If are running edgy or earlier, I think th idea is to create the mkdev.sh and run it yourself.

---

### Post by carpman on 2008-05-19
Does this guide still apply to Kubuntu Hardy?

If so where is this lm-sources it talks of running script in?

cheers

---

### Post by Nameless_one on 2008-05-19
There is no package lm-sources, if that's what you mean. The original poster means that you should run the mkdev.sh script from the source code of the package lm-sensors, but as of gutsy, that isn't necessary. 

Also, if you need to run the script, create it yourself (cut and paste the script from this guide).

---

### Post by DasCrushinator on 2008-05-19
So what is the way to do it for Gutsy/Hardy?

---

### Post by Nameless_one on 2008-05-20
[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

---

### Post by DasCrushinator on 2008-05-20
> **Nameless_one said:**
> [https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

That still shows using the mkdev.sh script?

---

### Post by Nameless_one on 2008-05-20
I am sorry, I should have probably quoted directly from the bottom of the page: 

> In Gutsy the process to configure lm-sensors is much simpler. I installed lm-sensors and sensors-applet, ran sudo sensors-detect (and said yes to everything). It asks if I want it to automatically add the modules to /etc/modules, I said yes. Then restart to get the modules (one could do some modprobing, but just restarting is easier) . Then I added the sensor applet to my panel. -- SamTygier

---

### Post by DasCrushinator on 2008-05-20
> **Nameless_one said:**
> I am sorry, I should have probably quoted directly from the bottom of the page:

Err, sorry about that.  I just saw all the instructions from this post and didn't realize I could get away with just doing that.

Thanks!

---

### Post by carpman on 2008-05-21
I have done this but sensors-detect finds no sensors, which is odd as hardinfo finds two temps plus hard drive temp?

---

### Post by DasCrushinator on 2008-05-21
> **carpman said:**
> I have done this but sensors-detect finds no sensors, which is odd as hardinfo finds two temps plus hard drive temp?

What release are you using?

---

### Post by carpman on 2008-05-22
I am using Kubuntu hardy KDE4 remix

---

### Post by markbuntu on 2008-05-22
Hi, I got lm-sensors and it is working fine and found all my sensors and can be seen in my syslog and when I run sensors in the terminal I just have this one small problem:

May 22 17:02:26 mark-desktop sensord: Sensor alarm: Chip dme1737-i2c-0-2e: V5stby: +0.00 V (min = +0.00 V, max = +6.64 V) [ALARM]

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +37.0°C                                    

dme1737-i2c-0-2e
Adapter: SMBus PIIX4 adapter at 0b00
V5stby:      +0.00 V  (min =  +0.00 V, max =  +6.64 V)   ALARM
Vccp:        +1.12 V  (min =  +0.00 V, max =  +2.99 V)   
V3.3:        +3.34 V  (min =  +0.00 V, max =  +4.38 V)   
V5:          +5.15 V  (min =  +0.00 V, max =  +6.64 V)   
V12:        +12.18 V  (min =  +0.00 V, max = +15.94 V)   
V3.3stby:    +3.34 V  (min =  +0.00 V, max =  +4.38 V)   
Vbat:        +3.25 V  (min =  +0.00 V, max =  +4.38 V)   
CPU_Fan:    1781 RPM  (min =    0 RPM)
Fan2:       1324 RPM  (min =    0 RPM)
Fan4:          0 RPM  (min =    0 RPM)
RD1 Temp:    +38.7°C  (low  = -127.0°C, high = +85.0°C)  
Int Temp:    +38.8°C  (low  = -127.0°C, high = +85.0°C)  
CPU Temp:    +47.2°C  (low  = -127.0°C, high = +85.0°C)  
cpu0_vid:   +1.550 V

Is there anyway to disable this V5stby sensor so I stop getting this message every minute?

Update: OK, I made a change in sensors3.conf according to the instructions and added

ignore in0


which is identified in sensors3.conf as V5stby like this

label in0 "V5stby"


 I added it after the chip "dme 1737-*" statement.

sensors3.conf has a very good information and instruction section at the top. 
I wish more .conf files were written like that.

I then ran sensors -s as suggested but sensord still reports an alarm on soft boot (ctrl-alt-Backspace) and the syslog reports this every minute.

The sensors applet no longer lists this sensor so the change seems to have worked for that but how can I change the sensord configuration since it appears that my motherboard does not seem to be using this particular sensor. It is an ASUS A8AE-LE motherboard (OEM) used in the HP Pavillion an1330 and others.

OK, fixed that. Hard reboot necessary. Duhhh... it is a hardware type thingy...

RTFM as they say...

I just hope this provides some help for someone.


I have tried this on both amd64 and 386i Hardy on this machine and can confirm that it works for both. No changes are necessary.

---

### Post by dbn79 on 2008-05-31
Hello,

I am new to Ubuntu and have been having issues with my Sony PCV-RX550.  When running xsensors my fan1 is running at ~4200 RPM - so it is a little loud.  I've been working through directions on this page and others and seem to be making some progress, but I can't get the fan to slow down (expect when running pwmconfig correlation).

I've been able to change some of my settings as follows (not sure how useful they are, but at least I've been able to change them):

Settings of hwmon0/device/pwm2:
  Depends on 
  Controls hwmon0/device/fan2_input
  MINTEMP=37
  MAXTEMP=41
  MINSTART=90
  MINSTOP=75
  MINPWM=75
  MAXPWM=80

Settings of hwmon0/device/pwm1:
  Depends on hwmon0/device/temp1_input
  Controls hwmon0/device/fan1_input
  MINTEMP=37
  MAXTEMP=41
  MINSTART=150
  MINSTOP=135
  MINPWM=135
  MAXPWM=140

When I run 'fancontrol start' I get the following message:
Enabling PWM on fans...
Starting automatic fan control...
/usr/sbin/fancontrol: line 265: ${tsens}: ambiguous redirect
Error reading temperature from /sys/class/hwmon/
Aborting, restoring fans...
Verify fans have returned to full speed

Not sure if this is useful, but when running sensors I get:
w83627hf-isa-0290
Adapter: ISA adapter
VCore 1:     +1.71 V  (min =  +1.65 V, max =  +2.05 V)
VCore 2:     +0.05 V  (min =  +1.65 V, max =  +2.05 V)
+3.3V:       +3.33 V  (min =  +2.82 V, max =  +3.79 V)
+5V:         +5.13 V  (min =  +2.61 V, max =  +3.09 V)
+12V:       +11.80 V  (min = +14.47 V, max = +11.61 V)
-12V:       -12.11 V  (min =  +1.95 V, max =  -1.83 V)
-5V:         +3.54 V  (min =  +5.10 V, max =  +0.93 V)
V5SB:        +5.56 V  (min =  +5.91 V, max =  +5.03 V)
VBat:        +1.55 V  (min =  +1.76 V, max =  +0.29 V)
fan1:       4218 RPM  (min = 3534 RPM, div = 2)
fan2:       2177 RPM  (min = 1584 RPM, div = 4)
fan3:          0 RPM  (min = 3082 RPM, div = 2)
temp1:       -48.0°C  (high = +123.0°C, hyst = -18.0°C)  sensor = thermistor
temp2:       +38.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
temp3:       +37.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
cpu0_vid:   +1.750 V
beep_enable:enabled

Any suggestions?  Thanks for any help...I'd like to actually run Ubuntu and move away from Windows a bit, but this fan speed is too much!

---

### Post by rshel on 2008-06-05
I really appreciate the ubuntu community for all of its kind efforts to  help people.  But it is really ridiculous that it takes such canoodling to get something as simple as temp sensors to work.  And the only reason I need them to work is because Ubunut 8 is running so hot--despite the pre-release hype about running cooler than ever--that I fear I will fry my computer.

But thanks, again.  Anybody recommend a good alternative to Ubuntu?

---

### Post by wilberfan on 2008-06-05
> **rshel said:**
> 

Anybody recommend a good alternative to Ubuntu?

Boy,  you're in for it now!  ;)

I'm pretty sure there are lot's of threads that discuss alternatives...but..since you asked...

I _**REALLY**_ like Sidux.  It's Debian based, takes less than 6 minutes to install (YMMV), and it's phenomenally easy to keep state-of-the-art (something I really enjoy) with it's "smxi" script.  (It's KDE by default, though..if that's an issue for you.)

I don't know if configuring lm-sensors will be any easier (it's been awhile since I did that), but their IRC room is *extremely* helpful.

I tried a dozen or so distros before I landed on Sidux, and I literally stopped distroshopping when I found it.

But that's the cool thing about *nix--there's' something perfect (or nearly so) for everyone!

:guitar:

---

### Post by jspiers on 2008-07-02
> **slick_nick said:**
> Seems like it's gotten a lot easier to get sensors up and running since this thread was started; I don't think anyone has given a new how-to so I will. Thanks to the folks in this thread [ [http://ubuntuforums.org/showthread.php?t=671015](http://ubuntuforums.org/showthread.php?t=671015) ] I got it working quickly taking the following steps:

1. Open a terminal and do the ol' *sudo apt-get install* and install *lm-sensors* and *sensors-applet*.  
2. After the install, run *sudo sensors-detect* and say Yes to everything. 
3. Restart your computer. 
4. Right-click the bar at the top of the screen and select Add to Panel. Find Hardware Sensors Monitor and click Add.


You can also type "sensors" into the terminal and get a readout like this:
slick@maritimus:~$ sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:   +9.0°C                                    
Core0 Temp:   +0.0°C                                    
Core1 Temp:  +12.0°C                                    
Core1 Temp:  +10.0°C                                    

it8718-isa-0228
Adapter: ISA adapter
in0:         +1.31 V  (min =  +0.00 V, max =  +4.08 V)
in1:         +2.10 V  (min =  +0.00 V, max =  +4.08 V)
in2:         +3.31 V  (min =  +0.00 V, max =  +4.08 V)
in3:         +2.94 V  (min =  +0.00 V, max =  +4.08 V)
in4:         +3.02 V  (min =  +0.00 V, max =  +4.08 V)
in5:         +3.18 V  (min =  +0.00 V, max =  +4.08 V)
in6:         +4.08 V  (min =  +0.00 V, max =  +4.08 V)
in7:         +0.00 V  (min =  +0.00 V, max =  +4.08 V)
in8:         +3.07 V
fan1:       2710 RPM  (min =    0 RPM)
fan2:          0 RPM  (min =    0 RPM)
fan3:          0 RPM  (min =    0 RPM)
fan5:          0 RPM  (min =    0 RPM)
temp1:       +32.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = transistor
temp2:       +36.0°C  (low  = +127.0°C, high = +70.0°C)  sensor = thermal diode
**temp3:       +80.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = transistor**
cpu0_vid:   +1.550 V


A couple people asked this a while ago in this thread, and didn't get an answer as far as I saw, so I'll ask again: Anyone know what temp3 is?!?


I asked Gigabyte about the temp readings from my it8718 on my Gigabyte GA-MA78GM-S2H (rev 1.0) and they said temp3 is the reading from the Northbridge.  But they gave no details as to how it is wired so as to get a useful calculation of the actual temperature.  I'm getting 87 degrees which seems rather crazy.  Does anyone have more details about the proper calculation for this sensor?

---

### Post by Nullack on 2008-07-03
On intrepid all I did was:

sudo apt-get install
sudo sensors-detect
Yes to everything
Reboot or load modules
sensors all work

This guide needs updating

---

### Post by MaPeD on 2008-07-03
Hmm... Heres my output and for some reason im getting negative readings on temp1 and sys temp.. and it cant be true unless my box has turned into a freezer
```

lm78-i2c-1-28
Adapter: SMBus nForce2 adapter at f000
VCore 1:     +2.85 V  (min =  +0.00 V, max =  +3.49 V)   
VCore 2:     +2.98 V  (min =  +0.26 V, max =  +0.51 V)   ALARM
+3.3V:       +3.25 V  (min =  +0.00 V, max =  +1.02 V)   ALARM
+5V:         +5.46 V  (min =  +0.03 V, max =  +0.32 V)   ALARM
+12V:       +10.52 V  (min =  +0.00 V, max =  +0.36 V)   ALARM
-12V:       -10.63 V  (min =  -0.78 V, max =  -2.23 V)   ALARM
-5V:         -5.44 V  (min =  -3.18 V, max =  -2.02 V)   ALARM
fan1:       5152 RPM  (min = 42187 RPM, div = 2)  ALARM
fan2:       2721 RPM  (min =   -1 RPM, div = 8)  ALARM
fan3:          0 RPM  (min = 5192 RPM, div = 2)  ALARM
temp1:       -65.0°C  (high =  +0.0°C, hyst = +127.0°C)  ALARM  
cpu0_vid:   +3.100 V

w83627dhg-isa-0290
Adapter: ISA adapter
VCore:       +1.42 V  (min =  +0.00 V, max =  +1.74 V)   
in1:         +9.82 V  (min =  +0.84 V, max =  +1.69 V)   ALARM
AVCC:        +3.25 V  (min =  +0.00 V, max =  +1.02 V)   ALARM
3VCC:        +3.25 V  (min =  +0.02 V, max =  +0.19 V)   ALARM
in4:         +1.38 V  (min =  +0.00 V, max =  +0.05 V)   ALARM
in5:         +1.53 V  (min =  +0.11 V, max =  +0.32 V)   ALARM
in6:         +5.79 V  (min =  +3.38 V, max =  +2.15 V)   ALARM
VSB:         +3.25 V  (min =  +2.90 V, max =  +0.06 V)   ALARM
VBAT:        +3.09 V  (min =  +2.11 V, max =  +2.66 V)   ALARM
Case Fan:   5113 RPM  (min = 42187 RPM, div = 2)  ALARM
CPU Fan:    2721 RPM  (min =    0 RPM, div = 8)  ALARM
Aux Fan:       0 RPM  (min = 5192 RPM, div = 4)  ALARM
fan4:          0 RPM  (min = 84375 RPM, div = 16)  ALARM
fan5:          0 RPM  (min = 7670 RPM, div = 2)  ALARM
Sys Temp:    -65.0°C  (high =  +0.0°C, hyst = +127.0°C)  sensor = diode
CPU Temp:    +33.5°C  (high = +127.0°C, hyst =  +0.0°C)  ALARM  sensor = diode
AUX Temp:    +34.0°C  (high = +127.0°C, hyst =  +0.0°C)  sensor = thermistor

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +16.0°C  (crit = +85.0°C)                  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +13.0°C  (crit = +85.0°C) 
```

---

### Post by jabertolin on 2008-07-03
Sorry for the question, I have been following all the steps of this HOWTO and just got, from *sensors-detect the following:

coretemp

I installed it into /etc/modules and with *sensors I only can see core 0 and 1 however nothing else, I am not able to get so much information as all of you showed here. Am I missing something else?

I installed sensors-applets and I can monitor core 0 and 1, hddtemp and acpi TZ01 and TZ00 (btw which is the difference between core 0 and acpi TZ00?)

I am looking for to monitor also nvidia GPU but unable to do it

Thanks

KJAB

---

### Post by adredz on 2008-07-09
when i try to edit /etc/modules i get this error:

adred@adred-desktop:~/Desktop$ sudo kate /etc/modules
Error: "/var/tmp/kdecache-adred" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-adred" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-adred" is owned by uid 1000 instead of uid 0.

same things happens when editing alises:

adred@adred-desktop:~/Desktop$ sudo kate /etc/modprobe.d/aliases
Error: "/var/tmp/kdecache-adred" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-adred" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-adred" is owned by uid 1000 instead of uid 0.

what should i do?:(

---

### Post by patoy on 2008-07-16
i'm struggling lm-sensors to work with nagios. whew..

---

### Post by Meserias on 2008-07-26
It's this **lm-sensors** stuff loaded from Synaptics work trough SNMP ??????!?! With scripts are working with no problem.
Please see this page down>>> [http://82.78.165.3:8081/]("http://82.78.165.3:8081/")

Promlem: using SNMPwalk I simply get no data 
```
root@NecServ:~# snmpwalk -v1 -c public localhost LM-SENSORS-MIB::lmTempSensorsTable
root@NecServ:~#
```
It's simply no answer to this list
I'm intending to use this with MRTG / RRDTool
Please help me...:confused:

---

### Post by Lakjin on 2008-07-29
```
lakjin@lakjin-laptop:~$ sudo sensors-detect
# sensors-detect revision 5016 (2007-11-11 22:20:16 +0100)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): y
Probing for PCI bus adapters...
Use driver `i2c-i801' for device 0000:00:1f.3: Intel 82801H ICH8

We will now try to load each adapter module in turn.
Load `i2c-i801' (say NO if built into your kernel)? (YES/no): y
Module loaded successfully.
If you have undetectable or unsupported adapters, you can have them
scanned by manually loading the modules before running this script.

To continue, we need module `i2c-dev' to be loaded.
Do you want to load `i2c-dev' now? (YES/no): y
Module loaded successfully.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Next adapter: SMBus I801 adapter at 1c00 (i2c-0)
Do you want to scan it? (YES/no/selectively): 
Client found at address 0x44
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Client found at address 0x4c
Probing for `National Semiconductor LM75'...                No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `Analog Devices ADT7466'...                     No
Probing for `Andigilog aSC7511'...                          No
Probing for `Dallas Semiconductor DS1621'...                No
Probing for `Analog Devices ADM1021'...                     No
Probing for `Analog Devices ADM1021A/ADM1023'...            No
Probing for `Maxim MAX1617'...                              No
Probing for `Maxim MAX1617A'...                             No
Probing for `Maxim MAX1668'...                              No
Probing for `Maxim MAX1805'...                              No
Probing for `Maxim MAX1989'...                              No
Probing for `Maxim MAX6655/MAX6656'...                      No
Probing for `TI THMC10'...                                  No
Probing for `National Semiconductor LM84'...                No
Probing for `Genesys Logic GL523SM'...                      No
Probing for `Onsemi MC1066'...                              No
Probing for `Maxim MAX1619'...                              No
Probing for `National Semiconductor LM82/LM83'...           No
Probing for `National Semiconductor LM90'...                No
Probing for `National Semiconductor LM89/LM99'...           No
Probing for `National Semiconductor LM86'...                No
Probing for `Analog Devices ADM1032'...                     No
Probing for `Maxim MAX6657/MAX6658/MAX6659'...              No
Probing for `Maxim MAX6648/MAX6692'...                      No
Probing for `Maxim MAX6680/MAX6681'...                      No
Probing for `Winbond W83L771W/G'...                         No
Probing for `Texas Instruments TMP401'...                   No
Probing for `National Semiconductor LM63'...                No
Probing for `Fintek F75363SG'...                            No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Probing for `Analog Devices ADT7461'...                     No
Probing for `Fintek F75383S/M'...                           No
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No
Client found at address 0x52
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!
Do you want to scan the ISA I/O ports? (YES/no): y
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM78-J' at 0x290...     No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No
Probing for `Silicon Integrated Systems SIS5595'...         No
Probing for `VIA VT82C686 Integrated Sensors'...            No
Probing for `VIA VT8231 Integrated Sensors'...              No
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some Super I/O chips may also contain sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): y
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No

Some CPUs or memory controllers may also contain embedded sensors.
Do you want to scan for them? (YES/no): y
AMD K8 thermal sensors...                                   No
AMD K10 thermal sensors...                                  No
Intel Core family thermal sensor...                         No
Intel AMB FB-DIMM thermal sensor...                         No

Sorry, no sensors were detected.
Either your sensors are not supported, or they are connected to an
I2C or SMBus adapter that is not supported. See doc/FAQ,
doc/lm_sensors-FAQ.html or http://www.lm-sensors.org/wiki/FAQ
(FAQ #4.24.3) for further information.
If you find out what chips are on your board, check
http://www.lm-sensors.org/wiki/Devices for driver status.

```

=( i followed those direction. why is it not working?

---

### Post by dvelev on 2008-07-29
Hello,
i have some problems with lm-sensors - when try to probe module i2c-sensors:
```
modprobe i2c-sensor
FATAL: Module i2c_sensor not found.

```
Here is my sensors-detect:
```
 sudo sensors-detect
# sensors-detect revision 5016 (2007-11-11 22:20:16 +0100)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no):
Probing for PCI bus adapters...
Use driver `i2c-i810' for device 0000:00:02.0: Intel 82815 GMCH

We will now try to load each adapter module in turn.
Module `i2c-i810' already loaded.
If you have undetectable or unsupported adapters, you can have them
scanned by manually loading the modules before running this script.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Next adapter: I810/I815 I2C Adapter (i2c-0)
Do you want to scan it? (YES/no/selectively):

Next adapter: I810/I815 DDC Adapter (i2c-1)
Do you want to scan it? (YES/no/selectively):

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!
Do you want to scan the ISA I/O ports? (YES/no):
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM78-J' at 0x290...     No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No
Probing for `Silicon Integrated Systems SIS5595'...         No
Probing for `VIA VT82C686 Integrated Sensors'...            No
Probing for `VIA VT8231 Integrated Sensors'...              No
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some Super I/O chips may also contain sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no):
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     Yes
Found `SMSC LPC47B357/M967 Super IO'
    (no hardware monitoring capabilities)
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No

Some CPUs or memory controllers may also contain embedded sensors.
Do you want to scan for them? (YES/no):
AMD K8 thermal sensors...                                   No
AMD K10 thermal sensors...                                  No
Intel Core family thermal sensor...                         No
Intel AMB FB-DIMM thermal sensor...                         No

Sorry, no sensors were detected.
Either your sensors are not supported, or they are connected to an
I2C or SMBus adapter that is not supported. See doc/FAQ,
doc/lm_sensors-FAQ.html or http://www.lm-sensors.org/wiki/FAQ
(FAQ #4.24.3) for further information.
If you find out what chips are on your board, check
http://www.lm-sensors.org/wiki/Devices for driver status.
```
And here is the lsmod output:
```
lsmod
Module                  Size  Used by
i2c_dev                 8836  0
iptable_filter          3840  0
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ide_generic             2176  0 [permanent]
ide_disk               17536  0
ide_cd                 32416  0
ide_core              114252  3 ide_generic,ide_disk,ide_cd
i810                   19968  0
drm                    82580  1 i810
eeprom                  8208  0
i2c_i801               10640  0
lp                     12324  0
loop                   19076  0
ipv6                  272804  28
serio_raw               7940  0
button                  9232  0
snd_intel8x0           35356  0
snd_ac97_codec        100772  1 snd_intel8x0
ac97_bus                3072  1 snd_ac97_codec
snd_pcm                78596  2 snd_intel8x0,snd_ac97_codec
snd_timer              24836  1 snd_pcm
snd                    56868  4 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_timer
soundcore               8800  1 snd
i2c_i810                5636  0
evdev                  12928  0
iTCO_wdt               13092  0
iTCO_vendor_support     4868  1 iTCO_wdt
snd_page_alloc         11528  2 snd_intel8x0,snd_pcm
i2c_algo_bit            7300  1 i2c_i810
i2c_core               24832  5 i2c_dev,eeprom,i2c_i801,i2c_i810,i2c_algo_bit
intel_agp              25620  1
shpchp                 34452  0
pci_hotplug            30880  1 shpchp
parport_pc             36644  1
parport                37704  2 lp,parport_pc
agpgart                34760  2 drm,intel_agp
pcspkr                  4224  0
psmouse                40208  0
ext3                  136584  1
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36496  0
sr_mod                 17828  0
cdrom                  37280  2 ide_cd,sr_mod
sd_mod                 30720  3
ata_generic             8324  0
floppy                 59332  0
uhci_hcd               27152  0
e100                   37516  0
usbcore               146028  2 uhci_hcd
ata_piix               19588  2
pata_acpi               8320  0
mii                     6400  1 e100
libata                159344  3 ata_generic,ata_piix,pata_acpi
scsi_mod              151180  4 sg,sr_mod,sd_mod,libata
thermal                16796  0
processor              37000  1 thermal
fan                     5636  0
fbcon                  42656  0
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  1

```
I use ubuntu 8.04.1 server with Compaq Deskpro EN SFF PIII-1000MHz
Any suggestion for this problem?

---

### Post by detroit/zero on 2008-08-08
I followed the tutorial step-by-step, and ran into problems. Most obvious is that when I try to run sudo update-modules, I get a notice saying that the "command is deprecated and should not be used". Here's my terminal history for each step, picking up after creating and running the mkdev.sh script:
```
zero@zero-laptop:~$ sensors-detect
You need to be root to run this script.
zero@zero-laptop:~$ sudo !!
sudo sensors-detect
# sensors-detect revision 5016 (2007-11-11 22:20:16 +0100)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): yes
Probing for PCI bus adapters...
Use driver `i2c-i801' for device 0000:00:1f.3: Intel 82801G ICH7

We will now try to load each adapter module in turn.
Load `i2c-i801' (say NO if built into your kernel)? (YES/no): yes
Module loaded successfully.
If you have undetectable or unsupported adapters, you can have them
scanned by manually loading the modules before running this script.

To continue, we need module `i2c-dev' to be loaded.
Do you want to load `i2c-dev' now? (YES/no): yes
Module loaded successfully.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Next adapter: SMBus I801 adapter at 18c0 (i2c-0)
Do you want to scan it? (YES/no/selectively): yes
Client found at address 0x44
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Client found at address 0x50
Handled by driver `eeprom' (already loaded), chip type `eeprom'
    (note: this is probably NOT a sensor chip!)
Client found at address 0x52
Handled by driver `eeprom' (already loaded), chip type `eeprom'
    (note: this is probably NOT a sensor chip!)

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!
Do you want to scan the ISA I/O ports? (YES/no): yes
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM78-J' at 0x290...     No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No
Probing for `Silicon Integrated Systems SIS5595'...         No
Probing for `VIA VT82C686 Integrated Sensors'...            No
Probing for `VIA VT8231 Integrated Sensors'...              No
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some Super I/O chips may also contain sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): yes
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No

Some CPUs or memory controllers may also contain embedded sensors.
Do you want to scan for them? (YES/no): yes
AMD K8 thermal sensors...                                   No
AMD K10 thermal sensors...                                  No
Intel Core family thermal sensor...                         Success!
    (driver `coretemp')
Intel AMB FB-DIMM thermal sensor...                         No

Now follows a summary of the probes I have just done.
Just press ENTER to continue:    

Driver `coretemp' (should be inserted):
  Detects correctly:
  * Chip `Intel Core family thermal sensor' (confidence: 9)

I will now generate the commands needed to load the required modules.
Just press ENTER to continue: 

To load everything that is needed, add this to /etc/modules:

#----cut here----
# Chip drivers
coretemp
#----cut here----

Do you want to add these lines automatically? (yes/NO)yes
zero@zero-laptop:~$ sudo gedit /etc/modules
zero@zero-laptop:~$ /etc/init.d/module-init-tools
open: Permission denied
 * Loading kernel modules...                                                    open: Permission denied
 * Loading manual drivers...                                                    open: Permission denied
                                                                         [ OK ]
zero@zero-laptop:~$ sudo !!
sudo /etc/init.d/module-init-tools
 * Loading kernel modules...                                                     * Loading manual drivers...                                             [ OK ] 
zero@zero-laptop:~$ sudo gedit /etc/modprobe.d/local
zero@zero-laptop:~$ sudo update-modules

************************************************************************
*
* The update-modules command is deprecated and should not be used!
*
************************************************************************

zero@zero-laptop:~$ update-modules --help

************************************************************************
*
* The update-modules command is deprecated and should not be used!
*
************************************************************************

zero@zero-laptop:~$ sudo gedit /etc/modules
zero@zero-laptop:~$ sudo modprobe i2c-sensor
FATAL: Module i2c_sensor not found.
zero@zero-laptop:~$ sudo modprobe i2c-viapro
zero@zero-laptop:~$ sudo modprobe i2c-isa
FATAL: Module i2c_isa not found.
zero@zero-laptop:~$ sudo modprobe it87
FATAL: Error inserting it87 (/lib/modules/2.6.24-20-generic/kernel/drivers/hwmon/it87.ko): No such device
zero@zero-laptop:~$ sudo depmod -a
zero@zero-laptop:~$ sudo update-modules 

************************************************************************
*
* The update-modules command is deprecated and should not be used!
*
************************************************************************

```And, of course, my horrendously short sensors output. It doesn't even show my HDD temp, even though there is a sensor feeding output to my panel applet and an AWN temp applet. I'm just [trying to find a way to pipe these outputs into conky]("http://ubuntuforums.org/showpost.php?p=5548586&postcount=3218") so I can ditch the panel and AWN applets.
```
zero@zero-laptop:~$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +48.0°C  (crit = +100.0°C)                  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +47.0°C  (crit = +100.0°C) 
```Where did I go wrong?

---

### Post by emperor on 2008-08-13
lm-sensors apparently detected no sensors with the exception of the Intel coretemp. If your motherboard has sensor chips, they are apparently not supported by lm-sensors.
At least in the version of lm-sensors you have installed from Ubuntu's repo.

The hard drive temperature is read by "hddtemp" not lm-sensors so no detection here.

---

### Post by Ripose on 2008-08-15
When you installed **lm-sensors** using Synaptic did you also install the "recommended" packages?** i2c, read-edid & sensord**

I also installed **hardinfo** for a graphical interface, this will be installed as "_System Profiler & Benchmark_" under System-Preferences.

I then ran **sensor-detect**, answered **y** to everything, at the end it automatically wrote the changes to etc/modules: for me.

Reboot!

All info shows up in _System Profiler & Benchmark_ (click on sensors), although I still need to change a file somewhere so cpu temp is displayed instead of Temp 3, MB instead of Temp 2, etc.

I did not follow any of the originally posted complicated code.

---

### Post by rustamb on 2008-08-17
do we really need lm-sensors on ubuntu 8.04? Doesn't powernowd do the work?

---

### Post by amigaone_xe on 2008-08-17
Anyone know if Intel Core2Quad (Q9550 - 45nm yorkfiled) is supported by lm-sensors?
I can't get it to work and the "supported device"-list on lm-sensors homepage says it supports Core/Core2, but maybe the Core2Quad isn't included there?

Is there any way to get it to work?
I'm running ubuntu 8.04.1 and lm-sensors 3.0.0

---

### Post by Ripose on 2008-08-18
> **rustamb said:**
> do we really need lm-sensors on ubuntu 8.04? Doesn't powernowd do the work?
_powernowd_ is used for things such as CPU speed (frequency). For example my PC runs at 1000 MHz, but if something needs a faster speed than it will go 1800 MHz or 2400 MHz. The way the speed is incremented is set with _powernowd_ (voltages too).

_lm-sensors_ displays current temperatures, voltages, etc.

---

### Post by Ripose on 2008-08-18
It does not appear that _lm-sensors_ supports the Intel Quad. At least it is not the website list: [http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices)

**Note:** The ALPHA version of _lm-sensors_ **Install Wizard** is now available at above website.

---

### Post by deepclutch on 2008-08-20
coretemp module shows wrong temperatures with my 2.4Ghz C2D .:( yes ,this is a 2.6.26 kernel.reason:
[http://lkml.org/lkml/2008/4/18/190](http://lkml.org/lkml/2008/4/18/190)
so ,it shows 56 degrees idle temp for cores.original temperature -you have to subtract 16 from the reading.that is , 56-16= 40 .

still no fix kya?:confused:

---

### Post by ram zu on 2008-09-03
System Ubuntu 8.04
I've installed lm-sensors
"sudo sensors-detect" with yes in all questions

Result of sensors:

> pedro@Home-Server:~$ sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +29.0°C                                    

w83697hf-isa-0290
Adapter: ISA adapter
VCore:       +1.10 V  (min =  +0.40 V, max =  +0.03 V)
+3.3V:       +3.30 V  (min =  +0.26 V, max =  +0.00 V)
+5V:         +5.03 V  (min =  +6.02 V, max =  +4.41 V)
+12V:       +11.31 V  (min =  +5.84 V, max =  +0.06 V)
-12V:        +0.72 V  (min = -10.30 V, max =  -9.56 V)
-5V:         +5.10 V  (min =  -7.46 V, max =  -4.49 V)
V5SB:        +5.51 V  (min =  +5.19 V, max =  +0.00 V)
VBat:        +0.00 V  (min =  +0.29 V, max =  +0.00 V)
fan1:       1454 RPM  (min = 3375 RPM, div = 8)
fan2:          0 RPM  (min = 33750 RPM, div = 4)
temp1:       +37.0°C  (high =  +0.0°C, hyst = +100.0°C)  sensor = thermistor
temp2:       +33.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
beep_enable:enabled


I think that is everything correct but I dont know how to make use of this information.
I've installed "X-Sensors" but nothing happens when executed.
Tryng to use this in conky but dont know what parameter to use (conky is working fine).

Any help will be very apreciated.
Thanks to all.

---

### Post by Tanker Bob on 2008-09-03
> I think that is everything correct but I know I cant make use of this information.
I'v installed "X-Sensors" but nothing happens when executed.
Tryng to use this in conky but dont know what parameter to use (conky is working fine).

I'm not sure what your issue is. Everything looks like it's working fine. What do you want to do?

---

### Post by ram zu on 2008-09-03
The problem was with x-sensors not working. I execute but no information displayed.
I've install the applet and is working now on the panel.
Only have two questions now. How can I know what temperature is temp1, temp2 and core0. The other question is how can I add this information to conky?

---

### Post by Tanker Bob on 2008-09-03
Got it. I use ksensors with KDE, so am not familiar with those programs. Did you install libsensors3 and libsensors4, plus whatever other support that x-sensors lists? That's the only thing that comes to mind.

---

### Post by jjgomera on 2008-09-03
> **ram zu said:**
> The problem was with x-sensors not working. I execute but no information displayed.
I've install the applet and is working now on the panel.
Only have two questions now. How can I know what temperature is temp1, temp2 and core0. The other question is how can I add this information to conky?
look up in directory /sys/bus where are your sensors and write it here

to configure in conky it depends from that

---

### Post by ram zu on 2008-09-03
What was supposed to find in the dir /sys/bus?
There are a lot of dirs there but can't find anything related to lm-sensors.

---

### Post by jjgomera on 2008-09-04
For example, for me this is the output of **sensors** command:

```
jjgomera@ordenata:~$ sensors
it8718-isa-0290
Adapter: ISA adapter
in0:         +1.20 V  (min =  +0.00 V, max =  +4.08 V)
in1:         +1.84 V  (min =  +0.00 V, max =  +4.08 V)
in2:         +3.23 V  (min =  +0.00 V, max =  +4.08 V)
in3:         +3.01 V  (min =  +0.00 V, max =  +4.08 V)
in4:         +2.96 V  (min =  +0.00 V, max =  +4.08 V)
in5:         +0.67 V  (min =  +0.00 V, max =  +4.08 V)
in6:         +0.70 V  (min =  +0.00 V, max =  +4.08 V)
in7:         +2.90 V  (min =  +0.00 V, max =  +4.08 V)
in8:         +3.07 V
fan1:       2777 RPM  (min =    0 RPM)
fan2:          0 RPM  (min =    0 RPM)
temp1:       +40.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = thermal diode
temp2:       +39.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = transistor
temp3:       +25.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = transistor
cpu0_vid:   +0.913 V


```

and if i look same directory not empty for in /sys/bus, i found only useful sensors in /sys/bus/platform/drivers/it87/it87.656

And really is there where sensors are:

```
jjgomera@ordenata:~$ ls /sys/bus/platform/drivers/it87/it87.656
alarms      in0_max    in3_max    in6_max    subsystem    temp3_input
cpu0_vid    in0_min    in3_min    in6_min    temp1_input  temp3_max
driver      in1_input  in4_input  in7_input  temp1_max    temp3_min
fan1_input  in1_max    in4_max    in7_max    temp1_min    temp3_type
fan1_min    in1_min    in4_min    in7_min    temp1_type   uevent
fan2_input  in2_input  in5_input  in8_input  temp2_input  vrm
fan2_min    in2_max    in5_max    modalias   temp2_max
hwmon       in2_min    in5_min    name       temp2_min
in0_input   in3_input  in6_input  power      temp2_type
jjgomera@ordenata:~$ 

```

For example, for fan:

[IMG]http://img364.imageshack.us/img364/5311/pantallazo2cc7.png[/IMG]

I'm lucky and conky support platform devices, so i can use conky platform variable, for fan i use:
${platform it87.656 fan 1}

Conky support other devices like i2c, hwmon, really i dont know if your sensors is supported by conky itself.

But no problem if conky dont support your sensors, in my system, if conky dont support platform, i could use:
```
${execi 5 cat /sys/bus/platform/drivers/it87/it87.656/fan1_input}
```
and work too, its heavier resources although

---

### Post by ram zu on 2008-09-04
Thanks a lot JJgomera.
I was melting my brain trying to discover how to put that sensor to work.

Now I just need to guess witch of the temp sensors is related to the CPU.

Once again... many Kudos to you.

Gracias neighbor

---

### Post by Despot Despondency on 2008-09-13
Hey, great how to. Everything seems to have installed correctly. A couple of questions though

1) When I got to the stage of doing the command

sudo depmod -a

I got a message saying it was depreciated. Do I need to run any other command?

2) When I type sensors I get the following output

```

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +34.0°C                                    
Core1 Temp:  +34.0°C                                    

dme1737-i2c-0-2e
Adapter: SMBus nForce2 adapter at 4c00
V5stby:      +0.00 V  (min =  +0.00 V, max =  +6.64 V)   ALARM
Vccp:        +1.12 V  (min =  +0.00 V, max =  +2.99 V)   
V3.3:        +3.35 V  (min =  +0.00 V, max =  +4.38 V)   
V5:          +5.08 V  (min =  +0.00 V, max =  +6.64 V)   
V12:        +12.07 V  (min =  +0.00 V, max = +15.94 V)   
V3.3stby:    +3.31 V  (min =  +0.00 V, max =  +4.38 V)   
Vbat:        +3.03 V  (min =  +0.00 V, max =  +4.38 V)   
CPU_Fan:    1365 RPM  (min =    0 RPM)
Fan2:          0 RPM  (min =    0 RPM)
Fan4:          0 RPM  (min =    0 RPM)
RD1 Temp:    +36.1°C  (low  = -127.0°C, high = +91.0°C)  
Int Temp:    +38.2°C  (low  = -127.0°C, high = +91.0°C)  
CPU Temp:    +32.2°C  (low  = -127.0°C, high = +91.0°C)  
cpu0_vid:   +1.550 V


```

How do I find out what things like V5stby actually correspond to? I've never used lm-sensors before so most of the readings are random to me.

3) In section 5) I tried

sudo modprobe i2c-sensor

but got FATAL:i2c_sensor not found. Do I need to worry about this? 

Cheers in advance

---

### Post by z00t on 2008-09-29
> **Hurky said:**
> Hi, I get this error trying to install lmsensors... What am I doing wrong?

```
sudo apt-get install lm-sensors
Reading Package Lists... Done
Building Dependency Tree... Done
Package lm-sensors is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package lm-sensors has no installation candidate
```

I get this as well.  Have a vanilla install of Ubuntu 8.04 LTS Desktop Edition on a Sony Vaio PCV-RX540.  Installed fresh an hour ago with only openssh-server installed since.

---

### Post by tnvkrishna on 2008-10-13
The output of 
command sudo sensors is just.

krishna@talupula:~$ sudo sensors
[sudo] password for krishna: 
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +46.0°C  (crit = +85.0°C)                  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +45.0°C  (crit = +85.0°C) 

I think something is wrong .....
Could you please help me.
I am using ubuntu 8.04 64bit
core 2 duo 1.83GHz.

---

### Post by b0k on 2008-11-08
> **Hurky said:**
> Hi, I get this error trying to install lmsensors... What am I doing wrong?

```
sudo apt-get install lm-sensors
Reading Package Lists... Done
Building Dependency Tree... Done
Package lm-sensors is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package lm-sensors has no installation candidate
```

The same thing happens to me when i try to install lm-sensors. :/

---

### Post by Tanker Bob on 2008-11-08
It's in the main repositories, so it should be available. If you cannot get it there, try downloading and installing it directly from the repository [here](http://packages.ubuntu.com/hardy/utils/lm-sensors). You may have to ensure that you've installed all the required support packages.

---

### Post by havok1977 on 2008-11-12
Hello everyone, i am having trouble setting up lm-sensors from 8.10 on my Sony Vaio VGN-S170F laptop...

The i2c modules are compiled and loaded into my running kernel; and the sensors-detect script does find my chipset:

```

Next adapter: SMBus I801 adapter at 1880 (i2c-0)

```

And yet not a single sensor is detected:

```

Do you want to scan it? (YES/no/selectively):   

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!   
Do you want to scan the ISA I/O ports? (YES/no):                        
Probing for `National Semiconductor LM78' at 0x290...       No          
Probing for `National Semiconductor LM78-J' at 0x290...     No          
Probing for `National Semiconductor LM79' at 0x290...       No          
Probing for `Winbond W83781D' at 0x290...                   No          
Probing for `Winbond W83782D' at 0x290...                   No          
Probing for `IPMI BMC KCS' at 0xca0...                      No          
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some Super I/O chips may also contain sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no):
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No

Some south bridges, CPUs or memory controllers may also contain
embedded sensors. Do you want to scan for them? (YES/no):
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD K10 thermal sensors...                                  No
Intel Core family thermal sensor...                         No
Intel AMB FB-DIMM thermal sensor...                         No

Sorry, no sensors were detected.

```

I seriously doubt that the laptop does not have any sensors... i have also tried with the SVN version of lm-sensors and got the same results.

Any ideas?

---

### Post by ubuser_7 on 2008-11-25
> **tnvkrishna said:**
> The output of 
command sudo sensors is just.

krishna@talupula:~$ sudo sensors
[sudo] password for krishna: 
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +46.0°C  (crit = +85.0°C)                  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +45.0°C  (crit = +85.0°C) 



I have the exact same problem. Did you find a solution? 

Sensors-detect only detects the coretemp module. I have a Intel(R) Core(TM)2 Duo CPU, E4600  @ 2.40GHz

I am running hardy.

```

Linux xml1 2.6.24-21-server #1 SMP Tue Oct 21 23:40:13 UTC 2008 x86_64 GNU/Linux

Description:	Ubuntu 8.04.1
Release:	8.04
Codename:	hardy

```

---

### Post by Outlit on 2008-11-25
Are you interested in making absolutely free money?

Nothing better then Bux.to!

Click here and join today -----V

[[IMG]http://i423.photobucket.com/albums/pp318/Outlit/banner.png[/IMG]]("http://bux.to/?r=Outlit")

---

### Post by Seba4.0 on 2008-11-26
Hi,

Im new to conky and I'm trying to have the temps from both cores (T7200) displayed.
Running *sensors* in the terminal gives me this output;

[I]seba@ARP-8944:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +43.0°C  (crit = +107.0°C)                  
temp2:       +49.0°C  (crit = +106.0°C)                  
temp3:       +44.0°C  (crit = +106.0°C)                  
temp4:       +40.0°C  (crit = +106.0°C)                  
temp5:       +41.0°C  (crit = +106.0°C)                  
temp6:       +40.0°C  (crit = +106.0°C)[/I] 

I've tried using the folowing lines in conky;

${color b0e2ff}${exec sensors | grep 'coretemp'}
${execi 60 sensors |grep temp | cut -c15-16}

This gives me the temperature (just the 2 digits) for all thermal zones.
Can someone explain how to display only *temp1* and *temp6*
I've tried using *cut --help* in the terminal but frankly I don't understand how to use the different parameters.
Thanks, Seba

Edit: Never mind, I've figured it out.
Cheers

---

### Post by GepettoBR on 2008-11-26
Thanks for the howto, it worked!

> **Seba4.0 said:**
> Hi,

Im new to conky and I'm trying to have the temps from both cores (T7200) displayed.
Running *sensors* in the terminal gives me this output;

[I]seba@ARP-8944:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +43.0°C  (crit = +107.0°C)                  
temp2:       +49.0°C  (crit = +106.0°C)                  
temp3:       +44.0°C  (crit = +106.0°C)                  
temp4:       +40.0°C  (crit = +106.0°C)                  
temp5:       +41.0°C  (crit = +106.0°C)                  
temp6:       +40.0°C  (crit = +106.0°C)[/I] 

I've tried using the folowing lines in conky;

${color b0e2ff}${exec sensors | grep 'coretemp'}
${execi 60 sensors |grep temp | cut -c15-16}

This gives me the temperature (just the 2 digits) for all thermal zones.
Can someone explain how to display only *temp1* and *temp6*
I've tried using *cut --help* in the terminal but frankly I don't understand how to use the different parameters.
Thanks, Seba

Edit: Never mind, I've figured it out.
Cheers

Try making two separate commands (one for temp1 and one for temp6). Instead of piping them both through "grep temp", use "grep temp1" on one and "grep temp6" on the other.

EDIT: It's worth mentioning that you can also pipe the command through grep more than once.

---

### Post by jdorenbush on 2008-12-01
I'm stuck at Steps 3 and 4. I got passed the part of getting the modules into my */etc/modules* file and that's about it.

```
# Generated by sensors-detect on Mon Dec  1 19:16:56 2008
# I2C adapter drivers
i2c-nforce2
# Chip drivers
# no driver for Analog Devices ADT7475 yet
it87
k8temp
```

And I don't even have this file, */etc/modprobe.d/local*

and Step 4 has lost me. Based off my sensors-detect above can someone help put Step 4 together for me please?

*Any word on GUI tool for fan control??* =]

---

### Post by Thameslink on 2008-12-22
I'm a bit stuck.
I'm trying to get lm-sensors working right on my vaio vgn-n38z
I need to control the fan speed

I run the script
it says

> /dev/i2c-0
/home/jake/Desktop/mkdev.sh: 25: +: not found
/dev/i2c-0
mknod: `/dev/i2c-0': File exists


which I don't understand, but I don't think it's right.

after going through the rest of the steps i run sensors and get

> jake@jake-vaio:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +52.0°C  (crit = +105.0°C)                  
temp2:       +52.0°C  (crit = +105.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +54.0°C  (high = +100.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +52.0°C  (high = +100.0°C, crit = +100.0°C)  

jake@jake-vaio:~$ sudo modprobe it87
FATAL: Error inserting it87 (/lib/modules/2.6.27-9-generic/kernel/drivers/hwmon/it87.ko): No such device


I think the it87 thing is the vpm module i need, but I'm quite far out of my depth. I only installed ubuntu 1 week ago.

Can anyone help me please?

---

### Post by quazar on 2009-01-30
I'm trying to display lm_sensors data on my 2x16 LCD running LCDd/lcdproc.

For the script I'm trying to run ([_lcdsensors.pl_]("http://www.esat.kuleuven.ac.be/~nvanhell/LCDsensors.html")), I need a location for the k8temp sensor.
I found the  it8718 chipset sensor under /sys/devices/platform/:
```
## variables regarding lm_sensors, update these conform to your system
my $chip='/sys/devices/platform/it87.552';  # directory where lm_sensors writes its data
```

But I cannot find the k8temp sensor in the directory /sys/devices/platform/

Is there a way to get the k8temp sensor files in that directory?

Edit: found the sensor under /sys/bus/pci/drivers/k8temp/0000:00:18.3

---

### Post by alzekak on 2009-02-03
Hey there, since I've been having issues installing lm-sensors properly for a while now on 8.10, (following any kinda guide i've found so far) I concluded on installing the sensors-applet for the gnome panel which works perfectly so far. 

It may not be the ideal solution since you don't really get all the indications you could get with lm-sensors yet still it's an alternative.

Hope to have helped,
Alexander.

---

### Post by newbie2 on 2009-02-24
> lm-sensors 3.0.3

This is a completely reworked package, for Linux 2.6.5+. It supports all the devices your kernel supports, as it no longer contains chip-specific code.
[http://www.lm-sensors.org/wiki/Download](http://www.lm-sensors.org/wiki/Download)

---

### Post by newbie2 on 2009-02-24
isn't it possible to 'integrate' lm-sensors into [Hardware-info]("http://www.watchingthenet.com/ubuntu-guide-for-windows-users-display-system-hardware-information.html")?...all info about my CPU sensors i get in this 'hardware-info' is this :

[[IMG]http://img6.imageshack.us/img6/4175/screenshot01j.th.png[/IMG]](http://img6.imageshack.us/my.php?image=screenshot01j.png)

:rolleyes::-(

---

### Post by narsaw on 2009-02-24
Anyone knows why my output from sensors haves these weird characters? They look like ( Â ).
 
Also, is my cpu temp +22 or +30. I see Core0 and Cpu Temp reported below.

```

% sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +40.0**Â**°C  (crit = +75.0Â°C)

k8temp-pci-00c3
Adapter: PCI adapter
**Core0 Temp:  +22.0[B]Â**°C
[/B]
it8712-isa-0290
Adapter: ISA adapter
VCore 1:     +1.12 V  (min =  +0.00 V, max =  +4.08 V)
VCore 2:     +0.00 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
+3.3V:       +3.28 V  (min =  +0.00 V, max =  +4.08 V)
+5V:         +4.81 V  (min =  +0.00 V, max =  +6.85 V)
+12V:       +12.42 V  (min =  +0.00 V, max = +16.32 V)
-12V:        -4.90 V  (min = -27.36 V, max =  +3.93 V)
-5V:        -13.64 V  (min = -13.64 V, max =  +4.03 V)   ALARM
Stdby:       +4.81 V  (min =  +0.00 V, max =  +6.85 V)
VBat:        +3.06 V
fan1:       1117 RPM  (min =  811 RPM, div = 8)
fan2:          0 RPM  (min =    0 RPM, div = 8)
fan3:          0 RPM  (min =    0 RPM, div = 8)
M/B Temp:    +23.0Â°C  (low  =  -1.0Â°C, high = +127.0Â°C)  sensor = transistor
**CPU Temp:    +30.0Â°C  (low  =  -1.0Â°C, high = +127.0Â°C)  sensor = transistor**
Temp3:       +25.0Â°C  (low  =  -1.0Â°C, high = +127.0Â°C)  sensor = transistor
cpu0_vid:   +0.875 V

```

---

### Post by deepclutch on 2009-02-24
huh.it has to do with locale support("locale" command will list your default locale.mine is en_US.utf8).you add this sensors-applet(install first) and to Gnome-Panel.it  works.

---

### Post by afeasfaerw23231233 on 2009-03-16
It cannot detect the voltage scanner. I am sure it must has voltage sensors because I can see the voltage of CPU in Windows. What to do?

---

### Post by Deathray on 2009-03-23
This is all I get, how come? My motherboard is an Asus P5Q Pro and I really like Ubuntu too much too uninstall it just because of the fan being so loud! :(

```
**deathray@deathray-desktop:~$ sudo sensors-detect **
# sensors-detect revision 5249 (2008-05-11 22:56:25 +0200)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): YES
Probing for PCI bus adapters...
Use driver `i2c-i801' for device 0000:00:1f.3: Intel ICH10

We will now try to load each adapter module in turn.
Module `i2c-i801' already loaded.
If you have undetectable or unsupported I2C/SMBus adapters, you can have
them scanned by manually loading the modules before running this script.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Next adapter: SMBus I801 adapter at 0400 (i2c-0)
Do you want to scan it? (YES/no/selectively): YES
Client found at address 0x4f
Probing for `National Semiconductor LM75'...                No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `Dallas Semiconductor DS1621/DS1631'...         No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No
Client found at address 0x52
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!
Do you want to scan the ISA I/O ports? (YES/no): YES
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM78-J' at 0x290...     No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some Super I/O chips may also contain sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): YES
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       Yes
Found unknown chip with ID 0xa513
    (logical device B has address 0x290, could be sensors)
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No

Some south bridges, CPUs or memory controllers may also contain
embedded sensors. Do you want to scan for them? (YES/no): YES
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD K10 thermal sensors...                                  No
Intel Core family thermal sensor...                         Success!
    (driver `coretemp')
Intel AMB FB-DIMM thermal sensor...                         No

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `coretemp' (should be inserted):
  Detects correctly:
  * Chip `Intel Core family thermal sensor' (confidence: 9)

I will now generate the commands needed to load the required modules.
Just press ENTER to continue: 

To load everything that is needed, add this to /etc/modules:

#----cut here----
# Chip drivers
coretemp
#----cut here----

Do you want to add these lines automatically? (yes/NO)YES
[B]deathray@deathray-desktop:~$ 
deathray@deathray-desktop:~$ sensors[/B]
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +33.0°C  (high = +82.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +33.0°C  (high = +82.0°C, crit = +100.0°C)  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +34.0°C  (high = +82.0°C, crit = +100.0°C)  

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +30.0°C  (high = +82.0°C, crit = +100.0°C)  

*deathray@deathray-desktop:~$ *

```

---

### Post by miegiel on 2009-04-11
Better late then never :)

All 4 of my k8temp-pci-00c3 outputs go up and down when I stress my GPU with the glxgears command, so I'm pretty sure it's my graphics card.

GPUs have cores too and that's probably what k8temp-pci-00c3 also senses in your case. I'm trying to figure out what exactly is being sensed here and if the the temps are accurate. It might be that they are (in my case) 4 GPU temp sensors, but it wouldn't surprise me if only 1 is and another senses my cards memory. And a 3rd might not be a temp sensor at all and actually be sensing the rpm of the cards fan.

> **narsaw said:**
> Anyone knows why my output from sensors haves these weird characters? They look like ( Â ).
 
Also, is my cpu temp +22 or +30. I see Core0 and Cpu Temp reported below.

```

% sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +40.0**Â**°C  (crit = +75.0Â°C)

k8temp-pci-00c3
Adapter: PCI adapter
**Core0 Temp:  +22.0[B]Â**°C
[/B]
it8712-isa-0290
Adapter: ISA adapter
VCore 1:     +1.12 V  (min =  +0.00 V, max =  +4.08 V)
VCore 2:     +0.00 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
+3.3V:       +3.28 V  (min =  +0.00 V, max =  +4.08 V)
+5V:         +4.81 V  (min =  +0.00 V, max =  +6.85 V)
+12V:       +12.42 V  (min =  +0.00 V, max = +16.32 V)
-12V:        -4.90 V  (min = -27.36 V, max =  +3.93 V)
-5V:        -13.64 V  (min = -13.64 V, max =  +4.03 V)   ALARM
Stdby:       +4.81 V  (min =  +0.00 V, max =  +6.85 V)
VBat:        +3.06 V
fan1:       1117 RPM  (min =  811 RPM, div = 8)
fan2:          0 RPM  (min =    0 RPM, div = 8)
fan3:          0 RPM  (min =    0 RPM, div = 8)
M/B Temp:    +23.0Â°C  (low  =  -1.0Â°C, high = +127.0Â°C)  sensor = transistor
**CPU Temp:    +30.0Â°C  (low  =  -1.0Â°C, high = +127.0Â°C)  sensor = transistor**
Temp3:       +25.0Â°C  (low  =  -1.0Â°C, high = +127.0Â°C)  sensor = transistor
cpu0_vid:   +0.875 V

```

My sensors output :
```
:~$ sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +34.0°C                                    
Core0 Temp:  +35.0°C                                    
Core1 Temp:  +28.0°C                                    
Core1 Temp:  +27.0°C                                    

it8716-isa-0228
Adapter: ISA adapter
VCore:       +1.18 V  (min =  +0.00 V, max =  +4.08 V)
VDDR:        +1.28 V  (min =  +0.00 V, max =  +4.08 V)
+3.3V:       +3.31 V  (min =  +0.00 V, max =  +4.08 V)
+5V:         +4.95 V  (min =  +0.00 V, max =  +5.99 V)
+12V:       +12.10 V  (min =  +0.00 V, max = +16.32 V)
in5:         +1.18 V  (min =  +0.00 V, max =  +4.08 V)
in6:         +2.30 V  (min =  +0.00 V, max =  +4.08 V)
5VSB:        +4.87 V  (min =  +0.00 V, max =  +6.85 V)
VBat:        +3.33 V
fan1:       1358 RPM  (min = 3245 RPM)
fan2:       1618 RPM  (min = 3245 RPM)
fan3:       1704 RPM  (min = 3245 RPM)
temp1:       +47.0°C  (low  = +127.0°C, high = +84.0°C)  sensor = thermal diode
temp2:       +47.0°C  (low  = +127.0°C, high = +84.0°C)  sensor = transistor
temp3:       +53.0°C  (low  = +127.0°C, high = +84.0°C)  sensor = transistor
cpu0_vid:   +1.550 V
```

---

### Post by alek66 on 2009-04-30
I hope I can get started this week, when Its done i´ll post my experiences and probably my issues! 

Cheers

---

### Post by vampire666eng on 2009-05-04
I have an Asus P5Q-E, I followed the instructions on the first post but it looks like the program couldn't find any sensors?

```
alain@VAMPIRE666:~$ sudo ./mkdev.sh
/dev/i2c-0
/dev/i2c-1
/dev/i2c-2
/dev/i2c-3
/dev/i2c-4
/dev/i2c-5
/dev/i2c-6
/dev/i2c-7
/dev/i2c-8
/dev/i2c-9
/dev/i2c-10
/dev/i2c-11
/dev/i2c-12
/dev/i2c-13
/dev/i2c-14
/dev/i2c-15
/dev/i2c-16
/dev/i2c-17
/dev/i2c-18
/dev/i2c-19
/dev/i2c-20
/dev/i2c-21
/dev/i2c-22
/dev/i2c-23
/dev/i2c-24
/dev/i2c-25
/dev/i2c-26
/dev/i2c-27
/dev/i2c-28
/dev/i2c-29
/dev/i2c-30
/dev/i2c-31
./mkdev.sh: line 32: b.: comando non trovato
./mkdev.sh: line 36: c.: comando non trovato
/dev/i2c-0
mknod: "/dev/i2c-0": Il file esiste
alain@VAMPIRE666:~$ sudo sensors-detect
# sensors-detect revision 5249 (2008-05-11 22:56:25 +0200)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): y
Probing for PCI bus adapters...
Use driver `i2c-i801' for device 0000:00:1f.3: Intel ICH10

We will now try to load each adapter module in turn.
Load `i2c-i801' (say NO if built into your kernel)? (YES/no): y
Module loaded successfully.
If you have undetectable or unsupported I2C/SMBus adapters, you can have
them scanned by manually loading the modules before running this script.

To continue, we need module `i2c-dev' to be loaded.
Do you want to load `i2c-dev' now? (YES/no): y
Module loaded successfully.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Next adapter: NVIDIA i2c adapter  (i2c-0)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x49
Probing for `National Semiconductor LM75'...                No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `National Semiconductor LM77'...                No
Probing for `Dallas Semiconductor DS1621/DS1631'...         No
Probing for `National Semiconductor LM92'...                No
Probing for `National Semiconductor LM76'...                No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter: NVIDIA i2c adapter  (i2c-1)
Do you want to scan it? (YES/no/selectively): y

Next adapter: NVIDIA i2c adapter  (i2c-2)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x2e
Probing for `Myson MTP008'...                               No
Probing for `National Semiconductor LM78'...                No
Probing for `National Semiconductor LM78-J'...              No
Probing for `National Semiconductor LM79'...                No
Probing for `National Semiconductor LM80'...                No
Probing for `National Semiconductor LM85 or LM96000'...     No
Probing for `Analog Devices ADM1027, ADT7460 or ADT7463'... No
Probing for `SMSC EMC6D100, EMC6D101 or EMC6D102'...        No
Probing for `Analog Devices ADT7462'...                     No
Probing for `Analog Devices ADT7467 or ADT7468'...          No
Probing for `Analog Devices ADT7470'...                     No
Probing for `Analog Devices ADT7473'...                     Success!
    (confidence 5, driver `to-be-written')
Probing for `Analog Devices ADT7475'...                     No
Probing for `Analog Devices ADT7476'...                     No
Probing for `Andigilog aSC7611'...                          No
Probing for `Andigilog aSC7621'...                          No
Probing for `National Semiconductor LM87'...                No
Probing for `National Semiconductor LM93'...                No
Probing for `Winbond W83781D'...                            No
Probing for `Winbond W83782D'...                            No
Probing for `Winbond W83792D'...                            No
Probing for `Winbond W83793R/G'...                          No
Probing for `Winbond W83791SD'...                           No
Probing for `Winbond W83627HF'...                           No
Probing for `Winbond W83627EHF'...                          No
Probing for `Winbond W83627DHG'...                          No
Probing for `Asus AS99127F (rev.1)'...                      No
Probing for `Asus AS99127F (rev.2)'...                      No
Probing for `Asus ASB100 Bach'...                           No
Probing for `Winbond W83L786NR/NG/R/G'...                   No
Probing for `Winbond W83L785TS-S'...                        No
Probing for `Analog Devices ADM9240'...                     No
Probing for `Dallas Semiconductor DS1780'...                No
Probing for `National Semiconductor LM81'...                No
Probing for `Analog Devices ADM1026'...                     No
Probing for `Analog Devices ADM1025'...                     No
Probing for `Analog Devices ADM1029'...                     No
Probing for `Analog Devices ADM1030'...                     No
Probing for `Analog Devices ADM1031'...                     No
Probing for `Analog Devices ADM1022'...                     No
Probing for `Texas Instruments THMC50'...                   No
Probing for `Analog Devices ADM1028'...                     No
Probing for `ITE IT8712F'...                                No
Probing for `SMSC DME1737'...                               No
Probing for `SMSC SCH5027D-NW'...                           No
Probing for `Fintek F75373S/SG'...                          No
Probing for `Fintek F75375S/SP'...                          No
Probing for `Fintek F75387SG/RG'...                         No
Probing for `Analog Devices ADM1024'...                     No
Probing for `Winbond W83791D'...                            No

Next adapter: SMBus I801 adapter at 0400 (i2c-3)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No
Client found at address 0x52
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!
Do you want to scan the ISA I/O ports? (YES/no): y
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM78-J' at 0x290...     No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some Super I/O chips may also contain sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): y
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       Yes
Found unknown chip with ID 0xa513
    (logical device B has address 0x290, could be sensors)
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No

Some south bridges, CPUs or memory controllers may also contain
embedded sensors. Do you want to scan for them? (YES/no): y
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD K10 thermal sensors...                                  No
Intel Core family thermal sensor...                         Success!
    (driver `coretemp')
Intel AMB FB-DIMM thermal sensor...                         No

Now follows a summary of the probes I have just done.
Just press ENTER to continue:  

Driver `to-be-written' (should be inserted):
  Detects correctly:
  * Bus `NVIDIA i2c adapter '
    Busdriver `UNKNOWN', I2C address 0x2e
    Chip `Analog Devices ADT7473' (confidence: 5)

Driver `coretemp' (should be inserted):
  Detects correctly:
  * Chip `Intel Core family thermal sensor' (confidence: 9)

I will now generate the commands needed to load the required modules.
Just press ENTER to continue: 

To load everything that is needed, add this to /etc/modules:

#----cut here----
# I2C adapter drivers
# modprobe unknown adapter NVIDIA i2c adapter 
# modprobe unknown adapter NVIDIA i2c adapter 
# modprobe unknown adapter NVIDIA i2c adapter 
# Chip drivers
# no driver for Analog Devices ADT7473 yet
coretemp
#----cut here----

Do you want to add these lines automatically? (yes/NO)y 

```

Any help?

---

### Post by abjt on 2009-05-04
doesn't work with integrated intel. I have a DG45FC mobo and sensors cannot detect the temp or voltage

---

### Post by cb_rex on 2009-05-04
> **vampire666eng said:**
> I have an Asus P5Q-E, I followed the instructions on the first post but it looks like the program couldn't find any sensors?
...
Any help?



> **Deathray said:**
> This is all I get, how come? My motherboard is an Asus P5Q Pro and I really like Ubuntu too much too uninstall it just because of the fan being so loud! :(
...


I was getting a similar issue to you with my ASUS P5Q SE, with it only showing my core temperatures and nothing else.  I found [this thread]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=871001") that helped me out.

Essentially running "sudo modprobe w83627ehf force_id=0x8860" and then "sensors -s" and then "sensors" revealed all the sensor information that had been missing.

I also added the lines:

echo "$(modprobe w83627ehf force_id=0x8860)"
echo "$(sensors -s)"

into the "etc/rc.local" file to load the correct sensors information for my motherboard on boot up, so now my sensors applet displays everything  properly.  

I don't know how to control the fan speeds in ubuntu, I just use the quiet setting in the BIOS, which seems to take care of everything.

[EDIT 2nd November 2009]

I've just performed a clean install of Karmic 9.10 and encountered some slight issues as described [>HERE<]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=871001&page=2"). 

I found that initially the sensors didn't work, so I decided to update my motherboard to the latest BIOS on the ASUS website. After doing this I could see temperatures, but not fan speeds.  

To fix this I first tried the "acpi_enforce_resources=lax" into grub menu.lst file; as described in post 15 from the above link, however this didn't work.  After a bit of reading round [>HERE<]("http://bugs.launchpad.net/ubuntu/+source/linux/+bug/418246") (post 11 was when it all made sense, thanks Stefan), I realised it was due to me having Grub 2 as I had done a clean install not an upgrade from 9.04.   Essentially its the same fix but the file is in a different place...

/etc/default/grub

Here I inserted: GRUB_CMDLINE_LINUX="acpi_enforce_resources=lax"
Saved and closed then in the terminal ran: update-grub
Then rebooted.

After reboot I applied the modprobe fix exactly as I describe above for 9.04 and it seems to be working fine again.

---

### Post by Wookiee on 2009-05-09
edit: Nevermind, I've got it configured and set up. But it seems my sensors aren't supported by x sensor.

---

### Post by iamboredr on 2009-05-09
nice info men wow great to use thanks

---

### Post by Shekibobo on 2009-05-10
The only thing my sensors detected was the intel-chipset cpus:

```
josh@ubuntu:~$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +52.0°C  (high = +85.0°C, crit = +85.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +54.0°C  (high = +85.0°C, crit = +85.0°C)  

```

And it automatically added the lines of code required:

```
Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `coretemp' (should be inserted):
  Detects correctly:
  * Chip `Intel Core family thermal sensor' (confidence: 9)

I will now generate the commands needed to load the required modules.
Just press ENTER to continue: 

To load everything that is needed, add this to /etc/modules:

#----cut here----
# Chip drivers
coretemp
#----cut here----

Do you want to add these lines automatically? (yes/NO)
```

I apparently didn't need to do anything else because the sensors command seems to work just fine.  I just don't get much info.  Might be because I'm on a laptop, though.

---

### Post by sharkcohen on 2009-05-14
Is anyone using lm-sensors with the Intel Core i7 965 Extreme?  I'm seeing temps of about 65C at idle with lm-sensors.  Is this accurate, can I trust what lm-sensors and coretemp are reporting?

---

### Post by cyberkost on 2009-05-14
I'm not using i7 965, but I read that:
1) many temp sensors return not the temp, but delta to critical temp.  So, the reading is a function of how correctly the critical temp is set in the BIOS
2) lm-sensors do a bit of math that is sensor specific.  The formulas may be wrong, chances of that are higher for newer/rarer hardware.
Can you check temp in a Windows environment?

---

### Post by o0Chris0o on 2009-05-14
ok I installed lm-sensors and everything. I don't think its listing right. Please have a look.

```
chris@TuX:~$ sensors
it8712-isa-0290
Adapter: ISA adapter
VCore 1:     +1.14 V  (min =  +0.00 V, max =  +4.08 V)   
VCore 2:     +4.08 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
+3.3V:       +3.28 V  (min =  +0.00 V, max =  +4.08 V)   
+5V:         +6.85 V  (min =  +0.00 V, max =  +6.85 V)   ALARM
+12V:       +12.80 V  (min =  +0.00 V, max = +16.32 V)   
-12V:       -14.97 V  (min = -27.36 V, max =  +3.93 V)   
-5V:         +4.03 V  (min = -13.64 V, max =  +4.03 V)   ALARM
Stdby:       +6.85 V  (min =  +0.00 V, max =  +6.85 V)   ALARM
VBat:        +3.17 V
fan1:       2509 RPM  (min =    0 RPM)
fan2:          0 RPM  (min =    0 RPM)
fan3:          0 RPM  (min =    0 RPM)
M/B Temp:    +45.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = thermistor
CPU Temp:    +31.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = thermistor
Temp3:      -128.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = disabled
cpu0_vid:   +0.763 V

```

any ideas? I am trying to get the temperatures/fan speed for my Motherboard, Processor and 4 cores for conky. My computer information is in my sig.

---

### Post by miegiel on 2009-05-15
@**o0Chris0o**, the calculations of the sensor output are probably wrong. If you're worried that there might be something wrong with the PSU go to the BIOS and check the voltages there. In any case at 4V your CPU would have already died.

---

### Post by Greyhound- on 2009-05-28
I have an Intel Core i7 on a Gigabyte GA-EX58-UD5 motherboard and am running Ubuntu 9.04. I've been trying like crazy to get lm-sensors to work but seem to be failing miserably. Could someone please tell me what I'm doing wrong? I first installed lm-sensors through the repository, ran sensors-detect.. had not luck, then I installed it from source, same thing happened again. Here's the output I get from running sensors-detect:

```
# sensors-detect revision 5666 (2009-02-26 17:15:04 +0100)
# System: Gigabyte Technology Co., Ltd. EX58-UD5

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): 
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD K10 thermal sensors...                                  No
Intel Core family thermal sensor...                         Success!
    (driver `coretemp')
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal and voltage sensors...                       No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): 
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      Yes
Found `ITE IT8720F Super IO Sensors'                        Success!
    (address 0x290, driver `it87')
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No

Some systems (mainly servers) implement IPMI, a set of common interfaces
through which system health data may be retrieved, amongst other things.
We have to read from arbitrary I/O ports to probe for such interfaces.
This is normally safe. Do you want to scan for IPMI interfaces?
(YES/no): 
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (yes/NO): yes
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): 
Using driver `i2c-i801' for device 0000:00:1f.3: Intel ICH10
Module i2c-i801 loaded successfully.
Module i2c-dev loaded successfully.

Next adapter: NVIDIA i2c adapter  (i2c-0)
Do you want to scan it? (YES/no/selectively): 

Next adapter: NVIDIA i2c adapter  (i2c-1)
Do you want to scan it? (YES/no/selectively): 
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter: NVIDIA i2c adapter  (i2c-2)
Do you want to scan it? (YES/no/selectively): 

Next adapter: NVIDIA i2c adapter  (i2c-3)
Do you want to scan it? (YES/no/selectively): 
Client found at address 0x2e
Probing for `Myson MTP008'...                               No
Probing for `National Semiconductor LM78'...                No
Probing for `National Semiconductor LM79'...                No
Probing for `National Semiconductor LM80'...                No
Probing for `National Semiconductor LM85'...                No
Probing for `National Semiconductor LM96000 or PC8374L'...  No
Probing for `Analog Devices ADM1027'...                     No
Probing for `Analog Devices ADT7460 or ADT7463'...          No
Probing for `SMSC EMC6D100 or EMC6D101'...                  No
Probing for `SMSC EMC6D102'...                              No
Probing for `SMSC EMC6D103'...                              No
Probing for `Winbond WPCD377I'...                           No
Probing for `Analog Devices ADT7467 or ADT7468'...          No
Probing for `Analog Devices ADT7470'...                     No
Probing for `Analog Devices ADT7473'...                     Success!
    (confidence 5, driver `adt7473')
Probing for `Analog Devices ADT7475'...                     No
Probing for `Analog Devices ADT7476'...                     No
Probing for `Andigilog aSC7611'...                          No
Probing for `Andigilog aSC7621'...                          No
Probing for `National Semiconductor LM87'...                No
Probing for `Analog Devices ADM1024'...                     No
Probing for `National Semiconductor LM93'...                No
Probing for `Winbond W83781D'...                            No
Probing for `Winbond W83782D'...                            No
Probing for `Winbond W83791D'...                            No
Probing for `Winbond W83792D'...                            No
Probing for `Winbond W83793R/G'...                          No
Probing for `Winbond W83627HF'...                           No
Probing for `Winbond W83627EHF'...                          No
Probing for `Winbond W83627DHG'...                          No
Probing for `Asus AS99127F (rev.1)'...                      No
Probing for `Asus AS99127F (rev.2)'...                      No
Probing for `Asus ASB100 Bach'...                           No
Probing for `Winbond W83L786NR/NG/R/G'...                   No
Probing for `Winbond W83L785TS-S'...                        No
Probing for `Analog Devices ADM9240'...                     No
Probing for `Dallas Semiconductor DS1780'...                No
Probing for `National Semiconductor LM81'...                No
Probing for `Analog Devices ADM1026'...                     No
Probing for `Analog Devices ADM1025'...                     No
Probing for `Analog Devices ADM1029'...                     No
Probing for `Analog Devices ADM1030'...                     No
Probing for `Analog Devices ADM1031'...                     No
Probing for `Analog Devices ADM1022'...                     No
Probing for `Texas Instruments THMC50'...                   No
Probing for `Analog Devices ADM1028'...                     No
Probing for `Texas Instruments THMC51'...                   No
Probing for `ITE IT8712F'...                                No
Probing for `SMSC DME1737'...                               No
Probing for `SMSC SCH5027D-NW'...                           No
Probing for `Fintek F75373S/SG'...                          No
Probing for `Fintek F75375S/SP'...                          No
Probing for `Fintek F75387SG/RG'...                         No
Probing for `Winbond W83791SD'...                           No

Next adapter: NVIDIA i2c adapter  (i2c-4)
Do you want to scan it? (YES/no/selectively): 

Next adapter: NVIDIA i2c adapter  (i2c-5)
Do you want to scan it? (YES/no/selectively): 
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                No
Client found at address 0x51
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Client found at address 0x52
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Client found at address 0x53
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No

Next adapter: SMBus I801 adapter at 0500 (i2c-6)
Do you want to scan it? (yes/NO/selectively): y
Client found at address 0x4e
Probing for `National Semiconductor LM75'...                No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `Dallas Semiconductor DS1621/DS1631'...         No
Probing for `Analog Devices ADM1021'...                     No
Probing for `Analog Devices ADM1021A/ADM1023'...            No
Probing for `Maxim MAX1617'...                              No
Probing for `Maxim MAX1617A'...                             No
Probing for `Maxim MAX1668'...                              No
Probing for `Maxim MAX1805'...                              No
Probing for `Maxim MAX1989'...                              No
Probing for `Maxim MAX6655/MAX6656'...                      No
Probing for `TI THMC10'...                                  No
Probing for `National Semiconductor LM84'...                No
Probing for `Genesys Logic GL523SM'...                      No
Probing for `Onsemi MC1066'...                              No
Probing for `Maxim MAX1618'...                              No
Probing for `Maxim MAX1619'...                              No
Probing for `National Semiconductor LM82/LM83'...           No
Probing for `Maxim MAX6654/MAX6690'...                      No
Probing for `Maxim MAX6659'...                              No
Probing for `Maxim MAX6647'...                              No
Probing for `Maxim MAX6680/MAX6681'...                      No
Probing for `Texas Instruments TMP411'...                   No
Probing for `National Semiconductor LM64'...                No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Probing for `Fintek F75121R/F75122R/RG (VID+GPIO)'...       No
Probing for `Fintek F75111R/RG/N (GPIO)'...                 No
Probing for `ITE IT8201R/IT8203R/IT8206R/IT8266R'...        Yes
    (confidence 6, not a hardware monitoring chip)
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No
Client found at address 0x52
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `it87':
  * ISA bus, address 0x290
    Chip `ITE IT8720F Super IO Sensors' (confidence: 9)

Driver `adt7473':
  * Bus `NVIDIA i2c adapter '
    Busdriver `nvidia', I2C address 0x2e
    Chip `Analog Devices ADT7473' (confidence: 5)

Driver `coretemp':
  * Chip `Intel Core family thermal sensor' (confidence: 9)

Do you want to overwrite /etc/sysconfig/lm_sensors? (YES/no): 
Copy prog/init/lm_sensors.init to /etc/init.d/lm_sensors
for initialization at boot time.
You should now start the lm_sensors service to load the required
kernel modules.

Unloading i2c-dev... OK
Unloading i2c-i801... OK
```

---

### Post by miegiel on 2009-05-28
> **Greyhound- said:**
> I have an Intel Core i7 on a Gigabyte GA-EX58-UD5 motherboard and am running Ubuntu 9.04. I've been trying like crazy to get lm-sensors to work but seem to be failing miserably. Could someone please tell me what I'm doing wrong? I first installed lm-sensors through the repository, ran sensors-detect.. had not luck, then I installed it from source, same thing happened again. Here's the output I get from running sensors-detect:

In hardy I'd say add```
# lm-sensors for Gigabyte GA-EX58-UD5
it87
coretemp
``` too the end of your */etc/modules* file. But your *sensors-detect* out put is different from mine :( so possibly stuff has changed ? Do you have a */etc/modules* file?

---

### Post by Greenwidth on 2009-06-01
Thanks for the HOW TO!
I seem to be getting conflicting results though from SMBus and ISA.. Not really important but how do I stop SMBus reporting? Remove it from etc/modules ?

```
acpitz-virtual-0
Adapter: Virtual device
temp1:       +40.0°C  (crit = +75.0°C)                  

w83791d-i2c-1-2d
Adapter: SMBus nForce2 adapter at 1c80
in0:         +1.26 V  (min =  +0.00 V, max =  +3.06 V)   
in1:         +1.54 V  (min =  +0.00 V, max =  +3.06 V)   
in2:         +1.26 V  (min =  +2.82 V, max =  +3.79 V)   ALARM
in3:         +3.06 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
in4:         +1.04 V  (min =  +0.26 V, max =  +0.00 V)   ALARM
in5:         +1.12 V  (min =  +1.02 V, max =  +0.00 V)   ALARM
in6:         +1.25 V  (min =  +0.03 V, max =  +0.00 V)   ALARM
in7:         +2.98 V  (min =  +0.51 V, max =  +1.02 V)   ALARM
in8:         +3.22 V  (min =  +1.02 V, max =  +2.11 V)   ALARM
in9:         +2.10 V  (min =  +1.02 V, max =  +0.51 V)   ALARM
fan1:          0 RPM  (min = 168750 RPM, div = 8)  ALARM
fan2:          0 RPM  (min =   -1 RPM, div = 8)  ALARM
fan3:          0 RPM  (min =   -1 RPM, div = 8)  ALARM
fan4:          0 RPM  (min =   -1 RPM, div = 8)  ALARM
fan5:          0 RPM  (min =   -1 RPM, div = 8)  ALARM
temp1:        -9.0°C  (high =  +0.0°C, hyst =  +4.0°C)  
temp2:        -7.5°C  (high = +80.0°C, hyst = +75.0°C)  
temp3:       -10.0°C  (high = +80.0°C, hyst = +75.0°C)  
cpu0_vid:   +1.419 V
beep_enable:enabled

it8718-isa-0290
Adapter: ISA adapter
in0:         +1.22 V  (min =  +0.00 V, max =  +4.08 V)   
in1:         +3.30 V  (min =  +0.00 V, max =  +4.08 V)   
in2:         +0.00 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
in3:         +2.99 V  (min =  +0.00 V, max =  +4.08 V)   
in4:         +2.94 V  (min =  +0.00 V, max =  +4.08 V)   
in5:         +0.00 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
in6:         +0.00 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
in7:         +2.93 V  (min =  +0.00 V, max =  +4.08 V)   
in8:         +2.99 V
fan1:       1155 RPM  (min = 3245 RPM)  ALARM
fan2:        868 RPM  (min = 3245 RPM)  ALARM
fan3:          0 RPM  (min =    0 RPM)
temp1:       +23.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = thermal diode
temp2:       +29.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = thermistor
temp3:       -55.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = thermistor
cpu0_vid:   +0.000 V

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +36.0°C  (high = +82.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +32.0°C  (high = +82.0°C, crit = +100.0°C)  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +36.0°C  (high = +82.0°C, crit = +100.0°C)  

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +31.0°C  (high = +82.0°C, crit = +100.0°C) 
```

---

### Post by miegiel on 2009-06-01
> **Greenwidth said:**
> Thanks for the HOW TO!
I seem to be getting conflicting results though from SMBus and ISA.. Not really important but how do I stop SMBus reporting? Remove it from etc/modules ?

In short yes, or put a # at the start of the line.

Running *sensors-detect* again and checking the "confidence" of the different sensors might be wise too.

---

### Post by Greenwidth on 2009-06-01
> **miegiel said:**
> 
Running *sensors-detect* again and checking the "confidence" of the different sensors might be wise too.

Good plan - SMBus scores a 5 and ISA gets 9 so i'll go with that :)

---

### Post by jetbelbes on 2009-06-22
Hi guys!

I'm quite new to lm-sensors. Anyway, I tried sudo sensors-detect but after answering YES to all questions, here's the terminal output.

```
Sorry, no sensors were detected.
Either your sensors are not supported, or they are connected to an
I2C or SMBus adapter that is not supported. See
http://www.lm-sensors.org/wiki/FAQ/Chapter3 for further information.
If you find out what chips are on your board, check
http://www.lm-sensors.org/wiki/Devices for driver status.
```

Please help me. I'm using ACER Travelmate 2420 and I badly need lm-sensors because this laptop heats up a lot and to a very high temp and, at times, even auto-shuts down because of the heat. Thanks!

-Jet

---

### Post by Tanker Bob on 2009-06-22
If sensors-detect didn't find any sensors, lmsensors probably doesn't support your motherboard. That's a lot more common on laptops that all have custom boards.

---

### Post by jetbelbes on 2009-06-22
Oh, If lmsensors does not support my motherboard, is there any other motherboard detection software/support that might be compatible with my board?:popcorn:

---

### Post by edemkrimea on 2009-06-23
The tutorial is great . However here is my sensors output . Could you point me what happened to M/B Temp and CPU Temp lines? Thanks in advance

---

### Post by miegiel on 2009-06-23
> **edemkrimea said:**
> The tutorial is great . However here is my sensors output . Could you point me what happened to M/B Temp and CPU Temp lines? Thanks in advance

Open /etc/sensors3.conf (disclaimer: I'm using hardy (8.04)) and search it for "it8712-" to find the stuff on your sensor. 

Quoting from the temperature section of the it8712 sensor:
> # Important - if your temperature readings are completely whacky
# you probably need to change the sensor type.
# Adujst and uncomment the appropriate lines below.

I'm guessing Temp3 is your CPU temperature, since it's a thermal diode.

---

### Post by Laysan_A on 2009-06-25
@jetbelbes

I'm sorry you can't find a solution for your laptop. 

I read your post and I wanted to offer you a warning (slightly off topic). I had (actually still do) an inspiron 8000 with a pIII that always ran hot (they were a very hot chip). I didn't have any monitoring software, didn't even know that I should have. Anyway, it started just dying unexpectedly, at first very rarely, but then more and more often until it finally wouldn't even stay on long enough to finish loading windows.

I didn't know what the problem was until I spent the money for a refirbished mb and a used processor to fix it with. When I opened the case I discovered that the heat sink was completely empty of coolant - it had all leaked out over time. 

If you have a windows partition I'd use it to find out what temp you're operating at, and check your processor's temp. limits (google it at the manufacturer's site). I don't think your laptop should ever overheat if everything's working properly (you're not blocking the vents are you?). Check your fans for good speed and smooth operation.

If your operating temp. and the processor's specs don't align, ie. you're operating outside the safe operating zone, you need to fix it or you'll likely lose it. You might look at ebay for inexpensive parts (buyer beware, though [my refirbished mb went bad]).

Good luck.

---

### Post by tonydunno on 2009-06-29
I'm having trouble with my pwmconfig.
 
```
Found the following PWM controls:
   hwmon2/device/pwm1
   hwmon2/device/pwm2
   hwmon2/device/pwm3
There are no usable PWM outputs.

```
 
Though my sensors cleary reads out the fans
 
```

nelis@nelis-desktop:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +41.0Â°C  (crit = +70.0Â°C)
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +36.0Â°C
Core1 Temp:  -49.0Â°C
f71862fg-isa-0220
Adapter: ISA adapter
in0:         +1.70 V
in1:         +2.04 V
in2:         +1.20 V
in3:         +2.04 V
in4:         +1.34 V
in5:         +1.18 V
in6:         +1.18 V
in7:         +1.68 V
in8:         +1.66 V
fan1:       2538 RPM
fan2:       2222 RPM
fan3:          0 RPM  ALARM
temp1:       +41.0Â°C  (high = +85.0Â°C, hyst = +81.0Â°C)
                      (crit = +70.0Â°C, hyst = +66.0Â°C)  sensor = transistor
temp2:       +89.0Â°C  (high = +85.0Â°C, hyst = +81.0Â°C)  ALARM
                      (crit = +100.0Â°C, hyst = +96.0Â°C)  sensor = transistor
temp3:       +44.0Â°C  (high = +254.0Â°C, hyst = +252.0Â°C)
                      (crit = +254.0Â°C, hyst = +252.0Â°C)  sensor = transistor
 

```
 
 
Anyone got an idea on how to deal with this ?
 
I did read through [http://ubuntuforums.org/showthread.php?t=42737](http://ubuntuforums.org/showthread.php?t=42737)

---

### Post by Laysan_A on 2009-06-29
I'd be interested if there's a fix for this too. Pwmconfig finds my case fan okay, but doesn't know my processor fan exists.

---

### Post by VastOne on 2009-07-25
I have a new MSI 790FX-GD70 motherboard and have run into this with sensors-detect:

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `to-be-written':
  * Chip `AMD K10 thermal sensors' (confidence: 9)
  * Bus `SMBus PIIX4 adapter at 0b00'
    Busdriver `i2c_piix4', I2C address 0x2e
    Chip `Fintek F75387SG/RG' (confidence: 7)

Note: there is no driver for AMD K10 thermal sensors yet.
Check [http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) for updates.

No modules to load, skipping modules configuration.


I have checked everywhere on the web for the AMD K10, the Fintek and i2c_piix4 help and have been stuck in the mud for over a month now.

Has anyone gotten any of these to work with lm_sensors? 

This is driving me nuts as one the unsolved mysteries affecting my sleep and even my work...:confused:

---

### Post by eddski on 2009-08-01
This is probably a dumb question, but how do set a minimum fan speed? I don't care about the noise (it's minimal), but I do want to cool down the CPU in my laptop.

---

### Post by miegiel on 2009-08-01
> **eddski said:**
> This is probably a dumb question, but how do set a minimum fan speed? I don't care about the noise (it's minimal), but I do want to cool down the CPU in my laptop.

No experience with that, but try: **[color=red]Search:[/color]   Keyword(s): fan, control  **

---

### Post by coller_girl on 2009-08-07
hi i need help with this my fan speeds al over the shop, so i tried installing lm-sensors and got this output... what to do next?


```
sara@sara-desktop:~$ gksudo sama
sara@sara-desktop:~$ sudo apt-get install lm-sensors
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libsensors4
Suggested packages:
  sensord read-edid i2c-tools
The following NEW packages will be installed
  libsensors4 lm-sensors
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 188kB of archives.
After this operation, 782kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 http://gb.archive.ubuntu.com jaunty/main libsensors4 1:3.0.2-2ubuntu4 [63.0kB]
Get: 2 http://gb.archive.ubuntu.com jaunty/main lm-sensors 1:3.0.2-2ubuntu4 [125kB]
Fetched 188kB in 1s (183kB/s)     
Selecting previously deselected package libsensors4.
(Reading database ... 134714 files and directories currently installed.)
Unpacking libsensors4 (from .../libsensors4_1%3a3.0.2-2ubuntu4_i386.deb) ...
Selecting previously deselected package lm-sensors.
Unpacking lm-sensors (from .../lm-sensors_1%3a3.0.2-2ubuntu4_i386.deb) ...
Processing triggers for man-db ...
Setting up libsensors4 (1:3.0.2-2ubuntu4) ...
.udevdb or .udev presence implies active udev.  Aborting MAKEDEV invocation.

Creating config file /etc/sensors3.conf with new version

Setting up lm-sensors (1:3.0.2-2ubuntu4) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
sara@sara-desktop:~$ sudo nano
sara@sara-desktop:~$ chmod 755 mkdev.sh
chmod: changing permissions of `mkdev.sh': Operation not permitted
sara@sara-desktop:~$ sudo chmod 755 mkdev.sh
sara@sara-desktop:~$ 
sara@sara-desktop:~$ sudo ./mkdev.sh
/dev/i2c-0
/dev/i2c-1
/dev/i2c-2
/dev/i2c-3
/dev/i2c-4
/dev/i2c-5
/dev/i2c-6
/dev/i2c-7
/dev/i2c-8
/dev/i2c-9
/dev/i2c-10
/dev/i2c-11
/dev/i2c-12
/dev/i2c-13
/dev/i2c-14
/dev/i2c-15
/dev/i2c-16
/dev/i2c-17
/dev/i2c-18
/dev/i2c-19
/dev/i2c-20
/dev/i2c-21
/dev/i2c-22
/dev/i2c-23
/dev/i2c-24
/dev/i2c-25
/dev/i2c-26
/dev/i2c-27
/dev/i2c-28
/dev/i2c-29
/dev/i2c-30
/dev/i2c-31
sara@sara-desktop:~$ sudo sensors-detect
# sensors-detect revision 5249 (2008-05-11 22:56:25 +0200)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): yes
Probing for PCI bus adapters...
Use driver `i2c-i801' for device 0000:00:1f.3: Intel 82801G ICH7

We will now try to load each adapter module in turn.
Load `i2c-i801' (say NO if built into your kernel)? (YES/no): yes
Module loaded successfully.
If you have undetectable or unsupported I2C/SMBus adapters, you can have
them scanned by manually loading the modules before running this script.

To continue, we need module `i2c-dev' to be loaded.
Do you want to load `i2c-dev' now? (YES/no): yes
Module loaded successfully.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Next adapter: SMBus I801 adapter at 0500 (i2c-0)
Do you want to scan it? (YES/no/selectively): yes
Client found at address 0x4e
Probing for `National Semiconductor LM75'...                No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `Dallas Semiconductor DS1621/DS1631'...         No
Probing for `Analog Devices ADM1021'...                     No
Probing for `Analog Devices ADM1021A/ADM1023'...            No
Probing for `Maxim MAX1617'...                              No
Probing for `Maxim MAX1617A'...                             No
Probing for `Maxim MAX1668'...                              No
Probing for `Maxim MAX1805'...                              No
Probing for `Maxim MAX1989'...                              No
Probing for `Maxim MAX6655/MAX6656'...                      No
Probing for `TI THMC10'...                                  No
Probing for `National Semiconductor LM84'...                No
Probing for `Genesys Logic GL523SM'...                      No
Probing for `Onsemi MC1066'...                              No
Probing for `Maxim MAX1619'...                              No
Probing for `National Semiconductor LM82/LM83'...           No
Probing for `Maxim MAX6659'...                              No
Probing for `Maxim MAX6680/MAX6681'...                      No
Probing for `National Semiconductor LM64'...                No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Probing for `ITE IT8201R/IT8203R/IT8206R/IT8266R'...        Yes
    (confidence 6, not a hardware monitoring chip)
Probing for `Fintek F75111R/RG/N (GPIO)'...                 No
Probing for `Fintek F75121R/F75122R/RG (VID+GPIO)'...       No
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No
Client found at address 0x52
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!
Do you want to scan the ISA I/O ports? (YES/no): yes
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM78-J' at 0x290...     No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some Super I/O chips may also contain sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): yes
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      Yes
Found `ITE IT8712F Super IO Sensors'                        Success!
    (address 0x290, driver `it87')
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No

Some south bridges, CPUs or memory controllers may also contain
embedded sensors. Do you want to scan for them? (YES/no): yes
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD K10 thermal sensors...                                  No
Intel Core family thermal sensor...                         No
Intel AMB FB-DIMM thermal sensor...                         No

Now follows a summary of the probes I have just done.
Just press ENTER to continue: yes

Driver `it87' (should be inserted):
  Detects correctly:
  * ISA bus, address 0x290
    Chip `ITE IT8712F Super IO Sensors' (confidence: 9)

I will now generate the commands needed to load the required modules.
Just press ENTER to continue: 

To load everything that is needed, add this to /etc/modules:

#----cut here----
# Chip drivers
it87
#----cut here----

Do you want to add these lines automatically? (yes/NO)yes
sara@sara-desktop:~$ 

```

---

### Post by miegiel on 2009-08-07
> **coller_girl said:**
> hi i need help with this my fan speeds al over the shop, so i tried installing lm-sensors and got this output... what to do next?

1st of all, *lm-sensors* is only a monitoring program, it doesn't control your fan speed.

You can open */etc/modules* in a text editor to make sure your *it87* is there. If it isn't just add it (you'll need root rights to edit it). The modules file gets read during boot up, to read the sensor's values run *sensors* in a terminal.

---

### Post by limejuice on 2009-08-29
If you have Intel i7 chip and 1366 mobo, see this thread  [http://ubuntuforums.org/showthread.php?t=1056681](http://ubuntuforums.org/showthread.php?t=1056681)


This said I needed to get lm-sensors 3.1.0 and build it from source. The current version in the Ubuntu repository for 09.04 release is 3.0.2.

However, you only need 3.1.0 to get sensors-detect to recognize the correct modules for you.
Here are the correct modules for i7. This works even with 3.0.2 lm-sensors.

> 
#Chip drivers
coretemp
w83627ehf force_id=0x8860


---

### Post by Feelin_froggy8877 on 2009-08-31
I cannot get past "sudo sensors-detect" Sorry, no sensors were detected.
Either your sensors are not supported, or they are connected to an
I2C or SMBus adapter that is not supported. See
[http://www.lm-sensors.org/wiki/FAQ/Chapter3](http://www.lm-sensors.org/wiki/FAQ/Chapter3) for further information.
If you find out what chips are on your board, check
[http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) for driver status. 

k-dawg@k-dawg-desktop:~$ sudo lshw
k-dawg-desktop            
    description: Desktop Computer
    product: OptiPlex GX270
    vendor: Dell Computer Corporation
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: administrator_password=enabled boot=normal chassis=desktop cpus=1 power-on_password=enabled uuid=44454C4C-0000-1020-8020-80C04F202020
  *-core
       description: Motherboard
       product: 0CG566
       vendor: Dell Computer Corp.
       physical id: 0
       serial: ..CN1374046O058I.
     *-firmware
          description: BIOS
          vendor: Dell Computer Corporation
          physical id: 0
          version: A07 (06/26/2006)
          size: 64KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppytoshiba int5printscreen int9keyboard int14serial int17printer acpi usb agp ls120boot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.40GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 15.2.9
          slot: Microprocessor
          size: 2400MHz
          capacity: 3600MHz
          width: 32 bits
          clock: 800MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid xtpr
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 8KiB
             capacity: 16KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 512KiB
             capacity: 512KiB
             capabilities: internal varies unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 1536MiB
        *-bank:0
             description: DIMM SDRAM Synchronous 333 MHz (3.0 ns)
             physical id: 0
             slot: DIMM_1
             size: 256MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:1
             description: DIMM SDRAM Synchronous 333 MHz (3.0 ns)
             physical id: 1
             slot: DIMM_2
             size: 512MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:2
             description: DIMM SDRAM Synchronous 333 MHz (3.0 ns)
             physical id: 2
             slot: DIMM_3
             size: 256MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:3
             description: DIMM SDRAM Synchronous 333 MHz (3.0 ns)
             physical id: 3
             slot: DIMM_4
             size: 512MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
     *-pci
          description: Host bridge
          product: 82865G/PE/P DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-pci:0
             description: PCI bridge
             product: 82865G/PE/P PCI to AGP Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
           *-display
                description: VGA compatible controller
                product: NV18 [GeForce4 MX 440 AGP 8x]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 bus_master cap_list
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia
        *-usb:0
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: c2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
           *-multimedia
                description: Multimedia audio controller
                product: SB Audigy
                vendor: Creative Labs
                physical id: 8
                bus info: pci@0000:02:08.0
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=EMU10K1_Audigy latency=64 maxlatency=20 mingnt=2 module=snd_emu10k1
           *-firewire
                description: FireWire (IEEE 1394)
                product: SB Audigy FireWire Port
                vendor: Creative Labs
                physical id: 8.2
                bus info: pci@0000:02:08.2
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2 module=ohci1394
           *-network
                description: Ethernet interface
                product: 82540EM Gigabit Ethernet Controller
                vendor: Intel Corporation
                physical id: c
                bus info: pci@0000:02:0c.0
                logical name: eth0
                version: 02
                serial: 00:1a:a0:aa:03:0f
                size: 100MB/s
                capacity: 1GB/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm pcix msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k3-NAPI duplex=full firmware=N/A ip=98.240.112.82 latency=64 link=yes mingnt=255 module=e1000 multicast=yes port=twisted pair speed=100MB/s
        *-isa
             description: ISA bridge
             product: 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801EB/ER (ICH5/ICH5R) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
           *-disk:0
                description: ATA Disk
                product: QUANTUM FIREBALL
                vendor: Quantum
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: APL.
                serial: 052123205633
                size: 19GiB (20GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=81108110
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 8074442b-808b-9d4a-94dd-c5dfffc703e5
                   size: 10001MiB
                   capacity: 10001MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2009-07-25 11:51:43 filesystem=ntfs label=Microshit state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 9467MiB
                   capacity: 9467MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 9467MiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
           *-disk:1
                description: ATA Disk
                product: Maxtor 6Y120P0
                vendor: Maxtor
                physical id: 1
                bus info: scsi@0:0.1.0
                logical name: /dev/sdb
                version: YAR4
                serial: Y33YD2BE
                size: 114GiB (122GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000784c4
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.1.0,1
                   logical name: /dev/sdb1
                   version: 1.0
                   serial: 63fc02f9-c191-4ec9-bd2c-0afd3eddd597
                   size: 4094MiB
                   capacity: 4094MiB
                   capabilities: primary bootable journaled extended_attributes large_files ext3 ext2 initialized
                   configuration: created=2009-07-25 17:56:26 filesystem=ext3 label=AntiX modified=2009-08-30 23:36:45 mounted=2009-08-30 23:36:45 state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.1.0,2
                   logical name: /dev/sdb2
                   size: 110GiB
                   capacity: 110GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: W95 FAT32 partition
                      physical id: 5
                      logical name: /dev/sdb5
                      logical name: /media/myshit
                      capacity: 101GiB
                      configuration: mount.fstype=vfat mount.options=rw,fmask=0000,dmask=0000,allow_utime=0022,codepage=cp437,iocharset=utf8 state=mounted
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sdb6
                      capacity: 2933MiB
                 *-logicalvolume:2
                      description: Linux swap / Solaris partition
                      physical id: 7
                      logical name: /dev/sdb7
                      capacity: 2557MiB
                      capabilities: nofs
                 *-logicalvolume:3
                      description: Linux filesystem partition
                      physical id: 8
                      logical name: /dev/sdb8
                      capacity: 3851MiB
           *-cdrom
                description: CD-R/CD-RW writer
                physical id: 2
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                capabilities: audio cd-r cd-rw
                configuration: status=nodisc
           *-disk:2
                description: ATA Disk
                product: WDC WD100EB-00BH
                vendor: Western Digital
                physical id: 3
                bus info: scsi@1:0.1.0
                logical name: /dev/sdc
                version: 15.1
                serial: WD-WMA713523734
                size: 9541MiB (10GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00730072
              *-volume
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@1:0.1.0,1
                   logical name: /dev/sdc1
                   version: 1.0
                   serial: d498af98-c9af-411b-aeb4-4942469e8d9d
                   size: 9538MiB
                   capacity: 9538MiB
                   capabilities: primary bootable journaled large_files ext3 ext2 initialized
                   configuration: created=2009-07-26 19:03:58 filesystem=ext3 label=Sabayon modified=2009-08-30 23:36:56 mounted=2009-08-30 23:36:55 state=clean
        *-ide:1
             description: IDE interface
             product: 82801EB (ICH5) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
        *-serial
             description: SMBus
             product: 82801EB/ER (ICH5/ICH5R) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: driver=i801_smbus latency=0 module=i2c_i801
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 76:45:b1:89:5d:86
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by jlh68 on 2009-09-18
On my _Laptop_, I can only get one temperature to show:  ACPI THRM CPU and lmsensors temp1, actually they are both reporting the same thing.  I do not get my HDD temp or any other data.  I can get my HDD temp by using the following command "sudo hddtemp /dev/sda", so I know it is available.  I do get the HDD temp on my desktop.

OK, please help me to get more data from lm-sensors.
thanks

---

### Post by abdusamed on 2009-10-14
can u recreate this thread.. because the thread is old..and mkdev isn't used now.. i REALLY want to slow my fan DOWN  in xubuntu 9.04


sensors-detect doesn'[t detect anny sensors what so ever in my old ***** p4.

---

### Post by miegiel on 2009-10-14
> **abdusamed said:**
> can u recreate this thread.. because the thread is old..and mkdev isn't used now.. i REALLY want to slow my fan DOWN  in xubuntu 9.04


sensors-detect doesn'[t detect anny sensors what so ever in my old ***** p4.

AFAIK you don't need to run that *mkdev* script anymore. Just install > detect > add detected sensor to */etc/modules* > reboot.

```
sudo apt-get install lm-sensors
sudo sensors-detect
sudo nano /etc/modules
```

Also, lm-sensors is just a monitor. So it will only tell you your fan speed and not change the speed. I normally set the fan speed in the BIOS, but not every BIOS gives you the option to change it.

---

### Post by whitethorn on 2009-10-14
> **miegiel said:**
> AFAIK you don't need to run that *mkdev* script anymore. Just install > detect > add detected sensor to */etc/modules* > reboot.

```
sudo apt-get install lm-sensors
sudo sensors-detect
sudo nano /etc/modules
```

Also, lm-sensors is just a monitor. So it will only tell you your fan speed and not change the speed. I normally set the fan speed in the BIOS, but not every BIOS gives you the option to change it.

Once you have lm-sensors installed and after running sensors-detect.  When you run sensors if it shows some fan speeds then running pwmconfig might be able to let you control your fan speeds.  pwmconfig is pretty straightforward.  Afterwards you only need a couple small steps to get fancontrol to start on boot and you can control your fanspeeds.  Maybe I should write a howto about it :)

---

### Post by abdusamed on 2009-10-16
okay..thanks..ill give it a try... and yes.. the module did open.. now to remember what to do :D

---

### Post by mr clark25 on 2009-10-31
this guide is great!

i should know this, but i dont.... how do you change a file when the owner is root? (need to do this to complete step 4 where you paste the modules to the modules file located in /ect/modules)
so, how do you do this? do you use sudo in the terminal?

im new to this kind of thing, but i really want to do this. i just cant save my changes in modules.

PLZ HELP!

---

### Post by Penguin Guy on 2009-11-01
> **mr clark25 said:**
> this guide is great!

i should know this, but i dont.... how do you change a file when the owner is root? (need to do this to complete step 4 where you paste the modules to the modules file located in /ect/modules)
so, how do you do this? do you use sudo in the terminal?

im new to this kind of thing, but i really want to do this. i just cant save my changes in modules.

PLZ HELP!
Run [COLOR="Green"]gksu gedit /etc/modules[/COLOR], and just paste it in.

---

### Post by mr clark25 on 2009-11-01
thanks so much for you help! i now now that my processor runs nice and cool with all stock settings and cooling.

output:

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +32.0°C  (high = +74.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +32.0°C  (high = +74.0°C, crit = +100.0°C)

---

### Post by swalker23 on 2009-11-01
Hopefully someone can help me.  I've installed lm_sensors on intrepid and jaunty from source on my i7 setup and didn't have any problems.  Lm-sensors detected all my cores,voltages, and etc.  I just did a fresh install of Kubuntu 9.1 Koala and the first thing I did was install lm-sensors from source 3.1.1.  Everything installed fine no hang ups on make or install and after running senors detect I ran sensors.  This is what it gave me:
```
acpitz-virtual-0
Adapter: Virtual device
temp1:       +25.0°C  (crit = +6280.3°C)

```

How can I get my temps to show?  I've been googling but didn't have any luck in solving my problem.  My motherboard is a EVGA classified.  I'm still a linux noob so bare with me.

Edit:
Please disregard my above question I got it working.  I will put my solution down for anyone else experiencing difficulties.
Copy and paste the below into /etc/modules and reboot after you save.  I pasted it hours ago and just didn't reboot.
```
#Chip drivers
coretemp
w83627ehf force_id=0x8860
```

---

### Post by mr clark25 on 2009-11-03
someone might have said this already, but this works great with the command: "watch"
this makes it re-fresh every 2 seconds.

just enter:
watch sensors

---

### Post by jsa13 on 2009-11-12
Running "sensors-detect" identified w83627hf, but modprobe wouldn't insert it.  Checking dmesg was the key.

For 9.10, I had to add kernel option "acpi_enforce_resources=lax" to /etc/default/grub (2.x, or /boot/grub/menu.lst w/ grub 1.x).  

Then w83627hf for my abit K8 loaded w/o issue.  Setting up the fan speeds w/ "pwmconfig" afterward was easy.

---

### Post by nishant.singh28 on 2009-11-14
ummm...a stupid question but what do the temp values stand for. I have a Dell Studio 1555 notebook with the GPU embedded onto the motherboard( all new laptops have them on the motherboard ). It would be appreciable if someone could tell me what the temp temperature signifies? :KS

---

### Post by miegiel on 2009-11-15
> **nishant.singh28 said:**
> ummm...a stupid question but what do the temp values stand for. I have a Dell Studio 1555 notebook with the GPU embedded onto the motherboard( all new laptops have them on the motherboard ). It would be appreciable if someone could tell me what the temp temperature signifies? :KS

Can't tell really, without the output of
```
sensors
```
It could be the CPU temp or the chipset temp or both.

---

### Post by nishant.singh28 on 2009-11-15
> **miegiel said:**
> Can't tell really, without the output of
```
sensors
```It could be the CPU temp or the chipset temp or both.

acpitz-virtual-0
Adapter: Virtual device
temp1:       +54.0°C  (crit = +100.0°C)                  
temp2:       +55.0°C  (crit = +100.0°C)                  
temp3:       +57.0°C  (crit = +100.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +45.0°C  (high = +100.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +45.0°C  (high = +100.0°C, crit = +100.0°C)  


 Now??

---

### Post by miegiel on 2009-11-15
> **nishant.singh28 said:**
> acpitz-virtual-0
Adapter: Virtual device
temp1:       +54.0°C  (crit = +100.0°C)                  
temp2:       +55.0°C  (crit = +100.0°C)                  
temp3:       +57.0°C  (crit = +100.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +45.0°C  (high = +100.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +45.0°C  (high = +100.0°C, crit = +100.0°C)  


 Now??
The *coretemp-isa-000X* sensors sense the temperatures of the cores of intel dual core CPUs (1 for each core). I think *acpitz-virtual-0* is the sensor of your laptop's motherboard, probably northbridge (with the graphics core in it), southbridge and a external CPU sensor.

If you can see the temperatures in the BIOS (my laptop BIOS doesn't show them, but my desktop BIOS does) you can compare the values there with the values you get from lm-sensors. If you let your laptop run idle for a few min and then reboot into the BIOS the temperatures will be more or less the same.

You can also stress different parts and see which temperature increases. For example *glxgears* (terminal) will stress your CPU and graphics core. And you might be able to tell which temperature is the southbridge by stressing your network (is likely connected to your southbridge) or copying files on your disk.

---

### Post by nishant.singh28 on 2009-11-15
> **miegiel said:**
> The *coretemp-isa-000X* sensors sense the temperatures of the cores of intel dual core CPUs (1 for each core). I think *acpitz-virtual-0* is the sensor of your laptop's motherboard, probably northbridge (with the graphics core in it), southbridge and a external CPU sensor.

If you can see the temperatures in the BIOS (my laptop BIOS doesn't show them, but my desktop BIOS does) you can compare the values there with the values you get from lm-sensors. If you let your laptop run idle for a few min and then reboot into the BIOS the temperatures will be more or less the same.

You can also stress different parts and see which temperature increases. For example *glxgears* (terminal) will stress your CPU and graphics core. And you might be able to tell which temperature is the southbridge by stressing your network (is likely connected to your southbridge) or copying files on your disk.


Well I figured it out....temp1 is GPU, temp2 is the Southbridge and temp3 the Northbridge...thanks!!!:)

---

### Post by jeremey on 2009-12-15
Ok, I'm not sure if I am doing something correctly...

```
jeremey@ubuntu:~$ sudo sensors-detect
# sensors-detect revision 5249 (2008-05-11 22:56:25 +0200)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): y
Probing for PCI bus adapters...
Use driver `i2c-viapro' for device 0000:00:11.0: VIA Technologies VT8233 VLink South Bridge

We will now try to load each adapter module in turn.
Module `i2c-viapro' already loaded.
If you have undetectable or unsupported I2C/SMBus adapters, you can have
them scanned by manually loading the modules before running this script.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Next adapter: SMBus Via Pro adapter at 0400 (i2c-0)
Do you want to scan it? (YES/no/selectively): 
Client found at address 0x18
Probing for `Analog Devices ADM1021'...                     No
Probing for `Analog Devices ADM1021A/ADM1023'...            No
Probing for `Maxim MAX1617'...                              No
Probing for `Maxim MAX1617A'...                             No
Probing for `Maxim MAX1668'...                              No
Probing for `Maxim MAX1805'...                              No
Probing for `Maxim MAX1989'...                              No
Probing for `Maxim MAX6655/MAX6656'...                      No
Probing for `TI THMC10'...                                  No
Probing for `National Semiconductor LM84'...                No
Probing for `Genesys Logic GL523SM'...                      No
Probing for `Onsemi MC1066'...                              No
Probing for `Maxim MAX1619'...                              No
Probing for `National Semiconductor LM82/LM83'...           No
Probing for `Maxim MAX6680/MAX6681'...                      No
Probing for `National Semiconductor LM64'...                No
Client found at address 0x2d
Probing for `Myson MTP008'...                               No
Probing for `National Semiconductor LM78'...                No
Probing for `National Semiconductor LM78-J'...              No
Probing for `National Semiconductor LM79'...                No
Probing for `National Semiconductor LM80'...                No
Probing for `National Semiconductor LM85 or LM96000'...     No
Probing for `Analog Devices ADM1027, ADT7460 or ADT7463'... No
Probing for `SMSC EMC6D100, EMC6D101 or EMC6D102'...        No
Probing for `Analog Devices ADT7476'...                     No
Probing for `Andigilog aSC7611'...                          No
Probing for `Andigilog aSC7621'...                          No
Probing for `National Semiconductor LM87'...                No
Probing for `National Semiconductor LM93'...                No
Probing for `Winbond W83781D'...                            No
Probing for `Winbond W83782D'...                            No
Probing for `Winbond W83783S'...                            No
Probing for `Winbond W83792D'...                            No
Probing for `Winbond W83793R/G'...                          No
Probing for `Winbond W83791SD'...                           No
Probing for `Winbond W83627HF'...                           Success!
    (confidence 8, driver `use-isa-instead', other addresses: 0x48 0x49)
Probing for `Winbond W83627EHF'...                          No
Probing for `Winbond W83627DHG'...                          No
Probing for `Asus AS99127F (rev.1)'...                      No
Probing for `Asus AS99127F (rev.2)'...                      No
Probing for `Asus ASB100 Bach'...                           No
Probing for `Winbond W83L784R/AR/G'...                      No
Probing for `Winbond W83L785R/G'...                         No
Probing for `Genesys Logic GL518SM Revision 0x00'...        No
Probing for `Genesys Logic GL518SM Revision 0x80'...        No
Probing for `Genesys Logic GL520SM'...                      No
Probing for `Genesys Logic GL525SM'...                      No
Probing for `Analog Devices ADM9240'...                     No
Probing for `Dallas Semiconductor DS1780'...                No
Probing for `National Semiconductor LM81'...                No
Probing for `Analog Devices ADM1026'...                     No
Probing for `Analog Devices ADM1025'...                     No
Probing for `Philips NE1619'...                             No
Probing for `Analog Devices ADM1029'...                     No
Probing for `Analog Devices ADM1030'...                     No
Probing for `Analog Devices ADM1031'...                     No
Probing for `Analog Devices ADM1022'...                     No
Probing for `Texas Instruments THMC50'...                   No
Probing for `VIA VT1211 (I2C)'...                           No
Probing for `ITE IT8712F'...                                No
Probing for `ALi M5879'...                                  No
Probing for `SMSC LPC47M15x/192/292/997'...                 No
Probing for `SMSC DME1737'...                               No
Probing for `SMSC SCH5027D-NW'...                           No
Probing for `Fintek F75373S/SG'...                          No
Probing for `Fintek F75375S/SP'...                          No
Probing for `Fintek F75387SG/RG'...                         No
Probing for `Analog Devices ADM1024'...                     No
Probing for `Winbond W83791D'...                            No
Client found at address 0x48
Probing for `National Semiconductor LM75'...                No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `National Semiconductor LM77'...                No
Probing for `Dallas Semiconductor DS1621/DS1631'...         No
Probing for `Maxim MAX6650/MAX6651'...                      No
Probing for `National Semiconductor LM92'...                No
Probing for `National Semiconductor LM76'...                No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Client found at address 0x49
Probing for `National Semiconductor LM75'...                No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `National Semiconductor LM77'...                No
Probing for `Dallas Semiconductor DS1621/DS1631'...         No
Probing for `National Semiconductor LM92'...                No
Probing for `National Semiconductor LM76'...                No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No
Client found at address 0x51
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!
Do you want to scan the ISA I/O ports? (YES/no): 
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM78-J' at 0x290...     No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some Super I/O chips may also contain sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): 
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       Yes
Found `Winbond W83627HF/F/HG/G Super IO Sensors'            Success!
    (address 0x290, driver `w83627hf')
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No

Some south bridges, CPUs or memory controllers may also contain
embedded sensors. Do you want to scan for them? (YES/no): 
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD K10 thermal sensors...                                  No
Intel Core family thermal sensor...                         No
Intel AMB FB-DIMM thermal sensor...                         No

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `w83627hf' (should be inserted):
  Detects correctly:
  * ISA bus, address 0x290
    Chip `Winbond W83627HF/F/HG/G Super IO Sensors' (confidence: 9)

I will now generate the commands needed to load the required modules.
Just press ENTER to continue: 

To load everything that is needed, add this to /etc/modules:

#----cut here----
# Chip drivers
w83627hf
#----cut here----

Do you want to add these lines automatically? (yes/NO)
jeremey@ubuntu:~$ sudo /etc/init.d/module-init-tools
Usage: /etc/init.d/module-init-tools COMMAND

----> My edit:  what goes into COMMAND? I tried w3627hf <------

jeremey@ubuntu:~$ sudo /etc/init.d/module-init-tools w83627hf
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service module-init-tools w83627hf

The script you are attempting to invoke has been converted to an Upstart
job, but w83627hf is not supported for Upstart jobs.
jeremey@ubuntu:~$ sudo gedit /etc/modprobe.d/local
jeremey@ubuntu:~$ sudo update-modules
sudo: update-modules: command not found
jeremey@ubuntu:~$ sudo gedit /etc/modules
jeremey@ubuntu:~$ sudo modprobe i2c-viapro
WARNING: All config files need .conf: /etc/modprobe.d/local, it will be ignored in a future release.
jeremey@ubuntu:~$ sudo i2c-0
sudo: i2c-0: command not found
jeremey@ubuntu:~$ sudo modprobe i2c-0
WARNING: All config files need .conf: /etc/modprobe.d/local, it will be ignored in a future release.
FATAL: Module i2c_0 not found.
jeremey@ubuntu:~$ sudo rm /etc/modprobe.d/local
jeremey@ubuntu:~$ sudo modprobe i2c-viapro
jeremey@ubuntu:~$ sudo modprobe i2c-0
FATAL: Module i2c_0 not found.
jeremey@ubuntu:~$ sudo modprobe use-isa-instead
FATAL: Module use_isa_instead not found.
jeremey@ubuntu:~$ sudo modprobe i2c-isa
FATAL: Module i2c_isa not found.
jeremey@ubuntu:~$ sudo modprobe w83627hf
FATAL: Error inserting w83627hf (/lib/modules/2.6.31-16-generic/kernel/drivers/hwmon/w83627hf.ko): Device or resource busy
jeremey@ubuntu:~$ sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
jeremey@ubuntu:~$ 

```

I have a MSI K7T266 Pro Ver.1 mobo, and I know there are sensors and I want to control fan speed after getting this working.  This thing sounds like it's gonna lift off!

I am running 9.10 and the latest updates.

Thanks,
J

---

### Post by miegiel on 2009-12-15
> **jeremey said:**
> Ok, I'm not sure if I am doing something correctly...

... snip ...

I have a MSI K7T266 Pro Ver.1 mobo, and I know there are sensors and I want to control fan speed after getting this working.  This thing sounds like it's gonna lift off!

I am running 9.10 and the latest updates.

Thanks,
J
After
```
sudo sensors-detect
```
you should have run
```
gksudo gedit /etc/modules
```
or
```
sudo nano /etc/modules
```
added the next 2 lines
```
# Chip drivers
w83627hf
```
save and reboot

---

### Post by jeremey on 2009-12-15
Thanks miegiel,

Ok, Here's my etc/modules:

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
floppy

# Chip drivers
w83627hf
```

I rebooted with that, then:

```
jeremey@ubuntu:~$ sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
jeremey@ubuntu:~$
```

:-k

---

### Post by miegiel on 2009-12-16
> **jeremey said:**
> Thanks miegiel,

Ok, Here's my etc/modules:

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
floppy

# Chip drivers
w83627hf
```

I rebooted with that, then:

```
jeremey@ubuntu:~$ sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
jeremey@ubuntu:~$
```

:-k

Before you reboot you need to add the sensor to the */etc/modules* file (you need root rights to do that). See the steps in my post above.

---

### Post by zedstrange on 2009-12-28
> **jlh68 said:**
> On my _Laptop_, I can only get one temperature to show:  ACPI THRM CPU and lmsensors temp1, actually they are both reporting the same thing.  I do not get my HDD temp or any other data.  I can get my HDD temp by using the following command "sudo hddtemp /dev/sda", so I know it is available.  I do get the HDD temp on my desktop.

Could someone please answer this unanswered question,  because i have the same question?

thanks

---

### Post by mhousel on 2009-12-28
I've tried all of this and still nothing will allow me to kep the fans running on my Toshiba satellite laptop.

The lm-sensors and sensor-detect do not work as shown here on this particular laptop it seems.
I can't get the sensor-applet to run either. (It is installed but not in /usr/bin as is the sensors executable)

#sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +59.0°C  (crit = +104.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +59.0°C  (high = +100.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +60.0°C  (high = +100.0°C, crit = +100.0°C)

/etc/moduels file-
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp

# Generated by sensors-detect on Sun Dec 27 12:08:12 2009
# Chip drivers
coretemp



The real problem is that the temperature limits seem to be set incorrectly and I have yet to find a way (that works on my laptop) to lower them.

No problems until I try to play any streaming video full screen then the CPU overheats because the fan doesn't speed up enough until right about the time it shuts off due to over temp.

Nothing related to monitoring or controlling the fan speeds works on this computer it seems.

From the files related to ACPI--
cat /proc/acpi/thermal_zone/THRM/cooling_mode
<setting not supported>

cat /proc/acpi/thermal_zone/THRM/polling_frequency
<polling disabled>

cat /proc/acpi/thermal_zone/THRM/state
state:                   ok

NOTE: This matches the sensors output and the output shown on the toolbar by kSensors.

cat /proc/acpi/thermal_zone/THRM/temperature
temperature:             54 C

cat /proc/acpi/thermal_zone/THRM/trip_points
critical (S5):           104 C
passive:                 104 C: tc1=2 tc2=3 tsp=40 devices=CPU0

And I've tried the things I can find related to changing the argument in grub:

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=" acpi_osi=force"
[COLOR="Red"]// tried these (Yeah, I ran grub-update between boots:
// quiet splash acpi_osi=Linux
// quiet splash acpi_osi=force
// quiet splash
// removing quiet and splash even though they have NOTHING to do with it.
// Nothing changes in the fan behavior.
#quiet splash[/COLOR]
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"

Oh, and also the things related to  **HOWTO Fix A Buggy DSDT File**
If I decompile and recompile my DSDT file the only errors are related to some sort of warnings about line terminators, nothing in the code itself.

---

### Post by miegiel on 2009-12-29
> **zedstrange said:**
> Could someone please answer this unanswered question,  because i have the same question?

thanks

You can't read hdd temps with lm-sensors (at least I never have). Use hddtemp to get your hdd temperature.

install :
```
sudo apt-get install hddtemp
```
display hdd temp in terminal :
```
sudo hddtemp /dev/sda
```
display hdd temp in conky :
```
${hddtemp /dev/sda}
```

---

### Post by zedstrange on 2009-12-31
> **miegiel said:**
> You can't read hdd temps with lm-sensors (at least I never have). Use hddtemp to get your hdd temperature.

I figured it out finally,   the hddtemp _daemon_ needs to be loaded at startup (one would think that such an obvious thing would have been published/discussed more often).  Then it will be displayed as options with any of the Sensors applications, like GkrellM and Hardware Sensors Monitor.

Credit goes to this thread
[http://swiss.ubuntuforums.org/showthread.php?t=1359129](http://swiss.ubuntuforums.org/showthread.php?t=1359129)

run this

```
sudo dpkg-reconfigure hddtemp
```

---

### Post by cannon_dt on 2010-01-04
I did all the stuff as outlines in the posts but I get the foll:
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.

What could this mean?
Mine is a new ASUS EVO motherboard and I just finished configuring all the stuff.

also I tried computer temp and that did not work too?

X sensors (from add software) also did not work.

I am running the 64 bit version, btw.

Please help.

Cannon

---

### Post by miegiel on 2010-01-05
> **cannon_dt said:**
> I did all the stuff as outlines in the posts but I get the foll:
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.

What could this mean?
Mine is a new ASUS EVO motherboard and I just finished configuring all the stuff.

also I tried computer temp and that did not work too?

X sensors (from add software) also did not work.

I am running the 64 bit version, btw.

Please help.

Cannon

Run
```
sudo sensors-detect
```
in a terminal. At the end of the detection process you get the option to let *sensors-detect* add the sensor to your */etc/modules* file or (default) to do it yourself.

---

### Post by cannon_dt on 2010-01-05
It did do that miegiel, here is what is there in my modules file
# Generated by sensors-detect on Mon Jan  4 20:44:35 2010
# Chip drivers
it87
# no driver for AMD K10 thermal sensors yet

So I dont know what else is missing.

Ananth

---

### Post by eddier on 2010-01-05
I think this must be the longest thread on the forum ?

Is the original post still relevant (to the current release)?

eddier.

---

### Post by cyberkost on 2010-01-05
Longest thread? Ha-ha-ha.  Check [this one]("http://ubuntuforums.org/showthread.php?t=281865") out .. just as an example.
One a more serious note -- yes, the OP has, perhaps, lost some relevance (now that lm-sensors is a package and could be installed through synaptic), but there's still quite a bit of useful info in the thread itself.
> **eddier said:**
> I think this must be the longest thread on the forum ?

Is the original post still relevant (to the current release)?

eddier.

---

### Post by sander815 on 2010-01-06
didn't work fo rme
[PHP]
[root@homeserver ~]# ./mkdev.sh
/dev/i2c-0
mknod: `/dev/i2c-0': File exists
[root@homeserver ~]# sensors-detect
# sensors-detect revision 5291 (2008-06-23 23:40:46 -0700)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no):
Probing for PCI bus adapters...
Sorry, no supported PCI bus adapters found.

If you have undetectable or unsupported I2C/SMBus adapters, you can have
them scanned by manually loading the modules before running this script.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!
Do you want to scan the ISA I/O ports? (YES/no):
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM78-J' at 0x290...     No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Some Super I/O chips may also contain sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no):
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       Yes
Found `Winbond W83627DHG Super IO Sensors'                  Success!
    (address 0x290, driver `w83627ehf')

Some south bridges, CPUs or memory controllers may also contain
embedded sensors. Do you want to scan for them? (YES/no):
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD K10 thermal sensors...                                  No
Intel AMB FB-DIMM thermal sensor...                         No

Now follows a summary of the probes I have just done.
Just press ENTER to continue:

Driver `w83627ehf' (should be inserted):
  Detects correctly:
  * ISA bus, address 0x290
    Chip `Winbond W83627DHG Super IO Sensors' (confidence: 9)

Do you want to overwrite /etc/sysconfig/lm_sensors? (YES/no): y
Starting lm_sensors: No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
                                                           [FAILED]
[root@homeserver ~]#
[/PHP]

---

### Post by pulpo69 on 2010-01-06
how to install this driver for k10 thermal sensors?

[http://khali.linux-fr.org/devel/misc/k10temp/](http://khali.linux-fr.org/devel/misc/k10temp/)

found on this page [http://lm-sensors.org/wiki/Devices](http://lm-sensors.org/wiki/Devices)

---

### Post by miegiel on 2010-01-13
> **sander815 said:**
> didn't work fo rme
[PHP]
[root@homeserver ~]# ./mkdev.sh
/dev/i2c-0
mknod: `/dev/i2c-0': File exists
[root@homeserver ~]# sensors-detect
# sensors-detect revision 5291 (2008-06-23 23:40:46 -0700)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no):
Probing for PCI bus adapters...
Sorry, no supported PCI bus adapters found.

If you have undetectable or unsupported I2C/SMBus adapters, you can have
them scanned by manually loading the modules before running this script.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!
Do you want to scan the ISA I/O ports? (YES/no):
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM78-J' at 0x290...     No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Some Super I/O chips may also contain sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no):
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       Yes
Found `Winbond W83627DHG Super IO Sensors'                  Success!
    (address 0x290, driver `w83627ehf')

Some south bridges, CPUs or memory controllers may also contain
embedded sensors. Do you want to scan for them? (YES/no):
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD K10 thermal sensors...                                  No
Intel AMB FB-DIMM thermal sensor...                         No

Now follows a summary of the probes I have just done.
Just press ENTER to continue:

Driver `w83627ehf' (should be inserted):
  Detects correctly:
  * ISA bus, address 0x290
    Chip `Winbond W83627DHG Super IO Sensors' (confidence: 9)

Do you want to overwrite /etc/sysconfig/lm_sensors? (YES/no): y
Starting lm_sensors: No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
                                                           [FAILED]
[root@homeserver ~]#
[/PHP]

2 things :
[LIST]
[*]I wouldn't run *sensors-detect* as root. Instead do : ```
sudo sensors-detect
```
[*]I don't know what *sensors-detect* wants with */etc/sysconfig/lm_sensors*, but for me the sensor module that should be loaded during boot up is listed in */etc/modules*
[/LIST]

---

### Post by miegiel on 2010-01-13
> **pulpo69 said:**
> how to install this driver for k10 thermal sensors?

[http://khali.linux-fr.org/devel/misc/k10temp/](http://khali.linux-fr.org/devel/misc/k10temp/)

found on this page [http://lm-sensors.org/wiki/Devices](http://lm-sensors.org/wiki/Devices)

AFAIK the k10 module comes with karmic (and should be detected with *sudo sensors-detect*), so you shouldn't need to install it.

---

### Post by miegiel on 2010-01-13
> **cyberkost said:**
> Longest thread? Ha-ha-ha.  Check [this one]("http://ubuntuforums.org/showthread.php?t=281865") out .. just as an example.
One a more serious note -- yes, the OP has, perhaps, lost some relevance (now that lm-sensors is a package and could be installed through synaptic), but there's still quite a bit of useful info in the thread itself.

Good example :cool: almost 1.7 million thread views !!!

Yeah, the OP is not up-to-date anymore. It's just 3 easy steps now :
[LIST=1]
[*]```
sudo apt-get install lm-sensors
```
[*]```
sudo sensors-detect
``` Note of the detected sensor module (take the *"confidence"* into account when more than 1 sensor is detected).
[*]```
sudo nano /etc/modules
``` Add the detected sensor from step 2 to the list.
[/LIST]

---

### Post by miegiel on 2010-01-13
> **cannon_dt said:**
> It did do that miegiel, here is what is there in my modules file
# Generated by sensors-detect on Mon Jan  4 20:44:35 2010
# Chip drivers
it87
# no driver for AMD K10 thermal sensors yet

So I dont know what else is missing.

Ananth

Hmmm ... maybe I'm wrong and the k10 isn't supported yet. When I run *sensors-detect* I get the output below, but I don't have a k10 to test :neutral: (32bit karmic on a core 2 duo laptop here).

```
...
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD K10 thermal sensors...                                  No
Intel Core family thermal sensor...                         Success!
    (driver `coretemp')
Intel AMB FB-DIMM thermal sensor...                         No
...
```

---

### Post by Glaucous on 2010-01-16
I've now been trying for a couple of hours to get this program working, I even compiled 3.1.1 from their site without any luck.
I followed the last post on the previous page.

sensors-detect:

> # sensors-detect revision 5729 (2009-06-02 15:51:29 +0200)
# System: Gigabyte Technology Co., Ltd. GA-MA790X-UD3P

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): yes
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD K10 thermal sensors...                                  Success!
    (driver `to-be-written')
Intel Core family thermal sensor...                         No
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal and voltage sensors...                       No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): yes
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      Yes
Found `ITE IT8720F Super IO Sensors'                        Success!
    (address 0x228, driver `it87')
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No

Some systems (mainly servers) implement IPMI, a set of common interfaces
through which system health data may be retrieved, amongst other things.
We first try to get the information from SMBIOS. If we don't find it
there, we have to read from arbitrary I/O ports to probe for such
interfaces. This is normally safe. Do you want to scan for IPMI
interfaces? (YES/no): yes
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (yes/NO): yes
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): yes
Using driver `i2c-piix4' for device 0000:00:14.0: ATI Technologies Inc SB600 SMBus
Module i2c-dev loaded successfully.

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `it87':
  * ISA bus, address 0x228
    Chip `ITE IT8720F Super IO Sensors' (confidence: 9)

Driver `to-be-written':
  * Chip `AMD K10 thermal sensors' (confidence: 9)

Note: there is no driver for AMD K10 thermal sensors yet.
Check [http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) for updates.

Do you want to overwrite /etc/sysconfig/lm_sensors? (YES/no): yes
Copy prog/init/lm_sensors.init to /etc/init.d/lm_sensors
for initialization at boot time.
You should now start the lm_sensors service to load the required
kernel modules.

Unloading i2c-dev... OK



I opened /etc/modules, and tried inserting the following (changed each reboot when it didn't work):

-
 Driver `it87':
  * ISA bus, address 0x228
    Chip `ITE IT8720F Super IO Sensors' (confidence: 9)

-
Chip `ITE IT8720F Super IO Sensors' (confidence: 9)

-
Chip `ITE IT8720F Super IO Sensors'

-
`ITE IT8720F Super IO Sensors

Without any luck, still says when I run sensors:
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.

Edit: NOW i realized that I was supposed to add "it87", which makes sense.

---

### Post by miegiel on 2010-01-16
> **Glaucous said:**
> I've now been trying for a couple of hours to get this program working, I even compiled 3.1.1 from their site without any luck.
I followed the last post on the previous page.

sensors-detect:



I opened /etc/modules, and tried inserting the following (changed each reboot when it didn't work):

-
 Driver `it87':
  * ISA bus, address 0x228
    Chip `ITE IT8720F Super IO Sensors' (confidence: 9)

-
Chip `ITE IT8720F Super IO Sensors' (confidence: 9)

-
Chip `ITE IT8720F Super IO Sensors'

-
`ITE IT8720F Super IO Sensors

Without any luck, still says when I run sensors:
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.

Edit: NOW i realized that I was supposed to add "it87", which makes sense.

My */etc/modules* looks like this :
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp

# Generated by sensors-detect on Sat Oct 31 00:06:50 2009
# Chip drivers
coretemp
```
I think yours should be something like :
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp

# Added for lm-sensors
it87

```
*it87* is probably a sensor on your motherboard and should give you CPU temps too.

---

### Post by Glaucous on 2010-01-16
Exactly what I did, sorry for not clarifying that. Fanspeed is working good, the only problem now is to get AMD K10 working, for my CPU.
Since I'm right now sitting on Wubi, I have no problem playing around, right now I'm testing stuff in order to install Ubuntu correctly later on.

I installed Linux kernel 2.6.33 RC4, which seems to be working okay. People said that AMD K10 was supposed to be working here, but it's not so far, might have to change something in lm sensors as well.

Edit: At last, got it working! A small problem though, how do I restart fancontrol? Right now I'm tweaking the config file, would be easier if I could restart it.

---

### Post by confusion_music on 2010-01-20
I've only just got a whole new setup up and running last night, so I've not tested this yet, but I believe the following thread may have the answers for K10 sensors.

[http://ubuntuforums.org/showthread.php?p=7871888#post7871888]("http://ubuntuforums.org/showthread.php?p=7871888#post7871888")

---

### Post by blortS on 2010-01-24
Hi,

I'm currently running 9.04 and my fan is constantly running (Sony Vaio VGN-Z serie).
My laptop is about a year and a half old.
I upgraded this week to 9.10 but this didn't change the situation.
I tried almost everything (even fansilencer program, but this doesn't work either).

I installed lm-config and the output of sensors is:

```

acpitz-virtual-0
Adapter: Virtual device
temp1:       +48.0°C  (crit = +107.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +37.0°C  (high = +100.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +37.0°C  (high = +100.0°C, crit = +100.0°C) 

```

pwmconfig gives following (after sensorsdetect)
```

/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed

```

The fan noise is really driving me crazy (I'm currently studying and I want SILENCE!)
I didn't had this problem about a couple of months ago.


Anyone can help?

---

### Post by miegiel on 2010-01-24
> **blortS said:**
> ...

The fan noise is really driving me crazy (I'm currently studying and I want SILENCE!)
I didn't had this problem about a couple of months ago.


Anyone can help?

The 1st place to go to change your is your BIOS, if your BIOS supports changing fan speeds. I haven't needed programs to change the fanspeed, so I can't help you with that. Sorry :(

---

### Post by Rayve on 2010-01-28
So I followed the guide, but ran into a problem, in that I have very little displayed when I run "sensors"... see below.

```

candice@candice-desktop:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +40.0°C  (crit = +75.0°C)                  

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +25.0°C                                    

candice@candice-desktop:~$ sensors-detect
You need to be root to run this script.
candice@candice-desktop:~$ sudo sensors-detect
# sensors-detect revision 5249 (2008-05-11 22:56:25 +0200)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): YES
Probing for PCI bus adapters...
Use driver `i2c-piix4' for device 0000:00:14.0: ATI Technologies Inc IXP SB400 SMBus Controller

We will now try to load each adapter module in turn.
Module `i2c-piix4' already loaded.
If you have undetectable or unsupported I2C/SMBus adapters, you can have
them scanned by manually loading the modules before running this script.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Next adapter: NVIDIA i2c adapter  (i2c-0)
Do you want to scan it? (YES/no/selectively): YES

Next adapter: NVIDIA i2c adapter  (i2c-1)
Do you want to scan it? (YES/no/selectively): YES
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter: NVIDIA i2c adapter  (i2c-2)
Do you want to scan it? (YES/no/selectively): YES

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!
Do you want to scan the ISA I/O ports? (YES/no): YES
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM78-J' at 0x290...     No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some Super I/O chips may also contain sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): YES
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     Yes
Found `SMSC DME1737 Super IO'                               
    (hardware monitoring capabilities accessible via SMBus only)
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No

Some south bridges, CPUs or memory controllers may also contain
embedded sensors. Do you want to scan for them? (YES/no): YES
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   Success!
    (driver `k8temp')
AMD K10 thermal sensors...                                  No
Intel Core family thermal sensor...                         No
Intel AMB FB-DIMM thermal sensor...                         No

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `k8temp' (should be inserted):
  Detects correctly:
  * Chip `AMD K8 thermal sensors' (confidence: 9)

I will now generate the commands needed to load the required modules.
Just press ENTER to continue: 

To load everything that is needed, add this to /etc/modules:

#----cut here----
# Chip drivers
k8temp
#----cut here----

```

Here is my /etc/modules:

```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp

# added for sound issues 20 Jan after upgrading to 9.10
snd-emu10k1

# Generated by sensors-detect on Thu Jan 28 09:43:18 2010
# Chip drivers
k8temp

```

Any ideas?  Thanks!

---

### Post by Scott O'Nanski on 2010-02-01
Could you explain step 4 a bit better. It's confusing. You stated to add the modules in reverse order but from looking at your example they are not.

---

### Post by Scott O'Nanski on 2010-02-01
Okay, you said to answer "yes" to all the "YES/no" questions. Are you implying that the "yes/NO" question at the end is to be answered "NO"?

I get this bounced back to me from the terminal:

```

#----cut here----
# I2C adapter drivers
# modprobe unknown adapter NVIDIA i2c adapter 
# modprobe unknown adapter NVIDIA i2c adapter 
# modprobe unknown adapter NVIDIA i2c adapter 
# modprobe unknown adapter NVIDIA i2c adapter 
# modprobe unknown adapter NVIDIA i2c adapter 
# modprobe unknown adapter NVIDIA i2c adapter 
# Chip drivers
# no driver for Analog Devices ADT7473 yet
it87
coretemp
#----cut here----

``` 

What am I being told here, what am I to do with it?

As well, you state
> I found that there was no "/etc/modprobe.d/local" and that "alias char-major-89 i2c-dev" was already listed in "/etc/modprobe.d/aliases". So, nothing to do here.

Can you explain the relevance of this statement? Following the post I don't see why this is important. It there something about this information I might want to know about?

---

### Post by Scott O'Nanski on 2010-02-01
When I;

```
sudo modprobe it87
```

I get;

```
FATAL: Error inserting it87 (/lib/modules/2.6.31-17-generic/kernel/drivers/hwmon/it87.ko): Device or resource busy
```

when I;

```
sensors
```

I get;

```
acpitz-virtual-0
Adapter: Virtual device
temp1:       +40.0°C  (crit = +75.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +53.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +45.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +48.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +46.0°C  (high = +80.0°C, crit = +100.0°C)  

```

---

### Post by miegiel on 2010-02-03
> **Scott O'Nanski said:**
> Okay, you said to answer "yes" to all the "YES/no" questions. Are you implying that the "yes/NO" question at the end is to be answered "NO"?

I get this bounced back to me from the terminal:

```

#----cut here----
# I2C adapter drivers
# modprobe unknown adapter NVIDIA i2c adapter 
# modprobe unknown adapter NVIDIA i2c adapter 
# modprobe unknown adapter NVIDIA i2c adapter 
# modprobe unknown adapter NVIDIA i2c adapter 
# modprobe unknown adapter NVIDIA i2c adapter 
# modprobe unknown adapter NVIDIA i2c adapter 
# Chip drivers
# no driver for Analog Devices ADT7473 yet
it87
coretemp
#----cut here----

``` 

What am I being told here, what am I to do with it?

...
But *sudo sensors-detect* tells you ;)
> To load everything that is needed, **add this to /etc/modules**:

#----cut here----
# Chip drivers
coretemp
#----cut here----

Do you want to add these lines automatically? (yes/NO)

Choosing *yes* saves yo some trouble. To do it by hand, in a terminal, do :
```
sudo nano /etc/modules
```
And add _your_ sensors to the modules list (makes the modules load during boot up).

---

### Post by JeffPH on 2010-02-04
hi, 

after running sensors-detect i get the following :

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `coretemp':
  * Chip `Intel Atom thermal sensor' (confidence: 9)

Do you want to overwrite /etc/sysconfig/lm_sensors? (YES/no): y
Copy prog/init/lm_sensors.init to /etc/init.d/lm_sensors
for initialization at boot time.
You should now start the lm_sensors service to load the required
kernel modules.


i dont have the cut here thing :(  when i ran sensors i get this :
jeff@xbmc:~$ sensors
w83667hg-isa-fff8
Adapter: ISA adapter
VCore:        +2.04 V  (min =  +2.04 V, max =  +2.04 V)   ALARM
VIN0 +12V:   +13.46 V  (min = +13.46 V, max = +13.46 V)   ALARM
AVCC:         +4.08 V  (min =  +4.08 V, max =  +4.08 V)   ALARM
3VCC:         +4.08 V  (min =  +4.08 V, max =  +4.08 V)   ALARM
VIN2 +5V:     +6.12 V  (min =  +6.12 V, max =  +6.12 V)   ALARM
in6:          +2.04 V  (min =  +2.04 V, max =  +2.04 V)   ALARM
3VSB:         +4.08 V  (min =  +4.08 V, max =  +4.08 V)   ALARM
VBat:         +4.08 V  (min =  +4.08 V, max =  +4.08 V)   ALARM
CPU Fan:        0 RPM  (min =    0 RPM, div = 128)  ALARM
Case Fan:       0 RPM  (min =    0 RPM, div = 128)  ALARM
fan4:           0 RPM  (min =    0 RPM, div = 128)  ALARM
CHIPSET Temp:  -1.0°C  (high =  -1.0°C, hyst =  -1.0°C)  ALARM  sensor = diode
CPU1 Temp:     +0.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = diode
cpu0_vid:    +0.000 V

the temps are way off hehe  what should i do?

Am using a Foxconn nt-330i intel atom ion netbox. running ubuntu 9.10 karmic.

thanks for your help

---

### Post by AlmaTlust on 2010-02-05
the output of sensors is:
acpitz-virtual-0
Adapter: Virtual device
temp1:       +48.0°C  (crit = +91.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +48.0°C  (high = +85.0°C, crit = +85.0°C)

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +47.0°C  (high = +85.0°C, crit = +85.0°C)

that is too high, my computer shuts off when going over 80. I didn't find coretemp in my sensors.conf, so I don't know how to set high and critical temperatures
Can someone give me a hint? How would an entry for coretemp in sensors.conf look like?

---

### Post by AlexanderDGreat on 2010-02-27
Hi anyone, today is February 27 2010 - Does the tutorial on the first page still applicable ? I'm using Karmic 32 bit. Thanks. As you can see the first post was still Nov. 1, 2004.

---

### Post by miegiel on 2010-02-27
> **AlexanderDGreat said:**
> Hi anyone, today is February 27 2010 - Does the tutorial on the first page still applicable ? I'm using Karmic 32 bit. Thanks. As you can see the first post was still Nov. 1, 2004.

No, but you can still use it for inspiration.

You don't need to do any of the script stuff anymore. If you have brand new hardware lm-sensors can have a problem using a sensor in your hardware because it doesn't know the sensor yet. But in most cases it's just 4 easy steps.
[LIST=1]
[*]Install lm-sensors ```
sudo apt-get install lm-sensors
```
[*]Detect sensors ```
sudo sensors-detect
```
[*]Add the found sensors to */etc/modules* ```
sudo nano /etc/modules
```
[*]Reboot
[/LIST]

---

### Post by AlexanderDGreat on 2010-02-27
@miegel - Would you know if all these can be replaced by sudo apt-get install sensors-applet? And add the sensors in your panel? Thank you so much.

---

### Post by miegiel on 2010-02-27
> **AlexanderDGreat said:**
> @miegel - Would you know if all these can be replaced by sudo apt-get install sensors-applet? And add the sensors in your panel? Thank you so much.

Don't know, sorry :D I use lm-sensors to get cpu temps for [my conky]("http://ubuntuforums.org/showthread.php?p=8487787#post8487787").

---

### Post by AlexanderDGreat on 2010-02-27
That's alright. Big help already. Thanks.

---

### Post by TomyVk on 2010-03-05
all i got from sensors is this:

acpitz-virtual-0
Adapter: Virtual device
temp1:       +40.0°C  (crit = +95.0°C)                  

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +39.0°C                                    
Core0 Temp:  +45.0°C                                    
Core1 Temp:  +39.0°C                                    
Core1 Temp:  +41.0°C                                    

Any help?

---

### Post by miegiel on 2010-03-05
> **TomyVk said:**
> all i got from sensors is this:

acpitz-virtual-0
Adapter: Virtual device
temp1:       +40.0°C  (crit = +95.0°C)                  

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +39.0°C                                    
Core0 Temp:  +45.0°C                                    
Core1 Temp:  +39.0°C                                    
Core1 Temp:  +41.0°C                                    

Any help?

With [my k8]("http://ubuntuforums.org/showthread.php?p=7052866&highlight=k8temp#post7052866") I got my stuff from the motherboard sensor and ignored the *k8temp* sensor. But that was almost a year ago and that machine is kind of comatose. Things might have changed since then.

Did you run
```
sudo sensors-detect
```
and maybe post the output ...

---

### Post by TheKbob on 2010-03-30
```
This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): y
Probing for PCI bus adapters...
Found unknown SMBus adapter 8086:3b30 at 0000:00:1f.3.
Sorry, no supported PCI bus adapters found.

If you have undetectable or unsupported I2C/SMBus adapters, you can have
them scanned by manually loading the modules before running this script.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!
Do you want to scan the ISA I/O ports? (YES/no): y
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM78-J' at 0x290...     No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some Super I/O chips may also contain sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): y
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       Yes
Found unknown chip with ID 0xb353
    (logical device B has address 0x290, could be sensors)
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No

Some south bridges, CPUs or memory controllers may also contain
embedded sensors. Do you want to scan for them? (YES/no): y
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD K10 thermal sensors...                                  No
Intel Core family thermal sensor...                         No
Intel AMB FB-DIMM thermal sensor...                         No

Sorry, no sensors were detected.
Either your sensors are not supported, or they are connected to an
I2C or SMBus adapter that is not supported. See
[http://www.lm-sensors.org/wiki/FAQ/Chapter3](http://www.lm-sensors.org/wiki/FAQ/Chapter3) for further information.
If you find out what chips are on your board, check
[http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) for driver status.
```Hello, I'm using an Intel Core i5 CPU with an ASUS P7P55D motherboard, G.Skill RAM, and a 9800GTX+ nVidia Graphics card and I am getting no where with this program.  I'm curious if this is just because my hardware is too new for the application.

Thanks

---

### Post by Alfred Ux on 2010-04-05
Hi,
I have the same problem as the preceding post: when I put "sudo sensors-detect", I dont get a cut-here part, so I dont know how to alter /etc/modules.

I have a Dell Studio, Intel Core i7.

Any help is appreciated.
Alfred



for completeness, i get this:
> _________________________
$ sudo sensors-detect
# sensors-detect revision 5249 (2008-05-11 22:56:25 +0200)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): y
Probing for PCI bus adapters...
Found unknown SMBus adapter 8086:3b30 at 0000:00:1f.3.
Sorry, no supported PCI bus adapters found.

If you have undetectable or unsupported I2C/SMBus adapters, you can have
them scanned by manually loading the modules before running this script.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!
Do you want to scan the ISA I/O ports? (YES/no): y
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM78-J' at 0x290...     No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some Super I/O chips may also contain sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): y
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   Yes
Found unknown chip with ID 0x8502

Some south bridges, CPUs or memory controllers may also contain
embedded sensors. Do you want to scan for them? (YES/no): y
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD K10 thermal sensors...                                  No
Intel Core family thermal sensor...                         No
Intel AMB FB-DIMM thermal sensor...                         No

Sorry, no sensors were detected.
Either your sensors are not supported, or they are connected to an
I2C or SMBus adapter that is not supported. See
[http://www.lm-sensors.org/wiki/FAQ/Chapter3](http://www.lm-sensors.org/wiki/FAQ/Chapter3) for further information.
If you find out what chips are on your board, check
[http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) for driver status.

__________________
$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +26.8°C  (crit = +127.0°C)                  
temp2:       +52.0°C  (crit = +85.0°C)                  

______________
$ pwmconfig
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.

We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.

/usr/sbin/pwmconfig: No sensors found! (modprobe sensor modules?)

---

### Post by JoaoMachado on 2010-04-05
I have an HP G60, dual core intel 2.0GhZ. Running U10.4, I wiped Vista basic off of the map, desiccated Ubuntu install, the heat and fan noise generated makes the laptop almost unusable. I installed CPU throttling, seems to help a tat but it is annoying.
I have lm_sensors installed, coretemp module is running, don't know what elese to do but spend $150.00 for windows7!

Any ideas?
> joao@HP-G60:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +61.0°C  (crit = +103.0°C)                  
temp2:       +61.0°C  (crit = +120.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +32.0°C  (high = +105.0°C, crit = +105.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +29.0°C  (high = +105.0°C, crit = +105.0°C)  

joao@HP-G60:~$ 


Coretemp running:
> snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ath5k                 121824  0 
i915                  281950  3 
drm_kms_helper         29297  1 i915
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
coretemp                4289  0 
mac80211              204470  1 ath5k
ath                     7611  1 ath5k
drm                   162599  4 i915,drm_kms_helper
uvcvideo               56990  0 
intel_agp              24181  1 


Any ideas anyone?

---

### Post by miegiel on 2010-04-05
Regarding the core i5 and i7:
Lucid will be out in 4 weeks and comes with *sensors version 3.1.2* and *libsensors version 3.1.2*, which might have better core i5 and i7 support. There are always some bumps to iron out with the latest hardware.
```
sensors -v
```

---

### Post by JoaoMachado on 2010-04-05
> **miegiel said:**
> Regarding the core i5 and i7:
Lucid will be out in 4 weeks and comes with *sensors version 3.1.2* and *libsensors version 3.1.2*, which might have better core i5 and i7 support. There are always some bumps to iron out with the latest hardware.
```
sensors -v
```

Running 3.1.2...

---

### Post by miegiel on 2010-04-06
> **JoaoMachado said:**
> Running 3.1.2...

Hmmmm .... :-k

I read somewhere that someone solved his fan hyperactivity disorder by adding a acpi kernel parameter to the kernel line in grub.

---

### Post by JoaoMachado on 2010-04-06
Tried that a while back, broke my system, luckily I was able to fix it with the live CD. Thanks for your help anyway.

John

---

### Post by JoaoMachado on 2010-04-10
Well, I decided to try out Fedora 12 live cd...lo and behold it runs at normal temps even on the CD.

So I decided to reinstall Ubuntu Lucid Lynx from scratch ( I was running from one of the first Alpha releases) and ran through all of the updates and now no excessive heat is gone and everything works nice!

Joao

---

### Post by Brian031168 on 2010-05-17
Maybe I'm doing something wrong or it's just my system, Any Ideas?

# sensors-detect revision 5818 (2010-01-18 17:22:07 +0100)
# System: Dell Inc. Studio 1536
# Board: Dell Inc. 0M273C

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): YES
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           Success!
    (driver `k10temp')
Intel Core family thermal sensor...                         No
Intel Atom thermal sensor...                                No
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): YES
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   Yes
Found unknown chip with ID 0x8512

Some systems (mainly servers) implement IPMI, a set of common interfaces
through which system health data may be retrieved, amongst other things.
We first try to get the information from SMBIOS. If we don't find it
there, we have to read from arbitrary I/O ports to probe for such
interfaces. This is normally safe. Do you want to scan for IPMI
interfaces? (YES/no): YES
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (YES/no): YES
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): YES
Using driver `i2c-piix4' for device 0000:00:14.0: ATI Technologies Inc SB600/SB700/SB800 SMBus
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
Module i2c-dev loaded successfully.

Next adapter: SMBus PIIX4 adapter at 30c0 (i2c-0)
Do you want to scan it? (YES/no/selectively): YES
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No
Client found at address 0x52
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter:  (i2c-1)
Do you want to scan it? (YES/no/selectively): YES

Next adapter:  (i2c-2)
Do you want to scan it? (YES/no/selectively): YES
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter:  (i2c-3)
Do you want to scan it? (YES/no/selectively): YES

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `k10temp':
  * Chip `AMD Family 11h thermal sensors' (confidence: 9)

Warning: the required module k10temp is not currently installed
on your system. If it is built into the kernel then it's OK.
Otherwise, check [http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) for
driver availability.

No modules to load, skipping modules configuration.

Unloading i2c-dev... OK

---

### Post by miegiel on 2010-05-17
> **Brian031168 said:**
> Maybe I'm doing something wrong or it's just my system, Any Ideas?

```
# sensors-detect revision 5818 (2010-01-18 17:22:07 +0100)
# System: Dell Inc. Studio 1536
# Board: Dell Inc. 0M273C

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): YES
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           Success!
    (driver `k10temp')
Intel Core family thermal sensor...                         No
Intel Atom thermal sensor...                                No
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): YES
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   Yes
Found unknown chip with ID 0x8512

Some systems (mainly servers) implement IPMI, a set of common interfaces
through which system health data may be retrieved, amongst other things.
We first try to get the information from SMBIOS. If we don't find it
there, we have to read from arbitrary I/O ports to probe for such
interfaces. This is normally safe. Do you want to scan for IPMI
interfaces? (YES/no): YES
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (YES/no): YES
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): YES
Using driver `i2c-piix4' for device 0000:00:14.0: ATI Technologies Inc SB600/SB700/SB800 SMBus
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
Module i2c-dev loaded successfully.

Next adapter: SMBus PIIX4 adapter at 30c0 (i2c-0)
Do you want to scan it? (YES/no/selectively): YES
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No
Client found at address 0x52
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter:  (i2c-1)
Do you want to scan it? (YES/no/selectively): YES

Next adapter:  (i2c-2)
Do you want to scan it? (YES/no/selectively): YES
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter:  (i2c-3)
Do you want to scan it? (YES/no/selectively): YES

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `k10temp':
  * Chip `AMD Family 11h thermal sensors' (confidence: 9)

Warning: the required module k10temp is not currently installed
on your system. If it is built into the kernel then it's OK.
Otherwise, check [http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) for
driver availability.

No modules to load, skipping modules configuration.

Unloading i2c-dev... OK
```

In short: The *k10temp* sensor has been detected, but there is no *k10temp* module to load. For more search the thread for "k10temp", I'm sure it's discussed here (though you probably won't like what you'll find).

---

### Post by NCLI on 2010-05-27
It's very easy to install. Just follow [this guide]("http://blog.morrigan.ch/?p=9").

Anyway, is there a way to monitor the sensors remotely, like a widget for Gnome or Android?

---

### Post by DannyBiker on 2010-06-04
Okay, I'm getting real tired of Windows 7 on my machine. The OS is a great improvement but it is so slow when several applications are running, that I want to switch to Ubuntu once and for all. But....my computer is so noisy that it is barely usable without a software like speedfan that can easily regulate the CPU fanspeed.

Therefore, before I dive into this :
will lm-sensors will let me regulate the CPU speed fan whenever I want ? I don't want to go back in the console every time I want to decrease or increase the speed.
Is there a script or a interface making the operation easier ?

Thank you. If the question has already been asked, don't hesitate to answer me with a link...:)

---

### Post by Tass on 2010-06-05
Hi guys

I've got lm-sensors installed and working and I'm now trying to figure out what it all means.  I'm trying to wade through the 42 pages of this post as well as the lm-sensors documentation on their website, but I think I'm a little out of my depth here!  Here's my output:

it8718-isa-0228
Adapter: ISA adapter
in0:         +1.07 V  (min =  +0.00 V, max =  +4.08 V)   
in1:         +1.60 V  (min =  +0.00 V, max =  +4.08 V)   
in2:         +3.38 V  (min =  +0.00 V, max =  +4.08 V)   
in3:         +3.04 V  (min =  +0.00 V, max =  +4.08 V)   
in4:         +3.09 V  (min =  +0.00 V, max =  +4.08 V)   
in5:         +3.38 V  (min =  +0.00 V, max =  +4.08 V)   
in6:         +4.08 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
in7:         +2.30 V  (min =  +0.00 V, max =  +4.08 V)   
Vbat:        +3.18 V
fan1:       3214 RPM  (min =    0 RPM)
fan2:          0 RPM  (min =    0 RPM)
fan3:          0 RPM  (min =    0 RPM)
fan4:          0 RPM  (min =    0 RPM)
temp1:       +42.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:       +42.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermal diode
temp3:       +44.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
cpu0_vid:   +1.050 V


So now I'm trying to figure out what in6 is, why it's so high and if this means I need to re-evaluate my hardware setup?

Thanks,

Tass

---

### Post by DannyBiker on 2010-06-08
> **DannyBiker said:**
> Okay, I'm getting real tired of Windows 7 on my machine. The OS is a great improvement but it is so slow when several applications are running, that I want to switch to Ubuntu once and for all. But....my computer is so noisy that it is barely usable without a software like speedfan that can easily regulate the CPU fanspeed.

Therefore, before I dive into this :
will lm-sensors will let me regulate the CPU speed fan whenever I want ? I don't want to go back in the console every time I want to decrease or increase the speed.
Is there a script or a interface making the operation easier ?

Thank you. If the question has already been asked, don't hesitate to answer me with a link...:)


Okay, coming back here with more precise questions...
I just installed Ubuntu to test lm-sensors. First off, I'm impressed with the lower CPU fan speed that the system offers compared to Windows. It does get noisy when heavier applications are launched but it's almost tolerable in "surf mode".

Now, I just typed the "sudo sensors-detect" command in the terminal and this is what I got :

```
# sensors-detect revision 5818 (2010-01-18 17:22:07 +0100)
# System: ASUSTeK Computer INC. ATI-Xpress200
# Board: ASUSTeK Computer INC. P5R8L

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): y
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
Intel Core family thermal sensor...                         No
Intel Atom thermal sensor...                                No
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): y
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      Yes
Found `ITE IT8712F Super IO Sensors'                        Success!
    (address 0x228, driver `it87')
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No

Some systems (mainly servers) implement IPMI, a set of common interfaces
through which system health data may be retrieved, amongst other things.
We first try to get the information from SMBIOS. If we don't find it
there, we have to read from arbitrary I/O ports to probe for such
interfaces. This is normally safe. Do you want to scan for IPMI
interfaces? (YES/no): y
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (yes/NO): y
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): y
Using driver `i2c-piix4' for device 0000:00:14.0: ATI Technologies Inc IXP SB400 SMBus Controller
Module i2c-dev loaded successfully.

Next adapter: SMBus PIIX4 adapter at 0b00 (i2c-0)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No
Client found at address 0x51
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter:  (i2c-1)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter:  (i2c-2)
Do you want to scan it? (YES/no/selectively): y

Next adapter:  (i2c-3)
Do you want to scan it? (YES/no/selectively): y

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `it87':
  * ISA bus, address 0x228
    Chip `ITE IT8712F Super IO Sensors' (confidence: 9)

To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
it87
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!

Do you want to add these lines automatically to /etc/modules? (yes/NO)y
Successful!

Monitoring programs won't work until the needed modules are
loaded. You may want to run '/etc/init.d/module-init-tools start'
to load them.

Unloading i2c-dev... OK

```


And when typing sudo pwmconfig

```
# pwmconfig revision 5770 (2009-09-16)
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.

We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.

/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed

```


It doesn't seem to identify my CPU fan at all. Beside, when installing the sensors applet for the Gnome Panel, most of the sensors seems undetected (temperature stays at 40° while SpeedFan in Windows has a 55-65° average), no fanspeed, etc. The thing is : it did work in previous versions of Ubuntu (9.10, I'm pretty sure), with the exact same machine (nothing was changed since then). Why isn't it working now ?
I just want to be able to easily decrease or increase the CPU fan speed depending on the system's temperatures. That's the two variables I would like to see working !

I have an Asus Pundit P1-PH1, Intel Pentium D 2,66 GHZ, AsusTek P5RL8 motherboard, Ati Xpress 200 graphic card and a Western Digital Eco Green 1 To hard drive.

Thank you !:)

---

### Post by DannyBiker on 2010-06-08
I desactived the Q-Fan Control in the BIOS. Now, the sensors applet gives me the right variables (including the Fan). But sensors-detect and pwnconfig still gives me nothing...:confused:

---

### Post by DannyBiker on 2010-07-07
Okay, I'm back with my questions after a fresh install.
I managed to have my CPU fan detected, the one I want to be able to switch the speed depending on my computer temperature.

This is what I get with pwnconfig :
```
sudo pwmconfig
# pwmconfig revision 5770 (2009-09-16)
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.

We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.

Found the following devices:
   hwmon0 is acpitz
   hwmon1/device is it8712

Found the following PWM controls:
   hwmon1/device/pwm1
   hwmon1/device/pwm2
   hwmon1/device/pwm3

Giving the fans some time to reach full speed...
Found the following fan sensors:
   hwmon1/device/fan1_input     current speed: 4326 RPM

Warning!!! This program will stop your fans, one at a time,
for approximately 5 seconds each!!!
This may cause your processor temperature to rise!!!
If you do not want to do this hit control-C now!!!
Hit return to continue: 

Testing pwm control hwmon1/device/pwm1 ...
  hwmon1/device/fan1_input ... speed was 4326 now 0
    It appears that fan hwmon1/device/fan1_input
    is controlled by pwm hwmon1/device/pwm1
Would you like to generate a detailed correlation (y)? y
Note: If you had gnuplot installed, I could generate a graphical plot.
    PWM 255 FAN 4218
    PWM 240 FAN 4218
    PWM 225 FAN 4218
    PWM 210 FAN 4017
    PWM 195 FAN 3668
    PWM 180 FAN 3443
    PWM 165 FAN 3125
    PWM 150 FAN 2909
    PWM 135 FAN 2556
    PWM 120 FAN 2280
    PWM 105 FAN 1985
    PWM 90 FAN 1670
    PWM 75 FAN 1350
    PWM 60 FAN 986
    PWM 45 FAN 0
    Fan Stopped at PWM = 45


Testing pwm control hwmon1/device/pwm2 ...
  hwmon1/device/fan1_input ... speed was 4326 now 4326
    no correlation

No correlations were detected.
There is either no fan connected to the output of hwmon1/device/pwm2,
or the connected fan has no rpm-signal connected to one of
the tested fan sensors. (Note: not all motherboards have
the pwm outputs connected to the fan connectors,
check out the hardware database on http://www.almico.com/forumindex.php)

Did you see/hear a fan stopping during the above test (n)? n

Testing pwm control hwmon1/device/pwm3 ...
  hwmon1/device/fan1_input ... speed was 4326 now 4218
    no correlation

No correlations were detected.
There is either no fan connected to the output of hwmon1/device/pwm3,
or the connected fan has no rpm-signal connected to one of
the tested fan sensors. (Note: not all motherboards have
the pwm outputs connected to the fan connectors,
check out the hardware database on http://www.almico.com/forumindex.php)

Did you see/hear a fan stopping during the above test (n)? n

Testing is complete.
Please verify that all fans have returned to their normal speed.

The fancontrol script can automatically respond to temperature changes
of your system by changing fanspeeds.
Do you want to set up its configuration file now (y)? y
What should be the path to your fancontrol config file (/etc/fancontrol)? y

Select fan output to configure, or other action:
1) hwmon1/device/pwm1  3) Just quit	      5) Show configuration
2) Change INTERVAL     4) Save and quit

```

What should I do now to get speed fan control ? I don't understand how can I obtain that.

Thank you !

---

### Post by Confused Computer User on 2010-07-11
> **Tass said:**
> Hi guys

I've got lm-sensors installed and working and I'm now trying to figure out what it all means.  I'm trying to wade through the 42 pages of this post as well as the lm-sensors documentation on their website, but I think I'm a little out of my depth here!  Here's my output:

it8718-isa-0228
Adapter: ISA adapter
in0:         +1.07 V  (min =  +0.00 V, max =  +4.08 V)   
in1:         +1.60 V  (min =  +0.00 V, max =  +4.08 V)   
in2:         +3.38 V  (min =  +0.00 V, max =  +4.08 V)   
in3:         +3.04 V  (min =  +0.00 V, max =  +4.08 V)   
in4:         +3.09 V  (min =  +0.00 V, max =  +4.08 V)   
in5:         +3.38 V  (min =  +0.00 V, max =  +4.08 V)   
in6:         +4.08 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
in7:         +2.30 V  (min =  +0.00 V, max =  +4.08 V)   
Vbat:        +3.18 V
fan1:       3214 RPM  (min =    0 RPM)
fan2:          0 RPM  (min =    0 RPM)
fan3:          0 RPM  (min =    0 RPM)
fan4:          0 RPM  (min =    0 RPM)
temp1:       +42.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:       +42.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermal diode
temp3:       +44.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
cpu0_vid:   +1.050 V


So now I'm trying to figure out what in6 is, why it's so high and if this means I need to re-evaluate my hardware setup?

Thanks,

Tass

I have a simillar out put so I'm thinking I did something wrong in the setup. Myne is:

sensors
w83627thf-isa-0290
Adapter: ISA adapter
in0:         +1.57 V  (min =  +0.00 V, max =  +3.84 V)   
in1:         +3.15 V  (min =  +0.69 V, max =  +0.38 V)   ALARM
in2:         +3.25 V  (min =  +0.10 V, max =  +0.54 V)   ALARM
in3:         +2.99 V  (min =  +2.38 V, max =  +0.00 V)   ALARM
in4:         +2.51 V  (min =  +0.06 V, max =  +0.45 V)   ALARM
in7:         +2.96 V  (min =  +1.44 V, max =  +1.34 V)   ALARM
in8:         +3.20 V  (min =  +0.51 V, max =  +2.30 V)   ALARM
fan1:          0 RPM  (min = 10546 RPM, div = 128)  ALARM
fan2:       3183 RPM  (min = 21093 RPM, div = 2)  ALARM
fan3:          0 RPM  (min = 2109 RPM, div = 128)  ALARM
temp1:       +41.0°C  (high = -125.0°C, hyst = +40.0°C)  ALARM  sensor = thermistor
temp2:       +40.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
temp3:        +5.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
beep_enable:enabled


Any way someone can point me in the re=ight direction as to identefying what's what?

---

### Post by sfp100 on 2010-07-14
> **GepettoBR said:**
> Thanks for the howto, it worked!



Try making two separate commands (one for temp1 and one for temp6). Instead of piping them both through "grep temp", use "grep temp1" on one and "grep temp6" on the other.

EDIT: It's worth mentioning that you can also pipe the command through grep more than once.

You can do it on one pipe:
```
 sensors | grep temp[16] 
```[16] tell 'one char, 1 or 6'

---

### Post by Vimmander on 2010-08-02
Well, seeing as I already had lm-sensors installed by default, I tried to run it, thinking all the stuff was configured already and that I just had to run the YES/no stuff once.  That didn't work, so then I tried to do the walkthrough. I obtained the following output:
```

# sensors-detect revision 5818 (2010-01-18 17:22:07 +0100)
# System: Dell Inc. Inspiron 1501
# Board: Dell Inc. 0UW744

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): yes
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   Success!
    (driver `k8temp')
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
Intel Core family thermal sensor...                         No
Intel Atom thermal sensor...                                No
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): yes
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   Yes
Found `Nat. Semi. PC87591 Super IO'                         
    (address 0x200, but not activated)
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No

Some systems (mainly servers) implement IPMI, a set of common interfaces
through which system health data may be retrieved, amongst other things.
We first try to get the information from SMBIOS. If we don't find it
there, we have to read from arbitrary I/O ports to probe for such
interfaces. This is normally safe. Do you want to scan for IPMI
interfaces? (YES/no): yes
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (YES/no): yes
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): no
Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `k8temp' (autoloaded):
  * Chip `AMD K8 thermal sensors' (confidence: 9)

No modules to load, skipping modules configuration.

```I seem to have borked something here, since step 3 isn't supposed to spew this out when I run sensors-detect.  Is there some way to undo any changes or delete any files created by running "mkdev.sh", as well as delete anything made by running the YES/no sequence?  In effect, I want to totally undo any changes made by running this walkthrough.

---

### Post by amishaa on 2010-08-30
```
# sensors-detect revision 5818 (2010-01-18 17:22:07 +0100)
# System: TOSHIBA Satellite L500 (laptop)
# Board: TOSHIBA NSWAA

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): yes
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
Intel Core family thermal sensor...                         No
Intel Atom thermal sensor...                                No
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): yes
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No

Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (YES/no): yes
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): yes
Found unknown SMBus adapter 8086:3b30 at 0000:00:1f.3.
Sorry, no supported PCI bus adapters found.

Sorry, no sensors were detected.
This is relatively common on laptops, where thermal management is
handled by ACPI rather than the OS.

```Install lm-sensors and run sensors-detect. No sensors were detected.
What can i do?

---

### Post by Ray_GTI-R on 2010-09-12
Sorry to butt in ...
I have downloaded lm-sensors OK. I tried to run lm-sensors directly but failed ... more than once. After a few days (weeks? see Note, below.) I noticed that k-sensors had been installed. After a number of tries I can manually get k-sensors to work (see Note 2, Below) and it runs lm-sensors 100% perfectly functionally with 100% perfectly accurate readings. :)
My question:- how do I get k-sensors to start up automatically upon cold-boot/warm-boot?
I have tried various (non-expert Ubuntu/Linux user) methods... and failed.
TIA, Ray
(Note: My Ubuntu install is on a hardware testbench rig that is used infrequently, for proving various bits of kit as received ... hence the need for lm-sensors and the uncertainty of exact diary.)
(Note 2: How I get k-sensors to run, manually ...
Accessories
Terminal
"ksensors"
{wait for lm-sensors to complete initialising and display the results]
Exit)

---

### Post by petrasflorin on 2010-10-19
FATAL: Error inserting w83627ehf (/lib/modules/2.6.32-5-686/kernel/drivers/hwmon/w83627ehf.ko): Device or resource busy

---

### Post by warfie on 2010-10-22
it8718-isa-0228
Adapter: ISA adapter
in0:         +1.25 V  (min =  +0.00 V, max =  +4.08 V)   
in1:         +1.95 V  (min =  +0.00 V, max =  +4.08 V)   
in2:         +3.20 V  (min =  +0.00 V, max =  +4.08 V)   
in3:         +2.82 V  (min =  +0.00 V, max =  +4.08 V)   
in4:         +2.90 V  (min =  +0.00 V, max =  +4.08 V)   
in5:         +3.10 V  (min =  +0.00 V, max =  +4.08 V)   
in6:         +4.08 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
in7:         +3.22 V  (min =  +0.00 V, max =  +4.08 V)   
Vbat:        +3.38 V
fan1:          0 RPM  (min =    0 RPM)
fan2:       1726 RPM  (min =    0 RPM)
fan3:          0 RPM  (min =    0 RPM)
temp1:       +43.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:       +42.0°C  (low  = +127.0°C, high = +80.0°C)  sensor = thermal diode
temp3:       +90.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
cpu0_vid:   +1.250 V



errrr.... any idea what "Temp1, Temp2, Temp3" are? which is the CPU? and what the heck could be running at 90°C?!?! :eek:
Could it really be that there is no 12v line? and no -5v?

Looks a little strange to me...

Cheers!

---

### Post by AttilaSVK on 2011-04-23
Hi all!

Yesterday I put together a small server with a Gigabyte H67M-D2-B3 motherboard and a Core i3 2100 CPU running 32-bit Ubuntu Server 10.10. Everything works flawlessly, I have only problem with lm-sensors, more particularly I cannot load the it87 module.

If I execute the ```
modprobe it87
``` command, this is what I get:

```
FATAL: Error inserting it87 (/lib/modules/2.6.35-28-generic-pae/kernel/drivers/hwmon/it87.ko): No such device

```

When I did ```
sensors-detect
``` the script that came with Ubuntu didn't find anything, so I downloaded the newest script which detected the CPU thermal diode (coretemp) and a ITE IT8728F Super IO Sensors, which needs the module it87.

I tried to google around, but after almost two hours of searching, I couldn't find anything.
Anyone with an idea?

PS: excuse me if I didn't post this to the correct topic - I'm new here.

---

### Post by miegiel on 2011-04-23
> **AttilaSVK said:**
> Hi all!

Yesterday I put together a small server with a Gigabyte H67M-D2-B3 motherboard and a Core i3 2100 CPU running 32-bit Ubuntu Server 10.10. Everything works flawlessly, I have only problem with lm-sensors, more particularly I cannot load the it87 module.

If I execute the ```
modprobe it87
``` command, this is what I get:

```
FATAL: Error inserting it87 (/lib/modules/2.6.35-28-generic-pae/kernel/drivers/hwmon/it87.ko): No such device

```

When I did ```
sensors-detect
``` the script that came with Ubuntu didn't find anything, so I downloaded the newest script which detected the CPU thermal diode (coretemp) and a ITE IT8728F Super IO Sensors, which needs the module it87.

I tried to google around, but after almost two hours of searching, I couldn't find anything.
Anyone with an idea?

PS: excuse me if I didn't post this to the correct topic - I'm new here.

Welcome to ubuntuforums :D

For intel CPUs the *coretemp* should get the CPU temps.

I didn't take a good look at your motherboard, but if the chips on the motherboard are relatively new (or new revisions) it's possible that the linux modules/drivers only support essential functions yet. Maybe ubuntu 11.04 (to be released this month) will bring relief. Often _full_ hardware support lags behind what you've been used to in windows (blame the manufacturers).

---

### Post by AttilaSVK on 2011-04-24
> **miegiel said:**
> Welcome to ubuntuforums :D

For intel CPUs the *coretemp* should get the CPU temps.

I didn't take a good look at your motherboard, but if the chips on the motherboard are relatively new (or new revisions) it's possible that the linux modules/drivers only support essential functions yet. Maybe ubuntu 11.04 (to be released this month) will bring relief. Often _full_ hardware support lags behind what you've been used to in windows (blame the manufacturers).

All right, it's not a big deal. For now it's enough to be able to check the CPU temp, because I'm a little bit paranoid about the system health, as I used to have a Dell PowerEdge 1550 server with two P3s (running Karmic Koala btw) which kept on shutting down because of overheating on hot summer days :D

---

### Post by papampi on 2011-05-04
Thanks for the great tut !
it seems I have my sensors running ok !
```
payam@payam-ubuntu:~$ sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:     +1.24 V  (min =  +0.85 V, max =  +1.60 V)
 +3.3 Voltage:     +3.28 V  (min =  +2.97 V, max =  +3.63 V)
 +5 Voltage:       +5.09 V  (min =  +4.50 V, max =  +5.50 V)
 +12 Voltage:     +12.25 V  (min = +10.20 V, max = +13.80 V)
CPU FAN Speed:    1163 RPM  (min =  600 RPM)
CHASSIS FAN Speed:   0 RPM  (min =  800 RPM)
CPU Temperature:   +41.0°C  (high = +60.0°C, crit = +95.0°C)  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +60.0°C  (high = +86.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +60.0°C  (high = +86.0°C, crit = +100.0°C)  

```

but the conky show my cpu temp 0 
any idea ?

---

### Post by miegiel on 2011-05-06
> **papampi said:**
> Thanks for the great tut !
it seems I have my sensors running ok !
```
payam@payam-ubuntu:~$ sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:     +1.24 V  (min =  +0.85 V, max =  +1.60 V)
 +3.3 Voltage:     +3.28 V  (min =  +2.97 V, max =  +3.63 V)
 +5 Voltage:       +5.09 V  (min =  +4.50 V, max =  +5.50 V)
 +12 Voltage:     +12.25 V  (min = +10.20 V, max = +13.80 V)
CPU FAN Speed:    1163 RPM  (min =  600 RPM)
CHASSIS FAN Speed:   0 RPM  (min =  800 RPM)
CPU Temperature:   +41.0°C  (high = +60.0°C, crit = +95.0°C)  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +60.0°C  (high = +86.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +60.0°C  (high = +86.0°C, crit = +100.0°C)  

```

but the conky show my cpu temp 0 
any idea ?

I use 
```
${hwmon 1 temp 1}
```
in my conky. The first 1 is the number of the sensor (counting starts at 0), you have 3 sensors. The second 1 is is the number of the temperature "reading", some sensors read more than 1 temperature (counting starts at 1).

Here's my *sensors* output. I read my temp from the red sensor.

```
acpitz-virtual-0
Adapter: Virtual device
temp1:       +54.0°C  (crit = +96.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
[COLOR="Red"]Core 0:      +47.0°C  (crit = +100.0°C)                  
[/COLOR]
eeepc-isa-0000
Adapter: ISA adapter
fan1:       3926 RPM
```
Make sure you're not using a bogus sensor. Just because *lm-sensors* finds a sensor that puts out a temperature doesn't mean it's actually reading a temperature. Some sensors are just not connected.

This is a [better thread]("http://ubuntuforums.org/showthread.php?t=281865") for asking conky questions (and conky inspiration).

---

### Post by Icche Ghuri on 2011-05-07
> **papampi said:**
> but the conky show my cpu temp 0 any idea ?

Run this command in your terminal,
```
sensors | grep -A 0 'Core 0' | cut -c1-23
```
you'll get similar result like this,
```
Core 0:      +47.0°C
```
So, add this two lines(for tow cpu cores) in your conkyrc
```
CPU 0: ${execi 2 sensors | grep -A 0 'Core 0' | cut -c15-23}
CPU 1: ${execi 2 sensors | grep -A 0 'Core 1' | cut -c15-23}
```
you'll get result like this on your conky wall,
```
CPU 0: 48.0°C
CPU 1: 48.0°C
```

---

### Post by miegiel on 2011-05-07
> **Icche Ghuri said:**
> Run this command in your terminal,
```
sensors | grep -A 0 'Core 0' | cut -c1-23
```
you'll get similar result like this,
```
Core 0:      +47.0°C
```
So, add this two lines(for tow cpu cores) in your conkyrc
```
CPU 0: ${execi 2 sensors | grep -A 0 'Core 0' | cut -c15-23}
CPU 1: ${execi 2 sensors | grep -A 0 'Core 1' | cut -c15-23}
```
you'll get result like this on your conky wall,
```
CPU 0: 48.0°C
CPU 1: 48.0°C
```

Using *${execi ..}* to *grep* and *cut* info from *sensors* is a resource hog compared to using *${hwmon ...}*.

Besides, how do you know he should use the *coretemp-isa-0000* and *coretemp-isa-0001* sensors and not the *atk0110-acpi-0* sensor? From here I can't know which sensor puts out BS and which is accurate. :-k

---

### Post by geazzy on 2011-05-10
great tutorial....
I will try it :)

---

### Post by xMohd on 2011-05-28
I give up. Been at it for sometime now. I could pay for anyone to fix this mess. I need my workstation to shut the hell up before it drives me crazy. With windows it runs super silent. The minute I reboot Ubuntu it gets really loud. I've followed several tutorials & methods but no use. Attached is screen shot of my xsensor readings & lm-sensor info.

---

### Post by miegiel on 2011-05-29
> **xMohd said:**
> I give up. Been at it for sometime now. I could pay for anyone to fix this mess. I need my workstation to shut the hell up before it drives me crazy. With windows it runs super silent. The minute I reboot Ubuntu it gets really loud. I've followed several tutorials & methods but no use. Attached is screen shot of my xsensor readings & lm-sensor info.

It seems like you're reading your motherboard sensor twice, though that is not necessarily the cause of the fan noise.

Post the contents of your */etc/modules* file and the full output when you run *sensors-detect*.

And post it in code boxes please, instead of using screenshots.
```
code box
```

---

### Post by xMohd on 2011-05-29
thanks for reply

this is when I run sensors


```
w83627hf-isa-0290
Adapter: ISA adapter
in0:         +3.49 V  (min =  +0.00 V, max =  +4.08 V)   
in1:         +3.50 V  (min =  +0.00 V, max =  +4.08 V)   
in2:         +3.49 V  (min =  +2.82 V, max =  +3.79 V)   
in3:         +3.02 V  (min =  +0.77 V, max =  +0.59 V)   ALARM
in4:         +3.02 V  (min =  +1.17 V, max =  +3.38 V)   
in5:         +3.04 V  (min =  +1.34 V, max =  +0.61 V)   ALARM
in6:         +3.06 V  (min =  +0.58 V, max =  +3.58 V)   
in7:         +3.36 V  (min =  +0.06 V, max =  +2.74 V)   ALARM
in8:         +3.30 V  (min =  +3.12 V, max =  +2.05 V)   ALARM
fan1:       4326 RPM  (min =  712 RPM, div = 8)
fan2:       4326 RPM  (min =  712 RPM, div = 8)
fan3:          0 RPM  (min = 2960 RPM, div = 8)  ALARM
temp1:       -43.0°C  (high = +27.0°C, hyst = +24.0°C)  sensor = thermistor
temp2:       -43.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
temp3:       -43.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
cpu0_vid:   +0.000 V
beep_enable:enabled

w83792d-i2c-0-2f
Adapter: SMBus I801 adapter at 1100
VcoreA:      +1.27 V  (min =  +0.00 V, max =  +2.04 V)   
VcoreB:      +1.32 V  (min =  +0.00 V, max =  +2.04 V)   
in2:         +3.28 V  (min =  +2.96 V, max =  +3.62 V)   
in3:         +2.92 V  (min =  +2.69 V, max =  +3.30 V)   
in4:         +0.52 V  (min =  +0.30 V, max =  +0.75 V)   
in5:         +3.05 V  (min =  +2.83 V, max =  +3.47 V)   
+5V:         +4.85 V  (min =  +4.49 V, max =  +5.50 V)   
5VSB:        +4.87 V  (min =  +4.49 V, max =  +5.50 V)   
Vbat:        +3.17 V  (min =  +2.69 V, max =  +3.30 V)   
fan1:          0 RPM  (min =  712 RPM, div = 8)  ALARM
fan2:          0 RPM  (min =  712 RPM, div = 8)  ALARM
fan3:          0 RPM  (min =  712 RPM, div = 8)  ALARM
fan4:          0 RPM  (min =  712 RPM, div = 8)  ALARM
fan5:       2445 RPM  (min =  712 RPM, div = 8)
fan6:       2678 RPM  (min =  712 RPM, div = 8)
temp1:       +35.0°C  (high = +75.0°C, hyst = +70.0°C)  
temp2:       +37.5°C  (high = +75.0°C, hyst = +70.0°C)  
temp3:       +32.0°C  (high = +80.0°C, hyst = +75.0°C) 
```

then i run sudo sensors-detect
i enter my password
answer yes to all questions
plz check the output /etc/modules

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp

# Generated by sensors-detect on Sat May 28 14:10:42 2011
# Adapter drivers
i2c_i801
ipmi-si
# Chip drivers
lm90
w83627hf
w83792d

# Generated by sensors-detect on Sat May 28 14:16:00 2011
# Adapter drivers
i2c_i801
ipmi-si
# Chip drivers
lm90
w83627hf
w83792d

# Generated by sensors-detect on Sun May 29 17:51:57 2011
# Adapter drivers
i2c_i801
ipmi-si
# Chip drivers
lm90
w83627hf
w83792d
```

---

### Post by miegiel on 2011-05-29
> **xMohd said:**
> thanks for reply

this is when I run sensors


```
w83627hf-isa-0290
Adapter: ISA adapter
in0:         +3.49 V  (min =  +0.00 V, max =  +4.08 V)   
in1:         +3.50 V  (min =  +0.00 V, max =  +4.08 V)   
in2:         +3.49 V  (min =  +2.82 V, max =  +3.79 V)   
in3:         +3.02 V  (min =  +0.77 V, max =  +0.59 V)   ALARM
in4:         +3.02 V  (min =  +1.17 V, max =  +3.38 V)   
in5:         +3.04 V  (min =  +1.34 V, max =  +0.61 V)   ALARM
in6:         +3.06 V  (min =  +0.58 V, max =  +3.58 V)   
in7:         +3.36 V  (min =  +0.06 V, max =  +2.74 V)   ALARM
in8:         +3.30 V  (min =  +3.12 V, max =  +2.05 V)   ALARM
fan1:       4326 RPM  (min =  712 RPM, div = 8)
fan2:       4326 RPM  (min =  712 RPM, div = 8)
fan3:          0 RPM  (min = 2960 RPM, div = 8)  ALARM
temp1:       -43.0°C  (high = +27.0°C, hyst = +24.0°C)  sensor = thermistor
temp2:       -43.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
temp3:       -43.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
cpu0_vid:   +0.000 V
beep_enable:enabled

w83792d-i2c-0-2f
Adapter: SMBus I801 adapter at 1100
VcoreA:      +1.27 V  (min =  +0.00 V, max =  +2.04 V)   
VcoreB:      +1.32 V  (min =  +0.00 V, max =  +2.04 V)   
in2:         +3.28 V  (min =  +2.96 V, max =  +3.62 V)   
in3:         +2.92 V  (min =  +2.69 V, max =  +3.30 V)   
in4:         +0.52 V  (min =  +0.30 V, max =  +0.75 V)   
in5:         +3.05 V  (min =  +2.83 V, max =  +3.47 V)   
+5V:         +4.85 V  (min =  +4.49 V, max =  +5.50 V)   
5VSB:        +4.87 V  (min =  +4.49 V, max =  +5.50 V)   
Vbat:        +3.17 V  (min =  +2.69 V, max =  +3.30 V)   
fan1:          0 RPM  (min =  712 RPM, div = 8)  ALARM
fan2:          0 RPM  (min =  712 RPM, div = 8)  ALARM
fan3:          0 RPM  (min =  712 RPM, div = 8)  ALARM
fan4:          0 RPM  (min =  712 RPM, div = 8)  ALARM
fan5:       2445 RPM  (min =  712 RPM, div = 8)
fan6:       2678 RPM  (min =  712 RPM, div = 8)
temp1:       +35.0°C  (high = +75.0°C, hyst = +70.0°C)  
temp2:       +37.5°C  (high = +75.0°C, hyst = +70.0°C)  
temp3:       +32.0°C  (high = +80.0°C, hyst = +75.0°C) 
```

then i run sudo sensors-detect
i enter my password
answer yes to all questions
plz check the output /etc/modules

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp

# Generated by sensors-detect on Sat May 28 14:10:42 2011
# Adapter drivers
i2c_i801
ipmi-si
# Chip drivers
lm90
w83627hf
w83792d

# Generated by sensors-detect on Sat May 28 14:16:00 2011
# Adapter drivers
i2c_i801
ipmi-si
# Chip drivers
lm90
w83627hf
w83792d

# Generated by sensors-detect on Sun May 29 17:51:57 2011
# Adapter drivers
i2c_i801
ipmi-si
# Chip drivers
lm90
w83627hf
w83792d
```

1st of all, your */etc/modules* file is a bit of a mess. Each time you answer YES to the _last_ question of *sensors-detect* the found sensors will be added to the */etc/modules* file, even if the sensor is listed in the file already. 

The second thing that doesn't seem to be right is that *sensors-detect* found 2 motherboard sensors, *w83627hf* and *w83792d*. Probably only 1 of the 2 found sensors is the right one.

When you run *sensors-detect*, after the detection process, you get a summary of the sensors that where found. Every sensor gets a "confidence" value (higher number == higher confidence). This can help you determine which of the 2 motherboard sensors *sensors-detect* found is the correct one. See example below.
```
... cut ...

Driver `coretemp':
  * Chip `Intel digital thermal sensor' **[COLOR="Red"](confidence: 9)[/COLOR]**

To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
coretemp
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!

Do you want to add these lines automatically to /etc/modules? (yes/NO)

Unloading i2c-dev... OK
Unloading cpuid... OK
```

To fix your */etc/modules* file open it in an editor as root:
```
gksudo gedit /etc/modules
```
and change it to something like:
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp

# Inspired by sensors-detect on Sun May 29 2011
# Adapter drivers
i2c_i801
ipmi-si
# Chip drivers
lm90
w83792d
```
I omitted the *w83627hf* sensor assuming the *w83792d* is the correct sensor.

That said, after cleaning up your */etc/modules* file you still might have fan noise issues. After all *lm-sensors* only reads the sensors and doesn't change the fan speed. There are fan controlling programs mentioned in this thread, but I've never had to use them and can't help you with those programs. Personally I control my fans from the [BIOS]("http://en.wikipedia.org/wiki/BIOS").

One last point: Linux often lags behind windows a little when it comes to supporting brand new hardware. If your motherboard/PC/laptop was introduced to the market less than 6 months ago it is likely that devs and bug-reporters are still working on making the hardware work as you would expect it to. My hot-from-the-factory laptop and linux didn't fall in love at first sight, their love grew a little every month and now they are inseparable. :D

---

### Post by xMohd on 2011-05-30
Dear miegiel, thanx alot for the info. am fairly new to Ubuntu world. Owe You 1 .. I've fixed my output/etc/modules & you were right, noise/fan issue is still on going. My machine is a 2006 BoxxTech. I'd assume it's not new. Bios already set to run (super quiet) but nothing it's certainly not when booting Ubuntu. Oh well I guess I have to live with this. thanx again.

---

### Post by akernan on 2011-10-10
I kinda got lm-senosors working.  I can't find my chipset in /etc/sensors3.conf.  I think it's Intel HM55.  I have an Inspiron 1564.  Here is the output from sensors.

```
acpitz-virtual-0
Adapter: Virtual device
temp1:        +26.8°C  (crit = +100.0°C)
temp2:         +0.0°C  (crit = +100.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +62.0°C  (high = +80.0°C, crit = +90.0°C)

coretemp-isa-0001
Adapter: ISA adapter
Core 2:       +64.0°C  (high = +80.0°C, crit = +90.0°C)


```

I'd like to get lm-sensors working correctly/fully.

---

### Post by miegiel on 2011-10-10
**@akernan** Did you run ```
sudo sensors-detect
``` in a terminal?

It should help you detect the correct sensor (pay attention to the *confidence* value when in doubt).

---

### Post by Little Blue on 2011-10-11
Hi, I recently installed a few updates on my lucid LTS box and now lm-sensors no longer works. I had a lot of trouble getting it working to begin with and now I'm extremely lost.

This is the output of sensors-detect using the default options:

```
# sensors-detect revision 5946 (2011-03-23 11:54:44 +0100)
# System: Packard Bell ixtreme M5800

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): 
Module cpuid loaded successfully.
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
AMD Family 12h and 14h thermal sensors...                   No
Intel digital thermal sensor...                             Success!
    (driver `coretemp')
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): 
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      Yes
Found `ITE IT8721F/IT8758E Super IO Sensors'                Success!
    (address 0xa10, driver `it87')
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No

Some systems (mainly servers) implement IPMI, a set of common interfaces
through which system health data may be retrieved, amongst other things.
We first try to get the information from SMBIOS. If we don't find it
there, we have to read from arbitrary I/O ports to probe for such
interfaces. This is normally safe. Do you want to scan for IPMI
interfaces? (YES/no): 
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (yes/NO): 

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): 
Using driver `i2c-i801' for device 0000:00:1f.3: Intel 3400/5 Series (PCH)
Module i2c-i801 loaded successfully.
Module i2c-dev loaded successfully.

Next adapter: SMBus I801 adapter at 0400 (i2c-0)
Do you want to scan it? (yes/NO/selectively): 

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `it87':
  * ISA bus, address 0xa10
    Chip `ITE IT8721F/IT8758E Super IO Sensors' (confidence: 9)

Driver `coretemp':
  * Chip `Intel digital thermal sensor' (confidence: 9)

Do you want to overwrite /etc/sysconfig/lm_sensors? (YES/no): 
Copy prog/init/lm_sensors.init to /etc/init.d/lm_sensors
for initialization at boot time.
You should now start the lm_sensors service to load the required
kernel modules.

Unloading i2c-dev... OK
Unloading i2c-i801... OK
Unloading cpuid... OK

```

I have copied files around as suggested as I would like to to start at boot. When a reboot didn't get things working I then tried to start the service manually, [FONT="Courier New"]service lm-sensors start[/FONT], but I get this error message: [FONT="Courier New"].: 39: Can't open /etc/init.d/functions[/FONT]. Looking in my /etc/init.d directory, there is no functions file!

[FONT="Courier New"]sensors[/FONT] just gives
```
acpitz-virtual-0
Adapter: Virtual device
temp1:        +30.0°C  (crit = +110.0°C)

```

which is a far cry from what it used to produce. I don't actually know what its attempting to measure there but it doesn't tally up with what the bios measurements are, whatever it is...

[FONT="Courier New"]/etc/modules[/FONT] contains
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
modprobe
modprobe

# For temperature sensing
coretemp
it87

```

I've been looking around and other scripts that have issues with a missing functions file tend to just comment an offending line out. Other times I've seen it get replaced with /lib/lsb/init-functions, which I do have. Is this the safest thing to do or is there some unmet dependency that hasn't been met / did I miss something?

Any help's appreciated, and if anyone needs any more info please let me know!

Cheers!

---

### Post by akernan on 2011-10-11
> **miegiel said:**
> **@akernan** Did you run ```
sudo sensors-detect
``` in a terminal?

It should help you detect the correct sensor (pay attention to the *confidence* value when in doubt).

Yes, I did.  Here's the output from sudo sensors-detect.

```
tony@tony-Inspiron-1564:~$ sudo sensors-detect
[sudo] password for tony: 
# sensors-detect revision 5984 (2011-07-10 21:22:53 +0200)
# System: Dell Inc. Inspiron 1564 (laptop)
# Board: Dell Inc. 08CNC9

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): 
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
AMD Family 12h and 14h thermal sensors...                   No
AMD Family 15h thermal sensors...                           No
AMD Family 15h power sensors...                             No
Intel digital thermal sensor...                             Success!
    (driver `coretemp')
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): 
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor/ITE'...               Yes
Found unknown chip with ID 0x8502

Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (YES/no): 
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): 
Using driver `i2c-i801' for device 0000:00:1f.3: Intel 3400/5 Series (PCH)

Next adapter: intel drm CRTDDC_A (i2c-0)
Do you want to scan it? (YES/no/selectively): 

Next adapter: intel drm LVDSDDC_C (i2c-1)
Do you want to scan it? (YES/no/selectively): 
Client found at address 0x28
Probing for `National Semiconductor LM78'...                No
Probing for `National Semiconductor LM79'...                No
Probing for `National Semiconductor LM80'...                No
Probing for `Winbond W83781D'...                            No
Probing for `Winbond W83782D'...                            No
Probing for `Winbond W83627HF'...                           No
Probing for `Winbond W83627EHF'...                          No
Probing for `Winbond W83627DHG/W83667HG/W83677HG'...        No
Probing for `Asus AS99127F (rev.1)'...                      No
Probing for `Asus AS99127F (rev.2)'...                      No
Probing for `Asus ASB100 Bach'...                           No
Probing for `Analog Devices ADM1029'...                     No
Probing for `ITE IT8712F'...                                No
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter: intel drm HDMIB (i2c-2)
Do you want to scan it? (YES/no/selectively): 

Next adapter: DPDDC-B (i2c-3)
Do you want to scan it? (YES/no/selectively): 

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `coretemp':
  * Chip `Intel digital thermal sensor' (confidence: 9)

Do you want to overwrite /etc/sysconfig/lm_sensors? (YES/no): n
To load everything that is needed, add this to one of the system
initialization scripts (e.g. /etc/rc.d/rc.local):

#----cut here----
# Chip drivers
modprobe coretemp
/usr/bin/sensors -s
#----cut here----

If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones! You really
should try these commands right now to make sure everything is
working properly. Monitoring programs won't work until the needed
modules are loaded.

tony@tony-Inspiron-1564:~$ sudo modprobe coretemp
tony@tony-Inspiron-1564:~$ sensors -s
tony@tony-Inspiron-1564:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +26.8°C  (crit = +100.0°C)
temp2:         +0.0°C  (crit = +100.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +60.0°C  (high = +80.0°C, crit = +90.0°C)

coretemp-isa-0001
Adapter: ISA adapter
Core 2:       +62.0°C  (high = +80.0°C, crit = +90.0°C)


```

Here's my /etc/module

```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc

#lm-sensors & i2c

cpuid
i2c-i801
i2c-dev
coretemp

```

---

### Post by akernan on 2011-10-13
Any ideas?

---

### Post by miegiel on 2011-10-16
> **akernan said:**
> Any ideas?

Try changing your */etc/modules* to :
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc

#lm-sensors & i2c

modprobe coretemp
/usr/bin/sensors -s

[COLOR="Red"]#[/COLOR]cpuid
[COLOR="Red"]#[/COLOR]i2c-i801
[COLOR="Red"]#[/COLOR]i2c-dev
#coretemp
```
If that helps you can try removing the red [COLOR="Red"]#[/COLOR]'s one by one.

---

### Post by miegiel on 2011-10-16
> **Little Blue said:**
> Hi, I recently installed a few updates on my lucid LTS box and now lm-sensors no longer works. I had a lot of trouble getting it working to begin with and now I'm extremely lost.

This is the output of sensors-detect using the default options:

```
# sensors-detect revision 5946 (2011-03-23 11:54:44 +0100)
# System: Packard Bell ixtreme M5800

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): 
Module cpuid loaded successfully.
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
AMD Family 12h and 14h thermal sensors...                   No
Intel digital thermal sensor...                             Success!
    (driver `coretemp')
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): 
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      Yes
Found `ITE IT8721F/IT8758E Super IO Sensors'                Success!
    (address 0xa10, driver `it87')
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No

Some systems (mainly servers) implement IPMI, a set of common interfaces
through which system health data may be retrieved, amongst other things.
We first try to get the information from SMBIOS. If we don't find it
there, we have to read from arbitrary I/O ports to probe for such
interfaces. This is normally safe. Do you want to scan for IPMI
interfaces? (YES/no): 
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (yes/NO): 

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): 
Using driver `i2c-i801' for device 0000:00:1f.3: Intel 3400/5 Series (PCH)
Module i2c-i801 loaded successfully.
Module i2c-dev loaded successfully.

Next adapter: SMBus I801 adapter at 0400 (i2c-0)
Do you want to scan it? (yes/NO/selectively): 

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `it87':
  * ISA bus, address 0xa10
    Chip `ITE IT8721F/IT8758E Super IO Sensors' (confidence: 9)

Driver `coretemp':
  * Chip `Intel digital thermal sensor' (confidence: 9)

Do you want to overwrite /etc/sysconfig/lm_sensors? (YES/no): 
Copy prog/init/lm_sensors.init to /etc/init.d/lm_sensors
for initialization at boot time.
You should now start the lm_sensors service to load the required
kernel modules.

Unloading i2c-dev... OK
Unloading i2c-i801... OK
Unloading cpuid... OK

```

I have copied files around as suggested as I would like to to start at boot. When a reboot didn't get things working I then tried to start the service manually, [FONT="Courier New"]service lm-sensors start[/FONT], but I get this error message: [FONT="Courier New"].: 39: Can't open /etc/init.d/functions[/FONT]. Looking in my /etc/init.d directory, there is no functions file!

[FONT="Courier New"]sensors[/FONT] just gives
```
acpitz-virtual-0
Adapter: Virtual device
temp1:        +30.0°C  (crit = +110.0°C)

```

which is a far cry from what it used to produce. I don't actually know what its attempting to measure there but it doesn't tally up with what the bios measurements are, whatever it is...

[FONT="Courier New"]/etc/modules[/FONT] contains
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
modprobe
modprobe

# For temperature sensing
coretemp
it87

```

I've been looking around and other scripts that have issues with a missing functions file tend to just comment an offending line out. Other times I've seen it get replaced with /lib/lsb/init-functions, which I do have. Is this the safest thing to do or is there some unmet dependency that hasn't been met / did I miss something?

Any help's appreciated, and if anyone needs any more info please let me know!

Cheers!

See what happens if you remove 1 of the *modprobe* lines */etc/modules*. I know no sane reason to have it in there twice, though your problem might be caused by something else.

---

### Post by akernan on 2011-10-16
> **miegiel said:**
> Try changing your */etc/modules* to :
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc

#lm-sensors & i2c

modprobe coretemp
/usr/bin/sensors -s

[COLOR="Red"]#[/COLOR]cpuid
[COLOR="Red"]#[/COLOR]i2c-i801
[COLOR="Red"]#[/COLOR]i2c-dev
#coretemp
```
If that helps you can try removing the red [COLOR="Red"]#[/COLOR]'s one by one.

This did not help, coretemp would not load.

---

### Post by Little Blue on 2011-10-16
> **miegiel said:**
> See what happens if you remove 1 of the *modprobe* lines */etc/modules*. I know no sane reason to have it in there twice, though your problem might be caused by something else.

Cheers, I dunno how that happened, makes no sense... Ultimately though, didn't help... I still get that error when I try to start the service...
```
blue@ruby:~$ sudo service lm-sensors start
.: 39: Can't open /etc/init.d/functions
```

---

### Post by miegiel on 2011-10-16
**@Little Blue**
Do you remember if you installed *lm-sensors* from the ubuntu repository or compiled it from the [http://www.lm-sensors.org](http://www.lm-sensors.org) source?

AFAIK */etc/init.d/functions* shouldn't exist in ubuntu, but the source code from lm-sensors.org might expect it to exist. There is also a naming issue, ubuntu (and debian) use *lm-sensors*, while lm-sensors.org uses *lm_sensors* (note the - and _). This might cause problems updating related packages.

**@akernan**
Did you install/upgrade to 11.10 yet? If so/not, consider doing a clean install instead of upgrading. It might solve your problems, but remember to backup the important stuff (or everything) in your home first.

---

### Post by akernan on 2011-10-16
> **miegiel said:**
> **@Little Blue**
Do you remember if you installed *lm-sensors* from the ubuntu repository or compiled it from the [http://www.lm-sensors.org](http://www.lm-sensors.org) source?

AFAIK */etc/init.d/functions* shouldn't exist in ubuntu, but the source code from lm-sensors.org might expect it to exist. There is also a naming issue, ubuntu (and debian) use *lm-sensors*, while lm-sensors.org uses *lm_sensors* (note the - and _). This might cause problems updating related packages.

**@akernan**
Did you install/upgrade to 11.10 yet? If so/not, consider doing a clean install instead of upgrading. It might solve your problems, but remember to backup the important stuff (or everything) in your home first.

I didn't update to 11.10 yet, still on 10.10.  I installed lm-sensor from the repo and got a newer version from lm-sensor.org site.

---

### Post by miegiel on 2011-10-16
> **akernan said:**
> I didn't update to 11.10 yet, still on 10.10.  I installed lm-sensor from the repo and got a newer version from lm-sensor.org site.

That might be causing your problems too then. [s]IIRC *lm-sensors* is installed in ubuntu by default now. So you only need to run[/s] ```
sudo sensors-detect
``` [s]and you're done.[/s] Note that the how-to in the first post is from October 2004, you should use it for inspiration only. ;) And if you do want to compile it from source, I suspect you should uninstall (or even purge) the *lm-sensors* from the repo first.

But it's time for you to move on to 11.10. Since 10.10 is not a LTS release you will only get updates for a year after it's release (October 2010).

---

### Post by markdark20 on 2011-10-17
Please help me, this is my output :

themoon@Marksman:~$ **sudo sensors-detect** #YES for all Y/N question
> 
# sensors-detect revision 5984 (2011-07-10 21:22:53 +0200)
# Board: Intel Corporation DG31GL

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): YES              
Module cpuid loaded successfully.
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
AMD Family 12h and 14h thermal sensors...                   No
AMD Family 15h thermal sensors...                           No
AMD Family 15h power sensors...                             No
Intel digital thermal sensor...                             Success!
    (driver `coretemp')
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): YES
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               Yes
Found `Winbond W83627DHG Super IO Sensors'                  Success!
    (address 0x290, driver `w83627ehf')
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No

Some systems (mainly servers) implement IPMI, a set of common interfaces
through which system health data may be retrieved, amongst other things.
We first try to get the information from SMBIOS. If we don't find it
there, we have to read from arbitrary I/O ports to probe for such
interfaces. This is normally safe. Do you want to scan for IPMI
interfaces? (YES/no): YES
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (yes/NO): YES
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): YES
Using driver `i2c-i801' for device 0000:00:1f.3: Intel 82801G ICH7
Module i2c-i801 loaded successfully.
Module i2c-dev loaded successfully.

Next adapter: i915 gmbus disabled (i2c-0)
Do you want to scan it? (YES/no/selectively): YES

Next adapter: i915 gmbus ssc (i2c-1)
Do you want to scan it? (YES/no/selectively): YES

Next adapter: i915 GPIOB (i2c-2)
Do you want to scan it? (YES/no/selectively): YES

Next adapter: i915 gmbus vga (i2c-3)
Do you want to scan it? (YES/no/selectively): YES
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                No

Next adapter: i915 GPIOA (i2c-4)
Do you want to scan it? (YES/no/selectively): YES
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                No

Next adapter: i915 gmbus panel (i2c-5)
Do you want to scan it? (YES/no/selectively): YES

Next adapter: i915 GPIOC (i2c-6)
Do you want to scan it? (YES/no/selectively): YES

Next adapter: i915 gmbus dpc (i2c-7)
Do you want to scan it? (YES/no/selectively): YES

Next adapter: i915 GPIOD (i2c-8)
Do you want to scan it? (YES/no/selectively): YES

Next adapter: i915 gmbus dpb (i2c-9)
Do you want to scan it? (YES/no/selectively): YES

Next adapter: i915 GPIOE (i2c-10)
Do you want to scan it? (YES/no/selectively): YES

Next adapter: i915 gmbus reserved (i2c-11)
Do you want to scan it? (YES/no/selectively): YES

Next adapter: i915 gmbus dpd (i2c-12)
Do you want to scan it? (YES/no/selectively): YES

Next adapter: i915 GPIOF (i2c-13)
Do you want to scan it? (YES/no/selectively): YES

Next adapter: SMBus I801 adapter at f000 (i2c-14)
Do you want to scan it? (yes/NO/selectively): YES
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `w83627ehf':
  * ISA bus, address 0x290
    Chip `Winbond W83627DHG Super IO Sensors' (confidence: 9)

Driver `coretemp':
  * Chip `Intel digital thermal sensor' (confidence: 9)

Do you want to overwrite /etc/sysconfig/lm_sensors? (YES/no): YES
Copy prog/init/lm_sensors.init to /etc/init.d/lm_sensors
for initialization at boot time.
You should now start the lm_sensors service to load the required
kernel modules.

Unloading i2c-dev... OK
Unloading i2c-i801... OK
Unloading cpuid... OKWhat am I to do in next step ?

This is my /etc/modules :

> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

psmouse
mousedev
ide-cd
ide-disk
ide-generic
lp

#For lm-sensors, i2c modules
it87
i2c-viapro
i2c-isa

     but Ican not run  /etc/init.d/module-init-tools, it shows:
Usage: /etc/init.d/module-init-tools COMMAND
     
     my /etc/modprobe.d/local:
> alias char-major-89 i2c-devBut when i run update-modules, it shows:
update-modules: command not found

I tried 
**sudo modprobe i2c-sensor**

> WARNING: All config files need .conf: /etc/modprobe.d/local, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/aliases, it will be ignored in a future release.
FATAL: Module i2c_sensor not found.the same for 
[B]sudo modprobe i2c-viapro
     sudo modprobe i2c-isa
     sudo modprobe it87[/B]


themoon@Marksman:~$ **sensors**
> No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.How can I fix this :confused:
Iam using Ubuntu oneiric

---

### Post by Little Blue on 2011-10-17
> **miegiel said:**
> **@Little Blue**
Do you remember if you installed *lm-sensors* from the ubuntu repository or compiled it from the [http://www.lm-sensors.org](http://www.lm-sensors.org) source?

AFAIK */etc/init.d/functions* shouldn't exist in ubuntu, but the source code from lm-sensors.org might expect it to exist. There is also a naming issue, ubuntu (and debian) use *lm-sensors*, while lm-sensors.org uses *lm_sensors* (note the - and _). This might cause problems updating related packages.


It was a bit of both. Tried the repo version but that didn't recognise my sensors (it was a fairly new setup at the time), and went to lm-sensors.org to see if there was anything there that hadn't filtered down into the repos yet. I compiled it from there and eventually I'd managed to coax it into working, which its now stopped.

I'm going to guess then the best thing to do is try and purge my system of all this stuff and reinstall from the repos to see if they now work? I guess sudo aptitude remove lm-sensors --purge will uninstall anything added by the repos but removing the stuff I compiled?

Thanks for your help :)

---

### Post by miegiel on 2011-10-17
**@markdark**

First of all: Welcome to ubuntuforums.

No offense, but if you post stuff from the terminal please put it in a code box (the **#** button in the post editor) instead of using quote boxes. It keeps the posts smaller and prevents smilies. ;)
```
code box :)
```

That said, it seems you're also using a self compiled *lm-sensors*. A lot has happened since October 2004 and unless your hardware is so new that the *lm-sensors* in the ubuntu repository doesn't support the sensor chips in your machine yet, there is no need to compile the *lm-sensors* from [http://www.lm-sensors.org/](http://www.lm-sensors.org/)


I just installed a fresh _u_buntu 11.10 and all I neded to do was:

1: Open a terminal and do ```
sudo apt-get install lm-sensors
```
2: Do ```
sudo sensors-detect
``` Unless you have run *sudo sensors-detect* before, answer all questions with "yes" (default for all but the last question).

3: Do ```
sudo service module-init-tools start
``` or reboot (both have the same effect).

4: Do ```
sensors
``` and you'll see the output of the sensors that have been found on your machine.


If at step 2 you answered the last question with "no", you'll need to ad the sensors *sensors-detect* found to */etc/modules* manually. Open */etc/modules* in an editor
```
gksudo gedit /etc/modules
```
and copy+paste what *sensors-detect* found for you (between the *#----cut here----* lines).



> **Little Blue said:**
> It was a bit of both. Tried the repo version but that didn't recognise my sensors (it was a fairly new setup at the time), and went to lm-sensors.org to see if there was anything there that hadn't filtered down into the repos yet. I compiled it from there and eventually I'd managed to coax it into working, which its now stopped.

I'm going to guess then the best thing to do is try and purge my system of all this stuff and reinstall from the repos to see if they now work? I guess sudo aptitude remove lm-sensors --purge will uninstall anything added by the repos but removing the stuff I compiled?

Thanks for your help :)

That's what I'd do. I rarely compile stuff and can't remember uninstalling something I complied, ever. But if I'd have to, I'd try using *synaptic*.

---

### Post by Little Blue on 2011-10-17
> **miegiel said:**
> 
That's what I'd do. I rarely compile stuff and can't remember uninstalling something I complied, ever. But if I'd have to, I'd try using *synaptic*.
Cheers. It turns out the lm-sensors in the lucid repos must be still quite out of date, the sensors-detect it installs is old and doesn't detect any sensors... This leaves me back to trying to install the current version (after purging the repos one) from source which has this issue in it.

Interestingly if I compile it and then install the repo on top (undoubtedly not a safe way to go about things), it stops complaining when I try to start the service and gives the impression that it's working! Doing [FONT="Courier New"]sensors[/FONT] tells me its not... Also, when I try to see if modprobe will actually work for my sensors sets, coretemp and it87 (e.g., sudo modprobe coretemp), I get this error: ```
FATAL: Error inserting coretemp (/lib/modules/2.6.32-34-generic/kernel/drivers/hwmon/coretemp.ko): No such device
```

Unless there's any sudden flashes of inspiration or there's a really simple fix knocking about somewhere we've overlooked, this is the point where I decide that being able to monitor temps, especially now that summer's well and truly over, is probably not that important in the grand scheme of things and that I can wait until the next LTS to see if I can get a working lm-sensors!

Thanks a bunch for your help miegiel, I really appreciate it!

---

### Post by markdark20 on 2011-10-17
Thank** [miegiel]("http://ubuntuforums.org/member.php?u=514319")  **:)
I'm sorry for my first post :D
I was tried again as you said and now it works like a charm ^^
Thanks so much ^^ (sorry, my Einglish is bad)

---

### Post by karmila on 2011-10-18
> **miegiel said:**
> I just installed a fresh _u_buntu 11.10 and all I neded to do was:


Hi miegiel,

Thanks for this post. It really helped me :)

---

### Post by It_s_Real on 2011-12-23
Hello all!8-)
I installed Ubuntu Server 11.10 64 bit, of HP Proliant DL 380 G4.

root@Server2:~# sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:         +8.3C  (crit = +31.3C)
root@Server2:~#

:(

What is the problem?

---

### Post by cakeonfire on 2012-02-15
Hey everyone, I'm trying to configure the sensors but the thing is... I'm a complete noob. But ubuntu is so pretty I wanted to install it hahaha, so I'll be asking for some help... Even if my questions seem completly dumb, if I ask it's because I couldn't understand any of the solutions proposed/that I found while surfing.


Ok, so I just tried doing what miegiel did, and this is the result.

```
Driver `coretemp':
  * Chip `Intel digital thermal sensor' (confidence: 9)

Driver `sbs':
  * Bus `i915 gmbus dpc'
    Busdriver `drm', I2C address 0x0b
    Chip `Smart Battery' (confidence: 5)
  * Bus `i915 GPIOD'
    Busdriver `drm', I2C address 0x0b
    Chip `Smart Battery' (confidence: 5)

```

So, I answer yes when asked if I want to load them to modules, and then run the sudo service start thingy (yes, I'm a complete noob) and this is the return:

```
Do you want to add these lines automatically to /etc/modules? (yes/NO)y
Successful!

Monitoring programs won't work until the needed modules are
loaded. You may want to run 'service module-init-tools start'
to load them.

Unloading i2c-dev... OK
Unloading i2c-i801... OK
Unloading cpuid... OK

envy@ubuntu:~$ sudo service module-init-tools start
[sudo] password for envy: 
module-init-tools stop/waiting


```

After that, when I run sensors, this is the return

```
envy@ubuntu:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +58.0°C  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +53.0°C  (high = +105.0°C, crit = +105.0°C)
Core 1:       +53.0°C  (high = +105.0°C, crit = +105.0°C)

```

I'm wondering if there's something I'm doing wrong because I don't get voltage readings or ... any of the other stuff I've seen around. Also, I really think it doesn't but I was wondering if anybody knew if this laptop had a temp sensor for the ati chip?

I'm running 11.10 x64 on an HP Envy13. If you need any other info you consider relevant, please ask.

Thanks in advance!

---

### Post by Blah91 on 2012-02-27
E: nvm

---

### Post by quadrupole on 2012-04-09
Hi! I have the same problem.

> 
$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +50.0°C  (crit = +100.0°C)                  
temp2:       +47.0°C  (crit = +100.0°C)                  
temp3:       +58.0°C  (crit = +100.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +48.0°C  (high = +90.0°C, crit = +90.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +48.0°C  (high = +90.0°C, crit = +90.0°C)  

$/usr/sbin/pwmconfig
# pwmconfig revision 5770 (2009-09-16)
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.

We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.

/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed

So in short i think my MOBO cant control the RPM of the fans. I cant check RPM even in BIOS so some "application based" control would seem strange to me at least. 

BTW i am running on DELL Studio 1555 and Debian/6.0.4(stable Squeeze)
BTW2(:p) GKRell is a nice app to have installed as monitor.

---

### Post by niglas on 2012-04-22
[LIST=1]
[*]Any idea what this error is?
[LIST]
[*]```
[COLOR=SeaGreen]niglas@machine ~ $[/COLOR] service module-init-tools start
start: Rejected send message, 1 matched rules; type="method_call",   sender=":1.125" (uid=1000 pid=14895 comm="start module-init-tools ")   interface="com.ubuntu.Upstart0_6.Job" member="Start" error   name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart"   (uid=0 pid=1 comm="/sbin/init"
```
[/LIST]
 
[*]The sensor section in [FONT=Courier New]hardinfo[/FONT] is still empty, how do I get it in there?
[*]*Core 1 & 2* are pretty self explanatory, but what are *temp1*, *temp2* & *Physical id 0*?
[/LIST]
 Full output:
```
[COLOR=SeaGreen]niglas@machine ~ $[/COLOR] sudo dmidecode | grep 'Base Board' -A 2
Base Board Information
    Manufacturer: ASUSTeK Computer INC.
    Product Name: P8Z68-V
[COLOR=SeaGreen]niglas@machine ~ $[/COLOR] cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc

# Generated by sensors-detect on Sat Apr 21 15:04:56 2012
# Chip drivers
coretemp
[COLOR=SeaGreen]niglas@machine ~ $[/COLOR] service module-init-tools start
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.125" (uid=1000 pid=14895 comm="start module-init-tools ") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init")
[COLOR=SeaGreen]niglas@machine ~ $[/COLOR] sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +27.8°C  (crit = +86.0°C)
temp2:        +29.8°C  (crit = +86.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +38.0°C  (high = +80.0°C, crit = +85.0°C)
Core 0:         +35.0°C  (high = +80.0°C, crit = +85.0°C)
Core 1:         +35.0°C  (high = +80.0°C, crit = +85.0°C)

[COLOR=SeaGreen]niglas@machine ~ $[/COLOR]

```

---

### Post by sebl on 2012-05-27
Hello,

I've tried to install lm_sensors several times, but it doesn't seem to recognize the smsc EMC2103-2 Sensor my notebook (2530p) uses. When I do sensors detect it says:

> Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): y
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     Yes
Found unknown chip with ID 0x4501
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No


"Found unknown Chip", but in the documentation I can see, that the EMC2103-2 sensor is supported. Does somebody know how to force sensors, to use the EMC2103-2 Sensor? I'm 100% certain that it is the EMC2103-2 sensor, because I use it under windows as well.

---

### Post by akernan on 2012-05-27
> **sebl said:**
> Hello,

I've tried to install lm_sensors several times, but it doesn't seem to recognize the smsc EMC2103-2 Sensor my notebook (2530p) uses. When I do sensors detect it says:



"Found unknown Chip", but in the documentation I can see, that the EMC2103-2 sensor is supported. Does somebody know how to force sensors, to use the EMC2103-2 Sensor? I'm 100% certain that it is the EMC2103-2 sensor, because I use it under windows as well.

What version of lm-sensors do you have?  I had trouble with it finding one of my sensors until I installed the latest.  Sensor emc2103 needs kernel 2.6.32 or newer.  What happens when you install the emc2103 module?

```
sudo modprobe emc2103
```

---

### Post by sebl on 2012-05-27
I use 3.2.0-24-generic-phc. I can install/load the  emc2103 -module @ startup or with modprobe. It even shows up with lsmod, but nothing happens. Or is there some way I can use it? Maybe its somehow possible to manually edit the cip IDs so that ID ID 0x4501 is recognized as emc2103?

The problem is just that my notebook really heats up, so I want the fan to run faster. Even @ 80°C it just runs with 50% speed.

---

### Post by akernan on 2012-05-27
> **sebl said:**
> I use 3.2.0-24-generic-phc. I can install/load the  emc2103 -module @ startup or with modprobe. It even shows up with lsmod, but nothing happens. Or is there some way I can use it? Maybe its somehow possible to manually edit the cip IDs so that ID ID 0x4501 is recognized as emc2103?

The problem is just that my notebook really heats up, so I want the fan to run faster. Even @ 80°C it just runs with 50% speed.

What's the output from the sensors command?  Sorry, can't help with fan speed.  Maybe someone else can.

Did you look at the lm-sensors FAQ?

[lm-sensors FAQ](http://lm-sensors.org/wiki/FAQ/Chapter3#MyfansreportexactlyhalfdoubletheirvaluescomparedtotheBIOS)

---

### Post by sebl on 2012-05-27
sensors only shows temperatures:

> acpitz-virtual-0
Adapter: Virtual device
temp1:        +48.0°C  (crit = +105.0°C)
temp2:        +37.4°C  (crit = +110.0°C)
temp3:        +62.0°C  (crit = +110.0°C)
temp4:        +57.0°C  (crit = +90.0°C)
temp5:        +57.0°C  (crit = +105.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +62.0°C  (high = +105.0°C, crit = +105.0°C)
Core 1:       +63.0°C  (high = +105.0°C, crit = +105.0°C)


With or withour the emc2103 driver loaded

---

### Post by akernan on 2012-05-27
> **sebl said:**
> sensors only shows temperatures:



With or withour the emc2103 driver loaded

Hmm...Did the lm-sensors FAQ help?

---

### Post by miegiel on 2012-05-30
**[COLOR=#dd4814]@sebl[/COLOR]** Did you check your fan for dust? (In the category "Answers that are not related to lm-sensors".) With notebooks you often only need to lift the keyboard to reach/clean the fan. The heatsink can be dusty too, but it's more difficult to reach. Use a new/clean paintbrush, old toothbrush or compressed air (you can buy it in spraypaint-like cans).

For the CPU temperature you can ignore the *acpitz-virtual-0* temps, I've found them not to be accurate. It's the *coretemp-isa-0000* temps you need to keep an eye on.

My netbook went over 70°C a few days ago. In the sun, air temps just under 30°C :D And I didn't even make the machine work that hard.

---

### Post by ratcheer on 2012-06-09
I am a bit confused. I feel like I installed and setup lm-sensors on Ubuntu 12.04 and Arch Linux in exactly the same way, but running sensors gives me much more output on Arch than it does on Precise. It seems like something is not working on Precise or I have done something wrong.

Also, when I try to start or restart service module-init-tools, it just immediately replies that it is in status "stop/waiting". My guess is that this is where my problem lies.

Here is my output on Ubuntu 12.04:

> coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +37.0°C  (high = +80.0°C, crit = +98.0°C)
Core 0:         +35.0°C  (high = +80.0°C, crit = +98.0°C)
Core 1:         +37.0°C  (high = +80.0°C, crit = +98.0°C)
Core 2:         +35.0°C  (high = +80.0°C, crit = +98.0°C)
Core 3:         +38.0°C  (high = +80.0°C, crit = +98.0°C)Here is the sensors output from Arch Linux:

> radeon-pci-0100
Adapter: PCI adapter
temp1:        +60.0 C  

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +39.0 C  (high = +80.0 C, crit = +98.0 C)
Core 0:         +39.0 C  (high = +80.0 C, crit = +98.0 C)
Core 1:         +37.0 C  (high = +80.0 C, crit = +98.0 C)
Core 2:         +36.0 C  (high = +80.0 C, crit = +98.0 C)
Core 3:         +39.0 C  (high = +80.0 C, crit = +98.0 C)

it8728-isa-0290
Adapter: ISA adapter
in0:          +1.04 V  (min =  +0.00 V, max =  +3.06 V)
in1:          +2.04 V  (min =  +0.00 V, max =  +3.06 V)
in2:          +2.93 V  (min =  +0.00 V, max =  +3.06 V)
in3:          +2.98 V  (min =  +0.00 V, max =  +3.06 V)
in4:          +0.00 V  (min =  +0.00 V, max =  +3.06 V)  ALARM
in5:          +0.74 V  (min =  +0.00 V, max =  +3.06 V)
in6:          +1.54 V  (min =  +0.00 V, max =  +3.06 V)
3VSB:         +3.36 V  (min =  +0.00 V, max =  +6.12 V)
Vbat:         +3.29 V  
fan1:        1421 RPM  (min =    0 RPM)
fan2:           0 RPM  (min =    0 RPM)
fan3:        1231 RPM  (min =    0 RPM)
fan4:           0 RPM  (min =    0 RPM)
temp1:        +39.0 C  (low  = +127.0 C, high = +127.0 C)  sensor = thermistor
temp2:        +25.0 C  (low  = +127.0 C, high = +127.0 C)  sensor = thermistor
temp3:        +28.0 C  (low  = +127.0 C, high = +127.0 C)  sensor = thermistor
intrusion0:  ALARMWhat is wrong on Ubuntu?

Tim

**PS - Never mind.** I need to go to post 1 and work my way through all that beginning info. But, I didn't need to do anything like all that on Arch. Sorry.

---

### Post by ratcheer on 2012-06-10
See the preceding post. Now, I have followed post #1 instructions and I get the same results. It seems to find another sensor, but it does not include it in the stuff it says to add to /etc/modules. It only says to add coretemp, which is already there.

> Just press ENTER to continue: 

Driver `to-be-written':
  * ISA bus, address 0x290
    Chip `ITE IT8728F Super IO Sensors' (confidence: 9)

Driver `coretemp':
  * Chip `Intel digital thermal sensor' (confidence: 9)

Note: there is no driver for ITE IT8728F Super IO Sensors yet.
Check [http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) for updates.

To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
coretemp
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!
So, it finds a "Chip `ITE IT8728F Super IO Sensors' (confidence: 9)", but then says there is no driver for it. Apparently, the driver is found and used in lm-sensors on Arch Linux. Is there a way to find and load this driver on Ubuntu?

Also, there is a module it87.ko in my drivers folder, but if I try to modprobe it, it responds that it does not exist. ???

Tim

PS - Later [SOLVED]

Downloaded newer driver from [http://khali.linux-fr.org/devel/misc/it87/](http://khali.linux-fr.org/devel/misc/it87/)
Ran make, make install, modprobe it87
sensors now returns all the info expected

> 
coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +39.0°C  (high = +80.0°C, crit = +98.0°C)
Core 0:         +36.0°C  (high = +80.0°C, crit = +98.0°C)
Core 1:         +38.0°C  (high = +80.0°C, crit = +98.0°C)
Core 2:         +37.0°C  (high = +80.0°C, crit = +98.0°C)
Core 3:         +39.0°C  (high = +80.0°C, crit = +98.0°C)

it8728-isa-0290
Adapter: ISA adapter
in0:          +1.04 V  (min =  +0.00 V, max =  +3.06 V)
in1:          +2.04 V  (min =  +0.00 V, max =  +3.06 V)
in2:          +2.98 V  (min =  +0.00 V, max =  +3.06 V)
in3:          +2.96 V  (min =  +0.00 V, max =  +3.06 V)
in4:          +0.00 V  (min =  +0.00 V, max =  +3.06 V)  ALARM
in5:          +0.74 V  (min =  +0.00 V, max =  +3.06 V)
in6:          +1.54 V  (min =  +0.00 V, max =  +3.06 V)
3VSB:         +3.36 V  (min =  +0.00 V, max =  +6.12 V)
Vbat:         +3.29 V  
fan1:        1412 RPM  (min =    0 RPM)
fan2:           0 RPM  (min =    0 RPM)
fan3:        1247 RPM  (min =    0 RPM)
fan4:           0 RPM  (min =    0 RPM)
temp1:        +40.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:        +25.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp3:        +29.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
intrusion0:  ALARM


---

### Post by heiko_s on 2012-10-02
Recently I got the feeling that lm-sensors (or coretemp) CPU temperature readings are way off.

I'm currently running kernel 3.2.0-30-generic and 3.2.0-31-generic on two different machines. My older Core2 machine ran Linux Mint 9 before and temperatures were well below 40C when idle. Now they are in the 50s.

On my new machine with an Intel 3930K CPU I also noticed higher temperature readings, but I can't remember exactly when it started (meaning which kernel update or lm-sensors update produced the problem).

Anyone noticed something similar? I believe the CPU temperatures reported by lm-sensors are some 15-20C higher than the actual temperature, or at least how the BIOS reads the temperature.

---

### Post by mechulkalan on 2012-11-27
Hi guys.  This is my konsole output

```
# sensors-detect revision 5984 (2011-07-10 21:22:53 +0200)
# System: LENOVO 20091 (laptop)
# Board: LENOVO Base Board Product Name

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): y
Module cpuid loaded successfully.
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
AMD Family 12h and 14h thermal sensors...                   No
AMD Family 15h thermal sensors...                           No
AMD Family 15h power sensors...                             No
Intel digital thermal sensor...                             Success!
    (driver `coretemp')
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): y
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No

Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (YES/no): y
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): y
Using driver `i2c-i801' for device 0000:00:1f.3: Intel Cougar Point (PCH)
Module i2c-i801 loaded successfully.
Module i2c-dev loaded successfully.

Next adapter: i915 gmbus ssc (i2c-0)
Do you want to scan it? (YES/no/selectively): y

Next adapter: i915 gmbus vga (i2c-1)
Do you want to scan it? (YES/no/selectively): y

Next adapter: i915 gmbus panel (i2c-2)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     yNo
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                
Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter: i915 gmbus dpc (i2c-3)
Do you want to scan it? (YES/no/selectively): 
Next adapter: i915 gmbus dpb (i2c-4)
Do you want to scan it? (YES/no/selectively): y

Next adapter: i915 gmbus dpd (i2c-5)
Do you want to scan it? (YES/no/selectively): y

Next adapter: DPDDC-B (i2c-6)
Do you want to scan it? (YES/no/selectively): y

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `coretemp':
  * Chip `Intel digital thermal sensor' (confidence: 9)

To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
coretemp
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!

Do you want to add these lines automatically to /etc/modules? (yes/NO)y
Successful!

Monitoring programs won't work until the needed modules are
loaded. You may want to run 'service module-init-tools start'
to load them.

Unloading i2c-dev... OK
Unloading i2c-i801... OK
Unloading cpuid... OK

```this is modules:

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc

# Generated by sensors-detect on Tue Nov 27 15:57:19 2012
# Chip drivers
coretemp
```and this is my sensors output:

```
acpitz-virtual-0
Adapter: Virtual device
temp1:        +61.0°C  (crit = +127.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +60.0°C  (high = +86.0°C, crit = +100.0°C)
Core 0:         +57.0°C  (high = +86.0°C, crit = +100.0°C)
Core 1:         +59.0°C  (high = +86.0°C, crit = +100.0°C)
Core 2:         +57.0°C  (high = +86.0°C, crit = +100.0°C)
Core 3:         +59.0°C  (high = +86.0°C, crit = +100.0°C)

```now where is the problem ? Did i something wrong ?

---

### Post by ErikaUbu on 2013-01-29
I get the following output, so it includes some temperature sensors, but it misses the sensor for the fan. Which I would like to control. I have had problems with my laptop shutting down randomly and suspect it is an overheating issue and would like to try to control the fan speed. My fan runs very slow most of the time.

erika@erika-Inspiron-N5110:/$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +52.5°C  (crit = +85.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +52.0°C  (high = +80.0°C, crit = +85.0°C)
Core 0:         +52.0°C  (high = +80.0°C, crit = +85.0°C)
Core 1:         +50.0°C  (high = +80.0°C, crit = +85.0°C)

radeon-pci-0100
Adapter: PCI adapter
temp1:        +54.0°C  


Thanks, Erika

---

### Post by miegiel on 2013-01-29
> **ErikaUbu said:**
> I get the following output, so it includes some temperature sensors, but it misses the sensor for the fan. Which I would like to control. I have had problems with my laptop shutting down randomly and suspect it is an overheating issue and would like to try to control the fan speed. My fan runs very slow most of the time.

erika@erika-Inspiron-N5110:/$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +52.5°C  (crit = +85.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +52.0°C  (high = +80.0°C, crit = +85.0°C)
Core 0:         +52.0°C  (high = +80.0°C, crit = +85.0°C)
Core 1:         +50.0°C  (high = +80.0°C, crit = +85.0°C)

radeon-pci-0100
Adapter: PCI adapter
temp1:        +54.0°C  


Thanks, Erika

Hi Erika, welcome to ubuntu forums.

Lm-sensors only reads the sensors, it doesn't control your fan speed. Maybe you'll have more success using *fancontrol* or *thinkfan*, people have mentioned fancontrol in this thread. I never used either myself, setting the fan speed in the BIOS has always been suficient for me.

---

### Post by vickoxy on 2013-03-01
Hi,
i just bought HP 2540p and when i run 
sensors-detect i got
```
root@linux:~# sensors-detect
# sensors-detect revision 5984 (2011-07-10 21:22:53 +0200)
# System: Hewlett-Packard HP EliteBook 2540p (laptop)
# Board: Hewlett-Packard 7008

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): y
Module cpuid loaded successfully.
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
AMD Family 12h and 14h thermal sensors...                   No
AMD Family 15h thermal sensors...                           No
AMD Family 15h power sensors...                             No
Intel digital thermal sensor...                             Success!
    (driver `coretemp')
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): y
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     Yes
Found `SMSC FDC37B72x Super IO'                             
    (no hardware monitoring capabilities)
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No

Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (YES/no): y
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): y
Sorry, no supported PCI bus adapters found.
Module i2c-dev loaded successfully.

Next adapter: i915 gmbus disabled (i2c-0)
Do you want to scan it? (YES/no/selectively): y

Next adapter: i915 gmbus ssc (i2c-1)
Do you want to scan it? (YES/no/selectively): y

Next adapter: i915 GPIOB (i2c-2)
Do you want to scan it? (YES/no/selectively): y

Next adapter: i915 gmbus vga (i2c-3)
Do you want to scan it? (YES/no/selectively): y

Next adapter: i915 GPIOA (i2c-4)
Do you want to scan it? (YES/no/selectively): y

Next adapter: i915 gmbus panel (i2c-5)
Do you want to scan it? (YES/no/selectively): y
 
Next adapter: i915 GPIOC (i2c-6)
Do you want to scan it? (YES/no/selectively): y

Next adapter: i915 gmbus dpc (i2c-7)
Do you want to scan it? (YES/no/selectively): y

Next adapter: i915 GPIOD (i2c-8)
Do you want to scan it? (YES/no/selectively): y

Next adapter: i915 gmbus dpb (i2c-9)
Do you want to scan it? (YES/no/selectively): y

Next adapter: i915 GPIOE (i2c-10)
Do you want to scan it? (YES/no/selectively): y

Next adapter: i915 gmbus reserved (i2c-11)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x18
Probing for `Analog Devices ADM1021'...                     No
Probing for `Analog Devices ADM1021A/ADM1023'...            No
Probing for `Maxim MAX1617'...                              No
Probing for `Maxim MAX1617A'...                             No
Probing for `Maxim MAX1668'...                              No
Probing for `Maxim MAX1805'...                              No
Probing for `Maxim MAX1989'...                              No
Probing for `Maxim MAX6655/MAX6656'...                      No
Probing for `TI THMC10'...                                  No
Probing for `National Semiconductor LM84'...                No
Probing for `Genesys Logic GL523SM'...                      No
Probing for `Onsemi MC1066'...                              No
Probing for `Maxim MAX1618'...                              No
Probing for `Maxim MAX1619'...                              No
Probing for `National Semiconductor LM82/LM83'...           No
Probing for `Maxim MAX6654'...                              No
Probing for `Maxim MAX6690'...                              No
Probing for `Maxim MAX6680/MAX6681'...                      No
Probing for `Maxim MAX6695/MAX6696'...                      No
Probing for `Texas Instruments AMC6821'...                  No
Probing for `National Semiconductor LM95245'...             No
Probing for `National Semiconductor LM64'...                No
Probing for `SMSC EMC1047'...                               No
Probing for `SMSC EMC1402'...                               No
Probing for `SMSC EMC1403'...                               No
Probing for `SMSC EMC1404'...                               No
Probing for `ST STTS424'...                                 No
Probing for `ST STTS424E'...                                No
Probing for `NXP SE97/SE97B'...                             No
Probing for `NXP SE98'...                                   No
Probing for `Analog Devices ADT7408'...                     No
Probing for `IDT TS3000/TSE2002'...                         No
Probing for `Maxim MAX6604'...                              No
Probing for `Microchip MCP98242'...                         No
Probing for `Microchip MCP98243'...                         No
Probing for `Microchip MCP9843'...                          No
Probing for `ON CAT6095/CAT34TS02'...                       No
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                No
Client found at address 0x51
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Client found at address 0x52
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Client found at address 0x53
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Client found at address 0x58
Probing for `Analog Devices ADT7462'...                     No
Probing for `Andigilog aSC7512'...                          No
Client found at address 0x5c
Probing for `Analog Devices ADT7462'...                     No
Probing for `SMSC EMC1072'...                               No
Probing for `SMSC EMC1073'...                               No
Probing for `SMSC EMC1074'...                               No
Client found at address 0x73
Probing for `FSC Poseidon I'...                             No
Probing for `FSC Poseidon II'...                            No
Probing for `FSC Scylla'...                                 No
Probing for `FSC Hermes'...                                 No
Probing for `FSC Heimdal'...                                No
Probing for `FSC Heracles'...                               No
Probing for `FSC Hades'...                                  No
Probing for `FSC Syleus'...                                 No

Next adapter: i915 gmbus dpd (i2c-12)
Do you want to scan it? (YES/no/selectively): y

Next adapter: i915 GPIOF (i2c-13)
Do you want to scan it? (YES/no/selectively): y

Next adapter: DPDDC-A (i2c-14)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter: DPDDC-B (i2c-15)
Do you want to scan it? (YES/no/selectively): y

Next adapter: DPDDC-D (i2c-16)
Do you want to scan it? (YES/no/selectively): y

Now follows a summary of the probes I have just done.
Just press ENTER to continue:  

Driver `coretemp':
  * Chip `Intel digital thermal sensor' (confidence: 9)

To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
coretemp
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!

Do you want to add these lines automatically to /etc/modules? (yes/NO)y
Successful!

Monitoring programs won't work until the needed modules are
loaded. You may want to run 'service module-init-tools start'
to load them.

Unloading i2c-dev... OK
Unloading cpuid... OK

```

Running sudo pwmconfig gets me:
```
root@linux:~# sudo pwmconfig
# pwmconfig revision 5857 (2010-08-22)
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.

We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.

/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed

```

I found nothin to solve this problem., I need this sensors of course to control fan with fancontrol.

---

### Post by miegiel on 2013-03-02
> **vickoxy said:**
> Hi,
i just bought HP 2540p and when i run 
sensors-detect i got
CODE

Running sudo pwmconfig gets me:
CODE

I found nothin to solve this problem., I need this sensors of course to control fan with fancontrol.

Does this thread hlp you ? [**[COLOR="#000000"]Thread:[/COLOR] 'There are no pwm-capable sensor modules installed'**]("http://ubuntuforums.org/showthread.php?t=1877114")

---

### Post by vickoxy on 2013-03-02
I tried, but i can not load i87k.
:-(

I noticed that temp 3 is actually FAN speed-as soon as it goes of, it stays 0, and for every further step the temp goes 10 grades up. But no idea what schould i do with this info.

```
acpitz-virtual-0
Adapter: Virtual device
temp1:         +0.0°C  (crit = +127.0°C)
temp2:         +0.0°C  (crit = +127.0°C)
temp3:        +11.0°C  (crit = +128.0°C)
temp4:        +39.0°C  (crit = +127.0°C)
temp5:         +0.0°C  (crit = +115.0°C)
temp6:        +32.2°C  (crit = +128.0°C)
temp7:         +0.0°C  (crit = +128.0°C)
temp8:        +42.0°C  (crit = +128.0°C)
temp9:        +48.0°C  (crit = +128.0°C)
temp10:       +59.0°C  (crit = +128.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +43.0°C  (high = +95.0°C, crit = +105.0°C)
Core 2:       +41.0°C  (high = +95.0°C, crit = +105.0°C)

```

---

### Post by vickoxy on 2013-03-02
Does anyonee know if HP 2540p has pwm capable sensors? Couldn´t find any help on line.
So, please...

---

### Post by miegiel on 2013-03-02
Update ubuntu to [12.04 (Support up to April 2017)]("http://www.ubuntu.com/download/desktop") or [12.10  (Support up to April 2014)]("http://www.ubuntu.com/download/desktop"). Ubuntu 11.04 is not supported anymore and you're not getting (security) updates. And as a side effect it might also solve your lm-sensors trouble, since you'll probably be using a newer version.

**Edit:** Sorry, I still need to get used to this new layout. Do you still use 11.04?

---

### Post by vickoxy on 2013-03-03
I use 12.04 (Xubuntu 12.04 64bit). Well i made some progress here:
[http://ubuntuforums.org/showthread.php?t=2008756&page=2](http://ubuntuforums.org/showthread.php?t=2008756&page=2)

<Still, it would be nice to see if i can get lm_sensors under ubuntu. Under Windows they should be well recocgnized....
Thanks

---

