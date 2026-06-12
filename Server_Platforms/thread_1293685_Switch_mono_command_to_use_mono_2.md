---
title: "Switch mono command to use mono 2?"
date: 2009-10-17
forum: Server Platforms
---

### Post by deakster on 2009-10-17
I already did this process on another server, but I forgot how I did it and can not for the life of me find the instructions again.

I am running an 8.04 ubuntu server, and have all the mono-2.0 packages installed, but the mono command points to the old mono 1.2.6, not 2.0.1.

Can anyone tell me how I get it to use the new mono 2?

---

### Post by directhex on 2009-10-17
> **deakster said:**
> I already did this process on another server, but I forgot how I did it and can not for the life of me find the instructions again.

I am running an 8.04 ubuntu server, and have all the mono-2.0 packages installed, but the mono command points to the old mono 1.2.6, not 2.0.1.

Can anyone tell me how I get it to use the new mono 2?

You're getting confused about something.

Packages with "2.0" in the name refer to the version of the .NET core library they use (there are two versions of .NET - 1.1 and 2.0)

Mono 1.2.6 includes support for both versions of .NET - hence the package *NAMES* contain 2.0, but *VERSIONS* contain 1.2.6

Try [http://directhex.mfgames.com/hardy.html](http://directhex.mfgames.com/hardy.html)

---

