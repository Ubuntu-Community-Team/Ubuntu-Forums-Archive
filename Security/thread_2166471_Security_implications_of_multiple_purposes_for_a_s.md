---
title: "Security implications of multiple purposes for a server"
date: 2013-08-09
forum: Security
---

### Post by SchnappiJedi on 2013-08-09
Hi,

I am concerned about using a single server as a web server (including hosting MySQL databases), email server, ssh server (for tunneling), in addition as a file share server on a LAN.

My biggest concern are files in the /srv & home directory folders being accessible due to an SQL exploit or webserver hack allowing an attacker to gain elevated privileges and see/use the entire system. Assuming strong SSH security (I am not worried about an SSH attack) am I being overly concerned or does my concern warrant separate servers in most people's mind?

I know that using encrypted containers for files within server is always an alternative to using separate servers, but I am inquiring as to others thoughts if this is even a concern in the first place if physical and SSH security are not in question.

---

### Post by CharlesA on 2013-08-09
I would not us a server exposed to the internet for file sharing locally. I might be paranoid about it, but IMHO a web server is "expendable" in that, if you have backups, and can restore it from backups if/when it gets owned, you are fine because you haven't really lost anything.

If you have a file server get owned, the attacker would wipe out all your data, and depending on how often you backup your stuff, you might have lost a ton of information.

Even if I wanted to run a web server/email server/whatever off the same box as a File server, I would run it as a VM -KVM, OpenVZ, whatever, so there is a separation of services that way.

---

