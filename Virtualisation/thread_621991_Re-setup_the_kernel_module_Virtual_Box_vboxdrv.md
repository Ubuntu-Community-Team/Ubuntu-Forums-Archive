---
title: "Re-setup the kernel module Virtual Box vboxdrv"
date: 2007-11-24
forum: Virtualisation
---

### Post by SonicSteve on 2007-11-24
Morning friends,
I'm not sure if this happens after every update, or if something else causes this to happen but...
Virtual box is continually giving me this message when I try to launch any one of my virtual machine installations. It doesn't do it every time but usually a few times per week.

> VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Re-setup the kernel module by executing '/etc/init.d/vboxdrv setup' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 
If I do as it asks and run;
'/etc/init.d/vboxdrv setup' as root.
It works perfectly again, but I'm trying to find out why it's happening in the first place, or if anyone else is experiencing it and we are all just accepting it in silence.

---

### Post by SonicSteve on 2007-11-25
Am I really the only one experiencing this? That makes me wonder all the more why?

---

### Post by bodhi.zazen on 2007-11-25
The only time I have seen that is with kernel updates.

---

### Post by SonicSteve on 2007-11-25
> **bodhi.zazen said:**
> The only time I have seen that is with kernel updates.

No kernel updates here! I can say for certain that is not the culprit.

---

### Post by ben2talk on 2008-03-10
I have the same problem, now I have a launcher next to my Virtualbox launcher with the command gksudo /etc/init.d/vboxdrv setup
I have to click this and enter my password, and then wait for it to recompilebefore launching - only after a reboot. I can close and open it as often as I like, and when it's running it works quite normally.

What is making it revert every time I reboot? Surely it should only be done once!

---

### Post by SonicSteve on 2008-03-11
That's interesting, only after a reboot. Till now I haven't been able to pin down what the cause has been. I just rebooted an hour ago, lets see shall we?

It seems you may be right. It was just yesterday that I had to recompile the virtualbox kernel. I don't know how long it had been since my last reboot before that though. Like I said  I rebooted the machine earlier today and now the kernel is out of whack again. 

Does anyone have any ideas about this? 

My only thought is to have that command run on a system restart. It seems rather hackish though and would add to the bootup time.

---

### Post by EvilAngel on 2008-06-28
Hi,

I am running here an up-to-date Kubuntu:
```
$ uname -r
2.6.24-19-generic
```

I try to use VirtualBox and I am experiencing the same problem.

I have the good packages installed:
```
$ dpkg -l |grep virtual
ii  virtualbox-ose                             1.5.6-dfsg-6ubuntu1                                x86 virtualization solution - binaries
ii  virtualbox-ose-modules-2.6.24-16-generic   24                                                 virtualbox-ose module for linux-image-2.6.24
```

But I have the same message (it is a french install):
```

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Code de résultat : 
0x80004005
Composant :
Console
Interface : 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

```

When I try to do what you said (/etc/init.d/vboxdrv setup) I can't.
I can only try to restart, but it is not working:
```
$ sudo /etc/init.d/vboxdrv start
 * Starting VirtualBox kernel module vboxdrv
 * No suitable module for running kernel found.
```

Ideas ?

---

### Post by SonicSteve on 2008-06-29
> **EvilAngel said:**
> Hi,

I am running here an up-to-date Kubuntu:
```
$ uname -r
2.6.24-19-generic
```I try to use VirtualBox and I am experiencing the same problem.

I have the good packages installed:
```
$ dpkg -l |grep virtual
ii  virtualbox-ose                             1.5.6-dfsg-6ubuntu1                                x86 virtualization solution - binaries
ii  virtualbox-ose-modules-2.6.24-16-generic   24                                                 virtualbox-ose module for linux-image-2.6.24
```But I have the same message (it is a french install):
```

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Code de résultat : 
0x80004005
Composant :
Console
Interface : 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

```When I try to do what you said (/etc/init.d/vboxdrv setup) I can't.
I can only try to restart, but it is not working:
```
$ sudo /etc/init.d/vboxdrv start
 * Starting VirtualBox kernel module vboxdrv
 * No suitable module for running kernel found.
```Ideas ?

Did you install Vbox from the Ubuntu repositories or from the virtualbox website .deb installer? I would un-install and re-install. I would also make sure I get the one from the Virtualbox website. It's not Gpl license, it's Puel (personal use, evaluation license) but it's the lastest program straight from the programmers.

---

### Post by Balau on 2008-06-30
Had a similar problem. I use the non-ose .deb version downloaded from the site. I solved reinstalling the package:
```

gnome-open virtualbox_1.5.6-28266_Ubuntu_gutsy_i386.deb

```
Reinstall package
Delete old module? check.
Next
Recompile module? check.
Next

At the end of the reinstallation it worked.

---

### Post by kewljoe on 2008-07-02
> **Balau said:**
> Had a similar problem. I use the non-ose .deb version downloaded from the site. I solved reinstalling the package:
```

gnome-open virtualbox_1.5.6-28266_Ubuntu_gutsy_i386.deb

```
Reinstall package
Delete old module? check.
Next
Recompile module? check.
Next

At the end of the reinstallation it worked.

I run that and I get a page Load error...:confused:

---

### Post by acron1 on 2008-07-03
> **SonicSteve said:**
> That's interesting, only after a reboot. Till now I haven't been able to pin down what the cause has been. I just rebooted an hour ago, lets see shall we?

It seems you may be right. It was just yesterday that I had to recompile the virtualbox kernel. I don't know how long it had been since my last reboot before that though. Like I said  I rebooted the machine earlier today and now the kernel is out of whack again. 

Does anyone have any ideas about this? 

My only thought is to have that command run on a system restart. It seems rather hackish though and would add to the bootup time.

Well I seem to be having the same exact problem with my VirtualBox  v1.5.6_OSE and openSUSE 11. I get:

"VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Re-setup the kernel module by executing '/etc/init.d/vboxdrv setup' as root."

It's annoying having to /etc/init.d/vboxdrv setup every time I want to start VB.
Has anyone figured out the solution yet?:confused:

---

### Post by SonicSteve on 2008-07-03
> **acron1 said:**
> Well I seem to be having the same exact problem with my VirtualBox  v1.5.6_OSE and openSUSE 11. I get:

"VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Re-setup the kernel module by executing '/etc/init.d/vboxdrv setup' as root."

It's annoying having to /etc/init.d/vboxdrv setup every time I want to start VB.
Has anyone figured out the solution yet?:confused:

I found that this only happens when I restart my PC. As long as I don't reboot I don't have to do this. That's as much of a pattern as I've found. I would love to know how many people actually have this issue though.

---

### Post by acron1 on 2008-07-04
> **SonicSteve said:**
> I found that this only happens when I restart my PC. As long as I don't reboot I don't have to do this. That's as much of a pattern as I've found. I would love to know how many people actually have this issue though.

It's the same here, it runs fine until I reboot. I shut down every night since 95-100 watts at idle would not be the green thing to do.
I can't imagine that this doesn't have a simple solution.

---

### Post by acron1 on 2008-07-06
OK I think this may solve it:

[http://forums.virtualbox.org/viewtopic.php?t=6920](http://forums.virtualbox.org/viewtopic.php?t=6920)

---

### Post by rbanavara on 2008-07-13
For the OSE version you may have to install the kernel modules separately! Theya re available in the respository as virtualbox-ose-guest-modules-2.6.24-16-generic & virtualbox-ose-modules-2.6.24-16-generic. It was the same case for me & after installing this, the VBox starts like a magic. This installation is not required for non OSE version (I had tried it before). I was under the impression that just the installation of virtualbox package should be sufficient (as that was my experience with the non OSE version). And when it did not work, I was wondering there is something wrong / missing with my kernel. Then I hit upon these packages in the repository. Not sure why OSE version looks for this!

---

### Post by montgoss on 2008-07-13
I was having a this issue as well with the "No suitable module for running kernel found." error.  But I realized that it worked if I ran virtualbox as root ("sudo virtualbox").  So I checked the vboxusers group and found that my login was not a member of that group.  After adding myself to that group and logging out and back in, Virtualbox works.

In case you aren't familiar with groups, here's how to add your login to the vboxusers group:
System->Administration->Users and Groups
Click "Unlock" and type your password.
Click "Manage Groups"
Select "vboxusers" from the list
Click "Properties"
Click the checkbox next to your login name
Click "OK"
Logout and back in
Run Virtualbox normally

Hope someone finds this helpful.

---

### Post by dsledge on 2008-07-30
Just wanted thank everyone for their assistance. I had the same problem and, through the information in this thread, have solved my problem.

Essentially, this is what I did:

sudo virtualbox

WARNING: The character device /dev/vboxdrv does not exist.
	 Please install the virtualbox-ose-modules package for your kernel,
	 which is likely virtualbox-ose-modules-generic.

	 You will not be able to start VMs until this problem is fixed.
$ sudo apt-get install virtualbox-ose-modules-generic

All is well now!

Dennis

---

### Post by McHoon on 2008-07-31
Is there any way to make taking a kernel upgrade dependent upon the availability of the correspnding vboxdrv module. Seems like there is always a delay between the availability of the kernel and the virtualbox-ose-modules-2.6.24-xx.

I recently accepted the systems prompt to update to the latest kernel and forgot (again doh!) that it would break virtualbox. 

Just seems like an unnecessary irritation all I need to do is defer the kernel upgrade until the vbox modules are ready right? Why can I not get the system to do this for me?  

So I am having to boot old kernel manually until "virtualbox-ose module for linux-image-2.6.24.20-genric" pops up in package manager - presumably the system will notice this and offer upgrade right?.

Any advice how to avoid this irriting problem in future very welcome.

---

### Post by bodhi.zazen on 2008-07-31
You can always put kernel upgrades on hold, then update manually when you want.

Sometimes there is a tendency to upgrade without thinking of the consequences, but if things are working, why do they need to be upgraded ? I tend to do security only updates.

---

### Post by Speed Demon on 2008-08-09
I get ```
$ sudo apt-get install virtualbox-ose-modules-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  virtualbox-ose-modules-generic: Depends: virtualbox-ose-modules-2.6.24-20-generic but it is not going to be installed
E: Broken packages
```
upon trying to install this under a fresh reinstall of VB ose and fully up-to-date ubuntu / kubuntu (both) 8.04.1 Hardy

---

### Post by Paladin Michael on 2008-08-17
Concerning the virtualbox-ose-modules-2.6.24-20-generic package, I'm also having the issue where I can't install it.  After some digging it seems that the actual linux-image-2.6.24-20-generic module where I'd be getting the kernel that ose module is for isn't available.

I searched for the missing linux-image package and it seems there were a bunch of problems with the package and that it wasn't a stable update yet.  I haven't found a confirmation for this, but my hypothesis is that they've probably taken it off the repositories which aren't slated as pre-release repositories.
I had to restore my xorg.conf file backup from a backup after my last update run which got me looking into this since I hadn't seen any other problems. I guess it's the perils of using the Unsupported updates repositories. :)

EDIT: Seems someone filed a bug report on launchpad about not being able to install the linux-image-2.6.24-20-generic package.  I added a comment about the fact that the package isn't showing up in the repository package lists and also the contents of my sources.list file so they know which repositories it's not showing up in.  The bug is here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/257386](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/257386)

---

