---
title: "[SOLVED] How do we enable/disable demons on boot?"
date: 2008-12-14
forum: Server Platforms
---

### Post by PryGuy on 2008-12-14
Good day!
I have a question, how do we enable/disable demons on boot? I have X installed for instance and I do not want to start it on boot on my server. How do I disable it. I speak of CLI solution only of course.

---

### Post by Iowan on 2008-12-14
I'm sure there is a more elegant way - otherwise, you could edit the rcX.d directories. For example, change **[COLOR="Red"]S[/COLOR]10xserver-xorg-input-wacom** to **[COLOR="Blue"]s[/COLOR]10xserver-xorg-input-wacom** to disable it.  (Ideally, the "K" values should be changed in other runlevels.)

---

### Post by iponeverything on 2008-12-14
Install and run this nice little utility

```
apt-get install sysvconfig
```

run it with;

```
sysvconfig
```

---

### Post by PryGuy on 2008-12-14
> **Iowan said:**
> I'm sure there is a more elegant wayYep, that's what I'm talking about :)

So if I want to disable GDM I have to rename all links to gdm in all rcX.d dirs? Well, I've read that init during startup on Debian is a mess actually...

**iponeverything**, sysvconfig is a charm, thank you! I'll definitely take in on account. But there should be a basic tool for that. There should be config files for hand editing. I couldn't find them... :( How do we choose which runlevel to start in general?

---

### Post by PryGuy on 2008-12-14
[This article is cool]("http://www.cyberciti.biz/faq/prevent-xorg-from-starting-in-linux/"), people!\\:D/

The following line solved my problem:
```
sudo update-rc.d -f gdm remove
```
You can get gdm start on boot again with this:
```
sudo update-rc.d -f gdm defaults
```
[COLOR="Red"]**Use it only if you know what you do!**[/COLOR]

---

