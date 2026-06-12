---
title: "Virtualbox XP host, Jaunty guest networking is not"
date: 2010-06-08
forum: Virtualisation
---

### Post by BetterSense on 2010-06-08
My networking is notworking.

I have XP pro at work, and installed Jaunty 32bit guest using the regular Virtualbox for Windows. It installed fine but I can't get on the internet with my virtual Ubuntu. I have it set to NAT, and everyone says NAT is supposed to just work. 

From the mega-thread:

> Again, NAT will work "out of the box".

It's not working. What should I do? Is this because my work has done something to prevent the use of virtual machines?

---

### Post by BetterSense on 2010-07-02
Help please? I completely got a new computer at work, reinstalled Virtualbox and reinstalled Ubuntu, and the networking is not working on this one either. Clearly there must be something that I have to change or set up?

---

### Post by lukeiamyourfather on 2010-07-02
Did you allow Windows to install the pseudo networking drivers during the VirtualBox install? A box should open asking if you want to install the unsigned drivers or some crap like that, answer yes. Are the pseudo networking drivers disabled in the device manager or network control panel of Windows? If you type this in a terminal in the Ubuntu guest, what does it say.

```
ifconfig eth0
```

Also what do you get if you type this into a terminal. 

```
ping www.google.com
```

---

