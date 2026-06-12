---
title: "Can't edit /etc/resolv.conf file as root"
date: 2010-06-14
forum: Server Platforms
---

### Post by azmiuzun on 2010-06-14
i can't edit /etc/resolv.conf with root account (Ubuntu Server 8.02)

root@webserver:~# sudo vim /etc/resolv.conf

"/etc/resolv.conf"
"/etc/resolv.conf" E212: Can't open file for writing

root@webserver:~# ls -l /etc/resolv.conf
-rw-r--r-- 1 root root 287 2010-06-14 15:20 /etc/resolv.conf

---

### Post by _Mark_ on 2010-06-14
Try without sudo as you are logged on as root is not needed, dunno if this is the problem but worth a try

---

### Post by azmiuzun on 2010-06-14
nothing changed..

root@webserver:~# vim /etc/resolv.conf
nameserver 194.0.0x.0x
nameserver 10.60.5x.3x
~
W10: Warning: Changing a readonly file

:wq!
"/etc/resolv.conf" E212: Can't open file for writing

---

### Post by surfer on 2010-06-14
is your filesystem mounted readonly?

---

### Post by Bachstelze on 2010-06-14
That's weird. Is it on a read-only file system, by any chance?

---

### Post by CharlesA on 2010-06-14
Sounds like it's mounted readonly for some reason.

Check the output of this:

```
mount
```

---

### Post by azmiuzun on 2010-06-14
root@webserver:~# mount
/dev/mapper/webserver-Root on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/sda1 on /boot type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)

---

### Post by CharlesA on 2010-06-14
That looks fine, I'd suggest running fsck on it from a livecd if you can. Just to make sure there are no problems.

---

### Post by doas777 on 2010-06-14
it's conceivable that the file is locked by another process (network-manager mabye?).

---

### Post by arrrghhh on 2010-06-14
> **doas777 said:**
> it's conceivable that the file is locked by another process (network-manager mabye?).

I'd hope that wouldn't be running on a server...


Can you do an lsof and grep for that file?  See if it is indeed in use?

---

### Post by azmiuzun on 2010-06-15
root@webserver:/# lsof /etc/resolv.conf
root@webserver:/# lsof /etc
root@webserver:/#

---

### Post by surfer on 2010-06-15
just to be sure it's not the filesystem. can you edit [FONT=Courier New]/etc/hosts[/FONT] (or any other file below / )?

---

### Post by azmiuzun on 2010-06-15
i can edit /etc/hosts and other system files.

root@webserver:/# vim -w /etc/resolv.conf
i can append /etc/resolv.conf and save, but i can't edit this file

---

### Post by surfer on 2010-06-15
hmmm. and brute force: delete and recreate? it does not work anyway now with your current [FONT="Courier New"]resolv.conf[/FONT], right?

---

### Post by azmiuzun on 2010-06-15
i solve the problem, thanks everybody..


root@webserver:~# lsattr /etc/resolv.conf
----ia------------ /etc/resolv.conf

root@webserver:~# chattr -a /etc/resolv.conf

root@webserver:~# lsattr /etc/resolv.conf
----i------------- /etc/resolv.conf

root@webserver:~# chattr -i /etc/resolv.conf

root@webserver:~# lsattr /etc/resolv.conf
------------------ /etc/resolv.conf

root@webserver:~# vim /etc/resolv.conf
root@webserver:~#


i found the solution from this blog
[Make your files immutable which even root can't delete]("http://linuxhelp.blogspot.com/2005/11/make-your-files-immutable-which-even.html")

---

### Post by xlyz on 2012-12-30
> **azmiuzun said:**
> i solve the problem, thanks everybody..

root@webserver:~# chattr -i /etc/resolv.conf

i found the solution from this blog
[Make your files immutable which even root can't delete]("http://linuxhelp.blogspot.com/2005/11/make-your-files-immutable-which-even.html")

thanks. you saved my day :)

---

