---
title: "Raid array over 16tb"
date: 2010-11-30
forum: Server Platforms
---

### Post by halfelite on 2010-11-30
So after building everything and thinking ext4 would be fine running at 20TB I ran into a problem that the version of e2fsprogs is to old to support the making of things over 16tb. Looking for a little help on how to upgrade to one of the beta versions of e2fsprogs.


  Thanks
      Chris

---

### Post by rubylaser on 2010-11-30
I would be leery about using my own compiled version of e2progs on my data, but if you'd like to try it on yours, here are the steps.  [COLOR="Red"]CAUTION: This could destroy any data you have in your array![/COLOR]

```
sudo apt-get install build-essential
wget http://goo.gl/tULV9
tar xzvf e2fsprogs-1.41.12.tar.gz
cd e2fsprogs-1.41.12
./configure
make
make check
sudo make install
```

If that's not current enough, you might need to pull from their git repo.

```

sudo apt-get install git-core
git clone git://git.kernel.org/pub/scm/fs/ext2/e2fsprogs.git

```
Once you have the folder, cd into it and follow the remaining steps above.

That should do it.  I'd unmount your drive after doing this and make sure that you can still run an fsck.ex4 on it.

Hope that helps.

---

### Post by halfelite on 2010-11-30
Thanks for the reply the raid set is empty so im not worried about losing anything.

---

### Post by halfelite on 2010-11-30
Will that overwrite the current one. or do i still need to sudo apt-get remove e2fsprog

---

### Post by rubylaser on 2010-11-30
You should be able to install it over the top of the existing one.

---

### Post by halfelite on 2010-11-30
Well i tried and it failed it compiled fine but still pulling the same error. im running a 64bit OS and tried compiling from the Git repo but it comes back as the same 1.41.12 version. Anyone know if there is not a dev release out to try?

Or is my only option going to XFS? or Splitting the device into two mounts

chris@Server2:/usr/local/src/e2fsprogs$ sudo mke2fs -t ext4 /dev/sdb1
mke2fs 1.41.12 (17-May-2010)
mke2fs: Size of device (0x12309cb00 blocks) /dev/sdb1 too big to be expressed
        in 32 bits using a blocksize of 4096.

chris@Server2:/usr/local/src/e2fsprogs$ uname -m
x86_64

chris@Server2:/usr/local/src/e2fsprogs$ file /usr/bin/file
/usr/bin/file: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, stripped

---

### Post by James78 on 2010-12-01
The ext4 Wikipedia page states that the limit of the ext4 filesystem is 1 EiB (but limited to 16TiB because of e2fsprogs). 16TiB is very close to 16TB.

I quote..
> Max volume size: 1 EiB (limited to 16TiB because of e2fsprogs limitation until v1.42)
That probably means that in v1.42 the limit will be removed. Clearly yours is limited to under 16TB because you're using a slightly older version (1.41).

[http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4)

---

### Post by rubylaser on 2010-12-01
Unfortunately, the git repo is the developer's source control management, so what you pulled from it, you where getting the developer release.  Everything else would be in branches and not stable enough to use on your data.

You could either use XFS, JFS, or use Debian Squeeze with the KFreeBSD kernel and run native ZFS (on a 20TB array, I'd probably do this with RAIDZ2).

---

### Post by WinstonChurchill on 2010-12-01
> **James78 said:**
> 16TiB is very close to 16TB.
Not that this has a great deal of bearing on the OP's question, but that really isn't true:

16TB = 16000000000000 bytes
16TiB = 17592186044416 bytes

16 TiB = 17.592 TB - that's no small difference...

---

### Post by James78 on 2010-12-02
> **WinstonChurchill said:**
> Not that this has a great deal of bearing on the OP's question, but that really isn't true:

16TB = 16000000000000 bytes
16TiB = 17592186044416 bytes

16 TiB = 17.592 TB - that's no small difference...
When I said very close, I meant close to, as in numbers (16 and 17 are closer than 16 and 78 ), and in idea, 16 TB and 16 TiB are similar in many ways. Either way, there's still a limit that could get in his way very easily. ;)

Thanks for the correction though. :)

---

### Post by halfelite on 2010-12-05
Just an update I got ext4 working. I compiled the master branch from the git. But for someone reason make install was not overwriting the original  mke2fs conf under /etc once I replaced that with one that had the auto 64 flag everything worked fine.

---

### Post by rubylaser on 2010-12-06
Glad to hear that.  I thought you said that your previous git pull ended up compiling the same version.  You should have been pulling from the Master with the command I gave you earlier.  If you want to be helpful for others in your situation in the future, it could be a great benefit to copy and paste the commands you ran to get this working.

Thanks.

---

### Post by halfelite on 2010-12-07
I still pulls the same version number but works so maybe the version number is changed int the git.

---

