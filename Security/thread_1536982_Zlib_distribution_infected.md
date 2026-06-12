---
title: "Zlib distribution infected?"
date: 2010-07-22
forum: Security
---

### Post by worksofcraft on 2010-07-22
The distribution files of zlib from [www.zlib.net](www.zlib.net) may contain a virus.

If you build and install it then next time you boot your computer. you will get...

1. Nautilus can't be used now, due to an unexpected error from Bonobo when attempting to register the file manager view server.

2. The panel could not register with the bonobo-activation server (error code: 3) and will exit. It may be automatically restarted.

You can repeat this test reliably in a virtual box machine. I tested both on a Windows and Ubuntu host with 3 different versions of virtualbox that all work fine with Hardy Heron installations that do not have zlib:

- Create new virtual machine
- Install Hardy Heron from ubuntu-8.04.1-desktop-i386.iso
- Do all the automatic updates.
- Install virtualbox guest additions.
- sudo apt-get install build-essential

- Fetch and extract zlib-1.2.5.tar.gz from zlib.net
- cd to your zlib folder, configure, build and then run
sudo make install.

reboot your virtual machine and it is unuseable.
If you send them e-mail about this you will get a virus alert back.

---

### Post by worksofcraft on 2010-07-23
Anyway I also tried installing zlib on a virtual machine running Ubuntu 10.04 (32bit) and I get similar problem:

Loads of dialog boxes saying:

The panel encountered a problem while loading
"OAFIID:GNOME_WorkspaceSwitcherApplet".
Do you want to delete the applet from your configuration?

ditto:
GNOME_FastUserSwitchApplet
GNOME_ClockApplet
GNOME_Panel_TrashApplet
GNOME_WindowListApplet
GNOME_ShowDesktopApplet
GNOME_IndicatorApplet
GNOME_NotificationAreaApplet
...but in this case if you delete them you do still have a panel with launchers and menus, so you might still be able to add them back. OTOH if you try doing system administration tasks it let's you type your password then simply doesn't work.

I'm so glad I use virtualbox and even have a snapshot to restore to :)

---

### Post by Lekensteyn on 2010-07-23
I don't think it's infected.
It might be an incompatibility between version 1.2.3 and 1.2.5, with libxml.
You shouldn't be compiling zlib for your system unless you know what you're doing.
Use package 'zlib1g' instead.

---

### Post by FuturePilot on 2010-07-23
> **Lekensteyn said:**
> I don't think it's infected.
It might be an incompatibility between version 1.2.3 and 1.2.5, with libxml.
You shouldn't be compiling zlib for your system unless you know what you're doing.
Use package 'zlib1g' instead.

This is more likely the case. Considering just how many packages have a dependency on zlib, installing a different version than what everything was compiled against is most certainly going to break something. Probably not a virus.

---

### Post by worksofcraft on 2010-07-23
Oh, well in that case it is important to know that we can't safely install the current version.

To avoid instabilities (such as Windows gets with .dll libraries) Linux .so libraries can have a version specified.

This must be what is needed for anyone who wants to learn or experiment with the latest zlib. I don't know the correct procedure yet, but will post it when I find out. ;)

---

### Post by worksofcraft on 2010-07-25
I explain in a mo, but my CONCLUSION is that zlib.net are innocent and the problem is distribution of Ubuntu being ignorant of how the File System Hyrarchy for libraries is intended!


Explanation:

Folder /lib contains libz.so.1.2.3.3 and a symbolic link libz.so.1 that also points to that tried and trusted library.
/lib is the folder that SHOULD be used by ALL the essential software! Certainly doing "sudo make install" of zlib 1.2.5 doesn't do anything to change /lib :o

Now there is also /usr/lib for user applications that are not part of the system software which would be essential to run your computer. Once again good old zlib "make install" does NOT do anything to corrupt what is there and so all our programming tools should just carry on as normal while we experiment with zlib.

What it DOES do is in /usr/local/lib where it creates libz.so.1.2.5 and symbolic links to the same, named libz.so and libz.so.1.

Now the entries in /usr/local/lib are precisely the ones that your local and possibly buggy development work is dealing with so that should be perefectly fine because the essential and the trusted installed software are not supposed to be using any of them... so why then are they getting used when I restart my virtual machine???!!!


IMHO the distribution packages need to be rebuilt to look in correct place for their shared object libraries :(

---

### Post by gargamelle on 2010-07-27
Hi everyone, I have the same problem, but I'm a novice linux user and being happy enough with having find out that is zlib what is making my login screen, my panel applets and some other issues to crash. Well, maybe is not zlib, as you say, but in anyway is when I install it or uninstall it when everything 'goes to the ****:spanish'.

Then, could I install libpng without installing zlib 1.2.5? because I really need to use libpng, which depends on zlib.

while some guru comes with the answers Ill try to install another zlib version or the libpng alone or whatever...

---

### Post by gargamelle on 2010-07-27
umm... I have been able to install this one [http://archive.ubuntu.com/ubuntu/pool/main/z/zlib/zlib_1.2.3.orig.tar.gz](http://archive.ubuntu.com/ubuntu/pool/main/z/zlib/zlib_1.2.3.orig.tar.gz) 

and there is no error in Ubuntu despite I have restarted: login screen ok, panel's applets allright, everything ok.
so... now I'm trying libpng...

ah! if zlib_1.2.3 is actually working, then there is something in 1.2.5 that works worse than in 1.2.3, or is less flexible or... dont know, it works!

---

### Post by worksofcraft on 2010-07-27
^ yes I agree, version 1.2.3.3 is fine.

You can install it with
System->Administration->Synaptic Package Manager

then search for zlib1g-dev, mark it for installation and click "Apply"

NOte: First it is best to remove the bad version 1.2.5
I did as follows:

cd /etc/local/lib
rm libz.so
rm libz.so.1

if it complains about them not being there then you don't need to remove them, but if you are not using root prompt in recovery mode then you may have to type "sudo" before the rm commands or permission could be denied!

---

### Post by gargamelle on 2010-07-27
hehe I'm novice but not so much (I guess xD) but thank you for being sensitive.

I have uninstalled with sudo make uninstall, and then installed the 1.2.3 with the typical ./configure;make;sudo make install

What I would like to know is if zlib boys or ubuntu people know that 1.2.5 with 10.04 is having such problems, because to people with little time with linux, ubuntu not having login screen and disabling all the panel applets etc could take us back to windows xp.

---

### Post by Ruslan Sharipov on 2013-02-15
I have downloaded [COLOR=Red]zlib-1.2.7[/COLOR] from [COLOR=Blue][http://www.zlib.net/](http://www.zlib.net/)[/COLOR] and have installed it by running 
[COLOR=Red]./configure
make test
make install[/COLOR]
from within the folder [COLOR=Red]/tmp/zlib-1.2.7[/COLOR], where I have unpacked the distribution archive [COLOR=Red]zlib-1.2.7.tar.gz[/COLOR]. Does it mean that I will have problems if I restart Ubuntu right now? 

The mattter is that I need to instal the latest version of Clam AntiVirus[COLOR=Red] clamav-0.97.6[/COLOR]. The matter is that zlib1g package is already installed on my computer. But running [COLOR=Red]./configure[/COLOR] from within [COLOR=Red]/tmp/clamav-0.97.6[/COLOR] package distribution folder I meet an error saying it needs [COLOR=Red]zlib[/COLOR] and [COLOR=Red]zlib-devel[/COLOR] packages to be installed. By the way, where can I download [COLOR=Red]zlib-devel[/COLOR] source file?

---

