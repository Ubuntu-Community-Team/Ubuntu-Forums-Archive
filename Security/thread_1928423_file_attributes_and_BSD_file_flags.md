---
title: "file attributes and BSD file flags"
date: 2012-02-20
forum: Security
---

### Post by fluca1978 on 2012-02-20
Hi all,
with regard to the file attributes (those that can be changed using the chattr command) I'd like to understand what is the difference with BSD file flags (those that can be changed with the chflags command). While the two are very similar, it seems to me that Linux is missing a kernel secure level feature. Am I wrong?

---

### Post by bab1 on 2012-02-21
> **fluca1978 said:**
> Hi all,
with regard to the file attributes (those that can be changed using the chattr command) I'd like to understand what is the difference with BSD file flags (those that can be changed with the chflags command). While the two are very similar, it seems to me that Linux is missing a kernel secure level feature. Am I wrong?

Yes you're wrong.  ;-)

For linux kernels this is *chattr*.  Wikipedia says [**_[COLOR="Blue"]this[/COLOR]_**]("http://en.wikipedia.org/wiki/Chattr").

---

### Post by fluca1978 on 2012-06-07
Uhm...I know that the *chattr* command can do almost the same as *chflags* but the user manual of the latter states that:

> Note that the ability to change certain flags is dependent on the current kernel securelevel setting. 

while I don't find the same on the Linux side. So the meaning of the flag is almost the same, but the behavior of the flags in Linux do not depends on the kernel status.

---

