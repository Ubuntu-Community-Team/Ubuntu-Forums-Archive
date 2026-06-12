---
title: "Upgrade to Server 18.04.4 from terminal"
date: 2020-02-14
forum: Server Platforms
---

### Post by chunkydrew2 on 2020-02-14
My file server is currently running Ubuntu Server 18.04 LTS, with no issues. I see that 18.04.4 has been released. Should I upgrade, since I'm having no issues with the running install? If I should, would I just use **do-dist-upgrade** or **do-release-upgrade** in terminal? Is there any danger in doing this on a running server? Since everything is working, don't want to take any chances. Any advice would be greatly appreciated.

---

### Post by mörgæs on 2020-02-14
You should update (within the 18.04 family) but not upgrade (to a higher release number).

Please run ```
sudo apt update
``` and ```
sudo apt dist-upgrade
```
and post the output in CODE tags. In spite of *upgrade* being part of the command name it's still an operation within the 18.04 family.

You might need a reboot afterwards so plan accordingly if you have users 24/7.

---

### Post by chunkydrew2 on 2020-02-14
Thanks, I upgraded with no issues.

---

### Post by mörgæs on 2020-02-15
Good, just run the two commands with short intervals and your system should be in good shape.

Please mark the thread solved.

---

