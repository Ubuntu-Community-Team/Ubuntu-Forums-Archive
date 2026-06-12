---
title: "Server installation hangs in detecting network hardware"
date: 2009-11-14
forum: Server Platforms
---

### Post by clavetika on 2009-11-14
Hi all,
    When installing Ubuntu Server on a Dell Poweredge 2600, the process always freezes during network hardware detection, on the "Starting PC card services" step. At this point, the keyboard lights begin to blink (maybe indicative of kernel panic? not sure...), and the system becomes nonresponsive.

Has anyone else had this problem? The disc used to perform the installation passed an integrity check, so I'm pretty sure it's not the culprit... any suggestions would be greatly appreciated.

---

### Post by dalesomers on 2009-12-17
I am having the same issue

I have tried to install the Regular Ubuntu 9.10 and Server Edition.

Both to no avail.

Any help would be Greatly appreciated.

---

### Post by chipper_farley on 2009-12-17
Does the server have a RAID?  If so...

I've had issues with Dell RAID controllers being poorly supported by linux and my installs dying as a result.  Many of the controllers Dell includes are not hardware controllers, they are dependent on Windows to run.  Without Windows, you sometimes don't have the ability to use them easily.  I've also seen where some older controllers have a major driver change and the old driver is replaced in the linux kernel in lieu of the new one, which won't run the old controller. 

Either way, it's possible that this is your issue.  There are two things you could try.  One is to get an older version of linux and see if you can get it to work.  I actually had to install Fedora Core 1 on an older Dell server recently because of this controller driver issue (it's all I had).  Another is to pick up a hardware RAID controller if you think that this might be the issue...not sure since the install seems to die during network hardware detection.  I've never seen the networking hardware be an issue so that's kind of weird.

Hope this helps.

---

### Post by Chromag on 2010-04-07
> **chipper_farley said:**
> Does the server have a RAID?  If so...

I'm also having this exact same problem.  We have a couple Dell 2600 servers that are currently running CentOS4 and have been for years.  It's time to wipe them and reinstall a newer OS and I wanted to give Ubuntu Server a try instead of going with CentOS5.

The server does have a RAID controller but CentOS4 is installed on it and runs just fine and has worked for a long time.

I'm trying out Ubuntu Server on one of the boxes to evaluate the performance compared to our CentOS4 boxes, but not being able to install is kinda throwing a monkey wrench into the evaluation process :p

Anyone have any idea how we can fix this problem?

Thanks.

---

### Post by Chromag on 2010-04-08
[SIZE=4][SOLVED!][/SIZE]

[SIZE=2]It turns out that specifying the following boot options fixed the problem and the install is moving along quite well now.  In case someone like me finds this thread here was the solution.

To get to boot options press F6 to see "Other Options" from the first install menu on the installation CD.  Add the following to the boot parameters:

```
noapic nolapic acpi=off pci=noacpi irqpoll pnpbios=off
```Hope this helps![/SIZE]

---

### Post by wbrb on 2010-09-06
THANK YOU CHROMAG

I've spent the last 2 days trying to get this working. I have 3 IBM xSeries 225 s that have been decommissioned and I couldn't figure out why the heck the installers kept freezing trying to drop lucid server on them.

At first I thought it was because of the multiple ultra320 controllers and the modules but playing with an alt CD and lspci proved me wrong, all the modules were loaded correctly and everything should have been working.

This did it. :D

---

### Post by Rich Valenta on 2011-12-12
I was having a problem where my Ubuntu Server 9.04 (and 10.10) was hanging when I tried to install it on a new machine.  I'd hit enter on "Install Ubuntu" and the DVDROM would quit reading, and the cursor would simply flash on the screen.  
 
This solution also fixed my problem.  Thank you!

---

