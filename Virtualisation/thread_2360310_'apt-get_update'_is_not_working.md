---
title: "'apt-get update' is not working"
date: 2017-05-03
forum: Virtualisation
---

### Post by abasu on 2017-05-03
Hi all,

I am new to Ubuntu. I have an Ubuntu VM. The details are as follows:

$ cat /etc/*release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.5 LTS"
NAME="Ubuntu"
VERSION="14.04.5 LTS, Trusty Tahr"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 14.04.5 LTS"
VERSION_ID="14.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"

Whenever I wanted to execute `apt-get update`, it gets stuck.
$ apt-get update
0% [Waiting for headers] [Waiting for headers]
0% [Waiting for headers] [Waiting for headers]


Steps which I have already done:
[COLOR=#686868][FONT=&amp]1. Temporary proxy session 
$ export http_proxy=[http://proxyip:proxyport]("http://proxyip:proxyport/") 
$ export https_proxy=[http://proxyip:proxyport]("http://proxyip:proxyport/") 
$ apt-get update[/FONT][/COLOR]
[COLOR=#686868][FONT=&amp]2. APT configuration file method 
$ vi /etc/apt/apt.conf.d/80proxy 
Acquire::http::Proxy "[http://proxyip:proxyport]("http://proxyip:proxyport/")"; 
Acquire::https::Proxy "[http://proxyip:proxyport]("http://proxyip:proxyport/")"; 
$ apt-get update[/FONT][/COLOR]
[COLOR=#686868][FONT=&amp]3. BASH rc method 
$ vi ~/.bashrc 
http_proxy=[http://proxyip:proxyport]("http://proxyip:proxyport/") 
https_proxy=[http://proxyip:proxyport]("http://proxyip:proxyport/") 
export http_proxy 
export https_proxy 
$ source ~/.bashrc 
$ apt-get update[/FONT][/COLOR]
[COLOR=#686868][FONT=&amp]4. Removed the sources.list 
$ mv /etc/apt/sources.list /tmp/ 
$ apt-get clean 
$ apt-get update

5. Removed /var/lib/apt/lists/*
$ rm -rf /var/lib/apt/lists/*
$ apt-get clean 
$ apt-get update
[/FONT][/COLOR]

This VM has intenet connection thru proxy. So I can wget packages from this VM. 
But I need apt-get to work because my script will use apt-get to install the required packages. Please help me out on this.

Have a great day.

Regards,
Arunava

---

### Post by ajgreeny on 2017-05-03
*Thread moved to **Virtualisation**.* which is more appropriate and a better fit.

What is the host OS and what are you using to run the VM?

---

### Post by abasu on 2017-05-03
Host OS details:
$ cat /etc/*release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.5 LTS"
NAME="Ubuntu"
VERSION="14.04.5 LTS, Trusty Tahr"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 14.04.5 LTS"
VERSION_ID="14.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"

$ uname -a
Linux test 4.4.0-66-generic #87~14.04.1-Ubuntu SMP Fri Mar 3 17:32:36 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

This VM has been created with Bosh ubuntu stemcell.
Please let me know if you want any specific details.

---

### Post by ajgreeny on 2017-05-04
Sorry but **Bosh ubuntu stemcell** means nothing to me and a search has not helped, so I will leave this to others.

---

### Post by ian-weisser on 2017-05-04
Have you tried [https://askubuntu.com/questions/257290/configure-proxy-for-apt](https://askubuntu.com/questions/257290/configure-proxy-for-apt) ?

---

### Post by abasu on 2017-05-05
I have already tried [https://askubuntu.com/questions/257290/configure-proxy-for-apt](https://askubuntu.com/questions/257290/configure-proxy-for-apt) but no help..

---

### Post by vasa1 on 2017-05-05
> **ajgreeny said:**
> Sorry but **Bosh ubuntu stemcell** means nothing to me and a search has not helped, so I will leave this to others.
I found [http://bosh.cloudfoundry.org/stemcells/](http://bosh.cloudfoundry.org/stemcells/)

---

### Post by ajgreeny on 2017-05-05
Thanks vasa1.

Still not much help to me however, as the only VMs that I know, or have ever used, are those I have personally installed from .iso image files using VBox.

---

