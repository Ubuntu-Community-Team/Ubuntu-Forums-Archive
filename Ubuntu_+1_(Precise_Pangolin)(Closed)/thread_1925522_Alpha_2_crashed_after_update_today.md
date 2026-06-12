---
title: "Alpha 2 crashed after update today"
date: 2012-02-14
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Penguin360 on 2012-02-14
I updated my 12.04 Alpha 2 this morning, but after I reboot to complete the update, I notice when I move my mouse over the Ubuntu icon in Unity bar, the bar disappears, and all I have is a blank screen with the default Ubuntu desktop wallpaper.

Can someone help me to fix the problem?

Thanks,

---

### Post by redcylon on 2012-02-14
I guess you did a partial-upgrade?

---

### Post by Penguin360 on 2012-02-14
No, I didn't do partial upgrade.

---

### Post by redcylon on 2012-02-14
If you run another Update-Manager does it offers you any other updates?

---

### Post by Gregory Lee on 2012-02-14
I had a crash today with Alpha 2, also, soon after an update.   My screen froze, mouse movements or clicks had no effect, no response from keys on keyboard.  It's comforting for me to hear about your crash, because it makes more likely that my crash was due to the system software rather than my nice brand new shiny computer hardware.

I rebooted and for the last hour and a half have seen no further problem.  Fingers crossed.

---

### Post by redcylon on 2012-02-14
I've had the same thing happened to me, though it was updates after I did a fresh install. When I ran another Update-Manager there's a bunch of Unity related files which I cannot update, though it did came out in Update Manager.

Common sense prevails that you wait till all relevant files are there. But I do not wanna wait, hence this is what I did (...I bear no responsibilities for this though)

1. sudo apt-get update && sudo apt-get upgrade

or 


2. as for me I went straight Unity 5.4 testing at [http://ubuntuforums.org/showthread.php?t=1925433](http://ubuntuforums.org/showthread.php?t=1925433)

---

### Post by Gregory Lee on 2012-02-14
> **redcylon said:**
> Common sense prevails that you wait till all relevant files are there. But I do not wanna wait, hence this is what I did (...I bear no responsibilities for this though)

Of course, we understand it wasn't your fault, but rather was due to an impetuous and impatient nature.

But my crash wasn't due to a partial update or testing the newest software, because I did neither.

---

### Post by redcylon on 2012-02-14
> **Gregory Lee said:**
> Of course, we understand it wasn't your fault, but rather was due to an impetuous and impatient nature.

But my crash wasn't due to a partial update or testing the newest software, because I did neither.

I'm not saying you did, it just when running an update manager certain files are updated which may conflicts with Unity. 

If you run another update manager, you may see a newer version of Unity. However it wasn't available for update ( check boxes were unticked).

Common sense prevails meant, therefore you wait for proper files uploaded to the repos. Hence it wise to wait, but I didn't. As such the comments were meant to those who wants to go ahead and dist-upgrade. 

I did just that and have a working desktop.

p/s: This is a test release. Hence when updating we're actually testing the newest software

---

### Post by Penguin360 on 2012-02-15
Because all icons are gone after the crash, press Alt+f2 does not do anything, I have to press Ctrl+Alt+f2 to log into the text mode, then run update command. But the message says: The following packages have been kept back: compiz compiz-core compiz-gnome .... and more packages.

Can someone help me?

Thanks a lot.

---

### Post by dino99 on 2012-02-15
via synaptic: purge ALL the related installed compiz packages, then reinstall compiz

---

### Post by Penguin360 on 2012-02-15
> **dino99 said:**
> via synaptic: purge ALL the related installed compiz packages, then reinstall compiz

Thanks. I removed compiz via sudo apt-get remvoe compiz*, then when I try to reinstall compiz, it gives me an unmet dependency error:
utouch-compiz: Depends: compiz-core-abiversion-20220703 but it is not installable
E: unable to correct problems, you have held broken packages.

What should I do now?

---

### Post by dino99 on 2012-02-15
> **CodingBeaver said:**
> 

What should I do now?

Read, understand then do what i said :)
You have done something different, if synaptic is not yet installed, then:

sudo apt-get install synaptic
sudo synaptic

on top bar, use "quick search" field about compiz, then "purge" (complete remove) by right clicking on each packages to purge.

---

### Post by Penguin360 on 2012-02-15
> **dino99 said:**
> Read, understand then do what i said :)
You have done something different, if synaptic is not yet installed, then:

sudo apt-get install synaptic
sudo synaptic

on top bar, use "quick search" field about compiz, then "purge" (complete remove) by right clicking on each packages to purge.

Sorry:oops:

The thing is I don't have any UI, all I have now is to use command in the text mode. But anyway, I will install synaptic as you said and give it another try.

Thanks.

---

### Post by redcylon on 2012-02-15
I'm not sure about your case, but in mine I still able to logs in via Unity 2D...hence available working gui.

---

### Post by Gregory Lee on 2012-02-15
Mine just crashed again.  Orange screen with thin light vertical lines -- does anyone know the significance of that screen?  No response from mouse or keyboard (including ctl-alt-backspace and ctl-alt-del), leaving nothing to do but hit the power switch and reboot.  After the reboot, everything seems normal.  No new files in /var/crash/.  I can't exclude bad hardware.

---

### Post by Penguin360 on 2012-02-16
Ok, I think I fixed the problem, though I still don't know how I did it :oops:

First, I installed Synaptic in the text mode, then I reboot my pc and then login by using Unity 2D so I can have graphic UI. In Synaptic, under Status -> Installed(Upgradable), I removed all packages under it, then click Apply. After all packages were all removed, I re-installed them. Then ran Update Manager to install new updates, after that, reboot into Ubuntu session (not Unity 2D), and now everything is fine now. Hope it will stay and no crash...

---

