---
title: "What Hardware for web server"
date: 2009-02-09
forum: Server Platforms
---

### Post by maloki on 2009-02-09
I've been browsing the forum all day to find relevant info on server hardware for web servers, but with no hit.

I'm planning to build a web server (LAMP & MySQL)
But I have NO idea what hardware to use.
My idea is as follows; 
Amd Athlon 64x2 4600-5000+ 2mb cache (preferably nothing over 65W, but in worst case 90W CPU)
4GB ECC RAM, pc 5600 ?
U160 SCSI Raid/adapter card with HD's: 1x36GB (10000rpm) and 4x18GB (10000rpm)
Abit motherboard (10/100/1000 built in LAN card) that needs capacitors changed (need to soldier new ones on)

I do have several P2 and P3 in the closet that can be used if there is any use for them!

Should I run separate SQL, LAMP, File servers ?

The load on the web server will be around 30 000 hits daily, with loads of audio and documents downloaded. Sitting on LAN 100/10 Mbit/s.

Will the suggested hardware be able to handle this kind of load, or should I get my hands on a HP Proliant DL580 G2 with 2x1,4GHz 4GB RAM ? 32bit (CPU) against my config 64bit? :confused:


PS: Do I need any hardware firewall or will the IP-Tables be enough?

---

### Post by jimv on 2009-02-09
>The load on the web server will be around 30 000 hits daily, with loads of audio and documents downloaded. Sitting on LAN 100/10 Mbit/s.


Wow!  What's the website?

---

### Post by beno1990 on 2009-02-09
> **maloki said:**
> 

Should I run separate SQL, LAMP, File servers ?


If it's financially feasible, then it's definitely a good thing to do. Otherwise, it might be better to have just 2 servers, both running all applications, and make a high availability cluster.

> 
The load on the web server will be around 30 000 hits daily, with loads of audio and documents downloaded. Sitting on LAN 100/10 Mbit/s.

Will the suggested hardware be able to handle this kind of load, or should I get my hands on a HP Proliant DL580 G2 with 2x1,4GHz 4GB RAM ? 32bit (CPU) against my config 64bit? :confused:


My site gets about half of the hits you're estimating for your site, and it's nowhere near even half-load on 2 HP ProLiant DL380 G3s. I think the spec you've listed above may work well enough, but for a dedicated server you should really be looking at hardware which was designed for server applications.

> 
PS: Do I need any hardware firewall or will the IP-Tables be enough?

A hardware firewall is always nice, but it can be infeasible. It might be better to install an intrusion detection system on the servers themselves. Other additional software like Portsentry might be a good idea, too, if you don't want to set up a full IDS.

---

### Post by maloki on 2009-02-10
> **jimv said:**
> >The load on the web server will be around 30 000 hits daily, with loads of audio and documents downloaded. Sitting on LAN 100/10 Mbit/s.


Wow!  What's the website?

There is no website yet, It's only a estimation.

Thank you Beno1990. The info provided was helpful.

---

### Post by volkswagner on 2009-02-10
The Pent2 or Pent3 could be used as a dedicated email server to reduce load on main server and help with administration.  Provided you won't be getting 30k emails in and out per day, the pent2 would be a good choice at 35-40 watts at the wall outlet.  :)

---

### Post by maloki on 2009-02-10
> **volkswagner said:**
> The Pent2 or Pent3 could be used as a dedicated email server to reduce load on main server and help with administration.  Provided you won't be getting 30k emails in and out per day, the pent2 would be a good choice at 35-40 watts at the wall outlet.  :)

Didn't think of that, good idea :)
Thx

---

