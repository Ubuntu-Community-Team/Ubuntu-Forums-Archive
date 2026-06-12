---
title: "overheating ubuntu (trusty)"
date: 2014-03-14
forum: Ubuntu Development Version
---

### Post by cqpphp on 2014-03-14
Before this thing was happened, I have installed bumblebee, bumblebee-nvidia, and primus and my laptop temperature was decreasing to 55 Celcius.
But somehow, my Laptop temperature is getting higher than before. I didn't do any "heavy" stuff like gaming or video editing.

[IMG]http://i.imgur.com/8CV8Nyw.png[/IMG]
(now it's 80 Celcius)

I've tried to install the intel graphics driver and it didn't work.

```
steve@mesack-cmdsudo:~$ intel-linux-graphics-installerdiagnostics-view.c/new_diagnostic: Adding diagnostic for Checking if Intel graphics card available...
diagnostics-view.c/new_diagnostic: Adding diagnostic for Retrieving information from 01.org...
diagnostics-view.c/new_diagnostic: Adding diagnostic for Checking distribution...
diagnostics-view.c/new_diagnostic: Adding diagnostic for Checking kernel version...
diagnostics-view.c/new_diagnostic: Adding diagnostic for Checking available repositories...
diagnostics-view.c/new_diagnostic: Adding diagnostic for Checking package manager status...
No LSB modules are available.
polkit: Fetching org.01.linuxgraphics.installer permissions...
diagnostics-view.c/diagnostics_view_start: Running diagnostic Checking if Intel graphics card available...
diagnostics-view.c/diagnostics_view_start: Running diagnostic Retrieving information from 01.org...
{
  errors: (nil)
  sources: []
  keys: []
  docs: []
  INSTALL: []
  install: []
  upgrade: []
}
diagnostics-view.c/diagnostics_view_start: Running diagnostic Checking distribution...
&#62811; package_manager_is_distro_supported
&#62811; Configuration : Loading &#8230;  [   0 % ] &#9202;
{
  errors: (nil)
  sources: []
  keys: []
  docs: []
  INSTALL: []
  install: []
  upgrade: []
}
&#62811; package_manager_is_distro_supported
&#62811; Configuration : Loaded  [  80 % ] &#9202;
&#62811; package_manager_is_distro_supported
&#62811; Configuration : Testing &#8230;  [  80 % ] &#9202;
&#62811; package_manager_is_distro_supported
&#62811; Configuration : Complete  [  ] &#9702;
main-window.c/on_diagnostics_finished: Diagnostics finished with an error
steve@mesack-cmdsudo:~$ 



```

how can I lower my laptop temperature ?

side note : I use gdm, not lightdm. I've tried both of them but the results are the same.

---

### Post by 23dornot23d on 2014-03-14
I found when that happened once to me - I had to keep killing compiz off

but that happened about a week ago .... things settled back down again
after some upgrades.

Also I found that with the monitoring sensors working the temps shot up too.

Thing is you do not want to be leaving it for long like that .......

I use htop to kill processes off quickly that are causing me problems. ( but there are other ways )

its just that if I have htop running in a console that quickly doing (ctrl + alt + f1) with htop running
in terminal 1 then its just a case of picking the offending process and killing it off with F9 and return.

Compiz tends to shoot all the processes upto full .

But lately things have been ok on my own system.

[IMG]http://i.minus.com/ibhGcG7FuPgXTI.png[/IMG]

_____________________________________________________________

Just realized this is in absolute beginners section ....... really should not be using 14.04 until
its officially released as its in testing at the moment and does not come out until 17th April
for mainstream use.

---

### Post by cqpphp on 2014-03-14
> **23dornot23d said:**
> I found when that happened once to me - I had to keep killing compiz off

but that happened about a week ago .... things settled back down again
after some upgrades.

Also I found that with the monitoring sensors working the temps shot up too.

Thing is you do not want to be leaving it for long like that .......

I use htop to kill processes off quickly that are causing me problems. ( but there are other ways )

its just that if I have htop running in a console that quickly doing (ctrl + alt + f1) with htop running
in terminal 1 then its just a case of picking the offending process and killing it off with F9 and return.

Compiz tends to shoot all the processes upto full .

But lately things have been ok on my own system.

_____________________________________________________________

Just realized this is in absolute beginners section ....... really should not be using 14.04 until
its officially released as its in testing at the moment and does not come out until 17th April
for mainstream use.

there is no compiz in my htop thingy. when I search (F3) for "compiz". there's no results. any ideas ?

---

### Post by Toz on 2014-03-14
*Since Trusty Tahr is still in beta, moved to the **Ubuntu +1** subforum.*

---

### Post by 23dornot23d on 2014-03-14
Psensors - I actually uninstalled it too ..... as it was a cause more than a help

Conky was another thing at the time that shot the processors upto full  ..........

But most of it related to the older version I was using - as 14.04 gets updated daily

______________________________________________________________________

The top process&#8217;s used are at the top of the list and the bars on the top show if the computer is 
working harder than it need be - when you are doing little.

Can you do a screenshot and post it back - or switch off to get your temps back down
again .........  

The option of loading something like Lxde in might be the thing to do as it uses little resources
then use that desktop environment until you can work out what is happening there and making the
temps shoot up like that. ( could be a number of things )

______________________________________________________________________

Good the mod has moved it into the right place for answers .........

---

### Post by cqpphp on 2014-03-14
[IMG]http://i.imgur.com/vOmqXHR.png[/IMG]

quick update. when I want to install lxde, something is wrong.
> steve@mesack-cmdsudo:~$ sudo apt-get install lxdeReading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 bumblebee-nvidia : Depends: nvidia-driver but it is not installable or
                             nvidia-glx but it is not installable or
                             nvidia-kernel-dkms but it is not installable or
                             nvidia-kernel-amd64 but it is not installable or
                             nvidia-kernel-686-pae but it is not installable or
                             nvidia-kernel-486 but it is not installable or
                             nvidia but it is not installable or
                             nvidia-current but it is not going to be installed or
                             nvidia-current-updates but it is not going to be installed or
                             nvidia-driver-binary or
                             nvidia-...



Hopefully running apt-get -f install will fix the problem.

update 2 : nope. still same.

---

### Post by 23dornot23d on 2014-03-14
The HTOP listing ..... if you can show that it would help to show which process is being used the most.

If you have have gnome classic as a login choice use that or use gnome fallback .....

Then work from there as they should be less demanding ......

---

### Post by cqpphp on 2014-03-14
[IMG]http://i.imgur.com/05pQ2Kp.png[/IMG]

---

### Post by 23dornot23d on 2014-03-14
There is nothing that stands out on that listing ......

But remove psensor for the time being ..... as it caused me a problem too - and I run optimus the same with
bumblebee ... maybe there is a conflict somewhere between them ........

sudo apt-get remove psensor

Then drop into another session  ....... gnome fallback ..... or gnome classic

log out .... and use one of the ones that may be less of a problem.



use lm_sensors instead - this is what I have installed ...... 

```

$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +50.0°C  (crit = +103.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +51.0°C  (high = +86.0°C, crit = +100.0°C)
Core 0:         +46.0°C  (high = +86.0°C, crit = +100.0°C)
Core 1:         +48.0°C  (high = +86.0°C, crit = +100.0°C)
Core 2:         +50.0°C  (high = +86.0°C, crit = +100.0°C)
Core 3:         +50.0°C  (high = +86.0°C, crit = +100.0°C)

pkg-temp-0-virtual-0
Adapter: Virtual device
temp1:        +50.0°C  

asus-isa-0000
Adapter: ISA adapter
temp1:        +50.0°C 

```

[URL="http://en.wikipedia.org/wiki/Lm_sensors"]http://en.wikipedia.org/wiki/Lm_sensors


[/URL]

---

### Post by cqpphp on 2014-03-14
same results
> steve@mesack-cmdsudo:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +82.0°C  (crit = +98.0°C)
temp2:        +68.0°C  (crit = +92.0°C)


coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +84.0°C  (high = +87.0°C, crit = +105.0°C)
Core 0:         +84.0°C  (high = +87.0°C, crit = +105.0°C)
Core 1:         +80.0°C  (high = +87.0°C, crit = +105.0°C)


pkg-temp-0-virtual-0
Adapter: Virtual device
temp1:        +83.0°C  


steve@mesack-cmdsudo:~$ 




I'm using gnome classic as the desktop environment.

---

### Post by 23dornot23d on 2014-03-14
I just installed psensor to see if it still caused me problems and it appears ok in the kernel I use
now which is 3.13.0-16-generic #36-Ubuntu SMP Tue Mar 4 23:06:51 UTC 2014 i686 i686 i686 GNU/Linux

[IMG]http://i.minus.com/ixDWiT3DN7CuY.png[/IMG]

I have also done this small video - showing the load and what happens in compiz ......... but even
with load and pushing it mine stays around 61 degrees max 

__________________________________

[http://youtu.be/Erw33az0DOA](http://youtu.be/Erw33az0DOA)

__________________________________

When did you last upgrade your system and what kernel are you using ...........

uname -a

---

### Post by stev99d on 2014-03-14
I upgraded my system 5 mins ago (before that, I upgrade it yesterday). and my kernel is Linux 3.13.0-17-generic #37-Ubuntu SMP Mon Mar 10 21:44:01 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux.

side note : I forgot that I have an account in here. gotta remove "cqpphp" :l

---

### Post by 23dornot23d on 2014-03-14
grep -Fn '(EE' /var/log/Xorg.0.log

grep -Fn '(EE' /var/log/Xorg.8.log

What do these commands give you back ........... this is where I get out of my depth - but it may help someone
else to see what is going on here ...... as the experts reside in this section usually ...........

---

### Post by stev99d on 2014-03-14
looks like a real problem
[IMG]http://i.imgur.com/M3gk5AH.png[/IMG]

---

### Post by howefield on 2014-03-14
> **stev99d said:**
> I forgot that I have an account in here. gotta remove "cqpphp" :l

Done.

---

### Post by 23dornot23d on 2014-03-14
Also what does this output please .......... ( just doing some recon until the cavalry arrive )

less /var/log/gpu-manager.log

---

### Post by stev99d on 2014-03-14
:o
> log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
error: Can't access /etc/force-laptop
is laptop? Yes
grep dmesg status 256
dmesg status 256 == 0? No
grep dmesg status 256
dmesg status 256 == 0? No
is nvidia loaded? No
was nvidia unloaded? No
is fglrx loaded? No
was fglrx unloaded? No
is intel loaded? Yes
is radeon loaded? No
is nouveau loaded? No
vendor/device id: 8086:166
busid "pci:0:2:0"
is boot vga? Yes
vendor/device id: 10de:de9
busid "pci:1:0:0"
is boot vga? No
last cards number = 2
has amd? No
has intel? Yes
has nvidia? Yes
how many cards? 2
has the system changed? No
main_arch_path x86_64-linux-gnu, other_arch_path i386-linux-gnu
current alternative: /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf
is nvidia enabled? No
is fglrx enabled? No
is mesa enabled? Yes
is pxpress enabled? No
is prime enabled? No
is nvidia available? Yes
is fglrx available? No
is mesa available? Yes
is pxpress available? No
is prime available? No
intel igp detected
desktop system detected
or laptop with open drivers
discrete nvidia card detected
driver not enabled or not in use
nothing to do
(end)



---

### Post by 23dornot23d on 2014-03-14
I cannot spot anything obvious and that file is so similar to mine - the main difference between us is that I 
am running 32 bit where you are on 64 bit ..........

```

log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
Error: can't access /etc/force-laptop
Is laptop? yes
grep dmesg status 256
dmesg status 256 == 0? No
grep dmesg status 256
dmesg status 256 == 0? No
Is nvidia loaded? no
Was nvidia unloaded? no
Is fglrx loaded? no
Was fglrx unloaded? no
Is intel loaded? yes
Is radeon loaded? no
Is nouveau loaded? no
Vendor/Device Id: 8086:116
BusID "PCI:0:2:0"
Is boot vga? yes
Vendor/Device Id: 10de:df4
BusID "PCI:1:0:0"
Is boot vga? no
last cards number = 2
Has amd? no
Has intel? yes
Has nvidia? yes
How many cards? 2
Has the system changed? No
main_arch_path i386-linux-gnu, other_arch_path x86_64-linux-gnu
Current alternative: /usr/lib/i386-linux-gnu/mesa/ld.so.conf
Is nvidia enabled? no
Is fglrx enabled? no
Is mesa enabled? yes
Is pxpress enabled? no
Is prime enabled? no
Is nvidia available? yes
Is fglrx available? no
Is mesa available? yes
Is pxpress available? no
Is prime available? yes
Intel IGP detected
Desktop system detected
or laptop with open drivers
Discrete NVIDIA card detected
Driver not enabled or not in use
Nothing to do

```

---

### Post by stev99d on 2014-03-14
well... that's the problem :l

wait is this the end of the case D: ?

---

### Post by 23dornot23d on 2014-03-14
When in testing - you are meant to report it as a bug ...... 

The people here tend to get on with the testing and tomorrow there may be a fix .......

I will download the iso if you show me which link you used to get the 14.04 that you are now running

[https://www.google.co.uk/search?client=ubuntu&channel=fs&q=14.04+daily+build&ie=utf-8&oe=utf-8&gfe_rd=ctrl&q=14.04+daily+build+64+bit](https://www.google.co.uk/search?client=ubuntu&channel=fs&q=14.04+daily+build&ie=utf-8&oe=utf-8&gfe_rd=ctrl&q=14.04+daily+build+64+bit)

then will try to confirm that it is to do with the 64 bit system and not the 32 bit one ......

That is as much as I can do at this moment in time ........ as I said earlier ..... the daily builds will come
out right up till the time the team decides to release it ....... at the moment that is on the 17 April from
what I have read .........

64 bit seems good for me - just done a clean install of the ubuntu 14.04 64 bit and my computer temperatures are the
same as in the 32 bit version .......... so we are looking at it being something other than that.

---

### Post by ventrical on 2014-03-14
> **23dornot23d said:**
> I just installed psensor to see if it still caused me problems and it appears ok in the kernel I use
now which is 3.13.0-16-generic #36-Ubuntu SMP Tue Mar 4 23:06:51 UTC 2014 i686 i686 i686 GNU/Linux

[IMG]http://i.minus.com/ixDWiT3DN7CuY.png[/IMG]

I have also done this small video - showing the load and what happens in compiz ......... but even
with load and pushing it mine stays around 61 degrees max 

__________________________________

[http://youtu.be/Erw33az0DOA](http://youtu.be/Erw33az0DOA)

__________________________________

When did you last upgrade your system and what kernel are you using ...........

uname -a

What kind of laptop? (i7)

How about the fans... ?

---

### Post by 23dornot23d on 2014-03-14
Mine was getting hot and the fans were not working about 2 weeks back now ......... but steve is experiencing similar problems

but his computer running 64 bit latest kernel as of today is upto 80 degrees C ............

I just installed the same on my own system and mine is down at 47 degrees C ........... so I do not have the problem

But how do we identify what is causing it on steves machine ....... have got him to print the logs for the Xorg.0.log and Xorg.8.log out
previously ......... but I am not at all sure what to look for to see what is pushing the temperatures up.

Maybe you can work something out from what was previously posted ventrical - but its over my head - but I did try to help where I could
the posts I made were just to show how compiz affected the temps ....... but the most I got mine up to was 60 degrees C then it would 
fall back to normal again ..........


See post 10 [http://ubuntuforums.org/showthread.php?t=2211088&p=12956529#post12956529](http://ubuntuforums.org/showthread.php?t=2211088&p=12956529#post12956529) for Steves temperatures and cores ....

 the username he started the thread with was changed half way through - cqpphp to stev99d .  sort of 
confuses things a little .......  .... but it is he that is having the problems not me .......... this was his first post ,,,,,

[IMG]http://i.imgur.com/8CV8Nyw.png[/IMG]

---

### Post by ventrical on 2014-03-14
That pic *does* accurately represent the original screenshot. Also, if you look at the youtube video he was running 8 cores, so , presumably and i7 and (laptop =yes) pressumably a laptop so I need to know what hardware the OP is using, or , at least it would help to know.

  I am about to test  same on quadcore/desktop

Regards..

(where are the fans?)

---

### Post by xREDEMPTIONx on 2014-03-14
Hello, if you are indeed using a laptop try cleaning it. I've had issues with overheating in the past that I swore were caused by software updates. One time in particular was when I upgraded to 11.04 and I started noticing my temps hitting 80+. Turns out my laptop was just dirty. I opened the panel on the bottom and used an air can and was shocked at the stuff that came out of the vents. Afterwards temps were high 40s low 50s!! It's amazing what dust can do in a laptop.

---

### Post by ventrical on 2014-03-14
No overheat here with ccsm.

---

### Post by ventrical on 2014-03-14
> **xREDEMPTIONx said:**
> Hello, if you are indeed using a laptop try cleaning it. I've had issues with overheating in the past that I swore were caused by software updates. One time in particular was when I upgraded to 11.04 and I started noticing my temps hitting 80+. Turns out my laptop was just dirty. I opened the panel on the bottom and used an air can and was shocked at the stuff that came out of the vents. Afterwards temps were high 40s low 50s!! It's amazing what dust can do in a laptop.

If OP is using a Dell (i7) then it may not be detecting and controlling the fans correctly but I cannot read minds as to what the hardware is.

---

### Post by ventrical on 2014-03-14
> **xREDEMPTIONx said:**
> Hello, if you are indeed using a laptop try cleaning it. I've had issues with overheating in the past that I swore were caused by software updates. One time in particular was when I upgraded to 11.04 and I started noticing my temps hitting 80+. Turns out my laptop was just dirty. I opened the panel on the bottom and used an air can and was shocked at the stuff that came out of the vents. Afterwards temps were high 40s low 50s!! It's amazing what dust can do in a laptop.


Happens notoriously with laptops if  intake vents are blocked ie; crumpled table cloth .. etc..

---

### Post by ventrical on 2014-03-14
> **23dornot23d said:**
> Mine was getting hot and the fans were not working about 2 weeks back now ......... but steve is experiencing similar problems

but his computer running 64 bit latest kernel as of today is upto 80 degrees C ............

I just installed the same on my own system and mine is down at 47 degrees C ........... so I do not have the problem

But how do we identify what is causing it on steves machine ....... have got him to print the logs for the Xorg.0.log and Xorg.8.log out
previously ......... but I am not at all sure what to look for to see what is pushing the temperatures up.

Maybe you can work something out from what was previously posted ventrical - but its over my head - but I did try to help where I could
the posts I made were just to show how compiz affected the temps ....... but the most I got mine up to was 60 degrees C then it would 
fall back to normal again ..........


See post 10 [http://ubuntuforums.org/showthread.php?t=2211088&p=12956529#post12956529](http://ubuntuforums.org/showthread.php?t=2211088&p=12956529#post12956529) for Steves temperatures and cores ....

 the username he started the thread with was changed half way through - cqpphp to stev99d .  sort of 
confuses things a little .......  .... but it is he that is having the problems not me .......... this was his first post ,,,,,

[IMG]http://i.imgur.com/8CV8Nyw.png[/IMG]



 I just seen the changed thread. I thought poster was 2 different users. It is you with the i7?

---

### Post by ventrical on 2014-03-14
I was having overheating problems with another cycle. Not sure if this will help.

[http://ubuntuforums.org/showthread.php?t=2192729](http://ubuntuforums.org/showthread.php?t=2192729)

---

### Post by 23dornot23d on 2014-03-15
> 
I just seen the changed thread. I thought poster was 2 different users. It is you with the i7? 				


I do indeed have the i7 and mine is a Asus laptop - I did the check by loading in the 64 bit system to see if I got
any different results to the OP.

I did mine kept within its normal working limits but it does labour with compiz ...... 

I hope that the OP returns to let us know if any of the information you have given helps him in any way

I also will check through to see if it helps my own computer to keep cooler too ....... ty

---

### Post by carterclan2 on 2014-03-15
Best way of checking if the Laptop needs cleaning (which in my opinion is more plausible than a software issue) is to check the temps from your bios. If it is hot there then nothing in Ubuntu is causing it.

---

