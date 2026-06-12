---
title: "[TIP] Virtualbox breaks after 2.6.24-21 upgrade"
date: 2008-10-15
forum: Virtualisation
---

### Post by brianfreytag on 2008-10-15
There have been several reports that issuing the following command will solve the issue.  It is simpler than how I described at first.  It did not work for me (that's why I posted this how-to), but I have been asked to add it to this main post.

```
sudo /etc/init.d/vboxdrv setup
```

This will re-setup virtualbox, obviously.

Again, this did not work for me, but several others are having success... If this doesn't work for you, follow my steps below: 

*****************************************
Begin original message
****************************************
Note that this is NOT an upgrade to Intrepid, but a Hardy upgrade.

Yesterday's (Oct. 14, 2008 ) upgrade takes the kernel up from 2.6.24-19 to 2.6.24-21.

When you try to boot up a virtual machine, it sits at spawning session.

IIf you remove "quiet splash" in the boot options you see that there are no kernel modules, and this is what is causing it to fail.

If you get the new modules installed through synaptic (for the 24-21  kernel) or:

```
sudo apt-get install virtualbox-ose-modules-2.6.24-21-generic
```when you boot up a virtual machine it will tell you that something isn't right (I apologize, I didn't copy the exact error down before I fixed it) and that you need to reinstall virtualbox.

If you go to synaptic and uninstall virtualbox-2.0, and try to reinstall it, it will tell you that it won't.

You have to go to the virtualbox site and download the .deb package from them:

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

Install it.

It will ask you if you want to recompile kernal modules, and several other things... Allow it to do that.

Problem is then solved, and everything will install like it should.

Let me know if this helps anyone else.

---

### Post by olivao on 2008-10-15
Hey that worked fine!

Thanks for your post.

---

### Post by Guillaume Lecomte on 2008-10-15
The mix of Virtualbox and ose edition remains mysterious but ...
It works fine.

Thank you for the tip.

---

### Post by beun on 2008-10-15
that did the trick

thanks

---

### Post by MaindotC on 2008-10-15
When you say this:

IIf you remove "quiet splash" in the boot options you see that there are no kernel modules, and this is what is causing it to fail.

Do you mean removing this from the host o/s boot option or a VM that uses grub?

---

### Post by brianfreytag on 2008-10-15
> **strAlan said:**
> When you say this:

IIf you remove "quiet splash" in the boot options you see that there are no kernel modules, and this is what is causing it to fail.

Do you mean removing this from the host o/s boot option or a VM that uses grub?

In the actual Ubuntu 8.04 grub when you start up your computer.

---

### Post by tuskenraider on 2008-10-15
hey man i appreciate this.... it helped me alot!!  

tusken

---

### Post by howefield on 2008-10-15
> **brianfreytag said:**
> ```
sudo apt-get install virtualbox-ose-modules-2.6.24-21-generic
```when you boot up a virtual machine it will tell you that something isn't right (I apologize, I didn't copy the exact error down before I fixed it) and that you need to reinstall virtualbox.

If you go to synaptic and uninstall virtualbox-2.0, and try to reinstall it, it will tell you that it won't.

Surely running the command in the error you mention will fix the problem after the kernel modules are installed ?

Also, you are replacing the repository version with a non repository version, so you won't get updates to virtualbox unless you also add the virtualbox repository to your sources.list.

---

### Post by joey-elijah on 2008-10-15
Downloaded the .deb etc, but still it won't work. 

Now all i get is a "spawning session" which never budges from it's 0%.

Any ideas?!

The error i lovingly get non-stop is

> 
The VirtualBox support driver which is running is from a different version of VirtualBox. You can correct this by stopping all running instances of VirtualBox and reinstalling the software..
VBox status code: -1912 (VERR_VM_DRIVER_VERSION_MISMATCH).


Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Console
Interface: 
IConsole {d5a1cbda-f5d7-4824-9afe-d640c94c7dcf}


---

### Post by brianfreytag on 2008-10-15
Make sure you uninstall virtualbox before running the .deb from the site:

```
sudo apt-get remove virtualbox-2.0
```

I believe that is the correct package.  I'm not at my Ubuntu box at the moment.

If that doesn't work, go to Synaptic, search virtualbox.

The first (at least on mine) package shows virtualbox-2.0 or something along those lines.  Right click on that, and click "Mark for Removal."  Don't click "Mark for Complete Removal."

THEN proceed to download the .deb from the site and install it.

---

### Post by brianfreytag on 2008-10-15
> **howefield said:**
> Surely running the command in the error you mention will fix the problem after the kernel modules are installed ?

Also, you are replacing the repository version with a non repository version, so you won't get updates to virtualbox unless you also add the virtualbox repository to your sources.list.

+1 on adding the repositories.

That'll make it easier.  I personally don't like to add many 3rd party repositories to my sources.list, so I do most things manually.

---

### Post by howefield on 2008-10-15
> **brianfreytag said:**
> +1 on adding the repositories.

That'll make it easier.  I personally don't like to add many 3rd party repositories to my sources.list, so I do most things manually.

Yep, that's fine but people need to know that just in case :)

Another thing that occurred is that the version on the virtualbox website is the PUEL version, (Personal Use and Evaluation Licence), as opposed to the OSE (Open SOurce Edition) in the repository.

A small point I grant, but it may matter to someone.

The PUEL version is more feature rich and is worth using whether or not you have issues with a kernel update stopping your vm from working.

---

### Post by joey-elijah on 2008-10-15
> **brianfreytag said:**
> Make sure you uninstall virtualbox before running the .deb from the site:

```
sudo apt-get remove virtualbox-2.0
```

I believe that is the correct package.  I'm not at my Ubuntu box at the moment.

If that doesn't work, go to Synaptic, search virtualbox.

The first (at least on mine) package shows virtualbox-2.0 or something along those lines.  Right click on that, and click "Mark for Removal."  Don't click "Mark for Complete Removal."

THEN proceed to download the .deb from the site and install it.

ahh. i had removed it via a 'complete removal'... installed everything again and no action.

What should i do now? Install the 2.0 and then remove it (but not completely)?

---

### Post by brianfreytag on 2008-10-15
> **joey-elijah said:**
> ahh. i had removed it via a 'complete removal'... installed everything again and no action.

What should i do now? Install the 2.0 and then remove it (but not completely)?

I'm not sure the 2.0 will install through Synaptic.

Can you list out the packages that are installed when you search virtualbox in Synaptic?  I might have to defer until later on this evening when I get home (I don't have Ubuntu at work), but will do my best to get your problem resolved.

---

### Post by brianfreytag on 2008-10-15
There is another fix for this that I figured I'd add to my thread:

```
sudo /etc/init.d/vboxdrv setup
```

This might fix your problems as well.

It didn't do it for me, I had to do all the stuff I listed in the first post in this thread, but apparently it's working for other individuals, so I'd try that first.  Quicker and easier.

---

### Post by stephanecharette on 2008-10-15
If you are running VirtualBox from a .deb file you originally downloaded directly from VirtualBox:

You don't have to completely re-install VirtualBox.

Simply rebuild the kernel mods for the host.  Here is what I did this morning when I was stuck at that "spawning" dialog box:

sudo killall VirtualBox
sudo /etc/init.d/vboxdrv setup

Then start the VirtualBox GUI and boot your VMs as usual.  Nothing more complicated than that.

(I think these steps wont work on the OSE [Open Source Edition] -- but I don't have OSE installed so I'm not 100% certain.)

Stéphane Charette

---

### Post by brianfreytag on 2008-10-15
> **stephanecharette said:**
> If you are running VirtualBox from a .deb file you originally downloaded directly from VirtualBox:

You don't have to completely re-install VirtualBox.

Simply rebuild the kernel mods for the host.  Here is what I did this morning when I was stuck at that "spawning" dialog box:

sudo killall VirtualBox
sudo /etc/init.d/vboxdrv setup

Then start the VirtualBox GUI and boot your VMs as usual.  Nothing more complicated than that.

(I think these steps wont work on the OSE [Open Source Edition] -- but I don't have OSE installed so I'm not 100% certain.)

Stéphane Charette

Yeah, I've seen this around.

This didn't work for me, that's why I figured I'd post the way I fixed it.

But thanks for the comments!

---

### Post by MaindotC on 2008-10-15
I followed the directions as OP originally suggested and didn't have any problems.  I didn't uninstall VB for fear of losing my .vdi's so I reinstalled the .deb on both 32 and 64 Hardy's and everything is working fine.  Star for OP!

---

### Post by rambo15 on 2008-10-16
This solution worked fine for me as well. 
sudo killall VirtualBox
sudo /etc/init.d/vboxdrv setup
These steps should be moved to the top of this thread.

---

### Post by distrachi on 2008-10-16
> **brianfreytag said:**
> There is another fix for this that I figured I'd add to my thread:

```
sudo /etc/init.d/vboxdrv setup
```

This might fix your problems as well.

It didn't do it for me, I had to do all the stuff I listed in the first post in this thread, but apparently it's working for other individuals, so I'd try that first.  Quicker and easier.

this fixed it for me, thanks! Much easier than the original solution you posted.

I'm running VBox 1.6.4 (not OSE)

---

### Post by Vadi on 2008-10-16
"sudo /etc/init.d/vboxdrv setup" worked for me, just one command instead of reinstalling whole virtualbox. didn't even need to reboot. please add to the first post!

---

### Post by mirkic on 2008-10-18
Second solution solved problem.
Thanks

---

