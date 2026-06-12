---
title: "vsftpd password incorrect"
date: 2013-07-06
forum: Server Platforms
---

### Post by Snitz on 2013-07-06
I just installed vsftpd on my vps, I setup a root folder and added a user. But whenever I connect I get login password incorrect.

I changed the password many times but that did not help 
```
sudo passwd myusername
```

I also checked if my username is present in /etc/passwd and it's there.

I restarted both vsftpd and the machine. Nothing works.

---

### Post by basicfreak on 2013-07-07
Can I see your vsftpd.conf
```
cat /etc/vsftpd.conf
```

---

