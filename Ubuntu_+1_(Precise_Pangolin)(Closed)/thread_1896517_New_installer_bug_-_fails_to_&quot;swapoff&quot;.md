---
title: "New installer bug - fails to &quot;swapoff&quot;"
date: 2011-12-17
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kansasnoob on 2011-12-17
I'd recently mentioned that Colin Watson was working on this bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/766265](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/766265)

He released a fix which I think is sufficient. Basically the Continue button changes to Install now if you're using "alongside" and adequate free space exists. Not my preferred choice but it'll work.

But now automated installs fail:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/905628](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/905628)

I'm sure the devs will get on that ASAP but with the weekend I thought I should make everyone aware :)

---

### Post by kansasnoob on 2011-12-19
In order to get this on the radar I'm probably going to need an "effects me too" here:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/905628](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/905628)

So, if someone feels like testing a new daily image that would be cool :D

To reproduce just try installing with an existing swap.

---

### Post by ronacc on 2011-12-19
downloading todays daily now , will try an install when I return from a job about noon eastern time .

---

### Post by ronacc on 2011-12-19
me too'd and added comment .

---

### Post by kansasnoob on 2011-12-20
I see Colin Watson is assigned to this now, so it's just wait time :)

---

### Post by kansasnoob on 2011-12-20
> **ronacc said:**
> me too'd and added comment .

Just realized I forgot to thank you ........... so, Thank You :)

I seem to notice there are certain ways to draw dev attention to bugs, and multiple reporters seems to be one of them.

Anything I can report during iso-testing is also generally guaranteed to get some comment from the devs though.

From what I've seen the devs are really intense about fixing confirmed bugs in Precise ............ I love it.

---

### Post by kansasnoob on 2011-12-22
This appears to be fixed:

[https://bugs.launchpad.net/ubuntu/+source/partman-basicfilesystems/+bug/905628](https://bugs.launchpad.net/ubuntu/+source/partman-basicfilesystems/+bug/905628)

But I notice that we're still seeing changes in 'ubiquity' since version 2.9.8 here:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/766265](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/766265)

We're now up to version 2.9.10:

> ubiquity (2.9.10) precise; urgency=low

  * Handle interface change in ICU 4.8: unknown time zones result in
    TimeZone instances with ID "Etc/Unknown" rather than "GMT".
  * Import icu rather than PyICU, preferred as of python-pyicu 1.0.
  * Automatic update of included source packages: partman-basicfilesystems
    71ubuntu3, partman-btrfs 7ubuntu1.

 -- Colin Watson <cjwatson@ubuntu.com>  Tue, 20 Dec 2011 17:59:53 +0000

ubiquity (2.9.9) precise; urgency=low

  * Cope with pygobject returning unicode objects rather than UTF-8-encoded
    str objects (LP: #905916, #906015).

 -- Colin Watson <cjwatson@ubuntu.com>  Mon, 19 Dec 2011 12:25:13 +0000


Looks like minor changes, but beware ;)

If one of the mods would be so kind, I think this should now be merged with this thread:

[http://ubuntuforums.org/showthread.php?t=1894929](http://ubuntuforums.org/showthread.php?t=1894929)

Sorry to be a pain in the neck :)

Thank you to all for everything they do.

---

