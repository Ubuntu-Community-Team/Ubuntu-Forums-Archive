---
title: "Virtualbox and DirectX9.0"
date: 2009-07-12
forum: Virtualisation
---

### Post by razorboy5 on 2009-07-12
Hi

I'm running my Jaunty 9.04 Ubuntu as Host and Windows XP as guest on VirtualBox.

I'm trying to play a game which requires 9.04. I did some research and most of the forums said that i cannot install DirectX9.0 on VirtualBox. However these forums were mostly from 2007-2008 and there were some mention of beta so my question is - is there a way to install DirectX 9.0 on Virtualbox?

also i heard that on VMware DirectX9.0 is capable. Having no experience with VM i would not know, is this true?

thx

---

### Post by razorboy5 on 2009-07-14
Bump

---

### Post by steveneddy on 2009-07-14
There is a new beta that supports direct x 9

found thru a quick google search

[http://blogs.vmware.com/teamfusion/2008/05/more-displays-m.html](http://blogs.vmware.com/teamfusion/2008/05/more-displays-m.html)

Here is the goole search for more info:

[http://www.google.com/search?hl=en&q=vm+ware+direct+x+9.0&aq=f&oq=&aqi=](http://www.google.com/search?hl=en&q=vm+ware+direct+x+9.0&aq=f&oq=&aqi=)

---

### Post by starfry on 2009-07-17
Hello,

Version 3.0.2 has EXPERIMENTAL support for DirectX. You need to install something called "wineD3D" on your guest for it to work and you must enable 3D in the settings box of the VirtualBox VM.

You can test your DirectX by using "start->run" to run "dxdiag"

That said, I have had limited success with it. But then I am trying to run MS Flight Sim X in it which may be a tad over ambitious :P

---

