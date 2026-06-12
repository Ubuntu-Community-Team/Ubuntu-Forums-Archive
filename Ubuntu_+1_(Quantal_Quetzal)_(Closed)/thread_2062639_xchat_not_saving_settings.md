---
title: "xchat not saving settings?"
date: 2012-09-25
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by ELD on 2012-09-25
So on 12.10 has anyone tested xchat? It seems to not save settings? I have to re-do my username on every launch.

---

### Post by Elfy on 2012-09-25
I've not had any trouble with it here at all - been using it for a long time in 12.10.

I did copy .xchat2 folder to get the logs from my 12.04

---

### Post by cariboo on 2012-09-25
We had a Forum Council meeting on Saturday, I used xchat with zero problems. I've been doing the same as Elfy, moving the xchat2 configuration file from one version to the next for the last couple of years.

---

### Post by ELD on 2012-09-25
Hmm what can I do to find out why my settings aren't being saved?

Mine seems to on every load revert to my ubuntu username, it saves my favourite servers and rooms though but not my username.

---

### Post by Elfy on 2012-09-25
Try manually editing them into .xchat2/xchat/conf before opening it

irc_nick1 = 
irc_nick2 = 
irc_nick3 = 

save and start xchat, close it and see what happens then iwth a restart

If you still get issues I can move my .xchat folder and see if I can confirm

---

### Post by mips on 2012-09-25
was working fine for me when I had 12.10 installed.

---

### Post by ELD on 2012-09-26
Thanks got it to work by editing the config file, no idea why it won't save when i use the gui?

---

### Post by Elfy on 2012-09-26
odd - glad you got it sorted, I'll have a look and see if a new install of it will save for me

---

### Post by ELD on 2012-09-26
The tray icon seems to dissapear after a while in Cinnamon 1.6 and gnome shell 3.6 as well very annoying.

---

### Post by Elfy on 2012-09-27
> **Elfy said:**
> odd - glad you got it sorted, I'll have a look and see if a new install of it will save for me
I did this, seemed to keep my details between instances without issue.

> **ELD said:**
> The tray icon seems to dissapear after a while in Cinnamon 1.6 and gnome shell 3.6 as well very annoying.
Can't help here I'm afraid other than - the icon works ok in Xubuntu.

---

### Post by philinux on 2012-09-27
> **ELD said:**
> Thanks got it to work by editing the config file, no idea why it won't save when i use the gui?

It's a bug. If you close xchat by hitting the X it will not save settings.

If you close it from the global menu xchat > quit it will save settings.

And it's an old bug. [https://bugs.launchpad.net/ubuntu/+source/xchat/+bug/851104](https://bugs.launchpad.net/ubuntu/+source/xchat/+bug/851104)

---

### Post by ELD on 2012-09-27
> **philinux said:**
> It's a bug. If you close xchat by hitting the X it will not save settings.

If you close it from the global menu xchat > quit it will save settings.

And it's an old bug. [https://bugs.launchpad.net/ubuntu/+source/xchat/+bug/851104](https://bugs.launchpad.net/ubuntu/+source/xchat/+bug/851104)

Any newer bugs? Any idea if anyone will actually fix it?

---

