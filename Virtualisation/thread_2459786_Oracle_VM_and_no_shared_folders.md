---
title: "Oracle VM and no shared folders"
date: 2021-03-26
forum: Virtualisation
---

### Post by oygle on 2021-03-26
I used Oracle VM about 4 years ago ( [https://ubuntuforums.org/showthread.php?t=2345585&page=3&p=13580112#post13580112](https://ubuntuforums.org/showthread.php?t=2345585&page=3&p=13580112#post13580112) ) and didn't encounter the types of problems with not being able to do file sharing. Seems things have changed since then.

Kubuntu 20.04
Oracle VM Virtual Box Version 6.1.18 r142142 (Qt5.12.8)
Windows 8.1 as the Guest

I can't get shared folders to work at all. They need the "guest additions". Have downloaded the ISO, added that under Virtual box; it recognises the ISO in the settings keep getting a message that the Virtual box guest additions doe snot appear to be available on this virtual machine. Have even tried

```
sudo apt install virtualbox-guest-dkms
```

still no go. In further desperation (LOL) I tried adding a USB to see if Windows 8.1 recognises that - nope. The shared folder is setup correctly and is shown under the settings. To be able to use this VM I need to either get shared folders going via Guest Additions or solve the problem of the usb not being recognised.

Reading through a few posts here, there is mention of a product called VMWare, and no doubt there are other tools available. Although I really don't want to have to install Windows 8.1, plus MS Works plus MS Money again in another VM environment, if there is an easier and better tool that "works out of the box" then I will do that.

One other thing, performance is terrible running Windows 8.1 in this VM. It has 40 Gb of hard drive space and only uses about 12 Gb, plus there is 2 Gb ram and have checked whilst it is running and not much over 15% memory being used by it, plus CPU use is low. yet it is so **SLOW.**

---

### Post by ajgreeny on 2021-03-26
You first need to insert the a CD drive in Windows if it doesn't already have one using the VBox settings for Win 8.1, then in the VM itself go to ***Devices -> Insert Guest Additions ISO*** (I can't remember the exact wording of this but it's obvious when you see it.)

A dialogue box should appear in the Windows VM with autorun offering to install from the virtual CD ISO and following the various prompts will install the Guest Additions in the VM itself; all you have done so far is install the Guest Additions in VBox manager, not the guest.

I have done this in a VM of Windows XP and 10 but not 8.1 but they should all follow the same process as far as I'm aware.

---

### Post by oygle on 2021-03-26
> **ajgreeny said:**
> You first need to insert the a CD drive in Windows if it doesn't already have one using the VBox settings for Win 8.1, then in the VM itself go to ***Devices -> Insert Guest Additions ISO*** (I can't remember the exact wording of this but it's obvious when you see it.)


Thanks, I was trying to avoid having to burn a CD, it seems so primitive these days. But it seems it is the only way. My attempts to add the ISO from a folder were done within the Windows 8.1 guest/client, and it was shown as being enabled/active, yet it didn't get to install.

Now, do you think I will have to load the CD each time I want to use the VM ?  From memory that is what I had to do 4 years ago. I do hope they have progressed there and it is installed in place, and not a merry go round that I have to jump on...lol

Thanks for your help.

---

### Post by CelticWarrior on 2021-03-26
> [COLOR=#000000]Thanks, I was trying to avoid having to burn a CD[/COLOR]
it has nothing to do with burning a CD.
It's all virtual.
Your Windows VM needs to have a (virtual) "CD/DVD drive" first of all so you can use Virtualbox's Devices menu > Insert Guest Additions ISO (or CD?)... Then it should appear to the guest system exactly as a physical drive would. From there you run the installer for guest additions. It's really this simple.

You don't install "guest additions" in the host, with APT. That is only for when Ubuntu is the guest and you want to conveniently install the guest additions from the Ubuntu repository instead of the VB's software like you must do in a Windows guest.

---

### Post by oygle on 2021-03-26
> **CelticWarrior said:**
> it has nothing to do with burning a CD.
It's all virtual.

Yes, that was my assumption, but clearly it didn't work for me at all. Meaning, I tried many times to add the ISO (from disk, not CD) yet, even though the guest/client recognised the ISO on disk, it was never installed, the guest/client gave mo indication to install.

> **CelticWarrior said:**
> Your Windows VM needs to have a (virtual) "CD/DVD drive" first of all so you can use Virtualbox's Devices menu > Insert Guest Additions ISO (or CD?)... Then it should appear to the guest system exactly as a physical drive would. From there you run the installer for guest additions. It's really this simple.

Yes, and as you have pointed out "_it should appear_" - recognise yes, install no.

> **CelticWarrior said:**
> You don't install "guest additions" in the host, with APT. That is only for when Ubuntu is the guest and you want to conveniently install the guest additions from the Ubuntu repository instead of the VB's software like you must do in a Windows guest.

Of course, how can APT run in a windows client ?  When I finally did burn the CD, the windows client was able to install it. Yet, horror of horrors, now all I see in Windows is a blank screen.

Now considering either VMWare or KVM, I hope they don't give the problems that Oracle VirtualBox has given.

---

### Post by kema77 on 2021-03-27
> Although I really don't want to have to install Windows 8.1, plus MS  Works plus MS Money again in another VM environment, if there is an  easier and better tool that "works out of the box" then I will do that.


Have you considered using Wine? I can't speak for Works in general, but I am running older versions of Excel, Word and MS Money without major issues on Ubuntu 18.04. I have those programs running in a VM as well, but in my experience they run much snappier in Wine. Also Wine won't require the use of shared folders or USB devices to exchange data with your Windows programs.

---

### Post by ajgreeny on 2021-03-27
> **oygle said:**
> Yes, that was my assumption, but clearly it didn't work for me at all. Meaning, I tried many times to add the ISO (from disk, not CD) yet, even though the guest/client recognised the ISO on disk, it was never installed, the guest/client gave mo indication to install.

Yes, and as you have pointed out "_it should appear_" - recognise yes, install no.

Of course, how can APT run in a windows client ?  When I finally did burn the CD, the windows client was able to install it. Yet, horror of horrors, now all I see in Windows is a blank screen.

Now considering either VMWare or KVM, I hope they don't give the problems that Oracle VirtualBox has given.
It really isn't as difficult as you seem to be making it by using an actual CD disk, if that's what you mean you did.
Follow this list one by one and you should get the Guest Additions added to Windows with ease.

[LIST=1]
[*]Download the Extension Pack from [https://download.virtualbox.org/virtualbox/6.1.18/Oracle_VM_VirtualBox_Extension_Pack-6.1.18.vbox-extpack](https://download.virtualbox.org/virtualbox/6.1.18/Oracle_VM_VirtualBox_Extension_Pack-6.1.18.vbox-extpack) using your host, not the guest.
[*]Double click on the Extension Pack and it will install in the VirtualBox application.
[*]Check in VBox settings for Windows VM that there is a virtual optical drive available; it doesn't matter if it's empty.
[*]Start Windows VM.
[*]Go to Device in the VM's menus and click on ***Insert Guest Additions ISO/CD***, The wording may not be exact but it is pretty obvious.
[*]A dialogue box should open in the Windows VM offering to install Guest Additions, so accept that and follow the prompts.
[*]Reboot the VM, as you will be prompted to do, and you should then have the shared folder that you setup in the VM's settings.
[*]
[/LIST]
Good luck; let us know if it doesn't work.

---

### Post by oygle on 2021-03-27
> **kema77 said:**
> Have you considered using Wine? I can't speak for Works in general, but I am running older versions of Excel, Word and MS Money without major issues on Ubuntu 18.04. I have those programs running in a VM as well, but in my experience they run much snappier in Wine. Also Wine won't require the use of shared folders or USB devices to exchange data with your Windows programs.

I did try WINE a few years ago, from memory it proved to be a mess and too many problems. It will still be like a VM, meaning it is still a system within another system, so performance issues will always be present with those types of models.

> **ajgreeny said:**
> It really isn't as difficult as you seem to be making it by using an actual CD disk, if that's what you mean you did.
Follow this list one by one and you should get the Guest Additions added to Windows with ease.

[LIST=1]
[*]Download the Extension Pack from [https://download.virtualbox.org/virtualbox/6.1.18/Oracle_VM_VirtualBox_Extension_Pack-6.1.18.vbox-extpack](https://download.virtualbox.org/virtualbox/6.1.18/Oracle_VM_VirtualBox_Extension_Pack-6.1.18.vbox-extpack) using your host, not the guest.
[*]Double click on the Extension Pack and it will install in the VirtualBox application.
[*]Check in VBox settings for Windows VM that there is a virtual optical drive available; it doesn't matter if it's empty.
[*]Start Windows VM.
[*]Go to Device in the VM's menus and click on ***Insert Guest Additions ISO/CD***, The wording may not be exact but it is pretty obvious.
[*]A dialogue box should open in the Windows VM offering to install Guest Additions, so accept that and follow the prompts.
[*]Reboot the VM, as you will be prompted to do, and you should then have the shared folder that you setup in the VM's settings.
[*]
[/LIST]
Good luck; let us know if it doesn't work.

Thanks for your reply, very much appreciated. However, I have now decided to erase an old laptop, purchase a Win 8.1 key, download the ISO from Microsoft and then have it all running on a seperate box. The VirtualBox  had performance issues, making it almost impossible to use, even with 2Gb ram and a 4 core CPU. Then there were the problems with the 'guest additions' and I finally left it after all I see now is a Windows blank screen. So it is not suitable for me, and having it all on a seperate box means there shouldn't be performance issues, the file sharing will not be necessary, and it I get to choose when the necessary file conversions take place, without it becoming an encumbrance to the Kubuntu 20.04 laptop.

Thanks for your help though.  :)

---

### Post by ajgreeny on 2021-03-29
Jußt a warning, but I think you'll find that 2G ram for Windows 8 might be insufficient though I've never used 8 so could be wrong; it is certainly not enough for Windows 10.

---

### Post by SeijiSensei on 2021-03-29
With 4 GB, I give 2.5 GB to Windows and keep the rest for the Linux host.

---

### Post by oygle on 2021-03-29
> **ajgreeny said:**
> Jußt a warning, but I think you'll find that 2G ram for Windows 8 might be insufficient though I've never used 8 so could be wrong; it is certainly not enough for Windows 10.

Thanks, it certainly had performance issues, so that is probably why. 

> **SeijiSensei said:**
> With 4 GB, I give 2.5 GB to Windows and keep the rest for the Linux host.

Thanks, is there also a method to 'unload' the VirtualBox software, after I have used it ?  Meaning if I gave it 2.5 Gb or even 3 Gb ram and made sure the Linux host apps were all closed, did the work/exports, exited the VM and then also killed any processes that still had the VM software running ?

As it turns out, the plan to erase an old laptop and install Win 8 or 10 on that, have now come to a halt. I had no end of problems with trying to use the Microsoft ISO and a purchashed key, plus it does seem the HDD is well on its way out. Whereas in the Virtualbox, installing Win 8.1 and even other MS software was a breeze, abeit a bit slow of course.

There are some good instructions at [https://ubuntuforums.org/showthread.php?t=2459786&p=14028673#post14028673](https://ubuntuforums.org/showthread.php?t=2459786&p=14028673#post14028673) for installing the extension pack.

So, it may be back to the drawing board, and to now consider having yet another go at using the Virtualbox ...sigh

---

### Post by CelticWarrior on 2021-03-29
> [COLOR=#000000]is there also a method to 'unload' the VirtualBox software, after I have used it ? Meaning if I gave it 2.5 Gb or even 3 Gb ram and made sure the Linux host apps were all closed, did the work/exports, exited the VM and then also killed any processes that still had the VM software running ?[/COLOR]

If there isn't any VM running the Virtualbox's process memory usage is negligible. If you then close Virtualbox it's zero. There are no processes hanging just because you used Virtualbox and a VM.

If you're having another go at using Virtualbox make sure to follow the advice already given for the resources to allocate and other settings and yes, please install the matching Extension Pack before installing the VM. And after installing Windows with the ISO, remove it but DON'T remove the (virtual) CD drive. Then run Windows and use the Virtualbox's Devices menu > Insert Guest additions that should mount it as a (virtual) CD drive, open File Explorer and then that CD and run the installer (.exe).

---

### Post by oygle on 2021-03-29
> **CelticWarrior said:**
> If there isn't any VM running the Virtualbox's process memory usage is negligible. If you then close Virtualbox it's zero. There are no processes hanging just because you used Virtualbox and a VM.

Okay thanks for the clarification.

> **CelticWarrior said:**
> If you're having another go at using Virtualbox make sure to follow the advice already given for the resources to allocate and other settings and yes, please install the matching Extension Pack **before** installing the VM. 

Hmm, but I'm sure the guest additions install needs the VM installed and in place, it was something like "**Device |  Add**" or similar, within the VM ?

> **CelticWarrior said:**
> And after installing Windows with the ISO, remove it but DON'T remove the (virtual) CD drive. Then run Windows and use the Virtualbox's Devices menu > Insert Guest additions that should mount it as a (virtual) CD drive, open File Explorer and then that CD and run the installer (.exe).

Does that indicate that every time I run the guest inside the VM, I have to have the CD in the drive ?

---

### Post by CelticWarrior on 2021-03-29
> [COLOR=#000000]Hmm, but I'm sure the guest additions install needs the VM installed and in place, it was something like "[/COLOR][B]Device | Add" or similar, within the VM ?
[/B]
Extension Pack is NOT the same as guest additions.

The Extension Pack that, again, needs to match the Virtuabox's version is to be installed in the host, after installing Virtualbox. As the name suggests it's optional but knowing what it adds, namely support for USB3.0 and other perks, one could say it's *de facto* mandatory. I can't think of a reason to not install it.

Guest additions is something to be installed, if available, in the guest OS. It provides DRIVERS for the virtualized hardware, namely the virtual graphics card so you can use the VM full-screen.

I suspect this confusion is at the root of your predicament. 

> [COLOR=#000000]Does that indicate that every time I run the guest inside the VM, I have to have the CD in the drive ?[/COLOR]
No, like any other drivers installation it's to be done once.
After running the installer and rebooting the VM you can remove the inserted Guest Additions CD.

---

### Post by oygle on 2021-03-30
> **CelticWarrior said:**
> Extension Pack is NOT the same as guest additions.  ............... Guest Additions CD.

Thanks for your help. Today was able to install Win 8.1 on the old laptop and get through a looping error by modifying the Registry. That means I have no need at present to install any VM.

---

