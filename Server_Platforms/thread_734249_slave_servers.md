---
title: "slave servers?"
date: 2008-03-24
forum: Server Platforms
---

### Post by schneider707 on 2008-03-24
I'm looking to set up a webserver off my desktop and I wanna use VMware to do this. I've installed Ubuntu 7.10(server ed) just fine and i have webmin running on it right now. I'm waiting for my domain name to become active (i guess it takes a day to get working). Now I'm looking through all sorts of tutorials and I keep seeing 'slave server' and 'master server'. What is this all about? Also, how do I know what my "ns1.mydomain.com and ns2.mydomain.com" is? Or do all websites use ns1/ns2 prefixes and then use their site domain? I've been looking around and I can't seem to find any direct answers to this.
I know that its really not that great to run a server off your home computer but for now its really just practice. I wanna make sure I know what I'm doing before I get a dedicated server.

Also, on a side note. How would I prevent x from starting on start up? I installed it to make my installation go a bit quicker but I really don't need it running anymore and its just sapping the computers resources.

Last question, why do I see so many using CentOS for servers. What are the benefits of that distro to Ubuntu in terms of servers. More efficient? Flexibility?

Thanks much for your time =P

[email]Schneider707@gmail.com[/email]

---

### Post by ikonia on 2008-03-24
this sounds like your making your self a world of pain.


1.) to run a dns environemtn your need 2 static IP addresses (master / slave)
2.) running dns servers in virtual hardware isn't great unless its a low usage dns environment
3.) running dns services on your desktop / home connections is not a good idea

the difference between distro's is personal preference, nothing more.

---

### Post by Mr. C. on 2008-03-25
You may be having trouble finding your answers because the approach you are taking is problematic.  Learn how the components fit together and how they are used so that your questions can be more refined and precise.

I read your goal as wanting to setup a web server. In order to do this, you will need to learn some basics about not only how to configure the web server, but also how domain names are translated into IP addresses, and the distinctions of web site hosting, IP-based virtual hosting, and name-based virtual hosting.

Your public domain names are unimportant for meeting your initial goal of setting up your web server.  You can do all this from within you VM machine, and should approach the setup one step at a time, perhaps in this order:

1) get a single website running.
2) learn how name -> IP address translation takes place
3) configure your system to correctly translate your desired web host name to server IP.
4) get name-based virtual hosts working.
5) configure external access as desired.

Have you achieved step 1 at this point ?

---

