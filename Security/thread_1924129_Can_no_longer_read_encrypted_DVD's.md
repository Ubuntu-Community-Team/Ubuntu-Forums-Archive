---
title: "Can no longer read encrypted DVD's"
date: 2012-02-12
forum: Security
---

### Post by lduperval on 2012-02-12
Hi,

Some time ago, I encrypted some data on DVDs and now I would like to access that data. The data was encrypted some time ago using this command:

```

mkisofs -r foldername | aespipe -e aes256 > someisoname.iso

```

Then it was burnt to a DVD. Before, I could mount those DVDs with this command:

```

sudo mount -t iso9660 /dev/dvd1 /mnt/dvd -o loop=/dev/loop0,encryption=aes256

```

When I use the above command, I get:

```

mount: stolen loop=/dev/loop0

```

So I tried the following :

```

$ sudo mount -t iso9660 /dev/dvd1 /mnt/dvd -o loop,encryption=aes256
Password: 
ioctl: LOOP_SET_STATUS: No such file or directory

$ sudo mount -t iso9660 /dev/dvd1 /mnt/dvd -o loop,encryption=aes
Password: 
mount: wrong fs type, bad option, bad superblock on /dev/loop5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


```

The last one is what I used to get when I gave an incorrect password, but I'm sure I've got the password right.

Can anybody explain to me what could be wrong?

The logs say this:

```

Feb 12 02:26:17 hplaptop kernel: [38501.945306] ISOFS: Unable to identify CD-ROM format.
Feb 12 02:26:17 hplaptop kernel: [38501.949591] sr 8:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 12 02:26:17 hplaptop kernel: [38501.949609] sr 8:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
Feb 12 02:26:17 hplaptop kernel: [38501.949622] sr 8:0:0:0: [sr1]  Add. Sense: Logical block address out of range
Feb 12 02:26:17 hplaptop kernel: [38501.949637] sr 8:0:0:0: [sr1] CDB: Read(10): 28 00 00 20 13 80 00 00 02 00
Feb 12 02:26:17 hplaptop kernel: [38501.949659] end_request: I/O error, dev sr1, sector 8408576
Feb 12 02:26:17 hplaptop kernel: [38501.949667] quiet_error: 22 callbacks suppressed
Feb 12 02:26:17 hplaptop kernel: [38501.949674] Buffer I/O error on device sr1, logical block 1051072
Feb 12 02:26:17 hplaptop kernel: [38501.949716] Buffer I/O error on device loop5, logical block 4204288

```

Thanks,

L

---

### Post by lduperval on 2012-02-12
Let me add that I followed this tutorial, originally:

[http://ubuntuforums.org/showthread.php?t=579173](http://ubuntuforums.org/showthread.php?t=579173)

If that tutorial is no longer valid, or if something has changed, the tutorial should be updated, or at the very least, a warning should be put so that others don't have the same issue.

L

---

### Post by needhelppeeps on 2012-02-12
Hopefully, someone can help you. I would recommend always immediately testing access to any backup data to make sure it is accessible when using a new system. I test my backup media by doing a test restore of a random folder every month. This helps ensure my encryption keys are working and that the media is still good.

---

### Post by lduperval on 2012-02-12
Well, after a good night's sleep I tried again and it turns out that around 3:00 AM, there are a lot of problems between a keyboard and a chair... like uninstalled packages... 

:|

L

---

