---
title: "Is firestarter nescessary?"
date: 2010-08-22
forum: The Cafe
---

### Post by mamamia88 on 2010-08-22
I have it installed but don't know if it's really nescessary if I have a firewall built into my router?   any opinions?

---

### Post by earthpigg on 2010-08-22
your router alone is fine.

---

### Post by mamamia88 on 2010-08-22
so is there an easy way to remove the built in firewall in ubuntu?

---

### Post by CharlesA on 2010-08-22
Don't enable it?

Why you'd use firestarter, I don't know, especually since it's out of development.

---

### Post by terry_gardener on 2010-08-22
you can unistall firestarter because it is only gui to iptables which is the firewall.

ubuntu also has UFW installed by default.

---

### Post by mamamia88 on 2010-08-22
I use firestarter as an easy way to turn off firewall so port in transmission is open.  is there a way to globally disable it?

---

### Post by terry_gardener on 2010-08-22
yes using UFW 

guide at 
[http://ubuntuforums.org/showthread.php?t=823741]("http://ubuntuforums.org/showthread.php?t=823741")

---

### Post by mamamia88 on 2010-08-22
thanks alot it says that firewall disabled at system startup exactly what i needed thanks alot

---

### Post by beetleman64 on 2010-08-22
I wouldn't really bother with Firestarter. The Ubuntu firewall is almost certainly good enough and I wouldn't trust security software which won't have major bugs fixed.

---

### Post by 3rdalbum on 2010-08-22
> **beetleman64 said:**
> I wouldn't really bother with Firestarter. The Ubuntu firewall is almost certainly good enough and I wouldn't trust security software which won't have major bugs fixed.

Ubuntu has no open ports by default so you don't need a firewall anyway. Unless of course you have installed some software that listens to incoming ports.

---

