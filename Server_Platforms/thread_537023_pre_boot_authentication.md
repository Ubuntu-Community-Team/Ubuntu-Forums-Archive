---
title: "pre boot authentication"
date: 2007-08-28
forum: Server Platforms
---

### Post by InGunsWeTrust on 2007-08-28
I was wondering if there was any way with Ubuntu to use pre-boot authentication. I know CompuSec offers a package to do this but it is only for RH and SUSE. Full disk encryption is a plus but not a must-have.

---

### Post by kidders on 2007-08-29
Hi there,

Disk encryption *is* a must-have, really. I'm not sure there's any other way of preventing people from using your system without authenticating. Thankfully, there's plenty of documentation available on the subject, so you shouldn't have much trouble. Often (as I'm sure you'll notice), people opt for solutions that involve authenticating yourself with a piece of hardware (eg a USB flash disk), rather than a password.

---

### Post by InGunsWeTrust on 2007-08-30
You are missing the point. I am having the theoretical situation that someone steals my laptop let's say if I go get a drink of water and leave it in a classroom and I come back and it's gone. Obviously I'd have that kind of USB authentication connected already.

---

### Post by kidders on 2007-08-30
In that case, encryption is *definitely* the way to go.

> **InGunsWeTrust said:**
> Obviously I'd have that kind of USB authentication connected already.Why? You would presumably have long since removed it & put it in your pocket. In any case, if you'd prefer password-based authentication, do that. The main advantage in using external devices to authenticate with is that you can have pretty arbitrary keyphrase complexity, but if you don't need that level of protection, you don't have to use it.

---

