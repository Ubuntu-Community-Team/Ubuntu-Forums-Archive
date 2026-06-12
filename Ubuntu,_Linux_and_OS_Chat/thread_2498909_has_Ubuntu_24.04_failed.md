---
title: "has Ubuntu 24.04 failed?"
date: 2024-07-03
forum: Ubuntu, Linux and OS Chat
---

### Post by alanm8 on 2024-07-03
still almost no major open source officially support Ubuntu 24.04

MongoDB
NodeJS  ( installer by NodeSource )
CUDA

etc



what happened?

---

### Post by TheFu on 2024-07-03
It takes time for enterprise software to support every new release.  By policy, they are probably waiting until 24.04.1 is release.  Some may not even start porting their software until AFTER .1 is released.

Relax.  It is best for enterprises NOT to run the newest software.  Over the decades, most of the clients I've worked with were usually 2-5 yrs behind on any UNIX release. This is normal.  Only software developers who are creating completely new stuff want the newest versions of all the libraries to have access to the newest features, but is that REALLY necessary?

---

### Post by alanm8 on 2024-07-03
it already takes 3 month

not necessary, but inconvenient and a bit annoying?

and i will have one less upgrade task in the future....

thanks for your expertise reply

---

### Post by TheFu on 2024-07-03
> **alanm8 said:**
> it already takes 3 month

not necessary, but inconvenient and a bit annoying?

and i will have one less upgrade task in the future....

thanks for your expertise reply

24.04.1 will be released in August, then give organizations 6 months to move their development through their internal validation, fix, hardening, processes.  Obviously, dev tools and libraries need to be ported first.

BTW, much of the world will deploy their servers into either VMs or containers to keep the OS running on physical hardware separate from the complex SW stack systems.  

In the old days, we'd put 20 different things onto a single servers. Only huge enterprises could afford to dedicated 1 machine = 1 service.  That continued until virtual machines took off around 2000.  Since then, organizations have been able to keep a 1 VM = 1 service and run 10-100 VMs on a single physical server.  With linux containers, that becomes 10-100x denser, so it is common for 100-1000 linux containers to run on a single physical server, each with the specific software stack just for that container.  

In short, the amount of an OS that runs on most containers is extremely small.  These are called application containers - docker is the most popular.  For system containers, like LXC provides, there is an OS, but stripped down OSes are commonly used which don't provide so much OS bloated tools.  These are a little heavier, but until Docker (and similar) application container systems default to running their containers unprivileged, the LXC containers make more sense. This is why Canonical has been on the LXC/LXD path for over a decade.

As an example, my physical servers run Ubuntu 20.04 still, but I have both VMs and containers running with 18.04, 20.04, 22.04 OSes (along with some MS-Windows and Debian) across them.

If you are frustrated with any specific SW stack, complain to that project. Canonical isn't the problem for most of those issues.  Project teams each have their own priorities, so only they can say when or if 24.04.x will be supported.

I have a 24.04 server running in a VM and it has been very solid.  It is a test system, definitely not production.  It doesn't appear that I will ever use a 24.04 desktop due to Canonical dropping support for how I handle storage layouts.  We all have critical stuff that will prevent us from using specific software.  For me, the lack of LVM support in the desktop installers is 100% a show stopper.  OTOH, Ubuntu Server installations do support LVM.

I read yesterday that the new Fedora is finally removing all Python 2.7 dependencies.  Python2 supported ended 1/1/2020 - so it is well beyond time for a leading Linux organization to have finally migrated off Python2 ... er ... 4 yrs too late, actually.  I suppose that's the opposite issue from what you are complaining.  Of course, we'd like all our software to support whatever we have, in a secure manner, forever.  If only pixie dust was magic, then we could get that.

For now, we have to live and work in the real world.  Being frustrated about things we cannot control is a good way to an ulcer. In my late 20s, I used to get really mad about lots of things outside my control. It wasn't doing my health any good, so I decided to stop.

---

### Post by alanm8 on 2024-07-03
your replies were very helpful and gave me another view

thank you again

---

