---
title: "How can I read the boot log?"
date: 2010-11-02
forum: Server Platforms
---

### Post by marquinos on 2010-11-02
Hi! I can't read the boot log In Ubuntu Server 10.10. I did this:
```
BOOTLOGD_ENABLE=yes in /etc/default/bootlogd
```But the file /var/log/boot is empty: 
```
cat /var/log/boot
(Nothing has been logged yet.)
```Thanks in advance!

---

### Post by cipherboy_loc on 2010-11-02
Open up a terminal. Type in:

```
dmesg
```

You might want to pipe it through less with:
```
dmesg | less
```

This is because dmesg output tends to be long...



Cipherboy

---

### Post by marquinos on 2010-11-02
@[cipherboy_loc]("http://ubuntuforums.org/member.php?u=1066963") Thanks!
But how can I know what messages are from boot? Are all from boot?
I want the messages that I see in the boot :)
Thanks very much!

---

### Post by brookie on 2010-11-08
hey marquinos,

don't know if you figured this one out yet but after enabling bootlogd, i had the same problem, until i looked and found /var/log/boot.log. 

so, all the bootup messages are being logged to /var/log/boot.log not /var/log/boot, so now how to get boot.log into System>Administration>Log File Viewer?

cheers,
brook

---

### Post by brookie on 2010-11-09
System>Administration>Log File Viewer, File>Open>boot.log
done
sweet! ;)

---

