---
title: "[SOLVED] update problem, repository connection failure"
date: 2007-08-14
forum: Repositories &amp; Backports
---

### Post by fethio on 2007-08-14
I've posted in Installation&Upgrade forum but I think this place may be more appropriate... Switched from XP to kubuntu recently. I used to use Debian when I was a student in the States many years ago.

I'm having a problem with my repository connection. First I noticed it using adept, the kubuntu package manager, and I thought it was the problem, so I decided to use apt-get instead. But, when I used apt-get install I had a similar problem. Here's the output of apt-get when I run the command:

fethi@desktop-A709:/$sudo apt-get install synaptic
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
docbook-xml libvte-common libvte9 scrollkeeper sgml-data
Suggested packages:
docbook docbook-doc docbook-dsssl docbook-xsl perlsgml doc-html-w3 opensp libxml2-utils dwww
Recommended packages:
gksu deborphan libgnome2-perl
The following NEW packages will be installed:
docbook-xml libvte-common libvte9 scrollkeeper sgml-data synaptic
0 upgraded, 6 newly installed, 0 to remove and 106 not upgraded.
3 not fully installed or removed.
Need to get 2973kB of archives.
After unpacking 16.8MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) feisty/main sgml-data 2.0.3 [279kB]
Err [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) feisty/main docbook-xml 4.4-5
Bad header line [IP: 91.189.89.8 80]
Get:2 [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) feisty/main libvte-common 1:0.16.1-0ubuntu1 [122kB]
Err [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) feisty/main libvte-common 1:0.16.1-0ubuntu1
Error reading from server. Remote end closed connection [IP: 91.189.89.6 80]
Get:3 [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) feisty/main libvte9 1:0.16.1-0ubuntu1 [736kB]
Err [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) feisty/main libvte9 1:0.16.1-0ubuntu1
Error reading from server. Remote end closed connection [IP: 91.189.89.6 80]
Get:4 [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) feisty/main scrollkeeper 0.3.14-11ubuntu7 [187kB]
Get:5 [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) feisty/main synaptic 0.57.11.1ubuntu14 [1310kB]
Err [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) feisty/main synaptic 0.57.11.1ubuntu14
Error reading from server. Remote end closed connection [IP: 91.189.89.6 80]
Fetched 466kB in 4m9s (1869B/s)
Failed to fetch [http://tr.archive.ubuntu.com/ubuntu/..._2.0.3_all.deb](http://tr.archive.ubuntu.com/ubuntu/..._2.0.3_all.deb) MD5Sum mismatch
Failed to fetch [http://tr.archive.ubuntu.com/ubuntu/..._4.4-5_all.deb](http://tr.archive.ubuntu.com/ubuntu/..._4.4-5_all.deb) Bad header line [IP: 91.189. 89.8 80]
Failed to fetch [http://tr.archive.ubuntu.com/ubuntu/...buntu1_all.deb](http://tr.archive.ubuntu.com/ubuntu/...buntu1_all.deb) Error reading from serve r. Remote end closed connection [IP: 91.189.89.6 80]
Failed to fetch [http://tr.archive.ubuntu.com/ubuntu/...untu1_i386.deb](http://tr.archive.ubuntu.com/ubuntu/...untu1_i386.deb) Error reading from server. Re mote end closed connection [IP: 91.189.89.6 80]
Failed to fetch [http://tr.archive.ubuntu.com/ubuntu/...ntu14_i386.deb](http://tr.archive.ubuntu.com/ubuntu/...ntu14_i386.deb) Error reading from se rver. Remote end closed connection [IP: 91.189.89.6 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
ll synaptic


I've looked at the following posts which report similar problems due to proxy configurations, but found out that in my case, I have no proxies set, and I connect to the internet directly, so their solution didn't work for me..

[http://ubuntuforums.org/showthread.php?t=266590](http://ubuntuforums.org/showthread.php?t=266590) Connection Fails to Repositories

[http://ubuntuforums.org/showthread.php?t=257988&page=2](http://ubuntuforums.org/showthread.php?t=257988&page=2) Connection Fails to Repositories

[http://thread.gmane.org/gmane.linux....67/focus=80212](http://thread.gmane.org/gmane.linux....67/focus=80212) Synaptec connection problem

BTW when I use adept to do the update, it is able to download some of the packages, but most of them leave with an error following the download. Again most of the time, the error appears when the download is almost complete. It says somethings like "connection with the server was reset"...

Could anyone help me with this please?

fethi

---

### Post by GeeZor on 2007-08-14
```

sudo apt-get upgrade

sudo apt-get update


```

and you should be on your way again.. but you may need to update before upgradeing.. 

if that fails, download a file calles sources.list and put that in /etc/apt

make sure it is a generic one and you problems are solved for sure. 

good luck.

ps. any reason for u to use the tr mirrors? use other mirrors if that is okay... but the tr in the url is what is causing your problems, that for sure.

---

### Post by Seisen on 2007-08-14
Try using the main server and see if that fixes the problem. Sometimes their are problems with the mirrors.

---

### Post by GeeZor on 2007-08-14
look here:
[http://file.twntwn.info/static/sources.list.feisty]("http://file.twntwn.info/static/sources.list.feisty")

---

### Post by fethio on 2007-08-15
Here's the fix from thread [http://ubuntuforums.org/showthread.php?t=257988&page=2](http://ubuntuforums.org/showthread.php?t=257988&page=2)

"guote"
hey i had similar problem and this is how itis to be fixed. On terminal type sudo gedit /etc/apt/sources.list to open and edit the file. open another terminal or system>administration>network tools. inthe open file wherever you find a web address e.g archive.ubuntu.com , security.ubuntu.com replace it with ipv4 address. So your entry will look like now
deb [http://123.123.123.123/ubuntu](http://123.123.123.123/ubuntu) ...... .
instead of

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) ....

. where 123.123.123.123 is the address u obtain when u ping respective web addresses.

Same way u can connect ur GAIM or evolution by giving ipv4 addresses in place of web addresses.
However firefox is all right . You dont need anything foe that.

Hope this works. Happy computing
"unquote"

---

### Post by GeeZor on 2007-08-16
that is a realy lame way of solving this issue. But if it works, it works. For your sake i hope they never change ip's..

---

### Post by ozooha on 2007-08-16
> **fethio said:**
> Here's the fix from thread [http://ubuntuforums.org/showthread.php?t=257988&page=2](http://ubuntuforums.org/showthread.php?t=257988&page=2)

"guote"
hey i had similar problem and this is how itis to be fixed. On terminal type sudo gedit /etc/apt/sources.list to open and edit the file. open another terminal or system>administration>network tools. inthe open file wherever you find a web address e.g archive.ubuntu.com , security.ubuntu.com replace it with ipv4 address. So your entry will look like now
deb [http://123.123.123.123/ubuntu](http://123.123.123.123/ubuntu) ...... .
instead of

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) ....

. where 123.123.123.123 is the address u obtain when u ping respective web addresses.

Same way u can connect ur GAIM or evolution by giving ipv4 addresses in place of web addresses.
However firefox is all right . You dont need anything foe that.

Hope this works. Happy computing
"unquote"

Its functional but rather lame coz if the IP address changes then you are back to square one.
The thread above also suggests the use of /etc/apt/apt.conf file but I do not have that file in the first place...so what do I do then?
OZooHA

---

