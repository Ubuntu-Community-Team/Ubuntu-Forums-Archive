---
title: "Problems with 64 bit Oracle VM Virtual Box"
date: 2011-08-16
forum: Virtualisation
---

### Post by the-new-x on 2011-08-16
Hey guys, I am having trouble installed a 64 bit OS inside VirtualBox (windows 7 ultimate SP1 x64 to be more exact, and also windows server 2008 R2 x64), none of them are working, I get a warning from VirtualBox (the program) that I will have to change the settings of the OS that I am trying to boot into 32 bits instead of 64 bits (but I can't do that, the windows is not even booting!), and the error I am getting from both windows OS's is that they need a 64 bit machine to run. (And yes I have a 64 bit machine, and I have installed Ubuntu 11.04 natty narwhal x64 and I am sure of that, please help, I need windows 7 for AutoCAD and some other programs, and windows server because I am studying a course that requires it...

Thanks in advance!

---

### Post by androssofer on 2011-08-16
> **the-new-x said:**
> Hey guys, I am having trouble installed a 64 bit OS inside VirtualBox (windows 7 ultimate SP1 x64 to be more exact, and also windows server 2008 R2 x64), none of them are working, I get a warning from VirtualBox (the program) that I will have to change the settings of the OS that I am trying to boot into 32 bits instead of 64 bits (but I can't do that, the windows is not even booting!), and the error I am getting from both windows OS's is that they need a 64 bit machine to run. (And yes I have a 64 bit machine, and I have installed Ubuntu 11.04 natty narwhal x64 and I am sure of that, please help, I need windows 7 for AutoCAD and some other programs, and windows server because I am studying a course that requires it...

Thanks in advance!

apparantly it selects all the right options for ya... it appears they lied! haha. 

found this:

> Warning

On any host, you should enable the I/O APIC for virtual machines that you intend to use in 64-bit mode. This is especially true for 64-bit Windows VMs. See the section called “"Advanced" tab”. In addition, for 64-bit Windows guests, you should make sure that the VM uses the Intel networking device, since there is no 64-bit driver support for the AMD PCNet card; see the section called “Virtual networking hardware”.

on this page:

[http://www.virtualbox.org/manual/ch03.html#intro-64bitguests](http://www.virtualbox.org/manual/ch03.html#intro-64bitguests)

if thats of any help?

---

### Post by Paqman on 2011-08-16
Check the settings in Virtualbox. Specifically you need to go to the "General" tab and check that the version is "Windows 7 (64-bit)" or similar for Win server.

---

### Post by the-new-x on 2011-08-16
> **androssofer said:**
> apparantly it selects all the right options for ya... it appears they lied! haha. 

found this:



on this page:

[http://www.virtualbox.org/manual/ch03.html#intro-64bitguests](http://www.virtualbox.org/manual/ch03.html#intro-64bitguests)

if thats of any help?
Just started the installation of windows server 2008, and I got no warning, guess it solved it, thank you!
(But just for curiosities sake, what exactly does the IO APIC option do!?)

---

### Post by the-new-x on 2011-08-16
> **Paqman said:**
> Check the settings in Virtualbox. Specifically you need to go to the "General" tab and check that the version is "Windows 7 (64-bit)" or similar for Win server.
I already chose windows 7, but there isn't a 64 bit option in there, neither for windows 7 nor for windows server 2008! Thanks for the reply anyways!

---

### Post by androssofer on 2011-08-16
> **the-new-x said:**
> Just started the installation of windows server 2008, and I got no warning, guess it solved it, thank you!
(But just for curiosities sake, what exactly does the IO APIC option do!?)

no idea dude, just found tht link about it... haha. probly some sorta API for vms to chat to the processor. (as a guess)

---

### Post by the-new-x on 2011-08-16
> **androssofer said:**
> no idea dude, just found tht link about it... haha. probly some sorta API for vms to chat to the processor. (as a guess)
OK then, thanks anyways, but do you just search Google and find the results (technical stuff just like what you posted above) or is there a better alternative!?

---

### Post by androssofer on 2011-08-16
> **the-new-x said:**
> OK then, thanks anyways, but do you just search Google and find the results (technical stuff just like what you posted above) or is there a better alternative!?

i use google, but is always a trail to follow.. haha. so like google "issues installing 64bit windows vitualbox" then find an thread in the results about it, then in the comments of that thread is a link with info on it, then click that...  u get the idea.

dont know of a simpler way tho.. :-( and often its luck of the draw u google the right thing. cus googling "issues installing 64bit windows vitualbox" will b vastly different from "64bit windows wont boot in vitualbox ubuntu". so try lotsa things and 1 might work :-)

---

### Post by the-new-x on 2011-08-16
thanks for the reply, I guess that google is what we always need!
And btw, I just finished installing windows 7 SP1 x64 in virtual box, it installed correctly, with no errors, but it is still not working, I am still getting the usual warning as shown below:

[IMG]http://i1236.photobucket.com/albums/ff445/iareX/Screenshot-6.png[/IMG]

So if you have any ideas, please help, and if not, I'm already trying out google, thanks in advance!

---

### Post by Paqman on 2011-08-16
> **the-new-x said:**
> I already chose windows 7, but there isn't a 64 bit option in there, neither for windows 7 nor for windows server 2008! Thanks for the reply anyways!

Are you sure you have a 64-bit processor, and you've installed 64-bit Ubuntu? The option should be there, see the screenshot of my system I just took:
[IMG]http://ubuntuone.com/p/1AeH/[/IMG]

---

### Post by the-new-x on 2011-08-16
> **Paqman said:**
> Are you sure you have a 64-bit processor, and you've installed 64-bit Ubuntu?
Positive! And if you want, tell me how I can know, and I can take a screen shot and prove it to you!

---

### Post by the-new-x on 2011-08-16
I just came up across something, it looks like I need to have hardware virtualization enabled from the BIOS, and I am positive that I have a 64 bit CPU, but I can't find this option in my BIOS, any suggestions!?

---

### Post by Paqman on 2011-08-16
Open a terminal and type in:
```
uname -m
```
If it spits out x86_64, then you're running 64-bit. Are you running the full version of Virtualbox, or the one in the Ubuntu repos?

---

### Post by the-new-x on 2011-08-16
I have 64 bits according to uname -m:

[IMG]http://i1236.photobucket.com/albums/ff445/iareX/Screenshot-7.png[/IMG]

And I have downloaded the VirtualBox .deb file from the official website, and installed it. (when I double click, it took me the the software manager, and I have installed it from there) So I guess I have the full version!

---

### Post by Paqman on 2011-08-16
> **the-new-x said:**
> 
And I have downloaded the VirtualBox .deb file from the official website, and installed it. (when I double click, it took me the the software manager, and I have installed it from there) So I guess I have the full version!

Could well be the virtualisation options in your BIOS then.

---

### Post by haqking on 2011-08-16
in your VM machine settings go to system and acceleration tab

enable VT

64 bit guests need hardware virtualisation

---

### Post by the-new-x on 2011-08-16
> **haqking said:**
> in your VM machine settings go to system and acceleration tab

enable VT

64 bit guests need hardware virtualisation
I can't access the acceleration tab, it is blocked, any solutions!?

---

### Post by haqking on 2011-08-16
> **the-new-x said:**
> I can't access the acceleration tab, it is blocked, any solutions!?

when you say blocked you mean greyed out ?

The virtual machine needs to be powered off to edit your VM settings.

---

### Post by the-new-x on 2011-08-16
> **haqking said:**
> when you say blocked you mean greyed out ?

The virtual machine needs to be powered off to edit your VM settings.
Yes I mean grayed out, sorry about that, and the virtual machine was powered off when I tried!

---

### Post by haqking on 2011-08-16
> **the-new-x said:**
> Yes I mean grayed out, sorry about that, and the virtual machine was powered off when I tried!

can you show us a screen dump

Though you might need to enable hardware virtualisation support in your bios.  That will depend on your BIOS.

It is common, and probably why it is greyed out

---

### Post by the-new-x on 2011-08-16
First of all, sorry it is taking me long time to reply, but my internet is killing me today, here is the screen dump you asked for:

[IMG]http://i1236.photobucket.com/albums/ff445/iareX/Screenshot-8.png[/IMG]

Don't ask why my desktop looks that way, I'm working on it, LOL!

And when you say that it depends on my BIOS, and I am pretty sure that the virtualization option is not available in my BIOS, can i change it!? (And btw, I have a Toshiba satellite A505 laptop, and I usually download some stuff from the Toshiba website after I format my computer which is something that I do on regular basis, and one of the things that I download is a tool which allows me to update my BIOS, my version is 1.8, and I am sure it is the latest, but if there is any way that I can change my BIOS without any damage, I will sure do it.)

Sorry this was long, and thanks for reading it all!

---

### Post by haqking on 2011-08-16
you will need to look at your BIOS to see.  I did a quick google on your model and found people asking same question, some say the option is in there and others are saying it isnt.

I will leave you to find that out.

If the option is in your bios to enable hardware virtualisation (VT) then enable it and you cna run 64 Bit OS as guests.

IF you cant enable it then not much you can do as far as i know

see here

[http://forums.computers.toshiba-europe.com/forums/thread.jspa?threadID=18827](http://forums.computers.toshiba-europe.com/forums/thread.jspa?threadID=18827)

old thread but will give you an idea of what i am talking about without me having to type too much ;-)

---

### Post by the-new-x on 2011-08-16
> **haqking said:**
> you will need to look at your BIOS to see.  I did a quick google on your model and found people asking same question, some say the option is in there and others are saying it isnt.

I will leave you to find that out.

If the option is in your bios to enable hardware virtualisation (VT) then enable it and you cna run 64 Bit OS as guests.

IF you cant enable it then not much you can do as far as i know

see here

[http://forums.computers.toshiba-europe.com/forums/thread.jspa?threadID=18827](http://forums.computers.toshiba-europe.com/forums/thread.jspa?threadID=18827)

old thread but will give you an idea of what i am talking about without me having to type too much ;-)
OK, thanks a lot my friend, you have been a great help for me, and hope you will still be, as for the VT option, I am absolutely sure it is not in BIOS, my BIOS is really simple compared to others, and although it have very few options, I have once spent more than half an hour looking for the VT option in it, and yet did not find it! (I wanted to try Ubuntu before I installed it on VMware, but it did not work, so I had to download the 32 bit version just to test it out, and with my 256k Internet connection, it took around 8 hours, hope I will not have to do the same with Windows!)

---

### Post by haqking on 2011-08-16
> **the-new-x said:**
> OK, thanks a lot my friend, you have been a great help for me, and hope you will still be, as for the VT option, I am absolutely sure it is not in BIOS, my BIOS is really simple compared to others, and although it have very few options, I have once spent more than half an hour looking for the VT option in it, and yet did not find it! (I wanted to try Ubuntu before I installed it on VMware, but it did not work, so I had to download the 32 bit version just to test it out, and with my 256k Internet connection, it took around 8 hours, hope I will not have to do the same with Windows!)

no problem.

try updating your BIOS to latest version.

You may get the option

---

### Post by the-new-x on 2011-08-16
> **haqking said:**
> no problem.

try updating your BIOS to latest version.

You may get the option
It is in the latest version, I have updated the BIOS around 10-15 days ago, and for a relatively old computer model like mine (I bought it 2 years ago), I don't guess another update is out, thanks anyways, and perhaps it is time to start saving and get a new laptop, I'm thinking of Toshiba Qosmio, or maybe a Dell laptop, I've been hearing they are better than Toshiba, but who knows!

---

### Post by bodhi.zazen on 2011-08-16
*Thread moved to **Virtualization**.*

---

### Post by dino99 on 2011-08-16
Look at 64-bit guests:

[http://www.virtualbox.org/manual/ch03.html](http://www.virtualbox.org/manual/ch03.html)

---

### Post by haqking on 2011-08-16
> **dino99 said:**
> Look at 64-bit guests:

[http://www.virtualbox.org/manual/ch03.html](http://www.virtualbox.org/manual/ch03.html)

Yeah ive already told him he needs to enable hardware virtualisation VT support, and if it is greyed out for him so he needs to enable it in his bios which he cant

---

### Post by the-new-x on 2011-08-16
> **dino99 said:**
> Look at 64-bit guests:

[http://www.virtualbox.org/manual/ch03.html](http://www.virtualbox.org/manual/ch03.html)
I have already read the contents of that link, and from where I am standing right now, it looks like the only solution is to start saving for a new laptop, sometime you just can't wait to finish school, then college, and then become rich to own the best hardware there is!

---

### Post by northd_tech on 2011-09-06
> **the-new-x said:**
> It is in the latest version, I have updated the BIOS around 10-15 days ago, and for a relatively old computer model like mine (I bought it 2 years ago), I don't guess another update is out, thanks anyways, and perhaps it is time to start saving and get a new laptop, I'm thinking of Toshiba Qosmio, or maybe a Dell laptop, I've been hearing they are better than Toshiba, but who knows!

I'm having similar troubles installing 64bit Windows OS'es under VirtualBox 4.1.2 (but it runs 32bit virtual machines quite well- possibly some sound issues but that's not a huge problem for me).

My Phoenix 4.0 BIOS (Hewlett Packard F.34 version, 3/22/2011) was just upgraded yesterday (but the older F.32 BIOS also showed a Virtualization Technology "Enabled" setting).   The F.34 BIOS still seems to throw the same Win7 "64bit" error under either VirtualBox or QEMU.

I did just discover that there seems to be a conflict with the KVM Kernel Extension (which I will apparently need to remove from my Linux kernel to get VirtualBox to work)- see the attached screenshots.

I think I'll try the new VMWare Sphere that I just downloaded tonight before I jump through all those hoops.

EDIT:  **lsmod | grep kv** tells me this:

> Module                  Size  Used by
kvm_amd                37070  0 
kvm                   286527  1 kvm_amd
and **lsmod | grep vbox** tells me:
> Module                  Size  Used by
vboxpci                14281  0 
vboxnetadp              5710  0 
vboxnetflt             16670  0 
vboxdrv              1853374  3 vboxpci,vboxnetadp,vboxnetflt
It looks like I might be able to do a little blacklisting, but I'm going to build VMWare Tools first before I make any system changes.

Also, here are some resources:

[http://www.virtualbox.org/manual/ch03.html#intro-64bitguests](http://www.virtualbox.org/manual/ch03.html#intro-64bitguests)

**[Checking for Virtualization and 64 bit support from Linux]("http://jamesmcdonald.id.au/it-tips/checking-for-virtualization-and-64-bit-support-from-linux")**
[http://jamesmcdonald.id.au/it-tips/checking-for-virtualization-and-64-bit-support-from-linux](http://jamesmcdonald.id.au/it-tips/checking-for-virtualization-and-64-bit-support-from-linux)

Oracle Virtualization &#8211; Installing Oracle VM Server 2.2.1, Oracle VM Manager 2.2.0 and Deploying Oracle RAC 11gR2 (11.2.0.2) Oracle VM templates Linux x86 64 bit for test configuration
[http://gjilevski.wordpress.com/2011/02/11/oracle-virtualization-installing-oracle-vm-server-2-2-1-oracle-vm-manager-2-2-0-and-deploying-oracle-rac-11gr2-11-2-0-2-oracle-vm-templates-linux-x86-64-bit-for-test-configuration/](http://gjilevski.wordpress.com/2011/02/11/oracle-virtualization-installing-oracle-vm-server-2-2-1-oracle-vm-manager-2-2-0-and-deploying-oracle-rac-11gr2-11-2-0-2-oracle-vm-templates-linux-x86-64-bit-for-test-configuration/)

[http://www.virtualbox.org/](http://www.virtualbox.org/)

KVM.org
[http://www.linux-kvm.org/page/Main_Page](http://www.linux-kvm.org/page/Main_Page)

---

