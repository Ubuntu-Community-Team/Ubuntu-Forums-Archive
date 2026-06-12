---
title: "Failed upgrade to 11.10"
date: 2012-07-30
forum: System76 Support
---

### Post by frogspawn on 2012-07-30
[SIZE=5][SIZE=4]I have a Wildebeest desktop and am attempting to Upgrade   to Natty Narwall 11.10 using the upgrade manager.[/SIZE][/SIZE]
 

 [SIZE=4]Because I have a very slow IP a friend provided me with a  disk to preform this upgrade which I inserted. I subsequently found out  that this disk was 11.10 and a 64 bit AMD version. This disk appears to  be inappropriate for the current version and processor. [/SIZE] 
 

 [SIZE=4]During the download process, using the upgrade manager,  the computer asks me to insert this disk. Clicking on continue allows me  to continue the downloa , however, at the end it aborts after 1500  files and six hours indicating that three files failed to fetch. Two of  these appear to be Amd 64.deb files and are requested, I suspect because  the CD was inserted. [/SIZE] 
 

 [SIZE=4]I have tried this both ways, on several occasions both by inserting the disk and by bypassing it to no avail.[/SIZE]
 

 [SIZE=4]Can you please tell  me what I need to do to solve this problem.[/SIZE]
 

 [SIZE=4]Thanks in advance for your help.[/SIZE]
 [SIZE=4]Bill[/SIZE]

---

### Post by isantop on 2012-07-30
> **frogspawn said:**
> [SIZE=5][SIZE=4]I have a Wildebeest desktop and am attempting to Upgrade   to Natty Narwall 11.10 using the upgrade manager.[/SIZE][/SIZE]
 

 [SIZE=4]Because I have a very slow IP a friend provided me with a  disk to preform this upgrade which I inserted. I subsequently found out  that this disk was 11.10 and a 64 bit AMD version. This disk appears to  be inappropriate for the current version and processor. [/SIZE] 
 

 [SIZE=4]During the download process, using the upgrade manager,  the computer asks me to insert this disk. Clicking on continue allows me  to continue the downloa , however, at the end it aborts after 1500  files and six hours indicating that three files failed to fetch. Two of  these appear to be Amd 64.deb files and are requested, I suspect because  the CD was inserted. [/SIZE] 
 

 [SIZE=4]I have tried this both ways, on several occasions both by inserting the disk and by bypassing it to no avail.[/SIZE]
 

 [SIZE=4]Can you please tell  me what I need to do to solve this problem.[/SIZE]
 

 [SIZE=4]Thanks in advance for your help.[/SIZE]
 [SIZE=4]Bill[/SIZE]

The disk is used to perform a fresh installation. It's possible to do an upgrade from it through update manager, but we don't recommend that.

I would get a 12.04 CD and do a fresh installation from that. 11.10 is out of date by now, and 12.04 has many more features and much better performance.

Also, the AMD64 version is the only 64-bit version of Ubuntu. It works just fine on all 64-bit Intel and AMD processors.

---

### Post by frogspawn on 2012-07-30
Thank you for your help. Does one lose the existing software with a fresh installation. I don't want to have to reinstall all of it if there is a way to avoid it. Probably a stupid question but I would rather keep what I have than have to go through the monumental task of recreating it.

---

### Post by isantop on 2012-07-30
> **frogspawn said:**
> Thank you for your help. Does one lose the existing software with a fresh installation. I don't want to have to reinstall all of it if there is a way to avoid it. Probably a stupid question but I would rather keep what I have than have to go through the monumental task of recreating it.

It does, but you can easily back up and restore the software you have. Just run this command in a terminal before installation:

```
sudo dpkg --get-selections > ~/software
```

Then install. Afterwards, use these commands to restore your software:

```
sudo dpkg --set-selections < selections
sudo apt-get update && sudo apt-get -u dselect-upgrade
```

---

