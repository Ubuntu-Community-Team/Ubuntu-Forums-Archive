---
title: "Lubuntu 14.04 virtualbox windows xp running real slow...."
date: 2014-06-25
forum: Virtualisation
---

### Post by therrera1550 on 2014-06-25
Hi,

I recently setup an old Dell laptop (Inspiron 1150) with Lubuntu 14.04 and a virtual box running Windows XP.  I wanted to have a safer computing environment and run our main app (Act! 11.0).  After some figuring out, I finally got it configured and running what I needed, able to browse the local network and access shares and run Act! 11.0 and synch with the Act! synch server.  This way if the test works out alright, the other workstations will be upgraded in this fashion so we can move away from Windows.

Everything works but the system is so slow to respond.  The laptop is a pentium 4 2.8 GHZ machine with 2 gigs of ram.  I configured the Windows host for 1 gig of ram.  Is there anything I can do to speed it up or is this the best I can hope for?

Thanks,

Tony

---

### Post by Vladlenin5000 on 2014-06-28
It probably is the best you can achieve. C'mon... Runing a VM in such limited hardware is asking for trouble. That said I would try with just 512MB for the XP VM *if* the apps I intend to run can live with that. Apparently not. Act! alone is such a resource hog and it requires 1GB RAM... So... I'm afraid we're back to square one.

---

### Post by TheFu on 2014-06-28
XP doesn't come with SATA or PRO/1000 network drivers. Get those, install them.  With a fully preallocated virtual HDD, I've seen 40% performance improvements ... with just those 3 things.

However, a P4 just isn't made for virtualization. Anything less than a C2D struggles to run VMs.
[http://blog.jdpfu.com/2010/06/22/virtualbox-performance-improved](http://blog.jdpfu.com/2010/06/22/virtualbox-performance-improved) is WinXP specific.
[http://blog.jdpfu.com/slowVbox](http://blog.jdpfu.com/slowVbox) has other settings that could help, but it targeted at Win7 and later Win guests.

BTW, my mother had a P4 and it just never handled virtualization well. A core i7 replacement system solved that.

I wish you luck - getting "ok" performance on old hardware is hard.

---

### Post by therrera1550 on 2014-07-07
Thanks for the replies and suggestions.  I think you are right, my hardware will not support decent speed on the vm side and I'm not versed enough to make the tweaks suggested in the article you pointed to.  My other option is to just use the laptop with xp as is, not use admin account for everyday use.

If I could find a linux contact management software that would allow synchronization between the various workstations like "Act!" does, then I'll be in business.  I'll just export my database into one of the accepted formats for the Linux database.

Thanks Again.  I think this problem would be considered solved.

---

