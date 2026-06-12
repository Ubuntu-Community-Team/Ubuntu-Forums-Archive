---
title: "Upgrade to Ubuntu 12.04"
date: 2012-03-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by silviutp on 2012-03-02
I want to upgrade to from 11.10 to 12.04 version of Ubuntu.
I tried to follow the instructions indicated here [https://help.ubuntu.com/community/PreciseUpgrades]("https://help.ubuntu.com/community/PreciseUpgrades")

I'm blocked at step 4. I have no "Release upgrade..." option in my update Update Manager. 
It cannot find any new distribution...

Any clues ?

---

### Post by Liova99 on 2012-03-02
Whery strange.... did you try to write on a terminal:
"sudo update-manager -d" ?? :-k

---

### Post by oldfred on 2012-03-02
Moved to Ubuntu +1 (Precise Pangolin).

It will not be shown as a normal upgrade until it is released, scheduled for April 26th. It still is beta and you should not be running it as your main system. 

I have not tried an upgrade, but if test on a second system some have posted how to test it.

If you just want to see how the beta works, it is best to allocate another 20GB for another / (root) partition and install to that. Then you have your working install when the beta breaks. You can also do a full install to a flash drive if you do not have room on your hard drive. 

I have a full install in a flash drive to test on my laptop and a full install in a new partition for my desktop, but boot 10.10 as my main systems on both computers.

---

### Post by silviutp on 2012-03-07
Thank you.
I will try on a different partition. You said it's best to have 20GB, what's the minimum space required ? 
I have one partition of 13GB.

---

### Post by coffeecat on 2012-03-07
A 13GB partition should be fine for testing a pre-release. A fresh installation takes between 2-3GB space so as long as you do not store too much personal data in the root partition you should be OK.

---

### Post by cariboo on 2012-03-07
The installer checks to see if you have a minimum of about 4.5GiB (I can't remember the exact figure at the moment) of empty space on your hard drive before it will continue, so you should be OK with a 13GiB partition.

---

### Post by scottbomb on 2012-04-01
> **Liova99 said:**
> Whery strange.... did you try to write on a terminal:
"sudo update-manager -d" ?? :-k

I'm running Xubuntu and I wonder if this will work for me. When I entered the above line in a terminal, Update Manager launches and tells me "New Ubuntu release '12.04 LTS' is available." Sounds good, but will this install the regular Ubuntu or will I keep my Xubuntu with just the underlying Ubuntu packages being updated?

---

### Post by scottbomb on 2012-04-02
Sorry, I think I just found the answer here. [Yes].
[https://www-admin.xubuntu.org/get](https://www-admin.xubuntu.org/get)

---

