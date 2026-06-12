---
title: "Running ubuntu in both vmware and physical."
date: 2009-10-30
forum: Virtualisation
---

### Post by birdman3131 on 2009-10-30
Ok I mess around with ubuntu every once in a while and just installed 9.10 64bit on my laptop.

What i would like to do is be able to run the same copy of ubuntu that i have installed on one of my partitions in a vm when i am in windows.

when i tried to do so by pointing vmware at the physical disk it goes to grub and goes past there and gets to a flashing login page.

Video of the flashing. [http://www.youtube.com/watch?v=6NvRtDROOvY](http://www.youtube.com/watch?v=6NvRtDROOvY) (I am not sure how long it takes for youtube to process so if you cant see it wait a few)

If i try to login it only gets about 1 out of every 5 letter presses. I could get my login name but with linux hidding password length i have no way of knowing if i am typing the proper password.


Any ideas on how to do what i am wanting?

---

### Post by lensman3 on 2009-10-30
I have moved a linux vmware XP client to and XP machine running vmware and installed the files. (Essentially a clone).  The XP OS was a legal copy which was then cloned.  The vmware XP "disks" that were copied worked on two different PCs.  I just copied the entire XP to a flash drive, went to the 2nd machine, and copied them back to the HD.  

Seems that what you want to do should work.

(Cloning of a running copy of XP should be scaring the **** out of M$ and all the software houses.  The cloned OS was long ago deleted).

---

### Post by birdman3131 on 2009-11-01
I can not find the bumping rules around here so if there are any could somebody let me know the specifics?


One other thing to add to my first post is that i did install the nvidia drivers for my video card. could that be what is causing the problems?

---

### Post by birdman3131 on 2009-11-02
bump

---

### Post by birdman3131 on 2009-11-04
bump

---

### Post by birdman3131 on 2009-11-04
bump

---

### Post by birdman3131 on 2009-11-05
bump

---

### Post by dcstar on 2009-11-06
> **birdman3131 said:**
> Ok I mess around with ubuntu every once in a while and just installed 9.10 64bit on my laptop.

What i would like to do is be able to run the same copy of ubuntu that i have installed on one of my partitions in a vm when i am in windows.
..........
Any ideas on how to do what i am wanting?

You are booting a system specifically configured (during install) to access physical hardware resources in a VM environment where it has no access to those resources - only very different VM resources.

If you want a VM of Ubuntu, install it properly inside the VM and - only if you are exceeding careful and accept all the risks of losing data - set up access to a separate (physical) /home partition that both can share.

And please put these sort of issues in the Virtualization forum where they belong (and have a better chance of being answered).

---

### Post by birdman3131 on 2009-11-07
> **dcstar said:**
> You are booting a system specifically configured (during install) to access physical hardware resources in a VM environment where it has no access to those resources - only very different VM resources.

If you want a VM of Ubuntu, install it properly inside the VM and - only if you are exceeding careful and accept all the risks of losing data - set up access to a separate (physical) /home partition that both can share.

And please put these sort of issues in the Virtualization forum where they belong (and have a better chance of being answered).

Understandable.

And I was unaware of there being a virtualzation forum. Ill try there. thanks for the heads up.

---

### Post by birdman3131 on 2009-11-09
bump. And thanks to the mod who moved this.

---

### Post by birdman3131 on 2009-11-13
bump

---

