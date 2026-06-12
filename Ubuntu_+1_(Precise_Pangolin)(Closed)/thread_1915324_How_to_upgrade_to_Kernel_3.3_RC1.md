---
title: "How to upgrade to Kernel 3.3 RC1"
date: 2012-01-26
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by CGriffiths86 on 2012-01-26
I'm fairly new to the Ubuntu scene and have upgraded my install from 11.10 to the current 12.04 build. I have noticed my battery life on my laptop seems to be shortened. On the 11.10 build I had the 3.2 kernel and the power fix for Sandy Bridge processors. I have read that the 3.3 kernel has a lot of good power fixes. What's the easiest way to upgrade to the 3.3 kernel? Terminal commands or what..?

---

### Post by G19star on 2012-01-26
> **CGriffiths86 said:**
> I'm fairly new to the Ubuntu scene and have upgraded my install from 11.10 to the current 12.04 build. I have noticed my battery life on my laptop seems to be shortened. On the 11.10 build I had the 3.2 kernel and the power fix for Sandy Bridge processors. I have read that the 3.3 kernel has a lot of good power fixes. What's the easiest way to upgrade to the 3.3 kernel? Terminal commands or what..?

I don´t know if you should upgrade to the 3.3 rc releases, if you are on 3.2 now i would leave it on that until 3.3 is stable.

---

### Post by coffeecat on 2012-01-26
Welcome to the forum, both of you.

@CGriffiths86, I'm sure you realise this, but it needs to be said. 12.04 is still in alpha. Even with your battery life issue, it is not a good idea to run 12.04 as your main system just yet.

I've moved this thread to the 12.04 testing forum.

---

### Post by elliotn on 2012-01-26
download the required .deb packages here 

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.3-rc1-precise/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.3-rc1-precise/) 

> linux-headers-3 .3.0 -030300rc1 -
generic-
pae_3.3 .0- 030300rc1.deb

linuxheaders-3.3.0-030300rc1_3.3.0-030300rc1.201201191835_all.deb

linux-image-3. 3.0 -030300rc1-generic-pae_3.3 .0-030300rc1.201201191835_i386. deb

and install them either with USC or command line

---

### Post by G19star on 2012-01-26
i&#7743; testing the 3.3 kernel now on my ubuntu 11.10, runs great needed tho mode-fie the nvidia installer, to make it compile but everything works great, some ACPI _pss issues trough but nothing big for my system.

So far great!:)

---

### Post by zika on 2012-01-26
Go to rc2... instead rc1...

---

### Post by mdurham on 2012-01-26
> **zika said:**
> Go to rc2... instead rc1...

How do you do that? I don't see an rc2

---

### Post by xyzzyman on 2012-01-26
If you use a 3.2 kernel from mainline deb's it doesn't have the sandy bridge fix backported. If you use 3.2's that come from ubuntu sources then it does. 

So far the power fixes for kernel 3.3 involve the 50+ patches intel submitted for ivy bridge. With that, if you are a new user you should stick with what works especially if you are already jumping into an Alpha build. Using kernel's not provided by ubuntu directly (Such as the mainline provided previously) you are losing AppArmor protection and things like ureadahead, etc... And if you are really up on testing the Alpha and want to "do your part" then testing the code from Ubuntu is important so they can fix any bugs that could wind up in the release edition.

---

### Post by zika on 2012-01-27
> **mdurham said:**
> How do you do that? I don't see an rc2
My mistake it is 3.2.2 [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2.2-precise/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.2.2-precise/") ...Sorry.
(I use daily so I did not look at numbers properly. I've only seen that yesterday new folder was opened at the bottom...)

---

### Post by mdurham on 2012-01-27
> **zika said:**
> My mistake it is 3.2.2 [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2.2-precise/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.2.2-precise/") ...Sorry.
(I use daily so I did not look at numbers properly. I've only seen that yesterday new folder was opened at the bottom...)
no worries

---

