---
title: "Ubuntu 10.04 Guest Under Hyper-V (2K8 R2):  Ethernet?"
date: 2010-06-30
forum: Virtualisation
---

### Post by Particle on 2010-06-30
I'm hoping someone has experience with this combination.  Surely someone has tried to run Ubuntu 10.04 as a guest OS under Server 2008 R2 using Hyper-V.  I've tried using both synthetic Ethernet adapters and legacy (Tulip) Ethernet adapter devices for an Ubuntu 10.04 guest.  I've also tried both the 32-bit and 64-bit builds of Ubuntu.

For the life of me I just cannot seem to get it to play along.  When I use a legacy adapter the device shows up but doesn't seem to function.  I give it an IP address and then try to ping other machines it should be able to talk to but receive destination network unavailable errors and lots of TX packet errors.  When I use a synthetic adapter it doesn't show up at all.

I'd really love to start using Ubuntu as a server platform for some of my services such as SRCDS.

---

### Post by Particle on 2010-07-05
So I guess nobody has ever tried to run Ubuntu as a virtual machine then?  Unlikely.

---

### Post by juancarlospaco on 2010-07-05
*Hyper-V ?   YAY!*

---

### Post by Particle on 2010-07-06
> **juancarlospaco said:**
> *Hyper-V ?   YAY!*

Very helpful, thanks.

---

### Post by Particle on 2010-07-06
Looks like this is only broken under 10.04.  I just installed a 9.10 guest and it works fine.

---

### Post by addiakogiannis on 2010-07-07
> **Particle said:**
> Looks like this is only broken under 10.04.  I just installed a 9.10 guest and it works fine.
Thnaks mate, just posted similar question and I will try your solution, are you using hyper-v r2???

---

### Post by juancarlospaco on 2010-07-07
> **Particle said:**
> Very helpful, thanks.

You are welcome.

---

### Post by Particle on 2010-07-07
> **addiakogiannis said:**
> Thnaks mate, just posted similar question and I will try your solution, are you using hyper-v r2???

Yes, this is with Server 2008 R2 (Hyper-V R2).  Make sure to use a legacy adapter--if you do it should work just fine with 9.10.

> **juancarlospaco said:**
> You are welcome.

Smart-***.

---

### Post by stephanhughson on 2010-07-21
I just installed Ubuntu Server 10.04 under Hyper-V Server and it worked fine, I had to use the legacy network adapter though.

Networking is working properly.

I also understand that you can install "Synthetic Devices" - [http://blog.allanglesit.com/Blog/tabid/66/EntryId/53/Hyper-V-Guests-Ubuntu-10-04-Alpha-3-Synthetic-Devices.aspx](http://blog.allanglesit.com/Blog/tabid/66/EntryId/53/Hyper-V-Guests-Ubuntu-10-04-Alpha-3-Synthetic-Devices.aspx) but haven't tried.

---

### Post by Victor Miasnikov on 2011-02-24
> **stephanhughson said:**
> you can install "Synthetic Devices" - 
-h-t-t-p://blog.allanglesit.com/Blog/tabid/66/EntryId/53/Hyper-V-Guests-Ubuntu-10-04-Alpha-3-Synthetic-Devices.aspx

 
-h-t-t-p://blog.allanglesit.com/Blog/tabid/66/EntryId/53/Hyper-V-Guests-Ubuntu-10-04-Alpha-3-Synthetic-Devices.aspx
 
[FONT=Times New Roman]Error 404 - Not Found[/FONT]
 
> **stephanhughson said:**
> I just installed Ubuntu Server 10.04 under Hyper-V Server and it worked fine, I had to use the legacy network adapter though.

 
[http://blogs.msdn.com/b/virtual_pc_guy/archive/2010/10/21/installing-ubuntu-server-10-10-on-hyper-v.aspx](http://blogs.msdn.com/b/virtual_pc_guy/archive/2010/10/21/installing-ubuntu-server-10-10-on-hyper-v.aspx)
 
On Russian language:
[http://blogs.technet.com/b/abeshkov/archive/2011/01/30/3383495.aspx](http://blogs.technet.com/b/abeshkov/archive/2011/01/30/3383495.aspx)
 
Translated by Google:
[http://translate.google.by/translate?hl=ru&ie=UTF-8&sl=auto&tl=en&u=http://blogs.technet.com/b/abeshkov/archive/2011/01/30/3383495.aspx&prev=_t](http://translate.google.by/translate?hl=ru&ie=UTF-8&sl=auto&tl=en&u=http://blogs.technet.com/b/abeshkov/archive/2011/01/30/3383495.aspx&prev=_t)
==
 
[Andrey Beshkov]("http://blogs.technet.com/abeshkov/ProfileUrlRedirect.ashx") 
29 Jan 2011 1:07 PM
. . .
 
This is not enough, so edit the file /etc/initramfs-tools/modules 
and add the line allow us to load the rest of the required modules:
hv_vmbus 
hv_storvsc 
hv_blkvsc 
hv_netvsc 
hv_utils 
 
Save the file and run the command: 
$ Sudo update-initramfs-u 
Put this in /etc/network/interfaces your new synthetic network interface seth0. 
If you have used an outdated network interface Legacy, it would be called eth0. 
For a static address: 
Auto seth0 
iface seth0 inet static 
address xxxx 
netmask xxxx 
Gateway xxxx 
To get the address for DHCP: 
Auto seth0 
iface seth0 inet dhcp 
I tested both methods of network addressing, they work. 
Reboot and see now in the process of such reports that the device associated with vmbus found. 
 
 
. . .
It is also worth noting that Ubuntu works fine in both uniprocessor and multiprocessor configurations.
==
 
 
And about mouse:
 
[http://ubuntuforums.org/showthread.php?p=10489887#post10489887](http://ubuntuforums.org/showthread.php?p=10489887#post10489887)
==
 
> **matthew.mattoon said:**
> 
[COLOR=black][FONT=Verdana]Now it sounds to me like the mouse is not working for you at all? If that is the case it is probably due to you using RDP from your workstation to another . . . server, then from their using SCVMM or Hyper-V Manager to connect to the VM. This will NOT work for mouse. If you use your workstation to connect to the VM directly via SCVMM or Hyper-V Manager it will work just fine. It is simply the problem with the RDP connection losing control of the mouse (this happens on Windows guests with no ICs as well).[/FONT][/COLOR]
 
Mini How-To about _practically_ method for worked mouse in Linux guest:
 
Linux on Hyper-V How-To FIX &#8220;Mouse not captured in Remote Desktop session&#8221;
[http://vvm.blog.tut.by/2011/02/22/hyper-v_mouse_in_linux/](http://vvm.blog.tut.by/2011/02/22/hyper-v_mouse_in_linux/) ( -h-t-t-p://vvm.blog.tut.by/2011/02/22/hyper-v_mouse_in_linux/)
==
. . .
Without Satori, mouse work in Linux Guest if connect to it from Windows _directly_
. . .
==
==

---

### Post by stephanhughson on 2011-02-26
Thanks for posting this.

I'm not using Hyper-V anymore, I was just testing it out for work (we decided not to go for it), but it's great to have this here for reference anyway just in case.

Thanks for taking the time.

---

### Post by mruiz@ic-sa.com on 2012-03-12
> **Victor Miasnikov said:**
> -h-t-t-p://blog.allanglesit.com/Blog/tabid/66/EntryId/53/Hyper-V-Guests-Ubuntu-10-04-Alpha-3-Synthetic-Devices.aspx
 
[FONT=Times New Roman]Error 404 - Not Found[/FONT]
 

 
[http://blogs.msdn.com/b/virtual_pc_guy/archive/2010/10/21/installing-ubuntu-server-10-10-on-hyper-v.aspx](http://blogs.msdn.com/b/virtual_pc_guy/archive/2010/10/21/installing-ubuntu-server-10-10-on-hyper-v.aspx)
 
On Russian language:
[http://blogs.technet.com/b/abeshkov/archive/2011/01/30/3383495.aspx](http://blogs.technet.com/b/abeshkov/archive/2011/01/30/3383495.aspx)
 
Translated by Google:
[http://translate.google.by/translate?hl=ru&ie=UTF-8&sl=auto&tl=en&u=http://blogs.technet.com/b/abeshkov/archive/2011/01/30/3383495.aspx&prev=_t](http://translate.google.by/translate?hl=ru&ie=UTF-8&sl=auto&tl=en&u=http://blogs.technet.com/b/abeshkov/archive/2011/01/30/3383495.aspx&prev=_t)
==
 
[Andrey Beshkov]("http://blogs.technet.com/abeshkov/ProfileUrlRedirect.ashx") 
29 Jan 2011 1:07 PM
. . .
 
This is not enough, so edit the file /etc/initramfs-tools/modules 
and add the line allow us to load the rest of the required modules:
hv_vmbus 
hv_storvsc 
hv_blkvsc 
hv_netvsc 
hv_utils 
 
Save the file and run the command: 
$ Sudo update-initramfs-u 
Put this in /etc/network/interfaces your new synthetic network interface seth0. 
If you have used an outdated network interface Legacy, it would be called eth0. 
For a static address: 
Auto seth0 
iface seth0 inet static 
address xxxx 
netmask xxxx 
Gateway xxxx 
To get the address for DHCP: 
Auto seth0 
iface seth0 inet dhcp 
I tested both methods of network addressing, they work. 
Reboot and see now in the process of such reports that the device associated with vmbus found. 
 
 
. . .
It is also worth noting that Ubuntu works fine in both uniprocessor and multiprocessor configurations.
==
 
 
And about mouse:
 
[http://ubuntuforums.org/showthread.php?p=10489887#post10489887](http://ubuntuforums.org/showthread.php?p=10489887#post10489887)
==
 

 
Mini How-To about _practically_ method for worked mouse in Linux guest:
 
Linux on Hyper-V How-To FIX “Mouse not captured in Remote Desktop session”
[http://vvm.blog.tut.by/2011/02/22/hyper-v_mouse_in_linux/](http://vvm.blog.tut.by/2011/02/22/hyper-v_mouse_in_linux/) ( -h-t-t-p://vvm.blog.tut.by/2011/02/22/hyper-v_mouse_in_linux/)
==
. . .
Without Satori, mouse work in Linux Guest if connect to it from Windows _directly_
. . .
==
==

I am going to try this.  I was using this thread as a basis. I would prefer to use VMware, however, the company does not want to use it. :( I have no choice but to use Hyper-V. 

[http://social.technet.microsoft.com/wiki/contents/articles/961.aspx](http://social.technet.microsoft.com/wiki/contents/articles/961.aspx)

---

### Post by mruiz@ic-sa.com on 2012-03-12
> **Victor Miasnikov said:**
> -h-t-t-p://blog.allanglesit.com/Blog/tabid/66/EntryId/53/Hyper-V-Guests-Ubuntu-10-04-Alpha-3-Synthetic-Devices.aspx
 
[FONT=Times New Roman]Error 404 - Not Found[/FONT]
 

 
[http://blogs.msdn.com/b/virtual_pc_guy/archive/2010/10/21/installing-ubuntu-server-10-10-on-hyper-v.aspx](http://blogs.msdn.com/b/virtual_pc_guy/archive/2010/10/21/installing-ubuntu-server-10-10-on-hyper-v.aspx)
 
On Russian language:
[http://blogs.technet.com/b/abeshkov/archive/2011/01/30/3383495.aspx](http://blogs.technet.com/b/abeshkov/archive/2011/01/30/3383495.aspx)
 
Translated by Google:
[http://translate.google.by/translate?hl=ru&ie=UTF-8&sl=auto&tl=en&u=http://blogs.technet.com/b/abeshkov/archive/2011/01/30/3383495.aspx&prev=_t](http://translate.google.by/translate?hl=ru&ie=UTF-8&sl=auto&tl=en&u=http://blogs.technet.com/b/abeshkov/archive/2011/01/30/3383495.aspx&prev=_t)
==
 
[Andrey Beshkov]("http://blogs.technet.com/abeshkov/ProfileUrlRedirect.ashx") 
29 Jan 2011 1:07 PM
. . .
 
This is not enough, so edit the file /etc/initramfs-tools/modules 
and add the line allow us to load the rest of the required modules:
hv_vmbus 
hv_storvsc 
hv_blkvsc 
hv_netvsc 
hv_utils 
 
Save the file and run the command: 
$ Sudo update-initramfs-u 
Put this in /etc/network/interfaces your new synthetic network interface seth0. 
If you have used an outdated network interface Legacy, it would be called eth0. 
For a static address: 
Auto seth0 
iface seth0 inet static 
address xxxx 
netmask xxxx 
Gateway xxxx 
To get the address for DHCP: 
Auto seth0 
iface seth0 inet dhcp 
I tested both methods of network addressing, they work. 
Reboot and see now in the process of such reports that the device associated with vmbus found. 
 
 
. . .
It is also worth noting that Ubuntu works fine in both uniprocessor and multiprocessor configurations.
==
 
 
And about mouse:
 
[http://ubuntuforums.org/showthread.php?p=10489887#post10489887](http://ubuntuforums.org/showthread.php?p=10489887#post10489887)
==
 

 
Mini How-To about _practically_ method for worked mouse in Linux guest:
 
Linux on Hyper-V How-To FIX “Mouse not captured in Remote Desktop session”
[http://vvm.blog.tut.by/2011/02/22/hyper-v_mouse_in_linux/](http://vvm.blog.tut.by/2011/02/22/hyper-v_mouse_in_linux/) ( -h-t-t-p://vvm.blog.tut.by/2011/02/22/hyper-v_mouse_in_linux/)
==
. . .
Without Satori, mouse work in Linux Guest if connect to it from Windows _directly_
. . .
==
==

I found the problem.  

seth0 apparently no longer works.  I did not know that. LOL.

you can just put eth0 and now it works fine.  I hope that helps someone out there.

---

### Post by Victor Miasnikov on 2012-03-13
Are You use Ubuntu 10.04? Or 11.04? Or?
> company does want to use Hyper-V
 And this is _right_ solution {= better TCO> seth0 apparently no longer works.
 Yes, but this is old news:[http://social.technet.microsoft.com/wiki/contents/articles/961.aspx](http://social.technet.microsoft.com/wiki/contents/articles/961.aspx)
[QUOTE=Code Chief]==
 10 Aug 2011 12:26 PM
If you install all the way with one default (synthetic) network adapter the device name is eth0 not seth0 .
==
[/QUOTE]> I did not know that.
Progress
 Read ( in creation time order):
[http://vvm.blog.tut.by/category/linux/](http://vvm.blog.tut.by/category/linux/)
[http://www.simweb.ch/blog/2011/12/experimental-hyper-v-branch/](http://www.simweb.ch/blog/2011/12/experimental-hyper-v-branch/)
[http://www.simweb.ch/blog/2011/10/state-of-linux-on-hyper-v/](http://www.simweb.ch/blog/2011/10/state-of-linux-on-hyper-v/)
[QUOTE=VVM]Are You use Ubuntu 10.04? Or 11.04? Or?[/QUOTE]
 This work fine ( SCSI , Syntetic LANCard, mouse in LiveCD and after install) on Hyper-V:
Ubuntu 12.04 LTS (Precise Pangolin) Daily Build
>  precise-desktop-amd64.iso           13-Mar-2012 07:55  700M  Desktop CD for 64-bit PC (AMD64) computers (standard download)
  ==
[http://cdimage.ubuntu.com/daily-live/20120313/precise-desktop-amd64.iso](http://cdimage.ubuntu.com/daily-live/20120313/precise-desktop-amd64.iso)
  ==

---

