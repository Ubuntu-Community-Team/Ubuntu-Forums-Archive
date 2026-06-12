---
title: "ubuntu studio 8.1 inconsistency?"
date: 2009-01-27
forum: Ubuntu Studio
---

### Post by downbeat on 2009-01-27
Hello fellas! I have one simple question. Why the ubuntu studio last version doesn't have a kernel rt by default? they do not seem inconsistent?

Thanks.

---

### Post by Stochastic on 2009-01-27
During 8.10's development cycle there were numerous issues with the kernel, late into the development cycle it was decided a different version would be used.  Because of this, there wasn't enough time to bugfix the realtime patch into the new kernel, and there were many problems with it once it was patched.  The UbuntuStudio developers issued a warning when they released 8.10 that the RT kernel was not fully functional and would not be included by default or as a dependency of the audio meta-package.  They also advised those serious about audio to stick with 8.04 until such time that the RT kernel issue could be sorted out.

---

### Post by demios on 2009-01-27
any idea on the progress? I really don't want to revert to 8.04 in the middle of a semester, but I also hate 40ms+ latency and xruns

or, if there's a rt capable kernel that works with studio 8.10?

[http://www.linuxmusicians.com/viewtopic.php?f=27&t=795](http://www.linuxmusicians.com/viewtopic.php?f=27&t=795) mentions a patch that stabilized 2.6.26-8-rt12, but I've never messed with kernels in depth so I have no real idea what they're talking about.
patch:
[http://marc.info/?l=linux-rt-users&m=123108406911298&w=4](http://marc.info/?l=linux-rt-users&m=123108406911298&w=4)

---

### Post by Stochastic on 2009-01-28
Um 2.6.26 was the kernel that got ditched from the Intrepid development cycle because it was not workable for a myriad of reasons - not just the lack of MIDI functionality that your referenced patch should solve.  Intrepid now runs 2.6.27 but there has been some talk on the UbuntuStudio-users list about using 2.6.24-rt in an Intrepid system (probably breaks a few things, but might be worth a try).

As for progress on the Intrepid RT, I'm hoping that they're working on the Jaunty RT rather than the Intrepid RT.

---

### Post by demios on 2009-01-28
true enough... guess I'll just downgrade to hardy until april then...
is this UbuntuStudio-users list an IRC or a forum? sounds like something I should be aware of...

---

### Post by Jormeliini on 2009-01-28
> **demios said:**
> any idea on the progress? I really don't want to revert to 8.04 in the middle of a semester, but I also hate 40ms+ latency and xruns


I've been running Ubuntu Studio 8.10 with the default kernel. I've had about 5ms latency and no xruns. RT kernel would be better but you can most likely manage without it too.

---

### Post by thorgal on 2009-01-28
as I am not depending on distro packaging for critical components like the kernel (I always compile my own), I find it more insightful to follow up on the RT kernel discussions outside any distro restricted forums. You then learn a few interesting things (correct me if I'm wrong, you out there that know better) :

no decent RT patch for 2.6.27 will happen. Instead, 2.6.28 is the focus of the RT patch guys. 

there's an RT kernel git tree that is updated regularly. I don't know if it really is a new thing but since I used to rely on the RT patch until (and including) kernel 2.6.24, I never was into the git thing.  For testing 2.6.28, I switched to the RT git tree as there's no more patches from Ingo Molnar in his usual repos. 

Basically, you clone the kernel source tree on your local HD, it comes with all the RT stuff of the day. You compile your RT kernel and check that it boots. For me, the current git tree is unbootable. But things will clear up in a matter of days or weeks. All you need is to update your local source tree by "git pulling" the latest changes. For many, this is a different way to do things but fear not, it is in fact very simple (... OK, this kind of procedure is not so weird for someone who revolved around some software development so my saying it's easy may be biased).  

For those who compile their own kernel, I left a quick how-to in the lunixmusicians.com forum :
[http://linuxmusicians.com/viewtopic.php?p=3922#p3922](http://linuxmusicians.com/viewtopic.php?p=3922#p3922)

and the discussion is about experimenting with 2.6.28:
[http://linuxmusicians.com/viewtopic.php?f=27&t=821#p3829](http://linuxmusicians.com/viewtopic.php?f=27&t=821#p3829)

---

### Post by downbeat on 2009-01-28
> **thorgal said:**
> as I am not depending on distro packaging for critical components like the kernel (I always compile my own), I find it more insightful to follow up on the RT kernel discussions outside any distro restricted forums. You then learn a few interesting things (correct me if I'm wrong, you out there that know better) :

no decent RT patch for 2.6.27 will happen. Instead, 2.6.28 is the focus of the RT patch guys. 

there's an RT kernel git tree that is updated regularly. I don't know if it really is a new thing but since I used to rely on the RT patch until (and including) kernel 2.6.24, I never was into the git thing.  For testing 2.6.28, I switched to the RT git tree as there's no more patches from Ingo Molnar in his usual repos. 

Basically, you clone the kernel source tree on your local HD, it comes with all the RT stuff of the day. You compile your RT kernel and check that it boots. For me, the current git tree is unbootable. But things will clear up in a matter of days or weeks. All you need is to update your local source tree by "git pulling" the latest changes. For many, this is a different way to do things but fear not, it is in fact very simple (... OK, this kind of procedure is not so weird for someone who revolved around some software development so my saying it's easy may be biased).  

For those who compile their own kernel, I left a quick how-to in the lunixmusicians.com forum :
[http://linuxmusicians.com/viewtopic.php?p=3922#p3922](http://linuxmusicians.com/viewtopic.php?p=3922#p3922)

and the discussion is about experimenting with 2.6.28:
[http://linuxmusicians.com/viewtopic.php?f=27&t=821#p3829](http://linuxmusicians.com/viewtopic.php?f=27&t=821#p3829)

Honestly! If the solution is to compile a new kernel, I prefer to use Slackware. 

Ubuntu Studio actually use is justified only insofar as he provides many facilities. 

I'm using Ubuntu Studio for the first time, is considered satisfactory performance to date, but precipitation was actually launch a version without the rt kernel, agree!

---

### Post by thorgal on 2009-01-28
compiling your own kernel is a workaround, not a real solution for a distro related issue. I just wanted to mention that 2.6.27 is probably a dead-end and that the 2.6.28 source tree is under the focus of the RT folks. The git stuff I mentioned is for those who don't mind compiling the kernel.

---

### Post by demios on 2009-01-28
> **Jormeliini said:**
> I've been running Ubuntu Studio 8.10 with the default kernel. I've had about 5ms latency and no xruns. RT kernel would be better but you can most likely manage without it too.

Are you using your onboard soundcard? just wondering how much that affects latency, I'm getting a presonous Firebox soon, so hopefully that helps -- I have 40ms latency and xruns with my onboard dell hardware

> **thorgal said:**
> compiling your own kernel is a workaround, not a real solution for a distro related issue. I just wanted to mention that 2.6.27 is probably a dead-end and that the 2.6.28 source tree is under the focus of the RT folks. The git stuff I mentioned is for those who don't mind compiling the kernel.

would the *.28 kernel work with 8.10, or would it be for (and released with) Jaunty? I'm going to try to avoid compiling my own kernel for the sake of the learning curve time which should be devoted to school...

---

### Post by Jormeliini on 2009-01-29
> **demios said:**
> Are you using your onboard soundcard? just wondering how much that affects latency, I'm getting a presonous Firebox soon, so hopefully that helps -- I have 40ms latency and xruns with my onboard dell hardware

I use an EMU1820 soundcard. No problems even when recording all 8 analog inputs at the same time. My best guess is that you get latency issues easier with an onboard soundcard.

---

