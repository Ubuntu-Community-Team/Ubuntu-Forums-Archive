---
title: "Placing quota/cap on users' /home directories?"
date: 2010-07-28
forum: Server Platforms
---

### Post by flatline on 2010-07-28
[SIZE="3"]_Background_[/SIZE]: I have my home server setup, running 10.04 x64.  The OS is installed on a 300GB WD Blue drive, and I have a RAID5 array md0, consisting of 4x 2TB WD Green drives, mounted as /home.  I am sharing the home directories using samba and using them to back-up the other computers in the house.  I have created a user account+password for each computer, giving it its own "/home/computername_backup/" directory to store it's backups in.

Computers being backed-up:[LIST]
[*](750GB) Gaming PC running Win7 Ultimate x64  
[*](30GB + 2TB) HTPC running Win7 Home Premium x64  
[*](32GB) Netbook running Win7 Home Premium x32  
[*](250GB) 2 Macbook Pros Running OS X 10.6.4  (tweaked to allow time machine to recognize the samba share as a time machine volume
[/LIST]

[SIZE="3"]_Question_[/SIZE]: 5.37TB of /home seems good for now, and I haven't run into any problems so far, but I don't want to have to keep checking.  **I'd like to put a size cap on each user's home**, to prevent one of the computers from gobbling up all the space.  Is there an easy (or hard) way to configure this type of thing?  My Macbook, for example, only has a 250GB HD.  I could give it 3-400GB of space for its home and that would be plenty - whenever it filled its /home/, it would start erasing the oldest backups.  If there is no size limit, I believe it will just continue to grow until all the free space is gone.

[SIZE="3"]_Considerations_[/SIZE]: Right now, the HTPC is storing all its media locally (on the installed 2TB drive).  However, I've already used 3/4 of the space and the HPTC enclosure can only hold one drive.  My plan moving forward is to have /home be used to store media files (iTunes music for all computers and tv/movies for the HTPC), which is another reason I'd like to ensure that the backups don't take up all the space.

I realize I could create a partition for each computer, but I'd prefer not to go down this route.  This would seem an untenable tactic if I added another computer next month, or if I realized that the partition was too small.

[SIZE="3"]_Addendum_[/SIZE]: Please note that this is just a system I hacked together for my needs; if there is a better solution to this, I'm open to suggestions.

---

### Post by ruffEdgz on 2010-07-28
How about using user or group quotas for your system. Do the following command to see if this is what you want or can do:
```

aptitude show quota

```
If it is, then maybe you can take a look at this for some guidence for setting it up: [http://www.ubuntugeek.com/how-to-setup-disk-quotas-in-ubuntu.html](http://www.ubuntugeek.com/how-to-setup-disk-quotas-in-ubuntu.html)

Hope this helps.

---

### Post by flatline on 2010-07-28
I *think* I got this setup using quota and quotatool, although I'm SSH'd in from work, so I haven't really tested it out.  One thing I'm wondering about is what happens if/when an account does approach it's limit.  Hopefully the configuration of warnquota can be tweaked such that I don't get a million emails telling me about users exceeding their quota.

```

sudo apt-get install quota quotatool
sudo vi /etc/fstab

```made the following addition to fstab:
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# /home was on /dev/md0 during installation
UUID=********** /home           ext4    defaults,errors=remount-ro,**_usrquota,grpquota_**        0       2

```
```

sudo touch /home/aquota.user /home/aquota.group
sudo chmod 600 /home/aquota.*
sudo mount -o remount /home
sudo quotacheck -avugm
sudo quotaon -avug

```
then i used quotatool to configure the quota for my macbook's time machine user account:
```
sudo quotatool -u *username* -bq 30000Mb -l "35000 Mb" /home -v
```


Here are the sites I used for reference:
[U][http://www.ubuntugeek.com/how-to-setup-disk-quotas-in-ubuntu.html](http://www.ubuntugeek.com/how-to-setup-disk-quotas-in-ubuntu.html)
[http://www.debianhelp.co.uk/Webmin.htm](http://www.debianhelp.co.uk/Webmin.htm)
[http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-3-p4](http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-3-p4)
[http://quotatool.ekenberg.se/index.php?node=documentation](http://quotatool.ekenberg.se/index.php?node=documentation)[/U]

---

