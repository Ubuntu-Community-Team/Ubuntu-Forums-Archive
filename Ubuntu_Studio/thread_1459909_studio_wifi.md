---
title: "studio wifi"
date: 2010-04-22
forum: Ubuntu Studio
---

### Post by zander1013 on 2010-04-22
hi,

i have just installed ubuntu studio on a laptop that usually runs vanila ubuntu 9.10 very well.

usually there is a network applet that shows available networks in the app panel but there is none in studio. and i can't seem to find any way to join wireless networks.

please advise.

---

### Post by unmole on 2010-04-22
You probably need to install WiFi drivers. Checkout the 'Hardware Drivers' from the System>Administration menu.

---

### Post by zander1013 on 2010-04-22
> **unmole said:**
> You probably need to install WiFi drivers. Checkout the 'Hardware Drivers' from the System>Administration menu.

ty umole, that sounds fair. do you know what drivers i should install?

---

### Post by unmole on 2010-04-22
> **zander1013 said:**
> ty umole, that sounds fair. do you know what drivers i should install?

Well that depends on what hardware you have. What Drivers are displayed in the **Hardware Drivers** window?

---

### Post by cchhrriiss121212 on 2010-04-22
Studio does not come with network manager installed, so you just need to download it from synaptic using a wired connection. Or install it using the dvd as a source.

---

### Post by unmole on 2010-04-22
> **cchhrriiss121212 said:**
> Studio does not come with network manager installed, so you just need to download it from synaptic using a wired connection. Or install it using the dvd as a source.

My bad. I did not know that. It's a bit weired tough...

---

### Post by zander1013 on 2010-04-22
ty for the assistance everyone.

installing gnome network manager and rebooting a few times turned the trick:guitar:

---

### Post by stephenmurdoch on 2010-05-10
Does anyone else have a hard time understanding why Ubuntu Studio does not ship with Network Manager installed?  

What happens if someone who doesn't have a wired ethernet connection wishes to use it?

I only have wireless.

I guess I need to connect from the command line then.  So what commands will do that for me?  Is there a guide?

My wifi uses WPA2 personal encryption.  I don't have easy access to the hub either as it's my neighbour's

---

### Post by stephenmurdoch on 2010-05-10
ok, so i found a bug which explains why the NMapplet doesn't ship with UbuntuStudio - [https://bugs.launchpad.net/ubuntu/+bug/380906](https://bugs.launchpad.net/ubuntu/+bug/380906) - something to do with NMapplet affecting realtime audio recording

so which network manager applet doesn't affect realtime audio recording?  does WiCD work ok with Studio?

---

### Post by cchhrriiss121212 on 2010-05-11
What I do is install network manager, then just run nm-applet from terminal whenever I want to update or something. As it says in the link, you can find network manager on the studio image.

---

### Post by lnxguit on 2010-05-11
I ran into that problem, too. I installed Wicd Network Manager, which I think is an improvement over nm-applet

---

