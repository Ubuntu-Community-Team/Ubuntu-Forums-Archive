---
title: "Upgrading phpMyAdmin"
date: 2008-09-02
forum: Server Platforms
---

### Post by unsoc on 2008-09-02
At the moment my current version of phpMyAdmin is 2.11.3 I took a look on the main site and the current version is 2.11.9

I tried doing the following

sudo apt-get upgrade phpmyadmin

And I got this in return

Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  bind9-host dnsutils libbind9-30 libisccfg30
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.


And when I try sudo apt-get update there is nothing for phpMyAdmin, how would I go about updating to the current version?

Thanks!

---

### Post by cariboo on 2008-09-02
Is there a reason why you want to upgrade? Aside from there being a new version. If it works just leave it until they get the dependencies for the four packages being held back to be availabe.

Jim

---

### Post by unsoc on 2008-09-02
I'd like to keep everything updated and as secure as I can.
 That's about the only reason.

I suppose this would be one of those cases " if it's not broken don't fix it"

---

