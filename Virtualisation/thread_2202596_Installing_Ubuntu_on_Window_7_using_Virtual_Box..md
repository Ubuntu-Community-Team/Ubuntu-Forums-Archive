---
title: "Installing Ubuntu on Window 7 using Virtual Box."
date: 2014-01-30
forum: Virtualisation
---

### Post by patrick26 on 2014-01-30
Hello,

       as my title says, I'm trying to install Ubuntu via Virtual Box. I used the following tutorial [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox) 
       to setup virtual box. However, when starting the machine, I got a nice black screen with nothing at all ever appearing.

       I'm aware this may not be a Ubuntu related problem, but I have simply no clue on how to solve this problem. Anyone can help me ?

---

### Post by sp-1070 on 2014-01-30
Hi i dont know about virtual box but i wrote this tutorial some time ago,
if you where to follow it im sure it will work and if it doesnt i will be able to help you.

[http://ubuntuforums.org/showthread.php?t=1646680](http://ubuntuforums.org/showthread.php?t=1646680)

---

### Post by mastablasta on 2014-01-30
give it a bit more video memorry maybe.
furthermore you are using the 64bit image. you need to enable 64bit CPU virtualisation in your BIOS/UEFI for it to work. you might also need to enable it in virtualbox. i forgot.
read more here: [http://en.wikipedia.org/wiki/X86_virtualization](http://en.wikipedia.org/wiki/X86_virtualization)
and here: [https://www.virtualbox.org/manual/ch03.html](https://www.virtualbox.org/manual/ch03.html)

or just use a 32 bit image ;-)

---

### Post by Elfy on 2014-01-30
*Thread moved to **Virtualisation**.*

---

### Post by patrick26 on 2014-01-30
Taking the 32 bits version has done the job :). 
Thanks a lot for the support!

...

How do I close the thread ?

---

### Post by TheFu on 2014-02-02
I don't do "tutorials", but I have written how to [ configure virtualbox for the best performance]("http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox"). Hope it helps.

---

