---
title: "Kernel upgrade - 10.04 LTS 32bit Server"
date: 2011-12-13
forum: Server Platforms
---

### Post by tedvan on 2011-12-13
Hallo Forum,

I read this:
[http://www.ubuntu.com/usn/usn-1256-1/](http://www.ubuntu.com/usn/usn-1256-1/)

how can i upgrade only my kernel package( and headers, and everything which is requred)?
I use LTS Version 10.04 Server 32bit - so I dont want to do a distribution upgrade.

I want to use apt. I didn't find a simple how to to do this task.

Thanks with kind regards
:KS
Tidy

---

### Post by arrrghhh on 2011-12-13
Seems like you can just apt-get install it if you have the 'backports' repo enabled.

Also, 12.04 is just around the corner.  I know, a few months off but still.

---

### Post by tedvan on 2011-12-13
Do I need backports if the required kernel is in the standard repo?

How do I do it without backuports repo?

Thank you wkr
Tidy

---

### Post by tedvan on 2011-12-13
Or is it possible to just download the deb-packages from packages.ubuntu.org?

with kind regards
teedy

---

### Post by arrrghhh on 2011-12-13
> **tedvan said:**
> Or is it possible to just download the deb-packages from packages.ubuntu.org?

with kind regards
teedy

You can certainly do this if you don't want to add backports.

[https://wiki.ubuntu.com/UbuntuBackports](https://wiki.ubuntu.com/UbuntuBackports)

That link isn't so helpful, but this one might be.

[http://ubuntuforums.org/showthread.php?t=45047](http://ubuntuforums.org/showthread.php?t=45047)

---

### Post by tedvan on 2011-12-13
I didn't find a "how to" /tutorial for the upgrade process with apt-get and the default repo.

Do you know one?

Which packages do i need to install?

wkregards
teedy

---

### Post by arrrghhh on 2011-12-13
> **tedvan said:**
> I didn't find a "how to" /tutorial for the upgrade process with apt-get and the default repo.

Do you know one?

Which packages do i need to install?

wkregards
teedy

Read that second link please.

---

### Post by wojox on 2011-12-13
What does this say?
```
uname -r
```

---

### Post by tedvan on 2011-12-13
Do I need to install just the package (from default repo) [B]linux-image-generic-lts-backport-natty?

[/B]Nothing else?
wkr
teedy

---

### Post by tedvan on 2011-12-14
The whole story ist that I am planing an LTS distribution upgrade from 8.04 to 10.04, because I need ext4 on the machine.

But then I read that there are many bugs in 10.04 so I do a second upgrade plan. I want to install the newer kernel after the distupgrade.

I dont know "uname -r" from 10.04 at the moment.

:popcorn:
Thanks with kind regards
teedvan

---

### Post by arrrghhh on 2011-12-14
> **tedvan said:**
> The whole story ist that I am planing an LTS distribution upgrade from 8.04 to 10.04, because I need ext4 on the machine.

But then I read that there are many bugs in 10.04 so I do a second upgrade plan. I want to install the newer kernel after the distupgrade.

I dont know "uname -r" from 10.04 at the moment.

:popcorn:
Thanks with kind regards
teedvan

Dude, there's going to be bugs in any OS.  10.04 is really quite stable for me, I don't think you'll have any problems upgrading to 10.04, then waiting for 12.04 which is just around the corner.

---

