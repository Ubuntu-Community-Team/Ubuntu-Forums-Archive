---
title: "Thunderbird stuck at version 45.2 in 16.10 ?"
date: 2016-09-28
forum: Ubuntu Development Version
---

### Post by fthx on 2016-09-28
Hi,

I was waiting for 45.3 update to avoid some bugs, but it is still the 45.2 which remains available.
So, I checked this stuff today and :
[https://launchpad.net/ubuntu/+source/thunderbird/1:45.3.0+build1-0ubuntu1/+build/10750921](https://launchpad.net/ubuntu/+source/thunderbird/1:45.3.0+build1-0ubuntu1/+build/10750921)
shows that the version should be 45.3 in Proposed but all builds failed.

Is that intended or is it a bug ?

Thanks.

---

### Post by PaulW2U on 2016-09-28
> **fthx said:**
> Is that intended or is it a bug ?
If Thunderbird has failed to build then it's something the the developers need to deal with.

It's common for the latest builds of Firefox or Thunderbird to **not** be available in the development release at the same time as the other releases. I'm sure whatever build problems there are will be sorted by October 13th when Yakkety is due to be released.

---

### Post by fthx on 2016-09-28
The underlying question was : why TB does not compile on Yakkety ?

---

### Post by fthx on 2016-10-11
I reported this bug and quickly after an update was published as there was a security notice in 45.3.
BUT... :
- I cannot start 45.3 version (proposed repos.) : crash, no error messages
- starting with a new profile allows to run TB but I prefer to not having to configure all that again
- v. 45.4 bugfix release has been published but not in Ubuntu

[https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/1631479](https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/1631479)

Other question : running Gnome Shell, I do not get any notification except if I install Gnotifier extension (e.g.). Is that a known bug ?

---

### Post by PaulW2U on 2016-10-11
> **fthx said:**
> [https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/1631479](https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/1631479)
I've seen some comments on IRC which have suggested that this issue may not fixed before Ubuntu 16.10 is released but might be resolved with a stable release update [SRU] some after. At least the bug report has been assigned to the person who I know is responsible within Canonical to work on new releases of Firefox and Thunderbird.

---

### Post by cariboo on 2016-10-11
I just updated to Thunderbird 45.3.0 a few minutes ago through regular updates.

---

### Post by fthx on 2016-10-12
Yes, the last *-ubuntu3 release works flawlessly.

---

### Post by PaulW2U on 2016-10-12
> **cariboo said:**
> I just updated to Thunderbird 45.3.0 a few minutes ago through regular updates.
You obviously have -proposed enabled. :)

An ancient version 38.6 will probably be on the final release ISO, the latest version of which is what I am using to post this on the day before Yakkety's release.
```
ubuntu@ubuntu:~$ apt policy thunderbird
thunderbird:
  Installed: 1:38.6.0+build1-0ubuntu1
  Candidate: 1:38.6.0+build1-0ubuntu1
  Version table:
 *** 1:38.6.0+build1-0ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu yakkety/main amd64 Packages
        100 /var/lib/dpkg/status

```
From what I'm reading on IRC, the latest version doesn't build on all architectures which is why it hasn't (yet) been made available on the final ISOs.

---

### Post by fthx on 2016-10-12
You can see it on Launchpad too... A new *ubuntu4 version is currently being built with GCC5.

---

### Post by PaulW2U on 2016-10-12
> **fthx said:**
> You can see it on Launchpad too... A new *ubuntu4 version is currently being built with GCC5.
Just downloaded - so it will be included on the final Yakkety ISOs, some or all of which, are being respun as I type   :D
```
paul@C50B~/I/GNOME> apt policy thunderbird
thunderbird:
  Installed: 1:45.3.0+build1-0ubuntu4
  Candidate: 1:45.3.0+build1-0ubuntu4
  Version table:
 *** 1:45.3.0+build1-0ubuntu4 500
        500 http://gb.archive.ubuntu.com/ubuntu yakkety/main amd64 Packages
        100 /var/lib/dpkg/status
```

---

