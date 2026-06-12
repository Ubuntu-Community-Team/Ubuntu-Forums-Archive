---
title: "Probles Signing *.deb Packages BADSIG _gpgbuilder"
date: 2013-09-21
forum: Security
---

### Post by Linsys on 2013-09-21
I am running Ubuntu 12.04 and I am apparently having problems signing some packages and I am not sure why, others sign just fine. 

Here is an example of a package I need to sign, you can see from the commands below there is no signature on this package at all, then I sign it and the -s builder goes just fine; however when I try and verify the package I get the BADSIG _gpgbuilder. 

I have tried to create a new gpg key and still the same problem. I don't have this problem with all packages, some I've created work fine; however some I have created or found on the internet don't sign. I would guess the problem is with the package but I can install the packages just fine (if I don't use APT). 


[https://s3.amazonaws.com/tarn-repo/libjzmq_2.1.7_amd64.deb](https://s3.amazonaws.com/tarn-repo/libjzmq_2.1.7_amd64.deb)

root@usw2c-pri-apt-01:/var/tmp/packages# wget [https://s3.amazonaws.com/tarn-repo/libjzmq_2.1.7_amd64.deb](https://s3.amazonaws.com/tarn-repo/libjzmq_2.1.7_amd64.deb) 
--2013-09-21 14:33:10--  [https://s3.amazonaws.com/tarn-repo/libjzmq_2.1.7_amd64.deb](https://s3.amazonaws.com/tarn-repo/libjzmq_2.1.7_amd64.deb)
Resolving s3.amazonaws.com (s3.amazonaws.com)... 207.171.189.80
Connecting to s3.amazonaws.com (s3.amazonaws.com)|207.171.189.80|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 185764 (181K) [application/octet-stream]
Saving to: `libjzmq_2.1.7_amd64.deb'
 
100%[===========================================================================   ================================================================================  >] 185,764      422K/s   in 0.4s    
 
2013-09-21 14:33:11 (422 KB/s) - `libjzmq_2.1.7_amd64.deb' saved [185764/185764]
 
root@usw2c-pri-apt-01:/var/tmp/packages# ls
libjzmq_2.1.7_amd64.deb
root@usw2c-pri-apt-01:/var/tmp/packages# dpkg-sig -l libjzmq_2.1.7_amd64.deb
Processing libjzmq_2.1.7_amd64.deb...
root@usw2c-pri-apt-01:/var/tmp/packages# dpkg-sig -c libjzmq_2.1.7_amd64.deb
Processing libjzmq_2.1.7_amd64.deb...
root@usw2c-pri-apt-01:/var/tmp/packages# dpkg-sig -s builder libjzmq_2.1.7_amd64.deb
Processing libjzmq_2.1.7_amd64.deb...
Signed deb libjzmq_2.1.7_amd64.deb
root@usw2c-pri-apt-01:/var/tmp/packages# dpkg-sig -l libjzmq_2.1.7_amd64.deb
Processing libjzmq_2.1.7_amd64.deb...
builder
root@usw2c-pri-apt-01:/var/tmp/packages# dpkg-sig -c libjzmq_2.1.7_amd64.deb
Processing libjzmq_2.1.7_amd64.deb...
BADSIG _gpgbuilder

---

### Post by cariboo on 2013-09-23
Wouldn't it be better to contact Amazon about this problem?

---

### Post by Linsys on 2013-09-23
This has nothing to do with Amazon, while the server and the s3 bucket with this package is actually located in in S3 the issue exists with packages on my own Ubuntu desktop. When I sign some packages in this manner I have the same issue... so I am guessing I am doing something wrong here.

---

### Post by obiwanmikenolte on 2014-02-15
I was having this same issue, and it was an existing bug: [https://bugs.launchpad.net/ubuntu/+source/dpkg-sig/+bug/1156988](https://bugs.launchpad.net/ubuntu/+source/dpkg-sig/+bug/1156988)

---

### Post by marcosramos on 2014-08-26
Hi,

try the following:

1. extract the content of the deb file using
$ ar vx file.deb

2. check the file _gpgbuilder and that the data file has an extension .tar.gz

IF it has a .tar.xz means that the package was created using a dpkg-deb on Ubuntu which has default compress-type xz (check dpkg-deb's man page on option compress-type/-Z)

dpkg-sig checks for data.tar.gz (as if the file was created with compress-type gzip - default behaviour on Debian).

A small hack would be change the dpkg-sig Perl script to verify even if the data file has extension .tar.xz

Hope it helps.

Edit: someone made a nice patch [http://osdir.com/ml/ubuntu-bugs/2014-07/msg09103.html](http://osdir.com/ml/ubuntu-bugs/2014-07/msg09103.html) :)

---

