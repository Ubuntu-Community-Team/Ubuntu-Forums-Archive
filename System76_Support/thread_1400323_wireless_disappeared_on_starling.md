---
title: "wireless disappeared on starling"
date: 2010-02-06
forum: System76 Support
---

### Post by smulloni on 2010-02-06
I had run my starling (which is still running Jaunty) on battery until it completely ran out and it powered down, at which point I charged it back up and restarted it.   It came up without the wireless light on.  I tried toggling the wireless switch once to the right and rebooting; no luck.  (I tried this multiple times.)  

Works fine with a wired connection.  The usual recovery procedure Tom has suggested on these forums involves re-installing the system76 driver, which we can't do right now due to the website outage.

Any suggestions about how I can get this back up and running?

Thanks!

Jacob S.

---

### Post by satsujinka on 2010-02-06
I don't remember what card the starling has, but (and this is massively _**unsupported**_, so backup your current system) you could try seeing if [sidux]("http://sidux.com/") can get your card running. Their hardware support is quite good and part of their installer will detect any firmware you may need. So what I would do (if you can't wait for the site to comeback up) would be backup your ubuntu install, install sidux (as well as any recommended firmware, you'll need to have the ethernet connected for this,) and see if your card works then. Then once system76's site is back up you can restore your backup.

---

### Post by smulloni on 2010-02-06
Actualy, I was looking for a solution more minimal than installing a new OS.:)

I rebooted again and choose an older kernel, and it worked.  The last update I installed must have upgraded the kernel without my noticing.  

So, is it the case that every time the kernel is updated, we should re-run the system76 driver?

---

### Post by black_ice=cream on 2010-02-06
I updated my kernel today with absolutely no trouble, and I didn't have to run any S76 driver.

---

### Post by pemadorje on 2010-02-06
I am experiencing the same issue although I am running Karmic. I installed the kernel update last night (2.6.31-19) and now my wireless doesn't work. I've tried reinstalling the System 76 driver, toggling the switch in front to the right (with reboot) and none of it makes a difference. I can however start with an older kernel (2.6.31-17) and get wireless to work again.

---

### Post by black_ice=cream on 2010-02-06
weird. Everything went fine for me when upgrading my kernel. Try something simple: Update Manager > 'Check' And then System76 Driver > 'Install' Tab > 'Install' button. Try that. That's how I fixed my wireless in Jaunty a long time ago. Let me know what happens.

---

### Post by pemadorje on 2010-02-06
> **black_ice=cream said:**
> weird. Everything went fine for me when upgrading my kernel. Try something simple: Update Manager > 'Check' And then System76 Driver > 'Install' Tab > 'Install' button. Try that. That's how I fixed my wireless in Jaunty a long time ago. Let me know what happens.


I've tried the 'restore' tab of the driver several times but hadn't tried the 'Install' before.... So I just tried it, as you suggested, but there's no difference. New kernel has no wireless, but the old does. It is weird, the wireless light is off, and if I click the network connection icon in the panel, it only shows and option for 'wired connection' and 'VPN connections'. It doesn't even display anything about wireless. 

Glad I can at least get things working with the old kernel though... but I hope an update or solution is forthcoming from System 76.

---

### Post by satsujinka on 2010-02-06
> **smulloni said:**
> Actualy, I was looking for a solution more minimal than installing a new OS.:)

I rebooted again and choose an older kernel, and it worked.  The last update I installed must have upgraded the kernel without my noticing.  

So, is it the case that every time the kernel is updated, we should re-run the system76 driver?

Yes, well... I'm not particularly familiar with how the system76 drivers work, but I figured that if you're desperate enough then any help is better than no help. Though if I was dependent on the system76 drivers, I'd probably find a way to get the drivers into my home folder so that I know where they are and can learn how they work... which I'll probably have to do once I do get a system76 laptop since I'm extremely fond of Arch linux (so yes, I recommended an OS I don't even use to solve your problem:P but I have used it in the past.)

---

### Post by black_ice=cream on 2010-02-07
> **pemadorje said:**
> I've tried the 'restore' tab of the driver several times but hadn't tried the 'Install' before.... So I just tried it, as you suggested, but there's no difference. New kernel has no wireless, but the old does. It is weird, the wireless light is off, and if I click the network connection icon in the panel, it only shows and option for 'wired connection' and 'VPN connections'. It doesn't even display anything about wireless. 

Glad I can at least get things working with the old kernel though... but I hope an update or solution is forthcoming from System 76.

I think it's particularly strange that it **does** work in the old kernel but not the new. I wonder if there's any way to reinstall the new kernel. I'm not exactly an expert with this and don't really know how to do that, but if anyone does I'm sure that'd be worth a try... let me know what happens

---

### Post by Eyore15 on 2010-02-07
> **black_ice=cream said:**
> I think it's particularly strange that it **does** work in the old kernel but not the new. I wonder if there's any way to reinstall the new kernel. I'm not exactly an expert with this and don't really know how to do that, but if anyone does I'm sure that'd be worth a try... let me know what happens

Wasn't part of the problem with the karmic update that the kernel did strange things to our systems?  It seem that part of the discussion was that they were making efforts to have all the necessary configuration in the new kernel.  Maybe that didn't happen and we're stuck with running th older kernel?

---

### Post by Eyore15 on 2010-02-07
> **black_ice=cream said:**
> I think it's particularly strange that it **does** work in the old kernel but not the new. I wonder if there's any way to reinstall the new kernel. I'm not exactly an expert with this and don't really know how to do that, but if anyone does I'm sure that'd be worth a try... let me know what happens

Wasn't part of the problem with the karmic update that the kernel did strange things to our systems?  It seem that part of the discussion was that they were making efforts to have all the necessary configuration in the new kernel.  Maybe that didn't happen and we're stuck with running th older kernel?

---

### Post by Eyore15 on 2010-02-07
> **black_ice=cream said:**
> I think it's particularly strange that it **does** work in the old kernel but not the new. I wonder if there's any way to reinstall the new kernel. I'm not exactly an expert with this and don't really know how to do that, but if anyone does I'm sure that'd be worth a try... let me know what happens

From the original note about the site outage ... This will also keep the System76 Driver from running, as it pings our website to determine that there is an Internet connection ...

might be why the new kernel/driver is having problems?

---

### Post by pemadorje on 2010-02-07
The site is up now and I'm able to connect fine. I've tried reinstalled the System 76 drivers again but get the same result. No wireless in new kernel, Wireless with old kernel. It still seems to me that something in the new kernel is breaking the wireless (especially when considering the other recent Starling kernel/driver/wireless issues). But then again, it doesn't make sense why this is affecting some but not others.

---

### Post by smulloni on 2010-02-07
In my case, I was able to get wireless working with the new kernel once I was ble to run the system76 driver again.  Good luck, pemadorje!

---

### Post by pemadorje on 2010-02-07
That's good news smulloni. I'm glad you're back in business. I guess if I am the only one experiencing this, then maybe something did get jacked up when I was upgrading when the site was down. I guess I'll try a reinstall of the OS.

---

### Post by pemadorje on 2010-02-08
Well, I have no idea what happened but I am back in business now too. Whether it was completely necessary or not, I did a reinstall and a restore of the System 76 drivers and now all is fine.

---

### Post by rlauzon on 2010-02-14
In my case, I got the network back by 
1. Reinstalling the System76 drivers.
2. After rebooting, going into System -> Administration -> Hardware drivers and DEACTIVATING the wireless hardware driver.
3. Powering all the way down.
4. Rebooting, then reactivating the wireless hardware driver.
5. Then moving the wireless switch to the LEFT (in my case /var/log/messages was reporting that the radio was off, so I turned it back on).

---

### Post by ants280 on 2010-03-02
Yay!  That was the fix for me (At least my networking started working after I did that (and it failed), did some other stuff posted on the forums, and did it again.

I got my starling the other week and really like it.

+rep

---

