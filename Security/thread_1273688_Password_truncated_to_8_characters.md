---
title: "Password truncated to 8 characters"
date: 2009-09-23
forum: Security
---

### Post by poctob on 2009-09-23
I just noted that Ubuntu 9.04 truncates my password to 8 characters.  Here is an example, if my password is 12345ABCDE I can login into the system only using 12345ABC.  I don't think that I've ever seen this issue before.  I have my password rules configure through pam here is my /etc/pam.d/common-password

password required	  pam_cracklib.so retry=3 minlen=15 difok=3 lcredit=2 ucredit=2 dcredit=2 ocredit=2

I understand that this configuration only deals with password policy enforcement, does anyone know if there is a system wide configuration that will not truncate the password?

Thanks in advance.

---

### Post by cdenley on 2009-09-24
It sounds like your reverted back to using DES encryption, which is very weak, and can only use the first 8 characters of a password if I remember correctly? The default PAM configuration uses SHA-512. Before 8.10, md5 was used. Neither have such a limitation, as far as I know. Fix your pam configuration, then reset any DES passwords.

My common-password, which I believe is default, without comments.
```

password	[success=2 default=ignore]	pam_unix.so sha512
password	[success=1 user_unknown=ignore default=die]	pam_ldap.so use_authtok try_first_pass
password	requisite			pam_deny.so
password	required			pam_permit.so
password	optional			pam_smbpass.so nullok use_authtok use_first_pass

```

This command should show you any users with DES password hashes.
```

sudo getent shadow|cut -d : -f 1,2|grep ":[^\$\*\!]"|cut -d : -f 1

```

---

