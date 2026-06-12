---
title: "Virtualisation on seperate HDs"
date: 2008-01-20
forum: Virtualisation
---

### Post by Tek-Noir on 2008-01-20
If I have ubuntu on one HD and Windows on another (not dual booting) and ubuntu as my primary OS is there anyway to set up a virtual machine to use my existing HD with windows on it with out to much trouble?

---

### Post by HermanAB on 2008-01-21
VMware has a product that can do that: [http://www.vmware.com/products/converter/](http://www.vmware.com/products/converter/)

I haven't used it, so do some googling before you buy.

Cheers,

Herman

---

### Post by scheuri on 2008-01-21
Short answer: No, it is NOT possible to do so!
At least not with major issues and real deep digging.
However, you might want to check out XEN, VmWare and other virtualization software which MIGHT be able to address an existing block device with a "real" installation (instead of a logical one).
But very most likely, no...no luck for you there.

VMware for example usually install the operating system you would like to virtualize in a normal file (which is the harddisk for that operation system).
That said, HermanAB is right. VMware has a tool which makes it possible to VIRTUALIZE an existing real installation and make a file (a vmware virtual harddisk) out of it which then can be copied onto linux (assuming you have enough space) and then can be used with Vmware.

I must, however, admit that it is always a good idea to make a clean install with vmware if you want to use windows as a guest system.
So you have a new shiny (and depending on your machine) fast enviroment.

Cheers
stefan

---

### Post by HermanAB on 2008-01-21
Well, you could also install VMware Server and then create a VM using the Windows HD as the target.

The following was copied from other threads:

You should be able to boot your XP installation from VMware Server by choosing "Advanced" when setting up the new VM. Choose to use a physical hard disk instead of a virtual disk, and point it to your XP drive.

You will need to boot XP natively first and create a new hardware profile, and then choose this profile when booting XP in the VM. Otherwise you will get the BSOD because XP will not be able to access the hard disk due to the native driver loaded, which is different than the VM driver. Choose a new hardware profile will force XP to load the low-performance Standard IDE driver and re-detect all hardware once in the VM. Don't forget to install the VMware Tools in the guest, and turn on Clock Sync option in VMware Tools!
 
---
 
File -> New Virtual Machine... -> Next -> Custom -> Next -> blah blah -> (Disk) Use a physical disk -> /dev/hda -> blah blah -> Finish.

When you boot the VM you'll see your GRUB menu where you should be able to select Windows XP. Be careful never to select your Ubuntu in this menu or you will have some issues trying to boot your OS twice!! haha.

Also remember that before you attempt to load XP in the VM, you need to boot it natively and create a new Hardware Profile. You'll then get the opportunity to select this Profile when XP is loading. I named my XP profiles "Native" and "Virtual" to make it obvious.

---

### Post by Tek-Noir on 2008-01-21
Brilliant, thanks. Ill give that a go (and keep my fingers crossed) lol

---

