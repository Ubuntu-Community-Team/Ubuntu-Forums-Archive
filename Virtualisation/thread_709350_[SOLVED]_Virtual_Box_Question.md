---
title: "[SOLVED] Virtual Box Question"
date: 2008-02-27
forum: Virtualisation
---

### Post by stuartwood89 on 2008-02-27
I tried running WINE for programs such as Photoshop, Winamp, Tubehunter etc.  But it just doesn't work.  I've heard a few good words about Virtual Box, so I'm willing to give it a go.  Before I do though, I just need to clear up a few things:

First and foremost, how do I uninstall WINE?

Secondly, do I 100% have to reinstall Windows inside VB, even though I have it on a separate drive?

Thirdly, will my 1GB of RAM and 2.4GHz single-core CPU be able to cope with it?

Running the x86 version of Ubuntu if that makes any difference.

Thanks for your help!

---

### Post by forestpixie on 2008-02-27
```
sudo apt-get remove --purge wine

```
there will be a hidden folder in you /home - .wine, you can get rid of that as well

yes with virtualbox you will need to install it 

I had no problems myself with similar ram and cpu

---

### Post by stuartwood89 on 2008-02-27
Ok, I'll give that a try.  I'll post again if I have any problems.

Thanks dude.

---

### Post by stuartwood89 on 2008-02-27
OK so I installed it, but when I went to try and install Windows I get:

> The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

Surely it shouldn't be this confusing?

---

### Post by forestpixie on 2008-02-27
you need to do as it says - go to users and groups - system >admin

pick the user you want to add - then find the vbox group and add it to the user 

then logout of buntu

---

### Post by stuartwood89 on 2008-02-27
Tried that and it still says the same thing when I try to start the VM.  I can't get to the stage where I install XP onto the VM.

---

### Post by MonctonJohn on 2008-02-27
Did you log out then log back in after adding your user to the vbox group? Any group changes only take effect on login.

---

### Post by stuartwood89 on 2008-02-27
Yeah Logged out but still doesn't work.

---

### Post by Marman on 2008-02-27
Open a terminal and type this command:

marker@marker-desktop:~$ grep vbox /etc/group
vboxusers:x:119:marker,pinto


If your name is not in the list of vboxusers, you can not start or use the interface. If your name is in fact listed and you *have* logged out and back in again, then try this command in the terminal:

sudo /etc/init.d/vboxdrv restart

If you get any errors, post them here and we can try to troubleshoot. 

cheers
-m

---

### Post by uxe1 on 2008-02-27
ok on the task bar, go to system/administration/users and groups
it'll ask for your password
click manage groups
scroll down to vboxusers, select it and hit property's
select all the users you want to have access to vbox
click ok, then log out and back in.
if that isn't working for you , then you may need to just reinstall vbox, because there is something weird going on

---

### Post by stuartwood89 on 2008-02-27
I know what I did wrong.  I made a new group.  Thanks for putting it in plain words for me uxe1, seems to be working now.

I'll keep this going in case there's anything else.

---

### Post by stuartwood89 on 2008-02-27
SO there's something else:  I have XP running in VB (and it works great), however when I go to My Computer, all I see is Local Disc (C:/), Floppy Disk and CD/DVD drive.  Is it possible to access the contents on both my actual Windows XP hard drive and my Ubuntu one?

Also:  There's no sound in the VM, how do I get thet working?

---

### Post by bodhi.zazen on 2008-02-27
For accessing your hard drive, I advise a network protocol, like samba.

The other option would be to install the addons and use a shared partition.

Last would be you could try to boot your physical install, there is a sticky here that walks you through it. Be warned however that doing so is beta.

---

### Post by stuartwood89 on 2008-02-27
I have no idea what any of those are. :confused:

---

### Post by bodhi.zazen on 2008-02-27
Samba : 	[https://wiki.ubuntu.com/ComprehensiveSambaGuide](https://wiki.ubuntu.com/ComprehensiveSambaGuide)
	[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

Shared folder : 

[noparse]http://doc.gwos.org/doku.php/doc:office:virtualbox#additions_.iso
[http://doc.gwos.org/doku.php/doc:office:virtualbox#sharing_your_hard_drive](http://doc.gwos.org/doku.php/doc:office:virtualbox#sharing_your_hard_drive)[/noparse]

With those last links, you need to manually copy-paste into your browser (problem with forums formatting on the url)

---

### Post by stuartwood89 on 2008-02-27
Just in case this all isn't necessary. The reason I want to access my Windows drive is because I have programs on there which I want to run from the disc.  Ideally I wouldn't have to install these programs in the virtual machine, but just shortcut them on the VMwin desktop.

---

### Post by bodhi.zazen on 2008-02-27
Naw, you need to install them on the virtual machine or boot your hard drive.

---

### Post by Fire_Chief on 2008-02-27
Unfortunately, because of how Windows manages program settings and libraries (read via the registry), you can't just shortcut the apps to your VM'd Windows environment. It won't know anything about the app you are trying to run (mostly applies to apps that use the registry, there are some exceptions).

The apps do need to be installed in your virtual environment to run properly (just as on a normal computer).

---

### Post by stuartwood89 on 2008-02-27
with that said, I'll just install my programs on the VM.  Thanks for your help guys.

---

