---
title: "Ubuntu Server with Ubuntu-desktop. Good or Bad? How to auto console mode?"
date: 2011-03-03
forum: Server Platforms
---

### Post by adriancs on 2011-03-03
A computer installed ubuntu server, then follow by executing this command
 
```
sudo apt-get install ubuntu-desktop
```
 
the computer automatically boot into desktop GNOME environment.
 
How to make the computer automatic boot into console mode? not desktop GNOME
 
Install ubuntu-desktop in ubuntu-server. is this a good practice?
will the ubuntu-desktop affect the speed of ubuntu-server?
is there any bad thing happen if ubuntu-desktop installed within ubuntu-server?
 
thanks for your advice

---

### Post by Dojan on 2011-03-03
I am wondering the same thing, but with xfce instead of gnome.

Thanks in advance!

---

### Post by HugoSerrano on 2011-03-03
> How to make the computer automatic boot into console mode? not desktop GNOMEsudo update-rc.d -f gdm remove


>  Install ubuntu-desktop in ubuntu-server. is this a good practice? Nop

> will the ubuntu-desktop affect the speed of ubuntu-server? Maybe, depends on your hardware, but the desktop always need some extra resources.

> is there any bad thing happen if ubuntu-desktop installed within ubuntu-server? More packages, more possible bugs, security failures, etc.


Do you really need a graphical interface? 

To remove it: sudo apt-get remove ubuntu-desktop


Regards!

Edit: typo

---

### Post by James78 on 2011-03-03
> **HugoSerrano said:**
> To remove it: sudo apt-get remove ubuntu-desktop
That only removes the ubuntu-desktop meta package, not all the packages that got installed by ubuntu-desktop.

For some solution ideas on completely removing ubuntu-desktop.
[http://ubuntuforums.org/showpost.php?p=10515879&postcount=2](http://ubuntuforums.org/showpost.php?p=10515879&postcount=2)

---

### Post by aeiah on 2011-03-03
to further expand:

having the desktop installed won't affect performance, providing the desktop environment isnt currently running. you could keep some kind of graphical environment installed in case you really need it, and just make sure it isnt running all the time.

mos of the stuff ubuntu-desktop drags with it is pointless for a server, and as was mentioned, just leads to a more complex install set with an increase in the chance of bugs and security vulnerabilities.

if you must have a gui either consider something like openbox and install only the gui applications you need, or better still, use webmin, and control things from a web based control panel.

the best option is often just to use the command line, however.

what is your server going to be doing? most tasks can be configured as easily from the command line as from a desktop environment, because in the end you'll just be editing the same config files.

---

### Post by James78 on 2011-03-03
If you seriously seriously need some tools to manage it with, I use Webmin + Virtualmin. It helps to complement the command line. :)

---

### Post by Dojan on 2011-03-03
In my case, I am simply to noob to be able to do all I want from the command line, but the server (a simple home server setup) will be running headless, accessed through remote desktop when I need to change something. While I could probably manage most stuff if I tried hard enough, and really started learning the CLI, I wouldn't feel comfortable, and would have no idea what went wrong whenever anything did. 
What I envision is something like this: On boot the desktop does not load, but only the programs I specify, but when I need it, I use remote desktop, and use some command to load the desktop. 

Doable? 

I'm not thrilled about the Webmin/Virtualmin approach, mostly because it's a whole new system to learn, then I'd rather learn the CLI...

Tell me if I should really be posting in the newbie forums :)

---

### Post by bsntech on 2011-03-03
I use OpenBox with my Ubuntu servers.  Reduces the load and less hard drive usage as well.

works just fine but was quite intensive to configure - but OpenBox just gives me a blank desktop with the ability to use Firefox and access a terminal to run any GUI activities.

Most people don't care - but I would rather have a slim server profile with as little hard drive use as possible.  I'm running about 1 GB with the server and installed services.  Means faster load times on the servers as well.

Brian S.
[http://www.bsntech.com]("http://www.bsntech.com")

---

### Post by GWBouge on 2011-03-03
> **Dojan said:**
> In my case, I am simply to noob to be able to do all I want from the command line, but the server (a simple home server setup) will be running headless, accessed through remote desktop when I need to change something. While I could probably manage most stuff if I tried hard enough, and really started learning the CLI, I wouldn't feel comfortable, and would have no idea what went wrong whenever anything did. 
What I envision is something like this: On boot the desktop does not load, but only the programs I specify, but when I need it, I use remote desktop, and use some command to load the desktop. 

Doable? 

I'm not thrilled about the Webmin/Virtualmin approach, mostly because it's a whole new system to learn, then I'd rather learn the CLI...

Tell me if I should really be posting in the newbie forums :)

I'm far from an expert, but if you really want to learn and keep things simple, I'd say just do what you need through ssh.  I run an Ubuntu Server through VirtualBox for web projects, and I still just minimize the VM and connect to it with ssh, lol.

---

### Post by bsntech on 2011-03-03
I do the same as GWBouge.  95% of all activities are done with ssh and very little is done via the GUI.

I do run speed tests and some backup utilities as needed using the GUI through OpenBox - but that is it.

Brian S.
[http://www.bsntech.com]("http://www.bsntech.com/bsntech-blog-mainmenu-321/computers-mainmenu-281/")

---

### Post by adriancs on 2011-03-03
I have tried typing this to make the computer to auto log into console mode (not Desktop GNOME)

```
sudo update-r.d .f gdm remove
```

but, it says: 

```
update-rc.d; /etc/init.d/ .f: file does not exist
```

what is missing in the code?

---

### Post by adriancs on 2011-03-03
Thanks for the advice, guys. 

I would like to disable or uninstall ubuntu-desktop.
I have tried executing some of the command stated in above posts.
below are some of the screenshot after executing the command.

Auto Log into console mode/disable desktop GNOME:
```
sudo update-rc.d .f gdm remove
```
[IMG]http://i1209.photobucket.com/albums/cc382/newcsleaner/4.jpg[/IMG]

Uninstall ubuntu-desktop:
```
sudo apt-get remove ubuntu-desktop
```
[IMG]http://i1209.photobucket.com/albums/cc382/newcsleaner/1.jpg[/IMG]

```
sudo apt-get autoremove ubuntu-desktop
```
[IMG]http://i1209.photobucket.com/albums/cc382/newcsleaner/2.jpg[/IMG]

```
sudo aptitude remove ubuntu-desktop
```
[IMG]http://i1209.photobucket.com/albums/cc382/newcsleaner/3.jpg[/IMG]

it seems that the ubuntu-desktop cannot be uninstalled.
The computer still automatic log into desktop mode. not console mode.

what command should be execute to disable GNOME desktop or uninstall it? Thanks.

---

### Post by James78 on 2011-03-03
For your GDM command, just remove ".f"!
```
sudo update-rc.d gdm remove
```Note: .f may have meant -f, which is to force removal.

Oh, and also, did you see my post on page 1, where I said that removing ubuntu-desktop only removes the meta package, and not ubuntu-desktop? Solution would be something similar to:
```
sudo apt-get remove ubuntu-desktop^
```In order to try to fix your problem..
Does it work if you kill the gdm process (probably throwing you back  to a TTY), then logon to the TTY, and try removing it again?
What happens if you try these commands?
```
sudo apt-get install -f
sudo dpkg --configure -a
```

---

### Post by roadrawts on 2011-03-04
I am using ubuntu 10.10 server.  None of these suggestions seem to apply in this version. Can you shed some light on how to boot into console mode in 10.10?

The suggestion about changing S??gdm does not exist in this version.

Thanks

---

### Post by egpetrich on 2011-03-04
> **roadrawts said:**
> I am using ubuntu 10.10 server.  None of these suggestions seem to apply in this version. Can you shed some light on how to boot into console mode in 10.10?
The suggestion about changing S??gdm does not exist in this version.

That's puzzling. I'm running 10.04LTS, and I wouldn't have expected something so fundamental to change on a point release.

Runlevels have either gotten more complicated or less so since I had to pay a lot of attention to them. If I'm understanding things correctly, you'll end up in runlevel 2 by default when you boot. (At the moment, I don't know how to change that default. Perhaps the Powers That Be have decided you don't need to do so.)

Still, you can determine your current runlevel with the simple command "runlevel". I get this on my system:
```
$runlevel
N 2
```
The "2" means that I'm in runlevel 2, and the "N" means that I haven't changed it since boot. Therefore I default to runlevel 2.

Assuming that you also default to runlevel 2, let's start by seeing what's in "/etc/rc2.d". On my system, I see this:
```
$ ls /etc/rc2.d/
README          S19cpufrequtils  S20postfix  S24dovecot     S50rsync      S70pppd-dns  S99grub-common  S99rc.local
S05loadcpufreq  S20cpufreqd      S20winbind  S25powersaved  S70dns-clean  S91apache2   S99ondemand
```
I don't have "gdm" installed, but I would expect to see "SNNgdm" in this directory if I did.

What's in your "/etc/rc2.d" directory?

---

### Post by roadrawts on 2011-03-04
Run Level

N 2

Same as you get.

ls /etc/rc2.d

README
S15bind9
S19postgresql
S20ebox
S20fancontrol
S20kerneloops
S20postfix
S20speech-dispatcher
S20winbind
S25bluetooth
S50pulseaudio
S50rsync
S50saned
S70dns-clean
S70pppd-dns
S75sudo
S90binfmt-support
S91apache2
S92tomcat6
S99acpi-support
S99grub-common
S99ondemand
S99rc.local
S99webmin

Hope this helps.  Thanks.

---

### Post by adriancs on 2011-03-05
I have successfully uninstall Ubuntu-Desktop from Ubuntu-Server by this code:
```
 
sudo apt-get remove Ubuntu-Desktop^

```
 
I should try disabling the Desktop GNOME mode before uninstalling. (auto log into console mode).
 
Thanks for the advice and guide. Truely appreciated. Thanks you.

---

### Post by egpetrich on 2011-03-07
> **roadrawts said:**
> Run Level
N 2
Same as you get.
ls /etc/rc2.d
...lots of files...

Agreed, you don't show "gdm" in this directory. If "gdm" isn't running automatically, what does your initial login screen look like?

---

### Post by James78 on 2011-03-09
> **adriancs said:**
> I have successfully uninstall Ubuntu-Desktop from Ubuntu-Server by this code:
```
 
sudo apt-get remove Ubuntu-Desktop^

```I should try disabling the Desktop GNOME mode before uninstalling. (auto log into console mode).
 
Thanks for the advice and guide. Truely appreciated. Thanks you.
Your welcome. ;)

---

### Post by shoe on 2011-03-10
> **egpetrich said:**
> That's puzzling. I'm running 10.04LTS, and I wouldn't have expected something so fundamental to change on a point release.

Runlevels have either gotten more complicated or less so since I had to pay a lot of attention to them. If I'm understanding things correctly, you'll end up in runlevel 2 by default when you boot. (At the moment, I don't know how to change that default. Perhaps the Powers That Be have decided you don't need to do so.)

Still, you can determine your current runlevel with the simple command "runlevel". I get this on my system:
```
$runlevel
N 2
```
The "2" means that I'm in runlevel 2, and the "N" means that I haven't changed it since boot. Therefore I default to runlevel 2.

Assuming that you also default to runlevel 2, let's start by seeing what's in "/etc/rc2.d". On my system, I see this:
```
$ ls /etc/rc2.d/
README          S19cpufrequtils  S20postfix  S24dovecot     S50rsync      S70pppd-dns  S99grub-common  S99rc.local
S05loadcpufreq  S20cpufreqd      S20winbind  S25powersaved  S70dns-clean  S91apache2   S99ondemand
```
I don't have "gdm" installed, but I would expect to see "SNNgdm" in this directory if I did.

What's in your "/etc/rc2.d" directory?

Same issue here guys. Can't for the love of god figure out how to disable gdm at boot. Don't you just hate it when they change things like this :confused:

I've tried:>  root@laura:~# update-rc.d -f gdm remove
 Removing any system startup links for /etc/init.d/gdm ...
   /etc/rc0.d/K20gdm
   /etc/rc1.d/K20gdm
   /etc/rc2.d/S20gdm
   /etc/rc3.d/S20gdm
   /etc/rc4.d/S20gdm
   /etc/rc5.d/S20gdm
   /etc/rc6.d/K20gdm
root@laura:~# sync
root@laura:~# reboot

To no avail.

Any ideas?

---

### Post by egpetrich on 2011-03-10
Well, my biggest idea so far is that **I'm** not going to install ubuntu-desktop on my own machine to test any of this out.

Oh, you want ideas that will help **you?** That's different....

I think we've been looking in the wrong places (/etc/rc*.d). Ubuntu currently uses the event-based init daemon "Upstart". [The Wikipedia entry for Upstart]("http://en.wikipedia.org/wiki/Upstart") notes:
> Upstart was first included in Ubuntu in the 6.10 (Edgy Eft) release in late 2006, replacing sysvinit. While the new Upstart daemon is used, most of the services are managed using the old sysvinit scripts. The reason for this has been attributed to missing features that prevent the complete replacement of the existing scripts with native Upstart service descriptions. Since then, Ubuntu 9.10 (Karmic Koala) introduced native Upstart bootup as of Alpha 6.

I think that the "/etc/rc*.d" directories are part of sysvinit and, as such, are potentially redundant. The important stuff is in "/etc/init/*.conf".

So I'll suggest looking for "/etc/init/gdm.conf". If you find it, and you're willing to trust suggestions from a guy who won't install "ubuntu-desktop" on his own system, you could try this:
```

sudo stop gdm
sudo mkdir -p /etc/init_disabled
sudo mv -v /etc/init/gdm.conf /etc/init_disabled

```
I figure it makes sense to stop "gdm" before you pull the config file out of "/etc/init". Since Upstart doesn't appear to support disabling scripts in place (in the way that the "/etc/rc*.d" directories do), I figure the safest course of action is to move the config script to another directory. (If your system won't boot correctly as a result, you can try using a live CD to move the config file back to its correct location.)

Hope this is helpful.

---

### Post by egpetrich on 2011-03-10
Looks like I can go one better on this topic. There was [another thread on this topic]("http://ubuntuforums.org/showthread.php?t=1305659") a while ago. Comment [#38]("http://ubuntuforums.org/showpost.php?p=8779720&postcount=38") from komputes suggests editing the GRUB2 configuration file to disable gdm.

Several people commented that without "gdm" in place, they weren't getting sound after bringing up the GUI with "startx". It's not clear that this was solved.

---

