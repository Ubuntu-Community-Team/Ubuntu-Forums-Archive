---
title: "the problem of seamlessrdp"
date: 2011-09-20
forum: Virtualisation
---

### Post by solrj on 2011-09-20
when I run the command on ubuntu 10.10 ```
rdesktop -A -s "c:\seamlessrdp\seamlessrdpshell.exe " <IP of VM>:3389 -u administrator -p password
``` It can work well.however when I run the command &#65306;```
rdesktop -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Program Files\Internet Explorer\iexplore.exe" <IP of VM>:3389 -u administrator -p password
``` 
It can't work well.It just login the XP VM.but can't call the IE .
thanks for any help&#65281;

---

### Post by CharlesA on 2011-09-20
There is a space in the path.

---

### Post by solrj on 2011-09-20
> **CharlesA said:**
> There is a space in the path.
Thanks CharlesA. However I reference  this  documents .[https://help.ubuntu.com/community/SeamlessVirtualization](https://help.ubuntu.com/community/SeamlessVirtualization) .

---

### Post by CharlesA on 2011-09-20
> **solrj said:**
> Thanks CharlesA. However I reference  this  documents .[https://help.ubuntu.com/community/SeamlessVirtualization](https://help.ubuntu.com/community/SeamlessVirtualization) .
Hmm, can you run something like notepad, that doesn't have a space in the path?

---

### Post by solrj on 2011-09-20
> **CharlesA said:**
> Hmm, can you run something like notepad, that doesn't have a space in the path?
It can't .but when I log out .It works.
I don't know why.

---

