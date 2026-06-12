---
title: "What is this?"
date: 2009-06-08
forum: Security
---

### Post by hambone79 on 2009-06-08
I have an Ubuntu 9.04 machine up and running behind a router so that the only service that is passed through is SSH. I also have a firewall running on the Ubuntu box as extra measure along with Logwatch and DenyHosts to keep me informed of what is going on.

I haven't used this machine in several weeks because I have been traveling and busy with my job.This evening I started checking through system e-mails and I started seeing tons of Logwatch e-mails with the following:

```

 --------------------- iptables firewall Begin ------------------------ 

 
 Listed by source hosts:
 Logged 627600 packets on interface eth0
   From 4.23.40.126 - 10 packets to tcp(53323) 
   From 4.23.60.126 - 11 packets to tcp(49932) 
   From 8.21.193.25 - 446 packets to tcp(39991,39992,39993,39994,39995,39996,39997,39998,39999,40000,40032,40039,40040,40041,40042,40043,40044,40054) 
   From 8.21.195.24 - 64 packets to tcp(42247,42266,42267,42268) 
   From 8.21.195.32 - 4 packets to tcp(43860) 
   From 8.21.195.64 - 142 packets to tcp(43235,43236,43237,43238,43239,43244) 
   From 17.149.160.10 - 734 packets to tcp(37484,37485,37486,37487,37488,37489,37490,37491,37492,37493,37494,37495,37496,37497,37498,37499,37500,37501,37502,37503,37504,37505,37506,37507,37508,37509,37510,37511,37512,37513,37514,37516,37517,37518,37519,37520,37521,37524,37525,37526) 
   From 17.251.200.32 - 439 packets to tcp(46510,46511,46512,46513,46514,46515,46516,46517,46518,46519,46520,46521,46522,46523,46524,46525,46526,46527,46528,46529,46530,46531,46532,46533) 
   From 58.120.225.167 - 3 packets to tcp(41552) 
   From 58.120.225.190 - 4 packets to tcp(33161,56803) 
   From 59.158.51.240 - 1 packet to udp(16038) 
   From 60.19.64.121 - 6 packets to tcp(40313,60926) 
   From 60.19.64.122 - 3 packets to tcp(37110) 
   From 60.19.64.124 - 3 packets to tcp(37243) 
   From 60.39.130.241 - 1 packet to udp(16038) 
   From 61.110.195.10 - 6 packets to tcp(37629,52908) 
   From 61.110.195.79 - 3 packets to tcp(49264) 
   From 61.110.195.80 - 3 packets to tcp(39827) 
   From 61.160.253.21 - 3 packets to tcp(49605) 
   From 61.160.253.22 - 3 packets to tcp(42587) 
   From 61.174.18.41 - 3 packets to tcp(42126) 
   From 61.174.18.42 - 3 packets to tcp(45582) 
   From 61.174.18.43 - 3 packets to tcp(32859) 
   From 61.195.23.182 - 1 packet to udp(16038) 
   From 62.78.182.10 - 1 packet to udp(16038) 
   From 62.118.240.140 - 3 packets to tcp(32990) 
   From 62.118.240.141 - 6 packets to tcp(42861,48360) 
   From 62.118.240.142 - 3 packets to tcp(39466) 
   From 62.148.157.219 - 3 packets to udp(16038) 
   From 63.150.161.165 - 6 packets to tcp(36634,60463)

```

After checking some of the IP addresses, the resolve back to websites here in the United States so I don't think this is any sort of DoS attack. Also, this started completely out of the blue on May 21st and hasn't stopped since.

Could this be some kind of kernel bug, firewall issue, or could it be someone trying to compromise my system?

---

### Post by rookcifer on 2009-06-09
Looks like fairly routine port scanning to me (actually, a couple of them where 700 packets were sent seem like they could possibly be aimed at you directly).  Is your SSH daemon running on port 22?

For kicks and grins, have you tried running an nmap scan against your network from both the inside and outside?

---

### Post by hambone79 on 2009-06-09
I haven't done an nmap scan but the thing that is throwing me off is that it is coming from so many different IP addresses...several of which resolve to Google, Yahoo, Ubuntu Forums, etc.

---

### Post by lensman3 on 2009-06-09
About 1200-1300 packets were written to the log.  Out of 600,000 plus packets that went through the interface.  I don't think they are worth worrying about unless you have somebody trying to login on ssh and then the log should have  lots of failed login attempts.  Compare the port number and what is in /etc/services to see if those are any registered services like ovsessionmgr.  Do a "more /var/log/messages" to see the specific packet messages that iptables writes out.

If one site gets to be very annoying, then set up an iptables rule to always drop that site's IP.  Whenever I do a lot of music downloads, I end up getting a lot of hits, but mostly from Asia.  The downloading software can generate a lot of hits from other programs.

But always spend time looking at the logs.  I had a site  once that tried to break my passwords using fetchmail and imap.  The attack resulted in a lot of hung processes, which used up the kernels process stack.  I finally noticed the attack when I couldn't download my email

---

