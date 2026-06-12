---
title: "Problem installing XFCE?"
date: 2009-04-12
forum: Server Platforms
---

### Post by Nixie Pixel on 2009-04-12
Hi, this might be a silly question, but I was trying to add a lightweight GUI to my server for administration, but am having problems adding XFCE.

I've tried both aptitude and apt-get, but neither can find the xfce4 (or xfce) packages.

Is "sudo aptitude install xfce4" the wrong command here?

Thanks!

---

### Post by lykwydchykyn on 2009-04-12
- Have you enabled the universe repositories by editing /etc/apt/sources.list? xfce is in the universe repos.
- Have you done an aptitude update?

---

### Post by Nixie Pixel on 2009-04-12
Repositories are enabled.

However, it seems I can't resolve "us.archive.ubuntu.com," "archive.ubuntu.com," or "archive.canonical.com."

I have assigned the server a static IP address, and had given it the OpenDNS servers as nameservers in /etc/resolv.conf.  However, since I am using a router which pulls DNS info from the same servers, I tried assigning my router as the nameserver.  Neither has worked.

Sorry for the noobish questions, I'm new!

---

### Post by lykwydchykyn on 2009-04-13
What output do you get from:
```

host us.archive.ubuntu.com

```
And are you sure your network connection is working at all?  Can you ping google from the server?

---

