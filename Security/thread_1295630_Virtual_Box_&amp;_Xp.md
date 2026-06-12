---
title: "Virtual Box &amp; Xp"
date: 2009-10-19
forum: Security
---

### Post by lizandeen on 2009-10-19
I'm thinking of using Virtual Box to run Xp. What I was wondering was, do I still need all the firewall/anti-virus/ anti-spyware programmes necessary in Xp even though Virtaul Box is run through Ubuntu?

---

### Post by squaregoldfish on 2009-10-19
The short answer is yes - as far as the world outside your machine is concerned, you're using Windows so it has the same vulnerabilities. The only exception to this may be the firewall, as Linux will be responsible for routing incoming traffic to the Windows VM.

However, you may consider that your virtual installation is disposable, in that it can be reinstalled at will if it gets compromised, without affecting your base OS. Whether or not this is something you can live with will depend on what you intend to do with your virtualised installation. If you want to use your Windows install for something important though, all the usual backup/protection stuff still applies.

Steve.

---

### Post by lizandeen on 2009-10-19
Thanks Steve, that was precisely what I was wondering

---

### Post by Lars Noodén on 2009-10-20
One advantage to be aware of is that you can take snapshots of the VM and keep them as backup.  Then it is possible to start each and every VirtualBox session as if it were an absolutely fresh install of XP and the packages you want.

[http://ubuntuforums.org/showthread.php?t=689982](http://ubuntuforums.org/showthread.php?t=689982)

[http://srackham.wordpress.com/cloning-and-copying-virtualbox-virtual-machines/](http://srackham.wordpress.com/cloning-and-copying-virtualbox-virtual-machines/)

[http://en.onsoftware.com/how-to-create-and-manage-snapshots-in-virtualbox/](http://en.onsoftware.com/how-to-create-and-manage-snapshots-in-virtualbox/)

---

