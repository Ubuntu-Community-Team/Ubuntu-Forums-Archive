---
title: "VMWare not responding"
date: 2008-05-28
forum: Virtualisation
---

### Post by RandyRandola on 2008-05-28
Installed VMware on ubuntu 8.04. Installed XP Pro and the two programs I really need. 

Worked awesome for two weeks. Now, when I click on

Applications
Other
VMware Server Console

The cursor does it circular thing, VMware appears at the bottom for a time, and then it all goes away.

No changes to the system except for the last two updates. Which dummy me did not test this after the updates.

So, VMware gurus out there in cyber land, how to troubleshoot and repair this? There is data there I need. 

Thanks!

Randy

---

### Post by albertogdy on 2008-05-28
Hi,
but maybe you upgraded the kernel and thats a change.
What kernel have you install recently?
Maybe the 2.6.24-17-generic?
Check and try with the previous one 2.6.24-16-generic
Brgds,

---

### Post by RandyRandola on 2008-05-28
sudo /usr/bin/vmware-config.pl

For whatever reason, VMware insisted it was loaded but not configured properly for this machine. ??? Anywa, I ran the above commend to configure it and it works. Now how about that!

Thanks for replying.

Randy

---

### Post by Scipio_Publius on 2008-05-29
I have a similar problem.  I am using Ubuntu 7.10.  I originally installed VMWare 1.4.x and all seemed well.  I decided to try to install 1.5 and it failed.  I removed everything and noticed 1.4.x was in the repository.  

I download it from the repo and it worked like a charm for a day but then the next day I started it up and it acted like it was starting but then disappeared.  I have conky open so i can see the process running and then it just stops.  I removed VMWare totally and reinstalled it and it works for a day then next day same thing.  I have now uninstalled and reinstalled 4x and get the same result.  Anyone else ran into this?

---

