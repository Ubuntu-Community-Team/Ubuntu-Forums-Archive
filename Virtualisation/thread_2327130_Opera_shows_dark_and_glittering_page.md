---
title: "Opera shows dark and glittering page"
date: 2016-06-07
forum: Virtualisation
---

### Post by arunck on 2016-06-07
Hi

I recently installed Ubuntu on VirtualBox in my Windows 10 system. Surprised to find Opera was not in the repository (returning to Ubuntu after few years) and installed from the .deb file downloaded from Opera site (version 37, stable). But when I open Opera, it just shows a blank page with glittering page where nothing is visible (even pointer or menu). I tried to take screenshot of the application but strangely only the desktop was shown and not the Opera app.

The same behavior was see on the Amazon app installed with Ubuntu. It too shows only a blank-flickering screen with nothing else visible.

Can someone help??

Thanks!

---

### Post by X-RED_Tech on 2016-06-08
Opera was never in the Ubuntu official repositories: [https://help.ubuntu.com/community/OperaBrowser](https://help.ubuntu.com/community/OperaBrowser)

---

### Post by howefield on 2016-06-08
Thread moved to the "*Virtualisation*" forum.

Just checking that you have installed the guest additions which provide better drivers than the default, including video graphics support.

> **X-RED_Tech said:**
> Opera was never in the Ubuntu official repositories: [https://help.ubuntu.com/community/OperaBrowser](https://help.ubuntu.com/community/OperaBrowser)

Hmm, off topic of course, but I seem to remember at one time Opera was installable with Add/Remove Software.

---

### Post by arunck on 2016-06-08
Yes, I've installed Guest Additions from Virtual box.

I agree with you on Opera being available in Ubuntu repository.

---

### Post by vasa1 on 2016-06-08
> **arunck said:**
> ... Surprised to find Opera was not in the repository (returning to Ubuntu after few years) ...
If an application is part of the repository, its man page should be available online. [Ubuntu's man pages]("http://manpages.ubuntu.com/cgi-bin/search.py?q=opera&op=&cx=003883529982892832976%3A5zl6o8w6f0s&cof=FORID%3A9&ie=UTF-8") for 12.04 and later come up empty for Opera. Opera's Presto engine was not open source and it's extremely unlikely that Opera was ever "in the repository". Of course, you may have installed a ppa and that way got the impression that Opera "is in the repository". Related reading:
[https://help.ubuntu.com/community/OperaBrowser12](https://help.ubuntu.com/community/OperaBrowser12)
[https://help.ubuntu.com/community/OperaBrowser](https://help.ubuntu.com/community/OperaBrowser)

---

### Post by MAFoElffen on 2016-06-10
Back to the display issues of Opera and Amaozon... 

You said you installed Ubuntu as a VM Guest, but did not mention which version. Desktop Editition, 16.04 LTS?

Next, with version of VirtualBox are you running in Windows? Because the Guest Additions stop back around version 4.2, 4.3... Not is the Extension Pack.

Then, what do you have allocated for VM memory, Video memory and other video settings for the VM Guest?

How much memory and what is your GPU on the Host machine?

Your comment on "glittery" reminds me of a low memory condition, therefore what steered those questions to you...

---

