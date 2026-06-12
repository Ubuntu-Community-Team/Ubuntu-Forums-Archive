---
title: "win7 and xp dual boot or VM?"
date: 2012-11-13
forum: The Cafe
---

### Post by Sarys on 2012-11-13
So I'm about to get Win7 for my desktop but some of my games only work with xp. So should I dual boot my Win7 and xp (there will be Ubuntu as well) or should I just use xp with virtualbox or something like that?

---

### Post by Gremlinzzz on 2012-11-13
Do what you find easiest for you:popcorn:

---

### Post by Sarys on 2012-11-13
> **Gremlinzzz said:**
> Do what you find easiest for you:popcorn:

So I presume that means they both work?

---

### Post by oldfred on 2012-11-13
If you have the hardware you can do virtual install, but it may not be quite as fast, but saves rebooting.

If you want to dual boot, understand Windows normally installs all its boot files to the first install with the boot flag. Grub then only finds one bootable install, then Windows will have two entries to boot from.

 To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

---

### Post by dannyboy79 on 2012-11-13
if your system has 4gb+ of RAM then VM's are the way to go. Remember both Win7 and WinXP are way more ram hungry then Ubuntu (maybe not so much anymore because of Unity 3D)

---

### Post by cwsnyder on 2012-11-13
There is an alternative you haven't discussed yet in this thread, and that is the Windows 7 Professional with VirtualPC which loads a licensed copy of Windows XP in a virtual machine in Windows 7, all sanctioned and supported by Microsoft.

---

### Post by Sarys on 2012-11-14
> **cwsnyder said:**
> There is an alternative you haven't discussed yet in this thread, and that is the Windows 7 Professional with VirtualPC which loads a licensed copy of Windows XP in a virtual machine in Windows 7, all sanctioned and supported by Microsoft.

Windows 7 Pro's virtualpc doesn't support gaming

---

### Post by cwsnyder on 2012-11-14
There is a HOW TO in the Linux Mint Forums 'HOW TO to make dual-boot obsolete' which uses the Xen hypervisor in Mint to allow gaming in Windows 7 with a simple switch back to Mint and there are mentions that the same could be done with Windows XP.  Unfortunately, at least for me, it takes several minutes and several tries to get to [http://forums.linuxmint.com](http://forums.linuxmint.com) , so I did not include an exact link to the thread.

---

### Post by Paqman on 2012-11-14
Depends on what games you want to run in XP. Hardware accelerated graphics support in VMs is pretty rudimentary, if you want to play anything with 3D graphics then running on bare metal is the way to go. Things like old DOS-era games or anything else not requiring meaty 3D will be fine in a VM though. Last time I checked even early 3D games like Shogun (c.2000) actually ran ok in Virtualbox.

---

### Post by forrestcupp on 2012-11-14
> **cwsnyder said:**
> There is a HOW TO in the Linux Mint Forums 'HOW TO to make dual-boot obsolete' which uses the Xen hypervisor in Mint to allow gaming in Windows 7 with a simple switch back to Mint and there are mentions that the same could be done with Windows XP.  Unfortunately, at least for me, it takes several minutes and several tries to get to [http://forums.linuxmint.com](http://forums.linuxmint.com) , so I did not include an exact link to the thread.

If you're considering using a VM for gaming, this is the only way to go. Xen allows you to pass through your real GPU instead of using a virtual one. From what I understand, it's a pain to get working, though.

Other than that, any VM will be using a virtual video card, which is total crap for gaming, even with the 3D support turned on. So I say, if your old XP games are really that important to you, it would be better to put up with the hassle of dual booting.

---

