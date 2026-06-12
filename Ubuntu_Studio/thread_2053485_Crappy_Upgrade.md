---
title: "Crappy Upgrade"
date: 2012-09-05
forum: Ubuntu Studio
---

### Post by Lucius Ferus on 2012-09-05
I upgraded my Ubuntu Desktop 12.04, 32bit, to ubuntu-studio full install. Received the packages and they were installed; after i tried this :     sudo apt-get install linux-rt     , were "no such file or directory" i guess is normal hence is related to Karmic.   After i achieved audio and video configurations. Everything should be OK. Although, when i'm using VLC i get playback interruptions when opening directorys or aplications. It doesn't suspend either when not in use for a long period of time, it's configured for 10 min. I don't have the ubuntu studio theme either on system settings- appearence.
I should remark that i attempted the install of linux kernel 3.5 ( it was 3.2) and didn't finished it couldn't go beyond step " make menuconfig", or the one just after. This was a forthnignt before the upgrade, but everything was working fine.
I don't know what i'm doing wrong. If i've no better solution, i'll do a fresh install on another partition, from ubuntu-studio DVD.:guitar:

---

### Post by sgx on 2012-09-05
Hi, the 'free' $pricetag for linux has the hidden cost
that upgrades work sometimes, and sometimes problems are abundant.

Since a fresh full install of linux and apps is easy, compared to
installing windows and reinstalling commercial apps, it's often
better to use the clean slate.

Include a separate /home partition, so you can keep personal settings and data from being formatted off the map, in future installations.

Cheers

---

### Post by smartboyhw on 2012-09-06
> **Lucius Ferus said:**
> I upgraded my Ubuntu Desktop 12.04, 32bit, to ubuntu-studio full install. Received the packages and they were installed; after i tried this :     sudo apt-get install linux-rt     , were "no such file or directory" i guess is normal hence is related to Karmic.   After i achieved audio and video configurations. Everything should be OK. Although, when i'm using VLC i get playback interruptions when opening directorys or aplications. It doesn't suspend either when not in use for a long period of time, it's configured for 10 min. I don't have the ubuntu studio theme either on system settings- appearence.
I should remark that i attempted the install of linux kernel 3.5 ( it was 3.2) and didn't finished it couldn't go beyond step " make menuconfig", or the one just after. This was a forthnignt before the upgrade, but everything was working fine.
I don't know what i'm doing wrong. If i've no better solution, i'll do a fresh install on another partition, from ubuntu-studio DVD.:guitar:

Best answer: There is NO rt for 3.5. Only 3.4:(

Next time when you do the upgrade please use 3.2...

---

### Post by Lucius Ferus on 2012-09-07
> **smartboyhw said:**
> Best answer: There is NO rt for 3.5. Only 3.4:(

Next time when you do the upgrade please use 3.2...

Cheers anyhow; though my kernel was still the 3.2 after the upgrade, and by the way generic too. So by one of your last comments, get me one of those low latency ones, please. It's true i don't understand much about this. But seem's like Kernel there's just one, maybe with low latency improvements on studio install.
Sorry i'm only 41.

---

### Post by Lucius Ferus on 2012-09-07
> **sgx said:**
> Hi, the 'free' $pricetag for linux has the hidden cost
that upgrades work sometimes, and sometimes problems are abundant.

Since a fresh full install of linux and apps is easy, compared to
installing windows and reinstalling commercial apps, it's often
better to use the clean slate.

Include a separate /home partition, so you can keep personal settings and data from being formatted off the map, in future installations.

Cheers
Thank'you. Seem's the best after all.

---

### Post by smartboyhw on 2012-09-07
> **Lucius Ferus said:**
> Cheers anyhow; though my kernel was still the 3.2 after the upgrade, and by the way generic too. So by one of your last comments, get me one of those low latency ones, please. It's true i don't understand much about this. But seem's like Kernel there's just one, maybe with low latency improvements on studio install.
Sorry i'm only 41.

Well you clearly HAD forgotten to ```
sudo apt-get install linux-lowlatency
```. Because if you don't install it it will still be generic even AFTER upgrade to Ubuntu Studio.

---

### Post by Lucius Ferus on 2013-02-11
OK;
Thank's to all.
Sorry i cannot attend the class, is too late. Should have came earlyer.
Just came back to mark the thread as solved.
bye.

---

