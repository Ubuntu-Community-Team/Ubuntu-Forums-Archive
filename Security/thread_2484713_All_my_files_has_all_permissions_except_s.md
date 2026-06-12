---
title: "All my files has all permissions except s"
date: 2023-03-07
forum: Security
---

### Post by dsnp on 2023-03-07
Hi,

I just noticed that whenever I create a new file, it always has 777 rights. I have no idea when I started to have this issue because ironically I just noticed this after taking the first lesson on Secure Programming. How can I revert this behaviour, or is it normal and I am panicking for nothing?

```

touch some.txt
ls -l

```

Outputs:
```

total 0
-rwxrwxrwx 1 user user 0 Mar  7 21:36 some.txt

```

I used touch here but the following commands also ended up in the same behaviour:
[LIST]
[*]vim file.txt 
[*]echo "some text" > file.txt 
[/LIST]

---

### Post by dsnp on 2023-03-07
Okay, I just noticed that I was having this issue only on my external drive (nfts). I am not having this issue on my local drive.

---

### Post by DuckHook on 2023-03-08
NTFS is not native to Linux. So, in the interest of safety, Ubuntu does not try to monkey with NTFS permissions, hence the default to 777. If Ubuntu were to take a more restrictive approach, some files/directories could be locked out when subsequently accessing from Windows.

If you want it to have different default permissions, you need to set this when the NTFS filesystem is mounted. This is done by setting its mask to your own specifications rather than just accepting the default.

Example:```
sudo mount -t ntfs -o rw,auto,user,fmask=0022,dmask=0000 /dev/path&#8209;to&#8209;ntfs /mnt/your&#8209;choice
```&#8230;where 0022 is changed to whatever mask you want. The above will yield files with 755 permissions.

It bears noting that working with NTFS filesystem is not a good idea in Linux. TBH, NTFS is a lousy filesystem that is decades old and showing both its age and its limitations. Linux works with tons of filesystems that are far more efficient, flexible, powerful and safe: ext2/3/4, zfs, xfs, btrfs, even reiserfs among others. Unless you are forced to use NTFS, don't.

---

### Post by dsnp on 2023-03-08
Oh, that explains the problem very clearly. Unfortunately, I am required to use Windows at some times, so I can't really apply your tip, though I will keep it in mind. Thanks for the fast reply!

---

### Post by DuckHook on 2023-03-08
> **dsnp said:**
> Oh, that explains the problem very clearly. Unfortunately, I am required to use Windows at some times, so I can't really apply your tip, though I will keep it in mind. Thanks for the fast reply!
Your quandary is common to those who must switch between Windows and Linux.

I have only very rudimentary familiarity with Windows, so take what follows with a large dose of salt, but…

I believe that Windows has an ext4 utility. This allows it to read and write ext4 files. If you will be working primarily in Linux, then it may be worthwhile to keep your data stored in the ext4 format rather than NTFS. Just another option to consider. I have no idea what your use case is, so can't advise you on particulars.

---

