---
title: "server backup including system files"
date: 2010-04-22
forum: Server Platforms
---

### Post by jm2 on 2010-04-22
I am researching how to make an effective backup on Ubuntu Server. This server will have Vsftp, VPN, Samba stuff , many other added packages +many printers, many users + data.

I know I can use tar for the data /u no problem.

1. I was testing tar on the /home directory on a few user directories. 
I then created a new directory and did a restore of the users directories on it. 
I noticed the /home/user owner and group were root. The files in each directory remained the same.

This gave me concern. If I had a crash and had to restore these to a new HD. I would have to change these, what else would I need to change? 

2. Since I have many config files, how do I back up them?  I know I can do a dump, but then users shouldn't be on the system. The system files will change as they add users, printers, etc, and asking users to not work, is not really an option while dump is running.

I thought I could do a tar on whole system. (cron late at night .. not as many users)
Then in event of crash of HD.

1. Boot from live cd 
2. format the new drive
3. tar back in the whole system
(hopefully it would restore all my config files and printer setups, etc)


Will this work right?
Is there something I am missing?

I'll take suggestions.

Thanks

---

### Post by Vegan on 2010-04-23
You might want to use a separate file server to store the backup, I have not tried to tar the who machine, I just backup my web folder.

---

### Post by HermanAB on 2010-04-23
Howdy,

I handle the problem of server backups through virtual machines.  I install a server as a small VM that can be backed up to a DVD.  The data, remains outside the VM on a networked storage device.  Then, I only make regular backups of the data.  

One day when the hardware fails, I can install VMware on a new machine and recover the VMs from DVDs and be up and going again in no time flat.

---

### Post by jm2 on 2010-04-24
Please, forgive me  I am sort of new to VM machines. I have only used it to test some software without taking the chance messing up a live system. And going back to see if it worked. I am struggling with some concepts.

So you set up your Host machine with whatever Ubuntu version you need. Then you have to load a VM program, install (restore) your VM image, then install (restore your data).


I am assuming the Host OS needs no other setup other than perhaps firewall, and initial network connection.

The VM Guest OS then can have control of users, printers and other devices over the network?
The data directory would need to be mounted in the VM 

I know this is a very stupid question, from my understanding a VM is supposed to be inclusive. I know how a user gets to the Host server, (via telnet/ssh) . But how does the user then get into VM to access resources and programs in there? 
I have many users on this system in different rooms, this isn't a one person trying to use this VM from the server. (Which has been my only experience.)

If someone could explain general concepts or point me into the direction I should be looking at, I would appreciate it.

Thanks again.

---

