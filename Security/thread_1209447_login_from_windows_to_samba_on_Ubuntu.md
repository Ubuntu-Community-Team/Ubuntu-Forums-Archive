---
title: "login from windows to samba on Ubuntu"
date: 2009-07-10
forum: Security
---

### Post by irv on 2009-07-10
I have samba setup on two of my Ubuntu PC's and I can access the shared folder and transfer file with no problems. But when I wan to access the shared folders in Ubuntu windows keeps asking for a password and no matter what I do it will not let me logon to the shared folders. Am I missing something here? is there a setting in the smb.conf file that needs to be fixed? or is there something in Windows?

Edit: My son just logged on to his WinXP PC on my network, and he can access my shared folders without being asked for a password. Even after shutting off my firewall and restarting my WinXP it still is asking for a password which it does not take. It has to be a setting in Windows if others can access shared folder. I have tried Vista yet, but I am going to do so.

---

### Post by Dr Small on 2009-07-10
```
sudo smbpasswd *username*
```

---

### Post by irv on 2009-07-11
Thanks, that did the trick.

---

