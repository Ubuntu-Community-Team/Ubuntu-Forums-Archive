---
title: "LDAP password reset on ssh connection attempt"
date: 2008-11-05
forum: Server Platforms
---

### Post by lexip on 2008-11-05
Hi there, 
I have a Ubuntu 8.04 LTS server running on LDAP account management. I further have sshd running, but a 

ALLOW_USERS root

statement in my /etc/ssh/sshd_config, because there are a lot of users, and I don't want people to access the server via ssh. 

The problem now is, that if anybody still tries to log in via ssh, their password is automatically changed! This is very anoying, because if some script-kiddy tries to hack the system, they try a lot of users, and will certainly hit one of the existing accounts. This results in a changed password for the corresponding user..

Does this problem sound as a miss-configuration to you, or is it rather a root-kit, or something similar?

Thanks a lot in advance..
Sincerely,
Harald

---

