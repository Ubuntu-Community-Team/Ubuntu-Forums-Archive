---
title: "boot windows partition from vbox"
date: 2012-07-19
forum: Virtualisation
---

### Post by z3nhakr on 2012-07-19
strange.. i tried to post this already but it didnt show up..whatever. ok so im trying to do exactly what the title says, boot into windows without rebooting but instead booting it using vbox. i tried and vbox so far just give me the error in the screenshot i attached. it would be sooooo cool if i could get it to work. Any ideas?

```
eerrrrrg nvm the screenshot. my connection is too slow so i copied the error:

Failed to open a session for the virtual machine seven.

VT-x features locked or unavailable in MSR. (VERR_VMX_MSR_LOCKED_OR_DISABLED).

Result Code: NS_ERROR_FAILURE (0x80004005)
Component: Console
Interface: IConsole {1968b7d3-e3bf-4ceb-99e0-cb7c913317bb}

```

---

### Post by z3nhakr on 2012-07-19
i was messing with vbox and found that i get that error whenever i try to boot any windows vm X_X  but linux vms work -.- . Any ideas?

---

### Post by CharlesA on 2012-07-19
Do you have hardware virtualization enabled in the BIOS?

---

### Post by sudodus on 2012-07-19
Are you trying to boot Windows via vbox from the same partition, that is booted directly via dual booting? Then I think that the copy protection of Windows will try to stop you, because the vbox is another machine (virtual, yes, but still another machine, and your license is for the real metal machine).

Years ago a found some web pages describing a work-around for XP, but I don't know if it is still possible. Anyway I would not recommend such work-arounds, since your license might be cancelled.

---

### Post by oldfred on 2012-07-19
I thought about trying to use virtual box for my existing XP, never did. Then someone posted these which now are very old. Use at your own risk.

Howto: Windows XP in both VM and native
[http://forums.virtualbox.org/viewtopic.php?t=9697](http://forums.virtualbox.org/viewtopic.php?t=9697)
Boot an existing XP (Physical HD) install with VirtualBox 
[http://ubuntuforums.org/showthread.php?t=769883](http://ubuntuforums.org/showthread.php?t=769883)
[http://ubuntuforums.org/showpost.php?p=6122463&postcount=6](http://ubuntuforums.org/showpost.php?p=6122463&postcount=6)

---

### Post by z3nhakr on 2012-07-19
i followed the instructions [here]("http://blog.amhill.net/2010/01/27/linux-ftw-using-virtualbox-with-an-existing-windows-partition/") and got to the boot manager but i cant boot into windows. i think it's because I'm using a wubi install. I'll attach a screenshot.

---

### Post by z3nhakr on 2012-07-19
> **CharlesA said:**
> Do you have hardware virtualization enabled in the BIOS?

I do now! :D
it was disabled by default. are there any drawbacks of having it enabled?

---

### Post by sudodus on 2012-07-20
What about the problem with repeated activations? See the attached picture.

---

### Post by z3nhakr on 2012-07-20
i doubt it. if it were repeated activations it would probably boot then tell me. i think it's because im using a wubi installation. ATM im working on migrating it to a new partition the i'll see if i still get the same error

---

### Post by sudodus on 2012-07-20
> **z3nhakr said:**
> i doubt it. if it were repeated activations it would probably boot then tell me. i think it's because im using a wubi installation. ATM im working on migrating it to a new partition the i'll see if i still get the same error
No, that is not the problem right now, that you cannot get it running. You will succeed :-)

But if you run the same instance of Windows directly, in vbox, directly, in vbox ..., you will need repeated activations (unless you find a way to by-pass that problem). And finally Microsoft might get tired of it and cancel your license.

So if you are 'moving' your Windows installation to vbox, it needs only one activation, which is OK.

---

### Post by CharlesA on 2012-07-20
> **z3nhakr said:**
> I do now! :D
it was disabled by default. are there any drawbacks of having it enabled?

No drawbacks.

> **sudodus said:**
> What about the problem with repeated activations? See the attached picture.

*shudders* Running into that with some VMs at work that have been moved between different VM software. NOT fun.

EDIT: @OP: If this is a wubi install, I doubt it will be a good idea to access the windows install on a VM because when you are using Wubi, you are running off a disk image on the windows partition.

---

### Post by z3nhakr on 2012-07-20
iv migrated my wubi install to a new partition but im still getting the same problem. grub is acting strangely and i think thats whats causing it. when i boot im first taken to the windows boot manager which looks like this:

Ubuntu 12.04 #wubi install#
windows 7 ultimate
ubuntu #migrated install/non wubi#

so i select the non wubi ubuntu which take me to grub. then i select the windows boot manager from the grub list and this is what the windows boot manager looks like now:

ubuntu
windows 7 ultimate (recovered)

this is what my windows boot manager looked like before i migrated?!?! and i also get the SAME one when i boot via virtualbox. so this means the previous configuration is still stored somewhere right? i deleted all of my windows BCD backup files and cant find anything else. this one has me stumped... Any ideas?

---

### Post by z3nhakr on 2012-07-20
grub is still being strange but i managed to boot windows 7 from virtualbox by running it as root. i know thats probably not the best idea but hey, it works

---

### Post by sudodus on 2012-07-21
If you want get a clean grub setting, I suggest that you reinstall grub (and after that update-grub) according to this link

[[COLOR="Red"]_https://help.ubuntu.com/community/Grub2_[/COLOR]]("https://help.ubuntu.com/community/Grub2")

> Reinstalling GRUB 2 from a Working System

If Ubuntu is operating normally, boot into the working installation and run the following command from a terminal.

    X is the drive (letter) on which you want GRUB to write the boot information. Normally users should not include a partition number, which would produce an error message as the command would attempt to write the information to a partition.

    ```
sudo grub-install /dev/sdX  # Example: sudo grub-install /dev/sda
```

This will rewrite the MBR information to point to the current installation and rewrite some GRUB 2 files (which are already working). Since it isn't done during execution of the previous command, running sudo update-grub after the install will ensure GRUB 2's menu is up-to-date. 

and ```
sudo update-grub
``` afterwards.

---

### Post by z3nhakr on 2012-07-21
thanks i'll try that. any ideas on why i have to boot as root?

---

