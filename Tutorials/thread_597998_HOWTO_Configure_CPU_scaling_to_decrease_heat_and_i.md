---
title: "HOWTO: Configure CPU scaling to decrease heat and increase battery life"
date: 2007-10-30
forum: Tutorials
---

### Post by thebert on 2007-10-30
This guide should work with Ubuntu Feisty or Gutsy 32 bit. Most of the guides that I have read on this subject way over complicate things and don't give information on how to change the scaling governor. So as requested by several other forum members here is a howto.

[B][SIZE="3"]
About CPU Frequency Scaling[/SIZE][/B]
You may have noticed the CPU Frequency Scaling Monitor that you can add to your Gnome panel. It gives you information about the speed of your processor if your processor has scaling abilities. Most notebook processors have this ability. To see which speeds your processor can run at, you can run this command:

```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies

```
The Pentium M in my laptop gives the following output:
```

2133000 1867000 1600000 1333000 1067000 800000 

```
The numbers are in Hz, so my CPU will scale between 800MHz and 2.13GHz.

If you add the CPU Frequency Scaling Monitor applet to your panel, it will inform you of what speed your CPU is currently running at. But there is more that this applet can do.

The cpufreqd process is what controls the cpu scaling. There are several different methods (known as governors) that dictate the way scaling will work. You can find what governors are available by running this command:
```

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors

```
You will see something like this:
```

userspace ondemand powersave conservative performance 

```
Ubuntu uses ondemand as the default governor. This means that the CPU will idle at the lowest setting, then when usage increases, it will jump to the highest setting until usage decreases.

Conservative is similar to ondemand, except that instead of jumping to the highest setting when usage increases, it will go to the next highest setting and move up through the settings as necessary. For example, when using the conservative governor, my CPU will idle at 800MHz. If usage goes above 80% it will move up to 1.067GHz. If usage is still above 80% it will move up to 1.333GHz, and so on. This method will use less power then ondemand, but you may take a performance hit.

Powersave will keep your cpu constant at the lowest available setting, and performance will keep the CPU at the highest available setting. Userspace means that another program will control the CPU scaling.

Ubuntu uses ondemand by default and that will be fine for most people, but I found that my laptop runs much cooler and gets better battery life by using conservative.

[SIZE="3"][B]
Using the CPU Frequency Scaling Monitor to control scaling[/B][/SIZE]
As I said above the CPU Frequency Scaling Monitor can do more than just display which frequency the CPU is running at. It can control which governor the cpufreqd process will use. This feature is disabled by default in ubuntu, but you can enable it with this command:

```
sudo dpkg-reconfigure gnome-applets
```

Then selecting 'yes' to 'Install cpufreq-selector with SUID root.'

Now if you click on the CPU Frequency Scaling Monitor on your applet you can change which governor to use, or even set the CPU to a constant speed.


[SIZE="3"]**Setting new default governors**[/SIZE]
Now when you change settings using panel applet they will not 'stick'. They will change back to the default ondemand value when you reboot, switch to battery power, or switch to AC power.

To change these default values you need to open up the gconf-editor. To do that press Alt+F2 and type
gconf-editor into the run dialog. Now navigate to apps>gnome-power-manger>cpufreq. Here you can change the value of policy_ac and policy_battery to whichever governor you wish to be default for AC power and battery.

Now you should be set. When you remove the AC power and switch to battery it will automatically change to whichever governor you have set as the value of policy_battery. Likewise when you switch back to AC power.

Please let me know of any improvements or mistakes in this guide, or post any problems you might have. Some information was taken from this site:
[http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/](http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/)

---

### Post by mfdc1969 on 2007-12-23
Thank you - it's nice when these simple things are brought to the attention of the masses! I found this how-to very very useful.

---

### Post by Maikelv on 2008-01-06
I know this is an old thread, but just a bump because this helped me alot !
Thanks

---

### Post by simplyw00x on 2008-01-06
Could you possibly point me to the right place to report bugs in this process? When unplugged, *nothing* I do will convince my laptop to run at anything other than its slowest setting. Nice tips though, thanks.

---

### Post by ve4cib on 2008-01-09
Did you make sure to open change the setting for battery_policy in the configuration editor?  I had the opposite problem; on battery the CPU would be running at full-tilt, when I really want it to scale itself down.

After changing the value of battery_policy to "powersave" it works fine (for me).  Chances are you want to set your battery_policy governor to conservative or ondemand (use conservative if you've got more than 2 frequency settings, otherwise ondemand seems to be the better option).

If you have tried that I don't know what the problem is, but you haven't really provided much information to help us help you...

---

### Post by Tu13erhead on 2008-01-10
Great tip!  Thanks!

---

### Post by jpittack on 2008-01-10
Thank you so much.  I am always in search of ways to better improve battery life.  This works under 64 bit Gutsy.

---

### Post by r!ots on 2008-01-13
Hey,
I have an Asus X51R notebook with an Intel Core Duo CPU T2450@2.00GHz.
When I try to add the frequency scaling monitor I get the following error message:

```
CPU frequency scaling unsupported
You will not be able to modify the frequency of your machine.  Your machine may be misconfigured or not have hardware support for CPU frequency scaling.
```

But actually my CPU should be able to support frequency scaling, shouldn't it? Does anyone know a solution?

EDIT: SOLVED
Alright I got it working myself by adding the line 'acpi-cpufreq' to /etc/modules. Thanks for this guide.

---

### Post by rouge568 on 2008-01-16
Great guide, though I found that I already had CPU scaling enabled by default. Oh, and you've been dugg! [http://digg.com/linux_unix/CPU_Scaling_Ubuntu_and_you_how_to_scale_your_CPU](http://digg.com/linux_unix/CPU_Scaling_Ubuntu_and_you_how_to_scale_your_CPU)

---

### Post by Yes_It's_Me on 2008-02-02
I would just like to say that this is a fantastic howto, simple and to the point with very effective results. Well done mate, it helped me out :)

---

### Post by thebert on 2008-02-09
Wow guys thanks for all of the replies. I wrote this months ago and totally forgot all about this thread and just found it again. If anyone has any improvements or suggestions I will be happy to add them.

---

### Post by midnightray on 2008-02-09
Thanks for guide :) worked great.

---

### Post by lutra on 2008-02-28
> **thebert said:**
> Wow guys thanks for all of the replies. I wrote this months ago and totally forgot all about this thread and just found it again. If anyone has any improvements or suggestions I will be happy to add them.



Hi All,
thanks for the guide!

I was noticing that on my core 2 duo processor laptop it is not possible to set different frequencies for the two cores. Is that normal?

PS
I'm not even sure that it can be somehow useful, just asking.

---

### Post by Bad_Byte on 2008-02-28
To op: Heres a simple script that allows one to select the modes without the manual hassle of cat <governor> /sys/.... for each core or without having to go overkill and use kpowersave. n00b scripting but it gets the job done =)

To lutra: yes, for C2D/Q all cores have to be set to the same governor to be in effect. Think the upcoming Phenoms from AMD will allow seperate core speeds.

[Download link](http://heim.ifi.uio.no/~andrelow/files/cpu_speed.sh)
```

#!/bin/bash
# cpu_speed.sh
# Last edit: 2008-02-28

if [ $1 = auto ] ; then MODE=ondemand
    elif [ $1 = max ] ; then MODE=performance
    elif [ $1 = min ] ; then MODE=powersave
    elif [ $1 = user ] ; then MODE=userspace
    elif [ $1 = laptop ] ; then MODE=conservative # Said to only work on laptop processors.
    else
        echo "No mode selected"
        exit
fi

CORES=$(ls /sys/devices/system/cpu | grep cpu | wc -l) # Outputs number of cores
let CORES=CORES-1 # Core adjustment for further use

COUNTER=0
while [ $COUNTER -le $CORES ]; do
    echo $MODE | sudo tee /sys/devices/system/cpu/cpu$COUNTER/cpufreq/scaling_governor > /dev/null 
    # Confused?. Tee reads std.out and writes that into file and std.out, that
    # part we don't need so the black hole /dev/null can eat that part
    echo Core $COUNTER mode: $MODE
    let COUNTER=COUNTER+1
done

```

---

### Post by chochem on 2008-02-28
For the XFCE4 people:
```
sudo apt-get install xfce4-cpu-freq-plugin xfce4-governor-plugin
```
and a thread:
[http://ubuntuforums.org/showthread.php?t=516383](http://ubuntuforums.org/showthread.php?t=516383)

---

### Post by beercz on 2008-06-19
Great guide - thanks for this.  Should now be able to extend my hp laptop's battery life a little bit more.

---

### Post by GijsH on 2008-07-12
After all the praise on this HowTo, a slightly more negative note: on my Feisty system (Sony Vaio) the very 1st command fails with:

[FONT="Courier New"]gijs@gijs:~$ ls /sys/devices/system/cpu/cpu0/cpufreq
ls: /sys/devices/system/cpu/cpu0/cpufreq: No such file or directory
[/FONT]

Now what I do to reduce the heat my laptop is emitting?

---

### Post by handsomeDave on 2008-07-31
> **GijsH said:**
> After all the praise on this HowTo, a slightly more negative note: on my Feisty system (Sony Vaio) the very 1st command fails with:

[FONT="Courier New"]gijs@gijs:~$ ls /sys/devices/system/cpu/cpu0/cpufreq
ls: /sys/devices/system/cpu/cpu0/cpufreq: No such file or directory
[/FONT]


I get that too

I've got a Pentium M 1.6Ghz

---

### Post by albasheers on 2008-08-02
****


**anybody please help me **

i have changed the setting to **performance** ,
and when just restarted my laptop its unable to start 
its making teet teet sound and then no display

my laptop is hp dv2000 and its configuration is

intel core 2 duo 1.83 ghz

1gm ram and 128 mb nvidia graphic card

---

### Post by InfinityCircuit on 2008-08-08
Sorry to break it to you, but ondemand is superior to conservative on intel chipsets.  Intel's own kernel developer explains why:

[http://www.bughost.org/pipermail/power/2007-May/000166.html](http://www.bughost.org/pipermail/power/2007-May/000166.html)
[http://www.bughost.org/pipermail/power/2007-May/000073.html](http://www.bughost.org/pipermail/power/2007-May/000073.html)
[http://www.bughost.org/pipermail/power/2007-May/000071.html](http://www.bughost.org/pipermail/power/2007-May/000071.html)

The basic idea is this: Since you always have to keep the northbridge running, power usages scale slower than cpu speed increases.  This means it is faster to jump to the highest speed and then back down to idle, because it takes longer to perform the same operations at a slower speed.

---

### Post by carreira87 on 2008-09-17
Hello!

I want to change cpu frequency and I tried this tutorial, but in my ubuntu only appears one governor, which is "performance"... I don't know where are the others, and because I only have one governor I can't change the cpu frequency.

How can I get the other governors, like "powersave", "ondemand", ... ?

Thanks in advance!

---

### Post by carreira87 on 2008-09-17
> **carreira87 said:**
> Hello!

I want to change cpu frequency and I tried this tutorial, but in my ubuntu only appears one governor, which is "performance"... I don't know where are the others, and because I only have one governor I can't change the cpu frequency.

How can I get the other governors, like "powersave", "ondemand", ... ?

Thanks in advance!

Well, I just solved that problem. Somehow, I manage to remove powernowd, but now I reinstalled and I have other governor modes to choose.

Unfortunately, changing the mode doesn't affect the cpu frequency, which is always at maximum speed.

[IMG]http://img352.imageshack.us/img352/120/cpufrequencyno2.jpg[/IMG]
From this image of the CPU Frequency Monitor, I have frequency options but when I click on those frequencies the cpu frequency remains the same. Clicking on the modes, it change the mode, but again the frequency remains the same. :confused:

---

### Post by carreira87 on 2008-09-17
Wow! 3 posts in a row! :lolflag:

Ok, I have all my problems solved now. I can choose the frequency now, a simple reboot solved my problem. :)

---

### Post by Synchro on 2008-09-18
I've tried the things mentioned in this thread with no joy. I'm running 8.04.1 on dual quad-core Xeon L5420 CPUs, and there just doesn't seem to be any support for them in cpufreqd. cpufreq-info just says "no or unknown cpufreq driver is active on this CPU".

I've installed the cpufreqd and cpufrequtils packages, but cpufreqd is marked as failed on startup and /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors is just not there. This is what one of my CPUs looks like in /proc/cpuinfo:

```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 23
model name      : Intel(R) Xeon(R) CPU           L5420  @ 2.50GHz
stepping        : 6
cpu MHz         : 2500.087
cache size      : 6144 KB
physical id     : 0
siblings        : 4
core id         : 0
cpu cores       : 4
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr dca sse4_1 lahf_lm
bogomips        : 5003.14
clflush size    : 64
cache_alignment : 64
address sizes   : 38 bits physical, 48 bits virtual
power management:
```

I know this isn't a laptop, but this box is pulling 190W at idle and 210W under full load; I'm sure it could be lower.

Any ideas?

---

### Post by InfinityCircuit on 2008-09-18
I don't know of any cpufreq support for ANY quads at the moment in the default Ubuntu computers.  You may have to just wait.

---

### Post by jdroflet on 2008-09-20
> **GijsH said:**
> 
[FONT="Courier New"]gijs@gijs:~$ ls /sys/devices/system/cpu/cpu0/cpufreq
ls: /sys/devices/system/cpu/cpu0/cpufreq: No such file or directory
[/FONT]


same here
Mythbuntu 8.04  Dell Latitude C840 

root@ubtop:/# **cpufreqd -D**
pmu_init                 : /proc/pmu/info: No such file or directory
apm_init                 : /proc/apm: No such file or directory
sensors_post_conf        : no sensors.conf found, sensors disabled!
plugins_post_conf        : Unable to configure plugin sensors_plugin, removing
nforce2_post_conf        : Unconfigured, exiting.
plugins_post_conf        : Unable to configure plugin nforce2_atxp1, removing
parse_config_profile     : Unable to calculate absolute values for profile "Performance High". <etc>

[INDENT]root@ubtop:/# less **/etc/cpufreqd.conf**
...
[acpi]
acpid_socket=/var/run/acpid.socket
[/acpi]
...[/INDENT]

Not much in the cpu0 dir
root@ubtop:/# ls -l **/sys/devices/system/cpu/cpu0**
total 0
drwxr-xr-x 4 root root    0 2008-09-20 13:19 cpuidle
-r-------- 1 root root 4096 2008-09-20 13:19 crash_notes
drwxr-xr-x 2 root root    0 2008-09-20 13:19 topology


[INDENT]root@ubtop:/# **less /proc/cpuinfo**
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Mobile Intel(R) Pentium(R) 4 - M CPU 1.80GHz
stepping        : 7
cpu MHz         : 1794.202
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht
 tm pbe up pebs bts sync_rdtsc cid
bogomips        : 3592.59
clflush size    : 64[/INDENT]

Thanks to any who can help.

---

### Post by edmondt on 2008-09-20
I forgot about this, and it a very useful tool to decrease laptop heat when you're on the road :)

---

### Post by Skivache on 2008-09-23
Excellent post, I wasn't sure my server (an old laptop) was changing the CPU frequency correctly, which it turns out it was.  The eggdrop bot I was checking frequency caches the CPU stats (which makes sense..), so a simple rehash solved my problem.

Thanks again for the awesome how-to :D

---

### Post by Karpah on 2008-09-29
Oh my gosh.... I was searching for a simple solution to my dismal battery life... from ~1.9 hours with wireless/Bluetooth disabled, to ~3 hours with both enabled, just by changing policy_battery to powersave, plus the laptop no longer burns my lap and runs whisper quiet... thank you!!!! :D

---

### Post by jhp-dk on 2008-10-04
I have a little problem with the scaling. The ondemand daemon is only running at 800mhz or 2ghz even though the processor have more frequencies.

```

jimmy@jimmy-laptop:~$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_available_frequencies
2001000 2000000 1600000 1200000 800000 
2001000 2000000 1600000 1200000 800000

```how do i make it scale to other frequencies?

---

### Post by sgleo87 on 2008-11-04
> **thebert said:**
> Now when you change settings using panel applet they will not 'stick'. They will change back to the default ondemand value when you reboot, switch to battery power, or switch to AC power.

To change these default values you need to open up the gconf-editor. To do that press Alt+F2 and type
gconf-editor into the run dialog. Now navigate to apps>gnome-power-manger>cpufreq. Here you can change the value of policy_ac and policy_battery to whichever governor you wish to be default for AC power and battery.


This option in the gconf-editor is not there anymore in Intrepid Ibex....has anyone figured out how to make the settings stick in 8.10?

---

### Post by orawax on 2008-11-05
**CPU Frequency Scaling on _Celeron M and Pentium 4_ processors**

[i]thanks to krazykit,
[http://ubuntuforums.org/showthread.php?t=190921](http://ubuntuforums.org/showthread.php?t=190921)[/i]

[quote=krazykit]First off, you need to insert the p4_clockmod module. Open a terminal and do
```
sudo modprobe p4_clockmod
```

This shouldn't give any feedback.

To make this module load every boot, add it to /etc/modules with your favorite editor ...it should look something like this

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

p4_clockmod
```[/quote]

Then enable the Frequency Scaling Monitor applet as described in the first post of this thread. (For me, in Hardy, the question was: 'Should cpufreq-selector run with root privileges?')

---

### Post by Andreas1 on 2008-11-05
> **sgleo87 said:**
> This option in the gconf-editor is not there anymore in Intrepid Ibex....has anyone figured out how to make the settings stick in 8.10?

no solution, but an explanation why:
[http://ubuntuforums.org/showthread.php?t=971578#post6109958]("http://ubuntuforums.org/showthread.php?t=971578#post6109958")

---

### Post by fieldstone on 2009-03-16
After some tinkering, and some help from the guide at [http://wiki.zenwalk.org/index.php?title=Power_Management#powerthend](http://wiki.zenwalk.org/index.php?title=Power_Management#powerthend) , I figured out how to set default CPU governors for ac and battery on Intrepid and Jaunty.

All you need to do is put a short script called something like 50-cpufreq.sh in both /etc/acpi/battery.d/ and /etc/acpi/ac.d/ .

The script should include the following:

#! /bin/sh
echo "governor" > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
echo "governor" > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor

Just change the word governor to performance, powersave, ondemand or conservative, depending on which one you want for battery and ac. (Mine is set to performance on ac, and to ondemand on battery.)

Set both scripts' permissions to 744 (sudo chmod 744 50-cpufreq.sh) and you're done. Try unplugging and re-plugging your power adapter, and you'll see it works right away.

I also installed powerthend for more responsive frequency scaling... all you have to do is download it, move it to your root directory, un-tar it, and then remove powernowd.

---

### Post by heffo_j on 2009-03-20
Hi there, I've broken my cpu scaling. 

For some reason I had the applets going okay then I must have fiddled with something and now I get a message to say that Frequency Scaling is Unsupported. They are both running at 100%. 

I have installed cpufreqd thinking this might help. I tried uninstalling this and made no difference. 

Any clues on how to get it back as my laptop fans are running flat out.

Regards
John

Edit note: 
SOLVED. I booted from a live CD. Noted that the gnome cpu applet worked okay, so I checked synaptic to see what cpu packages were installed. I noticed that "freqd" was not installed but instead "powernowd". I went back to my installed version and uninstalled "freqd" and reinstalled "powernowd" and in so doing fixed the problem. Next time I'll concentrate....

---

### Post by sincerelyydavid on 2010-03-07
great guide, but i have some questions: does lowering frequency use less power? using less power would result in less heat coming from laptop too, right? but wouldn't your laptop run slower because it's at a lower frequency?

---

### Post by goldsniper on 2010-03-25
i'm using ubuntu in my old trustworthy Compaq Presario v3201tu since Gutsy. And the overheating problem was first appeared in Hardy and solves in Intrepid. Since then, i did not have that overheating problem.

Now the problem appears again in Lucid! But this howto is still valid... until this is fixed again.. I'll be using this workaround! Thanks..

---

### Post by wilsontp on 2010-03-28
I have ubuntu 9.10 on an hp tx2525nr.

It has an AMD 64-bit x2 processor (RM-70, 2.00GHz), and when I have it set for performance, when running on AC, it runs 2GHz, but on battery it drops to 1GHz. If I tell it manually to run at 1GHz, it runs at 1GHz, but if I set it to manual 2GHz, it runs at 1GHz.

If I want to save battery I would've bought an intel.

How do I alter the cpu scaling kernel in ubuntu to run 2GHz on battery when I tell it to?

---

### Post by dalichey on 2012-10-07
helpful, thanks!

---

