---
title: "First Login for Newbie"
date: 2013-01-11
forum: System76 Support
---

### Post by Cliff Bentley on 2013-01-11
A Linux newbie here (as root, or sys-admin at least). I purchased a new Ratel Performance for my first Linux box, it should arrive in a couple of days. Looking forward to getting good at this. I have these questions for when I first get my new Ratel out of the box:
1) I presume that my Ratel will arrive with one user, root, is that correct?
2) Will the userID for root be 0? 
2a) If not, what will the userID for root be?
3) How will I know the first password for root? 
4) Won't I always have to log in as root to add a new user?
5) I intend to create a new user whose privilege is root for my own normal log on. Is that a good approach?
6) Also, I know I'm getting Ubuntu v12.10. But for my information, what version of Linux will it be running on?

Thanks! Looking forward to being part of the Ubuntu community.

---

### Post by MG&amp;TL on 2013-01-11
> 1) I presume that my Ratel will arrive with one user, root, is that correct?

Nope. On other linux distributions, that may be the case. However, Ubuntu comes with a standard user that can 'elevate' temporarily to root via a mechanism called *sudo*. See [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

This is put in place for good reasons, and I believe forum policy goes against enabling full root access.

> 2) Will the userID for root be 0? 

Yup.

> 3) How will I know the first password for root? 

See answer for 1), but I believe System76 machines come with a first-boot script that does setup for you, but normally you'd set this during install.

> 4) Won't I always have to log in as root to add a new user?

See 1), but you'll have to authenticate to *sudo* privileges to create new users, yes.

> 5) I intend to create a new user whose privilege is root for my own normal log on. Is that a good approach?

Nope. Use *sudo* if you need another user with these permissions, but the default account should be fine.

> 6) Also, I know I'm getting Ubuntu v12.10. But for my information, what version of Linux will it be running on?

Linux kernel 3.5, see [https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop]("https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop") for other software stack versions.

> Thanks! Looking forward to being part of the Ubuntu community.

Welcome!

---

### Post by Cliff Bentley on 2013-01-11
Thanks for the help. After that post, I did find/read an informative article on sudo, so that added plenty of context to your answers. The answer to #3 sounds like it's going to be the key. Thanks again.

---

