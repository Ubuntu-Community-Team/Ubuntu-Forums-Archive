---
title: "External monitor resulution"
date: 2009-10-03
forum: System76 Support
---

### Post by perce on 2009-10-03
I would like to buy an external monitor for my office - a big one possibly- but I could not get any monitor I have tried to display a resolution better than 1200 x 1048, even if my graphic card is apparently capable of doing better than that. Has any Darter 1 owner been able to do better? I will appreciate your advice.

---

### Post by thomasaaron on 2009-10-05
Perce,

I just ran into that problem with a Starling (which has basically the same graphics card as your DarU1.

Try booting with the monitor plugged in. Then try going to Prefs > Display and turning off the ext monitor, clicking 'Detect' and re-enabling it. Did that work?

---

### Post by thomasaaron on 2009-10-05
Perce,

If the above doesn't work, please post the output of...

cat /etc/X11/xorg.conf

---

### Post by Eyore15 on 2009-10-05
> **thomasaaron said:**
> Perce,

If the above doesn't work, please post the output of...

cat /etc/X11/xorg.conf

is that the same file I can use to find out what those two error messages are when I turn my machine on?

On topic -- I can't get my external monitor to work if I boot with the device plugged in.  Once I've booted, I can plug in the (in my case video projector) device.  Then if I "hit" "cntrl +f3" several times, the projector will receive a signal at can lock to.

tnx

mcm

---

### Post by jdb on 2009-10-05
> **Eyore15 said:**
> is that the same file I can use to find out what those two error messages are when I turn my machine on?



Everything that comes out on boot doesn't make it to the logs, but a lot of it does.
dmesg prints out a lot of the stuff that comes out on boot.

Piping dmesg to less allows you to page through it.
In less type h to get help.
```
dmesg | less
```

The logs are located in the /var/log directory.
To see whats there:
```
ls /var/log
```

Most of the logs don't have user read permissions so you have to use sudo to see what's in them.
For example:

```
sudo cat /var/log/messages | less
sudo cat /var/log/syslog | less
sudo cat /var/log/daemon.log | less
```

jdb

---

### Post by Eyore15 on 2009-10-05
> **Eyore15 said:**
> is that the same file I can use to find out what those two error messages are when I turn my machine on?

On topic -- I can't get my external monitor to work if I boot with the device plugged in.  Once I've booted, I can plug in the (in my case video projector) device.  Then if I "hit" "cntrl +f3" several times, the projector will receive a signal at can lock to.

tnx

mcm

i OBVIOUSLY MENT "FUNCTION f3

---

