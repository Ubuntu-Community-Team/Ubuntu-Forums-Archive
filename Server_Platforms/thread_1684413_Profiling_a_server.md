---
title: "Profiling a server"
date: 2011-02-09
forum: Server Platforms
---

### Post by gushy on 2011-02-09
Hi Guys,

I've got a potential new client with existing linux systems, normally that doesn't bother me but I already know that at least one of the systems "is a bit quirky" and will only run it's bespoke app with specific versions of software running on the box.

I was wondering what every one does when it comes to profiling a server?  Before I look to see if I can migrate their app to a new server / platform I want to make sure I know everything there is to know about the current installed server.

---

### Post by elico on 2011-02-09
packages list partitioning.
mem
cpu
and must check that app specification and dependencies.
if it's web like using PHP or MYSQl\POSTGRESQL then their settings.

---

### Post by gushy on 2011-02-09
Yeah those are the normal things I go through, plus package configs, users, df, du, fstab, /usr/local etc.

Just wanted to see if anyone suggested anything I didn't think of.

The ideal would be if someone suggesting a reporting package that showed all that sort of thing inc. hardware etc.

---

