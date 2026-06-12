---
title: "caveat: no/no/no ubuntu"
date: 2008-03-03
forum: Testimonials &amp; Experiences
---

### Post by lbelmond on 2008-03-03
=^.^=

---

### Post by oakgrove on 2008-03-03
So the moral of the story is, if you don't know what you're doing at all, and you really need Windows to keep working but you just gotta try this ubuntu thing on the bare metal (not in a virtual machine), pull the hard drive with Windows on it completely out of your machine, and set it aside.  Install a completely different hard drive that you can trash any way you like and install Ubuntu on that with no worries.  When you need it, just pull the cover off of your computer and put the Windows disk back in as good as new.

---

### Post by julian67 on 2008-03-03
No I don't think you're dumb but you definitely had some bad luck (too much!). 

As for the issues with Ubuntu, well some of them are persistent issues (certain scanners, wireless adapters and so on) and some are actually easily resolved but require a little time to learn some new tools. 

I can address a few issues as an example:

mbr: yes if you install from the live installer to external drive the  mbr on your PC's main drive will likely be overwritten. This can be prevented or cured; prevention: suggest reading the documentation here [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation). cure: there is a great free utility called supergrubdisk which can restore your windows mbr, it can also rewrite the bootloader to let you multiboot. I use this in preference to any of the commercial tools I was familiar with as a Windows user. 

Reading/writing to Win hard drives: this used to be unreliable and not possible by default. The latest version of Ubuntu can safely and easily write and read ntfs, it should do so without corrupting any files. If problems are arising from your version of ntfs-3g not respecting ntfs file permisssions you should probably update to a newer version. There's a useful link here [http://pagesperso-orange.fr/b.andre/security.html]("http://pagesperso-orange.fr/b.andre/security.html")

Most of the difficulties you experienced with Ubuntu can be overcome but it helps a lot if you're familiar with the environment in the same way as you're familiar with Windows. This can take time. Luckily there's a lot of great documentation and help available so you can take advantage of others' experiences and knowledge. It's true that there are a few pieces of hardware such as certain scanners, webcams and printers that may never be supported outside of Windows. Wireless difficulties look horrible but are more often overcome than not. 

As for Ubuntu merely being a tool, an enabler for your real work, well that's true. But a computer  isn't a hammer or a screwdriver, it's far more complex whatever OS is on there and it does take time to get comfortable with it. Hopefully you can get your mbr fixed and resume dual booting and the pressure will be off and you can learn at your own pace. Good luck.

---

### Post by ajgreeny on 2008-03-03
I am very sorry you feel this way about Ubuntu, but I think you are in a minority.  I would like to make a few points related to your problems.

1   Installing Ubuntu on a USB drive does not "destroy" your windows MBR in quite the way you suggest, it merely overwrites it with grub.  It is easy to restore the MBR if you wish and there are numerous references to how that can be done in this forum and on Windows websites.  Google is your friend; use it.

2   You made life slightly more difficult for yourself by choosing to install Ubuntu on to a USB disk; if you had chosen a partition on the internal disk there would be no problem of grub not appearing if the USB disk was not attached to the computer and you would get the option to boot to either OS at boot time. It is not too difficult to put grub onto the  external disk and then restore the windows MBR.  You will then need to set the boot sequence to external disk as the first boot device and the internal disk as the second boot device.  Now when you boot up, grub will appear if the USB disk is connected, but windows will boot automatically if the USB disk is not connected.

3   There should be no way that installing Ubuntu on your USB hard drive and then accessing your windows files by mounting the windows drive and using the files in some manner stops you using them when you boot into windows, as long as you didn't edit any windows system files in Ubuntu and then save them.  Remember windows does not even take any notice of linux permissions and ownership rights, so I am baffled by those comments of yours.

4   If you really do need x-root, as you call it, which I assume means a graphical login as root rather than normal user, it can easily be done. Again, a quick search in the forums would have taken you there, but in all honesty, there is really no need to log in as root; you can do everything that needs root privileges by using sudo in front of the command, or if you have a lot of commands to carry out over a considerable length of time you can get a root terminal by using ```
sudo -i
```which means you won't have to keep adding sudo and your password to every command.

As I said at the start, I am sorry you have had such an experience and are not happy with your Ubuntu use.  Most of us **are** very happy with the way this fine OS works and I suspect will not agree with your conclusions.  You were either very unlucky or did not do enough preparatory searching about the installation procedures, and the requirements of the system and the operator before you began.

I hope you do not give up entirely on linux or ubuntu after this bad experience, and wish you better luck when, or if, you try again

---

### Post by crackatoe on 2008-03-03
I have many questions about Ubuntu as well, but sometimes the help is a easy as keywords in this forum or out on the net.  I'm using Gutsy Gibbon, and NTFS Configuration Tool was the answer to access my various Window's volumes.  It's simple to use.

I also like how the terminal  window has the power and flexibility to seek and install an application, with one short command.  And if  the command wrong, the response from the terminal is so much more helpful than DOS in finding my mistake.  

It's not Windows, and I'm very glad of that.

---

### Post by PmDematagoda on 2008-03-03
This thread has been moved to the Ubuntu Testimonials and Experiences section as this is not a request for support.

---

### Post by lbelmond on 2008-03-03
> **oakgrove said:**
> So the moral of the story is, if you don't know what you're doing at all, and you really need Windows to keep working but you just gotta try this ubuntu thing on the bare metal (not in a virtual machine), pull the hard drive with Windows on it completely out of your machine, and set it aside.  Install a completely different hard drive that you can trash any way you like and install Ubuntu on that with no worries.  When you need it, just pull the cover off of your computer and put the Windows disk back in as good as new.

maybe the way... a little drastic... :-)

---

### Post by 3rdalbum on 2008-03-03
By "common user", you mean "Someone who has been using Windows all their life and have collected Windows-only peripherals"?

I'm sorry to say it, but the manufacturer of your printer, wireless card and webcam have not made drivers for Linux. In your current jobless situation, you probably can't afford to buy new things that *are* compatible.

But it makes sense that things that are made for Windows only will not work on Linux. If I buy something, I buy something that I know will be Linux-compatible rather than just buy any old junk and complain when it doesn't work.

I don't know what you mean by "x-root". I think you mean "root", which shouldn't be a problem for you if you are the administrator of the computer. The software in the repositories is not "obsolete" at all. There might be a newer version, but do you really need a newer version at this time? If you absolutely need a newer version, you can check on [www.getdeb.net](www.getdeb.net) or other Ubuntu packaging sites online for .deb packages. These still require you to be the administrator (of course) but they are simple one-click installs.

You could also look for "Autopackages" of the programs you want.

I have never had trouble with ownerships on Windows partitions mounted read/write from Linux. Your Windows partition must've had some damage on it.

For the third "No", you trusted your data to a proprietary program which messed things up too far. I fail to see how that is Ubuntu's fault.

It seems like most of your quibbles with Ubuntu are in regards to its treatment of your Windows, specifically its benign overwriting of your MBR (well, dude, it needs to get the bootloader somewhere in the boot process). Installing Windows would overwrite GRUB.

---

### Post by lbelmond on 2008-03-03
=^.^=

---

### Post by steveneddy on 2008-03-03
> **oakgrove said:**
> ... you don't know what you're doing at all....

I thought he was an IT professional.

> 
i'm a particular it professional:


You should have learned all of these skills in school.

Just an observation.

---

### Post by armandh on 2008-03-03
NO/NO/NO trying stuff out on mission critical machines DUH

---

### Post by K.Mandla on 2008-03-04
I'm not sure what the original message in this thread was, since the OPer has edited out his posts, and as a result the replies are very disjointed. I'm going to close it.

---

