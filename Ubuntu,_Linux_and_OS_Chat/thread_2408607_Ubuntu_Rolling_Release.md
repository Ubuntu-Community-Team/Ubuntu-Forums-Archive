---
title: "Ubuntu Rolling Release"
date: 2018-12-20
forum: Ubuntu, Linux and OS Chat
---

### Post by foobuntu2 on 2018-12-20
Hi Ubuntu-users,

I read through an older RR thread from 2010 and came to the point that we could discuss this again since something has changed since then. I know the drawbacks of RR (stability). The drawback of releases is, on the other hand, that you will have to wait until the new release is available. Since Ubuntu releases every 6 months this could be seen as solved but then another issue arises: Mint recommends not to upgrade your distro but to install it from scratch (without /home if you mind) to avoid conflicts with remaining old system files.

Well, a full install every six months? Hmm ... well ... it's gonna work, ok but ... no.

I recommend dividing the software in the repos into several repos. One repo for software that won't harm your system at all in case you upgrade it, such as Firefox, LibreOffice and stuff. And another repo that is in charge for my particular distro version keeping all operating system relevant files such as the kernel itself, root binaries, configs asf.

This way all distro versions could make use of the uncritical "app repo" getting latest versions of software over years. The "os repo" will be version-dependent to guarantee stability for a long time. So this model is neither RR nor release based but a hybrid of both. It's layered. The os layer is consistent and stable while the app layer is fresh and stable as well since apps won't brake the system.

(I'm not talking about PPA. It's a different concept.)

So what do you think of it? Layered-Hybrid-RR Ubuntu?

Cheers.

---

### Post by pauljw on 2018-12-20
Sounds great, let us know when you have all those repos completed and tested.

---

### Post by santosh83 on 2018-12-21
This is how KDE Neon works if I'm not wrong. The KDE packages are from a repo they maintain and that keeps rolling and "fresh" while the underlying system stays frozen on an Ubuntu LTS base.

Also Manjaro has the choice to opt to lock the kernel so its not updated I believe.

In general it's pretty difficult to get both stability and be a rolling release, especially with the traditional Linux distribution model where all packages are tightly coupled to each other.

---

