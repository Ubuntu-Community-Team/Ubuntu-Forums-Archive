---
title: "Why was the bunk intel driver included in Jaunty?"
date: 2009-07-12
forum: The Cafe
---

### Post by decoherence on 2009-07-12
So I just finished skimming through this thread in testimonials where this fellow was saying that, under vista, he got a 10 times better GL frame rate than under 9.04 using his Intel graphics. Typical responses ensued... people explaining about the problems with the Intel driver, suggesting that he use an LTS version, saying that it wouldn't be a problem in Karmic, etc....

I just want to know why people think (or if anyone actually knows) why this crummy driver was included in the release? Everybody who was following development knew about it, prior to the release. Did Canonical figure it didn't matter? Would it have been impossible to "reverse course" and ship older drivers that worked properly? What benefits is this new driver supposed to bring? Ubuntu 9.04 doesn't appear to make use of KMS or GEM in any significant way, so why include the new, buggy drivers? Does the latest X.org require it or something?

Shipping a driver that does not work properly on a large portion of the hardware it's supposed to be driving is not consistent with the "Linux for Human Beings" message.

I think we can all agree that the Intel performance regression is an unfortunate thing. Do you think Canonical could've/should've prevented it from appearing in their distro? Do you think that this sort of thing will happen again? Say a wireless driver gets a massive update and, due to a new bug, reduces your bandwidth to a max of 1MB/s... should Ubuntu be using that new driver? Is it even the same kind of situation?

How much damage to the "linux reputation" do you think these sorts of occurrences do? (i know, for me, it only damages ubuntu's rep, and only because it's supposed to be "linux for human beings" rather than linux for geeks like me, who i guess aren't actually human. If this problem cropped up in Debian unstable or Arch, I wouldn't care nearly so much)

---

### Post by Dimitriid on 2009-07-12
Aggressive release cycles are not for everybody. Canonical should do a better job at promoting LTS version. The current model is just not ideal if you ask me: You got a 6 month release cycle that includes a lot of new features and gets a lot of promotion while the LTS gets buried.

I think LTS should be offered more aggressively because to me, 90% of new users should default to the LTS version.

---

### Post by Paqman on 2009-07-12
> **decoherence said:**
> Do you think Canonical could've/should've prevented it from appearing in their distro? 

Absolutely. There are a ton of laptops out there using Intel graphics. Releasing with such a huge bug in such an important system on so many machines is not really acceptable.

---

### Post by cariboo on 2009-07-12
Ubuntu had nothing to do with it, the Intel drivers are compiled in the kernel, there is no separate driver. All distributions that have the same combination of kernel and Xorg have the same problem. Put the blame where it belongs, on Intel.

---

### Post by dicairo on 2009-07-12
hiiii every one , i was having the same problem i remember my first days with ubuntu 9.04 i was unable to run compiz (with compiz i convert some of my friends to use ubuntu they like comiz , the boot time no crash ect) i was really sad and i tried all the solutions on the internet but noway so i had to return back to 8.10 .
after 2 months i decided to upgrade again to 9.04 to see if the problem is solved or not and for my luck its now work. 
So this my story and i think that something like this shoudn't  happen again i was thinking about using another distro but i preferred 8.10 . I dont know why the didnt use the drivers of 8.10 for intel cards in ubuntu 9.04 to prevent this problem ????
I think the problem is the short time only six month to bring a new OS  (wich is great). So that is it and i was very angry but now its ok

---

### Post by Viva on 2009-07-12
> **cariboo907 said:**
> ubuntu had nothing to do with it, the intel drivers are compiled in the kernel, there is no separate driver. All distributions that have the same combination of kernel and xorg have the same problem. Put the blame where it belongs, on intel.

+1

---

### Post by Dimitriid on 2009-07-12
> **cariboo907 said:**
> Ubuntu had nothing to do with it, the Intel drivers are compiled in the kernel, there is no separate driver. All distributions that have the same combination of kernel and Xorg have the same problem. Put the blame where it belongs, on Intel.

No: all distributions can choose which combination of kernel, drivers and xorg version to distribute. Any distro which decided the newest versions of the kernel and xorg were ready to be massively adopted **are directly responsible** since they arbitrarily decide according to different standards and philosophies when to adopt new versions. Ubuntu apparently has no criteria and must follow arbitrary, pre-established rules which basically achieved little functionality in exchange of show-stopping regressions.

Saying distros are not to blame is an apologist argument at best.

---

### Post by Closed_Port on 2009-07-12
> **cariboo907 said:**
> Ubuntu had nothing to do with it, the Intel drivers are compiled in the kernel, there is no separate driver.

Nope, that's simply not true. The driver is not part of the kernel. That why you can download the driver separately and why ubuntu can provide newer and better drivers in a semi-official ppa that solves the problems discussed here.

> **cariboo907 said:**
> 
All distributions that have the same combination of kernel and Xorg have the same problem. Put the blame where it belongs, on Intel.
See above. And the blame should be put where it belongs: On the ubuntu devs who decided to ship with the broken drivers.

---

### Post by cariboo on 2009-07-12
I have an Intel Atom powered system that I use for a media center pc, It has the 945 chipset. I have have been able to use compiz from the day of the original install, the big problem I had was video tearing during fastr moving scenes when playing videos. I used the files available [here]("https://launchpad.net/~intel-gfx-testing/+archive/ppa") to solve the problem. FPS when running glxgears is low, but video quality when playing movies is excellent.

I'm not a gamer so FPS really means nothing to me.

I'm currently watching 3 Bats Live in HD and I'm quite happy with the quality.

---

### Post by Closed_Port on 2009-07-12
> **cariboo907 said:**
>  I used the files available [here]("https://launchpad.net/~intel-gfx-testing/+archive/ppa") to solve the problem.
Oh, are those the files that weren't supposed to exist as you claimed the drivers were part of the kernel and it wasn't ubuntu's fault? ;)

---

### Post by SunnyRabbiera on 2009-07-12
Still maybe a patch for it should be made more availible, I know you can get it with a PPA but maybe there should have been a patch for those who dont want to wait for karmic.
I mean OpenSuse 11.1 had simular issues on my machine but after a kernel fix its fine.

---

### Post by decoherence on 2009-07-12
> **cariboo907 said:**
> Ubuntu had nothing to do with it, the Intel drivers are compiled in the kernel, there is no separate driver. All distributions that have the same combination of kernel and Xorg have the same problem. Put the blame where it belongs, on Intel.

The intel drivers are compiled in to the kernel? I thought the driver was xserver-xorg-video-intel? Please enlighten :)

In any case, is it Intel's fault Canonical shipped their driver when Canonical knew it had major performance problems? Did Canonical *have* to ship that version of Xorg and kernel? I suppose it brought some new features to other users... was it worth the breakage?

I think that, if it's going to be this way, Dimitriid is absolutely right. The LTS has to be the promoted as the "main" version of Ubuntu for most of its target users.

Once again I'll mention that Ubuntu is supposed to be 'linux for human beings.' As in, flaky video drivers should not be a problem. Canonical, not Intel, are the ones who must take responsibility to ensure that is the case.

Ubuntu has historically done very well at solving usability problems, from having great autodetection when it came out, to including jockey (restricted driver manager) when it became clear that drivers for Nvidia, ATI, Broadcom et al were having a big affect on usability, and now with the papercuts project.

It seems completely bizarre that this issue just seemed to slide by in to the release, even though everyone knew about it.

If someone can enlighten me on why it was necessary to release this broken configuration, I would love to know. I'm sure (or at least, I hope) there must be some reason! Even if it doesn't sound like a good reason in hindsight, I really don't want to believe that it was just a simple "Intel sucks and Ubuntu WONTFIX."

---

### Post by -=hazard=- on 2009-07-12
> **Closed_Port said:**
> Oh, are those the files that weren't supposed to exist as you claimed the drivers were part of the kernel and it wasn't ubuntu's fault? ;)

Those drivers are still being tested 
**PPA for Intel graphics driver testing**

no one include testing drivers on OS[COLOR=Red] stable [/COLOR]release, so its not ubuntu fault but intel ;)

---

### Post by SunnyRabbiera on 2009-07-12
> **-=hazard=- said:**
> Those drivers are still being tested 
**PPA for Intel graphics driver testing**

no one include testing drivers on OS[COLOR=Red] stable [/COLOR]release, so its not ubuntu fault but intel ;)

Yes but as soon as the drivers are ready they should be backported to jaunty as a bugfix.

---

### Post by Mehall on 2009-07-12
Can I remind everyone that Compiz is fairly graphically intensive, overall, and Integrated Intel chipsets running it at all is a minor miracle?

And also, Compiz not running doesn't stop you using your machine.

As another poster said already, video playback has mostly been fine.

I honestly think the Intel graphics "issue" has been over-exaggerated.

---

### Post by Closed_Port on 2009-07-12
> **decoherence said:**
> The intel drivers are compiled in to the kernel? I thought the driver was xserver-xorg-video-intel? Please enlighten :)

They are neither compiled into the kernel, nor are they in any way part of the kernel. cariboo907 is simply wrong.

> **decoherence said:**
> 
In any case, is it Intel's fault Canonical shipped their driver when Canonical knew it had major performance problems? Did Canonical *have* to ship that version of Xorg and kernel? I suppose it brought some new features to other users... was it worth the breakage?

It's even worse. By the time they shipped jaunty there were already newer drivers available that solved most of the problems. But instead of making an exception and putting these drivers into jaunty though it was after the freeze, they decided to ship with the broken drivers and offer a ppa with the newer drivers.

---

### Post by SunnyRabbiera on 2009-07-12
> **Mehall said:**
> Can I remind everyone that Compiz is fairly graphically intensive, overall, and Integrated Intel chipsets running it at all is a minor miracle?

And also, Compiz not running doesn't stop you using your machine.

As another poster said already, video playback has mostly been fine.

I honestly think the Intel graphics "issue" has been over-exaggerated.

Actually intel is slow without compiz under jaunty with me.

---

### Post by Closed_Port on 2009-07-12
> **Mehall said:**
> Can I remind everyone that Compiz is fairly graphically intensive, overall, and Integrated Intel chipsets running it at all is a minor miracle? 
So?

> **Mehall said:**
> 
And also, Compiz not running doesn't stop you using your machine.

No, but having compiz working then upgrading and having compiz not working is a major regression.

> **Mehall said:**
> 
As another poster said already, video playback has mostly been fine.

What the other poster said was the video playback did not work and he had to install newer drivers from a ppa to make it work. How is that fine?

---

### Post by decoherence on 2009-07-12
> **-=hazard=- said:**
> no one include testing drivers on OS[COLOR=Red] stable [/COLOR]release, so its not ubuntu fault but intel ;)

I'm sorry, I don't understand. Surely you aren't saying that Ubuntu 9.04 isn't a stable release? Packages are frozen; it's stable by the definition of "stable" typically used in Linux distro development.

Unless you're saying that non LTS versions are unreliable? In this particular case, I would have to agree with you and would point back to Dimitriid's post. I would further say that, in this case, blame would still rest on Canonical for encouraging their users to use this unreliable system without giant caveats posted at every step of the download process.

Or maybe I'm just misunderstanding you completely... sorry!

---

### Post by Closed_Port on 2009-07-12
> **-=hazard=- said:**
> Those drivers are still being tested 
**PPA for Intel graphics driver testing**

no one include testing drivers on OS[COLOR=Red] stable [/COLOR]release, so its not ubuntu fault but intel ;)
The only problem of course is that these drivers are stable and were already stable when jaunty was released.

---

### Post by decoherence on 2009-07-12
> **Closed_Port said:**
> It's even worse. By the time they shipped jaunty there were already newer drivers available that solved most of the problems. But instead of making an exception and putting these drivers into jaunty though it was after the freeze, they decided to ship with the broken drivers and offer a ppa with the newer drivers.

That I did not know...

Why not push the fixed drivers in to the main repo after the fact? Because they weren't tested? wouldn't that be ironic... :lolflag:

---

### Post by -=hazard=- on 2009-07-12
There are 999999*** hardwares out there who do you think should develope and maintain the drivers? The os makers? C'mon It's all intel fault, just compare with nvidia what a great work they do, I use nvidia and never had a single problem with the drivers testing it in diferent distros.

---

### Post by Closed_Port on 2009-07-12
> **decoherence said:**
> That I did not know...

Why not push the fixed drivers in to the main repo after the fact? Because they weren't tested? wouldn't that be ironic... :lolflag:
I think that's exactly the reason.
To be fair, I think it's understandable that projects as complex as ubuntu have to have a version freeze sometime before a release. And I also can understand that the devs are very reluctant to make exceptions to this shortly before a release. The risks are simply to high.

So I can understand their reasoning and I don't claim that this was an easy situation or that I would have had an ideal solution at hand. But I think that in this case shipping with the broken drivers was the wrong decision.

To their credit, the devs made every effort to make it easy for people to get the newer drivers that fixed the problems. They immediately set up a ppa with them. 

But I simply think that people who chose a userfriendly distribution shouldn't have to set up a ppa to get working drivers.

---

### Post by Closed_Port on 2009-07-12
> **-=hazard=- said:**
> There are 999999*** hardwares out there who do you think should develope and maintain the drivers? The os makers? C'mon It's all intel fault, just compare with nvidia what a great work they do, I use nvidia and never had a single problem with the drivers testing it in diferent distros.
Look, first off, as I already mentioned, Intel had already shipped working drivers before jaunty came out. Now is it Intel's fault that they weren't included?

Second, the current problems with the intel drivers are due in large pare to intel really engaging with the linux and xorg community to fix some longstanding problems. For example, who do you think is working on dri2, kms, rootless X? Intel. And guess what, in the process of really changing the X infrastructure, there are bound to be some problems.

---

### Post by decoherence on 2009-07-12
> **-=hazard=- said:**
> There are 999999*** hardwares out there who do you think should develope and maintain the drivers? The os makers? C'mon It's all intel fault

The point of this whole thread is that I'm trying to find someone who can explain to me why Ubuntu shipped this driver when it was well known that it had major performance problems. I'm not saying it's canonical's reponsibility to fix Intel's driver. I'm saying it's their responsibility to ensure packages that have a huge negative effect on usability do not make it in to the system.

The community did their job. Everybody knew these new drivers sucked. And yet, there they were in the release.

From my perspective (after hearing what Closed_Port has to say) it seems like Ubuntu should've shipped the old "safe" drivers and offered the news ones through a PPA, or even as an alternate (non-default) package in the main repo.

---

### Post by SunnyRabbiera on 2009-07-12
> **decoherence said:**
> The point of this whole thread is that I'm trying to find someone who can explain to me why Ubuntu shipped this driver when it was well known that it had major performance problems. I'm not saying it's canonical's reponsibility to fix Intel's driver. I'm saying it's their responsibility to ensure packages that have a huge negative effect on usability do not make it in to the system.

The community did their job. Everybody knew these new drivers sucked. And yet, there they were in the release.

From my perspective it seems like Ubuntu should've shipped the old drivers and offered the news ones through a PPA, or even as an alternate (non-default) package in the main repo.

Well with in between releases Ubuntu can get away with testing out new kernels and stuff, this is not the first time this has happened.
It happened back with 7.04 where there was all that issue with ATA, it was gone in 7.10
It seems uneven number with .04 are cursed or something, but uneven number with .10 might be the recovery point...
we cant be certain though as its not out yet :D

---

### Post by -=hazard=- on 2009-07-12
> **decoherence said:**
> The point of this whole thread is that I'm trying to find someone who can explain to me why Ubuntu shipped this driver when it was well known that it had major performance problems..

Because if not, then all the intel/ubuntu users what would do? Downloading the driver from the intel site.. in that case would be the same thing. That driver is the official one so when an operating system come out and if the driver of an exact hardware works but have some "known bugs", you have to include it because all softwares have known bugs and developers are working to fix them. What I want to say is, why should a intel user go take the official driver on intel website (even if it have known bugs but still works and is official), when he can easily download and install it from ubuntu repo?!

---

### Post by decoherence on 2009-07-12
> **-=hazard=- said:**
> Because if not, then all the intel/ubuntu users what would do? Downloading the driver from the intel site.. in that case would be the same thing. That driver is the official one so when an operating system come out and if the driver of an exact hardware works but have some "known bugs", you have to include it because all softwares have known bugs and developers are working to fix them. What I want to say is, why should a intel user go take the official driver on intel website (even if it have known bugs but still works and is official), when he can easily download and install it from ubuntu repo?!

I think you misunderstand. What I'm saying is that Ubuntu should've shipped pre-regression Intel drivers (which are, of course, still available) and offered the new ones as an option to those who wanted them. In such a case, it would not be necessary for anyone to go to intel's website to get drivers.

What I want to know now is whether there is a reason they could NOT ship the pre-regression intel drivers and offer the new ones as an option through a repository. Was it just a case where everyone was hoping the regression would be fixed in time for the freeze and it wasn't? Or were the old drivers not compatible with the version of Xorg they wanted to ship? Or what?

I don't know, so I ask ;)

---

### Post by 23meg on 2009-07-12
[QUOTE=decoherence]I just want to know why people think (or if anyone actually knows) why this crummy driver was included in the release?[/QUOTE]

[http://www2.bryceharrington.org:8080/drupal/intel-2.6.1](http://www2.bryceharrington.org:8080/drupal/intel-2.6.1)
[http://www2.bryceharrington.org:8080/drupal/to-update-or-not-to-update](http://www2.bryceharrington.org:8080/drupal/to-update-or-not-to-update)

[QUOTE=decoherence]What I'm saying is that Ubuntu should've shipped pre-regression Intel drivers (which are, of course, still available) and offered the new ones as an option to those who wanted them. In such a case, it would not be necessary for anyone to go to intel's website to get drivers.[/QUOTE]

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by starcannon on 2009-07-12
> **Dimitriid said:**
> Aggressive release cycles are not for everybody. Canonical should do a better job at promoting LTS version. The current model is just not ideal if you ask me: You got a 6 month release cycle that includes a lot of new features and gets a lot of promotion while the LTS gets buried.

I think LTS should be offered more aggressively because to me, 90% of new users should default to the LTS version.

Exactly right. LTS versions are what most should probably be using; the 6 month releases are imo just for finding out what works/doesn't work for the next LTS. I may be clear off base there; though, for me, the only reason I move to a 6 month release is if there is some piece of hardware that works in it that didn't previously work. So far this has been a good choice for me. Currently I use 8.04 on my desktops, 8.10 on my laptops, and 9.04 on my netbooks. Since my netbooks are no nonsense workhorses, the benefits of the release for my particular hardware needs outwieghed the intel driver issue, otherwise I'd have run 8.10 on my netbooks as well.

Use the release cycle that gets the job done for you.

---

### Post by decoherence on 2009-07-12
Thank you 23meg! The 2nd link specifically was what I didn't know.

Assuming that Bryce Harrington is accurately representing the issue, and in particular considering his fifth consideration, I think that once again we go back to Dimitriid's first post. If Ubuntu is truly going to be user-centric, it should spare most of its users these kinds of issues. The best way that I can currently see to do this is by curbing a potential user's natural desire to download the latest and greatest and encouraging them to use an LTS release.

However this is in direct contradiction to the spirit of what Bryce Harrington has to say in his second and third reasons for staying close to upstream. If you encourange your users to use LTS versions, you're diminishing your own testing and feedback base. Really, people SHOULD be using the very latest they can, without falling prey to bugs.

Perhaps one solution would be posting those sorts of caveats on each step of the download process. We know what the major issues are probably going to be before the release (blessed open source development) it shouldn't be hard to get the word out, before people download the thing, and without them having to read the release notes.

Unfortunately that doesn't go far enough. As a user-centric distro, Ubuntu shouldn't assume people know whether or not they're using Intel video (for instance.) Perhaps the download page should have some kind of hardware scanning tool that will look for certain hardware configurations known to not work well. That'd be a tall order, though, both in terms of development (perhaps.... maybe there's something already out there?) and the burden of trust it would place on the site and the user.

Anyway, I'm actually on vacation and my cousin is giving me weird looks and dinners almost ready and I'm on my 2nd beer so... I guess I'll sign off for the night! I look forward to seeing if there are any other ideas or responses tomorrow.

Thanks, everyone who contributed to this thread!

---

### Post by lswb on 2009-07-12
> **cariboo907 said:**
> Ubuntu had nothing to do with it, the Intel drivers are compiled in the kernel, there is no separate driver. All distributions that have the same combination of kernel and Xorg have the same problem. Put the blame where it belongs, on Intel.

I didn't realize that Intel specified which kernel and xorg version ubuntu had to use...

---

### Post by lswb on 2009-07-12
This is nothing new really, look at past releases to see similar problems:

When the new version Ralink chip wifi drivers were first released, ad-hoc networking stopped working; I don't know if this was ever fixed, I've since gotten a new laptop with internal wifi adapter.

NetworkManager; too many problems to list, some are still not fixed; The big one that comes to mind is no network available without gui login.

Early versions of the newer style disk drivers (The ones that show IDE drives as sdxx instead of hdxx) would not work with certain pcmcia hardware;

PulseAudio, need I say more?

---

### Post by calrogman on 2009-07-12
> **cariboo907 said:**
> Ubuntu had nothing to do with it, the Intel drivers are compiled in the kernel, there is no separate driver. All distributions that have the same combination of kernel and Xorg have the same problem. Put the blame where it belongs, on Intel.

Since the xserver-xorg-video-intel package is just a placebo which definitely doesn't mention, in its description, providing the drivers for the i8xx and i9xx chipsets.

---

### Post by hanzomon4 on 2009-07-13
LTS was never about stability.. it's supported longer and that's it. The intel fiasco was Canonical's/Ubuntu's fault. You don't ship broken drivers for such an important and widely used device. They could have shipped the older drivers, requiring a ppa for normal performance is not acceptable.

---

### Post by decoherence on 2009-07-13
> **hanzomon4 said:**
> LTS was never about stability.. it's supported longer and that's it.

In theory, yes, however this very issue, as well as the ones mentioned by lswb, show that this isn't the case in practice. And that only makes sense... newer packages tend to have more bugs.

> The intel fiasco was Canonical's/Ubuntu's fault. You don't ship broken drivers for such an important and widely used device. They could have shipped the older drivers, requiring a ppa for normal performance is not acceptable.

I agree. Upon further thought of Bryce's points about staying upstream (particularly getting easy bug fixes) it seems to me that if the old Intel driver is still being supported in the LTS release anyway, why not keep it in the regular release?

---

