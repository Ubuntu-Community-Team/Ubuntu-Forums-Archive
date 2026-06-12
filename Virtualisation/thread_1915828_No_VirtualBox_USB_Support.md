---
title: "No VirtualBox USB Support"
date: 2012-01-27
forum: Virtualisation
---

### Post by Insi5464 on 2012-01-27
Greetings,
I'm on 11.10 and I am using Virtualbox from the repositories - 4.1.2, and I need USB support. So I went to the VB site and downloaded the extension and installed it, but I still have no USB support. I noticed that the VB site suggests that you should have the latest version - 4.1.8 - for the extension to work. So I downloaded the .deb and when I opened it with Software Center I got this message:
"Breaks existing package 'virtualbox' that conflict: 'virtualbox'. But the '/home/:D/Downloads/virtualbox-4.1_4.1.8-75467~Ubuntu~oneiric_amd64.deb' provides it via: 'virtualbox'"
I assume that by installing it, nothing bad would happen, but VB is CRITICAL for me and I cannot risk messing it up.
Is it safe for me to install 4.1.8? Or should I uninstall 4.1.2 first and then install 4.1.8?
Thanks

---

### Post by QIII on 2012-01-27
I don't know if this is stl the case since I just install VBox from their website, but it used to be that the version of VBox in the repos did not contain USB support because that part of the code was not open source.

You might try uninstalling via your package manager and installing from virtualbox.org per their instructions.  Make sure to install the Guest Additions and the extension.

I'd have to go look at my machine, which I am not at right now, but there are some steps/settings I think to get it working.  There is a manual at virtualbox.org that will be more helpful.

---

### Post by Insi5464 on 2012-01-27
Thanks for the reply QIII, but I really need to be sure nothing's going to 'break' before I start removing packages since I have to have VB working.

---

### Post by haqking on 2012-01-27
latest VB, extensions pack and make sure you are in the vboxusers group

This must be the 10000000000th time this has been asked so it is one of the above 3 that will solve the issue.

```
sudo usermod -a -G vboxusers username 
```

where username is obviously your username.

Also removing the old VB wont effect your actual machines, make sure you have backups of them, i put mine on a ext HDD.

Then remove old package, install latest and then point it to your VM folder whereever your VM hdd and files are stored

Cheers

---

### Post by Insi5464 on 2012-01-27
Thanks Haqking, I suspected that there was a way to change the group permission, but I could not find it in Unity. I also searched the forums a LONG time before posting this, but could not find anything. Anyhow, thank for the answer. I also back up my .vdi's to another location, I was more worried about the packages getting messed up.
Gonna give it a shot later today.

---

### Post by Insi5464 on 2012-02-07
Well, I removed the Repository version of VBox, and installed the latest version from the virtualbox site. I have the extension pack installed, and I added myself to the group 'vboxusers' [thanks haqking - there used to be a GUI for doing this in Gnome, I'm on Unity now] and I still get a message from VBox that says I do not have permission to access USB devices.
Any ideas?

---

### Post by Insi5464 on 2012-02-07
A system restart solved it. Thanks for the help.

---

### Post by physwizz on 2012-02-07
I have installed the latest vbox  (4.1.8 ) , I have installed the extensions and I have made myself a member of the vbox user group and I STILL have USB disabled. What else could be wrong?

---

### Post by haqking on 2012-02-07
> **physwizz said:**
> I have installed the latest vbox  (4.1.8 ) , I have installed the extensions and I have made myself a member of the vbox user group and I STILL have USB disabled. What else could be wrong?

have you restarted your machine

---

### Post by physwizz on 2012-02-07
> **haqking said:**
> have you restarted your machine
 
Yes I restarted both the vm and the ubuntu.

---

### Post by haqking on 2012-02-08
> **physwizz said:**
> Yes I restarted both the vm and the ubuntu.

using

```
groups
```

make sure you are in the vboxusers group.

and when you say disabled what do you mean ?

You go to devices menu and everything is greyed out ?

You know you need to select the device from devices menu you want to mount in the VM right ?

You can also try creating a USB filter.

Can you post a screen dump of your devices menu when the machine is running and the display of your group membership.

Cheers

---

### Post by physwizz on 2012-02-08
> **haqking said:**
> using

```
groups
```make sure you are in the vboxusers group.

and when you say disabled what do you mean ?

You go to devices menu and everything is greyed out ?

You know you need to select the device from devices menu you want to mount in the VM right ?

You can also try creating a USB filter.

Can you post a screen dump of your devices menu when the machine is running and the display of your group membership.

Cheers

yes, vboxusers is listed in the groups

The USB properties are greyed out

USB is not listed in devices.

---

### Post by haqking on 2012-02-08
> **physwizz said:**
> yes, vboxusers is listed in the groups

The USB properties are greyed out

USB is not listed in devices.

so you dont have a USB devices menu at all ?

from the VM itself (not the Vbox interface) go to devices menu, and there is not USB menu ?

Can you show us a screen dump.

Cheers

---

### Post by physwizz on 2012-02-09
> **haqking said:**
> so you dont have a USB devices menu at all ?

from the VM itself (not the Vbox interface) go to devices menu, and there is not USB menu ?

Can you show us a screen dump.

Cheers
  I'll do that soon.

Also, when I installed guest additions, there were a few occasions when I had to click "proceed anyway". Perhaps I could reinstall in safe mode?

---

### Post by haqking on 2012-02-09
> **physwizz said:**
> I'll do that soon.

Also, when I installed guest additions, there were a few occasions when I had to click "proceed anyway". Perhaps I could reinstall in safe mode?

proceed anyways because of what ?

errors ?

if so what errors ?

if you dont know what they were and clicked proceed anyways, then no comment ;-)

---

### Post by physwizz on 2012-02-10
> **haqking said:**
> proceed anyways because of what ?

errors ?

if so what errors ?

if you dont know what they were and clicked proceed anyways, then no comment ;-)
It looks like that was the problem. I reinstalled guest additions in with windows xp in safe mode and it has started to install the USB drivers after a reboot of ubuntu and windows guest.:)

IT WORKS!!!

---

### Post by haqking on 2012-02-10
> **physwizz said:**
> It looks like that was the problem. I reinstalled guest additions in with windows xp in safe mode and it has started to install the USB drivers after a reboot of ubuntu and windows guest.:)

IT WORKS!!!

cool glad you got it sorted.

Peace

---

