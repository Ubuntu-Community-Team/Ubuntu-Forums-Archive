---
title: "OpenSSH Version in Hardy Repo out of Date. What do I do?"
date: 2008-09-27
forum: Security
---

### Post by SSVegito888 on 2008-09-27
I am planning on installing OpenSSH on Ubuntu Hardy, but the OpenSSH Version is way out of date.



The current release according to openssh.com is OpenSSH 5.1/5.1p1 released July 21, 2008.

The Hardy repo version is 4.7p1?



What should I do?



Also, is it just me, or is the Hardy repo way behind in application updates?



Heck, even VLC Media Player is like 3 or 4 versions behind.


Why is the repo so far behind?


Thanks,

SSVegito888

---

### Post by Bakon Jarser on 2008-09-27
Ubuntu goes for stability which means once the version of software is picked they stick it.  If you want your programs to stay up to date then look into enabling the backports.

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

---

### Post by SSVegito888 on 2008-09-27
Is it generally safe to use backports?


Thanks,

SSVegito888

---

### Post by Bakon Jarser on 2008-09-27
> **SSVegito888 said:**
> Is it generally safe to use backports?


Thanks,

SSVegito888

The link provides that information.  Anyways there is no openssh backport.  Does the new version offer some feature you need?  If not then I'd stick with the version in the repos.  Ubuntu may not upgrade to newer versions of software but they do push out security updates.  Your other option is to either find a .deb of the new version or compile it from source.

---

### Post by SSVegito888 on 2008-09-27
I thought about installing from source.


The only thing is when I need to upgrade to the next future version, how will I do it?


I need sort of openssh repo don't I.


Do you know if openssh.com has an official repo?


I am still kind of new to Linux.


Thanks,

SSVegito888

---

### Post by kevdog on 2008-09-27
Just compile it from source!  Its easy to do.  That would be my suggestion.  The instructions are on the OpenSSH website.

---

### Post by cariboo on 2008-09-28
Ubuntu version numbers don't necessarily correspond to upstream version numbers. Ubuntu is based on debian unstable. I know that when the last ssh vulnerability was posted, it was fixed within a couple of hours of the report.

Jim

---

### Post by SSVegito888 on 2008-09-30
OK thanks.


Just for curiosity's sake how do you find the correct version numbers for software in Ubuntu's repos?


Thanks Again,

SSVegito888

---

### Post by sjwk on 2008-10-01
> **Bakon Jarser said:**
> Does the new version offer some feature you need?  If not then I'd stick with the version in the repos.
I can't speak for the OP, but in my case yes.  4.7p1 has a (non-security) bug where pam_close_session isn't called.  It's apparently fixed in 4.8 and above (patch supposedly works on 4.7p1), definitely in 5.1.  Under normal use it's not a problem but I'm trying to do some home directory automounting via PAM and coupled with another issue (where Ubuntu apparently gives up root privileges after opening the session and then no longer has them when closing) means that the filesystem doesn't get umounted on logout and the count not decreased so it doesn't then remount next time.

I could compile a later version or apply a patch from source, but on a production server don't want to complicate dependancies (where other things might think openssh isn't installed because it's not been installed as a package) or complicate security fixes by having to remember to check for patches, download, reapply other patches, compile...  Similarly I'd rather stick with Hardy since it's a LTS edition.

Steve.

---

### Post by cariboo on 2008-10-01
to find the version of ssh you are using in a terminal type:

```
ssh -V
```

This is the output on my laptop running LinuxMint Elyssa Lite

```
 ssh -V
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007

```

Jim

---

### Post by SSVegito888 on 2008-10-08
Thanks for the command and other information about the bug in openssh.




Thanks Again,

SSVegito888

---

