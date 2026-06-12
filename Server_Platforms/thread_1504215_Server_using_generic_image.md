---
title: "Server using generic image"
date: 2010-06-07
forum: Server Platforms
---

### Post by SabreWolfy on 2010-06-07
I've just upgraded my i386 Karmic server to Lucid and I've noticed that the server is using the "generic-pae" image. (I'm not saying this has anything to do with the upgrade -- I only really noticed now). I installed and upgraded from the "Server" CD download.

Why/how is this server using the generic-pae image and not the *server* image? How can I change this?

---

### Post by arrrghhh on 2010-06-07
My server is using 2.6.32-22-generic-pae.  I don't know what to tell you, it's a fresh 10.04 server install - no upgrades at all.

---

### Post by Vegan on 2010-06-07
> **SabreWolfy said:**
> I've just upgraded my i386 Karmic server to Lucid and I've noticed that the server is using the "generic-pae" image. (I'm not saying this has anything to do with the upgrade -- I only really noticed now). I installed and upgraded from the "Server" CD download.

Why/how is this server using the generic-pae image and not the *server* image? How can I change this?

The generic-pae is simply the kerenel, do not worry about it.

I noticed a new kernel was in the updates of late.

---

### Post by FuturePilot on 2010-06-07
They dropped the 32bit -server kernel. It doesn't exist anymore. The generic-pae kernel now takes its place.

---

### Post by SabreWolfy on 2010-06-08
Thanks. Some confusion as the 'server' image is still references [here]("https://help.ubuntu.com/community/ServerFaq#What's the difference between kernel linux-image-server and linux-image-generic? What architecture is linux-image-server? Which one should I use?").

---

### Post by arrrghhh on 2010-06-08
> **FuturePilot said:**
> They dropped the 32bit -server kernel. It doesn't exist anymore. The generic-pae kernel now takes its place.

Another reason to switch over to 64-bit...

---

### Post by SabreWolfy on 2010-06-08
> **arrrghhh said:**
> Another reason to switch over to 64-bit...

There is a special 64-bit server version? I've just upgraded x86 Karmic server to Lucid.

Can I "side"-grade a 32-bit Lucid to a 64-bit Lucid? :)

---

### Post by arrrghhh on 2010-06-08
Nope, gotta do a fresh install.  Sorry if I made it sound easier :P

---

### Post by SabreWolfy on 2010-06-08
> **arrrghhh said:**
> Nope, gotta do a fresh install.  Sorry if I made it sound easier :P

Argh! No real benefit to 64-bit though, as the machine "only" has 2GB of RAM and does not run/host any VMs. Guess it would not really be worth the effort. I told myself that I'd upgrade to 10.04 *LTS* and then leave the server alone for at least two years :)

---

