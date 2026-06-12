---
title: "Can't boot to ubuntu 12.04 after upgrade"
date: 2012-03-19
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kakalos12 on 2012-03-19
Hello, I'm having a problem with ubuntu 12.04. 
I had installed ubuntu since alpha 2. (don't remember exactly but I remember it's kernel is 3.2.0.17). After some upgrade some days ago, it's kernel is 3.2.0.18. I can boot ubuntu only once. After that time, It kept flashing the num lock and scroll lock light. But I was able to boot using 3.2.0.17 kernel.
Today, I decided to fresh install ubuntu 12.04 daily build. The kernel is 3.2.0.19, but I can only boot once . Now the problem is happening again . 
Please help me .
Today I install only oracle-java 7 , gnome-shell . Nothing else.

---

### Post by mraandtux on 2012-03-19
Try using EasyBCD on Windows or fix the grub?
Also see:
[http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html](http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html)

---

### Post by grahammechanical on 2012-03-19
Please provide more information. How else does it effect the desktop? Or is Ubuntu working fine except for the flashing of the number lock and scroll lock lights?

Regards.

P.S. It seems from your post that the thread title is misleading. It seems that you can boot Ubuntu but your problem is with the continued flashing of the number and scroll lock LEDs. Also, if this is still happening after a fresh install then it could not be caused by an upgrade.

---

### Post by kakalos12 on 2012-03-19
I can't even boot into ubuntu 12.04 using live .
It stops at some error like :
modgrobe tainted .... 
(Can't remember all string)

At the time the error occurs, the light flashing again (num lock and scroll lock lights turn off and turn on repeatedly )

---

### Post by grahammechanical on 2012-03-19
Do you have older versions of Ubuntu Live CDs? Is this an issue with 12.04? Or is it an issue with 11.10 live CD, as well?

Think very carefully about what you try to do to fix this. Do not do things in a hurry. I am wondering if this is a problem with the BIOS.

I do not speak with authority. So, I do not suggest what you should do. I do know that when the computer first starts to boot the BIOS tests for a keyboard and we can see that it is doing this because it momentarily lights up the number lock and scroll lock LEDs.

Can you try using another keyboard? Can you set the machine to boot and display the BIOS messages?

If you remove the hard disk and do not put in a live CD then the machine should boot up to the point that is looks for an operating system. At that point it will say:"No operating system found."

I used this to test my machine when I built it 5 years ago. It was how I tested that the motherboard was functioning before I installed the OS (Ubuntu).

I am just making suggestions. I am not speaking as an expect who knows the solution to this problem. I am trying to make suggestions that do not harm your machine or OS.

Regards.

---

### Post by kakalos12 on 2012-03-19
I'm using windows and I think that all the keyboard and BIOS is OK. 
I'm trying to test with the ubuntu 11.04 if there's an error like this

---

### Post by cariboo on 2012-03-19
Flashing caps lock and numlock led's is usually an indication of a kernel panic. You mentioned seeing a message about a tainted kernel, what proprietary drivers do you have installed?

---

### Post by kakalos12 on 2012-03-19
I just install nvidia and broadcom wifi .
I just test with the ubuntu 11.10 live cd and everything works fine.

Any suggestion.

---

### Post by grahammechanical on 2012-03-19
So, it is to do in some way with 12.04.

I am using kernel 3.2.0.18.20 without problems. I see from synaptic that it is about to be upgraded to 3.2.0.19.21. I wonder if I should allow that.

Regards

---

