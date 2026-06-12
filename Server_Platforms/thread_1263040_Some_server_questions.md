---
title: "Some server questions"
date: 2009-09-10
forum: Server Platforms
---

### Post by whaase on 2009-09-10
I have a couple questions

I've been reading around that upgrade a 8.04 LTS server to 9.x is not a good idea. I understand it :) But what is the best way to update a server?

I've also been reading that you should update mdadm to atleased 2.6.8. What is the safe way of doing this? I don't want to loose anything on my raid :(

Thanks for the help

---

### Post by hal10000 on 2009-09-10
You can enable some repositories (e.g. backports) in your /etc/apt/sources.list. You can do this manually or e.g. with synaptic.

> I don't want to loose anything on my raid
Why do you want to update it? If it works, then let it be. "Never touch a running system"

---

### Post by tgrimley on 2009-09-10
ditto, unless it's security or you're wanting a new feature, let it be.

as far as updating mdadm, think about why.. bug fixes, new features?  you can get the most recent code off the author's websites and compile it, not too much trouble.  I'd probably take my array offline to do that, but not sure what other precautions are wise.

---

### Post by whaase on 2009-09-10
> **tgrimley said:**
> ditto, unless it's security or you're wanting a new feature, let it be.

as far as updating mdadm, think about why.. bug fixes, new features?  you can get the most recent code off the author's websites and compile it, not too much trouble.  I'd probably take my array offline to do that, but not sure what other precautions are wise.

Thats basically what I want to do is update mdadm. Just worried lol

---

### Post by R.Bucky on 2009-09-11
I will operate Ubuntu Server 8.04 until the conclusion of the service updates. Only then, would I even think about tearing down my array. Unless there is a critical feature that you need to use in the later versions - leave it.

---

