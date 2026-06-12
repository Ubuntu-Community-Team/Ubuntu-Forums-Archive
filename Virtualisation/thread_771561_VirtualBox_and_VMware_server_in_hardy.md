---
title: "VirtualBox and VMware server in hardy?"
date: 2008-04-27
forum: Virtualisation
---

### Post by guy.thingy on 2008-04-27
im thinking of booting my xp partition on [B]hardy x64

[/B]so before i begin installing i would to know if anybody has tested virtualbox or vmware on hardy x64 bit and got it working with no trouble..


thank you, mind my username lol.

---

### Post by Sand Lee on 2008-04-27
Please see the sticky thread on VirtualBox. I have tried and tested it, however, there is one critical problem - once you've virtualized your partition, you can't bring it back. :mad: It will only be able to boot in virtualbox and not natively. This is because of the amount of hardware virtualbox changes to your install - ide controllers, video adapters, even your CPU. 

Therefore I recommend trying out vmware - if been able to use an existing partition with no problem appearing afterwards on Hardy 32-bit. But, that's just my experience. I'm guessing your mileage will vary.

---

### Post by guy.thingy on 2008-04-27
the stick has nothing in it...but yeah um i guess ill dl vmware..

---

### Post by Sand Lee on 2008-04-27
Sorry, I've just updated it. I wonder if it still isn't up? :confused:

---

### Post by fjgaude on 2008-04-27
This could be your ticket to ride, and it's up-to-date:

[http://ubuntuforums.org/showthread.php?p=4816827#post4816827](http://ubuntuforums.org/showthread.php?p=4816827#post4816827)

Message #3, does it for me and others with 64 and 32-bit Ubuntu.

---

### Post by guy.thingy on 2008-04-27
its alright, i installed virtualbox and i made a new virtual machine, for some reason it didnt want to read my xp partition so yeha i made a new virtual machine and it works fine thx though :D

---

### Post by RWT711 on 2008-04-28
I just reinstalled Hardy 3X because I was testing virtualbox. What a nightmare. Every single time i loaded the ose-guest module for linux image 2.6.24-16 generic it took my sound drivers away completely. The hardware didn't even show up anymore and its on the mobo.... VMWARE hard as hell to install but solid as a rock.

---

### Post by Sand Lee on 2008-04-30
Please take a second look at the thread; the problem has been fixed.

---

