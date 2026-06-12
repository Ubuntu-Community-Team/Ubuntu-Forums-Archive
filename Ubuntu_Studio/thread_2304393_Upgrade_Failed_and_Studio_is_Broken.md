---
title: "Upgrade Failed and Studio is Broken"
date: 2015-11-26
forum: Ubuntu Studio
---

### Post by vteve on 2015-11-26
Against my better judgement late last night, I clicked upgrade to 15.04 after receiving a message that this upgrade was available. I was running Ubuntu Studio 14.04.3 LTS. I received several error messages during the upgrade related to missing dependencies and it will not boot now.
The installation was only about a month old. The only clue I can give is: in the software sources selector, I unchecked the one about untrusted back-ports a couple weeks ago. This was after some previous software updates seemed to result in new glitches on the system.
Do I need to reinstall fresh? Please help.
Thanks.
Steve.

---

### Post by CrocoDuck on 2015-11-26
> **vteve said:**
> 
Do I need to reinstall fresh?

I think it is the best thing to do. Upgrade regression is not very straightforward with apt based distros, not even when you know all the packages that have been updated and the conf files that have been overwritten. Also, your package manager could be broken. It will take for sure less time reinstalling the whole system. You can access your data from a live Linux media (even UStudio media itself) and save them. I also suggest to install [Gparted]("http://gparted.sourceforge.net/") on the live Linux, erase all the partitions with that, then reboot and run the installer. I am used to boot with [this]("http://www.sysresccd.org/SystemRescueCd_Homepage"), save my data and prepare the partitions beforehand when installing a new distro.

In my experience advancing Ubuntu version or installing Ubuntu over a pre-existing Linux (even if erasing the partitions with the Ubuntu installation programs) always resulted in a broken system. I would suggest to avoid these actions unless you are brave.

---

### Post by ajgreeny on 2015-11-26
You can not upgrade in one jump from 14.04 to 15.04; you have to do it via 14.10 which is no longer supported.  I am surprised that you even managed to get started on this upgrade, and it may, indeed, be very difficult, if not impossible to now move back to 14.04 without a reinstallation.

I would personally recommend that you stick with 14.04 at least until April 2016 when the next LTS (Long Term Support) version is released, and then consider upgrading to 16.04 which you will be able to do in one jump if you really want to.  I always do a clean install and take the opportunity to make a fresh start with the LTS versions only, and I run the intermediate versions only in VirtualBox so that I can see any major improvements that may have come along.

---

### Post by vteve on 2015-11-27
Thanks for the comments. I reinstalled and am getting things back to normal.

> I am surprised that you even managed to get started on this upgrade


This is the strange part... the update manager popped up and the upgrade to 15.04 appeared like it was recommended... so I just clicked ok. :-/

I hope this doesn't happen to others!

---

### Post by yoshii on 2015-11-30
Just so you know, it's ok to DE-select unsupported backports.  That's actually the safer configuration that way.

---

### Post by vteve on 2015-12-11
Please tell me if everyone got the list of kernel updates (3.19.0.39.25) and are they safe to install?

It seems to me that last time things started to go bad after installing this kernel update stuff... I noticed USB devices randomly locking up, keyboard, mouse, wireless NIC.


Thanks.

---

### Post by vteve on 2015-12-12
I realized my last post was really incoherent so here's a screenshot of my software updater if that helps. Does this upgrade list look normal? As I mentioned in the last post, things seemed to go bad after I installed these upgrades... then I had to reinstall.

[ATTACH=CONFIG]266110[/ATTACH]

Thanks,
Steve.

---

### Post by CrocoDuck on 2015-12-12
Updates are generally safe a part [Ubuntu Version upgrade]("http://www.ubuntu.com/download/desktop/upgrade"), that really never worked in my experience (maybe they work better nowadays though). The ones you see are just packages being updated to the latest version, not a whole Ubuntu Version advancement, so it should be safe. Have a look if you can find [bugs reported]("https://bugs.launchpad.net/ubuntu/+source/linux/+bugs") on that particular kernel if it makes you feel safer. Personally, I think the Version Upgrade you did last time just messed up all the configuration files and package dependencies.

I think you can try to upgrade: these package upgrades should be more straightforward to [revert back]("https://encrypted.google.com/search?hl=en&q=downgrade%20kernel%20ubuntu") if bad things happen. Also, If they ruin the system you can pin down a kernel version that messes things up, know what to avoid and [file a bug to the developers]("https://wiki.ubuntu.com/Kernel/Bugs").

As a note, I had nothing but troubles from the latest versions of Ubuntu Software centre. Consider to use apt or Synaptic to update your system.

```

sudo apt-get update
sudo apt-get upgrade

```

You get some more info about the upgrades types [here]("http://askubuntu.com/questions/215267/will-apt-get-dist-upgrade-upgrade-my-system-to-newer-version").

---

