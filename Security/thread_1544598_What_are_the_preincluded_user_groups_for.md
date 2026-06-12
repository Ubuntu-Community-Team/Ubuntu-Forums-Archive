---
title: "What are the preincluded user groups for?"
date: 2010-08-02
forum: Security
---

### Post by lightningfox on 2010-08-02
Hi 

I want to know what the user groups that are preincluded on Linux (eg. mail, video) do.

Please tell me or give me a link to a website that explains it.

---

### Post by tim48134 on 2010-08-02
Groups in Linux have to do with permissions to certain files and the hardware. Members of a group, whether human or system, are only allowed to do what is permitted by the system's configuration. A normal user has both individual permissions, assigned just to them, and group permissions given to them because they belong to a group. For instance, members of the 'audio' group are allowed to access sound devices, and members of the 'display' group can change display properties. A common way to regulate what a user can do is to assign them to groups. You do not need to mess with these in Ubuntu; by changing 'User Privileges' under System -> Users and Groups -> Advanced Settings, Ubuntu will automatically assign the user to the necessary groups.

The most basic groups defined by the Linux Standard Base specification are [here]("http://refspecs.linux-foundation.org/LSB_3.2.0/LSB-Core-generic/LSB-Core-generic/usernames.html").

Hope this helped! :popcorn:

---

### Post by lightningfox on 2010-08-02
Hi tim48134

Thanks for your answer and the link.

---

