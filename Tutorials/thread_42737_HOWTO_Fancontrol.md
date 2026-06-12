---
title: "HOWTO: Fancontrol"
date: 2005-06-19
forum: Tutorials
---

### Post by remmelt on 2005-06-19
Controlling the speed (and sound!) of your CPU fan is easy!
*[COLOR=Red]Disclaimer: this can ruin your hardware. A CPU fan is needed to cool your CPU and in this howto it will be turned off for a couple of seconds. If you are not comfortable with doing this, don't![/COLOR]*

Update Nov 7, 2007: this still works in Gutsy Gibbon! Hurray!

**Setup lm-sensors**
First, you need to set up lm-sensors. This is explained [here](http://ubuntuforums.org/showthread.php?t=2780). That's for Warty, but still works under Hoary.

Once you have lm-sensors installed, you should have a readout with 'sensors'
```
$ sensors
w83627thf-isa-0290
Adapter: ISA adapter
VCore:     +1.54 V  (min =  +1.69 V, max =  +1.86 V)              
+12V:     +11.67 V  (min = +10.82 V, max = +13.19 V)              
+3.3V:     +3.42 V  (min =  +3.14 V, max =  +3.47 V)              
+5V:       +5.15 V  (min =  +4.75 V, max =  +5.25 V)              
-12V:     -14.91 V  (min = -10.80 V, max = -13.18 V)              
V5SB:      +5.05 V  (min =  +4.76 V, max =  +5.24 V)              
VBat:      +0.06 V  (min =  +2.40 V, max =  +3.60 V)              
fan1:        0 RPM  (min = 18750 RPM, div = 8)                     
CPU Fan:  1188 RPM  (min = 18750 RPM, div = 8)                     
fan3:        0 RPM  (min = 19285 RPM, div = 1)                     
M/B Temp:    +31Â°C  (high =   -73Â°C, hyst =   +21Â°C)   sensor = thermistor           
CPU Temp:  +50.0Â°C  (high =   +80Â°C, hyst =   +75Â°C)   sensor = thermistor           
temp3:     +15.0Â°C  (high =   +80Â°C, hyst =   +75Â°C)   sensor = thermistor           
vid:      +1.775 V  (VRM Version 9.0)
alarms:   
beep_enable:
          Sound alarm enabled

eeprom-i2c-0-51
Adapter: SMBus Via Pro adapter at 0400
Memory type:            DDR SDRAM DIMM
Memory size (MB):       256

eeprom-i2c-0-50
Adapter: SMBus Via Pro adapter at 0400
Memory type:            DDR SDRAM DIMM
Memory size (MB):       256

```

Notice that my CPU fan is running really slowly, only 1100 RPM. The CPU temp is a little high, so I need to do some tweaking of the config there. The fan can run so slowly and quietly, because it's a large 12 cm fan made by Zalman (it's the 7000B AlCu). If your output does not display an RPM for your CPU fan, and you are positive it is running, you need to increase the fan divisor. If your fan speed is shown and higher than 0, skip the next step.

**Increasing fan_div**
The first line of the sensors output is the chipset your motherboard uses to read the speeds/temps/voltages. Make a backup first:
```
$ sudo cp /etc/sensors.conf /etc/sensors.conf_original
```
Edit the /etc/sensors.conf file as root
```
$ sudo gedit /etc/sensors.conf
```
and look up your exact chipset. The names all look alike, so make sure the one you are editing is yours. Add the line fanX_div 4 near the start of your chipset config. Replace the X with the number of your CPU fan's, for me that was 2. You have to figure out for yourself which one it is, but it's probably 1, 2 or 3.

Save, and run 
```
$ sudo sensors -s
```
which will reload the sensors.conf's set variables.
Run sensors again and check if there is an RPM readout. If not, increase the divisor to 8, 16 or 32. YMMV!

Here is a sample from my sensors.conf
```
chip "w83627thf-*" "w83637hf-*"

    label in0 "VCore"
    label in1 "+12V"
    label in2 "+3.3V"
    label in3 "+5V"
    label in4 "-12V"
    label in7 "V5SB"
    label in8 "VBat"

    compute in1 ((28/10)+1)*@, @/((28/10)+1)
    compute in3 ((34/51)+1)*@, @/((34/51)+1)
    compute in4 (5.14*@)-14.91, (@+14.91)/5.14
    compute in7 ((6.8/10)+1)*@ ,  @/((6.8/10)+1)

    set fan2_div 8

    <snip>

```
You can safely ignore anything that's not fanX_div. I would advise you to leave the other default settings as they are.


**Patching pwmconfig** [Color=red]This is no longer needed if you run Dapper! Go to the next step unless you're running Hoary.[/color]
[There is a bug in pwmconfig](https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=145294) that you need to fix.
This is true for the version currently in Hoary, version 2.8.8-7ubuntu2.

First, try running pwmconfig:
```
$ pwmconfig
``` 
if that gives you the following error:
/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed
than you need to apply this fix. If not, proceed to the next step.

Backup:
```
$ sudo cp /usr/sbin/pwmconfig /usr/sbin/pwmconfig_original
``` 
Open pwmconfig:
```
$ sudo gedit /usr/sbin/pwmconfig
``` 
and go to line 68. Delete these three lines:
```
        MATCH='*/fan[1-9]_pwm'
else
        MATCH='*/pwm[1-9]'
```
and replace with:
```
        MATCH='*/pwm[1-9]'
else
        MATCH='*/fan[1-9]_pwm'
```
You just turned the if/else around! Now pwmconfig should work.

**Run pwmconfig**
```
$ sudo pwmconfig
```
One by one, all fans will be tested for 'speedcontrol' (Pulse Width Modulation, actually). Follow the onscreen help. Pwmconfig will write a config file in /etc. I set the interval to 5 seconds, just to be safe, but 10 should be fine too. Let the script run until you see "Select fan output to configure, or other action:" (all default options are fine, you can basically enter you way through the script).

Now press 5 to look at the configuration file. Press 1 to edit settings. Select a temperature that matches your CPU temp (usually the same number as the fan number, but check and double check!). Go with the defaults until you see: "Enter the minimum PWM value (0-255)
at which the fan STARTS spinning (press t to test) (150):"
Here, press t.
Keep pressing enter until you hear (or better: see) the fan spinning up. Then, press y and enter.
Same for the next step, but the other way around. If you see the fan stops spinning, press y and enter.

Press 5 again to display the config file one more time, then press 4 to save and quit. Almost there!

My /etc/fancontrol config looks like this:
```
INTERVAL=5
FCTEMPS= 1-0290/pwm2=1-0290/temp2_input
FCFANS= 1-0290/pwm2=1-0290/fan2_input
MINTEMP= 1-0290/pwm2=43
MAXTEMP= 1-0290/pwm2=53
MINSTART= 1-0290/pwm2=120
MINSTOP= 1-0290/pwm2=105

```
this is an example!

**Starting fancontrol** 
The last step is to start up fancontrol. Enter this:
```
$ sudo fancontrol &
``` 
Now you can see and hear that your CPU fan is running slower, unless your CPU heats up. Good stuff!

[B}Starting fancontrol automatically on boot[/B]
Create a file called "fancontrol" in /etc/init.d:
```
sudo gedit /etc/init.d/fancontrol
```

And paste this in there:
```
#!/bin/sh
#
# Fancontrol start script.
#

set -e

# Defaults
DAEMON=/usr/sbin/fancontrol
PIDFILE=/var/run/fancontrol.pid
PATH=/sbin:/bin:/usr/sbin:/usr/bin

test -f $DAEMON || exit 0

. /lib/lsb/init-functions


case "$1" in
        start)
                log_begin_msg "Starting fancontrol daemon..."
                start-stop-daemon --start -o -q -m -b -p $PIDFILE -x $DAEMON
                log_end_msg $?
                ;;
        stop)
                log_begin_msg "Stopping fancontrol daemon..."
                start-stop-daemon --stop -o -q -p $PIDFILE
                log_end_msg $?
                ;;
        force-reload|restart)
                sh $0 stop
                sh $0 start
                ;;
        *)
                log_success_msg "Usage: /etc/init.d/fancontrol {start|stop|restart|force-reload}"
                log_success_msg "  start - starts system-wide fancontrol service"
                log_success_msg "  stop  - stops system-wide fancontrol service"
                log_success_msg "  restart, force-reload - starts a new system-wide fancontrol service"
                exit 1
                ;;
esac

exit 0

```

Save and close, then run ```
sudo update-rc.d fancontrol defaults 99 01
``` and you should be set.

(Thanks, Mr Wonka and jotape99!)


I would advise you to have some sort of fan/temp monitoring software installed. There is a nice one in gkrellm, or you can use xsensors.

Most of this howto is from here:
[http://www.fedoraforum.org/forum/showpost.php?p=161610&postcount=5](http://www.fedoraforum.org/forum/showpost.php?p=161610&postcount=5)
Check if your hardware is supported here:
[http://www.almico.com/forumindex.php](http://www.almico.com/forumindex.php)

---

### Post by Mr Wonka on 2005-06-19
And if you want to have it startup on boot.

```
#!/bin/sh
#
# Fancontrol start script.
#

set -e

# Defaults
DAEMON=/usr/sbin/fancontrol
PIDFILE=/var/run/fancontrol/.fancontrol-pid
PATH=/sbin:/bin:/usr/sbin:/usr/bin

test -f $DAEMON || exit 0

. /lib/lsb/init-functions


case "$1" in
	start)
		log_begin_msg "Starting fancontrol daemon..."
		start-stop-daemon --start -o -q -m -b -p $PIDFILE -x $DAEMON
		log_end_msg $?
		;;
	stop)
		log_begin_msg "Stopping fancontrol daemon..."
		start-stop-daemon --stop -o -q -p $PIDFILE
		log_end_msg $?
		;;
	force-reload|restart)
		sh $0 stop
		sh $0 start
		;;
	*)
		log_success_msg "Usage: /etc/init.d/fancontrol {start|stop|restart|force-reload}"
		log_success_msg "  start - starts system-wide fancontrol service"
		log_success_msg "  stop  - stops system-wide fancontrol service"
		log_success_msg "  restart, force-reload - starts a new system-wide fancontrol service"
		exit 1
		;;
esac

exit 0

``` 

Stick this in a file called 'fancontrol' in your init.d startup scripts. eg.

```
/etc/init.d/fancontrol
```

Add this to your startup scripts in the usual way.

---

### Post by remmelt on 2005-06-20
Don't forget to 

```
$ sudo chmod 0755 /etc/init.d/fancontrol
``` 

and create a symlink to that script in rc3.d, for example.

```
$ sudo ln -s /etc/init.d/fancontrol /etc/rc3.d/S99fancontrol
``` 

(thanks for that, by the way!)

---

### Post by picpak on 2005-06-29
I fixed the code in pwmconfig, and it still doesn't work...any ideas?

*edit* Nevermind...I fixed it :)

---

### Post by cwf on 2005-07-24
[QUOTE=Mr Wonka]And if you want to have it startup on boot.

```
#!/bin/sh
#
# Fancontrol start script.
#

set -e

# Defaults
DAEMON=/usr/sbin/fancontrol
PIDFILE=/var/run/fancontrol/.fancontrol-pid
PATH=/sbin:/bin:/usr/sbin:/usr/bin

test -f $DAEMON || exit 0

. /lib/lsb/init-functions


case "$1" in
	start)
		log_begin_msg "Starting fancontrol daemon..."
		start-stop-daemon --start -o -q -m -b -p $PIDFILE -x $DAEMON
		log_end_msg $?
		;;
	stop)
		log_begin_msg "Stopping fancontrol daemon..."
		start-stop-daemon --stop -o -q -p $PIDFILE
		log_end_msg $?
		;;
	force-reload|restart)
		sh $0 stop
		sh $0 start
		;;
	*)
		log_success_msg "Usage: /etc/init.d/fancontrol {start|stop|restart|force-reload}"
		log_success_msg "  start - starts system-wide fancontrol service"
		log_success_msg "  stop  - stops system-wide fancontrol service"
		log_success_msg "  restart, force-reload - starts a new system-wide fancontrol service"
		exit 1
		;;
esac

exit 0

``` 

Stick this in a file called 'fancontrol' in your init.d startup scripts. eg.

```
/etc/init.d/fancontrol
```

Add this to your startup scripts in the usual way.[/QUOTE]

Great HOWTO.  Just what I was looking for...in Windows I was using Speedfan...this is  just as good!

However, I am unable to get the daemon to startup automatically.  

I created a file called fancontrol with the script given in /etc/init.d

Then I did update-rc.d fancontrol defaults and got this output:

 Adding system startup for /etc/init.d/fancontrol ...
   /etc/rc0.d/K20fancontrol -> ../init.d/fancontrol
   /etc/rc1.d/K20fancontrol -> ../init.d/fancontrol
   /etc/rc6.d/K20fancontrol -> ../init.d/fancontrol
   /etc/rc2.d/S20fancontrol -> ../init.d/fancontrol
   /etc/rc3.d/S20fancontrol -> ../init.d/fancontrol
   /etc/rc4.d/S20fancontrol -> ../init.d/fancontrol
   /etc/rc5.d/S20fancontrol -> ../init.d/fancontrol

However, when I restart my system and start Linux the fancontrol does not start automatically.

Note, it works great when I go to terminal and run 'fancontrol'.  Just can't get the startup working.

Help is greatly appreciated.

Thanks,
CWF

---

### Post by ubuntu dave on 2005-07-25
Hi all, thanks for this great guide, worked perfectly for me so far (yet to reboot  ;-) ). 
One thing of note that occured for me using the script kindly provided above:

```
 sudo /etc/init.d/fancontrol start
 * Starting fancontrol daemon...
start-stop-daemon: Unable to open pidfile `/var/run/fancontrol/.fancontrol-pid' for writing: No such file or directory     
``` 

```
# Defaults
DAEMON=/usr/sbin/fancontrol
PIDFILE=/var/run/fancontrol/.fancontrol-pid
PATH=/sbin:/bin:/usr/sbin:/usr/bin
``` 

I had to change the PIDFILE path to:

```
# Defaults
DAEMON=/usr/sbin/fancontrol
PIDFILE=/var/run/fancontrol-pid
PATH=/sbin:/bin:/usr/sbin:/usr/bin
``` 

I don't know if this was something specific to me....... But incase it helps others.

---

### Post by bored2k on 2005-07-25
I would seriously have a heart-attack just by trying this (I don't even need for it to _not_ work O.o). Just reading the red disclaimer sends shivers down my spine.

---

### Post by benplaut on 2005-07-25
[QUOTE=bored2k]I would seriously have a heart-attack just by trying this (I don't even need for it to _not_ work O.o). Just reading the red disclaimer sends shivers down my spine.[/QUOTE]

aye... what's the point of it, i'm wondering?

---

### Post by SuperMike on 2005-07-25
Geesh. What if a virus installed one of these things? My paranoid brain can see whole multimillion dollar server rooms catching on fire now.

---

### Post by benplaut on 2005-07-25
[QUOTE=SuperMike]Geesh. What if a virus installed one of these things? My paranoid brain can see whole multimillion dollar server rooms catching on fire now.[/QUOTE]

don't give them ideas  :roll:

---

### Post by remmelt on 2005-08-04
I guess the point is that it makes my life (even more) liveable because it makes the noise from my computer less. The cpu fan doesn't need to run 100% all the time, and I have described a way to make it less noisy.

That said, you shouldn't be running stuff like this on a server. Servers need all the cooling they can get, plus they are usually stored in places where no-one can hear the noise they make. Moreover, Ubuntu is a desktop-linux, right?

---

### Post by remmelt on 2005-08-04
[QUOTE=SuperMike]Geesh. What if a virus installed one of these things? My paranoid brain can see whole multimillion dollar server rooms catching on fire now.[/QUOTE]

You used to have Windows installed, right? ;)

Just kidding. It is a scary thought. This way, a virus could do actual physical damage to a computer. On the other hand, most companies value the data on the drives more than the hardware. Hardware is replacable, (unbackupped) data isn't. Virusses tend to steal or corrupt data more than mess up computers like they used to.

---

### Post by |cassidy| on 2005-10-10
[QUOTE=picpak]I fixed the code in pwmconfig, and it still doesn't work...any ideas?

*edit* Nevermind...I fixed it :)[/QUOTE]


Hello, the pwmconfig patch isn't helping the situation in my system. 
I still get the 
"/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed" error.

:confused: 

Any help is appreciated.

---

### Post by remmelt on 2005-10-10
Are you very sure you corrected the pwmconfig file right?

If so: it may be right, you may not have any pwm configurable fans in your computer. Most Dells don't, for instance, even the new ones.

Do you get any results in fancontrol under Windows?

---

### Post by |cassidy| on 2005-10-10
Yes, I've triple checked the procedure :)

I've got a desktop pc, via kt266 chipset and in windows I control the fans' speed using Speedfan.

I did a search on the forum and found this
[http://www.ubuntuforums.org/showthread.php?t=28465&highlight=pwmconfig](http://www.ubuntuforums.org/showthread.php?t=28465&highlight=pwmconfig)

I have the same motherboard chipset and the same kernel version.

I really gotta lower these fans, I've got low temperatures and a fan that sounds like a vacuum cleaner.

---

### Post by remmelt on 2005-10-11
Did you do all the things in [here]("http://ubuntuforums.org/showthread.php?t=2780")? If you go "sensors", what does it output?

---

### Post by |cassidy| on 2005-10-11
Yes that's the howto i followed to make lm-sensors working.
This is the output I get.

```

eeprom-i2c-1-51
Adapter: SMBus Via Pro adapter at 5000
Memory type:            DDR SDRAM DIMM
Memory size (MB):       256

eeprom-i2c-1-50
Adapter: SMBus Via Pro adapter at 5000
Memory type:            DDR SDRAM DIMM
Memory size (MB):       512

it87-isa-0290
Adapter: ISA adapter
VCore 1:   +1.71 V  (min =  +1.42 V, max =  +1.57 V)   ALARM
VCore 2:   +2.51 V  (min =  +2.40 V, max =  +2.61 V)
+3.3V:     +6.66 V  (min =  +3.14 V, max =  +3.46 V)   ALARM
+5V:       +4.92 V  (min =  +4.76 V, max =  +5.24 V)
+12V:     +12.35 V  (min = +11.39 V, max = +12.61 V)
-12V:     -19.38 V  (min = -12.63 V, max = -11.41 V)   ALARM
-5V:       +0.70 V  (min =  -5.26 V, max =  -4.77 V)   ALARM
Stdby:     +4.95 V  (min =  +4.76 V, max =  +5.24 V)
VBat:      +2.03 V
fan1:     2960 RPM  (min =    0 RPM, div = 8)
fan2:        0 RPM  (min =  664 RPM, div = 8)          ALARM
fan3:        0 RPM  (min = 2657 RPM, div = 2)
CPU temp:    +34&#176;C  (low  =   +15&#176;C, high =   +50&#176;C)   sensor = thermistor
M/B Temp:    +25&#176;C  (low  =   +15&#176;C, high =   +45&#176;C)   sensor = thermistor
Temp3:       -55&#176;C  (low  =   +15&#176;C, high =   +45&#176;C)   sensor = thermistor


```

---

### Post by remmelt on 2005-10-11
Have you tried booting the 2.6.8 kernel? It seems to solve things in the other thread... Weird though.

Part of my /etc/modules
```

# lm-sensors stuff (remmelt)
# I2C adapter drivers
i2c-viapro
i2c-isa
# I2C chip drivers
lm75
eeprom
smbus-arp
w83627hf

```

I don't know... Could you check the fix in the pwnconfig script again? I checked mine and it's been put back to the original setting, I don't know how.
Good luck!

---

### Post by qalimas on 2005-10-11
[QUOTE=benplaut]don't give them ideas  :roll:[/QUOTE]

A program that does this that runs on Windows would be the end of Microsoft as we know it, anyone know how to port it? ;)  Viruses, moms, 3 year old kids changing fan speeds and heating up hardware, that'd be hilarous :D 

Nice guide, I'll give it a try on an old test computer shortly ;)

---

### Post by remmelt on 2005-10-11
Yes, it's called speedfan and it's pretty good! Works very well under Windows.

---

### Post by Evil Dax on 2005-11-04
I've got the PWMconfig and LM-config working,
it's doing fine on both my fans (nforce2)
However, one of those fans is set to cool my HDDs.
I have read most of these forums, but can't seem to find my answers:
I've installed HDDtemp to monitor my discs (didn't find other tools for it)
But: is it possible to add these values to PWMconfig, so that fancontrol also regulates this fan ?

PS: I'm a linux-newbie, installed this last week....

---

### Post by yesplease on 2005-11-08
Just a warning, Speedfan was/is a good program for windows, but is not maintained or updated any more for some time now. Be carefull.

(I use the fancontroller made by MSI for my motherboard on windows, which works for me, but is considered malware by others :) )

---

### Post by jotape99 on 2005-11-22
Thanks for this great how to.

My little contribution: to add the start/stop links, I rather prefer the command:
```
sudo update-rc.d fancontrol defaults 99 01
```
I changed the pid file in the script:
```
PIDFILE=/var/run/fancontrol.pid
```

---

### Post by mozetti on 2006-04-16
Nevermind, got it sorted.

---

### Post by mistapotta on 2006-08-06
I recently built a computer with an Intel D945Gcz motherboard and an Intel Pentium-D 3.0 processor, and the fan sounds like a vacuum cleaner.  I'd like to find a way to regulate the fan speed, as other operating systems seem to be able to do it.

I installed lm-sensors as shown [here]("http://ubuntuforums.org/showthread.php?t=2780") and got an output from it:

```
lm85-i2c-0-2e
Adapter: SMBus I801 adapter at 2000
V1.5:       +1.58 V  (min =  +1.42 V, max =  +1.58 V)
VCore:      +1.25 V  (min =  +1.76 V, max =  +1.95 V)   ALARM
V3.3:       +3.33 V  (min =  +3.13 V, max =  +3.47 V)
V5:        +5.10 V  (min =  +4.74 V, max =  +5.26 V)
V12:      +12.19 V  (min = +11.38 V, max = +12.62 V)
CPU_Fan:   5268 RPM  (min = 1000 RPM)
fan2:         0 RPM  (min =    0 RPM)
fan3:         0 RPM  (min =    0 RPM)
fan4:         0 RPM  (min =    0 RPM)
CPU:         +39Â°C  (low  =   +10Â°C, high =   +60Â°C)
Board:       +30Â°C  (low  =   +10Â°C, high =   +35Â°C)
Remote:      +34Â°C  (low  =   +10Â°C, high =   +35Â°C)
CPU_PWM:   255
Fan2_PWM:  255
Fan3_PWM:  255
vid:      +1.850 V  (VRM Version 9.1)
```

I've tried following through the explanation [here]("http://ubuntuforums.org/showthread.php?t=42737") but haven't had any success.  In particular, when I try to add

```
set fan1_div 4
```

as specified, I get

```
~$ sudo sensors -s
Error: Line 2196: Unknown feature name
lm85-i2c-0-2e: No such feature known
```

I understand there are situations where my fan would need to run near 5300 RPM, but the baby in the next room does need to sleep.  

Anyone have any ideas?

~Tony David Potter

---

### Post by remmelt on 2006-08-06
For starters: do not try to patch the pwmconfig thing if you are running dapper. It's been fixed, you no longer need to patch the script.

mistapotta: It looks like your fan is being picked up correctly by lm_sensors. The speed is being reported, so you won't have to change the fan's divisor. You only need to do this if the fan is running so slowly that lm_sensors thinks it's turned off. Looks like this is not the case.
Also, fan1_div would point to a fan named fan1. Looking at your output, the CPU fan is actually called CPU_Fan (conveniently!) so it would be CPU_Fan_div, I guess.

You're now ready to run pwmconfig! Good luck!

If you want to silence your computer even more, I suggest getting a larger fan. I have a 12" one made by Zalman, and it's very quiet with the rotations turned down. With my CPU (amd athlon 64 3000+), it sometimes even turns off alltogether. I don't know how hot your Pentium runs though, could be a lot hotter. Anyway, try the pwmconfig and if it's still too loud after that you can always look at a larger fan.

---

### Post by mistapotta on 2006-08-06
The CPU_Fan is just a label set in my sensors.conf.
```

# Fan inputs
   label fan1   "CPU_Fan"

```
and changing CPU_Fan_div still gives "unknown feature name" error

When I tried to run pwnconfig, this was the output:


```

~$ sudo pwmconfig
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
   0-002e/pwm1
/usr/sbin/pwmconfig: line 102: 0-002e/pwm1_enable: Permission denied
   0-002e/pwm2
/usr/sbin/pwmconfig: line 102: 0-002e/pwm2_enable: Permission denied
   0-002e/pwm3
/usr/sbin/pwmconfig: line 102: 0-002e/pwm3_enable: Permission denied

Found the following fan sensors:
   0-002e/fan1_input     current speed: 5227 RPM
   0-002e/fan2_input     current speed: 0 ... skipping!
   0-002e/fan3_input     current speed: 0 ... skipping!
   0-002e/fan4_input     current speed: 0 ... skipping!

Warning!!! This program will stop your fans, one at a time,
for approximately 5 seconds each!!!
This may cause your processor temperature to rise!!!
If you do not want to do this hit control-C now!!!
Hit return to continue:

Testing pwm control 0-002e/pwm1 ...
/usr/sbin/pwmconfig: line 117: 0-002e/pwm1_enable: Permission denied
  0-002e/fan1_input ... speed was 5227 now 5227
/usr/sbin/pwmconfig: line 102: 0-002e/pwm1_enable: Permission denied
    no correlation

No correlations were detected.
There is either no fan connected to the output of 0-002e/pwm1,
or the connected fan has no rpm-signal connected to one of
the tested fan sensors. (Note: not all motherboards have
the pwm outputs connected to the fan connectors,
check out the hardware database on http://www.almico.com/forumindex.php)

Did you see/hear a fan stopping during the above test (n)?

Testing pwm control 0-002e/pwm2 ...
/usr/sbin/pwmconfig: line 117: 0-002e/pwm2_enable: Permission denied
  0-002e/fan1_input ... speed was 5227 now 5227
/usr/sbin/pwmconfig: line 102: 0-002e/pwm2_enable: Permission denied
    no correlation

No correlations were detected.
There is either no fan connected to the output of 0-002e/pwm2,
or the connected fan has no rpm-signal connected to one of
the tested fan sensors. (Note: not all motherboards have
the pwm outputs connected to the fan connectors,
check out the hardware database on http://www.almico.com/forumindex.php)

Did you see/hear a fan stopping during the above test (n)?

Testing pwm control 0-002e/pwm3 ...
/usr/sbin/pwmconfig: line 117: 0-002e/pwm3_enable: Permission denied
  0-002e/fan1_input ... speed was 5227 now 5232
/usr/sbin/pwmconfig: line 102: 0-002e/pwm3_enable: Permission denied
    no correlation

No correlations were detected.
There is either no fan connected to the output of 0-002e/pwm3,
or the connected fan has no rpm-signal connected to one of
the tested fan sensors. (Note: not all motherboards have
the pwm outputs connected to the fan connectors,
check out the hardware database on http://www.almico.com/forumindex.php)

Did you see/hear a fan stopping during the above test (n)?

Testing is complete.
Please verify that all fans have returned to their normal speed.

The fancontrol script can automatically respond to temperature changes
of your system by changing fanspeeds.
Do you want to set up its configuration file now (y)?
What should be the path to your fancontrol config file (/etc/fancontrol)?
Loading configuration from /etc/fancontrol ...

Select fan output to configure, or other action:
1) Change INTERVAL     3) Save and quit
2) Just quit           4) Show configuration
select (1-n): 4

Common Settings:
INTERVAL=10

```

Any idea how I can change the permission denied when accessing pwmX_enable (X=1,2,3)?

Thanks again for your prompt reply!

Tony David Potter

---

### Post by remmelt on 2006-08-07
:( [http://www.lm-sensors.org/ticket/2071](http://www.lm-sensors.org/ticket/2071)

That's not your exact motherboard, but it looks like the same error...

> Tried "chmod 644 /sys/bus/i2c/devices/0-002e/*enable*" and pwmconfig ran without complaint, but to no effect (fans did not appear to stop/start when tested). Fan speed is still constant.

According to [http://lists.debian.org/debian-user/2005/10/msg03283.html](http://lists.debian.org/debian-user/2005/10/msg03283.html) the lm85 kernel module needs to be patched to correct an Intel BIOS misfeature. I haven't tried this.

I'm sorry I can't help you more than this..

---

### Post by fakie_flip on 2006-08-07
Hackers who know about changing fan speed could be a dangerous and expensive thing. Window's XP is easily hacked through trojans, and if the people who got into a Window's XP computer were able to change the fans' speeds, BYE BYE cpu. Those things would be smoking without a fan. They can get hot.

---

### Post by fakie_flip on 2006-08-07
why is my cpu fan speed not being shown? i followed the directions.```
 You do not need any special privileges for this.
 Do you want to probe now? (YES/no):
Probing for PCI bus adapters...
Use driver `rivatv' for device 01:00.0: RIVA UVTNT2
Use driver `i2c-sis96x' for device 00:02.1: Silicon Integrated Systems SMBus Con troller
Probe succesfully concluded.

As you are not root, we can't load adapter modules. We will only scan
already loaded adapters.
If you have undetectable or unsupported adapters, you can have them
scanned by manually loading the modules before running this script.

 To continue, we need module `i2c-dev' to be loaded.
 If it is built-in into your kernel, you can safely skip this.
 i2c-dev is not loaded. As you are not root, we will just hope you edited
 `/etc/modules.conf' for automatic loading of
 this module. If not, you won't be able to open any /dev/i2c-* file.

 We are now going to do the adapter probings. Some adapters may hang halfway
 through; we can't really help that. Also, some chips will be double detected;
 we choose the one with the highest confidence value in that case.
 If you found that the adapter hung after probing a certain address, you can
 specify that address to remain unprobed. That often
 includes address 0x69 (clock chip).

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
 http://www2.lm-sensors.nu/~lm78/cvs/lm_sensors2/doc/lm_sensors-FAQ.html
 (FAQ #4.24.3) for further information.
 If you find out what chips are on your board, see
 http://secure.netroedge.com/~lm78/newdrivers.html for driver status.
ubuntu@ubuntu:~$ sudo sensors-detect
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
 Do you want to probe now? (YES/no):
Probing for PCI bus adapters...
Use driver `rivatv' for device 01:00.0: RIVA UVTNT2
Use driver `i2c-sis96x' for device 00:02.1: Silicon Integrated Systems SMBus Con troller
Probe succesfully concluded.

We will now try to load each adapter module in turn.
Load `rivatv' (say NO if built into your kernel)? (YES/no):
FATAL: Module rivatv not found.
Loading failed... skipping.
** Note: rivatv module is available at http://rivatv.sourceforge.net/
Module `i2c-sis96x' already loaded.
If you have undetectable or unsupported adapters, you can have them
scanned by manually loading the modules before running this script.

 To continue, we need module `i2c-dev' to be loaded.
 If it is built-in into your kernel, you can safely skip this.
 i2c-dev is not loaded. Do you want to load it now? (YES/no):
 Module loaded succesfully.

 We are now going to do the adapter probings. Some adapters may hang halfway
 through; we can't really help that. Also, some chips will be double detected;
 we choose the one with the highest confidence value in that case.
 If you found that the adapter hung after probing a certain address, you can
 specify that address to remain unprobed. That often
 includes address 0x69 (clock chip).

Next adapter: SiS96x SMBus adapter at 0x0c00
Do you want to scan it? (YES/no/selectively):
Client found at address 0x50
Probing for `SPD EEPROM'... Success!
    (confidence 8, driver `eeprom')
Probing for `DDC monitor'... Failed!
Probing for `Maxim MAX6900'... Failed!
Client found at address 0x51
Probing for `SPD EEPROM'... Success!
    (confidence 8, driver `eeprom')
Client found at address 0x69
Client found at address 0x6a

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
  Trying address 0x0290... Success!
    (confidence 7, driver `it87')
Probing for `IPMI BMC KCS'
  Trying address 0x0ca0... Failed!
Probing for `IPMI BMC SMIC'
  Trying address 0x0ca8... Failed!

Some Super I/O chips may also contain sensors. Super I/O probes are
typically a bit more dangerous, as we have to write to I/O ports to do
this. This is usually safe though.

Do you want to scan for Super I/O sensors? (YES/no):
Probing for `ITE 8702F Super IO Sensors'
  Failed! (0x8705)
Probing for `ITE 8705F Super IO Sensors'
  Success... found at address 0x0290
Probing for `ITE 8712F Super IO Sensors'
  Failed! (0x8705)
Probing for `Nat. Semi. PC87351 Super IO Fan Sensors'
  Failed! (skipping family)
Probing for `SMSC 47B27x Super IO Fan Sensors'
  Failed! (skipping family)
Probing for `VT1211 Super IO Sensors'
  Failed! (skipping family)
Probing for `Winbond W83627EHF/EHG Super IO Sensors'
  Failed! (skipping family)

Do you want to scan for secondary Super I/O sensors? (YES/no):
Probing for `ITE 8702F Super IO Sensors'
  Failed! (0x8705)
Probing for `ITE 8705F Super IO Sensors'
  Success... found at address 0x0290
Probing for `ITE 8712F Super IO Sensors'
  Failed! (0x8705)
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
  * Bus `SiS96x SMBus adapter at 0x0c00'
    Busdriver `i2c-sis96x', I2C address 0x50
    Chip `SPD EEPROM' (confidence: 8)
  * Bus `SiS96x SMBus adapter at 0x0c00'
    Busdriver `i2c-sis96x', I2C address 0x51
    Chip `SPD EEPROM' (confidence: 8)

Driver `it87' (should be inserted):
  Detects correctly:
  * ISA bus address 0x0290 (Busdriver `i2c-isa')
    Chip `ITE 8705F Super IO Sensors' (confidence: 9)


 I will now generate the commands needed to load the I2C modules.
 Sometimes, a chip is available both through the ISA bus and an I2C bus.
 ISA bus access is faster, but you need to load an additional driver module
 for it. If you have the choice, do you want to use the ISA bus or the
 I2C/SMBus (ISA/smbus)?

To make the sensors modules behave correctly, add these lines to
/etc/modules:

#----cut here----
# I2C adapter drivers
i2c-sis96x
i2c-isa
# I2C chip drivers
eeprom
it87
#----cut here----

Do you want to add these lines to /etc/modules automatically? (yes/NO)yes

ubuntu@ubuntu:~$ sudo modprobe i2c-sensor
FATAL: Module i2c_sensor not found.
ubuntu@ubuntu:~$ sudo modprobe i2c-viapro
ubuntu@ubuntu:~$ sudo modprobe i2c-isa
ubuntu@ubuntu:~$ sudo modprobe it87
ubuntu@ubuntu:~$ sudo depmod -a ( I canceled this because it didnt do anything)

ubuntu@ubuntu:~$
ubuntu@ubuntu:~$ sudo update-modules
ubuntu@ubuntu:~$ sensors
it87-isa-0290
Adapter: ISA adapter
VCore 1:   +1.65 V  (min =  +4.08 V, max =  +4.08 V)   ALARM
VCore 2:   +2.50 V  (min =  +4.08 V, max =  +4.08 V)   ALARM
+3.3V:     +6.40 V  (min =  +8.16 V, max =  +8.16 V)   ALARM
+5V:       +4.78 V  (min =  +6.85 V, max =  +6.85 V)   ALARM
+12V:     +12.22 V  (min = +16.32 V, max = +16.32 V)   ALARM
-12V:      -1.71 V  (min =  +3.93 V, max =  +3.93 V)   ALARM
-5V:       +2.36 V  (min =  +4.03 V, max =  +4.03 V)   ALARM
Stdby:     +4.95 V  (min =  +6.85 V, max =  +6.85 V)   ALARM
VBat:      +2.03 V
fan1:     3515 RPM  (min =    0 RPM, div = 8)
fan2:        0 RPM  (min =    0 RPM, div = 8)
fan3:        0 RPM  (min =    0 RPM, div = 2)
M/B Temp:    +36°C  (low  =    -1°C, high =    -1°C)   sensor = thermistor
CPU Temp:    +43°C  (low  =    -1°C, high =    -1°C)   sensor = thermistor
Temp3:       +44°C  (low  =    -1°C, high =    -1°C)   sensor = thermistor

ubuntu@ubuntu:~$
```

---

### Post by remmelt on 2006-08-07
Try sudo.

---

### Post by ExMachina on 2006-08-12
Sony Vaio 2.8 ghz p4

temp mon shows 135F.
 fan is moving i think coudl eb HDD hum <<
my read out on sensors = " no sensors found " how do i fix this?
Is there a nice gui type thing for fan control . Im very familiar wiht linux but, this lappy is my life and rather not kill it. 

Any hint / tips / tricks?

---

### Post by remmelt on 2006-08-12
If you can't be sure if what you are hearing is hd or fan hum, you have to ask yourself if you really need to lower the fan speed at all. Also, as stated, if you aren't a 110% sure of what you are doing, don't try this. It can kill your CPU if you aren't careful.

Having said that, it sounds like you haven't installed lm-sensors yet. Please check out the first post and tell me where you get stuck.

See here: [http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780)

---

### Post by ExMachina on 2006-08-12
I will now generate the commands needed to load the I2C modules.
 Sometimes, a chip is available both through the ISA bus and an I2C bus.
 ISA bus access is faster, but you need to load an additional driver module
 for it. If you have the choice, do you want to use the ISA bus or the
 I2C/SMBus (ISA/smbus)?


is were i get worried.
Like i said lappy = my life ...
But all the great peoele on the forums help me so much.
Also is there a "gui" type thing someoen has made? 
To switch fan though modes?

---

### Post by ExMachina on 2006-08-12
I choose ISA..

it looked to work.. but..

nothing works <.<
I dont wnat to lower the speed.. i want to be abel to change it.
Make fan speed faster would be nice.

---

### Post by fakie_flip on 2006-08-13
why isn't this howto put on the wiki? [http://www.wiki.ubuntu.com](http://www.wiki.ubuntu.com) It should be there.

---

### Post by remmelt on 2006-08-14
> **ExMachina said:**
> I choose ISA..

it looked to work.. but..

nothing works <.<
I dont wnat to lower the speed.. i want to be abel to change it.
Make fan speed faster would be nice.
If you haven't changed your fan speed, it's set to maximum. You can only lower the fan speed with this program. If you don't want to lower your speed, don't use it!

---

### Post by remmelt on 2006-08-14
> **fakie_flip said:**
> why isn't this howto put on the wiki? [http://www.wiki.ubuntu.com](http://www.wiki.ubuntu.com) It should be there.
I don't have the time right now! Next weekend at the earliest.

The first post needs to be updated (the code patch is no longer needed) before it can go in the wiki.

---

### Post by chrwei on 2007-04-10
running fiesty (dist-upgraded, not a clean install) on a Shutlte with a nForce2 chipset

for whatever reason, my pwm1_enable file already had the value "1" in it and the permissions were -r--r--r-- so there was a permission denied error.  chmod'ing that caused an I/O error.

I edited /usr/sbin/fancontrol and commented out the calls to pwmdisable and pwmenable and it works now.

---

### Post by starfry on 2007-05-23
Hello,
I can't get pwmconfig to work. It is responding with the following error mentioned earlier in this thread:
```

/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed

```

Now, I have tried to change the code as mentioned earlier, but I guess I have a later version because the code around line 68 does not look like that mentioned earlier:

```

MATCH='*/pwm[1-9]'
PWM=`echo $MATCH`
if [ "$SYSFS" = "1" -a "$MATCH" = "$PWM" ]
then
        # Deprecated naming scheme (used in kernels 2.6.5 to 2.6.9)
        MATCH='*/fan[1-9]_pwm'
        PWM=`echo $MATCH`
fi
if [ "$MATCH" = "$PWM" ]
then
        echo $0: 'There are no pwm-capable sensor modules installed'
        exit 1
fi

```

I looked for files similar to "pwm[1-9]" or "fan[1-9]" and could only find these:
```

-rw-r--r-- 1 root root 4096 2007-05-23 20:08 fan1_div
-r--r--r-- 1 root root 4096 2007-05-23 20:00 fan1_input
-rw-r--r-- 1 root root 4096 2007-05-23 20:08 fan1_min
-rw-r--r-- 1 root root 4096 2007-05-23 19:20 fan2_div
-r--r--r-- 1 root root 4096 2007-05-23 20:00 fan2_input
-rw-r--r-- 1 root root 4096 2007-05-23 20:08 fan2_min
-rw-r--r-- 1 root root 4096 2007-05-23 20:08 fan3_div
-r--r--r-- 1 root root 4096 2007-05-23 20:00 fan3_input
-rw-r--r-- 1 root root 4096 2007-05-23 20:08 fan3_min

```

I can see output from Sensors:

```

dual:~$ sensors
as99127f-i2c-0-2d
Adapter: SMBus Via Pro adapter at e800
VCore 1:   +1.71 V  (min =  +1.54 V, max =  +1.95 V)              
VCore 2:   +1.71 V  (min =  +1.54 V, max =  +1.95 V)              
+3.3V:     +3.31 V  (min =  +2.96 V, max =  +3.63 V)              
+5V:       +4.97 V  (min =  +4.49 V, max =  +5.51 V)              
+12V:     +11.92 V  (min =  +9.55 V, max = +14.41 V)              
-12V:      -2.10 V  (min =  -4.07 V, max =  -0.32 V)              
-5V:       -1.13 V  (min =  -1.76 V, max =  -0.82 V)              
fan1:     4500 RPM  (min =   -1 RPM, div = 2)                     
fan2:     4687 RPM  (min = 56250 RPM, div = 8)                     
fan3:        0 RPM  (min = 7031 RPM, div = 2)                     
M/B Temp:    +41°C  (high =   +70°C, hyst =   -32°C)          
CPU Temp:  +37.5°C  (high =   +67°C, hyst =   +60°C)          
temp3:     +39.0°C  (high =   +67°C, hyst =   +60°C)          
vid:      +1.750 V  (VRM Version 8.2)
alarms:   
beep_enable:
          Sound alarm enabled

```

Please if anyone can offer any pointers? The only solution at the moment is almost unthinkable: returning to Windows where my fans are very quiet.

---

### Post by chrwei on 2007-05-23
starfry:  that means you don't have any PWM enabled hardware, or the hardware you have has no linux driver.  you simply can't use fancontrol because your hardware does not have fan speed control support.

---

### Post by starfry on 2007-05-23
But my hardware must have fan control because it is controlled when in Windows.

My motherboard is an ASUS CUV4X-D (Coppermind PIII dual).

How do I find out if I need a Linux driver, and what might that driver be? If I know what module I need then I can try loading it.

Thanks for helping...

---

### Post by chrwei on 2007-05-23
there are other ways besides PWM to control the fan speed, and fancontrol doesn't support those ways.

see [http://vip.asus.com/forum/view.aspx?id=20060730030619838&board_id=1&model=P5WD2+Premium&page=1&SLanguage=en-us](http://vip.asus.com/forum/view.aspx?id=20060730030619838&board_id=1&model=P5WD2+Premium&page=1&SLanguage=en-us)

3 pin fan uses DC voltage control, 4 pin fans use PWM.  I'm not aware of any P3 fans with 4 pins.

---

### Post by foging on 2007-05-31
> **remmelt said:**
> 

And paste this in there:
```
#!/bin/sh
#
# Fancontrol start script.
#

set -e

# Defaults
DAEMON=/usr/sbin/fancontrol
PIDFILE=/var/run/fancontrol.pid
PATH=/sbin:/bin:/usr/sbin:/usr/bin

test -f $DAEMON || exit 0

. /lib/lsb/init-functions


case "$1" in
        start)
                log_begin_msg "Starting fancontrol daemon..."
                start-stop-daemon --start -o -q -m -b -p $PIDFILE -x $DAEMON
                log_end_msg $?
                ;;
        stop)
                log_begin_msg "Stopping fancontrol daemon..."
                start-stop-daemon --stop -o -q -p $PIDFILE
                log_end_msg $?
                ;;
        force-reload|restart)
                sh $0 stop
                sh $0 start
                ;;
        *)
                log_success_msg "Usage: /etc/init.d/fancontrol {start|stop|restart|force-reload}"
                log_success_msg "  start - starts system-wide fancontrol service"
                log_success_msg "  stop  - stops system-wide fancontrol service"
                log_success_msg "  restart, force-reload - starts a new system-wide fancontrol service"
                exit 1
                ;;
esac

exit 0

```



I can't get the startup script to work. When i reboot my computer and run >ps -e fancontrol isn't listed and the fans spin att full speed. I does however set a .pid-file in /var/run/ since it complains about it when i try to start manually. I'm using this fancontrol script: [http://volker.dnsalias.net/linux/tech/lm_sensors/fancontrol]("http://volker.dnsalias.net/linux/tech/lm_sensors/fancontrol") Could it be messing something up?

Running Ubuntu Feisty.

---

### Post by bomanizer on 2007-07-01
Hi,

I'm wondering.. does the script start every time the system boots up? How about surviving a hibernation? I think these are general init-script issues... or?

cheers

---

### Post by gheywood on 2007-07-27
I have got as far as running "sudo pwmconfig" and it successfully stops my fan so I can listen to it. However, when doing the config, it is never able to start or stop the fan with the "t" function. 

I run an ASUS M2M-MX motherboard. 

Is there some reason why it can stop the fan when pwmconfig is run, but cannot start/stop it when using the "t" option? 

I am a little concerned about using it otherwise, but it would be really nice to get it to work...

This is the output of the first run:

***************************************************************
greg@mediapc:/etc/init.d$ sudo pwmconfig
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
   9191-0290/fan1_input     current speed: 3245 RPM
   9191-0290/fan2_input     current speed: 0 ... skipping!
   9191-0290/fan3_input     current speed: 0 ... skipping!

Warning!!! This program will stop your fans, one at a time,
for approximately 5 seconds each!!!
This may cause your processor temperature to rise!!!
If you do not want to do this hit control-C now!!!
Hit return to continue: 

Testing pwm control 9191-0290/pwm1 ...
  9191-0290/fan1_input ... speed was 3245 now 5037
    no correlation

No correlations were detected.
There is either no fan connected to the output of 9191-0290/pwm1,
or the connected fan has no rpm-signal connected to one of
the tested fan sensors. (Note: not all motherboards have
the pwm outputs connected to the fan connectors,
check out the hardware database on [http://www.almico.com/forumindex.php](http://www.almico.com/forumindex.php))

Did you see/hear a fan stopping during the above test (n)?  
***************************************************************

It does successfully stop the fan..



Cheers

---

### Post by edfromballarat on 2007-10-03
Hi y'all,

Wondering if anybody could help me out.  Have followed howto for lm-sensors and fancontrol, seems to work okay until pwmconfig and then the fans don't stop when it says they should.

Set up lm-sensors and get output from sensors:

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:
             +37°C

w83627ehf-isa-0290
Adapter: ISA adapter
VCore:     +1.14 V  (min =  +0.00 V, max =  +1.74 V)
in1:      +12.41 V  (min =  +2.06 V, max =  +9.29 V) ALARM
AVCC:      +3.36 V  (min =  +1.02 V, max =  +2.69 V) ALARM
3VCC:      +3.38 V  (min =  +3.97 V, max =  +2.86 V) ALARM
in4:       +1.70 V  (min =  +0.86 V, max =  +1.75 V)
in5:       +1.73 V  (min =  +1.53 V, max =  +1.26 V) ALARM
in6:       +5.56 V  (min =  +6.02 V, max =  +5.04 V) ALARM
VSB:       +3.38 V  (min =  +3.95 V, max =  +0.61 V) ALARM
VBAT:      +0.26 V  (min =  +4.08 V, max =  +2.46 V) ALARM
in9:       +1.64 V  (min =  +0.09 V, max =  +0.38 V) ALARM
Case Fan: 1997 RPM  (min = 2766 RPM, div = 4) ALARM
CPU Fan:  3082 RPM  (min = 5232 RPM, div = 2) ALARM
Aux Fan:     0 RPM  (min =   68 RPM, div = 128) ALARM
fan5:        0 RPM  (min = 168750 RPM, div = 8) ALARM
Sys Temp:    +30°C  (high =  -127°C, hyst =   +58°C)
CPU Temp:  +27.5°C  (high = +80.0°C, hyst = +75.0°C)
AUX Temp:  +35.5°C  (high = +80.0°C, hyst = +75.0°C)

Then running 'pwmconfig':

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
/usr/sbin/pwmconfig: line 102: echo: write error: Invalid argument
   9191-0290/pwm2
/usr/sbin/pwmconfig: line 102: echo: write error: Invalid argument
   9191-0290/pwm3
/usr/sbin/pwmconfig: line 102: echo: write error: Invalid argument

Found the following fan sensors:
   9191-0290/fan1_input     current speed: 1985 RPM
   9191-0290/fan2_input     current speed: 3068 RPM
   9191-0290/fan3_input     current speed: 0 ... skipping!
   9191-0290/fan5_input     current speed: 0 ... skipping!

Warning!!! This program will stop your fans, one at a time,
for approximately 5 seconds each!!!
This may cause your processor temperature to rise!!!
If you do not want to do this hit control-C now!!!
Hit return to continue:

Testing pwm control 9191-0290/pwm1 ...
  9191-0290/fan1_input ... speed was 1985 now 2020
/usr/sbin/pwmconfig: line 102: echo: write error: Invalid argument
    no correlation
  9191-0290/fan2_input ... speed was 3068 now 3054
/usr/sbin/pwmconfig: line 102: echo: write error: Invalid argument
    no correlation

No correlations were detected.
There is either no fan connected to the output of 9191-0290/pwm1,
or the connected fan has no rpm-signal connected to one of
the tested fan sensors. (Note: not all motherboards have
the pwm outputs connected to the fan connectors,
check out the hardware database on [http://www.almico.com/forumindex.php](http://www.almico.com/forumindex.php))

Did you see/hear a fan stopping during the above test (n)? n

Testing pwm control 9191-0290/pwm2 ...
  9191-0290/fan1_input ... speed was 1985 now 1985
/usr/sbin/pwmconfig: line 102: echo: write error: Invalid argument
    no correlation
  9191-0290/fan2_input ... speed was 3068 now 3096
/usr/sbin/pwmconfig: line 102: echo: write error: Invalid argument
    no correlation

No correlations were detected.
There is either no fan connected to the output of 9191-0290/pwm2,
or the connected fan has no rpm-signal connected to one of
the tested fan sensors. (Note: not all motherboards have
the pwm outputs connected to the fan connectors,
check out the hardware database on [http://www.almico.com/forumindex.php](http://www.almico.com/forumindex.php))

Did you see/hear a fan stopping during the above test (n)? n

Testing pwm control 9191-0290/pwm3 ...
  9191-0290/fan1_input ... speed was 1985 now 2020
/usr/sbin/pwmconfig: line 102: echo: write error: Invalid argument
    no correlation
  9191-0290/fan2_input ... speed was 3068 now 3068
/usr/sbin/pwmconfig: line 102: echo: write error: Invalid argument
    no correlation

No correlations were detected.
There is either no fan connected to the output of 9191-0290/pwm3,
or the connected fan has no rpm-signal connected to one of
the tested fan sensors. (Note: not all motherboards have
the pwm outputs connected to the fan connectors,
check out the hardware database on [http://www.almico.com/forumindex.php](http://www.almico.com/forumindex.php))

Did you see/hear a fan stopping during the above test (n)? n

Testing is complete.
Please verify that all fans have returned to their normal speed.

The fancontrol script can automatically respond to temperature changes
of your system by changing fanspeeds.
Do you want to set up its configuration file now (y)? n

---

### Post by JohnLai on 2007-10-08
I can't seem to get the startup script to work either, any idea?

---

### Post by libos on 2007-10-22
Hi all,

I have a M2N-E MOBO with Athlon 3800 x2 processor. I got my fancontrol working with my MOBO.

I have written down what i did in my blog for my references in future. Anyone interested can refer to it. Hope this helps. :)

[http://bsling.blogspot.com/2007/06/fancontrol.html](http://bsling.blogspot.com/2007/06/fancontrol.html)
[http://bsling.blogspot.com/2007/10/configuring-fancontrol-further.html](http://bsling.blogspot.com/2007/10/configuring-fancontrol-further.html)

---

### Post by NeillHog on 2007-11-04
Thank you for the great how to.

I now have everything running and there is a direct correlation between CPU temperature and CPU fan speed as shown by KSensors (Kubuntu) so I assume that everything is running as it should. Automatic starting is also OK.

I just have one problem -

During the close down process for Kubuntu my CPU fan switches off completely. I assume that this is caused once it unloads fancontrol. 

Is there a command to unload fancontrol?
Can I do this automatically as a part of closing down Kubuntu? I suppose what I asking is "is there a way to automatically close fancontrol before continuing with the shut down process.

Thanks again for a great how to!

Neill

---

### Post by NeillHog on 2007-11-04
The problem is solved :-)

It only happens if I start fancontrol from hand in the console.
Doing it as in the how to and everything works. During shut down the fan speeds up!

Thank you!

---

### Post by libos on 2007-11-04
Was going to reply you.  :)

Yes, the fan speeds up. I guess once the script is unload, no software is taking control over the fan so all fans will go full speed.

---

### Post by braddyo on 2007-12-08
I get stuck at "Increasing fan_div" - here is my sensors output:

> bradford@bradford-desktop:~$ sensors
it8718-isa-0290
Adapter: ISA adapter
in0:       +1.25 V  (min =  +0.00 V, max =  +4.08 V)   
in1:       +1.87 V  (min =  +0.00 V, max =  +4.08 V)   
in2:       +3.31 V  (min =  +0.00 V, max =  +4.08 V)   
in3:       +2.98 V  (min =  +0.00 V, max =  +4.08 V)   
in4:       +0.88 V  (min =  +0.00 V, max =  +4.08 V)   
in5:       +0.00 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
in6:       +0.06 V  (min =  +0.00 V, max =  +4.08 V)   
in7:       +3.01 V  (min =  +0.00 V, max =  +4.08 V)   
in8:       +3.14 V
fan1:     2872 RPM  (min =   10 RPM)                   
fan2:        0 RPM  (min =    0 RPM)                   
fan3:        0 RPM  (min =    0 RPM)                   
temp1:       +34°C  (low  =  +127°C, high =  +127°C)   sensor = thermistor   
temp2:       +27°C  (low  =  +127°C, high =   +60°C)   sensor = diode   
temp3:        -2°C  (low  =  +127°C, high =  +127°C)   sensor = thermistor   
vid:      +0.000 V

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +42°C  (high =  +100°C)                   

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +38°C  (high =  +100°C)                   

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +35°C  (high =  +100°C)                   

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +35°C  (high =  +100°C)  

Notice that my fan1 is nearly 3000 rpm. In my case my cpi heatsink is facing sideways, and the fan blows air from the front, across the heatsink, and out the back. There is a 12cm fan on the back that runs much faster than my CPU fan - probably because it just sucks and the cpu fan doesn't have to work much. In my BIOS the case fan is always about 4-6x faster than the cpu fan. So I am not seeing my CPU fan speed. Following the instructions in the post to 

> look up your exact chipset. The names all look alike, so make sure the one you are editing is yours. Add the line fanX_div 4 near the start of your chipset config. Replace the X with the number of your CPU fan's, for me that was 2. You have to figure out for yourself which one it is, but it's probably 1, 2 or 3.

does NOT work, because I can't find a chip in the entire sensors.conf file that is named it8718. I found it871, it8712, and it8716, but NO it8718. I wonder if I need to create one myself, however I don't think that would be a good idea given my level of knowledge and the danger of permanently frying my computer. 

If any of you have any advice please give it!

B

---

### Post by libos on 2007-12-08
Not sure this can help you. I found the section to configure your chipset (it8718). I got the clue from 

[http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices)

Search for "it8718". It's using the it87 driver. In the sensors.conf file, i found the section at line 1537.

Good luck.  :)

---

### Post by JohnLai on 2007-12-18
I manage to configure the fancontrol properly, but now I want to disable the fancontrol completely. What step should I take? Delete the fancontrol script at /etc/init.d/fancontrol only?

---

### Post by Evil Dax on 2007-12-21
since Gutsy I'm unable to get it running at startup, while Feisty and Edgy worked smoothly... Any ideas?

---

### Post by tweedledee on 2008-01-03
JohnLai: In the event you haven't worked it out yet, you should delete /etc/init.d/fancontrol at a minimum, then execute ```

sudo update-rc.d fancontrol remove
``` to remove the links.  You can also delete the /etc/fancontrol file if you don't intend to return to using fancontrol.

Evil Dax: delete your /etc/fancontrol and start over.  When I upgraded to Gutsy, the names of the devices changed, so the old fancontrol settings did not work.  Actually, you probably want to note your exisiting configuration, so you can set it up the same way again using the original process.

---

### Post by LordKelvan on 2008-01-03
Hi:

I followed this helpful guide, and I have now successfully gotten the temperatures and fan speeds for my computer, just like in Windows.  I get the following output when I run 'sensors' from the terminal:

```

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:
             +37°C

w83627thf-isa-0290
Adapter: ISA adapter
VCore:     +1.43 V  (min =  +0.70 V, max =  +1.87 V)              
+12V:     +12.52 V  (min =  +4.62 V, max =  +4.32 V)       ALARM  
+3.3V:     +3.23 V  (min =  +0.77 V, max =  +3.60 V)              
+5V:       +4.93 V  (min =  +1.89 V, max =  +0.88 V)       ALARM  
-12V:     -12.03 V  (min = -10.96 V, max =  -4.38 V)       ALARM  
V5SB:      +5.00 V  (min =  +1.59 V, max =  +2.66 V)       ALARM  
VBat:      +2.93 V  (min =  +2.53 V, max =  +4.05 V)              
fan1:        0 RPM  (min = 6026 RPM, div = 4)              ALARM  
CPU Fan:  2596 RPM  (min = 2636 RPM, div = 8)              ALARM  
fan3:     6081 RPM  (min = 112500 RPM, div = 2)              ALARM  
M/B Temp:    +35°C  (high =   +74°C, hyst =    +0°C)   sensor = thermistor           
CPU Temp:  +36.0°C  (high =   +80°C, hyst =   +75°C)   sensor = thermistor           
temp3:     +15.0°C  (high =   +80°C, hyst =   +75°C)   sensor = diode           
vid:      +0.000 V  (VRM Version 2.4)
alarms:   
beep_enable:
          Sound alarm enabled

```

My problem is that I cannot get pwmconfig to work properly.  It seems that it is unable to stop any of my fans.  The following is the output I get when running pwmconfig from the terminal:

```

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
   hwmon0/device is k8temp
   hwmon1/device is w83627thf

Found the following PWM controls:
   hwmon1/device/pwm1
   hwmon1/device/pwm2
   hwmon1/device/pwm3

Found the following fan sensors:
   hwmon1/device/fan1_input     current speed: 0 ... skipping!
   hwmon1/device/fan2_input     current speed: 2556 RPM
   hwmon1/device/fan3_input     current speed: 6136 RPM

Warning!!! This program will stop your fans, one at a time,
for approximately 5 seconds each!!!
This may cause your processor temperature to rise!!!
If you do not want to do this hit control-C now!!!
Hit return to continue: 

Testing pwm control hwmon1/device/pwm1 ...
  hwmon1/device/fan2_input ... speed was 2556 now 2596
    no correlation
  hwmon1/device/fan3_input ... speed was 6136 now 6136
    no correlation

No correlations were detected.
There is either no fan connected to the output of hwmon1/device/pwm1,
or the connected fan has no rpm-signal connected to one of
the tested fan sensors. (Note: not all motherboards have
the pwm outputs connected to the fan connectors,
check out the hardware database on http://www.almico.com/forumindex.php)

Did you see/hear a fan stopping during the above test (n)? n

Testing pwm control hwmon1/device/pwm2 ...
  hwmon1/device/fan2_input ... speed was 2556 now 2596
    no correlation
  hwmon1/device/fan3_input ... speed was 6136 now 6136
    no correlation

No correlations were detected.
There is either no fan connected to the output of hwmon1/device/pwm2,
or the connected fan has no rpm-signal connected to one of
the tested fan sensors. (Note: not all motherboards have
the pwm outputs connected to the fan connectors,
check out the hardware database on http://www.almico.com/forumindex.php)

Did you see/hear a fan stopping during the above test (n)? n

Testing pwm control hwmon1/device/pwm3 ...
  hwmon1/device/fan2_input ... speed was 2556 now 2556
    no correlation
  hwmon1/device/fan3_input ... speed was 6136 now 6136
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
Do you want to set up its configuration file now (y)? n

```

I know that my motherboard is capable of controlling the fans, since I can control the fans in Windows using SpeedFan.

Can someone help me?  The fan noise is driving me nuts!!

Thanks,
LK

---

### Post by tweedledee on 2008-01-06
> **LordKelvan said:**
> I know that my motherboard is capable of controlling the fans, since I can control the fans in Windows using SpeedFan.

Can someone help me?  The fan noise is driving me nuts!!

Thanks,
LK

I had this problem on one of my desktops (which has the 83637hf chip and uses the 83627hf driver), and just found the solution today.  My BIOS was controlling the fan (but naturally did not have any configuration available).  To override the BIOS control, load your chip module (w83627thf in your case) with the paramter "reset=1".  To test this, first run
```
sudo modprobe -r w83627thf
``` to unload the module if you have already done a modprobe and/or put the module in your /etc/modules.  Then run
```
sudo modprobe w83627thf reset=1
``` and try pwmconfig again.  With luck, your fans will now be controllable.  If that does not work, you can also try "reset=0" and "init=0" instead of "reset=1" (based on Google searches, sometimes those work for other people).  Always unload the module between new modprobes, though, or it will just disregard the new load.  You'll have to add whichever command worked after the chip name in /etc/modules to ensure proper loading during boot.

Just for completeness, I should note that on my computer, the issue was that the BIOS was turning the fans so far down the computer was in serious danger of overheating when the processor was working hard - so when I used the "reset=1" command, my fans jumped up to full speed.  Since yours are already full speed, you may not notice any immediate change.

---

### Post by LordKelvan on 2008-01-06
tweedledee:  THANKS!!! Finally, it works (I tried it using "reset=1").  Now, I noticed a couple of things when trying this:

[LIST=1]
[*]Even though the chip name is w83627**t**hf, it actually uses the module w83627hf (it seems that module is used for both chips).  For example, I had to do 'sudo modprobe -r w83627hf' to unload the module.
[*]After I unloaded and reloaded the module, I noticed that when I ran 'sudo sensors' I had lost the CPU fan reading (it now reported 0 rpm with div=2), and that under beep_enable it said 'Sound alarm disabled' (it used to say 'Sound alarm enabled').  These changes persisted regardless of whether I reloaded the module without any extra parameters (i.e., 'sudo modprobe w83627hf') or with extra parameters (e.g., 'sudo modprobe w83627hf reset=1' or 'sudo modprobe w83627hf reset=0').  Hopefully the 'sound alarm' thing will be fixed with a restart, while I fixed the CPU fan reading thing using the method detailed below.
[*]In order to get back the CPU fan reading (i.e., the reading I mentioned losing above), I had to follow the guide (on pg. 1) on how to change the fan_div to get readings on fans which are running, but reported as 0 rpm.  For reference, I had to add the line 'set fan2_div 8' (it is fan2_div because my CPU fan is fan 2) to my /etc/sensors.conf file, under the section for w83627**t**hf.  Please note that the sections are according to chip name and NOT module name (I would imagine chip name and module name are usually the same, but they were a little different on my machine as I mentioned earlier in point #1).  This is why I placed it under the section for w83627**t**hf, and **NOT** w83627hf.
[/LIST]

Once again, things are finally working, so thank-you very very much to tweedledee, and of course, to remmelt for creating this guide in the first place.

Oh, one more thing - I think the guide forgets to mention that you should make the fancontrol file in /etc/init.d (NOT the one in /etc) executable.  I did so with the command:

```
sudo chmod +x fancontrol
```

Maybe remmelt could add this to his/her excellent guide.

---

### Post by tweedledee on 2008-01-06
> **LordKelvan said:**
> tweedledee:  THANKS!!! Finally, it works (I tried it using "reset=1").  Now, I noticed a couple of things when trying this:

[LIST=1]
[*]Even though the chip name is w83627**t**hf, it actually uses the module w83627hf (it seems that module is used for both chips).  For example, I had to do 'sudo modprobe -r w83627hf' to unload the module.
[*]After I unloaded and reloaded the module, I noticed that when I ran 'sudo sensors' I had lost the CPU fan reading (it now reported 0 rpm with div=2), and that under beep_enable it said 'Sound alarm disabled' (it used to say 'Sound alarm enabled').  These changes persisted regardless of whether I reloaded the module without any extra parameters (i.e., 'sudo modprobe w83627hf') or with extra parameters (e.g., 'sudo modprobe w83627hf reset=1' or 'sudo modprobe w83627hf reset=0').  Hopefully the 'sound alarm' thing will be fixed with a restart, while I fixed the CPU fan reading thing using the method detailed below.
[*]In order to get back the CPU fan reading (i.e., the reading I mentioned losing above), I had to follow the guide (on pg. 1) on how to change the fan_div to get readings on fans which are running, but reported as 0 rpm.  For reference, I had to add the line 'set fan2_div 8' (it is fan2_div because my CPU fan is fan 2) to my /etc/sensors.conf file, under the section for w83627**t**hf.  Please note that the sections are according to chip name and NOT module name (I would imagine chip name and module name are usually the same, but they were a little different on my machine as I mentioned earlier in point #1).  This is why I placed it under the section for w83627**t**hf, and **NOT** w83627hf.
[/LIST]

Once again, things are finally working, so thank-you very very much to tweedledee, and of course, to remmelt for creating this guide in the first place.



I neglected to mention I had a similar experience, using the w83627hf module but w83637hf chip (and did it take me a while to notice that 2->3 change), and also had to change the fan_div value for one of my fans.  I don't recall if I had any alarm status changes.  I'm not actually sure what the reset command does, other than allowing me to regulate the fan, but it is odd that it influences the display like that.  I'm not noted any other side effects so far, though, so I'll take it.

---

### Post by greys on 2008-03-30
Thanks for a great guide!

---

### Post by eje_s on 2008-04-06
I'm using a Asus A8N-SLI deluxe Nforce4 motherboard and had great problems getting fanspeed working. Speedfan under windows works, so I know that fan speed control is possible.

After many hours of googling I found out about kernel modules parameters and that solved my problem.

The chip found by sensors-detect is: it87 (it8712)
I don't use cool n' quiet, so by default the pwm controls is disabled, I'm not even sure that they will be enabled if so.
Newer kernels use /sys/class/hwmon/hwmon0/device/ as the base folder for these controls by the way. The goal is to have pwm[1-3] in that folder.

After the standard installation of lm-sensors I used these commands to solve my problem:
```
sudo modprobe -r it87
sudo modprobe it87 fix_pwm_polarity=1
ls /sys/class/hwmon/hwmon0/device/pwm*

```

The result should be that pwm1 to pwm3 now is listed.

Pwmconfig should now work as expected. However for me only pwm1 and 2 is usable and this is normal for my motherboard.

Now is the time to set up your fan control settings and enable fancontrol following any other guide. The later part of [http://ubuntuforums.org/showthread.php?t=42737](http://ubuntuforums.org/showthread.php?t=42737) for example.

I wish you a happy silent system!

---

### Post by sha_man on 2008-04-10
Hi, I do have the same problem LordKelvan had, but can't fix it with the solutions posted; pwmconfig always reports 'no correlation' :( I just want to lower the speed of the chassis fan, and it doesn't seem to work....

Here my 'sensors' output:

```
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:
             +33°C

w83627hf-isa-0290
Adapter: ISA adapter
VCore 1:   +1.30 V  (min =  +0.00 V, max =  +4.08 V)              
VCore 2:   +1.33 V  (min =  +0.00 V, max =  +4.08 V)              
+3.3V:     +3.33 V  (min =  +2.82 V, max =  +3.79 V)              
+5V:       +5.00 V  (min =  +0.48 V, max =  +5.30 V)              
+12V:     +12.04 V  (min =  +5.96 V, max =  +0.06 V)       ALARM  
-12V:      +1.46 V  (min =  -4.88 V, max = -10.96 V)       ALARM  
-5V:       +2.34 V  (min =  -7.01 V, max =  +0.33 V)       ALARM  
V5SB:      +5.48 V  (min =  +2.58 V, max =  +3.44 V)       ALARM  
VBat:      +0.02 V  (min =  +0.06 V, max =  +1.54 V)       ALARM  
fan1:     1622 RPM  (min = 9375 RPM, div = 8)              ALARM  
fan2:     1622 RPM  (min = 12053 RPM, div = 8)              ALARM  
fan3:        0 RPM  (min = 2033 RPM, div = 8)              ALARM  
temp1:       +30°C  (high =   +32°C, hyst =   +16°C)   sensor = thermistor           
temp2:     +28.5°C  (high =   +80°C, hyst =   +75°C)   sensor = thermistor           
temp3:     +27.0°C  (high =   +80°C, hyst =   +75°C)   sensor = thermistor           
vid:      +0.000 V  (VRM Version 2.4)
alarms:   
beep_enable:
          Sound alarm disabled

```


and here 'pwmconfig':

```
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
   hwmon0/device is k8temp
   hwmon1/device is w83627hf

Found the following PWM controls:
   hwmon1/device/pwm1
   hwmon1/device/pwm2

Found the following fan sensors:
   hwmon1/device/fan1_input     current speed: 1638 RPM
   hwmon1/device/fan2_input     current speed: 1622 RPM
   hwmon1/device/fan3_input     current speed: 0 ... skipping!

Warning!!! This program will stop your fans, one at a time,
for approximately 5 seconds each!!!
This may cause your processor temperature to rise!!!
If you do not want to do this hit control-C now!!!
Hit return to continue: 

Testing pwm control hwmon1/device/pwm1 ...
  hwmon1/device/fan1_input ... speed was 1638 now 1622
    no correlation
  hwmon1/device/fan2_input ... speed was 1622 now 1654
    no correlation

No correlations were detected.
There is either no fan connected to the output of hwmon1/device/pwm1,
or the connected fan has no rpm-signal connected to one of
the tested fan sensors. (Note: not all motherboards have
the pwm outputs connected to the fan connectors,
check out the hardware database on http://www.almico.com/forumindex.php)

Did you see/hear a fan stopping during the above test (n)? n

Testing pwm control hwmon1/device/pwm2 ...
  hwmon1/device/fan1_input ... speed was 1638 now 1638
    no correlation
  hwmon1/device/fan2_input ... speed was 1622 now 1654
    no correlation

No correlations were detected.
There is either no fan connected to the output of hwmon1/device/pwm2,
or the connected fan has no rpm-signal connected to one of
the tested fan sensors. (Note: not all motherboards have
the pwm outputs connected to the fan connectors,
check out the hardware database on http://www.almico.com/forumindex.php)

Did you see/hear a fan stopping during the above test (n)? n

Testing is complete.
```


Any ideas?

---

### Post by libos on 2008-04-10
Hi sha_man,

You might want to check out your mobo manual does your mobo comes with the pwm outputs. What is your mobo anyway?

---

### Post by sha_man on 2008-04-11
hey,
i have an Asrock 939Dual-SATA2 motherboard. Apparently, after some googling, i found out that other people with the same motherboard had similar problems with SpeedFan for windows (or whatever it's called). I think this motherboard does not allow any fan controlling.
What I will do, if nobody has any solution is to buy a hardware based controller.
Thanks anyway

---

### Post by PheonixKotori on 2008-05-26
sha_man: You've likely moved on since your last post, but I wanted to add this item for posterity.

One thing I haven't seen mentioned in fancontrol threads is the fact that some fans do not have speed sensors built-in. All my chassis fans are like that; you can tell because they only have 2 wires. fancontrol can adjust the pwm to their socket, but it has no idea how fast the fans are spinning. As such, pwmconfig always sees "no correlation," but I can physically inspect them to see that they have changed speeds.

This may not apply to your or anyone else's problem, but there you go.

---

### Post by dd976 on 2008-05-26
Thanks remmelt for the guide! I have a question though. I've tried sensors-detect, and nothing is found on my c600 laptop (which smells like it's melting btw). I just have no fan activity whatsoever, and the fan was working in xp when it was installed on this computer. I've tried looking at the bios screen, and can't find anything there. Does anyone have any suggestions? Or can you point me to the appropriate thread/post please? Thanks! I need to turn this comp off for a while now, before it starts to smoke.:(

---

### Post by cheetah1 on 2008-06-18
Well all that probably works well if you have a temp source.
Problem is that I don't quiet trust mine, as it is stuck on a constant 127°C.
The fan, however, is detected properly:

```
w83627hf-isa-0290
Adapter: ISA adapter
[...]
fan3:     2636 RPM  (min =   -1 RPM, div = 16)              ALARM
[...]
```

It also stopped during the pwmconfig test (although it is a 3-pin fan..), so it is controlable. Question is: is there something i can write in the fancontrol config file to set it to a constant RPM or voltage, or do I need some other app to do that?
My server really isn't working hard, running a wordpress blog with 5 visitors a day on an Athlon XP 1700+ with 512 MB of ram, so it's not like it's going to run hot if I set it at say 1800 RPM... Right now though, it sounds like a hurricane in my folks livingroom...

---

### Post by chrwei on 2008-06-18
fancontrol just cats stuff to the sys files for PWM, you could do that manually.

however, Athlon XP's tend to run on the hot side, especially the older ones, so lowering the fan speed may make it too hot.  does the temp in BIOS read a reasonable value?  adjust the fan speed and reboot check it after a while.  If the BIOS has a temp alarm set it to its loweest and see if you can trigger to, to make sure it works, then set it to 70C or 75C as a safety backup and let people know to unplug it if it squeals.

if you can spare the $20, just get a quieter fan, much safer thing to do since the older XP cpu's don't have thermal throttling, if it does overheat, it just catches fire where newer sysems will slow down and/or shut off via a BIOS function.

---

### Post by cheetah1 on 2008-06-18
> **chrwei said:**
> fancontrol just cats stuff to the sys files for PWM, you could do that manually.

however, Athlon XP's tend to run on the hot side, especially the older ones, so lowering the fan speed may make it too hot.  does the temp in BIOS read a reasonable value?  adjust the fan speed and reboot check it after a while.  If the BIOS has a temp alarm set it to its loweest and see if you can trigger to, to make sure it works, then set it to 70C or 75C as a safety backup and let people know to unplug it if it squeals.

if you can spare the $20, just get a quieter fan, much safer thing to do since the older XP cpu's don't have thermal throttling, if it does overheat, it just catches fire where newer sysems will slow down and/or shut off via a BIOS function.

As I said, the CPU temp sits constantly on 127,5°C, both in bios and when running sensors. The fan is pretty new, and way quieter, and it's supposed to be able to handle 3000+ CPUs. It appears to be out of stock, but it's similar to [this one]("http://www.datorbutiken.com/se/default.aspx?Product=XILCPUK8"), only the attatchment is different. Sorry about the Swedish, but I belive it can be understood anyway.

If you touch it when it's running, it's never particularly warm, usually just a couple of degrees warmer than room temperature.

An option, of course, would be to buy a harware fan controller with a proper temp sensor. I don't know. What do you think?

---

### Post by chrwei on 2008-06-18
I think its possible for a cpu core to get to 127C and have a cool to the touch HS when it is not installed properly.  I wouldn't expect it to run for very long that way, few weeks maybe.

if the BIOS says 127C, then it either really is at 127C or your mainboard and/or cpu are failing

---

### Post by cheetah1 on 2008-06-18
> **chrwei said:**
> I think its possible for a cpu core to get to 127C and have a cool to the touch HS when it is not installed properly.  I wouldn't expect it to run for very long that way, few weeks maybe.

if the BIOS says 127C, then it either really is at 127C or your mainboard and/or cpu are failing

Oh but please...
This machine has run for about 5 or 6 years, the last 6 months constantly and it has ALWAYS said 127,5.That is called a faulty thermistor wich is very common on older systems.

Also, the heatsink is new, perfectly well installed, with a good thermal compund. It is, with an another attatchment on it, able to cool a 3600+ Athlon 64 CPU. With my Athlon XP 1700+ almost constantly running at idle I would guess it's at about 30-35°C.

I am aware that these processors tend to run hot. That is why it's on that temperature with a coolingfan. A more modern, or better built processor wouldn't need a fan to stay on that temperature.

Please tell me how to lower the RPM instead of trying to tell me that something is or will become broken. I know my hardware, but I'm not that good with Ubuntu.

---

### Post by libos on 2008-06-18
You could just tweak the config file to set MINSTART and MINSTOP to the same PWM value depends on your comfortable noise level. This should get your fan speed constant for all temp values.

Hope this helps.

[http://bsling.blogspot.com/search?q=fancontrol](http://bsling.blogspot.com/search?q=fancontrol)

---

### Post by cheetah1 on 2008-06-23
Okey, great, now it works.
Until I close down putty, then the fan STOPS! So, ehm.. What do I do to keep it spinning? Without having to have putty running?
I could, of course, use a monitor and set it up directly, but should that really be necessary?

---

### Post by GladSepp on 2008-08-16
Hi guys !

I have this when I execute 'sensors':> 
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +35.0°C  (crit = +100.0°C)                  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +36.0°C  (crit = +100.0°C)

And for pwmconfig I get:
> /usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed


My fans are always at their maximum speed and it's very loud (I had the same problem under XP). My notebook is an MSI GX700-046 (Performance Edition).

Don't hesitate if you have any idea to slow them a bit...

---

### Post by iconoclast36 on 2008-09-29
Peace:

I'm having trouble running fancontrol adequately and need help restoring my system to it's defaults. 

If anyone out there can help me control the fans on my computer, step-by-step, I'd appreciate it. I've installed lm-sensors and run pwmconfig, but am having difficulty with some of the configuration settings. 

I'm working off a Sony Vaio PCV-RX463DS on Xubuntu Hardy. With 'sensors' I get the following readout: 

w83627hf-isa-0290
Adapter: ISA adapter
VCore 1:     +1.70 V  (min =  +1.65 V, max =  +2.05 V)
VCore 2:     +2.50 V  (min =  +1.65 V, max =  +2.05 V)
+3.3V:       +3.31 V  (min =  +2.82 V, max =  +3.79 V)
+5V:         +5.08 V  (min =  +3.87 V, max =  +4.84 V)
+12V:       +11.86 V  (min =  +9.61 V, max =  +5.41 V)
-12V:       -12.28 V  (min =  +1.54 V, max = -11.04 V)
-5V:         +3.54 V  (min =  +4.25 V, max =  -4.44 V)
V5SB:        +5.54 V  (min =  +1.61 V, max =  +0.22 V)
VBat:        +0.27 V  (min =  +1.46 V, max =  +1.36 V)
fan1:          0 RPM  (min = 5769 RPM, div = 2)
fan2:       2136 RPM  (min = 10546 RPM, div = 4)
fan3:          0 RPM  (min = 6428 RPM, div = 2)
temp1:       -48.0°C  (high = -91.0°C, hyst = +18.0°C)  sensor = thermistor
temp2:       +41.0°C  (high = +100.0°C, hyst = +90.0°C)  sensor = diode
temp3:       +41.0°C  (high = +122.0°C, hyst = +121.0°C)  sensor = thermistor
cpu0_vid:   +1.750 V
beep_enable:enabled

***
My aim is to regulate the fans akin to how they ran in Windows -- i.e., system boots up, fans quiet down and start up again when system heats up.  Presently the fans are fluctuating in speed -- and 'fan1' showing 0 RPMs worries me.

Thanks, everyone ;-)

---

### Post by Apollo11 on 2008-11-05
Hello everyone!

After upgrade 8.04 to 8.10 my fans are on full speed all the time. :confused:
```
:~$ sensors
it8718-isa-0290
Adapter: ISA adapter
in0:         +1.15 V  (min =  +0.00 V, max =  +4.08 V)   
in1:         +1.82 V  (min =  +0.00 V, max =  +4.08 V)   
in2:         +3.26 V  (min =  +0.00 V, max =  +4.08 V)   
in3:         +4.08 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
in4:         +3.10 V  (min =  +0.00 V, max =  +4.08 V)   
in5:         +0.00 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
in6:         +1.28 V  (min =  +0.00 V, max =  +4.08 V)   
in7:         +4.08 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
in8:         +4.08 V
fan1:      ** 2136** RPM  (min =    0 RPM)
fan2:       **2960** RPM  (min =    0 RPM)
fan3:          0 RPM  (min =    0 RPM)
temp1:       -54.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = transistor
temp2:        -1.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = transistor
temp3:       +14.0°C  (low  = +127.0°C, high = +70.0°C)  sensor = thermal diode
cpu0_vid:   +0.000 V

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +42.0°C  (high = +86.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +42.0°C  (high = +86.0°C, crit = +100.0°C)
```
```
:~$ uname -a
Linux apollo 2.6.27-7-generic #1 SMP Thu Oct 30 04:12:22 UTC 2008 x86_64 GNU/Linux
```


I can't control them. They're making so much noise I can't work on Ubuntu any more. Temperature also seems odd (minus 54?) but on 8.04 was the same (however bios shows diffrently) and fan control was ok.  most of the time about 1000 rpm. I've tried to change pwmconfig and made mkdev.sh as was before but with no efect. 


P.S. Sorry for my English, I'm from Poland. ):P

---

### Post by borgibo on 2008-11-06
This is from a super newbie, to show my appreciation for the Fancontrol howto by remmelt.

I followed  the instructions and succeeded in my 64Studio distro to render the fan speed rolling happily at around 350rpm ! with a cpu temp of around 36C ! My fan is a 12cm 'Coolermaster RR-CCH-PBU1-GP GEMINII S' with 1900 rpm max. ( Mobo Gigabyte GA-M61PME-S2, ram 2GB, cpu AMD64 x2 3800+ ).

I just now was able to activate pwm on reboot too, automatically, after I followed remmelt's next day's instructions ( June 20th, 2005 ) !

The only 2 things extra that I had to do, possibly due to not understanding the instructions properly, was that I had to configur both pwm1 and pwm3 ( pwm2 did not seem to have any effect ),to attain low speed,  and I had to disable the 'smart' fan control from the mobo, otherwise it took over and raised the speed to around 1200 rpm.

borgibo:)

---

### Post by Apollo11 on 2008-11-06
This is what I get from fancontrol:
```
~$ sudo fancontrol
Loading configuration from /etc/fancontrol ...

Common settings:
  INTERVAL=2

Settings for hwmon0/device/pwm2:
  Depends on hwmon0/device/temp2_input
  Controls hwmon0/device/fan2_input+hwmon0/device/fan1_input
  MINTEMP=20
  MAXTEMP=60
  MINSTART=10
  MINSTOP=10
  MINPWM=0
  MAXPWM=255

Settings for hwmon0/device/pwm3:
  Depends on hwmon0/device/temp3_input
  Controls hwmon0/device/fan2_input+hwmon0/device/fan1_input
  MINTEMP=20
  MAXTEMP=60
  MINSTART=0
  MINSTOP=0
  MINPWM=0
  MAXPWM=255

Settings for hwmon0/device/pwm1:
  Depends on hwmon0/device/temp3_input
  Controls 
  MINTEMP=20
  MAXTEMP=60
  MINSTART=45
  MINSTOP=45
  MINPWM=0
  MAXPWM=255

Enabling PWM on fans...
Starting automatic fan control...
/usr/sbin/fancontrol: line 304: hwmon0/device/fan2_input+hwmon0/device/fan1_input: No such file or directory
Error reading Fan value from /sys/class/hwmon/hwmon0/device/fan2_input+hwmon0/device/fan1_input
Aborting, restoring fans...
Verify fans have returned to full speed

```
:confused:

---

### Post by thierrybo on 2008-11-25
Just one question. Do we need fancontrol any more with PWM fans? 

As I understand, a PWM fan with a PWM enabled bios does more or less what fancontrol do, and automatically handled by bios?

---

### Post by Hoyland84 on 2008-12-23
Thanks for this great HOWTO! I now have full control over the CPU fan and noise level has been reduced considerably. However the two chassis fans still make quite a lot of noise. They seem to be running at a constant full speed. I have one fan sucking in and one blowing out. They are not equipped with any RPM sensors and are parallel coupled from the same source. It doesn't seem to be a way to tweak them in the BIOS setup either.

Is there a way to reduce the voltage going out to these fans and by that way reduce their speed? I know this is possible by installing hardware and tune the voltage manually but I wondered if there is a way to do this with fancontrol or any other software.

My sensors readout:
```

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +34.0°C                                    
Core1 Temp:  +27.0°C                                    

it8712-isa-0290
Adapter: ISA adapter
VCore 1:     +1.14 V  (min =  +0.00 V, max =  +4.08 V)   
VCore 2:     +4.08 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
+3.3V:       +3.30 V  (min =  +0.00 V, max =  +4.08 V)   
+5V:         +6.85 V  (min =  +0.00 V, max =  +6.85 V)   ALARM
+12V:       +12.54 V  (min =  +0.00 V, max = +16.32 V)   
-12V:       -15.46 V  (min = -27.36 V, max =  +3.93 V)   
-5V:         +4.03 V  (min = -13.64 V, max =  +4.03 V)   ALARM
Stdby:       +6.85 V  (min =  +0.00 V, max =  +6.85 V)   ALARM
VBat:        +3.15 V
fan1:        872 RPM  (min =    0 RPM)
fan2:          0 RPM  (min =    0 RPM)
M/B Temp:    +32.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = transistor
CPU Temp:    +28.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = transistor
Temp3:      +128.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = disabled
cpu0_vid:   +1.550 V


```

---

### Post by downhillgames on 2008-12-28
> **Hoyland84 said:**
> They are not equipped with any RPM sensors and are parallel coupled from the same source. It doesn't seem to be a way to tweak them in the BIOS setup either.[...]but I wondered if there is a way to do this with fancontrol or any other software.
You could buy some 4-pin-to-3-pin connectors and plug them directly into your motherboard if it has the jacks. Places like xoxide, newegg, zipzoomfly, frozencpu, etc. all sell those types of parts. Take a look and see what you can find; they're really, really cheap if you shop around, usually.

Hey OP & contributors, thanks a lot for the howto. Worked great on this socket 939 mobo! (DFI Lanparty Ultra-D)

Cheers!
-Downhill

PS: Wish they'd make the process easier, though. If it's gonna probe for when the fan stops anyway, why not use the numbers it collects automatically? *sigh* Well, at least it works well enough to get the job done.

---

### Post by flapane on 2008-12-30
works for me:
Sensor: w83627hf

INTERVAL=10
FCTEMPS= hwmon0/device/pwm2=hwmon0/device/temp2_input
FCFANS= hwmon0/device/pwm2=hwmon0/device/fan1_input
MINTEMP= hwmon0/device/pwm2=36
MAXTEMP= hwmon0/device/pwm2=53
MINSTART= hwmon0/device/pwm2=2
MINSTOP= hwmon0/device/pwm2=0
MINPWM= hwmon0/device/pwm2=0
MAXPWM= hwmon0/device/pwm2=255

```

-=[ CPU Full: Detected 2004.568 MHz processor. ]=-
-=[ CPU Mhz: 1896.000 ]=-
-=[ CPU Temp.: +42.0°C ]=-
-=[ CPU Vcore: +1.425 ]=-
-=[ CPU Fan: 3924 ]=-

-=[ CPU Mhz: 1404.000 ]=-
-=[ CPU Temp.: +41.5°C ]=-
-=[ CPU Vcore: +1.425 ]=-
-=[ CPU Fan: 3924 ]=-

-=[ CPU Mhz: 1404.000 ]=-
-=[ CPU Temp.: +40.0°C ]=-
-=[ CPU Vcore: +1.425 ]=-
-=[ CPU Fan: 3924 ]=-

-=[ CPU Mhz: 1404.000 ]=-
-=[ CPU Temp.: +37.5°C ]=-
-=[ CPU Vcore: +1.425 ]=-
-=[ CPU Fan: 3792 ]=-

-=[ CPU Mhz: 1404.000 ]=-
-=[ CPU Temp.: +36.5°C ]=-
-=[ CPU Vcore: +1.425 ]=-
-=[ CPU Fan: 3668 ]=-

-=[ CPU Mhz: 1404.000 ]=-
-=[ CPU Temp.: +36.0°C ]=-
-=[ CPU Vcore: +1.425 ]=-
-=[ CPU Fan: 0 ]=-
```


```
w83627hf-isa-0290
Adapter: ISA adapter
VCore 1:   +1.38 V  (min =  +3.18 V, max =  +3.58 V)       ALARM
VCore 2:   +2.59 V  (min =  +3.18 V, max =  +3.58 V)       ALARM
+3.3V:     +3.31 V  (min =  +2.82 V, max =  +3.79 V)
+5V:       +5.05 V  (min =  +2.02 V, max =  +5.30 V)
+12V:     +11.92 V  (min =  +7.30 V, max =  +1.95 V)       ALARM
-12V:     -11.87 V  (min =  -7.26 V, max =  -4.30 V)       ALARM
-5V:       -5.10 V  (min =  -7.01 V, max =  -4.39 V)
V5SB:      +5.43 V  (min =  +4.92 V, max =  +1.61 V)       ALARM
VBat:      +3.57 V  (min =  +1.14 V, max =  +1.65 V)       ALARM
fan1:     3629 RPM  (min = 3443 RPM, div = 4)
fan2:        0 RPM  (min = 2205 RPM, div = 4)              ALARM
fan3:        0 RPM  (min = 1562 RPM, div = 4)              ALARM
temp1:       +28°C  (high =   -74°C, hyst =   +20°C)   sensor = thermistor   ALARM
temp2:     +36.5°C  (high =   +60°C, hyst =   +55°C)   sensor = thermistor           (beep)
temp3:     -47.0°C  (high =   +60°C, hyst =   +55°C)   sensor = thermistor
vid:      +1.425 V  (VRM Version 9.0)
alarms:
beep_enable:
          Sound alarm enabled


```

```
PC statistic
-=[ Kernel info: 2.6.22-14-386 ]=-
-=[ Ubuntu 7.10 ]=-
-=[ CPU Info: AMD Athlon(tm)  ]=-
-=[ CPU Full: Detected 2004.568 MHz processor. ]=-
-=[ CPU Mhz: 1404.000 ]=-
-=[ CPU Temp.: +37.0°C ]=-
-=[ CPU Vcore: +1.425 ]=-
-=[ CPU Fan: 3629 (pwm 20)]=-
-=[ Incoming/Outgoing: (26.2MB) / (5.9MB) ]=-
-=[ Used/Total memory: 145 MB / 504 MB ]=-
-=[ Uptime: 3 hour, 14 min, 57 sec ]=-

```

---

### Post by tjansson on 2009-05-19
I have been running the init.d script for a long time using 8.04 flawlessly. I recently upgraded to 9.04 and even though /usr/sbin/fancontrol still works as usual the init script does not. 

Has something changed in way Ubuntu interprets the script? Furthermore I tried to find the log file where errors would be located but none of the log files in /var/log contains any information on fancontrol.

---

### Post by gam3r on 2009-05-24
hey guys - can anyone help me?

First time i set this up it worked fine, but when i rebooted the computer my fancontrol stopped working.

here is what i get when i try to run it manually:
> 
kevalp@ ~ $ fancontrol
File /var/run/fancontrol.pid exists, is fancontrol already running?

                         
kevalp@ ~ $ sudo /etc/init.d/fancontrol stop
 * Stopping fancontrol daemon...                                                start-stop-daemon: warning: failed to kill 6713: No such process
                                                                         [ OK ]
kevalp@ ~ $ fancontrol
File /var/run/fancontrol.pid exists, is fancontrol already running?
kevalp@ ~ $ 


any idea?

---

### Post by jazzminos on 2009-06-15
Hi, friends. Sorry for offtopic. Is here someone who can help me and others to solve fans problem on Mac Os (Hackintosh Toshiba Laptop). I'm suffering with the extreme overheating problem caused by fans stop at boot. The topic is here [http://www.insanelymac.com/forum/index.php?showtopic=101271&st=240&gopid=1178198&#entry1178198](http://www.insanelymac.com/forum/index.php?showtopic=101271&st=240&gopid=1178198&#entry1178198) . My email: jazzminosDOGgmailDOTcom .

Thanks for attention.

With great respect, jazzminos.

---

### Post by jsa13 on 2009-07-19
OMFG, I had forgotten what "silence" meant.  THANK YOU!!!

PS Worked great on 9.04!

---

### Post by jsa13 on 2009-07-19
> **gam3r said:**
> hey guys - can anyone help me?

First time i set this up it worked fine, but when i rebooted the computer my fancontrol stopped working.

here is what i get when i try to run it manually:


any idea?

Try deleting the fancontrol PID file displayed in the error.  

Appears the the process was killed w/o using the init.d script and the option "stop".

---

### Post by rushthedj on 2009-08-01
Hi guys, great thread - I've got this so close to working on Jaunty.

The /etc/init.d/fancontrol script won't work unless I sudo it, which means it won't run on startup. Any ideas why it's working for all of you lot but not me? I've only been using Linux for a few weeks so apologies if I'm being stupid!

In case it's useful here's what happens when I run it (I've edited the script to remove the --background suffix from the start-stop-daemon command so you can see what's going on):

> rory@Reg:~$ /etc/init.d/fancontrol start
 * Starting fan speed regulator fancontrol                                      /usr/sbin/fancontrol: line 50: /var/run/fancontrol.pid: Permission denied
Loading configuration from /etc/fancontrol ...

Common settings:
  INTERVAL=10

Settings for hwmon2/device/pwm1:
  Depends on hwmon2/device/temp1_input
  Controls hwmon2/device/fan1_input
  MINTEMP=40
  MAXTEMP=55
  MINSTART=80
  MINSTOP=45
  MINPWM=0
  MAXPWM=255

Enabling PWM on fans...
/usr/sbin/fancontrol: line 230: hwmon2/device/pwm1_enable: Permission denied
Error enabling PWM on /sys/class/hwmon/hwmon2/device/pwm1
Aborting, restoring fans...
/usr/sbin/fancontrol: line 198: hwmon2/device/pwm1_enable: Permission denied
Verify fans have returned to full speedCheers, Rory

---

### Post by d4v1dv00 on 2009-08-03
anyone has the pwconfig file for jaunty? the line 68 does not seems to be aligned with what mentioned in the root of this topic?

my line 68 script block:

DIR=/proc/sys/dev/sensors
if [ ! -d $DIR ]
then
	if [ -d "/sys/class/hwmon" ]
	then
		SYSFS=2
		DIR="/sys/class/hwmon"
	elif [ -d "/sys/bus/i2c/devices" ]
	then
		SYSFS=1
		DIR="/sys/bus/i2c/devices"
	else
		echo $0: 'No sensors found! (modprobe sensor modules?)'
		exit 1
	fi	
fi

---

### Post by djurny on 2009-08-03
attached is a gzip'ed tar file containing a modified /etc/fancontrol configuration file and a diff to generate a modified /usr/[local/]sbin/fancontrol..
some things i added are:
- multiple sensors per output
now you can have a fan controlled by lets say, 4 averaged or maximized coretemp readings instead of 1 cpu case temp sensor..
- "peak/hold" like operation
instead of fancontrol maxing out and idling fans on intermittent loads, the last highest pwm value is held on to for a specified amount of seconds..

maybe an idea to add these to the howto as a nice add-on?

anyway, let me know how you like it (or not) :)

---

### Post by Nerevar144 on 2009-08-05
I've been trying to lower my power fan speed for a few hours now and I can't seem to crack it.  I followed the guide and I get hung up on the pwmconfig command which gives me the  "There are no pwm-capable sensor modules installed" message.  I have a fintek super I/O chip.  I was stumbling around and found this on the lm-sensors web site.  Here's the url: [http://www.lm-sensors.org/ticket/2332](http://www.lm-sensors.org/ticket/2332)

That seems to be what i need, however it refers to a .patch file.  How does it work.  It appears to have html code in it.  I'm CONFUSED...  Hardware sensors are loaded and working as the hardware sensors applet is running and gives me cpu, gpu, hdd temps and cpu, and system fan speeds.  I just can't seem to adjust them.  (I bought an aftermarket CPU fan that is rated at just over 1 AMP and it's running at 3350 RPM which is kinda loud.  I'd like to run it at half that :).

---

### Post by djurny on 2009-08-06
> **Nerevar144 said:**
> I've been trying to lower my power fan speed for a few hours now and I can't seem to crack it.  I followed the guide and I get hung up on the pwmconfig command which gives me the  "There are no pwm-capable sensor modules installed" message.  I have a fintek super I/O chip.  I was stumbling around and found this on the lm-sensors web site.  Here's the url: [http://www.lm-sensors.org/ticket/2332](http://www.lm-sensors.org/ticket/2332)

That seems to be what i need, however it refers to a .patch file.  How does it work.  It appears to have html code in it.  I'm CONFUSED...  Hardware sensors are loaded and working as the hardware sensors applet is running and gives me cpu, gpu, hdd temps and cpu, and system fan speeds.  I just can't seem to adjust them.  (I bought an aftermarket CPU fan that is rated at just over 1 AMP and it's running at 3350 RPM which is kinda loud.  I'd like to run it at half that :).

google 'patch' and 'diff' and you will find your answers ;)

edit: [http://www.linuxforums.org/articles/using-diff-and-patch_80.html](http://www.linuxforums.org/articles/using-diff-and-patch_80.html)

---

### Post by zulek87 on 2009-11-26
Hi!

I did not want to set up new topic.

My mb has option that can automatically control fan speed, but rpm's are too high, so I want to decrease them. _I also can use lm-sensors to do that, but if I start fancontrol and stop it, my fan is on max speed_, I saw in script (**/usr/sbin/fancontrol**) part of code responsible for it:

```

**function restorefans()**
{
    local status=$1
    echo 'Aborting, restoring fans...'
    let fcvcount=0
    while (( $fcvcount < ${#AFCPWM[@]} )) # go through all pwm outputs
    do
        pwmo=${AFCPWM[$fcvcount]}
        pwmdisable $pwmo
        let fcvcount=$fcvcount+1
    done
    echo 'Verify fans have returned to full speed'
    rm -f "$PIDFILE"
    exit $status
}
```As we can see fans are restored to the max rpms. How to give back control to the BIOS when I stop fancontrol?

P.S.
I know, that fancontrol is for ppl who do not have this option in BIOS, so it's normal, that fans are restored to their max, but maybe there is a way to manage this?

Thanks for help!

---

### Post by chrwei on 2009-11-28
if the BIOS fan control isn't slowing down the fan enough, you have a cooling issue, or just a noisy fan.  forcing it to run slower is likely to cause too much heat and then CPU damage.  Keep in mind that lm-sensors isn't always exactly calibrated and so the temps you see can be quite wrong.

---

### Post by iminhell on 2009-12-14
I can't figure this thing out for the life of me. I went by a different install how-to because with it I gained control of my fan, though I use 'control' loosely. Right now my fan pulses and I have very little control over it. I can change the speed it spins to but not the speed it spins down to. ~4100 and 1900 respectively. It does not start on startup/reboot, I have to run:
```
sudo /usr/sbin/fancontrol
```
via terminal. I'm fine with that because at least I can turn it on at my discretion.

> Take the modprobe lines it recommends and paste them into the appropriate /etc/rc.d/xxxx file to be executed at startup.
[http://www.lm-sensors.org/wiki/FAQ/Chapter2](http://www.lm-sensors.org/wiki/FAQ/Chapter2)

That is confusing to me. I took a chance and edited what:
```
sudo sensors-detect
```
output:
> # Chip drivers
w83627hf

Then found "w83627hf" in "/etc/sensors.conf" and edit "set temp1_over 38" (line 512) and "set temp1_hyst 30" (line 513). Values prior where 50 and 37. I thought this would turn the fan on to a higher speed at a lower temp, seems not though.

Maybe the fan is supposed to pulse, kinda doubt it though. Being I haven't seen it work in person . . .


So what do you guys need so you can help me get this thing working properly?



(Wish it where nice and simple like Speedfan for Windows, set a speed and let it go, adjust on the fly as desired)

---

### Post by mhousel on 2009-12-28
> I can't figure this thing out for the life of me.

Same boat here...

Can't figure out fancontrl, nothing works like the examples.
Can't figure out pwmconfig either, nothing works like the examples.

**From another thread I tried:**

 Re: HOW TO: Install and configure lm-sensors
I've tried all of this and still nothing will allow me to kep the fans running on my Toshiba satellite laptop.

The lm-sensors and sensor-detect do not work as shown here on this particular laptop it seems.
I can't get the sensor-applet to run either. (It is installed but not in /usr/bin as is the sensors executable)

#sensors
acpitz-virtual-0
Adapter: Virtual device
temp1: +59.0°C (crit = +104.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0: +59.0°C (high = +100.0°C, crit = +100.0°C)

coretemp-isa-0001
Adapter: ISA adapter
Core 1: +60.0°C (high = +100.0°C, crit = +100.0°C)

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
state: ok

NOTE: This matches the sensors output and the output shown on the toolbar by kSensors.

cat /proc/acpi/thermal_zone/THRM/temperature
temperature: 54 C

cat /proc/acpi/thermal_zone/THRM/trip_points
critical (S5): 104 C
passive: 104 C: tc1=2 tc2=3 tsp=40 devices=CPU0

And I've tried the things I can find related to changing the argument in grub:

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=" acpi_osi=force"
// tried these (Yeah, I ran grub-update between boots:
// quiet splash acpi_osi=Linux
// quiet splash acpi_osi=force
// quiet splash
// removing quiet and splash even though they have NOTHING to do with it.
// Nothing changes in the fan behavior.
#quiet splash
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

Oh, and also the things related to HOWTO Fix A Buggy DSDT File
If I decompile and recompile my DSDT file the only errors are related to some sort of warnings about line terminators, nothing in the code itself.

---

### Post by Menthu_Rae on 2009-12-31
[SIZE="4"]For anyone having errors running "start" or "stop" for /etc/init.d/fancontrol[/SIZE], please use this as your /etc/init.d/fancontrol file:

```
#!/bin/sh
#
# Fancontrol start script.
#

set -e

# Defaults
DAEMON=/usr/sbin/fancontrol
PIDFILE=/var/run/fancontrol.pid
PATH=/sbin:/bin:/usr/sbin:/usr/bin

test -f $DAEMON || exit 0

. /lib/lsb/init-functions


case "$1" in
        start)
                log_begin_msg "Starting fancontrol daemon..."
                start-stop-daemon --start -o -q -m -b --pidfile $PIDFILE -x $DAEMON
                log_end_msg $?
                ;;
        stop)
                log_begin_msg "Stopping fancontrol daemon..."
                start-stop-daemon --stop -o -q --pidfile $PIDFILE
                log_end_msg $?
                ;;
        force-reload|restart)
                sh $0 stop
                sh $0 start
                ;;
        *)
                log_success_msg "Usage: /etc/init.d/fancontrol {start|stop|restart|force-reload}"
                log_success_msg "  start - starts system-wide fancontrol service"
                log_success_msg "  stop  - stops system-wide fancontrol service"
                log_success_msg "  restart, force-reload - starts a new system-wide fancontrol service"
                exit 1
                ;;
esac

exit 0
```

What I changed is the code below, instead of having...

[INDENT]start-stop-daemon --start -o -q -m -b **-p **$PIDFILE -x $DAEMON
start-stop-daemon --stop -o -q **-p** $PIDFILE[/INDENT]

I made it have...

[INDENT]start-stop-daemon --start -o -q -m -b **--pidfile** $PIDFILE -x $DAEMON
start-stop-daemon --stop -o -q **--pidfile** $PIDFILE[/INDENT]

This allowed me to start/stop the daemon properly! :)

---

### Post by magnaryder31 on 2010-02-22
Aloha Everyone, 

I just finally got this working somewhat better.....the noise in the room is finally at a calmer state.

I did want to just show you my data and hoped that someone could take a look at especially the fancontrol file and tell me if you see any red flags.

I did do it on my own.....worked on it for a few days, did a lot of reading through posts and all that, and would hate to see all that time go down the drain.

**My sensor report:**

desktop:~$ sensors
w83637hf-isa-0290
Adapter: ISA adapter
VCore:       +1.50 V  (min =  +1.64 V, max =  +1.00 V)   ALARM
+12V:       +11.98 V  (min = +15.38 V, max = +14.41 V)   ALARM
+3.3V:       +3.41 V  (min =  +3.63 V, max =  +3.70 V)   ALARM
+5V:         +5.17 V  (min =  +3.17 V, max =  +0.13 V)   ALARM
-12V:        +6.06 V  (min =  -5.86 V, max =  +1.95 V)   ALARM
V5SB:        +5.19 V  (min =  +4.89 V, max =  +4.60 V)   ALARM
VBat:        +3.25 V  (min =  +3.28 V, max =  +3.14 V)   ALARM
fan1:          0 RPM  (min = 3068 RPM, div = 2)  ALARM
CPU Fan:    1662 RPM  (min = 6617 RPM, div = 4)  ALARM
fan3:          0 RPM  (min =    0 RPM, div = 2)
M/B Temp:    -48.0°C  (high = -41.0°C, hyst = -11.0°C)  sensor = thermistor
CPU Temp:    +34.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
temp3:       +31.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
cpu0_vid:   +1.550 V
beep_enable:enabled

My **/etc/fancontrol** File:

# Configuration file generated by pwmconfig, changes will be lost
INTERVAL=10
FCTEMPS=hwmon0/device/pwm1=hwmon0/device/temp2_input hwmon0/device/pwm2=hwmon0/device/temp3_input
FCFANS=hwmon0/device/pwm1=hwmon0/device/fan1_input hwmon0/device/pwm2=hwmon0/device/fan2_input
MINTEMP=hwmon0/device/pwm1=20 hwmon0/device/pwm2=25
MAXTEMP=hwmon0/device/pwm1=60 hwmon0/device/pwm2=60
MINSTART=hwmon0/device/pwm1=72 hwmon0/device/pwm2=50
MINSTOP=hwmon0/device/pwm1=69 hwmon0/device/pwm2=87
MINPWM=hwmon0/device/pwm1=67 hwmon0/device/pwm2=81
MAXPWM=hwmon0/device/pwm1=150 hwmon0/device/pwm2=200

In the sensors report it shows fan1 at 0 speed, but it is actually my power supply fan that is running.

Please let me know if anyone sees something that I may need to give some attention to...

Thanks, 
Noooooobie

---

### Post by Glaucous on 2010-02-25
I have an odd problem with lm-sensors. I add the module and so on, no problems there. Then I run pwmconfig (as sudo, otherwise is doesn't work), it tests two fans which I physically see stopping. Then when I setup the temperature configuration, and I get to the part when I have to setup the PWM values for minimum and maximum, I choose test (t). 
But nothing happens, it sets the fan to 10 PWM, but it doesn't stop or slow down. So I tried setting all the values to 10 in the configuration and started the daemon, and it doesn't slow down the fans either.

---

### Post by psyopper on 2010-04-18
I don't know what I did wrong along the way but I had problems getting fancontrol to start at boot time correctly.

1. I had to go into my BIOS and disable the CPU Fan Control system. pwmconfig would detect and operate the fans and set up a fancontrol profile, but the profile was doing nothing because the BIOS was overriding the input.

2. I had to do the same renaming of the fancontrol.pid as described very early in the thread.

3. I had to use [i]sudo update-rc.d -f fancontrol remove
[/i] followed by *sudo update-rc.d fancontrol defaults* to get it to start correctly at boot time.

---

### Post by MrGreen on 2011-03-31
```
Loading configuration from /etc/fancontrol ...

Common settings:
  INTERVAL=10

Settings for hwmon2/device/pwm1:
  Depends on hwmon3/device/temp1_input
  Controls hwmon2/device/fan1_input
  MINTEMP=35
  MAXTEMP=50
  MINSTART=18
  MINSTOP=18
  MINPWM=10
  MAXPWM=75

Enabling PWM on fans...
Starting automatic fan control...

```

Got fancontrol working on my atom 330 little falls motherboard.. 

Only the Minstart and minstop do not look right?

Any ideas?

MrG

---

### Post by Anbech on 2011-05-28
first of all, thx alot folks for this! it just works.! :)
but, (of cause it cant be said without a _but_), well, i have it adjusting my CPU fan flawlessly, but want my GPU in the process too..
ive tried this, but cant seem to make it work:
```

# Configuration file generated by pwmconfig, changes will be lost
GPUTEMP=/usr/bin/nvidia-settings -q [gpu:0]/GPUCoreTemp\ | grep "Attribute" | sed -e "s/.*: //g" -e "s/\.//g"
INTERVAL=10
DEVPATH=hwmon0=devices/platform/it87.656 hwmon1=devices/pci0000:00/0000:00:18.3
DEVNAME=hwmon0=it8712 hwmon1=k10temp
FCTEMPS=hwmon0/device/pwm1=hwmon1/device/temp1_input hwmon0/device/pwm2=GPUTEMP
FCFANS=hwmon0/device/pwm1=hwmon0/device/fan1_input hwmon0/device/pwm2=hwmon0/device/fan2_input
MINTEMP=hwmon0/device/pwm1=45 hwmon0/device/pwm2=45
MAXTEMP=hwmon0/device/pwm1=50 hwmon0/device/pwm2=55
MINSTART=hwmon0/device/pwm1=150 hwmon0/device/pwm2=150
MINSTOP=hwmon0/device/pwm1=50 hwmon0/device/pwm2=50
MAXPWM=hwmon0/device/pwm1=255 hwmon0/device/pwm2=255

```

i really do hope that some of you guys/gals in here can/will help me out on this one... 

thx in advance, 
-Anbech

---

### Post by Anbech on 2011-05-29
NEVERMIND! got to work! :D

it was kind of a hassle and had to change some things inside "/usr/sbin/fancontrol", "/etc/fanctrol", and some other stuff... :)

ive packed down the files if anyone else should encounter the same, with the files as they should be to work with CPU and GPU (nVidia) fans. my gpu fan is connected to the motherboard, but it might work if its connected to the gpu too..

i can NOT guarantee that itll work for others, but it _should_ just by editing the "/etc/fancontrol" file, to your needs.

btw, remember to sudo chmod 755 the files after they are extracted to their right place.

oh, and for starting the process i have to use "sudo fancontrol &" and for stopping it "sudo /etc/init.d/fancontrol stop" .. kinda weird i know, but it works :)
still havent figured out how to make it start upon ubuntu startup (yet a thing to be made) :)

the package can be downloaded here (permanent link) :
[fancontrol.zip]("http://djanbech.com/ubuntu/fancontrol.zip")

hope some of you can use it too auto adjusting both cpu and gpu (nVidia) fans.
cheers
-Anbech

---

### Post by MrSlaggers on 2011-07-19
My laptop fan is constantly running, and I'm trying to find a way to fix it.

Here is my output when I run sensors.

```
acpitz-virtual-0
Adapter: Virtual device
temp1:       +48.0°C  (crit = +99.0°C)                  

k10temp-pci-00c3
Adapter: PCI adapter
temp1:       +48.0°C  (high = +70.0°C, crit = +109.5°C)  
```I don't have a sensors.conf file in /etc/ to modify, so I'm not sure what to do next. Can anyone help?

---

### Post by mikewhatever on 2011-07-19
> **MrSlaggers said:**
> My laptop fan is constantly running, and I'm trying to find a way to fix it.

Here is my output when I run sensors.

```
acpitz-virtual-0
Adapter: Virtual device
temp1:       +48.0°C  (crit = +99.0°C)                  

k10temp-pci-00c3
Adapter: PCI adapter
temp1:       +48.0°C  (high = +70.0°C, crit = +109.5°C)  
```I don't have a sensors.conf file in /etc/ to modify, so I'm not sure what to do next. Can anyone help?

That doesn't show any fan sensors, which most likely means that there are none. Many laptops don't have them, or at least, nothing is detected by lm-sensors. I'd suggest searching for your specific brand and model, hopefully someone else had the same problem and got it fixed.

---

### Post by MrSlaggers on 2011-07-19
> **mikewhatever said:**
> That doesn't show any fan sensors, which most likely means that there are none. Many laptops don't have them, or at least, nothing is detected by lm-sensors. I'd suggest searching for your specific brand and model, hopefully someone else had the same problem and got it fixed.

I've looked and I can't seem to find any way to fix the problem. The laptop I have is an HP Pavilion dv6.

---

### Post by mikewhatever on 2011-07-20
Right, I am going to post some suggestions in the other thread.

---

### Post by karg on 2011-08-29
Got the fancontrol working really nicely. This old Asus A7V880 MB gives the CPU fan only some minimum or then maximum and nothing between those. This is my /etc/fancontrol setup for Athlon XP 2800+ based machine running Ubuntu 10.04 32bit:

# Configuration file generated by pwmconfig, changes will be lost
INTERVAL=10
DEVPATH=hwmon0=devices/platform/it87.3072
DEVNAME=hwmon0=it8712
FCTEMPS= hwmon0/device/pwm1=hwmon0/device/temp1_input
FCFANS= hwmon0/device/pwm1=hwmon0/device/fan1_input
MINTEMP= hwmon0/device/pwm1=50
MAXTEMP= hwmon0/device/pwm1=65
MINSTART= hwmon0/device/pwm1=101
MINSTOP= hwmon0/device/pwm1=100
MINPWM=hwmon0/device/pwm1=90

CPU temp keeps at 54C at idle and the fan is at 1380RPM. Under load the CPU temp rises up to 57C and then the fan is at 1750RPM. That's the highest temp which I got currently. With the ASUS Q-Fan control the CPU fan is at 1200RPM until some configured limit has been reached. Then it pumps the fan to maximum speed up to something like 2600RPM and that I can also hear :P

---

### Post by www.rzr.online.fr on 2011-10-10
looks like the package is outdated 
I am building a new version if it matters

-- 
[http://rzr.online.fr/q/lenovo](http://rzr.online.fr/q/lenovo)

---

### Post by akernan on 2011-10-10
I kinda got lm-senosors working. I can't find my chipset in /etc/sensors3.conf. I think it's Intel HM55. I have an Inspiron 1564. Here is the output from sensors.

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

I'd like to get lm-sensors working correctly/fully so I can use fancontrol.

---

### Post by geronimo66 on 2011-10-16
Hello, 
does anybody knows, how to enable fancontrol, if pwm says "no, there are no sensors"?
I think, most users without working fancontrol suffer at this point.

I got this issue with a Toshiba Satellite. sensors just detects the thermal sensors, managed by coretemp, but no fan.
thanx for replying
geronimo

---

### Post by Shaktijar on 2012-08-08
> **bomanizer said:**
> Hi,

I'm wondering.. does the script start every time the system boots up? How about surviving a hibernation? I think these are general init-script issues... or?

cheers
Actually, my fancontrol, for instance, doesn't survive  a hibernation or suspend.


Have fan.

---

### Post by Wizzard on 2012-10-17
Hi. Is it possible to preserve the fan speed after stopping fancontrol service? I would like to let the fan speed constant after rebooting the computer. 

Now when I reboot the computer, after shutdown of all services, the fan start to spin very fast, like without fancontrol. In Windows, I use speedfan and it preserves the fan speed after its shutdown.

---

### Post by nalsanj on 2012-12-11
Hi 

i am on Ubuntu P. The processor is Intel i3. a desktop. 

 i installed lm-sensors and below is the report "sensors" gave

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +30.0°C  (high = +89.0°C, crit = +105.0°C)
Core 2:       +33.0°C  (high = +89.0°C, crit = +105.0°C)

w83627dhg-isa-0a10
Adapter: ISA adapter
Vcore:        +0.93 V  (min =  +0.00 V, max =  +1.74 V)
in1:          +0.75 V  (min =  +1.99 V, max =  +1.99 V)  ALARM
AVCC:         +3.36 V  (min =  +2.98 V, max =  +3.63 V)
+3.3V:        +3.36 V  (min =  +2.98 V, max =  +3.63 V)
in4:          +1.30 V  (min =  +0.90 V, max =  +1.77 V)
in5:          +0.76 V  (min =  +1.15 V, max =  +0.90 V)  ALARM
in6:          +1.06 V  (min =  +0.94 V, max =  +2.03 V)
3VSB:         +3.36 V  (min =  +2.98 V, max =  +3.63 V)
Vbat:         +3.36 V  (min =  +2.70 V, max =  +3.30 V)  ALARM
fan1:           0 RPM  (min = 3515 RPM, div = 128)  ALARM
fan2:           0 RPM  (min = 10546 RPM, div = 128)  ALARM
fan3:           0 RPM  (min = 10546 RPM, div = 128)  ALARM
fan5:           0 RPM  (min = 10546 RPM, div = 128)  ALARM
temp1:        +39.0°C  (high = -121.0°C, hyst =  +9.0°C)  ALARM  sensor = diode
temp2:        +39.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
temp3:       +127.0°C  (high = +80.0°C, hyst = +75.0°C)  ALARM  sensor = thermistor
cpu0_vid:    +2.050 V
intrusion0:  OK

radeon-pci-0100
Adapter: PCI adapter
temp1:        +70.5°C  


The  fans sensors are detecting 0 RPM and some temperatures are out of range  - the ALARMs above but i dont understand it very well. Can someone help  out?

---

### Post by Singtoh on 2013-04-17
Hello All,

I just upgraded to Ubuntu 13.04 64bit from Ubuntu 12.10 64bit. Fan control was working perfectly in Ubuntu 12.10 but now when I do sudo pwmconfig it says "hwmon2/device/pwm1_enable stuck to 2, Manual control mode not supported, skipping hwmon2/device/pwm1.
There are no usable PWM outputs." Like I said it was working like a dream but after the upgrade not working? It would be nice to get this working, I use max fan on my T61 when editing music or other cpu intensive stuf and it really keeps the lappy cool. Anyone have any ideas how to get this working??

Cheers,

Singtoh

---

### Post by guilhermemtr on 2013-04-20
> **benplaut said:**
> don't give them ideas  :roll:

Nowadays most of the SO's just shutdown if the critical temperatures are reached :)

It has already happened to me, but with my laptop, not because of the fans, but because of some accumulated "thrash" inside of it.
 (sorry for my english)

---

### Post by Singtoh on 2013-04-21
Hello All,

Well I got it going after looking at the How to fancontrol page. I was using this:"For example, in Ubuntu 8.04 (Hardy Heron), add the following to /etc/modprobe.d/options: options thinkpad_acpi fan_control=1" from that page. Now I am using this:"For Debian Squeeze (testing) create /etc/modprobe.d/thinkpad_acpi.conf with: options thinkpad_acpi fan_control=1 and install the package thinkfan" from the same page and it works just fine. I am using Ubuntu 13.04-64. I still have fancontrol installed along with thinkfan but I think this file is what fixed it for me:/etc/modprobe.d/thinkpad_acpi.conf and inserting this:
options thinkpad_acpi fan_control=1 into that file.

Cheers,

Singtoh

---

### Post by Merrattic on 2013-08-28
If you are not getting all your sensors identified, you may have a newer motherboard chipset with the repo version of lm-sensors cannot see.

To get the latest version of lm-sensors go to lm-sensors.org and click on the Devices Support Status link

In the blurb at the top of this page you will find a link to download the latest version of sensors-detect. It is a standalone script so no compiling needed.

Once downloaded, make it executable and run it e.g.

```
sudo ~/Downloads/sensors-detect
```

With any luck you will then find your sensors and be able to run pwmconfig.

With the correct chipset sensor module defined I had to go back to the Devices Support Status page and grab the source code for the module, a quick and easy make & sudo make install & sudo modprobe nct6775 got me up and running. (It was nct6775 in my case, may be different for you)

This worked for me with an Asus Z87M-PLUS mobo with i5 core 4670K processor

---

### Post by matthias-k on 2014-06-12
Hello,

in Ubuntu Gnome 14.04 the postet Startup Script hadn't worked for me.

I changed it to the following wich works for me.

```

### BEGIN INIT INFO
# Provides:          fancontrol
# Required-Start:    $remote_fs $syslog
# Required-Stop:     $remote_fs $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start fancontrol at boot time
# Description:       Enable fancontrolservice provided by daemon.
### END INIT INFO

# Using the lsb functions to perform the operations.
. /lib/lsb/init-functions
# Process name ( For display )
NAME=fancontrol-daemon
# Daemon name, where is the actual executable
DAEMON=/usr/sbin/fancontrol
# pid file for the daemon
PIDFILE=/var/run/fancontrol.pid

# If the daemon is not there, then exit.
test -x $DAEMON || exit 5

case $1 in
 start)
  # Checked the PID file exists and check the actual status of process
  if [ -e $PIDFILE ]; then
   status_of_proc -p $PIDFILE $DAEMON "$NAME process" && status="0" || status="$?"
   # If the status is SUCCESS then don't need to start again.
   if [ $status = "0" ]; then
    exit # Exit
   fi
  fi
  # Start the daemon.
  log_daemon_msg "Starting the process" "$NAME"
  # Start the daemon with the help of start-stop-daemon
  # Log the message appropriately
  if start-stop-daemon --start --quiet --oknodo --pidfile $PIDFILE --exec $DAEMON ; then
   log_end_msg 0
  else
   log_end_msg 1
  fi
  ;;
 stop)
  # Stop the daemon.
  if [ -e $PIDFILE ]; then
   status_of_proc -p $PIDFILE $DAEMON "Stoppping the $NAME process" && status="0" || status="$?"
   if [ "$status" = 0 ]; then
    start-stop-daemon --stop --quiet --oknodo --pidfile $PIDFILE
    /bin/rm -rf $PIDFILE
   fi
  else
   log_daemon_msg "$NAME process is not running"
   log_end_msg 0
  fi
  ;;
 restart)
  # Restart the daemon.
  $0 stop && sleep 2 && $0 start
  ;;
 status)
  # Check the status of the process.
  if [ -e $PIDFILE ]; then
   status_of_proc -p $PIDFILE $DAEMON "$NAME process" && exit 0 || exit $?
  else
   log_daemon_msg "$NAME Process is not running"
   log_end_msg 0
  fi
  ;;
 reload)
  # Reload the process. Basically sending some signal to a daemon to reload
  # it configurations.
  if [ -e $PIDFILE ]; then
   start-stop-daemon --stop --signal USR1 --quiet --pidfile $PIDFILE --name $NAME
   log_success_msg "$NAME process reloaded successfully"
  else
   log_failure_msg "$PIDFILE does not exists"
  fi
  ;;
 *)
  # For invalid arguments, print the usage message.
  echo "Usage: $0 {start|stop|restart|reload|status}"
  exit 2
  ;;
esac

```

---

