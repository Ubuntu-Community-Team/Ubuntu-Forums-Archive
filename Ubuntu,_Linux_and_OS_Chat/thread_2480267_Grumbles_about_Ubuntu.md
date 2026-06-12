---
title: "Grumbles about Ubuntu"
date: 2022-10-23
forum: Ubuntu, Linux and OS Chat
---

### Post by digitronics on 2022-10-23
Migrated completely from Windows to Linux at home early spring this year, to get away from all the Windows issues (*security, speed, flawed updates etc.*). After checking different distributions with intended software, including the whole Debian/Buntu family, I chose Lubuntu and Linux Mint was the runner up. In total, it seems to be a '*from bad to worse*' case.

Why? Quite soon, I learned that system updates in Buntu ...

[LIST]
[*]... often causes emergency mode at boot. [SUP]***[SIZE=1]not.1[/SIZE]***[/SUP][SIZE=2] I only found this thread today[/SIZE] and I think that some of it should be included in the installation procedure as options, even though the installation procedure should follow the KISS concept as much as possible. 
[*]... are not possible to disable completely. The occurring reboot prompt due to forced **secret** [critical?] system updates [SUP]***[SIZE=1]not.2 [/SIZE]***[/SUP]appears now and then anyway, despite being completely turned off in the settings. If updating specific software, I have to enable parts of the settings and soon, I will have a forced system update as a result, despite turning it off immediately afterwards. **[COLOR=#ff0000]It shouldn't work like that ...[/COLOR]** This reminds me about Samsung Android devices that keeps nagging about 'updating', despite updates being turned off (*leading to the thought that the update can't be good ...*). 
[/LIST]
 
If it was limited to only one computer, fine, but this occurs on **all** of my  (*13*) computers, so it is a software (*OS*) issue and not related to hardware. My intention with my computers is to set them up with needed software, getting them into work and leave them alone 24/7/365. So far, I have been forced to invest in a lot of work keeping them all running properly. In Windows, a situation like this will cause a forced reboot sooner or later. That's often problematic regarding the running software - lost work. I'm not sure yet if same apply in Buntu, but I will not test it. In Windows, the software auto start at boot, but not in Buntu. I'm not checking the computers every day, so ... This 'maintaining' has been almost at a weekly basis and it doesn't occur in all computers at the same time, despite being set up in groups.  Finding help on the Internet? Well, it isn't straight forward, as most  available 'advices' are outdated and in some cases with the correct OS  version, it doesn't work anyway ... So my alternatives are ...


[LIST]
[*]... stick with present situation. This is getting tiring and one answer to why Linux never will be widely used for private use. The knowledge threshold is sooner or later way too high for common people to deal with. A quite different situation to choosing a Windows or Apple system. As a 'newbie' to Linux, but not computers (*36 years*), I still have a lot to learn ... 
[*]... migrate back to Windows and accept all of its issues. The software will be running fine, but slow (*interfered by the OS*). Btw, the last decent and fastest version was (*is*) 7 x64 Pro SP2 and now sabotaged by Microsoft ... Subsequent versions are junk. So, no go ... 
[*]... migrating to a non Debian/Buntu distribution, but that require a lot of time consuming work to make the software (*BOINC*) work or it's not supported. So, no go ... 
[*]... give up my 'sidetrack' hobby and sell all my abundant hardware. Well, I'm considering this ... 
[/LIST]
  

***[SIZE=1]not.1[/SIZE]*** This  also happens when adding a new internal hard drive (*when using GRUB*) or replacing a  faulty GPU with the same brand and model. So far, the easiest way I found to fix  this, is to reinstall the Buntu on top of the old one, without formatting the partition of concern.  Most software needs to be reinstalled too (*and the usual removal of bloatware*). **I realised that personal data is not affected by this procedure. It remains intact.** I have not found a way to 'prepare' the GRUB ahead and I'm not interested to mess with it, as it seems to have similar issues as the Windows boot manager. In general, I'm avoiding GPT/GRUB(*2*), due to the bugs involved and use legacy boot instead - faster boot and less problems involved. In some of my computers, I have been refused to install Buntu in legacy mode. This is interesting, as my last six purchased computers have the exact same hardware spec's and BIOS settings, two of them was refused legacy boot. The very same install medium was used for all of them. The last computer that crashed (*part of the group of the last six*) after forced 'update', had a working legacy boot and at re-installation, GPT/GRUB was forced onto the hard drive without my acceptance. **[COLOR=#ff0000]Again, it shouldn't work like that ...[/COLOR]** I have noticed that the options at the hard drive configuration page varies and sometimes the desirable one is missing, just like in mentioned cases.

 ***[SIZE=1]not.2[/SIZE]*** Just like on Android and Windows, it's hard to know what's actually updated when automated/hidden and forced updates occurs. (*In a way, that's a security issue!*) From an experiential point of view, Android and Windows updates are not always good ones, but sometimes 'dirty'. Does the same apply to Debian/Buntu too? Any way, obviously some of them don't work ...

---

### Post by QIII on 2022-10-23
Moved to its own thread.

This is the second hijack you have had moved to its own thread.  Please don't add a third.

This post was originally added to a solved thread that had not been replied to in a very long time.  That thread is now closed.

This post rates as a chat because there are no direct requests for support.

If you have support requests, please start a new thread for each one, one subject per thread, in a support area of the forums.

---

### Post by digitronics on 2022-10-24
1. It's not a support request nor a hijack! It's just a description of my situation and concerned flawed updates, but forgot to mention that some of what I described relates to upgrades too. When I upgraded from 20.04 to 20.10, I got the 'emergency mode' issue on several of my computers, but not all of them. By checking Internet for answers, I come to realise that any version xx.10 installs/upgrades should be avoided, due to bugs. My systems are now running either 22.04 LTS or 22.04.1 LTS. Next possible upgrade will be 23.04, so I skip 22.10, like I did with 21.10.

2. I do place comments in relevant threads. This forum is a mess, so I'm not wasting hours finding the 'proper' thread. I'm dyslectic, so badly written language makes it even more difficult to read anything on the forum (*which includes your comment here, as you skipped all required commas in three of the sentences ...*).

3. If a thread is closed, logically, it would **not** be possible make any new comments, but it is ... Moderators on other forums (*using vBulletin*) manage this. Why not here?

---

### Post by kurt18947 on 2022-10-24
I view any Ubuntu release except LTS as a development release. I don't know if Canonical does but 9 months support rather than 5 (or 10) years support should be indicative. I am running 22.04.x on most machines, my next upgrade may be 24.04.1 the next LTS release. The only time I would use a non-LTS release is if I had hardware that was supported by the non-LTS version but not the LTS version. 

I've tried Lubuntu on old/low end hardware (its target market) and it worked but didn't seem as polished is Ubuntu or Mint. Many people don't do in-place upgrades between versions. I did do an in-place upgrade on this machine 20.04 to 22.04 and it mostly worked but had some issues. If I had created a separate home partition (I didn't) it would be pretty trivial to reinstall the OS between LTS releases. 

Bear in mind that many posters here are not native English speakers. I am certain that native Mandarin or Hindi speakers' English grammar posting here is better than my Mandarin or Hindi (I don't speak either).

---

### Post by grahammechanical on 2022-10-24
I am unfamiliar with the Lubuntu system settings utilities. On Ubuntu we can set "check for updates" to "Never." I do not think it is possible to disable checks for security updates. In my opinion it would be irresponsible for a developer of an operating system to allow the user to prevent notification of the availability of security updates. I also think that it is irresponsible for a user to run an OS that has not had the latest security fixes installed. Especially if the machine is being connected to the internet.

Regards

---

### Post by mastablasta on 2022-10-25
> **digitronics said:**
> 

Why? Quite soon, I learned that system updates in Buntu ...

[LIST]
[*]... often causes emergency mode at boot. [SUP]***[SIZE=1]not.1[/SIZE]***[/SUP][SIZE=2] I only found this thread today[/SIZE] and I think that some of it should be included in the installation procedure as options, even though the installation procedure should follow the KISS concept as much as possible
[/LIST]



even with problematic HW on one mascine (issue with sound chip) this was never the case. so far i had the following CPU/GPU combos: AMD+ATI later turned into Intel+ATI (yes, the old one), AMD+AMD (2 laptops), intel+AMD discrete chip (laptop), intel only, AMD+Nvidia (3 PCs); in addition i also run a headless (no monitor) HP server and a RapsberryPI

> 

[LIST]
[*]... are not possible to disable completely. The occurring reboot prompt due to forced **secret** [critical?] system updates [SUP]***[SIZE=1]not.2 [/SIZE]***[/SUP]appears now and then anyway, despite being completely turned off in the settings. If updating specific software, I have to enable parts of the settings and soon, I will have a forced system update as a result, despite turning it off immediately afterwards. **[COLOR=#ff0000]It shouldn't work like that ...[/COLOR]** This reminds me about Samsung Android devices that keeps nagging about 'updating', despite updates being turned off (*leading to the thought that the update can't be good ...*).
[/LIST]
 


it is possible to turn off updates. in fact you can lock each application or library to certain version. there are no "secret" updates, everything is logged in linux including how updates went, what if any issues occurred etc. same goes for system boot. you can see what went wrong, why it went to emergency mode etc. 
check:
var/log/

or use a log viewer.

on server i use:
daily automatic security updates
manual other updates - but receive a message they exist

on desktops we use manual updates only, but system check once a day for updates. usually we would do them immediatelly upon boot or as soon as we can (e.g. blue dot is other and can be ignored a bit; red dot we immediately trigger).

---

