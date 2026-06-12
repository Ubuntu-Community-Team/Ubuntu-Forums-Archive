---
title: "No joy.."
date: 2013-07-17
forum: Ubuntu Christian Edition
---

### Post by Olsbyn on 2013-07-17
I was looking forward to try out Ubuntu CE, with all software and the flavor I wanted as a christian, but I must say i am greatly disappointed, I don`t even know where to begin..my problem ? Dansguardian !!
Is this distribution geared towards christians or children, my guess is children, the reason I think so is that this program disables you completely from doing any work, I couldn`t even use bible analyzer because dansguardian stops me, I can`t even watch Hillsong on youtube because dansguardian stops me. I have now used at least 10 - 12 hrs trying to tweak it and nothing works. Very disappointing for a distro I really looked forward to using.
For me I would really like to completely disable or remove the dansguardian program, well, not an easy task since it totally disables your browser if you just remove it.

So, if anyone could help me on how to disable this virus i would be very grateful, if not, I see no reason to use or recommend this distribution to anyone, since out of the box it is not functional at all ?

---

### Post by Snowhog on 2013-07-17
Take a look at [Dansguardian Internet Content Filtering]("https://help.ubuntu.com/community/DansGuardian")
> DansGuardian is an award winning Open Source web content filter which currently runs on Linux, FreeBSD, OpenBSD, NetBSD, Mac OS X, HP-UX, and Solaris. It filters the actual content of pages based on many methods including phrase matching, PICS filtering and URL filtering. It does not purely filter based on a banned list of sites like lesser totally commercial filters.

DansGuardian is designed to be completely flexible and allows you to tailor the filtering to your exact needs. _**It can be as draconian or as unobstructive as you want**_. The *_default settings are geared towards what a **primary school** might want_* but DansGuardian puts you in control of what you want to block.

---

### Post by jonathonblake on 2013-08-05
> **Olsbyn said:**
> 
 the reason I think so is that this program disables you completely from doing any work,

It can be annoying to be sent a URL, which DansGuardian blocks.   This is why the end-user has to customize Dansguardian.
Security, and the sub-set of content filtering, is a compromise between ease-of-use, and what to block/restrict/prevent.  

For maximum effectiveness, the initial conditions should be set to block everything, with the end-user making minor adjustments, as required.

> if anyone could help me on how to disable this virus

A would not call a tool that is designed to block undesirable content, a virus. Instructions on how to configure Dansguardian are laid out on the Dansguardian support site.  

> I see no reason to use or recommend this distribution to anyone, since out of the box it is not functional at all ?

A distro that automatically blocks NSFW content, is a distro that most HR people will readily request, if only to further minimise "hostile work environment" related lawsuits.

jonathon

---

### Post by AnnaMary on 2013-09-03
I am really frustrated with dansguardian as well.  I have looked at the link above, and it is too advanced for me to know what to do with the information.  Of course, dansguardian blocks me from the disable info on it's own website as well.  I have ordered regular ubuntu 12.04 and I can't wait until it gets here.  I replaced vista with this ce version, but I've had to pull out my old computer to be able to get anything done.  The ce version should be advertised as geared for children maybe.  I don't know, but I won't make the mistake of trying to use it again.  I will, however, try to add the Bible components to regular ubuntu when it gets here.

---

### Post by jonathonblake on 2013-09-04
> **AnnaMary said:**
>  it is too advanced for me to know what to do with the information.

The instructions on that page include the specific commands, in the specific sequence to carry them out, in order to configure dansguardian to suit your needs and requirements.
It is about as simple as can be, without talking down, or otherwise insulting the reader.

> The CE version should be advertised as geared for children maybe.

One of the biggest criticisms of DansGuardian is that it is **too easy** for children to bypass.

jonathon

---

### Post by david_kt on 2013-09-05
You might try attached file, extract and install it. After that, you could find it in the menu titled "Configure parental control".
First, select autoconfigure/reset Dansguardian and tinyproxy
Second, if you do not like the setting, you could try "Filter setting"

If you think you do not need dansguardian, you could select "Stop Dansguardian". There are many other function you might want to explore, in case you want to let your kids use your computer.

DK

---

