---
title: "Apparmor skipping firefox"
date: 2014-12-17
forum: Security
---

### Post by Quarkrad on 2014-12-17
I love ubuntu, been using it since 8.04, but I guess this is an expamle of those that dislike ubuntu.  After all these years I have actually enabled apparmor and to slowly kick off my understanding I want to protect firefox.  I keep getting the message Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox whether I run the command as root or as user.  It is difficult to see the wood for the trees when you google this error - but I have asssertained that I have the correct version that a launchpad thread said fixed this issue.  So - now I'm a little stuck.  Is apparmor a step too far for an ordinary user like myself (newbie)?  For now I will switch off apparmor off.

---

### Post by maglin2 on 2014-12-17
Not quite sure what you mean here. I'm pretty much a newbie too, but I find that many appermor profiles are eabled by default in 14.04 - but not firefox.

To enable firefox apparmor profile I move the /etc/apparmor.d/disable/usr.bin.firefox symlink to somewhere else, eg
 
sudo mv /etc/apparmor.d/disable/usr.bin.firefox ~

Then reboot.

Seems to work for me.

---

### Post by vasa1 on 2014-12-17
I used```
sudo aa-enforce /etc/apparmor.d/usr.bin.firefox
```I don't know if that's still applicable. The reasoning, at least in the past, for having to enable Apparmor for Firefox and not have it on by default was given here: > Proactively protecting Ubuntu users against unknown and future vulnerabilities is why the profile was developed; however, enabling the profile by default has a high risk associated with it. The expectation for default enforcing AppArmor profiles in Ubuntu is that the profile must work for the vast majority of users in the default install, without any intervention on the part of the user. Looking at other operating systems shows that when users are faced with a security mechanism that gets in the way, they turn off the security mechanism rather than fix it.Source: [https://wiki.ubuntu.com/SecurityTeam/Specifications/Karmic/AppArmorFirefoxProfile](https://wiki.ubuntu.com/SecurityTeam/Specifications/Karmic/AppArmorFirefoxProfile)

---

