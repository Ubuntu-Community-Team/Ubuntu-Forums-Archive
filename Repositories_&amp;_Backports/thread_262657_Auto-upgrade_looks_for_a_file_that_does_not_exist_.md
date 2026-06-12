---
title: "Auto-upgrade looks for a file that does not exist on the server (security / Kernel)"
date: 2006-09-22
forum: Repositories &amp; Backports
---

### Post by Peacepunk on 2006-09-22
Hi Community

The auto Keep-Up-To-Date thingie of UBUNTU 6.06lts is warning me of a new update,

> linux-restricted-modules-common_2.6.15.11-4_all.deb

and Synaptic would try to download it from

> [http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.15](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.15)

where it doesn't exist (FYI the version 11-5 does exist)

Bug ?

While looking for this file somewhere else, I found a strong recommendation to apply it:
[URL="http://packetstormsecurity.org/0609-advisories/USN-346-2.txt"]
http://packetstormsecurity.org/0609-advisories/USN-346-2.txt[/URL]

This web advice points to the same repository source as the one synaptic tries to get the unexisting file from...

Still some web indexes points the file to be in the repository, but sure it's not (anymore ?)

I looked for alternative source: > [http://de2.vlsm.org/dists/dapper/de2ui/binary-i386/](http://de2.vlsm.org/dists/dapper/de2ui/binary-i386/)

there you can find this missing piece.

Peacepunk

---

