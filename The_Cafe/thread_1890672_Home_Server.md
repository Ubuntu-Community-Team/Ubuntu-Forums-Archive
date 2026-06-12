---
title: "Home Server"
date: 2011-12-04
forum: The Cafe
---

### Post by dRounse on 2011-12-04
I have a question about a home server, If you had a home server and you had it so you could access your files anywhere, could you make it so if you were at school you could sign onto your server instead of the schools? Because I have kinda heard of this but, for example, at my old school you would need to sign on through the web browser for internet access how would you get into your server without being undetected?

---

### Post by mikewhatever on 2011-12-04
If your home server is accessible from the internet (and not just from the home network), then you can log in from anywhere in the world.

PS: "without being undetected" = detected!

---

### Post by dRounse on 2011-12-04
> **mikewhatever said:**
> 

PS: "without being undetected" = detected!

Lol I missed that... I meant "without being detected"

---

### Post by mikewhatever on 2011-12-04
> **dRounse said:**
> Lol I missed that... I meant "without being detected"

Detected by who? Is there a school rule against having or accessing home servers?

---

### Post by Bachstelze on 2011-12-04
Short answer is probably not, because the firewall blocks all traffic to the Internet until you log in (and your home server is on the Internet side of the firewall).

---

### Post by dRounse on 2011-12-04
> **mikewhatever said:**
> Detected by who? Is there a school rule against having or accessing home servers?
I mean would I be able to access the internet and go on any site without them watching what I'm doing

---

### Post by LowSky on 2011-12-04
The best I can think of is using VPN software to establish a link to your home network. You would still be using the schools network but only to get info from your server so all traffic should be allowed. This means software and if it isn't your PC you wont be able to install any software to help you run the VPN.

The problem will be port access. Many ISP do not allow residential customers to use outgoing ports, you may need to upgrade to their business line if at all possible. Not to mention many since you will rely on the home network for sending you the data it will have to upload it to you, and that speed will be much slower than the usual download speed. For example my upload speed is only 5mbps versus the 15mbps i get for normal downloading. You may not even get a full upload speed due to network congestion at the place you are trying to access from. Sending and receiving at the same time could mean very high ping rates.

Last but not least. These Forums are not to be used for circumventing security features.

---

### Post by Lars Noodén on 2011-12-04
A lot of residential ISP actually do allow incoming connections.   You'll just have to [try](http://canyouseeme.org/) for yourself and see what is available.  A very secure way of providing access is to use SFTP.  It is built into the package OpenSSH-Server.  You can use either plain SFTP clients like Nautilus or fancier ones like SSHFS.

---

