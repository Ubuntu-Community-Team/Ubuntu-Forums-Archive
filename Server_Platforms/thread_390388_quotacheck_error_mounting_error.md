---
title: "quotacheck error mounting error"
date: 2007-03-21
forum: Server Platforms
---

### Post by icarius on 2007-03-21
I am trying to configure Ubuntu server on my machine and I keep getting a mounting error. I have been following the [http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p4](http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p4) tutorial and after entering in 
 
touch /quota.user /quota.group
chmod 600 /quota.*
mount -o remount /
quotacheck -avugm 

I get 

quotacheck: Can't find filesystem to check or filesystem not option.

I also have added 

/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0 

to /etc/fstab 

Can anyone PLEASE help???

---

### Post by wonk-o-matic on 2007-03-21
Try it with -acguvm.  The 'c' option is probably all you need.

---

### Post by icarius on 2007-03-21
I still get the same error using -acguvm,any other suggestions?

---

