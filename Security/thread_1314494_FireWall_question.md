---
title: "FireWall question"
date: 2009-11-04
forum: Security
---

### Post by Himself2007 on 2009-11-04
Hi

I'm a new Ubuntu user.
I read somewhere that Ubuntu still needs a FireWall.
I found these.
[B][I][COLOR="DarkSlateBlue"]Guarddog
FireStarter[/COLOR][/I][/B]
Which one would be the best choice on a P4-2.66MHz with 768Mb.Ram?
Thanks.

Luc

---

### Post by cdenley on 2009-11-04
The only reason to run a firewall on a typical desktop system is to protect you from yourself accidentally installing servers (if you have a direct internet connection, not a NAT router). A firewall isn't really needed, but if you insist on having one, I would recommend UFW, or it's graphical frontend, GUFW. Any "firewall" you find for ubuntu will simply be a tool which configures iptables, so your system specs are irrelevant. Iptables will run on any system specs, anyway, and already does by default but doesn't filter anything.

I would suggest not using firestarter. It is no longer maintained or supported, and you're probably safer without it.

---

### Post by scaine on 2009-11-04
Fully agree with cdenley regarding GUFW.
```
sudo apt-get install gufw
```Then run it from System/Administration/Firewall Configuration.

It's a little basic, but covers most use cases and seems to be improving with each Ubuntu release.  If you don't want a gui, then use the following commands to see the status of your inbuilt firewall, or enable it if it's not already up (which it's not by default).
```
sudo ufw status
sudo ufw enable
```

---

### Post by Himself2007 on 2009-11-04
Great advices.
Thanks guys!

Luc

---

