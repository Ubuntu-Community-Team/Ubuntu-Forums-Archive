---
title: "What's this .txz packaging format that comes with the new Slack release?"
date: 2009-08-31
forum: The Cafe
---

### Post by kevdog on 2009-08-31
Ok so I saw this on distrowatch.com describing the Slackware 13.0 release:  a new .txz package format with much better compression

What exactly is the txz (other than tarred) format?

---

### Post by &#32 Greg on 2009-08-31
It uses an xz compresses tar as opposed to a gz compressed tar.

---

### Post by kevdog on 2009-08-31
Doing some reading on the new xz format -- but it doesn't seem ubuntu offers a package at least in my version.  Will this be in Jaunty?

[http://linuxgazette.net/162/lindholm.html](http://linuxgazette.net/162/lindholm.html)
[http://tukaani.org/xz/](http://tukaani.org/xz/)

---

### Post by andrew.46 on 2009-09-14
Hi kevdog,

> **kevdog said:**
> Ok so I saw this on distrowatch.com describing the Slackware 13.0 release:  a new .txz package format with much better compression

What exactly is the txz (other than tarred) format?

New compression format. Have a look at [the changelogs]("http://slackware.osuosl.org/slackware-13.0/ChangeLog.txt"). The section you are after is marked:

> Fri May  8 18:49:03 CDT 2009


Andrew

---

