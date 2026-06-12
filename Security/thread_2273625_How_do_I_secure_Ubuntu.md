---
title: "How do I secure Ubuntu"
date: 2015-04-14
forum: Security
---

### Post by blackinfinitespace on 2015-04-14
Hi, I'm both new to Linux and new to the forums.  I have a Windows mindset and the first thing I normally do when installing that OS is secure the system.  While I know Linux is much more secure I've heard that treating it like it's completely secure is a mistake.  What sort of things do I need to do?  I've heard about app armor and that I need to set up the firewall.  

I'm so used to being on Windows that it feels quite weird to be on a system without an antivirus or without a software program such as Sandboxie.  However it does feel great to be using Ubuntu :p

---

### Post by sammiev on 2015-04-14
Welcome to the forums and I hope [this]("https://wiki.ubuntu.com/BasicSecurity") helps you.

---

### Post by blackinfinitespace on 2015-04-14
> **sammiev said:**
> Welcome to the forums and I hope [this]("https://wiki.ubuntu.com/BasicSecurity") helps you.

Thank you for the welcome and the link.  It did prove to be very useful and I set up the firewall.  App amor does seem to be a lot more complicated.  Does Ubuntu already have app armor profiles set up?

---

### Post by dino99 on 2015-04-14
> **blackinfinitespace said:**
> Thank you for the welcome and the link.  It did prove to be very useful and I set up the firewall.  App amor does seem to be a lot more complicated.  Does Ubuntu already have app armor profiles set up?

Linux is way more restrictive under the hood compared to what you were using:
- the packages comes from ubuntu archives
- they are open-sourced, so everyone can know about them, no blackbox here
- user need to open a session with rights, so others cant polute the system
- ubuntu configure itself with lot of rules (apparmor), auto configured firewall (fwts), antivurus (clamav) for paranoids ;)

So the common user does not need to be scared, ubuntu is for humans.
Only dont do silly decisions: avoid unknown/untrusted extra packages, never run the system as root but only open a user session.

---

### Post by blackinfinitespace on 2015-04-14
> **9d9 said:**
> Linux is way more restrictive under the hood compared to what you were using:
- the packages comes from ubuntu archives
- they are open-sourced, so everyone can know about them, no blackbox here
- user need to open a session with rights, so others cant polute the system
- ubuntu configure itself with lot of rules (apparmor), auto configured firewall (fwts), antivurus (clamav) for paranoids ;)

So the common user does not need to be scared, ubuntu is for humans.
Only dont do silly decisions: avoid unknown/untrusted extra packages, never run the system as root but only open a user session.

Thank you.  This was exactly the type of reassurance that I was looking for that I'm on a solid system and that I don't have the worries that I used to on Windows.

When you say open user session, is that what you're logged in as automatically?

---

### Post by HermanAB on 2015-04-14
Howdy,

You don't have to do anything.  Ubuntu is secure out of the box.  

However, you have to be careful that you don't destroy the default security by playing with things you don't understand yet, but that creates a Catch 22 - how can you ever learn anything?

The trick is to install Virtualbox and play inside a virtual machine (Linux inside Linux).  When you are done playing, you can simply stop the machine or blow it away, without messing up your regular desktop system.   This is how developers work on the Linux kernel for example.

---

### Post by grahammechanical on 2015-04-14
AppArmor is installed by default but we should not assume that all applications have an AppArmor profile. This page shows that it is mainly system executable files that are getting profiles.

[http://zsync http://cdimage.ubuntu.com/daily-live/20150414/vivid-desktop-amd64.iso.zsync](http://zsync http://cdimage.ubuntu.com/daily-live/20150414/vivid-desktop-amd64.iso.zsync)

Applications in the Ubuntu Software Centre are code audited to see if they contain malicious code but software that we download from some web site and install does not carry the same assurance.

When we install Ubuntu we set up a user name and password. We are then both the administrator and a standard user. When we log in to Ubuntu we work as a standard user. If we try to do something that only an administrator can do we are asked to authenticate the action. In this situation our password will act like we are the administrator. For indeed we are but we revert to being a standard user when the action is complete. So, if we leave the machine and another person gains access to the machine they cannot change system files because they will be required to authenticate. And, of course, they do not know our password. Or do they?

We can protect ourselves by always checking the action that we are being asked to authenticate before entering our password. If we get in the habit of entering our password whenever we are asked to without checking we may authorise some malicious code to do some bad.

A glance around the help sections of this forum will show that the greatest danger to our Ubuntu systems is not malicious code but we ourselves. 

Regards.

---

### Post by Habitual on 2015-04-14
and if you have a router, it's even safer, if correctly restricted.

---

