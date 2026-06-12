---
title: "server space increasing at alarm rate"
date: 2016-12-14
forum: Server Platforms
---

### Post by micahpage on 2016-12-14
I am trying to figure out why the server is using so much space. 2 months ago was 4GB and now is almost 10GB. I assumed the culprit would be log files but i think i cleared them

I changed rotate to lower
from 52 to 5


```
metulburr ~ $ cat /etc/logrotate.d/apache2
/var/log/apache2/*.log {
    weekly
    missingok
    rotate 5
    compress
    delaycompress
    notifempty
    create 640 root adm
    sharedscripts
    postrotate
                if /etc/init.d/apache2 status > /dev/null ; then \
                    /etc/init.d/apache2 reload > /dev/null; \
                fi;
    endscript
    prerotate
        if [ -d /etc/logrotate.d/httpd-prerotate ]; then \
            run-parts /etc/logrotate.d/httpd-prerotate; \
        fi; \
    endscript
}

```


and removed the numerous *.log.gz that existed beforehand. What is here is within the past day or so
```
metulburr /var/log $ ls
alternatives.log    boot.log               dpkg.log        lastlog     mysql.log.1.gz
alternatives.log.1  bootstrap.log          dpkg.log.1      mail.err    syslog
apache2             btmp                   faillog         mail.err.1  syslog.1
apport.log          btmp.1                 fontconfig.log  mail.log    syslog.2.gz
apport.log.1        cloud-init.log         fsck            mail.log.1  udev
apport.log.2.gz     cloud-init-output.log  installer       msmtp.log   unattended-upgrades
apt                 dist-upgrade           kern.log        mysql       upstart
auth.log            dmesg                  kern.log.1      mysql.err   wtmp
auth.log.1          dmesg.0                landscape       mysql.log   wtmp.1

```




but even after that the storage used is 9.1GB and doesnt seem to clear any space
```
metulburr /var/log $ df -h
Filesystem                 Size  Used Avail Use% Mounted on
udev                       487M  4.0K  487M   1% /dev
tmpfs                      100M  360K  100M   1% /run
/dev/disk/by-label/DOROOT   30G  9.1G   19G  33% /
none                       4.0K     0  4.0K   0% /sys/fs/cgroup
none                       5.0M     0  5.0M   0% /run/lock
none                       498M     0  498M   0% /run/shm
none                       100M     0  100M   0% /run/user

```

NOTE: I did create a 2GB swap, as well as the actual data on the server may go up to 300MB, but the rest is unkown.

size list
```
metulburr /var/log $ sudo du -a / | sort -n -r | head -n 45
sudo: unable to resolve host python-forum
du: cannot access &#8216;/proc/16370/task/16370/fd/4&#8217;: No such file or directory
du: cannot access &#8216;/proc/16370/task/16370/fdinfo/4&#8217;: No such file or directory
du: cannot access &#8216;/proc/16370/fd/4&#8217;: No such file or directory
du: cannot access &#8216;/proc/16370/fdinfo/4&#8217;: No such file or directory
7803708    /
2556844    /var
2097156    /swapfile
1850008    /usr
1396464    /var/www
1102820    /lib
943808    /lib/modules
727672    /var/www/html
616784    /usr/lib
606432    /var/www/html/pygame
598152    /var/www/html/pygame/ftp
553884    /usr/src
550624    /var/www/ftp
549000    /var/cache
433300    /var/cache/apt
406260    /usr/share
345140    /var/cache/apt/archives
322976    /var/lib
295088    /usr/lib/x86_64-linux-gnu
264032    /var/log
248892    /var/www/html/pygame/ftp/ftp.tar.gz
248892    /var/www/ftp/ftp.tar.gz
189076    /lib/modules/3.13.0-105-generic
189076    /lib/modules/3.13.0-103-generic
188940    /lib/modules/3.13.0-101-generic
188376    /lib/modules/3.13.0-61-generic
188336    /lib/modules/3.13.0-57-generic
185012    /lib/modules/3.13.0-105-generic/kernel
185012    /lib/modules/3.13.0-103-generic/kernel
184876    /lib/modules/3.13.0-101-generic/kernel
184328    /lib/modules/3.13.0-61-generic/kernel
184288    /lib/modules/3.13.0-57-generic/kernel
174360    /var/lib/apt
174288    /var/lib/apt/lists
163928    /var/log/apache2
159428    /usr/bin
153992    /boot
143848    /usr/lib/python2.7
140564    /lib/modules/3.13.0-105-generic/kernel/drivers
140564    /lib/modules/3.13.0-103-generic/kernel/drivers
140428    /lib/modules/3.13.0-101-generic/kernel/drivers
140364    /lib/modules/3.13.0-61-generic/kernel/drivers
140340    /lib/modules/3.13.0-57-generic/kernel/drivers
129168    /lib/firmware
118164    /var/www/metulburr.com



```
Everything in /var/www/*  is accounted for.

---

### Post by Habitual on 2016-12-14
Please post output of ```
df -hT /home
```

Thank you,

---

### Post by micahpage on 2016-12-14
i found a couple large files that i deleted dropping it 1.5GB

```
metulburr /var/log $ df -hT /home
Filesystem                Type  Size  Used Avail Use% Mounted on
/dev/disk/by-label/DOROOT ext4   30G  7.5G   21G  27% /



```

---

### Post by Habitual on 2016-12-14
Your $HOME disk usage is part of the / disk layout
What's in /home/* ?

```
sudo du -sh  /home/* | sort -n
``` output please.

---

### Post by micahpage on 2016-12-15
```
metulburr ~ $ sudo du -sh  /home/* | sort -nsudo: unable to resolve host python-forum
[sudo] password for metulburr: 
2.4M	/home/metulburr
16K	/home/ichabod801
20K	/home/yoriz
24K	/home/mekire
24K	/home/snippsat
32K	/home/micseydel
40K	/home/stranac



```

---

### Post by TheFu on 2016-12-15
Looks like a pure server. Nice.

I'd use a **find** cmd to look for large files.  Similarly, I'd use find to search for new file that are non-trivial in size.
If this is a web server, does it allow uploads? Could someone be pushing files and sharing those with others?

BTW, **sort -h** understands **du -h** output. Very convenient.

---

### Post by darkod on 2016-12-16
Taking into account that a clean ubuntu server installation is about 2GB and that you have 2GB swap file inside root (/swapfile), and that this is a web server and your /var already has another 2.5GB, I wouldn't say your current / size of 7.5GB is exaggerated. Looks normal to me.

Now, if in one week it jumps to 10-12GB, then you need to look more closely into it. Otherwise from what we can currently see, it all looks good... I don't think you can have it lower than 7-8GB with current setup.

PS. You say in two months it jumped from 4GB to 10GB but taking into account the 2GB swap file, the very basic clean installation would be 4GB in total (2GB basic ubuntu server + 2GB swap file). Was that before you started adding web files and various other files? I mean, your /usr alone is almost 2GB which looks like you have put some stuff there too.
You can't expect your total to be 4GB with 2GB swap file, 2GB in /var and 1.8GB in /usr.

---

