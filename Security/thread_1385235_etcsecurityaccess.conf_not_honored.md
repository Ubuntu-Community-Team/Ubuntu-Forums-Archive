---
title: "/etc/security/access.conf not honored"
date: 2010-01-19
forum: Security
---

### Post by itmozart on 2010-01-19
I've setup the access rules (actually only one) in /etc/security/access.conf, adding:

```
- : ALL EXCEPT user1 user2 : ALL
```

in /etc/pam.d/login, I added the line:

```
account  required       pam_access.so
```

which works on the servers, except one, where user3, which has the ssh keys properly set, can login, even if he shouldn't.

I read around that there's nothing to restart, so how is it possible?

thanks!
saverio

---

### Post by OurToaster on 2011-09-13
Hi,

I also had a problem with access.conf and netgroups via LDAP. Even if my problem was not related to ssh keys, I suppose people will land here, if they google for it (as I did).
In my case it was a stupid mistake. Perhaps someone is facing the same thing so here is my description:

(running Ubuntu 10.4)
in /etc/pam.d/login and in /etc/pam.d/sshd I uncommented the line 
account  required     pam_access.so 
and also put "debug" behind this line. This pointed me to the right solution. The line then looked like this:
```
account  required     pam_access.so debug
```in /etc/security/access.conf I had the following lines:
```
+ : testuser : ALL
+ : @test_netgroup : ALL
- : ALL : ALL
```So that only testuser and members of the test_netgroup could login. This worked for users not mentioned within any netgroup. For local users it worked perfectly. 
```
getent netgroup test_netgroup
``` also returned the correct values.

In LDAP the entry for nisNetgroupTriple looked like this:  ```
(-,netgroupUser,-)
``` like we had the entry before in the yp netgroup file. 

Following the log in /var/log/auth.log I could (now with debug enabled) see, that pam obtained the correct netgroup entry from the ldap but compared it to ```
(,netgroupUser,)
```. Mind the missing dashes! This was the problem. On another client I still had the old nisdomain name set in /etc/defaultdomain so that this was honored and the match failed.

The debug option turned on in /etc/pam.d/login and sshd is very useful. I was not able to find something on the web for this, which is reasonable, as it is just a stupid mistake but with big consequences :-)

---

