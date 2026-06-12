---
title: "SCPonly and hiding system files"
date: 2011-10-25
forum: Server Platforms
---

### Post by Engineer007 on 2011-10-25
Hello All, 

This is my first post, so I hope I am doing this correctly, please

let me know if I am breaking any forum rules or are in the wrong 

category.


 Anyways, I installed SCPonly on my 10.04 64-bit box. It works 

very well and I haven't had any issues. However, I was wondering 

if there was a way to hid the system files from users that are 

chrooted and login to the box using SCP. Specifically when you 

login to the machine there are bin, dev, etc, incoming, lib, 

lib64, and usr directories. I really only want them to see the 

incoming directory since that is what they have access to 

anyways. Even better yet is if they just logged into that 

directory, but either way would work. I've done some searching 

and can't seem to find how to do it, WinSCP throws errors if I 

try to do a usermod -d and also if I try mv file to .file. I'm 

not sure if this is possible, any help would be appreciated.

---

### Post by vasile002 on 2011-10-25
Here's a howto about how to chroot scp users:
[http://ubuntuforums.org/showthread.php?t=128206](http://ubuntuforums.org/showthread.php?t=128206)

I hope it helps.

---

### Post by Engineer007 on 2011-10-25
Thanks, that does help. Since those file are all required for the session of the chroot user the best solution would be to have a process to change their directory right away. That sounds like another post though. 

Thanks for the info.

---

