---
title: "VirtualBox and Encrypted storage"
date: 2017-03-17
forum: Virtualisation
---

### Post by Sami_Mattila on 2017-03-17
VirtualBox seems to have serious problems with encrypted drives.
After installing Virtuabox on brand new Ubuntu 16 LTS (Gnome3) and reboot my PC was dead.
I now have to boot in emergency mode then "fix" the packages before I can decrypt my drives and gain access to the GUI.
(In GUI there does not seem to be any packages that need fixing. But every time I boot in emergency mode packages need to be "fixed.")
In GUI mode the decryption page sometimes comes up but basically making the OS unresponsive/dead.
Uninstalling VirtualBox did not fix the problem. Nor installing latest VirtualBox from the Oracle repo.

How can I fix the boot back to normal?

---

### Post by TheFu on 2017-03-17
What do the log files show, exactly?

---

### Post by Paddy Landau on 2017-03-17
This sounds quite bizarre if VirtualBox itself is causing the system to fail to boot. VirtualBox is, after all, just another application and doesn't hook into the kernel or anything like that.

What it sounds more like is that something has gone seriously wrong with the installation.

I have an important question:

Are you absolutely sure that you installed VirtualBox from the genuine Oracle website?

To try to fix this, I have some suggestions, but please be aware that I'm not an expert; these might not solve the problem.

Once you have managed to get into your system, open a terminal (press Ctrl+Alt+T) and enter these commands, in order. The first one will ask for your account password.
```
sudo apt --fix-broken install
sudo dpkg --configure --pending
sudo apt purge 'virtualbox*'         # This will uninstall VirtualBox
sudo apt update
sudo apt upgrade
sudo apt dist-upgrade
```
Then try rebooting.

If it doesn't work, please post back any error messages that you get.

If it does work, reinstall VirtualBox. Go to [the download instructions]("https://www.virtualbox.org/wiki/Linux_Downloads"), scroll down to "Debian-based Linux distributions". and follow those instructions. (If you don't understand the instructions, post back here and I'll explain.)

---

### Post by Sami_Mattila on 2017-03-18
The log files don't really say anything because Grub GUI dies before I can enter media decryption password(s).
This does not happen in text mode emergency mode.

---

### Post by TheFu on 2017-03-18
> **Sami_Mattila said:**
> The log files don't really say anything because Grub GUI dies before I can enter media decryption password(s).
This does not happen in text mode emergency mode.

And on the host machine?

BTW, if you boot, see a failure, next boot, us alternate boot media so the grub/boot log files aren't overwritten. View them that way. Might show something.

---

### Post by Sami_Mattila on 2017-03-22
:) I guess I was not clear enough. I'm talking about host machine... with encrypted hard-drives and Gnome 3.

---

### Post by Sami_Mattila on 2017-03-27
This is what comes first when I boot in Maintenance mode. In this text mode I can enter the decryption password.
[ATTACH=CONFIG]274318[/ATTACH]

After that I get the "Fix" screen and when I select fix-packets I get this...
[ATTACH=CONFIG]274317[/ATTACH]

Only when I am normally logged in after this there is never anything to fix until next boot. Then it's same thing all over again.

---

### Post by Paddy Landau on 2017-03-27
Sami, looking at this, I believe that your installation of VirtualBox is a side-issue. It is almost impossible for VirtualBox to be doing this. As far as the operating system and Ubuntu are concerned, it's just another app.

Rather, it is more likely that the installation process (not VirtualBox, but dpkg) went wrong, and something was left corrupted.

It doesn't help that you have so many drives attached — why is that?

I think that you need to repost this in the [General Help]("https://ubuntuforums.org/forumdisplay.php?f=331") forum. Please include in your post the following.
[LIST]
[*]That you are unable to boot after installing VirtualBox.
[*]Your two screen photographs.
[*]That you are using Gnome3 instead of Ubuntu.
[*]Boot from a Live CD (or DVD or USB), open a terminal, enter the following command, and include the output in your post.```
sudo fdisk --list
```
[/LIST]
I think that you will get better help there.

---

### Post by Sami_Mattila on 2017-03-31
I'm almost certain that you are wrong. Almost.
VirtualBox was the first installed Application that needed it's own DKMS kernel driver.
Problem seems to derive from the fact that Grub/kernel can't load crypto/luks in GUI mode.
This appeared right after installation of VirtualBox and my only question is how to fix the boot so I don't have to boot in maintenance mode.
I think this is related to... [https://forums.virtualbox.org/viewtopic.php?f=3&t=76791](https://forums.virtualbox.org/viewtopic.php?f=3&t=76791)
Only I disabled UEFI first thing.

---

### Post by Paddy Landau on 2017-03-31
> **Sami_Mattila said:**
> I'm almost certain that you are wrong. Almost.
VirtualBox was the first installed Application that needed it's own DKMS kernel driver.
Problem seems to derive from the fact that Grub/kernel can't load crypto/luks in GUI mode.
This appeared right after installation of VirtualBox and my only question is how to fix the boot so I don't have to boot in maintenance mode.
I think this is related to... [https://forums.virtualbox.org/viewtopic.php?f=3&t=76791](https://forums.virtualbox.org/viewtopic.php?f=3&t=76791)
Only I disabled UEFI first thing.
DKMS kernel driver? All that you need to do is install dkms, which isn't a driver.

The link that you posted is about booting into the guest system, not the host system. You say that it's your host system giving problems.

I have been using VB for years, on various Ubuntu distros from 8.04 onwards, including both Ubuntu 16.04 and Lubuntu 16.04. VB can't do what you suggest unless you did something quite odd during the installation.

So…

You didn't answer my earlier question: Where did you obtain VirtualBox and how, specifically, did you install it?

---

### Post by Sami_Mattila on 2017-03-31
I'm almost certain that you are wrong. Almost.
VirtualBox was the first installed Application that needed it's own DKMS kernel driver.
Problem seems to derive from the fact that Grub/kernel can't load crypto/luks in GUI mode.
This appeared right after installation of VirtualBox and my only question is how to fix the boot so I don't have to boot in emergency mode.

---

### Post by Sami_Mattila on 2017-03-31
After 4 hours of debugging this I finally found a work around from here... [https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/1359689](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/1359689)
Honestly. No wonder people use Windows & Mac rather that LInux.
Well at least I can now boot my PC up in text mode and unlock the disks.
Here are the settings that VirtualBox messed with in Grub /etc/default/grub

These settings work for now...
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""
GRUB_GFXMODE=1920x1080
GRUB_GFXPAYLOAD_LINUX=text



Remember to do update-grub after your fix.

---

### Post by Paddy Landau on 2017-03-31
Ah, right. Yes, that is a problem. I have just finished documenting encrypting Ubuntu on a single-boot or dual-boot machine, and the instructions include getting around this bug. I am waiting for the instructions to be placed on the Community Help Wiki.

Of course, this bug has nothing whatsoever to do with VirtualBox. It's a pity that you weren't able to describe the problem clearly, or I might have recognised it. Never mind &#8212; you managed to figure it out, and I'm pleased that you did.

Anyway, if you don't like Linux, by all means return to Windows or Apple &#8212; that's why we have competition, to fit all sizes. Linux isn't for everyone. Alternatively, you can try a different distribution, e.g. Fedora, which is very different from Ubuntu.

(Incidentally, the problem that you have is not caused by Linux &#8212; for example, Android is also Linux, did you know? The problem is caused by a faulty implementation of encryption setup, which is in its early days still. In its present state, it should not have been offered to the newcomer to Ubuntu. There is the option to encrypt the home folder, which is well-established and works properly. That's what I recommend for the newcomer.)

Best of luck whichever way you decide to go. We're always here if you have further questions &#8212; even if we're not always able to help as well as we wish we could.

---

