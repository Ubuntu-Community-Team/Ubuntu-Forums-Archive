---
title: "How important are kernel updates for home desktop users?"
date: 2009-09-25
forum: Security
---

### Post by sweetleaf on 2009-09-25
The other day I noticed that, while my x86 Jaunty computer has been updated from 2.6.28-11 to 2.6.28-15, my PPC Jaunty computer is still running its original kernel version from the April release. The PPC machine *is* receiving repository updates for most other packages, so it seems to be a problem with Ubuntu kernel maintenance for PPC, not with my particular connection or setup. (For more on this, see my [post]("http://ubuntuforums.org/showthread.php?p=8008348") in the Apple Users forum.) Treating this unusual situation as a given, my question for the security forum is about just how important those missing kernel patches are.

I know that kernel updates often include security fixes. But I don't know what it takes to exploit vulnerabilities in an unpatched kernel. Given that my machine has only two users, and that the only server it's running is sshd (obfuscated by various precautionary settings), and that I AM receiving updates for packages like firefox, should I be concerned about running an unpatched kernel?

If I was running a server, I'd be inclined to move to one of the distributions that does seem to offer kernel updates for PPC, like Debian or Fedora. But after investing some time to get this machine up and running, I'd prefer to stick with Ubuntu for a while.

I'd appreciate any thoughts you might have. Thanks!

---

### Post by scorp123 on 2009-09-26
> **sweetleaf said:**
>  If I was running a server, I'd be inclined to move to one of the distributions that does seem to offer kernel updates for PPC, like Debian or Fedora. But after investing some time to get this machine up and running, I'd prefer to stick with Ubuntu for a while. Most of the security bugs recently involved local exploits, e.g. a local user (= someone who already has a login to the box anyway) could get "root" priviledges ... But I am not really sure if only Intel x86 was affected by those bugs or not. Anyway: If you are the only user on that machine and if you have e.g. a firewall/router between that system and the rest of the world ... then I think you have not much to worry about.

Yes, a server that's exposed to the Internet where thousands of users walk in and walk out day and night is a different story ..... but a desktop system at home where only you have access? It's not optimal ... but I see no need to become paranoid either.

---

### Post by falconindy on 2009-09-26
Kernel updates typically correct bugs, resulting in minor improvements in performance and stability. An example of this is the 2.6.28 kernel making ext4 stable enough for every day use after being introduced in kernel 2.6.19.

Is it worth upgrading? Probably. Is it unheard of that new kernels create new problems? Nope.

---

### Post by scorp123 on 2009-09-26
> **falconindy said:**
>  Is it worth upgrading? That wasn't the question. If you read again: he has a PPC platform, not x86. So for some odd reasons his PPC computer did not receive any kernel updates whereas the rest of us has got them. I'd say his assumption is correct -- nobody has cared to make new kernel packages for PPC until now. Maybe they will be there one day. Maybe not.

Upgrading the kernel himself is certainly possible ... but then again this might break things.

So is it worth the hassle? In my opinion: No. If that PPC machine is just a desktop where only he has access anyway then the risks are rather small, even though a few patches might now be missing from his 2.6.28-11 kernel (my Intel and AMD64 boxes are at 2.6.28-15 ... so I'd assume that this is the kernel Jaunty is currently at?)

---

### Post by falconindy on 2009-09-26
> **scorp123 said:**
> That wasn't the question. If you read again: he has a PPC platform, not x86. So for some odd reasons his PPC computer did not receive any kernel updates whereas the rest of us has got them. I'd say his assumption is correct -- nobody has cared to make new kernel packages for PPC until now. Maybe they will be there one day. Maybe not.

Upgrading the kernel himself is certainly possible ... but then again this might break things.

So is it worth the hassle? In my opinion: No. If that PPC machine is just a desktop where only he has access anyway then the risks are rather small, even though a few patches might now be missing from his 2.6.28-11 kernel (my Intel and AMD64 boxes are at 2.6.28-15 ... so I'd assume that this is the kernel Jaunty is currently at?)
To-may-to to-mah-to? If something is important, then I consider it to be worthwhile. I specifically qualified my statement and mentioned that there **are** pitfalls associated with upgrading your kernel simply because I don't consider the converse to be necessarily true: if something is worthwhile, it's not necessarily important.

---

### Post by cgroza on 2009-09-26
i upgrade kernel every time..better performance

---

### Post by scorp123 on 2009-09-26
> **cgroza said:**
> i upgrade kernel every time..better performance On PPC too?

---

### Post by cariboo on 2009-09-26
I have a G4 server, the kernel was updated in July:

```
uname -a
Linux horsefly 2.6.24-24-powerpc #1 Sat Jul 25 00:25:39 UTC 2009 ppc GNU/Linux

```

I wasn't sure if I rebooted since the upgrade, but I guess I have.

---

### Post by sweetleaf on 2009-09-26
Thanks for your input, everyone. 

Just to make sure we're on the same page, let me clarify that I'm not proposing to upgrade to a newer kernel [version]("http://en.wikipedia.org/wiki/Linux_kernel#Versions") (going from 2.6.28 to 2.6.31, for example). Instead, what I'm concerned about is receiving security and bug patches for the version of the kernel that I already have (going from 2.6.28.11 to 2.6.28.15, for example).

Since I'm running a desktop system behind a router, it sounds like running an unpatched kernel shouldn't be too much of a security risk. Thanks for helping to set my mind at ease!

---

### Post by cariboo on 2009-09-27
The big problem is that Canonical doesn't support the ppc architecture any more, so we have to rely on volunteers to update the kernel.

---

### Post by sweetleaf on 2009-09-28
> **cariboo907 said:**
> I have a G4 server, the kernel was updated in July:

```
uname -a
Linux horsefly 2.6.24-24-powerpc #1 Sat Jul 25 00:25:39 UTC 2009 ppc GNU/Linux

```

Your kernel version is 2.6.24... I think that means you're running Hardy (8.04), right? It [looks]("http://www.ubuntu.com/usn/usn-819-1") like Canonical is still releasing PPC kernel updates for 6.06 (2.6.15) and 8.04 (2.6.24)--but not for Jaunty (2.6.28). 

(I've also started a more specific (but long-winded) [thread]("http://ubuntuforums.org/showthread.php?p=8008348") about PPC kernel updates in the Apple Users forum.)

---

### Post by cariboo on 2009-09-28
You're right, I am running hardy, I tried installing Jaunty, and got a cdrom driver error. According to the ppc download page, the ppc architecture is no longer support by Canaonical.

See this [article]("http://www.macnn.com/articles/07/02/15/ubuntu.axes.ppc.support/").

---

### Post by sweetleaf on 2009-09-29
Thank you, cariboo907. I feel that we're wandering off-topic from the original, general question, "How important are kernel updates for home desktop users?" I'd be curious about what your comments might be on my thread in the Apple Users forum, "No kernel updates for Jaunty PPC?," which includes more specific discussion about PPC support from Canonical and from the community. 

[http://ubuntuforums.org/showthread.php?p=8008348]("http://ubuntuforums.org/showthread.php?p=8008348")

Cheers!

---

### Post by Coder543 on 2009-09-29
Look, kernel updates improve most aspects of an operating system; from security, to usability. However, for a PPC machine the security risks are probably nonexistant or minimal considering how few people have spent time trying to exploit the PPC version of Linux. This indicates to me that it is relatively safe, even without getting kernel updates. However, on an x86 machine it is very wise to keep your kernel up to date. Just my take on the situation...

---

### Post by cariboo on 2009-09-29
In a given version, you will only get kernel security updates. So depending on how worried you are about security, it is up to you whether you want to install an updated kernel or not.

---

