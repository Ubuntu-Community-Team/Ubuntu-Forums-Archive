---
title: "Is it true that BSD is more secure than Linux ? Looking for an unbiased opinion"
date: 2021-04-20
forum: Ubuntu, Linux and OS Chat
---

### Post by linuxyogi on 2021-04-20
I have read discussions on the web about this topic. Some people agree while others don't.

What is your opinion about this ?

There are 2 BSD OSs which have their primary focus on security namely [HardenedBSD]("https://hardenedbsd.org/content/about") & [OpenBSD]("https://www.openbsd.org/").

So in your  (unbiased) opinion are these 2 really more secure than Linux ?

 DuckHook & TheFU I am eager to know what you guys have to say on this topic.

---

### Post by scorp123 on 2021-04-20
> **linuxyogi said:**
>  I have read discussions on the web about this topic.
So much for *"reliable source"* :lolflag:

> **linuxyogi said:**
>   Some people agree while others don't. 
Welcome to the Internet where people can argue all day long about all kinds of topics and never reach an agreement ... :)

> **linuxyogi said:**
>  What is your opinion about this ? 
Pretty much _any_ OS can be made to be (reasonably) "secure" or can become very insecure, depending on who did the installation, what their level of knowledge (or lack thereof) is, what they use that OS for, and what they do with it, and how they do it.

> **linuxyogi said:**
>  There are 2 BSD OSs which have their primary focus on security namely [HardenedBSD]("https://hardenedbsd.org/content/about") & [OpenBSD]("https://www.openbsd.org/"). 
Security-centric Linux distributions exist too.

> **linuxyogi said:**
>  So in your (unbiased) opinion are these 2 really more secure than Linux ? 

Please define "Linux" ??  I feel you are comparing apples and oranges here. I feel this comparison is very flawed. And if by "Linux" you mean Ubuntu Linux: Comparing e.g. OpenBSD with e.g. Ubuntu Linux is "apples and oranges" again since the two cater to very different audiences who intend to do different things with it. A comparison between FreeBSD and Ubuntu Linux would be more appropriate. And something like HardenedBSD should probably best be compared with something like e.g. Qubes OS.

I feel the only fair unbiased answer is: **"It depends."**

---

### Post by grahammechanical on 2021-04-21
This is interesting. From the HardendBSD web site

> Our primary goal is to provide a clean-room reimplementation of the  publicly-documented parts of the grsecurity patchset for Linux.

When you compare it with this

> On April 26, the grsecurity project [announced]("https://grsecurity.net/passing_the_baton.php") that it was withdrawing public access to its kernel-hardening patch sets; henceforth, they will be available only to paying customers of Open Source Security, Inc., the company behind this work.

[https://lwn.net/Articles/721848/](https://lwn.net/Articles/721848/)

And with this

> Don't bother with grsecurity. Their approach has always been "we don't care if we break anything, we'll just claim it's because we're extra secure".
The thing is a joke, and they are clowns. When they started talking about people taking advantage of them, I stopped trying to be polite about their ********.Their patches are pure garbage.

Linus 

[https://www.spinics.net/lists/kernel/msg2540934.html](https://www.spinics.net/lists/kernel/msg2540934.html)

Debian used to make grsecurity patches available to Debian users but when grsecurity patches were no longer publicly available the Debian developers decided not to make them available in Debian any more.

[https://wiki.debian.org/grsecurity](https://wiki.debian.org/grsecurity)

OpenBSD takes a different approach;

> To ensure that novice users of OpenBSD do not need to become security experts overnight (a viewpoint which other vendors seem to have), we ship the operating system in a Secure by Default mode.  All non-essential services are disabled.  As the user/administrator becomes more familiar with the system, he will discover that he has to enable daemons and other parts of the system.  During the process of learning how to enable a new service, the novice is more likely to learn of security considerations.

[https://www.openbsd.org/security.html](https://www.openbsd.org/security.html)

I would contend that this approach is contrary to the principle that Ubuntu is for Humans. It is all a matter of choice. Which in turn is based upon need. Although for many people their so-called needs are determined by commercial organisations and advertising.

Regards

---

