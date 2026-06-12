---
title: "Custom Prompt configured via a custom package"
date: 2014-07-15
forum: Server Platforms
---

### Post by Frizianz on 2014-07-15
Hi Guys,

Currently I have a custom package that has all of my branding and motd etc in it for my servers.

This is all well and good, however the current problem is that its overriding the files in /etc/skel/ (for a custom $PS1 prompt) are part of package bash. I may be doing this in the complete wrong place, if so please let me know. Otherwise, how do I deal with conflicts in files between packages. EG, if package bash is installed, use my version of /etc/skel/.profile rather than the one from package bash. Doing this in a clean way is a must.

Anyone got any thoughts?

Cheers,

Fraser

---

