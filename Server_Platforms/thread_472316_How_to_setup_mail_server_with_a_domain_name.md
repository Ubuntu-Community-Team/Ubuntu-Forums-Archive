---
title: "How to setup mail server with a domain name"
date: 2007-06-12
forum: Server Platforms
---

### Post by tarek on 2007-06-12
Hi,

I have a domain name from namecheap.com, csmonkey.com, and I'm hosting my site on my computer using Ubuntu 7.04.

I got postfix working, sending emails using my ISP smtp server. I also installed Dovecot Server using this tutorial: [https://help.ubuntu.com/7.04/server/C/dovecot-server.html](https://help.ubuntu.com/7.04/server/C/dovecot-server.html) to setup pop3.

I can view emails in pine on my machine, but I want to be able to check the emails using an email program like thunderbird from other computers.

What is the pop3 server value I should use in thunderbird ?

pop3.csmonkey.com doesn't work, I'm sure how to set it up.

Any help is appreciated.

Thanks,
tarek

---

### Post by Mr. C. on 2007-06-13
The server name you enter depends on how you setup your host names for your systems.

If you add pop3.csmonkey.com to the hosts file (either windows or *nix), you can use host names.  Or if you run your own DNS server, you can use host names.  Otherwise, use the IP address of your POP3 server.

MrC

---

### Post by tarek on 2007-06-13
What's the IP address of my pop3? is it the same as the computer IP?

---

### Post by Mr. C. on 2007-06-13
I think you took me literally.  Services like pop3 do not have IP address - only network interface cards have IP addresses.  The IP address for your pop3 server is the same as what you are calling the machine's IP address (more correctly, its the IP address configured for the interface you are connected to, and that the pop3 server is listening on).

MrC

---

### Post by tarek on 2007-06-13
Thanks for the fast reply.

I should have explained more, in the domain settings I have mydomain.com uses an A address which is my IP. So if I just add a sub-domain such as pop3.mydomain.com and use an A address it will not work.

I got everthing working and the only problem is the domain setup. I don't have DNS installed.

Thanks,
tarek

---

### Post by Mr. C. on 2007-06-13
First...

When you connect from the WAN, you need to connect to the public WAN IP address provided by your ISP.  If you have a firewall, you need to port forward port 110 (POP) to the LAN IP address of the machine running the POP3 server.

When you connect from the LAN, you setup your email client to use the LAN IP address of the machine running the POP3 server.

Second...

If you want to use names like pop3.mydomain.com, you need to create an A record for pop3.mydomain.com, OR create an entry in your /etc/hosts file (or C:\Windows\System32\drivers\etc\hosts, the equivalent in Windows)

Otherwise, you must you the IP address as specified above.

MrC

---

### Post by tarek on 2007-06-13
I'm familiar with configuring the firewall, as I said I have everything setup, ports are open, I'm using the IP from my ISP, server is working. etc.

The problem is how to make thunderbird or other programs to understand that pop3.domain.com is a pop3 server not just an IP - A Address.

I tried the A address but it did not work, because the entery for an A address is just the IP without any ports therefore it simply forwars pop3.domain.com to the website not the pop3 server.

tarek

---

### Post by Mr. C. on 2007-06-13
pop3.domain.com is NOT a pop3 server.  It is just a hostname.  Period.  Networking applications call a name lookup routine to translate hostnames into IP address.  They do not communicate using hostnames.

You are very confused about hostnames, IP addresses and ports.  A records NEVER have ports.  They are just IP addresses.  An internet network connection (eg. a TCP/IP socket) is a PAIR of IP addresses / ports (one set for each side).  You configure your clients to connect on whatever port you desire.  If you are using the default 110 for POP, Thunderbird will already be configured for this - just enter the IP address of your server.

MrC

---

### Post by tarek on 2007-06-14
MrC, I understand what you are saying and that's the FIRST thing I tried but it did not work so I created this thread in search for another solution.

I will google *again* for other solutions, hopefully will find something.

I really appreciate your help.

Thanks,
tarek

---

### Post by Mr. C. on 2007-06-14
I'm not sure what else you're looking for.  It works the way I described.  Unless you can better describe exactly what is not working for you, there's not much else to go on.

Best of luck.
MrC

---

