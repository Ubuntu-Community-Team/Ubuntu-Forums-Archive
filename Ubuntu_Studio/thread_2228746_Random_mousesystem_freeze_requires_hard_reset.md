---
title: "Random mouse/system freeze requires hard reset"
date: 2014-06-09
forum: Ubuntu Studio
---

### Post by shaunthesheep on 2014-06-09
Using v12.04 LTS duel booting with Window 7 Home Premium SP1.

Using the AMD/ATI FGLRX proprietary graphics (post release updates) driver from Additional Drivers.

I have recently started getting random system freezes requiring a hard reset which is not doing my HDDs any good: the mouse freezes and keyboard short cuts like ALT + F2 don't work. They are happening once or twice a day but I can go for long periods without them.

I know that these can be caused by a variety of things like ineffective fans/CPU heat, memory bad sectors, drivers.

I have run the Dell diagnostics tests and it reports no problems.

What I am lacking is a system monitoring programme that can record CPU temp and usage. I have Sensor Value Viewer but I get a message when I launch it from Application Finder saying it doesn't have the necessary permissions. Any suggestions how I can get this functioning or an alternative?

---

### Post by uudruid74 on 2014-06-21
> **shaunthesheep said:**
> 
I have recently started getting random system freezes requiring a hard reset which is not doing my HDDs any good: the mouse freezes and keyboard short cuts like ALT + F2 don't work. They are happening once or twice a day but I can go for long periods without them.


Are you sure this is a hard freeze?  These are rare in Linux unless your hardware is really defective.   Can you change to a text console using CTRL-ALT-F1 ?  <CTRL-ALT-F7> will take you back to X.   If you can get to a console, log in and see what "top" is doing.  I'm wondering if its related to a similar problem I'm having, in which case you wait about 15 seconds or so and your system comes back.

Even if you can't change consoles, if you have ssh running, you can sometimes get in that way from another machine over the network and then diagnose the problem via ssh.   If you can't get in through ssh, your system is having a pretty severe problem and then you need to start looking at hardware problems.   Is your syslog telling you anything?

---

### Post by Micski on 2014-06-22
I would not say, that complete freezes are rare in Ubuntu. They are extremely rare in systems like FreeBSD, on the same hardware and same machine, but not in Ubuntu. Ubuntu has created these freezes for years. I wonder, how they do it.

---

### Post by shaunthesheep on 2014-08-16
> If you can get to a console, log in and see what "top" is doing.

Sorry, could you explain what "top" means? I am newish to Linux (refugee from Windows). Could you explain step by step what I should do or link me to instructions please?

Most of your suggestions went straight over my head. Heard of it but never used ssh. Will have to look it up. Had a look at syslog but can't see anything that makes sense to me.

I am now using Ubuntu Studio 14.04.1. Still getting occasional cursor freezes.

I am switching back to the default open source graphics drivers to see if it is the proprietary drivers that are the culprit.

EDIT

OK, I have read up on what the "top" (and "htop") command is and various ways of handling freezes without a hard reboot. Just type

> htop

In the terminal and it brings up a list of processes in real time along with how much ram and cpu they are using. Scroll down and kill any processes hogging resources. If htop is not installed, instructions will be given for installing it.

Here is one method of handling freezes that I came across that may be of use to others:

1. Hit Ctrl +ALT +F1. This brings up the terminal

2. Login by typing in the terminal  your user name and password.

3. Then type:

> kill -9 -1

That should take you to the Ubuntu login screen where you can start over without the hard rest.

---

### Post by JDorfler on 2014-08-17
If you are using an AMD processor, make sure your RAM timings are exactly what is specified and make sure your HyperThreading is matched to your processor.

---

### Post by shaunthesheep on 2014-08-18
Thanks but I am using an Intel CPU (see signature)

---

