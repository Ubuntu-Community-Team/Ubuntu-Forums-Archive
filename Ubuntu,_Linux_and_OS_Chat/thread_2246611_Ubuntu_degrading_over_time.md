---
title: "Ubuntu degrading over time"
date: 2014-10-02
forum: Ubuntu, Linux and OS Chat
---

### Post by DinghySailor on 2014-10-02
I've been a long term enthusiast of Ubuntu, but my enthusiasm is waning, as it seems Ubuntu is losing its way.

I recall my early experiences with Ubuntu being very positive - it did everything I needed and upgrades were not enforced. I could leave the computer on for more than a year without rebooting.

Now I have so many updates, and sometimes enforced reboots.

I used to be able to hibernate my laptop, not I can't. A week ago, I could suspend my laptop, now, thanks to "upgrades" I can't.

I used to be able to use a satellite dish card in my desktop. Thanks to an upgrade, I can't.

Each time I upgrade to a new version, I face having to reinstall ALL my applications, which is lunacy. If those applications need upgrading, they should be upgraded automatically. Better would be for them to be compatible.

And when I upgrade, finding that applications I regularly use, not only have they been deleted, but I can no longer install them!

I like the Gnome look and feel - and really hated the Windows 8 look and feel introduced a few years ago. And not to have an easy option to install the familiar look and feel was most annoying. Akin to the corruption of the command shell in Windows - or Windows 8. It may be good for a tablet, but for people used to being able to access all the applications they want from a simple menu, this was a massive retrograde step.

Please, please, please return to good practices, and stop thinking about competing with Windows, return to the ethos of making a good, fast, secure OS, and don't get hung up on "having to" provide updates that offer nothing apart from bloatware and reduction of functionality.

Many thanks,

---

### Post by buzzingrobot on 2014-10-02
What version were you upgrading from, and to?

If you were using PPA's or other non-official and unsupported repositories, did you disable them first and back out their packages?

If  by "upgrade" you mean moving from one release to another, then they are  not enforced. No one compels a user to upgrade from one release version  to another. Release versions do reach end-of-life and are no longer  supported, as is the case in other systems. Canonical's release  schedules and release lifetimes are regular and well publicized.

"Updates"  -- fixes and bug patches to existing packages -- are Good Things  because the alternative is to continue using unfixed and unpatched  software. Reboots are needed when a package, e.g., kernel or video card  driver or a service of some kind, that is executed only at boot time is  updated.

It seems pretty unlikely that "ALL" user-installed applications  would require updating after an upgrade from one release version to  another. That said, it certainly is not unusual for applications to  release new versions to leverage or ensure compatibility with new  features in new releases. Applications cannot be made compatible with  new release versions until, at the very least, some form of those  releases are available. This happens during the development process of a  new release, when independent app developers have the chance to test  their code against pre-release developmental versions of the forthcoming  upgrade. Logically, those updated packages are released after the release upgrade occurs.

---

### Post by Bucky Ball on 2014-10-02
I echo buzzingrobot. 12.04 LTS = supported until April 2017. 14.04 LTS = supported until April 2019. Stick with LTS releases.

---

### Post by rrnbtter on 2014-10-02
Greetings, 
Yes, hard to tell what you are doing from your post.  I have used every development release since I started with Karmic. The development process has become so refined that it is boring. I use to have to reinstall many times during a dev cycle. With Utopic I have only had one install. In that time I have kept my wife on Trusty and it has been a very smooth delightful experience. There are a few updates but advances will filter down to earlier versions. We both use five year old laptops and the one my wife uses is a 10" Netbook.  I get some satisfaction from the dev process by switching kernels and learning systemd. 
My suggestion based on your post is to stay with the current LTS "Trusty" then open your Software and Updates and uncheck "Preposed" and in addition do not switch to systemd until Ubuntu makes it default.  This should give you a smoother ride. 
My personal experience with the whole thing has been a delightful adventure with a few reinstalls here and there. I also install every daily update to Ubuntu-Desktop-Next on an alternate HD. From that experience I would say "fasten your seatbelt" it's not over yet.

---

### Post by tgalati4 on 2014-10-02
Others feel similar:  [http://arstechnica.com/gadgets/2014/06/mint-17-the-perfect-place-for-linux-ers-to-wait-out-ubuntu-uncertainty/](http://arstechnica.com/gadgets/2014/06/mint-17-the-perfect-place-for-linux-ers-to-wait-out-ubuntu-uncertainty/)

Ubuntu has been around long enough to gain a following and some history.  Those that want to go back to the "old Ubuntu" have found other distros that bring back the old-time feeling.

---

### Post by buzzingrobot on 2014-10-02
> **tgalati4 said:**
> Others feel similar:  [http://arstechnica.com/gadgets/2014/06/mint-17-the-perfect-place-for-linux-ers-to-wait-out-ubuntu-uncertainty/](http://arstechnica.com/gadgets/2014/06/mint-17-the-perfect-place-for-linux-ers-to-wait-out-ubuntu-uncertainty/)

Ubuntu has been around long enough to gain a following and some history.  Those that want to go back to the "old Ubuntu" have found other distros that bring back the old-time feeling.

It really *is* look and feel only.  Mint 17 is built on 14.04 and uses 14.04's repos.  Updates as they are done in Ubuntu have been SOP across Linux since packaging and dependency resolvers camee along. Upgrades to the next release version have always been problematic because users alter their systems, etc.

Failing to stay current with changes in Linux has a real downside.  XFCE, for example, has show little development for a some time, is based on the aging GTK2, and hasn't presented its plans, much less coding efforts, to deal with things like Wayland and systemd.  (Debian has just rejected XFCE as the default DE for Debian 8.)  Issues exist now -- often theming -- for users now who want to run GTK3 apps in XFCE or another GTK2 DE.

---

### Post by robin7 on 2014-10-02
My brief tenure on 14.04 was considerably slower and more problematic than 12.04.  I broke a promise to myself not to go to the next LTS until Precise reaches end-of-life, but I got curious... Trusty cured me and I'm back on 12.04 (except on LXLE instead of my old favorite Xubuntu), good for three more years.  But even on Precise some users are having working wireless/networking issues broken by updates, so caution is advised even on tried-and-true two-year-old LTS releases!

---

### Post by QIII on 2014-10-02
> I recall my early experiences with Ubuntu being very positive - it did everything I needed and upgrades were not enforced. I could leave the computer on for more than a year without rebooting.

No updates/upgrades are enforced.  You can still leave your machine on for a year.  Of course, you may be subject to security issues.

> Now I have so many updates, and sometimes enforced reboots.

Updates are a good thing.  And, again, you don't have to reboot if you don't want to.  Most updates do not require reboot.  Kernel updates do -- they have to.  But you don't have to reboot to keep using the kernel running while you have the machine on.

> I used to be able to hibernate my laptop, not I can't. A week ago, I could suspend my laptop, now, thanks to "upgrades" I can't.

Then start a support thread.  There may be a simple explanation.

> I used to be able to use a satellite dish card in my desktop. Thanks to an upgrade, I can't.

Does the manufacturer of your card provide driver updates that keep up with kernels?  Have you started a support thread?

> Each time I upgrade to a new version, I face having to reinstall ALL my applications, which is lunacy. If those applications need upgrading, they should be upgraded automatically. Better would be for them to be compatible.

If you have installed them from the repos, even often from independent .debs via dpkg or via PPAs, you can create a list of them and use that list to reinstall them easily.  You're on your own with third party apps.  Canonical has nothing to do with them.  Do you think Canonical should know what you want to reinstall when you upgrade to a new release?  (Does Microsoft?  You don't even have the option to make a tidy list and reinstall them with a few keystrokes.)

> And when I upgrade, finding that applications I regularly use, not only have they been deleted, but I can no longer install them!

Perhaps those who maintain them have abandoned them and they have been removed from the repo.  Perhaps those who maintain them are not keeping up and they will no longer work.  Of course, you could start a support thread.

> I like the Gnome look and feel - and really hated the Windows 8 look and feel introduced a few years ago. And not to have an easy option to install the familiar look and feel was most annoying. Akin to the corruption of the command shell in Windows - or Windows 8. It may be good for a tablet, but for people used to being able to access all the applications they want from a simple menu, this was a massive retrograde step.

There are quite a few people in the community who think that the GNOME approach is anachronistic.  I don't like Unity, so I just don't use it.  Simple as that.  But I do like the crack of the whip, the clopping of shod hooves and the squeaks of the springs on my surrey.  There's a hint there about the definition of "retrograde".

> Please, please, please return to good practices, and stop thinking about competing with Windows, return to the ethos of making a good, fast, secure OS, and don't get hung up on "having to" provide updates that offer nothing apart from bloatware and reduction of functionality.

We're just Ubuntu users here.  If you want things changed, we aren't the ones in a position to do it.  This is not the venue to ask for changes to be made.  You'll have to talk to Canonical.

Nothing you have said here is new, nor is any of it not covered by threads throughout the Ubuntu Forums.

---

### Post by help_me2 on 2014-10-02
> **DinghySailor said:**
> 

Please, please, please return to good practices, and stop thinking about competing with Windows, return to the ethos of making a good, fast, secure OS, and don't get hung up on "having to" provide updates that offer nothing apart from bloatware and reduction of functionality.

Many thanks,
Who are you pleading with? The devs rarely come here. This is an Ubuntu community for users, not for developers and suggestions. There are other avenues for that kind of stuff.

Anyways, I haven't had any of the problems you speak of. I couldn't be happier. Perhaps you should use Mac OS or Windows. Good luck.

---

### Post by buzzingrobot on 2014-10-02
> **help_me2 said:**
> Who are you pleading with? The devs rarely come here. This is an Ubuntu community for users, not for developers and suggestions. There are other avenues for that kind of stuff.

Anyways, I haven't had any of the problems you speak of. I couldn't be happier. Perhaps you should use Mac OS or Windows. Good luck.

I agree.  

Some info is missing: What release? Upgraded to which newer release? What new code represents "bloatware"? How big is that "bloatware" compared to what? What security risks have been introduced? What functionality has been lost, as opposed to doing the same things differently? (Losing a traditional hierarchical menu, for example, is not a loss of functionality.)

---

### Post by Rob Sayer on 2014-11-05
I'm concerned that ubuntu 14.04 does not use an lts kernel.

I'm unimpressed with xubuntu 14.04 or lubuntu 14.04.  They're too buggy.  Especially the latter.  That was ridiculous.  Frankly LXLE works better than Lubuntu.  If Canonical doesn't care about any other DE than Unity why should I care about ubuntu?

---

### Post by sudodus on 2014-11-05
It is not a problem, on the contrary, it is a very good feature of linux, as free and open software, that community re-spins and separately managed distros can be based on Ubuntu's repositories and the Ubuntu engine under the hood. If LXLE works well for you, we are happy that you are using it :-) I also like LXLE, particularly for old hardware, while I find the current versions of standard Ubuntu with Unity quite good too, but for newer and more powerful computers. I run Ubuntu 12.04.5 LTS with xubuntu-desktop in my production machine, and I take active part in testing Lubuntu. Don't forget Kubuntu, Ubuntu Gnome, Ubuntu Studio, Mythbuntu, Edubuntu, ... and all distros and re-spins based on Ubuntu not mentioned in this thread.

-o-

There is a reason why upgrading from the previous LTS version to the next LTS version (for example 12.04 --> 14.04) is not advertized until the first point release, so in effect it means (12.04.5 --> 14.04.1). That way, the new LTS release has approximately 3 months of debugging and polishing. ***If you want or need stability, run only LTS releases, and wait at least for the first point release until you upgrade to the next LTS release***. As a matter of fact, if a version is running well, there is no reason to upgrade or make a fresh installation until it approaches end of life (end of security updates).

It might be different when you get new hardware (a new computer or some vital part is added or replaced). Then you might need a new version of the operating system in order to get a driver for that new hardware. And you might need a feature that comes only with a new version of some software, which is easily available in a new version of the operating system, but difficult or impossible to run in older versions.

---

### Post by Bucky Ball on 2014-11-05
> **Rob Sayer said:**
> I'm concerned that ubuntu 14.04 does not use an lts kernel.



News to me an odd, considering 14.04 **LTS** is an **LTS** release supported until 2019. :-k

---

### Post by deadflowr on 2014-11-05
The kernel on 14.04 right now is the only true lts kernel for 14.04, as it will be supported until 2019.
The only one that will be supported for the whole release.

It's not called lts-something because it is not built from a different release version's kernel.
It's the original kernel.
If by chance when 14.04.2 comes out and you install that, then you would get the lts-utopic kernel.

---

### Post by craig10x on 2014-11-06
14.04 has the 3.13 kernel not the 3.16 (utopic kernel). However, in February, when 14.04.2 is released, it will have the utopic kernel...since you already have 14.04 installed, i believe you will be able to move to it with what they call the hardware enablement stack...i think a terminal command would add that in...that would also be available in february...

---

### Post by buzzingrobot on 2014-11-06
Torvalds and friends maintain 4 categories of kernel releases:

1. Prepatch -- Pre-releases, distributed by Torvalds as source.

2.  Mainline -- This is the kernel tree maintained by Torvalds; it's where the development and the new stuff happens.

3.  Stable --   What a mainline kernel is called after its release. There's a new one every few months.

4. Longterm --  Maintained to backport important bugfixes to older kernel trees.

Note that the term 'LTS' is not used. Also note the longterm kernels do not get all bugfixes.

The most recent long-term kernel is 3.14.23.  The current mainine kernel is 3.18-rc3.  There are two stable kernels at present, 3.17.2 and 3.16.7. 

Canonical is quite capable of maintaining whatever kernel goes into an LTS release, which is what they've done when they've adopted a kernel for LTS use that that needs to be maintained for longer than the Linux kernel team maintains it.

The important thing is the maintance -- what's actually in the kernel -- not the numbering scheme.

---

### Post by craig10x on 2014-11-06
@buzzingrobot: I moved on to 14.10 with the utopic kernel of course, which is currently running 3.16.0-24...when i left 14.04 is running the latest update of the 3.13 kernel (don't recall what number) did 14.04 move on to the 3.14 kernel? Or is that just a "typo" in your post...just curious ;)

---

### Post by buzzingrobot on 2014-11-06
> **craig10x said:**
> @buzzingrobot: I moved on to 14.10 with the utopic kernel of course, which is currently running 3.16.0-24...when i left 14.04 is running the latest update of the 3.13 kernel (don't recall what number) did 14.04 move on to the 3.14 kernel? Or is that just a "typo" in your post...just curious ;)

Ubuntu kernels use their own numbering scheme, as do many distros. There isn't a one-to-one correspondence with the releases from Torvalds, etc.

From kernel.org:  [https://www.kernel.org/](https://www.kernel.org/).

And, I think this ([https://wiki.ubuntu.com/Kernel/FAQ#Kernel.2BAC8-FAQ.2BAC8-GeneralUbuntuDelta.What_differentiates_the_Ubuntu_Kernel_from_the_upstream_Linux_Kernel.3F](https://wiki.ubuntu.com/Kernel/FAQ#Kernel.2BAC8-FAQ.2BAC8-GeneralUbuntuDelta.What_differentiates_the_Ubuntu_Kernel_from_the_upstream_Linux_Kernel.3F)) and the next few FAQ entries about Ubuntu kernels is stil current.

---

### Post by craig10x on 2014-11-06
Yes, that is true...i know they use different numbering because of the ubuntu specific patching they do...However, the 3.14 part would indicate that it's a patched version of the 3.14 kernel, so that is why i was curious..
When i was in 14.04, the numbers ALWAYS started with 3.13 (indicating of course that kernel) the rest of the numbers were different from the mainline (non ubuntu patched) version, as you said...
Could you check in the terminal (command:  uname -r) did this come down in your updates or did you install it yourself?

---

### Post by buzzingrobot on 2014-11-06
Didn't Canonical, in effect, take on maintenance of 3.13 when they decided to use it in an LTS? 

It does get a bit confusing.

---

