---
title: "Unix or Linux?"
date: 2010-04-27
forum: The Cafe
---

### Post by nene7 on 2010-04-27
Hi to all,
    I want to know what open source SO are clasified Unix like opensolaris?

---

### Post by aeiah on 2010-04-27
OpenBSD, FreeBSD and their derivatives are probably where you should look

---

### Post by nene7 on 2010-04-27
Why ubuntu is not clasified unix? What things make ubuntu are linux(like-unix)?

---

### Post by Shining Arcanine on 2010-04-27
> **nene7 said:**
> Hi to all,
    I want to know what open source SO are clasified Unix like opensolaris?

UNIX is anything that abides by the Single Unix Specification. Linux is a UNIX kernel that can be combined with various userland utilities to meet the requirements of the Single Unix Specification. It in itself is not necessarily UNIX, but it is close.

Some Linux distributions such as Redhat Enterprise Linux are certified to be Single Unix Specification compliant. I am not sure what is keeping Canonical from doing this with Ubuntu, but the primary factor is most likely cost. Any secondary factors could be resolved by modifying their choice of packages they provide with Ubuntu or changing kernel .config options.

In short, you can consider Ubuntu to be a UNIX OS.

---

### Post by nmccrina on 2010-04-27
ninja'd

---

### Post by kavon89 on 2010-04-27
According to wikipedia, no Linux distros have been certified to meet the [single Unix specification]("http://en.wikipedia.org/wiki/Single_UNIX_Specification"). Most Linux distros like Ubuntu, however, still follow the standard enough to where one can call Linux based OSes Unix-like.

---

### Post by Shining Arcanine on 2010-04-27
> **kavon89 said:**
> According to wikipedia, no Linux distros have been certified to meet the [single Unix specification]("http://en.wikipedia.org/wiki/Single_UNIX_Specification"). Most Linux distros like Ubuntu, however, still follow the standard enough to where one can call Linux based OSes Unix-like.

I thought that RedHat Enterprise Linux was certified. I guess I was wrong.

---

### Post by HermanAB on 2010-04-27
It is mainly a trademark issue.  To use the UNIX trademark, you got to pay a license fee to the Open Group.

So, legally, we are not allowed to say that Linux is a kind of UNIX.  However, we can say that UNIX is a kind of Linux.

---

### Post by nene7 on 2010-04-27
@Shining Arcanine why the cost is one factor?
Does canonial limit ubuntu not register or is that ubuntu bein linux never are goint to be unix because is unix clone?

---

### Post by kaldor on 2010-04-27
Linux is close enough to UNIX to be called a UNIX clone; compare Linux to BSD or Solaris which true UNIX. Not a massive amount of difference.

---

### Post by red_Marvin on 2010-04-27
> **HermanAB said:**
> However, we can say that UNIX is a kind of Linux.

Nope, Linux means that it is using the linux kernel. *BSD etc are running other kernels and are not linux.

---

### Post by nene7 on 2010-05-03
Hi to all i was reading a article,
> [http://www.cyberciti.biz/faq/what-is-the-difference-between-linux-and-unix/](http://www.cyberciti.biz/faq/what-is-the-difference-between-linux-and-unix/)
And i don't know is this what is but to Ubuntu be UNIX is just need to be private?

---

### Post by nicfallenangel on 2010-05-03
> **nene7 said:**
> ... [http://www.cyberciti.biz/faq/what-is-the-difference-between-linux-and-unix/]("http://www.cyberciti.biz/faq/what-is-the-difference-between-linux-and-unix/")...

The main difference between Linux and Unix is quoted from the kernel readme in that article:

> Linux is a Unix clone written from scratch by Linus Torvalds with assistance from a loosely-knit team of hackers across the Net. It aims towards POSIX compliance.

Linux is not Unix because it does not use the Unix kernels. Linux conforms to certain Unix standards of operation: command structure, GUIs, etc. The licensing and closed source conformity do play a part, but the Kernel is the main difference/hindrance in calling a Linux OS Unix(-like).

---

### Post by swoll1980 on 2010-05-03
To make a long story short they could all be UNIX if they want to pony up the dough. The BSDs and Solaris are really truly UNIX, and Linux is a reverse engineered clone.

---

### Post by phrostbyte on 2010-05-03
> **kaldor said:**
> Linux is close enough to UNIX to be called a UNIX clone; compare Linux to BSD or Solaris which true UNIX. Not a massive amount of difference.

BSD is not Unix, it was written from scratch and contains none of the original Unix code in it. Nor does it have the Single Unix Specification certification. So it is not Unix by any definition. Solaris is however, it is certified Unix as well containing actual code from the original Unix operating system.

Linux and BSD are Unix-like OSes, and implement a standard called "POSIX", which is the standard every Unix system is expected to implement. So the distinction in the end of the day between Unix and Unix-like is really pointless.

---

### Post by michaeldt on 2010-05-03
*BSD and *solaris are essentially derivatives of the UNIX which was developed very early on by AT&T and friends, and they have a lot of common code between them and UNIX. 

Linux is written from scratch by Linus. 

That's the difference.

---

### Post by phrostbyte on 2010-05-03
> **michaeldt said:**
> *BSD and *solaris are essentially derivatives of the UNIX which was developed very early on by AT&T and friends, and they have a lot of common code between them and UNIX. 

Linux is written from scratch by Linus. 

That's the difference.

BSD contains no Unix code since the 4.4-Lite release which EVERY *BSD that exists today is derived from! BSD can be not considered Unix any more than Linux is! :o

---

