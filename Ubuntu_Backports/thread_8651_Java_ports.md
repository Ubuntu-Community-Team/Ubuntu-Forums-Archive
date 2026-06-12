---
title: "Java ports"
date: 2004-12-19
forum: Ubuntu Backports
---

### Post by cpinto on 2004-12-19
Hello,
i'm slowly porting/creating some Java packages for Ubuntu. At the moment I've already ported the java-package Debian package and i'm going to create an automated installer. 
Because I'm thinking of creating packages for the Eclipse IDE (this will not have much in common with the current debian package) and as much plugins as I can, as well for common libraries, I was wondering if you'd be interested in hosting the necessary repository for these packages.

Cheers,
Celso

---

### Post by jdong on 2004-12-19
What kind of license are we talking about?

---

### Post by cpinto on 2004-12-20
What do you mean by license? If packages must have a license then, those that don't derive from an existing Debian package, will be GPL.
Is this what you mean?

---

### Post by jdong on 2004-12-20
no,

Are you packaging open-source software, like Blackdown Java, or sub-legally redistributing Sun Java?

---

### Post by cpinto on 2004-12-20
basically i'm trying to create a debconf script that has SUN's JDK/JRE download URL's hardcoded. When the user selects one of those to download, the debconf then downloads the corresponding package from SUN, displays the license agreement and uses the java-package converter to get a .deb package that is installed on the user's system.

Since I'm not actually redistributing SUN's binaries I'm hoping not to run into any troubles.

If this seems ok, i'm trying to learn my way with debconf so that maybe during the next couple of weeks I may have something working for SUN's binary packages.

---

### Post by jdong on 2004-12-20
That sounds good. I'll definitely consider it for inclusion in Warty Extras.

---

### Post by randy on 2004-12-22
Has anyone looked into how Slackware has packaged Sun's jre/jdk with there distribution?

---

### Post by cpinto on 2004-12-22
Does slackware distribute SUN's binaries? I don't think they're allowed to do that, but I'll try and check with a guy I know from the portuguese SUN office.

---

### Post by randy on 2004-12-22
Here's the link from Slackware's package browser. [http://www.slackware.com/pb/showdesc.php?q=10.0/j2sdk-1_4_2_04-i586-3](http://www.slackware.com/pb/showdesc.php?q=10.0/j2sdk-1_4_2_04-i586-3) .

---

### Post by randy on 2004-12-22
I'm pretty sure use in Ubuntu Backports would fall under this portion of the license.

B. License to Distribute Software. Subject to the terms and
conditions of this Agreement and restrictions and exceptions set
forth in the Software README file, including, but not limited to
the Java Technology Restrictions of these Supplemental Terms, Sun
grants you a non-exclusive, non-transferable, limited license without
fees to reproduce and distribute the Software, provided that (i) you
distribute the Software complete and unmodified and only bundled as
part of, and for the sole purpose of running, your Programs, (ii) the
Programs add significant and primary functionality to the Software,
(iii) you do not distribute additional software intended to replace
any component(s) of the Software, (iv) you do not remove or alter any
proprietary legends or notices contained in the Software, (v) you only
distribute the Software subject to a license agreement that protects
Sun's interests consistent with the terms contained in this Agreement,
and (vi) you agree to defend and indemnify Sun and its licensors from
and against any damages, costs, liabilities, settlement amounts and/or
expenses (including attorneys' fees) incurred in connection with any
claim, lawsuit or action by any third party that arises or results
from the use or distribution of any and all Programs and/or Software.

---

### Post by cpinto on 2004-12-22
Ubuntu Backports will fail on:
iii) if the project ever decides to backport kaffe, gcj and the GNU Classpath.

I personally cannot agree with:
vi) because I cannot indemnify SUN (I don't think Ubuntu Backports will do that as well).

Even so, I can't help but wonder how Slackware and Blackdown deal with these licence requirements.

Anyone with law practice background cares to share his opinion on this?

PS: if I could go ahead with this, I think I'd manage to have java packages in no time.

---

### Post by randy on 2004-12-22
In response to iii.
  When these solutions are at a comparable level you could remove sun's jdk/jre and begin using them.  

In reality when would you need to indemnify SUN?

And I'm pretty sure Slackware doesn't distribute Blackdown if thats what your referring to by dealing with these licence requirements.

(Sorry if i sound a bit harsh right now)

---

### Post by cpinto on 2004-12-22
Oh no, I mean, Blackdown AFAIK also distributes SUN's JVM. These are the only two products I'm aware of, that distribute SUN's JVM.

I suppose I can state that SUN's JVM is needed to run the Eclipse IDE. I wonder if that would stick.

**[UPDATE]** I went through Blackdown's FAQ and I reckon it's possible to distribute a custom package of SUN's binaries. This looks like good news :) I'm going to try and put out a package in the next few days, although it'll be a temporary repository until it's possible to put the package in the backports repository.

---

### Post by randy on 2004-12-22
Would it be possible to do some sort of virtual package so users could select there own jdk/jre?

---

### Post by 3dlex8026 on 2007-05-15
> **randy said:**
> Would it be possible to do some sort of virtual package so users could select there own jdk/jre?


[Girls chemistry Google Equity Line Credit blood pressure](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/index.php)

---

