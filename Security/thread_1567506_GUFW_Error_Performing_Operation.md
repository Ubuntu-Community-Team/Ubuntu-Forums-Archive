---
title: "GUFW: Error Performing Operation"
date: 2010-09-03
forum: Security
---

### Post by rowbird on 2010-09-03
Hi All, I am trying to add a simple rule to GUFW, but am getting an error. I am entering my static IP address from another computer in my home network. I have successfully added similar rules to all my other computers without error. What could be the problem? I don't even have any other rules on this computer. Thanks in advance.

---

### Post by rowbird on 2010-09-04
Update, I am getting Error: Bad Port, and sometimes Error: Bad token

---

### Post by bodhi.zazen on 2010-09-04
Who knows, could be anything.

Post your rule and the exact error message, only then can we provide anything more then :

```
man ufw
```

---

### Post by rowbird on 2010-09-04
I got a workaround! I entered "sudo ufw allow from xxx.xxx.xxx.xx" in the terminal, and it worked. Thanks for the reply.

---

