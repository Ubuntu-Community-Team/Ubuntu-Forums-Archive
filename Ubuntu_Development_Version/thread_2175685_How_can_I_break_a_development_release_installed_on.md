---
title: "How can I break a development release installed on my machine?"
date: 2013-09-20
forum: Ubuntu Development Version
---

### Post by amjjawad on 2013-09-20
Hi,

A side of well-known bugs and broken features reported, how can I break an installed development release? I know Beta 2 is approaching and things get more stable but from my own testing and other feedback from many different users, even Alpha Releases were a bit stable this cycle.

Now, don't get me wrong but I'm looking for some fun and above all, I am seeking to learn new stuff and better understanding :)

I want to learn how to break an installed system and how can I fix it. But, of course, if it is not broken, how would I fix it? ;)

Any good suggestions?

Thanks in advance!

P.S.
Do not worry, I have test machines (real ones) and I have extra IDE HDD and also some USB Drives :) and of course, to play that safe,  I can do it on VMs :)

P.S. 2
This is also will help me in Testing (learn more about it).

P.S. 3
Systems I usually Test: Ubuntu GNOME and Lubuntu

---

### Post by grahammechanical on 2013-09-20
For Ubuntu Gnome I would suggest installing the 3 PPAs and wait until something downloads and breaks something. There are a couple of threads in this section that confirm the warning that the code in these PPAs is experimental.

We can enable the proposed repository. That brings in code before it goes into the usual update channels. We can install upstream beta software. Some install Linux kernel versions before they get into the Ubuntu update channel. Likewise with proprietary video drivers.

Fixing them is another matter. It is not something that I have mastered. Far from it. I have found the Recovery Mode options to be useful, especially when we cannot get to a desktop. I think there is a sticky at the top of this section that has a list of useful commands/codes. I have used these many times in giving advice in the other forum sections.

Oh, it just now came to mind. The best way to break Ubuntu is to endlessly modify the user interface. Plenty of people in the other sections manage to break the OS quite easily. :) Seriously, just experiment.

Regards.

P.S. Here is an experiment for you. I have had Ubuntu and all the flavours running on Xmir except Ubuntu Gnome. Now why would that be the case? I installed the Ubuntu Gnome daily from the 18th and the situation is still the same. Could the difference be GDM instead of LightDM? Or something else? Practical experimentation. That is my way of breaking things.

---

### Post by amjjawad on 2013-09-20
Hello and thanks for your reply :)

> **grahammechanical said:**
> For Ubuntu Gnome I would suggest installing the 3 PPAs and wait until something downloads and breaks something. There are a couple of threads in this section that confirm the warning that the code in these PPAs is experimental.
Will give that a go :D
My only problem with Ubuntu GNOME is, I am testing it on my Real Hardware Machine which is not for testing. My Testing Machines ([https://wiki.ubuntu.com/QATeam/Hardware](https://wiki.ubuntu.com/QATeam/Hardware)) can't handle Ubuntu GNOME so I must play it safe on the VM. This is Core i5 2nd generation with 4GB RAM :P

> We can enable the proposed repository. That brings in code before it goes into the usual update channels. We can install upstream beta software. Some install Linux kernel versions before they get into the Ubuntu update channel. Likewise with proprietary video drivers.
Ah, I see deep complicated stuff here :P

> Fixing them is another matter. It is not something that I have mastered. Far from it. I have found the Recovery Mode options to be useful, especially when we cannot get to a desktop. I think there is a sticky at the top of this section that has a list of useful commands/codes. I have used these many times in giving advice in the other forum sections.
Yes, but let's break something first :P hehe

> Oh, it just now came to mind. The best way to break Ubuntu is to endlessly modify the user interface. Plenty of people in the other sections manage to break the OS quite easily. :) Seriously, just experiment.

By the way, I don't test Ubuntu, just Ubuntu GNOME and Lubuntu for now.

What do you mean by modify the user interface? settings and tweaks? 

Thank you!

---

### Post by amjjawad on 2013-09-20
> **grahammechanical said:**
> P.S. Here is an experiment for you. I have had Ubuntu and all the flavours running on Xmir except Ubuntu Gnome. Now why would that be the case? I installed the Ubuntu Gnome daily from the 18th and the situation is still the same. Could the difference be GDM instead of LightDM? Or something else? Practical experimentation. That is my way of breaking things.

I saw this after I posted my previous post.

It could be that because Ubuntu GNOME is using GDM and not LightDM but I have never tested XMIR except very few times when I was trying to help Xubuntu Team with their test and my test was a failure with the hardware I used at that time.

If I have enough time, I might try to look into this. Even though I'd like to focus more on features and/or packages which already exist and will be used rather than features/packages which will not be available with the stable release. But thanks a lot for this suggestion, will keep it in mind :D

---

### Post by grahammechanical on 2013-09-20
> [COLOR=#000000]What do you mean by modify the user interface? settings and tweaks? [/COLOR]

Yes. The usual procedure is to immediately forget what was changed and say, Ubuntu just broke itself. :) I do not get into it myself but installing themes and tweaking the desktop of the development branch is just as much a part of testing as anything else. I suppose.

Tomorrow I will install Lightdm in my new install of Ubuntu Gnome and replace GDM with it and see what happens. 

Regards.

---

### Post by deadflowr on 2013-09-20
Deleting, renaming, or moving configuration files usually works well to bork a system up.
You don't even need to be root to do so.
Start mucking around the various hidden files and folders in the home folder.
.config might be a good start.

Edit(Disclaimer) I do not condone or support any of this though. For the record

---

### Post by cariboo on 2013-09-20
You could always enable the proposed repository, although it may be to late in the cycle, some of the guys have experienced some satisfying breakage when doing this. :-)

---

### Post by whatthefunk on 2013-09-21
Install Mir.

---

### Post by grahammechanical on 2013-09-21
Actually, I have not found xmir to be breaking anything. I have had Ubuntu and all the flavours except Ubuntu Gnome running on xmir. I have just now finished an experiment that came into my mind yesterday - use lightdm instead of gdm. And it works. Having installed unity-system-compositor I then installed lightdm and configured it, in the process it deactivated gdm. On reboot Ubuntu Gnome is now running on xmir.

> 
graham@sda8-UG-Saucy:~$ grep -i LoadModule /var/log/Xorg.0.log
[    22.289] (II) LoadModule: "glx"
[    22.329] (II) LoadModule: "xmir"
[    22.400] (II) LoadModule: "nvidia"
[    22.401] (II) UnloadModule: "nvidia"
[    22.401] (II) LoadModule: "nouveau"
[    22.421] (II) LoadModule: "vesa"
[    22.428] (II) LoadModule: "modesetting"
 
As we will not be getting the full Mir on the desktop until sometime in the 14.10 development cycle, I do not see installing Mir as an effective way of breaking the desktop.

I am posting this from a fully functional Ubuntu Gnome + Xmir.

Regards

---

### Post by zika on 2013-09-21
> **grahammechanical said:**
> Yes. The usual procedure is to immediately forget what was changed and say, Ubuntu just broke itself. :) I do not get into it myself but installing themes and tweaking the desktop of the development branch is just as much a part of testing as anything else. I suppose.

Tomorrow I will install Lightdm in my new install of Ubuntu Gnome and replace GDM with it and see what happens. 

Regards.Brave... I did not see LightDM working for quite a while, Mir got it firmly...

---

### Post by VinDSL on 2013-09-21
> **amjjawad said:**
> I want to learn how to break an installed system [...]

Any good suggestions?
One of my favorite ways is to *[redacted]*.

Have fun...

**EDIT**

N/M  :)

---

### Post by ventrical on 2013-09-21
OSmetimes I get data corruption when I am overclocking. Today I aquired a bundle of old 3.20GHz Celeron Ds and I am currently at  4.591GHz stable  with saucy. :) Don't try this unless you got the extra machines or processors. 

```

ventrical@ventrical-P4M266A-8237:~$ sudo dmidecode -t processor | grep "Speed"
[sudo] password for ventrical: 
    Max Speed: 4000 MHz
    Current Speed: 4591 MHz
ventrical@ventrical-P4M266A-8237:~$ sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.56 V  (min =  +1.45 V, max =  +1.75 V)
 +3.3 Voltage:      +1.66 V  (min =  +3.00 V, max =  +3.60 V)
 +5.0 Voltage:      +1.58 V  (min =  +4.50 V, max =  +5.50 V)
+12.0 Voltage:     +12.09 V  (min = +11.20 V, max = +13.20 V)
CPU FAN Speed:     4066 RPM  (min =    0 RPM, max = 1800 RPM)
CHASSIS FAN Speed:    0 RPM  (min =    0 RPM, max = 1800 RPM)
POWER FAN Speed:      0 RPM  (min =    0 RPM, max = 1800 RPM)
CPU Temperature:    +33.0°C  (high = +90.0°C, crit = +125.0°C)
MB Temperature:     +32.0°C  (high = +70.0°C, crit = +125.0°C)
Power Temperature:  +21.0°C  (high = +80.0°C, crit = +125.0°C)

nouveau-pci-0400
Adapter: PCI adapter
temp1:        +38.0°C  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +105.0°C, hyst =  +5.0°C)
                       (emerg = +135.0°C, hyst =  +5.0°C)

ventrical@ventrical-P4M266A-8237:~$ 

```

ok.. so I'll try for 4.7GHz :) lol

---

### Post by whatthefunk on 2013-09-21
Play around with graphics drivers or activate the x-edgers ppa.

---

### Post by ventrical on 2013-09-21
I got to here:

```


ventrical@ventrical-P4M266A-8237:~$ sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.56 V  (min =  +1.45 V, max =  +1.75 V)
 +3.3 Voltage:      +1.67 V  (min =  +3.00 V, max =  +3.60 V)
 +5.0 Voltage:      +1.59 V  (min =  +4.50 V, max =  +5.50 V)
+12.0 Voltage:     +12.09 V  (min = +11.20 V, max = +13.20 V)
CPU FAN Speed:     4141 RPM  (min =    0 RPM, max = 1800 RPM)
CHASSIS FAN Speed:    0 RPM  (min =    0 RPM, max = 1800 RPM)
POWER FAN Speed:      0 RPM  (min =    0 RPM, max = 1800 RPM)
CPU Temperature:    +36.0°C  (high = +90.0°C, crit = +125.0°C)
MB Temperature:     +33.0°C  (high = +70.0°C, crit = +125.0°C)
Power Temperature:  +19.0°C  (high = +80.0°C, crit = +125.0°C)

nouveau-pci-0400
Adapter: PCI adapter
temp1:        +37.0°C  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +105.0°C, hyst =  +5.0°C)
                       (emerg = +135.0°C, hyst =  +5.0°C)

ventrical@ventrical-P4M266A-8237:~$ sudo dmidecode -t processor | grep "Speed"
[sudo] password for ventrical: 
    Max Speed: 4000 MHz
    Current Speed: 4931 MHz

```

and then higher than that and ff starts to get unstable, but not broken. Guess I should raise the vCore voltage :) lol

---

### Post by QDR06VV9 on 2013-09-21
> **ventrical said:**
> 

and then higher than that and ff starts to get unstable, but not broken. Guess I should raise the vCore voltage :) lol

ventrical  You are a Madman:)
Back when I was testing novel Suse I fried a few cpu's and a couple of video cards.
_NOT FOR THE FAINT OF HEART_

---

### Post by ventrical on 2013-09-22
I am beggining to wonder if I am getting a false report because my core heat is not increasing and I am only using a large , modded, Cooler Master air only.

Sorry for being off topic.  I went to a surplus garage sale and there were a bunch of these Celeon Ds 3.20GHzs for cheap so I am not worried frying them ...

```

ventrical@ventrical-P4M266A-8237:~$ sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.57 V  (min =  +1.45 V, max =  +1.75 V)
 +3.3 Voltage:      +1.67 V  (min =  +3.00 V, max =  +3.60 V)
 +5.0 Voltage:      +1.58 V  (min =  +4.50 V, max =  +5.50 V)
+12.0 Voltage:     +12.09 V  (min = +11.20 V, max = +13.20 V)
CPU FAN Speed:     4141 RPM  (min =    0 RPM, max = 1800 RPM)
CHASSIS FAN Speed:    0 RPM  (min =    0 RPM, max = 1800 RPM)
POWER FAN Speed:      0 RPM  (min =    0 RPM, max = 1800 RPM)
CPU Temperature:    +29.0°C  (high = +90.0°C, crit = +125.0°C)
MB Temperature:     +25.0°C  (high = +70.0°C, crit = +125.0°C)
Power Temperature:  +19.0°C  (high = +80.0°C, crit = +125.0°C)

nouveau-pci-0400
Adapter: PCI adapter
temp1:        +33.0°C  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +105.0°C, hyst =  +5.0°C)
                       (emerg = +135.0°C, hyst =  +5.0°C)

ventrical@ventrical-P4M266A-8237:~$ sudo dmidecode -t processor | grep "Speed"
[sudo] password for ventrical: 
    Max Speed: 4000 MHz
    Current Speed: 5051 MHz
ventrical@ventrical-P4M266A-8237:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Saucy Salamander (development branch)
Release:    13.10
Codename:    saucy
ventrical@ventrical-P4M266A-8237:~$ 

```

Ok.. I guess the Celeron D 352s are still the overclocking cpus of choice and high speeds on stock cooling are normal :) lol
[http://www.xbitlabs.com/news/cpu/display/20110823231427_Overclocker_Sets_New_World_s_CPU_Frequency_Record.html](http://www.xbitlabs.com/news/cpu/display/20110823231427_Overclocker_Sets_New_World_s_CPU_Frequency_Record.html)

---

### Post by VinDSL on 2013-09-22
> **ventrical said:**
> Ok.. I guess the Celeron D 352s are still the overclocking cpus of choice and high speeds on stock cooling are normal :) lol

[http://www.xbitlabs.com/news/cpu/display/20110823231427_Overclocker_Sets_New_World_s_CPU_Frequency_Record.html](http://www.xbitlabs.com/news/cpu/display/20110823231427_Overclocker_Sets_New_World_s_CPU_Frequency_Record.html)
AMD Bulldozer holds the world record...  :)

[https://en.wikipedia.org/wiki/Bulldozer_(microarchitecture)#Overclocking](https://en.wikipedia.org/wiki/Bulldozer_(microarchitecture)#Overclocking)

---

### Post by ventrical on 2013-09-22
> **VinDSL said:**
> AMD Bulldozer holds the world record...  :)

[https://en.wikipedia.org/wiki/Bulldozer_(microarchitecture)#Overclocking](https://en.wikipedia.org/wiki/Bulldozer_(microarchitecture)#Overclocking)


lol .. :)

  When it comes to liquid hemium .. it's all up in the air at that point... :) jk 

  Thanks....

---

### Post by grahammechanical on 2013-09-23
This is an update on my attempt to break Ubuntu Gnome or rather not break it, by running it on xmir. I have learnt a few things.

1) Installing lightdm brings in Unity. It is an altenative desktop at log in.
2) Lightdm does more than just manage the login screen. According to the Ubuntu wiki

> The most user visible aspect of the display manager is the login screen,  however it also manages the X servers and facilitates remote logins  using the XDMCP protocol.

So, I guess that Mir will replace lightdm. I am now going to try to revert back to gdm to see if the xmir module still loads. Some how I do not think it will. Although I use Ubuntu+Unity I do think that the GDM login screen suits Ubuntu Gnome. It is part of the concept. So, I suppose the question is can gdm be patched to load xmir? Most likely but messing with source code is beyond this practical experimenter. And the Ubuntu Gnome developers have enough to do at this time.

Regards.

_ Update:_ Found a new way to break an OS. Mis-type when editing a system file or script.

In Ubuntu Gnome we can revert from Lightdm to gdm by editing /etc/X11/default-display-manager and changing

> /usr/sbin/lightdm
to
> /usr/sbin/gdm

That brings back GDM as the display manager and with it the Ubuntu Gnome log in screen but the xmir module does not load. A pity. But at least I have narrowed the issue to within GDM. But if a person wants Unity as an alternative desktop on Ubuntu Gnome and they are happy with the lightdm log in screen then they can also have Ubuntu Gnome on xmir.

A thought just occurs to me. A different approach would be to modify lightdm to load the gdm log in screen. So, that lightdm is the display manger but the log in screen is the Ubuntu Gnome version. Now, how do i do that? More thinking and experimentation required.

Regards.

---

### Post by ventrical on 2013-09-23
> **grahammechanical said:**
> This is an update on my attempt to break Ubuntu Gnome or rather not break it, by running it on xmir. I have learnt a few things.

1) Installing lightdm brings in Unity. It is an altenative desktop at log in.
2) Lightdm does more than just manage the login screen. According to the Ubuntu wiki

_..._

A thought just occurs to me. A different approach would be to modify lightdm to load the gdm log in screen. So, that lightdm is the display manger but the log in screen is the Ubuntu Gnome version. Now, how do i do that? More thinking and experimentation required.

Regards.

Keep rolling Graham. You're on fire here. :)

Regards..

---

### Post by grahammechanical on 2013-09-23
@ventrical

Thanks.

Xubuntu and Lubuntu use lightdm. Do they use their own greeter session or a modified Ubuntu greeter with changes to the background image and a central placement of the log in box? That is what I am wondering. Perhaps I need to redesign the Ubuntu log in screen in the fashion of the Ubuntu Gnome log in scrren. Or I could edit /etc/lightdm/50-greeter-wrapper.conf and change this

> greeter-wrapper= /usr/lib/lightdm/lightdm-greeter-session

to

> greeter-wrapper= /usr/lib/gdm

I am giving my brain a chance to cool down and to let the information filter down.

Kubuntu also uses lightdm (I think). And I have had kubuntu running on xmir. Perhaps kwin is more forgiving of xmir than gdm. :)

Regards.

---

### Post by ventrical on 2013-09-23
> **grahammechanical said:**
> @ventrical

Thanks.


Kubuntu also uses lightdm (I think). And I have had kubuntu running on xmir. Perhaps kwin is more forgiving of xmir than gdm. :)

Regards.

You're welcome.
Question:

The kubuntu you are running. Is that a full install from the kubuntu iso or did you install the Kubuntu- desktop from the repos?

 It is a pointed question. Reason being is I am interested in this topic. Secondly, one sure way to break ubuntu-desktop is to install xubuntu-desktop or edubuntu-desktop or lubuntu-desktop or vis a versa on top of one another. This is where some of the depends will really collide with each other and theoretically they shouldn't - should they ?

Regards..

---

### Post by grahammechanical on 2013-09-23
These were installs to specifically test if I could install xmir. I followed the steps in the web page of Ollie Reis. So, this was several weeks ago. Before unity-system-compositor was put into the repos. I intend to reinstall the flavours to do a retest of this.

And I also tried installing all the desktops one on top of the other. Result = reinstall. They all tried to hijack the OS. Kubuntu desktop even changing the name from Ubuntu to Kubuntu in the grub menu. And they also brought in massive amounts of utilities. This is more than just a desktop user interface. It is closer to the full alternative distro.

There was a bit of a tussle as to which would be the login screen. First Xubuntu would appear briefly and then Lubuntu would bully its way on to the screen. I foresee a real mess when Ubuntu is sitting on Mir and Kubuntu and Lubuntu are sitting on whatever Wayland compositor makes it out of the starting blocks and someone wants an alternative desktop. And there is no easy way to remove an alternative desktop. Stuff gets left behind.

By the way, what I found was that both Xubuntu and Lubuntu use lightdm-greeter-session. But the greeters are different = conflict as to which one gets loaded. In my opinion.

Regards.

---

### Post by ventrical on 2013-09-23
> **grahammechanical said:**
> These were installs to specifically test if I could install xmir. I followed the steps in the web page of Ollie Reis. So, this was several weeks ago. Before unity-system-compositor was put into the repos. I intend to reinstall the flavours to do a retest of this.

And I also tried installing all the desktops one on top of the other. Result = reinstall. They all tried to hijack the OS. 

Regards.


This is exactly it.  I can't help but wonder as to the reasoning of why there is not some sort of caution that comes along with installing the  extra desktops. I mean .. not for me .. but for noobs.  It won't break the system entirely but it will break some aspects of it.

  Perhaps it is lightdm or the log on process itself .. but as you have said .. yes .. I have seen Kubuntu hijack (overwrite) grub without  permission it seems. Of course we give it permission when we install the desktop. So  the fix would be how could we have just the desktops install and not have them carfunkle GRub or other depends? I mean .. it's the same kernel .. etc... so why do they have to merge as they do .. or why ARE they merging when they should not be?

:) lol

just thinking out loud..:)

edit ..

and/or I know we could just install the different flavours on seperate partions  .. etc... but why can't we have the different desktops loaded sort of like seperate partions and only using one kernel?? ummm .. i don't get it..

---

### Post by QDR06VV9 on 2013-09-23
> **ventrical said:**
> This is exactly it.  I can't help but wonder as to _[COLOR=#ff0000]the reasoning of why there is not some sort of caution that comes along with installing the  extra desktops[/COLOR]_. I mean .. not for me .. but for noobs.  It won't break the system entirely but it will break some aspects of it.



edit ..

and/or I know we could just install the different flavours on seperate partions  .. etc... but why can't we have the different desktops loaded sort of like seperate partions and only using one kernel?? ummm .. i don't get it..

Boy I have often wondered the same toughts as you, and have had some very derogitive remarks back on this topic,gald it was you to ask this seemingly easy rerquest you seem to have a nice touch of asking such things:D.
On another thought I been doing testing for CyanogenMod Android and i always have the ablity to take only Stable RC,s This would be nice on buntu also, Not talking about LTS release's IMHO this just leaves a better taste in users mouth..
[h=2][/h]

---

### Post by ventrical on 2013-09-24
Thanks ! Really .. I hope it does not sound like I am complaining because I am not  :) lol

  I think it has to do with pointers and flags and conventions.  Most of the flavours are using  the same directories to get their buisness done so naturally there will be overwrites and thats fine .. but the kicker is that they will not uninstall cleanly without a lot of rucku..... err uhh.. fandangling :) around. It's like gum in one's hair, olive oil stain on the new carpet, hard drive with a  bad bearing, a cat on a hot tin roof .. ya know :)  geesh..

---

### Post by QDR06VV9 on 2013-09-24
```
Thanks ! Really .. I hope it does not sound like I am complaining because I am not  :smile: lol
```

Not at all!! I been told from time to time I have the Tact of a bull in a china shop:confused:
Its all good I Come in Peace! LOL

---

### Post by ventrical on 2013-09-24
Searching about , I found this:

[http://ubuntuxtreme.com/howto/how-to-change-desktop-environment-in-ubuntu-12-10/](http://ubuntuxtreme.com/howto/how-to-change-desktop-environment-in-ubuntu-12-10/)

and it offers *this* code :

```

sudo apt-get install --no-install-recommends kubuntu-desktop

```

so here goes .. I'll install it and try to uninstall it. Perhaps it will not break after uninstall.

---

### Post by ventrical on 2013-09-24
> **grahammechanical said:**
> 

By the way, what I found was that both Xubuntu and Lubuntu use lightdm-greeter-session. But the greeters are different = conflict as to which one gets loaded. In my opinion.

Regards.

```

Setting up ksnapshot (4:4.11.1-0ubuntu1) ...
Setting up lightdm-kde-greeter (0.3.2.1-1ubuntu2) ...

```

so I am assuming that lightdm for Ubuntu gets wiped. I am about to look-see.

(so we can pin these out) ?

edit..

Yup .. bullied lighdm right out. Now have default lightdm-kde-greeter (0.3.2.1-1ubuntu2) ...

So let's uninstall - (remove) and see what breaks.

```

sudo apt-get remove kubuntu-desktop

```



 It removed one package (kubuntu-desktop) an did nothing KDE Plasma is still there. Obviously something I did not do in my code... searching around .. here we go.. how to remove kubuntu-desktop?


ahhh.. lets try this..

```

sudo apt-get install ubuntu-desktop
sudo apt-get --purge remove kubuntu-desktop
sudo apt-get autoremove
  
```

edit.. No dice ... msg .. kubuntu-desktop is not installed .. etc..

---

### Post by ventrical on 2013-09-24
Now a real caveat to all of this is that when I use ;

```

sudo service lightdm restart

```

it brings me right back to the kde-greeter.!

scratchin my head.... hmmm

Ok... so the results of this experiment so far (in the theme of trying to cause breakage to saucy systems) is that the original Ubuntu install has been interfected with the KDE plasma desktop install. So the different desktop experiences are actually dueling at the stage of startup and log-on. They have no respect for each other.

---

### Post by ventrical on 2013-09-24
So I am going to try and remove :

```

lightdm-kde-greeter (0.3.2.1-1ubuntu2) ..


```

ok.. rebooted and got absolute blackspace. To recover I had to go to terminal and reinstall the lightdm-kde-greeter.

So.. in summation... although Unity 3D and Ubuntu in general is still operative, the original lightdm ubuntu greeter has been wiped, replaced, supplanted or overwritten and this in a sense is a mild form of breakage that will take a lot of cli codeing to fix& clean or even require a fresh install.

Regards..

---

### Post by ventrical on 2013-09-24
Gee.. this goes all the way back to 2005.

[http://ubuntuforums.org/showthread.php?t=96048&p=526325#post526325](http://ubuntuforums.org/showthread.php?t=96048&p=526325#post526325)

..

---

### Post by ventrical on 2013-09-24
And here is how I fixed it.

lightdm.conf

[SeatDefaults]
user-session=unity-greeter
#user-session=kde-plasma
#greeter-session=lightdm-kde-greeter
type=unity


Notice where the KDE Plasma DE *inserted* it's code into lightdm.conf. I never thought such a seemingly obscure little file would be given so much control, especially during the boot-up log on process.

 So I would assume that if an end_user were to try a DE from the repos that they could pin or make read only the lightdm.cong file, despite global permissions during install.

What cornundrum would this be then?

edit... it just occured to me that  most likely many seemingly irrecoverable installs could just basically be somthing that was injected into lightdm.conf and that this file should be checked out before crefloing (scrapping) a system, but if a beta tester wants to emulate a busted system then they could start right there at lightdm.conf.

---

### Post by ventrical on 2013-09-24
And the reason this is important for noobs is that all of the various flavors are in the Software Center and so Jane or John Enduser may  install out of curiosity without being able to recover.

---

### Post by ventrical on 2013-09-25
The benifit of keeping the unity-greeter in the lightdm.conf file is that you can create another user and then logon to a KDE plasma session under that user and then switch back to your regular account with Unity  (if that is your choice) and there are no borkfunkles to be contended with.  So in this sesne it is not really a bug. I think it is just a matter of practice to understand the learning curves involved in attempting to understand the log in process and lighdm and the configuration files and how they all work together - so basically, my previous assumption was wrong but for a new user it becomes a difficult discovery process.

Regards..

---

### Post by grahammechanical on 2013-09-25
I think what we are seeing from one particular flavour is territorial ambition. Rather like the Russians planting a flag on the seabed under the polar ice cap. Of course it could simply be taking the easy option of packaging the whole DE instead of separating the user interface and packaging that.

Another script that you might want to look into is /etc/X11/default-display-manager.

On Ubuntu Gnome it read

> /usr/sbin/gdm

but when I installed lightdm it was changed to

> /usr/sbin/lightdm

Just to complicate things further on Lubuntu /etc/lightdm/lightdm.conf says

> greeter-session=lightdm-gtk-greeter
user-session=Lubuntu

And on Xubuntu it says

> greeter-session=lighdm-gtk-greeter
user-session=xubuntu

Ubuntu 12.04 has

> greeter-session=unity-greeter
user-session=ubuntu

But saucy does not have /etc/lightdm/lighdm.conf It has /etc/lightdm/lightdm.conf.d/ and in that folder we find

10-ubuntu.conf; 10-unity-system-compositor.conf; 50-greeter-wrapper.conf; 50-ubuntu.conf; 50-unity-greeter.conf; 50-xserver-command.conf. This is with unity-system-compositor installed. I think that the numbering system is similar to that of Grub. It indicates the priority in which scripts are run.

Although I think it would be interesting if Ubuntu Gnome could be run on xmir, either by patching gdm to load xmir and xserver, or by modifying the lighdm login screen to look like the Ubuntu Gnome login screen, I am starting to think that it is irrelevant because Mir is coming. I think that summer 2014 will be the 'makeup or break up' time for the flavours.

Regards.

---

