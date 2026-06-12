---
title: "apt using strange ip address - DNS hijacking?"
date: 2018-11-15
forum: Security
---

### Post by logarithms on 2018-11-15
I noted getting a few packages apt was using [http://151.205.0.13:80/data/0719f27c3c87769d/us.archive.ubuntu.com/ubuntu](http://151.205.0.13:80/data/0719f27c3c87769d/us.archive.ubuntu.com/ubuntu) bionic-updates/main 

```
apt install curl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libpython3-dev libpython3.6-dev libsdl-ttf2.0-0 python-ptyprocess python3-wheel python3.6-dev virtualbox-guest-dkms-hwe virtualbox-guest-utils-hwe
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed:
  curl
0 upgraded, 1 newly installed, 0 to remove and 23 not upgraded.
Need to get 159 kB of archives.
After this operation, 395 kB of additional disk space will be used.
Get:1 [http://151.205.0.13:80/data/0719f27c3c87769d/us.archive.ubuntu.com/ubuntu](http://151.205.0.13:80/data/0719f27c3c87769d/us.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 curl amd64 7.58.0-2ubuntu3.5 [159 kB]
Fetched 159 kB in 0s (629 kB/s)
Selecting previously unselected package curl.
(Reading database ... 183264 files and directories currently installed.)
Preparing to unpack .../curl_7.58.0-2ubuntu3.5_amd64.deb ...
Unpacking curl (7.58.0-2ubuntu3.5) ...
Setting up curl (7.58.0-2ubuntu3.5) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
```



[LIST=1]
[*]The only information I could find was it is owned by Verizon [https://db-ip.com/151.205.0.13](https://db-ip.com/151.205.0.13)
[*]I could not find any references to this address in /etc/apt/ 
[*]No reverse DNS related to this IP address comes back
[*]After I did an apt update and started looking into this ip address, apt stopped using it....
[/LIST]


Am I being paranoid or is this some what of a red flag? 

Thank you

---

### Post by CharlesA on 2018-11-15
Sounds like you are going through a proxy. I don't know if that's specific to Verizon or not.

Is that your external IP address by chance? 

Check this out: [https://www.serverlab.ca/tutorials/linux/administration-linux/how-to-set-the-proxy-for-apt-for-ubuntu-18-04/](https://www.serverlab.ca/tutorials/linux/administration-linux/how-to-set-the-proxy-for-apt-for-ubuntu-18-04/)

---

### Post by SeijiSensei on 2018-11-16
I see this from time to time doing updates.  I have Verizon Fios.  Doesn't seem to be an issue.

---

