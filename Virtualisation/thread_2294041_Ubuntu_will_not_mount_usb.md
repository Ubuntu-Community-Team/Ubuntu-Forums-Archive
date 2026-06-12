---
title: "Ubuntu will not mount usb"
date: 2015-09-09
forum: Virtualisation
---

### Post by james166 on 2015-09-09
I broke my usb drive. I did some... interesting things with it, and I've run into some issues.

Basically, I used VMWare player on windows 7 to make a vm with windows vista, and I had it install directly to the usb drive. Took forever, but it worked. (why I did it that way I can explain, but it's kind of a long story.) So the vm was successfully made, but I ran into an issue when I tried to suspend the vm, i.e. make a copy of the system and store it so I can go directly back to where I was before.

Turns out I had formatted it as fat32, and the image file was larger than 4gb. So I shut down the vm without saving the image, and in Windows used ```
convert E: /fs:ntfs
``` It ran for a moment, and then returned an error about the disk. So I then in Windows I ran ```
chkdsk /r
``` and it went through and fixed the disk (supposedly). Again in Windows I then ran ```
convert E: /fs:ntfs
``` and everything went wonderfully. I started the vm back up and it worked great, and it suspended just fine. So I unmounted the drive, and transferred it over to my laptop which is running Ubuntu Gnome 15.04. I plugged it in and started Vmware, directed it to the necessary files, and boom it started up. The issues started when I went back to the previous computer with windows 7. I tried to boot up the vm, but it simply came up with an error, and would just shut back down. So I went back to my laptop and it worked fine, back to the desktop wouldn't work, back to laptop and now it wouldn't show up on Ubuntu. Tried making a file and mounting it at the point 
```
sudo mkdir -p /media/usb
``` and then 
```
~$ sudo mount /dev/sdb1 /media/usb
NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around
```?"
So I'm a bit stuck, I've run a few other commands to get info, but I don't know much about this, so I don't know what to do with it. I apologize for the length of the post. Any help is much appreciated.

---

### Post by ajgreeny on 2015-09-09
I was a bit lost by your post's large block of text so I have formatted the text to improve readability, and have also edited a few points of content where you talk of the commands ```
convert E: /fs:ntfs
``` and ```
chkdsk /r
``` which I believe must have been in Windows, but please check that and let me know if I'm wrong, as I do not use Windows or VMware player.

I have also moved the thread to the Virtualisation section as it seems more appropriate.

---

