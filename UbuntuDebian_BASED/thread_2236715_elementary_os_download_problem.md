---
title: "elementary os download problem"
date: 2014-07-28
forum: Ubuntu/Debian BASED
---

### Post by mulceber on 2014-07-28
I just recently installed elementary OS as a dual-boot with Windows on a  Lenovo ideapad Y500 and am encountering some difficulties. I know that  the ideapads have been a lot of trouble for the linux community in the  past because of secureboot, but I was able to get past that by switching  the machine to legacy boot and installing from a pen drive. I had the  new OS up and running and it seemed to be getting along with the  hardware reasonably well, but then this morning, when I tried to install  dropbox via the software center, I ran into my problem: dropbox reached  about 90% done and was at the "applying changes" phase, and then it  wouldn't go any further. It didn't crash and the computer didn't freeze,  the download just stopped making progress. I went to have breakfast,  and when I came back it was still the same. I rebooted my machine and  tried again. Software center still refused to make any progress on  downloading. I tried going to the terminal so that I could install  dropbox directly, thinking if I could just finish the install then maybe  the problem on Software Center would go away. The terminal gave me the  following message:

```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
```

I did so, and the following happened:

```
Setting up nautilus-dropbox (0.7.1-2) ...
Dropbox is the easiest way to share and store your files online. Want to learn more? Head to http://www.dropbox.com/
Downloading Dropbox... 100%
```

When it reached 100%, it simply stopped working, much like software center did. The irony is that dropbox is listed as one of the applications downloaded on my system, but whenever I click on it, it asks for authentication to run it as a super user and then fails to open when I do so.

Can anyone help me fix this problem? At this point I don't really care about dropbox, as I have other clouds already downloaded. I just want to be able to use the terminal/software center again.

---

### Post by ibjsb4 on 2014-07-28
Try
```
sudo apt-get -f install
```
That is the command to fix broken packages.

---

### Post by mulceber on 2014-07-28
Hi, Thanks for the response. I just tried what you suggested and got the same response where I was instructed to input 'sudo dpkg --configure -a', only to have that not work. Does anyone have any other ideas?

---

### Post by ibjsb4 on 2014-07-29
You have a dpkg backup in /var/lib/dpkg called status-old.  Try swapping it out with the current status.  Just rename current status, do not delete it.

Are you running any third party software?
```
ls /etc/apt/sources.list.d/*.list
```

---

### Post by mulceber on 2014-07-29
> **ibjsb4 said:**
> You have a dpkg backup in /var/lib/dpkg called status-old.  Try swapping it out with the current status.  Just rename current status, do not delete it.

Are you running any third party software?
```
ls /etc/apt/sources.list.d/*.list
```


Thanks for the suggestion - I actually ended up doing a reinstall last night, so the problem has gone away. If it comes back again (which it very well may, given that I'm using the same hardware and the same software) I'll try what you suggested. Thank you for your time and the help!

---

