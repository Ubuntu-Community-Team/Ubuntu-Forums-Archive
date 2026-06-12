---
title: "ubuntu 9.10 ext4 disk manage quota"
date: 2009-12-08
forum: Security
---

### Post by SocialEvil on 2009-12-08
EDIT : NEVER MIND I SOLVED THE PROBLEM
Hello,
i am trying to manage disc quotas on ubuntu 9.10 with ext4 fs

i am reading from [http://www.howtoforge.com/how-to-set-up-journaled-quota-on-debian-lenny ]("http://www.howtoforge.com/how-to-set-up-journaled-quota-on-debian-lenny")
here but i have one problem when i get here i got this problem 

root@SocialEvil:/home# quotacheck -avugm
quotacheck: WARNING -  Quotafile /home/aquota.user was probably truncated. Cannot save quota settings...
quotacheck: WARNING -  Quotafile /home/aquota.group was probably truncated. Cannot save quota settings...
quotacheck: Scanning /dev/sda6 [/home] quotacheck: lstat Cannot stat `/home/hdtdi/.gvfs': Permission denied
Guess you'd better run fsck first !
exiting...

then : #init 1 and fsck -C -f -v /dev/sda6 (thats my /home fs)
i dont really know what is it for but there were no errors or stuff like that.. but the problem is still there..

---

### Post by Gi0tis on 2009-12-17
Any chance posting the solution?

---

### Post by ygoe on 2010-07-18
No, the poster was a Social Evil...

Anyway I have the same problem with 10.4. Does anybody else maybe know the solution? Like this, quota cannot be enabled for a user that already has files in the filesystem that root may not be able to read, like commonly in a user's home.

---

### Post by cariboo on 2010-07-18
This thread is over a year old, If you want answers to your question, please start a new thread, as this one is closed.

---

