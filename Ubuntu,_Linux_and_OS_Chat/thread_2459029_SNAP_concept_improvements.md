---
title: "SNAP concept improvements?"
date: 2021-03-09
forum: Ubuntu, Linux and OS Chat
---

### Post by hdwkl on 2021-03-09
Hello, I was thinking a bit on SNAP, and perhaps how it could be changed to be more efficient.

So Ubuntu is trying to solve the problem that the software version of an application is currently more or less tied to the Linux distribution version you are running. This is indeed a huge inflexibility. And it especially hinders a Desktop OS a lot. The Idea of snap, is a good idea and also kinda solves that problem. But the execution is i.m.o. kinda full of disadvantages. The biggest disadvantage being the size of each snap package, and the way it is distributed to the user.

_**Whatif:**_

Snap would separate the requirements of software snaps into 1 (or several)** base-snap **

 I.o.w. one sand-boxed snap package that would consist of the all the different lib versions, core utility versions, etc (let's call it **base-snap** ), that software snap packages could use. The actual application snaps would not have to be sand-boxed, and would rely on that **base-snap**. 

Now there would be overlapping versions within that **base-snap **of for example the same libs with different versions . So there should be some kind of interfacing needed between the **base-snap** and the **application snaps**, where the application snap chooses the right environment within that **base-snap** that it requires[B].

[/B]This would solve the issue with the huge sizes per application snap. And it would also save a lot of bandwidth, since the application-snap would be much lighter. 

It would obviously require a change to the core of snap itself, and how snap makers would have to create their snaps. But on the long term I would think it's worth it.

Any thoughts on this?

---

### Post by CatKiller on 2021-03-09
> **hdwkl said:**
> Snap would separate the requirements of software snaps into 1 (or several)** base-snap **

[https://snapcraft.io/core](https://snapcraft.io/core)

---

### Post by hdwkl on 2021-03-09
> **CatKiller said:**
> [https://snapcraft.io/core](https://snapcraft.io/core)

Alright, so basically this is already the case. I'm sorry, I am not using Ubuntu at the moment, but when I tried it a while ago I saw the huge differences between a deb package and a snap package. I think I better run Ubuntu myself, and inform myself better, before spewing ideas ;) Thanks for the reply.

---

### Post by Swan_DB on 2021-03-09
> **hdwkl said:**
>  **and inform myself better, before spewing ideas**
Just wanted to say, you don't need to inform yourself better, at least in this case; **the sub forum you posted in is for chat/discussion**.  I found your post helpful :guitar:

---

### Post by hdwkl on 2021-03-09
> **Swan_DB said:**
> Just wanted to say, you don't need to inform yourself better, at least in this case; **the sub forum you posted in is for chat/discussion**.  I found your post helpful :guitar:

Thanks. Yes but at first sight it seemed like I posted in a car forum about a bright new idea where I suggested a new concept where cars could have batteries, and drive electrical ..... if you know what I mean. 

Anyway, I was planning to install Ubuntu anyway on my desktop that is currently running slackware. So i can inform myself a bit better :P

---

### Post by grahammechanical on 2021-03-10
Canonical developers are still developing the snap concept themselves. It is a work in progress. It started out as Click packaging for applications on a Ubuntu Unity 8 smartphone. There are several ideas in the concept. 

A method for auditing the source code that required less human intervention and so speeded up the release of applications and also their upgrades. Whilst providing applications that could be trusted as secure. A side affect would be that Community developers could more easily get their applications into the Snap store.

Furthermore, it would involve a method of sandboxing applications so that they were limited in the areas of the operating system they had access to. The idea is that applications such as games that did not need to access system files should not allowed to access those files. The same would apply to an application trying to access the internet when it did not need that access.

I think that the Canonical developers were more concerned with system security and reducing developer time spent auditing source code than avoiding applications getting broken by a new version of Ubuntu. After all, it is the responsibility of the application developer to make sure his code works under the operating system the application will be installed on and not the responsibility of the operating system developers to make sure someone else's code works on the OS.

As I see it the focus of Snap development is directed not towards the desktop but towards the Internet Of Things. Ubuntu Core is actually a Snap Operating System. I do not think it will run an application if it is not Snap packaged.

[https://ubuntu.com/core](https://ubuntu.com/core)

And as stated above, we like a good discussion on this forum. Provided, of course, that we avoid religion and politics.

Regards

---

### Post by grahammechanical on 2021-03-18
@ danielpe

I am glad that you agree with me. May be you do not agree with me. You do not say either way. Even so, a good discussion is welcome.

Regards

---

