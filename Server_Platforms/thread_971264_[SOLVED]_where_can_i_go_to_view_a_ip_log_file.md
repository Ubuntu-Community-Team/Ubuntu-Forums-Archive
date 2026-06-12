---
title: "[SOLVED] where can i go to view a ip log file"
date: 2008-11-04
forum: Server Platforms
---

### Post by Fertech on 2008-11-04
I'm running my Ubuntu as a server. I just wanted to know where can i do to view the ip address log files, if anyone has any information please let me know.

---

### Post by hrod beraht on 2008-11-04
What kind of server? Apache web server? If so, look in **/var/log/apache2/**

Bob

---

### Post by cariboo on 2008-11-05
If you are running openssh-server then at the prompt:

```
cat /var/log/auth.log | grep ssh
```

Jim

---

### Post by Fertech on 2008-11-05
i found it. it was here>>> /var/log/apache2/

---

