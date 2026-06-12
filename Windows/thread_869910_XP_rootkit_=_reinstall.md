---
title: "XP rootkit = reinstall?"
date: 2008-07-25
forum: Windows
---

### Post by Paqman on 2008-07-25
My girlfriend dualboots XP on her Ubuntu laptop. Yesterday she got suckered by some social engineering and installed a trojan. Thank god for being dual-boot and being able to get in and salvage her data off the Windows desktop!

Looks like it's installed more trojans, a vast army of spyware and *dramatic music* a rootkit!

So, given that security has been well and truly compromised, would it be a waste of time to try and clean it up? Or should I just bite the bullet and embark on the tedious odyssey that is a Windows reinstall?

---

### Post by Kernel Sanders on 2008-07-25
Windows reinstall. It's the only safe way.

You should think about anti-virus for your xp partition in future though!

---

### Post by sp0nge on 2008-07-25
your Ubuntu files should be ok, but I would most certainly NOT use the window$ partition for anything. If you can't convince her to ditch window$ all together, definitely re-install!

---

### Post by fiddledd on 2008-07-25
> **Kernel Sanders said:**
> Windows reinstall. It's the only safe way.

You should think about anti-virus for your xp partition in future though!

Agreed, and I would also suggest running as a Limited User.

---

### Post by insane_alien on 2008-07-25
all rootkits require reinstallation of the affected operating system. it is the only way to be sure.i'd  also scan the files you rescued off the infected partition.

this is why you make backups.so you don't need to have the risk of rescueing an infected file.

---

### Post by Paqman on 2008-07-25
> **Kernel Sanders said:**
> 
You should think about anti-virus for your xp partition in future though!

Dude, if it didn't have antivirus installed already, how would I know it was infected? ;)

She was tricked into clicking on a .exe, the worrying thing is that Avast didn't detect the infection until some time later. I'm guessing it never detected the original trojan, and only raised the alarm when it started to bring in it's grubby little friends.

---

### Post by Paqman on 2008-07-25
> **sp0nge said:**
>  If you can't convince her to ditch window$ all together, definitely re-install!

No convincing required, she likes Ubuntu. She just needs to dualboot Windows for work (Access databases, etc)

> **insane_alien said:**
> i'd  also scan the files you rescued off the infected partition.


Done, also the USB stick that was connected at the time, etc, etc.

Really kicking myself for never imaging her Win partition after the last reinstall. When will I learn? :)

---

### Post by insane_alien on 2008-07-25
> **Paqman said:**
> Really kicking myself for never imaging her Win partition after the last reinstall. When will I learn? :)

Now hopefully.

---

### Post by Paqman on 2008-07-25
> **insane_alien said:**
> Now hopefully.

We live in hope :)

Cheers for the help guys. I suspected the reinstall might be necessary, and in fact compared to grinding through a scan on every AV product under the sun, it's probably the quicker option.

---

### Post by Parp on 2008-07-25
Do a Google for Sophos Anti-Rootkit.....  seems to remove most rootkits fine (i've used it a few times on family's PCs), you'll need to disable system restore first though.

Worth a go first before wiping and re-installing..

---

### Post by uidb4056 on 2008-07-25
> **Paqman said:**
> No convincing required, she likes Ubuntu. She just needs to dualboot Windows for work (Access databases, etc)



Done, also the USB stick that was connected at the time, etc, etc.

Really kicking myself for never imaging her Win partition after the last reinstall. When will I learn? :)

May be you can found Virtualbox a good option to avoid dual boot, in this way she can work in Windows without having to reboot. In the repositories there are the OSE version of VirtualBox (open source without support for USB) or you can get the binary from VirtualBox at [http://www.virtualbox.org/](http://www.virtualbox.org/) Even is not open source is free and has support for USB.

---

### Post by nerd0795 on 2008-07-25
F-Secure BlackLight Rootkit revealer is good, but you have to becareful.  (I heard good things about it) it list's all hidden objects including safe ones so do a google search or use a security forum to find which ones to rename then delete.  There are alot of other good ones.

---

### Post by Paqman on 2008-07-26
> **uidb4056 said:**
> May be you can found Virtualbox a good option to avoid dual boot

Not really an option on a 1.5GHz Celeron with 512MB, but cheers anyway.

Reinstall is done. Not really a fun way to spend a Friday night, but at least I can be certain it's not another happy zombie in somebody's botnet.

---

### Post by damis648 on 2008-07-26
> **Paqman said:**
> Not really an option on a 1.5GHz Celeron with 512MB, but cheers anyway.

Reinstall is done. Not really a fun way to spend a Friday night, but at least I can be certain it's not another happy zombie in somebody's botnet.

Yep. And the old installation in Windows' Heaven. ...or is there really Such a thing as Windows Heaven?

---

### Post by seanc7 on 2008-07-26
You can try the rootkit scanner/removal route but in the long run, reinstalling Windows will be the easier approach.

Have you thought about setting up her Windows install in a virtual machine?

---

### Post by darco on 2008-07-26
Yes reformatting is the easiest and quickest way but too many "desktop" techs use this as their first and only option. I like to do it the hard way and have returned my clients pc is great shape w/o losing any data. I havent run across any rootkits yet so maybe in that instance I would have no choice but to reformat. 

darco

---

### Post by K.Mandla on 2008-07-27
Moved to Windows Discussions.

---

### Post by Paqman on 2008-07-29
> **darco said:**
> Yes reformatting is the easiest and quickest way but too many "desktop" techs use this as their first and only option. 

Tbh, Windows really benefits from a reinstall every 12 months or so anyway, so you can't rally blame them.

---

### Post by flameproof on 2008-10-13
After I re-install Xp, don't I have to re-install also the 100 programs I run?

---

### Post by seanc7 on 2008-10-13
Regardless of the OS, if you get a rootkit, the only sure way is to format and reinstall.

If I found a rootkit installed in Linux, I'd reinstall it in a heartbeat. You just don't know if it's all truly removed or not.

---

### Post by smoker on 2008-10-14
> **flameproof said:**
> After I re-install Xp, don't I have to re-install also the 100 programs I run?

yes, you will have to reinstall all your applications, which is why making a backup image of the partition is the easiest and quickest way to get a system back up and running again.

---

### Post by Thelasko on 2008-10-15
> XP rootkit=reinstall?
YES!


P.S. While you're at it, set her up as a limited user so it doesn't happen again.

---

### Post by ww711 on 2008-10-15
> **Thelasko said:**
>  set her up as a limited user so it doesn't happen again.

+1

Also educating the user about basic computer security and being socially engineered, will reduce the likely hood of a repeat.

---

### Post by Paqman on 2008-10-30
> **Thelasko said:**
> YES!


P.S. While you're at it, set her up as a limited user so it doesn't happen again.

Limited users are pretty pointless though. Sure it's more secure, but you also can't do anything useful. I'm inclined to think it was a setting aimed at small children, since one of XPs design goals was to make it usable by a 3-year old.

---

### Post by seshomaru samma on 2008-10-30
> **Paqman said:**
> Limited users are pretty pointless though. Sure it's more secure, but you also can't do anything useful. I'm inclined to think it was a setting aimed at small children, since one of XPs design goals was to make it usable by a 3-year old.

Of course you can
You can even install programmes by right clicking on them and "run as" (that as if you enable the 'server' service which is usually set to automatic be default) 
I installed many XPs with limited users, coupled with Firefox/no-script, a detailed Hosts file, a good firewall and a few tweaks,  they rarely get infected.

---

### Post by Paqman on 2008-10-30
> **seshomaru samma said:**
> 
I installed many XPs with limited users, coupled with Firefox/no-script, a detailed Hosts file, a good firewall and a few tweaks,  they rarely get infected.

Got a copy of your hosts file and these "tweaks"?

---

### Post by seshomaru samma on 2008-11-05
> **Paqman said:**
> Got a copy of your hosts file and these "tweaks"?

sure
[here ]("http://forums.windowsforum.org/index.php?showtopic=33716")
notice that there are updates to the hosts file on the 2nd page

edit> I don't use all the tips there. i do the hosts file, opera as browser, IP Port Filtrations, Use IP security policies, security registry hacks and plenty of anti-malware programmes (NOD32 as anti virus or if no money then AVG)

---

### Post by farmer ck on 2008-11-05
Before reinstalling windows you may want to try a program called combofix. I have used it to clean up a few xp installs.

---

### Post by perspectoff on 2008-11-06
Don't feel bad. Our corporate environment that has XP Pro was crippled by rootkits in early 2008.

(Note: Skype was known to propagate rootkits on Windows machines in early 2008).

Every one of those Windows computers required a full re-install. There is no way to salvage a Windows computer crippled with a rootkit.

However, we decided to go with Kubuntu (Hardy Heron) instead and are now converting the whole organization to an Ubuntu / Kubuntu basis.

What a great decision!

> **Paqman said:**
> My girlfriend dualboots XP on her Ubuntu laptop. Yesterday she got suckered by some social engineering and installed a trojan. Thank god for being dual-boot and being able to get in and salvage her data off the Windows desktop!

Looks like it's installed more trojans, a vast army of spyware and *dramatic music* a rootkit!

So, given that security has been well and truly compromised, would it be a waste of time to try and clean it up? Or should I just bite the bullet and embark on the tedious odyssey that is a Windows reinstall?

---

### Post by perspectoff on 2008-11-06
.

---

### Post by gimmejimmy on 2008-11-08
> Tbh, Windows really benefits from a reinstall every 12 months or so anyway, so you can't rally blame them.

Not true.  That Windows slows down over time is a myth.  I haven't reinstalled XP in over two years with no noticeable slowdown.  And yes, I do install a lot of apps and even edit the registry.
If you're sure you have a rootkit then a wipe and reinstall is the only option.  But I do agree that too many so-called 'techs' use it as their first option, sometimes without even taking a look.

---

### Post by Thelasko on 2008-11-10
> **gimmejimmy said:**
> Not true.  That Windows slows down over time is a myth.  I haven't reinstalled XP in over two years with no noticeable slowdown.  And yes, I do install a lot of apps and even edit the registry.
If you're sure you have a rootkit then a wipe and reinstall is the only option.  But I do agree that too many so-called 'techs' use it as their first option, sometimes without even taking a look.

I agree, XP doesn't slow down over time.  However, the Windows 9X family did.  I think people reinstall XP every 6-12 months because that's what they used to do with 9X.

Also, most computer repair shops aren't interested in finding the root cause, they only care about getting the machine fixed as fast as possible.  A complete reinstall yields the fastest turn around, so that's what they do.

---

