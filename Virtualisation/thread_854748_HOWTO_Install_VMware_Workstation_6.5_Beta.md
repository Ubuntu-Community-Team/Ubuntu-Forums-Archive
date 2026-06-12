---
title: "HOWTO: Install VMware Workstation 6.5 Beta"
date: 2008-07-09
forum: Virtualisation
---

### Post by CRCarl on 2008-07-09
This HOWTO was tested on - 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux

**INSTALL**

Download the Beta from [http://www.vmware.com/communities/content/beta/ws65/welcome.html]("http://www.vmware.com/communities/content/beta/ws65/welcome.html") in .bundle form.

Change to the directory you downloaded to - 

```
# sudo sh VMware-Workstation-e.x.p-<build>.<arch>.bundle
```

Step thru the GUI installer. When it completes - 

```
 # vmware 
```

That's it! In GNOME the VMWare launcher is in Application -> System Tools.

The drag and drop host <--> guest file transfer is almost the best thing ever! (You will need to update the VMware tools in your guest OS.)

**DISABLE DEBUG**
By default the Beta runs in debug mode, really, really slow. If you want to disable debug mode -

```
# sudo /etc/init.d/vmware stop
# sudo mv /usr/lib/vmware/bin/vmware-vmx-debug /usr/lib/vmware/bin/vmware-vmx-debug.orig
# sudo cp /usr/lib/vmware/bin/vmware-vmx /usr/lib/vmware/bin/vmware-vmx-debug
# sudo chmod ug+s /usr/lib/vmware/bin/vmware-vmx-debug
# sudo /etc/init.d/vmware start
```

Please let me know if I need to update this for 64-bit OS'es.

---

### Post by rainwalker on 2008-07-09
And this is stable? Won't break anything? Won't conflict with updates?

My dad is still on Dapper simply because of the lack of VMWare for Hardy...

---

### Post by CRCarl on 2008-07-10
There is a list of known bugs here - 

[http://www.vmware.com/products/beta/ws/releasenotes_ws65_beta.html#issues]("http://www.vmware.com/products/beta/ws/releasenotes_ws65_beta.html#issues")

I have not had any issues.

---

### Post by rainwalker on 2008-07-10
Hm...well you said this is beta; when will it be official?

---

### Post by CRCarl on 2008-07-10
I'm not sure. On the up side it is free...

---

### Post by StormPCs on 2008-07-11
Yes please modify the instructions for 64 bit if it's not too much trouble.  Thanks.

---

### Post by the guitarist on 2008-09-14
hello there ... just wanted to ask is the new " unity " feature available in this version?

thanx

---

### Post by binbash on 2008-09-14
thanks for disable debug hint

---

### Post by Tanker Bob on 2008-09-15
> **rainwalker said:**
> And this is stable? Won't break anything? Won't conflict with updates?

My dad is still on Dapper simply because of the lack of VMWare for Hardy...
VMWare Workstation 6.04 and 6.05 both work fine on 32-bit Hardy. No reason to hold back.

---

### Post by p_quarles on 2008-09-15
Moved to Virtualization.

---

### Post by CRCarl on 2008-09-18
Unity is included. So is record and replay. Very cool.

C

---

### Post by HDave on 2008-09-25
Wow...rarely is anything every this easy.  Followed the instructions...and POW -- just worked.

EDIT:  By the way...Unity view TOTALLY ROCKS.

---

### Post by darco on 2008-09-25
Does anyone know how to upgrade VMWare Tools? I see a message that says the tool is out of date. Under Settings/Options it has an option to upgrade the tool automatically but it does not seem to do anything.
Any help would be appreciated....
thxs
darco

---

### Post by Tanker Bob on 2008-09-25
If you just upgraded to VMware Workstation 6.5, just use VM/Install VMWare Tools... That will install the new set. If you didn't just upgrade, then try Help/Check for Updates. I have Workstation set up to check for updates weekly, and that seems to have worked in the past.

---

### Post by HDave on 2008-09-26
Click right on the VMWare tools tray icon within Windows XP, and open VMWare tools.  On the first tab called "Options" you will find a button labeled "upgrade".  

It took about 1 minute to respond once I hit the button so be patient.

---

### Post by darco on 2008-09-26
> **HDave said:**
> Click right on the VMWare tools tray icon within Windows XP, and open VMWare tools.  On the first tab called "Options" you will find a button labeled "upgrade".  

It took about 1 minute to respond once I hit the button so be patient.

well, the funny thing is, XP doesnt report the tool is out of date, only my linux boxes report that. I did try your suggestion tho in XP but the upgrade button was grayed out.....
 What I really thing the problem is, I had VMWare Server before and when I up/down graded to 6.5 Beta I brought over the vm machines and added XP after, so thats probably why my Linux boxes cant be upgraded but XP can....

Did 6.5 go gold yet or is it still in Beta?

thxs

darco

---

### Post by HDave on 2008-09-26
> **darco said:**
> Did 6.5 go gold yet or is it still in Beta?

It's officially [available.]("http://www.vmware.com/products/ws/buy.html")

---

### Post by akram.bazina on 2009-10-19
I couldn't install it.. could someone help me with that .

<<
bazina@bazina-laptop:~/Desktop$ sudo sh VMware-Workstation-6.5.3-185404.i386
[sudo] password for bazina: 
magic number does not match
bazina@bazina-laptop:~/Desktop$ sudo sh VMware-Workstation-6.5.3-185404.i386.bundle
magic number does not match
>>

---

### Post by corsakh on 2009-10-19
I am totally clueless, how do you connect to this thing with a VNC client when it runs in background?

---

