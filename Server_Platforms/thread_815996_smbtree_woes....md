---
title: "smbtree woes..."
date: 2008-06-02
forum: Server Platforms
---

### Post by stanger192 on 2008-06-02
hey all

ive just installed ubuntu 8.04 server, icewm, system-samba-config and a few other apps
now the problem is that i dont get any listing from smbtree at all. it asks for my password then it goes back to the command prompt (ive also set up a share thru system-samba-config and it doesnt show up on my ubuntu desktop pc either)

so what am i doing wrong?

---

### Post by ssouffri on 2009-09-08
Did you add exceptions to the firewall to allow netbios and smb traffic? You can always just disable the firewall completely to test if it actually is the problem.

---

