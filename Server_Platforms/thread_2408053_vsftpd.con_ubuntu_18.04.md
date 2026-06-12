---
title: "vsftpd.con ubuntu 18.04"
date: 2018-12-13
forum: Server Platforms
---

### Post by cod3r- on 2018-12-13
Hello I have the following problem how can I see this directory* etc/vsftpd.conf  os ububtu server 18.04 *I installed vsftpd  but when I try to edit the configuration file there is nothing *sudo nano /etc/vsftpd.conf   *I'll be grateful to someone to say where I can find this file

---

### Post by slickymaster on 2018-12-13
*Thread moved to **Server Platforms**.*

---

### Post by cod3r- on 2018-12-13
> **slickymaster said:**
> *Thread moved to **Server Platforms**.*

Thanks for the move!!!

---

### Post by cod3r- on 2018-12-13
additional...

```


 service vsftpd status
&#9679; vsftpd.service - vsftpd FTP server
   Loaded: loaded (/lib[COLOR=#a52a2a][/COLOR]/systemd/system/vsftpd.service; enabled; vendor preset: enabled)
   [COLOR=#b22222]**Active: failed**[/COLOR] (Result: exit-code) since Wed 2018-12-12 14:37:08 UTC; 19h ago
 Main PID: 1019 (code=exited, status=2)


Dec 12 14:37:07 ubuntu systemd[1]: Starting vsftpd FTP server...
Dec 12 14:37:08 ubuntu systemd[1]: Started vsftpd FTP server.
Dec 12 14:37:08 ubuntu systemd[1]: vsftpd.service: Main process exited, code=exited, status=2/INVALIDARGUMENT
Dec 12 14:37:08 ubuntu systemd[1]: vsftpd.service: Failed with result 'exit-code'.




```

---

### Post by LHammonds on 2018-12-13
I documented how to install it on Ubuntu 16.04 but have yet to migrate it to 18.04.

You can [look here](http://hammondslegacy.com/forum/viewtopic.php?f=40&t=228) and see if anything I documented helps you with your setup.

LHammonds

---

### Post by cod3r- on 2018-12-14
There is nothing in this directory  [COLOR=#3C3B37][FONT=&amp]/etc/vsftpd.conf


[IMG]("http://prikachi.com/images/338/9459338y.jpg")



```
[/FONT][/COLOR]apt -y install vsftpd
Reading package lists... Done
Building dependency tree
Reading state information... Done
vsftpd is already the newest version (3.0.3-9build1).
The following packages were automatically installed and are no longer required:
  libcgi-fast-perl libcgi-pm-perl libencode-locale-perl libevent-core-2.1-6
  libfcgi-perl libhtml-parser-perl libhtml-tagset-perl libhtml-template-perl
  libhttp-date-perl libhttp-message-perl libio-html-perl
  liblwp-mediatypes-perl libtimedate-perl liburi-perl
Use 'apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
```


[COLOR=#3C3B37][FONT=&amp]
[/FONT][/COLOR]

---

### Post by LHammonds on 2018-12-14
vsftpd 3.0.3 is the same version I documented on Ubuntu 16.04.  Ubuntu has not changed where it stores config files (/etc) in 18.04 so I would think it "should" be there.

I have some phone calls I need to make this morning (recently unemployed) and will later install it on a fresh copy of 18.04 and see what it does.

LHammonds

---

### Post by cod3r- on 2018-12-14
do not have such a vsftpd.conf file in a directory  [COLOR=#3C3B37]/etc/vsftpd.conf

[img]("http://prikachi.com/images/433/9459433l.jpg")

[/COLOR]In my opinion, this file at 18.04 should be with the slow name   ***vsftpd.conf_orig***   as in the picture.?

---

### Post by LHammonds on 2018-12-14
> **cod3r- said:**
> do not have such a vsftpd.conf file in a directory  [COLOR=#3C3B37]/etc/vsftpd.conf

[img]("http://prikachi.com/images/433/9459433l.jpg")

[/COLOR]In my opinion, this file at 18.04 should be with the slow name   ***vsftpd.conf_orig***   as in the picture.?

I understand it is not behaving as expected...which is why I will see for myself what happens when I install it on a fresh 18.04 server.

---

### Post by cod3r- on 2018-12-14
> **LHammonds said:**
> I understand it is not behaving as expected...which is why I will see for myself what happens when I install it on a fresh 18.04 server.


Okay, I'm glad to share the result. :)  cheers

---

### Post by LHammonds on 2018-12-14
The file showed up for me.

Here, you can see me installing vsftpd:

```

# apt install vsftpd
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  vsftpd
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 115 kB of archives.
After this operation, 334 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 vsftpd amd64 3.0.3-9build1 [115 kB]
Fetched 115 kB in 1s (115 kB/s)
Preconfiguring packages ...
Selecting previously unselected package vsftpd.
(Reading database ... 112516 files and directories currently installed.)
Preparing to unpack .../vsftpd_3.0.3-9build1_amd64.deb ...
Unpacking vsftpd (3.0.3-9build1) ...
Processing triggers for ureadahead (0.100.0-20) ...
Setting up vsftpd (3.0.3-9build1) ...
Created symlink /etc/systemd/system/multi-user.target.wants/vsftpd.service &#8594; /lib/systemd/system/vsftpd.service.
Processing triggers for systemd (237-3ubuntu10.9) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
Processing triggers for ureadahead (0.100.0-20) ...

```

This took about 10 seconds.  Immediately after I listed any vsftpd files in /etc.

```

# ls -l /etc/vsftp*
-rw-r--r-- 1 root root 5850 Feb  5  2018 /etc/vsftpd.conf

```
The config file showed up as you can see.

Here is my server info for documentation purposes:

```
# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 18.04.1 LTS
Release:        18.04
Codename:       bionic
```

```
# uname -a
Linux srv-ubuntu 4.15.0-42-generic #45-Ubuntu SMP Thu Nov 15 19:32:57 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
```

LHammonds

---

### Post by cod3r- on 2018-12-14
with me wrong name means ..   

```


 ls -l /etc/vsftp*
-rw-r--r-- 1 root root 5850 Feb  5  2018 /etc/vsftpd.conf_orig




```

---

### Post by LHammonds on 2018-12-14
Type this in:

```

sudo apt purge vsftpd
sudo rm /etc/vsftp*
sudo apt install vsftpd
ls -l /etc/vsftp*

```

---

### Post by cod3r- on 2018-12-14
> **LHammonds said:**
> Type this in:

```

sudo apt purge vsftpd
sudo rm /etc/vsftp*
sudo apt install vsftpd
ls -l /etc/vsftp*

```


10x bro!!!!

---

### Post by LHammonds on 2018-12-14
> **cod3r- said:**
> 10x bro!!!!
Are you saying you did this already?  If so, we need to step back and find out what is different with your OS compared to mine.

I install Ubuntu using the alternative / traditional installer so I can use LVM.  If you used the "live" image, maybe there is something different with it.

I also never do the in-place upgrade when going from one major version to another (e.g. My 18.04 servers are not upgraded from 16.04)

I also have only ever installed Ubuntu inside virtual environments such as Oracle VirtualBox on Windows or VMware vSphere on ESXi.  However, I do not think the OS and applications will "act" differently like this if it is installed on a physical or virtual.

LHammonds

---

### Post by Morbius1 on 2018-12-14
According to: [https://www.internetslang.com/10X-meaning-definition.asp](https://www.internetslang.com/10X-meaning-definition.asp)
>  The definition of 10X is "Thanks"
From the same source:
>  The definition of BRO is "Brother, buddy, friend"
I suspect it means: Thank you very much sir and/or madam.

---

### Post by cod3r- on 2018-12-15
> **LHammonds said:**
> Are you saying you did this already?  If so, we need to step back and find out what is different with your OS compared to mine.

I install Ubuntu using the alternative / traditional installer so I can use LVM.  If you used the "live" image, maybe there is something different with it.

I also never do the in-place upgrade when going from one major version to another (e.g. My 18.04 servers are not upgraded from 16.04)

I also have only ever installed Ubuntu inside virtual environments such as Oracle VirtualBox on Windows or VMware vSphere on ESXi.  However, I do not think the OS and applications will "act" differently like this if it is installed on a physical or virtual.

LHammonds


Hello ,
  I will try it on Monday if she is working on the suggestion you mentioned above...  i will notify you of the result as soon as possible

---

### Post by cod3r- on 2018-12-17
another problem arose...

```

sudo service vsftpd restart
sudo service vsftpd restartsudo: unable to resolve host myke: Resource temporarily unavailable



```

---

