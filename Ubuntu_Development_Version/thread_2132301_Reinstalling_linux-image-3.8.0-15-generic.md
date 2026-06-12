---
title: "Reinstalling linux-image-3.8.0-15-generic"
date: 2013-04-04
forum: Ubuntu Development Version
---

### Post by DrCake on 2013-04-04
Hi,

I've been running Ubuntu 13.04, and everything is working fine. But today, when i tried to update, i get this message from the terminal:
```
E: The package linux-image-3.8.0-15-generic needs to be reinstalled, but I can't find an archive for it.
```

And i have to idea how to fix this. Can anybody help me?

---

### Post by dino99 on 2013-04-04
install synaptic, then purge & reinstall the packages related to 3.8.0-15 kernel

---

### Post by DrCake on 2013-04-04
I cant open synaptics, i get almost the same error
```
E: The package linux-image-3.8.0-15-generic needs to be reinstalled, but I can't find an archive for it.E: Internal error opening cache (1). Please report.
```

---

### Post by dino99 on 2013-04-04
then select an other kernel to boot with inside the grub menu (if you have at least the previous kernel installed) or select the recovery mode

---

### Post by grahammechanical on 2013-04-04
What image are you booting into? Linux-image 3.8.0-15? Try booting into a previous image - 3.8.0-14 or 3.8.0-13. Look under Advance Options for Ubuntu in the Grub menu.

If you can load Synaptic search for Linux 3.8.0-15 and you will find linux-headers, linux-headers-generic, linux-image-extras-generic, linux-image-generic. All marked 3.8.0-15. Select each one and right click and select Mark for Complete Removal. In your case you might find that each line in marked with a grey icon and you have the right click option if upgrading or reinstalling.

You may need to try ```
sudo apt-get -f  install
``` and ```
sudo dpkg --configure -a
```

Regards.

---

### Post by Cavsfan on 2013-04-04
Wouldn't this work?

```
sudo apt-get purge linux-headers-3.8.0-15 linux-headers-3.8.0-15-generic linux-image-3.8.0-15-generic linux-image-extra-3.8.0-15-generic
```

then 

```
sudo apt-get install linux-headers-3.8.0-15 linux-headers-3.8.0-15-generic linux-image-3.8.0-15-generic linux-image-extra-3.8.0-15-generic
```

---

### Post by Cavsfan on 2013-04-04
grahammechanical beat me to it.

Possibly this to fix the broken packages:


```
sudo apt-get install -f
```

---

### Post by DrCake on 2013-04-05
Non of the tips work, i always get the same error
```
The package linux-image-3.8.0-15-generic needs to be reinstalled, but I can't find an archive for it.


```

---

### Post by dino99 on 2013-04-05
inside synaptic, check that repos are activated, then update

> sudo apt-get install synaptic

---

### Post by DrCake on 2013-04-05
> **dino99 said:**
> inside synaptic, check that repos are activated, then update

Like i told dino99, i already have synaptic. But when i try to open it i get an error.

---

### Post by Cavsfan on 2013-04-05
I have the 3.8.0-16-generic kernel installed which is the latest.

Maybe try this:

```
sudo apt-get install linux-headers-3.8.0-16 linux-headers-3.8.0-16-generic linux-image-3.8.0-16-generic linux-image-extra-3.8.0-16-generic
```

---

### Post by DrCake on 2013-04-05
I can't install anything, because i get that error.

---

### Post by Elfy on 2013-04-05
Only time I have ever been able to get past a " needs to be reinstalled, but I can't find an archive for it." error I've had to use reinstreq 
```

sudo dpkg --remove  --force-remove-reinstreq *package name*
```

but I only use it if I really have to.

man dpkg - > remove-reinstreq: Remove a package,  even  if  it's  broken  and
              marked  to  require reinstallation. This may, for example, cause
              parts of the package to remain on the system, which will then be
              forgotten by dpkg.

---

### Post by zika on 2013-04-05
> **DrCake said:**
> I can't install anything, because i get that error.Do You have any other kernel installed?
If You do, boot with it then```
sudo apt-get purge linux-image-3.8.0-15-generic
``` and You should be OK...
If You do not have any other kernel installed install one from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) (picking 4 .deb's) and You could either reboot in new kernel and purge offending one or purge offending one and boot into new kernel or do update/upgrade and You should get -16 and then...
Just keep one kernel beside that one and You should be OK...
Carefully... ;)

---

### Post by DrCake on 2013-04-05
When i boot into an other kernel, i get the same error.
I check with uname -r and it returns: 3.5.0-23

---

### Post by Cavsfan on 2013-04-05
> **DrCake said:**
> When i boot into an other kernel, i get the same error.
I check with uname -r and it returns: 3.5.0-23

```
cavsfan@cavsfan-MS-7529:~$ uname -r
3.8.0-16-generic
cavsfan@cavsfan-MS-7529:~$ 
```


What is the output of **cat /etc/fstab**? Highlight the output and click the # button above to put CODE around it so it is legible.

Sounds like a fresh install may be necessary.

---

### Post by Cavsfan on 2013-04-05
Oh and the output of **sudo blkid** also wrapped in CODE.

---

### Post by DrCake on 2013-04-05
> **Cavsfan said:**
> ```
cavsfan@cavsfan-MS-7529:~$ uname -r
3.8.0-16-generic
cavsfan@cavsfan-MS-7529:~$ 
```


What is the output of **cat /etc/fstab**? Highlight the output and click the # button above to put CODE around it so it is legible.

Sounds like a fresh install may be necessary.

The output is
```
goubuntu@MonsterDesktopU:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=ae9d1883-d5e2-44a8-bda6-ccf5bdb28d64 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=2a6b3372-c91f-4763-8ef5-65dad5702db1 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=8ac0a990-1e3f-417a-9ff2-449ce36548a2 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

I would hate doing a fresh install, is there an easy way to backup applications?

---

### Post by DrCake on 2013-04-05
The output of sudo blkid
```
goubuntu@MonsterDesktopU:~$ sudo blkid
[sudo] password for goubuntu: 
/dev/sda2: LABEL="Data" UUID="488EDA228EDA07F8" TYPE="ntfs" 
/dev/sda5: UUID="8ac0a990-1e3f-417a-9ff2-449ce36548a2" TYPE="swap" 
/dev/sda6: UUID="ae9d1883-d5e2-44a8-bda6-ccf5bdb28d64" TYPE="ext4" 
/dev/sda7: UUID="2a6b3372-c91f-4763-8ef5-65dad5702db1" TYPE="ext4" 
/dev/sdb1: LABEL="System Reserved" UUID="3A84FB8F84FB4C3F" TYPE="ntfs" 
/dev/sdb2: UUID="12E00807E007EFB1" TYPE="ntfs" 


```

---

### Post by Cavsfan on 2013-04-05
> **DrCake said:**
> I would hate doing a fresh install, is there an easy way to backup applications?

Surely you do not have all of your important stuff on a development OS?

I have a 1TB USB drive I copy all of my stuff to before a clean install.

Make sure you back up your **/home/cavsfan/.mozilla** folder. Saves bookmarks, settings and a bunch more.

Everything looks good with your fstab matching your partitions.

---

### Post by DrCake on 2013-04-05
The files are not important for me, because i have them backup on my NAS. But its the applications and Nvidia driver that takes so much time.

---

### Post by dino99 on 2013-04-05
have you ran :

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install -f

sudo dpkg-reconfigure -phigh -a
( be patient, can take a while, dont stop it yourself)

---

### Post by DrCake on 2013-04-05
> **dino99 said:**
> have you ran :

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install -f

sudo dpkg-reconfigure -phigh -a
( be patient, can take a while, dont stop it yourself)

yes but it doesnt work

---

### Post by Elfy on 2013-04-05
Did you try 

```
sudo dpkg --remove --force-remove-reinstreq linux-image-3.8.0-15-generic
```

---

### Post by DrCake on 2013-04-05
Yes but i get an error
```
goubuntu@MonsterDesktopU:~$ sudo dpkg --remove -force --force-remove-reinstreq linux-image-3.8.0-15-generic
dpkg: error: conflicting actions -f (--field) and -r (--remove)

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !


```

---

### Post by Elfy on 2013-04-05
```
sudo dpkg --remove  --force-remove-reinstreq linux-image-3.8.0-15-generic
```

Mucked up that paste - try this

---

### Post by DrCake on 2013-04-05
It looks like that worked! Thanks! Ubuntu is updating now, ill do a reboot when its done and post an update if it worked

---

### Post by DrCake on 2013-04-05
The problem is solved! Thank you all for helping me!

---

### Post by Cavsfan on 2013-04-05
> **Elfy said:**
> ```
sudo dpkg --remove  --force-remove-reinstreq linux-image-3.8.0-15-generic
```

Mucked up that paste - try this

Elfy, that is awesome!!!  :D

Glad I am subscribed to this thread for future reference.

> **DrCake said:**
> The problem is solved! Thank you all for helping me!

Glad you got it back! I am with you, I hate clean installs if they can be avoided and it looks like Elfy saved the day! 

The final release is April 25th so it would have been a pain to do a fresh install now. :(

That is what is so good about this forum - so many people willing to help. :)

---

### Post by Elfy on 2013-04-05
Good - sorry I fail pasted the first time. 

I'd even checked it before hand to make sure it worked :)

---

