---
title: "GDM3 + LDAP in Ubuntu 18.04"
date: 2018-06-07
forum: Ubuntu, Linux and OS Chat
---

### Post by ivan-a-wolf on 2018-06-07
[COLOR=#242729][FONT=Arial]I'm trying to configure LDAP using GDM3 (3.28.0) in Ubuntu 18.04.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]But i can just log in terminal with ldap users. In the GUI I can't log in (famous GDM loop login).
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I configure pam to create the home folder:[/FONT][/COLOR]
```
vim /etc/pam.d/common-session
session required     pam_mkhomedir.so       umask=077 skel=/etc/skel
```

[COLOR=#242729][FONT=Arial]But, it wasn't sufficient!
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I installed lightdm, and in this GUI, I can login!
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Any suggestion?
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Thanks![/FONT][/COLOR]

---

