---
title: "SRPM alternate?"
date: 2009-12-20
forum: Server Platforms
---

### Post by shoaibi on 2009-12-20
Is there any SRPM altenate available in ubuntu? i miss the flexibility of .spec files :'(

If there is, can you point a link which will guide me more on that?

PS:
I do have a fallback to pkgsrc.. :)

---

### Post by craigp84 on 2009-12-20
Hi shoaibi,

Yeah, best place for the details is [http://www.debian.org/doc/maint-guide/](http://www.debian.org/doc/maint-guide/) -- it's pretty similar process just different commands and the spec file is split across the the control file and rules file in debian.

However if you want to reuse your existing srpms take a look at the "alien" package.

Hope it helps

---

### Post by shoaibi on 2009-12-20
another related question:
When i keep doing the same post-installation configuration tasks, whats better:
> create a custom deb which installs the package as well as configures it my need?
> create a script instead

Eitherway i plan to public this stuff to improve and keep a track...

---

### Post by craigp84 on 2009-12-20
> When i keep doing the same post-installation configuration tasks

I guess it depends on your specific case, what actions you keep redoing.

For code reuse (snippets of post install code etc.) i tend to manage that upstream of the package build process. i.e. i have an include/ dir in my package builder user's home area. I have a bunch of helper scripts and they just source in a couple of templates from the includes dir when im setting up a completely new package.

Just experiment, find what fits for you. For me, most of my time spent in packaging isn't packaging new software, it's just building newer packages with newer versions of the code. My helper scripts etc. are geared around that, and to a large extent, around the company's way of working.

---

