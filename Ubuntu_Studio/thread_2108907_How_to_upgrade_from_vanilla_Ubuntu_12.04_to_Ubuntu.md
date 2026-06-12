---
title: "How to upgrade from vanilla Ubuntu 12.04 to Ubuntu Studio?"
date: 2013-01-25
forum: Ubuntu Studio
---

### Post by potiphera on 2013-01-25
I've been using 64-bit Ubuntu Studio 10.04 for a few years. Since it's reaching the end of its lifespan in a few months, I've decided to install 12.04. However, I understand that Ubuntu Studio 12.04 doesn't have full disk encryption available from the installer, so what I need to do is install regular Ubuntu with disk encryption from the alternate installer and upgrade from that to Ubuntu Studio. So my question is, what's the proper way to fully upgrade vanilla Ubuntu 12.04 to Ubuntu Studio? (The guide [here]("https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu") is under construction and appears to be somewhat outdated, as it still refers to linux-rt and Karmic.) Thanks!

---

### Post by jejeman on 2013-01-26
First install Xubuntu, then instal UbuntuStudio meta packages. Or install Ubuntu minimal CD, and then install UbuntuStudio meta packages. If lowlatency kernel isn't installed as dependecy install it manualy. RT prirority will be set with JACK install, only thing you should check is are you a member of audio group.

---

### Post by potiphera on 2013-01-26
Awesome, thanks! I'll do it with the Xubuntu 12.04 alternate CD and see how that goes.

---

### Post by potiphera on 2013-01-27
I tried installing every package in Synaptic with "ubuntustudio" in the name (except ubuntustudio-live-settings and ubuntustudio-default-settings, which conflicted with ubuntustudio-menu, so I tried it both ways). Unfortunately, while that installs the proper software, it leaves me with a really ugly-looking system that doesn't have most of the appearance changes I see when using a live USB of Ubuntu Studio. Then I tried installing the exact combination of packages listed in Synaptic when you search for ubuntustudio in the live system, but that still didn't make my installed system look the same.

The problems I currently have are:
[LIST]
[*]there's a Xubuntu splash screen (although this might be necessary so I can enter a password for disk encryption, not sure)
[*]the menu still has the Xfce mouse logo instead of the Ubuntu Studio one
[*]the appearance settings are somewhat different from on a live system, although perhaps not significantly so
[*]the panel with the icons that comes up from the bottom of the screen has become completely opaque
[*]the layout of the menu hasn't changed to be like on the live USB system -- it's still the default Xubuntu one, whereas the live USB has programs categorized much more logically.
[/LIST]

(I'd also like to figure out which kernel the system is running, but I'm not sure how to do that in Xfce.)

How can I fix all these issues to have a standard Ubuntu Studio system? I'll install everything again if necessary, since I plan on using 12.04 for the rest of its lifespan.

---

### Post by jejeman on 2013-01-27
See if there is ubuntu studio session. Log to it.
You find out what kernel with
```
uname -r
```You should have something like:
3.2.0-36-lowlatency

---

### Post by potiphera on 2013-01-27
Excellent, thanks so much! I also had to change the menu icon manually and use the settings editor to change the LCD filter to lcdlight as described [here]("http://askubuntu.com/questions/140311/bad-anti-aliasing-in-some-applications") so fonts would look decent.

I think my only remaining question is, how do I change the appearance of the bottom panel to have an alpha value of 15 like it's supposed to? When I right-click on it and look at the panel preferences on the live image, there's an alpha setting on the appearance tab, but there's none there on my installed system. How can I fix that?

---

### Post by jejeman on 2013-01-27
Strangly enough, I don't have transparency option either. I could sware it was there. :)

---

### Post by potiphera on 2013-01-28
OK, I figured it out. I'm not sure how to do it the proper way (i.e., by installing a package), but I went to Settings>Settings Editor, then to xfwm4, and then enabled "use_compositing" under "general," and voilà, the panel had an alpha channel set at 15.

---

