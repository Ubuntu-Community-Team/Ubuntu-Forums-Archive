---
title: "Strange Message of the Day problem"
date: 2011-06-11
forum: Server Platforms
---

### Post by kroq-gar78 on 2011-06-11
Hello Ubuntu Forums Community,

I have installed Ubuntu Server on my 2TB external hard drive some time ago, and have recently seen a strange problem. when I log in, the MOTD pops up and there are TWO of them, as shown here:

```
Linux nas-ubuntu 2.6.32-32-generic-pae #62-Ubuntu SMP Wed Apr 20 22:10:33 UTC 2011 i686 GNU/Linux
Ubuntu 10.04.2 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

  System information as of Sat Jun 11 20:57:14 CDT 2011

  System load:  0.15               Temperature:          0 C
  Usage of /:   13.1% of 28.83GB   Processes:            127
  Memory usage: 4%                 Users logged in:      0
  Swap usage:   0%                 IP address for wlan0: 192.168.2.101

  Graph this data and manage this system at https://landscape.canonical.com/

Ubuntu 10.04.2 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

  System information as of Sat Apr 23 17:23:02 CDT 2011

  System load:  0.01              Temperature:          48 C
  Usage of /:   6.4% of 28.83GB   Processes:            104
  Memory usage: 14%               Users logged in:      1
  Swap usage:   0%                IP address for wlan0: 192.168.2.101

  Graph this data and manage this system at https://landscape.canonical.com/

```As you can see, the first one is more recent (from today) and the bottom one is from april. How do I change it? Do I just edit /etc/motd? Furthermore, do you possibly know why this happened?

Thanks in advance.

Sincerely,
kroq-gar78

P.S. Also, why does it say that the temperature is 0?

---

### Post by papibe on 2011-06-11
It's a [bug]("https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/768360") that's being worked on.

Regards.

---

### Post by kroq-gar78 on 2011-06-11
thanks. so do I just delete the 2nd message? and what about the 1st line? it says April, too.

---

### Post by papibe on 2011-06-11
So far, the trick would be:
```
$ sudo rm -rf /etc/motd.tail
$ sudo touch /etc/motd.tail
```
So basically creating and empty motd.tail file.

Regards.

---

### Post by kroq-gar78 on 2011-06-15
> **papibe said:**
> So far, the trick would be:
```
$ sudo rm -rf /etc/motd.tail
$ sudo touch /etc/motd.tail
```
So basically creating and empty motd.tail file.

Regards.
yay thanks that did the trick. marking thread as solved.

---

