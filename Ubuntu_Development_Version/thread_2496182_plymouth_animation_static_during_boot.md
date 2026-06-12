---
title: "plymouth animation static during boot"
date: 2024-03-17
forum: Ubuntu Development Version
---

### Post by Claus7 on 2024-03-17
Hello,

I have noticed that plymouth theme is static during the latest updates. This happens only during boot though, since during shutdown process is working fine.

Regards!

---

### Post by ajgreeny on 2024-03-17
For the past few days ISOs Xubuntu is no longer showing he plymouth screen at all but instead shows the text scrollinh that is not expected and did not appear until recently.

This has been solved in most of my KVM virtual installs simply by adding quiet splash to the **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"** which previously showed only the **""** without the words **quiet splash**, though in one of my many installs that has not brought back the large **Xubuntu** word but a small text version only of **Xubuntu 24.04** at boot but the expected large **Xubuntu** at shutdown

Any ideas? Perhaps this is a similar problem but on these two different DE versions, Ubuntu vs Xubuntu?

---

### Post by Claus7 on 2024-03-17
Hello,

> **ajgreeny said:**
> For the past few days ISOs Xubuntu is no longer showing he plymouth screen at all but instead shows the text scrollinh that is not expected and did not appear until recently.

This has been solved in most of my KVM virtual installs simply by adding quiet splash to the **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"** which previously showed only the **""** without the words **quiet splash**, though in one of my many installs that has not brought back the large **Xubuntu** word but a small text version only of **Xubuntu 24.04** at boot but the expected large **Xubuntu** at shutdown

Any ideas? Perhaps this is a similar problem but on these two different DE versions, Ubuntu vs Xubuntu?

all the time I had under /etc/default/grub file the option you mention. I still have it and I face the issue mentioned in the OP. Indeed I think that they might be similar, since there is a difference between boot and shutdown processes. Plymouth is working fine during shutdown, yet not during boot process. I'm on the same boat with you, since I have quiet splash option enabled.

Regards!

---

### Post by ajgreeny on 2024-03-18
Did your system (Ubuntu?) have the quiet splash enabled at installation? My Xubuntu didn't; I had to edit the file manually.

---

### Post by Claus7 on 2024-03-18
Hello,

> **ajgreeny said:**
> Did your system (Ubuntu?) have the quiet splash enabled at installation? My Xubuntu didn't; I had to edit the file manually.

I do not remember the last time this was enabled. It was there for years, I do not speak about a new installation. I remember many years ago that I was seeing a lot of text during boot and this was one of the solutions proposed. What I can tell for sure is that if it was there from the beginning, I had changed it once and reverted it back or I changed it to what it is now, once and for all. There is no saying that I had tampered with it though.

Regards!

---

### Post by ajgreeny on 2024-03-18
I think the plymouth problem on my systems has now righted itself, presumably from the normal updates which I try to do every day.
I have no idea what update may have been.

I also have a Ubuntu-Mate install, again using KVM/QEMU but I haven't booted that for a while, and it is incidentally a guest on a Xubuntu-24.04 full install.   I will check that as soon as possible to see if there is any plymouth problem in that and also whether or not the quiet splash option is shown in the grub configuration.

---

### Post by ajgreeny on 2024-03-21
I was wrong to say the problem had completely righted itself as I have one VM in KVM/QEMU which still does not display the plymouth animation, though all the others work as they should, including the Mate version which I had not booted for a long time.

---

### Post by Claus7 on 2024-03-22
Hello,

I tried a new iso the other day, which I didn't install in the end. Yet, during boot of the iso, the original ubuntu theme wasn't static. In between, using my system, I saw a non static ubuntu text once, and all the rest boot attempts resulted in the same situation: a static plymouth theme.

Thanks of updating this, because in my case I didn't see an improvement.

Regards!

---

### Post by Claus7 on 2024-04-28
Hello,

checking a little bit more the issue the results are the following: selecting the solar theme results in an "endless" text even if the quiet splash string exists in grub. I tried to change the theme and the text disappeared. So I think that the problem lies with the theme. The problem is during boot only. I tested also some themes from gnome-look.org and they are working as normal.

Regards!

---

