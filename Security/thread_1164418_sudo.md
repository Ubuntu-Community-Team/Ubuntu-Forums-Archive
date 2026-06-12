---
title: "sudo"
date: 2009-05-19
forum: Security
---

### Post by Find on 2009-05-19
Hi,

If i enter my pass once, for example in sudo apt-get ..., then in the next line i have anothe sudo apt-get ..., usually ubuntu does not ask me the pass for the second time?!

---

### Post by koenn on 2009-05-19
yes, that's correct.

---

### Post by Z0014ND3l2 on 2009-05-19
Because Linux is smart like that ;D

---

### Post by sisco311 on 2009-05-19
By default sudo remembers your password for 5 (or 10?) minutes.
You can change the timeout in the sudoers file.

[uhelp]community/RootSudo[/uhelp]

EDIT: [uhelp]community/RootSudoTimeout[/uhelp]

---

### Post by scorp123 on 2009-05-19
> **Find said:**
> usually ubuntu does not ask me the pass for the second time?! there is a cache and a timeout. For as long as you don't hit the timeout it will not ask for the "sudo" password again. This is normal.

---

### Post by bodhi.zazen on 2009-05-19
If you do not want to change the default, use :

```
sudo -k
```

when you are done with your sys admin tasks.

This way you still have the convenience.

---

