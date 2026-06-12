---
title: "Lost in common-password PAM configuration"
date: 2010-09-08
forum: Security
---

### Post by luvshines on 2010-09-08
Recently installed some application which screwed the default common-passwd file and has put some restrictions on the passwords which I could set

The present file looks like this
```
#password required  pam_passwdqc.so min=disabled,8,8,8,8 passphrase=0 enforce=users
password  required  pam_passwdqc.so min=1,0,0,0,0 passphrase=0 enforce=none random=0
#password sufficient  pam_unix.so remember=8 nullok_secure use_authtok sha512 shadow
password  sufficient  pam_unix.so remember=0 nullok_secure use_authtok sha512 shadow
password  [success=2 default=ignore]  pam_unix.so obscure use_authtok try_first_pass sha512
password  [success=1 default=ignore]  pam_winbind.so use_authtok try_first_pass
# here's the fallback if no module succeeds
password  requisite     pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
password  required      pam_permit.so
# and here are more per-package modules (the "Additional" block)
password  optional  pam_gnome_keyring.so
password  optional  pam_ecryptfs.so
# end of pam-auth-update config
```

I tried to change some restrictions (as seen in first 2 lines) but I am still unable to remove the restrictions
Basically, I need to allow any kind of password(even a single character) and remove any restrictions but 'passwd' command complains of 'length' all the time

Tried removing the 'obscure' keyword as well but didn't help
Since it's a test system which is purely on private IP and get's re-OS'ed every other day, I don't have any issues with a single character password. Moreover, it helps in writing test script :)

---

### Post by Bachstelze on 2010-09-09
Commenting line 2 will revert to the original configuration. Otherwise, check the documentatin of the module to find out what the parameters mean.

---

