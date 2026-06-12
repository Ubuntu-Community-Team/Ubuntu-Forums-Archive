---
title: "Feisty: Intermittent &quot;W: Duplicate sources.list entry...&quot;"
date: 2007-10-02
forum: Repositories &amp; Backports
---

### Post by Phrawm48 on 2007-10-02
For Feisty / 7.04, I have an intermittent annoyance rather than a show-stopping problem.  Still, I'd like if possible to understand why the problem occurs and how to prevent it from occurring if possible.

_**THE PROBLEM:**_
Occasionally -- but not always -- I'll receive the following error message after using Synaptic to *Reload* my Feisty system's repositories, then clicking *Mark Upgrades*:

```
W: Duplicate sources.list entry http://us.archive.ubuntu.com feisty/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_feisty_main_binary-i386_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com feisty-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_feisty-security_main_binary-i386_Packages)

```This error only occurs sporadically (i.e. not after every *Reload* / *Mark* sequence), and when it does occur it tends not to be repeatable immediately afterwards; the error is sort of "self clearing" after one occurrence and doesn't happen again for a while.

If I inspect */etc/apt/sources.list*, I can see both of the repositories mentioned in the error message, but I'm not sure which of them -- if any -- I should be commenting out or deleting from *sources.list*.

Any ideas or suggestions?  I'd prefer that my repositories and upgrades ran "clean" 100-percent of the time...

Cheers & thanks,
Ric
SFO

---

### Post by thelocust on 2007-10-03
Is there a # sign before the lines that begin with src for those 2?

---

### Post by aysiu on 2007-10-03
Just get a fresh sources.list.

Try this:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by Phrawm48 on 2007-10-03
Thanks for your responses.

[I]   Is there a # sign before the lines that begin with src for those 2?
[/I]
No.  I've attached my current sources.list as  *COPY-of-intermittently-misbehaving_sources.list.zip *in the hopes it will be helpful.

 *J*[I]ust get a fresh sources.list.
[/I]
I'm certainly willing to do that if I can't readily identify why the problem occurs as it does.  (The intermittent and "self correcting" nature of the problem make me wonder if I'm not seeing something that might eventually make a worthwhile bug report...)

Cheers and thanks again,
Ric
SFO

---

