---
title: "What to do if mount does not help?"
date: 2009-09-11
forum: Server Platforms
---

### Post by Vegan on 2009-09-11
I have tried everything, and I have concluded that SAMBA simply does not like a mounted link. So anyone have any ideas?

what is better? Thoughts?

---

### Post by cariboo on 2009-09-11
I have 4 drives mounted in /media and share them over the whole network:

```
/dev/sdb1             373G  110G  263G  30% /media/documents
/dev/sdc1             298G   73G  226G  25% /media/music
/dev/sdd1             115G   52G   64G  45% /media/stuff
/dev/sde1             699G  551G  149G  79% /media/external
/dev/sdf1              74G  1.3G   69G   2% /media/www_backup

```

this is what the appropriate part of /etc/samba/smb.conf looks like:

```
[movies]
	path = /media/movies
	comment = Movies and TV 
	guest ok = yes
	writeable = yes
	browseable = yes

[music]
	path = /media/music
	comment = tunes
	guest ok = yes
	writeable = yes
	browseable = yes

[documents]
	path = /media/documents
	comment = documents and such
	guest ok = yes
	writeable = yes
	browseable = yes

[stuff]
	path = /media/stuff
	comment = whatever fits
	guest ok = yes
	browseable = yes
	writeable = yes

[images]
	path = /mnt
	comment = mounted iso images
	guest ok = yes
	browesable = yes
	writeable = yes
```

Note: because everyone has guest access the files will be own by nobody.

---

### Post by Vegan on 2009-09-26
Turns out the problem is using ext4, seems a friend using Fedora was able to mount disks with ext4 no problem.

So formatting ext3 allowed the shares to work.

I notice my disks are sda and sdb, so what will USB disks likely be so I can mount them as additional storage.

---

### Post by cariboo on 2009-09-26
My server is formatted as ext3 and the shares are formatted as xfs, so how the partitions are formatted doesn't make any difference. Samba is file system agnostic.

---

### Post by Vegan on 2009-09-26
I have not experimented with alternative file systems outside the defaults. I wanted to get past the 16GB file limit that exists in some ext3 configurations.

A friend suggest ext4 has no such headaches but 9.04 still is weak with support.

I guess I will have to wait until I can migrate the disk with a later release.

---

### Post by falconindy on 2009-09-27
> **Vegan said:**
> I have not experimented with alternative file systems outside the defaults. I wanted to get past the 16GB file limit that exists in some ext3 configurations.

A friend suggest ext4 has no such headaches but 9.04 still is weak with support.

I guess I will have to wait until I can migrate the disk with a later release.
Sense. This makes none. 

Ext3 can be formatted with a block size of 2KiB, and the file size limit goes up to 256GiB.

Ext4 has been reliable since kernel 2.6.28. I assure you there are many people using Ext4 with 9.04 for everyday use (myself included).

To reiterate cariboo, Samba doesn't care what filesystem you use. It's your configuration which is at fault.

---

### Post by Vegan on 2009-09-28
Well when I formatted a 500GB disk with ext4 and tried to mount it, no luck, but when I used ext3 it works. Seems 9.04 is still not completely ready for ext4.:(

---

### Post by cariboo on 2009-09-29
With mount, you have to tell it what file system you are using:

```
sudo mount -t ext4 /dev/sda1 /media/disk
```

---

### Post by Vegan on 2009-09-29
I did that, and mount complained that it was an unsupported type.

At present the disk is now using ext3, i wanted to use ext4 as it has some desirable advantages for chess related projects.

---

