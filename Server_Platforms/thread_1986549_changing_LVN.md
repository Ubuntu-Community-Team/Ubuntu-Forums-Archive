---
title: "changing LVN"
date: 2012-05-25
forum: Server Platforms
---

### Post by enboig on 2012-05-25
I created a LVM where I gave 100gb to /tmp, but now I would need them for /var; how do I remove the volume from /tmp and add to /var?

# df -h
S. fitxers            Mida En ús Lliure %Ús Muntat a
/dev/mapper/base-arrel
                       97G  7,7G   85G   9% /
none                 1000M  244K 1000M   1% /dev
none                 1006M  164K 1006M   1% /dev/shm
none                 1006M  368K 1006M   1% /var/run
none                 1006M     0 1006M   0% /var/lock
/dev/mapper/base-tmp   97G  188M   92G   1% /tmp
/dev/mapper/base-home
                       97G  461M   92G   1% /home
/dev/mapper/base-logic1
                       12M  1,2M   10M  11% /mnt
/dev/mapper/base-var  1,1T  1,1T  1,3G 100% /var

---

### Post by darkod on 2012-05-25
You will first need to use resize2fs for example to shrink the filesystem on base-tmp to how much you want, for example 4GB.
Then use lvresize to resize the size of the actual LV, base-tmp to 5GB for example. It has to be a little larger than the filesystem so that you are sure it will have enough space to fit on the LV.

After that you can use lvresize again to add the space to base-var and resize2fs to expand the filesystem on it.

---

### Post by enboig on 2012-05-25
I tried
```

    resize2fs /dev/mapper/base-tmp 3G

```
but it didn't work

---

### Post by darkod on 2012-05-25
I think sometimes the LVM volumes appear without the mapper. Try with /dev/base-tmp

---

### Post by enboig on 2012-05-25
It returns the same error:
```

~# resize2fs /dev/base/tmp 3000M
resize2fs 1.41.12 (17-May-2010)
El sistema de fitxers a /dev/base/tmp està muntat a /tmp; cal un canvi de mida en línia
La reducció de mida en línia de 25600000 a 768000 no és compatible.

```

which in English would mean "/tmp is mounted; you need a change of size in line \n The resize of line from 25600000 to 768000 is not compatible".

---

### Post by darkod on 2012-05-25
You can't do it when it's mounted. But now you have the correct syntax.

You will have to do it from live mode. /tmp needs to be unmounted.

Note that in live mode the LVM doesn't exist by default. You need to install the package in the live session and activate the LVM:

sudo apt-get install lvm2
sudo vgchange -a y

That will activate it but will NOT mount it. That way you can shrink the FS.

---

### Post by LHammonds on 2012-05-25
Yep.  That was an oops.

You can "expand" file systems and logical volumes while online all day long.

Whenever you need to "shrink" a volume, you need to have free space available in the FS and it MUST be dismounted first.

If you shrink an FS smaller than the data that is stored on it, you will lose data.  Of course, this is a "tmp" volume so I doubt anything of value is in there but you need to know this for anything you shrink.

LHammonds

---

### Post by enboig on 2012-05-28
Thanks to everybody, I will try it today and post the results.

---

### Post by enboig on 2012-05-31
Ok, finally I got it working. I resized one file system and after that I resized the volume with no problem.

After that I was doing the same with another volume, but I resized one filesystem and resized the wrong volume, making it smaller than its filesystem. Lucky me I resized it twice its allocated space, so after resizing back the volume everything was ok.

---

