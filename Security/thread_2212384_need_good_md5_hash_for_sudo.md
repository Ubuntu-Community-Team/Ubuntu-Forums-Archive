---
title: "need good md5 hash for sudo"
date: 2014-03-20
forum: Security
---

### Post by rebeltaz on 2014-03-20
Before I tell rkhunter to ignore the fact that the "properties have changed" warning in regards to sudo (by issuing the --popupd parameter), I would like to be sure. Could someone either provide me with a md5 checksum for sudo (1.8.3p1-1ubuntu3.6) from Ubuntu 12.04 LTS Server or explain to me how to find a clean value with which to compare my own? Thank you. 

BTW - mine is: de6380daaa142c01df328fb8dd6e43bb  /usr/bin/sudo

---

### Post by CharlesA on 2014-03-20
Same version I have installed.

```
ii  sudo                                   1.8.3p1-1ubuntu3.6                      Provide limited super user privileges to specific users
```

```
56c83980cd46ac029a2f01a1f2eda0a7  /usr/bin/sudo

```

---

### Post by rebeltaz on 2014-03-20
hmmm.... that's not good then, huh? Since the checksums don't match....

---

### Post by CharlesA on 2014-03-21
> **rebeltaz said:**
> hmmm.... that's not good then, huh? Since the checksums don't match....

Uh, yep.

I just checked another 12.04 box and it has the same md5sum as my other post. Did you get any other hash mismatch errors ?

---

### Post by rebeltaz on 2014-03-21
I got a few 

```
...exists on the system, but it is not present in the rkhunter.dat file.
```
and
```
...it is whitelisted for the 'script replacement' check.
```
warnings. 

The only other thing out of place is this:
```
[23:05:15] Warning: The command '/usr/bin/unhide.rb' has been replaced by a script: /usr/bin/unhide.rb: Ruby script, ASCII text
```

I do not understand. I did a fresh install from a newly downloaded ISO directly from Ubuntu. I enabled ufw and only allowed ports 80 and 443 from the out side world. I did allow ports 22, 21 and 8888 (for ispConfig) from two of my local computers only. I made sure that ssh did not allow root login. I changed my login passwords to totally different strings with alphanumeric characters as well as symbols. Last night I disallowed ssh login with password altogether and created RSA pairs. While apache has been running for a few days, the sites themselves were only last night put back online....

---

### Post by CharlesA on 2014-03-21
See here:
[http://askubuntu.com/questions/250006/rootkits-should-i-be-concerned](http://askubuntu.com/questions/250006/rootkits-should-i-be-concerned)

---

### Post by rebeltaz on 2014-03-21
Before I posted here, I did find a lot of discussion similar to that page, and it looks from there as if the warnings aren't too worrysome, and I can understand that based on how rkhunter is determining suspicious files, but I am a little concerned about the sudo hash difference.

---

### Post by CharlesA on 2014-03-21
Check the hash of the deb files:
[https://launchpad.net/ubuntu/+source/sudo/1.8.3p1-1ubuntu3.6](https://launchpad.net/ubuntu/+source/sudo/1.8.3p1-1ubuntu3.6)

/var/cache/apt/archives if I remember right.

---

### Post by rebeltaz on 2014-03-21
hmmm... the only files/checksums I see on that site are two .gz files and a .dsc file (whatever that is), while the sudo* file in .../apt/archives is a .deb file. 

BUT....

Just for the heck of it, I ran md5 on the sudo file on my laptop 12.04 (desktop version instead of server), which dpkg shows as version 1.8.3p1-1ubuntu3.4 (instead of 3.6) and it shows the exact same hash as the 3.6 version on my server. 

When I ssh'd into the server, I did notice that apt is not upgrading the packages:
  linux-headers-generic-lts-saucy linux-image-generic-lts-saucy

Is it possible that even though dpkg lists sudo as v3.6 (on the server), until I do a local apt-get upgrade that file won't be updated properly and is still showing the hash of the older version?

Tomorrow when I have local access to the server, I'll apt upgrade and run md5 again.

---

### Post by Lars Noodén on 2014-03-21
You can also use the package debsums to check the MD5 checksums for installed packages.

---

### Post by rebeltaz on 2014-03-21
> **Lars Noodén said:**
> You can also use the package debsums to check the MD5 checksums for installed packages.


I did run that and it says that the checksum is ok...

I ran the upgrade and I am still getting the same hash as before. I just don't understand how that's possible?

---

### Post by CharlesA on 2014-03-21
Do you still have the deb file in /var/cache/apt/archives?

You can reinstall it from there or just download it from the repos and reinstall it. 
[http://www.cyberciti.biz/faq/debian-ubuntu-linux-reinstall-a-package-using-apt-get-command/](http://www.cyberciti.biz/faq/debian-ubuntu-linux-reinstall-a-package-using-apt-get-command/)

---

### Post by rebeltaz on 2014-03-21
It is still in archives, but I did a reinstall anyway and.... I still get the same md5 hash as before.

---

### Post by CharlesA on 2014-03-21
wut.

What's the md5sum of the deb?

---

### Post by rebeltaz on 2014-03-21
> **CharlesA said:**
> wut.

What's the md5sum of the deb?

```

071c41aa6676d57de3d58e409a810c48  /var/cache/apt/archives/sudo_1.8.3p1-1ubuntu3.6_i386.deb

```

---

### Post by CharlesA on 2014-03-21
Uh I just downloaded it from  [https://launchpad.net/~ubuntu-security/+archive/ppa/+build/5802002/+files/sudo_1.8.3p1-1ubuntu3.6_i386.deb](https://launchpad.net/~ubuntu-security/+archive/ppa/+build/5802002/+files/sudo_1.8.3p1-1ubuntu3.6_i386.deb)

071c41aa6676d57de3d58e409a810c48  sudo_1.8.3p1-1ubuntu3.6_i386.deb

Looks right...

---

### Post by rebeltaz on 2014-03-21
That's just odd then that the reinstalled sudo gives a different hash. I guess I'll just let it go. Thanks...

---

