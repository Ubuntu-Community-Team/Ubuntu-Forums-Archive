---
title: "Will the 21.04 nightlies and alphas/betas update to final?"
date: 2021-03-16
forum: Ubuntu Development Version
---

### Post by t9yz3w4ogbvn7w on 2021-03-16
I really would like to move away from Windows to Ubuntu today instead of waiting a bit more than a month for the final release of 21.04. If I install 21.04 and keep it up to date, will it, by the final 21.04 release, basically be the same as the final release? 

Or is it generally best to reinstall the final version if keeping non-final versions can still produce stability and other issues?

---

### Post by oldfred on 2021-03-16
Moved to Development sub-forum since not about current release.

We get this question with every new Ubuntu version.

Yes, it will be the same.
It just with all the updates, your log files & other cruft will be large. If you are knowledgeable on major housecleaning you can continue to use it. It is not a LTS - long term support version, so will be updating again in 9 months.

I typically use current LTS as main working install, but install each new version just to test it. If I plan to keep it, then I do a totally new install with the final version. Back in 2016, I had to use daily with new build before it was released as I needed all the new kernels and other updates. But then reinstalled.

---

### Post by t9yz3w4ogbvn7w on 2021-03-16
> **oldfred said:**
> Moved to Development sub-forum since not about current release.

We get this question with every new Ubuntu version.

Yes, it will be the same.
It just with all the updates, your log files & other cruft will be large. If you are knowledgeable on major housecleaning you can continue to use it. It is not a LTS - long term support version, so will be updating again in 9 months.

I typically use current LTS as main working install, but install each new version just to test it. If I plan to keep it, then I do a totally new install with the final version. Back in 2016, I had to use daily with new build before it was released as I needed all the new kernels and other updates. But then reinstalled.

It kind of sounds like you contradict yourself a little :lol: at first you say it will be the same, but then you say you had to use a daily for a while and decided to reinstall it once the final was released. If it's the same and you experienced and expected no issues, why did you choose to reinstall?

---

### Post by CelticWarrior on 2021-03-16
> **t9yz3w4ogbvn7w said:**
> It kind of sounds like you contradict yourself a little :lol: at first you say it will be the same, but then you say you had to use a daily for a while and decided to reinstall it once the final was released. If it's the same and you experienced and expected no issues, why did you choose to reinstall?

You need to read more attentively.

---

### Post by crip720 on 2021-03-16
Why not install 20.04?  It is supported for 4 more years, 21.04 is only supported for 9 months before needing to upgrade.

---

### Post by guiverc on 2021-03-16
If you install a *daily *and upgrade packages as normal; eg. my system currently reports as 

```
guiverc@d960-ubu2:/de2900/kubuntu_64$   lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu Hirsute Hippo (development branch)
Release:        21.04
Codename:       hirsute
```

you'll find, usually a few days (but even hours) before release time the "Description" will change and it'll become the fully Ubuntu 21.04 system.

I *bumped* to hirsute about 30 hours after *groovy* became 20.10, and I'll do the same when *hirsute* becomes 21.04 (*the only variable is the when, it could be 30, 36, 42 hours etc*).  A*development* release can be treated as a normal release, just upgrades/changes occur more often, and you've more risk for issues occurring, less support options (*many sites don't allow development support questions, or fewer people can provide help as don't use them*), but I treat it as the same.  I dual boot, so if the box is *broken* I can always reboot & use my other backup system (currentlystill *bionic*)

fyi:  I'd suggest using `sudo apt full-upgrade` to ensure all upgraded packages are installed, there are circumstances where `apt upgrade` can not install upgrades (*which is really useful! but if you're not aware of that fact it can lead to support questions*).

---

### Post by t9yz3w4ogbvn7w on 2021-03-16
Thank you.
P.S I found this (from the sticky I failed to read): [https://wiki.ubuntu.com/U%2B1/common-problems](https://wiki.ubuntu.com/U%2B1/common-problems)
> **If I install the alpha/beta now, do I need to reinstall the final version when it's released?**

 You  don't have to (Update Manager will let you upgrade to the final  version), but you may want to, if one or more of the below apply: 

[LIST]
[*]You have tweaked your testing installation to a point where you're not aware of its exact components and configuration 
[*]You have replaced essential components of your installation with versions from external repositories/PPAs 
[*]You have used package installation scripts or similar tools which are not trusted by the Ubuntu development community 
[*]You  have applied hacks/workarounds for testing purposes for good reason  (prompted during structured testing, bug triage etc.), which may cause  problems during daily usage of a stable installation 
[*]You're affected by potential corner cases that may require a reinstall to fix (which will be documented in the release notes) 
[/LIST]


---

### Post by ActionParsnip on 2021-03-17
They use the same sources as the stable version so simply run updates as normal and you'll go from development to stable. No additional steps are required

---

### Post by zebra2 on 2021-03-17
Unless you are eager and willing to engage in a learning experience I suggest that you use the LTS Version on your primary everyday system. If you choose to use a dev version please don't blame anyone on this forum for your results. With Linux in general you are your own system engineer without regard to whose advice you may follow. I suggest you put /Home on its own partition no matter what you decide.  Don't reformat /Home if you reinstall and your data should be ok. Anything other than LTS is a dev version even if it is released. That is the reason for the short update window. Either way you go a newly released version my have problems with some software for the first thirty days after the release and possibly beyond that. The problems are not as bad as in the past but still occur. When you get past the learning curve things get pretty lazy and you may need another hobby.  I built a house with the time I saved by dropping Windows. 
Welcome to Linux.

---

### Post by t9yz3w4ogbvn7w on 2021-03-19
> **zebra2 said:**
> Unless you are eager and willing to engage in a learning experience I suggest that you use the LTS Version on your primary everyday system. If you choose to use a dev version please don't blame anyone on this forum for your results. With Linux in general you are your own system engineer without regard to whose advice you may follow. I suggest you put /Home on its own partition no matter what you decide.  Don't reformat /Home if you reinstall and your data should be ok. Anything other than LTS is a dev version even if it is released. That is the reason for the short update window. Either way you go a newly released version my have problems with some software for the first thirty days after the release and possibly beyond that. The problems are not as bad as in the past but still occur. When you get past the learning curve things get pretty lazy and you may need another hobby.  I built a house with the time I saved by dropping Windows. 
Welcome to Linux.

I had actually just tried installing the latest LTS the other day. Unfortunately with my hardware and it being on kernel 5.8, I am missing out on things. On my RX 6800 and Ryzen 5600x I was unable to even change the refresh rate - the option was just missing, and it was in 1024x768 - this is all after making sure the system is fully up to date. Whereas with 21.04 it works great. I don't want to go through PPAs and doing any workarounds to get things working =/ my barrier of entry to entry distro for me is - if it doesn't work right out of the box with my hardware, it's not for me. 

That's why I was thinking 21.04 might be my best option for the time being.

Thanks a lot for the /home tip! Would make distro swapping easy and/or reinstalls :KS

---

### Post by zebra2 on 2021-03-19
> **t9yz3w4ogbvn7w said:**
> I 
That's why I was thinking 21.04 might be my best option for the time being.
Thanks a lot for the /home tip! Would make distro swapping easy and/or reinstalls :KS

Sounds like a good plan to me. In addition I suggest you create a separate /swap partition also and avoid using Ubuntu's new "swap file". If the swap partition is present the swap file won't be created by the system.  

So it looks like this with three partitions.
/swap
/ "root"
/home

I suggest that you keep Windows 10 on a separate computer and not dual boot. Dual boot can be a messy bog for Linux beginners.

---

### Post by oldfred on 2021-03-19
+1 on zebra2 suggestion.

But if UEFI system and UEFI install, you also need an ESP - efi system partition for UEFI boot files. Not to be confused with a Linux /boot partition which for desktops usually is not required. If LVM and encrypted install, then you may want a /boot.

The ESP is FAT32 and 300 to 500MB. Only if small drive like a flash drive may you then want a smaller ESP like 100MB.

And if UEFI use gpt partitioning. 
Windows requires gpt for UEFI install, but Ubuntu will let you use the now 40 year old MBR partitioning with UEFI and it really should not.
With gparted select gpt under device, advanced over msdos(MBR) default partitioning before starting.

---

### Post by corradoventu on 2021-03-19
If You don't have a windows partition the ESP FAT32 partition can be smaller. I have 5 different install of Ubuntu Linux in 5 partitions and my ESP partition is 250MB used less than 22% so only 55MB.

---

### Post by t9yz3w4ogbvn7w on 2021-03-20
> **zebra2 said:**
> Sounds like a good plan to me. In addition I suggest you create a separate /swap partition also and avoid using Ubuntu's new "swap file". If the swap partition is present the swap file won't be created by the system.  

So it looks like this with three partitions.
/swap
/ "root"
/home

I suggest that you keep Windows 10 on a separate computer and not dual boot. Dual boot can be a messy bog for Linux beginners.

Thank you. Why is root in air quotes? And is there a reference for this "swap file" someone could link to? This would be for a desktop without hibernation. Is a swap partition still recommended in that case?

---

### Post by zebra2 on 2021-03-20
root is in quotes because the /  is root.  Regarding the swap file, it is a variable sized file inside of the /root and it is still in a dev stage.  I have always used a 4Gig partition for /swap but many recommend a /swap the same size as installed RAM. I personally think it would be rare for a system to sleep more than 2G of RAM but then I personally do not use the sleep function. You will get a different answer on this swap matter from everyone that own a linux based system. The swap file idea was evolved from the need for those that have an encrypted system to have the swap(file) inside of the encrypted partition and not on a not encrypted swap partition which could be a possible security breech. The swap partition will be faster and more stable though. Your choice.

---

