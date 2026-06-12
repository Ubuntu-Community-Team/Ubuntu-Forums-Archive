---
title: "Trusty Tahr Incremental Releases"
date: 2014-06-01
forum: Ubuntu, Linux and OS Chat
---

### Post by craig10x on 2014-06-01
I installed 14.04 when it came out...i am a bit confused how it works on the point (incremental) upgrades...

1) do they come in through the software updater or do you have to install something to get them?
2) what about the newer kernels?  I read something about a hardware stack that you have to do manually to get the newer kernels from say, 14.10 and on...how is that done?  do you have to install that manually?  
3) I got the impression on the 12.04 wiki that the hardware stack (kernels) are only available for 32 bit...will it be available for 64 bit as well for 14.04?

Hope some of you guys can un-confuse me...:D
in the past i always moved into each new version and was considering staying with LTS...that is why i am not familiar with this...

---

### Post by howefield on 2014-06-01
You don't get the LTS Enablement Stacks unless you manually install them or do an fresh install from the point releases.

Updating in the normal manner through the life of 14.04 will keep you current and up to date but on the 3.15 series kernel.

Same rules apply for 32 bit and 64 bit.

---

### Post by pfeiffep on 2014-06-01
The point releases are produced incrementally - this eases re-installs. If you keep up with software updater, or use apt-get, or use aptitude your installation should be up to date. 
I believe [version 12.04]("http://releases.ubuntu.com/12.04/") was available both 32 and 64 bit.

---

### Post by malspa on 2014-06-01
> **pfeiffep said:**
> The point releases are produced incrementally - this eases re-installs. If you keep up with software updater, or use apt-get, or use aptitude your installation should be up to date.

For example, from my Kubuntu 12.04 (LTS) installation (I've used only Synaptic to keep it up-to-date):

```
$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.4 LTS
Release:	12.04
Codename:	precise
```

---

### Post by craig10x on 2014-06-01
Ok...i get that now...just keep up to date with the ubuntu updater and i will be square with the point releases...
Regarding the hardware stack to get the newer kernels...how do you do that manually?  (what kind of commands do you put in the terminal)....and is it reliable? What i mean is you don't have to worry about borking your system or causing any problems? And are they released at the same time that they release the new incremental isos?

---

### Post by monkeybrain20122 on 2014-06-01
The point releases only upgrade the kernel and the x-stack as far as I know. It would only make sense if you also upgrade your hardware. But if 14.04.x already works and works well on your hardware is there really a point to go for 14.04.x+1? (other than testing for regressions)

On the other hand the applications never get upgraded. If you install Ubuntu 12.04.4 today it is still the same version of unity, the same version of compiz, the same version of LibreOffice.. (well Firefox does get updated) as they were two years ago with the same old bugs which have been long fixed upstream and the same limitations which have long been overcome in newer releases. I don't expect them to backport everything, but at least for Unity and the default applications. If I keep a LTS for more than 18 months it would be because of ppas, not because of Canonical's "support" of stale and often buggy software that outlives its life.

So I really don't see any reason for great excitement.

---

### Post by craig10x on 2014-06-01
I hear you...well perhaps then for me it might just be best to continue upgrading into each new 6 month release since i have had very good results when i do upgrades using the option to do that on the iso installer...
in that way i roll into each new version with the newest features, apps and kernels all included...

---

### Post by malspa on 2014-06-01
> **craig10x said:**
> I hear you...well perhaps then for me it might just be best to continue upgrading into each new 6 month release since i have had very good results when i do upgrades using the option to do that on the iso installer...
in that way i roll into each new version with the newest features, apps and kernels all included...

Yeah, maybe so. I didn't know about these LTS Enablement Stacks before seeing this thread, but I'd think that most people who prefer to stick with LTS releases (like me) are not concerned about keeping up with the newest kernels.

---

### Post by monkeybrain20122 on 2014-06-01
> **craig10x said:**
> I hear you...well perhaps then for me it might just be best to continue upgrading into each new 6 month release since i have had very good results when i do upgrades using the option to do that on the iso installer...
in that way i roll into each new version with the newest features, apps and kernels all included...

I would probably keep 14.04 for a bit longer because I expect a lot of breakage and feature loss when Mir + Unity8 roll out. :)

---

### Post by d-cosner on 2014-06-01
In 12.04 I always got the xserver and kernel packages as updates, never had to manually upgrade anything. I also would not be in any hurry to upgrade to 14.10, MIR  and Unity 8 will take time to mature and I would expect quite a few bugs.

---

### Post by DuckHook on 2014-06-01
> **craig10x said:**
> I hear you...well perhaps then for me it might just be best to continue upgrading into each new 6 month release since i have had very good results when i do upgrades using the option to do that on the iso installer...
in that way i roll into each new version with the newest features, apps and kernels all included...You may want to consider dual-booting:

First partition: 14.04 with no point releases (for stability)
Second partition: whichever is the latest and greatest (just because)
Third partition: data which can be accessed and shared between either of the above releases.

If you partition using GPT, you could conceivably have dozens of partitions with different versions/releases/flavours.

<Thanks to oldfred for this setup>

---

### Post by monkeybrain20122 on 2014-06-01
> **DuckHook said:**
> 
If you partition using GPT, you could conceivably have dozens of partitions with different versions/releases/flavours.



Well if you have an extended partition you can also have many flavours. I would advoid gpt as it makes other things inflexible, such as file system level cloning with fsarchiver. One use of which is just clone the / partition before some risky updates (like graphic driver update just blew up last night and 5 minutes later I was back in business) Another use is to keep the latest and greatest on an external drive and throughly test and configure it to my satisfaction and then just clone it over to the internal drive. All these are much more flexible with fsarchiver than with something like clonezilla but it won't work with gpt.

---

### Post by malspa on 2014-06-01
> **DuckHook said:**
> First partition: 14.04 with no point releases (for stability)
Second partition: whichever is the latest and greatest (just because)
Third partition: data which can be accessed and shared between either of the above releases.

Best of both worlds, kinda. This is sort of like how I do things, except with Debian Stable and Ubuntu LTS on the more "stable" side, and Arch and Sabayon for newer stuff.

---

### Post by craig10x on 2014-06-02
Thanks to all for the input...well, don (dcosner) mentioned to me in a private message that while running 12.04 he DID get the newer kernels that came with 12.10, 13.04, 13.10 without doing any terminal command for hardware stacks...and that they came in the usual ubuntu updater updates...wonder if anyone else who ran 12.04 had noticed that (those who did not put in any terminal commands for it)....

Other then that, i guess i have time to decide...whether to go LTS to LTS (upgrading only every 2 years) or continue upgrading into each new 6 month version of ubuntu...
Oh, if only they would make this a rolling release....things would be so much easier :D ;)

---

### Post by monkeybrain20122 on 2014-06-02
> **craig10x said:**
> Thanks to all for the input...well, don (dcosner) mentioned to me in a private message that while running 12.04 he DID get the newer kernels that came with 12.10, 13.04, 13.10 without doing any terminal command for hardware stacks...and that they came in the usual ubuntu updater updates...wonder if anyone else who ran 12.04 had noticed that (those who did not put in any terminal commands

The flavours may work a little differently. I just installed xubuntu 12.04 on someone's old laptop and still got kernel 3.2 (new iso which I just downloaded) That is actually the reason I got 12.04 since the webcam needs a kernel module that would not work for any higher kernel version. I checked that the graphic stack is still the same as 12.04.0 but you can manually switch to higher version by installing the same packages with suffix like "lts-saucy" which would then remove the original one. It seems like xubuntu doesn't have point releases, you just manually switch to the hardware enabling stack like you would if you have installed Ubuntu 12.04.0.

> Other then that, i guess i have time to decide...whether to go LTS to LTS (upgrading only every 2 years) or continue upgrading into each new 6 month version of ubuntu...
Oh, if only they would make this a rolling release....things would be so much easier :D ;)

Why? There is no reason to stick to one way or the other. Before the shortening to 9 month support for interim releases I usually kept a release for one year give or take a  month or two. Now I would use an interim release for may be 7-8 months  and LTS for a year. I switched to 13.10 around December and intend to keep it all the way til July. I may keep 14.04 for 1.5 to 2 years and skip a few or all the interim releases though because I am sure Mir will break a lot of stuffs.

I keep my software very up to date with ppas and compiling so I am not forced to update the whole OS just to get the latest (or not so old) foo (well to a degree, 12.04 is so old now that new releases of some applications may not even compile and even ppa versions for some applications are relatively old, but those are probably exceptions)

---

### Post by malspa on 2014-06-05
> **monkeybrain20122 said:**
> Why? There is no reason to stick to one way or the other.

Well, that depends on the user. The 9-month cycle for non-LTS releases is much too short for my tastes. I go from LTS to LTS every two years or so, although I have not yet replaced Kubuntu 12.04 with Kubuntu 14.04. I'm good with older software as long as I can get security updates for my web browser, etc. For "the latest-and-greatest" I kinda prefer a rolling-release distro like Arch over Ubuntu's non-LTS releases, but that's just me.

---

### Post by monkeybrain20122 on 2014-06-05
> **malspa said:**
>  For "the latest-and-greatest" I kinda prefer a rolling-release distro like Arch over Ubuntu's non-LTS releases, but that's just me.

My problem with Arch is that it rolls everything and that would be too unstable. I want the end user software to be up to date, like having the latest vlc, gimp etc, but I don't necessarily want the whole system to roll along. Ubuntu + PPA + some compiling for me is optimal (also ppas can be purged easily if something goes wrong, with true rolling there is no going back ) Fedora is static but kind of functions a bit like rolling because there doesn't seem to be any real 'freeze' in the repo, new kernels still keep coming and it manages to be quite stable for offering the bleeding edge (for some packages any way) though in my experience it does break more often than Ubuntu ( Ubuntu actually never breaks on me)

---

### Post by d-cosner on 2014-06-05
I have a Ubuntu Gnome 14.04 and Ubuntu 14.04 installs on my laptop and desktop, I consider these to be stable. Recently I installed Sabayon Gnome on a spare hard drive in my desktop to have the latest Gnome and apps. I am enjoying following the Gnome release cycle and Sabayon makes it easy to keep it current. Sabayon's rolling release updates make it a little risky but it keeps things interesting.

I look forward to seeing changes and improvements in Gnome Shell just as much as I do Unity. Both are really looking good!

---

### Post by malspa on 2014-06-05
> **monkeybrain20122 said:**
> My problem with Arch is that it rolls everything and that would be too unstable. I want the end user software to be up to date, like having the latest vlc, gimp etc, but I don't necessarily want the whole system to roll along. Ubuntu + PPA + some compiling for me is optimal (also ppas can be purged easily if something goes wrong, with true rolling there is no going back ) Fedora is static but kind of functions a bit like rolling because there doesn't seem to be any real 'freeze' in the repo, new kernels still keep coming and it manages to be quite stable for offering the bleeding edge (for some packages any way) though in my experience it does break more often than Ubuntu ( Ubuntu actually never breaks on me)

For me, Arch (so far) has turned out to be more "stable" than either Fedora or Sabayon, for example (and, not to knock either of those distros, which I've enjoyed running). Arch has really been a pleasant surprise here. pacman is a great package manager. It seems that for Arch, the key is checking the home page and keeping an eye on the forums, as well as making use of Arch's excellent wiki.

How all that compares to Ubuntu's non-LTS releases, I can't say. I do know that the LTS releases, keeping up with the incremental/point updates, have been dependable here. Two years is a good period of time for me for any given installation.

---

### Post by LastDino on 2014-06-06
> **malspa said:**
> For me, Arch (so far) has turned out to be more "stable" than either Fedora or Sabayon, for example (and, not to knock either of those distros, which I've enjoyed running). Arch has really been a pleasant surprise here. pacman is a great package manager. It seems that for Arch, the key is checking the home page and keeping an eye on the forums, as well as making use of Arch's excellent wiki.

How all that compares to Ubuntu's non-LTS releases, I can't say. I do know that the LTS releases, keeping up with the incremental/point updates, have been dependable here. Two years is a good period of time for me for any given installation.

That key point is what makes difference to most end users in terms of what's stable and what is not. I used 13.10 for 6-7 Months and I never ever saw this forum or Ubuntu Wiki. I did see ask ubuntu and launchpad once when I couldn't figure out as to why my Time & date thingy disappeared once in a while. I would personally call this quite stable. However, my arch experience has been completely opposite of this, and that to when I'm using Manjaro which holds back packages for 2 weeks to avoid breakages.

---

