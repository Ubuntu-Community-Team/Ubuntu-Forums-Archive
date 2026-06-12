---
title: "LTS version 10.04 using unstable software?"
date: 2010-04-28
forum: Server Platforms
---

### Post by elarrarte on 2010-04-28
I have a question to the ubuntu server team ... I tried 10.04 Server in expert mode. When you reach the boot manager section, the installer asks you: "Install GRUB2 boot manager?".
In the same window, the installer recommends not to install GRUB2 in productions systems because it is in development phase ... but the default answer to that question in YES (install GRUB2) ... :confused:

Is that correct for an LTS version to use the GRUB2 boot manager as default if it s in development phase? I d prefer an LTS server the stable as possible ... not using testing software ... don t you think? 8)

Thanks!

---

### Post by windependence on 2010-04-28
I am of the opinion that any new version is not going to be stable. I will not be deploying any new LTS servers until this new version has been out for 3-4 months. Users have a tendency to want to always use the latest and greatest and that is not always the best OR the fastest necessarily. Sadly, Ubuntu seems to be one of the worst as far as this goes. I also use two other Red Hat based distros and they don't seem to have as many problems as Ubuntu does with new releases. 

That being said, I think a server OS especially should be rock solid before it's released. 8.04 was pretty good from the get go. I have not tried 10.4 yet but I hope this is not a sign of things to come.

-Tim

---

### Post by snowpine on 2010-04-28
10.04 is called "Ubuntu Long Term Support," not "Ubuntu Stable." :)

A similar situation occured with the 8.04 release. Firefox 3 was still in beta at the time, however Canonical chose it over Firefox 2, the stable version at the time. Why? Canonical decided it was more important to have a browser they could realistically support for 3 years than to have a brower that was stable at that moment.

Ubuntu Server 6.06 and 8.04 are still being supported (through 2011 and 2013 respectively) if you're looking for a more stable and conservative choice. I also believe grub-legacy is available as an option if you prefer. Like it or not, Grub2 is the wave of the future, at least as far as Ubuntu is concerned. :)

---

### Post by arrrghhh on 2010-04-28
Pretty much how it goes.  If you want the latest and greatest, install the newest Ubuntu version - but it won't be stable.  (Obviously it *can* be, but since it has all the newest stuff in it, it may not be.  I like this because you have a choice - run an old version of Ubuntu if stability is your main concern, but if you want all the new features run a newer version.  Much better than no choice at all, old or nothing!)

If you want stability, grab an older LTS version.  As snowpine pointed out, both LTS releases are still supported.  You just won't get the newest software, but that's with the benefit of stability... So it's one or the other, can't have the newest software with rock solid stability!  On the flip side you can't have all the new features with old, 'stable' software.  C'est la vie!

---

### Post by windependence on 2010-04-28
I might mention that if you use 8.04 and do all the updates, you will have an up to date OS that's stable and every but as up to date as anything out there. For me, I'll stick with 8.04 for now an give 10.4 another few months to stabilize before I deploy any new servers on it.

-Tim

---

### Post by Bachstelze on 2010-04-28
The problem is thar GRUB Legacy is not maintained anymore, which means that if a security vulnerability or other bug is found in it, it might never get fixed. GRUB 2 on the other hand is actively developed, so the developers can fix bugs as they appear.

---

### Post by TBABill on 2010-04-28
IMHO the version of Grub is irrelevant when you consider the amount of bugs you will deal with using a new Ubuntu version (or Karmic for that matter). Just a browse of the forums shows you there are several weaknesses that are posted about over and over....sound, wireless and updates come to mind immediately. But, we take that in trade for great support through the forums with a wealth of knowledge and experience to get through those issues when they arise. Things get better with age, but new issues arise. It's a great OS, don't get me wrong, but LTS won't necessarily make it less buggy than a non-LTS version of Ubuntu. I'm really liking 10.04 RC right now though. Most of my problems are gone so far and I have 1 left to contend with that happens across many distros, not just Ubuntu.

---

### Post by elarrarte on 2010-04-28
I think a more appropriate decision would be a package called just **grub** that points to a package called **grub1** (grub -> grub1) ... later, when the new generation of GRUB is ready ... include it in a package called **grub2** and make **grub** point to that new package (grub -> grub2) ... so in the next upgrade we get the newer software ... that comes with a script that migrates the grub1 to grub2 configuration.
By the other hand, we maintain the older version **grub1** for those who prefer it ... but we recommend the newer version because of the security updates.

Not to recommend using a software in the expert-installer because it s in a development phase ... and install it by default in the LTS version (for large deployments and production systems) ... it s like a joke ... dont you think?

---

### Post by snowpine on 2010-04-28
> **elarrarte said:**
> I think a more appropriate decision would be a package called just **grub** that points to a package called **grub1** (grub -> grub1) ... later, when the new generation of GRUB is ready ... include it in a package called **grub2** and make **grub** point to that new package (grub -> grub2) ... so in the next upgrade we get the newer software ... that comes with a script that migrates the grub1 to grub2 configuration.
By the other hand, we maintain the older version **grub1** for those who prefer it ... but we recommend the newer version because of the security updates.

Not to recommend using a software in the expert-installer because it s in a development phase ... and install it by default in the LTS version (for large deployments and production systems) ... it s like a joke ... dont you think?

I couldn't disagree more. The major features of an LTS release should never change mid-stream. Pushing a Grub1 to Grub2 conversion script through updates is not going to happen. 

I also think that if you migrate your "large deployments and production systems" to 10.04 on the day it is released, you will have bigger problems that Grub2. Ubuntu is not a conservative "let's wait and see what everyone else does" distro, they are always innovating and looking to the future. Fortunately, they support older releases for years, so you don't have to use the latest release if you don't want to be a guinea pig. :)

---

### Post by Cracauer on 2010-04-28
The real question is whether the old grub is any better :)

And yes, "LTS" means it will be usable longer into the future. It does not mean it comes with particularly conservative software releases at the beginning.

---

### Post by elarrarte on 2010-04-29
> **snowpine said:**
> I couldn't disagree more. The major features of an LTS release should never change mid-stream. Pushing a Grub1 to Grub2 conversion script through updates is not going to happen. 

I also think that if you migrate your "large deployments and production systems" to 10.04 on the day it is released, you will have bigger problems that Grub2. Ubuntu is not a conservative "let's wait and see what everyone else does" distro, they are always innovating and looking to the future. Fortunately, they support older releases for years, so you don't have to use the latest release if you don't want to be a guinea pig. :)

OK ... a migration was an idea for avoiding grub2 as default ... I see ur point and ur are right ... but I disagree in including grub2 if it is in experimental phase ... imagine that you install the server and grub2 crashes ... then u realice that it s an experimental software ... what idea of ubuntu do u get? ... not serious at all ... u need a more recent version of the server because it support newer hardware and one of ur servers dosent work with 8.04 ... u expect an evolution in 10.04 ... not these kinda things like booting en 10-secs ... plymouth? or an experimental software ...

---

### Post by Nizumzen on 2010-04-29
> **TBABill said:**
> sound, wireless and updates come to mind immediately

This is the server forum. Sound and wireless are completely irrelevant for servers.

I've yet to have any problems with updates either.

---

### Post by Vegan on 2010-04-29
I have my machine setup to update automatically, I have not had problems as I barely use anything.

---

