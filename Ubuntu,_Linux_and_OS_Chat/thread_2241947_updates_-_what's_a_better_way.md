---
title: "updates - what's a better way?"
date: 2014-08-29
forum: Ubuntu, Linux and OS Chat
---

### Post by v-piotr on 2014-08-29
Hi guys,

I have been using linux systems for a long time (on servers). And from time to time I try to get myself to use it on a desktop (I use OS X as my main desktop). 
I am quite happy with current state of Ubuntu on desktop however I have one thing that would like to be looked at.

Updates - for instance today update manager poped out saying that new updates are ready. Well I didn't think much about it (got used to OS X too much) and I clicked to install it. After reboot what was my surprise to find out that unity is broken, virtualbox and few other bits. To got it fixed - I had to reinstall kernel headers and some other packages.

However my point is that for someone who is not used to cmd line it might be a show stopper.

Don't get me wrong this post is not a rant I just would like to see wider linux on desktop adoption by average Joe.

So I think the question is how do you think we can improve updates?

Thanks

---

### Post by mcduck on 2014-08-29
It seems to be really, really rare for the updates to break anything unless you are using third-party software sources or have made some other modifications to the system yourself. So I doubt the updates are anywhere close to being an issue to the basic desktop users (who are more likely to just use the default setup and what's available in the official repositories).

I'd say the biggest issues updates might cause are for the people who fall in the gap between a basic user and a skilled user, comfortable enough with computers and Linux to mess around with things, but not always sure what changes might cause problems and how to fix/avoid them.

...and then there's the very rare case of an update actually causing something to break on a standard Ubuntu setup running on some specific hardware etc, but that really doesn't seem to be a common thing so if you are unlucky enough and that's the case with your problems, then my advice would be to file a bug report, and if needed then ask around in the forums how to fix the problem.

(I've been using Ubuntu since 2005, I always just install all the available updates, and have never had any issues. I really can't remember more than one or two occasions when there's been update that has caused problems to any larger amounts of users, it's pretty much always something specific to certain user's systems, most of the time incompatibility with third-party drivers installed from outside of repositories, or additional software sources)

edit: If I'd really have to think of something to improve, it seems that the warning about partial update (which you should only really ever see if using incompatible 3rd-party repository or development version of Ubuntu) isn't always enough to stop people from proceeding with the update without understanding the risk. People are too happy to click OK on windows without reading (and understanding ) the warning text, so it might help avoid some troubles if partial updates would only be allowed from CLI or Synaptic, and the GUI update tool would just show the warning instead and advice the user to try again later...

---

### Post by v-piotr on 2014-08-29
Well, in my case it was mostly virtualbox and unity-scope-virtualbox (which broke unity)  which comes from standard ubuntu repo (and other stuff which relates to virtualbox as I route my traffic through internal VM). 
I agree that partial updates shouldn't be allowed with one click if they can break stuff. I also believe that perhaps we shouldn't push updates from upstream as soon as they are ready - first would prefer to have it tested throughout (with every combination of packages in standard repos) to make sure that nothing breaks - even if that means that updates are delivered a bit later.
An exception could be a critical security patch that needs to be pushed ASAP.

---

### Post by ian-weisser on 2014-08-29
> **v-piotr said:**
> After reboot what was my surprise to find out that unity is broken, virtualbox and few other bits. To got it fixed - I had to reinstall kernel headers and some other packages.

However my point is that for someone who is not used to cmd line it might be a show stopper.

You're assuming that the upgrades are responsible for your breakage.

What you describe is common in systems with non-Ubuntu software installed. We see it a lot here. Video drivers from goodness-knows-where, VBox from Oracle (instead of the Ubuntu Repos), etc. In such cases, it's not Ubuntu's fault that the third-party software didn't include the header dependency, and it's not Ubuntu's fault that the third-party software didn't use the correct hook to recognize new headers to recompile against.
Please file a bug report on the non-Ubuntu software's bug tracker. Developers would generally like their software to work.

If your broken software *is* from the Ubuntu repositories, then please file a bug report. Bug reports are how you fix the problem.

---

### Post by ian-weisser on 2014-08-29
> **v-piotr said:**
> I also believe that perhaps we shouldn't push updates from upstream as soon as they are ready - first would prefer to have it tested throughout (with every combination of packages in standard repos) to make sure that nothing breaks - even if that means that updates are delivered a bit later.
An exception could be a critical security patch that needs to be pushed ASAP.

That pretty much describes how upgrades work in Ubuntu already.
Well done.

---

### Post by uRock on 2014-08-29
I believe the biggest problem here is the repo version of VirtualBox. It causes too many problems.

OP, I recommend installing the VirtualBox offered on the the Oracle website. [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) 
You will have to uninstall the repo version first.

---

### Post by deadflowr on 2014-08-29
Thread moved to [I][B]Ubuntu, Linux and Os Chat

[/B][/I]They have been trying
[https://wiki.ubuntu.com/PhasedUpdates](https://wiki.ubuntu.com/PhasedUpdates)
maybe they could have an opt-in for those willing to be the first to get the updates.

---

### Post by v-piotr on 2014-08-29
> **ian-weisser said:**
> 

If your broken software *is* from the Ubuntu repositories, then please file a bug report. Bug reports are how you fix the problem.

Thanks, will do

---

### Post by grahammechanical on 2014-08-29
Here is the existing procedure.

[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

Regards.

---

### Post by speedwell68 on 2014-08-29
I have to say that other than the update from 7.04 to 7.10 I don't think I have ever had an update that broke anything.  I wish I could say the same for Windows XP and Windows 7.:D

---

### Post by cariboo on 2014-08-29
I've been running pr-release versions for years, and usually update at twice a day. It's only been since I built a new system with a graphics card that isn't supported by the Nvidia driver in the repositories that I've had problems with upgrades. I started out using the nvidia-340 driver from the xorg-edgers ppa, but as newer kernels have been released, I've had to install new drivers. I'm currently running nvidia-343, and I'm quite impressed with the quality of my desktop.

---

### Post by diepnguyen on 2014-09-01
I run these commands: apt-get update and apt-get upgrade every week  on my servers.

---

