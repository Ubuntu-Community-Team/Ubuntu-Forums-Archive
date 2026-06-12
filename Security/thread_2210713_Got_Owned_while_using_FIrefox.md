---
title: "Got Owned while using FIrefox"
date: 2014-03-12
forum: Security
---

### Post by linuxyogi on 2014-03-12
Hi, I am almost sure that my Firefox installation has been compromised. What happens is when I download files to me /home/username/Downloads folder some of the files get deleted. IIRC I started noticing this activity for the past 2-3 days. At first I thought may it was me who deleted them but now I am quite sure. This guy whoever he is doesnt delete all of my files.He/she deletes only p***.  I have files of similar content stored in other folders of my HDD but none of them got deleted. So I can only guess that he had access to on the Downloads folder.I use noscript, adblockplus but still this happened. Even if choose to put the apparmor profile in enforce mode the Downloads folder will surely be within the reach of Firefox.By any chance if the attacker had gained access to my entire home folder I am finished coz I was stupid enogh to keep my pass key of the password manager I use.

Firefox 27.0.1
12.04

---

### Post by cprofitt on 2014-03-12
Any other unusual signs that would lead you believe that you have been compromised?

---

### Post by bashiergui on 2014-03-12
I have my firefox browser set to delete all history and cookies upon exit. That erases anything I downloaded too. See if you have that option checked.

---

### Post by Carl H on 2014-03-13
You sure it's not someone else with physical access to your computer that's checking what you've downloaded and deleting certain files?

---

### Post by linuxyogi on 2014-03-14
> Any other unusual signs that would lead you believe that you have been compromised?No, nothing else.> I have my firefox browser set to delete all history and cookies upon exit. That erases anything I downloaded too. See if you have that option checked. No that option was not enabled. I am sure.> You sure it's not someone else with physical access to your computer that's checking what you've downloaded and deleting certain files? There's no one else at my house who uses a PC.I have deleted the Elementary OS installation. I tried installed Ubuntu 14.04 using the daily image but the boot process kept on hanging. So I installed Xubuntu 12.04. I am no longer using FF. I am using Chromium now.

---

### Post by untrustytahr on 2014-03-14
Do you have Bluetooth turned on and sharing?  It gives access to the ~/Downloads directory and, if setup, allows remote devices to delete files

[ATTACH=CONFIG]251132[/ATTACH]

---

### Post by open2reason on 2014-03-14
An idea maybe to download a test file into something other than the default FireFox download folder some thing like ~/doesthiswork. 
Then switch off and on again and see if this new folder still holds your download. 
If you did this for a few days you would then see if things were going missing on a regular bases or not.
This might indicate that your Firefox settings were not to blame for the deleting of downloaded files upon exiting Firefox.

---

### Post by leclerc65 on 2014-03-15
I switch ISP recently, because my previous one used to throttle my internet. I get my downloads cancelled mysteriously (when the files are large, and especially at the end of the month).
I use torrent now when possible. 
One more reason not to distro-hop.

---

