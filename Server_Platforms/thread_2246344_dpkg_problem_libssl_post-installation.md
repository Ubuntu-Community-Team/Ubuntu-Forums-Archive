---
title: "dpkg problem libssl post-installation"
date: 2014-09-30
forum: Server Platforms
---

### Post by Yu_Shu on 2014-09-30
Hello,

I wanted to upgrade libssl and openssl on my debian server to patch for heartbleed.

This is what I got:

[http://pastebin.com/TRGrXCr2](http://pastebin.com/TRGrXCr2)

> 
# apt-get install libssl1.0.0 openssl
...
Setting up libssl1.0.0:amd64 (1.0.1e-2+deb7u12) ...
dpkg: error processing libssl1.0.0:amd64 (--configure):
 subprocess installed post-installation script returned error exit status 128


Please help me
/Yu

---

### Post by slickymaster on 2014-09-30
*Moved to the ***Server Platforms*** sub-forum*

---

### Post by Vegan on 2014-09-30
try using a regular update

su apt-get update
su apt-get upgrade

then see if the desired components are installing properly

---

### Post by Yu_Shu on 2014-09-30
Thanks for your answer

I get the same thing, same output

---

### Post by slickymaster on 2014-09-30
Please try, one at a time:```
sudo apt-get -f install
sudo dpkg --configure -a
```

---

### Post by Yu_Shu on 2014-09-30
Thanks for the answer

This also just outputs the exact same thing as before

Is it something wrong with the post-installation script for libssl?

> Setting up libssl1.0.0:amd64 (1.0.1e-2+deb7u12) ...
dpkg: error processing libssl1.0.0:amd64 (--configure):
 subprocess installed post-installation script returned error exit status 128

All other packages fails because 'libssl is not configured yet'

---

### Post by slickymaster on 2014-09-30
Please try:```
sudo apt-get install --reinstall libssl1.0.0:amd64
```and copy/paste all the output you get into the thread, [using code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") for the effect.

---

### Post by ian-weisser on 2014-09-30
Ah, version confusion.
Heartbleed and many other security patches have already been backported to previous versions of libssl1.0.0.

In other words, if you are downloading libssl *from the upstream website*, use 1.1.0 as they recommend.
If you are using Ubuntu, simply ensure your security updates are enabled. Even though the version says 1.0.1-4ubuntu5.17 (12.04/Precise) or 1.0.1f-1ubuntu2.5 (14.04/Trusty), the heartbleed -and many other fixes- are implemented.

You DON'T need to install a non-Ubuntu package to get security updates. If you have the ubuntu-security repositories enabled, you already are patched against heartbleed.

For more details, dig out the CVE number of the specific vulnerability you want to know about, then look up that CVE number at [http://www.ubuntu.com/usn/](http://www.ubuntu.com/usn/)

---

### Post by Vegan on 2014-09-30
openssl is in the standard Ubuntu program library, its a pretty standard for all distributions

---

### Post by Yu_Shu on 2014-10-01
Thanks for all the answer


@slickymaster
Thanks, here is the output
```

# apt-get install --reinstall libssl1.0.0:amd64
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
26 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
E: Internal Error, No file name for libssl1.0.0:amd64

```
:o

@[COLOR=#000000]ian-weisser
I've downloaded the package from the website also, but it yield no difference from the one in the repo. Security channel is used and 1.0.0 is coming from there, I supposed that it was patched just as you said


@[/COLOR][COLOR=#000000]Vegan
I'm using the standard program library[/COLOR]

---

### Post by slickymaster on 2014-10-01
Let's try another approach.

I'm assuming that you are on a Trusty box, if you aren't please don't run these commands:```
sudo apt-get install --download-only libssl1.0.0:amd64
sudo dpkg -i /var/cache/apt/archives/libssl1.0.0_1.0.1f-1ubuntu2.5_amd64.deb
sudo apt-get update && sudo apt-get upgrade
sudo dpkg --audit
```And please copy/paste the output as done before.

---

### Post by Yu_Shu on 2014-10-01
Sorry I'm on debian.

I put a "exit 0" line in the begining of the post-installation script, to manually shedule a reboot and restart of services.

The bug may only exist on that debian-specific package.

---

