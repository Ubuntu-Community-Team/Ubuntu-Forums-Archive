---
title: "Video Driver Problems"
date: 2013-02-05
forum: Ubuntu Development Version
---

### Post by chenriques on 2013-02-05
Hi,

I've been using Ubuntu 13.04 for two weeks and it was running great.
Yesterday I had the stupid idea of installing nvidia-310 drivers and everything went bad.
I managed to access the terminal and I ran these commands to uninstall nvidia-310 and install nouveau:

```
sudo apt-get remove --purge nvidia-*
sudo rm /etc/X11/xorg.conf #if file does not exit is OK#
sudo apt-get install nvidia-common ubuntu-desktop
sudo apt-get install --reinstall xserver-xorg-video-nouveau
sudo dpkg-reconfigure xserver-xorg
```

After this my laptop was at least usable, my it's not like it was before the nvidia driver installation.
Mostly I have some mouse pointer flickering that is really annoying.

How can I configure Ubuntu video drivers like it was in the original setup?

PS: I'm in a laptop with Intel integrated HD4000 and a nVidia GT650M.

Thanks.

---

### Post by chenriques on 2013-02-05
I think the problem is with my xorg.conf file.
Anyone knows the correct config?

I'm using the nouveau driver, nvidia GT650M, 1920x1080 resolution.

---

### Post by Harry33 on 2013-02-06
> **chenriques said:**
> I think the problem is with my xorg.conf file.
Anyone knows the correct config?

I'm using the nouveau driver, nvidia GT650M, 1920x1080 resolution.

You do not need a xorg.conf file nowadays anymore.

---

### Post by Yellow Pasque on 2013-02-06
For reference, installing the nvidia driver directly on an Optimus system is much more likely to result in borkage than 3D bliss. Here's how you do it (but PPA is not made for Raring yet, so don't do this now): [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

Can you post /var/log/Xorg.0.log ?

---

### Post by chenriques on 2013-02-06
> **Harry33 said:**
> You do not need a xorg.conf file nowadays anymore.

But the system is still processing this file, because if I change it's content something happens..


> **Temüjin said:**
> For reference, installing the nvidia driver directly on an Optimus system is much more likely to result in borkage than 3D bliss. Here's how you do it (but PPA is not made for Raring yet, so don't do this now): [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

Can you post /var/log/Xorg.0.log ?

Before installing nvidia-310 (with RR fresh install) everything was working perfectly.
When I get back to home I'll post that file. Thanks.

---

### Post by Harry33 on 2013-02-06
> **chenriques said:**
> But the system is still processing this file, because if I change it's content something happens..
...


I didn't say the system would not be using it.
It does use it, if it exists. And if there are errors in that file, the system will suffer.
But, the system will automatically detect drivers and use appropriate settings without the xorg.conf file too.

---

### Post by chenriques on 2013-02-06
Attached Xorg.0.log (compressed in zip file).

Thanks ;)

---

### Post by Yellow Pasque on 2013-02-06
It's using a generic frame-buffer driver when it should be using intel. Quite frankly, I'm not sure what you did to get it to behave like that. You did delete the /etc/X11/xorg.conf file, correct?

Also, is there a reason you're using Ubuntu 13.04? It would be a lot easier for you if you used Ubuntu 12.10 and followed the bumblebee instructions...

---

### Post by alphacrucis2 on 2013-02-06
On my Lenovo laptop which I dual boot, I ended up disabling Optimus. Seems to be more trouble than its worth. Even Windows seems to be better off running the Nvidia driver all the time.

---

### Post by Yellow Pasque on 2013-02-06
> **alphacrucis2 said:**
> On my Lenovo laptop which I dual boot, I ended up disabling Optimus. Seems to be more trouble than its worth. Even Windows seems to be better off running the Nvidia driver all the time.
Running everything with the nvidia GPU will decrease battery life...

---

### Post by chenriques on 2013-02-06
I think the problem is solved.
Following Harry33 idea that it shouldn't use xorg.conf at all, I've deleted it and rebooted the laptop.

The stupid thing is that Ubuntu then start with the lowest resolution possible. I manage to get to the display settings and change the resolution to 1920x1080, although I couldn't see tha apply button at all. After that everything is running smoothly again :)

I think it's using intel now. At least the "details app" shows this:

[IMG]http://i.imgur.com/LmZycoL.jpg[/IMG]


PS: I'm running 13.04 because didn't like 12.10 that much. Although RR is still in alpha, it's very stable, runs fast and I'm enjoying it. And it will get at least more 3 month of development, so this really promises. And I like to contribute and report some bugs.

---

### Post by alphacrucis2 on 2013-02-06
> **Temüjin said:**
> Running everything with the nvidia GPU will decrease battery life...

Hardly ever run off battery. It sits the majority of the time on a docking station running off mains power but I can see it might be an issue if you run off battery a lot.

---

