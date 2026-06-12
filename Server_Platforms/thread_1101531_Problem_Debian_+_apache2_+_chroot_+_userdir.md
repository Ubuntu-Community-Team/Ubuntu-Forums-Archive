---
title: "Problem: Debian + apache2 + chroot + userdir"
date: 2009-03-20
forum: Server Platforms
---

### Post by Hablas on 2009-03-20
Move this thread, if this is in a wrong place!

I have a problem with my Debian Etch.

The setup is this:
Apache2 with mod-chroot enabled.

Users asked me to enable userdir.

The problem is that Apache can't find users public_html, witch is in their own /home directory, from inside the chroot.

Is this fixable or is chroot and userdir just not meant to be run at the same time?

---

### Post by rrll1977 on 2009-05-18
Hi,

Have you got to work mod_rewrite with mod_userdir

I can't get mod_rewrite to work with user's pages on /home/user/public_html, although it appears to work fine for server root pages on /opt/lampp/htdocs

Regards

---

