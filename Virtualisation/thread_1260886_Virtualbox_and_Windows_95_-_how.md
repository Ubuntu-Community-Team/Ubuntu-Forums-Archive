---
title: "Virtualbox and Windows 95 - how?"
date: 2009-09-08
forum: Virtualisation
---

### Post by Thanh-BKK on 2009-09-08
Hi.

I am not sure if this is the right place to ask, but i'll give it a try. 

I used to have Ubuntu Hardy and VMware Server and several virtual machines, namely Windows 3.11, Windows 95, Windows XP and Haiku.

Then my hard disk went up in smoke, i replaced it, installed Ubuntu Jaunty and could not get that (old) version of VMware Server installed, so i got me the new version with the web interface.

It sucks so bad that i changed to VirtualBox.

Now after some trickery back-and-forth i managed to get the existing (VMware) VM's of XP, 3.11 and Haiku to work in VirtualBox, however Windows 95 does not like me. 

Now it does not matter if i try "as is" or with VMware Tools removed first - booting it in VirtualBox stalls right after the splash screen appears, it freezes there. I managed to boot it in Safe Mode but there i don't have the CD drive to install the VirtualBox Guest Additions, so i can't get the driver problem sorted - it appears to be the IDE driver.

So i created a NEW vitual machine in VirtualBox and re-installed Windows 95 - DOS first, CD driver next, then Win 95.... and that, too, freezes right after the splash screen appears.

So here my question - is it possible at all to install and run Windows 95 in VirtualBox (Windows 95b by the way) and if so, how do i get it done? Preferably starting with a fully installed and working VMware image (which still works just fine in VMware Server, however see above - that one sucks). 

I highly appreciate any advice on this matter. Many thanks in advance.

Kind regards.....

Thanh

---

### Post by dk06 on 2009-09-08
> **Thanh-BKK said:**
> Hi.

I am not sure if this is the right place to ask, but i'll give it a try. 

I used to have Ubuntu Hardy and VMware Server and several virtual machines, namely Windows 3.11, Windows 95, Windows XP and Haiku.

Then my hard disk went up in smoke, i replaced it, installed Ubuntu Jaunty and could not get that (old) version of VMware Server installed, so i got me the new version with the web interface.

It sucks so bad that i changed to VirtualBox.

Now after some trickery back-and-forth i managed to get the existing (VMware) VM's of XP, 3.11 and Haiku to work in VirtualBox, however Windows 95 does not like me. 

Now it does not matter if i try "as is" or with VMware Tools removed first - booting it in VirtualBox stalls right after the splash screen appears, it freezes there. I managed to boot it in Safe Mode but there i don't have the CD drive to install the VirtualBox Guest Additions, so i can't get the driver problem sorted - it appears to be the IDE driver.

So i created a NEW vitual machine in VirtualBox and re-installed Windows 95 - DOS first, CD driver next, then Win 95.... and that, too, freezes right after the splash screen appears.

So here my question - is it possible at all to install and run Windows 95 in VirtualBox (Windows 95b by the way) and if so, how do i get it done? Preferably starting with a fully installed and working VMware image (which still works just fine in VMware Server, however see above - that one sucks). 

I highly appreciate any advice on this matter. Many thanks in advance.

Kind regards.....

Thanh

  		 			 			**[Tutorial: Windows 95/98 guest OSes]("http://forums.virtualbox.org/viewtopic.php?t=9072#p34587")**

 [http://forums.virtualbox.org/viewtopic.php?t=9072](http://forums.virtualbox.org/viewtopic.php?t=9072)

---

### Post by Thanh-BKK on 2009-09-08
Hi.

Thank you, but i have been there.... "For this tutorial, I presume, that you are able to install the OS. "

Mine will not boot for the first time right after install due to a problem with the IDE controller driver. When i remove that driver through Safe mode, reboot, Windows will install that very same driver again automatically and immediately BSOD. I already tried all three or four options for IDE controllers that VirtualBox offers.

I have not yet gotten to sound, VGA and network - first i need to get the guest OS itself working, that is what i am currently failing at. 

Best regards.....

Thanh

---

