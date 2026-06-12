---
title: "Adding Feisty Repositories Into Dapper Server"
date: 2008-03-30
forum: Server Platforms
---

### Post by vital101 on 2008-03-30
Hey everyone,

I was wondering if their would be any negative side effects to replacing my  current apt sources.list file with one from Feisty.  I'd like access to newer versions of software.

Thanks,
vital101

---

### Post by dmizer on 2008-03-30
adding feisty repos to your dapper server will break things.

what exactly are you needing more current versions of and why?  there's probably a much better way of going about this.

---

### Post by vital101 on 2008-03-30
The program I need a newer version of is Plone.  The version of plone in the dapper repositories is on 2.1 or so.  I need 2.5.  I tried installed from the Plone.org site, but I didn't like how it was an all inclusive binary.  I'd rather have an apt install that's tailored for my distribution.

---

### Post by dmizer on 2008-03-31
looks like plone 2.5 will need a more current version of python, and may break many things.  2.5 probably hasn't been included in dapper repos because 2.5 has some critical bugs and security vulnerabilities, as well as because it requires a more current version of python.

if the server is in service at this time, i would suggest you make a backup or set up a virtual server for testing purposes.  that way, when things break, you're not interrupting service.

if you don't want the binary, the tarball source is also available for download. [https://launchpad.net/plone/2.5/2.5.3/+download/Plone-2.5.3-final.tar.gz](https://launchpad.net/plone/2.5/2.5.3/+download/Plone-2.5.3-final.tar.gz) ... even though installing from source may seem like a real headache.  it'll be less of a headache than most any other way you have for upgrading.  i would also strongly suggest to upgrade to 2.5.3 instead of just 2.5, as 2.5.3 will give you the security updates.

alternatively, you can wait until hardy final is released and upgrade your server from dapper to hardy (which is also LTS).

---

### Post by vital101 on 2008-03-31
Thanks for the heads up.  I'll probably just install from source.  I wasn't able to find the source code before, so it shouldn't be too hard.

---

