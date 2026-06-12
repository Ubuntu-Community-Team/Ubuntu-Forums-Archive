---
title: "Hacked!!"
date: 2011-01-26
forum: Security
---

### Post by Lawliet1 on 2011-01-26
Recently, I've determined I was hacked by a very skilled script kitty, and I was wondering what I should do to get them out of my systems. I have three computers hooked up to a router. All of them have been compromised. 

What should I do? Does anyone have any advice they could offer? I would greatly appreciate it. I thought about reinstalling Ubuntu on all the computers and resetting the router to factory settings but I don't know if that would get them out of my system.

---

### Post by IWantFroyo on 2011-01-26
If you use GParted to wipe the harddrives, their nasties will go too. Just delete all partitions. Then reset router and reinstall ubuntu.

---

### Post by Rubi1200 on 2011-01-26
Sorry for being suspicious, but what evidence do you have that you were hacked?

---

### Post by Kirboosy on 2011-01-26
I would change all your passwords after you clean install everything. Just in case he left a backdoor somewhere in the system (unless you want to find it manually) If a script kiddie got in their then their must of been a really weak password on the system. Try to shake things up with upper and lower case and numbers/symbols

The router password should definitely be changed immediately. You also might want to check to see if any updates are available to the firmware. Another alternate firmware that *might* work is [DD-WRT]("http://www.dd-wrt.com/site/index") but you need to check to see if your device is supported.

---

### Post by Lawliet1 on 2011-01-26
I caught them changing my log files. After that, I turned them into the authorities, but I need to secure my system. There were at least 3 perpetrators that were doing it, so I am concerned they will be back. They are determined to keep track of all my Internet traffic.

---

### Post by Kirboosy on 2011-01-26
That is why we are recommending reinstalling everything. Make sure nothing stays the same. If you change everything it will at least slow them down, if not stop them totally. Script kiddies can only go as far as the tool will let them. Meanwhile real hackers will keep trying until they get through.

---

### Post by Lawliet1 on 2011-01-26
@ Caboose885 and the other people that helped.

Thank you all so much for the Help. I really appreciate it greatly. 

Caboose was right about the passwords. They got in when I wasn't using any passwords at all for my boxes and a password I didn't change from the router's previous owner. I'm using really strong passwords and changing them monthly. 

So if I reinstall my operation systems on all the computers while deleting my previous partitions and resetting the router configuration, will that get rid of them? The operation systems are on read only CDs so they are not compromised.

---

### Post by Kirboosy on 2011-01-26
Yes that should work. Are you installing 10.10 Ubuntu? Just make sure you back up all your data before you wipe the partition. ;)

When you reset the router that you reconfigure it with a *strong* password. Some routers even allow you to set admin access restrictions based on IP/MAC address. 

If its a Wireless router I would highly recommend WPA or WPA2 encryption. WEP is super easy to crack (as a hacker I know that from personal experience) However I wouldn't recommend MAC Filtering. MAC filtering gives you a false sense of security and gives you (the normal user) more of a headache. Trust me its easy to get around.

---

### Post by HermanAB on 2011-01-26
Howdy,

Re-install
Use passwords longer than 8 characters
Do not use VNC

---

### Post by Kirboosy on 2011-01-26
> **HermanAB said:**
> Howdy,

Re-install
Use passwords longer than 8 characters
Do not use VNC

You can use VNC as long as you VNC over SSH ;)

---

### Post by Lawliet1 on 2011-01-26
@ Caboose

I'm about to upgrade to the 10.10 version. The version I have now is the one before it. I bought the book "Linux Bible 2010" and it came with Ubuntu and 18 other distributions of Linux.  After trying Ubuntu once, I was head over heels for it. 

Yea, I use a wireless router. I will do what you suggested first thing. Changing my Ip address after the clean installs would be a good Idea too, right? 
------------------------

They told me there would be cake, but the cake was a lie.

---

### Post by Kirboosy on 2011-01-26
If it doesn't change your IP thats not a big deal because thats only your local IP. I have a feeling since you reset the router your IPs will change but if it doesn't, not a big deal.

Edit2:*facepalm* if your router has the capabilities for a firewall, turn that on. That will close off some ports to limit access to your network. You can turn individual computer firewalls on but that is known to cause communication issues between the networked computers for various things. Like if you share files across the network, etc...

---

