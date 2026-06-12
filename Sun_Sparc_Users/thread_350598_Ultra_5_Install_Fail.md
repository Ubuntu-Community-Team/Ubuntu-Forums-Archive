---
title: "Ultra 5 Install Fail"
date: 2007-01-31
forum: Sun Sparc Users
---

### Post by thekidrio on 2007-01-31
I am attempting to install ubuntu edgy server on my ultra 5 workstation. after the opb prompt (version 3.25.3) i type 
boot cdrom
it restarts and it comes to a prompt

[ENTER - boot install]  [Type "rescue" - boot into rescue mode]
boot:

I then hit ENTER and it starts... 
Allocated 8 megs of memory at 0x40000000 for kernel
Loading Kernel version 2.6.17
Loading initial ramdisk (5260517 bytes at 0x400000 phys, 0x40C00000 virt)...
Illegal Instruction


below is machine info

400 mhz Ulra sparc iii 384 mb ram

I would love to get this running as my dev server to play around with and such...

---

### Post by thekidrio on 2007-02-01
I followed the instructions for a net install found here

[http://ubuntuforums.org/showthread.php?t=270058]("http://ubuntuforums.org/showthread.php?t=270058")

I had to leave my cage early so i did not see it finish, however I have noticed that several people have had problems getting a UI to run. I am guessing the main problem is video ram and lack of support as I think linux sparc users are in the minority. I am hoping that because GNOME and CDE were running under solaris that I am going to be able to get atleast something running as a GUI. Not really much use as a desktop to me with out one. It would make a nice little home server maybe.  Once I am more familiar with the OBP and such I will see if I can't get a full read of the hardware on it.

---

### Post by Moulton on 2007-02-02
The 'illegal instruction' error message on an UltraSparc could arise if you attempt to boot without doing a 'reset-all' at the Open-Boot Prompt.  I found on my Ultra II that a simple 'reset' did not suffice.  Either power the machine off and on before booting from the CD, or do a 'reset-all'.  I'm not sure what additional hardware is reset, either at power-on or with 'reset-all', but I do know that the CD simply would not boot correctly otherwise.

---

### Post by Moulton on 2007-02-02
The 64-bit Sparc distribution of Ubuntu is designated as a 'Server' configuration, meaning it comes without the GUI Desktop.

On my Ultra II, I initially only had a VT login screen with no X-Windows GUI.

Using the curses-based 'aptitude' interface to 'apt', I downloaded one of the Desktop pagages.  (I found that I liked XFCE4 best.)  

My next problem was that the X.Org drivers did not work correctly with my older S-Bus video adaptor (CG-Six).  I found that I could connect to my Ultra from a remote X-Server over the LAN, but I had no local X-Server at the console.  The only fix for me was to buy the 24-bit UPA-slot video adaptor, for which the X.Org drivers do work.  Fortunately, I found the upscale video adaptor at bargain prices on eBay.

Since not very many people use the Sparc platform at all, and even fewer use it with the GUI Desktop installed, it won't surprise you to learn that there are some bugs in it above and beyond what I've already mentioned.

For example, I am obliged to use the Opera Web Browser because both the Firefox and Epiphany browsers freeze up shortly after being started.  Other applications (notably the VLC Media Player) operate erratically as well.  There exist drivers for the native Sun audio hardware, but you might have to add manual entries to /etc/modules to load the drivers.

One other thing -- a lot of the plugins that one might want for the browser may not exist for the Sparc architecture.  For example, GMail wants to use Macromedia Flash, but there is no Flash for the Sparc architecture.  The same is true for a lot of media plugins for codecs.  And of course there is no iTunes or Windows Media Player for the Sparc Linux platform.  Many other packages in the Ubuntu repository do not exist for the Sparc architecture.

---

### Post by thekidrio on 2007-02-02
I got it working with a few strange quirks. Such as it saying it can't find gnome when I know its installed. I use xubuntu on my laptop so I do like XFCE and thats working fine. It just seems strange that it will not see/run gnome. I am going to play with it some more today see what I can get running. Fun stuff for sure this, what ho. 

I chose the ATI driver I read that was usually the correct choice.

---

### Post by Moulton on 2007-02-02
Regarding Gnome, you might not have all the package components installed or configured.  You might go into Synaptic and do a reinstall of the dummy package that depends on all the many and varied parts for the Gnome Desktop.

If you have an ATI graphics adaptor, that's great.  All of my Sun machines are the older models with S-Bus and UPA slots for expansion cards.  There is limited support for S-Bus peripherals in the 64-bit versions of Sparc Linux.

For example, I have a SunVideo card.  As far as I know, the only drivers ever written for it run in Solaris only, and then only in legacy versions of Solaris.

Also, there is (as far as I know) no virtualization for the Sparc platform, so there is no way to boot into one of Solaris or Linux and run the other OS in a virtual machine.  At best, one can run Solaris binaries in Linux with a compatiblity package, much the way one can run Windows applications on x86 Linux with Wine.  I haven't played with that, as the only application that would be of interest is the one that accesses the SunVideo Card, and I'm assuming that the drivers for it are in the Solaris Kernel rather than in the UserLand application.

---

