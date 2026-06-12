---
title: "Possible security problems with bacula."
date: 2010-04-01
forum: Security
---

### Post by ivze on 2010-04-01
Good time of day!

Recently I was experimenting bacula on ubuntu 10.04. After apt-get installing it on two separate computers I noticed that password in bacula-dir.conf in section ```
Director {...}
``` was equal to  ```
"Ui3dLcjKWiR6QIyTu+PjPK6wHlziIf7fZlSiCgiZZ3jq"
```  on both machines. Other passwords, used for authentication between different bacula components, were different.

Can anyone confirm this, please?
Any ideas about what I have done wrong?

Waiting for responce.

---

