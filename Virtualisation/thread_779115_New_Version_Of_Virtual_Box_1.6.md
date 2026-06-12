---
title: "New Version Of Virtual Box 1.6"
date: 2008-05-02
forum: Virtualisation
---

### Post by drsox1899 on 2008-05-02
BREAKING NEWS !!!!

New version of Virtual Box now available at :

[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)

Version 1.60

Supports Hardy Heron.

---

### Post by Tux Aubrey on 2008-05-02
Thanks for the heads-up.  

Hopefully the video driver issue with hardy guests will be solved now.

Interesting to see the extensive Sun branding now too - and the license agreement stuff.  That's "progress".

---

### Post by tighem on 2008-05-02
Hmm.. Had it running for 5 minutes and already:

1) Had to up my video memory to get it to display more than 8 bit colors.
2) Lost shared folders

Not off to a promising start

---

### Post by Tux Aubrey on 2008-05-02
> Hmm.. Had it running for 5 minutes and already:

1) Had to up my video memory to get it to display more than 8 bit colors.
2) Lost shared folders

Not off to a promising start

yes - I haven't had the video memory problem (although I tend to give VMs 32Mb anyway) - but none of my saved states could be saved (coming from 1.5.6)

Otherwise its working fine for me.

---

### Post by tighem on 2008-05-02
So I read in the VB forums to use the intel nic. I did put an intel NIC on and downloaded the driver for it and it does work. Rebooted, had to re-install the Guest drivers and rebooted again and I have shared folders back.

But they seem "slower" than before. I may try going back to the AMD drivers. I'm think the guest software didn't install right the first time.

---

### Post by oksi on 2008-05-03
I have this error when I install it on my AMD64 computer:

Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.

---

### Post by drsox1899 on 2008-05-03
Look at posts 3 and 4 of this thread.  It's a well known and easy to solve problem !

[http://ubuntuforums.org/showthread.php?t=691780&highlight=Host+USB+Proxy+Service+Virtual+box](http://ubuntuforums.org/showthread.php?t=691780&highlight=Host+USB+Proxy+Service+Virtual+box)

Note : These all refer to VB on 7.04.

---

### Post by oksi on 2008-05-03
Sorry :) 

The solution is: 
Enter
Code:

sudo gedit /etc/init.d/mountdevsubfs.sh

in the terminal (substitute gedit with either kedit/kate/kwrite if you're using Kubuntu). Scroll down to the following lines
Quote:
#
# Magic to make /proc/bus/usb work
#
#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb
remove the # mark from mkdir down to mount so it looks now like this
Quote:
#
# Magic to make /proc/bus/usb work
#
mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb
The HowTo states to log out and back in, but the changes won't fully work UNTIL you reboot. So, restart and you'll notice that the error message no longer appears.


On a side note, can anyone tell me why I can't get Internet using NAT on the xp guest in Virtual box? I'm thinking of purging everything and starting afresh.



After that I have to recompile vboxdrv as root to make it works.
enter code: /etc/init.d/vboxdrv setup

Thank you very  much

---

### Post by drsox1899 on 2008-05-03
> **oksi said:**
> 


On a side note, can anyone tell me why I can't get Internet using NAT on the xp guest in Virtual box? I'm thinking of purging everything and starting afresh.



You're the second person I've seen with this problem.

Tell me some more about what you are trying to do as I can't reproduce this problem.  See my posts on : [http://ubuntuforums.org/showthread.php?t=778437](http://ubuntuforums.org/showthread.php?t=778437).

---

### Post by cb951303 on 2008-05-03
I wish virtualbox had a GTK frontend too
I was very excited about kvm in 8.04 but it's been too unstable for me so I turned back to vb

edit: thinkin of it, solaris has gnome as a DE right? so sun may add a GTK frontend ?

---

### Post by FredB on 2008-05-03
Maybe. But it won't be a no-go for me until 64bits OS guests are not supported.

---

### Post by cb951303 on 2008-05-03
I installed the amd64 version of 1.6 from sun's site. vboxdrv module is properly loaded and I added myself to vboxusers groups (then relogged)

It seems I did everything right but when I enable AMD-V virtualbox doesn't boot. I don't even see the bios screen. When I disable it, everything works fine

And yes my CPU does support AMD-V ;)

any ideas?

thanks

EDIT: I forgot to tell you that I did "sudo rmmod kvm && sudo rmmod kvm_amd" before enabling amd-v in virtualbox.

---

### Post by Milos_SD on 2008-05-03
My system freezes when I try to start virtual machine with Intel VT enabled, but with Intel VT disabled I can start the virtual machine without problem. I have Intel Core2Duo E6550 CPU which have VT.

---

### Post by drsox1899 on 2008-05-03
> **Milos_SD said:**
> My system freezes when I try to start virtual machine with Intel VT enabled, but with Intel VT disabled I can start the virtual machine without problem. I have Intel Core2Duo E6550 CPU which have VT.

Hi.  Is it VB for Ubuntu 7.10 ?  Is this the Intel PRO/1000 NIC driver or something else ?  If it is, have you downloaded the driver from the Intel site ?

---

### Post by Milos_SD on 2008-05-03
It is VB for Ubuntu 8.04. I do not understand the part with Intel PRO/1000 NIC driver?

---

### Post by drsox1899 on 2008-05-03
> **Milos_SD said:**
> It is VB for Ubuntu 8.04. I do not understand the part with Intel PRO/1000 NIC driver?

It's not relevant for 8.04 as the driver is loaded automatically now.

---

### Post by cb951303 on 2008-05-03
> **Milos_SD said:**
> My system freezes when I try to start virtual machine with Intel VT enabled, but with Intel VT disabled I can start the virtual machine without problem. I have Intel Core2Duo E6550 CPU which have VT.

it seems like we have the same problem. does it freeze in windows or soesn't start at all?

---

### Post by Milos_SD on 2008-05-03
I don't have Widnows host. I have Ubuntu host and windows guest that I use two times in 4 weeks. I just freez and I need to reboot PC with restart button.

Here is a bug ticket: 

[http://www.virtualbox.org/ticket/1454](http://www.virtualbox.org/ticket/1454)

---

### Post by scottro on 2008-05-03
I've only installed it in Fedora 9, 32 bit and CentOS 5.1, 64 bit,  and have had the following issues.

Fedora 9 wouldn't boot the old VM that I'd created in VBox 1.5.x.  It would start to boot and give the Windows BSOD. 

Doing a fresh install of a Windows guest, wireless NAT worked, but bridged networking didn't work with wireless. I didn't test it with wired--on that laptop, if it doesn't work with wireless, it's not useful for me and I need it for work.  

In CentOS, I updated the rpm and it seemed to go smoothly. It was the first install I'd done of the new one, and I was impressed, everything seemed to work, it used my old VM without trouble.  
However, today, it didn't work with the bridged network.  In all cases, I've used the PCIII card.  I did try switching to the Intel card, but it wanted a driver--how was I going to get a driver if I couldn't connect to the Internet?  At that point, I was annoyed.  (Yes, I know the answer, I could get the driver while otherwise connected, but by this time, I was annoyed.)

I tried a few more times as it had worked the day before, and had seemed snappier than the 1.5.x version, and it worked one out 4 or 5 times. 
I thought perhaps it was that I was using the old VM image (by this time, I'd already had the BSOD with the Fedora install) so went to do a fresh Win2k install.  The install failed at the end--it would start installing network components and the VM would then reboot and start over. 


 So, I uninstalled, reinstalled the old version and everything was fine again. 

Looking on their forums, I see a few others with similar problems.  I'm not sure if it's the network card for Windows hosts or something else, but at this point, I'm irked and saying mean things about Sun under my breath.

As for Ubuntu--after all this, I booted up my Hardy Heron and went to their site to get the deb--but then, I said to myself, "Self--do you really want to go through this aggravation a *third* time?"  So, I haven't tried it on Hardy, however, judging from this thread, I probably only saved myself a bit more annoyance.  :)

At this point, I think I would recommend that people wait a bit.  I'm not sure what the deal is with the NIC on a Windows guest, it's still new and googling is giving me conflicting answers.

---

### Post by ricnar456 on 2008-05-08
i have this error when installing

root@ricnar456-desktop:~/Escritorio# dpkg -i virtualbox_1.6.0-30421_Ubuntu_hardy_i386.deb 
(Leyendo la base de datos ...  
154061 ficheros y directorios instalados actualmente.)
Desempaquetando virtualbox (de virtualbox_1.6.0-30421_Ubuntu_hardy_i386.deb) ...
dpkg: error al procesar virtualbox_1.6.0-30421_Ubuntu_hardy_i386.deb (--install):
 intentando sobreescribir `/lib/modules/2.6.24-16-generic/misc/vboxdrv.ko', que está también en el paquete virtualbox-ose-modules-2.6.24-16-generic
dpkg-deb: el subproceso paste fue terminado por la señal (Tubería rota)
Se encontraron errores al procesar:
 virtualbox_1.6.0-30421_Ubuntu_hardy_i386.deb
root@ricnar456-desktop:~/Escritorio# 

My version of kernel is different i don' undertand why he try write in old kernel files.


root@ricnar456-desktop:~/Escritorio# uname -a
Linux ricnar456-desktop 2.6.24-17-generic #1 SMP Thu May 1 14:31:33 UTC 2008 i686 GNU/Linux

thanks 
ricnar


ricnar

---

### Post by MemoryDump on 2008-05-08
is it still possible to install VB using apt-get?
I checked [http://www.virtualbox.org/debian/dists/](http://www.virtualbox.org/debian/dists/) and I don't HARDY listed :(

---

### Post by leetcharmer on 2008-05-08
Host Interface is broken in 1.6

---

### Post by OldTimeTech on 2008-05-08
I didn't have a problem with VB 1.6 and had fought and fought with 1.5.?

And the documentation was really good on what I did need help on...mho!

---

### Post by zorkerz on 2008-05-09
Im trying to install virtualbox ose 1.6. I get an error with the ubunto 8.04 dob from sun. They do not offer a .deb.

---

### Post by ricnar456 on 2008-05-09
the deb are in the page but don´t work in 2.6.24-17-generic kernel.

ricnar

---

### Post by zorkerz on 2008-05-09
[This]("http://www.virtualbox.org/wiki/Downloads") is the only official download page that i know of. It has debs for virtualbox but not for virtuabox-ose for which you must compile the source. I do not know of any debs for the 1.6 ose. 

As of last night I was able to install virtualbox (the free but closed source version) on my AMD64 2.6.24-17-generic kernel. I had to install two packages (libqt3-mt libaudio2) and remove virtualbox-ose-modules-generic.

---

### Post by Robbyx on 2008-05-11
Host: Hardy H Guest:Win2K
VB 1.6

The Guest keeps freezing. I use it with logmein and in the past found it to be very fast and stable. I would prefer to use Ub for logmein but  I have found the slow screen updates using Firefox too much to be useable.

It even freezes on a restart of VB. I have to reset it and it works for a short time and then freezes.

Any ideas to solve it?

Robin

---

### Post by scottro on 2008-05-11
Will you be mad if I say, "Yes, downgrade."?

Seriously, I think it will, in the end, keep improving--for example, 1.5.6 was much faster than 1.5.2.  However, it seems there are several problems in this release--for me the big one was that host interface networking is not reliable, even with a fix posted by someone on their forums.

One tip if you are going to downgrade.  There are some changes that were made in the xml files.  So, I found the lazy man's way to do it was to just do a mv of my win2k.vdi file out of my $HOME/.VirtualBox directory, do a rm -rf $HOME/.VirtualBox, then, after reinstalling the older version, choosing use existing and then move my win2k.vdi back into the newly created $HOME/.VirtualBox.

It's still a great program, the host networking is already pretty much fixed in subversion, and even though I have a 64 bit SMP machine, I still find that running a 32 bit single processor Windows 2k guest in VirtualBox is faster than running an SMP Windows 2k VMware or KVM guest.  (KVM doesn't seem to do that well with Windows 2K guests--it runs Linux guests beautifully, but apparently there are some sort of mouse issues with WIndows and qemu.)

Hopefully, someone will give you a better answer than mine, but at the moment, that was the course that I've chosen.

---

### Post by Robbyx on 2008-05-12
> **scottro said:**
> Will you be mad if I say, "Yes, downgrade."?

Seriously, I think it will, in the end, keep improving--for example, 1.5.6 was much faster than 1.5.2.  However, it seems there are several problems in this release--for me the big one was that host interface networking is not reliable, even with a fix posted by someone on their forums.

One tip if you are going to downgrade.  There are some changes that were made in the xml files.  So, I found the lazy man's way to do it was to just do a mv of my win2k.vdi file out of my $HOME/.VirtualBox directory, do a rm -rf $HOME/.VirtualBox, then, after reinstalling the older version, choosing use existing and then move my win2k.vdi back into the newly created $HOME/.VirtualBox.


Do you know the url for the previous version? 

I wonder if the ose 1.6 version  is any better. 

There are a number of changes showing in the source code repository, ie post 1.6. It looks very time consuming to put together!
[http://www.virtualbox.org/browser/trunk/debian](http://www.virtualbox.org/browser/trunk/debian)

Does ose now support usb2?

Robin

---

### Post by scottro on 2008-05-12
For older versions (but not OSE)
[http://www.virtualbox.org/download/](http://www.virtualbox.org/download/)

As for your OSE question, I'm afraid I don't know te answer.  I've been using the regular version.  I don't use it for USB, so I haven't been keeping up with that.  From what I see on their pages, it hasn't changed and OSE will not be supporting USB. 

As my needs for it are extremely simple (I need a Windows host for my company's VPN, but once on the company network, I go into my Linux workstation or Linux servers there), I didn't pay too much attention to any new features.  It seemed a wee bit faster, but that was a subjective impression.  For me, the big issue was host interface networking, which is what caused me to go back.

---

