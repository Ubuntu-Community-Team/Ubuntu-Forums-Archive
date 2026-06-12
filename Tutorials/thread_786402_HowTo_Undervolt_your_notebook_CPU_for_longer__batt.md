---
title: "HowTo: Undervolt your notebook CPU for longer  battery life"
date: 2008-05-08
forum: Tutorials
---

### Post by Ares Drake on 2008-05-08
[COLOR="Teal"]**Edit: This Post is outdated! The underlying principles still apply, but newer Ubuntu versions requiere a slightly different approach.**
[LIST]
[*]Ubuntu 10.04 LTS
A newer guide for Ubuntu 10.04 LTS Lucid Lynx can be found at: [http://openmindedbrain.info/09/05/2010/undervolting-in-ubuntu-10-04-lucid-lts/](http://openmindedbrain.info/09/05/2010/undervolting-in-ubuntu-10-04-lucid-lts/)
[*]Recent versions
An even more recent guide for the most recent Versions of Ubuntu is linked here: [http://linuxsolver.blogspot.com/2011/02/undervolting-cpu-in-ubuntu.html]("http://linuxsolver.blogspot.com/2011/02/undervolting-cpu-in-ubuntu.html"). It offers a graphical utility to set the voltages for you, but only covers installation. Afterwards, you still have to find and test your individual voltages. Therefor you can use [this method]("http://linuxsolver.blogspot.com/2011/10/how-to-set-cpu-voltage.html") from the same author or the method in this post. Whitchever method you choose, be sure to read the short chapter on safety below. Especially important are points 3 and 4 and these still aply to all current and future methods.
[/LIST][/COLOR]



This howto is based on own experiences and this german [wiki page]("http://wiki.ubuntuusers.de/Prozessorspannung_absenken"), so thx to them.

It is tested for [COLOR="Blue"]intel[/COLOR] Core2Duo and CoreDuo cpus. I have no clue if it works for [COLOR="Green"]AMD[/COLOR] as well. Some answers I received suggest that it currently doesn't work with AMD cpus however.

**From [wikipedia:]("http://en.wikipedia.org/wiki/Undervolting") *Undervolting* **is the practice of reducing the supply voltage of a computer's CPU. There are many reasons to perform this sort of modification, but a common one is to reduce power consumption and thus heat generation in laptop computers. Lower heat generation provided by undervolting and underclocking is also helpful in making computers quieter.

Performance will not suffer as the energy you will save was just wasted (as heat) before.

[B]
Safety:[/B]
Undervolting notebook processors is not uncommon. My older notebook (Toshiba S1) even came with a Windows utility that did automatic undervolting preinstalled. So the "undervolted" processor is nothing dangerous.

The way to get there might be, if no care is taken.
What might happen:
[INDENT]1) The voltage controls stability and temperature. The higher the voltage the higher the temp, but without enough voltage the cpu wont be stable and your PC will lock up. In fact with the following procedure we are trying to find the minimum stable voltage to get the cpu as cool as possible. The energy saved will increase battery life as well.

2) So if you were to INCREASE the voltage, you would rise the temperature. This might damage the cpu in case it got too hot - obvious one. (Though all Intel (probably AMD as well) mobile chips are equiped with safety cut off mechanisms afaik) However with the optimizer scipt it automatically REDUCES the voltage so harm to your hardware is very unlikely.

3) To find the named "minimum" voltage, the optimizer scipt needs to test if the cpu runs stable at every voltage setting. So in case it gets too low, your notebook will lock up. Then afterwards the script knows what is too low and will stay safely above.
That sth gets damaged by locking up is rather unlikely - overclocking my desktop machine in younger years I experienced it at least a hundred times and never fried anything.

4) While locking up however your linux and all open applications crash as well. Wich might result in data loss. Be prepared to see the fsck utility at next boot up checking for data integrity. And let it run! ;) Furthermore, don't open any files while running the optimizer script and, before doing this optimization, unmount as many partitions as possible to reduce the risk. (unmounted partitions cannot be corrupted during the lockup)[/INDENT]

Once the scipt finishes (you need to run it several times, once for every freqency your cpu is capable of), no more lock-ups are to be expected as the script now knows the individual critical voltage for your cpu and will stay savely above.

With all these precautions I think it is rather save to undervolt.


**[SIZE="2"]Still there? Then let's get on to it! Step by step:[/SIZE]**

**1.** This howto depends on the kernel module acpi-cpufreq to control your cpu. To find out if you're using it try
```
lsmod | grep acpi_cpufreq
```
You should see sth. like this:
```
acpi_cpufreq           14892  2 
freq_table              5536  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
processor              36872  4 acpi_cpufreq,thermal
```
In case you don't see anything, you don't use acpi-cpufreq, but maybe the speedstep.centrino module. Then this howto is not for you unfortunately. speedstep.centrino is in theory supported as well, but I have no experience with it. If someone knows how to do it with speedstep.centrino please tell me and I will add it here.

**2. **You need to get a modified version of your acpi_cpufreq module, one with [PHC support]("http://phc.athousandnights.de/") build in. [PHC]("http://phc.athousandnights.de/") means processor hardware control and is the magic that makes it going. There are several ways to get this module.

[INDENT]a) You can download a patch on [their website]("http://phc.athousandnights.de/") and **compile it yourself**. If you have never compiled anything, this is not for you as there are easier ways (see  b) ). However as I hardly find the time to post updates here I will give a mini-howto for compilation here in case a kernel update breakes compatibility with old modules. You need to compile yourself in case you are running 64 bit as well as the precompiled modules I offer below are 32bit only.
[INDENT]Mini-Howto for compilation
```

sudo apt-get install build-essential linux-source
```
extract the tar from /usr/src to /home/"your-username"/"kernelversion"
download latest [patch]("http://phc.athousandnights.de/") to /home/"your-username"/"kernelversion"
copy /boot/config-$(uname -r).config to /home/"your-username"/"kernelversion"
```

cd /home/"your-username"/"kernelversion"
patch -p1 < linux-phc*.patch
make oldconfig
make prepare
make scripts
make M=./arch/x86/kernel/cpu/cpufreq
```
The finished module should be in  /home/"your-username"/"kernelversion"/arch/x86/kernel/cpu/cpufreq
Proceed as if you had downloaded this module with copying it to the right place (see **2.** c) ). After all is done you can savely remove the folder /home/"your-username"/"kernelversion" and uninstall linux-source to save harddisk space.
[/INDENT]

b) Download a **precompiled module**. It has to match your kernel.
[INDENT]
1) First backup your old module.
```
sudo cp /lib/modules/`uname -r`/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko /lib/modules/`uname -r`/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko.old
```
(basically copies it to a new name)

2) There are right now versions for kernel 2.6.24-1**6**-generic, 2.6.24-1**7**-generic, 2.6.24-1**8**-generic and 2.6.24-1**9**-generic. To find out what kernel you have open a terminal and type:
```
uname -r
```[/INDENT]
So once you know, download the right kernel module for [2.6.24-1**6**-generic]("www.s3pp.de/misc/16/acpi-cpufreq.ko") or [2.6.24-1**7**-generic]("www.s3pp.de/misc/17/acpi-cpufreq.ko") or [2.6.24-1**8**-generic]("www.s3pp.de/misc/18/acpi-cpufreq.ko")  or [2.6.24-1**9**-generic]("www.s3pp.de/misc/19/acpi-cpufreq.ko"). 

c) Then copy the downloaded file to the right place:
```
sudo cp acpi-cpufreq.ko /lib/modules/$(uname -r)/kernel/arch/x86/kernel/cpu/cpufreq
``` *You have to redo the entire Step 2 every time you update your kernel, so you might want to save your downloaded module file, as it might work again after a kernel upgrade, i.e. the version -16 worked with -14 and -15 as well, but not with -17.*[/INDENT]

**3.** Reboot. If the module is installed correctly,
```
cat /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
```
should give you sth like this:
```
12:38 10:30 8:24 6:18
```
The value before the : stands for the frequency, the later for the voltage.
[B]
4.[/B] Okay, now we need to find the lowest save voltages. We will use [this optimizer script]("http://www.s3pp.de/misc/linux-phc-optimize.bash"). 
Download it (you will need [this file]("http://www.s3pp.de/misc/functions.bash") as well), then right-click the files, open the permissions tab, and and down at the bottom check the box that says "allow executing the file....." Then run it from the terminal with ```
sudo ./linux-phc-optimize.bash
``` It needs cpuburn installed, so you might want to install it in advance with synaptic. What this scipt does is: It stresses your cpu while lowering the cpu voltage step by step unil your system crashes. Then the script knows what is too low and will stay safely above. The script needs to run once for every frequency step your cpu is capable of, usually around 4-6 times. It will tell you, just run it so often until it tells you finished.
[INDENT][COLOR="Red"]IMPORTANT:[/COLOR]
This script will crash your system. Several times. This is normal and intended. No harm to your hardware is to be expected. However in case you have open files and / or mounted filesystems data loss or corruption might occur. So be advised to unmount as many partitions as possible and open as few files as necessary while doing this. After a reset the fsck utility will check your partitions for data corruption so be strongly advised to let that check run!

Second, the script stresses only one cpu core. In case you have a dual core, open a terminal and type "burnMMX" to run a second thread to stress the second core while doing this.[/INDENT]

When you're finished with the script, you will have a text file with the new and optimized frequency : voltage pairs.

**5.** To use these optimized values, you will need to echo them to /sys/devices/system/cpu/cpu0/cpufreq/phc_controls. An easy way to do it automatically every reboot is to add a line like this:
```
echo "12:21 10:1 8:1 6:1" > /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
```
to your /etc/rc.local file. Of course you have to replace the values with your own. Any second core should automatically use the same voltages.
[B]
6.[/B] Check if it works:
```
cat /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
```
should now give you the new values (after a reboot) compared to before, see above.

---

### Post by w4ngsta07 on 2008-05-10
Hi,

Thanks for posting this how-to. I am a complete beginner in linux and know absolutely nothing, so its refreshing that someone has posted a tutorial thats easy to understand even for people like me(believe me, Ive been trying to get linux PHC to work for days).

So I have a problem, when I use your command on Step 5, the terminal says "bash: echo: write error: Invalid argument". 

I tried using this command, "echo "20:18 20:18 20:18 20:18 12:11" > /sys/devices/system/cpu/cpu0/cpufreq/phc_controls" to replace my default(?) voltages, which were "11:47 10:39 8:29 6:18 136:11" on Step 3. 

I am running a Lenovo T61 with a Core 2 Duo T7300 (2 GHZ) on Ubuntu 8.04 64-bit.

Thanks alot for your responses, this is a very great and helpful community!

EDIT: I dont know why there are 5 of these settings for mine and you only have 4. I searched around and found a formula for the VID: Vcc = 712.5 + VID*12.5  Is this the right formula for the VID? I wanted to run my laptop at a constant 2 GHZ with .9375 volts.

---

### Post by w4ngsta07 on 2008-05-11
Well ok, this is probably easy to answer. I cant run the linux-phc optimizer script. I downloaded it to my desktop. double clicking it does nothing, just runs the text editor, and terminal says 'command not found'

---

### Post by Harpoon on 2008-05-11
w4ngsta07:

you need to make a script executable before you can run it.

The easiest way is right-click the file, open the permissions tab, and and down at the bottom check the box that says "allow executing the file....."

That should do it.

---

### Post by Ares Drake on 2008-05-13
> **w4ngsta07 said:**
> 
So I have a problem, when I use your command on Step 5, the terminal says "bash: echo: write error: Invalid argument". 

I tried using this command, "echo "20:18 20:18 20:18 20:18 12:11" > /sys/devices/system/cpu/cpu0/cpufreq/phc_controls" to replace my default(?) voltages, which were "11:47 10:39 8:29 6:18 136:11" on Step 3. 

You might try:
```
sudo -s
``` -> password,
then run your echo command again.

But to be honest, I don't think it is an access problem to that file so it probably won't help. I think it is rather a problem with your value pairs.

I don't know if it is possible to use PHC to keep your cpu constant at 2ghz. I for myself kept the first value for the frequency step and just changed the voltage for it after the :

Try doing the same, you then can still lock your cpu frequency with other methods to 2ghz, i.e. there is a terminal command (wich I can't remember, but I read it in this forum) to change the access permissions of the panel cpu freq applet to let you control your cpu speed manually from there.

---

### Post by Ares Drake on 2008-05-13
Thanks for your hint, I added it to the howto.

> **Harpoon said:**
> w4ngsta07:

you need to make a script executable before you can run it.

The easiest way is right-click the file, open the permissions tab, and and down at the bottom check the box that says "allow executing the file....."

That should do it.

---

### Post by hruskin on 2008-05-13
When I run phc optimize script, I get 
```
./linux-phc-optimize.bash: line 3: functions.bash: No such file or directory
ERROR: Could not load functions.bash 


```
Where can I find functions.bash? 
Thanks

---

### Post by Ares Drake on 2008-05-13
> **hruskin said:**
> 
[/CODE]
Where can I find functions.bash? 
Thanks

Sorry, I just forgot that file. I updated the howto, but without reading through all that again, here is the [link]("http://www.s3pp.de/misc/functions.bash") You need to make it executable as well.

---

### Post by Daelyn on 2008-05-14
Would you undervolting guys with multi core systems please have a look at: 
[http://ubuntuforums.org/showthread.php?p=4960606](http://ubuntuforums.org/showthread.php?p=4960606) 
and provide some thoughts?

---

### Post by w4ngsta07 on 2008-05-15
Is it possible for you to also make a HOW-TO for compiling the linux phc in case our kernels get updated?

---

### Post by M4rotku on 2008-05-15
Will undervolting affect the performance of the laptopz/  It seems to me that if it is using less power, it will be less powerful.

Also, I was wondering if my battery might not be fully enabled.  I have an extra battery pack and in Vista I was able to get 10 hours, with Ubuntu, I get about 4.5 hours and I am assuming that Vista uses more power than Ubuntu.

---

### Post by Ares Drake on 2008-05-16
> **M4rotku said:**
> Will undervolting affect the performance of the laptopz/  It seems to me that if it is using less power, it will be less powerful.

Performance will be the same. The power you saved was just wasted before, did nothing good.


> **M4rotku said:**
> Also, I was wondering if my battery might not be fully enabled.  I have an extra battery pack and in Vista I was able to get 10 hours, with Ubuntu, I get about 4.5 hours and I am assuming that Vista uses more power than Ubuntu.

Is the second battery shown, i.e. in the tray icon or in /proc/acpi/battery?

Win might be a little better in powersaving, but still the difference you post is huge!

> **w4ngsta07 said:**
> Is it possible for you to also make a HOW-TO for compiling the linux phc in case our kernels get updated?

It is not that simple to do and I can't really make a generic how-to for that as I don't know if extra workarounds will be needed. Second, for the new kernel there might be the need of a new patch form the PHC guys.
In the link I gave right at the top there is a german how-to for .16.

In case of a kernel change just try your old .17 module again. If that doesn't work give me a PM and I'll look into it and make a new module.

---

### Post by Charlie708 on 2008-05-19
Is the VID read from the script or from the chip?  I have a T8300 in my T61, and the script bugged out on me, because even when both cores were fully loaded, the script reached 0 on the highest clock level without a crash.

Also, there are two problems (typos) with the guide.  One is when you point to the original acpi-cpufreq.ko, you have two kernel/ directories.  The second one is when you talk about loading the second core; the command burnmmx does nothing, but burnMMX works.  Other than that, extremely helpful :guitar:

---

### Post by sdennie on 2008-05-19
Can you provide some hard numbers on what the power savings is like before and after on your machine.  Something like cleanly booting the machine, logging in, unplugging the AC power, waiting for a few minutes and then running powertop like this (don't touch the machine for 5 minutes after this):

```

sudo powertop -d -t 300

```

Having the average watts used during a 5 minute powertop run on an idle system would be an interesting baseline.  I'm interested in trying this out but only if there is a noticeable drop in power usage.

---

### Post by M4rotku on 2008-05-21
I was in step 2.b.1 and I recieved the following error when i entered the command.

command:
```
sudo cp /lib/modules/`uname -r`/kernel/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko /lib/modules/`uname -r`/kernel/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko.old

```

Error:
```
cp: cannot stat `/lib/modules/2.6.24-16-generic/kernel/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko': No such file or directory

```

If this file doesn't exist, then can I still undervolt?  And how would I go about doing so if able.

---

### Post by Ares Drake on 2008-05-22
> **M4rotku said:**
> I was in step 2.b.1 and I recieved the following error when i entered the command.

command:
```
sudo cp /lib/modules/`uname -r`/kernel/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko /lib/modules/`uname -r`/kernel/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko.old

```

Error:
```
cp: cannot stat `/lib/modules/2.6.24-16-generic/kernel/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko': No such file or directory

```

If this file doesn't exist, then can I still undervolt?  And how would I go about doing so if able.

Seems as if you're not using acpi-cpufreq. Then you can't use this how-to. What did step 1 give you?
```

lsmod | grep acpi_cpufreq

```

---

### Post by stred on 2008-05-23
hi all

my system uses the speedstep.centrino module.. is there a way to force it to use the acpi freq module?

i have a pentium-m 740 (1.73mhz)

thnks

---

### Post by krlhc8 on 2008-05-23
Thanks for the help with my cpu--it works like a charm and doesn't overheat anymore!  Would you know anything about undervolting the graphics card?  It gets fairly hot, too.

At any rate, thanks for the incredible help.

---

### Post by aldeby on 2008-05-23
> **M4rotku said:**
> I was in step 2.b.1 and I recieved the following error when i entered the command.

command:
```
sudo cp /lib/modules/`uname -r`/**kernel/kernel**/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko /lib/modules/`uname -r`/kernel/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko.old

```

Error:
```
cp: cannot stat `/lib/modules/2.6.24-16-generic**/kernel/kernel**/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko': No such file or directory

```

If this file doesn't exist, then can I still undervolt?  And how would I go about doing so if able.

There is a typo in the command on first post tutorial: kernel/ is there twice, whereas the path has only one folder named kernel above arch/!

BTW Thanks a lot for this really interesting tutorial!

---

### Post by Ares Drake on 2008-05-23
> **aldeby said:**
> There is a typo in the command on first post tutorial: kernel/ is there twice, whereas the path has only one folder named kernel above arch/!

BTW Thanks a lot for this really interesting tutorial!

Thanks for pointing out, I corrected the how-to.

---

### Post by Ares Drake on 2008-05-23
> **M4rotku said:**
> I was in step 2.b.1 and I recieved the following error when i entered the command.

command:
```
sudo cp /lib/modules/`uname -r`/kernel/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko /lib/modules/`uname -r`/kernel/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko.old

```

Error:
```
cp: cannot stat `/lib/modules/2.6.24-16-generic/kernel/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko': No such file or directory

```

If this file doesn't exist, then can I still undervolt?  And how would I go about doing so if able.

I am sorry, I just had a typo in the howto. The path to the module is now corrected, so you might try again :)

---

### Post by Ares Drake on 2008-05-23
> **stred said:**
> hi all

my system uses the speedstep.centrino module.. is there a way to force it to use the acpi freq module?

i have a pentium-m 740 (1.73mhz)

thnks

You can try to blacklist the speedstep.centrino module and make the acpi_cpufreq the default to load at boot. However it might be that your notebook has a broken acpi implementation, in which case acpi-cpufreq won't work. So you need to try.

Maybe it is possible to rmmod speedstep.centrino and to insmod acpi_cpufreq to try it without permanent changes.
In case that works you need to can automate it.

---

### Post by stred on 2008-05-24
> **Ares Drake said:**
> You can try to blacklist the speedstep.centrino module and make the acpi_cpufreq the default to load at boot. However it might be that your notebook has a broken acpi implementation, in which case acpi-cpufreq won't work. So you need to try.

Maybe it is possible to rmmod speedstep.centrino and to insmod acpi_cpufreq to try it without permanent changes.
In case that works you need to can automate it.

you are correct, simple blacklisting and adding acpi-cpufreq to etc/modules worked like a charm.. also the script did  very nice job..

voltages before-after:
"41 32 25 18"-> "14 7 3 1"

that's huge difference.. especially in full load i am 10-15 deggres down(difficult to tell cause the fan rans now at different speeds)

thank you very much sir.

---

### Post by aldeby on 2008-05-24
> **stred said:**
> 
that's huge difference.. especially in full load i am 10-15 deggres down(difficult to tell cause the fan rans now at different speeds)


That's not that difficult to tell, just install sensors-applet and you'll have your CPU temperature displayed on your desktop!
```

sudo apt-get install sensors-applet
rightclick on a GNOME panel and select "+ Add to panel"

```

---

### Post by stred on 2008-05-24
> **aldeby said:**
> That's not that difficult to tell, just install sensors-applet and you'll have your CPU temperature displayed on your desktop!
```

sudo apt-get install sensors-applet
rightclick on a GNOME panel and select "+ Add to panel"

```

thnks for your answer but i have allready done that.. 

i didnt explain well my thoughts before..

what i meant is that before in full load i had 62 degrees and fan at 60% approximately

now in full load i am in 52 degrees but fan is at 30-35% so it's difficult to estimate the gains in lower heat produced cause of the different fan speeds.

the major difference is in noise.. now even in full load the system is allmost silent..

---

### Post by eldragon on 2008-05-24
ive got an everex stepnote SA2053T notebook.

ive decided to give this a go, it comes with an intel CPU T2080 dual core thingy.

ran the script, and it didnt hang the computer at all.

so i ended with these settings.


```

$ cat /sys/devices/system/cpu/cpu0/cpufreq/phc_controls 
13:2 10:1 8:1 6:1 1:1 1:1 1:1 1:1 2:1 2:1 

```

is this ok? or is somehow the cpu ignoring the new values?
my script said something like this:
```

Default VIDs: 40 32 27 21 134 134 134 134 134 134 
Current VIDs: 2 1 1 21 134 134 134 134 134 134

```
which seems to set a higher VID for lower freqs? something doesnt add up...

when test started cpu jumped to a new high of 66C, and fan at full speed. it did start scaling down to 55C till it reached a VID of 0.

then the script exited, and (there seems to be a bug), files it created ended up empty.
i deleted the files, ran the script again, and killed the process (allowed it to generate valid files), then edited the file with the tweaks, and gave the first value a 0 (my working value). then the script ran all tests no problems.


the thing is.....how do i know if its working? cpu fan turns on at 60degrees and shuts down at 49degrees, so its just the same everytime. gonna test battery life, but i dont expect this to work, gonna post after..


EDIT: battery life is the same. dead at 1hr, the battery led on the notebook starts blinking. so i guess the notebook isnt undervolting. or am i missing something out?

---

### Post by stred on 2008-05-26
I have downloaded the precompiled module for kerner 2.26.24-17-generic but it doesnt load...

when i try insmod it sais:
insmod: error inserting 'acpi-cpufreq.ko': -1 Invalid module format

---

### Post by krlhc8 on 2008-05-27
2.6.24-17-generic kernel acpi_cpufreq file (32-bit x86 processor compiled version):

Try this attached acpi_cpufreq file for all those who have the upgraded 2.6.27-generic kernel installed.  I'm afraid the one that's originally posted does not work for most people.  

Anyways, thanks for the help.  I went from an idle 24 watts with 2 hours of battery life to 12.8 watts with 4 hours of battery life! (I used Intel's powertop application fyi)

---

### Post by sdennie on 2008-05-27
> **krlhc8 said:**
> 
Anyways, thanks for the help.  I went from an idle 24 watts with 2 hours of battery life to 12.8 watts with 4 hours of battery life!

Are you sure this is correct?  I can't for the life of me find the link (it must have been somewhere on lesswatts.org but, I can never find the useful stuff I've previously found on it (I really think they hide it from me after I've seen it)) but, for example, on my processor, I believe it uses like 13W in the C0 state and like 3.2W in the C3 state.  I don't see how it would be possible to cause an average of 11W decrease in power unless all the C states were running at the normal C3 wattage (which seems impossible because that wattage is essentially the equivalent of "the CPU is turned off").

I still want to try this but, I'd love to see some scientific evidence that this is actually really useful for power savings.  I'm a power savings fanatic but, I don't like to try potentially dangerous things without understand the risk/benefit.

Edit:
I asked a similar question in [http://ubuntuforums.org/showpost.php?p=4999040&postcount=14](http://ubuntuforums.org/showpost.php?p=4999040&postcount=14).  If someone could do that and provide hard numbers I'd be greatly pleased.  ;)

---

### Post by pressureman on 2008-05-27
> **krlhc8 said:**
> I'm afraid the one that's originally posted does not work for most people.

```

acpi-cpufreq.ko: ELF 64-bit LSB relocatable, x86-64, version 1 (SYSV), not stripped

```

It probably mainly works for those people running 64 bit kernels ;-)

---

### Post by eldragon on 2008-05-27
> **krlhc8 said:**
> 2.6.27-generic kernel acpi_cpufreq file (another compiled version):

Try this attached acpi_cpufreq file for all those who have the upgraded 2.6.27-generic kernel installed.  I'm afraid the one that's originally posted does not work for most people.  

Anyways, thanks for the help.  I went from an idle 24 watts with 2 hours of battery life to 12.8 watts with 4 hours of battery life!

dont you mean 2.6.24.17?

im trying right now with this file and the newer kernel, but i dont think there will be any difference....

how did you measure power consumption?

---

### Post by krlhc8 on 2008-05-27
woops, sorry: 2.6.24-17-generic (twas a long night!).  I used Intel's powertop application to find the power consumption.  Did the file work for you?

---

### Post by krlhc8 on 2008-05-27
> **pressureman said:**
> ```

acpi-cpufreq.ko: ELF 64-bit LSB relocatable, x86-64, version 1 (SYSV), not stripped

```

It probably mainly works for those people running 64 bit kernels ;-)
Good point :D

---

### Post by eldragon on 2008-05-27
> **krlhc8 said:**
> woops, sorry: 2.6.24-17-generic (twas a long night!).  I used Intel's powertop application to find the power consumption.  Did the file work for you?

it did work, but it running the script goes all the way to zero. and leaves me (after tweaking the results a bit to let it finnish) with something like:
2 1 1 1 1 1 1 1 for all freqs. (computer never freezes).

i guess my notebook isnt giving a rat's *** about what undervoltage i give to it.

anyone experiencing this? know of a fix for it? i really long for the above 1hour battery life too :D

---

### Post by stred on 2008-05-27
> **krlhc8 said:**
> 2.6.24-17-generic kernel acpi_cpufreq file (32-bit x86 processor compiled version):

Try this attached acpi_cpufreq file for all those who have the upgraded 2.6.27-generic kernel installed.  I'm afraid the one that's originally posted does not work for most people.  

Anyways, thanks for the help.  I went from an idle 24 watts with 2 hours of battery life to 12.8 watts with 4 hours of battery life! (I used Intel's powertop application fyi)



thnks for the module, it worked..instant magic

---

### Post by Sebastral on 2008-05-29
This is so awesome!! I fixed up a gutsy 2.6.22-14-generic kernel by following [this other guide]("https://www.dedigentoo.org/trac/linux-phc/wiki/phc_howto_ubuntu_001"), and for finding the voltages I used the optimizer script. It gave me the shits, cause after every lock up I got an 'error 16 - inconsistent file system' and I had to run reiserfsck --check to fix it, but I got the results;

Default VIDs: 15 14 13 11 10 7 
Current VIDs:  7  5  3  1  1 1

I actually changed it to 7 5 3 1 0 0 initially but then I realized I didn't really know what I was doing. But because the script adds 2 to the lowest VID tested I'm wondering if a VID of -1 is possible? and what about 0? The other guide says 'remember: you can not set lower VIDs than the lowest default VID'. is that true?

I haven't done a full battery unload yet btw, but the remaining time remains stable while remaining percentage goes down.. I guess it needs calibration..

edit; mm, just got a lockup doing nothing special so I now put in 12:**7** 11:**6 **10:**5** 9:**4** 8:**3** 6:**1** which makes more sense anyway :)

---

### Post by pambos on 2008-05-30
Hey guys...
Running the script goes all the way to zero, then tries -1 and the PC crashes. It gave me a message "Recovering CPU", and I waited for a couple of minutes, but it did not recover. Is there anything wrong ? Shouldn't it have stopped before 0 ?

Thanks in advance!

---

### Post by pambos on 2008-05-31
Bump

---

### Post by eldragon on 2008-05-31
> **pambos said:**
> Bump

ive got the same problem, but computer never froze.

 my take is acpi_freq isnt working as advertised with some hardware configurations. (it isnt undervolting at all).

---

### Post by skinnie on 2008-06-01
Hi,first of all thanks for this how to.In windows I have undervolted my T7300 to 0.937v@2.0GHz,and had that undervolt in my last 7.10 installation.
Now I am running a fresh install of kubuntu 64bit,and when I make the 

> cat /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
it says file or folder inexistant (translation of portuguese).
Any thoughts?
Undervolt again would be perfect :guitar:

---

### Post by K.Mandla on 2008-06-01
Very nice howto. I've moved it into Tutorials and Tips. :)

---

### Post by Arthur Archnix on 2008-06-02
I got to the step where you run the script, and it wasn't clear if the script itself started burnMMX or not, so I opened up a new tab and typed "burnMMX". It's not clear to me that it's working or doing anything, it kinda just sits there.

Anyway, then I ran the script and it counted all the way down to zero, but failed to crash my system. It just stopped and said something about "that's not a valid VID to try". I tried to rerun the script but it gave me and error saying
> Load VIDs from 'phc_tweaked_vids'
> ERROR: Wrong VID count!
I've deleted those and am rerunning the script. Everything else appears to be working, and all the steps up to this point have worked great. Any ideas what's going wrong?

---

### Post by eldragon on 2008-06-02
> **skinnie said:**
> Hi,first of all thanks for this how to.In windows I have undervolted my T7300 to 0.937v@2.0GHz,and had that undervolt in my last 7.10 installation.
Now I am running a fresh install of kubuntu 64bit,and when I make the 


it says file or folder inexistant (translation of portuguese).
Any thoughts?
Undervolt again would be perfect :guitar:

hmmm, first of all, youve got to install the 64bit version of the kernel module, which i dont know if its available :(

---

### Post by Ares Drake on 2008-06-02
> **Arthur Archnix said:**
> I got to the step where you run the script, and it wasn't clear if the script itself started burnMMX or not, so I opened up a new tab and typed "burnMMX". It's not clear to me that it's working or doing anything, it kinda just sits there.

One thread of burnMMX is started automatically. You can verify this with "top" in a terminal or the gnome system monitor. In case you have a dualcore just start a second thread of burnMMX as described in the howto.

> **Arthur Archnix said:**
> Anyway, then I ran the script and it counted all the way down to zero, but failed to crash my system. It just stopped and said something about "that's not a valid VID to try". I tried to rerun the script but it gave me and error saying

I've deleted those and am rerunning the script. Everything else appears to be working, and all the steps up to this point have worked great. Any ideas what's going wrong?

The voltage are calculated with a formula that looks like voltage = a+bx, where a is a base level of voltage witch is increased in x steps with a step size of b.
The script returning zero means x=0, so you don't need to increase the base voltage for your cpu. So everything should be fine, the script will write 1 instead of zero to its result file and you can use that. In my example I get zeros as well.

---

### Post by Sebastral on 2008-06-02
> **Sebastral said:**
> The other guide says 'remember: you can not set lower VIDs than the lowest default VID'. is that true?
I know. it would be horrible news, cause if true it explains why some people don't get battery time improvements.. but is it? or how can I find out? I don't seem to have battery improvements doing office work and the cpu running on lowest speed while the VID went from 7 to 1..

---

### Post by Arthur Archnix on 2008-06-02
> **Ares Drake said:**
> The script returning zero means x=0, so you don't need to increase the base voltage for your cpu. So everything should be fine, the script will write 1 instead of zero to its result file and you can use that. In my example I get zeros as well.

I don't think I made myself clear. The script doesn't do anything. It steps down to zero, stops and says run it again, and then fails to run claiming there is not a valid VID count. It's almost like the script has to fail in order to work, but because it can't make my system crash it returns errors. Almost like saying, check for crash=1, error, crash=0, exiting. This is just a guess. In any event, I can't get it to generate anything because I can only run it once.

Should I do a hard power off just before it finishes the very last test of VID=0? Maybe that will work?

Also, it wasn't clear from the comments. Is the acpi module you've supplied for a x86 or x86-64 system? Someone else attached a file, but what was that for? 32 or 64?

Thanks for the answer regarding the burnMMX.

EDIT: Do I need to run the script while on battery power?

---

### Post by Ares Drake on 2008-06-02
> **Arthur Archnix said:**
> I don't think I made myself clear. The script doesn't do anything. It steps down to zero, stops and says run it again, and then fails to run claiming there is not a valid VID count. It's almost like the script has to fail in order to work, but because it can't make my system crash it returns errors. Almost like saying, check for crash=1, error, crash=0, exiting. This is just a guess. In any event, I can't get it to generate anything because I can only run it once.

Should I do a hard power off just before it finishes the very last test of VID=0? Maybe that will work?

I'll try to explain again. The cpu voltage is a calculated value. It is calculated```
 voltage=base voltage + number of steps (=VID) * stepsize

```
For Pentium M cpus the base voltage is 700.0 mV and stepsize is 16mV, for Core(2)Duos it is 712.5 mV and stepsize 12.5mV.

The optmize script lowers the number of steps step by step to see if your cpu is stable with a lower step and thus lower voltage. In your case it reaches zero, that means your cpu is stable with just the base voltage. So it doesn't lock up. It reaches zero even for the highest frequency and as the lower frequencies would need even less voltage and you cannot go below base voltage, the script doesn't need to run for the lower frequencies. As 0 for VID may not work you can just use 1. So you are 1 step above base voltage, that would mean for example for a core2duo 712.5mV+1*12.5mV=725mV.
Your values are then for example 12:1 10:1 8:1 6:1. (The values before the colon are for the frequency and from my machine, you have to use yours).

That you can go down to base voltage either means that you are lucky and got a nice cpu or that your acpi is broken and the instruction to lower the voltage gets ignored. Are you positive that the phc-modified acpi-cpufreq is installed correctly? Then maybe your acpi table is broken, I am unfortunately no expert on acpi.

> **Arthur Archnix said:**
>  Also, it wasn't clear from the comments. Is the acpi module you've supplied for a x86 or x86-64 system? Someone else attached a file, but what was that for? 32 or 64?

Both modules are for 32bit.

---

### Post by Arthur Archnix on 2008-06-02
Ok, I think I understand now. Thanks for the patient replies. I used your settings applied at boot in rc.local (my values were the same, so I could just use those directly), and after a reboot I show the following:
> arthur@archnix:~$ cat /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
12:1 10:1 8:1 6:1 
So, it appears that the settings have been applied properly, I suppose if it crashes on my I just reboot in single user mode and increase the multiplier. So, if I edit a video and the system crashes, I can change 12:1 10:1 etc... to 12:2 10:2.. and so on. 

Thanks again,

---

### Post by eldragon on 2008-06-02
> **Ares Drake said:**
> I'll try to explain again. The cpu voltage is a calculated value. It is calculated```
 voltage=base voltage + number of steps (=VID) * stepsize

```
For Pentium M cpus the base voltage is 700.0 mV and stepsize is 16mV, for Core(2)Duos it is 712.5 mV and stepsize 12.5mV.

The optmize script lowers the number of steps step by step to see if your cpu is stable with a lower step and thus lower voltage. In your case it reaches zero, that means your cpu is stable with just the base voltage. So it doesn't lock up. It reaches zero even for the highest frequency and as the lower frequencies would need even less voltage and you cannot go below base voltage, the script doesn't need to run for the lower frequencies. As 0 for VID may not work you can just use 1. So you are 1 step above base voltage, that would mean for example for a core2duo 712.5mV+1*12.5mV=725mV.
Your values are then for example 12:1 10:1 8:1 6:1. (The values before the colon are for the frequency and from my machine, you have to use yours).

That you can go down to base voltage either means that you are lucky and got a nice cpu or that your acpi is broken and the instruction to lower the voltage gets ignored. Are you positive that the phc-modified acpi-cpufreq is installed correctly? Then maybe your acpi table is broken, I am unfortunately no expert on acpi.



Both modules are for 32bit.

well, thats where i was heading, ive got the module installed correctly (if i get phc_control file it should be fine, right?), yet, i dont see any difference with all voltages on 1, or the default (Which is something like 40). i guess my acpi is not compatible enough...which  is too bad, battery life is next to useless :( . Under windows, it took twice the time to drain it completely.

this is no show stopper for me, but its annoying none the less. and it might definately be a show stopper for others.

---

### Post by Arthur Archnix on 2008-06-03
Anyone else having trouble resuming from suspend after using this cpufreq module? If I copy the old one back it resumes fine. With this one however, the fan spins up to full and the video never gets restored.

Can someone confirm?

---

### Post by sullust on 2008-06-03
hi all,

I installed this patch and got my new values. I edited the rc.local file, and put the new voltage pairs in. But now, after i reboot, the system starts up but my screen goes black right before xserver starts and prompts me for a login.

I think it may be caused by the speedstep-centrino module I see, but I am not sure how to blacklist it. Has anyone else seem this?

How do I blacklist the centrino module?

---

### Post by sullust on 2008-06-04
Apparently it wasn't the speedstep-centrino module. The optimize script just set my values too low.

I ran into the same issue as Arthur, in that the first time I ran the optimize script, the steps counted all the way down to zero, then lock when the script exited.

I reset the script and executed it until the end. The results:
Before: 12:44 10:36 8:28 6:19 
After: 12:46 10:1 8:1 6:1

When I tried to run on these settings, my laptop display would just turn off right before it booted into xserver and the fan would go into overdrive. Eventually, I was able to test certain settings by running the following script (I have a dual core cpu):

```

dp@dp-acer:~$ sudo -i
[sudo] password for dp:
root@dp-acer:~# cd /sys/devices/system/cpu/
root@dp-acer:/sys/devices/system/cpu# 
root@dp-acer:/sys/devices/system/cpu# for PHC_VID in ./cpu*/cpufreq/phc_vids; do echo "35 25 5 1" > $PHC_VID; done

```

...and just keep lowering the numbers until my laptop froze.

This seems to be a fairly incomplete solution though, because apparently my numbers can be lower once xserver is running, but need to be higher to start it, otherwise I get the black screen again.

Also, my laptop doesn't seem to be running that much cooler. It ran from 65C-70C before, and now seems to be 63C-68C. So not much difference. Maybe I just need to see if I can get the numbers lower. Windoze runs pretty cool and quiet though, and that's aggravating!

---

### Post by M4rotku on 2008-06-04
I have the 2.6.24-18-generic kernel, is there any way to undervolt that using the same meathod? wouldn't I just need to use a different patch?  I really need to undervolt due to how much I use this laptop.

Much thanks,
M4rotku

---

### Post by jocko on 2008-06-05
> **M4rotku said:**
> I have the 2.6.24-18-generic kernel, is there any way to undervolt that using the same meathod? wouldn't I just need to use a different patch?  I really need to undervolt due to how much I use this laptop.

Much thanks,
M4rotku

I managed to get it working by patching the kernel source and recompiling the acpi-cpufreq module. I found [this old howto]("https://www.dedigentoo.org/trac/linux-phc/wiki/phc_howto_ubuntu_001"), which got me started.

Here's a quick howto, updated to work on hardy (just copy-paste the commands to a terminal):

1. Open up a terminal and install subversion, the kernel source and build-essential:
```
sudo apt-get install subversion linux-source build-essential
```2. Get the linux-PHC patch:
```
mkdir ~/linux-PHC
cd linux-PHC
svn co http://phcpatches.googlecode.com/svn/trunk/acpi-cpufreq phcpatches/cpufreq
```3. Apply the patch to the kernel and build the module:
```
sudo bash
cd /usr/src
tar -xjf linux-source-2.6.24.tar.bz2
cd linux-source-2.6.24/
cp ~/linux-PHC/phcpatches/cpufreq/patches/linux-phc-kernel-vanilla-2.6.24-rc1.patch .
patch -p1 < linux-phc-kernel-vanilla-2.6.24-rc1.patch
cp /boot/config-$(uname -r) .config
make oldconfig
make prepare
make scripts
make M=./arch/x86/kernel/cpu/cpufreq
```4. Replace your old module:
```
cp /lib/modules/$(uname -r)/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko /lib/modules/$(uname -r)/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko.old
cp arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko /lib/modules/$(uname -r)/kernel/arch/x86/kernel/cpu/cpufreq
depmod
``` **Reboot**.

I hope I didn't miss anything...

---

### Post by skinnie on 2008-06-05
> **jocko said:**
> I managed to get it working by patching the kernel source and recompiling the acpi-cpufreq module. I found [this old howto]("https://www.dedigentoo.org/trac/linux-phc/wiki/phc_howto_ubuntu_001"), which got me started.

Here's a quick howto, updated to work on hardy (just copy-paste the commands to a terminal):

1. Open up a terminal and install subversion, the kernel source and build-essential:
```
sudo apt-get install subversion linux-source build-essential
```2. Get the linux-PHC patch:
```
mkdir ~/linux-PHC
cd linux-PHC
svn co http://phcpatches.googlecode.com/svn/trunk/acpi-cpufreq phcpatches/cpufreq
```3. Apply the patch to the kernel and build the module:
```
sudo bash
cd /usr/src
tar -xjf linux-source-2.6.24
cd linux-source-2.6.24/
cp ~/linux-PHC/phcpatches/cpufreq/patches/linux-phc-kernel-vanilla-2.6.24-rc1.patch .
patch -p1 < linux-phc-kernel-vanilla-2.6.24-rc1.patch
cp /boot/config-$(uname -r) .config
make oldconfig
make prepare
make scripts
make M=./arch/x86/kernel/cpu/cpufreq
```4. Replace your old module:
```
rmmod acpi-cpufreq
cp /lib/modules/$(uname -r)/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko /lib/modules/$(uname -r)/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko.old
cp arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko /lib/modules/$(uname -r)/kernel/arch/x86/kernel/cpu/cpufreq
depmod
modprobe acpi-cpufreq
```I hope I didn't miss anything...

Can I try it in 64bit version of ubuntu or it won't work?

---

### Post by jocko on 2008-06-05
> **skinnie said:**
> Can I try it in 64bit version of ubuntu or it won't work?

I did it in 64 bit, so yes, try it. I haven't tried in 32 bit, but I guess it works with the same instructions...

> **skinnie said:**
>  Edit:tried and it worked..only thing is when doing  	Quote:
 	 	 		 			 				rmmod acpi-cpufreq 			 		 	 	 
 it says it is in use.
As I knew +- the values for my voltages,I did
sudo nano /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
and edited...

If the module is in use, just skip the  "rmmod" and "modprobe" commands in step 4 and reboot instead.
Remember that if you have a dual core cpu, you need to change both cores.
So edit both /sys/devices/system/cpu/[COLOR=Red]cpu0[/COLOR]/cpufreq/phc_controls and /sys/devices/system/cpu/[COLOR=Red]cpu1[/COLOR]/cpufreq/phc_controls

---

### Post by skinnie on 2008-06-05
> **jocko said:**
> I did it in 64 bit, so yes, try it. I haven't tried in 32 bit, but I guess it works with the same instructions...
How do I setup the vids manually and make them applied every reboot?

---

### Post by jocko on 2008-06-05
> **skinnie said:**
> How do I setup the vids manually and make them applied every reboot?
See step 5 in [post #1]("http://ubuntuforums.org/showpost.php?p=4908896&postcount=1") in this thread.

---

### Post by skinnie on 2008-06-05
> **jocko said:**
> See step 5 in [post #1]("http://ubuntuforums.org/showpost.php?p=4908896&postcount=1") in this thread.

Sorry I didn't notice.
I did 
> sudo bash
echo "11:32 10:16 8:10 6:9 136:11" > /sys/devices/system/cpu/cpu0/cpufreq/phc_controls

rebooted....
then
> cat /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
and obtain the default values
> 11:47 10:38 8:28 6:18 136:11 

any clue?

> **jocko said:**
> I did it in 64 bit, so yes, try it. I haven't tried in 32 bit, but I guess it works with the same instructions...



If the module is in use, just skip the  "rmmod" and "modprobe" commands in step 4 and reboot instead.
Remember that if you have a dual core cpu, you need to change both cores.
So edit both /sys/devices/system/cpu/[COLOR=Red]cpu0[/COLOR]/cpufreq/phc_controls and /sys/devices/system/cpu/[COLOR=Red]cpu1[/COLOR]/cpufreq/phc_controls
That's what I did...I verified that once you change the values in cpu0,it will change to the same in cpu1

---

### Post by jocko on 2008-06-05
> **skinnie said:**
> Sorry I didn't notice.
I did 


rebooted....
then

and obtain the default values


any clue?


That's what I did...I verified that once you change the values in cpu0,it will change to the same in cpu1

Read step 5 again. It tells you to add the line to your /etc/rc.local file, to have it apply during boot.
And I need to change it for both cpu0 and cpu1, otherwise core 1 will run at the default voltage while core 0 runs at lower voltage.

---

### Post by skinnie on 2008-06-05
> **jocko said:**
> Read step 5 again. It tells you to add the line to your /etc/rc.local file, to have it apply during boot.
And I need to change it for both cpu0 and cpu1, otherwise core 1 will run at the default voltage while core 0 runs at lower voltage.

Thank you very much,I wasn't understanding quite well the thing.
Undervolting sucessful :guitar:
Ubuntu 8.04 64bit kernel 2.6.24-18-generic

---

### Post by sullust on 2008-06-05
> **Sebastral said:**
> This is so awesome!! I fixed up a gutsy 2.6.22-14-generic kernel by following [this other guide]("https://www.dedigentoo.org/trac/linux-phc/wiki/phc_howto_ubuntu_001"), and for finding the voltages I used the optimizer script. 

Has anyone run the 'msrinfo' utility after making these changes? According to the guide mentioned by Sebastral (which I later verified as true) lowering the voltage below the minimum doesn't have any effect. (msrinfo tool is explained in quoted guide, with a link to dl it.)

Example:
My original settings were 12:44 10:36 8:28 6:19. After tweaking my settings are 34 23 1 1.

However, running msrinfo tells me a different story:

        |     CPU 0     |     CPU 1     |
        +-------+-------+-------+-------+
        | FID   | VID   | FID   | VID   |
--------+-------+-------+-------+-------+
Min     | 6     | 19    | 6     | 19    |
Max     | 12    | 44    | 12    | 44    |
--------+-------+-------+-------+-------+
Target  | 6     |** 1 **    | 6     |** 1 **    |
Current | 6     | **19 **   | 6     | **19**    |
--------+-------+-------+-------+-------+

So basically, even though I am attempting to lower my base voltage, it's not going any lower than the original setting. The 12:44 -> 12:34 setting does limit the upper end though, so during heavy cpu loads it should run a bit cooler than normal.

Has anyone else run this tool to see the results? Since my laptop fan runs on high at my base voltage, I haven't really seen any net inprovement. I am wondering if the people that have seen their core temps go down originally started with a minimum setting higher than their minimum voltage, or if different versions of the patch allow forcing the minimum voltage lower.

---

### Post by krlhc8 on 2008-06-05
How do you get msrinfo?

---

### Post by RadiusXE on 2008-06-05
Hi...
I' ve got some problem' s

1.I compile my own module (I have 64b core)
tar -xjf linux-source-2.6.24
err... a change the command to tar -xjf linux-source-2.6.24.tar.bz2
all ok

2. script runs to zero, then write some info and notebook freezes
what can I do? NTB Fujitsu Siemens Esprimo mobile D9500, C2D T7300@2GHz, Ubuntu 8.04 LTS 64b

Please help, fan is **** I need undervolting or something to regulate fan (or all together)

:confused:

---

### Post by M4rotku on 2008-06-05
Jocko,

When I entered the command

```
root@joey-laptop:/usr/src# tar -xjf linux-source-2.6.24

```

I recieve the following errors:

```
tar: linux-source-2.6.24: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

```

and then I "ls" to see what files were there and this is what i got:

```
root@joey-laptop:/usr/src# ls
linux-headers-2.6.24-18          linux-source-2.6.24.tar.bz2
linux-headers-2.6.24-18-generic  rpm

```

so the file "linux-source-2.6.24" was not there, there was only a .tar version of such file.

How do I do this with the tar'ed file?

---

### Post by sullust on 2008-06-06
> **krlhc8 said:**
> How do you get msrinfo?

From the guide I linked to above:
There is a tool named msrinfo that shows up information about current FIDs and VIDs and those you set (they can be different for example if you set a VID below the lowest one).

Download the tool here ( [https://www.dedigentoo.org/bdz/linux-phc/]("https://www.dedigentoo.org/bdz/linux-phc/") ) and compile it. You may need to copy the msr.h (same source like msrinfo) to "/usr/include/asm/".

---

### Post by jocko on 2008-06-06
> **M4rotku said:**
> Jocko,

When I entered the command

```
root@joey-laptop:/usr/src# tar -xjf linux-source-2.6.24

```I recieve the following errors:

```
tar: linux-source-2.6.24: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

```and then I "ls" to see what files were there and this is what i got:

```
root@joey-laptop:/usr/src# ls
linux-headers-2.6.24-18          linux-source-2.6.24.tar.bz2
linux-headers-2.6.24-18-generic  rpm

```so the file "linux-source-2.6.24" was not there, there was only a .tar version of such file.

How do I do this with the tar'ed file?
Apparently I didn't give you the complete command...
It should be:
```
tar -xjf linux-source-2.6.24.tar.bz2
```

---

### Post by RadiusXE on 2008-06-06
> **M4rotku said:**
> Jocko,

When I entered the command

```
root@joey-laptop:/usr/src# tar -xjf linux-source-2.6.24

```

I recieve the following errors:

```
tar: linux-source-2.6.24: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

```
...

I wrote it at post 64, 


tar -xjf linux-source-2.6.24.tr.bz2

---

### Post by RadiusXE on 2008-06-06
> **Arthur Archnix said:**
> Anyone else having trouble resuming from suspend after using this cpufreq module? If I copy the old one back it resumes fine. With this one however, the fan spins up to full and the video never gets restored.

Can someone confirm?

for me doesn' t work hibernation (ntb make only shutdown)

:confused:

---

### Post by Arthur Archnix on 2008-06-07
I'm not sure if this is related to the suspend issue some have noted... > While under*volting* has a clear measurable effect, it's not clear if under*clocking* really works. /proc/cpuinfo reflects the underclocked frequency, but enabling debug output on cpufreq causes it to say things like "CPU frequency out of sync: cpufreq and timing core thinks of 533000, is 800000 kHz." where the former is the chosen underclocked frequency and the latter is the documented minimum frequency. This discrepancy also causes [Software Suspend 2]("http://www.thinkwiki.org/wiki/Software_Suspend_2") to oops during suspend.

Quoted from here: [http://www.thinkwiki.org/wiki/Pentium_M_undervolting_and_underclocking](http://www.thinkwiki.org/wiki/Pentium_M_undervolting_and_underclocking)

---

### Post by M4rotku on 2008-06-07
Jocko, where do I pick up in the main guide after the steps you gave me?

Much thanks,
M4rotku

---

### Post by jocko on 2008-06-07
> **M4rotku said:**
> Jocko, where do I pick up in the main guide after the steps you gave me?

Much thanks,
M4rotku

What I described was instead of step 2, so start at step 3 (skip the reboot if you already done it, of course).
Good luck.

---

### Post by M4rotku on 2008-06-07
I ran the ./linux-phc-optimize.bash script and the first time it went though and told me that the lowest acceptable VID is 0.

I ran the script again per guide and recieved the following response:

> Read phc_default_vids:
> Success!

Load VIDs from 'phc_tweaked_vids'
> ERROR: Wrong VID count!


What does this mean and is it because I'm using a different kernel?

Edit:  Also, when I run "cat /sys/devices/system/cpu/cpu0/cpufreq/phc_controls", I only get 2 outputs:

9:43 6:19 

instead of the usual four that everyone else is talking about.  could this be the problem?

---

### Post by sullust on 2008-06-09
Has anyone checked out the REAL frequency their CPU is running at after these changes using the msrinfo tool mentioned on page 7?

I am really curious if anyone has been able to get their CPU to operate at a voltage lower than their original minimum.

For example, even after I changed my lowest FID to use a VID of 1, it is still running at 19.

---

### Post by dixon on 2008-06-09
> **sullust said:**
> Has anyone checked out the REAL frequency their CPU is running at after these changes using the msrinfo tool mentioned on page 7?

I am really curious if anyone has been able to get their CPU to operate at a voltage lower than their original minimum.

For example, even after I changed my lowest FID to use a VID of 1, it is still running at 19.
I was not able to lower my voltage under the original minimum...

EDIT: My cpu is Core 2 Duo T5470

---

### Post by stred on 2008-06-11
hi all, anyone has handy the acpi-cpufreq.ko for kernel 2.6.24.18 32-bit?

thnks.

---

### Post by ssc351 on 2008-06-11
Thanks!  Works so far...had similar problems as other people with the VID going to zero...just put in "1"s at the end as shown in some previous posts  and seems to work great with video running.

Don't know if I have gained any battery life or not, since my battery is broken and only lasts 10mins, but bottom of the computer is definitely cooler.

---

### Post by SyntheticShield on 2008-06-12
I tried running lsmod | grep acpi_cpufreq and got no output at all.  So does that mean I cannot implement this proceedure?  If so, is there any work around?  I have an AMD Sempron 3000+ (1.8ghz) processor in my laptop and the fan is on nearly constantly and would love to do anything that would save the battery and cut down on the fan use and heat.

I also went to the PHC website and I dont see anywhere that you can download the files.

Im also on the 2.6.24.18 kernel.

I tried rmmod on the speedstep.centrino and insmod acpi_cpufreq and it tells me that module speedstep doesnt exist and it cant read acpi_cpufreq as no such file or directory exists.

Is there anything I can do or am I stuck?

---

### Post by skinnie on 2008-06-12
> **stred said:**
> hi all, anyone has handy the acpi-cpufreq.ko for kernel 2.6.24.18 32-bit?

thnks.

2 or three pages before you have the solution to "new" kernels.

---

### Post by Ares Drake on 2008-06-13
I updated the howto with a 32bit module for 2.6.24-18 and a mini-howto to compile the module yourself in case you need a 64bit module or for a newer kernel version.

---

### Post by pressureman on 2008-06-16
> **Ares Drake said:**
> I updated the howto with a 32bit module for 2.6.24-18 and a mini-howto to compile the module yourself in case you need a 64bit module or for a newer kernel version.

2.6.24-19 just got released... :-?

---

### Post by InfinityCircuit on 2008-06-17
You must enable CONFIG_CPU_FREQ_GOV_USERSPACE to use the script.

---

### Post by aashay on 2008-06-17
I can confirm it not working for me. The scripts goes through the values till -1 where it crashes. Even after echoing the values 13:3 10:1 8:1 6:1 to phc_controls, while working at 800MHZ, phctool shows the target VID to be 3 (.75V) and the current to be 19 (.95V) which was the default for 800MHZ. So basically phc was unable to really use the new values. 
Also, I just downloaded and installed the patched module provided in the first post. Would it make a difference if I compiled it on my own?

---

### Post by Hooya on 2008-06-18
I've looked through the thread.  Any new information on those of us using speedstep?  I've tried blacklisting it and using the acpi_cpufreq but it didn't work since I was just guessing on how to blacklist one and invoke the other.  Can someone detail how to do this?  What about just using the speedstep module?

I have a Celeron processor, so it's possible I can't even do this though.  Can anyone confirm?

Thanks in advance.

Edit, here is the contents of /proc/modules if that will help:
```
af_packet 23812 4 - Live 0xefd10000
binfmt_misc 12808 1 - Live 0xefd0b000
i915 32512 2 - Live 0xefc88000
drm 82452 3 i915, Live 0xefc97000
ppdev 10372 0 - Live 0xefc79000
ipv6 267780 10 - Live 0xefcc8000
speedstep_lib 6532 0 - Live 0xefc76000
cpufreq_userspace 5284 0 - Live 0xefc73000
cpufreq_ondemand 9740 0 - Live 0xefc6f000
cpufreq_conservative 8712 0 - Live 0xefc6b000
cpufreq_stats 7104 0 - Live 0xefb74000
cpufreq_powersave 2688 0 - Live 0xefb1f000
container 5632 0 - Live 0xefb77000
toshiba_acpi 12100 0 - Live 0xefb4c000
sbs 15112 0 - Live 0xefb7a000
sbshc 7680 1 sbs, Live 0xefb50000
dock 11280 0 - Live 0xefb70000
iptable_filter 3840 0 - Live 0xef96b000
ip_tables 14820 1 iptable_filter, Live 0xefb6b000
x_tables 16132 1 ip_tables, Live 0xefaee000
lp 12324 0 - Live 0xefb47000
freq_table 5536 2 cpufreq_ondemand,cpufreq_stats, Live 0xefb02000
joydev 13120 0 - Live 0xefb1a000
pcmcia 40876 0 - Live 0xefb60000
snd_intel8x0 35356 2 - Live 0xefb27000
snd_ac97_codec 101028 1 snd_intel8x0, Live 0xefb81000
ac97_bus 3072 1 snd_ac97_codec, Live 0xefaab000
arc4 2944 2 - Live 0xef8f3000
snd_pcm_oss 42144 0 - Live 0xefb54000
snd_mixer_oss 17920 1 snd_pcm_oss, Live 0xefb21000
ecb 4480 2 - Live 0xefaff000
blkcipher 8324 1 ecb, Live 0xefafb000
snd_pcm 78596 3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss, Live 0xefb32000
snd_seq_dummy 4868 0 - Live 0xefaf8000
parport_pc 36260 0 - Live 0xefb10000
parport 37832 3 ppdev,lp,parport_pc, Live 0xefb05000
evdev 13056 6 - Live 0xefaf3000
serio_raw 7940 0 - Live 0xefaa5000
rt2500pci 20352 0 - Live 0xefa94000
rt2x00pci 11264 1 rt2500pci, Live 0xef9ba000
rt2x00lib 22528 2 rt2500pci,rt2x00pci, Live 0xefae7000
snd_seq_oss 35584 0 - Live 0xefab2000
rfkill 8592 2 rt2x00lib, Live 0xefa90000
input_polldev 5896 1 rt2x00lib, Live 0xef9c5000
crc_itu_t 3072 1 rt2x00lib, Live 0xef890000
snd_seq_midi 9376 0 - Live 0xefa8c000
psmouse 40336 0 - Live 0xefa9a000
mac80211 165652 3 rt2500pci,rt2x00pci,rt2x00lib, Live 0xefabd000
pcspkr 4224 0 - Live 0xef9c2000
snd_rawmidi 25760 1 snd_seq_midi, Live 0xef9f8000
yenta_socket 27276 1 - Live 0xef9e1000
rsrc_nonstatic 13696 1 yenta_socket, Live 0xef9dc000
cfg80211 15112 1 mac80211, Live 0xef9d7000
pcmcia_core 40596 3 pcmcia,yenta_socket,rsrc_nonstatic, Live 0xefa81000
eeprom_93cx6 3200 1 rt2500pci, Live 0xef83d000
snd_seq_midi_event 8320 2 snd_seq_oss,snd_seq_midi, Live 0xef9be000
snd_seq 54224 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event, Live 0xef9e9000
snd_timer 24836 2 snd_pcm,snd_seq, Live 0xef9a8000
snd_seq_device 9612 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq, Live 0xef9b6000
snd 56996 15 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device, Live 0xef9c8000
video 19856 0 - Live 0xef9b0000
output 4736 1 video, Live 0xef99c000
soundcore 8800 1 snd, Live 0xef9a4000
snd_page_alloc 11400 2 snd_intel8x0,snd_pcm, Live 0xef945000
iTCO_wdt 13092 0 - Live 0xef99f000
iTCO_vendor_support 4868 1 iTCO_wdt, Live 0xef94c000
ac 6916 0 - Live 0xef949000
battery 14212 0 - Live 0xef994000
button 9232 0 - Live 0xef990000
shpchp 34452 0 - Live 0xef957000
pci_hotplug 30880 1 shpchp, Live 0xef962000
intel_agp 25492 1 - Live 0xef94f000
agpgart 34760 3 drm,intel_agp, Live 0xef8fb000
ext3 136712 1 - Live 0xef96d000
jbd 48404 1 ext3, Live 0xef92d000
mbcache 9600 1 ext3, Live 0xef81d000
sg 36880 0 - Live 0xef93a000
sr_mod 17956 0 - Live 0xef8f5000
cdrom 37408 1 sr_mod, Live 0xef8da000
sd_mod 30720 3 - Live 0xef8e5000
pata_acpi 8320 0 - Live 0xef8d6000
ata_generic 8324 0 - Live 0xef839000
ata_piix 19588 2 - Live 0xef854000
e100 37388 0 - Live 0xef8bf000
mii 6400 1 e100, Live 0xef83f000
libata 159344 3 pata_acpi,ata_generic,ata_piix, Live 0xef905000
ehci_hcd 37900 0 - Live 0xef8cb000
uhci_hcd 27024 0 - Live 0xef8b7000
scsi_mod 151436 4 sg,sr_mod,sd_mod,libata, Live 0xef866000
usbcore 146028 3 ehci_hcd,uhci_hcd, Live 0xef892000
thermal 16796 0 - Live 0xef84e000
processor 36872 2 thermal, Live 0xef85b000
fan 5636 0 - Live 0xef836000
fbcon 42912 0 - Live 0xef842000
tileblit 3456 1 fbcon, Live 0xef825000
font 9472 1 fbcon, Live 0xef821000
bitblit 6784 1 fbcon, Live 0xef818000
softcursor 3072 1 bitblit, Live 0xef81b000
fuse 50580 1 - Live 0xef828000

```

---

### Post by aashay on 2008-06-19
> **aashay said:**
> I can confirm it not working for me. The scripts goes through the values till -1 where it crashes. Even after echoing the values 13:3 10:1 8:1 6:1 to phc_controls, while working at 800MHZ, phctool shows the target VID to be 3 (.75V) and the current to be 19 (.95V) which was the default for 800MHZ. So basically phc was unable to really use the new values. 
Also, I just downloaded and installed the patched module provided in the first post. Would it make a difference if I compiled it on my own?

Okay an update on this.
Seems my CPU (Core 2 Duo, don't know the exact model no.) limits the VIDs to a lower bound of 19. So I just set 19 as the VID for all the frequencies. Works like a charm. The processor is 10-15 degrees (C) cooler than what it used to be.

---

### Post by tesna on 2008-06-20
mine always crashes when I tried to manually echoing the values. 

```

tesna@zorg:/etc/init.d$ cat /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
11:45 10:43 8:33 6:23 136:15 

```

the script tells me only 4 values, which is:
```

tesna@zorg:~$ cat phc_tweaked_vids 
24 24 1 1 15

```

I tried to echoing 11:24 10:24 8:1 6:1 to /sys/devices/system/cpu/cpu0/cpufreq/phc_controls  then it crash instantly.

Tried to echoing higher values than those four, and I added fifth values with them, no success. still crash. 

I was able to lower the voltage when booting into windows (I forgot the program name), and got 15-20 degrees decrease in cpu temp. Now using ubuntu my cpu sits at 63 degrees C at idle :( 

How do I fix this?

---

### Post by aashay on 2008-06-20
> **tesna said:**
> mine always crashes when I tried to manually echoing the values. 

```

tesna@zorg:/etc/init.d$ cat /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
11:45 10:43 8:33 6:23 136:15 

```

the script tells me only 4 values, which is:
```

tesna@zorg:~$ cat phc_tweaked_vids 
24 24 1 1 15

```

I tried to echoing 11:24 10:24 8:1 6:1 to /sys/devices/system/cpu/cpu0/cpufreq/phc_controls  then it crash instantly.

Tried to echoing higher values than those four, and I added fifth values with them, no success. still crash. 

I was able to lower the voltage when booting into windows (I forgot the program name), and got 15-20 degrees decrease in cpu temp. Now using ubuntu my cpu sits at 63 degrees C at idle :( 

How do I fix this?
The last in the default list 136:15 seems a bit weird if you ask me. As an alternate, look up on phctool. It's got a GUI if you are more comfortable that way

---

### Post by aldeby on 2008-06-20
I also get 11:vv 10:vv 8:vv 6:vv 136:vv 

this is weired since I noticed that there is a fixed divider between the processor frequency and the number before the colon: this is 200.

This is valid for all the first 4 values, however my lowest frequency 800Mhz although should be represented in the phc_controls and phc_default_controls as 4 it is actually represented by 136.

I can't understand why...

PS: my lowest possible voltage is v ID 11, 0.850 v. PHC seems not capable to further lower it.

---

### Post by tesna on 2008-06-20
Update. I tried to set the CPU frequency at a fixed frequency (userspace) before I echoing the values, and guess what. My computer didn't crash! I changed the freq (increase/decrease) after echoing the values and it also didn't crash. But as soon I changed the cpu freq mode to "ondemand" my system instantly crash. Oh I'm confused.

---

### Post by eldragon on 2008-06-20
> **aashay said:**
> Okay an update on this.
Seems my CPU (Core 2 Duo, don't know the exact model no.) limits the VIDs to a lower bound of 19. So I just set 19 as the VID for all the frequencies. Works like a charm. The processor is 10-15 degrees (C) cooler than what it used to be.

oh, where did you find that? i have the exact same problem and would love to see if my vids kick at a lower limit too :(

---

### Post by aashay on 2008-06-21
> **eldragon said:**
> oh, where did you find that? i have the exact same problem and would love to see if my vids kick at a lower limit too :(
I used phctool. You can get it from here: [http://phc.athousandnights.de/files]("http://phc.athousandnights.de/files")
The tool has a Analysis tab as you can see in the screenshot.
To get this to work, you first need to ```
sudo modprobe msr
```
After this, let the script run and keep refreshing the analysis tab. 
For me, the target vids kept decresing, but the reached vid was stuck at 19... indicating that it was the lower limit for my CPU.

---

### Post by eldragon on 2008-06-21
> **aashay said:**
> I used phctool. You can get it from here: [http://phc.athousandnights.de/files]("http://phc.athousandnights.de/files")
The tool has a Analysis tab as you can see in the screenshot.
To get this to work, you first need to ```
sudo modprobe msr
```
After this, let the script run and keep refreshing the analysis tab. 
For me, the target vids kept decresing, but the reached vid was stuck at 19... indicating that it was the lower limit for my CPU.

thanks a lot. i was half way through, already had installed phctools, just didnt know what to do with it :D

i found mi lowest vid is 21, so i just set it to that. and thats it?

how odd to have the setting when every perceived frequency works on the lowest of settings.

anyway, thanks, gonna testdrive my battery now... hope it does something

---

### Post by shae on 2008-06-21
This guide is great!  I managed to get my C2D 7500T down to 12:31 11:22 8:15 6:15 136:15 though I have not worked much on the 12:31 setting.  (15 is the lowest)  I have not checked battery life but it is running much cooler.

---

### Post by sarah.fauzia on 2008-06-22
> **pressureman said:**
> 2.6.24-19 just got released... :-?

I'd really like to know if the HOW-TO is compatible with the updated kernel--my Motion LE1700 always gets hot, so I constantly have to use a laptop fan (it's Intel Core 2 Duo). So I hope the answer is a yes!

And my computer has a 64-bit processor...

---

### Post by jocko on 2008-06-22
> **sarah.fauzia said:**
> I'd really like to know if the HOW-TO is compatible with the updated kernel--my Motion LE1700 always gets hot, so I constantly have to use a laptop fan (it's Intel Core 2 Duo). So I hope the answer is a yes!

And my computer has a 64-bit processor...

It will work with any kernel if you compile the module yourself ([see instructions in this post]("http://ubuntuforums.org/showpost.php?p=5119140&postcount=54") ). But there is a precompiled module for 2.6.24-19 in the first post (it's only 32 bit, which may or may not work with a 64 bit kernel. I know the module for 32 bit 2.6.24-18 worked fine with my 64 bit kernel...)
The script from this howto does not always work (for me it just works on full processor frequency and fails to keep the processor at any lower frequency, so the script thinks it can go all the way down to zero when in fact the lowest working setting is 19... ).

---

### Post by eldragon on 2008-06-22
> **shae said:**
> This guide is great!  I managed to get my C2D 7500T down to 12:31 11:22 8:15 6:15 136:15 though I have not worked much on the 12:31 setting.  (15 is the lowest)  I have not checked battery life but it is running much cooler.

battery life didnt change one bit. :(

i seriously believe there is something really incompatible with this notebook. thanks god i dont rely that much on the battery..

---

### Post by sarah.fauzia on 2008-06-22
Okay, I was able to run the module, and all the scripts for that matter...I just want to make sure I interpreted what to echo correctly.

This is what I got from running the last step:

```
Default VIDs: 22 21 20 19 
Current VIDs: 0 21 20 19
Testing VID: 0 (700 mV)
..............................
Default VIDs: 22 21 20 19 
Current VIDs: -1 21 20 19
Testing VID: -1 (684 mV)
./linux-phc-optimize.bash: line 161: printf: -1: invalid option
printf: usage: printf [-v var] format [arguments]


The lowest acceptable VID is 0.
```

When I open the phc_controls I get (I mistakenly thought I had to reboot after this step, so after rebooting):

```
cat /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
9:1 8:21 7:20 6:19
```

Unless I'm mistaken, it changed on its own, without me having to "echo" it. But I still added, as the steps said:

```
echo "9:1 8:21 7:20 6:19" > /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
``` to /etc/rc.local

Did I do everything correctly? I just want to make sure--again, I really hope this helps! My computer didn't freeze at all during this risky procedure, thankfully.

---

### Post by sarah.fauzia on 2008-06-22
Ah! I was able to see how the script worked--because I hadn't changed <i>both</i> cores yet:

```

sara@sara-tablet:~$ cat /sys/devices/system/cpu/cpu1/cpufreq/phc_controls
9:22 8:21 7:20 6:19 
sara@sara-tablet:~$ cat /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
9:1 8:21 7:20 6:19 

```

So it worked! (Correct me if I'm mistaken)

---

### Post by jocko on 2008-06-23
> **sarah.fauzia said:**
> Ah! I was able to see how the script worked--because I hadn't changed <i>both</i> cores yet:

```

sara@sara-tablet:~$ cat /sys/devices/system/cpu/cpu1/cpufreq/phc_controls
9:22 8:21 7:20 6:19 
sara@sara-tablet:~$ cat /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
9:1 8:21 7:20 6:19 

```So it worked! (Correct me if I'm mistaken)

I don't think that you allowed the script to finish. It first test the highest cpu frequency until it freezes, then after reboot you have to run the script again to test the next cpu frequency. As you see you still have the original vid's on the 8x, 7x and 6x multipliers.
Also I don't think your processor really ran at full speed during those tests, as the script was able to run all the way to zero. For me the original vid for the highest multiplier was 42 and I managed to lower it to 19 (which causes my computer to freeze, so I set it at 21 to keep it stable). On the lower multipliers the script ran all the way down to zero, but I could clearly see that after the script had set the cpu frequency, my system regained control and re-set the frequency governor back to "ondemand". So the script ran only some kind of simulation.
When I tested what vid's I can use I noticed that even if I set the vid's for the lower multipliers in /sys/devices/system/cpu/cpu*/cpufreq/phc_controls to zero, the actual value never gets lower than 19 (probably a limit in the bios or cpu itself).

Have you tried really stressing your cpu with those settings, making sure it runs att maximum usage at the higest speed on both cores?
If it really runs stable with those settings, I'm pretty sure you can set the vid's for the other multipliers to 1 as well, as it makes no sense to use higher voltage on the 8x, 7x and 6x multipliers than you use on 9x.
Oh, and to get both cores to use the settings, you need to echo the values to both cores.

---

### Post by sarah.fauzia on 2008-06-23
> **jocko said:**
> I don't think that you allowed the script to finish. It first test the highest cpu frequency until it freezes, then after reboot you have to run the script again to test the next cpu frequency. As you see you still have the original vid's on the 8x, 7x and 6x multipliers.
Also I don't think your processor really ran at full speed during those tests, as the script was able to run all the way to zero. For me the original vid for the highest multiplier was 42 and I managed to lower it to 19 (which causes my computer to freeze, so I set it at 21 to keep it stable). On the lower multipliers the script ran all the way down to zero, but I could clearly see that after the script had set the cpu frequency, my system regained control and re-set the frequency governor back to "ondemand". So the script ran only some kind of simulation.
When I tested what vid's I can use I noticed that even if I set the vid's for the lower multipliers in /sys/devices/system/cpu/cpu*/cpufreq/phc_controls to zero, the actual value never gets lower than 19 (probably a limit in the bios or cpu itself).

Have you tried really stressing your cpu with those settings, making sure it runs att maximum usage at the higest speed on both cores?
If it really runs stable with those settings, I'm pretty sure you can set the vid's for the other multipliers to 1 as well, as it makes no sense to use higher voltage on the 8x, 7x and 6x multipliers than you use on 9x.
Oh, and to get both cores to use the settings, you need to echo the values to both cores.

Hmmm. I ran the script three times (restarting after each time), the second and third time making sure to stress the second core as well by running burnMMX simultaneously (and it did say "Terminated" when the first script finished). I can't think of anything I did wrong...could it possibly be that my computer is very good, and can handle the lower voltage? I would truly hope so!

I'll set the other ones down to 1, and see how that goes. And my computer didn't freeze at all while the script was running... It was only after the initial INSTALL of the script that my computer checked my drives, after I had rebooted (that's the step for or after step four, from the guide you linked me to?).

The reason I didn't change the voltages for the other multipliers was because I thought Current VIDs would show me what exact values to use--did everyone else also assume to change all the lower multipliers to the same value? I'm quite new to this, so forgive me! I would just really, really like to have a more *temperate* computer (and perhaps learn more how it works, too).

Thank you for the help!

---

### Post by HellBoyz77 on 2008-06-23
I followed the guide with just some changes for match my machine.

I have a T5500 Core 2 Duo, Hardy x86.

The script linux-phc-optimize.bash did not work for me, it gave the -1 issue. Also running the script with another istance of burnMMX in a separate tab made the temperature up to 104 degree, it's almost the limit that can support. So, be aware on using it. 

Instead i suggest if you have this type of cpu to put the VID at 19, as other users say seems that is impossibile to set a lower level.

You can use PHCTools to set the VID for both the cpu, just pay attention to mark the option "Restore VIDs on Load" under Settings Tab. Before using it launch the script install.sh to set the permissions.

I can confirm that the average temperature has dropped around 10-15 degree.

The compiled module for 2.6.24-19 32bit is below.

Good job Ares Drake.

---

### Post by mailforbiz on 2008-06-23
I have Intel 7250 C2D, x86. I followed the steps in the original post and used the PHC patch for kernel -16. The original values I got on doing a cat of phc_controls were
> 
$ cat  /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
11:45 10:37 8:30 6:23 136:15 


That doesn't seem right, esp the last pair 136:15. From what I understand, the first value should be much lower. 

Can anyone with knowledge of this confirm whether this values sound fishy ?

By the way, I still went through the rest of the steps and the script gives me the -1 issue.

Maybe I need to compile my own patch.

Any response appreciated. 

TIA,
HT

---

### Post by SyntheticShield on 2008-06-23
does this how to work with AMD processors, or does this only work with dual core processors?

---

### Post by mailforbiz on 2008-06-24
I went ahead and put 19 as the voltage values for all the frequencies like some folks here have done. I would say there has been maybe a 3-4 deg drop in the temp but not the 10-15 deg some folks have reported. But this could just be my perception. I haven't tried compiling the patch myself yet. Don't know if this matters but I'm using kernel -16.

> **mailforbiz said:**
> I have Intel 7250 C2D, x86. I followed the steps in the original post and used the PHC patch for kernel -16. The original values I got on doing a cat of phc_controls were


That doesn't seem right, esp the last pair 136:15. From what I understand, the first value should be much lower. 

Can anyone with knowledge of this confirm whether this values sound fishy ?

By the way, I still went through the rest of the steps and the script gives me the -1 issue.

Maybe I need to compile my own patch.

Any response appreciated. 

TIA,
HT

---

### Post by blazercist on 2008-06-24
I'd like to try this but before I do can someone confirm this actually has a positive effect on battery life?  Can someone post some detailed values in reference to "before and after" battery life.   Thanks

---

### Post by aashay on 2008-06-24
Ill gladly run the tests given the right tools. Right now, I can say there has been a marginal increase (10-20 mins). Though the 10-15 degs reduction in temperature makes the whole thing worth it

---

### Post by mailforbiz on 2008-06-24
I don't know how you guys are getting a 10-15 degrees drop. I played around quite a bit to come up with VID values that didn't freeze my laptop. Eventually though, setting the VIDs at those values made my HDD temp go upto 46 deg when earlier it used to hover around 42 deg. Besides it didn't make much difference for my other temps - GPU and cores. So for now I've reverted back to the original values. Maybe I'm doing something wrong.

Has anyone measured the before/after HDD temp using hddtemp ?

I'd love to get the 10-15 deg drop as my laptop gets quite hot and this is one annoying thing which makes me pine for Vista. Oh Gosh, nooooooooooooo!! [Realizes with horror what he just said]

---

### Post by aashay on 2008-06-25
hddtemp shows equal if not lower values after the undervolt.

---

### Post by jocko on 2008-06-25
> **mailforbiz said:**
> Has anyone measured the before/after HDD temp using hddtemp ?
Why do you think undervolting the cpu would change the hdd temperature?
It will only change the cpu temperature, nothing else.

---

### Post by mailforbiz on 2008-06-25
Good question, I have no idea why the HDD temp would rise. I was running burnMMX at times but that is only supposed to exert the cpu so who knows. In short, either the steps depicted in this tutorial don't work for my cpu/system configuration else I'm  being a braindead bugger and doing something wrong. Either way, there are unpleasant side-effects. :-)

> **jocko said:**
> Why do you think undervolting the cpu would change the hdd temperature?
It will only change the cpu temperature, nothing else.

---

### Post by excogitation on 2008-06-26
From my experience undervolting lowers your temperature by a few (~3-8 °C) degrees depending on the the CPU load, ...

I think you're unreasonable expecting figures as high as 15 °C.

Most the time it's only a matter of a few degrees to get those laptop fans to stop and that's what my main interest was when I started using NHC (windows) a few years back.

Unfortunately in Ubuntu my fan still runs about 85% of the time but at least it isn't running 100% and maybe it'll change to the better in the future (... it definitely will with the next laptop ...)

Also undervolting NEVER had any effect on my harddrive temperature (and I've undervolted numerous laptops and even my fileserver running on a Dothan mATX-board).

---

### Post by eldragon on 2008-06-26
doing a dmesg i get the following concerning acpi_cpufreq:
 acpi_cpufreq: no version for "struct_module" found: kernel tainted.

does anyone know what that means?

---

### Post by mrpeaches on 2008-06-26
Ok, let me start off by saying that I'm a total Linux newbie. This is my first Ubuntu install and I'm a big fan for the most part. However, I'm interested in undervolting because my CPU fan is always blowing and my laptop does run hotter under ubuntu as compared to XP (I'm dual booting).

So, I looked at the guide and managed to compile and install the PHC thing. I ran the script as well as burnMMX concurrently, but the script counted all the way down to 0 and then crashed. So, going on the advice of others in this thread, I set the values all to 19 and put them in the rc.local file. Unfortunately, this caused my Ubuntu to hang. It loads at boot, then just when it normally goes to the login screen, it just stops with a black screen and is unresponsive. when i went to the recovery boot, and edited out the "echo" commands, ubuntu boots as normal, which is to say, overly warm with the fan always blowing. 

Here is some extra information in case it helps:
Ubuntu 8.04 64-Bit
Lenovo X61 laptop
Core2Duo T8300 2.4 Ghz
4GB RAM

and here is what I put into my rc.local file (I upped the 19 to 21 to try and boot with it again, no luck):
echo "13:21 12:21 10:21 8:21 6:21 136:21" > /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
echo "13:21 12:21 10:21 8:21 6:21 136:21" > /sys/devices/system/cpu/cpu1/cpufreq/phc_controls

So, anyone have any ideas? I am totally at a loss as to what to do next. Thank you all for being so kind and helpful so far, and any help anyone could give me would be appreciated!

---

### Post by aashay on 2008-06-26
> **mrpeaches said:**
> Ok, let me start off by saying that I'm a total Linux newbie. This is my first Ubuntu install and I'm a big fan for the most part. However, I'm interested in undervolting because my CPU fan is always blowing and my laptop does run hotter under ubuntu as compared to XP (I'm dual booting).

So, I looked at the guide and managed to compile and install the PHC thing. I ran the script as well as burnMMX concurrently, but the script counted all the way down to 0 and then crashed. So, going on the advice of others in this thread, I set the values all to 19 and put them in the rc.local file. Unfortunately, this caused my Ubuntu to hang. It loads at boot, then just when it normally goes to the login screen, it just stops with a black screen and is unresponsive. when i went to the recovery boot, and edited out the "echo" commands, ubuntu boots as normal, which is to say, overly warm with the fan always blowing. 

Here is some extra information in case it helps:
Ubuntu 8.04 64-Bit
Lenovo X61 laptop
Core2Duo T8300 2.4 Ghz
4GB RAM

and here is what I put into my rc.local file (I upped the 19 to 21 to try and boot with it again, no luck):
echo "13:21 12:21 10:21 8:21 6:21 136:21" > /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
echo "13:21 12:21 10:21 8:21 6:21 136:21" > /sys/devices/system/cpu/cpu1/cpufreq/phc_controls

So, anyone have any ideas? I am totally at a loss as to what to do next. Thank you all for being so kind and helpful so far, and any help anyone could give me would be appreciated!
Please refer to [http://ubuntuforums.org/showpost.php?p=5231160&postcount=91]("http://ubuntuforums.org/showpost.php?p=5231160&postcount=91") to see how I got the 19 value for *MY* system. Find the correct value for your system in a similar way.

---

### Post by HellBoyz77 on 2008-06-27
> **excogitation said:**
> From my experience undervolting lowers your temperature by a few (~3-8 °C) degrees depending on the the CPU load, ...

I think you're unreasonable expecting figures as high as 15 °C.

I think that it depends on cpu. For example, with my T5500 i get impressive result. Before the undervolting, when playing Civ4 with Wine, my cpu go always 97-99 degree. Now i get an impressive 75-85 ... This is very reasonable result.

> **excogitation said:**
> Most the time it's only a matter of a few degrees to get those laptop fans to stop and that's what my main interest was when I started using NHC (windows) a few years back.

Unfortunately in Ubuntu my fan still runs about 85% of the time but at least it isn't running 100% and maybe it'll change to the better in the future (... it definitely will with the next laptop ...)

If you want to manage the fan noise, you probably need to recompile your DSDT table, when i do it the fan lower the noise a lot. I don't remember the link, but i found a guide in this forum on how to do that.

---

### Post by tesna on 2008-07-02
Do anyone know how to patch cpufreq in 26.25.9 kernel? Currently in svn only got patch for 26.24

---

### Post by Tao on 2008-07-03
yes (I've test it on 2.6.25.8 vanilla), with the Teknohog PHC patch. [http://howflow.com/tricks/undervolt_your_cpu_with_linux_phc_and_kernel_2_6_25]("http://howflow.com/tricks/undervolt_your_cpu_with_linux_phc_and_kernel_2_6_25")

But I didn't succeed on the intrepid kernel... (2.6.26rc6 with ubuntu patches)

---

### Post by chuck232 on 2008-07-03
Core 2 Duos should have a min voltage of 15. The minimum for Core 2's is 0.9V, so 712mV + 15*12.5mV. This is a documented lowest voltage.

As for the 136: xx number people are seeing, this is a setting available for many of the 800MHz FSB Core 2 Duo's. Typically the lowest multiplier is 6, and for a 800MHz quad-pumped FSB CPU, that equates to 6*200MHz = 1.2GHz. However these 800MHz Core 2 Duos can also drop the FSB. At its lowest operating power state, it downclocks to 8 multiplier * 100MHz FSB (400MHz quad-pumped), or 800MHz. That's why it's listed as the last entry. The 136 number is just the represenation of that power state. I'd go out on a limb and say that every 800MHz FSB Core 2 Duo should be able to do that state at 136:15 (or 0.9V i.e. the lowest operating voltage).

---

### Post by tesna on 2008-07-03
> **Tao said:**
> yes (I've test it on 2.6.25.8 vanilla), with the Teknohog PHC patch. [http://howflow.com/tricks/undervolt_your_cpu_with_linux_phc_and_kernel_2_6_25]("http://howflow.com/tricks/undervolt_your_cpu_with_linux_phc_and_kernel_2_6_25")

But I didn't succeed on the intrepid kernel... (2.6.26rc6 with ubuntu patches)

that works great on 2.6.25.9, Thanks!

---

### Post by M4rotku on 2008-07-04
Ok guys,

I've tried to do this several times now and I think I officially qualify as the least competent person ever to view this thread because it seems that everyone else is able to do this.

Would anyone be willing to work with me through private messages or AOL IM or Skype to give me step by step instructions.

It keeps going wrong and I think I know why, but I have no clue what to do about it and I am just really confused at this point.  I would've given up by now but my computer really needs to be undervolted.

Much thanks in advance,
M4rotku

---

### Post by excogitation on 2008-07-04
> **M4rotku said:**
> Ok guys,

... give me step by step instructions.



Derived from the first post:
> Step by step:

**1.** This howto depends on the kernel module acpi-cpufreq to control your cpu. To find out if you're using it try
```
lsmod | grep acpi_cpufreq
```
You should see sth. like this:
```
acpi_cpufreq           14892  2 
freq_table              5536  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
processor              36872  4 acpi_cpufreq,thermal
```
**In case you don't see anything**, you don't use acpi-cpufreq, but maybe the speedstep.centrino module.
**Then this howto is not for you** ...

**2. **You need to get a modified version of your acpi_cpufreq module, one with [PHC support]("http://phc.athousandnights.de/") build in. [PHC]("http://phc.athousandnights.de/") means processor hardware control and is the magic that makes it going. There are several ways to get this module.

... the precompiled modules I offer below are **32bit only**.
 It has to match your kernel. **If there isn't the right one compile it yourself or wait for someone to provide it to the community.**

**3. **There are right now versions for kernel 2.6.24-1**6**-generic, 2.6.24-1**7**-generic, 2.6.24-1**8**-generic and 2.6.24-1**9**-generic. To find out what kernel you have open a terminal and type:
```
uname -r
```
So once you know, download the right kernel module for [2.6.24-1**6**-generic]("www.s3pp.de/misc/16/acpi-cpufreq.ko") or [2.6.24-1**7**-generic]("www.s3pp.de/misc/17/acpi-cpufreq.ko") or [2.6.24-1**8**-generic]("www.s3pp.de/misc/18/acpi-cpufreq.ko")  or [2.6.24-1**9**-generic]("www.s3pp.de/misc/19/acpi-cpufreq.ko").
**4. **First backup your old module.
```
sudo cp /lib/modules/`uname -r`/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko /lib/modules/`uname -r`/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko.old
```
(basically copies it to a new name)

 

**5. ** Then copy the downloaded file to the right place:
```
sudo cp acpi-cpufreq.ko /lib/modules/$(uname -r)/kernel/arch/x86/kernel/cpu/cpufreq
``` [/INDENT]

**5.** Reboot. If the module is installed correctly,
```
cat /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
```
should give you sth like this:
```
12:38 10:30 8:24 6:18
```
The value before the : stands for the frequency, the later for the voltage.
[B]


I'd get the PHC tool to start tweaking after that.

---

### Post by M4rotku on 2008-07-04
At the line:

> cat /sys/devices/system/cpu/cpu0/cpufreq/phc_controls

Is where I have the problem.  Instead of four outputs, I only get two:

> joey@joey-laptop:~$ cat /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
9:43 6:19 


I think that this is where the problem is coming from and I have no idea how to go about fixing it.  I have not heard of anyone else having this problem and so I'm starting to wonder what's going wrong.

Can anyone tell me why I'm only getting 2 outputs and how I would go about adjusting the process because of this?

Much thanks,
M4rotku

---

### Post by jocko on 2008-07-05
> **M4rotku said:**
> At the line:



Is where I have the problem.  Instead of four outputs, I only get two:



I think that this is where the problem is coming from and I have no idea how to go about fixing it.  I have not heard of anyone else having this problem and so I'm starting to wonder what's going wrong.

Can anyone tell me why I'm only getting 2 outputs and how I would go about adjusting the process because of this?

Much thanks,
M4rotku

I don't think you need to adjust anything because of this.
How many "outputs" you get is built in to your cpu, there's no way you can change that. If the cpu can only be set to two different frequencies, you only get two outputs...

Exactly what is your problem? At which step does the howto fail, and what is the command line output from that step?

---

### Post by M4rotku on 2008-07-05
Ok jocko,

I got to the point at which I got confused.  In the step in which the script is run, I get confused about how to do it with dual core.

Do I enter "burnMMX" in the same terminal in which I am running the script, or in a different terminal?

Much thanks,
M4rotku

---

### Post by jocko on 2008-07-06
> **M4rotku said:**
> Ok jocko,

I got to the point at which I got confused.  In the step in which the script is run, I get confused about how to do it with dual core.

Do I enter "burnMMX" in the same terminal in which I am running the script, or in a different terminal?

Much thanks,
M4rotku

Either you run:
```
burnMMX &
``` before you start the script in the same terminal, or you run it in a different terminal after you have started the script. Doesn't really matter, as long as you have two burnMMX processes running (one started manually and one started by the script), both cores will be used.

But a little warning on using/trusting the script:
On some cpus it doesn't apply the settings to both cores (it doesn't on mine) and it also doesn't manage to keep control of the cpu frequency governor (mine gets reset to "ondemand" directly after the script claims it has succesfully set a lower frequency), so the script only tests the highest frequency and when it thinks it tests lower frequencies, the cpu still runs full speed...

---

### Post by M4rotku on 2008-07-06
Ok, I think I ran the script correctly and this was the eventual output:

> Default VIDs: 43 19 
Current VIDs: 0 19
Testing VID: 0 (700 mV)
..............................
Default VIDs: 43 19 
Current VIDs: -1 19
Testing VID: -1 (684 mV)
./linux-phc-optimize.bash: line 161: printf: -1: invalid option
printf: usage: printf [-v var] format [arguments]


The lowest acceptable VID is 0.

Recovering CPU.

Run this script again to continue the optimization.
./linux-phc-optimize.bash: line 138:  8816 Terminated              burnMMX
[1]+  Terminated              burnMMX  (wd: ~)
(wd now: ~/Desktop)


Then, when I tried to run the script again, I got this result:

> joey@joey-laptop:~/Desktop$ sudo /.linux-phc-optimize.bash
sudo: /.linux-phc-optimize.bash: command not found


Then, I ls'ed to see if it was there and it was:

> joey@joey-laptop:~/Desktop$ ls
acpi-cpufreq.ko  functions.bash  linux-phc-optimize.bash  phc_cur_pos  phc_tweaked_vids



What am I doing wrong?  It didn't crash and I couldn't run the script again as it told me to.

---

### Post by jocko on 2008-07-06
> joey@joey-laptop:~/Desktop$ sudo **[COLOR=Red]/.[/COLOR]**linux-phc-optimize.bash

 sudo: [COLOR=Red]**/.**[/COLOR]linux-phc-optimize.bash: command not foundit should be:
```
sudo [COLOR=Red]./[/COLOR]linux-phc-optimize.bash
```Note that the point is before the slash, not after (which means "run the file **"linux-phc-optimize.bash"** which is **in the current (./) directory**", the way you wrote it it means "run the file "**[COLOR=Red].[/COLOR]linux-phc-optimize.bash"** which is (hidden) **in the root (/) directory**", and as that file does not exist you get a command not found error).

---

### Post by M4rotku on 2008-07-06
I swear this script hates me.  How does it know that it's me when I run it.  Ok, here's the problem this time.

When I tried to run the script for the second time, I recieved the following error starting from where it would install cpuburn:

> Install required packages.
Will use burnMMX (part of cpuburn package) to stress CPU.
Install: cpuburn
> SKIPPED: Already installed


Will use current directory to store/retrieve test results.

Read phc_default_vids:
> Success!

Load VIDs from 'phc_tweaked_vids'
> ERROR: Wrong VID count!
joey@joey-laptop:~/Desktop/Undervolt$ 


and then the script quits and I end up back where i started in my Undervolt folder. :confused: grr.

I think this is where I finally gave up the last time.  I want to keep going though, so if anyone can tell me what to do, then I'll do it.

Much thanks,
M4rotku

---

### Post by aldeby on 2008-07-06
try deleting these files in your home directory (or in /root one if you are running the script from recovery console) 
```

phc_cur_pos
phc_tweaked_vids

```

then run the script again.

as for burnMMX simply run 
```

burnMMX &

```
in the terminal before running the script, 
this way you are going to stress both cores of your dual core CPU.

cheers!

---

### Post by M4rotku on 2008-07-06
Don't I need those scripts to run it the second time so that the main script will know where it left off the last time?

---

### Post by aldeby on 2008-07-07
Of course, but something went wrong last time.
I'm not suggesting you to always delete them, just once to try fixing the problem you are experiencing.

---

### Post by M4rotku on 2008-07-07
I tried deleting those files and running it again.  Once again, it ran the first time and then the second time I received the same error.

---

### Post by aldeby on 2008-07-07
As far as I remember in phc_tweaked_vids VIDs on the right cannot be higher than those on the left: i.e. 40 34 23 15 is OK while 0 34 23 15 will probably prompt the reported error. Values in phc_tweaked_vids are related to the number listed in phc_cur_pos 

phc_cur_pos should list number 0 or 1 since you only have two power states.
It should be 0 if your CPU crashed while running the script the first time.

you can use the vids listed in phc_tweaked_vids after the CPU crashes by adding a few extra values to ensure stability.

if the scripts goes down to 0 most of the times there are some problems.
in my case, for example, it manages to go down to 0 for the first FID, however the second lower one crashes at 35. I cannot set phc 0 35 -- -- because this will prompt an error. First value should definitely be equal of higher.

Hope to remember well...

---

### Post by M4rotku on 2008-07-07
My value on the left went down to 0 and then the script quit after it got to a negative one.  But the value on the right stayed at 19 the whole time.  I assumed that it was supposed to do that.

But the script didn't crash the system yet, so it still needs to run a few more times.

How would I go about fixing this?

---

### Post by Tao on 2008-07-08
There is a new version of PHC (0.3.1) (two days ago). [http://sourceforge.net/project/showfiles.php?group_id=161063]("http://sourceforge.net/project/showfiles.php?group_id=161063")

Some changes, longer documentation and a patch for 2.6.26rc8 kernel. :)

---

### Post by M4rotku on 2008-07-09
Tao,

that looks promising.  However, I have no idea as to which thing I need off of that site.  If I am using 2.6.24-19-generic as my kernel and an Intel Core2 Duo CPU, then which package would I want to download and use?  Also, would I still be following this guide or would I have to use a new set of instructions?

Much thanks,
M4rotku

---

### Post by Sebastral on 2008-07-10
> **M4rotku said:**
> Tao,

that looks promising.  However, I have no idea as to which thing I need off of that site.  If I am using 2.6.24-19-generic as my kernel and an Intel Core2 Duo CPU, then which package would I want to download and use?  Also, would I still be following this guide or would I have to use a new set of instructions?

Much thanks,
M4rotku


- find out if you use acpi_cpufreq with **lsmod | grep cpufreq**

- if you do follow these instructions to enable phc;

[http://ubuntuforums.org/showpost.php?p=5119140&postcount=54](http://ubuntuforums.org/showpost.php?p=5119140&postcount=54)

- install phctool from the link that looked promising to you.

- do **sudo modprobe msr** to enable the analasys feature

- find out the lowest possible vid for your cpu with the relevant steps in this howto

- set the new vids using the relevant steps in this howto

Hope this helps. Ever since I couldn't get the vids lower then the lowest official vid I gave up on this. but I've upgraded to kernel 2.6.24 and gave it a shot again. if I can believe phctool and powertop it seriously appears lower vids than the lowest standard vid is possible (using 2.6.24-19 and phc 0.3.1) :cool:

---

### Post by M4rotku on 2008-07-11
> **Sebastral said:**
> 
- if you do follow these instructions to enable phc;

[http://ubuntuforums.org/showpost.php?p=5119140&postcount=54](http://ubuntuforums.org/showpost.php?p=5119140&postcount=54)

- install phctool from the link that looked promising to you.

Those instructions were for the 18 kernel, will they work with the 19?

---

### Post by Sebastral on 2008-07-12
> **M4rotku said:**
> Those instructions were for the 18 kernel, will they work with the 19?
Positive, I have done it myself.

---

### Post by M4rotku on 2008-07-12
Tao,

How do I install that patch, it wasn't a .deb package and I don't have any idea how to use it?  When I tried to use the install script, it tried to go through wine so it might be a windows app.

---

### Post by aroedl on 2008-07-14
> **Tao said:**
> yes (I've test it on 2.6.25.8 vanilla), with the Teknohog PHC patch. [http://howflow.com/tricks/undervolt_your_cpu_with_linux_phc_and_kernel_2_6_25]("http://howflow.com/tricks/undervolt_your_cpu_with_linux_phc_and_kernel_2_6_25")

But I didn't succeed on the intrepid kernel... (2.6.26rc6 with ubuntu patches)

Today I created a PHC patch for the brand new stable kernel 2.6.26:

[Undervolt your CPU with Linux PHC and kernel 2.6.26]("http://howflow.com/tricks/undervolt_your_cpu_with_linux_phc_and_kernel_2_6_26")

Andreas

---

### Post by aashay on 2008-07-14
> **M4rotku said:**
> My value on the left went down to 0 and then the script quit after it got to a negative one.  But the value on the right stayed at 19 the whole time.  I assumed that it was supposed to do that.

But the script didn't crash the system yet, so it still needs to run a few more times.

How would I go about fixing this?

Just set 19 as the VID for everything. The script will never crash as the processor is limiting the value to 19 whenever you put 18, 17..., 0. See my post a few pages back

---

### Post by M4rotku on 2008-07-14
> **aashay said:**
> Just set 19 as the VID for everything. The script will never crash as the processor is limiting the value to 19 whenever you put 18, 17..., 0. See my post a few pages back

How would I go about doing so without the script doing it for me since the script keeps going lower?  can you give me a terminal command to set the VID as such?

---

### Post by jocko on 2008-07-14
> **M4rotku said:**
> How would I go about doing so without the script doing it for me since the script keeps going lower?  can you give me a terminal command to set the VID as such?

The only thing the script does (when it works) is that it tells you which vid's you can use safely. Even if the script misbehaves, you can still follow the rest of the instructions in the howto, but you'll have to test your vid's manually.

If your default vid's are as from your post a few pages back:
> **M4rotku said:**
> cat /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
9:[COLOR=Blue]43[/COLOR] 6:[COLOR=Blue]19[/COLOR]
Then, to set all vid's temporarily to [COLOR=Blue]19[/COLOR], you can use these commands:
```
sudo bash
echo "9:[COLOR=Blue]19[/COLOR] 6:[COLOR=Blue]19[/COLOR]" > /sys/devices/system/cpu/cpu[COLOR=Red]0[/COLOR]/cpufreq/phc_controls
echo "9:[COLOR=Blue]19[/COLOR] 6:[COLOR=Blue]19[/COLOR]" > /sys/devices/system/cpu/cpu[COLOR=Red]1[/COLOR]/cpufreq/phc_controls
exit
```(the second "echo" command is only if you have a dual core cpu...)
And to really stress the cpu run "burnMMX" in a terminal (or in two terminals to stress both cores of a dual core cpu). Let it run for a while, and if it doesn't freeze the computer within a minute or so, it's *probably* going to be stable.

If it seems stable, make it automatically load on boot:
```
gksudo gedit /etc/rc.local
```And add these lines:
```
echo "9:[COLOR=Blue]19[/COLOR] 6:[COLOR=Blue]19[/COLOR]" > /sys/devices/system/cpu/cpu[COLOR=Red]0[/COLOR]/cpufreq/phc_controls
echo "9:[COLOR=Blue]19[/COLOR] 6:[COLOR=Blue]19[/COLOR]" > /sys/devices/system/cpu/cpu[COLOR=Red]1[/COLOR]/cpufreq/phc_controls
```(again, the second line is only if you have a dual core cpu...)

---

### Post by M4rotku on 2008-07-14
It didn't freeze the computer when set to 19, but when I tried to run a virtual machine which would've consumed 512 MB of ram, it virtual machine (VirtualBox) aborted.  Would this be caused by the low VID or is this a separate problem?

---

### Post by aashay on 2008-07-16
I would blame it on something else. This would be an all or nothing. Either everything freezes or it all works fine.

---

### Post by patrickfromspain on 2008-07-16
Thank you!!!

For me, the originals VID's were 10:43 8:31 6:19 and running the script wouldn't crash the system; I set the VIDs all to 1, and then found, using PHCtool, that it wouldn't run any lower than 19 (probably already discussed, didn't read the whole thread).

So now I've set all VIDs to 19 and the system seems perfectly stable and so on, hasn't crashed. A very good thing is that I believe that now the system consumes the same power running with the cpu in performance mode or powersave, is that true?

Sad thing: the battery life won't increase, since the VID was already the lowest possible when running at 1GHz (lowest speed for my proc).

---

### Post by patrickfromspain on 2008-07-17
One more question: whenever I suspend or hibernate, when coming back, phctool won't work. If run in terminal, the message it outputs is this one:
```

Traceback (most recent call last):
  File "./phctool.py", line 467, in <module>
    app=appgui()
  File "./phctool.py", line 103, in __init__
    self.ShowThrottlingControl()		##display trottling Controls
  File "./phctool.py", line 258, in ShowThrottlingControl
    getattr(self, 'label_TState'+str(cpu)).set_text(self.throttling.data[cpu]['states']['T'+str(tid)]+"%")
KeyError: 'T8'

```

any ideas? anyone getting the same problem?

---

### Post by aashay on 2008-07-18
I'm not getting any problems running phctool after hibernate

---

### Post by M4rotku on 2008-07-18
I was wondering if this may've messed up some of my start-up things.  The startup music bit plays before I log in, but the music that normally plays after I log in doesn't play anymore.  Also, it takes a minute or so longer than usual to log in.  These alone aren't really that big of problems.  However, my Firefox is also messed up.  When I try to start Firefox, it fails the first few times and then finally seems stable.  Then, when I try to play a game, it fails as soon as the java starts loading.

This has only happened since I made the changes to the "/etc/rc.local" script and i was wondering if I added the lines incorrectly somehow:

> #!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
echo "9:19 6:19" > /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
echo "9:19 6:19" > /sys/devices/system/cpu/cpu1/cpufreq/phc_controls

exit 0

Does anything look wrong?

---

### Post by KillaW0lf04 on 2008-07-18
hey, im running this script at the moment and its been going on for quite a few times now......started at 46 and now its at 26 :| am i doing something wrong? It hasnt crashed once

---

### Post by KillaW0lf04 on 2008-07-18
ok, so i tried this thing out but it never seemed to want to end. Startet at 46 and was going all the way down to 0 from what i can tell. Also i only realised that i had to run BurnMMX till about half way through so i cancelled. What im scared of is that when im running both cores (ie 100% CPU usage, the temperature scales up ALOT), i was scared of it overheating (it was at 98 degrees) so i cancelled. Any advice? Im using an MSI GX600, the one with the turbo button on it........should i not run this becuase of the turbo button configuration?

---

### Post by KillaW0lf04 on 2008-07-18
sorry to post yet again, but now when i try running the script the computer just freezes and either restarts or forces me to restart it.........is this the crashing i was supposed to expect?

This is what i got from what the tutorial asked for in the beginning
12:47 11:43 8:28 6:18 134:18

---

### Post by KillaW0lf04 on 2008-07-20
bump

---

### Post by Ares Drake on 2008-07-21
[QUOTE=KillaW0lf04;5412549]sorry to post yet again, but now when i try running the script the computer just freezes and either restarts or forces me to restart it.........is this the crashing i was supposed to expect?
/QUOTE]

Indeed. Just run the script again and again until it says finished. Afterwards you will find a text file with the new values in the same directory as you placed the scipt. Substitute the old values after the colon with the new ones. In case the new ones go down to zero, you might use 19 inestead of zero.

---

### Post by KillaW0lf04 on 2008-07-21
ok i decided to start ollfrom the beginning again since i dont think i did it proporly at first and once again it doesnt want to crash for me, it just keeps giving me this output (im typing this while running the script):

EDIT: now it says the script has failed due to a segmentation fault

```
Default VIDs: 47 43 28 18 18 
Current VIDs: 48 42 28 18 18
Testing VID: 42 (1372 mV)
..............................
Default VIDs: 47 43 28 18 18 
Current VIDs: 48 41 28 18 18
Testing VID: 41 (1356 mV)
..............................
Default VIDs: 47 43 28 18 18 
Current VIDs: 48 40 28 18 18
Testing VID: 40 (1340 mV)
..............................
Default VIDs: 47 43 28 18 18 
Current VIDs: 48 39 28 18 18
Testing VID: 39 (1324 mV)
..............................
Default VIDs: 47 43 28 18 18 
Current VIDs: 48 38 28 18 18
Testing VID: 38 (1308 mV)
..............................
Default VIDs: 47 43 28 18 18 
Current VIDs: 48 37 28 18 18
Testing VID: 37 (1292 mV)
..............................
Default VIDs: 47 43 28 18 18 
Current VIDs: 48 36 28 18 18
Testing VID: 36 (1276 mV)
..............................
Default VIDs: 47 43 28 18 18 
Current VIDs: 48 35 28 18 18
Testing VID: 35 (1260 mV)
..............................
Default VIDs: 47 43 28 18 18 
Current VIDs: 48 34 28 18 18
Testing VID: 34 (1244 mV)
..............................
Default VIDs: 47 43 28 18 18 
Current VIDs: 48 33 28 18 18
Testing VID: 33 (1228 mV)
..............................
Default VIDs: 47 43 28 18 18 
Current VIDs: 48 32 28 18 18
Testing VID: 32 (1212 mV)
..............................
Default VIDs: 47 43 28 18 18 
Current VIDs: 48 31 28 18 18
Testing VID: 31 (1196 mV)
..............................
Default VIDs: 47 43 28 18 18 
Current VIDs: 48 30 28 18 18
Testing VID: 30 (1180 mV)
..............................
Default VIDs: 47 43 28 18 18 
Current VIDs: 48 29 28 18 18
Testing VID: 29 (1164 mV)
..............................
Default VIDs: 47 43 28 18 18 
Current VIDs: 48 28 28 18 18
Testing VID: 28 (1148 mV)
..............................
Default VIDs: 47 43 28 18 18 
Current VIDs: 48 27 28 18 18
Testing VID: 27 (1132 mV)
./linux-phc-optimize.bash: line 138: 15815 Segmentation fault      burnMMX

burnMMX crashed!

Recovering CPU.

Run this script again to continue the optimization.

```

PS: Is the text file your talking about called phc_tweaked_vids? because after running the script 6 times after (and only having the system crash twice:/), i got the following: 48 29 15 1 1

---

### Post by KillaW0lf04 on 2008-07-22
bump

---

### Post by Ares Drake on 2008-07-22
> **Ares Drake said:**
> Afterwards you will find a text file with the new values in the same directory as you placed the scipt. Substitute the old values after the colon with the new ones. In case the new ones go down to zero, you might use 19 inestead of zero.

> **KillaW0lf04 said:**
> Is the text file your talking about called phc_tweaked_vids? because after running the script 6 times after (and only having the system crash twice:/), i got the following: 48 29 15 1 1

Yeah that is the file. Go for it. In case it doesn't work try replacing the values below 19 to 19 as other people suggested.

---

### Post by KillaW0lf04 on 2008-07-23
> **Ares Drake said:**
> Yeah that is the file. Go for it. In case it doesn't work try replacing the values below 19 to 19 as other people suggested.

ok, and in case it doesnt run proporly, how can i reset it back to normal?

---

### Post by Rizado on 2008-07-23
> **aashay said:**
> I would blame it on something else. This would be an all or nothing. Either everything freezes or it all works fine.Not correct, the cpu starts making misscalculations that can crash apps before the computer crash. It also heavely depends on the temperature. Cold air mean more stable computer.

Just do a torture test with prime95 to see if it can cope with the voltages.

---

### Post by quirks on 2008-07-26
First of all: thank you soooooooooooooooooooooo much for this incredible post! This reduced my CPU fan speed by two levels and decreased my CPU temperature by 12°C under max load!!! I don't know what the impact is on my laptop battery, since I haven't checked that yet, but probably the effect is almost as impressive.

What makes me wonder a little though is the fact, that at all frequencies, the script went down to -1 and then aborted (without crashing the machine). But my system has run stable so far.

(Why is there no "Thank" button in Ares Drake's post? I want to thank him a thousand times! EDIT: never mind, I thanked him for another post in this thread instead.)

---

### Post by Supersaiyan.IV on 2008-07-26
I've made a 2.6.24-20-generic 32bit precompiled module. Works wonderful on my Pentium M 1.6Ghz.

---

### Post by pressureman on 2008-07-26
Here are some modules for recent kernels in Intrepid Ibex (32 bit).

---

### Post by RadiusXE on 2008-08-01
where can I download phctool? I' m looking for it about one hour and no results

---

### Post by vandorjw on 2008-08-01
>  cat /sys/devices/system/cpu/cpu0/cpufreq/phc_controls

this give me..
12:**46** 11:**43** 8:**31** 6:**23** 136:**15 **
Which are my default values.



>  echo "12:44 11:41 8:15 6:15" > /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
gives me....

[B][I]bash: /sys/devices/system/cpu/cpu0/cpufreq/phc_controls: Permission denied
[/I][/B]
**I need to run as root?**
Last time I did that, my screen turned black, and my Inspiron 1520 wouldn't start up until I loaded the default values in BIOS.

Notice that my default Values give me 5 pairs.

I have the  Intel Core 2 Duo T7300.
Avail Frequencies :
800MHz
1.2 Ghz
1.6 Ghz
2.2 Ghz

---

### Post by RadiusXE on 2008-08-02
> **RadiusXE said:**
> where can I download phctool? I' m looking for it about one hour and no results

wow I found it somewhere, but I got this err, when I try to load the phctool.sh

sudo ./phctool.sh
generic function library missing or corrupted


whats wrong?

---

### Post by pressureman on 2008-08-02
> **RadiusXE said:**
> where can I download phctool? I' m looking for it about one hour and no results

svn checkout [http://phctool.googlecode.com/svn/trunk/](http://phctool.googlecode.com/svn/trunk/) phctool

---

### Post by pressureman on 2008-08-02
The best thing to do is run the phc-optimize tool as desribed earlier in this thread. It will find the lowest voltages possible for your system. Be prepared for some crashes/lockups while running the optimize tool however.

I added a line to my /etc/rc.local, so that the voltages get set at bootup. eg.

```

echo "16:22 14:17 12:12 10:8 8:3 6:1" > /sys/devices/system/cpu/cpu0/cpufreq/phc_controls

```

---

### Post by RadiusXE on 2008-08-02
> **pressureman said:**
> The best thing to do is run the phc-optimize tool as desribed earlier in this thread. It will find the lowest voltages possible for your system. Be prepared for some crashes/lockups while running the optimize tool however.

I added a line to my /etc/rc.local, so that the voltages get set at bootup. eg.

```

echo "16:22 14:17 12:12 10:8 8:3 6:1" > /sys/devices/system/cpu/cpu0/cpufreq/phc_controls

```

phc-optimize don' t work for me

---

### Post by jocko on 2008-08-02
> **cc7gir said:**
> this give me..
12:**46** 11:**43** 8:**31** 6:**23** 136:**15 **
Which are my default values.




gives me....

[B][I]bash: /sys/devices/system/cpu/cpu0/cpufreq/phc_controls: Permission denied
[/I][/B]
**I need to run as root?**
Last time I did that, my screen turned black, and my Inspiron 1520 wouldn't start up until I loaded the default values in BIOS.

Notice that my default Values give me 5 pairs.

I have the  Intel Core 2 Duo T7300.
Avail Frequencies :
800MHz
1.2 Ghz
1.6 Ghz
2.2 Ghz

Yes, that needs to be run as root. But why do you try to use only four pairs, when the default for your cpu is five? That can't be good.
And another thing: The echo command is not meant to be run manually; you are supposed to put it (with appropriate values for YOUR cpu) in the file /etc/rc.local as stated in step 5 of the HowTo. That will load the settings on every boot.
You can of course do it manually for testing (e.g. if the script does not work), in that case the settings will be lost on reboot, which means if you set bad values you won't completely kill your ubuntu install...

---

### Post by tony.research on 2008-08-08
Anyone knows how to configure a pc that uses speedstep-centrino instead of acpi-cpufreq?
i have just tried to make not to load the module speedstep- centrino and instead i loaded at the boot the module acpi-cpufreq, if i go to  /sys/.../phc-controls the file is there but if i try cat of the file it's says that file doesn't exist.
Anyone can help? even a link...
thanx

---

### Post by pressureman on 2008-08-09
speedstep-centrino has been deprecated since about 2.6.18, and will be completely removed in future.

Is the (unpatched) acpi-cpufreq module even loading? If not, you may need to look at BIOS upgrades for your system. Once you can get the vanilla acpi-cpufreq to load, then you try the phc patch.

---

### Post by pressureman on 2008-08-09
> **RadiusXE said:**
> I got this err, when I try to load the phctool.sh

sudo ./phctool.sh
generic function library missing or corrupted

It sounds like you're missing functions.bash, a bash "library" used by the linux-phc-optimize script.

As stated in the first post of this thread, you need [http://www.s3pp.de/misc/functions.bash](http://www.s3pp.de/misc/functions.bash) as well as [http://www.s3pp.de/misc/linux-phc-optimize.bash](http://www.s3pp.de/misc/linux-phc-optimize.bash)

---

### Post by TheJackal12 on 2008-08-09
Thank you Ares Drake for this guide. I've used Ubuntu since 5.10 and have always wanted to undervolt my Pentium M in Ubuntu like I could do in XP. I've even switched back to Windows just for the undervolting. This guide worked great on my Thinkpad. Thank you so much. :)

---

### Post by Mine's Ultimate R on 2008-08-11
does anybody know if it works for amd processors yet? i really wanna try this but don't wanna waste my time if it doesn't work

thanks! :)

edit: actually i don't mean yet, i meant has anyone got it to work on machines with amd?

---

### Post by Ares Drake on 2008-08-12
> **Mine's Ultimate R said:**
> does anybody know if it works for amd processors yet? i really wanna try this but don't wanna waste my time if it doesn't work

thanks! :)

edit: actually i don't mean yet, i meant has anyone got it to work on machines with amd?

I recieved some comments suggesting it doesn't work with AMD. However I am not sure. Your best bet is probably to check the website of the PHC Project. The link is in the HowTo.

---

### Post by pressureman on 2008-08-27
Module for latest Intrepid kernel, 2.6.27-1-generic

---

### Post by Crafty Kisses on 2008-08-28
Thanks for this! :)

---

### Post by Nathan_M on 2008-08-28
```
~$ uname -r
2.6.24-12-generic
```

I have all the sources set, and all the latest updates... so why does everyone else have newer kernel versions than me.

Anyway, I tried it with the 24-16 module. If I run the script, the first time, it counted all the way down to VID 0, then asked me to run the script again. When I do, I get this output, after the normal stuff:

```
Will use current directory to store/retrieve test results.

Read phc_default_vids:
> Success!

Load VIDs from 'phc_tweaked_vids'
> ERROR: Wrong VID count!
```

My phc_cur_pos file just contains a 0, and phc_tweaked_vids is empty! Any explanation?

Edit: I just deleted the files, and this is what I get the first time I ran it:

```
Default VIDs: 40 35 30 25 
Current VIDs: 0 35 30 25
Testing VID: 0 (700 mV)
..............................
Default VIDs: 40 35 30 25 
Current VIDs: -1 35 30 25
Testing VID: -1 (684 mV)
./linux-phc-optimize.bash: line 161: printf: -1: invalid option
printf: usage: printf [-v var] format [arguments]


The lowest acceptable VID is 0.

Recovering CPU.
./linux-phc-optimize.bash: line 138: 12435 Terminated              burnMMX

Run this script again to continue the optimization.
```

---

### Post by pressureman on 2008-08-28
> **Nathan_M said:**
> ```
~$ uname -r
2.6.24-12-generic
```

I have all the sources set, and all the latest updates... so why does everyone else have newer kernel versions than me.

Try running 'sudo apt-get dist-upgrade' from a terminal, in case the later kernels are being held back for some reason. If you still don't get anything later than 2.6.24-12 (which is really ancient - in fact, I seem to remember that was way back when Hardy was still in testing), please paste your /etc/apt/sources.list.

If you're running Hardy, the latest kernel is 2.6.24-19. The module I posted just above is for Intrepid, hence why it's 2.6.27.

---

### Post by InfinityCircuit on 2008-08-28
If you get an error when building the module that says "/lib/modules/2.6.24-19-generic/modules.dep not found", you will be unable to insert the module.

To fix this, a better way to build an individual module is:

```
$ sudo apt-get install linux-headers-$(uname -r)
$ apt-get source linux-image-$(uname -r)
$ cd linux*
$ patch -p1 -i /path/to/phc-linux-patch.patch
$ cp arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.c ~
$ cd ~
$ cat > Makefile << EOF
obj-m := acpi-cpufreq.c
KDIR := /lib/modules/$(shell uname -r)/build
PWD := $(shell pwd)
default:
        $(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules
EOF
$ make
$ sudo cp acpi-cpufreq.ko /lib/modules/$(uname -r)/kernel/arch/x86/kernel/cpu/cpufreq
```

---

### Post by pressureman on 2008-08-29
Module for latest Intrepid kernel, 2.6.27-2-generic

---

### Post by Nathan_M on 2008-08-30
> **pressureman said:**
> Try running 'sudo apt-get dist-upgrade' from a terminal, in case the later kernels are being held back for some reason. If you still don't get anything later than 2.6.24-12 (which is really ancient - in fact, I seem to remember that was way back when Hardy was still in testing), please paste your /etc/apt/sources.list.

```
$ sudo apt-get dist-upgrade 
[sudo] password for nathan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
nathan@nathan-macinnes:~$ cat /etc/apt/sources.lst
deb http://getswiftfox.com/builds/debian unstable non-free
```

Now this is weird. I have a sources.list file which contains all this:

[SIZE="1"]```
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner
deb http://gb.archive.ubuntu.com/ubuntu/ hardy main universe restricted multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy universe main multiverse restricted #Added by software-properties
deb http://security.ubuntu.com/ubuntu/ hardy-security universe main multiverse restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-security universe main multiverse restricted
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates universe main multiverse restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-updates universe main multiverse restricted

deb http://gb.archive.ubuntu.com/ubuntu/ hardy-backports universe main multiverse restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-backports universe main multiverse restricted
deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu gutsy main
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-proposed universe main multiverse restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-proposed universe main multiverse restricted
```
[/SIZE]
but I've never heard of sources.*list*.

Also, there are updates listed in my history:
linux-generic (2.6.24.20.22) to 2.6.24.21.23
linux-headers-generic (2.6.24.20.22) to 2.6.24.21.23
linux-image-generic (2.6.24.20.22) to 2.6.24.21.23
linux-restricted-modules-common (2.6.24.14-20.46) to 2.6.24.14-21.47
linux-restricted-modules-generic (2.6.24.20.22) to 2.6.24.21.23
and
linux-restricted-modules-2.6.24-21-generic (2.6.24.14-21.47) to 2.6.24.14-21.48
linux-restricted-modules-common (2.6.24.14-21.47) to 2.6.24.14-21.48

Is it possible that uname -r is reporting the wrong version for some reason. Sorry this is going off topic, but I presume the undervolting isn't working for me because of this. And sorry that it's so long.

---

### Post by pressureman on 2008-08-30
What do you get from 'dpkg -l | grep linux-image' ?

You can also see what kernel is currently running with 'cat /proc/version'

---

### Post by Nathan_M on 2008-09-01
```
$ dpkg -l | grep linux-image
ii  linux-image-2.6.24-12-generic              2.6.24-12.22                                               Linux kernel image for version 2.6.24 on x86
ii  linux-image-2.6.24-14-generic              2.6.24-14.25                                               Linux kernel image for version 2.6.24 on x86
ii  linux-image-2.6.24-15-generic              2.6.24-15.27                                               Linux kernel image for version 2.6.24 on x86
ii  linux-image-2.6.24-16-generic              2.6.24-16.30                                               Linux kernel image for version 2.6.24 on x86
ii  linux-image-2.6.24-17-generic              2.6.24-17.31                                               Linux kernel image for version 2.6.24 on x86
ii  linux-image-2.6.24-18-generic              2.6.24-18.32                                               Linux kernel image for version 2.6.24 on x86
ii  linux-image-2.6.24-19-generic              2.6.24-19.41                                               Linux kernel image for version 2.6.24 on x86
ii  linux-image-2.6.24-20-generic              2.6.24-20.38                                               Linux kernel image for version 2.6.24 on x86
ii  linux-image-2.6.24-21-generic              2.6.24-21.42                                               Linux kernel image for version 2.6.24 on x86
ii  linux-image-generic                        2.6.24.21.23                                               Generic Linux kernel image
$ cat /proc/version
Linux version 2.6.24-12-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu4)) #1 SMP Wed Mar 12 23:01:54 UTC 2008
```
Weird. So which kernel version do I have?

---

### Post by pressureman on 2008-09-01
Well, it looks like you have the latest kernel there (and a whole lot of previous kernels). But for whatever reason, your box is not booting the latest kernel.

So it's most likely a GRUB issue. Check that in your /boot/grub/menu.lst, you actually have all those kernels listed. If not, there may be a problem with the update-grub hooks that get run whenever a new kernel is installed. Also check that you have "default 0" in your menu.lst - that way, the default/first kernel to be selected will be the latest (since the list sorts reverse-alphanumerically).

If all that fails, try selecting one of the kernels manually by pressing Esc during bootup, so that you actually see what GRUB thinks is installed.

---

### Post by tzorg on 2008-09-06
> **Nathan_M said:**
>  If I run the script, the first time, it counted all the way down to VID 0, then asked me to run the script again. When I do, I get this output, after the normal stuff:

```
Will use current directory to store/retrieve test results.

Read phc_default_vids:
> Success!

Load VIDs from 'phc_tweaked_vids'
> ERROR: Wrong VID count!
```

My phc_cur_pos file just contains a 0, and phc_tweaked_vids is empty! Any explanation?

Edit: I just deleted the files, and this is what I get the first time I ran it:

```

The lowest acceptable VID is 0.

Recovering CPU.
./linux-phc-optimize.bash: line 138: 12435 Terminated              burnMMX

Run this script again to continue the optimization.
```

First of all, thx for this tuto i was waiting for a long time such solution for my laptop.=D>
I obtain the same result, but i don't have any problem with my kernel revision, mine is 6.24.19.
Is anyboby can help ? I'm not easy with kernel things.:(

Please excuse my frenchenglish

---

### Post by cheaptrick on 2008-09-07
hi there. i couldnt find a .config file in my /boot to copy over in step 2, all i had was a config-2.6.24-19-generic , is that the one? when i ran patch -p1 < linux-phc*.patch

this was the output

patching file arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.c
Hunk #2 FAILED at 60.
Hunk #3 succeeded at 110 (offset -1 lines).
Hunk #4 FAILED at 749.
Hunk #5 succeeded at 757 (offset -12 lines).
2 out of 5 hunks FAILED -- saving rejects to file arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.c.rej

---

### Post by tzorg on 2008-09-08
Hi there,
Next step in my tries,
now with kernel 2.6.24-21-generic, the script do the same, going down to -1 and refusing the second run coz of invalid values...

> Default VIDs: 38 29 19 
Current VIDs: -1 29 19
Testing VID: -1 (684 mV)
./linux-phc-optimize.bash: line 161: printf: -1 : option non valable
printf: usage: printf [-v var] format [arguments]


The lowest acceptable VID is 0.

Recovering CPU.

Run this script again to continue the optimization.
./linux-phc-optimize.bash: line 138:  7301 Compl

I think the script don't change the VID values coz the cores temp rise to 77/75 °C and never drop, at such theorical low voltage the temp should be lower, isn't it?
THX for help or comments

---

### Post by guilleml on 2008-09-09
Hi! first of all thank you all for posting this tutorial, I've used it to make some tests in my new laptop.

I have a Dell inspiron 1525 with a T5750@2Ghz cpu.

The script didn`t work for me but I followed the instructions from [https://www.dedigentoo.org/trac/linux-phc/wiki/FindingTheLowestVoltages](https://www.dedigentoo.org/trac/linux-phc/wiki/FindingTheLowestVoltages)

My original VIDS were:

43 35 27 19

So I setup the clock to each one of them (2Ghz, 1,67Ghz, 1,33Ghz and 1Ghz) and I tryed each VID while 2 mprimes were running at 100% in the cpu.
I looked to the cpu temperature, I did the tests whith the battery so I could check the power used using powertop.

I noticed a change in the power required at 2Ghz, not much at 1Ghz.
The VIDS after the test were:

24 1 1 1

At 2Ghz it was using 35W when the VID was 43,when I changed it to 24, it was using 28W.
At 1Ghz it changes from 25-26W to 24-25W and 14W when idle.

Temperature didn't change so much, only when 100% is used, at 2Ghz it was 60C, now it's 54C.

I have some questions:
¿can I change the VIDS to 24 0 0 0?¿or it will be the same as 24 1 1 1?
¿why are the cpu wasting so much energy when they can run at lower voltage with the same results?if this is safe it would be better, ¿is it safe?

---

### Post by Ares Drake on 2008-09-10
> **guilleml said:**
> 
I have some questions:
¿can I change the VIDS to 24 0 0 0?¿or it will be the same as 24 1 1 1?
¿why are the cpu wasting so much energy when they can run at lower voltage with the same results?if this is safe it would be better, ¿is it safe?

1. I think 0 doesn't work, so 24 1 1 1 is the lowest. Wouldn't make much difference anyway.

2. Making CPUs is a little bit like growing tomatoes. Not all fruits are equal. Likewise, all cpus even of the same kind differ a little bit. So the lowest safe voltage is an individual value for each single cpu. For the cpu manufacturer (intel) it would be too expensive to test them all for their lowest save voltage. So they specify a limit and just test if they work at that limit. As the lowest safe voltage for a given cpu is lower than the specified limit, the difference is wasted.

3. If it is not save (i.e. you set the voltage too low) your computer will freeze / lock up. But as you discribed above you checked for that, so you can assume it is safe.

---

### Post by guilleml on 2008-09-10
> **Ares Drake said:**
> 1. I think 0 doesn't work, so 24 1 1 1 is the lowest. Wouldn't make much difference anyway.

2. Making CPUs is a little bit like growing tomatoes. Not all fruits are equal. Likewise, all cpus even of the same kind differ a little bit. So the lowest safe voltage is an individual value for each single cpu. For the cpu manufacturer (intel) it would be too expensive to test them all for their lowest save voltage. So they specify a limit and just test if they work at that limit. As the lowest safe voltage for a given cpu is lower than the specified limit, the difference is wasted.

3. If it is not save (i.e. you set the voltage too low) your computer will freeze / lock up. But as you discribed above you checked for that, so you can assume it is safe.

Thanks for your answers :)
The system seems pretty stable now, it's even safe! I'm quite happy with this tune.

---

### Post by shador on 2008-09-11
Just one question before I get this started. If I by some reason want all of this undone, how do I do that?

---

### Post by knix on 2008-09-11
Anybody got a 2.6.27-2 64-bit module? I'm running Intrepid 64 bit on a C2D and Pressureman's module didn't work.

Thanks.

edit: or 2.6.27-3?
Or a patch for either?

---

### Post by cheaptrick on 2008-09-12
i'm using a C2D LV7500 1.6ghz

cat /sys/devices/system/cpu/cpu0/cpufreq/phc_controls gives me
9:37 8:27 6:21 136:11 


The first test stoped at
Default VIDs: 37 27 21 11 
Current VIDs: 2 27 21 11
Testing VID: 2 (732 mV)

it did not stop until i accidentally pressed a key
and i did noticed that the cpu temperature increased by more 10 degrees during the test
ok the 1st test did not crash at all!
the next few tests crashed during the first round

and i got this 
Default VIDs: 37 27 21 11 
Current VIDs: 4 2 1 1

Before i continue with step 5 ,does this look right? it seems weird for me.

---

### Post by pressureman on 2008-09-12
Module for latest Intrepid kernel, 2.6.27-3-generic (32 bit)

---

### Post by Tao on 2008-09-12
Which PHC patch did you use for interpid kernel?

---

### Post by pressureman on 2008-09-12
> **Tao said:**
> Which PHC patch did you use for interpid kernel?

The one contained in this forum thread [http://phc.athousandnights.de/viewtopic.php?f=13&t=2](http://phc.athousandnights.de/viewtopic.php?f=13&t=2)

It says it's for 2.6.26, but works fine in 2.6.27. I guess the acpi-cpufreq source hasn't changed between versions (or at least, not significantly enough for the patch to fail to apply cleanly).

---

### Post by kszonek on 2008-09-14
> **pressureman said:**
> The one contained in this forum thread [http://phc.athousandnights.de/viewtopic.php?f=13&t=2](http://phc.athousandnights.de/viewtopic.php?f=13&t=2)

It says it's for 2.6.26, but works fine in 2.6.27. I guess the acpi-cpufreq source hasn't changed between versions (or at least, not significantly enough for the patch to fail to apply cleanly).

I used this patch with 2.6.27-3 64bit kernel, it was my first time with phc. After reboot i have problems with 'podprobe acpi_cpufreq':

> 
FATAL: Error inserting acpi_cpufreq (/lib/modules/2.6.27-3-generic/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko): Invalid module format


I tried to recompile module, I also used your module from post above (32bit one, there was a chance...), but I cant make it working. I left Microsoft 3 weeks ago, I am fresh with linux and the last thing I miss is long battery time with Vista+RMCLock.

Any idea what is wrong?

edit:
of course with backup version of acpi_cpufreq.ko scalling works OK and "lsmod | grep acpi_cpufreq" shows loaded module, but after replace module is not loaded at startup and it cant be loaded manually. Some HOWTOs says to check for speedstep module, but it is not loaded.

edit2:
I have 2 ubuntu on hdd, because I dont want to damage main one with experiments, but I tried to use acpi_cpufreq with first OS (2.6.24-19 64bit). Precompiled module didn't work, but I made one myself and it seems to be ok. Only seems, because every change of phc_controls does nothing. With dual burnMMX in background temps are about 85oC with 11:43, 11:20 and even 11:1. Same with other multipliers - on Vista temperature drop was huge.

I should add that my laptop is Compal FL90, with T7500 cpu and 8600gt.

Now I am trying to run linux-phc-optimize-script, but I am receiving error about missing file functions.bash (i have download it of course, to the same directory - Desktop). Now I am tired fighting with phc (why it is not as simple as with Microsoft) - I should better go sleep.

---

### Post by anjie on 2008-09-15
Hello,

First, thank very much for the useful howto (hope it will work for me soon).

could anyone tell me why at this step
```

cat /sys/devices/system/cpu/cpu0/cpufreq/phc_controls

```

I get 

"no device"? I'm sure I've done all the previous steps well.
I've checked that the copied file was in the right place, and it is.
I've rebooted twice, using two different kernels... 18 - 19.


Thanks,
Anjie

---

### Post by cheaptrick on 2008-09-19
the test werent giving me accurate Vids, 
i got this 9:37 8:27 6:21 136:11 
from  cat /sys/devices/system/cpu/cpu0/cpufreq/phc_controls

my tweaked vids output was 6 6 1 1
echoed it, and was never able to boot up again in ubuntu until i undo the echo

---

### Post by pressureman on 2008-09-22
Module for latest Intrepid kernel, 2.6.27-4-generic (32 bit)

---

### Post by Lure on 2008-09-23
Did anybody build the module successfully for 64-bit Intrepid kernel? It seems that all positive reports are with 32-bit kernel...

When I try to build it myself, it fails to load with module format error. :-(
If somebody would share a working 64-bit module, I would be more than happy.

---

### Post by linkmaster03 on 2008-09-25
OK. I did everything and it was correct, up until I ran the script. It went all the way down to 0 and stopped. 

```
Default VIDs: 40 34 30 25
Current VIDs: 0 34 30 25
Testing VID: 0 (700 mV)
..............................
Default VIDs: 40 34 30 25
Current VIDs: -1 34 30 25
Testing VID: -1 (684 mV)
./linux-phc-optimize.bash: line 161: printf: -1: invalid option
printf: usage: printf [-v var] format [arguments]


The lowest acceptable VID is 0.

Recovering CPU.
./linux-phc-optimize.bash: line 138: 11296 Terminated              burnMMX

Run this script again to continue the optimization.

```

Then when I tried to run the script again...

```
Load VIDs from 'phc_tweaked_vids'
> ERROR: Wrong VID count!
```

And it stops. :( Help?

---

### Post by dman4486 on 2008-09-26
I have set everything up and run the script, but it will not run past my 3rd VID....it will not save the 3rd VID either.

here is what it saves:

16 8 30 26 22 18

why will it not continue?

when I run the script now, it goes down to "4" which would replace the 30 and crashes, but never saves the "4":confused:

---

### Post by dman4486 on 2008-09-30
> **dman4486 said:**
> i have set everything up and run the script, but it will not run past my 3rd vid....it will not save the 3rd vid either.

Here is what it saves:

16 8 30 26 22 18

why will it not continue?

When i run the script now, it goes down to "4" which would replace the 30 and crashes, but never saves the "4":confused:



nobody?:(

---

### Post by dman4486 on 2008-09-30
ok....figured out that issue, now how do I do step 5?  I have rc0, rc1, rc2, rc3, rc4

---

### Post by kasjak2000 on 2008-10-01
Hey guys,

I have a T5870 and my fids are:

```
root@x64ubuntu8041:~# cat /sys/devices/system/cpu/cpu0/cpufreq/phc_fids 
11 10 8 6 136 
root@x64ubuntu8041:~# cat /sys/devices/system/cpu/cpu1/cpufreq/phc_fids 
11 10 8 6 136 
root@x64ubuntu8041:~#
```

But I cant set down the processor to 600mHz, to 800mHz only :-(

In the windows I can set the 600mHz (6x100) with rmclock successful, why not in linux?

Can anyone set down a C2D-processor to 600mHz? And if yes, how?

Regards 
kasjak2000

---

### Post by pressureman on 2008-10-05
Module for latest Intrepid kernel, 2.6.27-5-generic (32 bit)

---

### Post by patrickfromspain on 2008-10-06
I'm running latest intrepid kernel (2.6.27-5-generic) succesfully with the phc extensions, and also was running 2.6.27-4-generic.

How I did? First I moved the acpi-cpufreq.ko original module to acpi-cpufreq.ko-original, then installed the linux-phc package from here [http://ppa.launchpad.net/bonniot-users/ubuntu/pool/main/l/linux-phc/](http://ppa.launchpad.net/bonniot-users/ubuntu/pool/main/l/linux-phc/) and rebooted. 

After rebooting you can run sudo linux-phc-install and reboot, it should work fine. After that I removed the linux-phc package, since it seemed to give out an error when installed.

If I didn't move the acpi-cpufreq.ko module out of the way it gave me an error.

Hope it helps

---

### Post by pressureman on 2008-10-07
Module for latest Intrepid kernel, 2.6.27-6-generic (32 bit)

---

### Post by stillka on 2008-10-09
> **pressureman said:**
> Module for latest Intrepid kernel, 2.6.27-6-generic (32 bit)

thanks a much for providing compiled modules, it save time :-)

---

### Post by Black16V on 2008-10-10
Hi,

where can I download the patch for 2.6.27 ?

---

### Post by pressureman on 2008-10-10
Module for latest Intrepid kernel, 2.6.27-7-generic (32 bit)

---

### Post by pressureman on 2008-10-10
> **Black16V said:**
> where can I download the patch for 2.6.27 ?

The 2.6.26 patch works fine with 2.6.27.

[http://phc.athousandnights.de/viewtopic.php?f=13&t=2](http://phc.athousandnights.de/viewtopic.php?f=13&t=2)

---

### Post by virtuoso88 on 2008-10-11
Has anyone actually saved battery life?  I read through all 22 pages and only 1 person mentioned something.  I just did this on my W500 and my battery usage is exactly the same.

---

### Post by linkmaster03 on 2008-10-11
This is not supposed to save battery life, it is supposed to make your PC cooler and quieter. Can ANYONE help me? :(

---

### Post by Pogeymanz on 2008-10-12
So, I followed this guide to undervolt, but my cpu is not running any cooler. What's up with that?

Here is lsmod | grep acpi_cpufreq:
```

acpi_cpufreq           14864  0 
freq_table              6400  1 acpi_cpufreq
processor              39744  2 acpi_cpufreq,thermal

```

cat /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
```
10:2 8:2 6:2 
```

Why wouldn't my CPU run any cooler? My defaults were:
10:40 8:35 6:29

---

### Post by jmmL on 2008-10-13
Pogeymanz, your output of " cat /sys/devices/system/cpu/cpu0/cpufreq/phc_controls " looks suspiciously low. If your CPU is anything like mine, the VIDs cannot be set any lower than the lowest factory VID - which is 19 in my case (with an Intel T5450) and looks to be 29 in your case.

You might want to try manually adjusting your VIDs to
```

10:29 8:29 6:29

```

Absolutely no guarantees that that won't harm your computer though; you have been warned.

Also, with regards to the battery life; it should help the CPU draw less power even when it's under load, and should therefore help extend battery life. Anecdotally, I'd say mine has improved by 5 minutes or so - compared to a vanilla install. Lowering my VIDs reduced the voltage across the cores by about 0.3V, which is about a 1/4 reduction in voltage. This should correspond to a 1/4 reduction in power drawn by the processor.

---

### Post by Pogeymanz on 2008-10-13
Thank you JimmL. Can I ask how you found your lowest factory VIDs? I forgot what the number is for my processor, but it's the Intel Dual Pentium 2.0 GHz.

So far my computer is stable. I even ran burnMMX just for funzies and nothing crashed or anything. I guess my temps under stress were a little lower than before, but idle temps are about the same. Maybe it did work and I was just expecting too much?

---

### Post by jmmL on 2008-10-13
When I ran the optimisation script on the first page - I had the same problem. It kept on "testing" VIDs below 19, and reported everything was okay. I killed it at about 5, because I could see it was headed to nonsense, from reading others' experiences in the first few pages of this thread. One guy then posted that you couldn't reduce any of the VIDs below the lowest factory VID, and then mentioned that for him, with his CPU, this number was 19. His CPU was very similar to mine, so I tried it, and sure enough it works. Any lower, and the system just ignores the instruction.

You're using a mobile CPU right? I know there's a command-line way to get this information, but i forget how. Anyway, can you open up Gnome System Monitor (type "gnome-system-monitor" in a terminal) and look under the "System" tab. There should be a number there of the form Txxx or maybe Pxxx, where x is a number. That will be a start to finding out your VIDs.

However, I suspect we might have very similar CPUs - our frequency multipliers are the same (10: 8: 6: ). In this case, it might be safe to try setting all your VIDs to 19, and just see what happens. Emphasis on MIGHT. **Do at your own risk.**

I noticed about a 2C drop at idle (to about 52C) and a 5C drop under load (about 55C). I wasn't so concerned about the heat though - i did just to eke improvements in battery life.

---

### Post by Pogeymanz on 2008-10-14
Actually this isn't a mobile computer. It's my desktop. But my thought is this: I can make it run cooler and maybe use less electricity, and the price is the same (ZERO), so why the heck not?

I'll try all 19's. I guess it can't really hurt. If it just ignores anything too low, they worst case is that it wont do anything. If that doesn't work, I'll try 29. Thanks for the help.

---

### Post by linkmaster03 on 2008-10-17
jmmL, what should I set my VIDs at? (since the script just kept going to 0) I have an Intel T2080.

---

### Post by jmmL on 2008-10-17
What do you get from 
```
cat /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
```

?

---

### Post by linkmaster03 on 2008-10-17
```
13:40 10:34 8:30 6:25
```

---

### Post by jmmL on 2008-10-17
In that case, try this:
```
echo "13:25 10:25 8:25 6:25" > /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
```

You can also place that command in your rc.local, so it gets run every time you boot up. I do this, but also echo it to cpu1 as well as cpu0 - I've got a dual core cpu, and it's just to make sure nothing odd happens. I'm told you can leave out echo to the other core though, as it will automatically adjust.

No guarantees it will work. If it's anything like my CPU, it will do. Run burnMMX for a while, until you're happy it's stable.

---

### Post by linkmaster03 on 2008-10-18
Thanks, it worked! I'll see if I notice any heat/fan noise difference.

---

### Post by KillaW0lf04 on 2008-10-18
Hey, i got an msi gx600p laptop which has an overclock button included as a feature. 

[http://global.msi.com.tw/index.php?func=proddesc&maincat_no=135&cat2_no=271&prod_no=1307](http://global.msi.com.tw/index.php?func=proddesc&maincat_no=135&cat2_no=271&prod_no=1307)

Would using this screw around with the whole overclocking thing?

---

### Post by raphoun on 2008-10-21
Does anyone make it work with a T7700 on a dell XPS M1530?

---

### Post by jmmL on 2008-10-21
@ KillaWolf: It won't directly mess up your overclocking I don't think - i.e., having lowering voltage doesn't necessarrily mean lower clocks. However, i wouldn't be surprised if the overclocking made it unstable using lower VIDs. I'd run the stress-test tool on page 1 with your overclocking enabled, just to be on the safe side. Again - **NO GUARANTEES**.

@ raphoun: these threads are probably of interest to you as well:
[http://ubuntuforums.org/showthread.php?t=847773](http://ubuntuforums.org/showthread.php?t=847773)
[http://ubuntuforums.org/showthread.php?t=729644](http://ubuntuforums.org/showthread.php?t=729644)

I'm sure people have - it's a common Intel CPU.

---

### Post by easytool on 2008-10-25
Can someone post a 64bit apci-cpufreq.ko for kernel 2.6.27-7 ? 64bit please~~

I tried to compiled it for a whole night, but couldnot work it out.

Many Thanks!!!

---

### Post by coolen on 2008-10-26
This sounds great.

One thing I'm wondering, though: when on AC, can I automatically switch to a higher voltage? I don't particularly mind about heat: the cooling on this laptop is fantastic. If I'm on AC anyway, I want to get the most out of my CPU.

Is there a way to do this?

---

### Post by sarah.fauzia on 2008-10-26
> **patrickfromspain said:**
> I'm running latest intrepid kernel (2.6.27-5-generic) succesfully with the phc extensions, and also was running 2.6.27-4-generic.

How I did? First I moved the acpi-cpufreq.ko original module to acpi-cpufreq.ko-original, then installed the linux-phc package from here [http://ppa.launchpad.net/bonniot-users/ubuntu/pool/main/l/linux-phc/](http://ppa.launchpad.net/bonniot-users/ubuntu/pool/main/l/linux-phc/) and rebooted. 

After rebooting you can run sudo linux-phc-install and reboot, it should work fine. After that I removed the linux-phc package, since it seemed to give out an error when installed.

If I didn't move the acpi-cpufreq.ko module out of the way it gave me an error.

Hope it helps

With linux kernel 2.6.27-7 in 64-bit Intrepid still gives me an error, and I've been unsuccessful in compiling... I went through all the steps prior to the reboot without any errors, and when I run ```
cat /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
``` I get:

```
cat: /sys/devices/system/cpu/cpu0/cpufreq/phc_controls: No such file or directory
```

Also, when I enter ```
lsmod | grep acpi_cpufreq
```
Nothing happens. It just gives another blank prompt, as if I hadn't asked for anything.

But when I restore the backup copy and reboot, I get normal values again.

By the way, I'm using an Lenovo X61T with the latest release of Intrepid (kernel 2.6.27-7).

---

### Post by pardes3 on 2008-10-29
I also tried to compile it on 64 bit but was not successful.  Anyone here have ahd success yet? If so, please post the compiled version for us.

Thanks!!!

---

### Post by landal on 2008-10-30
The compilation on a 64bit system works well with this how-to : [http://wiki.ubuntuusers.de/Prozessorspannung_absenken]("http://wiki.ubuntuusers.de/Prozessorspannung_absenken") (link on the first post)

command isn't the same as in this forum. This works :
```
cd arch/x86/kernel/cpu/cpufreq/
make -C /lib/modules/$(uname -r)/build SUBDIRS=$(pwd) modules
```

And I post the result.

---

### Post by pardes3 on 2008-10-30
> **landal said:**
> The compilation on a 64bit system works well with this how-to : [http://wiki.ubuntuusers.de/Prozessorspannung_absenken]("http://wiki.ubuntuusers.de/Prozessorspannung_absenken") (link on the first post)

command isn't the same as in this forum. This works :
```
cd arch/x86/kernel/cpu/cpufreq/
make -C /lib/modules/$(uname -r)/build SUBDIRS=$(pwd) modules
```

And I post the result.

Sir, very kind of you. Thanks!

---

### Post by quirks on 2008-10-30
I couldn't find the compiled module for the latest Hardy kernel (2.6.24-21-generic), so I compiled it myself. Here it is:

---

### Post by pardes3 on 2008-10-30
I am not sure why when I run the optimize script... it starts and goes all the way to -1 and stops.  It throws line 161 printf error and says 0 is lowest VID, run the test again.  But if I run again it complains about WRONG VID COUNT.

Help?

Thanks

---

### Post by knix on 2008-10-31
> **pardes3 said:**
> I am not sure why when I run the optimize script... it starts and goes all the way to -1 and stops.  It throws line 161 printf error and says 0 is lowest VID, run the test again.  But if I run again it complains about WRONG VID COUNT.

Help?

Thanks
honestly how i finally did it was use RMclock in windows xp to find the best voltage, then translated it into the vids i got from the script (i wrote them down)

---

### Post by sarah.fauzia on 2008-11-01
Well, the compiled module for 64-bit works, but I think my case might be unique...

```
cat /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
10:36 9:25 6:21 136:11
```

I get a VID for my first frequency of 0. I took the precaution and used 1 instead. However, when I echo it, my computer freezes, and when I added it to my startup in /etc/rc.local, my computer becomes unbootable and the screen strangely dark (though I connected it to the AC). Removing it from /etc/rc.local with the root terminal fixes the problem (though I was scared for a few minutes there!) Does that mean I can't undervolt my processor?

I have a Lenovo X61T, running Ubuntu Intrepid, 64-bit.

---

### Post by seish on 2008-11-07
> **linkmaster03 said:**
> jmmL, what should I set my VIDs at? (since the script just kept going to 0) I have an Intel T2080.

Hey man, this might come too late but for just in case:

Same thing happened to me (ASUS f3e laptop Intel T5750 2.0ghz) VIDs went down to 0. 

I deleted the *phc_tweaked_vids* and *phc_current_pos* files 
And ran the test again, but I ran burnMMX BEFORE starting the test.

sorry if im speaking as to an idiot but thats how I explain things to myself :)

so: 
1) deleted old files
2) run $burnMMX in separate gterm window
3) $sudo ./linux-phc-optimize

This time it crashed(yay!) and after reboot recorded value 10 instead of 0. result was 12:10 10:1 8:1 6:1.

EDIT: I'm not sure i'm noticing any difference between 19 and 10 actually don't know if my cpu igrnores commands below 19 as some users pointed, but its strange that crashed at 10 if values below 19 get ignored. i doubt something else crashed my pc tho its possible i guess 

Hope that helps.

---

### Post by stillka on 2008-11-09
> **pressureman said:**
> Module for latest Intrepid kernel, 2.6.27-7-generic (32 bit)

After last update of 2.6.27-7 kernel phc_controls in this module stop working for me. Could you please recompile it?

---

### Post by sneakersupplier on 2008-11-09
Wholesale Jordan shoes: [Air Jordan](http://www.sneakersupplier.com)

---

### Post by pressureman on 2008-11-09
> **stillka said:**
> After last update of 2.6.27-7 kernel phc_controls in this module stop working for me. Could you please recompile it?

It's working fine for me. Check that the recent update didn't overwrite acpi-cpufreq.ko with a new (unpatched) copy.

---

### Post by stillka on 2008-11-11
> **pressureman said:**
> It's working fine for me. Check that the recent update didn't overwrite acpi-cpufreq.ko with a new (unpatched) copy.

I verified this possibility with diff and I have right patched version from this forum. Anyway, new kernel is here so I'll try patched version again...

My notebook is IBM Thinkpad X40:

root@X40:~# lsmod | grep acpi
thinkpad_acpi          66176  0 
rfkill                 17176  1 thinkpad_acpi
led_class              12164  1 thinkpad_acpi
nvram                  16524  1 thinkpad_acpi
pata_acpi              12160  0 
libata                177312  3 pata_acpi,ata_piix,ata_generic
acpi_cpufreq           15500  0 
freq_table             12672  3 cpufreq_ondemand,cpufreq_stats,acpi_cpufreq
processor              42156  3 thermal,acpi_cpufreq

---

### Post by ivanhoe1024 on 2008-11-11
> **pressureman said:**
> It's working fine for me. Check that the recent update didn't overwrite acpi-cpufreq.ko with a new (unpatched) copy.

Hi everybody!!
It's working fine for me, too, so: a lot of thanks!! (ps. I'm not English, so I'm sorry if I write like an idiot, sometimes!!)
I'd like to ask you a question: with my kubuntu 8.04, I used to compile the patched acpi-cpufreq module by myself, patching the linux-sources from ubuntu, and using this command:
first I copy the config-xxx file from /boot, then
make oldconfig
make prepare
make scripts
make M=./arch/x86/kernel/cpu/cpufreq
all done! And this always worked... Now, with the Intrepid, and 2.6.27, I fails... when I restart the system with the new module, it is not loaded, and phc doesn't work... moreover, I can't use cpufreq anymore... if I try to load acpi-cpufreq manually, it says "invalid module format", or something similar... but with your precompiled module, it works... Does anybody know what's the problem?? I use kubuntu 8.10 32 bit, with a Core2 t7500... thanks!!

---

### Post by stillka on 2008-11-12
Please compile version for 2.6.27-8-generic.

---

### Post by bmidgley on 2008-11-13
I've noticed the same thing. Run "dmesg|tail" and you'll probably see this in the log:

acpi_cpufreq: no symbol version for struct_module

I also don't know how to fix it or what is wrong with the 8.04 instructions. It sure would be nice to be able to build it myself again.

> **ivanhoe1024 said:**
> I used to compile the patched acpi-cpufreq module by myself, patching the linux-sources from ubuntu, and using this command:
first I copy the config-xxx file from /boot, then
make oldconfig
make prepare
make scripts
make M=./arch/x86/kernel/cpu/cpufreq
all done! And this always worked... Now, with the Intrepid, and 2.6.27, I fails... when I restart the system with the new module, it is not loaded, and phc doesn't work... moreover, I can't use cpufreq anymore... if I try to load acpi-cpufreq manually, it says "invalid module format

---

### Post by bmidgley on 2008-11-14
ok... here's a fix. from /usr/src/linux-source-2.6.27:

cp ../linux-headers-2.6.27-7-generic/Module.symvers .

before running any of the make targets. I also removed a Module.symvers from the acpi-cpufreq directory to be sure it was using the toplevel version. I followed all the other instructions and it works again. (woohoo)

> **bmidgley said:**
> I've noticed the same thing. Run "dmesg|tail" and you'll probably see this in the log:

acpi_cpufreq: no symbol version for struct_module

I also don't know how to fix it or what is wrong with the 8.04 instructions. It sure would be nice to be able to build it myself again.

---

### Post by Virgofenix on 2008-11-14
I have an [*Intel Pentium T2370*]("http://processorfinder.intel.com/details.aspx?sSpec=SLA4J"). 

The initial VID values:

13:43 10:33 8:26 6:19 

I'm having a problem with the optimization script. The VID value of the first pair(13:43) goes all the way down to 0(700mV)(, and even attempts -1(684mV)), at which point, the script terminates and asks me to run the script again:

> ./linux-phc-optimize.bash: line 161: printf: -1: invalid option
printf: usage: printf [-v var] format [arguments]


The lowest acceptable VID is 0.

Recovering CPU.
./linux-phc-optimize.bash: line 138: 17047 Terminated              burnMMX

Run this script again to continue the optimization.

However, running the script again gives me a read error of the tweaked VID file:

> Will use current directory to store/retrieve test results.

Read phc_default_vids:
> Success!

Load VIDs from 'phc_tweaked_vids'
> ERROR: Wrong VID count!


This is a dual-core, so I have burnMMX on.

What's wrong?

---

### Post by ivanhoe1024 on 2008-11-14
> **bmidgley said:**
> ok... here's a fix. from /usr/src/linux-source-2.6.27:

cp ../linux-headers-2.6.27-7-generic/Module.symvers .

before running any of the make targets. I also removed a Module.symvers from the acpi-cpufreq directory to be sure it was using the toplevel version. I followed all the other instructions and it works again. (woohoo)

Fantastic!! I'll try as soon as I can, hoping it'll work for me too...

---

### Post by ivanhoe1024 on 2008-11-14
> **bmidgley said:**
> ok... here's a fix. from /usr/src/linux-source-2.6.27:

cp ../linux-headers-2.6.27-7-generic/Module.symvers .

before running any of the make targets. I also removed a Module.symvers from the acpi-cpufreq directory to be sure it was using the toplevel version. I followed all the other instructions and it works again. (woohoo)

To compile the module from the 2.6.27-8 sources, where do I have to take the Module.symvers? From 2.6.27-7 headers, or from the 2.6.27-8 ones?? I'm sorry, but I'm not so expert in kernel matters...

---

### Post by bmidgley on 2008-11-14
the versions should probably match what you are running... to recap I had already done:

cd /usr/src/linux-source-2.6.27
patch -p1 < linux-phc*.patch

then to get it to work:

make clean
cp ../linux-headers-`uname -r`/Module.symvers .
make oldconfig
make prepare
make scripts
make M=./arch/x86/kernel/cpu/cpufreq

> **ivanhoe1024 said:**
> To compile the module from the 2.6.27-8 sources, where do I have to take the Module.symvers? From 2.6.27-7 headers, or from the 2.6.27-8 ones?? I'm sorry, but I'm not so expert in kernel matters...

---

### Post by ivanhoe1024 on 2008-11-16
> **bmidgley said:**
> the versions should probably match what you are running... to recap I had already done:

cd /usr/src/linux-source-2.6.27
patch -p1 < linux-phc*.patch

then to get it to work:

make clean
cp ../linux-headers-`uname -r`/Module.symvers .
make oldconfig
make prepare
make scripts
make M=./arch/x86/kernel/cpu/cpufreq

Ok, thank you a lot, I'll try all these things... If it works for me to, maybe it'll work for everyone...

---

### Post by skinnie on 2008-11-16
can someone post apci-cpufreq.ko for 2.6.27-8 i386?

---

### Post by ivanhoe1024 on 2008-11-16
@ bmidgley: wow, it's working!! A lot of thanks, you're a monster!!=D>=D>

@skinnie: here is your modded module, but... why don't you try to compile it yourself? it doesn't take more than 5 minutes...

acpi-cpufreq for 32-bit intrepid 2.6.27-8

---

### Post by skinnie on 2008-11-16
> **ivanhoe1024 said:**
> @ bmidgley: wow, it's working!! A lot of thanks, you're a monster!!=D>=D>

@skinnie: here is your modded module, but... why don't you try to compile it yourself? it doesn't take more than 5 minutes...

acpi-cpufreq for 32-bit intrepid 2.6.27-8

it's strange..in the other day I tried and I coulnd't do it,I don't know why...
thanks anyway :)

---

### Post by ivanhoe1024 on 2008-11-16
> **skinnie said:**
> it's strange..in the other day I tried and I coulnd't do it,I don't know why...
thanks anyway :)

It's a pleasure, it's only the first time I can help someone in something concerning GNU/linux, so I'm very happy I can start to contribute actively to this wonderful forum!! :lolflag:

---

### Post by Virgofenix on 2008-11-17
Could somebody please post the increase in their notebook's battery life from the undervolting procedure?

---

### Post by ivanhoe1024 on 2008-11-17
> **Virgofenix said:**
> Could somebody please post the increase in their notebook's battery life from the undervolting procedure?

Uhm, Uhm :-k:-k I don't think it is the most important aspect of the phc patch... I read in this forum that the battery life doesn't change a lot... But I can tell you that my cpu temperature is lower of about 4-5 ° Celsius in idle, and about 10-15 ° Celsius during video conversion!!

---

### Post by ivanhoe1024 on 2008-11-18
> **skinnie said:**
> it's strange..in the other day I tried and I coulnd't do it,I don't know why...
thanks anyway :)

Hi, I have just noticed that my module works fine until I have my AC adapter plugged in, but at the moment I'm using my laptop (asus f3sv) with the battery, and it seems that the module fails... Have you the same problem?? Can you check it for me, please??

---

### Post by blakjesus on 2008-11-20
How can i compile the patch for the 64-bit version of the 2.6.27-7? I downloaded what the website said was the source code but there are already patch files for previous kernels. (I dont even know if they are even compatible with 64-bit)

Please help. I know  how to compile stuff, but i have never worked with the kernel source code.

---

### Post by ivanhoe1024 on 2008-11-25
Here is the module compiled for 2.6.27-10 and 64 bit... It works for me, hope this can interest someone... bye :)

---

### Post by skinnie on 2008-11-26
> **ivanhoe1024 said:**
> Hi, I have just noticed that my module works fine until I have my AC adapter plugged in, but at the moment I'm using my laptop (asus f3sv) with the battery, and it seems that the module fails... Have you the same problem?? Can you check it for me, please??

how do I check?

---

### Post by XRayA4T on 2008-11-26
Here is a 32 bit version for 2.6.27-10

---

### Post by aashay on 2008-11-26
> **XRayA4T said:**
> Here is a 32 bit version for 2.6.27-10

This is the first thread I check whenever a new version is released. Too lazy to compile my own modules :)
Thanks!

---

### Post by Ev1L on 2008-11-27
hey guys, you skipped 2.6.27-9 which has been just made available from update manager.
could someone take care of it please? :p

---

### Post by Ev1L on 2008-11-27
did it by myself, enjoy ;)

---

### Post by ivanhoe1024 on 2008-11-27
> **skinnie said:**
> how do I check?

You can turn up your laptop only with the battery, without AC adapter, and if your cpu can scaling frequencies, it's all right, instead if it can't, the module has got a bug: it works only with the laptop in AC mode, not in battery mode... I haven't tried it recently, I'm sorry... Moreover, I shifted to the 64 bit version of kubuntu, so I'm busy with some configurations...:guitar:

---

### Post by winnibob on 2008-11-28
> **Ev1L said:**
> hey guys, you skipped 2.6.27-9 which has been just made available from update manager.
could someone take care of it please? :p

> **Ev1L said:**
> did it by myself, enjoy ;)

Could you tell us wether it is 32 bits or 64 bits version, because I tried it on my 32 bits Intrepid and it didn't work...

Thanks

---

### Post by Ev1L on 2008-11-28
oh sorry, i forgot, it's 32bits

i cannot tell why it's not working, i used it yesterday evening and it was all like before the kernel update, also after reboots :)

---

### Post by Samfisher on 2008-11-28
Could someone please either upload an acpi-cpufreq.ko module or give instructions on how to create one for
**_Ubuntu Intrepid kernel 2.6.27-9 64-bit_** ?

Thank you!

---

### Post by winnibob on 2008-11-28
> **Ev1L said:**
> oh sorry, i forgot, it's 32bits

i cannot tell why it's not working, i used it yesterday evening and it was all like before the kernel update, also after reboots :)

I tried several time with your module, but it really doesn't work for me. So I compiled it myself and now it works perfect.
I post my file here in case people have trouble or just wanna check.
The module has been compiled for kernel 2.6.27-9 on a 32 bits Intrepid.

---

### Post by Schnitzelpudding on 2008-11-28
Thanks winnibob, that one works for me as well.

Ev1l: Your module failed to load with a "acpi_cpufreq: disagrees about version of symbol struct_module" syslog message.

---

### Post by Ev1L on 2008-11-28
mh ok, i cannot explain it but i am glad that you were able to compile it yourself.
in case of bad surprise tonight when i'll go home, i'll try yours ;)

---

### Post by Samfisher on 2008-11-29
Still no 64-bit module for 2.6.27-9? :(

---

### Post by Mizzou_Engineer on 2008-11-29
> **kasjak2000 said:**
> Hey guys,

I have a T5870 and my fids are:

```
root@x64ubuntu8041:~# cat /sys/devices/system/cpu/cpu0/cpufreq/phc_fids 
11 10 8 6 136 
root@x64ubuntu8041:~# cat /sys/devices/system/cpu/cpu1/cpufreq/phc_fids 
11 10 8 6 136 
root@x64ubuntu8041:~#
```

But I cant set down the processor to 600mHz, to 800mHz only :-(

In the windows I can set the 600mHz (6x100) with rmclock successful, why not in linux?

Can anyone set down a C2D-processor to 600mHz? And if yes, how?

Regards 
kasjak2000

I was wondering the same. Apparently the 800 MHz FSB Core 2 Duos on 965 or 45-series chipsets run at 100x8 rather than 100x6 despite the lowest SpeedStep multiplier being 6x. This is the default behavior under Windows and Linux, except I've not seen anybody able to change the multiplier from 8x to 6x in Linux.

---

### Post by skinnie on 2008-12-03
> **winnibob said:**
> I tried several time with your module, but it really doesn't work for me. So I compiled it myself and now it works perfect.
I post my file here in case people have trouble or just wanna check.
The module has been compiled for kernel 2.6.27-9 on a 32 bits Intrepid.
Sorry I can't test it now :S I'm back to 64bit...

---

### Post by dirtytofu on 2008-12-04
Need some pointers for a new guy here.

I tried to compile my own acpi_cpufreq module, but after I copied it over it didn't work.

I downloaded the one winnibob uploaded and everything works fine with that module.

I followed all the steps correctly to my belief.  The source code I downloaded is "linux-source-2.6.27", but my "uname -r" shows "2.6.27-9-generic".  Did I get the right source code to compile off of?

---

### Post by skinnie on 2008-12-13
the "patching" instruction for X64 are different from the ones described in 1st post?
I can't get my phc working...trying it in 2.6.28-2-generic kernel...I assume it is my patching that is not well done...
edit: tried today in ubuntu 8.10 x64 and the same thing happens..
when I do
>  cat /sys/devices/system/cpu/cpu0/cpufreq/phc_controlIt says it doesn't exist...kernel 2.6.27-10-generic

---

### Post by julakali on 2008-12-16
Precompiled for ubuntu linux-image-2.6.27-10-generic (32bit)
Don't know wether this was necessary or the module compiled for 2.6.27-9 is still working...

---

### Post by homeriq5 on 2008-12-20
could someone post the compiled 2.6.27-9 64-bit module as well?  That would be quite swell if someone could do that.

---

### Post by XRayA4T on 2008-12-20
Here is the 32-bit version of 2.6.27-11

---

### Post by ivanhoe1024 on 2008-12-20
Here's the 64 bit version of the module... give it a try, it works for me... enjoy!!

PS. fixed...:lolflag:

---

### Post by evgeny1978 on 2008-12-20
For 64-bit 2.6.27-11

---

### Post by toasty_ghosty on 2008-12-20
About this working on AMD processors....if you built your laptop you can decrease the voltage simply through the bios. I've done this more on one occasion. This might have been answered before but just in case...

---

### Post by Samfisher on 2008-12-21
> **ivanhoe1024 said:**
> Here's the 64 bit version of the module... give it a try, it works for me... enjoy!!

hey, the archive gives the error 'not a valid bzip2 archive'! would you be able to upload it again please? thank you!

---

### Post by ivanhoe1024 on 2008-12-21
> **Samfisher said:**
> hey, the archive gives the error 'not a valid bzip2 archive'! would you be able to upload it again please? thank you!

I'm sorry, I fixed it...

---

### Post by jcm4 on 2008-12-21
```

cd /home/"your-username"/"kernelversion"
patch -p1 < linux-phc*.patch
make oldconfig
make prepare
make scripts
make M=./arch/x86/kernel/cpu/cpufreq

```

What am I doing wrong in this? My directory is correct.

john@john-laptop:~/2.6.27-9-generic$ patch -p1 < linux-phc*.patch
can't find file to patch at input line 4
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff --new-file -a --unified=5 --recursive  linux-source-2.6.26-rc9_orig/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.c linux-source-2.6.26-rc9-custom8/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.c
|--- linux-source-2.6.26-rc9_orig/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.c	2008-07-09 16:59:37.000000000 +0200
|+++ linux-source-2.6.26-rc9-custom8/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.c2008-07-09 12:41:37.000000000 +0200
--------------------------
File to patch:

---

### Post by svpersteve on 2008-12-26
> **sarah.fauzia said:**
> With linux kernel 2.6.27-7 in 64-bit Intrepid still gives me an error, and I've been unsuccessful in compiling... I went through all the steps prior to the reboot without any errors, and when I run ```
cat /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
``` I get:

```
cat: /sys/devices/system/cpu/cpu0/cpufreq/phc_controls: No such file or directory
```

Also, when I enter ```
lsmod | grep acpi_cpufreq
```
Nothing happens. It just gives another blank prompt, as if I hadn't asked for anything.

But when I restore the backup copy and reboot, I get normal values again.

By the way, I'm using an Lenovo X61T with the latest release of Intrepid (kernel 2.6.27-7).


This is exactly what I get, only I'm not using 64-bit. I'm using an HP dv6000 notebook with Intrepid 8.10 (kernel 2.6.27-9). Can someone please help me out? It gets really hot and my fan is unbelievably noisy!

---

### Post by skinnie on 2008-12-27
> **svpersteve said:**
> This is exactly what I get, only I'm not using 64-bit. I'm using an HP dv6000 notebook with Intrepid 8.10 (kernel 2.6.27-9). Can someone please help me out? It gets really hot and my fan is unbelievably noisy!

Your problem is not only the voltage...
I have a dv9500 and before undervolt and renew of thermal paste,it was like hell,believe or not,now it is cold...and silent :)
End of offtopic :D

---

### Post by pressureman on 2008-12-29
Module for latest Jaunty kernel, 2.6.28-4-generic (32 bit)

---

### Post by zeez on 2009-01-02
> **svpersteve said:**
> This is exactly what I get, only I'm not using 64-bit. I'm using an HP dv6000 notebook with Intrepid 8.10 (kernel 2.6.27-9). Can someone please help me out? It gets really hot and my fan is unbelievably noisy!


Hello, you need to use the correct kernel...

---

### Post by zeez on 2009-01-02
```
Default VIDs: 43 33 26 19 
Current VIDs: 0 33 26 19
Testing VID: 0 (700 mV)
..............................
Default VIDs: 43 33 26 19 
Current VIDs: -1 33 26 19
Testing VID: -1 (684 mV)
[COLOR="Magenta"][B]./linux-phc-optimize.bash: line 161: printf: -1: invalid option
printf: usage: printf [-v var] format [arguments][/B[/COLOR]]


The lowest acceptable VID is 0.

Recovering CPU.
./linux-phc-optimize.bash: line 138: 22244 Terminated              burnMMX

```

I am getting this error when i execute the script :/

---

### Post by XRayA4T on 2009-01-09
I just upgraded to a new version of the 2.6.27-11 kernel and finally got around to putting together scripts to automate the build and install:

makeACPI:
```

#!/bin/bash

cd /home/your user name
mkdir `uname -r`
cd `uname -r`
bunzip2 -c /usr/src/linux-source-2.6.27.tar.bz2 | tar xp
cd linux-source-2.6.27/
cp /usr/src/linux-headers-`uname -r`/Module.symvers .
cp /usr/src/linux-headers-`uname -r`/Module.symvers arch/x86/kernel/cpu/cpufreq/
patch -p1 < ../../Downloads/phc/linux-phc-0.3.2-kernel-vanilla-2.6.26.patch
rm ./arch/x86/kernel/cpu/cpufreq/*.symvers
make oldconfig
make prepare
make scripts
make M=./arch/x86/kernel/cpu/cpufreq
cp ./arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko ..
cd ..
rm -rf linux-source-2.6.27/

```

installACPI:
```

#/bin/bash
cd /lib/modules/`uname -r`/kernel/arch/x86/kernel/cpu/cpufreq/
rmmod speedstep_centrino
rmmod acpi-cpufreq
mv acpi-cpufreq.ko acpi-cpufreq.ko.orig
mv speedstep-centrino.ko speedstep-centrino.ko.orig
cp /home/your user name/`uname -r`/acpi-cpufreq.ko .
modprobe acpi-cpufreq
/etc/init.d/undervolt start

```

I added the stuff to remove the speedstep-centrino because on my laptop if steedstep-centrino.ko is there it will get loaded instead of acpi-cpufreq and the undervolting does not work.

Run by:
./makeACPI
sudo ./installACPI

Ray

---

### Post by paquito187 on 2009-01-12
Here's the 2.6.28.4 generic 64 bit module

---

### Post by pressureman on 2009-01-23
Module for latest Jaunty kernel, 2.6.28-5-generic (32 bit)

---

### Post by Sacob on 2009-01-23
my values return to the first ones after i reboot. what can i do to solve this problem?

---

### Post by pressureman on 2009-01-24
> **Sacob said:**
> my values return to the first ones after i reboot. what can i do to solve this problem?

Add a line like this to your /etc/rc.local (replace my values with your ones).

```

echo "16:22 14:17 12:12 10:8 8:3 6:1" > /sys/devices/system/cpu/cpu0/cpufreq/phc_controls

```

Make sure you add it before the "exit 0" line at the end of rc.local.

---

### Post by Sacob on 2009-01-26
i did the 

```
echo "13:24 10:1 8:1 6:1" > /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
```

and the result of the

>  cat /sys/devices/system/cpu/cpu0/cpufreq/phc_controls

is indeed "13:24 10:1 8:1 6:1". the problem is that after i reboot this values return to the first ones


ps: sorry for my bad english

---

### Post by seish on 2009-01-27
> **paquito187 said:**
> Here's the 2.6.28.4 generic 64 bit module


EDIT: Nvm just googled and found the new kernel for ubuntu.

---

### Post by seish on 2009-01-27
How can I find/compile a module for kernel 2.6.28 64 bit ?

The precompiled module for 64 bit posted on page 30 doesn't work. Also the links in the guide are broken and the guide is kinda outdated to be useful now. Not to mention I can't find the linux PHC website anywhere. 
Either I'm really clueless or noone cares about undervolting anymore.

I want to use the new kernel, but I can't unless I get this working.

---

### Post by Ev1L on 2009-01-28
> **Sacob said:**
> i did the 

```
echo "13:24 10:1 8:1 6:1" > /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
```

and the result of the



is indeed "13:24 10:1 8:1 6:1". the problem is that after i reboot this values return to the first ones


ps: sorry for my bad english
did you just wrote that command in the console or actually put it in rc.local?
the second is supposed to be permanent, and i couldn't figure out why it would be reset at reboot

---

### Post by marcelorider on 2009-01-28
easy way to undervolt a speedstep centrino is

opening blacklist list and add blacklist speedstep_centrino (if im not wrong)

then simply replace the acpi kernel for the modified :P
and put boot command or what u guys whant :P

the 32bits patch for kernel 2.6.27.11-generic on page 29 works like sharm :)

good undervolting :)

original topic need update for new kernels

ohh i forgot its the 3th time i undervolt my laptop sucessfully with this topic

---

### Post by pressureman on 2009-01-28
> **Ev1L said:**
> did you just wrote that command in the console or actually put it in rc.local?
the second is supposed to be permanent, and i couldn't figure out why it would be reset at reboot

I wrote that you should add the line to /etc/rc.local (since that gets executed upon booting). Also, you should replace my values with the ones that the script determined for your CPU. It's unlikely that your values will be the same as mine, unless we have identical CPUs.

---

### Post by Sacob on 2009-01-28
> **Ev1L said:**
> did you just wrote that command in the console or actually put it in rc.local?
the second is supposed to be permanent, and i couldn't figure out why it would be reset at reboot

i only wrote this line in the console, as it was in the tutorial

didn't understand the rc.local thing

---

### Post by Ev1L on 2009-01-29
> **pressureman said:**
> I wrote that you should add the line to /etc/rc.local (since that gets executed upon booting). Also, you should replace my values with the ones that the script determined for your CPU. It's unlikely that your values will be the same as mine, unless we have identical CPUs.
I am not the one asking for help, I was not sure Sacob understood your point on adding to rc.local.

Now I guess he did :)

---

### Post by pressureman on 2009-01-29
> **Ev1L said:**
> I am not the one asking for help, I was not sure Sacob understood your point on adding to rc.local.

Now I guess he did :)

Ooops... sorry #-o

Must be the sleep deprivation and constant travelling.

---

### Post by pressureman on 2009-01-29
Module for latest Jaunty kernel, 2.6.28-6-generic (32 bit)

---

### Post by m4cph1sto on 2009-01-29
I have a speedstep-centrino Pentium M.  Interestingly, when I switch to the PHC- modded acpi-cpufreq, and undervolt, my CPU temp actually increases, and consumes MORE power.  So I have a request:

Can anyone compile a PHC modded speedstep-centrino.ko for Ubunto kernel 2.6.27-11-generic? I've tried myself but couldn't quite get it to work, and now it seems the Linux-PHC website is down.  So if someone has downloaded the patch for speedstep-centrino that was posted on Linux-PHC - it is also posted and still available here: 

[http://ubuntuforums.org/showthread.php?t=970662](http://ubuntuforums.org/showthread.php?t=970662)

and can spend a few minutes to compile the module for this most recent kernel, I would greatly appreciate it!

---

### Post by Ev1L on 2009-01-30
> **m4cph1sto said:**
> I have a speedstep-centrino Pentium M.  Interestingly, when I switch to the PHC- modded acpi-cpufreq, and undervolt, my CPU temp actually increases, and consumes MORE power.  So I have a request:

Can anyone compile a PHC modded speedstep-centrino.ko for Ubunto kernel 2.6.27-11-generic? I've tried myself but couldn't quite get it to work, and now it seems the Linux-PHC website is down.  So if someone has downloaded the patch for speedstep-centrino that was posted on Linux-PHC - it is also posted and still available here: 

[http://ubuntuforums.org/showthread.php?t=970662](http://ubuntuforums.org/showthread.php?t=970662)

and can spend a few minutes to compile the module for this most recent kernel, I would greatly appreciate it!
have you tried the couple already compiled that are present in this thread?
by the way i experienced a little increase in temp too, but i suspect that it was cause i was doing almost nothing when i was without PHC

---

### Post by m4cph1sto on 2009-02-01
I can't find any patched speedstep-centrino.ko posted in this thread. Compiling my own results in a fully functioning speedstep-centrino module, but generates no phc files in /sys/devices/system/cpu/cpu0/cpufreq/, so the undervolting part isn't working.  Switching to acpi-cpufreq and following the method in the first post of this thread seems to work fine, however I'm not seeing any temperature decrease or power saving with acpi-cpufreq and undervolting (in fact if anything it's worse), which is why I wanted to try patching speedstep-centrino instead.  

Maybe I'm just asking too much, since speedstep-centrino is only for older hardware, it doesn't make sense to devote much time in getting this to work. But it would sure be nice for people with older laptops, like me :)

---

### Post by pressureman on 2009-02-09
Module for latest Jaunty kernel, 2.6.28-7-generic (32 bit)

---

### Post by wubi-user on 2009-02-14
> **marcelorider said:**
> easy way to undervolt a speedstep centrino is

opening blacklist list and add blacklist speedstep_centrino (if im not wrong)

then simply replace the acpi kernel for the modified :P
and put boot command or what u guys whant :P

the 32bits patch for kernel 2.6.27.11-generic on page 29 works like sharm :)

good undervolting :)

original topic need update for new kernels

ohh i forgot its the 3th time i undervolt my laptop sucessfully with this topic

that's great to know, marcelorider.  I'm a complete novice with linux, but i'm ready to make the switch from windows if I could get the undervolting done.  But this is by far the hardest thing I've come across so I would love to get all the help i can.  My notebook has a Pentium M 740 and I know that it is currently running speedstep_centrino.  My kernel is 2.6.27.11 and I know there are tutorials around that teach my how to do it, BUT this whole **blacklisting** business isn't covered. Any advice is welcomed.  Thanks.

---

### Post by Mizzou_Engineer on 2009-02-14
> **wubi-user said:**
> that's great to know, marcelorider.  I'm a complete novice with linux, but i'm ready to make the switch from windows if I could get the undervolting done.  But this is by far the hardest thing I've come across so I would love to get all the help i can.  My notebook has a Pentium M 740 and I know that it is currently running speedstep_centrino.  My kernel is 2.6.27.11 and I know there are tutorials around that teach my how to do it, BUT this whole **blacklisting** business isn't covered. Any advice is welcomed.  Thanks.

Here's how to blacklist a module:

1. Hit Alt-F2 to bring up the "Run Application" dialog.

2. Type in "gksudo gedit" (less quotes) to run GEdit as root.

3. Open /etc/modprobe.d/blacklist with GEdit.

4. Scroll down to the end of the list.

5. Type in "blacklist speedstep_centrino" (less quotes) to blacklist speedstep_centrino.

6. Save and close GEdit.

That should do it. 

Note: If you are a CLI guy like I am, just open /etc/modprobe.d/blacklist as root with your favorite text editor and add "blacklist speedstep_centrino" at the end.

---

### Post by primus454 on 2009-02-14
Okay, I finished step two and rebooted. Everything came up fine, but I lost my internet. I reinstalled my / drive because I can't live without internet. Any insight as to why that happened and how to fix it? I'm running Intrepid 64 on a 64bit machine. I'm running 2.6.27-11-generic.

---

### Post by vasiauvi on 2009-02-15
Hello all,
I have read almost all this thread and I've tried to run the scripts.
As I understood from the first page after installing PHC controls with this command :
```
cat /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
``` I can see the default values. Then, my default values appeared to be:
```
**14:1** 12:36 10:32 8:28 6:25
```
First 14:1 means that by default my CPU is set on the lowest voltage???
After running the script in parallel with burnMMX this is the output:
```

Default VIDs: 40 36 32 28 25 
Current VIDs: 39 36 32 28 25
Testing VID: 39 (1324 mV)
..........
Default VIDs: 40 36 32 28 25 
Current VIDs: -1 36 32 28 25
Testing VID: -1 (684 mV)
./linux-phc-optimize.bash: line 161: printf: -1: invalid option
printf: usage: printf [-v var] format [arguments]


The lowest acceptable VID is 0.

Recovering CPU.
./linux-phc-optimize.bash: line 138: 10115 Terminated              burnMMX

Run this script again to continue the optimization.
paula@paula:~/Documents$ sudo ./linux-phc-optimize.bash

 I assume you have linux-phc correctly installed and working.
 This script will optimize your voltages at every speed setting by
systematically lowering them while stressing the CPU.
 Each voltage will be turned down until your system crashes, and the final
setting for that voltage will be 2 VIDs above that to "ensure" stability.

WARNING:
This script will crash your system as many times as there are VIDs to tweak.
You might destroy your hardware, break laws and/or die in vain if you continue.

Do you want to continue? [Y/n/?] Yes

Install required packages.
Will use burnMMX (part of cpuburn package) to stress CPU.
Install: cpuburn
> SKIPPED: Already installed


Will use current directory to store/retrieve test results.

Read phc_default_vids:
> Success!

Load VIDs from 'phc_tweaked_vids'
> ERROR: Wrong VID count!

```
I don't understand what is wrong or if it's something wrong.
My CPU temp is between 52 and 62 degrees C.
I am missing something???
Thank you in advance!!!

---

### Post by vasiauvi on 2009-02-15
OK, today i have tried all the possibilities but i think that the undervoltage doesn't work.Now i've put 14:25 12:25 10:25 8:25 6:25 and the temperature is the same.I have installed PHCtool i have used the script but nothing.I have Intel Duo T2130 on ASUS laptop.
In /etc/rc.local i've put:
```

echo "14:1 12:19 10:19 8:19 6:19" > /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
echo "14:1 12:19 10:19 8:19 6:19" > /sys/devices/system/cpu/cpu1/cpufreq/phc_controls

```
When i run the script the laptop doesn't hung up or freeze.
I've give up, time spend for nothing!!:(:confused:

Although this forum and the community is GREAT!!!!

---

### Post by mister_playboy on 2009-02-17
> **jcm4 said:**
> ```

cd /home/"your-username"/"kernelversion"
patch -p1 < linux-phc*.patch
make oldconfig
make prepare
make scripts
make M=./arch/x86/kernel/cpu/cpufreq

```

What am I doing wrong in this? My directory is correct.

john@john-laptop:~/2.6.27-9-generic$ patch -p1 < linux-phc*.patch
can't find file to patch at input line 4
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff --new-file -a --unified=5 --recursive  linux-source-2.6.26-rc9_orig/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.c linux-source-2.6.26-rc9-custom8/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.c
|--- linux-source-2.6.26-rc9_orig/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.c	2008-07-09 16:59:37.000000000 +0200
|+++ linux-source-2.6.26-rc9-custom8/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.c2008-07-09 12:41:37.000000000 +0200
--------------------------
File to patch:

I'm getting the exact same problem... trying to compile for 2.6.28-8 64bit kernel.

Thanks to this thread, I had undervolting working perfectly with 2.6.27-11, but I'm trying out the new kernel to improve my folding@home SMP performance.

---

### Post by mister_playboy on 2009-02-17
Nevermind, digging through the whole thread solved my problem.

I was having trouble since I hadn't downloaded the linux-headers package for my new kernel.

Thanks for all the guidance! :) Here is the fruit of my labors:

---

### Post by pressureman on 2009-02-17
Module for latest Jaunty kernel, 2.6.28-8-generic (32 bit)

---

### Post by nigelhealy on 2009-02-17
So I spent hours on this. I have Ubuntu 8.10 AMD64 o a Thinkpad T60. I was looking at undervolting to reduce heat and therefore the fan and therefore quieter and some hope of better battery. This having used laptop_mode and powertop tips.

On wifi, screen on a low brightness, am getting about 3.5 hours, down from 2 hours before I tried all the tweaks going.

This underclocking guide the scripts simply would not work. The pre-compiled modules and the instructions to replace existing did work, but I had to use the phctool to manually trial+error find the lowest reliable VID for each of my 5 clock frequency.

I would like to get over 4 hours of battery. I notice the laptop spends about 98% of its time in the lowest clock.

---

### Post by XRayA4T on 2009-02-18
Here is Intrepid 2.6.27-12 32-bit

---

### Post by pressureman on 2009-02-19
Patching the acpi-cpufreq module just got a little bit harder in Jaunty. As of 2.6.28-8.24, the CPU frequency scaling modules are built in to the kernel, meaning that we can no longer just patch and overwrite an individual module.

---

### Post by Mizzou_Engineer on 2009-02-19
> **pressureman said:**
> Patching the acpi-cpufreq module just got a little bit harder in Jaunty. As of 2.6.28-8.24, the CPU frequency scaling modules are built in to the kernel, meaning that we can no longer just patch and overwrite an individual module.

It's not that big of a deal to change, though. The kernel source patching procedure is the same, although you will need to recompile the entire kernel and move the kernel bzImage to /boot rather than compiling the acpi_cpufreq.ko module and moving it to /lib/modules/. It's not that much more difficult and given that the acpi_cpufreq driver only supports newer CPUs, compile time ought not to be all that ridiculous either.

---

### Post by gmc on 2009-02-19
Aww now that just sucks. Well I guess I'll just have to get off my lazy butt and start custom compiling my own kernel for my AAO-150.

I wonder why the change from module to internal, or if it was just an oversight.

G.

---

### Post by pressureman on 2009-02-19
I've been running the unpatched kernel for a few hours now, and I can't honestly say I've noticed any difference. This is a pretty old laptop, and the battery is completely shot anyway, so it only gets about 25 mins runtime. For me, patching the module was never about increasing battery runtime.

As far as temperature however, it's about the same, and the fan pretty much always ran non-stop anyway. I think the graphics chipset is reponsible for most of the heat (ATI Radeon Mobility 9700).

This really just hastens my decision to get a new laptop with better cooling.

---

### Post by Ev1L on 2009-02-19
> **Mizzou_Engineer said:**
> It's not that big of a deal to change, though. The kernel source patching procedure is the same, although you will need to recompile the entire kernel and move the kernel bzImage to /boot rather than compiling the acpi_cpufreq.ko module and moving it to /lib/modules/. It's not that much more difficult and given that the acpi_cpufreq driver only supports newer CPUs, compile time ought not to be all that ridiculous either.
Well, I cannot say that download and recompile the kernel everytime is anything comparable to get the update automatically from update manager, grab the library from here, and replace the old one.

There is always someone here recompiling the new module and sharing it, now it's pointless, and everyone has to do the long and annoying procedure himself.

I'd like to know the reason of this change, and I hope there will be a more comfortable workaround.
Actually, I was also wondering why kernels and phc don't come together.

---

### Post by Mizzou_Engineer on 2009-02-19
> **Ev1L said:**
> Well, I cannot say that download and recompile the kernel everytime is anything comparable to get the update automatically from update manager, grab the library from here, and replace the old one.

There is always someone here recompiling the new module and sharing it, now it's pointless, and everyone has to do the long and annoying procedure himself.

I'd like to know the reason of this change, and I hope there will be a more comfortable workaround.
Actually, I was also wondering why kernels and phc don't come together.

I was always compiling my own modules, since I was also trying to use the Broadcom wl driver as well (which required a very similar procedure.) Maybe somebody could write a script that would do the necessary actions all in one shot...

---

### Post by evgeny1978 on 2009-02-20
64 bit acpi-cpufreq.ko for 2.6.27-12-generic

---

### Post by gmc on 2009-02-22
Not having a whole lot of luck here. I've downloaded and applied linux-phc-0.3.2-kernel-vanilla-2.6.26.patch to the current Jaunty kernel (2.6.28-8-generic #24). 

Applying the patch didn't report any error's but I'm not able to get the module to compile.  but get the following:

```

:~/src/linux-source-2.6.28$ make M=./arch/x86/kernel/cpu/cpufreq

  WARNING: Symbol version dump /home/gord/src/linux-source-2.6.28/Module.symvers
           is missing; modules will have no dependencies and modversions.

  LD      arch/x86/kernel/cpu/cpufreq/built-in.o
ld: no input files
make[1]: *** [arch/x86/kernel/cpu/cpufreq/built-in.o] Error 1
make: *** [_module_./arch/x86/kernel/cpu/cpufreq] Error 2

```Am I missing something somewhere?

G.

---

### Post by Mizzou_Engineer on 2009-02-22
> **gmc said:**
> Not having a whole lot of luck here. I've downloaded and applied linux-phc-0.3.2-kernel-vanilla-2.6.26.patch to the current Jaunty kernel (2.6.28-8-generic #24). 

Applying the patch didn't report any error's but I'm not able to get the module to compile.  but get the following:

```

:~/src/linux-source-2.6.28$ make M=./arch/x86/kernel/cpu/cpufreq

  WARNING: Symbol version dump /home/gord/src/linux-source-2.6.28/Module.symvers
           is missing; modules will have no dependencies and modversions.

  LD      arch/x86/kernel/cpu/cpufreq/built-in.o
ld: no input files
make[1]: *** [arch/x86/kernel/cpu/cpufreq/built-in.o] Error 1
make: *** [_module_./arch/x86/kernel/cpu/cpufreq] Error 2

```Am I missing something somewhere?

G.

Look at message #323 in this thread- the module is compiled into the kernel and unable to be patched. Plus, you need to grab Module.symvers out of the kernel headers folder and put it in the linux-source folder, else you won't be able to insert any module you would have compilied.

---

### Post by mister_playboy on 2009-02-22
> **Mizzou_Engineer said:**
> Plus, you need to grab Module.symvers out of the kernel headers folder and put it in the linux-source folder, else you won't be able to insert any module you would have compilied.

That was the problem I had originally, but in my haste I forgot to post the fix (which is very simple).  :)

---

### Post by Dark_vampel on 2009-02-23
I'm having problems after copying the module into the kernel. I copied the correct module for the 2.6.24-19-generic. I reboot then try to run the cat command but then I get an error saying the device does not exist. Where could I have made a mistake or is my processor not supported? It is a pentinium 4.

---

### Post by matmat07 on 2009-02-24
Could someone make me a 64 bit 2.6.27-9 one? I tried but something went wrong and I had to reinstall the kernel.

---

### Post by matmat07 on 2009-02-26
nvm, I found one while searching in this thread

---

### Post by Yink on 2009-03-03
I hate to sound ignorant but does this mean for 2.6.27-13-generic I will need to download the kernel source and apply a patch to it, or is the module been moved inside the kernel on the next Ubuntu version ?

Sorry if my question is n00bish.

---

### Post by zcats on 2009-03-04
Thanks.  Undervolting has been a fantastic for reducing temperature and fan noise....
Can someone please post 32 bit for 2.6.27-13?:P

Would be really useful if all these .ko files could be tabulated or a sticky made with links to all the downloads...takes ages looking for the right .ko for the kernel.
Will try the 2.6.27-12.ko and see if it works with 2.6.27-13 in the meantime (guess I will have to learn to compile my own one day soon!)

Thanks
zcats

---

### Post by alkis on 2009-03-10
Intrepid 2.6.27-13 64 bit

---

### Post by XRayA4T on 2009-03-11
Here is Hardy 2.6.27-13-generic-32bit

---

### Post by Yink on 2009-03-11
Thanks a lot!

---

### Post by zcats on 2009-03-14
Thanks! The 2.6.27-13-generic 32 bit worked fine for me.

NB
In the instructions (1st page) for ubuntu you do need to run
>sudo -s
before you change the voltages with
>echo "17:15 14:9 12:28 10:5 8:1 6:1" > /sys/devices/system/cpu/cpu0/cpufreq/phc_controls

Also, I have T42 Thinkpad laptop with 2 gig RAM.This was a bit wierd...
17:36 14:32 12:28 10:25 8:22 6:18 original vids
17:15 14:9 12:5 10:1 8:1 6:1 optimal as tested after sudo ./linux-phc-optimize.bash.
But thinkwiki recommends
17:19 14:12 12:8 10:4 8:1 6:1 

......but in the end I settled for 17:15 14:9 12:28 10:5 8:1 6:1 because I had some stability issues.  This is one of the best tweaks for cooling laptop and the fan running at high speed often.  My laptop used to be a gasping beast with the fan belting a lot of the time and the cpu temps going abobe 80 celcius (yikes! but the Pentium M can take more than 100 celcius..amazing but I do not like it). After this undervolt, I can max out this laptop, its stable and temps are usually less than 60 celsius with the fan off or at 10%.  Cool Thinkpad fan control was also useful, but the undervolting sorted out the excessive heat production and made it just cool:P

When will this get into the kernel? no danger of UNDERvolting right? So lets have it inbuilt into the vanilla please

---

### Post by shadeslayer on 2009-03-14
hey guys,amazing guide...... but after a reboot the values return to the default one's.
Mine are : 75:40 74:34 8:28 6:23 136:15 <--after Reboot
           75:31 74:34 8:28 6:23 136:15 <--before running scripts
           75:36 74:34 8:1 6:1 136:1    <--what the script gives me

I have a T8100 on my XPS M1530,and the thing runs wayyyy to hot to sit on my lap.A urgent fix required please!!! :) 
Thanks in advance

Kernel : 2.6.27-13 64 bit

---

### Post by Mizzou_Engineer on 2009-03-14
> **shadeslayer said:**
> hey guys,amazing guide...... but after a reboot the values return to the default one's.
Mine are : 75:40 74:34 8:28 6:23 136:15 <--after Reboot
           75:31 74:34 8:28 6:23 136:15 <--before running scripts
           75:36 74:34 8:1 6:1 136:1    <--what the script gives me

I have a T8100 on my XPS M1530,and the thing runs wayyyy to hot to sit on my lap.A urgent fix required please!!! :) 
Thanks in advance

Kernel : 2.6.27-13 64 bit

The phc_controls get reset to default when the computer reboots. I just set up a script that echoes the desired undervolting values and run it after reboot.

---

### Post by shadeslayer on 2009-03-15
> **Mizzou_Engineer said:**
> The phc_controls get reset to default when the computer reboots. I just set up a script that echoes the desired undervolting values and run it after reboot.

So that means that either i set up my own script or i echo the values each time i login? That well kinda sucks if you are a average user and have just started to use ubuntu.Cant i have something that starts up automatically on boot(during the load period) to echo the new values??

---

### Post by Mizzou_Engineer on 2009-03-15
> **shadeslayer said:**
> So that means that either i set up my own script or i echo the values each time i login? That well kinda sucks if you are a average user and have just started to use ubuntu.Cant i have something that starts up automatically on boot(during the load period) to echo the new values??

Yes, you can. Put the (executable) script in /etc/rc.d and then do a "sudo /usr/sbin/update-rc.d $SCRIPT_NAME defaults" to have it set the PHC controls at boot. 

If you need a hand in doing this, just say so.

---

### Post by shadeslayer on 2009-03-16
> **Mizzou_Engineer said:**
> Yes, you can. Put the (executable) script in /etc/rc.d and then do a "sudo /usr/sbin/update-rc.d $SCRIPT_NAME defaults" to have it set the PHC controls at boot. 

If you need a hand in doing this, just say so.

yep,ill need all the help i can :D ,could you possibly post step by step instructions and the script i would need??

---

### Post by zcats on 2009-03-17
Changes will be lost on reboot unlees you add YOUR values to  your /etc/rc.local file to make permanent (no script needed just add few lines to /etc/rc.local so it looks like that below (replace vids with your optimal values).  Values stay after new kernel upgrade (PHC patched)...
>sudo gedit /etc/rc.local 

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
echo "17:19 14:12 12:18 10:4 8:1 6:1" > /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
exit 0

[http://ubuntuforums.org/showthread.php?t=786402&highlight=phc](http://ubuntuforums.org/showthread.php?t=786402&highlight=phc)

---

### Post by XRayA4T on 2009-03-23
It appears that with Jaunty the ACPI stuff is now in the kernel rather than in a module which requires you to patch and build the kernel. Having never done this before I decided to take the plunge and give it a go! I followed the instructions here [http://beginlinux.wordpress.com/2008/12/03/how-to-compile-an-ubuntu-810-kernel/](http://beginlinux.wordpress.com/2008/12/03/how-to-compile-an-ubuntu-810-kernel/) and it was pretty straight forward if time consuming.

I have created a script to simplify the process. Create a folder where you have write access. Put the following script in that folder, buildKernel:
```

#!/bin/sh
if [ "$1" = "" ]; then
echo "Usage: $N {version number}" >&2;
		exit 1;
fi
start=`date`
echo "Started : $start"
bunzip2 -c /usr/src/linux-source-2.6.28.tar.bz2 | tar xp
cd linux-source-2.6.28
cp /boot/config-`uname -r` ./.config 
patch -p1 < ../linux-phc-0.3.2-kernel-vanilla-2.6.26.patch
make-kpkg clean
fakeroot make-kpkg --initrd --append-to-version=-rb${1} kernel_image kernel_headers
cd ..
rm -rf linux-source-2.6.28
echo "Started : $start"
echo "Ended   : `date`"

```
You can replace the rb in --append-to-version=-rb${1} with your initials. You can then make it executable and run it as "buildKernel 2" where 2 is the version number you want to assign. 

It takes up about 4GB during the build process (which the last line in the script deletes) to build the 2 deb packages which are about 300MB. The build took about 2 hours on my machine. You can then install the 2 packages and use the undervolting as you did when it was a module.

Hope this helps
Ray

---

### Post by Ev1L on 2009-03-23
I am not expert enough, so I ask again.
Are you sure that for something so useful as phc there isn't a way to install it seamlessly like any package from apt?

could someone quickly explain me a bit the logic before the new kernel and the current one?
and maybe also why change something requiring everyone to recompile a kernel instead of just a module?

thanks

---

### Post by Ares Drake on 2009-03-24
> **Ev1L said:**
> I am not expert enough, so I ask again.
Are you sure that for something so useful as phc there isn't a way to install it seamlessly like any package from apt?

could someone quickly explain me a bit the logic before the new kernel and the current one?
and maybe also why change something requiring everyone to recompile a kernel instead of just a module?

thanks


Well in theory you could compile your own phc-enabled kernel into a *.deb and distribute it via apt, i guess. Unfortunately I am a) no kernel expert and b) still using Hardy, so I am probably of little help in that matter for now.

---

### Post by Ev1L on 2009-03-24
well, i read the discussion on phc forum, i hope they'll come up with a nice, clean and easy solution.
i could really stop using phc if i should recompile the kernel everytime, i kinda like ubuntu telling me that there is a new kernel and installing it for me :)
quickly reinstall phc, asus stuff, virtual box and vmware was still acceptable, but the whole kernel...

i hope not :)

---

### Post by juanmoreno92 on 2009-03-29
Any word on support for dual cores yet? My Pentium Dual Core Toshiba Satellite can cook a T-bone in about 2 min. right now.

---

### Post by kabaiz on 2009-03-31
Thanks for the great script! I hope it will work for me, too.

Before compiling I have some questions:

Is that a 32 or 64 bit system? Can you tell us the properties of your processor?

Is there a difference between patching a 32 bit or a 64 bit kernel?

Have a nice day :)

Zoltan

---

### Post by Supermattt on 2009-04-01
Am I totally Crazy or the acpi_cpufreq is hardcoded in last jaunty  2.6.28-11 kernel? :confused:

```
matt@merom:~ $ uname -r
2.6.28-11-generic
matt@merom:/lib/modules/2.6.28-11-generic/kernel/arch/x86/kernel/cpu/cpufreq $ ls
e_powersaver.ko  p4-clockmod.ko


root@merom:~ # lsmod |grep acpi
root@merom:~ # lsmod |grep cpu
root@merom:~ # 



```

---

### Post by pressureman on 2009-04-01
It's compiled in now. This was discussed earlier in this rather epic thread.

```
pressureman@thinkpad:~$ egrep "CPUFREQ|POWERNOW|SPEEDSTEP" /boot/config-2.6.28-11-generic 
CONFIG_X86_ACPI_CPUFREQ=y
# CONFIG_X86_ACPI_CPUFREQ_PROC_INTF is not set
CONFIG_X86_CPUFREQ_NFORCE2=y
CONFIG_X86_POWERNOW_K6=y
CONFIG_X86_POWERNOW_K7=y
CONFIG_X86_POWERNOW_K7_ACPI=y
CONFIG_X86_POWERNOW_K8=y
CONFIG_X86_POWERNOW_K8_ACPI=y
CONFIG_X86_SPEEDSTEP_CENTRINO=y
CONFIG_X86_SPEEDSTEP_CENTRINO_TABLE=y
CONFIG_X86_SPEEDSTEP_ICH=y
CONFIG_X86_SPEEDSTEP_LIB=y
CONFIG_X86_SPEEDSTEP_RELAXED_CAP_CHECK=y
CONFIG_X86_SPEEDSTEP_SMI=y

```

---

### Post by Supermattt on 2009-04-04
I created a thread about the hard-coded thing in idea's box, hope someone will read it !

If you want to add comments ->
[http://ubuntuforums.org/showthread.php?p=7010930#post7010930](http://ubuntuforums.org/showthread.php?p=7010930#post7010930)

---

### Post by nick_edwards on 2009-04-09
I'm loosing my mind, 
I've followerd this guide before and it worked great but now upgraded kernel and I need to compile the module again, I remember I had trouble last time with this same step but ca't remember what I did:

basically I can't > copy /boot/config-$(uname -r).config to /home/"your-username"/"kernelversion" as I don't have that file???????

> root@amd64:/boot# ls /boot/config-$(uname -r).config
ls: cannot access /boot/config-2.6.27-14-generic.config: No such file or directory


even though:

> root@amd64:/boot# apt-get install build-essential linux-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
linux-source is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


WTF???? am I being a retard here or has something changed??

---

### Post by nick_edwards on 2009-04-10
ok ignore my last post, I followed the how to on the PHP website and got it compiled and installed..

now....

I don't think it's working... 

running 2 x burnMMX on my dell M1330 gets the temperature well over 90 degrees in very little time. :oops:

>  cat /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
13:25 12:15 10:1 8:1 6:1 136:1 


which is the same values I used to use and they used to work very well temperature wouldn't rise much over 70 with the same test. 

I'm using x86 ubuntu 8.10 with the 2.6.27-14-generic kernel - anyone had any luck with it? want to post me your compiled module?? anyone want my compiled module?

any help is greatly appreciated, these things tend to screw with my sanity far more than they should.](*,)

---

### Post by Sianis on 2009-04-11
Hello!

I'm running Intrepid Ibex with 2.6.27-11-generic on a T61 with T8300 Core 2 Duo.

I run the script with two burnMMX.

The script (after 6 system crash) give me this:

```

cat phc_tweaked_vids
23 23 1 1 1 1

```

My default phc_control file is:
```

cat /sys/devices/system/cpu/cpu0/cpufreq/phc_controls 
13:40 12:34 10:31 8:27 6:23 136:17

```

So my new phc_control file should be:
```

13:23 12:23 10:1 8:1 6:1 136:1

```

But this version crash my system randomly. What is the problem?
Thanks for your help!

---

### Post by Ev1L on 2009-04-11
maybe it was too undervolted for some reason.
you could try the test again maybe

---

### Post by Pluies on 2009-04-11
About the following error while running **linux-phc-optimize.bash** :

> 
(...)
Default VIDs: 34 28 21 15 
Current VIDs: [COLOR="Red"]1[/COLOR] 28 21 15
Testing VID: 1 (716 mV)
..............................
Default VIDs: 34 28 21 15 
Current VIDs: [COLOR="Red"]0[/COLOR] 28 21 15
Testing VID: 0 (700 mV)
..............................
Default VIDs: 34 28 21 15 
Current VIDs: [COLOR="Red"]-1[/COLOR] 28 21 15
Testing VID: -1 (684 mV)
./linux-phc-optimize.bash: line 161: printf: -1: invalid option
printf: usage: printf [-v var] format [arguments]


The lowest acceptable VID is 0.

Recovering CPU.
pkill: 11249 - Operation not permitted
./linux-phc-optimize.bash: line 138:  9516 Terminated              burnMMX

Run this script again to continue the optimization.
**pluies@pluies-laptop ~/phctools $** ./linux-phc-optimize.bash 

 I assume you have linux-phc correctly installed and working.
 This script will optimize your voltages at every speed setting by
systematically lowering them while stressing the CPU.
 Each voltage will be turned down until your system crashes, and the final
setting for that voltage will be 2 VIDs above that to "ensure" stability.

WARNING:
This script will crash your system as many times as there are VIDs to tweak.
You might destroy your hardware, break laws and/or die in vain if you continue.

Do you want to continue? [Y/n/?] [COLOR="Green"]Yes[/COLOR]

Install required packages.
Will use burnMMX (part of cpuburn package) to stress CPU.
Install: [COLOR="Green"]cpuburn[/COLOR]
[COLOR="RoyalBlue"]> SKIPPED:[/COLOR] Already installed


Will use current directory to store/retrieve test results.

Read phc_default_vids:
[COLOR="Green"]> Success![/COLOR]

Load VIDs from 'phc_tweaked_vids'
[COLOR="Red"]> ERROR:[/COLOR] Wrong VID count!



It seems like there's a bug when your processor is *too good* and can run without crashing at a very low vid (typically, at a VID of 0).

One workaround is to modify line 161 of the linux-phc-optimize.bash script.
Replace:
```
while [[ 1 ]]; do
```
By:
```
while [[ vid[cur_pos] -ge 1 ]]; do
```

It will prevent the tool from trying to set VIDs lower than 1.

You will then have to delete **phc_cur_pos** and **phc_tweaked_vids** (the two files where the bash script saves its VIDs); then relaunch the script... Ta-dam. Worked perfectly fine here. :)

---

### Post by Sianis on 2009-04-11
Ok. So I created an other test. Results are same. BUT. My system crashes when it want to change the cpu scale, frequency. It is stable on the fixed frequency, but changing crashes it. Have you ever this problem. What could this be?

Thank you!

---

### Post by Pluies on 2009-04-11
> **Sianis said:**
> Ok. So I created an other test. Results are same. BUT. My system crashes when it want to change the cpu scale, frequency. It is stable on the fixed frequency, but changing crashes it. Have you ever this problem. What could this be?

Thank you!

I don't know about you, but on my install, phc-intel doesn't seem to actually modify the VIDs. It may explain why the processor is able to run this low during the script without any problem.

I think the best solution so far is to set voltage manually (using PHCTools). Not very practical, but it should work better.



[COLOR="Red"]Edit:[/COLOR] hehe. I just understood my problem.

My default VIDs are (in /sys/devices/system/cpu/cpu0/cpufreq/phc_default_vids ):
```
pluies@pluies-laptop ~/Desktop $ cat /sys/devices/system/cpu/cpu0/cpufreq/phc_default_vids 
34 28 21 15 

```
My available frequencies are:
```
pluies@pluies-laptop ~/Desktop $ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies 
1600000 1400000 1200000 800000 

```

So, when I try to set a VID lower than 15... PHC will never reach it; and will stop at 15, which is the **default lowest VID of my lowest frequency** (in my case, 800Mhz). Let's call it "EXTRAMINVID".

My tests so far showed that **you can't set a VID inferior to this value**. For each frequency, every value between your default value for this frequency and EXTRAMINVID are possible though. :)


I just set all my voltages at 15 using PHCTools. Now, for every frequency, VID is always 15. Even at max frequency (1,6Ghz).

I'm letting burnMMX run a bit to see if it is stable and let you know.

---

### Post by Mizzou_Engineer on 2009-04-11
> **Pluies said:**
> 

My tests so far showed that **you can't set a VID inferior to this value**. For each frequency, every value between your default value for this frequency and EXTRAMINVID are possible though. :)


That is correct. Intel does not let you set a voltage lower than the default voltage at the lowest frequency for your particular CPU. This voltage will lie between the upper and lower boundaries of Vcc_LFM (Intel chips on 945 and older chipsets) or Vcc_SLFM (Intel chips on 965 and newer chipsets) and can be different for each individual CPU. But whatever this lowest VID is, you cannot set any VID for any frequency below this value. This is also true for AMD desktop chips- you cannot set the voltage lower than the voltage when the chip is at its idle speed (which generally is 0.9-1.1 volts, depending on model.)

AMD laptop chips are a different story. You can lower the VIDs on those guys well below the pre-defined idle VID for any FID, as long as the CPU remains stable. I think my wife's Mobile Sempron 3600+ that normally idles at about 950 mV has VIDs unlocked to something like 0.5625 volts or something crazy like that.

---

### Post by mister_playboy on 2009-04-24
It appears that 19 is the lowest acceptable setting for many Intel Core 2 Duos and Pentium Dual-cores.  I was having the same problem with the script going to 0 or -1.  I just set 19's across the board and every thing is fine.

If you have one of these chips, give this setting a try.

---

### Post by ivanhoe1024 on 2009-04-24
Ehi guys, I've got a big problem with jaunty... I read that I have to recompile the whole kernel, and I did it, with no errors, but... I have not enough free disk space!! In the root partition I've got about 5 gb free, but when the pc create the kernel image, it is full... I reached now 6,2 gb free, are they enough? How can I do?? Any Ideas?? ps. sorry for my english, I'm italian :P
I've got another partition, bigger that that, which I use for the Home directory, but I think I can't use that free space, can I??

If someone posts online the kernel-image and the kernel-headers packages with the mod indicated in the original phc site, everybody who use the default kernel and the phc patch could download and use it... Is there someone who wants to became a hero???

---

### Post by evgeny1978 on 2009-04-27
You can download recompiled kernel 64-bit version for jaunty with "ACPI Processor P-States driver" as a module at [ftp://129.93.36.1/linux-headers-2.6.28.9-phc001_2.6.28.9-phc001-10.00.Custom_amd64.deb](ftp://129.93.36.1/linux-headers-2.6.28.9-phc001_2.6.28.9-phc001-10.00.Custom_amd64.deb) and [ftp://129.93.36.1/linux-image-2.6.28.9-phc001_2.6.28.9-phc001-10.00.Custom_amd64.deb](ftp://129.93.36.1/linux-image-2.6.28.9-phc001_2.6.28.9-phc001-10.00.Custom_amd64.deb) (I followed instructions at [http://www.linux-phc.org/forum/viewtopic.php?f=13&t=67](http://www.linux-phc.org/forum/viewtopic.php?f=13&t=67) and [http://www.linux-phc.org/forum/viewtopic.php?f=13&t=2](http://www.linux-phc.org/forum/viewtopic.php?f=13&t=2) for phc-intel-0.3.2-4.tar.gz file. By the way this is actually 2.6.28.11 kernel). This kernel files will be available for downloading for several days only (week maximum).

---

### Post by ivanhoe1024 on 2009-04-28
> **evgeny1978 said:**
> You can download recompiled kernel 64-bit version for jaunty with "ACPI Processor P-States driver" as a module at [ftp://129.93.36.1/linux-headers-2.6.28.9-phc001_2.6.28.9-phc001-10.00.Custom_amd64.deb](ftp://129.93.36.1/linux-headers-2.6.28.9-phc001_2.6.28.9-phc001-10.00.Custom_amd64.deb) and [ftp://129.93.36.1/linux-image-2.6.28.9-phc001_2.6.28.9-phc001-10.00.Custom_amd64.deb](ftp://129.93.36.1/linux-image-2.6.28.9-phc001_2.6.28.9-phc001-10.00.Custom_amd64.deb) (I followed instructions at [http://www.linux-phc.org/forum/viewtopic.php?f=13&t=67](http://www.linux-phc.org/forum/viewtopic.php?f=13&t=67) and [http://www.linux-phc.org/forum/viewtopic.php?f=13&t=2](http://www.linux-phc.org/forum/viewtopic.php?f=13&t=2) for phc-intel-0.3.2-4.tar.gz file. By the way this is actually 2.6.28.11 kernel). This kernel files will be available for downloading for several days only (week maximum).

Wow, you're my hero!! Ok, I'm downloading them... Just a question: after I downloaded them, Do I have to patch them looking at [http://www.linux-phc.org/forum/viewtopic.php?f=13&t=2](http://www.linux-phc.org/forum/viewtopic.php?f=13&t=2), or are they just patched??
Thanks a lot!!

PS. I installed your two packages, but I have this error. Does anyone know what does it mean??

```
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
run-parts: executing /etc/kernel/postinst.d/nvidia-common
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 20
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.28.9-phc001.postinst line 1186.
dpkg: errore processando linux-image-2.6.28.9-phc001 (--install):
 il sottoprocesso post-installation script ha restituito un codice di errore 2
Sono occorsi degli errori processando:
 linux-image-2.6.28.9-phc001

```

---

### Post by ivanhoe1024 on 2009-04-28
> **ivanhoe1024 said:**
> Wow, you're my hero!! Ok, I'm downloading them... Just a question: after I downloaded them, Do I have to patch them looking at [http://www.linux-phc.org/forum/viewtopic.php?f=13&t=2](http://www.linux-phc.org/forum/viewtopic.php?f=13&t=2), or are they just patched??
Thanks a lot!!

PS. I installed your two packages, but I have this error. Does anyone know what does it mean??

```
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
run-parts: executing /etc/kernel/postinst.d/nvidia-common
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 20
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.28.9-phc001.postinst line 1186.
dpkg: errore processando linux-image-2.6.28.9-phc001 (--install):
 il sottoprocesso post-installation script ha restituito un codice di errore 2
Sono occorsi degli errori processando:
 linux-image-2.6.28.9-phc001

```

Ok, I fixed all... Now I've got just to patch the module (I think it sin't yet, is it??)

Why don't you post the new kernel you'll compile in the future in this thread, so we can download it?? ):P

---

### Post by evgeny1978 on 2009-04-28
This kernel is not patched, you need to apply patch from [http://www.linux-phc.org/forum/viewtopic.php?f=13&t=2](http://www.linux-phc.org/forum/viewtopic.php?f=13&t=2). By the way I also had this stupid error with /etc/kernel/postinst.d/nvidia-common, I didn't try to figure out what is the problem here, just removed this file temporarily when was installing kernel, after installation put it back. How did you fix this error?

---

### Post by tocoli on 2009-04-29
> **XRayA4T said:**
> It appears that with Jaunty the ACPI stuff is now in the kernel rather than in a module which requires you to patch and build the kernel. Having never done this before I decided to take the plunge and give it a go! I followed the instructions here [http://beginlinux.wordpress.com/2008/12/03/how-to-compile-an-ubuntu-810-kernel/](http://beginlinux.wordpress.com/2008/12/03/how-to-compile-an-ubuntu-810-kernel/) and it was pretty straight forward if time consuming.

I have created a script to simplify the process. Create a folder where you have write access. Put the following script in that folder, buildKernel:
```

#!/bin/sh
if [ "$1" = "" ]; then
echo "Usage: $N {version number}" >&2;
		exit 1;
fi
start=`date`
echo "Started : $start"
bunzip2 -c /usr/src/linux-source-2.6.28.tar.bz2 | tar xp
cd linux-source-2.6.28
cp /boot/config-`uname -r` ./.config 
patch -p1 < ../linux-phc-0.3.2-kernel-vanilla-2.6.26.patch
make-kpkg clean
fakeroot make-kpkg --initrd --append-to-version=-rb${1} kernel_image kernel_headers
cd ..
rm -rf linux-source-2.6.28
echo "Started : $start"
echo "Ended   : `date`"

```
You can replace the rb in --append-to-version=-rb${1} with your initials. You can then make it executable and run it as "buildKernel 2" where 2 is the version number you want to assign. 

It takes up about 4GB during the build process (which the last line in the script deletes) to build the 2 deb packages which are about 300MB. The build took about 2 hours on my machine. You can then install the 2 packages and use the undervolting as you did when it was a module.

Hope this helps
Ray

This script above aint ok in my Ubuntu (Jaunty, 2.6.28.11).
After the build there aint any acpi-cpufreq.ko... 
I ve just recomplied the kernel on PHC-forum way, and patch with phc-intel-0.3.2-5 offtree package. It's working fine.

---

### Post by m4cph1sto on 2009-04-30
I'm experiencing CPU overheating after upgrading to Jaunty.  There are some other threads on this issue, but readers of this thread seem to have some expertise.  My Pentium M/centrino laptop has always used speedstep-centrino by default, and I used to be able to switch to acpi_cpufreq by just blacklisting speedstep-centrino and loading acpi_cpufreq.  Now that they are hard-coded into the kernel, I don't know how to do this.  I'm wondering if switching from speedstep-centrino to acpi_cpufreq, or vise-versa, would fix the overheating issue.  Is there any way to do this now (without recompiling the entire kernel)?

---

### Post by ivanhoe1024 on 2009-04-30
> **evgeny1978 said:**
> This kernel is not patched, you need to apply patch from [http://www.linux-phc.org/forum/viewtopic.php?f=13&t=2](http://www.linux-phc.org/forum/viewtopic.php?f=13&t=2). By the way I also had this stupid error with /etc/kernel/postinst.d/nvidia-common, I didn't try to figure out what is the problem here, just removed this file temporarily when was installing kernel, after installation put it back. How did you fix this error?

I fixed it just in the same way, I can't understand what is the matter with nvidia-common... But it's not a problem of your kernel, because I've read of people in other forum with the same problem...

---

### Post by zcats on 2009-05-01
So, using Jaunty  PHC control now requires rebuilding and patching the kernel. There is an easier way!- download a patched kernel.
 
See the launchpad ppa for linux-PHC:

[https://launchpad.net/~linux-phc/+archive/ppa](https://launchpad.net/~linux-phc/+archive/ppa)

>add this ppa to sources.list and import key
>install updates (will include the patched undervolt kernel)
>reboot
>set vids using echo by editing rc.local as I described earlier in this thread
i.e. my optimal vids were:
echo "17:19 14:12 12:18 10:4 8:1 6:1" > /sys/devices/system/cpu/cpu0/cpufreq/phc_controls


:guitar:Done
zcat:)

---

### Post by ivanhoe1024 on 2009-05-03
> **zcats said:**
> So, using Jaunty  PHC control now requires rebuilding and patching the kernel. There is an easier way!- download a patched kernel.
 
See the launchpad ppa for linux-PHC:

[https://launchpad.net/~linux-phc/+archive/ppa](https://launchpad.net/~linux-phc/+archive/ppa)

>add this ppa to sources.list and import key
>install updates (will include the patched undervolt kernel)
>reboot
>set vids using echo by editing rc.local as I described earlier in this thread
i.e. my optimal vids were:
echo "17:19 14:12 12:18 10:4 8:1 6:1" > /sys/devices/system/cpu/cpu0/cpufreq/phc_controls


:guitar:Done
zcat:)

I asked The Fallen (phc developer) about this repository, and this is his answer:

this ppa is ours, we are currently trying to create it. There is already a kernel you can use but it will replace your default ubuntu kernel and will be replaced on the next ubuntu kernel update.

You see, we do not know how to set other version numbers to the ppa.
As soon as we solved this problem the ppa will be published.

Hope you'll find it useful, bye

---

### Post by jmmL on 2009-05-03
> **ivanhoe1024 said:**
> I asked The Fallen (phc developer) about this repository, and this is his answer:

this ppa is ours, we are currently trying to create it. There is already a kernel you can use but it will replace your default ubuntu kernel and will be replaced on the next ubuntu kernel update.

You see, we do not know how to set other version numbers to the ppa.
As soon as we solved this problem the ppa will be published.

Hope you'll find it useful, bye

To set the correct version number you need to add one and suffix ~ppaN

I don't know what the current kernel version is on jaunty, but say it's 2.6.28-11, then the maintainers of that ppa need to put 2.6.28-12~ppa1 .

I'm pretty sure that's right, anyone with more experience feel free to correct me. I'm new to all this ppa maintaining stuff! :D

---

### Post by M4rotku on 2009-05-03
Can someone post the modified kernel for:

2.6.24-23



Thanks,
M4rotku

---

### Post by mister_playboy on 2009-05-07
The modified kernel works like a charm!  Now everything is working perfectly in 9.04 for me (other than my Intel GMA965 graphics, anyway)!

Thank you so much.

---

### Post by rk. on 2009-05-13
Hi,
 I try to build a 2.6.28 Jaunty kernel with a modified versionnumber **INSIDE** **PPA**, but it failed.

 ******************************************************************************
**FIRST Try:**
 - CONFIG_DEBUG_INFO >>> OFF
 - CONFIG_LOCALVERSION >>> "phc0"
 - apply linux-phc patch 0.3.2 (undervolting patch)
- add ~ppa0 to Changelog


 **FULL-LOG:**
 [http://launchpadlibrarian.net/25179325/buildlog_ubuntu-jaunty-i386.linux_2.6.28-11.42~ppa2_FAILEDTOBUILD.txt.gz]("http://launchpadlibrarian.net/25179325/buildlog_ubuntu-jaunty-i386.linux_2.6.28-11.42%7Eppa2_FAILEDTOBUILD.txt.gz")
 
```

# The main image
install -m644 -D /build/buildd/linux-2.6.28/debian/build/build-generic/arch/i386/boot/bzImage \
  /build/buildd/linux-2.6.28/debian/linux-image-2.6.28-11-generic/boot/vmlinuz-2.6.28-11-generic
install -m644 /build/buildd/linux-2.6.28/debian/build/build-generic/.config \
  /build/buildd/linux-2.6.28/debian/linux-image-2.6.28-11-generic/boot/config-2.6.28-11-generic
install -m644 /build/buildd/linux-2.6.28/debian/abi/2.6.28-11.42~ppa2/i386/generic \
  /build/buildd/linux-2.6.28/debian/linux-image-2.6.28-11-generic/boot/abi-2.6.28-11-generic
install -m644 /build/buildd/linux-2.6.28/debian/build/build-generic/System.map \
  /build/buildd/linux-2.6.28/debian/linux-image-2.6.28-11-generic/boot/System.map-2.6.28-11-generic
makedumpfile -g /build/buildd/linux-2.6.28/debian/linux-image-2.6.28-11-generic/boot/vmcoreinfo-2.6.28-11-generic \
  -x /build/buildd/linux-2.6.28/debian/build/build-generic/vmlinux
get_debug_info: Can't create a handle for a new debug session.
 makedumpfile Failed.
make: *** [install-generic] Error 1
dpkg-buildpackage: failure: /usr/bin/fakeroot debian/rules binary gave error exit status 2

```******************************************************************************
**SECOND Try:**
 - remove of MAKEDUMPFILE in deban/rules.d/binary-arch.mk

 **FULL-LOG:**
 [http://launchpadlibrarian.net/25099133/buildlog_ubuntu-jaunty-i386.linux_2.6.28-11.42~ppa1_FAILEDTOBUILD.txt.gz]("http://launchpadlibrarian.net/25099133/buildlog_ubuntu-jaunty-i386.linux_2.6.28-11.42%7Eppa1_FAILEDTOBUILD.txt.gz")


 ```
#
# Remove files which are generated at installation by postinst, except for
# modules.order.
#
mv /build/buildd/linux-2.6.28/debian/linux-image-2.6.28-11-generic/lib/modules/2.6.28-11-generic/modules.order \
  /build/buildd/linux-2.6.28/debian/linux-image-2.6.28-11-generic/lib/modules/2.6.28-11-generic/_modules.order
mv: cannot stat `/build/buildd/linux-2.6.28/debian/linux-image-2.6.28-11-generic/lib/modules/2.6.28-11-generic/modules.order': No such file or directory
make: *** [install-generic] Error 1
dpkg-buildpackage: failure: /usr/bin/fakeroot debian/rules binary gave error exit status 2
``` ******************************************************************************


 [COLOR=Black][B]I don't know what's wrong with the build. I read the Kernel Build Guide of Ubuntu, but I can't find the solution. [COLOR=Red]Why the buildprocess fail with a modified Versionnumber?[/COLOR]
[/B][/COLOR]

---

### Post by Mr Pink57 on 2009-05-16
I am not sure if this is really working or my values are sticking.

The stress test went to -1 then stopped so it never actually crashed.  And I only saw one value in my list which was 15 1 and that does not work, so I did 17:1 and my system completely freezes once I hit enter.  So I am a little confused I guess any insight would be great.

pink

---

### Post by Mr Pink57 on 2009-05-17
> **Mr Pink57 said:**
> I am not sure if this is really working or my values are sticking.

The stress test went to -1 then stopped so it never actually crashed.  And I only saw one value in my list which was 15 1 and that does not work, so I did 17:1 and my system completely freezes once I hit enter.  So I am a little confused I guess any insight would be great.

pink

I did end up getting this to work I set my second value to my lowest cpu mhz second value for all (only 2) and now I am no joke 30c cooler, that does include me taking a air can to this laptop.

pink

---

### Post by skinnie on 2009-05-19
> **ivanhoe1024 said:**
> I asked The Fallen (phc developer) about this repository, and this is his answer:

this ppa is ours, we are currently trying to create it. There is already a kernel you can use but it will replace your default ubuntu kernel and will be replaced on the next ubuntu kernel update.

You see, we do not know how to set other version numbers to the ppa.
As soon as we solved this problem the ppa will be published.

Hope you'll find it useful, bye

how do I know if phc is working with this method?it is the same method as the old one?

---

### Post by adambro7 on 2009-05-24
> **rk. said:**
> Hi,
 I try to build a 2.6.28 Jaunty kernel with a modified versionnumber **INSIDE** **PPA**, but it failed.
(...)
 [COLOR=Black][B]I don't know what's wrong with the build. I read the Kernel Build Guide of Ubuntu, but I can't find the solution. [COLOR=Red]Why the buildprocess fail with a modified Versionnumber?[/COLOR]
[/B][/COLOR]
I'm not an expert but this may help:
- [Building your source package]("https://help.launchpad.net/Packaging/PPA#Building%20your%20source%20package") - PPA help explains versioning
- [Kernel DKMS Package](https://help.ubuntu.com/community/Kernel/DkmsDriverPackage) - describes how to compile dynamic kernel modules and since ACPI is a module (compiled-in) it may help resolve ABI issues

---

### Post by anjie on 2009-06-08
> **zcats said:**
> So, using Jaunty  PHC control now requires rebuilding and patching the kernel. There is an easier way!- download a patched kernel.
 
See the launchpad ppa for linux-PHC:

[https://launchpad.net/~linux-phc/+archive/ppa](https://launchpad.net/~linux-phc/+archive/ppa)

>add this ppa to sources.list and import key
>install updates (will include the patched undervolt kernel)
>reboot
>set vids using echo by editing rc.local as I described earlier in this thread
i.e. my optimal vids were:
echo "17:19 14:12 12:18 10:4 8:1 6:1" > /sys/devices/system/cpu/cpu0/cpufreq/phc_controls


:guitar:Done
zcat:)



Hello, I've just followed the 1st 2nd 3rd step of your tips. Before setting vids, how can I check if the new kernel works? For example, if I enter this command

```
cat /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
```

I get a missing device error.
Excuse me for my "too noob" questions...

Thanks,

A.

---

### Post by mister_playboy on 2009-06-11
> **anjie said:**
> Hello, I've just followed the 1st 2nd 3rd step of your tips. Before setting vids, how can I check if the new kernel works? For example, if I enter this command

```
cat /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
```

I get a missing device error.
Excuse me for my "too noob" questions...

Thanks,

A.

You have to install the modified kernel before you can set the VIDs... the module is in the kernel now.  The test would be to run:


```
cat /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
```

which should give you the default VIDs with the newly installed modded kernel, rather than a missing device error with the normal kernel.  You then need to set the VIDs and have them echoed to run at startup as is detailed in the first post.

The process is actually easier for end users now that we have the repo.  :)

---

### Post by anjie on 2009-06-11
> **mister_playboy said:**
> You have to install the modified kernel before you can set the VIDs... the module is in the kernel now.  The test would be to run:


```
cat /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
```

which should give you the default VIDs with the newly installed modded kernel, rather than a missing device error with the normal kernel.  You then need to set the VIDs and have them echoed to run at startup as is detailed in the first post.

The process is actually easier for end users now that we have the repo.  :)

Thanks for your answer, I also thought that the process would be easy , I've simply updated ubuntu after entering the new repo and have a reload after entering keys. When updating it downloaded again the same kernel version, and I think it has substituted the old one. It seems it has got the same name as the previous one, am I wrong? Shouldn't the name be different?

uname -r gives me:

2.6.28-11-generic

Looking in synaptic manager there undervolt packages installed such as 
linux-headers-2.8.28.11-gener 2.6.28.11.43-undervolt1

Is there a way to install it? Maybe I've only downloaded it and the old one is still the "head" kernel

Thanks again!!


I ADD a part of menu.lst


kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID= [cut]
initrd		/boot/initrd.img-2.6.28-11-generic

---

### Post by zcats on 2009-06-12
Even when you have the patched kernel installed >uname-r gives
>2.6.28-11-generic
The way to test if the patched kernel is installed is to run
>cat /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
it should return YOUR vids (mine are..)
>17:19 14:12 12:8 10:4 8:1 6:1 
If the above command does not give vids you have not got the patched kernel installed OR you are not booting the correct kernel. Check synaptic to see if the "installed version" column shows 2.6.28-11-generic~undervolt.
If OK then check menu.lst to see that you are booting the correct kernel!
******BTW i did not need to change anything in menu.lst....seems that the generic kernel in menu.lst points to the ~undervolt kernel without actually needing to specify this...

My section looks like (yours will have a different UUID) :
title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		9ee9e3e1-ef67-4be4-a0df-03ed23443615
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=9ee9e3e1-ef67-4be4-a0df-03ed23443615 ro splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

Hope this solves it:p

---

### Post by anjie on 2009-06-12
> **zcats said:**
> Even when you have the patched kernel installed >uname-r gives
>2.6.28-11-generic
The way to test if the patched kernel is installed is to run
>cat /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
it should return YOUR vids (mine are..)
>17:19 14:12 12:8 10:4 8:1 6:1 
If the above command does not give vids you have not got the patched kernel installed OR you are not booting the correct kernel. Check synaptic to see if the "installed version" column shows 2.6.28-11-generic~undervolt.
If OK then check menu.lst to see that you are booting the correct kernel!
******BTW i did not need to change anything in menu.lst....seems that the generic kernel in menu.lst points to the ~undervolt kernel without actually needing to specify this...

My section looks like (yours will have a different UUID) :
title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		9ee9e3e1-ef67-4be4-a0df-03ed23443615
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=9ee9e3e1-ef67-4be4-a0df-03ed23443615 ro splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

Hope this solves it:p


First of all thanks for answering me.
It seems there is nothing to do. As you see in my previous post I've checked synaptics and the installed version is just the undervolt one. 

cat /sys/devices/system/cpu/cpu0/cpufreq/phc_controls 
Always: no device

my menu.lst, I've posted it above, is the same as yours. :(

I don't think I'm missing something, that's sad, my noisy fan keeps bothering and I have always to run windows :-& in order to undervolt and keep cool my cpu... what can I do? :cry:

---

### Post by Rizado on 2009-06-13
I don't think this is working for me, the script goes way down to -1 without any problems. This goes for all frequencies... It doesn't seem to be any problems with the phc patch either. The temperaturer is stable at 76C throughout the testing so I don't believe it's worling at all :(

I have a Core 2 Duo T5870 and the latest 2.6.30 vanilla kernel (with patches of course).

EDIT: I got it to work! It seem that the script doesn't want to change governor on both cores (or maybe it's cpu1 that matters for me). I changed it a bit and made it change both cpu0 and cpu1 at the same time. The voltages go ridiculously low anyway but the temperature is decreasing so it is working. The two lowest frequencies is stable at 0... After 30 minutes of stress test at the highest frequency (2Ghz) the temperature has stabilized at about 65C. That is with the fan at 45%! There should be no problem on a hot day as it has a lot more fan to spin :) Right now the room temperature is about 22C
Btw, I have a HP 2230s with a 2Ghz C2D T5870 and my phc_vids is: "22 20 10 0 0"
The second value is 4 steps above crash. The others I don't know since I didn't bother letting the script finish.

I have a question too. As the two lowest frequencies have the same voltages, is it really necessary to use the lowest? Wouldn't the second lowest use the same amount of energy, or less (no wasted cycles when switching modes), when idling?

---

### Post by dementic on 2009-06-14
> **Rizado said:**
> I have a question too. As the two lowest frequencies have the same voltages, is it really necessary to use the lowest? Wouldn't the second lowest use the same amount of energy, or less (no wasted cycles when switching modes), when idling?Did the test on Windows with RmClock and it uses more power when running at 1.2Ghz with 0.85v than on 800mhz with 0.85v. I have core2duo 7250 on a dell inspiron 1520 laptop

---

### Post by Ares Drake on 2009-06-14
> **dementic said:**
> Did the test on Windows with RmClock and it uses more power when running at 1.2Ghz with 0.85v than on 800mhz with 0.85v. I have core2duo 7250 on a dell inspiron 1520 laptop


I seem to remember that used energy scales about linearly with frequency and about ^2 with voltage. (Info must be from overclockers.com if I remember correctly)

---

### Post by Noahod on 2009-06-14
> **Rizado said:**
> I don't think this is working for me, the script goes way down to -1 without any problems. This goes for all frequencies... It doesn't seem to be any problems with the phc patch either. The temperaturer is stable at 76C throughout the testing so I don't believe it's worling at all :(

I have a Core 2 Duo T5870 and the latest 2.6.30 vanilla kernel (with patches of course).

EDIT: I got it to work! It seem that the script doesn't want to change governor on both cores (or maybe it's cpu1 that matters for me). I changed it a bit and made it change both cpu0 and cpu1 at the same time. The voltages go ridiculously low anyway but the temperature is decreasing so it is working. The two lowest frequencies is stable at 0... After 30 minutes of stress test at the highest frequency (2Ghz) the temperature has stabilized at about 65C. That is with the fan at 45%! There should be no problem on a hot day as it has a lot more fan to spin :) Right now the room temperature is about 22C
Btw, I have a HP 2230s with a 2Ghz C2D T5870 and my phc_vids is: "22 20 10 0 0"
The second value is 4 steps above crash. The others I don't know since I didn't bother letting the script finish.


Hi, I have the same problem, mine goes to -1 and stops. How did you edit the script to make it change it for both cores?

Thanks

---

### Post by XRayA4T on 2009-06-15
> **tocoli said:**
> This script above aint ok in my Ubuntu (Jaunty, 2.6.28.11).
After the build there aint any acpi-cpufreq.ko... 
I ve just recomplied the kernel on PHC-forum way, and patch with phc-intel-0.3.2-5 offtree package. It's working fine.

THe script builds the .deb packages with the new kernel and headers. You still need to install the packages you build.
Ray

---

### Post by mister_playboy on 2009-06-19
Kernel 2.6.28.13 is available in update manager, but you'll want to hold off on upgrading for now unless you are okay with losing your undervolting!  :)

---

### Post by Uhuu on 2009-06-29
Is the kernel updated yet at the phc repos?

---

### Post by sarah.fauzia on 2009-06-29
I'm an Arch Linux user now, and I've tried the script again, and it works great. The only catch is that I'm having random lock-ups...

So, to try to figure out why, I tried the script in three different states: 
1) My computer with the lowest brightness set, wireless not on
2) With the highest brightness set, wireless on, AC adapter connected
3) With the highest brightness set, wireless on, AC not connected

Here are the values I get (respectively):
```
[sara@sara-thinkpad without_ac]$ cat phc_tweaked_vids
20 17 1 1
[sara@sara-thinkpad with_ac]$ cat phc_tweaked_vids
16 1 1 -1
[sara@sara-thinkpad without_ac_high]$ cat phc_tweaked_vids
16 15 1 1

```

My machine is C2D, an X61 tablet, with the latest kernel 2.6.30. I'm getting the lock-ups with using the first set of values (20 17 1 1) on both cores.

```

[sara@sara-thinkpad ~]$ cat /sys/devices/system/cpu/cpu1/cpufreq/phc_controls
10:20 9:17 6:1 136:1
```

The default values: **36 25 21 11**

[edit] So far, just bumping up each of the values (20 17 1 1) by two seems to have fixed the problem, but I wonder why the script's values didn't work (when the script had already bumped the values by two based off the minimum my computer could take). [/edit]

---

### Post by mister_playboy on 2009-07-05
> **Uhuu said:**
> Is the kernel updated yet at the phc repos?

Not yet... [-o<

---

### Post by Shikaku2 on 2009-07-06
I wonder if it works with an AMD Turion X2 Laptop.  I'll wait for the patch and mess with it when it comes out.

---

### Post by Kiddion on 2009-07-06
> **Shikaku2 said:**
> I wonder if it works with an AMD Turion X2 Laptop.  I'll wait for the patch and mess with it when it comes out.

Depends on the AMD Turion X2 you're talking about... What family does it belong to, as mentioned in /proc/cpuinfo? If it is 17, then it is not supported at the moment... But I am working on it. 
If it is <16 it is already supported. And with "direct_transitions" enabled, you can even unlock new frequencies.

---

### Post by Shikaku2 on 2009-07-06
```
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 72
model name	: AMD Turion(tm) 64 X2 Mobile Technology TL-50
```

Oh!  I'll reread this whole thread and check it out then.

Thanks :cool:

---

### Post by philcamlin on 2009-07-06
very cool post 

i should try it on my laptop :popcorn:

---

### Post by Shikaku2 on 2009-07-06
> **Kiddion said:**
> Depends on the AMD Turion X2 you're talking about... What family does it belong to, as mentioned in /proc/cpuinfo? If it is 17, then it is not supported at the moment... But I am working on it. 
If it is <16 it is already supported. And with "direct_transitions" enabled, you can even unlock new frequencies.

I reread this thread and even installed the undervolt patch from the supplied repositories.  But I can't get it to work right.  Can anyone help me?

Running cat /sys/devices/system/cpu/cpu0/cpufreq/phc_controls gives does not exist.

```
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 72
model name	: AMD Turion(tm) 64 X2 Mobile Technology TL-50
```

This is my CPU.

---

### Post by Kiddion on 2009-07-07
> **Shikaku2 said:**
> I reread this thread and even installed the undervolt patch from the supplied repositories.  But I can't get it to work right.  Can anyone help me?

Running cat /sys/devices/system/cpu/cpu0/cpufreq/phc_controls gives does not exist.

```
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 72
model name	: AMD Turion(tm) 64 X2 Mobile Technology TL-50
```

This is my CPU.
That's perhaps because I only wrote an out-of-tree AMD k8 patch and therefore it's probably not included in the PHC ppa kernel (but you will need it or another kernel without built-in powernow-k8 driver).

Just install "dkms" if you don't have it (`sudo apt-get install dkms`) download the driver, unpack it somewhere and run `sudo make dkms_install`. Your driver will be called "phc-k8" and should show up in `lsmod`. 
To unlock all fids, you need to edit /etc/modprobe.d/phc-k8.conf and uncomment the line with "#option phc-k8 direct_transitions=1".

There's a patch for Gentoo that can be applied on top of the kernel, I'll ask the-fallen whether this can be included in the PPA, so it will be a part of the ppa kernel as well...

---

### Post by Shikaku2 on 2009-07-08
> **Kiddion said:**
> That's perhaps because I only wrote an out-of-tree AMD k8 patch and therefore it's probably not included in the PHC ppa kernel (but you will need it or another kernel without built-in powernow-k8 driver).

Just install "dkms" if you don't have it (`sudo apt-get install dkms`) download the driver, unpack it somewhere and run `sudo make dkms_install`. Your driver will be called "phc-k8" and should show up in `lsmod`. 
To unlock all fids, you need to edit /etc/modprobe.d/phc-k8.conf and uncomment the line with "#option phc-k8 direct_transitions=1".

There's a patch for Gentoo that can be applied on top of the kernel, I'll ask the-fallen whether this can be included in the PPA, so it will be a part of the ppa kernel as well...

This is so strange...  I did it right I think but it's not in lsmod at all.

Here's what I did.  I have the repository undervolt kernel, it's downloaded and installed.

It wasn't working.

I already had DKMS.  I downloaded the latest AMD phc from linux-phc.org.  I went to the directory and did sudo make dkms_install.  Reboot.

I still get nothing in lsmod about it nor does the phc options appear in the cpu0/cpufreq folder.

I make sure it loads by editing the /etc/modules and adding phc-k8.  It doesn't load.

I then BLACKLIST powernow-k8 to see if it was a conflict.

I check dmesg and this is the only line about PHC i get:

[   15.730675] phc-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-50 processors (2 cpu cores) (version 2.20.00)

It's still not in lsmod though :(

---

### Post by Kiddion on 2009-07-08
> **Shikaku2 said:**
> This is so strange...  I did it right I think but it's not in lsmod at all.

Here's what I did.  I have the repository undervolt kernel, it's downloaded and installed.

It wasn't working.

I already had DKMS.  I downloaded the latest AMD phc from linux-phc.org.  I went to the directory and did sudo make dkms_install.  Reboot.

I still get nothing in lsmod about it nor does the phc options appear in the cpu0/cpufreq folder.

I make sure it loads by editing the /etc/modules and adding phc-k8.  It doesn't load.

I then BLACKLIST powernow-k8 to see if it was a conflict.

I check dmesg and this is the only line about PHC i get:

[   15.730675] phc-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-50 processors (2 cpu cores) (version 2.20.00)

It's still not in lsmod though :(

Hmmm, what are the outputs of:

uname -a
dmesg|grep k8
lsmod|grep k8
modprobe -l *k8*
dkms status

BTW, you can also contact me directly, see at the top of phc-k8.c for my email ;)

---

### Post by Shikaku2 on 2009-07-08
> **Kiddion said:**
> uname -a
dmesg|grep k8
lsmod|grep k8
modprobe -l *k8*
dkms status

```
computer:~$ uname -a
Linux computer-laptop 2.6.28-11-generic #43~undervolt1-Ubuntu SMP Fri Apr 17 18:32:02 UTC 2009 i686 GNU/Linux
computer:~$ dmesg|grep k8
[    2.364875] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-50 processors (2 cpu cores) (version 2.20.00)
[    2.364976] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x13
[    2.365032] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x14
[   15.754779] phc-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-50 processors (2 cpu cores) (version 2.20.00)
[   18.456738] phc-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-50 processors (2 cpu cores) (version 2.20.00)
computer:~$ lsmod|grep k8
k8temp                 12416  0 
computer:~$ modprobe -l *k8*
kernel/drivers/hwmon/k8temp.ko
kernel/drivers/mtd/maps/ck804xrom.ko
updates/dkms/phc-k8.ko
computer:~$ dkms status
phc-k8, 0.4.1, 2.6.28-11-generic, i686: installed
```

I found the email too btw.  If I need further assistance I'll email.

---

### Post by Kiddion on 2009-07-08
> **Shikaku2 said:**
> ```
computer:~$ uname -a
Linux computer-laptop 2.6.28-11-generic #43~undervolt1-Ubuntu SMP Fri Apr 17 18:32:02 UTC 2009 i686 GNU/Linux
computer:~$ dmesg|grep k8
[    2.364875] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-50 processors (2 cpu cores) (version 2.20.00)
[    2.364976] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x13
[    2.365032] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x14
[   15.754779] phc-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-50 processors (2 cpu cores) (version 2.20.00)
[   18.456738] phc-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-50 processors (2 cpu cores) (version 2.20.00)

```

I found the email too btw.  If I need further assistance I'll email.

I seems the powernow-k8 module is (still) built-in, I'll contact the-fallen, that shouldn't have happened and it will be fixed ASAP. So it's the ppa kernel that is causing this to fail...

---

### Post by Kiddion on 2009-07-12
There's a newer kernel available with the powernow-k8 patch integrated at [https://launchpad.net/~linux-phc/+archive/ppa](https://launchpad.net/~linux-phc/+archive/ppa)

The driver is built as a module, so you can even override it by a different PHC K8 patch in the future.

---

### Post by mister_playboy on 2009-07-14
Ahhh... there's the new kernel so we can update now! :)

Thank you to the repo maintainers for helping out n00bs such as myself.

EDIT: I updated to the new kernel from the repo, but I don't have undervolting... huh?  It is listed as installed, but I don't have PHC.  I just downloaded all the available updates in Update Manager... do we need to do something else?  I only have two kernel images in /boot, so I believe I am booting to the modified kernel when choosing 2.6.28.13... and 2.6.28.11 still works correctly.  What's going on?

---

### Post by winnibob on 2009-07-16
> **mister_playboy said:**
> EDIT: I updated to the new kernel from the repo, but I don't have undervolting... huh?  It is listed as installed, but I don't have PHC.  I just downloaded all the available updates in Update Manager... do we need to do something else?  I only have two kernel images in /boot, so I believe I am booting to the modified kernel when choosing 2.6.28.13... and 2.6.28.11 still works correctly.  What's going on?
I have updated my system yesterday with kernel 2.6.28.13 from the ppa and it is working fine on my dual core.

---

### Post by Kiddion on 2009-07-18
> **mister_playboy said:**
> EDIT: I updated to the new kernel from the repo, but I don't have undervolting... huh?  It is listed as installed, but I don't have PHC.  I just downloaded all the available updates in Update Manager... do we need to do something else?  I only have two kernel images in /boot, so I believe I am booting to the modified kernel when choosing 2.6.28.13... and 2.6.28.11 still works correctly.  What's going on?
There was a problem for Centrino's (the depricated speedstep-centrino module was built-in and therefore used instead of the PHC acpi-cpufreq module). This should be solved in the latest 2.6.28.13-generic version 2.6.28-13.46~undervolt3.

---

### Post by asuna on 2009-07-19
> **anjie said:**
> First of all thanks for answering me.
It seems there is nothing to do. As you see in my previous post I've checked synaptics and the installed version is just the undervolt one. 

cat /sys/devices/system/cpu/cpu0/cpufreq/phc_controls 
Always: no device

my menu.lst, I've posted it above, is the same as yours. :(



I've been following the steps to install the linux_phc module, and I got as far as ^anjie

I've downloaded and installed the 2.6.28-13.46~undervolt3 kernel from the PPA (via Update Manager), rebooted to it (although the grub menu says 2.6.28-13-generic), and I got this:

cat /sys/devices/system/cpu/cpu0/cpufreq/phc_controls : No such file or directory

I tried: cat: /sys/devices/system/cpu/cpu0: Is a directory

lsmod | grep acpi_cpufreq gives nothing (blank)

menu.lst looks normal, contains both 2.6.28-13-generic and 2.6.28-11-generic. Do I need to add the 2.6.28-13.46~undervolt3 entry to the list?

It seems as if I never installed the undervolt3 kernel, even though synaptics tells me its installed. Can anyone help? 

I'm using an Intel Core 2 Duo T5500, dual boot with windows xp

---

### Post by Schnitzelpudding on 2009-07-19
No (automatic) fun here either.

Clean install of 9.04, updated everything (including kernel to 2.6.28-13), removed 2.6.28-11, added the PPA, ran Update Manager and let it install its stuff. This seems to have overwritten the original kernel, the acpi-cpufreq module exists but isn't loaded automatically ("CPU frequency scaling unsupported" popup after login and processor stuck at full speed). I've added it to /etc/modules and that seems to be working for now... is this supposed to happen? This is on a Core Duo (T2350) laptop, so nothing particularly exotic.

---

### Post by Kiddion on 2009-07-19
Did you add the acpi_cpufreq module to /etc/modules ? The modules isn't loaded automatically by the default Ubuntu startup scripts, as those suppose that the modules are built-in. If the /sys/devices/system/cpu/cpu0/cpufreq/ directory isn't there, the module has never been loaded.

---

### Post by Shikaku2 on 2009-07-19
Oops, I don't know what I'm doing, ignore me.

---

### Post by asuna on 2009-07-19
Ok thanks for all the help

EDIT:
Finally got it to work!

After I downloaded and used PHC Tool

From [http://linux.aldeby.org/linux-phc-cpu-undervolting.html](http://linux.aldeby.org/linux-phc-cpu-undervolting.html)

"There is no package, you have to download a subversion snapshot via:

sudo apt-get install subversion

svn co [http://phctool.googlecode.com/svn/trunk/](http://phctool.googlecode.com/svn/trunk/) phctool

The tool has a Analysis tab as you can see in the screenshot.

To get this to work, you first need to

sudo modprobe msr"

---

### Post by adempewolff on 2009-07-21
I hope this hasn't already been addressed in the thread. I tried looking for a while but did not see anything.

Nothing happens when I enter "lsmod | grep acpi_cpufreq".  However I am using an Intel Core 2 Duo (which the howto states it has been tested with) and cannot figure out for the life of me why my kernal would be using a module for Centrino processors...  (if it matters I'm also using 9.04, 2.6.28-13-generic)

Am I missing something here?  Is there any other reason why I wouldn't get any output from that command?

---

### Post by hegoburu on 2009-07-23
Ok maybe someone could help me out here. I re compiled the kernel per phc forum instructions, installed phc-k8, rebooted. Lsmod gives me phc-k8 as loaded, checking scaling_driver in cpufreq reports phc-k8, however, there are no phc-specific files in the cpufreq directory. ?? Any ideas?

---

### Post by Kiddion on 2009-07-24
> **adempewolff said:**
> I hope this hasn't already been addressed in the thread. I tried looking for a while but did not see anything.
[...]
Am I missing something here?  Is there any other reason why I wouldn't get any output from that command?
It was mentioned before, but you'll have to add a line containing "acpi-cpufreq" to /etc/modules

> **hegoburu said:**
> Ok maybe someone could help me out here. I re compiled the kernel per phc forum instructions, installed phc-k8, rebooted. Lsmod gives me phc-k8 as loaded, checking scaling_driver in cpufreq reports phc-k8, however, there are no phc-specific files in the cpufreq directory. ?? Any ideas?

Your processor isn't supported (yet). The current phc-k8 driver does not support undervolting for family 10h and family 11h processors (Phenoms and recent Turion X2 processors).

---

### Post by mister_playboy on 2009-07-24
> **Kiddion said:**
> There was a problem for Centrino's (the depricated speedstep-centrino module was built-in and therefore used instead of the PHC acpi-cpufreq module). This should be solved in the latest 2.6.28.13-generic version 2.6.28-13.46~undervolt3.

Hmm... I downloaded the newer version and it still doesn't work for me.  My laptop is a Pentium dual-core.

---

### Post by Kiddion on 2009-07-25
> **mister_playboy said:**
> Hmm... I downloaded the newer version and it still doesn't work for me.  My laptop is a Pentium dual-core.
If you added a line containing "acpi-cpufreq" to /etc/modules and it is still not working (but the module *is* loaded), then I don't know what is happening either, the-fallen has to answer that... I don't know if he watches this forum, perhaps it is best to start a new topic at [http://www.linux-phc.org](http://www.linux-phc.org) then.

---

### Post by adempewolff on 2009-07-26
> **Kiddion said:**
> It was mentioned before, but you'll have to add a line containing "acpi-cpufreq" to /etc/modules

Thank you for your advice but it hasn't worked for me.  I added the line:

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
sbp2
ndiswrapper
acpi-cpufreq

```

and rebooted but I am still not getting any output from the lsmod:

```
austin@austin-laptop:~$ lsmod | grep acpi_cpufreq
austin@austin-laptop:~$
```

My kernel is 2.6.28-13-generic #45-Ubuntu, although I will be upgrading to amd64 this week when I get a new hdd.  I've heard rumors that jaunty kernels do not have acpi_cpufreq as a module.  I know that acpi_cpufreq works because I use it for the ondemand frequency governor.  I just can't get it to show up for the first step of this howto! ](*,)

Any advice would be greatly appreciated!

---

### Post by mark540 on 2009-07-26
Thank you very much

---

### Post by Kiddion on 2009-07-28
> **adempewolff said:**
> My kernel is 2.6.28-13-generic #45-Ubuntu, although I will be upgrading to amd64 this week when I get a new hdd.  I've heard rumors that jaunty kernels do not have acpi_cpufreq as a module.  I know that acpi_cpufreq works because I use it for the ondemand frequency governor.  I just can't get it to show up for the first step of this howto! ](*,)

Any advice would be greatly appreciated!
You WILL need to use the kernel from the Linux-PHC PPA for Ubuntu 9.04 as it is mentioned a couple of times in this topic. That is because Ubuntu decided to built all frequency scaling drivers into the kernel, eliminating all possibilities for undervolting using the stock Ubuntu kernel.
I wish someone could update the first post, because it is so outdated, it does not apply at all to Ubuntu 9.04...

---

### Post by Snakekick on 2009-07-30
Hello, i have a problem .
i use a desktop with q6600 intel quadcore cpu with 2.6.28-13-generic #46~undervolt5 kernel
with windows i use rmclock and i can undervolt the cpu.
but with ubuntu that not working.
phc run and i can see phc_controls and the rest:

cat /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
9:35 8:33 7:30 6:27

but when i change the setting nothing happen.
i have try 9:1 8:1 7:1 6:1
and phc_controls and phc_vids say the new setting but lmsensors say that nothing change.

---

### Post by htrex on 2009-08-03
I've sent an idea on brainstorm to ship karmic koala with acpi-cpufreq as a module or patch directly the kernel instead:

[http://brainstorm.ubuntu.com/idea/20847/](http://brainstorm.ubuntu.com/idea/20847/)

please vote for it if you care about this.

---

### Post by ArmenianLeader4 on 2009-08-03
I would do this, but I dont know if my PC can handle another crash

---

### Post by mobad on 2009-08-22
I installed the newest ppa kernel (it's -15 now) and I'm trying to modprobe acpi_cpufreq and it gives me:
FATAL: Error inserting acpi_cpufreq (/lib/modules/2.6.28-15-generic/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko): No such device

I've got a AMD Athlon(tm) Neo Processor MV-40.

"lsmod | grep k8" gives me k8temp and "dmesg | grep k8" gives me nothing.

I don't know whether it supports my processor yet but I should be at least able to run the module...

EDIT: I guess I was try to mount the Intel module...
For some reason the kernel doesn't come with phc_k8 so I compiled it.
I get "8:22 0:22" in phc_controls now.
But... changing the 22s does nothing so I will assume AMD Neo support is has not been added yet, so I will wait patiently...
Supposedly RMClock works amazingly on the processor.

---

### Post by Kiddion on 2009-08-23
> **mobad said:**
> I installed the newest ppa kernel (it's -15 now) and I'm trying to modprobe acpi_cpufreq and it gives me:
FATAL: Error inserting acpi_cpufreq (/lib/modules/2.6.28-15-generic/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko): No such device

I've got a AMD Athlon(tm) Neo Processor MV-40.

"lsmod | grep k8" gives me k8temp and "dmesg | grep k8" gives me nothing.

I don't know whether it supports my processor yet but I should be at least able to run the module...
Hi, the howto on the first post of this thread is outdated. For Intel processors you need to add "acpi-cpufreq" to /etc/modules, but for AMD processors you need to add "powernow-k8" instead to run the Linux-PHC PPA kernel (with Intel and AMD patches included). Please try to load "powernow-k8" and please please contact me with your findings (I'm the writer/maintainer of the phc-k8 driver).

---

### Post by ashcroft3000 on 2009-09-07
Hey there, forum mateyz!

I'm having a hard time getting usable voltages with this script (Running Jaunty with 2.6.28-15-generic #50~undervolt2-Ubuntu). "cat /sys/devices/system/cpu/cpu0/cpufreq/phc_default_controls" returns "10:44 8:32 6:19". Since I've got a CoreDuo (Intel CoreDuo T2300 @ 1.66 GHz), 19 is the lowest VID possible on this CPU, right?

Just like for [Pluies]("http://ubuntuforums.org/member.php?u=809462"), [Mr Pink57]("http://ubuntuforums.org/member.php?u=175982"), [Rizado]("http://ubuntuforums.org/member.php?u=52168") and [Noahod]("http://ubuntuforums.org/member.php?u=34070") (see links below), the OP's script doesn't stop before VID=-1 on my machine. "So far, so good!", I thought and echoed "10:19 8:19 6:19" into "...cpufreq/phc_default_controls". Well, machine dies as soon GDM is started (before that, /etc/rc.local is successfully executed, btw). So, I guess, I shouldn't use 19 for the first two VIDs...

Question: How can I get this script to work, so it returns meaningful values? (Yep, I did stress core #2, as well...)

Thanks in advance!
 Richard

[http://ubuntuforums.org/showthread.php?p=7291038#post7291038](http://ubuntuforums.org/showthread.php?p=7291038#post7291038)
[http://ubuntuforums.org/showthread.php?p=7450495#post7450495](http://ubuntuforums.org/showthread.php?p=7450495#post7450495)
[http://ubuntuforums.org/showthread.php?p=7457918#post7457918](http://ubuntuforums.org/showthread.php?p=7457918#post7457918)

---

### Post by indosupremacy on 2009-09-10
ouch , my laptop using speed*.centrino model . Wait for another tutorial for my kind of core

---

### Post by beezwings on 2009-09-16
Hi~

I'm a complete nooB.  I've just upgraded to Jaunty and lost my previous undervolting settings.  I've added the repositories from [https://launchpad.net/~linux-phc/+archive/ppa]("https://launchpad.net/~linux-phc/+archive/ppa") but now what am I supposed to do?  There's a long list of "files included" but I can't seem to find any one particular file to download or search for in synaptic.  Help!  (Sorry so new...all the more complex posts in this thread were way beyond me!)

beez

---

### Post by winnibob on 2009-09-20
> **beezwings said:**
> Hi~

I'm a complete nooB.  I've just upgraded to Jaunty and lost my previous undervolting settings.  I've added the repositories from [https://launchpad.net/~linux-phc/+archive/ppa]("https://launchpad.net/~linux-phc/+archive/ppa") but now what am I supposed to do?  There's a long list of "files included" but I can't seem to find any one particular file to download or search for in synaptic.  Help!  (Sorry so new...all the more complex posts in this thread were way beyond me!)

beez

You just have to update your system with System->Update_Manager after adding the ppa, and the modified kernel should be available for update.

---

### Post by beezwings on 2009-09-21
> **winnibob said:**
> You just have to update your system with System->Update_Manager after adding the ppa, and the modified kernel should be available for update.

I've updated a couple of times, but nothing happens except for the normal security updates.  It doesn't offer to update the kernel.  What to do?  I'm running 9.04 with 2.6.28-15.  Thanks!

---

### Post by winnibob on 2009-09-23
> **beezwings said:**
> I've updated a couple of times, but nothing happens except for the normal security updates.  It doesn't offer to update the kernel.  What to do?  I'm running 9.04 with 2.6.28-15.  Thanks!

Has your problem been solved?

If not, please check which version you have for the following packets, just to be sure that the ~undervolt version of the kernel is not already installed on your system :

linux-headers-2.6.28-15
linux-headers-2.6.28-15-generic
linux-image-2.6.28-15-generic

---

### Post by beezwings on 2009-09-23
> **winnibob said:**
> Has your problem been solved?

If not, please check which version you have for the following packets, just to be sure that the ~undervolt version of the kernel is not already installed on your system :

linux-headers-2.6.28-15
linux-headers-2.6.28-15-generic
linux-image-2.6.28-15-generic

Not solved yet...I couldn't  find anything with 2.6.28-15 ~undervolt in the repositories, so I tried installing 2.6.28-13 ~undervolt a few days ago. Now I have some strange mix.  What is installed is the following:


linux-headers-2.6.28-13 ~undervolt5
linux-headers-2.6.28-13-generic ~undervolt5
linux-image-2.6.28-13-generic  ~undervolt5
linux-image-2.6.28-15-generic
linux-image-generic (version 2.6.28-15.20)

Thanks for your help!

---

### Post by Ev1L on 2009-09-23
you are sure you have these lines in /etc/apt/sources.list?

deb [http://ppa.launchpad.net/linux-phc/ppa/ubuntu](http://ppa.launchpad.net/linux-phc/ppa/ubuntu) jaunty main 
deb-src [http://ppa.launchpad.net/linux-phc/ppa/ubuntu](http://ppa.launchpad.net/linux-phc/ppa/ubuntu) jaunty main

---

### Post by beezwings on 2009-09-23
Yes, they're there.  (That's where I had found the 2.6.28-13 ~undervolt files).  What did I do wrong?

---

### Post by Ev1L on 2009-09-23
mmmhhh that's weird, i don't know, maybe you have blocked some kernel version?
(just guessing, i never did it)
or you have commented out some other repository preventing that update?

---

### Post by beezwings on 2009-09-23
> **asuna said:**
> Ok thanks for all the help

EDIT:
Finally got it to work!

After I downloaded and used PHC Tool

From [http://aldeby.org/blog/index.php/linux-phc-cpu-undervolting.html:](http://aldeby.org/blog/index.php/linux-phc-cpu-undervolting.html:)

"There is no package, you have to download a subversion snapshot via:

sudo apt-get install subversion

svn co [http://phctool.googlecode.com/svn/trunk/](http://phctool.googlecode.com/svn/trunk/) phctool

The tool has a Analysis tab as you can see in the screenshot.

To get this to work, you first need to

sudo modprobe msr"
Asuna--How did you get it to work?

---

### Post by beezwings on 2009-09-23
Don't know.  I don't even know what commenting is!  Any way to restart the whole thing?  Ie, downgrade, then upgrade?  Please post step-by-step, thanks!

---

### Post by Ev1L on 2009-09-23
from here:
[https://launchpad.net/~linux-phc/+archive/ppa](https://launchpad.net/~linux-phc/+archive/ppa)

Follow exactly the instructions in the link "Read about installing"
Especially the part adding the key to authenticate the repository

---

### Post by beezwings on 2009-09-23
I had already done that.  I followed the exact steps again anyway.  Still, there's no sign of a 2.6.28-15 ~undervolt kernel.  Looks like someone else in this forum had the problem of downloading the 2.6.28.13 ~undervolt kernel, but the system wasn't recognizing it to be undervolted.  Don't know how she fixed it though.

---

### Post by Ev1L on 2009-09-24
i am sorry but i wouldn't know what else to try without having the machine in my hands.
from synaptic you can't see 2.6.28.15 installable/upgradable?
when i added the repository here, i could see such kernel to upgrade but i can't remember if it was clear it was the undervolt one if not looking at the properties of the package or doing uname -a after installing it

---

### Post by beezwings on 2009-09-24
No, there isn't anything to upgrade...the only versions of 2.6.28.15 is the one I currently have (not the ~undervolt).  Too bad.

---

### Post by winnibob on 2009-09-24
> **beezwings said:**
> Not solved yet...I couldn't  find anything with 2.6.28-15 ~undervolt in the repositories, so I tried installing 2.6.28-13 ~undervolt a few days ago. Now I have some strange mix.  What is installed is the following:


linux-headers-2.6.28-13 ~undervolt5
linux-headers-2.6.28-13-generic ~undervolt5
linux-image-2.6.28-13-generic  ~undervolt5
linux-image-2.6.28-15-generic
linux-image-generic (version 2.6.28-15.20)

Could you tell us where you found the packages for 2.6.28-13~undervolt5 , since I can't find them any more on the ppa? Did you just update the kernel via update-manager or synaptics, or did you get these packages from somewhere else?
Anyway, you could try undervolting with this older kernel, choosing it at startup in grub.

If you can't connect to linux-phc's ppa for updates, you can download udeb packages of the most recent version (i.e. 2.6.28-15.50 for now) [here]("https://launchpad.net/~linux-phc/+archive/ppa/+packages"), but it is not really safe because your system can't check the authenticity of the packages as update-manager do.
The best way to get ~undervolt kernel is to find out why you can't connect to the ppa for updating you current kernel

---

### Post by Uhuu on 2009-10-03
2.6.28-15 undervolt-kernel was in the ppa few weeks ago, but now synaptic only offers 2.6.28-11 :confused:


EDIT:

downloaded kernel manually from [https://launchpad.net/~linux-phc/+archive/ppa/+sourcepub/705101/+listing-archive-extra](https://launchpad.net/~linux-phc/+archive/ppa/+sourcepub/705101/+listing-archive-extra)

now all works

---

### Post by htrex on 2009-10-05
the latest version from jaunty-updates is 2.6.28-15.52 while on [https://launchpad.net/~linux-phc/+archive/ppa](https://launchpad.net/~linux-phc/+archive/ppa) is 2.6.28-15.50.

I seriously hope Karmic is not shipping with acpi modules compiled into kernel.

(please vote [http://brainstorm.ubuntu.com/idea/20847/](http://brainstorm.ubuntu.com/idea/20847/) if you care about this too)

---

### Post by mister_playboy on 2009-10-10
> **htrex said:**
> the latest version from jaunty-updates is 2.6.28-15.52 while on [https://launchpad.net/~linux-phc/+archive/ppa](https://launchpad.net/~linux-phc/+archive/ppa) is 2.6.28-15.50.

I seriously hope Karmic is not shipping with acpi modules compiled into kernel.

(please vote [http://brainstorm.ubuntu.com/idea/20847/](http://brainstorm.ubuntu.com/idea/20847/) if you care about this too)

I agree.  I'm still running 2.6.28-11 since I haven't been able to get undervolting in anything newer.

I won't be moving to 9.10 without undervolting... :(

---

### Post by kevinguillorytraining on 2009-10-10
I followed all of your instructions but my Latitude E6400 battery not increased more than half hour. Is it possible to increase more time?

---

### Post by mister_playboy on 2009-10-10
> **kevinguillorytraining said:**
> I followed all of your instructions but my Latitude E6400 battery not increased more than half hour. Is it possible to increase more time?

Generally speaking, lowering the CPU temp is the main advantage of undervolting.  It won't increase the battery life too much since the CPU doesn't use much power compared to the screen or hard drive... 30 minutes is probably as good as could be expected.

---

### Post by Uhuu on 2009-10-30
Anybody got this working on Karmic?

---

### Post by tula on 2009-11-11
still not working on karmic koala + turion x2 RM processor ?

---

### Post by zcats on 2009-11-26
Undervolting for 9.10 Karmic was as simple as adding the ppa for PHC  and installing the kernel 2.6.31-14-generic-phc using synaptic.
BTW I have a Pentium M processor 1.70GHz and previously had acpi-cpufreq.ko in home (separate partition) before I upgraded to karmic
Of course I still needed to determine and set my optimal values and edit your /etc/rc.local file to make permanent. Add this (using *your* values):-
echo "17:19 14:12 12:18 10:4 8:1 6:1" > /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
exit 0

The 2.6.31-15-generic-phc is not in the phc ppa yet so I am staying with 2.6.31-14-generic-phc (a bit behind on kernel updates, but thats OK;)

---

### Post by zcats on 2009-12-01
Ermmmm.  This is not quite right, sorry!. Please see my other Ubuntu post in
"Undervolting in Karmic on a Pentium M - a Howto".

Use the instructions by Ebsbel and it works on Karmic..:p

---

### Post by zcats on 2009-12-01
see
[http://ohioloco.ubuntuforums.org/showthread.php?p=8418342#post8418342](http://ohioloco.ubuntuforums.org/showthread.php?p=8418342#post8418342)

---

### Post by aldeby on 2010-01-04
[QUOTE=asuna;7644198]Ok thanks for all the help
EDIT:
Finally got it to work!

After I downloaded and used PHC Tool

From [http://aldeby.org/blog/index.php/linux-phc-cpu-undervolting.html](http://aldeby.org/blog/index.php/linux-phc-cpu-undervolting.html):

Thank you asuna for quoting my post. 
Although the actual blog page is [http://linux.aldeby.org/linux-phc-cpu-undervolting.html]("http://linux.aldeby.org/linux-phc-cpu-undervolting.html")

---

### Post by H.i.M on 2010-01-16
I installed the phc kernel by the ppa:linux-phc/ppa.

```
uname -r
2.6.31-17-generic-phc

```


Could someone tell me where the phc_controls-file is gone?
Isnt the phc kernel the right one to undervolt?

```
ls -a /sys/devices/system/cpu/cpu0/cpufreq/
.   affected_cpus     cpuinfo_max_freq  cpuinfo_transition_latency  related_cpus                   scaling_available_governors  scaling_driver    scaling_max_freq  scaling_setspeed
..  cpuinfo_cur_freq  cpuinfo_min_freq  ondemand                    scaling_available_frequencies  scaling_cur_freq             scaling_governor  scaling_min_freq  stats

```

thanks
h.i.m

---

### Post by mister_playboy on 2010-01-19
Honestly, we really need a new thread for this topic.  The instruction in the first post don't work for any recent kernel and most people aren't going to dig through this whole thread to find the answer.

Anybody who knows exactly what they are doing want to start a new one?  I will admit I'm not the one to do it... ;)

---

### Post by Ares Drake on 2010-01-20
> **mister_playboy said:**
> Honestly, we really need a new thread for this topic.  The instruction in the first post don't work for any recent kernel and most people aren't going to dig through this whole thread to find the answer.

Anybody who knows exactly what they are doing want to start a new one?  I will admit I'm not the one to do it... ;)

Unfortunately I currently find no time at all for updates in this matter.

If you however want the first post changed, either with a link to a new thread or with new, provided information & guidelines I am more than willing to help!

Greetz
Drake

---

### Post by jocko on 2010-02-13
> **H.i.M said:**
> I installed the phc kernel by the ppa:linux-phc/ppa.

```
uname -r
2.6.31-17-generic-phc

```
Could someone tell me where the phc_controls-file is gone?
Isnt the phc kernel the right one to undervolt?

```
ls -a /sys/devices/system/cpu/cpu0/cpufreq/
.   affected_cpus     cpuinfo_max_freq  cpuinfo_transition_latency  related_cpus                   scaling_available_governors  scaling_driver    scaling_max_freq  scaling_setspeed
..  cpuinfo_cur_freq  cpuinfo_min_freq  ondemand                    scaling_available_frequencies  scaling_cur_freq             scaling_governor  scaling_min_freq  stats

```thanks
h.i.m
Any news on this? None of the phc kernels after 2.6.31-14-generic-phc has any phc_controls file. Interesting how the acpi-cpufreq module in the phc kernel seems to be built without phc support... Or have they just changed how it works and forgotten to inform the users?

---

### Post by jocko on 2010-02-13
> **jocko said:**
> Any news on this? None of the phc kernels after 2.6.31-14-generic-phc has any phc_controls file. Interesting how the acpi-cpufreq module in the phc kernel seems to be built without phc support... Or have they just changed how it works and forgotten to inform the users?
Found the answer to my own question. Apparently the patched module is no longer included in the phc kernel (why?), so this has to be done by the user...

This is how to get it working with an intel cpu:
1. Boot into the latest phc kernel.
2. Download the linux-phc patch from [here]("http://www.linux-phc.org/forum/viewtopic.php?f=13&t=2") (get the latest intel "offtree" patch).
3. Unpack the tar.bz2 file.
4. Build and install the patched module (instructions from the included README file):
```
make prepare
make
sudo make install

```
5. Reboot into the same kernel.

Note that this was the simple process for the "offtree" patch, which as far as I can see is only available for intel at the moment. The amd patches use dkms to build ad install the module.

---

### Post by Ev1L on 2010-02-13
I can confirm that is the current easiest procedure.

> **jocko said:**
> Note that this was the simple process for the "offtree" patch, which as far as I can see is only available for intel at the moment. The amd patches use dkms to build ad install the module.

There are separate instructions for amd somewhere on phc website.
But once you get dkms working, you won't need future compiling at each phc kernel upgrade (as it is for intel offtree).

---

### Post by karunadheera on 2010-02-19
I do not get the file content of "phc_tweaked_vids" as freq:voltage pairs.
It contains only following.

7 7 7 1 1

What should I echo to pch_controls then? 

Thanks in advance.

---

### Post by beezwings on 2010-03-11
Hi~

Can someone help?  I used to have my laptop undervolted. Since my upgrade to a few days ago to Karmic koala, I get through to all the undervolting steps, but for some reason, when I reboot, the system doesn't seem to be reading the rc.local file, since my values are still the same.  When I try either sudo echo "11:22 8:1 6:1" > /sys/devices/system/cpu/cpu0/cpufreq/phc_controls, I get a "permission denied" message. I'm a newbie, so please walk me through, thanks!

---

### Post by kasjak2000 on 2010-03-11
> **beezwings said:**
> Hi~

Can someone help?  I used to have my laptop undervolted. Since my upgrade to a few days ago to Karmic koala, I get through to all the undervolting steps, but for some reason, when I reboot, the system doesn't seem to be reading the rc.local file, since my values are still the same.  When I try either sudo echo "11:22 8:1 6:1" > /sys/devices/system/cpu/cpu0/cpufreq/phc_controls, I get a "permission denied" message. I'm a newbie, so please walk me through, thanks!

Hi,

please try this with help of tee.

echo "11:22 8:1 6:1" | sudo tee /sys/devices/system/cpu/cpu0/cpufreq/phc_controls

and th same for cpu1, if you have one with 2 cores.

---

### Post by beezwings on 2010-03-11
> **kasjak2000 said:**
> Hi,

please try this with help of tee.

echo "11:22 8:1 6:1" | sudo tee /sys/devices/system/cpu/cpu0/cpufreq/phc_controls

and th same for cpu1, if you have one with 2 cores.

Great, that works for this session, but when I reboot, it still resets. How can I load that for every boot?

Additionally, I have a program called "vaiofand" that I would also like to run at every boot. How would I add that as well?

Thanks!

---

### Post by kasjak2000 on 2010-03-12
> **beezwings said:**
> Great, that works for this session, but when I reboot, it still resets. How can I load that for every boot?

Additionally, I have a program called "vaiofand" that I would also like to run at every boot. How would I add that as well?

Thanks!

Hey cool :)

Ok, please add this 2 lines (if you have one with 2 cores, if you have 1 core, the first line only ) into the /etc/rc.local with sudo vi /etc/rc.local


echo "11:22 8:1 6:1" > /sys/devices/system/cpu/cpu0/cpufreq/phc_controls

echo "11:22 8:1 6:1" > /sys/devices/system/cpu/cpu1/cpufreq/phc_controls


Now make a reboot and debug the settings with:

cat /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
and
cat /sys/devices/system/cpu/cpu1/cpufreq/phc_controls

---

### Post by beezwings on 2010-03-12
> **kasjak2000 said:**
> Hey cool :)

Ok, please add this 2 lines (if you have one with 2 cores, if you have 1 core, the first line only ) into the /etc/rc.local with sudo vi /etc/rc.local


echo "11:22 8:1 6:1" > /sys/devices/system/cpu/cpu0/cpufreq/phc_controls

echo "11:22 8:1 6:1" > /sys/devices/system/cpu/cpu1/cpufreq/phc_controls


Now make a reboot and debug the settings with:

cat /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
and
cat /sys/devices/system/cpu/cpu1/cpufreq/phc_controls

I had done this previously, but it seems this file is not being read at reboot because when I run the cat /sys/devices/system/cpu/cpu0/cpufreq/phc_controls I get my old values and have to sudo tee again manually.  

Additionally, how can I run the vaiofand command automatically at startup (requires root).

Thanks!

---

### Post by kasjak2000 on 2010-03-12
> **beezwings said:**
> I had done this previously, but it seems this file is not being read at reboot because when I run the cat /sys/devices/system/cpu/cpu0/cpufreq/phc_controls I get my old values and have to sudo tee again manually.  

Additionally, how can I run the vaiofand command automatically at startup (requires root).

Thanks!

Regarding the /etc/rc.local -> it has to end with exit 0 in the last line.

Is it so in your rc.local?

Regarding the autostart of programs, please check .config/autostart/ directory in your home. There are some *.desktop files. Just study some of them.

[http://wiki.ubuntuusers.de/autostart](http://wiki.ubuntuusers.de/autostart)

Good luck

---

### Post by beezwings on 2010-03-12
Thanks for the info.

Unfortunatly, I already had exit 0 as the last line of rc.local, so the problem seems to be something else. Any ideas?

---

### Post by kasjak2000 on 2010-03-16
> **beezwings said:**
> Thanks for the info.

Unfortunatly, I already had exit 0 as the last line of rc.local, so the problem seems to be something else. Any ideas?

Please check the output of chkconfig -list

This should be something like that:

```
rc.local                  0:off  1:off  2:on   3:on   4:on   5:on   6:off
```

Here you can see, that the rc.local starts in runlevels 2, 3, 4 and 5(GUI).

I have a speculation, that your rc.local doesnt start.

best regards
kasjak2000

---

### Post by beezwings on 2010-03-16
> **kasjak2000 said:**
> Please check the output of chkconfig -list

This should be something like that:

```
rc.local                  0:off  1:off  2:on   3:on   4:on   5:on   6:off
```

Here you can see, that the rc.local starts in runlevels 2, 3, 4 and 5(GUI).

I have a speculation, that your rc.local doesnt start.

best regards
kasjak2000

That's exactly what it outputs...what to do now?

---

### Post by kasjak2000 on 2010-03-16
> **beezwings said:**
> That's exactly what it outputs...what to do now?

Oh man, sorry, i dont know anymore :(

Colleagues, could you please assist here?

---

### Post by ChaosHead on 2010-03-19
Hi
I am wondering if there is any update on undervolting cpus on amd platform. 
Last 4-5 months I was trying to get started with undervolting of my laptops MV-40(amd neo) cpu, but I could not find any guide. All guys/girls are just talking about intel... 
Is there actually anyone who undervolts those cpus? Here is my laptop: 

[http://arstechnica.com/hardware/news/2009/01/amds-neo-processor-debuts-in-hp-notebook-whoah.ars](http://arstechnica.com/hardware/news/2009/01/amds-neo-processor-debuts-in-hp-notebook-whoah.ars)

This is the only thing that holds me back from abadoning windows. :(.

---

### Post by nema.arpit on 2010-03-20
I don't know if it'll work,but try this thread:
[http://ubuntuforums.org/showthread.php?t=1433885](http://ubuntuforums.org/showthread.php?t=1433885)

---

### Post by ChaosHead on 2010-03-20
Thanks for making a guide specially for me. You are the best ;).
I'll tell all my friends in Norway about great ubuntu-community.
I can finally sit down and get my computer running cool... 
It will not be forgotten, may force be with you.

---

### Post by NESFreak on 2010-05-06
Hi, i'm heaving some problems with the optimization script: it forces my laptop into thermal throttling (dell m1330 damn this thing runs hot), resulting in quite unreliable results.

So if by any chance anyone has an intel T8100 could there be any chance of sharing your optimal values with me? On some german forum I've already found the following values 75:27 74:27 8:23 6:19 136:15 and for now it seems to be working quite well.

thanks

(PS. maybe it would be a good idea to make a wiki page of all the processors and their optimal values. Just a thought.)

---

### Post by mihai.ile on 2010-05-08
Hello.
I created a updated guide for Ubuntu 10.04LTS, with a new script that checks the minimum voltage that works for multi core cpu's.
Take a look at
[http://openmindedbrain.info/09/05/2010/undervolting-in-ubuntu-10-04-lucid-lts/](http://openmindedbrain.info/09/05/2010/undervolting-in-ubuntu-10-04-lucid-lts/)

---

### Post by Naaktgeboren on 2010-05-12
beezwings: As regards [vaiofand]("http://vaio-utils.org/fan/"), if you install the Debian package from [https://launchpad.net/~vaiofand/+archive/ppa]("https://launchpad.net/~vaiofand/+archive/ppa"), it will be started automatically upon boot.

---

### Post by zcats on 2010-06-01
:guitar::guitar::guitar::guitar
LOOK here
[http://openmindedbrain.info/09/05/2010/undervolting-in-ubuntu-10-04-lucid-lts/](http://openmindedbrain.info/09/05/2010/undervolting-in-ubuntu-10-04-lucid-lts/)

Instructions copied below....
   1. As we are going to use a custom kernel, we need to add the linux-phc PPA repository, so just open a terminal and execute:
   
      1	$ sudo add-apt-repository ppa:linux-phc/ppa
      2	$ sudo apt-get update
      Basically they provide the same kernel as the Ubuntu one but with the patch that is capable for Undervolting.
   2. Next we need to install the phc kernel, with headers:
   
      1	$ sudo apt-get install linux-generic-phc linux-headers-generic-phc
      Ok, now we need to restart and use the installed phc kernel when booting. After restarting, you can check if you are using the phc kernel by using
    
      1	$ uname -r
      2	2.6.32-21-generic-phc
      If no "phc" appears, then you have to configure grub2 to allow you to chose boot options and select the phc kernel at boot time. This can be done many ways one would be:
   *(This section was NOT necessary for me....   zcats)* 

 1	sudo update-grub
      and count the number of lines that says "Found linux image" (first one is 0) and, when you found the phc one, do:
    
      1	sudo gedit /etc/default/grub
      then just change the "GRUB_DEFAULT=0" to the number of the entry you found that has phc. Save the file and do a update-grub command again like in the first step. Now you can reboot into the phc kernel.
   3. Great, we are using a phc kernel, now we need to add the actual undervolt module, as the kernel comes only with support for it, not the actual module. First download phc-intel offtree module from here. Right now they have "phc-intel-0.3.2-10 offtree" version. Direct link to the tar.bz2 file here. Unpack the files anywhere and point the terminal to the directory where you extracted the files and do:
    
      1	$ make prepare
      2	$ make
      3	$ sudo make install
      Right now you should have the module installed, check if everything worked by typing:
 
      1	$ cat /sys/devices/system/cpu/cpu0/cpufreq/phc_default_vids
      2	40 34 31 27 23 15
      If everything worked, you should see some numbers (the ones above are the default ones for my CPU). If not, you may try to restart and check back to see if it works.
   4. So right now we are set, the only thing we have to do is... undervolt the CPU.
      Now we have to discover the limits of the CPU by lowering it's current voltage one step at a time and set the voltage 4 steps above the critical limit (where the cpu starts to give wrong calculations or the PC simply crashes).

      Why four? Well the recommendation was 2 steps above, but with this limit the PC crashed in the same day hours later, so I made it 3 steps, then some days after it crashed again. So I think 4 steps should actually do it. If not, you may increase this value until it suits you.

      Ok great now how to find the actual critical limit? There exists a script, created by the community, but it's old and it does not work for multi core CPU's and also in my particular case it sets the voltage directly below this critical limit so the PC crashes instantly.

      I updated this script and made it work on multi core CPU's (hopefully it will work for you too), so you just have to download the script, then give it execution permissions and execute it and follow on-screen indications see [http://openmindedbrain.info/wp-content/uploads/2010/05/intel-phc-undervolt.bash:](http://openmindedbrain.info/wp-content/uploads/2010/05/intel-phc-undervolt.bash:)
   
      1	$ chmod +x intel-phc-undervolt.bash
      2	$ ./intel-phc-undervolt.bash
      Oh and make sure you close as many applications as possible when executing the script as the system may actually turn instable (it is intended actually) just to prevent any data loss. The script treats all CPU's cores with the same voltages, so if one of them is weaker than the other (does not support such a aggressive undervolting) is this the critical value that the script uses for all of the others, even if they could possibly use a even lower value.
   5. After you finished with the script, now you should have a "phc_tweaked_vids" file, containing the acceptable steps for your CPU. Now you only have to make changes permanent (load them at every boot of the pc) by editing /etc/rc.local file:
  
      1	$ sudo gedit /etc/rc.local
      and adding one entry for every core you have, something like:
  
      1	echo "23 20 4 4 4 4" > /sys/devices/system/cpu/cpu0/cpufreq/phc_vids
      2	echo "23 20 4 4 4 4" > /sys/devices/system/cpu/cpu1/cpufreq/phc_vids
   
      just before the "exit 0". Note that "23 20 4 4 4 4" are my values, you have to replace the above with your values, that came from the "phc_tweaked_vids" file. So that's about it. Not too easy, not too complicated.

So... is it worth it? I have done some tests to see if the above actually works as said, so first I tested to see if on battery using powertop application and the CPU temperature I could see any differences. None actually, if the CPU is in idle state, there is no actual gain using undervolting, be it battery or temperature.

But when I've done the test under full load (using 2 burnMMX instances, one for every core) and with the CPU set at it's maximum 2.4Ghz I could see a very very noticeable difference.

see website for data of temp and energy (W) saved:):):)

---

### Post by Vladimir_S on 2010-06-28
Please, who can tell me, what is wrong?
```

vladimir@vladimir-laptop:~/Downloads/phc-intel-0.3.2-10$ make prepare
FOUND AVAILABLE PATCHSET. PREPARING.
patching file phc-intel.c
vladimir@vladimir-laptop:~/Downloads/phc-intel-0.3.2-10$ make
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/vladimir/Downloads/phc-intel-0.3.2-10 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic-phc'
  CC [M]  /home/vladimir/Downloads/phc-intel-0.3.2-10/phc-intel.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/vladimir/Downloads/phc-intel-0.3.2-10/phc-intel.mod.o
  LD [M]  /home/vladimir/Downloads/phc-intel-0.3.2-10/phc-intel.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic-phc'
vladimir@vladimir-laptop:~/Downloads/phc-intel-0.3.2-10$ sudo make install
install -m 644 -o root -g root phc-intel.modprobe /etc/modprobe.d/phc-intel.conf
mkdir -p /lib/modules/2.6.32.11+drm33.2/extra
install -m 644 -o root -g root phc-intel.ko /lib/modules/2.6.32.11+drm33.2/extra/
depmod 2.6.32.11+drm33.2 -a
vladimir@vladimir-laptop:~/Downloads/phc-intel-0.3.2-10$ cat /sys/devices/system/cpu/cpu0/cpufreq/phc_default_vids
cat: /sys/devices/system/cpu/cpu0/cpufreq/phc_default_vids: No such file or directory
vladimir@vladimir-laptop:~/Downloads/phc-intel-0.3.2-10$ 

```

Ubuntu 10.04. My CPU is Core2Duo T5600 (Mobile) And i used manual in previous post by zcats(#481)

Thank You!

---

### Post by nicocarbone on 2010-08-02
I am having the same problem that Vladimir_S. I am using a Core 2 Duo T5550 laptop on Ubuntu 10.4 amd64.

Any ideas??

---

### Post by jocko on 2010-08-03
> **Vladimir_S said:**
> Please, who can tell me, what is wrong?
```

vladimir@vladimir-laptop:~/Downloads/phc-intel-0.3.2-10$ make prepare
FOUND AVAILABLE PATCHSET. PREPARING.
patching file phc-intel.c
vladimir@vladimir-laptop:~/Downloads/phc-intel-0.3.2-10$ make
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/vladimir/Downloads/phc-intel-0.3.2-10 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic-phc'
  CC [M]  /home/vladimir/Downloads/phc-intel-0.3.2-10/phc-intel.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/vladimir/Downloads/phc-intel-0.3.2-10/phc-intel.mod.o
  LD [M]  /home/vladimir/Downloads/phc-intel-0.3.2-10/phc-intel.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic-phc'
vladimir@vladimir-laptop:~/Downloads/phc-intel-0.3.2-10$ sudo make install
install -m 644 -o root -g root phc-intel.modprobe /etc/modprobe.d/phc-intel.conf
mkdir -p /lib/modules/2.6.32.11+drm33.2/extra
install -m 644 -o root -g root phc-intel.ko /lib/modules/2.6.32.11+drm33.2/extra/
depmod 2.6.32.11+drm33.2 -a
vladimir@vladimir-laptop:~/Downloads/phc-intel-0.3.2-10$ cat /sys/devices/system/cpu/cpu0/cpufreq/phc_default_vids
cat: /sys/devices/system/cpu/cpu0/cpufreq/phc_default_vids: No such file or directory
vladimir@vladimir-laptop:~/Downloads/phc-intel-0.3.2-10$ 

```Ubuntu 10.04. My CPU is Core2Duo T5600 (Mobile) And i used manual in previous post by zcats(#481)

Thank You!

> **nicocarbone said:**
> I am having the same problem that Vladimir_S. I am using a Core 2 Duo T5550 laptop on Ubuntu 10.4 amd64.

Any ideas??

You need to reboot.

---

### Post by nicocarbone on 2010-08-03
The problem cannot be solved by rebooting (is the first thing I tried), but I found the solution.

The problem is related to a bug in the phc modified kernel 2.6.32-24-generic-pch. The file utsrelease.h, located in "/usr/src/linux-headers-2.6.32-24-generic-phc/include/linux" is used by the install script oh the intel-phc module to locate the kernel in use, but the string UTS_RELEASE is badly defined ([http://www.linux-phc.org/forum/viewtopic.php?f=9&t=211](http://www.linux-phc.org/forum/viewtopic.php?f=9&t=211)) Where it says "2.6.32.15+drm33.5", it should say "2.6.32-24-generic-phc".

Changing this line, and the repeating the install process, I could load the intel-phc module and I successfully undervolted my CPU. Now it uses 10w less under load and the temperatures are around 10-15C lower.

---

### Post by nicocarbone on 2010-08-03
Another question: Will it be necessary to repeat all the installation/undervolt process every time Ubuntu releases a new kernel?

Sorry If this was explained before, I couldn't read the 49 pages.

---

### Post by nicocarbone on 2010-08-03
Me again, with another question:
Everytime I suspend/resume the laptop, the volts are restored to defaults (at least I think this is what happens, because the watts used under load increase after a suspend/resume cycle). Is there a way to avoid this?

Thanks

---

### Post by phazixc on 2010-08-04
I'm Running:-

Toshiba q505 888

Ubuntu 10.04 lucid 64Bit

Core 7i q740
Nvidia Gts 360m 1gb
4 Gb Ram 


I Updated to 256.35  =  Excellent / perfect

Then my updates from X-swat and Xorg Egders updated to 256.44 this  =  my world falling apart.

My system completely locks up / hags / kills its self within 4 mins of logging in. 

If I load anything I.E wine to run a game. 

It really doesnt like that...   My problem is i'm only a year into ubuntu and I have done manual updates before, but what im doing isnt working as I have tried purge remove nvidia .44 and disabling the two ppa's then manually installing .35 ..

BUT

when I start the gdm = great it works, then when I restart = not great....because I'm on failsafe graphics and the x sever setting not in menu  (if it is in menu then theres nothing in there; apart from that msg to restart X) and when I load Hardware drivers the nvidia card isnt there..

I would like to think that some of your reading this are laughing because you are what I would call a pro in the ubuntu area and that you could / will post a detailed step by step to help me install .35 through the x-swat or x-org egder ppa or even manually download it and install it that way, so when I restart it works, and more to the point I can keep those two ppa's in my system so when i hit the update button I can see ubuntu wants to update to .44 which I WONT DO....

One year into ubuntu and I haven't logged into windows since.

As I find theres always someone will to help fix something in ubuntu..

anyway thats that, Mr/Mrs pro.... can you post that guide please.

P.S im currently on Linux-x86_64 NVIDIA Driver Version: 195.36.24 Server Version Number: 11.0 and Server Vendor Version: 1.8.2  NV-CONTROL Version: 1.22
gnome 2.30.2  and kernel linux 2.6.32-24 generic
platform X86_64



Thanks

---

### Post by nicocarbone on 2010-08-04
phazixc: 

I would like to help you, but I have no experience in Nvidia drivers under Ubuntu. I would suggest you to purge the ppa, but you already did this, so I am out of ideas. 

What I suggest you is to open a new thread posting you problem, because it is completely off-topic here. Posting a new topic (in Absolute Beginner Talk, or maybe one of the Main Support Categories, like Multimedia and Video) will surely make it viewable to more people, and I am sure someone with the required experience in Nvidia drivers will help you.

---

### Post by phazixc on 2010-08-04
yeap no problem, i thought i posted this in a different form, sorry and thanks anyway.

---

### Post by lemino on 2010-11-22
Great info, allthough it didn't do the trick for me. Everything seems to be ok: i changed the file so that it pointed to the right kernel, saved, repeated the install process whithout any errors, everything looked right. But when I try to do 

cat sys/devices/system/cpu/cpu0/cpufreq/phc_default_vids

it says that it can't find that file, and it's right, the folder "cpufreq" doesn't exist in cpu0. It does exist in "cpu" however, but is empty.

What can be done about this?

/Erik

---

### Post by Docet on 2011-03-04
I found a new guide that also includes the graphiocal tool to set VIDs... take a look here!

```
[http://linuxsolver.blogspot.com/2011/02/undervolting-cpu-in-ubuntu.html](http://linuxsolver.blogspot.com/2011/02/undervolting-cpu-in-ubuntu.html)
```Cheers!

---

### Post by ursoouindio on 2011-03-10
Hi.

I'm having troubles to follow the steps on this guide: [http://openmindedbrain.info/09/05/2010/undervolting-in-ubuntu-10-04-lucid-lts/](http://openmindedbrain.info/09/05/2010/undervolting-in-ubuntu-10-04-lucid-lts/)


I manage to get to step 2 ok:
```
$ uname -r
2.6.32-29-generic-phc
```

But on step 3 i get:
(I've used the [tar.bz2 file]("http://www.linux-phc.org/forum/download/file.php?id=87&sid=b05ae625e9678a0efa00fa1d72631d68") suggested on the how-to)
```
$ sudo make prepare
[sudo] password for marco: 
FOUND AVAILABLE PATCHSET. PREPARING.
patching file phc-intel.c
```

```
$ sudo make
make -C /lib/modules/`uname -r`/build SUBDIRS= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-29-generic-phc'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
make[2]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make[1]: *** [prepare0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-29-generic-phc'
make: *** [phc-intel.ko] Error 2
```

```
$sudo make install
make -C /lib/modules/`uname -r`/build SUBDIRS= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-29-generic-phc'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
make[2]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make[1]: *** [prepare0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-29-generic-phc'
make: *** [phc-intel.ko] Error 2
```

So please help me as my notebook is getting too hot even after a good cleanup. And I don't know much about those kernel errors :/


well.. I think I figured it out. Just comparing with other how-to suddenly it worked. Thanks anyway.

---

### Post by ursoouindio on 2011-03-22
I have undervolted my processor, it is now cooler and quieter :)

But, I noticed I'm still getting the 'normal' kernel updates and compiling them. Just after a while I download the phc version.

As new kernels are released all the time, it seems that I get half the time without the undervolting on my notebook.

How to disable the 'normal' kernel upgdates and leave just the customized phc one?

Thanks

---

### Post by Axa-Ru on 2011-08-15
Hi.
Laptop: Lenovo Thinkpad x220
CPU: i7-2620M
```
$ cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 42
model name    : Intel(R) Core(TM) i7-2620M CPU @ 2.70GHz
stepping    : 7
cpu MHz        : 800.000
cache size    : 4096 KB
physical id    : 0
siblings    : 4
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 x2apic popcnt xsave avx lahf_lm ida arat epb xsaveopt pln pts dts tpr_shadow vnmi flexpriority ept vpid
bogomips    : 5381.84
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:
```


I downloaded and installed the kernel
```
$ uname -r
2.6.38-8-generic-pae-phc 
```I downloaded from here [http://aur.archlinux.org/packages.php?ID=24980](http://aur.archlinux.org/packages.php?ID=24980) [phc-intel-pack-rev2.tar.bz2]("http://www.linux-phc.org/forum/download/file.php?id=127"), compiled and instlled the phc module:
```
$ lsmod | grep phc
phc_intel              17942  1 
mperf                  12603  1 phc_intel

```After reboot i have this:
```
$ cat /sys/devices/system/cpu/cpu0/cpufreq/phc_version
0.3.2:2
$ cat /sys/devices/system/cpu/cpu0/cpufreq/phc_fids
34 27 24 22 20 18 16 14 12 10 8
$ cat /sys/devices/system/cpu/cpu0/cpufreq/phc_default_vids
0 0 0 0 0 0 0 0 0 0 0 
$ cat /sys/devices/system/cpu/cpu0/cpufreq/phc_vids
0 0 0 0 0 0 0 0 0 0 0
$ cat /sys/devices/system/cpu/cpu0/cpufreq/phc_default_controls
34:0 27:0 24:0 22:0 20:0 18:0 16:0 14:0 12:0 10:0 8:0

```Where did I go wrong?
Thanks in advance,
Alex.


[U]Update                                                                                                 .
[/U]Compile with "make brave"

```
$ ls /sys/devices/system/cpu/cpu0/cpufreq/phc_*
/sys/devices/system/cpu/cpu0/cpufreq/phc_default_rawcontrols
/sys/devices/system/cpu/cpu0/cpufreq/phc_default_vids
/sys/devices/system/cpu/cpu0/cpufreq/phc_rawcontrols
/sys/devices/system/cpu/cpu0/cpufreq/phc_version
/sys/devices/system/cpu/cpu0/cpufreq/phc_vids
$ cat /sys/devices/system/cpu/cpu0/cpufreq/phc_default_rawcontrols
00002200 00001b00 00001800 00001600 00001400 00001200 00001000 00000e00 00000c00 00000a00 00000800
$ cat /sys/devices/system/cpu/cpu0/cpufreq/phc_default_vids
0 0 0 0 0 0 0 0 0 0 0
$ cat /sys/devices/system/cpu/cpu0/cpufreq/phc_rawcontrols
00002200 00001b00 00001800 00001600 00001400 00001200 00001000 00000e00 00000c00 00000a00 00000800
$ cat /sys/devices/system/cpu/cpu0/cpufreq/phc_version
0.3.199-2
$ cat /sys/devices/system/cpu/cpu0/cpufreq/phc_vids
0 0 0 0 0 0 0 0 0 0 0
```

---

### Post by ShamoIdol on 2011-12-31
> **Axa-Ru said:**
> Hi.
Laptop: Lenovo Thinkpad x220

$ cat /sys/devices/system/cpu/cpu0/cpufreq/phc_default_vids
0 0 0 0 0 0 0 0 0 0 0 
$ cat /sys/devices/system/cpu/cpu0/cpufreq/phc_vids
0 0 0 0 0 0 0 0 0 0 0


I have exactly the same ThinkPad and the same problem. Googling gives only the same reports with X220.

---

### Post by ShamoIdol on 2012-01-01
Also you might be interested in what I've found so far.

1. Undervolting of i7 2620m seems to be not possible. Or at least so far I'm not able to find a solution.
2. Install liqourix kernel, boot with "i915.i915_enable_rc6=1" and do not use any other power-related options including pcie_aspm and you'll get around 5.6 Watt in pure iddle (no radio, min backlight, no Xorg) and around 7-9 in Desktop iddle.

Read this for more info:
[http://liquorix.net/](http://liquorix.net/)

Works like a sharm in Kubuntu oneiric.

---

### Post by drklunk on 2012-01-04
Im in the process of undervolting my CPU in 10.04 LTS using this guide: [http://openmindedbrain.info/09/05/20...-04-lucid-lts/](http://openmindedbrain.info/09/05/20...-04-lucid-lts/)

my uname -r returned 2.6.32-37, no -phc, so I needed to go into gedit to change "GRUB_DEFAULT=0" to the corresponding line's number. my question is do I count only the "linux image" lines or also the "initrd image" lines?

update-grub returned 
```

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-37-generic
Found initrd image: /boot/initrd.img-2.6.32-37-generic
Found linux image: /boot/vmlinuz-2.6.32-36-generic
Found initrd image: /boot/initrd.img-2.6.32-36-generic
Found linux image: /boot/vmlinuz-2.6.32-33-generic-phc
Found initrd image: /boot/initrd.img-2.6.32-33-generic-phc
Found linux image: /boot/vmlinuz-2.6.32-33-generic
Found initrd image: /boot/initrd.img-2.6.32-33-generic
Found memtest86+ image: /boot/memtest86+.bin
done

```
I tried switching "GRUB_DEFAULT" to 2 as well as 4, then ran uname -r again after saving both times and it returned 2.6.32-37 as it did before.

---

### Post by Ares Drake on 2012-01-05
> **drklunk said:**
> 

my uname -r returned 2.6.32-37, no -phc, so I needed to go into gedit to change "GRUB_DEFAULT=0" to the corresponding line's number. my question is do I count only the "linux image" lines or also the "initrd image" lines?


Grub counts the titles. First title is 0, second one is 1 and so on.

---

### Post by drklunk on 2012-01-05
> **Ares Drake said:**
> Grub counts the titles. First title is 0, second one is 1 and so on.

thanks man, Ill give it another go

---

### Post by gregd72002 on 2012-10-30
Hello everyone,

I was just wondering - any chance of getting this working on 12.10?

Any success stories?  :)

---

### Post by ivotkl on 2013-01-13
Reviving an old thread here. Apparently PHC is no longer available (or not supported on 3.0+ Kernels).

Please see below and if you can help me, I would really appreciate it. For those who read this and cannot assist me, thank you as well for your time. =)

```
$ sudo apt-get install linux-generic-phc linux-headers-generic-phc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 linux-headers-generic-phc : Depends: linux-headers-3.2.0-25-generic-phc but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

Same / similar error appeared before and I did update -f, which I thought fixed it. It did not.

---

### Post by Ares Drake on 2013-01-14
Sorry I cannot help you. I switched to CentOS due to the recent decisions from the ubuntu leadership.

Best wishes
Ares Drake

---

### Post by ivotkl on 2013-01-14
Thank you anyways. I will try workaround suggested [here](http://ubuntuforums.org/showpost.php?p=12453749&postcount=2).

---

