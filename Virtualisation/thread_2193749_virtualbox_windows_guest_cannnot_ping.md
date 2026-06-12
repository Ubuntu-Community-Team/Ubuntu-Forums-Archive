---
title: "virtualbox windows guest cannnot ping"
date: 2013-12-14
forum: Virtualisation
---

### Post by noworldorder on 2013-12-14
I am running Ubuntu 13.04 with windows 7 as a guest in virtualbox.  I want to share folders but I can't.  Windows cannot find the folder on Ubuntu and when I ping Ubuntu I get nothing.  I am guessing it is a firewall in windows but don't know hw to resolve that.  Thanks

---

### Post by Toz on 2013-12-14
First, make sure you have guest additions installed in your Windows 7 guest VM.

Secondly, from the Ubuntu Virtualbox Window 7 Window, create a shared folder where:
- Folder Path = the path to the Ubuntu folder that you want to share
- Folder Name = a one word name for this share
- check the "Make Permanent" checkbox

Thirdly, from within the Windows 7 guest, "Map a Network Drive" to:
```
\\vboxsvr\SHARE
```
...where **SHARE** is the Folder Name you specified above.

A similar thread found [here]("http://ubuntuforums.org/showthread.php?t=2193218").

---

### Post by noworldorder on 2013-12-14
Thanks but I did all htat and giet this message "windows cannot access \\vboxsvr\home\chris"

---

### Post by CharlesA on 2013-12-14
> **noworldorder said:**
> Thanks but I did all htat and giet this message "windows cannot access \\vboxsvr\home\chris"

You would need to access it by going to \\vboxsvr\sharename, not by using the full path.

---

### Post by noworldorder on 2013-12-14
that was simple. Thanks!

---

