---
title: "Do I need to increase size of my / partition?"
date: 2010-11-21
forum: Security
---

### Post by newboyo on 2010-11-21
Hi all,

I have separate partitions for / and ~, with ~ being encrypted (using the encrypt option during installation).

```
df - h shows 
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              49G   46G   85M 100% /
none                  1.9G  352K  1.9G   1% /dev
none                  1.9G  256K  1.9G   1% /dev/shm
none                  1.9G   92K  1.9G   1% /var/run
none                  1.9G     0  1.9G   0% /var/lock
none                  1.9G     0  1.9G   0% /lib/init/rw
/home/XXX/.Private   49G   46G   85M 100% /home/XXX
```

where sda6 is my / partition.

Do you think it useful to increase the size of / - in case it would help performance of the box (currently there are no problems, the box is absolutely fine)? If so, how should I do so?

Thanks 

New

---

### Post by theozzlives on 2010-11-21
If every thing's fine then I'd say no. I get along just peachy with a 10 GB /. If yours is as big, or bigger, you should be a-ok.

---

### Post by newboyo on 2010-11-21
> **theozzlives said:**
> If every thing's fine then I'd say no. I get along just peachy with a 10 GB /. If yours is as big, or bigger, you should be a-ok.

Hi,

Thanks for your reply. Just curious, your / is 10 G, while mine is 49 G. Is it common to have such a large diff in the / sizes?

Rgds

new

---

### Post by atomizer on 2010-11-21
> **newboyo said:**
> 

```
df - h shows 
Filesystem            Size  Used Avail Use% Mounted on
_/dev/sda6              49G   46G   85M 100% /_
none                  1.9G  352K  1.9G   1% /dev
none                  1.9G  256K  1.9G   1% /dev/shm
none                  1.9G   92K  1.9G   1% /var/run
none                  1.9G     0  1.9G   0% /var/lock
none                  1.9G     0  1.9G   0% /lib/init/rw
_/home/XXX/.Private   49G   46G   85M 100% /home/XXX_
```



Thanks 

New

Are you shure you have a seperate /home partition? df shows exactly the same size/used/avail. for / and /home (and it is full, you have 85MB left)

---

### Post by CharlesA on 2010-11-21
If you choose to encrypt the home directory during install, it doesn't place yer home directory on another partition.

Your drive is almost completely full.

---

### Post by newboyo on 2010-11-21
oh shoot!!!!

will using gparted to increase size of / be safe?

---

### Post by CharlesA on 2010-11-21
> **newboyo said:**
> oh shoot!!!!

will using gparted to increase size of / be safe?
Only if you backup all yer stuff first.

Resizing partitions can cause data loss.

---

### Post by Elfy on 2010-11-21
Might not be as easy as just firing up gparted - but as I don't bother with encrypted drives I could be wrong ;)

This might be of help - [http://ubuntuforums.org/showthread.php?t=726724](http://ubuntuforums.org/showthread.php?t=726724)

Long post warning ... read it though if it looks like you might need to :lol:

---

### Post by newboyo on 2010-11-22
Hi all,
 
Thanks for your feedback. I deleted the unencrypted (and separate) ~. fired up gparted and resized my /.
 
It did work.
 
Will try LUKS whenever I next reinstall.
 
Rgds
 
New

---

