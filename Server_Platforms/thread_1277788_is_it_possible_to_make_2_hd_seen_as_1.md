---
title: "is it possible to make 2 h/d seen as 1?"
date: 2009-09-28
forum: Server Platforms
---

### Post by gobbledigook on 2009-09-28
hi!

i'm running out of space on one of my 1tb drives and it holds a lot of files in alphabetical order, obviously to extend my storage i need a new drive, however i need to add more files of the same category . 

so is there anyway to make ubuntu see the two drives as one? or to   get it to automagically sort the files into alphabetical order over the 2 drives?  

any help greatly appreciated:)

d

---

### Post by Bölvaður on 2009-09-28
Would you consider formating the drives to xfs?
That way you can even have this one partition extend over an entire network of harddisks if you want.

But I highly doubt this is the answer you hoped for. Nor do I recommend it if you do not understand how xfs works.

---

### Post by falconindy on 2009-09-28
For all intents and purposes, your file system IS seen as one drive. How you mount your drives determines how/when you run out of space. You could, for example, mount each directory in the root on a different drive. /etc/fstab would look something like:

```
/dev/sda1    /bin    defaults    0    0
/dev/sdb1    /home    defaults    0    0
/dev/sdc1    /etc    defaults    0    0
/dev/sdd1    /lib   defaults    0    0
/dev/sde1    /boot    defaults    0    0
```etc etc. Very commonly, /home is mounted separately, not just for concerns regarding space, but for convenience as well. Splitting up your OS like this is a smart choice, up to a point, as each additional drive increases the chances of a physical failure. But then, of course, you made backups... right?

edit: I think I misread your post. A JBOD span would do what you're looking for, but neither jbod or software based raid are good ideas.

---

### Post by gobbledigook on 2009-09-29
ok, thanx for your replies!

The server is used as a fileserver at home, so loads on it aren't too high... i run xbmc, utorrent and sabnzbd and a samba share and host a small website, but that's about it.

Unfortunately i am not at the stage yet where i can afford to have my system backed up entirely, as i have 2x 1tb drives and 1x 300gb for storage and 1x 40gb for my system. The system drive is easy enough to raid (when i get around to it!!) but i simply cannot afford to fork out for another couple of tb drives to use as backup AND another couple to use as extra storage!

So i would not currently be in the position to reformat the filesystem from ext3 to xfs as i've no-where to put the date whilst the drive is being formated:) 

I'm intrested in the possibility of mounting 2 drives in the same folder though? would this work??

```

/dev/sda1    /media/stuff    defaults    0    0
/dev/sdb1    /media/stuff    defaults    0    0

```

or would this just end up as a mad jumble of information?

Thanx!

---

### Post by demosthene1 on 2009-09-29
When I was using Fedora 10 it did this by default, installing LVM. Logical Volume Management didn't make sense for me on my little laptop,

So, look into LVM. Visit the Fedora website for info and/or Google it.

---

### Post by MattiJ on 2009-09-29
You can do this with mhddfs [http://vds.uvw.ru/mhddfs/trunk/README]("http://vds.uvw.ru/mhddfs/trunk/README") 

```
sudo apt-get install mhddfs
```

Then in fstab have something like this to join the disks

```
mhddfs#/mnt/d1,/mnt/d2,/mnt/d3  /media/mhddfs fuse mlimit=6G,defaults,allow_other 0 0
```

---

### Post by gobbledigook on 2009-09-29
hey!

mhddfs looks perfect! thanks Mattij, looks nice and simple and no extra formatting needed:)

will implement this later and see how i get on!

---

### Post by MattiJ on 2009-09-29
Just download an compile latest version 0.1.22 if You have older.

---

