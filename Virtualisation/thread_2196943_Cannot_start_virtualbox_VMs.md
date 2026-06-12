---
title: "Cannot start virtualbox VMs"
date: 2014-01-01
forum: Virtualisation
---

### Post by pet546 on 2014-01-01
I'm completely new to this. I uninstalled and reinstalled virtualbox to the new latest version (4.3.6) available on virtualbox.org.  The installation went fine but the moment I try and run my machines it comes up with the error about not having the kernel driver.  If I run the command sudo /etc/init.d/vboxdrv setup  in the terminal I get this in the log:>  DKMS: add completed. Failed to install using DKMS, attempting to install without Makefile:183: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR= and run Make again. Stop.   I have also run in the terminal > sudo apt-get install build-essential linux-headers-`uname -r` the error I get is:>  Package linux-headers-3.8.0-33-generic is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source  E: Package 'linux-headers-3.8.0-33-generic' has no installation candidate   I have looked on all the forums I could none provide a solution for me, hence my positing here.   Other information:  Ubuntu 13.10 (upgraded from 13.04) 64 bit >    peter@peter-desktop:~$ dpkg --get-selections | grep linux-headers linux-headers-3.11.0-13                install linux-headers-3.11.0-13-generic            install linux-headers-3.11.0-14                install linux-headers-3.11.0-14-generic            install linux-headers-generic                install    If anyone needs any other information I will be glad to assist.

---

### Post by howefield on 2014-01-01
Looks like you are using the 13.04 kernel and not the newer 13.10 one that would come with saucy, what does the following terminal command

```
uname -a
```

give you ?

---

### Post by pet546 on 2014-01-02
Here is the output:

> Linux peter-desktop 3.8.0-33-generic #48-Ubuntu SMP Wed Oct 23 09:16:58 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

Hope that helps. Thanks for replying:D.

---

### Post by howefield on 2014-01-02
[http://ubuntuforums.org/showthread.php?t=2194395&p=12876970&viewfull=1#post12876970](http://ubuntuforums.org/showthread.php?t=2194395&p=12876970&viewfull=1#post12876970)

Installing linux-generic worked for the poster.

---

### Post by pet546 on 2014-01-04
Okay thank you will give it a try and let you know if it worked.

---

### Post by pet546 on 2014-01-04
Thank you, yes this solved my problem!:D

---

