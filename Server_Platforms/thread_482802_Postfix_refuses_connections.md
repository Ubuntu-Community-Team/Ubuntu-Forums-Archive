---
title: "Postfix refuses connections?"
date: 2007-06-24
forum: Server Platforms
---

### Post by BroadArrow on 2007-06-24
I am trying to set up a new Postfix installation. 

I'm able to telnet to the Postfix server as follows:

> [samuel@samuel ~] telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 samuel ESMTP Postfix (Ubuntu)

But if I try telneting to it from another computer on the network I get:

> [zev@zev ~] telnet samuel 25
Trying 192.168.0.3...
telnet: Unable to connect to remote host: Connection refused

192.168.0.3 is the right IP address for the mail server and the Firestarter firewall on it is set to all all traffic on the local network and isn't showing that it is blocking a port 25 connection so I'm thinking that it might be Postfix rather than something else on the system refusing the connection? Or have I missed something?

---

### Post by phar0z on 2007-06-24
I think I'm seeing what is wrong :)

When you are trying to contact your mailserver at your server:

[samuel@samuel ~] telnet localhost 25
Trying 127.0.0.1...

You see? Postfix only works at your localhost (127.0.0.1) 
it's not binded to your 192.168.0.3 local IP

So you have to modify the mynetworks line in /etc/postfix/main.cf

In Your case it should look like:
mynetworks = 127.0.0.0/8, 192.168.0.3

Please make sure your local IP (=192.168.0.3) is static.

---

### Post by MJN on 2007-06-24
> **phar0z said:**
> When you are trying to contact your mailserver at your server:

[samuel@samuel ~] telnet localhost 25
Trying 127.0.0.1...

You see? Postfix only works at your localhost (127.0.0.1) 


This isn't right, the 'Trying 127.0.0.1' line is simply the result of the local lookup of 'localhost'. The /etc/hosts file of course contains the mapping from localhost to 127.0.0.1. It's an output from telnet, not Postfix.

Mathew

---

### Post by BroadArrow on 2007-06-24
That did it! Thanks!

Bit odd that the IP addresses of all network cards aren't in there by default...

Obviously I'm a newbie to mail servers... :-)

---

### Post by MJN on 2007-06-24
<duplicate post deleted>

(Good to see you're sorted BTW!)

---

### Post by BroadArrow on 2007-06-24
> **MJN said:**
> This isn't right, the 'Trying 127.0.0.1' line is simply the result of the local lookup of 'localhost'. The /etc/hosts file of course contains the mapping from localhost to 127.0.0.1. It's an output from telnet, not Postfix.

Interesting. Maybe I changed something else as well when restarting Postfix! At least it's working!

My next task is to get SSL working for Postfix and Dovecot. It didn't work out of the package so they're both running without at the moment -- but only for local mail behind my router's firewall.

---

### Post by MJN on 2007-06-24
Oh no, the mynetworks change may have done the trick - I was just pointing out that the 'Trying 127.0.0.1 ....' line is a result of the lookup of the connecting name and not indicative of what interface Postfix is listening on.

Mathew

---

### Post by phar0z on 2007-06-24
In your case  this would be an excellent /etc/hosts file 

127.0.0.1       localhost
192.168.0.3   localhost, samuel

---

