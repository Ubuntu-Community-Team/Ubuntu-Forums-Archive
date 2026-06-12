---
title: "lax testing before releasing updated packages?"
date: 2008-01-18
forum: The Cafe
---

### Post by PetePete on 2008-01-18
it seems that over the course of a year theres a handful of packages which get released as updates and as a result end up breaking stuff.

take for instance todays new x-org package which kills all java gui apps,  a few months ago a kernel was released which (for some reason i cant remember) had to be taken back and fixed before re-release..

sometimes it seems that the ubuntu team dont do enough vigorous testing on these packages to ensure they wont mess stuff up.

i dont care what anyone says or what excuses people make but a  OS of ubuntus popularity and resources should have updates thoroughly tested before deployment, even if this does mean a slight delay.

---

### Post by K.Mandla on 2008-01-18
So jump in there and help out, friend. File some bug reports. Start coding some patches. Do some test installs. Donate to a project.

Complaining about package quality in the Cafe is rather like shouting into a bucket.

---

### Post by PetePete on 2008-01-18
surely this should all be funded by canacol, considering they must be making a profit from ubuntu.

its the companies responsibility to ensure correct testing, maybe they should spend more money employing people to do these things properly.

its a ridiculous situation and no good for anyone... example...
i run a software company, all desktops are ubuntu running eclipse for development
the update server pushes out the new patch, now non of my team can work until the issue is resolved. ... costing me money.. 

urgh..

---

### Post by tehet on 2008-01-18
I hear they eat babies too.

---

### Post by quinnten83 on 2008-01-18
well, why not buy support from canonical. they will ensure things work they should, cause that is what you are paying for.
In case you haven't read the license, when installing it clearly states that this OS comes with no guarantees whatsoever or even the implied notion of a guarantee. Yes, it is usually stable, but there is no guarantee.
AFAIK canonical does not make a profit from Ubuntu OS, just the support they sell.

Also, if you are running Ubuntu on a business, you're best off using an update server. I think it can be set as a repository.
you can then first test the updates to see if they work, then place is on your update server after which they can be picked up by the other computers. Eliminates the problems you described.

---

### Post by quinnten83 on 2008-01-18
That being said, I am not opposed to some more testing b4 some of the software in the FOSS is released.

---

### Post by PetePete on 2008-01-18
ps i dont actually have a software company, that was just an example 

you say canonical dont make money from ubuntu os, but form the support, well those two things go hand in hand really dont they.?! no OS no support...

i hate to draw comparisions to windows but if microsoft released an update which killed all java apps there'd be massive news about it and tech websites would be laughing at them.. ubuntu released a dodgey patch and nothings said and worse still the patch is still avaliable!!!!! common guys this just isn't good enough. just cos its free shouldn't mean a reduction in software quality.... that is what FOSS is all about... right...?

Tot ziens

---

### Post by quinnten83 on 2008-01-18
Indeed no OS, no support.
but again, I refer to the licensing. No guarantees.
Although it would be nice if they did do more testing.
Would I put Ubuntu (or any other F/LOSS application for that matter) in my business, YES, but it would still be a risk and I would not do it without some precautions.
Also, you can start a support company for Ubuntu too. Can we hold you responsible for that which the FLOSS developers don't do?

Gegroet.

---

### Post by p_quarles on 2008-01-18
> **PetePete said:**
> i hate to draw comparisions to windows but if microsoft released an update which killed all java apps there'd be massive news about it and tech websites would be laughing at them.. ubuntu released a dodgey patch and nothings said and worse still the patch is still avaliable!!!!! common guys this just isn't good enough. just cos its free shouldn't mean a reduction in software quality.... that is what FOSS is all about... right...?
"If"? That sort of thing has befallen Microsoft several times. 

In any case, is there any indication that this is a widespread problem? You say that Ubuntu released a bad update, but so far this is the only thing I've heard about it. 

And I agree with K. Mandla: complaining here won't change anything. File a bug report to ensure that the package maintainers are aware of the problem. Heck, even submitting a story on Slashdot or Digg is more likely to get their attention than posting here.

---

### Post by PetePete on 2008-01-18
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/183969](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/183969)

already a bug report with 11 duplicates 

quote from Martin Pitt  
> 
After the reverted packages are published, we will have a discussion how this could happen, and what to change so that it doesn't happen again. We apologize for any inconvenience this has caused, and promise that we will provide updated packages as soon as possible.


---

### Post by beniwtv on 2008-01-18
Well, that's really bad luck in your case.

These things *might* happen from time to time, but I think Canonical and the devs try everything possible that this won't happen (or at least not that often).

On another note, I once had a Windows machine die because a update from Microsoft, so no exceptions there also.

I must be very lucky, so far no Ubuntu update did break anything for me ... 

*knocks on wood*

:)

---

### Post by p_quarles on 2008-01-18
Just got an e-mail from the Debian Security list saying that the same thing is happening with them. So, this appears to be an upstream bug. One of the hazards of the Bazaar development model.

---

### Post by PriceChild on 2008-01-18
Personally I would choose the **5 security fixes **to xorg over functional java apps.

---

### Post by p_quarles on 2008-01-18
Specifically:
[quote=debian-security-announce@lists.debian.org]
Several local vulnerabilities have been discovered in the X.Org X
server. The Common Vulnerabilities and Exposures project identifies the
following problems:

CVE-2007-5760

    "regenrecht" discovered that missing input sanitising within
    the XFree86-Misc extension may lead to local privilege escalation.

CVE-2007-5958

    It was discovered that error messages of security policy file
    handling may lead to a minor information leak disclosing the
    existance of files otherwise unaccessible to the user.

CVE-2007-6427

    "regenrecht" discovered that missing input sanitising within
    the XInput-Misc extension may lead to local privilege escalation.

CVE-2007-6428

    "regenrecht" discovered that missing input sanitising within
    the TOG-CUP extension may lead to disclosure of memory contents.

CVE-2007-6429

    "regenrecht" discovered that integer overflows in the EVI and MIT-SHM extensions may lead to local privilege escalation.[/quote]

---

### Post by PetePete on 2008-01-18
> **PriceChild said:**
> Personally I would choose the **5 security fixes **to xorg over functional java apps.

really? the security fixes in question are hardly critical, not remote root exploits by any means.

the way i see it is,

no update = i MIGHT very unlikely be exploited by something and can't work

update = i can't work.. plain and simple

hmmmm now which one do I want?!! 


hahaha obviously if i worked for a company and its a friday afternoon the answers obvious ;)

---

### Post by p_quarles on 2008-01-18
Whether those security holes are critical or not depends entirely upon the use situation. 

As for this hypothetical company being able to get work done, I look at it this way: no competent IT admin is going to apply patches willy-nilly. The admin should have first read the notices regarding the patch, and then make a decision to apply them based upon their relevance. So, this company should not have upgraded the X server if it didn't find those security holes to be a problem.

---

### Post by FuturePilot on 2008-01-18
Well at least they've blocked access to the update.

---

### Post by kvonb on 2008-01-18
-

---

### Post by -Vampyre- on 2008-01-18
Not that this is solely a ilinux thing. I work for a software developement co and we have a windows update server with a test group to test updates.

---

