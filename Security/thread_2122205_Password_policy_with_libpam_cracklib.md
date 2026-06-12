---
title: "Password policy with libpam cracklib"
date: 2013-03-04
forum: Security
---

### Post by lundgren_o on 2013-03-04
```
sudo apt-get install libpam-cracklib
```

I am not getting cracklib password complexity to work on my system. This is what my settings look like in /etc/pam.d/common-password
```
# here are the per-package modules (the "Primary" block)
password        required        pam_cracklib.so retry=3 minlen=10 difok=3 dcredit=1 ucredit=1 lcredit=1 ocredit=1
password        required        pam_unix.so obscure try_first_pass sha512 use_authtok
#next line is default
#password       [success=1 default=ignore]      pam_unix.so obscure try_first_pass sha512 use_authtok
# here's the fallback if no module succeeds
password        requisite                       pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
password        required                        pam_permit.so
# and here are more per-package modules (the "Additional" block)
# end of pam-auth-update config

```

I saved file and tried to change file with a regular user. It still accepts 6 lowercase char passwords. Im trying to read the man pages, but Im not sure I understand them really. And there aren't so many good guides on the net. Does cracklib-check use my common-password settings?
I tried commenting out pam_unix.so line, tried to play with different values in the cracklib.so line, but nothing seems to change, and get it working. Im running Ubuntu 10.04.4 LTS.

---

### Post by CharlesA on 2013-03-06
This probably won't help, but have you read this?
[http://www.cyberciti.biz/tips/linux-check-passwords-against-a-dictionary-attack.html](http://www.cyberciti.biz/tips/linux-check-passwords-against-a-dictionary-attack.html)

---

