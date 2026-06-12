---
title: "Managing kvm instance like a service?"
date: 2008-10-19
forum: Server Platforms
---

### Post by jeffk on 2008-10-19
I completed a physical-to-virtual Windows server migration to kvm using fre tools (Yay!).

Now I have to make sure this kvm instance stays available across Ubuntu 8.04 server reboots, is easily monitored for up-status, etc.

Anyone have a clever implementation for init.d -style services of kvm instances?

Absent any existing solution that I could use when this goes into production Monday morning ;), I was thinking of using a process monitor called [supervisord ]("http://supervisord.org/"), since I'll eventually be using that to keep similar availablility for web application server processes (zope/plone/trac/django).

---

### Post by jeffk on 2008-10-20
I see a lot of information on this subject at:

[http://help.ubuntu.com/community/KVM](http://help.ubuntu.com/community/KVM)

---

