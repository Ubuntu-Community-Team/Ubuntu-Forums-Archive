---
title: "Please help to test dansguardian-gui 2.1"
date: 2009-08-10
forum: Ubuntu Christian Edition
---

### Post by david_kt on 2009-08-10
Please help to test dansguardian gui 2.1 attached. I have included custom firewall to replace firehol.

This is mainly to prepare for server edition, but I would replace the desktop edition also to use dansguardian gui 2.1.

DK

---

### Post by stlsaint on 2009-08-10
will do!!

---

### Post by stlsaint on 2009-08-10
alright...replaced desktop version and now using 2.1! tried a few basic settings and all seems well! change settings from 50 to 75, add a few to whitelist...blacklist etc, will update as i go!!

---

### Post by oneinch on 2009-08-10
I will give it a shot too and let you know.

---

### Post by david_kt on 2009-08-10
> **oneinch said:**
> I will give it a shot too and let you know.

Dansguardian gui 1.X is using firehol, all ports are closed.
Dansguardian gui 2.0 has no firewall, all ports are open.
Dansguardian gui 2.1 has firewall, but I have open below port:

- 80 (for web server)
- 22 (for ssh)
- 25 (for mail server)

If you are using torrent, you should:
1 Do a port forward on your router/modem
2 open the port the bittorrent client is using.

Otherwise, there would not be any incoming connection. It still work though.

DK

---

### Post by oneinch on 2009-08-10
David_kt:  What are you development goals for the dansguardian_gui? What are you wanting to achieve? I have an itch to hack it a little and help :D

---

### Post by david_kt on 2009-08-10
> **oneinch said:**
> David_kt:  What are you development goals for the dansguardian_gui? What are you wanting to achieve? I have an itch to hack it a little and help :D

It is for ubuntu ce server. With firehol, I am not sure how to open the port safely.

Now I have written a simple firewall rule for ubuntu ce, it should be able to give some protection for server and at the same time web, mail and ssh service is available as well.

I have uploaded dansguardian gui 2.1 for default setting in ubuntu ce this morning. If everything is alright, I would soon release ubuntu ce server beta.

DK

---

### Post by oneinch on 2009-08-10
> **david_kt said:**
> It is for ubuntu ce server. With firehol, I am not sure how to open the port safely.
DK

Are you wanting to configure the firewall to when it is installed it comes configured with the services you want to run already open, or are you talking about opening and closing ports from dansguardian_gui kind of like on the fly?

---

### Post by david_kt on 2009-08-10
> **oneinch said:**
> Are you wanting to configure the firewall to when it is installed it comes configured with the services you want to run already open, or are you talking about opening and closing ports from dansguardian_gui kind of like on the fly?

I think I will leave 3 ports open to simplify the script. Later on if it is really necessary to close those 3 ports when not in use I will add the feature.

User experience is one aspect of closing and opening the ports. It is not convenience.

Put it this way, windows is so much vulnerable and yet many people are using it, that is because it is easy to use. So, I think it is not necessary to make it very safe but become annoying to use.

What is change on hte fly is transparent proxy only. When you disable dansguardian, transparent proxy is removed because you will not have internet connection if it is not removed. And when you enable dansguardian, transparent proxy is enable again. Regardless of dansguardian status, firewall is still on all the time.

Previously, firehol is also disable when dansguardian is disable.

DK

---

### Post by wildman4god on 2009-08-14
how well does this filter work, I want to use ubuntu or some form of Linux on my pc but I need to know if there is an effective filter for Linux, thats about the only thing keeping me on windows.

---

### Post by david_kt on 2009-08-14
> **wildman4god said:**
> how well does this filter work, I want to use ubuntu or some form of Linux on my pc but I need to know if there is an effective filter for Linux, thats about the only thing keeping me on windows.

[http://mirror.dansguardian.org/?page=dgvssg](http://mirror.dansguardian.org/?page=dgvssg)

DansGuardian is the very best web content filtering engine available and; this is why SmoothWall uses the DansGuardian filtering technology. They use the best web content filter around and make it easy to use and maintain, while giving their customers the highest possible level of support. DansGuardian is used to test leading-edge functionality and we have a good group of testers in the DansGuardian users. 

DK

---

