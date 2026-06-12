---
title: "No password hashes found (John the ripper)"
date: 2011-12-30
forum: Security
---

### Post by slashwannabe94 on 2011-12-30
Hello all, 

I've installed "JTR" and have created an original UNIX passwd file using ```
sudo unshadow /etc/passwd /etc/shadow > passwd_shadow
```I then added my password to the /usr/share/john/password.lst file and ran this command. 

```
john -w=/usr/share/john/password.lst -rules passwd_shadow
``` and received this output
```
No password hashes loaded
```

Is there something i am doing wrong?

---

### Post by c2ypt1c on 2012-01-04
> **slashwannabe94 said:**
> ```
No password hashes loaded
```Is there something i am doing wrong?
You are probably using an unpatched version of jtr. Since linux uses the SHA hashing algorithm, you need to apply a patch that supports this. Alternatively, you can download/install the community-enhanced version, which should come with the patch already applied.

---

