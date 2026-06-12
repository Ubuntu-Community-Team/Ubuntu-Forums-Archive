---
title: "zsync - what am i doing wrong?"
date: 2024-01-10
forum: Ubuntu Development Version
---

### Post by grahammechanical on 2024-01-10
I have the noble ISO image in the Downloads folder. I also have the noble zsync meta control file in the Downloads folder. I cd into the Downloads folder and run this command

```
graham@UbuntuDev:~/Downloads$ zsync https://cdimage.ubuntu.com/daily-live/current/noble-desktop-amd64.iso.zsync
```

and I get this error message.

> failed on url [https://cdimage.ubuntu.com/daily-live/current/noble-desktop-amd64.iso.zsync](https://cdimage.ubuntu.com/daily-live/current/noble-desktop-amd64.iso.zsync)
could not read control file from URL [https://cdimage.ubuntu.com/daily-live/current/noble-desktop-amd64.iso.zsync](https://cdimage.ubuntu.com/daily-live/current/noble-desktop-amd64.iso.zsync)

I am using this guide

[https://help.ubuntu.com/community/ZsyncCdImage](https://help.ubuntu.com/community/ZsyncCdImage)

Source of both the ISO image and the zsync meta file

[URL="https://cdimage.ubuntu.com/daily-live/current/"]https://cdimage.ubuntu.com/daily-live/current/

[/URL]
Both file have permissions of Read and Write to Owner and Group. Which is me, of course.

Regards

---

### Post by oldfred on 2024-01-10
I have downloaded both Kubuntu & Lubuntu. I have to change names of ISO once downloaded as it has same name.

zsync [http://cdimage.ubuntu.com/kubuntu/daily-live/current/noble-desktop-amd64.iso.zsync](http://cdimage.ubuntu.com/kubuntu/daily-live/current/noble-desktop-amd64.iso.zsync)
zsync [http://cdimage.ubuntu.com/lubuntu/daily-live/current/noble-desktop-amd64.iso.zsync](http://cdimage.ubuntu.com/lubuntu/daily-live/current/noble-desktop-amd64.iso.zsync)

I note the it is http not https?

---

### Post by Irihapeti on 2024-01-10
Try it using http in the URL (not https) and it should work.

You don't need to download the .zsync file separately. That happens automatically when you issue the command.

---

### Post by ajgreeny on 2024-01-10
You need to change the https URL and use simple http in its place.
For reasons I've not understood or even tried to, the https version never works.

However, just for your information, I only ever use zsync to update an iso file I already have on disk to save a huge amount of download data which saves a lot of time.
For example
```
zsync http://cdimage.ubuntu.com/xubuntu/daily-live/current/noble-desktop-amd64.iso.zsync -i /home/user/Downloads/ISOs/xubuntu-noble-desktop-Jan01-amd64.iso -o /home/user/Downloads/ISOs/xubuntu-noble-desktop-Jan10-amd64.iso
```
So if you want to update your iso file you do not need to download the whole 3G file again, just the parts that have changes since the last download; that is why I change the names of the iso files by adding the date.

---

### Post by grahammechanical on 2024-01-11
Thank you!

It worked. Changing the address from https:// to http://  worked. 

I downloaded the zsync meta file because I follow the rule: If nothing works - get desperate.

This explains

> You don't need to download the .zsync file separately. That happens automatically when you issue the command.

why two zsync meta files were downloaded. I know I only downloaded one meta file.

Learning all the time.

Regards

---

