---
title: "Internet connection sharing not working after uninstalling firestarter"
date: 2006-02-08
forum: Server Platforms
---

### Post by RAZZ on 2006-02-08
Hi,

I just uninstalled firestarter, and now my Windows XP machines cant access the internet. It was working fine before I installed firestarter.

My setup is as follows:

ADSL modem---eth1 Ubuntu eth0---switch---XP mashines.

The Ubuntu machine is running dhcp3, and that seems to work correctly (gives IP witin set range). I can also ping both ways.

I hope that is all the info I need to give to make it easy to help. If not, bear with me, as I am new to both linux and networking.

Thank you in advance!

---

### Post by el3ktro on 2006-02-09
You need a firewall to be able to "share" your Internet connection. The Linux built-in firewall is called "Netfilter", and this firewall can be controlled by a program called "IPTables". Firestarter is just a nice GUI for this IPTables program. So either you have to know how to set up forwarding aka connection sharing in IPTables, or you install Firestarter again...

Tom

---

### Post by RAZZ on 2006-02-09
Hi Tom, an thank you for your reply.
In my slight panic attack, I guess I was just hoping for an easy "fix", since I had it working before I installed firestarter. Some one else is helping me setting up shorewall in another thread, but it is nice to know that it was to be expected, and why.
Thanks again!

---

