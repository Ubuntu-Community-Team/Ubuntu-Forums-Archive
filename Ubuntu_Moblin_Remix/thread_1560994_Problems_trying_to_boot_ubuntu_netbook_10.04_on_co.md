---
title: "Problems trying to boot ubuntu netbook 10.04 on compaq mini cq10-120la"
date: 2010-08-25
forum: Ubuntu Moblin Remix
---

### Post by gabe1986 on 2010-08-25
Hello everybody!!, my problem is this:

I bought a new computer a month ago :p, it is a compaq mini cq10-120la, and I´ve tried to install ubuntu netbook 10.04 on it several times, but the same problems always appears. 

I use an USB memory stick to load the OS. Nothing strange happens when I'm in live CD mode. Then I install the system, and there are no problems, apparently the installation was succesfull, but then, when I reboot my machine and I try to boot my new ubuntu, a flashing dash appears, never disappears :(, to recover the control of my computer I need to reboot.

A couple of times, when I tried to install ubuntu 10.04, after rebooting the system (something that I could do putting out the battery), I could boot my ubuntu, but only when I put out the battery, and after having reboot the computer, the same problem appeared :(.

I wish I could find a response to my problems, and thanks to all in advance :p.

---

### Post by camorri on 2010-09-15
Is this still failing? Or have you got it going?

Can you post some more information. Is this a dual boot system? 

If yes, what other OS do you have installed? 

If you boot from live from the usb, have you looked at the partitions to see if the system 'appears' to be there?

---

### Post by gabe1986 on 2010-09-16
Hello there!!

I had been a little busy and I couldn't post the solution before :P. Fortunately I have solved my problem and I'm writing happily from my Ubuntu.

I have a dual boot system with windows 7 and Ubuntu 10.04. The problem appeared when I tried to boot the system, but I realized that some times my Ubuntu loaded! (after having reboot my system 5, 6, 7...10 times!!) 

So I thought that the problem was in the grub. When I loaded Ubuntu in safe mode, I received the message [2.304584] ata4: DUMMY, and the system didn't load any more.

Being honest, I found the answer in a post at [http://www.ubuntu-es.org/node/139044](http://www.ubuntu-es.org/node/139044), but I modified the step were says that we must reboot Ubuntu 100 times (hehe), and instead I did something a little different. The solution is this:

When you boot your computer, in the grub menu you press the **e** key and a command line console appears, and in the line that says **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"** , you write instead **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash hpet=force nolapic"**, with this you can be able to load Ubuntu without problems. Once you have boot Ubuntu, you open a terminal and write **sudo gedit /etc/default/grub**, and in the line that says **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"** you write **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash hpet=force nolapic"** (we did this to load Ubuntu, but we need to save the file to do this action every time we turn on our computer), then we save the file and close the gedit window. Then we write **sudo update-grub**, and reboot (to see that we are going to be able to load Ubuntu normally).

I hope this answer could be useful to someone, and thanks for your attention :p

Gabe

---

### Post by camorri on 2010-09-17
Thank-you for posting the solution.

---

