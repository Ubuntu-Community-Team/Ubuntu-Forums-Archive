---
title: "Question about Preload 0.6.3"
date: 2008-12-06
forum: The Cafe
---

### Post by CraigPaleo on 2008-12-06
I've noticed that the latest version of Preload is 0.6.3 but the version in the repository is 0.4-5. 

Is there a reason for the older version being in the repository. Has anyone tried the latest version? If so, are there any bugs/problems with it? Is it any better or worse than the one in the repository?

---

### Post by Vadi on 2008-12-06
> **CraigPaleo said:**
> I've noticed that the latest version of Preload is 0.6.3 but the version in the repository is 0.4-5. 

Is there a reason for the older version being in the repository. Has anyone tried the latest version? If so, are there any bugs/problems with it? Is it any better or worse than the one in the repository?

Same reason why you're asking...

---

### Post by CraigPaleo on 2008-12-06
> **Vadi said:**
> Same reason why you're asking...

I see. So, there hasn't been enough testing for the latest to be worthy of inclusion in the repository. That makes sense. 

I do like preload. It now loads Firefox lickety-split, though it took about a week for preload to "learn" it. 

I had always wondered why Macs load Safari and Windows loads Explorer each faster than they load Firefox but from what I've read, they use their own versions of Preload for their own applications and not for the third-party apps. I figured they somehow gave their own apps some kind of edge. 

I really like how preload figures out which apps you use most often and goes by that rather than by the apps origins or DE environment.  

Mandriva must have something similar but pre-configured because Firefox pops up immediately while some KDE apps take longer - even Konqueror.

---

### Post by Vadi on 2008-12-06
Yep, preload is definitely a nice thing.

And don't worry about getting it updated - it will be in the next ubuntu version :)

---

### Post by Paqman on 2008-12-06
> **CraigPaleo said:**
> 
I had always wondered why Macs load Safari and Windows loads Explorer each faster than they load Firefox but from what I've read, they use their own versions of Preload for their own applications and not for the third-party apps. I figured they somehow gave their own apps some kind of edge. 


Kind of. For Windows, IE is so intrinsically bound up with the OS that large parts of it are always loaded up whenever the machine is running. So it's not really an intelligent app like preload doing clever things, it's just the way Windows is built.

No idea about OS X, though.

---

### Post by CraigPaleo on 2008-12-06
> **Vadi said:**
> Yep, preload is definitely a nice thing.

And don't worry about getting it updated - it will be in the next ubuntu version :)

Awesome! Though I don't know how it could work much better. :D

---

### Post by CraigPaleo on 2008-12-06
> **Paqman said:**
> Kind of. For Windows, IE is so intrinsically bound up with the OS that large parts of it are always loaded up whenever the machine is running. So it's not really an intelligent app like preload doing clever things, it's just the way Windows is built.

No idea about OS X, though.

I can't, for the life of me, find what it's called now but OS X does have a similar feature to windows. It may be that Coco apps are as intrinsic to the Mac OS as Windows apps are to Windows. Either way, third-party apps, on those OS's are much slower to load. 

But, Ubuntu with preload makes it much less embarrassing when trying to convince others that Linux is actually faster without having them ask why the web browser or file manager takes so long to load.

---

### Post by Magnes on 2009-01-04
I installed on Intrepid package for Jaunty from here:

[http://ppa.launchpad.net/uninea/ubuntu/pool/main/p/preload/](http://ppa.launchpad.net/uninea/ubuntu/pool/main/p/preload/)

Works for now. :)

---

### Post by ssam on 2009-01-04
> **Magnes said:**
> I installed on Intrepid package for Jaunty from here:

[http://ppa.launchpad.net/uninea/ubuntu/pool/main/p/preload/](http://ppa.launchpad.net/uninea/ubuntu/pool/main/p/preload/)

Works for now. :)

i'll give that a try. preload ought to be installed by default (at least until prefetch is ready).

---

### Post by mali2297 on 2009-01-04
> **CraigPaleo said:**
> I've noticed that the latest version of Preload is 0.6.3 but the version in the repository is 0.4-5. 

Is there a reason for the older version being in the repository. Has anyone tried the latest version? If so, are there any bugs/problems with it? Is it any better or worse than the one in the repository?

I use CRUX and upgraded preload to 0.6 almost immediately when it was released in July 2008. It was seriously buggy; patches 0.6.1, 0.6.2, 0.6.3 came the same month. Since the last patch, it is stable.

Is it better than 0.4? I can't say, but I would like to think so.

---

### Post by binbash on 2009-01-05
> **Magnes said:**
> I installed on Intrepid package for Jaunty from here:

[http://ppa.launchpad.net/uninea/ubuntu/pool/main/p/preload/](http://ppa.launchpad.net/uninea/ubuntu/pool/main/p/preload/)

Works for now. :)

I will give it a try, thanks

---

### Post by CraigPaleo on 2009-01-22
> **Magnes said:**
> I installed on Intrepid package for Jaunty from here:

[http://ppa.launchpad.net/uninea/ubuntu/pool/main/p/preload/](http://ppa.launchpad.net/uninea/ubuntu/pool/main/p/preload/)

Works for now. :)

Thank you! I've just upgraded to preload-0.6.3 after completely removing 0.4-5. Wow! what a difference! It's now re-learning my most frequently used apps and I had forgotten how much longer it takes Firefox and others to load without preload installed and how much faster boot-times are. I'll restart my computer and the apps I want preloaded a few times. That should get me there faster. 

Preload should really be installed by default on Ubuntu! I notice a lot posts asking, or *complaining* that Ubuntu appears slower to launch apps than Windows and Mac, which both have a similar feature. Ubuntu could even pre-configure preload to load commonly used apps such as Firefox, Network Manager, and Nautilus. If a user uses other apps more frequently than the most common, preload will figure it out by itself and adapt soon enough. 

Where do I go to suggest this? Brainstorming?

---

### Post by Paqman on 2009-01-22
> **CraigPaleo said:**
> 
Where do I go to suggest this? Brainstorming?

Yep, although it's already been suggested:

[Install Preload by default]("http://brainstorm.ubuntu.com/idea/14092")

I've +1'd it btw. I agree, this would be a good default app.

---

### Post by CraigPaleo on 2009-01-22
> **Paqman said:**
> Yep, although it's already been suggested:

[Install Preload by default]("http://brainstorm.ubuntu.com/idea/14092")

I've +1'd it btw. I agree, this would be a good default app.

Thanks for finding that. I've +1'd it too. Only 61 votes since October though. Could it just be that not many people know about it? I happened to find out about it by stumbling across an optimization thread myself.

---

### Post by Paqman on 2009-01-22
> **CraigPaleo said:**
> TCould it just be that not many people know about it?

Probably. Unfortunately we're not allowed to use Brainstorm's "promote this idea" images in sigs on this forum, which seems odd. A text link would work fine, though.

---

