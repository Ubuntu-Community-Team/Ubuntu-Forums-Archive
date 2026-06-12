---
title: "Question on windows client log in to samba domain controller"
date: 2008-04-16
forum: Server Platforms
---

### Post by cpthk on 2008-04-16
If I have windows clients log in to samba domain controller. In windows side, which group are samba users under? Users group?

I am trying to set permission to lock users to write to c drive.

---

### Post by cdenley on 2008-04-17
I think after joining the domain, the client doesn't have any domain users or groups in any local groups. However, any local user (including domain users) are considered a member of "NT AUTHORITY\Authenticated Users" and belong to the "Users" group by default. You can remove this special group, and/or create your own group assignments in the windows user/group management console using users/groups from the domain controller.

---

