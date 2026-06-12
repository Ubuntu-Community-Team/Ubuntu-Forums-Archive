---
title: "HDD/RAID help."
date: 2010-08-09
forum: Server Platforms
---

### Post by ipng on 2010-08-09
I've mountet my second HDD in /var/www/HDD2 and is using the HDD for media purposes, so i dont fill up the original HDD with all my pictures etc. But.. Well.. I cant link to the HDD (mountet in /var/www/HDD2). Is it because i need to setup a RAID?

It's being mountet automatically by the way.

EDIT: I'm mounting the HDD in /var/www/HDD2 so I easily can link to the directory in my index.html.

---

### Post by CharlesA on 2010-08-09
Huh?

You shouldn't mount anything in /var/www/ as that is the apache working directory.

You'd be better off making a folder in your home directory named "mediafiles" or something and mounting the drive there so you can find it.

Are you mounting the drive using fstab?

---

### Post by abix_adam_pl on 2010-08-09
Please send more info:

```
df -h
mount
cd
sudo ln -s /var/www/HDD2
ls -l H*

```and post here what is in Terminal. And remember, link to another directory has nothing to make a RAID, it is not the same. Read more about RAID in net...

Adam

---

### Post by ipng on 2010-08-09
Hello again. And thanks for the quick replies :)

Here is the output of your codes:
```
usrname@usrname:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             145G  2,9G  135G   3% /
udev                 1007M  236K 1007M   1% /dev
none                 1007M     0 1007M   0% /dev/shm
none                 1007M   76K 1007M   1% /var/run
none                 1007M     0 1007M   0% /var/lock
none                 1007M     0 1007M   0% /lib/init/rw
/dev/sdb1             151G  6,0G  137G   5% /var/www/HDD2
usrname@usrname:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sdb1 on /var/www/HDD2 type ext3 (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
usrname@usrname:~$ cd
usrname@usrname:~$ sudo 1n -s /var/www/HDD2
[sudo] password for png: 
sudo: 1n: command not found
usrname@usrname:~$ sudo ln -s /var/HDD2
usrname@usrname:~$ ls -l H*
lrwxrwxrwx 1 root root 9 2010-08-09 16:54 HDD2 -> /var/HDD2
usrname@usrname:~$ 

```

More info:
Yeah, I'm mounting the HDD using fstab.
I'm mounting the HDD in /var/www/HDD2 so I easily can write the path in HTML to my media files. I dont know how to write a path in HTML that starts in the root directory 

Do you need more details? Wich?

(Sorry if I'm not using the correct terms, still working on my overview)

---

### Post by CharlesA on 2010-08-09
Oh, I see what you are doing. If you wanted to do it that way, would it be easier to just mount the hard drive as /var/www and have seperate folders for your media and html files there.

What do you mean you can't link the drive? You should be able to browse it by opening the places menu and browing out to "file system" then go to /var/www/HDD2

---

### Post by ipng on 2010-08-09
Well, I can browse it through "Cyberduck" and actually see all the media content, but I cant link to the media's in my HTML file. Seems like it's linking to the folder HDD2, instead of the second HDD, but I'm not quite sure. 

And I would like HDD2 to be a seperate folder, unless i have got no choice :)

---

### Post by abix_adam_pl on 2010-08-09
I think my english is bad - I dont't understand, what you want to do. You CAN link the directory, the command "ln" do it very good. In first post you wrote about RAID and link, now you are writing about link and write HTML and settings in Apache.

Please, specyfy very carrefouly and deeply, what you want to achieve.

Adam

---

### Post by ipng on 2010-08-10
Sorry for my ambiguity. I shouldn't have mentioned RAID at all.. Well, the thing is, I want to link from the "Index.html" (placed in /var/www) to the second HDD in /var/www/HDD2. It's like it's linking to an empty folder where the second HDD isn't mountet (wich it obviously should be, just take a look at the terminal output I've written in a former post), because when I go to "http://myipaddress/HDD2/somemediafile" it says that there's no page or directory named that, wich is wrong. And yes, I've double checked.

My HTML link will look like this ```
<a href="/HDD2/index.html">some text</a>
``` 

I really hope you can help me out :)

---

### Post by dragos2 on 2010-08-10
> **ipng said:**
> Sorry for my ambiguity. I shouldn't have mentioned RAID at all.. Well, the thing is, I want to link from the "Index.html" (placed in /var/www) to the second HDD in /var/www/HDD2. It's like it's linking to an empty folder where the second HDD isn't mountet (wich it obviously should be, just take a look at the terminal output I've written in a former post), because when I go to "http://myipaddress/HDD2/somemediafile" it says that there's no page or directory named that, wich is wrong. And yes, I've double checked.

My HTML link will look like this ```
<a href="/HDD2/index.html">some text</a>
```I really hope you can help me out :)

Are you serious.. ?

---

### Post by ipng on 2010-08-10
I restarted the server twice and made an update. Seems like it's fixed :/ 
Many thanks for your time and comments though! :)

---

