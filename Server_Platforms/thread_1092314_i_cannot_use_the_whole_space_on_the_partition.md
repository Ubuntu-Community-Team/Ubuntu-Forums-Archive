---
title: "i cannot use the whole space on the partition"
date: 2009-03-10
forum: Server Platforms
---

### Post by ballapaldaniel on 2009-03-10
Hello, 

I have a big problem. I have 2 80 GB SCSI disk. /dev_sda is the /, and the /dev/sdb patitioned on /dev/sdb1 and /dev/sdb2 (as swap) 

The problem, that I cannot use the whole space. Tnhe output of df -ha is is the following: 

             Size     Used    Avail    Use%    Mounted on
/dev/sdb1    69G      30G     36G      46%      /salv

But when I try to create any file on the /dev/sdb1, an error occure : "No space left on device (28)"

Anybody has some ideas what is the problem? 

Thank you in advance

p

---

### Post by pmlxuser on 2009-03-10
do you have the ownership on the partition, try creating a file as Super user. i think during the creation of the partition you have set the wrong setting and as a normal user you don't have writting rights (i think ;D ) correct me if am wrong

---

### Post by ballapaldaniel on 2009-03-10
I tried with different usernames to create a file on the /dev/sdb1, but without change. With sudo also, but nothing with effect. 


Thanks pmlxuser

---

### Post by ballapaldaniel on 2009-03-10
The problem is that are millions of little (index) file. 
With "du --apparent-size -h --summarize" the result is 24G. No savvy. 

Thanks.

---

