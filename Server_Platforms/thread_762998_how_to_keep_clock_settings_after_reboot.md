---
title: "how to keep clock settings after reboot"
date: 2008-04-22
forum: Server Platforms
---

### Post by nephish on 2008-04-22
hello all, 
i have adjusted my clock with the command
```
date -s 12:12
```

now, if i reboot, that clock setting will go away. (this is one hour ahead of what the hw clock is) 
how do i make linux remember this setting? Or if i need to change the hardware clock, how do i know if it is on local or ut time?
thanks for any tips

---

### Post by Wim Sturkenboom on 2008-04-23
> 
how do i know if it is on local or ut time

Go into the BIOS and check what the date is set to.

> 
how do i make linux remember this setting

Can't you use the 'normal' way? Example below sets the date to the 22nd of april 13H55; on my slackbox, it remembers it.
```

date 04221355

```

---

### Post by bluefrog on 2008-04-23
date will show the time AND the time zone

date
Wed Apr 23 11:53:05 CEST 2008

date -u
Wed Apr 23 09:53:10 UTC 2008

hwclock
Wed 23 Apr 2008 11:53:31 AM CEST  -0.002611 seconds

If you adjusted the time with administrative rights, then the time should have been kept. Now at install time, the installer asked you what your hardware clock was using, local time or UTC.

if you don't remember and want your hardware clock to use UTC then issue

hwclock --utc

(beware hwclock will still display something like Wed 23 Apr 2008 11:53:31 AM CEST  -0.002611 seconds)

if you want your hardware clock to use local time then issue 
hwclock --localtime

set the date afterwards. It will be kept on reboot (if you set the date with administrative rights of course).

If you are not in the correct time zone then dpkg-reconfigure tzdata.

James Dupin

---

### Post by erginemr on 2008-04-23
Please refer to this discussion and see if there is anything there that you can try:
*[http://ubuntuforums.org/showthread.php?p=4635329](http://ubuntuforums.org/showthread.php?p=4635329)*

---

### Post by nephish on 2008-04-23
ok, thanks for the tips and info, gents.

---

