---
title: "sshfs access problems"
date: 2006-04-24
forum: Server Platforms
---

### Post by donbing on 2006-04-24
Hi, like many here i'm fairly new to linux. ubuntu seemed like a good starting point so i'm currently running it as a virtual machine... (i like BF2 too much to go all out linux just yet)

after following the how-to on this forum i managed to get my university homespace mounted locally using sshfs. 

a day later (an maybe a reboot or 2) and it's now giving me the following error:

```
ld.so.1: sftp-server: fatal: libncurses.so.5: open failed: No such file or directory
end of file read
```

i can mount my local win2003 servers ssh connection ok. so i'm guessing something may have changed at the servers end?

any suggestions greatly appreciated...  I dont think i can face going back to windows+putty to edit my scripts.

---

### Post by donbing on 2006-04-25
after some frustration it appears that it was the server throwing the error message, not my ubuntu install...

the server gives the same error if i try to ssh to another computer from it. seems a bit odd to me as i can happily ssh into a shell on it.

hey ho. now to try and get eclipse working..

---

### Post by imagine on 2006-04-25
The SSH daemon uses a subserver called sftp for file exchange. Seems as this is broken.

---

