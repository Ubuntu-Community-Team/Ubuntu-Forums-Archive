---
title: "Help with groups"
date: 2008-06-04
forum: Security
---

### Post by skipsbro on 2008-06-04
Yes, its me again, and I seem to have locked myself out of administrator privileges on my computer. After installing the program VirtualBox OSE on my Ubuntu 8.04 computer, it prompted me to change the group my user was in. I followed it's instructions without thinking and I am now unable to do anything that requires admin powers or a "sudo" command. I have also never enabled the root user. Is there anything I can do?

---

### Post by Dr Small on 2008-06-04
Apparently you have been taken out of the 'admin' group. Simply reboot into Recovery Mode and then type at the prompt:
```
usermod -G admin *username*
```

---

