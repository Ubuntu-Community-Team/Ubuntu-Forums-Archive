---
title: "Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2014-11-18
forum: Server Platforms
---

### Post by khangsf on 2014-11-18
Hello,

Could you please tell me know to fix error message below? I am running Ubuntu server 14.04. The server has been running fine until another administrator tried to install Python 2.7 on it.
He tried to remove it but the situation got messier. Now smb doesn't work and package manager is also not working. 

I have tried all the following commands but no luck

sudo apt-get remove install-info

 sudo apt-get clean

 udo apt-get update

 sudo apt-get upgrade
sudo apt-get -f install



The following NEW packages will be installed:
  python2.7-minimal
0 upgraded, 1 newly installed, 0 to remove and 7 not upgraded.
4 not fully installed or removed.
Need to get 1,190 kB of archives.
After this operation, 3,482 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/main python2.7-minimal amd64 2.7.6-8 [1,190 kB]
Fetched 1,190 kB in 0s (1,447 kB/s)          
(Reading database ... 128621 files and directories currently installed.)
Preparing to unpack .../python2.7-minimal_2.7.6-8_amd64.deb ...
new installation of python2.7-minimal; /usr/lib/python2.7/site-packages is a directory
which is expected a symlink to /usr/local/lib/python2.7/dist-packages.
please find the package shipping files in /usr/lib/python2.7/site-packages and
file a bug report to ship these in /usr/lib/python2.7/dist-packages instead
aborting installation of python2.7-minimal
dpkg: error processing archive /var/cache/apt/archives/python2.7-minimal_2.7.6-8_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/python2.7-minimal_2.7.6-8_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Could you please advise how to remove python 2.7 and get rid of the "Sub-process /usr/bin/dpkg returned an error code (1)" error?

Thanks,
K

---

