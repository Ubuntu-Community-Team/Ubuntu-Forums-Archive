---
title: "About Ubuntu Server installation without graphic output?"
date: 2011-01-03
forum: Server Platforms
---

### Post by acastrolorenzo on 2011-01-03
Hi everyone,

I am trying to install Ubuntu Server on a tower with no graphic output (no graphic card, no graphic on the motherboard).

Then, I´ve solved two ways:

1. (What I wanna try): Take a graphic card "rent", just for the installation. And remove it after. 

2. Take the Server HD and install it on another computer, then replace.

Wich problems could have each option? :confused:

Thanks in advance!!

---

### Post by HugoSerrano on 2011-01-03
Hi.

Probably it wont boot. You will only get some beeps.

Regards :-)

Happy New Year!

---

### Post by acastrolorenzo on 2011-01-03
Mmm.. will look for the card when boot?

---

### Post by wgas on 2011-01-03
Installing the server on another computer and then moving the harddrive is not going to be a good move.

Putting a graphics card in installing then removing the graphics card would work.

Have a read of [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation) the Server and network installations section.

---

### Post by HugoSerrano on 2011-01-03
> **wgas said:**
> Installing the server on another computer and then moving the harddrive is not going to be a good move.

Putting a graphics card in installing then removing the graphics card would work.

Have a read of [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation) the Server and network installations section.


He don't need to do a network installation. Installing a graphic card will give him a way to do a local installation.

The problem is that when he removes the card, the BIOS will look for it and won't boot. Of course, it may happens that his BIOS wont do the check... only testing it... I never did that, so i'm just guessing the result! :-D

Regards!

---

### Post by LepeKaname on 2011-06-09
I have done that (#1). You can install it with a video card and then just remove it. It worked for me. However, if for some reason your BIOS is checking for it, and there is no way to disable that, then I think the best way is to buy a cheap-used one.

About #2, I would like to try that as well. Theoretically (correct me if I'm wrong) it should work, as linux does not install computer-specific drivers (unless you do). I gave a search and this come up (it worked): [http://ubuntuforums.org/showthread.php?t=891903](http://ubuntuforums.org/showthread.php?t=891903)

---

### Post by ZuOverture on 2011-06-10
#2 will work, if second pc hardware is similar to your server's hardware. This includes x86 or x64 processor (best is with equal amount of cores) and mainboard chipset. Though, this way is never 100% reliable, when pc's are not absolutely equal.

Personally, I'd voted for #1. You'll need that graphics card if your server someday will stop responding ssh.

---

