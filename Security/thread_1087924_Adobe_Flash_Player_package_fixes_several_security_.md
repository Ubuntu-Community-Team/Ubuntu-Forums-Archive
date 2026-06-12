---
title: "Adobe Flash Player package fixes several security issues"
date: 2009-03-05
forum: Security
---

### Post by registerdown on 2009-03-05
Hi all, 

Today Adobe released a fix for proprietary the flash player which also closes critical Linux issues. Redhat has realsed a fix for it: [http://freshmeat.net/articles/view/3552/]("http://freshmeat.net/articles/view/3552/")

It this something I should worry about if I have a flash player via synaptic installed in Ubuntu 8.10? (I am a newbie!!):o

---

### Post by bodhi.zazen on 2009-03-05
Thank you for the information.

If the Ubuntu packages are affected I would expect a fix shortly.

You might also consider filing a security "bug" on Launchpad.

You could either disable flash or if you prefer, install the update from adobe.

I would **not** install a Red hat .rpm w./ alien.

---

### Post by cdenley on 2009-03-05
An update fixing the bugs mentioned and more appears to have been released last week.
[http://changelogs.ubuntu.com/changelogs/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_10.0.22.87ubuntu1~intrepid1/changelog](http://changelogs.ubuntu.com/changelogs/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_10.0.22.87ubuntu1~intrepid1/changelog)
> 
flashplugin-nonfree (10.0.22.87ubuntu1~intrepid1) intrepid-security; urgency=low

  * SECURITY UPDATE: New upstream release 10.0.22.87
    - debian/config, debian/postinst: Updated for sha256sums.
    - CVE-2009-0114
    - CVE-2009-0519
    - CVE-2009-0520
    - CVE-2009-0522
    - CVE-2009-0521

 -- Jamie Strandboge <jamie@ubuntu.com>  Wed, 25 Feb 2009 10:08:27 -0600


---

### Post by registerdown on 2009-03-05
Hi bodhi.zazen and cdenley - thanks for your quick answers! Great to see that this update has already been relased - I love Ubuntu!:D 

Now I also learned I can check the changelogs here: [http://changelogs.ubuntu.com/changelogs/pool/]("http://changelogs.ubuntu.com/changelogs/pool/")

---

