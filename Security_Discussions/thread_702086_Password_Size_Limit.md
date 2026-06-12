---
title: "Password Size Limit?"
date: 2008-02-19
forum: Security Discussions
---

### Post by Notld224 on 2008-02-19
Now I'm quite serious here. So recently I've been working on my memory. And I've managed to ingrain a fairly long password (40+ characters). Now while I am SURE to enter it correctly into both fields... Ubuntu gives me a password change confirmation error.

Could this be because of a password size limit?

---

### Post by lsmobrian on 2008-02-19
I've never heard of a password limit.  I understand that u are using a long password, but have you thought of using a larger character set (i.e. uppercase,lowercase,numbers,symbols)  and a shorter password

a password length 8 with at least 1 char from each set is pretty much unbreakable by brute force methods

---

### Post by rickyjones on 2008-02-20
> **Notld224 said:**
> Now I'm quite serious here. So recently I've been working on my memory. And I've managed to ingrain a fairly long password (40+ characters). Now while I am SURE to enter it correctly into both fields... Ubuntu gives me a password change confirmation error.

Could this be because of a password size limit?

Check files in /etc/pam.d - specifically the password file - for anything about password lengths.

-Richard

---

### Post by euler_fan on 2008-02-20
I haven't done a comprehensive search of the files in /etc/pam, but this is from /etc/pam.d/common-password:

```
#
# /etc/pam.d/common-password - password-related modules common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of modules that define  the services to be
#used to change user passwords.  The default is pam_unix

# The "nullok" option allows users to change an empty password, else
# empty passwords are treated as locked accounts.
#
# (Add `md5' after the module name to enable MD5 passwords)
#
# The "obscure" option replaces the old `OBSCURE_CHECKS_ENAB' option in
# login.defs. Also the "min" and "max" options enforce the length of the
# new password.

password   required   pam_unix.so nullok obscure min=4 max=8 md5

# Alternate strength checking for password. Note that this
# requires the libpam-cracklib package to be installed.
# You will need to comment out the password line above and
# uncomment the next two in order to use this.
# (Replaces the `OBSCURE_CHECKS_ENAB', `CRACKLIB_DICTPATH')
#
# password required       pam_cracklib.so retry=3 minlen=6 difok=3
# password required       pam_unix.so use_authtok nullok md5

```

If I read right (and this is the default file on Gusty) there a password max of 8 characters. Hmmm . . . I don't like this and will be changing to something longer, like 20.

EDIT: But then I try to start something with gksude (like firestarter) and use only the first eight characters it won't take it. Perhaps its the last eight?

---

### Post by lsmobrian on 2008-02-20
I think i read about this sometime in Jan

The max=8 refers to complexity, after a length of 8 pam stops checking because it assumes a strong password.

---

### Post by wirelessmonkey on 2008-02-20
> **lsmobrian said:**
> I think i read about this sometime in Jan

The max=8 refers to complexity, after a length of 8 pam stops checking because it assumes a strong password.

I believe this is correct.

---

### Post by wirelessmonkey on 2008-02-20
Just for fun, I just tried a 52 char password, and it was valid.

---

