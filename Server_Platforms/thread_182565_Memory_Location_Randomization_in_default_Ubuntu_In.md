---
title: "Memory Location Randomization in default Ubuntu Install"
date: 2006-05-26
forum: Server Platforms
---

### Post by jpoe on 2006-05-26
--EDIT:  Apologies if you read this twice, I originally posted it in the main forum but I think it makes much more sense here.

I was playing with some memory monitoring software on my local machine today and I noticed something peculiar. It seems Ubuntu has a linux patch to randomize the location of environmental variables?

I quickly did a few google searches and found that a kernel patch called PaX does something like this, but I haven't been able to find any information about the default Ubuntu Linux install. Does anyone know if this is indeed the case? I compared it to a few other distros and none of them seem to be employing the memory randomization feature (for example, this doesn't happen on Debian Sarge, although it does on Fedora Core 5).

I think this is interesting, and I was wondering if anyone knew about this; or where I could read up on Ubuntu's implementation in more detail? Thanks in advance.

---

