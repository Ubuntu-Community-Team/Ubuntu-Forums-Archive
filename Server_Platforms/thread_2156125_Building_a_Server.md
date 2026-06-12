---
title: "Building a Server"
date: 2013-06-20
forum: Server Platforms
---

### Post by gerrman97 on 2013-06-20
I recently aquired a 2005 Compaq Presario. My plan is to turn it into a fileserver for me and my friends to store our designs. Anyway, for specs:
2.46 GHZ AMD Athlon X64 Processor, 1 gig ram (not sure what kind yet), and it will have a 1TB hdd. Will that suffice? What OS should I use? I have a copy of Ubuntu server 12.04 LTS. If you have any suggestions, that'd help.

---

### Post by gerrman97 on 2013-06-20
I have another computer, a Dell Inspiron 531 with the same processor, but double the ram. Should I use that instead. Currently no hard drive. The one I usually use is in my laptop. Or, maybe I should combine them. Idk. Opinions please.

---

### Post by d4rk0wl on 2013-06-20
I am running a server with the same intentions as you, generally a file server to share information with friends, and I have a cloud setup with it too. Depending on how much traffic you plan on getting to the box the above specs should be more then enough to suffice. My server has about the same specs as yours and I have had it up for days with no problems.
As I said before, depends on how much traffic you are looking at.

Regards,
D4rk0wl

---

### Post by papibe on 2013-06-20
Hi gerrman97.

For a file server you don't much specs. 1gig of RAM is plenty, and the processor looks powerful enough.

Another thought: In my experience, even when 1Tb looks like a lot, you may be run out of space in a certain amount of time. I'd recommend using the machine that allows you grow in storage capacity (have more disks). An inspection of the SATA ports in the each motherboard should make the decision very easy.

Regards.

---

### Post by rubylaser on 2013-06-20
Another very important thing to consider is if the data is important, how do you make it redundant (RAID1/5/6 or SnapRAID, etc) and how you will back it up.

---

### Post by 3L33T on 2013-06-20
Use both computers you just described.  Make one computer your internal fileserver in the LAN/office to host your drawings.  Put the 2nd server somewhere remotely outside of the office where you have good internet connection.  Setup rsync on the internal fileserver and backup it up to the 2nd server remotely.

---

### Post by CharlesA on 2013-06-20
> **rubylaser said:**
> Another very important thing to consider is if the data is important, how do you make it redundant (RAID1/5/6 or SnapRAID, etc) and how you will back it up.

Huge +1 to that. Backing up isn't too bad if you have a script for it, but you also have to test your backups and make sure everything is ok before you actually need those backups.

you could run a server off a single drive, but I wouldn't recommend it unless you are keeping very, very recent backups. if that drive dies, you just lost all your data.

I've been running RAID5 for a while now with little problems and I have my server set it backup daily + offsite backups via crashplan.

---

### Post by wlraider70 on 2013-06-20
On the OS side stick to an LTS. Be aware that the server version has no desktop environment. 

When I set up my first ever linux machine I wanted it right so I went no desktop, I couldn't do anything.

---

