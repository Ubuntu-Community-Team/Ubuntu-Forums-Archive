---
title: "Harddisk I/O error"
date: 2016-05-08
forum: Server Platforms
---

### Post by ellehoejmagnus on 2016-05-08
hey there i got an ubuntu server which i just installed a new harddisk in, the problem is that i cant seem to get access to it, i can see it using lshw -short and a couple of other tools but i cant access it or make partitions on it. the harddrive was a used one i had lying around i thought i could get some use out of, so i plugged it into my desktop pc and it actually started up so i put it over into my server and then i couldnt access it anymore. 
i have tried looking on some other threads but none seem to fit my problem or give me a solution.
if anybody could help thatd be great

---

### Post by volkswagner on 2016-05-08
Check your BIOS to see if SATA (or whatever type of drive interface you have) ports are enabled.

You can also check demsg for any errors or drive connection information.

---

### Post by nerdtron on 2016-05-08
What is the server hardware? You probably have a RAID controller on the server? If yes, you'll need to access the BIOS or the hardware RAID config utility on the server to configure the hard drive.

If will help if you post the output of the commands below. And tell us too if the size of the hard drive, just to make see if it's on the list:
```
 
sudo lsblk
sudo lshw -C Disk
sudo dmidecode | grep -i raid
sudo parted -l

```

---

