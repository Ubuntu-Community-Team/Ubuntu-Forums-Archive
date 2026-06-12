---
title: "restrict access to service based on pam and group membership"
date: 2007-10-02
forum: Server Platforms
---

### Post by jodeet on 2007-10-02
Hello,

I want to use pam to control access to certain services.  I want to be able to say that any user who is a member of group XYZ can access a given service, and I want to be able to use locally defined groups (i.e. groups in /etc/group).  pam_ldap, and pam_winbind give you this kind of ability, but not, of course, with locally defined groups.  What pam module can I use to restrict access by group?  pam_group seems to be something else: it seems to grant group membership.  pam_unix doesn't seem to have what i want either.  pam_require does, but isn't part of feisty.  Why isn't pam_require included in ubuntu?

---

