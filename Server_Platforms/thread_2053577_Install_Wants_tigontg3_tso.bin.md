---
title: "Install Wants tigon/tg3_tso.bin"
date: 2012-09-05
forum: Server Platforms
---

### Post by JSeymour on 2012-09-05
Hello,

Trying to install 12.04.1 LTS Server on a Dell PowerEdge 1750.  Installation is stopping with wanting tigon/tg3_tso.bin on USB or floppy.  Problem is: I've no clue where to find this and no clue was to what format (i.e.: file/path/directory structure) the installer is going to expect to find it in.

Can somebody lend me a hand?

Why have I never encountered this before, with either 8.04 or 10.04 on the same hardware, or 9.04 or 10.04 on a Dell PE 1600SC?

Thanks,
Jim

---

### Post by cortman on 2012-09-05
> **JSeymour said:**
> Hello,

Trying to install 12.04.1 LTS Server on a Dell PowerEdge 1750.  Installation is stopping with wanting tigon/tg3_tso.bin on USB or floppy.  Problem is: I've no clue where to find this and no clue was to what format (i.e.: file/path/directory structure) the installer is going to expect to find it in.

Can somebody lend me a hand?

Why have I never encountered this before, with either 8.04 or 10.04 on the same hardware, or 9.04 or 10.04 on a Dell PE 1600SC?

Thanks,
Jim

Since there doesn't seem to be a lot else online about this, I'm guessing it's either bad installation media or else something related to [this bug]("https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1021747"), which appears to be fixed for quantal.
I'd first check the md5sum of your ISO.

---

### Post by JSeymour on 2012-09-06
> **cortman said:**
> Since there doesn't seem to be a lot else online about this, I'm guessing it's either bad installation media or else something related to [this bug]("https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1021747"), which appears to be fixed for quantal.
I'd first check the md5sum of your ISO.
Thanks for the pointer.

I used the script written by "didi," on [this page]("http://forums.debian.net/viewtopic.php?f=10&t=36571") to check the CD.  It was good, so I proceeded with the install--ignoring the message.

Other than complaining about not being able to install MySQL, which it obviously installed, because I was asked for the "root" password for the server, then leaving me with an unusable console, which I'm now trying to figure out how to work around, the install... er... installed.

I guess.

Jim

---

