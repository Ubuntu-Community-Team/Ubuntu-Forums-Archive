---
title: "is this computer adequate..."
date: 2010-02-04
forum: Server Platforms
---

### Post by ja660k on 2010-02-04
hey guys,
i saw a lil computer which is quite cheap and im thinking of buying it.
to dump ubuntu server on it.

the computer was... as i remember...
2.0Ghz 
512 mb ram
320 gb HDD

and it has xp on it but thats not important.
is that enough to run the server?

i plan to have upnp server for my local network. along with apache, tomcat, glassfish to test my php,java and ruby on

is that processing power enough?
thanks in advance

---

### Post by lisati on 2010-02-04
You might be able to use it, but I'd suggest investing in some more RAM if your server is likely to be busy.

---

### Post by ja660k on 2010-02-04
define busy?
it wont be accessible from the WAN. maybe just for ssh

---

### Post by lisati on 2010-02-04
> **ja660k said:**
> define busy?
it wont be accessible from the WAN. maybe just for ssh

It'll *probably* be ok if it's just on your own network. (I haven't used a machine with 512Mb for a while....)

---

### Post by ja660k on 2010-02-04
> **lisati said:**
> It'll *probably* be ok if it's just on your own network. (I haven't used a machine with 512Mb for a while....)

yeah the ram is the thing i am worried about also.

---

### Post by FuturePilot on 2010-02-04
If it's only going to be used on the LAN and lightly used, that is plenty. I have an internal only server that is mainly a file server and print server. It's a Pentium 3 @ 1GHz, 512MB RAM and combined disk space of 140GB. 512MB of RAM is plenty for what it does and it runs great.

```
             total       used       free     shared    buffers     cached
Mem:           497        473         24          0         59        308
-/+ buffers/cache:        104        392
Swap:         1105          7       1098

00:40:52 up 53 days, 22:37,  3 users,  load average: 0.00, 0.02, 0.01
```

---

### Post by trundlenut on 2010-02-04
it should be fine, it will be quicker than my 550mhz P3 with 512mb of ram and I use that for apache and as a file server.

---

### Post by samalex on 2010-02-04
> **ja660k said:**
> hey guys,
i saw a lil computer which is quite cheap and im thinking of buying it.
to dump ubuntu server on it.

the computer was... as i remember...
2.0Ghz 
512 mb ram
320 gb HDD

and it has xp on it but thats not important.
is that enough to run the server?

i plan to have upnp server for my local network. along with apache, tomcat, glassfish to test my php,java and ruby on

is that processing power enough?
thanks in advance

I think it'd run fine...  Our Linux User Group website runs on the following setup with zero problems or latency:
- 32-bit Ubuntu 9.04 Server
- 2Ghz AMD Athlon(tm) XP 2800+
- 1GB Ram
- 120 Gig HD

This server runs about 10 websites (different domains), IRC server, News server, and locally I have Netatalk and NFS setup to connect to it from Linux and OSX.  I'm even running an old-school BBS using Synchronet from the system :)  All this over my cablemodem.

Now we don't get just a ton of traffic, and if Slashdot'ed or Dugg the server wouldn't hold up... but for the 50 to 100 connections we get a day this system keeps up quite well.

Linux is VERY robust and one thing I like is the fact that it can run very well on little hardware.  My only suggestion would be to upgrade the RAM if you'll be running lots of database processes or web applications, but outside of that I think it'd make a good _home_ server.

Take care ...

Sam

---

### Post by Demented ZA on 2010-02-04
Assuming your sunning server without x, its more than enough! :-)

I'm running an ubuntu server with lamp hosting a joomla website, its a firewall, gateway, dhcp, dns, samba file share, ftp, and does automatica backups and its running fine on a 
P4 3GHz (Underclocked to 1.7GHz for running without a fan) and an 8gb flashdrive as hdd with 512mb DDR1 ram.

In the end, its faster than my Netgear router. If that helps :-)

---

### Post by Sporkman on 2010-02-05
My website once got deluged by stumbleupon visitors - >10K per day over a week or two. At the time it ran on an athlon 2K w/ 256 megs RAM, and it didn't break a sweat.

---

