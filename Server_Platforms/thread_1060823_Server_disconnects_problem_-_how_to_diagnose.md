---
title: "Server disconnects problem - how to diagnose?"
date: 2009-02-05
forum: Server Platforms
---

### Post by SoundFriend on 2009-02-05
My server now runs 8.04 and Samba on an old PIII machine.  It is an old installation, originally running Fiesty but has been upgraded over time.  For some months (using Gutsy) I have experienced seemingly random disconnects to the Samba shares, and a ssh connections can fail too.  The server eventually reconnects itself. Pinging another machine from the server and vice-versa seems to work reliably, strangely. I had suspected a faulty network card but have replaced it with no improvement. 

The server is issued a fixed IP address by the DHCP server in the router.  I found yesterday that issuing a 'dhcp' command on the server console would instantly reconnect the server.  

My question: is this a hardware or software issue, and how do I monitor/diagnose the problem?

Incidentally I have tried another similar server on my network, and it is absolutely fine.

John

---

### Post by Endwin on 2009-02-05
You could try looking at your **/var/log/syslog** and **/var/log/daemon.log** See if you find something going on around the time of the disconnect. It is possible it is trying to renew the IP for a static lease and for some odd reason in the process it is dropping the connection till the lease is renewed. You could consider setting a static IP for the machine, and not deal with DHCP static leases at all. Also since this is an upgraded machine. There could be some odd problem. (I had this before when upgrading a few times especially with finicky things like samba) and you just need a clean reinstall to make everything work correctly.

---

### Post by SoundFriend on 2009-02-05
Thanks 'Endwin' for the pointers to the log files, I'll try to see what's going on.  

I am out of the office today, and logged in using ssh for about 5hours without mishap, so that's interesting.

> **Endwin said:**
> ..you just need a clean reinstall to make everything work correctly.

I was afraid that you'd say that :)

John

---

### Post by SoundFriend on 2009-02-05
Looking at the **daemon.log** file DHCP seems to operate ok, but I've just taken a look at **syslog** and I am seeing the following entry every 80 sec or so:

Feb  5 15:29:35 chef kernel: [92862.707710] parport0: FIFO is stuck
Feb  5 15:29:35 chef kernel: [92862.747699] parport0: BUSY timeout (1) in compat_write_block_pio
Feb  5 15:29:45 chef kernel: [92872.744240] DMA write timed out

This may not be relevant to my IP address problems but...?

John

---

### Post by Endwin on 2009-02-05
A quick search on that looks like that message is a problem with printing to a printer. Is this machine some kind of print server? It may affect the network, if the server is being overwhelmed with requests, and cannot print.

---

### Post by SoundFriend on 2009-02-05
> **Endwin said:**
> A quick search on that looks like that message is a problem with printing to a printer. Is this machine some kind of print server? It may affect the network, if the server is being overwhelmed with requests, and cannot print.

Interesting. It is a print server. There are some very old docs in a print queue for a parallel port printer that isn't currently in use.  Is this a problem for the server ?

John

---

### Post by Endwin on 2009-02-05
Hard for me (personally) to tell I don't have a lot of experience with print servers. Never really had a need to set them up. (I have printers with built in nics that I set a static IP for and just point all the machines to it. If something goes wrong swap printer and switch the nic and away I go.) I would clean out the que, and see if that helps, old print jobs sitting there are not helping anything, and who knows maybe some conflict is coming up. I have seen stranger things happen with computers. Sometimes its like voodoo :D

Clean out the print que and see if that helps anything.

---

### Post by SoundFriend on 2009-02-05
> **Endwin said:**
> I have seen stranger things happen with computers. Sometimes its like voodoo :D

Clean out the print que and see if that helps anything.

Thanks, I'll try this later and report back if it fixes the problem.

---

### Post by SoundFriend on 2009-02-06
I cleaned out the print queue (after having fixed CUPS server which wasn't talking on port 631 - something had changed the configuration file), and the FIFO stuck kernel messages have now stopped.  

I'm still left with my original DHCP problem.  I guess a re-install in on the cards.  I thought that was what Windows users always had to do ;)

John

---

### Post by SoundFriend on 2009-02-06
Ok, I've done a clean install... and I still have the problem.

I think that I'll change the router.

[Edit]
I seem to have solved the problem by making the IP address unfixed in the router. I can probably make the IP address static by editing /etc/network/interfaces. 

I may change the router anyway soon as the WAN port is too slow.

John

---

### Post by cariboo on 2009-02-07
Wouldn't it have been easier to install another nic?

Jim

---

### Post by SoundFriend on 2009-02-07
> **cariboo907 said:**
> Wouldn't it have been easier to install another nic?

Jim

Thanks, but I already have tried that.

John

---

### Post by mstrap123 on 2009-06-04
hi.. i am also experiencing the same problem as this, is it solved yet, wat causes this problem

---

### Post by SoundFriend on 2009-06-05
> i am also experiencing the same problem as this, is it solved yet, wat causes this problem 

Hi mstrap123,

Yes, I have fixed the problem, sorry I couldn't find out how to mark the thread as fixed.  

It wasn't a software problem at all.  My old server Pentium III hardware had some problem with the IDE ports which was causing the disconnects (and data loss).  I ran the machine on the bench and connected two IDE drives. There were errors apparent copying large files between drives.

As a cure I simply swapped the hard disks over to another PIII machine, (just try doing that with Windows) and it hasn't missed a beat so far, latest uptime is 100days.

As a result of the problems I added an external USB hard drive, and a script to perform a daily snaphot backup that rotates after a week.  This has given me additional security over my data.

My original question was how to diagnose the problem.  Actually I rather failed to do that from looking at log files etc, but a cure was eventually found :)

John

---

