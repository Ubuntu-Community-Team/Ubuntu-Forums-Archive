---
title: "Ubuntu 8.04 on new HP DL120G6"
date: 2010-05-06
forum: Server Platforms
---

### Post by Tribl on 2010-05-06
Hello Forum
 
We are about to get a new Asterisk telephone system which only runs on Ubuntu 8.04 (dont ask me why).
So i need a new Server and found a HP DL120 G6. 
How do i find out if ubuntu 8.04 works on that server and has all the necessary drivers for it, cause I'm kind of a complete noob with Linux. 
The HP Support couldnt help me because they dont support Ubuntu officially
 
Please help me
 
Thank You
 
Tribl

---

### Post by windependence on 2010-05-06
I don't think you'll have any problems with the HP box as I have loaded it on similar hardware. Did Asterisk recommend any particular hardware? 8.04 is pretty forgiving. 

-Tim

---

### Post by Tribl on 2010-05-06
Not that i know of. The guy that handles this matter for us, recommended a Dell D200 simply because he has the same Asterisk on that machine running without any problems. So i guess there is no special hardware that is needed but since the Dell Server is "older" its better supportet by Ubuntu, i think
 
Problem is we have HP Servers only and my boss wants it to stay this way

---

### Post by spynappels on 2010-05-06
You'll have no problems.

Is that an Intel or AMD box? I have run Asterisk on ML110G5 and ML115G5 (Intel and AMD resp), both on Ubuntu and CentOS (AsteriskNOW) and have had no problems. Install seems to take longer on Intel box for some reason, but is fine in the end.

---

### Post by ghost_ryder35 on 2010-05-06
> **Tribl said:**
> Not that i know of. The guy that handles this matter for us, recommended a Dell D200 simply because he has the same Asterisk on that machine running without any problems. So i guess there is no special hardware that is needed but since the Dell Server is "older" its better supportet by Ubuntu, i think
 
Problem is we have HP Servers only and my boss wants it to stay this way

HP will work great.  To bad they (whatever company said only 8.04) dont support it on 9.04 or 9.10 cause HP has awesome tools for those versions (HP tools might work on 8.04 but would not be supported by HP).

---

### Post by Tribl on 2010-05-06
So in essence i put the cd in install ubuntu and everything should work. No need to get a linux freak (no offense) to  help with driver issues?

Its an Intel sytem btw

sorry if i ask silly questions, but i dont want to buy a new Server and then cannot use it for its purpose

---

### Post by windependence on 2010-05-06
> **Tribl said:**
> So in essence i put the cd in install ubuntu and everything should work. No need to get a linux freak (no offense) to  help with driver issues?

Its an Intel sytem btw

sorry if i ask silly questions, but i dont want to buy a new Server and then cannot use it for its purpose

Linux != Windoze

We don't generally have driver issues as they are built into the kernel for the most part. I have installed 8.04 on an ML115G5 without problems. HP is great about this and supports Linux quite well.

Good luck!

-Tim

---

### Post by ghost_ryder35 on 2010-05-06
^^^^^^^^^^^^ what he (or she) said ;-)

---

### Post by Tribl on 2010-05-06
> **windependence said:**
> Linux != Windoze

We don't generally have driver issues as they are built into the kernel for the most part. I have installed 8.04 on an ML115G5 without problems. HP is great about this and supports Linux quite well.

Good luck!

-Tim

Except for the part where they told me that officially they only support Enterprise Editions of Redhat and Suse and give no guarantee that ubuntu will work without problems ;). Since they are in the kernel , doesnt that mean i would have to update the kernel??

But thanks to all of you, guess I'll place my order and hope for the best

---

### Post by windependence on 2010-05-06
> **Tribl said:**
> Except for the part where they told me that officially they only support Enterprise Editions of Redhat and Suse and give no guarantee that ubuntu will work without problems ;). Since they are in the kernel , doesnt that mean i would have to update the kernel??

But thanks to all of you, guess I'll place my order and hope for the best
The kernel today is modular, that is to say that it is rare to have to rebuild the kernel to add support for hardware. The kernel would be the same in RedHat or SuSE as it is in Debian or Ubuntu. Trust us when we say we are confident that you will have no problems. Linux support for HP hardware is very very good.

> HP also committed to testing and ensuring compatibility of Ubuntu 8.04  LTS Server Edition on select Proliant servers &#8211; but failed short of  offering certification or support beyond that.

[http://www.zdnet.com/blog/open-source/ubuntus-corporate-ready-804-is-released-but-is-three-a-crowd-in-linux-server-market/2337](http://www.zdnet.com/blog/open-source/ubuntus-corporate-ready-804-is-released-but-is-three-a-crowd-in-linux-server-market/2337)

-Tim

---

### Post by Tribl on 2010-05-06
Quote from your Link:
“While HP continued to closely monitor demand for pre-loaded Linux PC offerings all of our regions around world, we are not seeing significant customer demand for expansion of our Linux plans to include Ubuntu,” said Tiffany Smith, a spokeswoman for HP Personal Systems Group.;)

---

### Post by kharcell on 2010-05-25
Hello @ all,
 
i am a colleague of tribl's and have to do the ubuntu installation he mentioned. 
 
Our problem is that the dvdrom drive will not be recognized. **i8042o.c no controller found** flashes when initializing the install routine. And it seems that it is especially a problem with the ubuntu 8.04 server version, because we've already installed a working centos and ubuntu 9x on the same machine.
 
Just for your information.
 
With best regards
 
kharcell

---

### Post by dragos2 on 2010-05-25
> **kharcell said:**
> Hello @ all,
 
i am a colleague of tribl's and have to do the ubuntu installation he mentioned. 
 
Our problem is that the dvdrom drive will not be recognized. **i8042o.c no controller found** flashes when initializing the install routine. And it seems that it is especially a problem with the ubuntu 8.04 server version, because we've already installed a working centos and ubuntu 9x on the same machine.
 
Just for your information.
 
With best regards
 
kharcell

Please try 10.04.

---

### Post by Tribl on 2010-05-26
> **dragos2 said:**
> Please try 10.04.
 
As i said before its necessary to use 8.04, which simply doesnt work, cause it doesnt find the cd drive or the raid controller. Guess its not that easy and without problems like all of you wanted me to believe

---

