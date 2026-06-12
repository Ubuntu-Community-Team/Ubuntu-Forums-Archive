---
title: "Can't upgrade or remove anything because a driver is not fully installed"
date: 2019-11-08
forum: Ubuntu/Debian BASED
---

### Post by pokspell on 2019-11-08
Hello friends!

i have a problem with my ubuntu.
In fact, i install the driver for my video card (amdgpu-core), but because my ubuntu was in 19.04, it didn't fully installed.

So, i restart my computer at forst to see if it would be correct, and then the problem come.
When booting, i got the message "pkcs#7 signature not signed with a trusted key" 5 times and then just waiting here...
So i go in cli mode ans checking, with help of plenty of forum, what could be the problem and how to fix it.

I decided to downgrade my ubuntu to 18.04 to be able to fully install the amdgpu-core, BUT, when i want to do "sudo apt upgrade", i got dependencies problem,
because the driver is not install...
So, i did "sudo apt --fix-broken install" and the install don't occure because my version of ubuntu is at 19.04, not 18.04...

So i'm stuck here, can't remove the driver neither because it's not fully installed :/ (the computer says to do the "sudo apt --fix-broken install" to be able to remove correctly)


What do i do? or what should i do?

Thank for you help and have a nice day!

(Hope my english is correct, my first language is French ^^')

pokspell

---

### Post by pokspell on 2019-11-08
I finally resolve the problem...
The topic can be close!

Have a nice day!

---

