---
title: "Disk usage error"
date: 2008-03-10
forum: Server Platforms
---

### Post by Gishten on 2008-03-10
Hi everybody!

I've installed ubuntu server with LAMP a couple of weeks ago. I've been using it as a fileserver (samba and FTP) as well as a torrent client (deluge with web gui) and lastly to as a web server for my own domain.

I've runned in to a problem that i just can't find the answer to. So here's the deal.

According to SAMBA, deluge and df. My sdb1 partition is full (this is where the OS is installed):

df -h:

Filesystem Size Used Avail Use% Mounted on
/dev/sdb1 70G 66G 0 100% /
varrun 252M 200K 252M 1% /var/run
varlock 252M 0 252M 0% /var/lock
udev 252M 56K 252M 1% /dev
devshm 252M 0 252M 0% /dev/shm
/dev/sda1 114G 80G 29G 74% /mnt/120an
overflow 1.0M 0 1.0M 0% /tmp 

According to sudo du -sh /*:

”3.5M /bin
17M /boot
0 /cdrom
212K /dev
4.1M /etc
12G /home
4.0K /initrd
0 /initrd.img
77M /lib
16K /lost+found
8.0K /media
80G /mnt
4.0K /opt
0 /proc
44K /root
5.8M /sbin
4.0K /srv
0 /sys
0 /tmp
420M /usr
123M /var
0 /vmlinuz” 

My question is, how does this add up? And how can i make the system to report the correct disk usage

What is taking up ~55GB?

I'm kind of a linux noob so be nice :)

---

### Post by OffAxis on 2008-03-10
could you post the output of 

```
sudo du -shc /*
```

the c just sums the output.

---

### Post by Gishten on 2008-03-10
> **OffAxis said:**
> could you post the output of 

```
sudo du -shc /*
```

the c just sums the output.

I've gotten some help from another forum and the solution was that I've accidentally copied some data to the /mnt dir before mounting sda1.:lolflag:

umounting and du /mnt showed that there was indeed 54GB of data there.

Deleting this data and then mounting solved the problem totally.

Thx for the help anyways.

---

