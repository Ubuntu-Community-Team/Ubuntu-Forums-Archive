---
title: "Ubuntu Desktop Team Q&amp;A on Youtube"
date: 2021-04-23
forum: Ubuntu, Linux and OS Chat
---

### Post by grahammechanical on 2021-04-23
The Ubuntu Desktop team held a question and answer session on Ubuntu On Air on Youtube at 15.00 UTC Friday 23 April 2021. I missed it but it is recorded. Here is the link

[https://www.youtube.com/watch?v=SmthCRF-NQQ](https://www.youtube.com/watch?v=SmthCRF-NQQ)

Some interesting questions were asked and answered on the future direction of Ubuntu desktop. There were other questions which in my opinion were .... Shall we say? Were answered as well.

It seems that in future there may be other Ubuntu On Air Q&A sessions but no schedule has be decided yet. As if knowing how to pronounce Ubuntu was not enough, there is another South African word for us to learn.

Regards

---

### Post by guiverc on 2021-04-23
Thank you, I missed it too (a bit passed my bedtime, and I so needed sleep b/c release..)

---

### Post by TheFu on 2021-04-23
Listening now. Nothing really added by video.

Maybe someone could ask why Ubuntu employees don't spend any time in UbuntuForums?  

54 min in, there's a discussion about LTS updates and choices. 
"We don't tend to generally release new features" ... with the exception of HWE kernels. They try to stay on "point-release" updates from upstream projects. Those are bugfixes, not features.

---

### Post by grahammechanical on 2021-04-24
To tell the truth I was disappointed but I decided to draw attention to the broadcast anyway. I was hoping for some interesting news about the future direction of Ubuntu. The nearest I came to being interested was when I heard an almost causal remark that a little bit of work was being done on producing a version of Ubuntu core with a modular desktop environment. 

Ubuntu core is a snap OS. It lacks any means of running more than one GUI application at a time (Kiosk type app). Now, I know that snaps are controversial but they do have a level of security greater than present deb based Ubuntu. And Ubuntu core has a roll back feature should an upgrade to the OS fail. No more black screens after an update. In fact. in 2015 I did experiment with something call Ubuntu Personal or Snappy Ubuntu Desktop Next. It worked well but development was not continued. The only apps available were click apps and they did not work on the snappy OS.

When Ubuntu Discourse came out I hoped that developers would use that as an opportunity to present news of projects under development. I no longer visit Ubuntu Discourse.

Regards

P.S. OMG! Ubuntu was my original source for this Ubuntu On Air Q&A and I have just been reading though the comments. What a flame war! But I learnt something from Jorge Castro. The expression to watch out for in the future is "Immutable Desktop." Whatever that means. To quote Jorge:

> they  just talked about the single most important change in the history of  the Ubuntu desktop!! We've needed an immutable desktop for the longest  time and now we're finally going to get one!

---

### Post by grahammechanical on 2021-04-24
Answer to what an immutable desktop is - Apparently Fedora has one. It is called Silverblue. The operating system cannot be changed during runtime.

> In Silverblue&#8217;s case, it&#8217;s the operating system that&#8217;s immutable. You  install applications in containers (more on this later) using [Flatpak]("https://flatpak.org"),  rather than onto the root filesystem. This means not only that the  installation of applications is isolated from the core filesystem, but  also that the ability for malicious applications to compromise your  system is significantly reduced. It&#8217;s not impossible&#8212;we generally try to  avoid the word "impossible" when describing attacks or vulnerabilities  in security&#8212;but the risk is significantly lower.

[https://www.redhat.com/sysadmin/immutability-silverblue](https://www.redhat.com/sysadmin/immutability-silverblue)

Sound familiar?

Regards

---

### Post by TheFu on 2021-04-24
ChromeOS on chromebooks works that way.  There are two "root" partitions. Updates happen to the one not in use currently. If the boot into the updated OS fails, it tries to boot the alternative.

Using snaps for a kiosk setup seems like a smart idea.

---

