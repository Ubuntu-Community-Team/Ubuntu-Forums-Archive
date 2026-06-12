---
title: "Update with apt-get update"
date: 2009-11-26
forum: Server Platforms
---

### Post by alaya.zied on 2009-11-26
Hi to all,
when I wanna to update my server, I do:
```
apt-get update
apt-get -u upgrade
```
but I see this message: The following packages have been kept back

what does this mean exactly ?

I see in the list 'linux-...' (I suppose the kernel).

Some google search, I found only upgrade or dist-upgrade.
I don't need to upgrade to the next release (I have ubuntu server 8.04).

---

### Post by redelek on 2009-11-26
This happens on ubuntu.
Try to 
```
apt-get dist-upgrade
```
This should help


Best regards
Redelek

---

### Post by alaya.zied on 2009-11-26
thx redelek,
but I need to understand why and how ?
I have a real server here and it's not about my personal computer.

---

### Post by slakkie on 2009-11-27
Hi, please see here what it means:

[http://ubuntuforums.org/showthread.php?t=1286309](http://ubuntuforums.org/showthread.php?t=1286309)

The short version, one of the packages has a dependency which is unmet and will therefor not be installed.

You could run aptitude -s install <package> on all of the packages to see what it wants to do. Or similarly, aptitude -s full-upgrade. This will not execute the action, but simulate it. 

On stable releases the impact is quite low, it should not break anything, on development releases it could be quite harmful. Simulate the action and see what it does, if it looks sane, execute as action without simulating it (remove the -s flag).

---

### Post by alaya.zied on 2009-12-01
thank you very much slakkie :)

---

