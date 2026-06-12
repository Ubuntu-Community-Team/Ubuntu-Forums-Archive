---
title: "(ldap) passwd: Authentication information cannot be recovered"
date: 2010-12-07
forum: Server Platforms
---

### Post by vrillusions on 2010-12-07
We use ldap for authentication and have been for several years now.  On new installs (10.04) and using the ldap-auth-client and related packages.  Logins using the new system have worked fine but when trying to change a password it won't work.

```
$ passwd
Enter login(LDAP) password: 
passwd: Authentication information cannot be recovered
passwd: password unchanged
```

And in /var/log/auth.log (hotname and username have been masked):
```
Dec  7 09:41:14 HOSTNAME passwd[5238]: pam_unix(passwd:chauthtok): user "USERNAME" does not exist in /etc/passwd
```

Running 'getent passwd' works as expected, returning passwd lines for all ldap users.  On servers I upgraded to 10.04 from 8.04 they still used a more manual setup and I can change passwords from those servers fine.

(edit)Didn't see the "mark as solved" option in menu

---

### Post by windependence on 2010-12-07
What is the content of your /etc/pam.d/common-password file?
 
-Tim

---

### Post by vrillusions on 2010-12-08
```
#
# /etc/pam.d/common-password - password-related modules common to all services
# -- removed comment header talking about various options --

# here are the per-package modules (the "Primary" block)
password	[success=2 default=ignore]	pam_unix.so obscure sha512
password	[success=1 user_unknown=ignore default=die]	pam_ldap.so use_authtok try_first_pass
# here's the fallback if no module succeeds
password	requisite			pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
password	required			pam_permit.so
# and here are more per-package modules (the "Additional" block)
password	optional	pam_gnome_keyring.so 
# end of pam-auth-update config
```

---

### Post by windependence on 2010-12-08
Try removing the use_authtok parameter and save the file. You may need to restart.
 
-Tim

---

### Post by vrillusions on 2010-12-08
Thanks, that fixed it.  Next question, how do I setup pam-auth-config so it knows not to include that?  I'll probably end up going back to modifying the files by hand, which won't be too bad if I ever get things automated.  Thanks for you help.

---

