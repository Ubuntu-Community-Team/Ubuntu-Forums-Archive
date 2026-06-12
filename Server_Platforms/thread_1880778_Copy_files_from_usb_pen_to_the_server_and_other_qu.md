---
title: "Copy files from usb pen to the server and other question"
date: 2011-11-14
forum: Server Platforms
---

### Post by barezi6 on 2011-11-14
Hi everyone
i am using ubuntu server 8.04 LTS and i need to copy my website files to the server, how i can copy the usb pen files to the server? only need to know how i can see the usb pen because i know how to copy etc, but i dont find the usb pen files.


About other question, i know where i need to send my website files to show on internet, is /var/www but i dont know where i should send the database

Thanks

---

### Post by MG&amp;TL on 2011-11-14
You want to copy files from a memory stick to your server via command-line?

Something like (although it may differ slightly, I last did this on debian command-line):

```
sudo mkdir /mnt/usb
sudo fdisk -l
<look for your usb pen in the entries>
sudo mount /dev/<yourusbpen, probably /sdb> /mnt/usb
sudo cp /mnt/usb/yourfiles /var/www/
```

---

### Post by deltacomp on 2011-11-14
Other devices such as USB drives are found in the media directory. For example;

sudo cp /media/"USBDrivename"/(www) /var/www

will copy and replace the www folder. 

As to your other question, "the database"? I am not sure what you mean? If you are referring to the configuration files for the web address? Such as sites-available, those will go in /etc/apache2/sites-available

Good Luck

---

### Post by barezi6 on 2011-11-14
thanks for both the helps :) 


MG&TL

the code that you tell me works fine but when i try this line :
- sudo mount /dev/<yourusbpen, probably /sdb> /mnt/usb

the system tell it:

mount: you should specify the file system type


deltacomp

about my secound question i have a mysql database on my localhost computador, i use wampp and i will exporte this database to a external file and need to put this file on the server, to run it, but i dont know where i should put this file. what folder normally is used to put the database?

---

### Post by darkod on 2011-11-14
If the filesystem of your stick is fat32 it would probably be:

sudo mount -t fat32 /dev/sdb /mnt/usb

If it's ntfs, it's better to use ntfs-3g instead of mount, that will also give read/write support for the usb (if sometimes you are writing to it too):

sudo ntfs-3g /dev/sdb /mnt/usb

---

### Post by MG&amp;TL on 2011-11-14
It should tell you the filesystem with the fdisk -l command.

---

### Post by barezi6 on 2011-11-14
all done 

Thanks very much for the help people :)

---

### Post by MG&amp;TL on 2011-11-15
No prob. One last thing:

```
umount /dev/sdb
```

unmounts it safely.

---

