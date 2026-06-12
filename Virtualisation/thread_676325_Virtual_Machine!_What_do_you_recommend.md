---
title: "Virtual Machine! What do you recommend?"
date: 2008-01-23
forum: Virtualisation
---

### Post by ryanlhjess on 2008-01-23
Im looking for a PC emulator solution like virtual pc,  for linux.

What do you recommend?

---

### Post by solarwind on 2008-01-23
1. VMWare for Linux (search on torrent sites, or download free trial and put a serial in there ;))
2. Bochs (bochs.sourceforge.net/)

---

### Post by DFlame on 2008-01-23
I'm a QEMU user myself

[http://fabrice.bellard.free.fr/qemu/about.html](http://fabrice.bellard.free.fr/qemu/about.html)

---

### Post by DillyP on 2008-01-23
VirtualBox is another one to look at.

[http://virtualbox.org]("http://virtualbox.org")

---

### Post by linuxvacuum on 2008-01-23
There is no competition here, [**VirtualBox**]("http://www.virtualbox.org/") clearly stands out :redface: . It is so easy to use and very fast.

---

### Post by bodhi.zazen on 2008-01-23
There are many options, what features do you want?

See the sticky at the top of this section for some ideas ...

---

### Post by ryanlhjess on 2008-01-23
well i decided to go with virtual box

i installed it using synaptic, 

I've did some basic setup but when i try to turn on the virtual pc i get the following error. 



any suggestions

```
The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).
```

---

### Post by bodhi.zazen on 2008-01-23
> **ryanlhjess said:**
> well i decided to go with virtual box

i installed it using synaptic, 

I've did some basic setup but when i try to turn on the virtual pc i get the following error. 



any suggestions

```
The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).
```

You need to add your user to the vboxusers group, log out, and log back in .

---

### Post by DillyP on 2008-01-23
I think you need the virtualbox-ose-source package installed too, also available through synaptic.

---

### Post by ryanlhjess on 2008-01-23
will try

---

### Post by ryanlhjess on 2008-01-23
Nope....no wooorky

---

### Post by p_quarles on 2008-01-23
What exactly did you try? Anyway, using the graphical user management app, you can follow bodhi.zazen's instructions (including the logging out part).

If you aren't sure how to use that, you can run the command line equivalent:
```
sudo useradd *yourname* vboxusers
```
Log out, log back in.

---

### Post by ryanlhjess on 2008-01-23
Adding myself to the vboxusers group did work...

thank you very much for the help


I need to be able to access the internet on the virtual box...is this possible....?
If not what virtual machines can?

---

### Post by solarwind on 2008-01-23
> **ryanlhjess said:**
> Adding myself to the vboxusers group did work...

thank you very much for the help


I need to be able to access the internet on the virtual box...is this possible....?
If not what virtual machines can?

I don't know if the one your using is able to (it should be able to), but if you want to reconsider, VMWare is really good and you can use the internet through it for sure, I have used it before.

---

### Post by ryanlhjess on 2008-01-23
Well that was super simple

It's quite impressive really, 


I was wondering though,   why is it that at times my arrow just freezes? 

Is there a way for me to fix this annoyance?  cause if there is...it would be the perfect virtual box\

---

### Post by bodhi.zazen on 2008-01-23
> **ryanlhjess said:**
> Adding myself to the vboxusers group did work...

thank you very much for the help


I need to be able to access the internet on the virtual box...is this possible....?
If not what virtual machines can?

Yes, you can access the internet with VBox.

[http://www.montanalinux.org/node/561](http://www.montanalinux.org/node/561)

[http://samiux.wordpress.com/2007/07/11/bridge-network-interface-on-virtualbox/](http://samiux.wordpress.com/2007/07/11/bridge-network-interface-on-virtualbox/)

---

### Post by ryanlhjess on 2008-01-23
i got the internet working...actually it worked without any config

now i just have to stop my pointer from stalling out

---

### Post by theZoid on 2008-01-23
> **ryanlhjess said:**
> will try

Ryan, good choice IMO on VirtualBox....go here to get your usb devices working....excellent 'how-to'

[http://www.arsgeek.com/?p=2776](http://www.arsgeek.com/?p=2776)

Let us know.

---

### Post by NullHead on 2008-01-23
I like QEMU best along with qemu-launcher, but thats just me. :)

---

### Post by SyCo123 on 2008-01-24
For anyone reading this who would like to know the GUI way to add yourself to the virtual box group, you can do this.

System>Administration>Users and Groups
Click Manage Groups
Click the virtual box users group
Click properties
Check (tick) your username
OK out

Phew, thank goodness for the command line!

---

### Post by ryanlhjess on 2008-01-24
everything seems to be working great. My keyboard and mouse were properly installed, along with some other devices.  However, it seems that the UI quite frequently stalls out on my mouse,  meaning that, the arrow on the screen will just stop moving, but the keyboard will still work. 

Thanks for all the help thus far, I have been over on ubuntu for the last six months, and it as treated me very well...the community online has been soooo helpful in the transition.   All of you are to commended for your great helpful spirit...i can't wait until i can be helpful to the n00bies that are going to be coming over when ubuntu releases 8.10.   

Virtual Box is treating me very well, and im going to be testing out all sort of linux distributions, with it,  although i expect none of them to live up to the high standard of user friendliness that ubuntu has given me.

---

### Post by theRightNee on 2008-01-24
if you are still willing to try, i'm a avid supporter of VMWare (simply because it allows free 3D acceleration-though its only limited to XP guests) =]

---

### Post by theZoid on 2008-01-24
> **theRightNee said:**
> if you are still willing to try, i'm a avid supporter of VMWare (simply because it allows free 3D acceleration-though its only limited to XP guests) =]

Does the free Vmware Server do this (3d acceleration)?  Can I share files with my linux partition?  Can I use my usb devices?  Or is it the workstation?  thanks!

---

### Post by allad on 2008-01-25
> **theZoid said:**
> Does the free Vmware Server do this (3d acceleration)?  Can I share files with my linux partition?  Can I use my usb devices?  Or is it the workstation?  thanks!

No It doesn't. You need the commercial version : VmWare Workstation in order to do that. USB support, 3D hardware acceleration and other goodies are only available in the commercial VmWare Workstation. And also, from trying both solutions, I can tell u that VmWare Workstation has better (much metter actually) overall performance and speed. It runs like 2 or 3 times faster than  VmWare Server. 
Good luck :)

---

### Post by theRightNee on 2008-01-25
VMWare Player also supports 3D acceleration

---

### Post by Comhra on 2008-01-25
Thanks to this thread, I have come to realise why previous attempts to run Vbox in Ubuntu didn't work; I was missing the virtualbox-ose-source package.  

VB is working really well now and I'm delighted because I can experiment further with various distros and maybe even contemplate re-installing XP and running it on the virtual machine.

I do however have a query.  It relates to those occasions when I use the entire screen for VB and when my panals,both of them are not visible.  Pressing the right-hand Ctrl frees the curser but afterwards, I am unable to return to my Ubuntu desktop.

Thanks to the versitility of Linux, I can get out of this situation by REISUB but I realise that this contingency should not be used in such circumstances; however, it's infinately preferable to an hard shutdown.

How do I make a smooth exit from VB in situations like that.  What keys do I press?

I'm still quite new to Linux (4 months now and loving it) and I have been very patient with myself because I know there is an answer and it's just that I haven't found it yet.

 
It's ok guys, I got it.

---

### Post by theZoid on 2008-01-25
> **allad said:**
> No It doesn't. You need the commercial version : VmWare Workstation in order to do that. USB support, 3D hardware acceleration and other goodies are only available in the commercial VmWare Workstation. And also, from trying both solutions, I can tell u that VmWare Workstation has better (much metter actually) overall performance and speed. It runs like 2 or 3 times faster than  VmWare Server. 
Good luck :)

thanks....just wanted to make sure I wasn't missing something.

---

### Post by BLTicklemonster on 2008-07-27
> **SyCo123 said:**
> For anyone reading this who would like to know the GUI way to add yourself to the virtual box group, you can do this.

System>Administration>Users and Groups
Click Manage Groups
Click the virtual box users group
Click properties
Check (tick) your username
OK out

Phew, thank goodness for the command line!

Thank you.

---

### Post by Tanker Bob on 2008-07-27
I've been using VMWare Workstation for over a year and really like it. I've built a number of disposable virutal systems for various reasons, and the process is quick and simple. Performance for Linux guests is especially good because they use the host's virtualization capability in the newer kernels. Customization and isolation/interoperability are also excellent, and version 6.x supports USB 2 very well. It isn't free, but it's worth the price if you will be building a number of VMs, especially with different guest OSs.

---

### Post by bodhi.zazen on 2008-07-28
> **Tanker Bob said:**
> I've been using VMWare Workstation for over a year and really like it. I've built a number of disposable virutal systems for various reasons, and the process is quick and simple. Performance for Linux guests is especially good because they use the host's virtualization capability in the newer kernels. Customization and isolation/interoperability are also excellent, and version 6.x supports USB 2 very well. It isn't free, but it's worth the price if you will be building a number of VMs, especially with different guest OSs.

VMWare Server is freely available and has many of the same features.

---

### Post by project4 on 2008-08-06
excellent thread! I followed the steps and all... and I've got XP working under the VM... not that I am a windows fan...just because a colleague gave me a xp crack + shared his enthusiasm for VMs....

One problem though... I cannot get the RIGHT CRTL working.. so need everytime to turn of the virtual machine to be able to get back in Ubuntu (the host machine)

If any tips on that. Thanks!

---

### Post by project4 on 2008-08-06
> **project4 said:**
> excellent thread! I followed the steps and all... and I've got XP working under the VM... not that I am a windows fan...just because a colleague gave me a xp crack + shared his enthusiasm for VMs....

One problem though... I cannot get the RIGHT CRTL working.. so need everytime to turn of the virtual machine to be able to get back in Ubuntu (the host machine)

If any tips on that. Thanks!


Sorry to quote myself... I was pressing right arrow + crtl
It is instead the crtl button on the right side of the keyboard

---

### Post by philetus on 2008-08-06
I installed Virtual Box in Gutsy last night.

When I select full screen, I get full screen, but the windows OS is not full screen.
Is there any way to fix this?

---

