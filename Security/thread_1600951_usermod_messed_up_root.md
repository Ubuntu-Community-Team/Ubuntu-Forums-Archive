---
title: "usermod messed up root?"
date: 2010-10-19
forum: Security
---

### Post by BigRedButton on 2010-10-19
I installed Intrepid on my netbook a few months ago, and since I'm the only one who uses it I decided to set it to log me in automatically.  Unfortunately, I recently realized that for whatever reason, even if I disable screen lock in configuration editor, it still wants my password (which I can't remember for the life of me).  To solve this problem, i ran
```
sudo usermod acidicninja --password <new password>
```Two problems: the new password doesn't log me in, and my root password no longer unlocks root! I'm in deep trouble... is there any way to reset the root password without reinstalling?

---

### Post by sisco311 on 2010-10-19
EDIT:
Boot into recovery mode and reset your password:
[http://psychocats.net/ubuntu/resetpassword](http://psychocats.net/ubuntu/resetpassword)

---

