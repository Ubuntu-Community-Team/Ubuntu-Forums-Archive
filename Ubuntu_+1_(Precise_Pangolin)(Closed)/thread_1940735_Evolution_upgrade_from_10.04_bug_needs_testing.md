---
title: "Evolution upgrade from 10.04 bug needs testing"
date: 2012-03-14
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by dcstar on 2012-03-14
I encountered this bug in migrating Evolution to a version earlier than the one in 12.04, **so it would be good if a 10.04 user with multiple "On This Computer" address books could test it** and confirm if the bug still exists:

[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/761037](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/761037)
And this is the Upstream Bug:
[https://bugzilla.gnome.org/show_bug.cgi?id=648045](https://bugzilla.gnome.org/show_bug.cgi?id=648045)

Basically only the first "On This Computer" address book is converted correctly, any following address books won't open with an error message after conversion.

I found a fairly simple fix on my system but it would be better if people didn't need to use it! Since it would seem reasonable that many 10.04 LTS users will migrate to 12.04 LTS, those that continue to use Evolution would like a smooth upgrade.

---

### Post by dcstar on 2012-03-14
> **dcstar said:**
> I encountered this bug in migrating Evolution to a version earlier than the one in 12.04, **so it would be good if a 10.04 user with multiple "On This Computer" address books could test it** and confirm if the bug still exists:
..........
Basically only the first "On This Computer" address book is converted correctly, any following address books won't open with an error message after conversion.
..........

Ok, that first bug has been resolved in the current Evolution version in 12.04 - all "On This Computer" address books convert ok.

But doing a test upgrade from a standard 10.04 system to 12.04 (using the same /home folder) has resulted in discovering this bug:

[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/955673](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/955673)

---

### Post by dcstar on 2012-03-15
> **dcstar said:**
> 
.........
[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/955673](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/955673)

Issue is that **evolution-couchdb** package (and therefore all CouchDB components) is not installed by default in 12.04. Once this is installed Evolution works ok (after a reboot).

Anyone currently migrating from 10.04 needs to manually install this package as well as the basic Evolution packages if they want to maintain full functionality of the e-mail client that they are currently using.

---

