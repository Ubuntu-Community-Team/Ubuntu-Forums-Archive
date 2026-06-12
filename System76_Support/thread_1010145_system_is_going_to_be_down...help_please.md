---
title: "system is going to be down...help please"
date: 2008-12-13
forum: System76 Support
---

### Post by daci007 on 2008-12-13
hello ther..
i have a problem in the file system free space ,it's when i go to System>Admin>System Monitor,in the system info section, i see 
system statue: 200Mb free space,and yesterday was 600MB that's before i installed a some package,what can i do to make more space in the file system,and to make things clear i have about 71GB free in my all hard drive....please help

---

### Post by daci007 on 2008-12-14
please any help....????

---

### Post by MorphWVUtuba on 2008-12-14
I've seen some symptoms like this.  

Can you check to see if process klogd is taking up a lot of your processor?  Also, how big are some of the files under /var/log/?

If you've got that much free space overall, you can resize your partitions using an Ubuntu live (desktop) CD.  It's under the System>>Administration menu.

BACK UP YOUR DATA FIRST!  Low risk, but I'm sure it'd be catastrophic if something did happen. :)

---

### Post by thomasaaron on 2008-12-15
Yes, there is a bug that causes /var/log/syslog and /var/log/messages to get very large very quickly. It doesn't seem to affect everybody, so I've not been able to isolate what causes it. Please keep your computer completely updated, as this is where the fix will ultimately come from. In the mean time, delete your log files with these commands:

sudo rm /var/log syslog

sudo rm /var/log messages

sudo rm /var/log kern.log

Don't worry. They will be re-created when you reboot.

---

### Post by osx424242 on 2008-12-15
Thomas, I think you unintentionally left out some slashes. I think you meant to say:
```
sudo rm /var/log/syslog
sudo rm /var/log/messages
sudo rm /var/log/kern.log
```

---

### Post by thomasaaron on 2008-12-15
Thank you for catching that.

---

