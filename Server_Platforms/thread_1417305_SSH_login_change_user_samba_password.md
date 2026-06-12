---
title: "SSH login change user samba password"
date: 2010-02-27
forum: Server Platforms
---

### Post by Frunktz on 2010-02-27
Hi!
I've a Ubuntu Server with Karmic 9.10.
On a fresh installation I have this problem, each SSH login with a user ("foo") change my samba password of that user, with the password of "foo" UNIX username (pass is "bar")

Example:
UNIX User Account: "foo" Pass: "bar"
Samba User account: "foo" Pass: "foobar"

When I login in SSH with user foo, the situation belong:
UNIX User Account: "foo" Pass: "bar"
Samba User account: "foo" Pass: "bar"

Obviouly this is a problem when I use samba share on other machine, I must change manually samba password with smbpasswd and restore it to "foobar"..

In smb.conf I try to enable/disable "unix password sync", "obey pam restriction", ecc, but the situation remain the same...

Why??

Thanks a lot

Ps:- Sorry for my worst English

---

### Post by othin on 2012-04-23
Greetings!

I had similar problem. 

User db is on LDAP. After/during ssh login, though it was successful, i got "Failed to add entry for user xxx." message for all local users. 
For users with ldap entry there was no such message but the password was updated (sambaPwdLastSet field changed). 

To avoid this, the pam-auth-update feature must be disabled. 

Edit the /etc/pam.d/common-auth file
There is a 
```
auth   optional                        pam_smbpass.so migrate

```line. The "migrate" word is to be removed. 
```
#auth   optional                        pam_smbpass.so migrate
auth   optional                        pam_smbpass.so

```
Requires no restart of anything, works immediately. 

Cheers!

---

