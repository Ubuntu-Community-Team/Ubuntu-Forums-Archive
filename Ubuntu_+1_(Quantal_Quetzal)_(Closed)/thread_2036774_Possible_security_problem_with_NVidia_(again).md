---
title: "Possible security problem with NVidia (again?)"
date: 2012-08-02
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by effenberg0x0 on 2012-08-02
**UPDATE:** This was fixed and version 304.32 was released. See [post #4]("http://ubuntuforums.org/showpost.php?p=12150422&postcount=4") for download links.

This was discussed in some boards (in my country) yesterday:
[http://permalink.gmane.org/gmane.comp.security.full-disclosure/86747](http://permalink.gmane.org/gmane.comp.security.full-disclosure/86747)

It was even posted here (but on the Café, I didn't get it) and didn't grab too much attention:
[http://ubuntuforums.org/showthread.php?t=2036447](http://ubuntuforums.org/showthread.php?t=2036447)

People in some local forums have successfully managed to exploit it (or so they say - trustno1). I thought it would be important to bring this up here, since we're testers. 

Considering we know nothing about the NVidia binary blob, and it has happened in the recent past, I'm inclined to consider the possibility as true. 

<rant>
And, if that's the case, we should remember that simply because our Olympus people trusted NVidia would fix their problems quick and refused to roll back a couple versions in the final ISO, PP was released with broken drivers, LP was quickly flooded with posts about it (more work for the triage fest), we got LP bugs with 10's of dups and 100's of submissions (still going strong!), an unnecessary mess.
</rant>

Regards,
Effenberg

---

### Post by ventrical on 2012-08-02
<rant>

The most recent sudo-apt-get update/upgrade pulled nividia-current *AGAIN* and installed the new 3.5.0-7 kernel .. so lots of breakage going on.
<rant>

---

### Post by Harry33 on 2012-08-03
> **ventrical said:**
> <rant>

The most recent sudo-apt-get update/upgrade pulled nividia-current *AGAIN* and installed the new 3.5.0-7 kernel .. so lots of breakage going on.
<rant>

The most recent nvidia-current (302.17-0ubuntu2) is for xorg-video-abi-12 (=xserver 1.12).

I use that one and there is no issues with the latest kernel.
The only real issue (upstream) is the newest (in proposed repo) xserver 1.13.
Nvidia (from xorg-edgers PPA) supports xserver 1.13, but does not support 3D in it.

---

### Post by effenberg0x0 on 2012-08-04
IT looks like NVidia fixed it:
[http://www.phoronix.com/scan.php?page=news_item&px=MTE1Mzk](http://www.phoronix.com/scan.php?page=news_item&px=MTE1Mzk)

Here are the links for 304.32 installers:

**32-bit**
wget [ftp://download.nvidia.com/XFree86/Linux-x86/304.32/NVIDIA-Linux-x86-304.32.run](ftp://download.nvidia.com/XFree86/Linux-x86/304.32/NVIDIA-Linux-x86-304.32.run)

**64-bit**
wget [ftp://download.nvidia.com/XFree86/Linux-x86_64/304.32/NVIDIA-Linux-x86_64-304.32.run](ftp://download.nvidia.com/XFree86/Linux-x86_64/304.32/NVIDIA-Linux-x86_64-304.32.run)

Regards,
Effenberg

---

### Post by paul_in_london on 2012-08-04
> **effenberg0x0 said:**
> IT looks like NVidia fixed it:
[http://www.phoronix.com/scan.php?page=news_item&px=MTE1Mzk](http://www.phoronix.com/scan.php?page=news_item&px=MTE1Mzk)

Here are the links for 304.32 installers:

**32-bit**
wget [http://us.download.nvidia.com/XFree86/Linux-x86/304.32/NVIDIA-Linux-x86-304.32.run](http://us.download.nvidia.com/XFree86/Linux-x86/304.32/NVIDIA-Linux-x86-304.32.run)

**64-bit**
wget [http://us.download.nvidia.com/XFree86/Linux-x86_64/304.32/NVIDIA-Linux-x86_64-304.32.run](http://us.download.nvidia.com/XFree86/Linux-x86_64/304.32/NVIDIA-Linux-x86_64-304.32.run)

Regards,
Effenberg

It's available from xorg-edgers:

```
paul@quantal-64:~$ apt-cache policy nvidia-current                              
nvidia-current:
  Installed: 304.32-0ubuntu1~xedgers~quantal1
  Candidate: 304.32-0ubuntu1~xedgers~quantal1
  Version table:
 *** 304.32-0ubuntu1~xedgers~quantal1 0
        500 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ quantal/main amd64 Packages
        100 /var/lib/dpkg/status
     302.17-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/restricted amd64 Packages
paul@quantal-64:~$ 
```

---

