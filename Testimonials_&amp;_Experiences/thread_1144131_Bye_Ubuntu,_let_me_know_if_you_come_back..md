---
title: "Bye Ubuntu, let me know if you come back."
date: 2009-04-30
forum: Testimonials &amp; Experiences
---

### Post by Alexzander J. on 2009-04-30
I have a HP DV3z with AMD Turion ZM-82 2.2Ghz, 2mb L2 Cache and 4Gig RAM(upgradeable to 8gig). It has a ATI HD 3200 with 64mb sideport and currently uses 320mb of system memory (I guess it could use up to 1.9gig). I loved how well 8.10 with compiz ran on my notebook the only real problem I had was with the sound card (master volume very sensitive) but it was nothing more than a minor annoyance at times. I just updated to 9.04 and It seems my Graphics and Sound are no longer supported in jaunty (ATI drivers are in synaptic but didn't work). Good bye Ubuntu it was great for a couple months even got some friends to switch but I guess I'm not supported anymore.

---

### Post by Tamlynmac on 2009-04-30
"Goodbye"

If you'd rather leave than reinstall 8.1, then there is little to say. Why did you install JJ without doing some investigation to assure it would work?

If your "not supported anymore" why not leave 8.1 on your system? There is no mandatory reason to upgrade. No where did you sign a document that stated you had to. Upgrading is a choice and one that should be taken seriously. Investigation into the new version should at the least include confirming system compatibility.

But the use of Ubuntu is also  optional (as in free choice). So Good Luck with what ever OS you decide to switch to and no I don't need to know which one it will be (don't care). It's your choice.

I just recently had a system failure and installed JJ after fixing. It went smooth and without issue. The actual time spent recovering and installing JJ was minimal, compared to my experiences with Windows. Everything just worked and required very little interaction. My system is much faster than it was running Hardy.

There is no reason to upgrade any OS immediately upon a new version release and to do so without investigating is like gambling.

Good Bye and I wish you luck with your OS of choice.

---

### Post by dwanders on 2009-04-30
Since you did not really ask a question, there is little reason to respond other than to say - Wonder how many XP folks experienced the very same thing when they jumped into Vista on its first release? Or even the "smart ones" that wanted to wait a year for all the bugs to get worked out - and they still experienced the same things! Have to agree with Tamlynmac - there is a lot of common sense in:

   "If it ain't broke don't fix it" 
   "Look before you leap"
   "Stay off the bleeding edge for production PC's"

The list goes on and on ... 

See if Vista Ultimate supports you. It might - I suppose. Or you could get back to the 8.10 that worked for you specific hardware.

---

### Post by Alexzander J. on 2009-04-30
The Ubuntu site doens't have 8.10 listed as a download, how long before it's repository's are gone too? I have vista home premium and can't stand vista incompairison to Ubuntu. I know my hardware isn't "bleeding edge" but this particular HP has only been for sale since january (5 months)so I guess alot of Hp's current AMD/ATI notebooks won't work with Ubuntu 9.04. It took a few hours to get 8.10 to work properly, I had to fix suspend and a few other small things. Im not entirly sure how it will run using 8.04 untill 2011 when it becomes unsuported.

---

### Post by BslBryan on 2009-04-30
[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

You can download all versions of Ubuntu there, starting with Dapper Drake.

---

### Post by Saint Angeles on 2009-04-30
you may wanna try a fresh install (with ext4). this way, your video card will be automatically detected by the live cd and the appropriate driver will be used.

i've been using FGLRX since feisty... until now. jaunty lets me use the open source driver for the first time and its a hundred times smoother than fglrx ever was. videos play without any choppiness and compiz is a dream come true now.

---

### Post by lemuriaX on 2009-04-30
8.10 is officially supported until April of next year.

---

### Post by dwanders on 2009-05-01
I would try and get your old working one back (8.10). You already have an idea what it will take to get it going. Once it is running, I would hold off upgrading till the next long term version is release. I have many servers and workstations running 8.04 LTS - and they will stay there till the next LTS. And I will hold off upgrading them until a few months after the release. It is always fun to hit the new releases with the understanding that some things wont work until I dig into them (extensively sometimes) and I never do it on a production PC.

---

### Post by jordey24 on 2009-05-01
i had this problem before,but i fixed it,ill look it up for you.
Ubuntu 9.04 rocks! :P

---

### Post by jordey24 on 2009-05-01
Open up a terminal window and paste :
```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```
press enter and close the terminal.

logout and login again.re-apply.

let me know if this works or not! ;-)

---

### Post by 3rdalbum on 2009-05-01
If ATI's latest driver doesn't work on your system, it's not Ubuntu's fault. The ATI driver is closed-source, remember?

---

### Post by kwacka on 2009-05-01
try the ATI drivers from the AMD site.

Several cards have been shifted to 'legacy' status.

Instead of complaining about Ubuntu here it might be useful to ask for advice from Ubuntu users and complain to ATI about their lack of support for their product.

---

### Post by caravel on 2009-05-01
> **3rdalbum said:**
> If ATI's latest driver doesn't work on your system, it's not Ubuntu's fault. The ATI driver is closed-source, remember?
The latest driver (9.4) *does* support the OP's integrated graphics (HD 3200 IGP).

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_94_linux.pdf](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_94_linux.pdf)

The problem here is that the OP updated and that does not seem to install the new driver, but holds on to the existing one.  This results in the old driver/new kernel/new xorg incompatibility and this is what is causing a lot of these problems.

Yes the new release has issues but IMHO the OP is quitting to hastily.  I'd advise that you clean install 9.04 (or 8.10 if you prefer it) and you should then be up and running.

Proprietary drivers cause a mess with distro upgrades.  Really users need more warnings in the update manager to inform them that the update could potentially cripple their system.  Proprietary drivers may need to be totally removed before you upgrade.  The update manager does not make this clear, but instead presents the update to the next version as easy as running any other update.

---

### Post by mdsmedia on 2009-05-01
> **caravel said:**
> The latest driver (9.4) *does* support the OP's integrated graphics (HD 3200 IGP).

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_94_linux.pdf](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_94_linux.pdf)

The problem here is that the OP updated and that does not seem to install the new driver, but holds on to the existing one.  This results in the old driver/new kernel/new xorg incompatibility and this is what is causing a lot of these problems.

Yes the new release has issues but IMHO the OP is quitting to hastily.  I'd advise that you clean install 9.04 (or 8.10 if you prefer it) and you should then be up and running.

Proprietary drivers cause a mess with distro upgrades.  Really users need more warnings in the update manager to inform them that the update could potentially cripple their system.  Proprietary drivers may need to be totally removed before you upgrade.  The update manager does not make this clear, but instead presents the update to the next version as easy as running any other update.
I tend to agree. I've upgraded, before, and had little problem, and then upgraded later and had problems. A clean install has then made me wonder why I had any problem.

I have to say that I have NEVER had any problem after a clean install, but then, I'm using pretty basic hardware. My desktop has an nvidea card and my notebook has intel. They've always just worked.

---

### Post by gtr32 on 2009-05-01
The ATI problem should go away easily. I had my X Window corrupted after upgrade. Booted up to safe mode, uninstalled ATI drivers, booted back up to X Windows, installed the new 9.4 driver from ATI's website.

Either run the fxglr_uninstall.sh script or execute 'apt-get purge fxglr*'.

---

### Post by jordey24 on 2009-05-02
Did anyone tried my post?

```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```

works for me.

paste it in a terminal,press enter,and logout and relogin.
what the code does,is it skips the videocard checking. some cards are marked as unsupported,while they do work.by doing this,you turn off the check and it should work fine again.

---

