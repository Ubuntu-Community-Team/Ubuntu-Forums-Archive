---
title: "ubuntu 9.10 ext4 disk manage quota"
date: 2010-11-01
forum: Security
---

### Post by bonomartin on 2010-11-01
Hello,
i am trying to manage disc quotas on ubuntu 9.10 with ext4 fs

here but i have one problem when i get here i got this problem 

# quotacheck -avugm
quotacheck: WARNING -  Quotafile /home/aquota.user was probably truncated. Cannot save quota settings...
quotacheck: WARNING -  Quotafile /home/aquota.group was probably truncated. Cannot save quota settings...
quotacheck: Scanning /dev/sda2 [/home] quotacheck: lstat Cannot stat `/home/hdtdi/.gvfs': Permission denied
Guess you'd better run fsck first !
exiting...

then : 
#init 1 and fsck -C -f -v /dev/sda6 (thats my /home fs)
i dont really know what is it for but there were no errors or stuff like that.. but the problem is still there..

Thank you for help me...

Bono

---

### Post by psusi on 2010-11-01
It is getting confused because of that damn broken gvfs.  Run sudo umount /home/hdtdi/.gvfs and try again.

---

### Post by bonomartin on 2010-11-01
Thank you it works!
I will try to understand that damn broken gvfs...
I've been searching for two days! Thank you very much!:)

---

