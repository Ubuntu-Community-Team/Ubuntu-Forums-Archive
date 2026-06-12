---
title: "difficult VMWare /Virtualbox decision"
date: 2008-03-07
forum: Virtualisation
---

### Post by stefansmith on 2008-03-07
Hi all,

This is my first post here.

I'm a Windows user since 3.1, but like many people, Vista is the end of the MS road for me. I can live with XP, but see the future as Linux, so I'm moving over -- something I've been meaning to do for years. After much experimention , I've opted for Ubuntu, and I like it, a lot.

A few of my key windows apps, however, do not run with Wine. These include J River Media Center (very family friendly) and Flight Simulator 2004, and specific in-house work apps. Plus a key piece of hardware -- a Nikon Coolscan.

For flexibility, I'd like to remain with a dual boot system (WinXP - Ubuntu), but am intrigued with virtualisation as a way of limiting the need to reboot, and I've narrowed down the choice to either VMWare or VirtualBox. Despite much searching, I'm having trouble deciding though, and would be most grateful for any help. Basically, I need a virtualisation that can:

- use the windows partition, as I don't really want to have two separate XP installs on the same machine.
- use USB devices, wifi, Internet;
- access a 500 GB media library (currently on an NTFS formatted HDD)
- Be as fast as possible and not too processor hungry (!)
- Be able to function on an Ubuntu with an RT kernel.
- Would be nice to run Windows apps on the Ubuntu desktop, kind of like with Wine, without the need for the full XP background. (think this is called 'seamless'?)
- Be easy to keep updated

My system is a Semron 3200+, 2GB RAM etc etc.

If running off a windows partition is considered a compromise, I may consider ditching dual boot altogether.

thanks in advance for any pointers!

---

### Post by drsox1899 on 2008-03-07
Hi there. 

Me too with a first posting !

I'm trying Ubuntu as I wasn't too impressed with Xandros 4, but I did use VirtualBox on Xandros to create a WinXp virtual machine.  I am guessing that it will work in much the same way on U.

You will need to create a FULL WinXp environment and go through the whole WinXp install (plus User Key Code etc).  After that it runs in its own window and can be entered/left at will (easy to do).  It communicates with the outside world easily (easy to email, internet from within).  Communicating with other part of a network are not difficult but involves creating a network bridge.

Some realtime hardware may not work inside the Virtual Xp as there are no "real" device drivers to install  e.g. I have a sound card that works outside Xp (Maudio 2496) that I used due to its professional level of D:A.  Can't get that working in the Virtual Xp.

Other than that all the "normal" Xp apps I tried seemed to work OK - iTunes etc.

Very fast, but does need a decent amount of RAM.

Regards

---

### Post by H_out on 2008-03-07
Hey,

Here are some details about my experience with VirtualBox 1.5.4.

I'm running Xubuntu 7.10 (host) with Windows XP Pro as a guest.

**USB:**
I'm using the VirtualBox Personal Use and Evaluation License (PUEL) version, NOT the VirtualBox-OSE version.  Among other differences, the OSE version doesn't have USB support.  The PUEL version requires a few minor tweaks to get USB devices working.


**Viewing NTFS drives:**
I have a shared folder that I use to swap files between my Xubuntu host and Windows guest.  It's easy to set up, and I'm guessing you can also share entire drives as well.  If you can see the drive from your host OS, then I'm pretty sure you can share it with your guest OS.


**Seamless:**
I don't run seamless, but I've attached a screenshot with seamless enabled.  It shows Notepad (Windows) and Mousepad (Xubuntu) running at the same time.  The desktop in the background is my Xubuntu desktop.  Seamless has some minor quirks, the main one being it won't work unless you have atleast one window open in the Windows guest.  My actual non-seamless setup is Xubuntu on viewport one and Windows on viewport two.  I use Compiz's Desktop Cube thing to switch between the two.  It switches in less than a second, and looks really slick when it's switching!
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=61876&stc=1&d=1204887556[/IMG]


**Speed:**
I have 1 GB of RAM and an Athlon64 3000 1.8Ghz processor.  I get occasional "hiccups" when I'm running things on the host and guest simultaneously, but it's really not that bad.  Other than that, it's extremely fast and responsive.  My Xubuntu boot time is about 30 seconds, and my guest OS boots in about the same amount of time.


**Internet:**
It's a snap!  It was literally as easy as checking a box that said "Enable Network Adaptor".


**Installing:**
I installed my guest OS onto a virtual hard drive that's basically a .VDI file that VirtualBox creates.  The VDI file is on the same partition as my Xubuntu, but I'm pretty sure you can create a virtual hard drive anywhere your host OS as access.

Hope this helps!

---

### Post by stefansmith on 2008-03-07
many thanks!
Think I'll give VirtualBox a try.
One other question -- I read that with VMWare, if the hardware doesn't work on Ubuntu, it won;t work in the guest. Is this the same with VirtualBox?

---

### Post by mozetti on 2008-03-07
In all virtualization, if the Host can't recognize the hardware the the guest won't be able to use it. It's the nature of virtualization -- the guest doesn't use the hardware in the traditional sense. The Virtualization software creates psuedo-hardware for the guest to use, and maps it to the Host's physical hardware. To visualize it (very) simply:

Guest OS<-->Psuedo-Hardware<-->Virtualization Software<-->Host OS<-->Physical Hardware

For that reason, some of your initial questions were redundant but only because you're learning (don't take this as an insult). :)

Here are the redundancies -- but the redundancy means that there should be no problems getting it to work:

USB devices/WiFi/Internet -- if it works in the Host OS, then you should be able to get it to work in the Guest OS.

Networking (wired or WiFi) -- there are multiple ways to do it, but the bottom line is that if you have a working network connection, then the Guest OS will have a working pseudo-network connection as long as you set it up correctly.

NTFS-formatted partition -- Again, as long as Ubuntu can use the drive (which it should) then the Guest OS will be able to use it. Just understand that the XP Guest won't interact with the drive natively as NTFS because it will be going through the Ubuntu Host and using ntfs-3g.

Finally, a word about the seamless mode in VirtualBox. It's how I've got mine set up and I really like it. As mentioned, seamless mode requires at least one windows program open and unminimized (windowed or maximized). I accomplish this by just putting a shortcut to the Calculator in my 'Startup' folder in XP.

---

### Post by stefansmith on 2008-03-07
> **mozetti said:**
> 
For that reason, some of your initial questions were redundant but only because you're learning (don't take this as an insult). :)


and none taken! you're right - I'm still learning... so thanks for the help. :)

So bottom line is that I'll need to stay with a dual boot setup for the time being, and I'm reading up on mounting that partition inside VirtualBox.

---

### Post by karyonix on 2008-03-09
With VirtualBox (non-OSE), you can let the guest OS have raw access to USB connected device.  Host OS have to be able to use USB controller (with USB hub), so VirtualBox can access the USB device.  VirtualBox does not emulate that USB device for the guest OS.  It just emulate USB controller and let guest OS drives the USB device.

With VirtualBox (non-OSE), you can use raw host hard disk from guest OS.  It can use entire disk, or some partitions.  
If you do it incorrectly, you can lose data in the drive.  But it is not really difficult to setup correctly.

---

### Post by mozetti on 2008-03-09
> **karyonix said:**
> With VirtualBox (non-OSE), you can let the guest OS have raw access to USB connected device.  Host OS have to be able to use USB controller (with USB hub), so VirtualBox can access the USB device.  VirtualBox does not emulate that USB device for the guest OS.  It just emulate USB controller and let guest OS drives the USB device.

With VirtualBox (non-OSE), you can use raw host hard disk from guest OS.  It can use entire disk, or some partitions.  
If you do it incorrectly, you can lose data in the drive.  But it is not really difficult to setup correctly.

Good to know, thank you.

---

### Post by HermanAB on 2008-03-10
BTW, the Linux equivalent for MS Flight Simulator is Flight Gear.  It has the same planes as MS.

---

### Post by stefansmith on 2008-03-11
Thanks. I'm trying flightgear, but to be honest I don;t find it anywhere near as good as FS2004. Nearly there, but not quite....

---

### Post by irw on 2008-03-21
Having used vmware for some time, I recently decided to ty VirualBox.

It was a relevation!  VirtualBox is so much easier to set up from scratch and to use.

Within a day I had removed vmware and now sticking with virtualbox

---

### Post by Kiri on 2008-03-21
I think VMWare allows you to use a physical XP install in the VM... But I personally haven't tried it. If you want to check it out, I think it is a sticky in this forum.

Personally I tried VMWare briefly, but found virtualbox much easier to use.

---

### Post by HermanAB on 2008-03-21
Virtualbox is good for use with Windows XP, but if you need to run other systems like Windows 2003 Server, or whatever, then VMware is better.

Basically, VMware works with anything while Virtualbox works with some things.  For that reason, I use VMware Workstation, but it depends on your needs.

---

### Post by siepo on 2008-03-21
VMware may have the edge in supported guest OS-es, but, according to [http://www.virtualbox.org/wiki/Guest_OSes](http://www.virtualbox.org/wiki/Guest_OSes) , VirtualBox works with 2000/XP/Server2003/Vista, most Linuxes, several other Unices and a few more exotic OS-es. I am using it myself with 2000/XP/Vista and Ubuntu Gutsy. I also have a win95 vm, but that one doesn't work too well.

---

### Post by HermanAB on 2008-03-21
Possibly true for low values of 'work'...

Eg, Win2003 - if it installs at all - will crash after about 30 minutes in Virtualbox.  VB is mainly geared towards WinXP and is very fast with WinXP.

---

### Post by siepo on 2008-03-21
Well, people often have wildly different experiences with the same piece of software. I didn't try server2003, but apart from win95 all the OSes I tried work fine for me.

---

### Post by obalonye on 2008-03-21
hi, i just just installed the Vmware workstation and i have created windows XP and i am getting this error trying to power on the virtual machine.. the error sayz

Unable to change virtual machine power state: Failed to connect to peer process.

---

### Post by fjgaude on 2008-03-21
The reason I use VMware server is that of all the stuff I've done with it it's reliable. It's how deep you go into the vm guest with apps and such that the strength of vmware starts to show.

That's my opinion at the moment. <smile>

---

### Post by squidhm3 on 2008-04-23
> **stefansmith said:**
> Thanks. I'm trying flightgear, but to be honest I don;t find it anywhere near as good as FS2004. Nearly there, but not quite....
Frankly with all the add-ons for FS2004 I don't think FlightGear can hold a candle to it - I still haven't figured out how to do things, not that I've spent a WHOLE lot of time with it.  Just too used to MS's flight sim i guess.

---

### Post by Chayak on 2008-04-24
> **obalonye said:**
> hi, i just just installed the Vmware workstation and i have created windows XP and i am getting this error trying to power on the virtual machine.. the error sayz

Unable to change virtual machine power state: Failed to connect to peer process.

Have you ran vmware-config.pl and let it compile the kernel module?  To get workstation to work on 8.04 and every time there is a kernel update I have to run in to recompile the kernel module.  Just make sure you have the build-essential package installed first as it needs gcc and the kernel headers.

---

### Post by fjgaude on 2008-04-24
> **obalonye said:**
> hi, i just just installed the Vmware workstation and i have created windows XP and i am getting this error trying to power on the virtual machine.. the error sayz

Unable to change virtual machine power state: Failed to connect to peer process.

Try running vmware from command line as root. If you can go to the directory where you have the VM and power up. Then exit and then use the GUI and see if you can now access the VM as non-root.

Let us know how you doing.

---

### Post by Registered2read on 2008-05-09
I have the exact same problem. I run a fresh install of Hardy 64 bit on an iMac Alu 24". The error message is the same either running vmware as user or as root. There is no log - nor in the vm directory nor in /var/log.

--
Nicolas

---

### Post by hdotcom on 2008-05-10
Hi,

I am a big fan of Vmware Server however i sometimes feel that its a cpu/resource hog. I've dedicated sufficient RAM to the VMs but i really havent been to use the VMs completely to the extent that id some times have to RDP to the VM in oppose to using the console.

Virtualbox on the other hand is lightweight and works like a charm on both Ubuntu and Windows XP. The seamless integration is a bit shakey on Windows XP guests but thats no biggie. 

I havent tried Vmware Server 2.0 beta on linux but i have tried it on Windows XP and i didnt like the whole web GUI at all! 

Rgds,

H.

---

### Post by Kaida on 2010-06-30
Superbump to ask if there's any new developments.  I'm a Linux new-user, and would REALLY like to "be rid of Microsoft" and virtualize anything I need them for.

Thanks!

---

