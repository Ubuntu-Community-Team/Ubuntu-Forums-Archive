---
title: "Pam_access and netgroups"
date: 2012-08-27
forum: Security
---

### Post by spoon103 on 2012-08-27
I'm trying to get restricted ssh login working on my 12.04 system, and running into an issue with pam_access.so and how it interprets netgroups. 

Netgroup:
UserDev ( ,alloweduser, )
SystemDev (host.sub.domain.com,,)

Here is the /etc/security/access.conf file:
+ : root :ALL
+ : @UserDev@@SystemDev : ALL

Relevant /etc/pam.d/sshd config:
account  required     pam_access.so debug

And here is what happens when alloweduser logs in via ssh:
```

login_access: user=alloweduser, from=192.168.1.10, file=/etc/security/access.conf
line 1: +  :  root : ALL
list_match: list= root , item=alloweduser
user_match: tok=root, item=alloweduser
string_match: tok=root, item=alloweduser
user_match=0, "alloweduser"
line 2: +  :  @UserDev@@SystemDev  :  ALL
list_match: list= @UserDev@@SystemDev , item=alloweduser
user_match: tok=@UserDev@@SystemDev, item=alloweduser
netgroup_match: 0 (netgroup=UserDev@@SystemDev, machine=NULL, user=alloweduser, domain=)
user_match=0, "alloweduser"
line 3: -  :  ALL  :  ALL
list_match: list= ALL , item=alloweduser
user_match: tok=ALL, item=alloweduser
string_match: tok=ALL, item=alloweduser
user_match=2, "alloweduser"
list_match: list= ALL, item=alloweduser
from_match: tok=ALL, item=192.168.1.10
string_match: tok=ALL, item=192.168.1.10
from_match=2, "192.168.1.10"
access denied for user `alloweduser' from `192.168.1.10'

```

Notice the line: netgroup_match: 0 (netgroup=UserDev@@SystemDev, machine=NULL, user=alloweduser, domain=)

It isn't correctly interpreting the netgroups as 2 separate groups, but one group named : UserDev@@SystemDev which obviously fails.  This works fine on other non Ubuntu systems I have.  I'm not sure what is different with pam_access.so on this system. Any help is of course appreciated.

Here is a valid session with the same config on a CentOS system.

login_access: user=alloweduser, from=192.168.1.20, file=/etc/security/access.conf
line 1: +  :  root  : ALL
user_match: tok=root, item=alloweduser
string_match: tok=root, item=alloweduser
user_match=0, "alloweduser"
line 2: +  :  @UserDev@@SystemDev  :  ALL
user_match: tok=@UserDev@@SystemDev, item=alloweduser
user_match: tok=@UserDev, item=alloweduser
netgroup_match: 1 (group=UserDev, machine=NULL, user=alloweduser, domain=NULL)
from_match: tok=@SystemDev, item=devsystem2
netgroup_match: 1 (group=SystemDev, machine=devsystem2, user=NULL, domain=NULL)
user_match=1, "alloweduser"
from_match: tok=ALL, item=192.168.1.20
string_match: tok=ALL, item=192.168.1.20
from_match=2, "192.168.1.20"

---

### Post by spoon103 on 2012-08-27
This was fixed in a version of Pam > 1.1.3.

---

### Post by TedSki on 2012-10-17
Any guidance on how to get the fix in 12.04?

---

### Post by antoncheck on 2013-02-26
I am experiencing the same problem on 12.04 running with 1.1.3-7ubuntu2 of the libpam-modules - was there a solution to this?

Thanks

---

