---
title: "serv content from another box"
date: 2006-08-21
forum: Server Platforms
---

### Post by mmcclure79 on 2006-08-21
I want to know how to serve content from IIS to a site ran on Apache 2. IS this even possible. At firist  Itried mounting shared folders from the windows box to /var/www, but Kubuntu wouldn't mount the samba file systems. something about not compatable with a particuliar version of something.

before you wonder why I would even think about doing this, my webserver has limited space and I want to serve up stuff from my 250 GB usb drive on the windows box (wife's computer).

---

### Post by chrisfay on 2006-08-21
Are you sure you followed the correct steps to mount the folder?

You have to have the samba files system first:
sudo apt-get install smbfs

Then follow this: [http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html](http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html)

I was having problems mounting my share until I realized I didn't have smbfs. Then it worked perfectly. 

You can also add the share into /etc/fstab so it mounts on boot. Much nicer especially if you plan on serving files from the share; would suck to forget to mount it and your site goes down.

---

### Post by mmcclure79 on 2006-08-22
and here I assumed that since I could browse to it and even open files from the folder that I had smbfs installed. Go figure I didn't.

installed it and  verything works flawlessly. Thanks.

---

### Post by chrisfay on 2006-08-22
I had the same problem...Glad it worked for you too!!

---

