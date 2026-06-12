---
title: "documentation on what release-upgrader does"
date: 2007-12-01
forum: Ubuntu Brainstorm
---

### Post by strave on 2007-12-01
Ok, I understand that an automated release-upgrade tool is of great value for unexperienced users. And it makes support easier, if this is the only recommendend method for a release upgrade.

But it think it would be really helpful to have some information about what this tool exactly does, so that I can do the same manually. (My gentoo-friends laugh at me!) I have searched for quite some time and couldn't find anything. (Please correct me, if I am wrong.)

This information is especially valuable, if the release-upgrade-tool once again says: "There was an error, I'm giving up! Your system is messed up, good bye!"

This already happened to me two times. Fixing with the standard tools was always possible, but it would have been easier, if I had known, what to pay attention to. E.g. during my gutsy upgrade I ran into the evms-upgrade bug (see [#115616]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/115616")). The release-upgrader removes the evms-package. But not for me, because it crashed before and all I could do was to "aptitude dist-upgrade" and hope for the best.

---

### Post by smartboyathome on 2007-12-01
Well, this would be NICE, but not exactly necessary.

---

### Post by loa on 2007-12-04
I support this. Proper documentation is always good. And in case something goes wrong when upgrading, I would be happy having access to that kind of docs. So, if the developers has time for this, it would be great if they could document it.

---

