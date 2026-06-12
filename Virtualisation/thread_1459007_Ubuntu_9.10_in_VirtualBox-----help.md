---
title: "Ubuntu 9.10 in VirtualBox-----help"
date: 2010-04-20
forum: Virtualisation
---

### Post by SVEN1 on 2010-04-20
Before I upgrade from 9.04 decided to install 9.10 in VirtualBox first and check for problems.

I am trying to get Guest Additions to install. It fails to install.
Unable to build "kernal module"

Any ideas on how to fix this. Had the same problem installing Guest Additions in Mint 8. In Mint 7, no problem, installed flawlessly.

Thanks

---

### Post by drs305 on 2010-04-20
Are you running an older version of VBox? I ask because the Guest Additions I'm running (OSE) is 3.1.6.

I just reinstalled it on VBox 3.1.6 and it installed without issue (64-bit). And it runs Lucid without problems as well.

---

### Post by SVEN1 on 2010-04-20
> **drs305 said:**
> Are you running an older version of VBox? I ask because the Guest Additions I'm running (OSE) is 3.1.6.

I just reinstalled it on VBox 3.1.6 and it installed without issue (64-bit). And it runs Lucid without problems as well.

**2.2.4 version**
I get this message after I try to update to the new version:
*Error: Conflicts with the installed package 'virtualbox-2.2'*

---

### Post by drs305 on 2010-04-20
> **SVEN1 said:**
> **2.2.4 version**
I get this message after I try to update to the new version:
*Error: Conflicts with the installed package 'virtualbox-2.2'*

Yes, that is normal. You have to uninstall the current version first. It shouldn't remove your existing VMs.

---

### Post by SVEN1 on 2010-04-21
Removed older VB and installed the latest version.
Guest additions seemed to install but, will not function.

On the good side, Windows XP that I have  also running in VB, can now use all USB devices. :P

I'll try again Wednesday getting Guest additions to work in Ubuntu 9.10

---

### Post by SVEN1 on 2010-04-21
Ubuntu 9.10 now functions perfectly with 
Guest Additions in VB.

---

### Post by drs305 on 2010-04-21
> **SVEN1 said:**
> Ubuntu 9.10 now functions perfectly with 
Guest Additions in VB.

:-)

Any ideas what you did differently to get it to work (not counting the upgrade)? Or was it simply the first reboot that might have done it?

---

### Post by SVEN1 on 2010-04-21
Not sure what happened.....I re-installed Guest Additions again thru the terminal and over wrote the first install. I was able to now turn on seamless mode. But, the background disappeared. Turned off VM. Restarted my computer, then restarted VB. Everything was fine with 9.10 in VB. But, now Mint 7 and Mint 8 would not go into seamless mode, kept loosing mouse control to Mint and it would disappear. Would have to hit Control + H to turn off Mint. Managed to retreive several video off Mint. Then removed those two Mint OS from VB. They are no longer a problem.

I have been playing with 9.10 in VB and impressed, I did not see any slow down compared to 9.04, my main OS. But, I like 9.04 just as well, no real reason to update to 9.10 yet. I am using a Radeon ATI x1900xt video card and just manged to get Urban Terror video game to run half way decent again. It was pretty jittery, had to completely remove it and re-install the game a few times and adjust settings. Not sure if upgrading to 9.10 will cause problems with that card. I may want to get a GeForce card to keep on hand, before the next upgrade, just in case. Just being cautious, reading there may be problems if using an ATI card.

Thanks for suggesting removing the older VB and installing the newer version.:)

---

