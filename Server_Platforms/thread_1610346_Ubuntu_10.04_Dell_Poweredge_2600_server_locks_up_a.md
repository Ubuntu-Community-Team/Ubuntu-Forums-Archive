---
title: "Ubuntu 10.04 Dell Poweredge 2600 server locks up at 94% on Detecting Network Hardware"
date: 2010-10-31
forum: Server Platforms
---

### Post by bloodhacker2 on 2010-10-31
Hey guys.
So basically what I am trying to do is install Ubuntu 10.04 on a Dell Poweredge 2600 server. Right now I don’t care wither I get the server version or the desktop version, I just need to get it on their. 
Ok so this is what I have run into. When installing the regular Ubuntu 10.04 desktop for 32bit, the server just locks up on the very first ubuntu install screen and the keyboard lights just start blinking non stop. When I use the server version, the server get to the Detecting Network Hardware and locks up at 94% and the keyboard will also start blinking nonstop. 
I have looked all over for an answer to this problem and have yet to find one. 
This guy figured out how to make it work but he never mentioned what version he was using. 
[http://ubuntuforums.org/showthread.php?t=1326678](http://ubuntuforums.org/showthread.php?t=1326678)

On this server I have 6 HD’s, 5 of them are RAID 0 with 1 Hot Spare. I have also tried using the ubuntu-10.04.1-alternate-i386.iso.torrent and still had the same problem. I have spent the last 3 days searching all over google and the forum to an answer but had no luck.

---

### Post by P4man on 2010-10-31
Its probably not the same issue I had, but on an older poweredge I struggled with ubuntu as well; it was due to the ide cd/dvd controller which was connected to the raid controller. and the installer didnt like it. It would boot up initially but fail to get anywhere, it would just hang sometime after loading the kernel. I had to resort to a PXE network boot to get it going (that machine didnt boot from USB, or it would have been eaiser).

---

### Post by bloodhacker2 on 2010-10-31
so how do i do this?

---

### Post by bloodhacker2 on 2010-10-31
is it possible that i can install a older version of ubuntu and update it to 10.04?

---

### Post by P4man on 2010-11-01
IF the machine supports booting from USB, I would give that a try. Just make a bootable USB stick with unetbootin or whatever.

---

### Post by bloodhacker2 on 2010-11-01
JW, but what difference would this make?

---

### Post by P4man on 2010-11-01
If you have a different problem then I had, then it will make no difference. But on the poweredge I tried, it was the difference between locking up and installing without  a problem. In my case it was just the cdrom controller chained to the raid controller that caused issues, but my symptoms where slightly different (booting from CD would crawl to a halt and eventually stop at some time after loading the kernel).

---

### Post by bloodhacker2 on 2010-11-01
Interesting, i will try this and let you know how it goes. 

Thanks for all the help you are providing :)

---

### Post by bloodhacker2 on 2010-11-01
lol well, the dell poweredge 2600 will not support booting from USB stick or any other USB device.

God any other ideas?

---

### Post by samosamo on 2010-11-02
What have you done to troubleshoot?  You said it gets to detecting network hardware and then fails.  Did you try disabling the network adapters in BIOS as well as pulling all PCI network adapters?

In the first post you said you have 6 hard drives configured as RAID0+spare.  Are you sure that is true?  I won't question why you configured it that way, but this is uncommon and undesirable for several reasons and may even be causing your problem.

---

### Post by P4man on 2010-11-02
> **bloodhacker2 said:**
> lol well, the dell poweredge 2600 will not support booting from USB stick or any other USB device.

God any other ideas?

Yep. Two ideas in fact. Create a plop boot disc (cd or floppy) and use that to boot from USB even if the machine doesnt support it:
[http://www.plop.at/en/bootmanager.html](http://www.plop.at/en/bootmanager.html)

Or use this trick:
[http://ubuntuforums.org/showthread.php?t=1026616](http://ubuntuforums.org/showthread.php?t=1026616)

The fact your machine is old enough it doesnt support USB booting reinforces my guess that you also have a PERC raid controller which is used for the cd/dvd, and its actually the same problem I had and the person in the above link.

---

### Post by bloodhacker2 on 2011-01-10
> **samosamo said:**
> What have you done to troubleshoot?  You said it gets to detecting network hardware and then fails.  Did you try disabling the network adapters in BIOS as well as pulling all PCI network adapters?

In the first post you said you have 6 hard drives configured as RAID0+spare.  Are you sure that is true?  I won't question why you configured it that way, but this is uncommon and undesirable for several reasons and may even be causing your problem.


OK so after doing a bunch of trouble shooting i this its my raid setup that is causing this problem.

So, what im asking for now is some suggestions for this RAID set up.

How would you guys set it up for a web server?

---

### Post by samosamo on 2011-01-10
Why did you put your disks in RAID0 in the first place?  Do you know what RAID is?

I can't suggest what RAID you need.  Only you can determine that.  Maybe you want RAID50.  Maybe RAID10 + spare.  Maybe you want 2x in RAID1 and the rest in RAID5, or RAID6 even.  One thing is for sure, you do not want RAID0 on your server.

---

### Post by bloodhacker2 on 2011-01-11
This is the deal. 
I was trying to get all the drives to be seen as one with a hot spare.

See i have been reading up on RAID for a few months now and figured that would bee my best option for a web server.  

But i can see now how this could have been foolish decision. 

what would your recommendations be? 



I am learning, bare with me.

---

### Post by bloodhacker2 on 2011-01-11
> **samosamo said:**
> Why did you put your disks in RAID0 in the first place?  Do you know what RAID is?

I can't suggest what RAID you need.  Only you can determine that.  Maybe you want RAID50.  Maybe RAID10 + spare.  Maybe you want 2x in RAID1 and the rest in RAID5, or RAID6 even.  One thing is for sure, you do not want RAID0 on your server.


Ok, after doing endless amounts of research about raid i think i have found a solution that will work.

I have found the best option to do is have a RAID 1 for the OS and a RAID 10 for the site data due to the website applications. 

What do you think? 
Will this work with linux?

---

### Post by jcdudc on 2011-05-29
how did you end up configuring your sever?  trying to do same with poweredge 2600 and can't get raid issues resolved.

---

### Post by novafluxx on 2011-05-29
Boot from live CD of Ubuntu 10.04, see if the network works in the live environment.

---

### Post by novafluxx on 2011-05-29
> **jcdudc said:**
> how did you end up configuring your sever?  trying to do same with poweredge 2600 and can't get raid issues resolved.

Dell has an alternate OS queue. That server has lifetime phone support. Call Dell at 1-800-822-8965. They may be able to help you troubleshoot the RAID issue. I assume the system has a PERC3 RAID controller.

NEVER use RAID 0 for a server. Unless its a plaything you're just experimenting on. If you put a server into production with a RAID 0...you're just asking to lose all of your data.

---

