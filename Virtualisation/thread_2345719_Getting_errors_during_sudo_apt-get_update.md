---
title: "Getting errors during sudo apt-get update"
date: 2016-12-07
forum: Virtualisation
---

### Post by mgomalley on 2016-12-07
Hi,

I am using VERSION="16.04 LTS (Xenial Xerus)" installed as a VM on my windows laptop.

I am having problems as I do an apt-get to install java

```
sudo apt-get update
sudo apt-get install openjdk-7-jre
```Here is a snapshot of the errors I get below. Any ideas what could be wrong here?

```
$ sudo apt-get update
Get:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [11.7 kB]                                 
Err:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease                                           
  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
Get:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial InRelease [11.7 kB]                      
Err:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial InRelease

  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
.
.
Reading package lists... Done
W: The repository 'https://apt.dockerproject.org/repo ubuntu-xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/xenial/InRelease](http://gb.archive.ubuntu.com/ubuntu/dists/xenial/InRelease)  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
.
.
$ sudo apt-get install openjdk-7-jre
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package openjdk-7-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'openjdk-7-jre' has no installation candidate
```

Thanks in advance for your help,
Mike

---

### Post by howefield on 2016-12-07
> **mgomalley said:**
> E: Package 'openjdk-7-jre' has no installation candidate

As for the last error, as it explains the package doesn't exist in the repositories.

Do a 

```
apt-cache policy openjdk-*-jre
```

to see which openjdk packages have installation candidates.

---

### Post by mgomalley on 2016-12-07
Hi,

Here is the output

```
$ apt-cache policy openjdk-*-jre
openjdk-6-jre:
  Installed: (none)
  Candidate: (none)
  Version table:
openjdk-7-jre:
  Installed: (none)
  Candidate: (none)
  Version table:
$
```

Thanks

---

### Post by slickymaster on 2016-12-07
Take a look at this AskUbuntu thread: [How do I install openjdk 7 on Ubuntu 16.04 or higher?]("http://askubuntu.com/questions/761127/how-do-i-install-openjdk-7-on-ubuntu-16-04-or-higher")

---

### Post by mgomalley on 2016-12-08
Hi

When I try the suggestion you mentioned, i get the following some Exceptions & Erorrs

```
softwareproperties.shortcuts.ShortcutException: Cannot add PPA: 'ppa:~openjdk-r/ubuntu/ppa'.
ERROR: '~openjdk-r' user or team does not exist.
Error: 'ppa:openjdk-r/ppa' invalid
```


The following is the complete list of what I get

```
# sudo add-apt-repository ppa:openjdk-r/ppa 
Traceback (most recent call last):
  File "/usr/lib/python3.5/urllib/request.py", line 1243, in do_open
    h.request(req.get_method(), req.selector, req.data, headers)
  File "/usr/lib/python3.5/http/client.py", line 1106, in request
    self._send_request(method, url, body, headers)
  File "/usr/lib/python3.5/http/client.py", line 1151, in _send_request
    self.endheaders(body)
  File "/usr/lib/python3.5/http/client.py", line 1102, in endheaders
    self._send_output(message_body)
  File "/usr/lib/python3.5/http/client.py", line 934, in _send_output
    self.send(msg)
  File "/usr/lib/python3.5/http/client.py", line 877, in send
    self.connect()
  File "/usr/lib/python3.5/http/client.py", line 1260, in connect
    server_hostname=server_hostname)
  File "/usr/lib/python3.5/ssl.py", line 376, in wrap_socket
    _context=self)
  File "/usr/lib/python3.5/ssl.py", line 748, in __init__
    self.do_handshake()
  File "/usr/lib/python3.5/ssl.py", line 984, in do_handshake
    self._sslobj.do_handshake()
  File "/usr/lib/python3.5/ssl.py", line 629, in do_handshake
    self._sslobj.do_handshake()
ssl.SSLError: [SSL: TLSV1_ALERT_ACCESS_DENIED] tlsv1 alert access denied (_ssl.c:645)
```


During handling of the above exception, another exception occurred:


```
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 102, in _get_https_content_py3
    lp_page = urllib.request.urlopen(request, cafile=LAUNCHPAD_PPA_CERT)
  File "/usr/lib/python3.5/urllib/request.py", line 162, in urlopen
    return opener.open(url, data, timeout)
  File "/usr/lib/python3.5/urllib/request.py", line 465, in open
    response = self._open(req, data)
  File "/usr/lib/python3.5/urllib/request.py", line 483, in _open
    '_open', req)
  File "/usr/lib/python3.5/urllib/request.py", line 443, in _call_chain
    result = func(*args)
  File "/usr/lib/python3.5/urllib/request.py", line 1286, in https_open
    context=self._context, check_hostname=self._check_hostname)
  File "/usr/lib/python3.5/urllib/request.py", line 1245, in do_open
    raise URLError(err)
urllib.error.URLError: <urlopen error [SSL: TLSV1_ALERT_ACCESS_DENIED] tlsv1 alert access denied (_ssl.c:645)>
```


During handling of the above exception, another exception occurred:


```
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 327, in get_ppa_info
    ret = get_ppa_info_from_lp(user, ppa)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 92, in get_ppa_info_from_lp
    return get_info_from_lp(lp_url)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 88, in get_info_from_lp
    return _get_https_content_py3(lp_url)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 108, in _get_https_content_py3
    raise PPAException("Error reading %s: %s" % (lp_url, reason), e)
softwareproperties.ppa.PPAException: 'Error reading [https://launchpad.net/api/1.0/~openjdk-r/+archive/ubuntu/ppa:](https://launchpad.net/api/1.0/~openjdk-r/+archive/ubuntu/ppa:) [SSL: TLSV1_ALERT_ACCESS_DENIED] tlsv1 alert access denied (_ssl.c:645)'

```

During handling of the above exception, another exception occurred:


```
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 393, in shortcut_handler
    return PPAShortcutHandler(shortcut)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 356, in __init__
    info = get_ppa_info(self.shortcut)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 339, in get_ppa_info
    _get_suggested_ppa_message(user, ppa))
softwareproperties.shortcuts.ShortcutException: Cannot add PPA: 'ppa:~openjdk-r/ubuntu/ppa'.
ERROR: '~openjdk-r' user or team does not exist.
Error: 'ppa:openjdk-r/ppa' invalid
```

Thanks

---

### Post by slickymaster on 2016-12-09
There's nothing wrong with this PPA. Just set up a Xenial VB box and was able to install it```
slickymaster@VirtualBox:~$ sudo add-apt-repository ppa:openjdk-r/ppa
[sudo] password for slickymaster: 
 
 More info: https://launchpad.net/~openjdk-r/+archive/ubuntu/ppa
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpxpvy7y6_/secring.gpg' created
gpg: keyring `/tmp/tmpxpvy7y6_/pubring.gpg' created
gpg: requesting key 86F44E2A from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpxpvy7y6_/trustdb.gpg: trustdb created
gpg: key 86F44E2A: public key "Launchpad OpenJDK builds (all archs)" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
slickymaster@VirtualBox:~$ sudo apt-get update
Hit:1 http://archive.canonical.com/ubuntu xenial InRelease
Hit:2 http://security.ubuntu.com/ubuntu xenial-security InRelease                                                         
Hit:3 https://packages.microsoft.com/ubuntu/16.04/prod xenial InRelease                                                   
Hit:4 https://packages.microsoft.com/ubuntu/16.04/mssql-server xenial InRelease                    
Get:5 http://ppa.launchpad.net/openjdk-r/ppa/ubuntu xenial InRelease [17,5 kB]                     
Get:6 http://ppa.launchpad.net/openjdk-r/ppa/ubuntu xenial/main amd64 Packages [6380 B]
Get:7 http://ppa.launchpad.net/openjdk-r/ppa/ubuntu xenial/main i386 Packages [6372 B]
Get:8 http://ppa.launchpad.net/openjdk-r/ppa/ubuntu xenial/main Translation-en [1528 B]
Hit:9 http://pt.archive.ubuntu.com/ubuntu xenial InRelease
Hit:10 http://pt.archive.ubuntu.com/ubuntu xenial-updates InRelease
Hit:11 http://pt.archive.ubuntu.com/ubuntu xenial-backports InRelease
Hit:12 http://pt.archive.ubuntu.com/ubuntu xenial-proposed InRelease
Fetched 31,8 kB in 5s (5765 B/s)                   
Reading package lists... Done
slickymaster@VirtualBox:~$ sudo apt-get install openjdk-7-jdk 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libxdelta2 linux-headers-4.4.0-49 linux-headers-4.4.0-49-generic linux-headers-4.4.0-51 linux-headers-4.4.0-51-generic linux-image-4.4.0-49-generic linux-image-4.4.0-51-generic linux-image-extra-4.4.0-49-generic
  linux-image-extra-4.4.0-51-generic xdelta
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  ca-certificates-java fonts-dejavu-extra java-common libatk-wrapper-java libatk-wrapper-java-jni libbonobo2-0 libbonobo2-common libgif7 libgnome-2-0 libgnome2-common libgnomevfs2-0 libgnomevfs2-common libice-dev
  liborbit-2-0 libpthread-stubs0-dev libsctp1 libsm-dev libx11-dev libx11-doc libxau-dev libxcb1-dev libxdmcp-dev libxt-dev openjdk-7-jre openjdk-7-jre-headless x11proto-core-dev x11proto-input-dev x11proto-kb-dev
  xorg-sgml-doctools xtrans-dev
Suggested packages:
  default-jre libbonobo2-bin libgnomevfs2-bin libgnomevfs2-extra gamin | fam gnome-mime-data libice-doc lksctp-tools libsm-doc libxcb-doc libxt-doc openjdk-7-demo openjdk-7-source visualvm icedtea-7-plugin
  icedtea-7-jre-jamvm sun-java6-fonts fonts-ipafont-gothic fonts-ipafont-mincho ttf-wqy-microhei | ttf-wqy-zenhei fonts-indic
The following NEW packages will be installed:
  ca-certificates-java fonts-dejavu-extra java-common libatk-wrapper-java libatk-wrapper-java-jni libbonobo2-0 libbonobo2-common libgif7 libgnome-2-0 libgnome2-common libgnomevfs2-0 libgnomevfs2-common libice-dev
  liborbit-2-0 libpthread-stubs0-dev libsctp1 libsm-dev libx11-dev libx11-doc libxau-dev libxcb1-dev libxdmcp-dev libxt-dev openjdk-7-jdk openjdk-7-jre openjdk-7-jre-headless x11proto-core-dev x11proto-input-dev
  x11proto-kb-dev xorg-sgml-doctools xtrans-dev
0 upgraded, 31 newly installed, 0 to remove and 0 not upgraded.
Need to get 61,8 MB of archives.
After this operation, 108 MB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://pt.archive.ubuntu.com/ubuntu xenial/main amd64 libbonobo2-common all 2.32.1-3 [34,7 kB]
Get:2 http://pt.archive.ubuntu.com/ubuntu xenial/main amd64 liborbit-2-0 amd64 1:2.14.19-1build1 [140 kB]
Get:3 http://ppa.launchpad.net/openjdk-r/ppa/ubuntu xenial/main amd64 openjdk-7-jre-headless amd64 7u95-2.6.4-3 [39,4 MB]
Get:4 http://pt.archive.ubuntu.com/ubuntu xenial/main amd64 libbonobo2-0 amd64 2.32.1-3 [211 kB]
Get:5 http://pt.archive.ubuntu.com/ubuntu xenial/main amd64 ca-certificates-java all 20160321 [12,9 kB]
Get:6 http://pt.archive.ubuntu.com/ubuntu xenial/main amd64 java-common all 0.56ubuntu2 [7742 B]
Get:7 http://pt.archive.ubuntu.com/ubuntu xenial/main amd64 libsctp1 amd64 1.0.16+dfsg-3 [8088 B]
Get:8 http://pt.archive.ubuntu.com/ubuntu xenial/main amd64 fonts-dejavu-extra all 2.35-1 [1749 kB]
Get:9 http://pt.archive.ubuntu.com/ubuntu xenial/universe amd64 libatk-wrapper-java all 0.33.3-6 [33,9 kB]                                                                                                                       
Get:10 http://pt.archive.ubuntu.com/ubuntu xenial/universe amd64 libatk-wrapper-java-jni amd64 0.33.3-6 [27,4 kB]                                                                                                                
Get:11 http://pt.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libgif7 amd64 5.1.4-0.3~16.04 [30,5 kB]                                                                                                                     
Get:12 http://pt.archive.ubuntu.com/ubuntu xenial/main amd64 libgnomevfs2-common amd64 1:2.24.4-6.1ubuntu1 [23,0 kB]                                                                                                             
Get:13 http://pt.archive.ubuntu.com/ubuntu xenial/main amd64 libgnomevfs2-0 amd64 1:2.24.4-6.1ubuntu1 [213 kB]                                                                                                                   
Get:14 http://pt.archive.ubuntu.com/ubuntu xenial/main amd64 libgnome2-common all 2.32.1-5ubuntu1 [33,5 kB]                                                                                                                      
Get:15 http://pt.archive.ubuntu.com/ubuntu xenial/main amd64 libgnome-2-0 amd64 2.32.1-5ubuntu1 [53,7 kB]                                                                                                                        
Get:16 http://pt.archive.ubuntu.com/ubuntu xenial/main amd64 xorg-sgml-doctools all 1:1.11-1 [12,9 kB]                                                                                                                           
Get:17 http://pt.archive.ubuntu.com/ubuntu xenial/main amd64 x11proto-core-dev all 7.0.28-2ubuntu1 [254 kB]                                                                                                                      
Get:18 http://pt.archive.ubuntu.com/ubuntu xenial/main amd64 libice-dev amd64 2:1.0.9-1 [44,9 kB]                                                                                                                                
Get:19 http://pt.archive.ubuntu.com/ubuntu xenial/main amd64 libpthread-stubs0-dev amd64 0.3-4 [4068 B]                                                                                                                          
Get:20 http://pt.archive.ubuntu.com/ubuntu xenial/main amd64 libsm-dev amd64 2:1.2.2-1 [16,2 kB]                                                                                                                                 
Get:21 http://pt.archive.ubuntu.com/ubuntu xenial/main amd64 libxau-dev amd64 1:1.0.8-1 [11,1 kB]                                                                                                                                
Get:22 http://pt.archive.ubuntu.com/ubuntu xenial/main amd64 libxdmcp-dev amd64 1:1.1.2-1.1 [25,1 kB]                                                                                                                            
Get:23 http://pt.archive.ubuntu.com/ubuntu xenial/main amd64 x11proto-input-dev all 2.3.1-1 [118 kB]                                                                                                                             
Get:24 http://pt.archive.ubuntu.com/ubuntu xenial/main amd64 x11proto-kb-dev all 1.0.7-0ubuntu1 [224 kB]                                                                                                                         
Get:25 http://pt.archive.ubuntu.com/ubuntu xenial/main amd64 xtrans-dev all 1.3.5-1 [70,5 kB]                                                                                                                                    
Get:26 http://pt.archive.ubuntu.com/ubuntu xenial/main amd64 libxcb1-dev amd64 1.11.1-1ubuntu1 [74,2 kB]                                                                                                                         
Get:27 http://pt.archive.ubuntu.com/ubuntu xenial/main amd64 libx11-dev amd64 2:1.6.3-1ubuntu2 [642 kB]                                                                                                                          
Get:28 http://pt.archive.ubuntu.com/ubuntu xenial/main amd64 libx11-doc all 2:1.6.3-1ubuntu2 [1465 kB]                                                                                                                           
Get:29 http://pt.archive.ubuntu.com/ubuntu xenial/main amd64 libxt-dev amd64 1:1.1.5-0ubuntu1 [394 kB]                                                                                                                           
Get:30 http://ppa.launchpad.net/openjdk-r/ppa/ubuntu xenial/main amd64 openjdk-7-jre amd64 7u95-2.6.4-3 [173 kB]                                                                                                                 
Get:31 http://ppa.launchpad.net/openjdk-r/ppa/ubuntu xenial/main amd64 openjdk-7-jdk amd64 7u95-2.6.4-3 [16,3 MB]                                                                                                                
Fetched 61,8 MB in 2min 19s (442 kB/s)                                                                                                                                                                                           
Extracting templates from packages: 100%
Selecting previously unselected package libbonobo2-common.
(Reading database ... 254022 files and directories currently installed.)
Preparing to unpack .../libbonobo2-common_2.32.1-3_all.deb ...
Unpacking libbonobo2-common (2.32.1-3) ...
Selecting previously unselected package liborbit-2-0:amd64.
Preparing to unpack .../liborbit-2-0_1%3a2.14.19-1build1_amd64.deb ...
Unpacking liborbit-2-0:amd64 (1:2.14.19-1build1) ...
Selecting previously unselected package libbonobo2-0:amd64.
Preparing to unpack .../libbonobo2-0_2.32.1-3_amd64.deb ...
Unpacking libbonobo2-0:amd64 (2.32.1-3) ...
Selecting previously unselected package ca-certificates-java.
Preparing to unpack .../ca-certificates-java_20160321_all.deb ...
Unpacking ca-certificates-java (20160321) ...
Selecting previously unselected package java-common.
Preparing to unpack .../java-common_0.56ubuntu2_all.deb ...
Unpacking java-common (0.56ubuntu2) ...
Selecting previously unselected package libsctp1:amd64.
Preparing to unpack .../libsctp1_1.0.16+dfsg-3_amd64.deb ...
Unpacking libsctp1:amd64 (1.0.16+dfsg-3) ...
Selecting previously unselected package openjdk-7-jre-headless:amd64.
Preparing to unpack .../openjdk-7-jre-headless_7u95-2.6.4-3_amd64.deb ...
Unpacking openjdk-7-jre-headless:amd64 (7u95-2.6.4-3) ...
Selecting previously unselected package fonts-dejavu-extra.
Preparing to unpack .../fonts-dejavu-extra_2.35-1_all.deb ...
Unpacking fonts-dejavu-extra (2.35-1) ...
Selecting previously unselected package libatk-wrapper-java.
Preparing to unpack .../libatk-wrapper-java_0.33.3-6_all.deb ...
Unpacking libatk-wrapper-java (0.33.3-6) ...
Selecting previously unselected package libatk-wrapper-java-jni:amd64.
Preparing to unpack .../libatk-wrapper-java-jni_0.33.3-6_amd64.deb ...
Unpacking libatk-wrapper-java-jni:amd64 (0.33.3-6) ...
Selecting previously unselected package libgif7:amd64.
Preparing to unpack .../libgif7_5.1.4-0.3~16.04_amd64.deb ...
Unpacking libgif7:amd64 (5.1.4-0.3~16.04) ...
Selecting previously unselected package libgnomevfs2-common.
Preparing to unpack .../libgnomevfs2-common_1%3a2.24.4-6.1ubuntu1_amd64.deb ...
Unpacking libgnomevfs2-common (1:2.24.4-6.1ubuntu1) ...
Selecting previously unselected package libgnomevfs2-0:amd64.
Preparing to unpack .../libgnomevfs2-0_1%3a2.24.4-6.1ubuntu1_amd64.deb ...
Unpacking libgnomevfs2-0:amd64 (1:2.24.4-6.1ubuntu1) ...
Selecting previously unselected package libgnome2-common.
Preparing to unpack .../libgnome2-common_2.32.1-5ubuntu1_all.deb ...
Unpacking libgnome2-common (2.32.1-5ubuntu1) ...
Selecting previously unselected package libgnome-2-0:amd64.
Preparing to unpack .../libgnome-2-0_2.32.1-5ubuntu1_amd64.deb ...
Unpacking libgnome-2-0:amd64 (2.32.1-5ubuntu1) ...
Selecting previously unselected package xorg-sgml-doctools.
Preparing to unpack .../xorg-sgml-doctools_1%3a1.11-1_all.deb ...
Unpacking xorg-sgml-doctools (1:1.11-1) ...
Selecting previously unselected package x11proto-core-dev.
Preparing to unpack .../x11proto-core-dev_7.0.28-2ubuntu1_all.deb ...
Unpacking x11proto-core-dev (7.0.28-2ubuntu1) ...
Selecting previously unselected package libice-dev:amd64.
Preparing to unpack .../libice-dev_2%3a1.0.9-1_amd64.deb ...
Unpacking libice-dev:amd64 (2:1.0.9-1) ...
Selecting previously unselected package libpthread-stubs0-dev:amd64.
Preparing to unpack .../libpthread-stubs0-dev_0.3-4_amd64.deb ...
Unpacking libpthread-stubs0-dev:amd64 (0.3-4) ...
Selecting previously unselected package libsm-dev:amd64.
Preparing to unpack .../libsm-dev_2%3a1.2.2-1_amd64.deb ...
Unpacking libsm-dev:amd64 (2:1.2.2-1) ...
Selecting previously unselected package libxau-dev:amd64.
Preparing to unpack .../libxau-dev_1%3a1.0.8-1_amd64.deb ...
Unpacking libxau-dev:amd64 (1:1.0.8-1) ...
Selecting previously unselected package libxdmcp-dev:amd64.
Preparing to unpack .../libxdmcp-dev_1%3a1.1.2-1.1_amd64.deb ...
Unpacking libxdmcp-dev:amd64 (1:1.1.2-1.1) ...
Selecting previously unselected package x11proto-input-dev.
Preparing to unpack .../x11proto-input-dev_2.3.1-1_all.deb ...
Unpacking x11proto-input-dev (2.3.1-1) ...
Selecting previously unselected package x11proto-kb-dev.
Preparing to unpack .../x11proto-kb-dev_1.0.7-0ubuntu1_all.deb ...
Unpacking x11proto-kb-dev (1.0.7-0ubuntu1) ...
Selecting previously unselected package xtrans-dev.
Preparing to unpack .../xtrans-dev_1.3.5-1_all.deb ...
Unpacking xtrans-dev (1.3.5-1) ...
Selecting previously unselected package libxcb1-dev:amd64.
Preparing to unpack .../libxcb1-dev_1.11.1-1ubuntu1_amd64.deb ...
Unpacking libxcb1-dev:amd64 (1.11.1-1ubuntu1) ...
Selecting previously unselected package libx11-dev:amd64.
Preparing to unpack .../libx11-dev_2%3a1.6.3-1ubuntu2_amd64.deb ...
Unpacking libx11-dev:amd64 (2:1.6.3-1ubuntu2) ...
Selecting previously unselected package libx11-doc.
Preparing to unpack .../libx11-doc_2%3a1.6.3-1ubuntu2_all.deb ...
Unpacking libx11-doc (2:1.6.3-1ubuntu2) ...
Selecting previously unselected package libxt-dev:amd64.
Preparing to unpack .../libxt-dev_1%3a1.1.5-0ubuntu1_amd64.deb ...
Unpacking libxt-dev:amd64 (1:1.1.5-0ubuntu1) ...
Selecting previously unselected package openjdk-7-jre:amd64.
Preparing to unpack .../openjdk-7-jre_7u95-2.6.4-3_amd64.deb ...
Unpacking openjdk-7-jre:amd64 (7u95-2.6.4-3) ...
Selecting previously unselected package openjdk-7-jdk:amd64.
Preparing to unpack .../openjdk-7-jdk_7u95-2.6.4-3_amd64.deb ...
Unpacking openjdk-7-jdk:amd64 (7u95-2.6.4-3) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...
Processing triggers for ca-certificates (20160104ubuntu1) ...
Updating certificates in /etc/ssl/certs...
0 added, 0 removed; done.
Running hooks in /etc/ca-certificates/update.d...
done.
Processing triggers for fontconfig (2.11.94-0ubuntu1.1) ...
Processing triggers for gconf2 (3.2.6-3ubuntu6) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Setting up libbonobo2-common (2.32.1-3) ...
Setting up liborbit-2-0:amd64 (1:2.14.19-1build1) ...
Setting up libbonobo2-0:amd64 (2.32.1-3) ...
Setting up java-common (0.56ubuntu2) ...
Setting up libsctp1:amd64 (1.0.16+dfsg-3) ...
Setting up fonts-dejavu-extra (2.35-1) ...
Setting up libatk-wrapper-java (0.33.3-6) ...
Setting up libatk-wrapper-java-jni:amd64 (0.33.3-6) ...
Setting up libgif7:amd64 (5.1.4-0.3~16.04) ...
Setting up libgnomevfs2-common (1:2.24.4-6.1ubuntu1) ...
Setting up libgnomevfs2-0:amd64 (1:2.24.4-6.1ubuntu1) ...
Setting up libgnome2-common (2.32.1-5ubuntu1) ...
Setting up libgnome-2-0:amd64 (2.32.1-5ubuntu1) ...
Setting up xorg-sgml-doctools (1:1.11-1) ...
Setting up x11proto-core-dev (7.0.28-2ubuntu1) ...
Setting up libice-dev:amd64 (2:1.0.9-1) ...
Setting up libpthread-stubs0-dev:amd64 (0.3-4) ...
Setting up libsm-dev:amd64 (2:1.2.2-1) ...
Setting up libxau-dev:amd64 (1:1.0.8-1) ...
Setting up libxdmcp-dev:amd64 (1:1.1.2-1.1) ...
Setting up x11proto-input-dev (2.3.1-1) ...
Setting up x11proto-kb-dev (1.0.7-0ubuntu1) ...
Setting up xtrans-dev (1.3.5-1) ...
Setting up libxcb1-dev:amd64 (1.11.1-1ubuntu1) ...
Setting up libx11-dev:amd64 (2:1.6.3-1ubuntu2) ...
Setting up libx11-doc (2:1.6.3-1ubuntu2) ...
Setting up libxt-dev:amd64 (1:1.1.5-0ubuntu1) ...
Setting up openjdk-7-jre-headless:amd64 (7u95-2.6.4-3) ...
update-alternatives: using /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/rmid to provide /usr/bin/rmid (rmid) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/java to provide /usr/bin/java (java) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/keytool to provide /usr/bin/keytool (keytool) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/pack200 to provide /usr/bin/pack200 (pack200) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/rmiregistry to provide /usr/bin/rmiregistry (rmiregistry) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/unpack200 to provide /usr/bin/unpack200 (unpack200) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/orbd to provide /usr/bin/orbd (orbd) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/servertool to provide /usr/bin/servertool (servertool) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/tnameserv to provide /usr/bin/tnameserv (tnameserv) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-openjdk-amd64/jre/lib/jexec to provide /usr/bin/jexec (jexec) in auto mode
Setting up openjdk-7-jre:amd64 (7u95-2.6.4-3) ...
update-alternatives: using /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/policytool to provide /usr/bin/policytool (policytool) in auto mode
Setting up openjdk-7-jdk:amd64 (7u95-2.6.4-3) ...
update-alternatives: using /usr/lib/jvm/java-7-openjdk-amd64/bin/idlj to provide /usr/bin/idlj (idlj) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-openjdk-amd64/bin/wsimport to provide /usr/bin/wsimport (wsimport) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-openjdk-amd64/bin/rmic to provide /usr/bin/rmic (rmic) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-openjdk-amd64/bin/jinfo to provide /usr/bin/jinfo (jinfo) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-openjdk-amd64/bin/jsadebugd to provide /usr/bin/jsadebugd (jsadebugd) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-openjdk-amd64/bin/native2ascii to provide /usr/bin/native2ascii (native2ascii) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-openjdk-amd64/bin/jstat to provide /usr/bin/jstat (jstat) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-openjdk-amd64/bin/javac to provide /usr/bin/javac (javac) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-openjdk-amd64/bin/javah to provide /usr/bin/javah (javah) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-openjdk-amd64/bin/jstack to provide /usr/bin/jstack (jstack) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-openjdk-amd64/bin/jrunscript to provide /usr/bin/jrunscript (jrunscript) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-openjdk-amd64/bin/javadoc to provide /usr/bin/javadoc (javadoc) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-openjdk-amd64/bin/javap to provide /usr/bin/javap (javap) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-openjdk-amd64/bin/jar to provide /usr/bin/jar (jar) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-openjdk-amd64/bin/extcheck to provide /usr/bin/extcheck (extcheck) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-openjdk-amd64/bin/schemagen to provide /usr/bin/schemagen (schemagen) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-openjdk-amd64/bin/jps to provide /usr/bin/jps (jps) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-openjdk-amd64/bin/xjc to provide /usr/bin/xjc (xjc) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-openjdk-amd64/bin/jarsigner to provide /usr/bin/jarsigner (jarsigner) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-openjdk-amd64/bin/jmap to provide /usr/bin/jmap (jmap) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-openjdk-amd64/bin/appletviewer to provide /usr/bin/appletviewer (appletviewer) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-openjdk-amd64/bin/jconsole to provide /usr/bin/jconsole (jconsole) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-openjdk-amd64/bin/jstatd to provide /usr/bin/jstatd (jstatd) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-openjdk-amd64/bin/jhat to provide /usr/bin/jhat (jhat) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-openjdk-amd64/bin/jdb to provide /usr/bin/jdb (jdb) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-openjdk-amd64/bin/serialver to provide /usr/bin/serialver (serialver) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-openjdk-amd64/bin/wsgen to provide /usr/bin/wsgen (wsgen) in auto mode
update-alternatives: using /usr/lib/jvm/java-7-openjdk-amd64/bin/jcmd to provide /usr/bin/jcmd (jcmd) in auto mode
Setting up ca-certificates-java (20160321) ...
Adding debian:Chambers_of_Commerce_Root_-_2008.pem
Adding debian:Equifax_Secure_Global_eBusiness_CA.pem
Adding debian:Staat_der_Nederlanden_Root_CA_-_G2.pem
Adding debian:QuoVadis_Root_CA_2.pem
Adding debian:Root_CA_Generalitat_Valenciana.pem
Adding debian:Entrust_Root_Certification_Authority_-_EC1.pem
Adding debian:Network_Solutions_Certificate_Authority.pem
Adding debian:VeriSign_Universal_Root_Certification_Authority.pem
Adding debian:QuoVadis_Root_CA_2_G3.pem
Adding debian:T-TeleSec_GlobalRoot_Class_3.pem
Adding debian:Certinomis_-_Root_CA.pem
Adding debian:Visa_eCommerce_Root.pem
Adding debian:IGC_A.pem
Adding debian:Certinomis_-_Autorité_Racine.pem
Adding debian:IdenTrust_Commercial_Root_CA_1.pem
Adding debian:CA_WoSign_ECC_Root.pem
Adding debian:Verisign_Class_2_Public_Primary_Certification_Authority_-_G2.pem
Adding debian:EE_Certification_Centre_Root_CA.pem
Adding debian:QuoVadis_Root_CA_1_G3.pem
Adding debian:certSIGN_ROOT_CA.pem
Adding debian:Verisign_Class_3_Public_Primary_Certification_Authority_-_G3.pem
Adding debian:Taiwan_GRCA.pem
Adding debian:Comodo_AAA_Services_root.pem
Adding debian:DigiCert_Assured_ID_Root_CA.pem
Adding debian:QuoVadis_Root_CA_3.pem
Adding debian:ssl-cert-snakeoil.pem
Adding debian:Entrust.net_Premium_2048_Secure_Server_CA.pem
Adding debian:DigiCert_High_Assurance_EV_Root_CA.pem
Adding debian:Verisign_Class_3_Public_Primary_Certification_Authority.pem
Adding debian:ACEDICOM_Root.pem
Adding debian:Starfield_Services_Root_Certificate_Authority_-_G2.pem
Adding debian:Atos_TrustedRoot_2011.pem
Adding debian:XRamp_Global_CA_Root.pem
Adding debian:DigiCert_Trusted_Root_G4.pem
Adding debian:Buypass_Class_3_Root_CA.pem
Adding debian:AC_Raíz_Certicámara_S.A..pem
Adding debian:Starfield_Root_Certificate_Authority_-_G2.pem
Adding debian:Verisign_Class_2_Public_Primary_Certification_Authority_-_G3.pem
Adding debian:USERTrust_RSA_Certification_Authority.pem
Adding debian:Actalis_Authentication_Root_CA.pem
Adding debian:SwissSign_Platinum_CA_-_G2.pem
Adding debian:Camerfirma_Global_Chambersign_Root.pem
Adding debian:Sonera_Class_1_Root_CA.pem
Adding debian:Camerfirma_Chambers_of_Commerce_Root.pem
Adding debian:Deutsche_Telekom_Root_CA_2.pem
Adding debian:WoSign_China.pem
Adding debian:TÜRKTRUST_Elektronik_Sertifika_Hizmet_Sa&#287;lay&#305;c&#305;s&#305;_H6.pem
Adding debian:Certigna.pem
Adding debian:ComSign_CA.pem
Adding debian:Starfield_Class_2_CA.pem
Adding debian:thawte_Primary_Root_CA_-_G3.pem
Adding debian:NetLock_Notary_=Class_A=_Root.pem
Adding debian:Verisign_Class_3_Public_Primary_Certification_Authority_-_G2.pem
Adding debian:QuoVadis_Root_CA_3_G3.pem
Adding debian:TWCA_Global_Root_CA.pem
Adding debian:CNNIC_ROOT.pem
Adding debian:Verisign_Class_3_Public_Primary_Certification_Authority_2.pem
Adding debian:USERTrust_ECC_Certification_Authority.pem
Adding debian:GlobalSign_Root_CA_-_R3.pem
Adding debian:EBG_Elektronik_Sertifika_Hizmet_Sa&#287;lay&#305;c&#305;s&#305;.pem
Adding debian:GeoTrust_Primary_Certification_Authority.pem
Adding debian:VeriSign_Class_3_Public_Primary_Certification_Authority_-_G4.pem
Adding debian:Buypass_Class_2_Root_CA.pem
Adding debian:AddTrust_External_Root.pem
Adding debian:SwissSign_Gold_CA_-_G2.pem
Adding debian:Staat_der_Nederlanden_Root_CA_-_G3.pem
Adding debian:Comodo_Secure_Services_root.pem
Adding debian:Swisscom_Root_CA_2.pem
Adding debian:GeoTrust_Global_CA_2.pem
Adding debian:Security_Communication_Root_CA.pem
Adding debian:Certum_Trusted_Network_CA.pem
Adding debian:StartCom_Certification_Authority.pem
Adding debian:Security_Communication_RootCA2.pem
Adding debian:Certplus_Class_2_Primary_CA.pem
Adding debian:Trustis_FPS_Root_CA.pem
Adding debian:Go_Daddy_Class_2_CA.pem
Adding debian:AddTrust_Low-Value_Services_Root.pem
Adding debian:COMODO_Certification_Authority.pem
Adding debian:Certum_Root_CA.pem
Adding debian:COMODO_RSA_Certification_Authority.pem
Adding debian:PSCProcert.pem
Adding debian:NetLock_Arany_=Class_Gold=_F&#337;tanúsítvány.pem
Adding debian:IdenTrust_Public_Sector_Root_CA_1.pem
Adding debian:GlobalSign_ECC_Root_CA_-_R4.pem
Adding debian:Cybertrust_Global_Root.pem
Adding debian:NetLock_Qualified_=Class_QA=_Root.pem
Adding debian:Entrust_Root_Certification_Authority_-_G2.pem
Adding debian:Hongkong_Post_Root_CA_1.pem
Adding debian:Sonera_Class_2_Root_CA.pem
Adding debian:GlobalSign_Root_CA.pem
Adding debian:RSA_Security_2048_v3.pem
Adding debian:CFCA_EV_ROOT.pem
Adding debian:D-TRUST_Root_Class_3_CA_2_2009.pem
Adding debian:TC_TrustCenter_Class_3_CA_II.pem
Adding debian:DigiCert_Assured_ID_Root_G2.pem
Adding debian:GeoTrust_Global_CA.pem
Adding debian:Verisign_Class_1_Public_Primary_Certification_Authority.pem
Adding debian:Microsec_e-Szigno_Root_CA_2009.pem
Adding debian:Hellenic_Academic_and_Research_Institutions_RootCA_2011.pem
Adding debian:StartCom_Certification_Authority_G2.pem
Adding debian:StartCom_Certification_Authority_2.pem
Adding debian:Juur-SK.pem
Adding debian:Entrust_Root_Certification_Authority.pem
Adding debian:thawte_Primary_Root_CA.pem
Adding debian:SwissSign_Silver_CA_-_G2.pem
Adding debian:QuoVadis_Root_CA.pem
Adding debian:EC-ACC.pem
Adding debian:CA_Disig_Root_R2.pem
Adding debian:SecureSign_RootCA11.pem
Adding debian:DigiCert_Global_Root_G3.pem
Adding debian:WellsSecure_Public_Root_Certificate_Authority.pem
Adding debian:AffirmTrust_Networking.pem
Adding debian:DST_ACES_CA_X6.pem
Adding debian:GeoTrust_Primary_Certification_Authority_-_G3.pem
Adding debian:TÜRKTRUST_Elektronik_Sertifika_Hizmet_Sa&#287;lay&#305;c&#305;s&#305;_H5.pem
Adding debian:DigiCert_Global_Root_G2.pem
Adding debian:Autoridad_de_Certificacion_Firmaprofesional_CIF_A62634068.pem
Adding debian:GlobalSign_ECC_Root_CA_-_R5.pem
Adding debian:Buypass_Class_2_CA_1.pem
Adding debian:D-TRUST_Root_Class_3_CA_2_EV_2009.pem
Adding debian:Global_Chambersign_Root_-_2008.pem
Adding debian:Secure_Global_CA.pem
Adding debian:GeoTrust_Primary_Certification_Authority_-_G2.pem
Adding debian:ACCVRAIZ1.pem
Adding debian:Swisscom_Root_CA_1.pem
Adding debian:S-TRUST_Universal_Root_CA.pem
Adding debian:DigiCert_Global_Root_CA.pem
Adding debian:S-TRUST_Authentication_and_Encryption_Root_CA_2005_PN.pem
Adding debian:DigiCert_Assured_ID_Root_G3.pem
Adding debian:TWCA_Root_Certification_Authority.pem
Adding debian:OISTE_WISeKey_Global_Root_GA_CA.pem
Adding debian:TURKTRUST_Certificate_Services_Provider_Root_2007.pem
Adding debian:OISTE_WISeKey_Global_Root_GB_CA.pem
Adding debian:Staat_der_Nederlanden_EV_Root_CA.pem
Adding debian:CA_Disig.pem
Adding debian:AffirmTrust_Premium.pem
Adding debian:China_Internet_Network_Information_Center_EV_Certificates_Root.pem
Adding debian:T-TeleSec_GlobalRoot_Class_2.pem
Adding debian:ApplicationCA_-_Japanese_Government.pem
Adding debian:ePKI_Root_Certification_Authority.pem
Adding debian:UTN_USERFirst_Hardware_Root_CA.pem
Adding debian:Verisign_Class_1_Public_Primary_Certification_Authority_-_G2.pem
Adding debian:GeoTrust_Universal_CA_2.pem
Adding debian:Swisscom_Root_EV_CA_2.pem
Adding debian:Equifax_Secure_eBusiness_CA_1.pem
Adding debian:Certification_Authority_of_WoSign_G2.pem
Adding debian:TeliaSonera_Root_CA_v1.pem
Adding debian:WoSign.pem
Adding debian:TÜB&#304;TAK_UEKAE_Kök_Sertifika_Hizmet_Sa&#287;lay&#305;c&#305;s&#305;_-_Sürüm_3.pem
Adding debian:SecureTrust_CA.pem
Adding debian:AffirmTrust_Commercial.pem
Adding debian:Microsec_e-Szigno_Root_CA.pem
Adding debian:AffirmTrust_Premium_ECC.pem
Adding debian:Izenpe.com.pem
Adding debian:GeoTrust_Universal_CA.pem
Adding debian:AddTrust_Public_Services_Root.pem
Adding debian:Comodo_Trusted_Services_root.pem
Adding debian:NetLock_Express_=Class_C=_Root.pem
Adding debian:Staat_der_Nederlanden_Root_CA.pem
Adding debian:Security_Communication_EV_RootCA1.pem
Adding debian:VeriSign_Class_3_Public_Primary_Certification_Authority_-_G5.pem
Adding debian:COMODO_ECC_Certification_Authority.pem
Adding debian:NetLock_Business_=Class_B=_Root.pem
Adding debian:CA_Disig_Root_R1.pem
Adding debian:UTN_USERFirst_Email_Root_CA.pem
Adding debian:GlobalSign_Root_CA_-_R2.pem
Adding debian:AddTrust_Qualified_Certificates_Root.pem
Adding debian:thawte_Primary_Root_CA_-_G2.pem
Adding debian:Verisign_Class_1_Public_Primary_Certification_Authority_-_G3.pem
Adding debian:Baltimore_CyberTrust_Root.pem
Adding debian:Equifax_Secure_CA.pem
Adding debian:E-Tugra_Certification_Authority.pem
Adding debian:Go_Daddy_Root_Certificate_Authority_-_G2.pem
Adding debian:DST_Root_CA_X3.pem
done.
Processing triggers for libc-bin (2.23-0ubuntu5) ...
Processing triggers for ca-certificates (20160104ubuntu1) ...
Updating certificates in /etc/ssl/certs...
0 added, 0 removed; done.
Running hooks in /etc/ca-certificates/update.d...

done.
done.
slickymaster@VirtualBox:~$ 

```

I believe your problem is related to this bug: [add-apt-repository explodes on missing ppa]("https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/1594776"), which was fixed in the package **software-properties - 0.96.20.3**

---

### Post by mc4man on 2016-12-09
your not even getting the normal ubuntu repos - 
> sudo apt-get update
Get:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [11.7 kB]                                 
Err:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease                                           
  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
Get:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial InRelease [11.7 kB]                      
Err:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial InRelease

  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
Are you using a proxy?

---

### Post by mgomalley on 2016-12-13
Thanks for pointing out that Bug

I am struggling to figure out what I need to install to fix the Bug

I tried the following...

```
sudo apt-get install software-properties - 0.96.20.3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package software-properties is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'software-properties' has no installation candidate
E: Unable to locate package 0.96.20.3
E: Couldn't find any package by glob '0.96.20.3'
E: Couldn't find any package by regex '0.96.20.3'

sudo apt-get install 0.96.20.3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package 0.96.20.3
E: Couldn't find any package by glob '0.96.20.3'
E: Couldn't find any package by regex '0.96.20.3'
```

Thanks in advance

Thanks for your update.

Yes, i have my proxies set in my .bashrc file

---

### Post by mgomalley on 2016-12-21
Thanks


Where did you get the Xenial image for your VBox? Perhaps I have a bad image?

Thanks in advance.

Mike

---

### Post by slickymaster on 2016-12-21
> **mgomalley said:**
> Thanks


Where did you get the Xenial image for your VBox? Perhaps I have a bad image?

Thanks in advance.

Mike

Here you go: [http://cdimages.ubuntu.com/xubuntu/releases/16.04/release/](http://cdimages.ubuntu.com/xubuntu/releases/16.04/release/)

---

### Post by mgomalley on 2016-12-21
Hi,

In virtualBox I set up a new ubuntu environment.  I download 64bit 16.04 Xenial image from -> [http://www.osboxes.org/ubuntu/#ubuntu-16-04-vmware](http://www.osboxes.org/ubuntu/#ubuntu-16-04-vmware).

I used the downloaded .vmdk file to create the new vm in virtualbox. 

After setting up the correct proxies, I still get the same error when trying to install Java
```

#sudo apt-get update
#sudo add-apt-repository ppa:openjdk-r/ppa  
#sudo apt-get install openjdk-7-jdk
```

Thanks in advance.

---

### Post by slickymaster on 2016-12-21
> **mgomalley said:**
> Hi,

In virtualBox I set up a new ubuntu environment.  I download 64bit 16.04 Xenial image from -> [http://www.osboxes.org/ubuntu/#ubuntu-16-04-vmware](http://www.osboxes.org/ubuntu/#ubuntu-16-04-vmware).

I used the downloaded .vmdk file to create the new vm in virtualbox. 

After setting up the correct proxies, I still get the same error when trying to install Java
```

#sudo apt-get update
#sudo add-apt-repository ppa:openjdk-r/ppa  
#sudo apt-get install openjdk-7-jdk
```

Thanks in advance.

Can you please past into the thread the full output you get when you try to install it, using code tags for the effect.

---

### Post by howefield on 2016-12-22
Moved to the "*Virtualisation*" forum.

---

