---
title: "AntiVirus 2010 Scam"
date: 2010-09-29
forum: Security
---

### Post by FreshRevenge on 2010-09-29
Hello everyone, I just made a switch to Ubuntu two days ago which before I was on Windows XP. Now I  

                 came across of getting some type of Malware program called AntiVirus 2010 which when I investigated is similar to AntiVirus 2009, 2008. Now it pop up and it just got really irritating so I look for another Operating system to run on my Netbook.

I finally decided to go with Ubuntu 10.04 for netbooks. Now when setting it up I deleted Windows XP since I didnt want the Operation System. I have all ways had security issues with Windows. Now I am running Ubuntu but I am getting the same malware antivirus 2010 pop up in a window when I tried to go to gaming website. How can a malware program carry over to Ubuntu?

So far I love the new interface, I have installed firewalls and virus scanners but is there a method of determining how to get this annoying Antivirus 2010 off my system?

Thank you if you can help me.

---

### Post by Ahava591 on 2010-09-29
Um, don't go to that website?

(Malware isn't necessarily OS-dependent; however, I must note that just because a Windows virus, for example, is carried to Ubuntu, for example, that doesn't mean the malware is going to actually hurt you. Malware is just software that is designed to behave, well, maliciously; if your OS does not allow it to behave at all, then it can't behave maliciously as its' writers intended.

There is a built-in firewall within the Linux kernel called Netfilter, something along that line. iptables allows you to configure the built-in firewall; there are also GUI programs that allow you to configure the firewall such as Firestarter and gufw. As far as I know, you don't really need to add another software firewall to your system. The one that comes with Linux is good enough.)

In all seriousness, though, it sounds like there's just a script that runs when you visit that website that causes these pop-ups. Try NoScript or Adblock Plus. They are both free as in free beer and I think open source, although NoScript allegedly contains some closed code. Both of these are used as a plugin for your web browser.
-I use Mozilla Firefox and have experienced no problems with either. 

So try NoScript, maybe Adblock Plus, and see what happens. I must recommend that you not visit that website if this happens every time you do.

I hope you solve your problem soon and please let us know if you want more help.

---

### Post by TBABill on 2010-09-29
Most likely you aren't infected, but rather now just seeing the popup browser window trying to appear like the virus (I think it's actually a trojan) in Windows. I had it on a computer (Windows machine) once and just cleaned it off my in-laws' machine as well. But never in Ubuntu or any Linux distro. Can you close it like it's a window or is it attempting to control your machine like it did in Windows?

In Windows it blocks access to Windows Explorer, anti-virus software and many other tools. I ended up finding the path to it, opening a command prompt window and deleting it the old fashioned way (manually - command line). 

Anyway, please describe further the problem. What can/can't you do when it appears or can you just close it and go on about your business? It's a trojan that runs via a .exe file so your machine will NOT allow it to execute, which leads me to believe you are just seeing a popup and not actually infected.

---

### Post by wilee-nilee on 2010-09-29
Look in the security section of the forum there is good info there. If your using FF you should have a flash blocker installed. I use noscript, but it has a learning curve, and you get the session allow and block buttons in the FF right click customize. There is also flashblock. Most of these scareware popups are running in flash so blockum, I haven't seen one of those for a couple of years in Linux, XP, or W7.

---

### Post by CharlesA on 2010-09-29
+1 to Adblock as well.

---

### Post by HermanAB on 2010-09-30
Howdy,

Fortunately Linux is not Windows...

So, relax and enjoy your nice new secure system.  If you did a default install of Ubuntu, then you don't need extra firewalls and virus scanners.  

As mentioned above, Adblock in your browser should be enough to keep junk off your screen.

---

### Post by OpSecShellshock on 2010-09-30
Yeah, the gaming website has been compromised either by a script having been embedded in their page or due to an advertisement that is pointing to a malicious script. That stuff is rampant, but the browser add-ons like Adblock and NoScript will keep the code from running. All that really happens initially with these fake AV things is that a script opens a browser window that is designed to look like Windows Explorer or Control Panel or Security whatever. Then it has little animations that create the illusion that it's scanning your C drive (which doesn't exist in Linux) for malware.

On Windows it will reconfigure things and drop other files, will try to modify the hosts file, alter the registry, hook other legitimate processes and generally ruin the installation. However, those things are specific to Windows, so the most a Linux user will ever see is the pop-up web page. Well, it may also crash the browser session if it keeps trying to do things that can't be done and starts consuming cycles. That's easy enough to spot because the whole browser will turn grey and become unresponsive. You can just force quit at that point.

---

