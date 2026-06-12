---
title: "Can viruses on windows drive affect ubuntu drive?"
date: 2008-10-26
forum: Security
---

### Post by madsc89 on 2008-10-26
I've dicided to run mainly ubuntu, but to keep Windows on another drive. This because I can't seem to get playable fps on windows games through wine.
I intend to make a fresh instalation on my windows drive and use it only for games. I'm wondering if I could easily skip antivirus and firewall on windows.
Is there viruses that for example format my other drive, screwing up ubuntu?
Is it likely to get viruses when almost only using Steam on that windows install (a windows question)?

Thank you


_Answer:_

They can if you have installed the driver to let windows access your ubuntu drive. As described in one of the latter post on page 2.

You also **must** have AV and similar if you're connected to the net.

---

### Post by Xiong Chiamiov on 2008-10-26
If you are connected to the internet on a Windows machine, you need (at least) antivirus protection.

There are always viruses in the wild that exploit undiscovered vulnerabilites, so even if your machine is fully patched, you can still be caught with your pants down.

If you don't wish to pay for an antivirus, I highly recommend avast!.

---

### Post by scorchgeek on 2008-10-26
It's unlikely that a Windows virus could affect your Linux installation, but I would still highly recommend installing antivirus software under Windows if you're going to be connected to the Internet. It is, however, generally agreed that you don't need any antivirus for Linux.

---

### Post by lukjad on 2008-10-26
I have heard of some viruses that render the DRIVE inoperable, But I'm not sure if that's because they infect the MBR or something else. I'll try to find out.

---

### Post by Paqman on 2008-10-26
I have a Windows install that I use only for gaming. It probably connects to less than ten servers, all of them owned by trustworthy companies.

Nevertheless, I have antivirus installed. There's no way i'd ever let a Windows machine connect to the net without it. You could argue that the CPU cycles could be better used for your games, but you could also argue that they're better used running antivirus than they are acting as a zombie in somebody's botnet.

Viruses which cause damage to your system are extremely rare. What would be the point? Most successful viruses are designed to deliver a useful payload once they infect you. What use is trashing your system?

---

### Post by HereInOz on 2008-10-26
The other issue is that you are probably running a dual boot situation, where you install Windows first and then Ubuntu.  If this is the situation, and your Windows install gets broken, you will not be able to re-install the Windows partition without also re-installing Ubuntu.

So if a virus breaks your Windows install, and you need to re-install Windows, it is a full rebuild from a clean disk, Ubuntu and all.

---

### Post by howefield on 2008-10-26
> **HereInOz said:**
> ..you will not be able to re-install the Windows partition without also re-installing Ubuntu...

not exactly, you could reinstall grub after the windows install.

---

### Post by lisati on 2008-10-26
Having protection against [malware]("http://en.wikipedia.org/wiki/Malware") is always a good idea, even though it's more likely to hurt Windows than Linux. The best defense is a dose of good sense followed by having some kind of defenses installed on the computer you're using. I've had more problems from my own stupidity and ignorance than from malware. This hasn't stopped the virus writers from trying though, with only one or two times where I got caught out by a "present" I got through the internet.

> **HereInOz said:**
>   If this is the situation, and your Windows install gets broken, you will not be able to re-install the Windows partition without also re-installing Ubuntu.

So if a virus breaks your Windows install, and you need to re-install Windows, it is a full rebuild from a clean disk, Ubuntu and all.

> **howefield said:**
> not exactly, you could reinstall grub after the windows install.

It can be done: Just reinstalled XP on my laptop without damaging Ubuntu (messed up some settings while tinkering with my home network and a "brute force" reinstall seemed easiest)
There's quite a few threads dealing with getting *ubuntu and grub back in business after uninstalling and/or re-installing Windows e.g. here: [http://ubuntuforums.org/showthread.php?t=959106](http://ubuntuforums.org/showthread.php?t=959106)

---

### Post by madsc89 on 2008-10-27
Thank you all fr good and quick replies!
I'll definitely install AV on my fresh windows install. I'm currently using AVG internet security (which is AV, anti malware, firewall and everything else you're supposed to need), but I think I've experienced both Avast and Avira needing less resources. The question is if I need to replace the windows firewall, and add some anti malware or similar. Remember that I will only use it for gaming and I use common sense about unknown files etc. Is it perhaps best to keep the AVG all-in-one package? 

> **lukjad007 said:**
> I have heard of some viruses that render the DRIVE inoperable, But I'm not sure if that's because they infect the MBR or something else. I'll try to find out.
I got to thinking, and I would guess that this isn't that dangerous, considering that windows can't even find the ubuntu drive.

> **HereInOz said:**
> The other issue is that you are probably running a dual boot situation, where you install Windows first and then Ubuntu.  If this is the situation, and your Windows install gets broken, you will not be able to re-install the Windows partition without also re-installing Ubuntu.

So if a virus breaks your Windows install, and you need to re-install Windows, it is a full rebuild from a clean disk, Ubuntu and all.
Remember that Windows and Ubuntu are on two completely different hard drives. I find it hard to believe that formatting one would ruin the other.

Thanks to the ones I didn't quote, as well!

---

### Post by madsc89 on 2008-10-28
bump

---

### Post by lukjad on 2008-10-28
The GRUB Boot Loader is in sector Zero, as is the MBR. If one is damaged, both will be. At least, so I hear.

---

### Post by bodhi.zazen on 2008-10-28
> **madsc89 said:**
> I've dicided to run mainly ubuntu, but to keep Windows on another drive. This because I can't seem to get playable fps on windows games through wine.
I intend to make a fresh instalation on my windows drive and use it only for games. I'm wondering if I could easily skip antivirus and firewall on windows.
Is there viruses that for example format my other drive, screwing up ubuntu?
Is it likely to get viruses when almost only using Steam on that windows install (a windows question)?

Thank you

The best solution would be to physically disconnect from the network when you boot windows.

If you connect to the internet with windows, you absolutely need antivirus and firewall and anything else you can think of to protect yourself.

viruses can infect your linux drive if you have it mounted with a driver or network share. This would do nothing to Ubuntu mind you as they will not run on Linux.

And you can have irreparable damage to the system, but 99% of the time you would be able to recover Ubutnu.

---

### Post by madsc89 on 2008-10-29
> **bodhi.zazen said:**
> The best solution would be to physically disconnect from the network when you boot windows.

If you connect to the internet with windows, you absolutely need antivirus and firewall and anything else you can think of to protect yourself.

viruses can infect your linux drive if you have it mounted with a driver or network share. This would do nothing to Ubuntu mind you as they will not run on Linux.

And you can have irreparable damage to the system, but 99% of the time you would be able to recover Ubutnu.

Sadly, I can't disconnect from the network as I play online multiplayer games.

What do you do you mean "mounted with a driver or network share"? Are those some options to enable other computers to connect to Ubuntu?

I am aware that Linux based operating systems do not need AV, but I'm wondering if there is a danger of my ubuntu hard drive might be accessed and messed up through my other Windows drive. Or do you for example need to enter ubuntu -username and -password to change anything on that drive?
I'm going to use AV on Windows anyway, so I don't know if this is really a problem.


Originally, I had Windows on my C drive, then I formatted the D drive (two separate hard drives) and installed ubuntu there. Does formatting drive C, and reinstalling Windows there affect Ubuntu on D?

Thank you

---

### Post by bodhi.zazen on 2008-10-29
Well, windows is a closed minded OS and can not access your Ubuntu partition.

That is unless you install a driver

[http://www.fs-driver.org/](http://www.fs-driver.org/)

If you install that driver and mount your Ubuntu partition windows, and thus viruses, would have read/write access to it.

---

### Post by madsc89 on 2008-10-29
Thank you for good reply!

Does formatting drive C, and reinstalling Windows there affect Ubuntu on D?

---

### Post by bodhi.zazen on 2008-10-29
> **madsc89 said:**
> Thank you for good reply!

Does formatting drive C, and reinstalling Windows there affect Ubuntu on D?

No, but you will need to re-install grub to boot Ubuntu

[uwiki]RecoveringUbuntuAfterInstallingWindows[/uwiki]

---

### Post by lukjad on 2008-10-29
Thanks! I just had to reinstall Win XP on my school computer and was trying to figure out what to do!

---

### Post by madsc89 on 2008-10-29
Thank you!

I now got the answers I wanted.

---

### Post by madsc89 on 2008-10-29
Thank you!

I now got the answers I wanted.

Added [solved] on thread name.

---

### Post by hyper_ch on 2008-10-30
> **scorchgeek said:**
> It's unlikely that a Windows virus could affect your Linux installation

Not really... if a virus can affect Windows then it most likely could also wipe all unmounted partitions... so a Windows virus could be able to just formate your linux partition.

---

