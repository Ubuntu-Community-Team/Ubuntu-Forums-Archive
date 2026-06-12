---
title: "[SOLVED] VirtualBox - Keyboard not working...!!?"
date: 2008-06-11
forum: Virtualisation
---

### Post by hopelessone on 2008-06-11
Hi,

Just installed What to do to get Keyboard??

Did a reinstall and no response when keys pressed...please help...

Thanks..

---

### Post by hopelessone on 2008-06-11
Anybody got any suggestions?

I installed OSE first then uninstalled it installed PSE gave some error....uninstalled all things with virtualbox in Synaptic...reinstalled PUEL..

Whats this install guest OS tools? how to?

---

### Post by Fleuris on 2008-06-11
I've not really experience with virtualbox, but I know it's known for his errors. It seems to me that you should try to install Guest OS tools. Or maybe you should google this problem, and hope you'll find someone else with this problem, and maybe an solution ;)

---

### Post by hopelessone on 2008-06-11
please help....

---

### Post by hopelessone on 2008-06-11
Whooooo...

What a pain in the @ss...SCIM input interfers with the keyboard caputre...works after you unclick "enable input for complex characters"....then you have to reboot !! WTF !!!
+ Compiz interferes aswell have to set settings to NONE!!

So get this... i installed VirtualBox for my wife because Korea is addicted to activeX ies4linux don't work...installed Virtual OS to find out i can't use it !!

I really don't wanna duel boot...dam windows sucks...

---

### Post by shusai on 2008-08-27
[Here]("http://forums.virtualbox.org/viewtopic.php?t=5721") I found a solution which works for me:

```
sudo apt-get install scim-bridge-client-qt

```

Then reboot and everything should work.

---

### Post by Mazehero55 on 2008-09-03
Somebody should sticky this, or put it in the community tutorial for VirtualBox.

Cause I was having the same problem till I found this

---

### Post by derelict888 on 2009-08-18
> **shusai said:**
> [Here]("http://forums.virtualbox.org/viewtopic.php?t=5721") I found a solution which works for me:

```
sudo apt-get install scim-bridge-client-qt

```

Then reboot and everything should work.

This worked for me, I had the same problem as thread creator.
:guitar:

---

### Post by AlanQ on 2009-10-29
I have the same problem.

Ubuntu 9.04 64bit host -- VirtualBox 3.0.8 -- Ubuntu 9.04 32bit guest

No keyboard input inside guest.
Used this forum thread to locate the solution.

A short-term solution:
Simply dropping out of the guest by exiting full screen and then back in again re-enables text input, but only temporarily.

---

### Post by BillPet on 2010-04-10
> **shusai said:**
> [Here]("http://forums.virtualbox.org/viewtopic.php?t=5721") I found a solution which works for me:

```
sudo apt-get install scim-bridge-client-qt

```

Then reboot and everything should work.

Should this be installed on the host or the guest? I did figure out that if I just minimize the guest window then restore it the keyboard works, but that's annoying.

---

### Post by RomanIvanov on 2010-04-10
AlanQ, did you solve the problem ?  I have the same problem as you

---

### Post by useResa on 2010-06-25
I ran into the same issue, but installing the indicated package did not solve the issue for me. However, a search showed there are two additional scim-bridge-client packages.

I also installed these two packages
```
sudo aptitude install scim-bridge-client-qt4 scim-bridge-client-gtk
```

After rebooting I could use my keyboard in VirtualBox, so one of the two resolved it for me.    :p
Thanks for pointing me in this direction

---

### Post by jfekendall on 2010-10-30
> **shusai said:**
> [Here]("http://forums.virtualbox.org/viewtopic.php?t=5721") I found a solution which works for me:

```
sudo apt-get install scim-bridge-client-qt

```Then reboot and everything should work.

Sorry to resurrect a dead thread, but thanks for this. Worked for me.

---

