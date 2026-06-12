---
title: "Reporting XFCE Bugs"
date: 2018-05-30
forum: Ubuntu, Linux and OS Chat
---

### Post by kazakore on 2018-05-30
The instructions here are broken. There are zero packages listed on the Xubuntu Team page which it says to go through!

[https://wiki.ubuntu.com/Bugs/Upstream/Xfce](https://wiki.ubuntu.com/Bugs/Upstream/Xfce)

Pretty sure as Ubuntu users, generally using fairly old and often already patched versions of software, we shouldn't be directly reporting upstream only..... (And that does goes against the instructions.)

---

### Post by Autodave on 2018-05-30
What version of Xubuntu are you using?  What problem(s) are you having?

---

### Post by Frogs Hair on 2018-05-30
I see bug lists from the last 7 day and 24 hours. Can you explain what you mean by broken . I used the upstream link in the following page.

[https://docs.xubuntu.org/contributors/qa-bugs.html](https://docs.xubuntu.org/contributors/qa-bugs.html)

Last 24 Hours.
[https://bugzilla.xfce.org/buglist.cgi?chfieldfrom=24h](https://bugzilla.xfce.org/buglist.cgi?chfieldfrom=24h)

---

### Post by kazakore on 2018-05-30
> **Frogs Hair said:**
> I see bug lists from the last 7 day and 24 hours. Can you explain what you mean by broken .

Well it says:
"Most packages listed in [bug contact packages for the Xubuntu Team]("https://bugs.launchpad.net/~xubuntu-team/+packagebugs"), including:"
and that text posts to:
[https://bugs.launchpad.net/~xubuntu-team/+packagebugs](https://bugs.launchpad.net/~xubuntu-team/+packagebugs)
Which doesn't have a single package listed there to file a bug about!

So there are no actually valid instructions for reporting Bugs on LP, just a link that takes you to a useless place making it sound like there should be a list of the software packages they maintain which doesn't exist.

> 
 I used the upstream link in the following page.

[https://docs.xubuntu.org/contributors/qa-bugs.html](https://docs.xubuntu.org/contributors/qa-bugs.html)

That one actually has useful information about normal bug reporting on LP, so that's good. 

Actually it may be mainly a non-issue but the link in my original post is the number one result when searching for something like "report ubuntu xfce/thunar bug" and I didn't see the ones for the normal reporting, rather than reporting Upstream. Finding that page first made me wonder if I was even meant to do it on LP so I ended up reporting upstream on the XFCE Bugzilla before coming back and afterwards finding the package on LP and then linking the two together. I always thought generally as Ubuntu users we should always report it to LP and then the maintainer would push it upstream if need be but because of the wording of the page I initially found and the empty looking page it sends you to I thought that must have changed for some strange reason.....

---

### Post by flocculant on 2018-05-30
That wiki [page]("https://wiki.ubuntu.com/Bugs/Upstream/Xfce") is well out of date - it was last edited in 2009 ...

I certainly didn't know it existed. That page is in fact specifically about reporting upstream

I've now changed it to point to the Xubuntu Team [subscribed packages]("https://bugs.launchpad.net/~xubuntu-bugs/+packagebugs")

The page at docs.xubuntu.org should be up to date - I wrote them.

As far as upstream goes, Xubuntu and Xfce are rather intimate - all of our devs are Xfce devs - so generally while reporting to Launchpad is the right thing to do - often we'd want it reported upstream - perhaps the docs don't make that point.

Reporting bugs to Launchpad has a rather exhaustive wiki [page]("https://help.ubuntu.com/community/ReportingBugs")

---

### Post by wildmanne39 on 2018-05-30
*Thread moved to **Ubuntu, Linux and OS Chat for a more appropriate fit**.*

---

### Post by kazakore on 2018-05-31
> **flocculant said:**
> 
I've now changed it to point to the Xubuntu Team [subscribed packages]("https://bugs.launchpad.net/~xubuntu-bugs/+packagebugs")




Perfect, that's the major point that caused my confusion. Shame such an old (out of date) page seems to have the highest SEO ranking when searching for terms related to reporting ubuntu xfce bugs but I believe that should help anybody else landing on the same page as I did :)

---

