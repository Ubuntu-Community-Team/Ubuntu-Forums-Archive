---
title: "Security issues with personal repositories"
date: 2011-04-21
forum: Security
---

### Post by oldmankit on 2011-04-21
In my journeys with Ubuntu I have many times been told (by a website) to  add a ppa.  I'm a security-conscious guy, and I wonder what the  security issues are.  How do other people decide that a ppa is  trustworthy?  Am I right in thinking there are no checks  whatsoever---that anyone can have a ppa on launchpad, regardless of the  malicious code they are inserting into their programs?  If someone is  flagged for uploading malicious content, are they banned?  How effective  is the ban?

If I am not sure about a ppa, are there any tools  (I'm thinking anti-virus) with which I can scan a .deb file to see if  there is anything suspicious in it?  I have avg for linux, but I've so  far only used it for scanning for windows vulnerabilities.

---

### Post by bodhi.zazen on 2011-04-21
> **oldmankit said:**
> In my journeys with Ubuntu I have many times been told (by a website) to  add a ppa.  I'm a security-conscious guy, and I wonder what the  security issues are.  How do other people decide that a ppa is  trustworthy?  Am I right in thinking there are no checks  whatsoever---that anyone can have a ppa on launchpad, regardless of the  malicious code they are inserting into their programs?  If someone is  flagged for uploading malicious content, are they banned?  How effective  is the ban?

If I am not sure about a ppa, are there any tools  (I'm thinking anti-virus) with which I can scan a .deb file to see if  there is anything suspicious in it?  I have avg for linux, but I've so  far only used it for scanning for windows vulnerabilities.

Depends on the ppa

As with all projects, I trust the ones run by large groups (ie gnuzilla / icecat). 

I am cautions about the ones run by a single individual, depends on if I know the person or not.

The ppa are reviewed from time to time, and there is a mechanism to report problems, but if you want technical details I suggest you ask on launchpad or on IRC.

Linux is not windows and, IMO, running antivirus on Linux is an exercise in futility. See any of the various recurring discussions on these forums if you want more details.

---

### Post by rookcifer on 2011-04-21
> **oldmankit said:**
> How do other people decide that a ppa is  trustworthy?  Am I right in thinking there are no checks  whatsoever---that anyone can have a ppa on launchpad, regardless of the  malicious code they are inserting into their programs? 

That's correct.  Canonical does no checking of PPA's.  It's up to you and/or the community to vet them.  There are a number of PPA's that should be trustworthy due to the amount of people that use them and the fact that the official developers of the software in question run them.  The PPA's to be the most suspicious of are those ran by people not involved with the official software development (that is people who only "build" software written by others).

>  If someone is  flagged for uploading malicious content, are they banned?  How effective  is the ban?


I believe it would result in a ban, yes.  How effective it would be is anyone's guess since the Internet allows for a bit of anonymity and a malicious person could sneak back in after changing his IP, etc. 


> If I am not sure about a ppa, are there any tools  (I'm thinking anti-virus) with which I can scan a .deb file to see if  there is anything suspicious in it?  I have avg for linux, but I've so  far only used it for scanning for windows vulnerabilities.

It's doubtful AV software would find any malicious Linux code since there isn't that much malicious code out there.  And anyone who did want to compromise a PPA would likely write their own code which wouldn't be detected anyway.

---

### Post by tgm4883 on 2011-04-21
> **rookcifer said:**
> That's correct.  Canonical does no checking of PPA's.  It's up to you and/or the community to vet them.  There are a number of PPA's that should be trustworthy due to the amount of people that use them and the fact that the official developers of the software in question run them.  The PPA's to be the most suspicious of are those ran by people not involved with the official software development **(that is people who only "build" software written by others)**.



I believe it would result in a ban, yes.  How effective it would be is anyone's guess since the Internet allows for a bit of anonymity and a malicious person could sneak back in after changing his IP, etc. 




It's doubtful AV software would find any malicious Linux code since there isn't that much malicious code out there.  And anyone who did want to compromise a PPA would likely write their own code which wouldn't be detected anyway.

Just a quick note on the bolded part above. There is a lot of software in the official repositories that is there because someone not involved in the development of it decided to package and build it.

---

### Post by brian_p on 2011-04-21
> **oldmankit said:**
> In my journeys with Ubuntu I have many times been told (by a website) to  add a ppa.  I'm a security-conscious guy, and I wonder what the  security issues are.

You would have to ask yourself why your trust in packages from a Ubuntu repository should be greater than than those obtained from elsewhere. Even though ppa packages do not meet the same criteria you could consider the  track record of that repository and come to a decision.

A nice discussion is at:

[http://forums.linuxmint.com/viewtopic.php?f=18&t=68352](http://forums.linuxmint.com/viewtopic.php?f=18&t=68352)

---

### Post by bodhi.zazen on 2011-04-21
> **brian_p said:**
> You would have to ask yourself why your trust in packages from a Ubuntu repository should be greater than than those obtained from elsewhere.

Anyone can create a ppa, but adding a package to the ubuntu repos is not as easy. You would need to either be a Canonical developer or a MOTU (or go the dark path - crack the Ubuntu servers).

There is an obvious difference between a main line ppa:

[https://launchpad.net/~gnuzilla-team/+archive/ppa](https://launchpad.net/~gnuzilla-team/+archive/ppa)

Which is referenced by a well respected project:
[http://www.gnu.org/software/gnuzilla/](http://www.gnu.org/software/gnuzilla/)

> If you are running a .deb based GNU/Linux distro, you may find useful to use the launchpad repository available here: [https://launchpad.net/~gnuzilla-team/+archive/ppa](https://launchpad.net/~gnuzilla-team/+archive/ppa) It is recommended to use it whenever it is possible, it this way you will not have to worry about update manually the packages. The langpacks in the PPA are the same available for download. 

And a ppa run by an individual:

[https://launchpad.net/~paultag/+archive/fluxbox](https://launchpad.net/~paultag/+archive/fluxbox)
[https://launchpad.net/~gekkio/+archive/cairo-compmgr](https://launchpad.net/~gekkio/+archive/cairo-compmgr)

With the former ([https://launchpad.net/~paultag/+archive/fluxbox](https://launchpad.net/~paultag/+archive/fluxbox)) I know paultag personally, have known him for several years, and he is a developer for the Fluxbox project.

With the latter (chosen at random mind you) - I am unfamiliar with the cairo-compmgr project and I have no idea who the maintainer of that ppa is.

So, I personally would add the icecat and fluxbox ppa without reservations. The third I would not, I would personally either download the .deb directly from the ccm project ([http://cairo-compmgr.tuxfamily.org/download/](http://cairo-compmgr.tuxfamily.org/download/) ) or build from source.

So, as you can see, not all ppa were created equally and you are sure you will get different opinions on the trust worthiness of the various repos depending on paranoia levels, familiarity with various projects, and who you ask.

You can also see why google can not (directly) answer the question either (nor can the mint forums), it is not a yes or no" question, it is a matter of who do you trust, how much you know about compiling for yourself, your paranoia level, and probably other factors as well =)

---

### Post by tgm4883 on 2011-04-21
> **bodhi.zazen said:**
> Anyone can create a ppa, but adding a package to the ubuntu repos is not as easy. You would need to either be a Canonical developer or a MOTU (or go the dark path - crack the Ubuntu servers).

There is an obvious difference between a main line ppa:

[https://launchpad.net/~gnuzilla-team/+archive/ppa](https://launchpad.net/~gnuzilla-team/+archive/ppa)

Which is referenced by a well respected project:
[http://www.gnu.org/software/gnuzilla/](http://www.gnu.org/software/gnuzilla/)



And a ppa run by an individual:

[https://launchpad.net/~paultag/+archive/fluxbox](https://launchpad.net/~paultag/+archive/fluxbox)
[https://launchpad.net/~gekkio/+archive/cairo-compmgr](https://launchpad.net/~gekkio/+archive/cairo-compmgr)

With the former ([https://launchpad.net/~paultag/+archive/fluxbox](https://launchpad.net/~paultag/+archive/fluxbox)) I know paultag personally, have known him for several years, and he is a developer for the Fluxbox project.

With the latter (chosen at random mind you) - I am unfamiliar with the cairo-compmgr project and I have no idea who the maintainer of that ppa is.

So, I personally would add the icecat and fluxbox ppa without reservations. The third I would not, I would personally either download the .deb directly from the ccm project ([http://cairo-compmgr.tuxfamily.org/download/](http://cairo-compmgr.tuxfamily.org/download/) ) or build from source.

So, as you can see, not all ppa were created equally and you are sure you will get different opinions on the trust worthiness of the various repos depending on paranoia levels, familiarity with various projects, and who you ask.

You can also see why google can not (directly) answer the question either (nor can the mint forums), it is not a yes or no" question, it is a matter of who do you trust, how much you know about compiling for yourself, your paranoia level, and probably other factors as well =)

While this is correct, I would argue that the MOTU's are not all coding gods, but instead focus on packaging issues. Anyone can submit a package to the REVU process to be reviewed and added to the Universe repository. There is no way MOTU could review every piece of code and know that it is 100% safe. Heck, I've even had to change code that I've written that was already in the Universe repository because it violated one of the rules. Not because a MOTU or anyone else found it, but because I specifically asked what the policy was. The point is that the code was already in the repository for multiple releases.

---

### Post by bodhi.zazen on 2011-04-21
> **tgm4883 said:**
> While this is correct, I would argue that the MOTU's are not all coding gods, but instead focus on packaging issues. Anyone can submit a package to the REVU process to be reviewed and added to the Universe repository. There is no way MOTU could review every piece of code and know that it is 100% safe. Heck, I've even had to change code that I've written that was already in the Universe repository because it violated one of the rules. Not because a MOTU or anyone else found it, but because I specifically asked what the policy was. The point is that the code was already in the repository for multiple releases.

I am not really tracking what you are trying to say. Are you saying you do not trust the Ubuntu repositories ? Are you saying that because you trust the Ubuntu repositories you also trust the ppa on launchpad ? Are you saying Ubuntu packages may have bugs and are therefore untrustworthy? That makes no sense, even the upstream source code can (and often does) have bugs.

My point was anyone can open a ppa, but uploading a package to any of the Ubuntu repositories is restricted and, as you point out, undergoes peer review. Because of the lack of restrictions on who can open a ppa, trusting a ppa is more variable then trusting the Ubuntu repositories and the decision to trust (or not trust) a ppa is more complex, at least for me.

I never claimed the Ubuntu repositories were free from bugs, errors, or security problems (vulnerabilities) or that the MOTU were in any way gods of any kind.

YMMV

---

### Post by tgm4883 on 2011-04-21
> **bodhi.zazen said:**
> I am not really tracking what you are trying to say. Are you saying you do not trust the Ubuntu repositories ? Are you saying that because you trust the Ubuntu repositories you also trust the ppa on launchpad ? Are you saying Ubuntu packages may have bugs and are therefore untrustworthy? That makes no sense, even the upstream source code can (and often does) have bugs.

My point was anyone can open a ppa, but uploading a package to any of the Ubuntu repositories is restricted and, as you point out, undergoes peer review. Because of the lack of restrictions on who can open a ppa, trusting a ppa is more variable then trusting the Ubuntu repositories and the decision to trust (or not trust) a ppa is more complex, at least for me.

I never claimed the Ubuntu repositories were free from bugs, errors, or security problems (vulnerabilities) or that the MOTU were in any way gods of any kind.

YMMV

Nope, I was actually agreeing with you for the most part. The official repositories are much safer/trustyworthy than PPA's. The issue I have is I see a lot of people say that because it's in the official repositories that it is 100% safe, which isn't entirely the case. However remote that it may be, it wouldn't be extremely difficult to get malware into the official repositories.

---

### Post by rookcifer on 2011-04-21
> **tgm4883 said:**
> Just a quick note on the bolded part above. There is a lot of software in the official repositories that is there because someone not involved in the development of it decided to package and build it.

Yes but that software is also vetted or else it wouldn't be in the official repositories.  PPA's are not vetted.  Anyone can put up a PPA in a few minutes.

> **tgm4883 said:**
> Nope, I was actually agreeing with you for the most part. The official repositories are much safer/trustyworthy than PPA's. The issue I have is I see a lot of people say that because it's in the official repositories that it is 100% safe, which isn't entirely the case. However remote that it may be, it wouldn't be extremely difficult to get malware into the official repositories.

I agree that just because it's in the official repos does not necessarily mean it is malware free.  But there's also no guarantee that Linus Torvalds isn't secretly working for the KGB and has compromised the Linux kernel to spy on everyone.  There's no guarantee that AMD and Intel have not put firmware backdoors in their CPU's.  There's no guarantee a meteor wont hit my house and kill me tonight.  Just like everything else in life, it's about risk assessment, and I think it is more risky to blindly trust an unknown PPA than the official repos.  Either could be trojaned, but I would lay odds that a PPA is more likely to be malicious.

---

### Post by bodhi.zazen on 2011-04-21
> **tgm4883 said:**
> Nope, I was actually agreeing with you for the most part. The official repositories are much safer/trustyworthy than PPA's. The issue I have is I see a lot of people say that because it's in the official repositories that it is 100% safe, which isn't entirely the case. However remote that it may be, it wouldn't be extremely difficult to get malware into the official repositories.

Thank you for clarifying that. For some reason I was not understanding what you were saying, but with this additional information your post is more clear.

I agree, your points regarding the official Ubuntu repositories are right on target.

---

### Post by oldmankit on 2011-04-22
> **rookcifer said:**
> I agree that just because it's in the official repos does not necessarily mean it is malware free.  But there's also no guarantee that Linus Torvalds isn't secretly working for the KGB and has compromised the Linux kernel to spy on everyone.  There's no guarantee that AMD and Intel have not put firmware backdoors in their CPU's.  There's no guarantee a meteor wont hit my house and kill me tonight.  Just like everything else in life, it's about risk assessment, and I think it is more risky to blindly trust an unknown PPA than the official repos.  Either could be trojaned, but I would lay odds that a PPA is more likely to be malicious.

That's a good take on security.  It's all about trust and probability.  And I won't be meteor-proofing my house this afternoon.

> **brian_p said:**
> 
A nice discussion is at:

[http://forums.linuxmint.com/viewtopic.php?f=18&t=68352](http://forums.linuxmint.com/viewtopic.php?f=18&t=68352)
Thanks, that helped clear things up.

> **bodhi.zazen said:**
> Anyone can create a ppa, but adding a package to the ubuntu repos is not as easy. You would need to either be a Canonical developer or a MOTU (or go the dark path - crack the Ubuntu servers).

There is an obvious difference between a main line ppa:

[https://launchpad.net/~gnuzilla-team/+archive/ppa]("https://launchpad.net/%7Egnuzilla-team/+archive/ppa")

Which is referenced by a well respected project:
[http://www.gnu.org/software/gnuzilla/](http://www.gnu.org/software/gnuzilla/)



And a ppa run by an individual:

[https://launchpad.net/~paultag/+archive/fluxbox]("https://launchpad.net/%7Epaultag/+archive/fluxbox")
[https://launchpad.net/~gekkio/+archive/cairo-compmgr]("https://launchpad.net/%7Egekkio/+archive/cairo-compmgr")

With the former ([https://launchpad.net/~paultag/+archive/fluxbox]("https://launchpad.net/%7Epaultag/+archive/fluxbox")) I know paultag personally, have known him for several years, and he is a developer for the Fluxbox project.

With the latter (chosen at random mind you) - I am unfamiliar with the cairo-compmgr project and I have no idea who the maintainer of that ppa is.

So, I personally would add the icecat and fluxbox ppa without reservations. The third I would not, I would personally either download the .deb directly from the ccm project ([http://cairo-compmgr.tuxfamily.org/download/](http://cairo-compmgr.tuxfamily.org/download/) ) or build from source.

So, as you can see, not all ppa were created equally and you are sure you will get different opinions on the trust worthiness of the various repos depending on paranoia levels, familiarity with various projects, and who you ask.

You can also see why google can not (directly) answer the question either (nor can the mint forums), it is not a yes or no" question, it is a matter of who do you trust, how much you know about compiling for yourself, your paranoia level, and probably other factors as well =)
Thanks for giving some specific ideas in which ppas are more trustworthy than others.

I consider this question well and truly answered; thanks so much to everyone. :KS

---

