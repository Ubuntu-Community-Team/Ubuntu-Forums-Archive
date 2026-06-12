---
title: "Error during install from direct download."
date: 2012-10-03
forum: Server Platforms
---

### Post by pstonge on 2012-10-03
Hey everyone

I am kind of new to Ubuntu, and I have been tasked at work to setup an Ubuntu Apache2, perl, and Squid server. Which I have been learning.

But I was installing Ubuntu 12.04 64-bit, downloaded right from the ubuntu webpage. I am running it through a VMware Workstation and I can install from an actual CD/DVD, that worked for me. I have also downloaded the iso 2 times thinking that maybe it was a bad download. 

I still keep getting this error; 

sorry cant figure out how to post picture in here lol)

##############################################################
[!!] Install the base system 
Cannot install Kernel
The installer cannot find a suitable kernel package to install.
###############################################################

any help on this would be thankful. 

Thanks 
Paul

---

### Post by hasan.akgoz on 2012-10-04
Hi;

Can you verify a burned CD/DVD ? md5 etc..

---

### Post by pstonge on 2012-10-04
Ya i was reading about that, but when i opened up the md5 file, like its huge...FULL of text, how to I find if its all there? 
 
Thanks

---

### Post by Wim Sturkenboom on 2012-10-05
[http://mirrors.melbourne.co.uk/ubuntu-releases/12.04/MD5SUMS](http://mirrors.melbourne.co.uk/ubuntu-releases/12.04/MD5SUMS)
or
[http://mirrors.melbourne.co.uk/ubuntu-releases/12.04.1/MD5SUMS](http://mirrors.melbourne.co.uk/ubuntu-releases/12.04.1/MD5SUMS)

e.g
```

*[COLOR="Red"]a8c667e871f48f3a662f3fbf1c3ddb17[/COLOR]* *ubuntu-12.04.1-server-amd64.iso

```
The part in italic red is the MD5sum for the specific iso. On the computer that you used to download the iso, you can verify it. If that's a Linux box, you can use *_md5sum_*. For Windows, there are utilities available like *_digestit_*.

Note: you verify the downloaded iso itself !

---

### Post by koenn on 2012-10-05
```
Cannot install Kernel
The installer cannot find a suitable kernel package to install.
##################################################
```

this could mean there's a mismatch between the OS you're trying to install and the hardware (CPU, ...) you're trying to install it on. 
As in : you might be trying to install 64 bit Ubuntu on a 32 bit machine, that sort of thing.

---

