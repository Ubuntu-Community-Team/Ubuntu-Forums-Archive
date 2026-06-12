---
title: "How do I edit conf files??"
date: 2009-12-02
forum: Server Platforms
---

### Post by shawyn on 2009-12-02
ok, I'm new to ubuntu or anything linux, but my expirience with Windows has prepared me to learn if nothing else. I am  trying to edit the samba smb.conf file, ummmm how the heck do u edit it? I have tried nano /etc/samba/smb.conf , and I can change the files as needed, but when I go to save or write it out,  it gives me:
  [ Error writing /etc/samba/smb.conf: Permission denied ]
So where do i go from here? I have freshly installed 8.10 (this is a trial run on an old pc to get used to it, but will upgrade to 9.10 or most current version/new hardware as soon as I am confident I can configure it comfortably) The samba server and openSSH were the only things checked on the install, and I am the only user set up on it. Thanks for your help in advance!

---

### Post by wojox on 2009-12-02
Try;

```
sudo nano /etc/samba/smb.conf
```

Then you will have root privileges to save it.

---

### Post by shawyn on 2009-12-02
OMG it works, thank you! Is there a more preferred editor, or am I on the right track?

---

### Post by wojox on 2009-12-02
nano is the easiest I've found. On the Cli.

---

### Post by Vegan on 2009-12-02
nano is fine, its easy to use, but very crude.

---

### Post by lisati on 2009-12-02
On the rare occasions I've edited conf files, I've used gedit.

---

