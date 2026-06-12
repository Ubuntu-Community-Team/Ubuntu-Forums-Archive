---
title: "Adjust screen resolution Acer Aspire 5736z"
date: 2013-03-08
forum: Ubuntu Development Version
---

### Post by Ibrahim717 on 2013-03-08
Hello all..... 

I am new to Ubuntu and linux for that matter and I am attempting to learn to program and making the switch at the same time.... Thus I would be considered a beginner. The reason I am running 13.04 is because 12.10 gave me so many problems which no one could answer that I began to try new versons of Ubuntu and 13.04 has been the by far the best i.e. touchpad works ... I have been able to get the wifi to work and i dont have a black screen when booting up or after updating.... These things are essential or me making the switch to linux due to the fact that, I fully commited to Ubuntu and erased windows 7....... Anyways thats just a little backround info and why I will be probally asking question that someone who is testing the daily build should know already and why if you chose to provide support please dont assume that I know what you are talking about....With that said 


How do I change the screen resolution... When I go to system settings --display ---- it only has one setting " Laptop" is there a way to put more settings "i.e. code into the termanal that will allow me to create a sharper image .... and utilize the high res of my monitor.... 

Thanks in advance 

Ibrahim717

---

### Post by cariboo on 2013-03-08
Changing screen resolution, depends on what graphics driver you are using. Could you paste the output of the following command in you next post:

```
sudo lshw -C display
```

The output should look similar to this:

```
sudo lshw -C display
[sudo] password for cariboo: 
  *-display               
       description: VGA compatible controller
       product: GT218 [GeForce 210]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:18 memory:df000000-dfffffff memory:c0000000-cfffffff memory:dc000000-ddffffff ioport:ef80(size=128) memory:def80000-deffffff
```

---

### Post by Ibrahim717 on 2013-03-09
OK,  Talk about diving into Ubuntu this issue has taught me a lot and I'm only half way to resolving it... good this is I think i have learned how to communicate in a way where I am help able.

The issue was that i was using the default Intel driver because in order to install 13.04 I had to press f6 and select nomodeset..... in order to see what I was doing....  

To get back to using my  [COLOR=#333333][FONT=Ubuntu Mono]Intel GMA 4500M I took out nomodeset  and added  [/FONT][/COLOR][COLOR=#000000]acpi_osi= to the grub .... this has given me the resolution options that I want.... However now My back light goes off if I change resolution or upon reboot.   so each time I have to run this command in the terminal on a black screen "[/COLOR][COLOR=#333333][FONT=Ubuntu Mono]sudo setpci -s 00:02.0 F4.B=00".......
[/FONT][/COLOR]

So no I need to know how to get the setpci script to run automatically at boot and during every other instance when its needed..... 
here are the links I used to deal with this issue....

[http://ubuntuforums.org/showthread.php?t=1840959](http://ubuntuforums.org/showthread.php?t=1840959)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/752165](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/752165)

---

### Post by Ibrahim717 on 2013-03-09
*-display:0             
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:44 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:4110(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:d3400000-d34fffff

---

### Post by Ibrahim717 on 2013-03-09
Here is a possible solution that I found in one of the links posted earlier.... I want to try this but have no Idea how to perform those tasks.... i.e. add setpci to file or make a new executable file.... can someone give a step by step or post a link or two..... 

"I run this command under no-backlight condition on terminal (I still can read my screen under flashlight):
sudo setpci -s 00:02.0 F4.B=00
and my back light is back!
but back light is off again after reboot, need to run that command again :(
All I did was add the setpci command into sudoers file (sudo visudo) so i don't need to type password when running setpci,
and make a new executable file contains that command, then make new startup entry to run that executable file every startup.
Now i have my back light function normally every startup..
Try this guys, who knows it can help you."

---

### Post by zika on 2013-03-09
> **Ibrahim717 said:**
> [COLOR=#333333][FONT=Ubuntu Mono]Here is a possible solution that I found in one of the links posted earlier.... I want to try this but have no Idea how to perform those tasks.... i.e. add setpci to file or make a new executable file.... can someone give a step by step or post a link or two..... [/FONT]

[FONT=Ubuntu Mono]"I run this command under no-backlight condition on terminal (I still can read my screen under flashlight):[/FONT]
[FONT=Ubuntu Mono]sudo setpci -s 00:02.0 F4.B=00[/FONT]
[FONT=Ubuntu Mono]and my back light is back![/FONT]
[FONT=Ubuntu Mono]but back light is off again after reboot, need to run that command again :([/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]All I did was add the setpci command into sudoers file (sudo visudo) so i don't need to type password when running setpci,
and make a new executable file contains that command, then make new startup entry to run that executable file every startup.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]Now i have my back light function normally every startup..
Try this guys, who knows it can help you."[/FONT][/COLOR]Did You try putting it in /etc/rc.local which runs with elevated privileges...?

---

### Post by Ibrahim717 on 2013-03-09
> **zika said:**
> Did You try putting it in /etc/rc.local which runs with elevated privileges...?


I was going to ask how to do this but though to myself I better figure that out on my own..... 

so by typing into the terminal :  gksu gedit /etc/rc.local 
 I was able to put: 

sudo setpci -s 00:02.0 F4.B=00      into the file

 my rc.local now looks like this :

```
The following command has solved my problem. To make it run after reboot
just insert the command in /etc/rc.local (by default this file is empty and
is equivalent to windows' autoexec.bat). My rc.local looks like this:
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
sudo setpci -s 00:02.0 F4.B=00
exit 0
```

Now I can reboot with out a black screen and my resolution is nice.  However when adjusting screen resolution my screen still goes black.... This is not a deal breaker for me but I would love to figure out how to fix this issue also.


( Horray my first big Ubuntu problem solved..I see why this stuff is addicting.... Thank YOU All who helped now and in the past)

---

### Post by Ibrahim717 on 2013-03-09
Another issue that I'm having is that when my computer hibernates it goes to black screen and i cant get it to come back on with out running the "setpci" command or restarting my laptop....

---

### Post by zika on 2013-03-10
> **Ibrahim717 said:**
> I was going to ask how to do this but though to myself I better figure that out on my own..... 

so by typing into the terminal :  gksu gedit /etc/rc.local 
 I was able to put: 

sudo setpci -s 00:02.0 F4.B=00      into the file

 my rc.local now looks like this :

```
The following command has solved my problem. To make it run after reboot
just insert the command in /etc/rc.local (by default this file is empty and
is equivalent to windows' autoexec.bat). My rc.local looks like this:
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
sudo setpci -s 00:02.0 F4.B=00
exit 0
```

Now I can reboot with out a black screen and my resolution is nice.  However when adjusting screen resolution my screen still goes black.... This is not a deal breaker for me but I would love to figure out how to fix this issue also.


( Horray my first big Ubuntu problem solved..I see why this stuff is addicting.... Thank YOU All who helped now and in the past)
As I said You do not need sudo in /etc/rc.local since it is executed with elevated privileges already...

---

### Post by bcbc on 2013-03-11
> **Ibrahim717 said:**
> Another issue that I'm having is that when my computer hibernates it goes to black screen and i cant get it to come back on with out running the "setpci" command or restarting my laptop....
Create a file called /etc/pm/sleep.d/99_fixbacklight and set it executable:

```
sudo chmod +x /etc/pm/sleep.d/99_fixbacklight
```

Contents of file:
```
#!/bin/sh


# workaround for backlight issue


case "$1" in
    resume|thaw)
        [COLOR=#000000]setpci -s 00:02.0 F4.B=00[/COLOR]
        ;;
esac
```

---

### Post by Ibrahim717 on 2013-03-14
> **bcbc said:**
> Create a file called /etc/pm/sleep.d/99_fixbacklight and set it executable:

```
sudo chmod +x /etc/pm/sleep.d/99_fixbacklight
```

Contents of file:
```
#!/bin/sh


# workaround for backlight issue


case "$1" in
    resume|thaw)
        [COLOR=#000000]setpci -s 00:02.0 F4.B=00[/COLOR]
        ;;
esac
```





I've been at this all day but I cant figure out how to create a file and set it as executable when I type in the command   " sudo chmod +x /etc/pm/sleep.d/99_fixbacklight ...    it states " cannot access no such file exists..... I think I'm missing a step..

---

### Post by nomenkultur on 2013-03-14
I have the same exact intel gfx card...


 why are you messing with the settings? or booting with parameters? everything works automatically without fiddling

---

### Post by bcbc on 2013-03-14
> **Ibrahim717 said:**
> I've been at this all day but I cant figure out how to create a file and set it as executable when I type in the command   " sudo chmod +x /etc/pm/sleep.d/99_fixbacklight ...    it states " cannot access no such file exists..... I think I'm missing a step..
The way I wrote it was a bit strange. Create the file with the contents shown. Then run: sudo chmod +x etc.

---

### Post by Ibrahim717 on 2013-03-15
> **nomenkultur said:**
> I have the same exact intel gfx card...


 why are you messing with the settings? or booting with parameters? everything works automatically without fiddling


As stated earlier in the post.... When I attempted to install Ubuntu on my lap top I continually got dark screens, thus I had to install using the nomodeset setting..... This is a common issue with the 4500 g card as noted in the links that I attached to this thread. Using nomodeset allows Ubuntu to use the default graphics driver which made is so I could only have the lowest screen resolution possible. The work in this thread has been to 1. Use my lintel graphics card so I can enjoy better screen res.... and two fix the back light issue and prevent dark screen.....  What kind of computer are you using because this issues is more prevalent in ACER's  from what I can tell

---

### Post by nomenkultur on 2013-03-16
Xx

---

### Post by Ibrahim717 on 2013-03-16
> **bcbc said:**
> Create a file called /etc/pm/sleep.d/99_fixbacklight and set it executable:

```
sudo chmod +x /etc/pm/sleep.d/99_fixbacklight
```

Contents of file:
```
#!/bin/sh


# workaround for backlight issue


case "$1" in
    resume|thaw)
        [COLOR=#000000]setpci -s 00:02.0 F4.B=00[/COLOR]
        ;;
esac
```





Ok finnally got this done...... and it worked to fix the issue of black screen when comming out of suspend mode...... However this only works when I manually put the computer into suspend mode..... When the computer goes to sleep by its self it gets the black screen and  I have to manually put it into suspend mode then wake it back up to turn the back light back on...... This allows me not to loose my doc or what ever Im  working on so it is very useful........


I still need some help with backlight issues when changing resolution also.... 


fyi when I installed the kernal updates my whole system went waky and none of the modifications worked anymore..... I had to re-install the OS from disk with the update and re-do all the modifications.....


BBHEEM

---

### Post by Ibrahim717 on 2013-03-16
when installing todays updates 3/16/2013....... I am able to get my system back running but my back light is worse... Im gonna start a new thread because I think there was a kernal update and it did something to my grub.....(I say this because it asked me if I wanted to keep my modified grub or change it)......... so what I did was..... do a fresh reinstall from my old disk......using the nomodeset....... then I performed the updates.... then I took off the nomodeset .. to see if the updates fixed the problem.... (they did not fix the back light issue) but I am using the right graphic driver (4500) .  I went ahead and added the setpci to the rc.local ..... and I created the 99_fixbacklight file and set it as excutable...... I have not changed the grub however...... at this point my back light doesn't come on after a reboot ...... but it does when comming out of suspend mode........

---

### Post by Ibrahim717 on 2013-03-16
> **nomenkultur said:**
> same model, everything worked here out of the box


 but I have installed 13.04 a few months back with different intel drivers and then I have been auto updating


you have a 5736- 4460 ......  What do you mean a different set of intel drivers and did you install x86 or 64amd

cause Im having all sorts of issues and when I did the nightly update all the modifications that i made to get my back light working halfway normal went out the window.... and I cant get the back light to work after a reboot...

---

