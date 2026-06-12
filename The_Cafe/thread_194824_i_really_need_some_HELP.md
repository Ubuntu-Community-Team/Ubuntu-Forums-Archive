---
title: "i really need some HELP"
date: 2006-06-12
forum: The Cafe
---

### Post by airzer0 on 2006-06-12
hey all first off as always UBUNTU ROCKS! ok so i am having a few major problems but i have narrowed it down to just a couple of questions. just to let you know where i am at. i run ubuntu breezy. in terminal i typed sudo apt-get dist-upgrade to upgrade to dapper. here are my problems 1. i have 2.6.16 kernel ,dapper and breezy as well as xp. when i updated to dapper i try to load into it and at the usplash screen it hangs on loading root drive then in about 5 min it drops to a bash console saying that tty is not loaded. went back to breezy and my xserver-xorg a long with some lib got deleted, no worries fixed that. but when i try to reload my nvidia driver i get "warning linux headers do not match kernel" i really don't want to have to reinstall ubuntu because i have put a lot of work into it and i have a lot of information i do not want to lose. so any help would be greatly appriciated. i know reinstalling is the quick answer, but there has to be a way i can fix it. i really want to use dapper im not sure what i did wrong. thank you for reading my long post

---

### Post by Ptero-4 on 2006-06-12
For the Nvidia drivers go back to the basic nv. Then remove your linux headers and nvidia drivers and reinstall your linux headers ensuring that the headers are from the same version as the kernel and finally reinstall the nvidia drivers.

---

### Post by airzer0 on 2006-06-12
ok thanks so i would type sudo apt-get remove "what" , idid some looking and a lot of people have had the same issues so breezy is fine with me but im sorry what do i need to type?

---

