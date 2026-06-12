---
title: "Anyone seeing a huge lag when using Log Out"
date: 2012-10-17
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by philinux on 2012-10-17
It seems to take ages, watch timing about 10/15 seconds.

I'd like to bug this if anyone else can confirm this.

I assume the package is lightdm ?

(in comparison alt sysrq k is instant.)

---

### Post by dino99 on 2012-10-17
Does not see it with nouveau on i386.
Have you installed the new nvidia version ? 
If that issue is new on your side, then we have got a new gdm; but i dont see why it should have changed the upstart job. Maybe check with pum.

---

### Post by philinux on 2012-10-17
> **dino99 said:**
> Does not see it with nouveau on i386.
Have you installed the new nvidia version ? 
If that issue is new on your side, then we have got a new gdm; but i dont see why it should have changed the upstart job. Maybe check with pum.

Dino, this is an acer 1410 so intel not nvidia.

---

### Post by dino99 on 2012-10-17
> **philinux said:**
> Dino, this is an acer 1410 so intel not nvidia.

hehe, you are invincible, im not ;)

---

### Post by philinux on 2012-10-17
> **dino99 said:**
> hehe, you are invincible, im not ;)

Lol. But do you see a lag when log out?

---

### Post by 67GTA on 2012-10-17
I'm seeing a definite lag when logging in or logging out with two nvidia machines. It takes 10-20 seconds. My i7/ Intel HD4000 laptop doesn't show this lag.

---

### Post by philinux on 2012-10-17
> **67GTA said:**
> I'm seeing a definite lag when logging in or logging out with two nvidia machines. It takes 10-20 seconds. My i7/ Intel HD4000 laptop doesn't show this lag.

Ok login on this intel netbook is much quicker than logging out. Something must be hanging.

---

### Post by 67GTA on 2012-10-17
I've noticed the last thing to happen is the network manager icon showing up as soon as lightdm finally loads. Maybe network manager is hanging?

---

### Post by Frogs Hair on 2012-10-17
I saw this with one kernel update but that was replaced the next day and it seemed to only affect the XFCE session. There was a process not terminating. I have also changed Nvidia drivers from current to the experimental because I was seeing text during logout and shutdown.

---

### Post by philinux on 2012-10-17
Partly solved.

In startup apps I turned off:-
at-spi
backup monitor
bluetoothe manager
chat
gwibber
onboard
orca
ubuntu-one

Non of the above I need to be auto running. Logout is now back to "normal".

---

