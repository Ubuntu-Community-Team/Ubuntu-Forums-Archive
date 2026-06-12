---
title: "Antivirus guy runs WannaCry on Linux using Wine"
date: 2017-05-17
forum: Ubuntu, Linux and OS Chat
---

### Post by dark. on 2017-05-17
[https://www.youtube.com/watch?v=TErrIvyj_lU](https://www.youtube.com/watch?v=TErrIvyj_lU)

He manages to encrypt files in /home using windows ransomware, not good for anyone using Wine.
I hope Wine developers patch this soon by completely sandboxing windows stuff from Linux so windows malwares or ransomwares wont even know /home exist.

PS. Ignore antivirus guy rant, he has never used Linux before.

---

### Post by TheFu on 2017-05-18
Linux isn't immune.  Windows people often use Linux-based storage and NAS, devices.  If Windows can see it, and gets infected, then the Linux storage is at risk.  Assuming a mounted file system or CIFS shares are network browsable.

I've never heard of a Windows virus using sftp, scp, or sshfs, however.  So, be certain to use something based on those for your backups, not normal Windows network shares (like samba provides).

---

### Post by montag dp on 2017-05-19
> **dark. said:**
> I hope Wine developers patch this soon by completely sandboxing windows stuff from Linux so windows malwares or ransomwares wont even know /home exist.That would be extremely inconvenient. There's a good reason why wine programs are normally able to access stuff on $HOME, and that's because that's where people keep their documents, not in some hidden wineprefix.

---

### Post by ChuangTzu on 2017-05-20
this is a very good example of why its better to sandbox Windows in a virtual machine rather then using wine.  Also, don't allow Windows VM to share folders or files.  If you must transfer back and forth do so via USB stick and scan it thoroughly before the switch.

---

### Post by dark. on 2017-05-22
Apparently wannacry was able to encrypt files in Pictures, Documents, Desktop, etc. because Wine links to these folders in /home.

~/.wine/drive_c/users/$USER

---

