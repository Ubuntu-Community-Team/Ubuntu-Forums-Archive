---
title: "how to tell if swap is in use AND encrypted"
date: 2013-03-01
forum: Security
---

### Post by techiebiker on 2013-03-01
I had disk trouble, imaged / partition (/ included all mount points), installed new larger disk, restored / image and didn't set up swap partition.

Have since set up swap and believe it is in use. I want to know how to tell for certain if swap is encrypted? 

I used the following commands to get system information. They show swap in use but I can only infer that it is encrypted. If this confirms swap is encrypted will someone please explain why. If its not encrypted or can't tell please let me know what steps to encrypt and/or confirm encrypted swap.

```
#free
             total       used       free     shared    buffers     cached
Mem:       3013268    1894392    1118876          0      56400     663808
-/+ buffers/cache:    1174184    1839084
Swap:      3076092      24404    3051688
```

```
#swapon -s
Filename				Type		Size	Used	Priority
/dev/mapper/cryptswap1                  partition	3076092	24404	-1
```

```
# mount | column -t | grep -e "/dev\|crypt"
/dev/sda5            on  /                         type  ext4             (rw,errors=remount-ro)
udev                 on  /dev                      type  devtmpfs         (rw,mode=0755)
devpts               on  /dev/pts                  type  devpts           (rw,noexec,nosuid,gid=5,mode=0620)
/home/name/.Private  on  /home/name                type  ecryptfs         (ecryptfs_check_dev_ruid,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=xxxxx,ecryptfs_fnek_sig=zzzzz)
```
Given that mount shows /home/name/.Private as type ecryptfs  I'm thinking there should be some way to get similar confirmation of that swap is encrypted.


```
#df -h
Filesystem           Size  Used Avail Use% Mounted on
/dev/sda5            340G  144G  180G  45% /
udev                 1.5G  8.0K  1.5G   1% /dev
tmpfs                589M  868K  588M   1% /run
none                 5.0M     0  5.0M   0% /run/lock
none                 1.5G  480K  1.5G   1% /run/shm
none                 100M   28K  100M   1% /run/user
/home/name/.Private  340G  144G  180G  45% /home/name
```

```
#cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx /               ext4    errors=remount-ro 0       1
/dev/mapper/cryptswap1 none swap sw 0 0
```

---

### Post by bodhi.zazen on 2013-03-01
Swap is on and encrypted. From your question I am guessing you do not understand how LUKS (encryption) works.

The data is encrypted, but when the partition is in use it is decrypted. So if you boot a live CD, all of / and all of swap would be encrypted. You can verify this by booting a live CD and attempting to look at the contents of your partitions.

---

### Post by techiebiker on 2013-03-01
> **bodhi.zazen said:**
> Swap is on and encrypted. From your question I am guessing you do not understand how LUKS (encryption) works.

The data is encrypted, but when the partition is in use it is decrypted. So if you boot a live CD, all of / and all of swap would be encrypted. You can verify this by booting a live CD and attempting to look at the contents of your partitions.

I understand that part, encrypted when off, decrypted when on. (I'm not clear if it's dynamically decrypted on demand or in bulk. The former seems more likely o/w decrypting ~/* on login would take forever.)

What I don't see/understand in the listings of my first post is a direct association between swap and encryption. 

Seems straightforward with /home/name because "mount" shows /home/name/.Private as type ecryptfs and "df" shows /home/name/.Private mounted at /home/name.

With swap fstab shows /dev/mapper/cryptswap1 being type swap, but fstab is static whereas mount and df report state of the system running now. 

Is it just that I don't recognize what's reported does explicitly say swap is encrypted or is there some way to see it explicitly as the combination of df and mount do for /home/name?

---

### Post by Ranko Kohime on 2013-03-02
Perhaps this will confirm encryption for you?

```
sudo cryptsetup status /dev/mapper/**your_mapping_here**
```

---

### Post by HermanAB on 2013-03-05
Howdy,

To understand swap, you got to read the swapon man page.  It is a good one.

You can verify whether something is actually encrypted by trying to compress it.  Encrypted data won't compress.  So when the computer is running off a Live CD, you can read a block of the swap partition using dd and then try to zip it.  If the resulting zip is smaller, then the encryption is bad.  A chi-square test can be used to tell whether the encryption is good.  If the zip test shows compression, then there is no point in doing a chi-square test - you already know that the encryption is bad.

---

### Post by techiebiker on 2013-03-05
@Ranko
Yes, thank you. This shows the swap partition as active and encrypted.

Interesting though in /dev/mapper there's only one active device and that's the swap partition.

It's a bit confounding to me that confiming ~ is encrypted is confirmed by mount and that swap is encrypted is confirmed by cryptsetup.

Leads me to wondering about other things like...
- if home was a separate partition would both mount and cryptsetup show it encrypted?
- if a swap file were used instead of a swap partition would mount be the place to see that it's encrypted and cryptsetup wouldn't show that?

Rehtorical questions. Thanks for the help, I've marked the thread solved.

---

### Post by thnewguy on 2013-03-06
On Ubuntu home directories and swap space are encrypted using different methods, that's why you need two different ways to check. If you're curious, I recommend reading the manual pages for swap/swapon and luks encryption. Those two pieces of documentation will probably clear up all of your queries.

By the way, this statement, "Encrypted data won't compress" isn't true. Don't use compression as a test for encryption.

---

### Post by HermanAB on 2013-03-09
Zip is not a test for good compression.  It is a test for BAD compression. This is how the cryptoloop file system was discredited years ago.  If encrypted data would compress, it means that there are repeating structures that can be used to attack the cypher.  

You need statistical analysis to know whether the encryption is GOOD - e.g. Chi-Square.

---

