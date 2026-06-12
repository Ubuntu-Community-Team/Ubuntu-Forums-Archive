---
title: "pam_cracklib - optimal configuration"
date: 2013-09-13
forum: Security
---

### Post by rollyah on 2013-09-13
i just installed  pam_cracklib 

here's relevant part of my common-password (This file should affect all accounts that authenticate with /etc/shadow or am i mistaken?) :

```
# here are the per-package modules (the "Primary" block)
**password        [success=1 default=ignore]      pam_unix.so obscure sha512**
# here's the fallback if no module succeeds
**password        requisite                       pam_deny.so**
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
**password        required                        pam_permit.so**
# and here are more per-package modules (the "Additional" block)
# end of pam-auth-update config
```

i'd like to accomplish the following:
- A user can try to enter a new password a max of 3 times: ** retry=3**
- Minimum length of new password is 8:  **minlen=8**
- Difference of characters allowed between old and new password is max 4: **difok=4**
- User cannot use the same password as the one used for the past year: **remember=12**  (i already set max password age to 30 in login.defs)
- User must have at least 1 of the following characters: lower/upper case, numerical,special: **lcredit=-1 ucredit=-1 dcredit=-1 ocredit=-1**

I'm fairly confident of the above requirements (if you think there's any reason not to use the above setup, please let me know) 
But i'm confused on how to add the above config into my exiting file. 
i realize that presiding rules take effect, but i'm not confident with the exact order so that's where i'm hoping you could help

 


~

---

