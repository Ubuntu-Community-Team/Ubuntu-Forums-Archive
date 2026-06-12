---
title: "cannot mount truecrypt encrypted NTFS"
date: 2009-09-11
forum: Security
---

### Post by jomex on 2009-09-11
i encrypted my whole Windows system with pre-boot authentication (sdc1, sdc2) but i can't access them in Ubuntu (truecrypt 6.2a)

i tried every permutation of:
used partition: sdc/sdc1/sdc2
pre-boot auth: yes/no
mount options: -t ntfs, -t ntfs-3g, --filesystem=ntfs, --filesystem=ntfs-3g

does anybody know whats wrong?

---

### Post by falconindy on 2009-09-13
> **jomex said:**
> does anybody know whats wrong?
Yeah, you encrypted your hard drive.

Encryption is always based off of a key, and in this case it was generated in Windows. I don't know how the Truecrypt software works, but if you want to be able to read the drive outside Windows, you need to get a hold of the key that was used in Windows to encrypt the drive.

---

### Post by jomex on 2009-09-13
isn't the key usually stored on the harddrive itself
enter password -> decrypt key with password -> decrypt harddrive with key
because this way you use the same key for the actual encryption and if you want to change the password, all you have to do is to encrypt the key again, which is only 4k instead of 400GB

---

### Post by falconindy on 2009-09-13
Like I said, I'm not entire familiar with the inner workings of Truecrypt. A little bit of poking around reveals that yeah... you can have just a key stored on the hard drive, or you can provide a keyfile as well. Did you create a keyfile?

source: [http://www.linux.com/archive/feature/59548](http://www.linux.com/archive/feature/59548)

Also, dumb question. Did you install truecrypt on your linux setup before trying to access the drive? It looks like truecrypt takes over mounting operations of encrypted drives.

---

### Post by jomex on 2009-09-13
nope, no keyfile, just a password

what do you mean with installed? i apt-get installed it :)

---

### Post by falconindy on 2009-09-13
Ok, so are you not seeing the drive on the output of `sudo lshw -C disk` or `sudo fdisk -l`?

---

### Post by jomex on 2009-09-14
lhsw and fdisk both successfully display the harddisk

[quote="sudo lhsw -c disk"]
       ...

description: ATA Disk
       product: SAMSUNG SP1604N
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sdc
       version: TM10
       serial: 0651J1FX115421
       size: 149GiB (160GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=3b4dd7d3

...
[/quote]

[quote="sudo fdisk -l"]
...

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3b4dd7d3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        6403    51432066    7  HPFS/NTFS
/dev/sdc2            6404       19457   104856255    7  HPFS/NTFS

...
[/quote]

---

### Post by falconindy on 2009-09-14
Sooo then what's the response of the following?
```
sudo truecrypt /dev/sdc1 /mount/point
```

---

### Post by jomex on 2009-09-15
> 
Incorrect keyfile(s) and/or password or not a TrueCrypt volume.

Note that pre-boot authentication passwords need to be typed in the pre-boot environment where **non-US keyboard layouts are not available**. Therefore, pre-boot authentication passwords must always be typed using the standard US keyboard layout (otherwise, the password will be typed incorrectly in most cases). However, note that you do NOT need a real US keyboard; you just need to change the keyboard layout in your operating system.


lol, that was it, german/english keyboard >_<
thx! :D

---

### Post by falconindy on 2009-09-15
> **jomex said:**
> lol, that was it, german/english keyboard >_<
thx! :D
Wow. Not at all the response I expected. Glad you figured it out.

---

### Post by jomex on 2009-09-16
hmm what did you expect? :)

---

### Post by falconindy on 2009-09-16
I expected it to work!

---

