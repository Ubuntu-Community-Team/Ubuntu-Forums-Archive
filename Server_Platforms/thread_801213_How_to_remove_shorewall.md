---
title: "How to remove shorewall"
date: 2008-05-20
forum: Server Platforms
---

### Post by virbonus on 2008-05-20
I'm pretty much a newbie. I installed Shorewall on Server 8.04 and now want to fully remove it. Can anyone tell me how?

---

### Post by cdtech on 2008-05-20
Shorewall is a great firewall, what is the reasoning?

sudo apt-get remove --purge shorewall

---

### Post by virbonus on 2008-05-21
Thank you.

Right this minute, because I don't know what I am doing, I don't want a firewall. I believe it is interfering with my ability to try to setup this machine remotely. I have two NICs in it and I can access it through either without Shorewall, but because I don't yet understand how to configure it to allow remote SSH access I just felt it easier to get rid of it, and then figure it out.

---

