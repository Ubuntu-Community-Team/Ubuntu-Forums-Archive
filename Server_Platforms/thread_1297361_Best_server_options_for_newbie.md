---
title: "Best server options for newbie"
date: 2009-10-21
forum: Server Platforms
---

### Post by Pat-UK on 2009-10-21
Hi everyone, 
 
I have been asked to set up a server in a building with 6 or 7 WindowsXP machines, they need roaming profiles and central file storage, so I guess I need to set it up as a domain controller
 
I want to try using linux for the server side, I have an old HP dual 1.3gig CPU server with a 6 drive raid array, it has loads of memory so I think it will be more than up for the job.
 
What would be the best linux option to achieve this.
 
Any help would be great.
 
Thanks

---

### Post by cariboo on 2009-10-22
Have a look at [howto]("http://www.howtoforge.com/samba_setup_ubuntu_5.10"), it is for an older version, but it should work for what you need.

---

### Post by Pat-UK on 2009-10-22
Many Thanks for your reply, just to confirm will I habve to use the old version as mentioned in the post or should I use the latest version and just apply the instructions.
 
Also I could see no referance to roaming profiles, will that all fall into place once installed  ??

---

### Post by Lars Noodén on 2009-10-22
Samba is a good choice, especially when old platforms are involved.  

If you are looking just for file sharing, then web_dav+https is another option.

---

### Post by Pat-UK on 2009-10-23
well I have followed the Howto and fallen over at page 3.
 
The machine boots and gives me a DOS command prompt type screen, and thats it .
 
I have tried following the instructions to change the IP to static, and all I get is no such file or directory, it seems that there are some vital instructions missing between page 2 and 3, maybe I need a page 2.5 ??
 
are there any more idiot proof guides around ??

---

### Post by The Real Dave on 2009-10-23
> **Pat-UK said:**
> well I have followed the Howto and fallen over at page 3.
 
The machine boots and gives me a DOS command prompt type screen, and thats it .
 
I have tried following the instructions to change the IP to static, and all I get is no such file or directory, it seems that there are some vital instructions missing between page 2 and 3, maybe I need a page 2.5 ??
 
are there any more idiot proof guides around ??

That howto uses a very old version of Ubuntu. An article I used to set up an Ubuntu server a few months ago was [this]("http://www.howtoforge.com/perfect-server-ubuntu-9.04-ispconfig-2"), but it doesn't mention anything about domain controlling, so I don't know how relavent it is for your needs

---

### Post by whoop on 2009-11-07
This is the most up-to-date complete tutorial on roaming profiles, domain controller etc. I could ever find:
[http://www.rrcomputerconsulting.com/view.php?article_id=3](http://www.rrcomputerconsulting.com/view.php?article_id=3)

Sadly it is written for ubuntu 7.10, although it works for ubuntu 8.04 LTS (with just tiny obvious changes).

All in all we could say that the documentation on this crucial topic is very outdated, so please **vote** to change this:
[http://brainstorm.ubuntu.com/idea/22151/](http://brainstorm.ubuntu.com/idea/22151/)

---

