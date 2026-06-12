---
title: "More security !?!"
date: 2017-06-20
forum: Security
---

### Post by mic487 on 2017-06-20
I'm under attack from my provider ! So I need to know every thing about getting access (remote) to my ubuntu-system. So please share your know-how with me, so that I'm able to give these suckers no chance to get access to my system.
I set root-passwd, disable ssh-root-login, use ufw, unistall remmina.
What else do I have to do ? And please don't tell me that I have to read this or that, PLEASE tell me exactly which holes do I have to close and how.

---

### Post by Frogs Hair on 2017-06-20
> I'm under attack from my provider !  Can you provide some details as to why you think so ?

---

### Post by slickymaster on 2017-06-20
Thread moved to ***Security*** for a better fit

> **mic487 said:**
> ......
What else do I have to do ? And please don't tell me that I have to read this or that, PLEASE tell me exactly which holes do I have to close and how.
Please don't make demands when requesting help. Forum members and/or staff are more like likely to provide help when addressed in a friendly tone.

Since you're just joining the Ubuntu Forums I'd recommend you a read of [Posting Guidelines]("https://ubuntuforums.org/showthread.php?t=2158945") and [Suggestions on how to get your support questions answered as quickly as possible]("https://ubuntuforums.org/showthread.php?t=1422475&p=8920811#post8920811") threads

---

### Post by QIII on 2017-06-20
You have not provided any information that would give a clue as to the nature of the supposed attack.  Under those circumstances, we cannot provide advice.  We cannot even determine if there has been an attack.

You would have to read any answers given here just as you would elsewhere.  Why demand that the community to re-invent the wheel  when there is a plethora of articles covering every detail of security?

---

### Post by lisati on 2017-06-20
As others have indicated, some more information would be useful to help us provide a useful diagnosis.

The only sure way of protecting your devices from attack, real or imagined, is to completely disconnect them from the outside world. The down side to this approach is that it can seriously degrade the device's usefulness.

---

### Post by HermanAB on 2017-06-21
Paranoid much?  First relax and drink a cuppa, then think about your sins: What programs did you install that may be causing a problem, since Ubuntu is quite secure by default.

---

### Post by TheFu on 2017-06-21
> **mic487 said:**
> I set root-passwd,

Well, that is mistake #1.  The default Ubuntu setup root cannot login, so it cannot be remotely attacked. By setting a password, you've provided another, deadly, attack, vector.

It is simply not possible to > 
So I need to know every thing about getting access (remote) to my ubuntu-system.
You cannot run a marathon without any training. How could we possibly "teach you everything" that we've spent decades learning?  Crawl, walk, run, marathon.  Usually, when people think they are intermediate level in their knowledge, they are just passed beginner and barely entering intermediate.  I've been programming and running linux/Unix systems for 20+ yrs and think I know about 10% of the topic, BTW.

Depending on the network provider, you may not be able to prevent their access to your systems.  They can insert javascript into any unencrypted web pages that you view, which will be run by your computer inside the LAN.  I've seen LAN subnet scanners created that do this and send the data back to the provider.  If the provider is owned by the state (like happens throughout the world), then you should be VERY CAREFUL and not really prevent their access unless you want worse things to happen.  It isn't too likely this is an issue, unless you already know about that practice in the location.

The best that most people can do is:
* stay patched.
* always use HTTPS, TOR, and a VPN (if that is legal)
* Have a fully patched router. If your home router can't be patched weekly, then there is a known bug in the software that can be exploited.  There are probably 50-200 bugs in most home routers firmware right now that haven't been publicly announced.
* Don't do anything online that would be considered illegal in your location.
* If you use a cloud server, there isn't any privacy. Get over it.

So ... get your network security right, then get your OS security right, then work on locking down everything.

---

### Post by Habitual on 2017-06-22
[Ubuntu Security]("https://ubuntuforums.org/showthread.php?t=510812")
Sorry, it is all **I **have. Anything we tell you is likely in that thread.

---

### Post by HermanAB on 2017-06-25
Sooo, backup your data (if any) reinstall and always use looong (>12 character) passwords for everything.

Reinstalling only takes a few minutes and after that the machine is refreshed and secure again.

---

### Post by Habitual on 2017-06-26
Reset your Router, if you have one. 
Change and utilize a new admin password for it.

---

