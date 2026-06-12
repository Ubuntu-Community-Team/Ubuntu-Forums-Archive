---
title: "Setting up a repository mirror"
date: 2005-06-06
forum: Repositories &amp; Backports
---

### Post by radbrad on 2005-06-06
Hi there,

we are in the process of setting up a local ubuntu mirror, but the help documents are not very specific (on the wiki)

We cannot afford to mirror 75gb of a full mirror, but could afford the 15gb idea. My question is, is : 

Does the 15gb mirror only track current CD releases? i.e. all architecures, and only packages indexed off the CD?

How can i refine that? 

We would like to keep a repository of only (current release) packages indexed in the multiverse, universe, restricted, and main files, for only the x86 architecture. Since we are not running a diverse network (in terms of achitectures), and we only really need to track packages associated to the current release.

I am new to both ubuntu and debian, so i am sure this has been solved somewhere, just curious where i could find that help doc ;)

---

### Post by Gtaylor on 2005-06-06
There is a package called 'debmirrror' that you'll want to check out. I'm not sure how to use it but this would be what you'd need to search on.

---

