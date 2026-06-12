---
title: "VirtualBox xVM how do I get USB to work"
date: 2008-09-11
forum: Virtualisation
---

### Post by charonred on 2008-09-11
I'm using Hardy 8.04.1 and have VirtualBox xVM installed which has USB support.

I can't figure out how to gain access to the USB ports from within VirtualBox XP

---

### Post by Goico on 2008-09-12
I have the same problem, I have created a filter with no specifications .. so every device I plug .. should be detected by de WinXP virtual machine right? well .. it does not :(
I had trouble connecting my gf's cellphone on Ubuntu 8.04.1 (it's a Samsung D900) so I went to the VM and installed Samsung's software .. but it didn't work either .. 

Thanks for your time, and excuse me charonred for not beeing helpful

---

### Post by Bakon Jarser on 2008-09-12
[http://ubuntuforums.org/showthread.php?t=770745](http://ubuntuforums.org/showthread.php?t=770745)

---

### Post by Goico on 2008-09-12
I have just edited the file as the how to explains. But using ssh because I'm not at home. I will try to plug the phone first thing in the morning tomorrow. Thanks a lot Bakon.

---

### Post by Bakon Jarser on 2008-09-12
No problem.  If you installed virtualbox through synaptic, or apt, or add-remove it may not work.  I think it only works with the binary from innotek.  There may be other ways to make usb work with the open source version but I'm not sure.

---

### Post by charonred on 2008-09-12
OK, I've nutted some of it out, but still need help.

Before starting a virtual XP (or other OS), go into settings > USB and add a blank filter. that should get a least one USB device going (in theory).

I had my Epson MFC scanner working briefly using the above method, but something went wrong and now I can't use my scanner at all (Xsane won't detect it in 'Hardy')

I found though that generally it doesn't seem to work with USB printers; with them I go into virtual XP and add a printer, choosing 'network' and not 'local', then feed XP your printers driver CD if it asks for it - that also keeps the printer accessible through 'Hardy' at the same time.

Unfortunately I still can't get access to my USB 'thumb' drives

---

### Post by Goico on 2008-09-13
I edited those files .. and got the VM to recongnize hardware I plug, BUT ... I can't transfer files .. I use Samsung's software but when I try to transfer pictures it freezes at 3x%
Same thing with a pendrive ... WinXP recongnizes it, but it freezes copying :(


I still have winxp (dual boot) but I hate rebooting :(

---

### Post by charonred on 2008-09-13
yeah, it's frustrating - xVM has USB support, but getting it to work is another thing altogether.

Until I get this XP VM working properly, I still have to dual boot; and I hate going into the actual XP install because after 6 months it's bloated and bogging down - takes forever to load and to do anything useful :(

---

### Post by haroldwong4728 on 2009-11-24
how do i get usb to work in virtual box in ubuntu 9.1 HELP!!!!!!!! i am new to ubuntu HELP!!!!!!!!!!!

---

### Post by howefield on 2009-11-24
Why are you bumping a more than year old thread ?

Which version of Virtualbox are you running ? (from Ubuntu repository or the version downloaded from the virtualbox website) ?

---

### Post by charonred on 2009-11-24
If you are using Virtualbox OSE (open source edition) which is the one available through Ubuntu's software channel, then USB is not supported; if this is the case then you need to install Virtualbox PUEL (personal use and evaluation licence) which does support USB.

It's available from Virtualbox.org on their [downloads page here]("http://www.virtualbox.org/wiki/Linux_Downloads") - just download the version you require to your desktop, once downloaded just click on the .deb file to start installation (this should also remove the OSE version).

Depending on the actual USB device, once you plug it in, then Ubuntu may detect it and open a file browser window or attempt run an application, or your guest OS may detect it and do likewise, sometimes at the same time as Ubuntu - so once plugged in, you may need to shut down the guest OS and adjust its Virtualbox settings; go to the USB section and add a device, then restart the guest OS (it's pretty self explanatory, but if unsure, read the documentation on their website).

tip: for future postings, a little more info is usually better than a posting messages like 
HELP!!!!!!!! i am new to ubuntu HELP!!!!!!!!!!! 
many users are new to Ubuntu, and require HELP, but making posts such as that don't clarify the problem being experienced, it's always best to keep the post on the actual topic, and then you'll get plenty of helpful advice from others on this forum.

And don't panic over Ubuntu (or any other flavour of Linux), there's a steep learning curve involved, but you'll be surprised after a few months just how much you have learnt, and how more control you have over your operating system when compared to something like Windows - have fun.

---

### Post by mister_p_1998 on 2009-11-25
Im running the latest VirtualBox (£.0.12.r54655) on Hardy and with default settings, USB devices are greyed out & I cant access them. HOWEVER, if I open a terminal and type 'sudo chmod -R 777 /proc/bus/usb' and then run virtualbox, it works! and I can use USB devices. Unfortunately these settings are lost on reboot, how can I make these chmod values permanent?

Steve

---

### Post by charonred on 2009-11-25
That's odd; I'm using 3.0.12 r54655 as well (on Hardy 8.04.3 LTS), and USB works fine, not greyed out, no sudo needed - is yours the OSE or PUEL version ?

Maybe try uninstalling it via Synaptic, then download and install the PUEL version from Virtualbox website.

---

### Post by mister_p_1998 on 2009-11-25
PUEL, strangely my home pc sees usb fine but my works one has the problem! both Hardy & same VB version.
The FSTAB entry Fix seems to work so far anyway.

Steve

---

### Post by charonred on 2009-11-25
are both the PCs the same specs, or completely different units, either way it's still weird; I have VBox PUEL running on several PCs, mine & friends, Hardy, Jaunty and Karmic all with no USB probs ... strange.

---

### Post by mister_p_1998 on 2009-11-25
Home pc is a crappy asrock p4 3.0ghz, work is a dual core, very nice.

---

### Post by i_doc on 2009-11-26
Hi 
I also stumbled onto this thread. Have same problem with virtualbox ose and usb  which was installed from the ubuntu  repository. I love Ubuntu and only need windows to run a billing program.
I hope someone can help.

---

### Post by charonred on 2009-11-26
i_doc
see my [post above]("http://ubuntuforums.org/showpost.php?p=8380135&postcount=11") - to get USB working you need to install the PUEL version instead of OSE version

---

### Post by ubu-for on 2009-12-11
Same here!

My USB devices are greyed out even though the VirtualBox USB filter says 2 devices, my USB hard disk (ext3) and my USB stick (fat), are active.

Now, I've unplugged the USB stick in MacOS X and plugged in again and got the following error message from VirtualBox.

```
Failed to create a proxy device for the USB device. (Error: VERR_READ_ERROR).

Details

Errorcode:
NS_ERROR_FAILURE (0x80004005)
Komponente:
Console
Interface:
IConsole {6375231a-c17c-464b-92cb-ae9e128d71c3}
```

---

### Post by ubu-for on 2009-12-11
Now, I've found the following thread and they could solve the problem because the host OS was Ubuntu and they changed the properties for vboxusers.

[http://ubuntuforums.org/showthread.php?t=1318160&highlight=virtualbox+usb](http://ubuntuforums.org/showthread.php?t=1318160&highlight=virtualbox+usb)

So I've switched to my guest OS Ubuntu instead, chose "Manage Group" and added a new group "vboxusers" with "Group Identifier" 1000. The USB devices were still greyed out, but Ubuntu (guest) recognized my USB stick immediately.

During the next boot Ubuntu (guest) tried to find my "Shared Folder" on my USB stick and ended up in a system freeze.

After every reboot the new group "vboxusers" is gone and another idea to solve the problem by unchecking the USB 2.0 support in the VirtualBox settings was without success, aside from recognizing both USB devices, if I point over the little VM USB icon on the lower toolbar, but without any further effect.

---

### Post by ubu-for on 2009-12-11
The bug is now mentioned at the official forum.

[http://forums.virtualbox.org/viewtopic.php?f=8&t=25474&sid=a363a4663669cfb5abff35d7d2e5793c](http://forums.virtualbox.org/viewtopic.php?f=8&t=25474&sid=a363a4663669cfb5abff35d7d2e5793c)

And here is some more.

[http://forums.virtualbox.org/viewtopic.php?f=8&t=23701&sid=a363a4663669cfb5abff35d7d2e5793c](http://forums.virtualbox.org/viewtopic.php?f=8&t=23701&sid=a363a4663669cfb5abff35d7d2e5793c)

---

### Post by ubu-for on 2009-12-12
After one day reading and testing USB works with MacOS as host and Ubuntu as guest with VirtualBox 3.0.12, VBoxGuestAdditions from VirtualBox 3.0.10 and adding a new empty USB 2.0 filter for my guest OS.

---

