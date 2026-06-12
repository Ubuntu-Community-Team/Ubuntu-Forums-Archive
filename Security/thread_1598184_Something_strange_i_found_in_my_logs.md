---
title: "Something strange i found in my logs"
date: 2010-10-16
forum: Security
---

### Post by dogdo on 2010-10-16
I use a pptp vpn and all seems to work ok but i just noticed this in my log file viewer-

'Oct 16 13:27:41 daddy-laptop kernel: [   74.227325] padlock: VIA PadLock Hash Engine not detected.' 

Is this a error-what does it mean?

---

### Post by cariboo on 2010-10-16
Have a look a [this]("http://ubuntuforums.org/showthread.php?t=710243") thread, to see if it helps you solve your problem.

---

### Post by dogdo on 2010-10-17
> **cariboo907 said:**
> Have a look a [this]("http://ubuntuforums.org/showthread.php?t=710243") thread, to see if it helps you solve your problem.

No offense but im not that IT smart-the link you sent me seems overly complicated-i dont even know what it means...

There are times i wish ubuntu could be more user friendly like windows-granted ubuntu is more secure but if say something was wrong with windows it would be somewhat obvious-blue screen, slowness, virus popup's etc. I have no idea of whether or not my ubuntu machine is acting up or is this normal behavior.

---

### Post by Jive Turkey on 2010-10-17
is daddy-laptop a computer you own or what?

---

### Post by FuturePilot on 2010-10-17
It's a harmless message. It just means that you don't have a VIA padlock. Something is either expecting or probing for this piece of hardware and it's just stating that it doesn't exist.

---

### Post by dogdo on 2010-10-18
> **FuturePilot said:**
> It's a harmless message. It just means that you don't have a VIA padlock. Something is either expecting or probing for this piece of hardware and it's just stating that it doesn't exist.


When you say probing do you mean as in hacking in? 

Id still like to know what a VIA padlock does though. Its stuff like this that scares off people off ubuntu.

---

### Post by FuturePilot on 2010-10-18
> **dogdo said:**
> When you say probing do you mean as in hacking in? 

Id still like to know what a VIA padlock does though. Its stuff like this that scares off people off ubuntu.

I mean probing as in looking for.

More info on a VIA padlock. [http://www.via.com.tw/en/initiatives/padlock/hardware.jsp]("http://www.via.com.tw/en/initiatives/padlock/hardware.jsp")

---

