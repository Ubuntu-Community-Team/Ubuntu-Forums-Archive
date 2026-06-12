---
title: "When will we have VBS(Virtualization Based Security) of Windows 11 in Ubuntu distro?"
date: 2022-02-13
forum: Security
---

### Post by vyacheslav4 on 2022-02-13
[https://www.linux-kvm.org/images/4/40/01x05-Jun_Nakajima-Kernel_Protection_Using_Hardware-Based_Virtualization.pdf](https://www.linux-kvm.org/images/4/40/01x05-Jun_Nakajima-Kernel_Protection_Using_Hardware-Based_Virtualization.pdf)

 We have already VBS in Windows 11. I do need that technology in Ubuntu. When do we have it in Ubuntu distro?

---

### Post by TheFu on 2022-02-13
Ubuntu gets kernel capabilities at the same time that the rest of the world does.  You are free to use whatever kernel you like with Ubuntu.
Linux Kernel Runtime Guard has been available for some time (2016). It isn't just for VMs.

There are also patches for [https://en.wikipedia.org/wiki/Hooksafe](https://en.wikipedia.org/wiki/Hooksafe) which has been around since 2016.

Many things that MSFT puts marketing around have been part of Linux for years, though Linux doesn't have a $1B marketing budget.

---

### Post by DuckHook on 2022-02-13
> **TheFu said:**
> ..Many things that MSFT puts marketing around have been part of Linux for years, though Linux doesn't have a $1B marketing budget.
:-|
Try **twenty** billion: [https://www.statista.com/statistics/506534/microsoft-sales-marketing-expenditure/](https://www.statista.com/statistics/506534/microsoft-sales-marketing-expenditure/)

---

### Post by linux-sysop on 2022-02-14
If the OP is concerned about security, they can install SE Linux.  As for Microsoft they are still stuck in neutral with NTFS, maybe if they want to keep up, they should offer other file systems?  

Speaking of statistical data DuckHook, I heard a random trivia fact; the most popular Windows OS **today** is XP SP3.  Isn't that weird? There are literally tons of Windows users that refuse to let go of their XP.  

[Here is a video.]("https://youtu.be/NdRtzwshSI4")  I agree with TheFu, since the beginning MS made Widows 1.0 by cloning Mac windows and running it with MS DOS.  It seems while they claim to be innovators, they just keep cloning what other OS have already done.

---

### Post by DuckHook on 2022-02-14
> **linux-sysop said:**
> If the OP is concerned about security, they can install SE Linux.  As for Microsoft they are still stuck in neutral with NTFS, maybe if they want to keep up, they should offer other file systems?
=d>
Well said.

As an additional measure to those in TheFu's post, SELinux has also been available for years. It's a good safeguard and anyone can install it if they want.

And let's not overlook apparmor, which comes preinstalled, preconfigured and has existed in a typical Ubuntu install pretty much since its inception. Most people don't harden it nearly enough, but that's not the fault of apparmor. The reality is that typical users are oblivious to both the tools already within Linux and how superior Linux is to Windows in pretty much every respect, but especially in matters of security.
> Speaking of statistical data DuckHook, I heard a random trivia fact; the most popular Windows OS **today** is XP SP3.  Isn't that weird? There are literally tons of Windows users that refuse to let go of their XP.
This is not surprising at all. Windows users are notorious for being clueless about things like security, patching, magic-thinking or computing hygiene. I would further surmise that the majority of those XP installs are witless nodes in various botfarms: whether they be cryptominers, DDoS bots, CnC servers or malware relays.
> [Here is a video.]("https://youtu.be/NdRtzwshSI4")  I agree with TheFu, since the beginning MS made Widows 1.0 by cloning Mac windows and running it with MS DOS.  It seems while they claim to be innovators, they just keep cloning what other OS have already done.
Apple doesn't get off the hook that easily. The desktop paradigm was originally developed by Xerox. So was the mouse. Apple is not as "original" as ***their*** marketing hype either.

Frankly, I'm highly skeptical of MS motives when it comes to security. Every move that they've ever made to "harden" security has had the side effect of locking out alternatives to their dominance. This behaviour goes back decades and I see no evidence that the leopard has changed its spots. Secure boot continues to be a boondoggle that doesn't even improve security very much. The newest ploy is TPM.

If they were serious about security, then they would do things the Linux way: offer whole disk encryption with off disk bootloaders. The hardware-locking Microsoft-centric half-measures that they are always pushing in our faces are highly suspect and outright cynical when easy alternatives are passed over with a corporate wave of the hand.

---

### Post by #&amp;thj^% on 2022-02-14
> **DuckHook said:**
> :-|
Try **twenty** billion: [https://www.statista.com/statistics/506534/microsoft-sales-marketing-expenditure/](https://www.statista.com/statistics/506534/microsoft-sales-marketing-expenditure/)

Wow what a waste, money could be used in abetter manner (Just an opinion from a very picky user) and  my Off Topic.

---

### Post by SeijiSensei on 2022-02-14
> **linux-sysop said:**
> Speaking of statistical data DuckHook, I heard a random trivia fact; the most popular Windows OS **today** is XP SP3.  Isn't that weird? There are literally tons of Windows users that refuse to let go of their XP. 
I suspect that figure is worldwide. I bet the XP share is much smaller if limited to the US or the OECD.

---

### Post by TheFu on 2022-02-14
There are always over 1M botnets and C&C servers running linux online daily. Most are people that installed to a cloudy service and never did anything again.  Most seem to be running self-installed wordpress and other php webapps because the barrier to entry is very low.  

Computer OSes aren't like washing machines. We don't just buy them, hook them up, and forget about them until it is time to call the Maytag Repairman (very US-centric joke?).  They need weekly care with migrations to a new OS every few years. The longer they are left on the old OS, the harder it will be to migrate.  Same for any specific version of a software stack for an application. If we aren't constantly planning to move every 1-2 yrs, the stack will become too old and the migration to "current" becomes harder and harder.  In the Ubuntu world, every 4 yrs is about the longest anyone should hold off on OS upgrades. After that point, it just becomes too hard.

IMHO.

---

### Post by DuckHook on 2022-02-14
> **TheFu said:**
> There are always over 1M botnets and C&C servers running linux online daily.
I entirely agree with what you say. It was not my intent to imply that Linux is better than Windows by magic. It takes work and constant care, as we on these forums remind new users ad nauseum. I would go even further and state that the current wave of IoT will make Linux bots a problem of truly frightening proportions. IoT is almost entirely comprised of Linux and the vast majority of their various pushers and OEMs don't give a hoot about anything but the most cursory security. And since most of these devices are hybrids with some of the most critical systems hard baked into their guts, good luck updating them even if you figure out how to get inside of them.

The reference, however, was to XP. This Windows version was a security joke even when it was maintained. Now that it's been out of support for years, it has become nothing but a menace to society. And its users do not have the excuse of leaving forgotten instances up and running on some cloud. They are purposefully engaging in daily conduct that harm not only themselves but others.

---

