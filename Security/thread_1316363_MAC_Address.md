---
title: "MAC Address"
date: 2009-11-05
forum: Security
---

### Post by littlebear on 2009-11-05
Is it ok to give out your MAC address in terms of my security so that someone can configure the wireless internet connection.

---

### Post by HermanAB on 2009-11-06
Howdy,

a. Your MAC address is in *every* packet anyway.
b. You can change the MAC with ifconfig.

The MAC address is a really bad way to do WiFi access control...

---

### Post by kevdog on 2009-11-06
How about the macchanger package?  I believe its in the repos

---

### Post by littlebear on 2009-11-06
OK I will go ahead and give out my MAC address then. Can you please let me know what the command is to get at the command prompt. Thanks.

---

### Post by QLee on 2009-11-06
[QUOTE=littlebear]Is it ok to give out your MAC address in terms of my security so that someone can configure the wireless internet connection.[/QUOTE]

The MAC address is a unique address that identifies your interface card. (Of course they can be spoofed as mentioned by HermanAB)

To answer you question, I think it depends somewhat on *who* that "someone" you mention is. If it is the system administrator, then as also mentioned by HermanAB, you can't hide it from them anyway and they may be going to use it to make DHCP always assign your system the same IP address on the network and that would be fine. 

On the other hand, someone else may be asking with less reasonable intent.

Generally speaking, it is not necessary to have the MAC address to successfully set up a wireless internet connection and a system admin can easily get it, so ask yourself, why is this "someone" asking for it and do I trust them? This is how to approach security, be skeptical.

---

### Post by i.r.id10t on 2009-11-06
The ifconfig command will display your MAC addy.

---

