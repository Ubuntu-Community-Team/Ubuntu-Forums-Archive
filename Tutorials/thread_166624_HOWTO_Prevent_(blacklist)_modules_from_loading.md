---
title: "HOWTO: Prevent (blacklist) modules from loading"
date: 2006-04-26
forum: Tutorials
---

### Post by eklitzke on 2006-04-26
**[SIZE="2"]Introduction[/SIZE]**
It is sometimes useful to prevent a module from loading.  This howto will show you how to do this, and should be applicable to most modern Linux distros.  This is really easy to do, so if you want you can just skip to the end to see how to do it; if you are more interested in how this stuff actually works, read the full howto.

My motivation for doing this was to prevent the system bell from sounding.  In other words, I didn't want my laptop to beep if I backspaced on an empty line in a virtual console, or put my laptop into sleep mode.  The system bell (which is actually a buzzer not controlled by your speakers) is accessed via the [FONT="Lucida Console"]pcspkr[/FONT] module.

In most modern Linux distributions (I *think* from kernel 2.2 onwards) the module settings are controlled by the file [FONT="Lucida Console"]/etc/modprobe.conf[/FONT] and the files in the [FONT="Lucida Console"]/etc/modprobe.d[/FONT] directory.  In particular, if you are running udev on your system one of the things that udev does is check all of these files and load modules based on their contents.  This is a good thing, because it means that you can create your own files in [FONT="Lucida Console"]/etc/modprobe.d[/FONT] to fiddle with the files that come with the module-init-tools package.

**[SIZE="2"]Creating a blacklist file[/SIZE]**
Since you probably don't want to mess with any of the files that come with your system, you will want to create a new file to hold all of the rules that you write.  I called mine [FONT="Lucida Console"]blacklist-custom[/FONT], but you can call yours anything that isn't already taken.  This file goes in the /etc/modprobe.d directory.  Once you have created the file, you can blacklist modules by adding a line of the form "blacklist name_of_module".  Lines starting with a # are ignored.  My file looks like this:
```
# /etc/modprobe.d/blacklist-custom
# Custom blacklist file so I don't mess with any of the files that come with
# the module-init-tools package.
blacklist pcspkr
```
The changes will take place next time you reboot (well, technically the next time you reload udev).

**[SIZE="2"]Manually loading/unloading and listing modules[/SIZE]**
If you want to unload the module without rebooting, you can use the command
```
user@ubuntu$ sudo modprobe -r pcspkr
```
If you later decide you want to manually load a module, issue the command
```
user@ubuntu$ sudo modprobe pcspkr
```
To check whether or not a module is running, use the [FONT="Lucida Console"]lsmod[/FONT] command.  Since you will probably get a pretty long list, you can check for a particular module by combining [FONT="Lucida Console"]lsmod[/FONT] with [FONT="Lucida Console"]grep[/FONT].  For example to list all loaded modules, use
```
user@ubuntu$ lsmod
```
and to check if any modules with "spkr" in the name are loaded, use
```
user@ubuntu$ lsmod | grep spkr
```

---

### Post by cvmostert on 2006-05-08
Thanx for the info, i am going to try and use this for my wireless card, rather use ndiswrapper instead. hopefully it works better.

---

### Post by flow_ca on 2008-07-29
thanks, your info was helpful.
only one thing: sometimes it's necessary to update the initramfs with
update-initramfs -u
so that the module really does not load.
flow

---

### Post by expatex on 2008-12-01
Thanks to both eklitzke and flow_ca -- this is great information and helped me along a good bit.

---

### Post by lamcro on 2008-12-07
Thanks.  Just tried it and worked.

---

### Post by kaos_frack on 2009-02-10
thanks!

and as for disabling the beep sound you also can use the command:
```

setterm -blength 0

```
and put it in your .profile

---

### Post by majeru on 2009-04-22
newer versions need the blacklist file to have the .conf extension.

offtopic:
A wiki would be much better for such tutorials, don't you guys think?

---

### Post by Gresley on 2009-11-18
I've got a problem with Virtualbox since upgrading to 9.10. The modules kvm-intel and kvm are running and prevent virtualbox from starting a VM. I've added the lines

blacklist kvm_intel
blacklist kvm

to the blacklist.conf file, however after a reboot these modules still load. 

every time I start virtualbox I need to preceed this with:

sudo rmmod kvm_intel kvm

Anyone got any ideas how to get rid of this nasty beastie thats making my Koala far from Kalm?

---

### Post by johnzollo on 2009-11-28
Anybody have any ideas for Gresley?

---

### Post by carson.gee on 2009-12-09
I had this same problem.  It turns out the qemu manually loads the kvm kernel module.  So if you run
> sudo apt-get remove qemu-kvm qemu --purge

It should no longer load the kvm kernel modules.

---

### Post by jeff93063 on 2009-12-11
I had the same problem with a different module. Just adding it to the blacklist did nothing. I found the answer here:
[http://ubuntuforums.org/showthread.php?t=1324246]("http://ubuntuforums.org/showthread.php?t=1324246")
From Temüjin's post:
> After you blacklist it:
```
sudo update-initramfs -u
```
Do that to make the blacklist change stick.

---

### Post by mbah.pande on 2011-07-30
iam new in linux now using natty 11.04
my plymouth broken by 
SP5100 TCO timer: mmio address 0xfec000f0 already in use

how to disable that module

---

### Post by dinoc on 2011-08-13
I've tried to blacklist firewire_ohci and firewire_core modules following this tutorial, but is not working.
I'm using the latest Ubuntu 11.04

Anyone know how to blacklist these 2 modules ?

---

### Post by realzippy on 2011-08-13
...have you tried adding them to
/etc/modprobe.d/blacklist.conf  ?

---

### Post by Rolandmaffia on 2011-11-14
Oh thank you for that enough information!
Regards!

---

### Post by mr1holmes on 2012-10-25
hi.. i'm completely new to ubuntu.
i have dual os (win7 and ubuntu 12.10) on sony vaio.
i think my problem is somewhere related with disabling device modules..
i want to turn off my wireless network as i never use it.
i've already tried disabling wireless network from windows.
in ubuntu it says "wireless is disabled by hardware switch" but the LED of wireless on my laptop is still turned on.(any function key is not provided in my laptop to turn off the wireless).
in windows "vaio smartnetwork" automatically turn off the wireless when the system boots but in ubuntu it never goes off.

---

