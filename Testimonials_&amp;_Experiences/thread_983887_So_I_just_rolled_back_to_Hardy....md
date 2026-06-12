---
title: "So I just rolled back to Hardy..."
date: 2008-11-16
forum: Testimonials &amp; Experiences
---

### Post by cdekter on 2008-11-16
Yup... I just ditched Intrepid and went back to Hardy. What made me do this?

On my laptop with 1Gb of RAM, Intrepid behaved like it had half that amount of RAM - constantly thrashing the hard disk whenever switching/opening/closing applications, even with only a couple of things open. 

Many applications took longer to start (Evolution, Firefox, etc etc).

Boot time was noticeably longer than Hardy.

An annoying regression in the Intel 965GM driver that causes all video playback to tear (vsync can't be enabled, unless you switch to Metacity).

None of these problems are present in Hardy, and the couple of apps that I want newer versions of, I can get them from PPAs.

I guess I'll wait a few months and see if the problems are fixed, but to be honest, there wasn't that much in Intrepid that made me want to upgrade as it is. It is, yes, disappointing...

---

### Post by exploder on 2008-11-16
cdekter, your experience is almost identical to mine. I run Mint and it is Ubuntu based. Elyssa based on Hardy runs much better for me. I updated most of my applications through getdeb.net to have the newer versions. The Hardy based system runs much faster and has considerably less bugs at this point in time. Probably after a few months Intrepid will receive enough updates to run better. 

Most of the new features that are in Intrepid, I will never use. I have no use for a guest account, eject buttons or encrypting my system. Those that are enjoying Intrepid probably had hardware issues with Hardy so they are benefiting from the new kernel and better wireless support.

I will wait and see what happens with Intrepid or wait and see how Jaunty runs. The LTS release will be supported for some time yet so there is plenty of time to see how things develop.

---

### Post by Tamlynmac on 2008-11-16
My aversion to beta video drivers kept me from upgrading (NVIDIA) one of our five machines. That machine was to be used as a benchmark for when to install 8.1 on all of our systems. Obviously, I'm also waiting.

I truly did appreciate one aspect of Ubuntu. A pop up window informed me prior to install that my video card was not supported beyond 800x600. This feature alone saved me from either re-installing 8.04 or being forced to use a beta video driver as I simply hit the cancel button. I don't ever recall receiving a pop up or any other driver support notification in Windows prior to install. It always came after install when my drivers didn't work. The driver issue is with NVIDIA not Ubuntu and after notifying NVIDIA I received a response that they were already working on the driver. Guess I really can't complain.

Hardy works fine on all our systems and meets / exceeds our expectations. As with you, I'll remain here until 8.1 works out all the issues. A number of long term forum members have posted statements noting they would wait until the new release had at least one update. Obviously good advice. Patience must be a virtue.

---

### Post by Crafty Kisses on 2008-11-16
A lot of people are having issues with Intrepid, I was having a lot of issues. Hopefully they can patch some of the problems soon enough.

---

### Post by loell on 2008-11-16
I always dual boot current version - 1 :)

---

### Post by wolfen69 on 2008-11-16
it's OK.

---

### Post by cdekter on 2008-11-17
Well I've been back on Hardy for about a day now, and honestly the improvement is dramatic. The system is much more responsive, Compiz seems to achieve higher framerates, and it's generally a joy to use. Good thing its an LTS release!

---

### Post by Golem XIV on 2008-11-17
Problems here, too.  Resuming from suspend is broken in Intrepid (in Hardy it "just works").  Seems to be a kernel probem, I tried Sidux that has the same kernel version and it had the same symptoms.

A minor problem is the nVidia driver related title bar corruption, also not an issue in Hardy.

I'll be waiting for Jaunty for my next upgrade, or maybe try Mepis? hmmmm...

---

### Post by Afkpuz on 2008-11-17
Every release, there are threads like this.  I have to say that I have had the opposite experience.  My boot time improved, as well as compiz running pretty much identically to my hardy experience.  I did however have a bad install the first time I tried intrepid.  I reinstalled and it was fine.  Sorry intrepid didn't work for yall.

---

### Post by Luke has no name on 2008-11-17
Intrepid seems to suspend/resume better than Hardy for me. In any case, I don't like how fixing bugs are secondary to providing new features. If Ubuntu had half the bugs it has now, it would be a dramatically less painful than it is now. (It's not THAT painful... I just tried Kubuntu ;) ) 

Forget Empathy! Forget the aesthetics of the top menu bar! Make sure our computer is FUNCTIONAL!

---

### Post by zero244 on 2008-11-17
Im not running 8.10 right now, but I did try it in live cd mode and surprisingly it ran faster than any Ubuntu Ive tried from the CD.
It ran faster from the CD than Edgy does from my hard drive.
I dont plan on upgrading anytime soon. Edgy runs great.......>Ive got some 3D effects with Beryl 2.0.
I think someday Ubuntu will become a polished complete OS.
I actually still think Linux in five to ten years will be the OS of choice.
Microsoft's greed and Windows horrible security will eventually be its downfall.
Unless Microsoft does what apple did and makes linux\unix the core of its OS with Windows only as a window manager.

---

### Post by cdekter on 2008-11-18
Can I add that I experienced these performance issues on BOTH my systems:

Laptop with Intel Dual Core @ 1.73Ghz, 1Gb of RAM, Intel GM965 graphics
Desktop with AMD X2 4000+, 2Gb of RAM, GeForce 7900GT

As you can see, totally different hardware in every respect, so the problem can't be hardware specific. Both of these were clean installs too.

---

### Post by softtower on 2008-11-18
Well... sometimes you have no choice. I *loved* Hardy and could have stayed on it forever, but the new laptop comes in, and only the latest kernel has any drivers for it...

By the way, do LTS versions receive any driver updates? Ever? Is it reasonable to expect that Hardy will ever "learn" how to talk with both of my network cards and a newest integrated graphics from Intel?

I hate being bleeding edge: upgrading OS once every 3 years is what I need, but I want to have the fastest hardware available. Is it possible with any Linux distro? I checked Arch, and it seems to be the same way: updates are constantly rolling, so one day you can suspend/resume but then the next version of driver FOO comes in, and not anymore.

---

### Post by cdekter on 2008-11-19
> **softtower said:**
> Well... sometimes you have no choice. I *loved* Hardy and could have stayed on it forever, but the new laptop comes in, and only the latest kernel has any drivers for it...

By the way, do LTS versions receive any driver updates? Ever? Is it reasonable to expect that Hardy will ever "learn" how to talk with both of my network cards and a newest integrated graphics from Intel?

I hate being bleeding edge: upgrading OS once every 3 years is what I need, but I want to have the fastest hardware available. Is it possible with any Linux distro? I checked Arch, and it seems to be the same way: updates are constantly rolling, so one day you can suspend/resume but then the next version of driver FOO comes in, and not anymore.

You can have some of that by enabling the backports repository and installing the linux-backports-modules-xxx where xxx is the release you are on (eg hardy). This means you'll get at least some newer drivers that have been backported. Usually this is done for a good reason (like hardware not working at all), so you may have some luck with it.

---

