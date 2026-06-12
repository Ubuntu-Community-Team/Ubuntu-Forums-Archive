---
title: "DNS Server not working"
date: 2013-06-18
forum: Server Platforms
---

### Post by Chris2K on 2013-06-18
Hey. First post here, which means I've exhausted all other options. I hope someone here can help me, because I'm at my wits end and something this 'simple' is being far too complicated and exhausting. Basically my DNS server in Ubuntu 10.04 and now 12.04 refuses to work. I keep getting SERVFAIL (dig). I've been working on this on/off for the past 1.5years (yes, years) and it's getting ridiculous.

-I've searched through Google like a man possesed
-I've asked friends
-I've got the'Unix and Linux System Administration Handbook, Fourth Edition'
-I've got an Ubuntu 10.04 book
-I've asked a teacher 
-None of my classmates have been helpful 
-The logs show nothing relevant. I looked in /var/log/syslog

Basically it's a college assignment, but I'm having the most incredibly tough time with something that shouldn't be this hard. This is the setup:
4x VMWare Ubuntu 12.04 servers/clients (last year I tried 10.04)

RouterEXT <-------> Server1 (BIND DNS server) <---------> RouterINT (ISC-DHCP) <-------> Client1 (different subnet)
Config for DNS server posted below:

[http://i.imgur.com/lFh3yNy.png](http://i.imgur.com/lFh3yNy.png)


Obviously I need to get DNS working correctly before I can go further into the assignment. The next step is to push the DNS settings from the DHCP to the Client1 (already configured, but if DNS doesn't work, it's kinda pointless. FYI the client can ping the dns server, but not using a name.) and then an Apache webserver, with some modifications to DNS. 

I've tried various things, various ways to configure the files using information I have found, but nothing at all seem to work. Even going from to a newer version (where I had to re-learn where stuff was configured) didn't help me. I really hope someone can help me and/or shed some light on this issue, because it's driving me up the wall.

---

### Post by linuxtechguy on 2013-06-18
Your ptr record is missing a trailing period. Also you should check /var/log/messages for the errors your dns server is spitting out and fix them.

---

### Post by romeroc24 on 2013-06-18
Hello

Take a look on the nslookup test: 
nslookup Server1.school.test
server can´t find Server1.school.test.school.test: SERVFAIL

Server expect:
nslookup Server1

I your file db.school.test:

Put:
              IN NS Server1.chool.test.
Server1    IN A   172.16.1.1

Against:
@            IN  NS Server1.school.test.
@            IN  A   172.16.1.1

In the file db.192:

Put:
              IN NS Server1.
1            IN  PTR Server1.

Against:

@            IN NS Server1.
10           IN PTR Server1.school.test

In the /etc/network/interfaces

Put
dns-search school.test

Against
dns-search server1.school.test

And reboot the interface and bind9.

Good Luck

---

### Post by Chris2K on 2013-06-18
LinuxTG: Good spot, completely missed that. As for the /var/messages, doesn't exist (only syslog). I'm guessing that the /message part is something you have to enable (logging). 

Romeroc: OMG OMG OMG OMG OMG OMG OMG OMG !!!!!!!!!!!!!!!!!!!!!!! IT WORKS !!!!!!!!!!!!!!!!!! You have no idea how long I've been tinkering with all of this and how happy I am right now. Also, Client1 can resolve the DNS name (via dig). AWESOME ! Now on to the next part :) (Apache!)
[http://i.imgur.com/VUtW9k5.png](http://i.imgur.com/VUtW9k5.png)

Thanks :popcorn:

---

### Post by koenn on 2013-06-18
bind config is finicky - a single . can change the meaning of a statement or record

there are tools to check your configuration : [http://wiki.debian.org/Bind9#Testing_tools](http://wiki.debian.org/Bind9#Testing_tools)

---

### Post by romeroc24 on 2013-06-18
Very Good! Well done!

---

