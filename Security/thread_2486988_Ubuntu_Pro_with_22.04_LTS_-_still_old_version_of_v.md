---
title: "Ubuntu Pro with 22.04 LTS - still old version of vim (or gradle)"
date: 2023-05-19
forum: Security
---

### Post by mondayconsulting on 2023-05-19
Hi,

hope, this is the right place for the question - and maybe it's a stupid beginner question...

Ubuntu Pro comes with "Reduce your average CVE exposure time from 98 days to 1 day with expanded CVE patching". Therefore I got Ubuntu Pro for 22.04 LTS. 
BUT (just examples)
- vim is included in version 8.2.3995. This version has some CVEs (e.g. CVE-2022-2182 or CVE-2022-286 and some more). Version 9.0 was released in June 2022 and fixes these CVEs. 
- gradle is included in version 4.4.1. - released in 2017. Newest version is 8.1.1.

Is there a reason why these versions are not updated, even with Ubuntu Pro?
(Of course, there are more examples.)

Thanks a lot!
Andreas

---

### Post by The Cog on 2023-05-19
```
$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 22.04.2 LTS
Release:	22.04
Codename:	jammy
$ vim --version
VIM - Vi IMproved 8.2 (2019 Dec 12, compiled Apr 18 2023 11:40:57)
Included patches: 1-3995, 4563, 4646, 4774, 4895, 4899, 4901, 4919
Modified by team+vim@tracker.debian.org
Compiled by team+vim@tracker.debian.org
```
I think you need to look into those patches that have been included. They probably address the CVEs you are concerned about.
Also, I think Ubuntu Pro offers security updates to a wider selection of packages, i.e outside of the core Ubuntu package set, like the Multiverse and Universe packages. I'm pretty sure it doesn't offer more or faster patching to the core Ubuntu package set, which includes vim. That said, I'm not sure what they mean by reduced exposure time.

---

