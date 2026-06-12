---
title: "nm command not found"
date: 2010-03-09
forum: Server Platforms
---

### Post by gdecoster on 2010-03-09
Running Ubuntu 9.10 64bit server. Installed it as a minimal virtual machine. The 'nm' command does not exist in /usr/bin. Assuming this is because the nm command is not included in a minimal install.
How can I install the nm command ?

---

### Post by x33a on 2010-03-09
try
```
sudo apt-get install binutils
```

---

### Post by gdecoster on 2010-03-09
Thanks for the quick turnaraound.
Installing binutils solved my problem.

---

