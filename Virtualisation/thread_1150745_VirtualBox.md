---
title: "VirtualBox"
date: 2009-05-06
forum: Virtualisation
---

### Post by watsgoodg on 2009-05-06
I checked Synaptic Package Manager and didnt see VirtualBox to install.  Some help would be great!

-Thanks.

---

### Post by Kareeser on 2009-05-06
It should be there under "virtualbox-ose" or "virtualbox-2.2"

**virtualbox-ose - x86 virtualization solution - binaries**
virtualbox-ose-dbg - x86 virtualization solution - debugging symbols
virtualbox-ose-guest-source - x86 virtualization solution - guest addition module source
virtualbox-ose-guest-utils - x86 virtualization solution - guest utilities
virtualbox-ose-source - x86 virtualization solution - kernel module source
**virtualbox-2.2 - Sun VirtualBox**

The two bolded ones.

---

### Post by Therion on 2009-05-06
Be advised the OSE version (the one in the repos) will NOT support USB devices -- Zero USB support.  

Just mentioning that in case you weren't aware of the fact.

---

### Post by watsgoodg on 2009-05-06
> **Therion said:**
> Be advised the OSE version (the one in the repos) will NOT support USB devices -- Zero USB support.  

Just mentioning that in case you weren't aware of the fact.

What version will support USB... and how to you install.

Thanks for all the replys.

---

### Post by Therion on 2009-05-06
First off go here to download and install the .deb of Virtual Box that you want:  [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

Then, go here to learn how to set up and configure your Virtual Machine.  Do NOT use the download link provided in the tutorial - it goes to an older version of VB:

[http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html](http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html)

---

### Post by watsgoodg on 2009-05-07
> **Therion said:**
> First off go here to download and install the .deb of Virtual Box that you want:  [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

Then, go here to learn how to set up and configure your Virtual Machine.  Do NOT use the download link provided in the tutorial - it goes to an older version of VB:

[http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html](http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html)

Therion thanks much!!  The links was exactly what i was looking for. 

I have 2 questions?

1.  How can I configure virtualbox to auto start at startup of ubuntu?
2.  How can I configure the Virtual Machine to auto start once the machine boots up? 

Thanks again.
-Jason

---

### Post by Therion on 2009-05-07
> **watsgoodg said:**
> Therion thanks much!!
You're welcome.  Glad I could help.
 
> **watsgoodg said:**
> 1.  How can I configure virtualbox to auto start at startup of ubuntu?
You could try adding Virtual Box to your System Session I suppose.  I've never tried that but it would be the simple solution.

To do that see this link:  [http://www.linuxscrew.com/2007/08/09/autostart-programs-in-ubuntu/](http://www.linuxscrew.com/2007/08/09/autostart-programs-in-ubuntu/)

> **watsgoodg said:**
> 2.  How can I configure the Virtual Machine to auto start once the machine boots up? 
I don't know that you can.

---

### Post by Kareeser on 2009-05-07
You can add a script (or just a command) to the Ubuntu startup in "System -> Preferences -> Startup Applications

I believe the command is
```
VirtualBox -startvm [VM Name]
```

Check the casing on that... it might be "virtualbox" or "Virtualbox"...

---

### Post by watsgoodg on 2009-05-07
> **Kareeser said:**
> You can add a script (or just a command) to the Ubuntu startup in "System -> Preferences -> Startup Applications

I believe the command is
```
VirtualBox -startvm [VM Name]
```

Check the casing on that... it might be "virtualbox" or "Virtualbox"...

thanks again guys the following script worked!  I cannot believe it!  

VirtualBox -startvm WinXp

This might be a tough one anyone know how to set the virtual machine to automatically go into full screen mode when it opens up?

---

### Post by watsgoodg on 2009-05-08
Nothing...

---

### Post by thomasr on 2009-05-08
I think this will work:

~$ VBoxSDL -fullscreen -vm YourVirtualMachine

---

### Post by watsgoodg on 2009-05-08
> **thomasr said:**
> I think this will work:

~$ VBoxSDL -fullscreen -vm YourVirtualMachine

?

ubuntu@ubuntu-laptop:~$ VBoxSDL -fullscreen -vm WinXP
Sun VirtualBox SDL GUI version 2.2.2
(C) 2005-2009 Sun Microsystems, Inc.
All rights reserved.

Error: machine with the given ID not found!

---

### Post by thomasr on 2009-05-08
subsitute the name of the virtual machine for "YourVirtualMachine" in the command.

---

### Post by lukeiamyourfather on 2009-05-08
Look at the documents and help for command line arguments. It'll save a time and be easier than asking people on a forum for the basics. There's probably a man page for it when it was installed.

```
man virtualbox
```

Or maybe built in help for it...

```
virtualbox -h
```

There are no dumb questions, you just might get a dumb answer that you could have found yourself in 30 seconds. Cheers!

---

### Post by watsgoodg on 2009-05-11
> **lukeiamyourfather said:**
> Look at the documents and help for command line arguments. It'll save a time and be easier than asking people on a forum for the basics. There's probably a man page for it when it was installed.

```
man virtualbox
```

Or maybe built in help for it...

```
virtualbox -h
```

There are no dumb questions, you just might get a dumb answer that you could have found yourself in 30 seconds. Cheers!

ubuntu@ubuntu-laptop:~$ man virtualbox
No manual entry for virtualbox

ubuntu@ubuntu-laptop:~$ virtualbox -h
The program 'virtualbox' is currently not installed.  You can install it by typing:
sudo apt-get install virtualbox-ose
bash: virtualbox: command not found

---

### Post by watsgoodg on 2009-05-11
> **thomasr said:**
> subsitute the name of the virtual machine for "YourVirtualMachine" in the command.

ubuntu@ubuntu-laptop:~$ VBoxSDL -fullscreen -vm WinXP.vdi
Sun VirtualBox SDL GUI version 2.2.2
(C) 2005-2009 Sun Microsystems, Inc.
All rights reserved.

Error: machine with the given ID not found!

Same error what am i doing wrong?

---

### Post by bigboy_pdb on 2009-05-11
Take out the ".vdi". It sould be:
```
VBoxSDL -fullscreen -vm WinXP
```

**EDIT**: The name that you use isn't the name of the .vdi file. It's the name of the virtual machine in the VirtualBox GUI.

---

### Post by albinootje on 2009-05-11
> **watsgoodg said:**
>  This might be a tough one anyone know how to set the virtual machine to automatically go into full screen mode when it opens up?

Looking at :
```

VirtualBox --help
VBoxManage --help|less

```
It looks like there's no such option.

Edit.. ah, good. VBoxSDL does the trick ;-) Thanks for the information.

---

### Post by watsgoodg on 2009-05-11
> **bigboy_pdb said:**
> Take out the ".vdi". It sould be:
```
VBoxSDL -fullscreen -vm WinXP
```

**EDIT**: The name that you use isn't the name of the .vdi file. It's the name of the virtual machine in the VirtualBox GUI.

ubuntu@ubuntu-laptop:~$ VBoxSDL -fullscreen -vm WinXP
Sun VirtualBox SDL GUI version 2.2.2
(C) 2005-2009 Sun Microsystems, Inc.
All rights reserved.

Error: machine with the given ID not found!

Same error.

I know its the right VM Name?


General
Name:

WinXp
OS Type:

Windows XP

---

### Post by albinootje on 2009-05-11
> **watsgoodg said:**
> ubuntu@ubuntu-laptop:~$ VBoxSDL -fullscreen -vm WinXP
What gives :
```

VBoxSDL --fullscreen --startvm WinXP

```

---

### Post by watsgoodg on 2009-05-11
> **albinootje said:**
> What gives :
```

VBoxSDL --fullscreen --startvm WinXP

```

ubuntu@ubuntu-laptop:~$ VBoxSDL --fullscreen --startvm WinXP
Sun VirtualBox SDL GUI version 2.2.2
(C) 2005-2009 Sun Microsystems, Inc.
All rights reserved.

Error: machine with the given ID not found!

---

### Post by albinootje on 2009-05-11
> **watsgoodg said:**
>  Error: machine with the given ID not found!

A search engine search for this :
```

VBoxSDL "ID not found"

```
shows very little :(

Did you mix different VirtualBox version by installing and uninstalling them ?
What's the output of :
```

ls -la .VirtualBox/
ls -la .VirtualBox/Machines/

```

---

### Post by watsgoodg on 2009-05-11
> **albinootje said:**
> A search engine search for this :
```

VBoxSDL "ID not found"

```
shows very little :(

Did you mix different VirtualBox version by installing and uninstalling them ?
What's the output of :
```

ls -la .VirtualBox/
ls -la .VirtualBox/Machines/

```

ubuntu@ubuntu-laptop:~$ ls -la .VirtualBox/
total 40
drwxr-xr-x  4 ubuntu ubuntu  4096 2009-05-06 05:53 .
drwxr-xr-x 37 ubuntu ubuntu  4096 2009-05-11 09:09 ..
-rw-r--r--  1 ubuntu ubuntu  1055 2009-05-06 05:48 compreg.dat
drwxr-xr-x  2 ubuntu ubuntu  4096 2009-05-11 07:48 HardDisks
drwxr-xr-x  3 ubuntu ubuntu  4096 2009-05-06 05:53 Machines
-rw-------  1 ubuntu ubuntu  1912 2009-05-11 07:49 VirtualBox.xml
-rw-r--r--  1 ubuntu ubuntu 14404 2009-05-06 05:48 xpti.dat

ubuntu@ubuntu-laptop:~$ ls -la .VirtualBox/Machines/
total 12
drwxr-xr-x 3 ubuntu ubuntu 4096 2009-05-06 05:53 .
drwxr-xr-x 4 ubuntu ubuntu 4096 2009-05-06 05:53 ..
drwxr-xr-x 3 ubuntu ubuntu 4096 2009-05-06 05:55 WinXp

---

### Post by bigboy_pdb on 2009-05-11
The options "--fullscreen" "--startvm" don't work with my version of VirtualBox. It looks like they work with yours, but you should use the command
```
VBoxSDL --help
```
to see what options should work with your version of VirtualBox

You can also try:
```
VBoxSDL -fullscreen -vm WinXP
```

You should also check that you're using the correct name in the VirtualBox GUI. For example, if the name is "Win XP" in the GUI (without the quotes) then you need to use "Win XP" (with the quotes) in the command line.

If this doesn't work then you can use the hard drive UUID to start the virtual machine. You can find them using the command:
```
VBoxManage list vms
```

You would then use the command
```
VBoxSDL -fullscreen -vm *UUID*
```
where *UUID* is the UUID that was listed for the Windows XP virtual machine (but you may need to modify it based on the parameters that your version expects).

---

### Post by albinootje on 2009-05-11
> **watsgoodg said:**
> 
ubuntu@ubuntu-laptop:~$ ls -la .VirtualBox/Machines/
total 12
drwxr-xr-x 3 ubuntu ubuntu 4096 2009-05-06 05:53 .
drwxr-xr-x 4 ubuntu ubuntu 4096 2009-05-06 05:53 ..
drwxr-xr-x 3 ubuntu ubuntu 4096 2009-05-06 05:55 WinXp

Thanks for that. 

So you should try again with "WinXp" instead of "WinXP" (lowercase p instead of uppercase P)!

---

### Post by watsgoodg on 2009-05-12
> **albinootje said:**
> Thanks for that. 

So you should try again with "WinXp" instead of "WinXP" (lowercase p instead of uppercase P)!

You guys Rock!  I cant believe it actually worked!  I am able to completely switch over to Linux!  Cannot believe it...Thanks again guys!

---

### Post by albinootje on 2009-05-12
> **watsgoodg said:**
> I am able to completely switch over to Linux!  Cannot believe it...Thanks again guys!

Cool, congrats! :)

---

