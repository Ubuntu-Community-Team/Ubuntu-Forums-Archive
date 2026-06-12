---
title: "seahorse question"
date: 2008-12-02
forum: Security
---

### Post by albandy on 2008-12-02
I wish to know if it's possible to change the keyring password by command line instead of using the seahorse gtk client.

I'm using ldap authentication and I want to change the ldap password and the keyring password through a bash script to avoid changing it in ldap and keyring separately.

Thanks in advance.

---

### Post by tubbygweilo on 2008-12-02
```
Applications > Accessories > Terminal seahorse --help-all
``` is the best I can find but I fear that you may be looking for a bit more.

---

### Post by albandy on 2008-12-02
I know that command. I need all the command line options to know how to manage it by command line.

Thanks for your answer but this is not what I need.

---

### Post by cariboo on 2008-12-02
Seahorse is only a gui frontend for Gnupg. Check the documentaion available in gnupg-doc. Gnupg-doc is available in the repositories. Also check: 

```
man gpg
```

and 

```
man pgpv
```

Jim

---

### Post by albandy on 2008-12-04
Thanks, but seems that login.keyring is not a pgp crypted file:

command-line$ file login.keyring

login.keyring: GNOME keyring, major version 0, minor version 0, crypto type 0 (AEL), hash type 0 (MD5), name "login", last modified Wed Nov 19 18:56:20 2008, created Wed Nov 19 18:56:20 2008, not locked if idle, hash iterations 1188, salt 1331446290787132954, 1 item(s)

So I think I should look for info about AEL crypted files.  If I find a solution I will post it here.

---

