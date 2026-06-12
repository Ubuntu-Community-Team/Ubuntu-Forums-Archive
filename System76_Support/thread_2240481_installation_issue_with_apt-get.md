---
title: "installation issue with apt-get"
date: 2014-08-20
forum: System76 Support
---

### Post by heinrich2 on 2014-08-20
Hey,

I am currently running into an issue with apt-get install openssh-server. I am running ubuntu 12.10 in virtual box. Seems like it could be a repository issue, could someone point me into the right direction?

I have tried sudo apt-get update several times and my server is selected as the main one.

Here what i am getting:

user@user-VirtualBox:~$ sudo apt-get install openssh-server openssh-client
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openssh-client is already the newest version.
The following extra packages will be installed:
  ncurses-term ssh-import-id
Suggested packages:
  rssh molly-guard openssh-blacklist openssh-blacklist-extra monkeysphere
The following NEW packages will be installed:
  ncurses-term openssh-server ssh-import-id
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 775 kB of archives.
After this operation, 3,066 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  ncurses-term openssh-server ssh-import-id
Install these packages without verification [y/N]? Y
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main ncurses-term all 5.9-10ubuntu1
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main openssh-server i386 1:6.0p1-3ubuntu1
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main ssh-import-id all 2.12-0ubuntu1
  404  Not Found [IP: 91.189.92.201 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/n/ncurses/ncurses-term_5.9-10ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/ncurses/ncurses-term_5.9-10ubuntu1_all.deb)  404  Not Found [IP: 91.189.92.201 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-server_6.0p1-3ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-server_6.0p1-3ubuntu1_i386.deb)  404  Not Found [IP: 91.189.92.201 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/s/ssh-import-id/ssh-import-id_2.12-0ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/s/ssh-import-id/ssh-import-id_2.12-0ubuntu1_all.deb)  404  Not Found [IP: 91.189.92.201 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

Thank you for your help in advanced.

---

### Post by overdrank on 2014-08-20
Hi and welcome, please do not create multiple threads on the same issue. Duplicate _[here]("http://ubuntuforums.org/showthread.php?t=2240484")_. Thread closed.

---

