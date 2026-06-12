---
title: "usb external drive - random device name?"
date: 2017-01-20
forum: Ubuntu, Linux and OS Chat
---

### Post by marchello_lippi2 on 2017-01-20
Hi all, 

My usb external drive was mounted before as /dev/sda1 and this name is in /etc/fstab > /dev/sda1       /mnt/wd         ntfs    defaults          0       0
Today I discovered that it is /dev/sdb1 already and managed to mount it using > sudo mount /dev/sdb1 /mnt/wd
Well, I don't know if tomorrow it would be /dev/sdc1 or something else? 
How do I distinguish it by script and then mount it using some variable? 
Please advise. 

> $ cat /etc/*release
PRETTY_NAME="Raspbian GNU/Linux 7 (wheezy)"
NAME="Raspbian GNU/Linux"
VERSION_ID="7"
VERSION="7 (wheezy)"
ID=raspbian
ID_LIKE=debian
ANSI_COLOR="1;31"
HOME_URL="http://www.raspbian.org/"
SUPPORT_URL="http://www.raspbian.org/RaspbianForums"
BUG_REPORT_URL="http://www.raspbian.org/RaspbianBugs"

---

### Post by marchello_lippi2 on 2017-01-20
Update: just discovered that my usb external drive is /dev/sdc1 already! So my question is really actual. 
Please advise.

---

### Post by vanadium on 2017-01-20
That is why UUID's were designed. Refer to the partition by UUID rather than by device name.
- You will find the UUID name in the output of the command "sudo blkid"
- In fstab, replace the device name, e.g. "/dev/sdc1" by the corresponding UUID from the blkid command, e.g. UUID="###..."

---

### Post by marchello_lippi2 on 2017-01-20
vanadium, 
thx, changed my /etc/fstab record to > UUID="84B46F79B46F6C9C" /mnt/wd         ntfs    defaults          0       0
will see how it works.

---

### Post by marchello_lippi2 on 2017-01-20
Sorry, cross-posting also here

[https://ubuntuforums.org/showthread.php?t=2346859&p=13596875#post13596875](https://ubuntuforums.org/showthread.php?t=2346859&p=13596875#post13596875)

ok, after some real-life testing I discovered that if mounted drive  became available under another device name, then > if [ -f  /mnt/folder1/file.txt ]; then echo 'true'; else echo 'false'; fi  gives **true**, but ls /mnt/folder1 gives i/o error. 
So, the question so far is, how do I check in script if ls /mnt/folder1 gives i/o error or not? 
Please advise.

---

### Post by oldos2er on 2017-01-20
Hello, this subforum is for chat, not support. Since you already have a thread in the support area, I will close this. Duplicates are not allowed; they are confusing for you and those trying to help you.

Thanks for your understanding.

---

