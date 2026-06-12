---
title: "mountall:plymouth command failed"
date: 2012-08-04
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by ronacc on 2012-08-04
I have an install of precise that has been updated to qunatal at repo open and daily since , for the last couple of days I cannot log into the desktop , when I try it flips to a terminal for a few seconds and shows severa lines of text the last one of which is .  mountall:plymouth command failed   . then flips back to the login screen . I can ctrl>alt>F1 at the login screen , log iin to the terminal and update/install/etc without problems just can't log in to the DT . 

my install on another partition of yesterdays daily ( amd64 desktop ) does not show this behavior , I can login and it runs normaly .

any Ideas on how to fix the updated precise ?

---

### Post by ronacc on 2012-08-04
reinstalled mountall and plymouth  , message changed but same result , cant log in to DT , message now reads mountall : disconnected from plymouth .

---

### Post by effenberg0x0 on 2012-08-04
Hi Ron, 

It's hard to say, I'm not having this problem with Precise. I'm inclined to say VGA drivers/modules, etc when X won't load. Maybe it's best if you use the terminal and have a look at some logs using cat, nano, etc.

/var/log/kern.log
/var/log/xorg.0.log
~/.xsession-errors

I have a command inside my ~/.bash_aliases I named "checklog". It searches some of the log files for errors, warnings, etc and outputs only the lines with this errors to a separate and timestamped log file in my home directory. Then I usually just use nano to read the file it created and see what's interesting.I thought you might find it useful.

```
alias checklog="sudo grep 'warning\|oops\|segfault\|error' -iHnr /var/log/dmesg /var/log/syslog /var/log/kern.log /var/log/Xorg.0.log ~/.xsession-errors > ~/checklog-$(date +%d-%m-%y_%H:%M:%S).log"
```

Regards,
Effenberg

---

### Post by ronacc on 2012-08-04
thanks I'll give that a shot .

---

### Post by ronacc on 2012-08-04
I am getting a warning about resource temporarily unavailable on xserver :0

also many other errors that may or may not be meaningful .

I'm using the nvidia driver from xorg-eddgers on that install  how do I switch back to nouveau from the console ?

---

### Post by effenberg0x0 on 2012-08-04
I use the NVIdia binary installer and no non-standard PPAs, so it's a little off my league. Other guys here know about this, for sure. 

Anyway, to achieve what you want, I would probably consider safer to ppa-purge xorg-edgers, apt update/upgrade using standard sources, see if it goes OK and fix broken deps if any, and then apt-get install xserver-xorg-video-nouveau.

```
sudo ppa-purge xorg-edgers
sudo apt-get update && sudo apt-get upgrade 
apt-get install xserver-xorg-video-nouveau
```

Then if things were screwed up after boot, I'd probably look into the logs again, to look for something nvidia or nouveau. Then I would also use lsmod | grep nv and lsmod | grep nouveau to see if nvidia or nouveau modules were being loaded at all. In case this was messed up, I would go to /etc/modprobe.d/, check if nvidia or nvidia-current were blacklisted or not, etc, and fix it accordingly. 

But this is all just guessing, I mean, there's likely an easier way. Let's just wait for better advice here.

Regards,
Effenberg

---

### Post by ronacc on 2012-08-04
I was wondering if ppa-purge would do it . its sure doing something ! 75 packages removed 26 downgraded and 1 installed , updating and upgrading now , a little adventure is good for the soul if not the install :lolflag:

---

### Post by ronacc on 2012-08-04
it must have been the nvidia driver because that fixed it , the upgrade put back all the xorg stuff that the purge removed ( repo versions not the ppa stuff) and reboot autologged me in and it seems to be working of with the 3.5.0-8 kernel .

thanks .

---

### Post by effenberg0x0 on 2012-08-04
Glad to hear it :) I knew ppa-purge was the way to go, but I was not sure apt would manage to fix packages and depd after it. I never trust apt, maybe I should.

I just installed NVIDIA-Linux-x86_64-304.32.run from the link I posted in the other thread. This is the binary NVidia installer. As usual, no problem at all with install and things are running smooth with QQ fully upgraded (and 3.5.0-7 kernel).

Regards,
Effenberg

---

### Post by ronacc on 2012-08-04
I usually use the Nvidia .run myself ,I don't trust jockey/dkms  ,but this time in the spirit of testing I decided to go with it . So I guess it serves me right to get my fingers burned ,  of course throwing in the PPA didn't help much either .

---

