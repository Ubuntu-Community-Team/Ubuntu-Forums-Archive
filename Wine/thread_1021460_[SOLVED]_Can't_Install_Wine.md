---
title: "[SOLVED] Can't Install Wine"
date: 2008-12-25
forum: Wine
---

### Post by vegetarianshrimp on 2008-12-25
Hi. I am fairly newish to Ubuntu but I still want to install Wine. I did what they told me to do on the website (winehq.org). When the Software Sources aksed to reload the package information, there was some error. I thought it didn't matter, so I went to Add/Remove software, but it wouldn't let me click the box next to Wine (it was all greyish). I decided to do it with synaptics, but when I go to install Wine, it has some error message (see thumbnails)

Is there a way to install this non-installable file that wine depends on?

---

### Post by alex.rayu on 2008-12-25
Hi. Are you installing it from how it's reccomended here [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb) ?

If yes, then did you do anything to the system?

---

### Post by vegetarianshrimp on 2008-12-25
Yes, I am downloading it from there. The error message when it was trying to do the package information thing had to do with dell, and I do have a dell computer that came with ubuntu. Is that what you mean?

---

### Post by albinootje on 2008-12-25
> **vegetarianshrimp said:**
> Hi. I am fairly newish to Ubuntu but I still want to install Wine. I did what they told me to do on the website (winehq.org). When the Software Sources aksed to reload the package information, there was some error. I thought it didn't matter, so I went to Add/Remove software, but it wouldn't let me click the box next to Wine (it was all greyish). I decided to do it with synaptics, but when I go to install Wine, it has some error message (see thumbnails)

Is there a way to install this non-installable file that wine depends on?

Do you really need the latest Wine version ?
Why not use the one that comes with Ubuntu ?

Here are instructions for the Wine-versions from winehq.org for Ubuntu.

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

If you follow those instructions properly you should not get any errors during the "reload package information".

Which Ubuntu release are you using ?
And can you post the errors you got during the "reload package information" ?

---

### Post by vegetarianshrimp on 2008-12-25
> **albinootje said:**
> Do you really need the latest Wine version ?
Why not use the one that comes with Ubuntu ?

Here are instructions for the Wine-versions from winehq.org for Ubuntu.

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

If you follow those instructions properly you should not get any errors during the "reload package information".

Which Ubuntu release are you using ?
And can you post the errors you got during the "reload package information" ?

I didn,t know Wine came with Ubuntu. How do I get to it?
I am using 8.04 hardy heron. Those were the instructions I followed, but as I said, when I went to Add/Remove, I couldn't check the box (it wouldn't let me). 
About the error message, It happens every time, even when I deleted the Wine stuff. Here it is:
> W: Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy/Release.gpg](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy/Release.gpg)  Could not resolve 'dell-mini.archive.canonical.com'

W: Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2)  Could not resolve 'dell-mini.archive.canonical.com'

W: Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2)  Could not resolve 'dell-mini.archive.canonical.com'

W: Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'dell-mini.archive.canonical.com'

W: Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'dell-mini.archive.canonical.com'

W: Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-updates/Release.gpg](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-updates/Release.gpg)  Could not resolve 'dell-mini.archive.canonical.com'

W: Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'dell-mini.archive.canonical.com'

W: Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2)  Could not resolve 'dell-mini.archive.canonical.com'

W: Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'dell-mini.archive.canonical.com'

W: Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'dell-mini.archive.canonical.com'

W: Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-security/Release.gpg](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-security/Release.gpg)  Could not resolve 'dell-mini.archive.canonical.com'

W: Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2)  Could not resolve 'dell-mini.archive.canonical.com'

W: Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2)  Could not resolve 'dell-mini.archive.canonical.com'

W: Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'dell-mini.archive.canonical.com'

W: Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'dell-mini.archive.canonical.com'

W: Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-netbook-base/Release.gpg](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-netbook-base/Release.gpg)  Could not resolve 'dell-mini.archive.canonical.com'

W: Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-netbook-base/main/i18n/Translation-en_US.bz2](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-netbook-base/main/i18n/Translation-en_US.bz2)  Could not resolve 'dell-mini.archive.canonical.com'

W: Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-netbook-base/universe/i18n/Translation-en_US.bz2](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-netbook-base/universe/i18n/Translation-en_US.bz2)  Could not resolve 'dell-mini.archive.canonical.com'

W: Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-netbook-base/multiverse/i18n/Translation-en_US.bz2](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-netbook-base/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'dell-mini.archive.canonical.com'

W: Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-netbook-base/restricted/i18n/Translation-en_US.bz2](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-netbook-base/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'dell-mini.archive.canonical.com'

W: Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/Release.gpg](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/Release.gpg)  Could not resolve 'dell-mini.archive.canonical.com'

W: Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/i18n/Translation-en_US.bz2](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/i18n/Translation-en_US.bz2)  Could not resolve 'dell-mini.archive.canonical.com'

W: Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/universe/i18n/Translation-en_US.bz2](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/universe/i18n/Translation-en_US.bz2)  Could not resolve 'dell-mini.archive.canonical.com'

W: Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/multiverse/i18n/Translation-en_US.bz2](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'dell-mini.archive.canonical.com'

W: Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/restricted/i18n/Translation-en_US.bz2](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'dell-mini.archive.canonical.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-lpia/Packages.gz)  404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-lpia/Packages.gz)  404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-lpia/Packages.gz)  404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-lpia/Packages.gz)  404 Not Found

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Some index files failed to download, they have been ignored, or old ones used instead.


(My computer is a dell computer that came with Ubuntu, that might explain the tthings that have to do with dell)

---

### Post by albinootje on 2008-12-25
> **vegetarianshrimp said:**
> I didn,t know Wine came with Ubuntu. How do I get to it?
In a terminal you would do :
```

sudo apt-get update
sudo apt-get install wine

``` I am using 8.04 hardy heron. 
Interesting errors, it looks like you have a problem with the /etc/apt/sources.list somehow, and have/had a problem with internet-connection somehow.
This one :
[http://dell-mini.archive.canonical.com/ubuntu/dists/hardy/Release.gpg](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy/Release.gpg)
is visible for me, but some others give 404's also.
It's possible that there's a temporary error with the Dell mini repositories, see here :

[http://ubuntuforums.org/showthread.php?t=1020384](http://ubuntuforums.org/showthread.php?t=1020384)
There's a bug-report about it :
[https://bugs.launchpad.net/dell-mini/+bug/296430](https://bugs.launchpad.net/dell-mini/+bug/296430)
The attached file is the "default" repositories for a "normal" Ubuntu desktop installation.

---

### Post by vegetarianshrimp on 2008-12-25
> **albinootje said:**
> Interesting errors, it looks like you have a problem with the /etc/apt/sources.list somehow, and have/had a problem with internet-connection somehow.
This one :
[http://dell-mini.archive.canonical.com/ubuntu/dists/hardy/Release.gpg](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy/Release.gpg)
is visible for me, but some others give 404's also.
It's possible that there's a temporary error with the Dell mini repositories, see here :

[http://ubuntuforums.org/showthread.php?t=1020384](http://ubuntuforums.org/showthread.php?t=1020384)
There's a bug-report about it :
[https://bugs.launchpad.net/dell-mini/+bug/296430](https://bugs.launchpad.net/dell-mini/+bug/296430)
The attached file is the "default" repositories for a "normal" Ubuntu desktop installation.


Is there a way to make Ubuntu "normal" on my computer?

---

### Post by albinootje on 2008-12-25
> **vegetarianshrimp said:**
> Is there a way to make Ubuntu "normal" on my computer?

You can do the following in a terminal :
```

sudo gedit /etc/apt/sources.list

```

You can then put # signs in front of all the lines you already have in /etc/apt/sources.list
And then insert/add the lines from the attachment of my previous reply.
Save the file, and after that start the "add/remove" or Synaptic package manager.

For more information about that file and adding repositories :
[https://help.ubuntu.com/community/SourcesList](https://help.ubuntu.com/community/SourcesList)

---

### Post by vegetarianshrimp on 2008-12-25
> **albinootje said:**
> You can do the following in a terminal :
```

sudo gedit /etc/apt/sources.list

```

You can then put # signs in front of all the lines you already have in /etc/apt/sources.list
And then insert/add the lines from the attachment of my previous reply.
Save the file, and after that start the "add/remove" or Synaptic package manager.

For more information about that file and adding repositories :
[https://help.ubuntu.com/community/SourcesList](https://help.ubuntu.com/community/SourcesList)

I did all that, then:
I opened Add/Remove. It asked to reload the repositories or something like that. I  said yes, it did its thing, there was some error. Wine was still non-clickable. I went to synaptics and did reload, and i got this (I'm pretty sure its the same thing that it said in Add/Remove):
> Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct. 
ailed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://uk.archive.ubuntu.com/ubuntu/dists/hardy/main/binary-lpia/Packages.gz](http://uk.archive.ubuntu.com/ubuntu/dists/hardy/main/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://uk.archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz](http://uk.archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://uk.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz](http://uk.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://uk.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-lpia/Packages.gz](http://uk.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://uk.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-lpia/Packages.gz](http://uk.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://uk.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-lpia/Packages.gz](http://uk.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://uk.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-lpia/Packages.gz](http://uk.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://uk.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-lpia/Packages.gz](http://uk.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-lpia/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.


---

### Post by albinootje on 2008-12-25
> **vegetarianshrimp said:**
> I did all that, then:
I opened Add/Remove. It asked to reload the repositories or something like that. I  said yes, it did its thing, there was some error. I went to synaptics and did reload, and i got this (I'm pretty sure its the same thing that it said in Add/Remove):

Well done! :)
But you don't seem to be online with your Dell Mini.

Can you post the output of :
```

ifconfig -a
route -n
cat /etc/resolv.conf
ping -c3 ping.xs4all.nl
ping -c3 62.108.1.65

```

And, as a side-note, did you check these two webpages already ?
[https://help.ubuntu.com/community/DellMini9](https://help.ubuntu.com/community/DellMini9)
[http://www.ubuntumini.com/](http://www.ubuntumini.com/)

---

### Post by vegetarianshrimp on 2008-12-25
I saw the blog one, but not the official one. Thanks! That will be helpful

How am I not online if I'm on the Ubuntu forums with it? 
Ok, so I did the code you asked me to do in the terminal, and I got this
```
daniel@daniel:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:21:70:ca:58:2b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:2625726076 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:220 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr 00:23:08:1c:e2:62  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:8ff:fe1c:e262/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6770 errors:0 dropped:0 overruns:0 frame:8097
          TX packets:6266 errors:5 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6867750 (6.5 MB)  TX bytes:1105585 (1.0 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1265 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1265 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:68276 (66.6 KB)  TX bytes:68276 (66.6 KB)

daniel@daniel:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1
daniel@daniel:~$ cat /etc/resolv.conf
### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   5453
#
### END INFO



nameserver 192.168.1.1


daniel@daniel:~$ ping -c3 ping.xs4all.nl
PING uucp1.xs4all.nl (194.109.21.51) 56(84) bytes of data.
64 bytes from uucp1.xs4all.nl (194.109.21.51): icmp_seq=1 ttl=50 time=173 ms
64 bytes from uucp1.xs4all.nl (194.109.21.51): icmp_seq=2 ttl=50 time=173 ms
64 bytes from uucp1.xs4all.nl (194.109.21.51): icmp_seq=3 ttl=50 time=176 ms

--- uucp1.xs4all.nl ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 173.533/174.524/176.053/1.148 ms
daniel@daniel:~$ ping -c3 62.108.1.65
```

---

### Post by albinootje on 2008-12-25
> **vegetarianshrimp said:**
> I saw the blog one, but not the official one. Thanks! That will be helpful

How am I not online if I'm on the Ubuntu forums with it? 

Thanks for the output! :)

Ping is working as it should, and you write that you have internet in your browser, however apt-get is having problems finding those repositories :(
It is possible that you're behind a proxy-ing firewall.
Do you need proxy settings in Firefox ?

---

### Post by vegetarianshrimp on 2008-12-25
I don't really understand what you're asking, but proxy-wise, I think I have the default right now on firefox.

---

### Post by albinootje on 2008-12-25
> **vegetarianshrimp said:**
> I don't really understand what you're asking, but proxy-wise, I think I have the default right now on firefox.

Okay, good.
Can you open [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) in Firefox ?

---

### Post by LANT on 2008-12-25
Trying to provide a longer and alternative solution to your problem. You can also compile wine.
[http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449]("http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449")
Once you got the source code, right click, extract here. 
Open a terminal.
**cd whateverFolferWineIsIn**
**./configure**
If you have any dependency missing, it will warning you, install dependencies (you can do that with synaptic if you want).
If you installed dependencies repeat the **./configure**
**make depend && make**
**sudo make install**

Hope that help you, if so please don't forget to thank me :p

EDIT: Oh, and don't think it is looping while making, it takes a loooong time to compile wine (it took about 15-20 minutes on my pc, dual core 2.3ghz)

---

### Post by albinootje on 2008-12-25
> **vegetarianshrimp said:**
> I did all that, then:
I opened Add/Remove. It asked to reload the repositories or something like that. I  said yes, it did its thing, there was some error. Wine was still non-clickable. I went to synaptics and did reload, and i got this (I'm pretty sure its the same thing that it said in Add/Remove):

Ah, I see a problem here.
Somehow you didn't correctly copy and paste from the attached sources.list.txt file that I offered or something else went wrong.
Can you please show the content of your /etc/apt/sources.list as a txt attachment here ?
Thanks in advance.

---

### Post by vegetarianshrimp on 2008-12-25
> **albinootje said:**
> Okay, good.
Can you open [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) in Firefox ?
Yes I can:

Index of /
[ICO]	Name	Last modified	Size
[DIR]	ubuntu/	25-Dec-2008 21:54 	- 	 
Apache/2.2.8 (Ubuntu) Server at uk.archive.ubuntu.com Port 80

---

### Post by albinootje on 2008-12-25
> **vegetarianshrimp said:**
> Yes I can:

Index of /
[ICO]	Name	Last modified	Size
[DIR]	ubuntu/	25-Dec-2008 21:54 	- 	 
Apache/2.2.8 (Ubuntu) Server at uk.archive.ubuntu.com Port 80

Cool, thanks.
Now it's a matter of fixing the content of /etc/apt/sources.list.

---

### Post by vegetarianshrimp on 2008-12-25
> **LANT said:**
> Trying to provide a longer and alternative solution to your problem. You can also compile wine.
[http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449]("http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449")
Once you got the source code, right click, extract here. 
Open a terminal.
**cd whateverFolferWineIsIn**
**./configure**
If you have any dependency missing, it will warning you, install dependencies (you can do that with synaptic if you want).
If you installed dependencies repeat the **./configure**
**make depend && make**
**sudo make install**

Hope that help you, if so please don't forget to thank me :p

EDIT: Oh, and don't think it is looping while making, it takes a loooong time to compile wine (it took about 15-20 minutes on my pc, dual core 2.3ghz)

Sorry, I don't understand what you want me to do. Can you tell me **exactly** what I should do? I extracted it to Desktop, what now?

---

### Post by vegetarianshrimp on 2008-12-25
> **albinootje said:**
> Cool, thanks.
Now it's a matter of fixing the content of /etc/apt/sources.list.

And how do I do that?:P

---

### Post by albinootje on 2008-12-25
> **vegetarianshrimp said:**
> Sorry, I don't understand what you want me to do. Can you tell me **exactly** what I should do? I extracted it to Desktop, what now?

Forget about compiling Wine for the moment, it will take many hours to compile and needs loads of disk-space, and it won't work as long as you don't fix the repositories problem first.

---

### Post by albinootje on 2008-12-25
> **vegetarianshrimp said:**
> And how do I do that?:P

Did you make a backup of /etc/apt/sources.list ?
Then you might as wel remove all the content of /etc/apt/sources.list and add only the content of the attached txt file i've attached earlier on in this thread.

---

### Post by LANT on 2008-12-25
> **vegetarianshrimp said:**
> Sorry, I don't understand what you want me to do. Can you tell me **exactly** what I should do? I extracted it to Desktop, what now?

Oh... sorry, not used to talk to new ones.
First of all, open a terminal, Alt+F2 and type "terminal" without quotes, then hit enter.
Then, you should type the commands I wrote (the words in bold).

Try it, you will also learn something new :D

---

### Post by LANT on 2008-12-25
> **albinootje said:**
> Forget about compiling Wine for the moment, it will take many hours to compile and needs loads of disk-space, and it won't work as long as you don't fix the repositories problem first.

True, sorry for posting it as a solution then... you should repair first your sources.lst file!!! Hope to have at least provided you a preview of maybe future knowledge

---

### Post by vegetarianshrimp on 2008-12-25
> Did you make a backup of /etc/apt/sources.list ?
Then you might as wel remove all the content of /etc/apt/sources.list and add only the content of the attached txt file i've attached earlier on in this thread.
I'll try that, but can you tell me how to make a backup? (sorry that sounded stupid:().

---

### Post by albinootje on 2008-12-25
> **vegetarianshrimp said:**
> I'll try that, but can you tell me how to make a backup? (sorry that sounded stupid:().

No worries.
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list-backup
sudo gedit /etc/apt/sources.list

```
Then:
1) ctl-a to select all
2) then e.g. backspace key to remove all text
3) then copy and paste the content of the attached sources.lists.txt
4) save and exit

---

### Post by albinootje on 2008-12-25
> **LANT said:**
> True, sorry for posting it as a solution then... you should repair first your sources.lst file!!! Hope to have at least provided you a preview of maybe future knowledge

:)
I know it can be exciting and interesting to start compiling software if you have the time for it.

It is quite possible that the last time I compiled Wine was on my 486 years ago, I can imagine it took a few days to finish, hehe.
Luckily nowadays machines are faster, and if you have a network of more computers you can try distcc (which I still would like to try).

---

### Post by vegetarianshrimp on 2008-12-25
> **albinootje said:**
> No worries.
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list-backup
sudo gedit /etc/apt/sources.list

```
Then:
1) ctl-a to select all
2) then e.g. backspace key to remove all text
3) then copy and paste the content of the attached sources.lists.txt
4) save and exit

Ok i did all that. I went to Add/Remove to see if Wine was downloadable, and I got the same error message!
> Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://uk.archive.ubuntu.com/ubuntu/dists/hardy/main/binary-lpia/Packages.gz](http://uk.archive.ubuntu.com/ubuntu/dists/hardy/main/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://uk.archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz](http://uk.archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://uk.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz](http://uk.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://uk.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-lpia/Packages.gz](http://uk.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://uk.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-lpia/Packages.gz](http://uk.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://uk.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-lpia/Packages.gz](http://uk.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://uk.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-lpia/Packages.gz](http://uk.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://uk.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-lpia/Packages.gz](http://uk.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-lpia/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by albinootje on 2008-12-25
> **vegetarianshrimp said:**
> Ok i did all that. I went to Add/Remove to see if Wine was downloadable, and I got the same error message!

Hmmm, weird... [edited]
Is it possible that the Dell Mini uses a special processor that really needs special repositories, which are now offline temporarily ? :(

Can try the lines from this posting :
[http://ubuntuforums.org/archive/index.php/t-983005.html](http://ubuntuforums.org/archive/index.php/t-983005.html)

by "pleinad, November 17th, 2008, 10:57 PM"

I've copied them in here, but the lines where too long.
Make sure to remove the old lines.

---

### Post by vegetarianshrimp on 2008-12-25
same thing. Yes, it is the only thing there. Yes, Im clicking save.

---

### Post by vegetarianshrimp on 2008-12-25
got your message, Thanks, It worked! I'm going to try to install Wine again, I'll let you know my results.

---

### Post by albinootje on 2008-12-25
> **vegetarianshrimp said:**
> same thing. Yes, it is the only thing there. Yes, Im clicking save.

Sorry for the confusion earlier on. :(

As stated in my previous edited reply, this seems to be the right solution for the Dell Mini repository problems :
[http://ubuntuforums.org/archive/index.php/t-983005.html](http://ubuntuforums.org/archive/index.php/t-983005.html)

---

### Post by albinootje on 2008-12-25
> **vegetarianshrimp said:**
> got your message, Thanks, It worked! I'm going to try to install Wine again, I'll let you know my results.

Good, I'm glad it's fixed in the end! :)

---

### Post by vegetarianshrimp on 2008-12-25
oh wait...it didn't :( I get the same error mesage but only these show up:

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-lpia/Packages.gz)  404 Not Found

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]

Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by albinootje on 2008-12-25
> **vegetarianshrimp said:**
> oh wait...it didn't :( 

Please remove from /etc/apt/sources.list all of the lines which are not those ones :

```

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-dell-mini main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-dell-mini main universe multiverse restricted

```

---

### Post by vegetarianshrimp on 2008-12-25
wine worked, i still get the error message though.thank you sooooooooo much!!!!!!!

---

