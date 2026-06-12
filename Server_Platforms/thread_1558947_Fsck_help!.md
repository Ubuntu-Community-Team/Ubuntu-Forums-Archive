---
title: "Fsck help!"
date: 2010-08-22
forum: Server Platforms
---

### Post by baudday on 2010-08-22
I really need help with this. This is the 2nd time this has happened to me and I have no idea what causes it or how to fix it.

I installed Ubuntu Server on my system using this guide. [http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-3-p2](http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-3-p2). 

I have a RAID5 setup.

So after installing, I had to reboot for something and after I did I got something saying fsck... don't really remember the rest. I made a thread about it on here and no one could help me. So I reinstalled basically hoping it wouldn't happen again.

So after a new install, my server had been running for about 4 days. Today when I ssh'd to it, it said there was an update that needed to be applied so I should reboot. So I backed everything up and rebooted. And of course I got the same fsck bull. I really don't know what to do because if this is how it's gonna be, I just don't see it working. 

I'm really hoping someone can help me out this time, I would hate to have to reinstall again. If you need more info, I'll be watching this thread like a hawk, so just let me know.

---

### Post by amauk on 2010-08-22
without knowing the actual messages, it's going to be impossible to debug

but, fsck is just the filesystem checker
and shouldn't be anything to worry about
have you actually let it do a check?

---

### Post by baudday on 2010-08-22
```
fsck from util-linux-ng 2.17.2
/dev/md1: clean, 74060/8724480 files, 965799/34867168 blocks
```

That's the message I got last time. I'm not at the server, but it should be near the same. Last time I tried to let it go, but it literally was sitting on the check for hours if not a day.

---

### Post by CharlesA on 2010-08-22
Make sure the RAID array is mounting correctly.

Hit "s" and see if it proceeds.

---

### Post by baudday on 2010-08-22
THAT WAS IT!! Thank you so much! Could you maybe explain why it may not be mounting properly and how I can avoid this next time I have to reboot? Thanks again!

---

### Post by CharlesA on 2010-08-22
I don't know. If you've got physical access to the machine, boot to the grub menu and add "splash" to the kernel options and see what errors it displays.

Also, please post the output of these commands:

```
sudo fdisk -l
```

```
cat /etc/fstab
```

```
mount
```

---

### Post by baudday on 2010-08-22
Awesome. Will do. I'm so happy this is resolved now. I can't believe I did a complete reinstall last time when I just had to hit "S". Haha, oh well I guess since I didn't have anything on the server at that time, I didn't mind.

---

### Post by CharlesA on 2010-08-22
The problem was that it uses plymouth to display error messages (splash screen) instead of just displaying them in a terminal. =/

To see the errors you need the splash screen enabled.

---

