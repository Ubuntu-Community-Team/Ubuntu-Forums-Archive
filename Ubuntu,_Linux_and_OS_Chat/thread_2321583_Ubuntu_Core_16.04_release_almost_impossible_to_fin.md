---
title: "Ubuntu Core 16.04 release almost impossible to find!"
date: 2016-04-23
forum: Ubuntu, Linux and OS Chat
---

### Post by candlerb on 2016-04-23
I don't know where best to post this, so my apologies if this is the wrong place.

Ubuntu 16.04 makes a big thing about including the snap(py) packaging system from Ubuntu Core. So I thought I'd download Ubuntu Core to have a look at a system built around this whole concept.

However the current website organisation makes this almost impossible to find - it gives the impression that Ubuntu Core was abandoned at version 15.04, and you have to be extremely persistent. Here is what I tried.

(1) If you start at
[http://www.ubuntu.com/download](http://www.ubuntu.com/download)
and follow the link to "Ubuntu Core" and then the link to the Intel NUC instructions, then you end up at:

[https://developer.ubuntu.com/en/snappy/start/intel-nuc/](https://developer.ubuntu.com/en/snappy/start/intel-nuc/)

There they give you wget URLs for 15.04 (vivid) only. It's also a link to people.canonical.com - not an official release location. [http://people.canonical.com/~platform/snappy/](http://people.canonical.com/~platform/snappy/) does not have anything newer than 15.04.

(2) If you start at
[http://releases.ubuntu.com/](http://releases.ubuntu.com/)
and click on "15.04" then you get Snappy; but if you click on "16.04" then you only get Desktop and Server.

(3) If you start at
[http://cdimage.ubuntu.com/](http://cdimage.ubuntu.com/)
and click on "ubuntu-snappy" then there are directories for 15.04, daily, and vivid (=15.04) only.

If you click on "ubuntu-core" then there are directories including trusty, vivid, wily (15.10) but not xenial. And it seems these are just daily builds.

(4) So now I fall back to Google. If I google for "ubuntu core 16.04" I find as the first two hits:

"Ubuntu Core 16.04 (Xenial Xerus) Daily Build - CdImage"
[http://cdimage.ubuntu.com/ubuntu-core/daily-preinstalled/current/](http://cdimage.ubuntu.com/ubuntu-core/daily-preinstalled/current/)
[http://cdimage.ubuntu.com/ubuntu-core/daily/pending/](http://cdimage.ubuntu.com/ubuntu-core/daily/pending/)

But I don't want daily builds, I want the 16.04 release.

The third hit is
"Ubuntu Core 16.04 (Xenial Xerus) Beta 2 - CdImage"
[http://cdimage.ubuntu.com/ubuntu-core/releases/16.04/beta-2/](http://cdimage.ubuntu.com/ubuntu-core/releases/16.04/beta-2/)

Aha! Finally something which looks like it might be a recent release! Except... that link gives a 404 when you follow it.

So finally I manually modify the URL to walk up to the parent directory, i.e. [http://cdimage.ubuntu.com/ubuntu-core/releases/16.04/](http://cdimage.ubuntu.com/ubuntu-core/releases/16.04/),
and at last I find this:
[http://cdimage.ubuntu.com/ubuntu-core/releases/16.04/release/](http://cdimage.ubuntu.com/ubuntu-core/releases/16.04/release/)

HOORAY!

But this is far too much work, and I'm sure this must put people off trying Ubuntu Core. Surely either the Ubuntu download page or the snappy developer page should link to this?

Regards,

Brian Candler.

P.S. The snap(py) documentation is pretty poor too, but that's a different issue. For example
[https://developer.ubuntu.com/en/snappy/guides/system-updates/](https://developer.ubuntu.com/en/snappy/guides/system-updates/)
says "Newer snappy systems use a different mechanism called "all-snap" that is using a different strategy for the transnational [sic] updates" - but I can't find any documentation on how "all-snap" works.

---

### Post by Bucky Ball on 2016-04-23
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by candlerb on 2016-04-23
P.S. After all that, [http://cdimage.ubuntu.com/ubuntu-core/releases/16.04/release/](http://cdimage.ubuntu.com/ubuntu-core/releases/16.04/release/) gives just a .tar.gz file of the root filesystem - not a bootable .img file that you could dd to persistent storage.

(I wondered if perhaps that was the difference between "snappy" and "core"; but the page at [https://developer.ubuntu.com/en/snappy/start/intel-nuc/](https://developer.ubuntu.com/en/snappy/start/intel-nuc/) explicitly says that the 15.04 img file is "Ubuntu Core")

---

### Post by candlerb on 2016-04-25
Another thing: Ubuntu Core is mentioned in the "Support Lifecycle" section of
[https://wiki.ubuntu.com/XenialXerus/ReleaseNotes](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes)
but there is no link to it in the "Download Ubuntu 16.04 LTS" section.

---

### Post by ian-weisser on 2016-04-25
That's right.
Ubuntu Core is not intended to be a polished, consumer-installable, supported flavor of Ubuntu. The Core project has a very different purpose.
Unless you are a (real) embedded device developer, you are not in the target market.

See [https://wiki.ubuntu.com/Core](https://wiki.ubuntu.com/Core)
The wiki page is a bit stale..like most user-contributed Ubuntu documentation.
As an Ubuntu participant, you are of course welcome to improve and update the wiki page.

---

### Post by yoshii on 2016-04-25
Thanks for the heads up.  Good points.

---

### Post by claudioandre.br on 2016-06-07
> **candlerb said:**
> 
However the current website organisation makes this almost impossible to find - it gives the impression that Ubuntu Core was abandoned at version 15.04, and you have to be extremely persistent. Here is what I tried.


Ubuntu Core 16.04 is not ready yet.

See the developers commenting on the subject (you can see all posts using previous/next):
- [https://lists.ubuntu.com/archives/snapcraft/2016-June/000101.html](https://lists.ubuntu.com/archives/snapcraft/2016-June/000101.html)

There has not yet been a release of snappy Ubuntu Core based on Ubuntu
16.04 LTS.

---

