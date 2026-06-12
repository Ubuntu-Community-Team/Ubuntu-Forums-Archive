---
title: "GnuPG Security Problem?"
date: 2007-01-10
forum: Server Platforms
---

### Post by DnasTheGreat on 2007-01-10
Ermm... I hate to be the hey-look-you-guys-are-behind guy, but....

[http://lists.gnupg.org/pipermail/gnupg-announce/2006q4/000246.html](http://lists.gnupg.org/pipermail/gnupg-announce/2006q4/000246.html)
> Affected versions: All versions of GnuPG   < 1.4.6 

```
$ gpg --version
gpg (GnuPG) 1.4.3
```

> edgy (utils): GNU privacy guard - a free PGP replacement
1.4.3-2ubuntu3.2: amd64 i386 powerpc 

And... err.... GnuPG... kinda... bad... to... have.... security... holes...

[SIZE="1"]My apologies if I'm supposed to report this elsewhere... I'm rather new to Ubuntu...[/SIZE]

---

### Post by spliner on 2007-10-16
Don't feel bad, so far I've found a bunch of security holes in ubuntu which there are no clear instructions for fixing.  gnupg is one of them.  I'm hoping that it'll be updated in 7.10 but kind of bad to have a supported version (7.04) with holes like that.  I recently installed xubuntu 7.04 on a lower end system to set it up for a Nessus scanner, but securing it has been a terrible hassle, and it still isn't secure.

So far the only suggestions I have gotten have been "switch to debian".

---

### Post by ruibernardo on 2007-10-16
From [http://lists.gnupg.org/pipermail/gnupg-announce/2006q4/000246.html](http://lists.gnupg.org/pipermail/gnupg-announce/2006q4/000246.html):

...
[I]Wed **Dec  6** 16:55:52 CET 2006
...[/I]

From [http://changelogs.ubuntu.com/changelogs/pool/main/g/gnupg/gnupg_1.4.3-2ubuntu3.3/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/g/gnupg/gnupg_1.4.3-2ubuntu3.3/changelog)

```
gnupg (1.4.3-2ubuntu3.2) **edgy**-security; urgency=low

  * SECURITY UPDATE: unwound stack data use, leading to arbitrary code
    execution.
  * Add debian/patches/29_dxf_context_stack.dpatch: upstream patch, use heap
    for allocation instead.
  * References
    [http://lists.gnupg.org/pipermail/gnupg-announce/2006q4/000491.html](http://lists.gnupg.org/pipermail/gnupg-announce/2006q4/000491.html)
    CVE-2006-6235

 -- Kees Cook <kees@ubuntu.com>  Wed,  **6 Dec 2006** 11:56:02 -0800 
```So, this post was misinformation when it was first posted (Jan 2007)...

If you understand something about Debian, you should know that most of the time, packages aren't always the latest versions available, but the more stable ones plus security patches, at least the ones that are maintained by Ubuntu official repositories (main, restricted and security), which was the case here.

---

### Post by /etc/init.d/ on 2007-10-17
Debian tends to just patch the source without incrementing the version number.  It creates this kind of confusion in that you don't actually know whether you're running security-patched software by looking at its version number, you need to check the Debian changelog.

---

