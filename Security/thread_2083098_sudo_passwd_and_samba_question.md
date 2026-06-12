---
title: "sudo passwd and samba question"
date: 2012-11-11
forum: Security
---

### Post by broecher on 2012-11-11
I was setting up my home samba server and I was trying to change my user password. Since my server is also open to the internet (www and ssh) I wanted to make sure to set a very strong password right away.

I am not sure if this is a problem, but when trying to change the password I typed sudo passwd and changed the password. Then I tried to log on it still only accepted the old password. I realized I should have just typed passwd. So I would like to know if I should do anything to fix the password I changed when I entered sudo passwd.

Also in my smb.conf I have the following. This protects the samba server from the internet, correct? It is set to allow write access to all without login (security = share).

```
interfaces = lo eth0
bind interfaces only = true
```

---

### Post by broecher on 2012-11-11
Found the answer to my first question:

[https://help.ubuntu.com/community/RootSudo#root_account](https://help.ubuntu.com/community/RootSudo#root_account)

```
sudo passwd -dl root
```

Still wondering if my samba is safe.

---

