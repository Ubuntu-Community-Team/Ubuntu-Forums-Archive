---
title: "Issue regarding the dual os in my laptop Win7/UbuntuStudio"
date: 2011-08-17
forum: Ubuntu Studio
---

### Post by abkandula on 2011-08-17
I installed UbuntuStudio on my laptop, planning to learn and try its environment,  and wanted to make it as dual os with Win7,

The thing for this thread is I dnt know what went wrong, The moment I start my Laptop, only Ubuntu starts rather to ask for an option to load one of these os's...

Please do help to recover my win7 and its related data...

help needed..

---

### Post by jejeman on 2011-08-17
Well, if you didn't format youre win7 partition, it should be fine.
Give us the output of the following command
```
sudo parted -l
```

---

### Post by abkandula on 2011-08-17
Number  Start   End    Size    Type      File system  Flags
 1      1049kB  496GB  496GB   primary   ext4         boot
 2      496GB   500GB  4257MB  extended
 5      496GB   500GB  4257MB  logical


Model: Linux device-mapper (crypt) (dm)
Disk /dev/mapper/cryptswap1: 4257MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  4257MB  4257MB  linux-swap(v1)

I am messed up with the partition system in ubuntu :(( need help to recover win7 and my lost data and make my system 
as dual boot... help needed..

---

### Post by jejeman on 2011-08-18
It looks like you didn't copy whole output, next time please do.
From the output you provided there is no windows partition. Obviosly you have formated it with ubuntu studio installation. Also you didn't make swap partition. You should seriously read some ubuntu install how to. And when you are absolutly shure do the install. Use virtual machine to practice.
Hm, not much you can do to recover. I don't know how partition table looked before ubuntu instalation, and what have changed. Writing new data erased old data.
You can try program TestDisk, and that's all I know about recovery formated data.

---

