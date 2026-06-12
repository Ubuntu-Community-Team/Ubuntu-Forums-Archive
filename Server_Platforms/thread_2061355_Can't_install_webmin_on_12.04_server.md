---
title: "Can't install webmin on 12.04 server"
date: 2012-09-22
forum: Server Platforms
---

### Post by fblauer on 2012-09-22
I am trying to install webmin on Ubuntu server 12.04. I get to "unpacking webmin ..." and it never completes. I can't figure out what could be causing this problem, since other people seem to be able to install on ubuntu 12.04?? Any help would be much appreciated.

---

### Post by Extol11 on 2012-09-22
I've always installed it from the CLI and it's never given me any problems.
Download the .tar.gz file and unzip it. Then, in a terminal, navigate to the folder where the unzipped folder is. For example:
cd /home/me/...
then run the command sh setup.sh and it will start installing and asking you about the simple configuration stuff. Everything should be left in default. See if that works.

---

### Post by fblauer on 2012-09-22
OK, I was able to get it working now. There was a previous version which didn't get installed properly, and that's why it was getting stuck. Thanks for the help.

---

### Post by cybercity@localhost on 2012-09-23
mark thread as solved.

---

### Post by mjitkop on 2012-11-24
> **Extol11 said:**
> I've always installed it from the CLI and it's never given me any problems.
Download the .tar.gz file and unzip it. Then, in a terminal, navigate to the folder where the unzipped folder is. For example:
cd /home/me/...
then run the command sh setup.sh and it will start installing and asking you about the simple configuration stuff. Everything should be left in default. See if that works.

I'm having a problem installing it too. The way I started doing it was by downloading the DEB package for it and I used the scp command to copy the file onto the server. No problem to this point. 

The problem right now is that I can't get past the installation of the dependencies:

```
basement@UbuntuServer:~$ sudo apt-get install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl libapt-pkg-perl apt-show-versions
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libpam-runtime is already the newest version.
perl is already the newest version.
The following NEW packages will be installed:
  apt-show-versions libapt-pkg-perl libauthen-pam-perl libio-pty-perl libnet-ssleay-perl
The following packages will be upgraded:
  openssl
1 upgraded, 5 newly installed, 0 to remove and 59 not upgraded.
1 not fully installed or removed.
Need to get 883 kB of archives.
After this operation, 1,318 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  libnet-ssleay-perl openssl libauthen-pam-perl libio-pty-perl libapt-pkg-perl apt-show-versions
Install these packages without verification [y/N]? y
Err http://us.archive.ubuntu.com/ubuntu/ precise/main libnet-ssleay-perl i386 1.42-1build1
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ precise-updates/main openssl i386 1.0.1-4ubuntu5.5
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ precise/universe libauthen-pam-perl i386 0.16-2build2
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ precise/main libio-pty-perl i386 1:1.08-1build2
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ precise/main libapt-pkg-perl i386 0.1.25build2
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ precise/universe apt-show-versions all 0.17
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libn/libnet-ssleay-perl/libnet-ssleay-perl_1.42-1build1_i386.deb  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_1.0.1-4ubuntu5.5_i386.deb  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/liba/libauthen-pam-perl/libauthen-pam-perl_0.16-2build2_i386.deb  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libi/libio-pty-perl/libio-pty-perl_1.08-1build2_i386.deb  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/liba/libapt-pkg-perl/libapt-pkg-perl_0.1.25build2_i386.deb  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/a/apt-show-versions/apt-show-versions_0.17_all.deb  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?



basement@UbuntuServer:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  apt-show-versions libapt-pkg-perl libauthen-pam-perl libio-pty-perl libnet-ssleay-perl
The following NEW packages will be installed:
  apt-show-versions libapt-pkg-perl libauthen-pam-perl libio-pty-perl libnet-ssleay-perl
0 upgraded, 5 newly installed, 0 to remove and 60 not upgraded.
1 not fully installed or removed.
Need to get 364 kB of archives.
After this operation, 1,318 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  libnet-ssleay-perl libauthen-pam-perl libio-pty-perl libapt-pkg-perl apt-show-versions
Install these packages without verification [y/N]? y
Err http://us.archive.ubuntu.com/ubuntu/ precise/main libnet-ssleay-perl i386 1.42-1build1
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ precise/universe libauthen-pam-perl i386 0.16-2build2
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ precise/main libio-pty-perl i386 1:1.08-1build2
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ precise/main libapt-pkg-perl i386 0.1.25build2
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ precise/universe apt-show-versions all 0.17
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libn/libnet-ssleay-perl/libnet-ssleay-perl_1.42-1build1_i386.deb  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/liba/libauthen-pam-perl/libauthen-pam-perl_0.16-2build2_i386.deb  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libi/libio-pty-perl/libio-pty-perl_1.08-1build2_i386.deb  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/liba/libapt-pkg-perl/libapt-pkg-perl_0.1.25build2_i386.deb  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/a/apt-show-versions/apt-show-versions_0.17_all.deb  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?



basement@UbuntuServer:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.1 LTS
Release:    12.04
Codename:    precise
basement@UbuntuServer:~$ 
```
Does the tar.gz file include all dependencies? What are the exact commands to uncompress it properly?

Thank you  in advance for your help.

---

### Post by darkod on 2012-11-24
Yes, the tar.gz should include all. The instructions to extract are probably on their website, but if I remember correctly it's something like:
tar -zxvf filename

---

