---
title: "Console Login s/b root-level user with no su/sudo"
date: 2014-07-03
forum: Server Platforms
---

### Post by ghughes on 2014-07-03
Good morning, all!

I'm working on a new gold build for Ubuntu 12.04 and 14.04 LTS and I'm running into some problems with console login.

My systems have Centrify Express installed to provide access to Active Directory.  This is where normal user logins go to authenticate against.  These systems also have RSA SecurID PAM module installed, with sshd, sudo and login PAM modified to require or use SecurID tokencodes for authentication.  The PAM configs for sshd and sudo are exclusively SecurID to keep users from authenticating with any other credential source.  Login, however, has local authentication still enabled to allow for a console login to local /etc/passwd authentication.

I've tried to stack PAM with multiple modules and use pam_succeed_if and pam_listfile to separate authentication groups, with no success.  All I really want, anyway, is to lock down remote sshd access, including sudo, to require RSA SecurID.  I want the console login, however, to be a single user with complete root-level access.   However, because of the sudo lockdown, I can't just create a user.  I've also had no luck making the user a member of group wheel - that new user is blocked from root-level operations even if they're in wheel.

I've enable root login to get around this, but would like very much to remove that root access and still be able to have a single console-only login user that has complete and unfettered access in case of emergency.

Any thoughts on how I might achieve this?

Thanks in advance!

Gregg

---

