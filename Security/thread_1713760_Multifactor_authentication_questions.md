---
title: "Multifactor authentication questions"
date: 2011-03-24
forum: Security
---

### Post by asdfghjkl67 on 2011-03-24
First off is there any way to configure ubuntu to log in with a password, fingerprint and usb token? 

Secondly what is the difference between the standard home folder encryption and the alternate install encryption? 

Thirdly is it possible on  new external hard drives that incorporate thumb scanners to install truecrypt on these? 

Fourthly does anyone here on ubuntu forums use lastpass with the 'yubikey' device-does it work well on ubuntu? 

And fifthly are ironkey usb keys worth the money or are they a scam?

---

### Post by tgm4883 on 2011-03-24
> **asdfghjkl67 said:**
> 
Fourthly does anyone here on ubuntu forums use lastpass with the 'yubikey' device-does it work well on ubuntu? 


I use it with chromium-browser and it works great.

---

### Post by bodhi.zazen on 2011-03-24
> **asdfghjkl67 said:**
> Secondly what is the difference between the standard home folder encryption and the alternate install encryption? 

Both use encryption, but there is variation in what exactly is encrypted.

"standard home" - Only a users home ( /home/user ) is encrypted using ecryptfs.

"alternate install encryption" - By default everything but /boot is encrypted ( / , swap, etc) using LUKS + LVM. You can modify various things (LVM or not, separate partitions for /home / var , etc, multiple crypts) if you desire.

---

### Post by asdfghjkl67 on 2011-03-28
bump bump

---

### Post by BkkBonanza on 2011-03-28
With encrypted home you can move the **/home/.ecryptfs/<user>/.ecryptfs/wrapped-passphrase** file to a usb stick and replace it with a symlink to the new location. Then the usb stick has to be inserted in order for the login to succeed, giving two factors.

According to what I've read those fingerprint scanner things aren't that great for security as you leave lots of fingerprints all over your keyboard and apparently it's been shown that can used to fake them. I say apparently because it seems a stretch to me, but that's what I've read.

---

### Post by trundlenut on 2011-03-28
As it happens I have literally just installed [fingerprint-giu]("http://www.n-view.net/Appliance/fingerprint/") to allow me to use the fingerprint scanner on my laptop.  Have a look at this for the fingerprint side of things.

---

### Post by BkkBonanza on 2011-03-28
See below for simple method of deceiving fingerprint readers.
[http://www.ccc.de/updates/2007/umsonst-im-supermarkt?language=en](http://www.ccc.de/updates/2007/umsonst-im-supermarkt?language=en)

---

### Post by mathuin on 2011-03-29
I just started using LastPass everywhere I can and additionally configured my Google account to use two-factor authentication.  I would love to have two-factor authentication for Ubuntu (shell and graphical) -- is this anywhere on the roadmap?

Jack.

---

