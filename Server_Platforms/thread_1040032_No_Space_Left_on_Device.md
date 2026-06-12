---
title: "No Space Left on Device"
date: 2009-01-15
forum: Server Platforms
---

### Post by damo12 on 2009-01-15
I am running a server with Ubuntu server 8.04 and Webmin on it.  When I try to run a "Distribution upgrade" on it I get the error message:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
``` 

when I try to run dpkg --configure -a I get the message:

```
gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-16-server
dpkg: subprocess post-installation script returned error exit status 1

```

I installed the system on an 80Gb hard drive using the recommended settings and have only system files on that drive, all other files are stored on a separate drive.  Can someone please help and let me know what I need to do to correct this problem.

---

### Post by aaron.d on 2009-01-15
what does the output of:

```
$ df -ah
```

it looks like maybe '/boot' is too small. Have you got a separate '/boot', or disk quotas setup?

---

### Post by damo12 on 2009-01-16
The output is:
```
> df -ah
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             146G  145G     0 100% /
proc                     0     0     0   -  /proc
/sys                     0     0     0   -  /sys
varrun                505M  2.5M  503M   1% /var/run
varlock               505M     0  505M   0% /var/lock
udev                  505M   60K  505M   1% /dev
devshm                505M     0  505M   0% /dev/shm
devpts                   0     0     0   -  /dev/pts
/dev/sdb1             373G  213G  160G  58% /media/server
/dev/sdc1             373G  372G  931M 100% /media/backup
securityfs               0     0     0   -  /sys/kernel/security
overflow              1.0M  172K  852K  17% /tmp

```

Ubuntu is installed on one hard drive (160Gb not 80) which was installed following the "guided install" method of the installation CD, there are no disc quotas set up.

---

### Post by gtdaqua on 2009-01-16
> 
> df -ah
Filesystem            Size  Used Avail Use% Mounted on
**/dev/sda1             146G  145G     0 100% /**


Based on the above info, you have ubuntu installed on the 160BG partition. 

You have to free up some space. Try autocleaning packages that are no longer required in cache: "sudo apt-get autoclean" and also try "sudo apt-get autoremove".


Under root partition, type:
```

sudo du * -s | sort -nr | head

```

That will tell you the file/folder with the highest size. Descend upon them and remove if you dont need it.

---

### Post by aaron.d on 2009-01-16
> **damo12 said:**
> The output is:
```
> df -ah
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             146G  145G     0 100% /
proc                     0     0     0   -  /proc
/sys                     0     0     0   -  /sys
varrun                505M  2.5M  503M   1% /var/run
varlock               505M     0  505M   0% /var/lock
udev                  505M   60K  505M   1% /dev
devshm                505M     0  505M   0% /dev/shm
devpts                   0     0     0   -  /dev/pts
/dev/sdb1             373G  213G  160G  58% /media/server
/dev/sdc1             373G  372G  931M 100% /media/backup
securityfs               0     0     0   -  /sys/kernel/security
overflow              1.0M  172K  852K  17% /tmp

```

Ubuntu is installed on one hard drive (160Gb not 80) which was installed following the "guided install" method of the installation CD, there are no disc quotas set up.

yeah dude, like I said, the first line says it all. your root (/) partition is filled to the gills.

You used an entire ~145G (formatted 160G) drive in one catch-all partition, which means if you wipe that partition you lose everything. In the future, depending on what you are doing with the install, you may want to create separate /home, /boot, or /var partitions.

In this case, since I have never seen an installation take anywhere near this much space, especially for a server (my server installation, for example, takes ~700M. That is including /boot and /var), I will assume you managed to fill your home directory. check there. Other than that I cant be sure. Are you running a db server with large datasets? Hosting a webserver with a ton of data? mailserver with large mail files? etc.

---

### Post by damo12 on 2009-01-16
I've checked the home directory and it's empty.  The server is a straight forward samba file server accessed by a number of PCs.  The files are all stored on /dev/sdb1 and /dev/sdc1.

Is there any way I can run a scan to find out what is taking up all of the space?  Sorry for asking what is probably a really obvious question but I'm pretty new to Linux servers.

---

### Post by aaron.d on 2009-01-16
> **damo12 said:**
> 

Is there any way I can run a scan to find out what is taking up all of the space?  Sorry for asking what is probably a really obvious question but I'm pretty new to Linux servers.



do like 'gtdaqua' suggested:
> 
Under root partition (cd /), type:
Code:

sudo du * -s | sort -nr | head

That will tell you the file/folder with the highest size. Descend upon them and remove if you dont need it. 

---

### Post by albinootje on 2009-01-16
> **damo12 said:**
> The server is a straight forward samba file server accessed by a number of PCs.  The files are all stored on /dev/sdb1 and /dev/sdc1.


```

sudo apt-get clean

```
might help a little.
It is also possible that, due to a lot of errors, your logfiles have eaten a lot of disk space.
Check :
```
 
sudo du -sh /var/log

```
You can remove the *.gz logfiles in /var/log if you like.

---

### Post by damo12 on 2009-01-17
Thank you so much for all of your help, following the instructions I found that for some reason a backup of the file server had been placed in the mmt folder instead of an external drive.  I deleted that and everything worked fine.

thanks again for all of the help.

---

