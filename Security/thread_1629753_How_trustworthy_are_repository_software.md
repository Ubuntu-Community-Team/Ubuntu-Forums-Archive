---
title: "How trustworthy are repository software?"
date: 2010-11-24
forum: Security
---

### Post by castro1 on 2010-11-24
I am fairly new to Ubuntu, so maybe my question sound trivial to most, but here it goes:  How trustworthy are repository software?  Some software are labeled as maintained by Canonical, and thus it feels very safe to just hit the Install button. What about the ones that are not?  More specifically: how much concerned (or not) should one be with the risk of malware through the installation of software from the repositories? How much is the reasoning "It is in the repositories, therefore trustworthy" applicable? What should a low risk-taker use as rule of thumbs for installing from repositories?  Thank you.

---

### Post by TNT1 on 2010-11-24
As a general rule, what is in the USC/Synaptic, is fine. If you are going to start adding custom sources and PPA's, then you better know what you are doing.

---

### Post by CharlesA on 2010-11-24
> **TNT1 said:**
> As a general rule, what is in the USC/Synaptic, is fine. If you are going to start adding custom sources and PPA's, then you better know what you are doing.

Yep. The stuff in the repos is checked, but once you start adding third-party PPAs and building stuff from source, all bets are off.

That is unless you actually look at the source code to see what all it does.

---

### Post by cariboo on 2010-11-24
Each package in the repositories is signed by the maintainer, so if something does get through all the checks and balances needed to place a package in the repositories, we know who to blame. :)

---

### Post by castro1 on 2010-11-25
Great, thank you all!  So one can "blindly" add something from the Universe without being concerned? - at least regarding malware, I mean; whether the software itself does the job or is appealing is something else.

---

### Post by CharlesA on 2010-11-25
Blindly in that you look at see what said program does and if it's what you want to use before installing it, yes.

---

### Post by TNT1 on 2010-11-26
> **CharlesA said:**
> Blindly in that you look at see what said program does and if it's what you want to use before installing it, yes.

Yeah, like the man said, linux assumes you know what you are doing... don't be blind:D

---

### Post by castro1 on 2010-11-28
Sure, I meant "blindly" in terms of trusting the absence of malware. Because otherwise, algorithmically, it's a waste of energy to stop and decide at every single time whether it is safe or not. So, "blindly" here means that it's safe to make a global (that is, not local, not every time) decision of trying new software without worrying about harms.

---

### Post by akand074 on 2010-11-28
In all honesty, I never worry about security/malware in Ubuntu. First off, Ubuntu as well as most GNU/Linux distributions are already very secure and I would be super surprised if anyone runs into malware in Ubuntu. I have never once heard of anyone ever getting malware in any Linux distribution personally. Unlike windows, there isn't any benefits from writing malware for GNU/Linux based distributions. There are no money to make from anti-virus companies, I've noticed that a much larger percent of users are actually quite computer literate, and the OS is actually really secure (as long as your not in a root account) that its rather difficult to do anything "behind the scenes". I personally wouldn't worry so much about that. Not saying you should forget about it all together, but I mean its not that big of an issue as I see it.

---

### Post by appier on 2010-11-28
So far, the only time I have ever run into Malware on a Ubuntu system is when it is associated with WINE (not the beverage...) or a virtual machine.

---

### Post by Decatf on 2010-11-28
There was that one incident where someone uploaded something malicious on gnome-look.org.

I don't think anyone has done the same with a PPA (that we know of) but isn't it really only a matter of time? I mean anybody can register a launchpad account and host something fishy on there. Of course the packages have to be "signed" off but as far as security goes that doesn't mean much other than letting us know who did it after the fact. If they had half a brain they would not use their true identity on launchpad anyways.

---

### Post by movieman on 2010-11-28
> **Decatf said:**
> I don't think anyone has done the same with a PPA (that we know of) but isn't it really only a matter of time?

If you keep installing random software on your system you're screwed, no matter what OS you're running.

Most people probably have no PPAs enabled and everyone should think carefully before they do enable any.

---

### Post by Decatf on 2010-11-28
Of course users aren't going to install libfishyapp-6ubuntu66 from ppa:randomdude/malware but the PPA system has made it way to easy for users especially new and inexperienced users. When that '200 line' kernel patch madness was going on some users were begging and begging for someone to host a PPA or compile a kernel for them. By no means does that come off as random software infact most users without any hesitation at all seem to jump on any link to a kernel .deb file that got posted in blog comments. What's more I think since the Launchpad.net PPA system is run by Canonical it might imply a certain level of trust for software that does get hosted on there regardless of who is actually maintaining a specific PPA.

---

### Post by OpSecShellshock on 2010-11-28
> **Decatf said:**
> Of course users aren't going to install libfishyapp-6ubuntu66 from ppa:randomdude/malware but the PPA system has made it way to easy for users especially new and inexperienced users. When that '200 line' kernel patch madness was going on some users were begging and begging for someone to host a PPA or compile a kernel for them. By no means does that come off as random software infact most users without any hesitation at all seem to jump on any link to a kernel .deb file that got posted in blog comments.

There's really nothing that Canonical or this community can do to help such users as you've described. The best that can be hoped for is that some other person has read through the code to check it out, and has posted a warning somewhere if anything unacceptable was found. I wouldn't expect that a suspicious or malicious package would last very long if enough people became aware of the problem.

---

### Post by cariboo on 2010-11-28
> **Decatf said:**
> There was that one incident where someone uploaded something malicious on gnome-look.org.

I don't think anyone has done the same with a PPA (that we know of) but isn't it really only a matter of time? I mean anybody can register a launchpad account and host something fishy on there. Of course the packages have to be "signed" off but as far as security goes that doesn't mean much other than letting us know who did it after the fact. If they had half a brain they would not use their true identity on launchpad anyways.

Do you also remember how long it took for the malicious package to be analysed and the content published on the forums? 

Within an hour of the first post about it, the creator of the malicious .deb had been tracked down, and he was named on several popular forums and other web sites.

If it were that easy, why hasn't it happened numerous times already?

---

