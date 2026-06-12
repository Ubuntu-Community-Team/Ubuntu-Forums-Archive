---
title: "Upgrading from... 8.04."
date: 2009-10-30
forum: Server Platforms
---

### Post by GolemdX on 2009-10-30
Hi, I'm running Ubuntu Server 8.04 with Ubuntu Desktop 8.04 installed over-top of it.

First, my parents see a computer without a desktop environment as useless, but I don't want the WHOLE Ubuntu desktop installed, all I need is plain-old GNOME. Is there any way I can fully remove Ubuntu Desktop and replace it with GNOME?

Second, the IMPORTANT part, is how can I upgrade Ubuntu Server, and if Ubuntu Desktop is irremovable, how can I upgrade that too?

Basically, I want to know the order in which to do things to make the upgrade as smooth as possible.

---

### Post by GolemdX on 2009-10-30
Actually, NO desktop environment is needed anymore, I can just use webadmin and/or ssh.

---

### Post by hantechbl on 2009-10-30
I upgrade my computer by installing over the top of my current version.  After backing up.
Although this is not smooth it works.

---

### Post by cariboo on 2009-10-30
If you want to upgrade to a newer version, depending on how far you want to go, you'll have to do it in steps.

```
8.04-->8.10-->9.04-->9.10
```

The other option is to do a clean install of the version you want to use.

---

### Post by GolemdX on 2009-10-30
What about removing ubuntu desktop?
Also, can I upgrade VIA command or do I need discs?

---

### Post by zemon_ on 2009-10-31
```
sudo do-release-upgrade
```

---

### Post by slakkie on 2009-10-31
> **GolemdX said:**
> What about removing ubuntu desktop?
Also, can I upgrade VIA command or do I need discs?

If you want to remove all ubuntu-desktop deps you need to do some bit of work:

```

sudo aptitude markauto $(apt-cache depends ubuntu-desktop | egrep -v "Conflict|Replaces" | sed -e 's/[<>]//g' | tail -n +2| awk '{print $NF}')
sudo aptitude remove ubuntu-desktop

```

You would then need to have a look at left-over gnome packages:

```

dpkg -l | grep gnome | awk '{print $2}'

```

And remove these too. 
```

aptitude remove $(dpkg -l | grep gnome | awk '{print $2}')

```

You could replace remove with markauto. 

For upgrade possibilities, please have a look in my sig.

---

### Post by GolemdX on 2009-11-03
Removing Desktop was fine, but after the upgrade from 8.04 to 8.10 I get the error:

```
ata2: SRST failed (errno=-16)
Gave up waiting for the root device.
ALERT! /dev/disk/by-uuid/ea2d2361-1f40-48a3-ba76-7b53f2764abf does not exist. Dropping to a shell!

BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu7) built-in shell (ash)
(initramfs)
```

...the rest is generic or irrelevant...

So now I'm stuck at a shell and Ubuntu won't boot any longer. :(

---

