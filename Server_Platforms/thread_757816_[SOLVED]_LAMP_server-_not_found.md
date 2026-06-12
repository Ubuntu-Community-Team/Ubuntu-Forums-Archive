---
title: "[SOLVED] LAMP server- not found"
date: 2008-04-17
forum: Server Platforms
---

### Post by El Rogueo on 2008-04-17
Hi all, just got an old machine up and running with Gutsy server edition, but I've never done a server install of Gutsy so I'm having a bit of trouble

766MHz
312MB RAM
32GB hdd

I've gone through and installed LAMP and OpenSSH in the standard installation menu, and then I picked up Lynx, phpsysinfo, webmin, and webalizer through apt-get, but I'm having problems finding the server through the internets. Here's what happens:

my server is 192.168.2.10. Using [http://192.168.2.10](http://192.168.2.10) from another computer on the local network finds the computer. Using the computer's hostname (oldman) does not. Attempting to connect with [https://192.168.2.10](https://192.168.2.10) tells me to use the hostname ([https://oldboy.kicks-***.org](https://oldboy.kicks-***.org)) because the server is running OpenSSL, even though I've disabled it, which then fails to even find anyway.

Ideas?

I'm also willing to start from scratch using the forum tutorial if general opinion is that the business is too mucked up as-is

thanks

---

### Post by cdenley on 2008-04-17
How are you handling name resolution? Did you install a DNS server?

---

### Post by El Rogueo on 2008-04-17
I tried installing bind9 and configuring it using the guide here: 

[http://ubuntuforums.org/showthread.php?t=236093](http://ubuntuforums.org/showthread.php?t=236093)

but I'm not 100% sure how to configure it, or what it looks like when it's configured properly.

Is that what you mean, or is bind9 something completely different?

---

### Post by El Rogueo on 2008-04-17
purged bind9, reinstalled, and reconfigured, works fine

thanks for identifying the problem!

---

