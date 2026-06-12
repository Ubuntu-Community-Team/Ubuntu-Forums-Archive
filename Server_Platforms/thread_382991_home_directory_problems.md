---
title: "home directory problems"
date: 2007-03-12
forum: Server Platforms
---

### Post by fernando_lopes_jr on 2007-03-12
I just made a fresh new install of Ubuntu 6.06 on a pc with 2 hdd, one with 40 gb and other with 300 gb. The 40 gb is for the system and swap files and the 300 gb is intended to store my personal data so i mounted it as /home. When I get samba shares working and start filling up my persinal folder in /home wich should be the 300gb it gets full at about 35gb of data that sugestes the system is using the 40 gb. I don't understand what is wrong since everything should be right can't find anything wrong.

---

### Post by Mr. C. on 2007-03-12
Show the output from the following commands:

```
mount
ls -l /home
df -h /home
```

MrC

---

### Post by fernando_lopes_jr on 2007-03-12
Output:
> 
cda@cda-server:~$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
/dev/hdc1 on /home type ext3 (rw)

cda@cda-server:~$ ls -l /home
total 52
drwxr-xr-x 2 cda  cda   4096 2007-03-12 23:07 cda
drwxr-xr-x 2 root root 49152 2007-03-12 22:53 lost+found

cda@cda-server:~$ df -h /home
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdc1             276G  129M  261G   1% /home

Do you think it was anything to do with my samba shares?

---

### Post by Mr. C. on 2007-03-12
I don't see your output from the mount command.

Your /home has plenty of room.

What is causing you to believe "it gets full at about 35gb" ?  In other words, where are you seeing this error or message, and what exactly is the error ?

MrC

---

### Post by fernando_lopes_jr on 2007-03-12
I have a shared folder that I use as a network drive each time I copy my data to my folder It gets to a point where I can't copy more data because it says the drive is full.

---

### Post by Mr. C. on 2007-03-12
Let's see what folder you are sharing.

Let's see the outout of the mount command

We can't help without sufficient data to see what is wrong.

MrC

---

### Post by gombadi on 2007-03-13
Output from mount command is given above
```

Output:
Quote:
cda@cda-server:~$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
/dev/hdc1 on /home type ext3 (rw)


```

---

### Post by fernando_lopes_jr on 2007-03-14
Problem solved there was a file that each time I tryed to copy over the network rendared a strange error and said the drive was full.

---

### Post by Mr. C. on 2007-03-14
Oh, good.  Seems like an incorrect error message was returned.

Nice detective work!
MrC

---

### Post by fernando_lopes_jr on 2007-03-15
how can I edit the title of the thread to put solved in the title.

---

### Post by Mr. C. on 2007-03-15
Click Edit for the thread, and the Go Advanced.

---

