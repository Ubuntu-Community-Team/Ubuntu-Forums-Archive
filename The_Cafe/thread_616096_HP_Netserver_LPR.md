---
title: "HP Netserver LPR"
date: 2007-11-17
forum: The Cafe
---

### Post by Compucore on 2007-11-17
I recently took a plunge and went to a local computer recycling center near by where I live and picked up a server by hp. Its a Netserver LPR 2U with 2 18 gig scsi drives,a Pentium III 650 CPU. I am going to be speaking with a guy that I know there in order to get a second CPU for it Since the person I had purchased it at the store mis understood that I needed a a sual PIII 650 instead of a single. The gig of ram that is in there is nice forthis system. I am going to negotiate a price for the second because I still need a second CPU if I am going to be adding Oracle 11I into it to tinker around. And install ubuntu gutsy Gibson on it as well. I paid about $100 for ut used. And I'll see at a later time how much a raid array will cost as well since tao 18 gig is not that much space to work with. And there seems to be almost no room to swap in a 160 gig drive underneath the hood to add into it as well. 

ANd wanted to know what you thought about that system to tinker around with in ubuntu. And I am also looking for the manual as well for this machin and still can't find the pdf file from HP or elsewhere on the net for this as well. Since I needed to get some more information about the machine in order to get more familiar with it as well.

Regards,

Compucore.

---

### Post by HermanAB on 2007-11-17
You should install Xubuntu, then it will run OK, even with a single CPU.

Cheers,

Herman

---

### Post by Compucore on 2007-11-17
Well I will be running it as a server with Oracle 11i or 10G on it to do remote databasing with it. So the interface of Ubuntu will not be on there. Including Xubuntu interface. Basically its to try and do some dataprocessing on a server of my own with it. For a learning experience with Oracle. And setting up a server on my own with ubuntu. the worste case I might put in there Solaris 10 as an alternative. right now I just think of what other OS could be user with this can of system. Since windows will not be an alterntaive.

---

### Post by Slade Winstone on 2007-11-27
Hey Compucore,

Any luck with the Ubuntu/Xubuntu install on the HP Netserver LPR?  I might be picking up one myself, and I'm interested in running Ubuntu server on it.

Slade.

---

### Post by Slade Winstone on 2008-01-15
Hi,

I got my HP Netserver LPRs up and running.

The key for me was to use CTRL+M and  enter the Netraid setup and change the Adapter setting from I20 to MASS STORAGE.

Then to boot and install Ubuntu 6.06 LTS, I had to specifiy the kernel boot paramter of NOAPIC.

After that everything is working fine and I'm very happy.

If you have any questions let me know.

Slade.

---

