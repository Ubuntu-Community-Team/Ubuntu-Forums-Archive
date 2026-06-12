---
title: "apt-get update problem and pakage install problem"
date: 2005-04-24
forum: Repositories &amp; Backports
---

### Post by MakarX on 2005-04-24
**ok whenever i udate through synaptic pakage manager or through terminal i get this error:**
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/main Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/universe Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/multiverse Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/restricted Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/main Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/universe Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/multiverse Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/restricted Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/main Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/universe Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/multiverse Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/restricted Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/main Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/universe Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/multiverse Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/restricted Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
[B]
When ever i update with apt-get update i get this problem:[/B]

E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory




HELP ME PLZ

---

### Post by Nis on 2005-04-24
Right now the Ubuntu backports server is down.  Your first problem will fix itself in a few days.  Try running 'sudo apt-get update' to fix the second problem.  Running apt-get update without sudo will not work since apt-get needs to run with root priviledges.

---

### Post by Zensunni on 2005-05-01
Herm...

I have this same problem. But when I try to update my apt-get, I get this:

Failed to fetch [ftp://ftp.nerim.net/debian-marillat/dists/stable/Release](ftp://ftp.nerim.net/debian-marillat/dists/stable/Release)  Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)
Failed to fetch [ftp://ftp.nerim.net/debian-marillat/dists/testing/Release](ftp://ftp.nerim.net/debian-marillat/dists/testing/Release)  Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

So, I can't do apt-get for anything else, and apt-get won't update....any help would be awesome.

---

### Post by mendicant on 2005-05-03
Zensunni, your issue is that the debian-marillat repository doesn't have amd64 packages in the testing and stable repositories.

---

### Post by talkingwires on 2005-06-18
> When ever i update with apt-get update i get this problem:

E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
I was having this very same problem this morning. It turned out that the System Notifier was busy checking for updates and had a lock on the apt package list while it worked.

---

### Post by hakimu on 2005-10-10
to get rid of the permission problem run apt-get update as root, or simply 

[INDENT]sudo apt-get update[/INDENT]

if you get the other errors, probebly is somthing wrong with the proxy setting

[INDENT]export http_proxy="http://proxyIPAddress:ServerPortnumber"[/INDENT] 

and the you can run sudo apt-get update

Hope it works:cool:

---

### Post by dta on 2006-08-23
i have an issue. i search and search, and i am still a newb.( about 3 hours ago). lol so i figured that this will be a good place to put it on. can you help me, and explain how to do it, since i am a real noob when it comes to this stuff. thanks

```
# apt-get update
Ign file: apt-build Release.gpg
Get:1 file: apt-build Release [89B]
Ign file: apt-build/main Packages
Get:2 http://archive.ubuntu.com dapper-updates Release.gpg [189B]
Get:3 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:4 http://archive.ubuntu.com dapper-backports Release.gpg [189B]
Hit http://archive.ubuntu.com dapper-updates Release
Hit http://archive.ubuntu.com dapper Release
Hit http://archive.ubuntu.com dapper-backports Release
Hit http://archive.ubuntu.com dapper-updates/main Packages
Get:5 http://security.ubuntu.com dapper-security Release.gpg [189B]
Get:6 http://archive.ubuntu.com dapper-updates/restricted Packages [14B]
Hit http://security.ubuntu.com dapper-security Release
Hit http://archive.ubuntu.com dapper-updates/universe Packages
Hit http://archive.ubuntu.com dapper-updates/multiverse Packages
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://archive.ubuntu.com dapper/restricted Packages
Ign http://archive.ubuntu.com dapper/multiverse Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Get:7 http://archive.ubuntu.com dapper-backports/main Packages [14B]
Get:8 http://archive.ubuntu.com dapper-backports/restricted Packages [14B]
Get:9 http://archive.ubuntu.com dapper-backports/universe Packages [14B]
Get:10 http://archive.ubuntu.com dapper-backports/multiverse Packages [14B]
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/multiverse Packages
Hit http://security.ubuntu.com dapper-security/universe Sources
Get:11 http://archive.ubuntu.com dapper/multiverse Packages [121kB]
99% [11 Packages gzip 0] [Connecting to us.archive.ubuntu.com]      13.3kB/s 0s
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com dapper/multiverse Packages
  Sub-process gzip returned an error code (1)
Get:12 http://us.archive.ubuntu.com dapper Release.gpg [189B]
Get:13 http://us.archive.ubuntu.com dapper-updates Release.gpg [189B]
Get:14 http://us.archive.ubuntu.com dapper-backports Release.gpg [189B]
Hit http://us.archive.ubuntu.com dapper Release
Hit http://us.archive.ubuntu.com dapper-updates Release
Hit http://us.archive.ubuntu.com dapper-backports Release
Hit http://us.archive.ubuntu.com dapper/main Sources
Hit http://us.archive.ubuntu.com dapper/restricted Sources
Ign http://us.archive.ubuntu.com dapper/universe Sources
Hit http://us.archive.ubuntu.com dapper-updates/main Sources
Hit http://us.archive.ubuntu.com dapper-updates/restricted Sources
Hit http://us.archive.ubuntu.com dapper-backports/main Sources
Hit http://us.archive.ubuntu.com dapper-backports/restricted Sources
Hit http://us.archive.ubuntu.com dapper-backports/universe Sources
Hit http://us.archive.ubuntu.com dapper-backports/multiverse Sources
Get:15 http://us.archive.ubuntu.com dapper/universe Sources [1312kB]
99% [15 Sources gzip 0]                                              3095B/s 0s
gzip: stdin: not in gzip format
Err http://us.archive.ubuntu.com dapper/universe Sources
  Sub-process gzip returned an error code (1)
Fetched 168B in 28s (6B/s)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
W: Duplicate sources.list entry cdrom://Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1) dapper/main Packages (/var/lib/apt/lists/Ubuntu%206.06.1%20%5fDapper%20Drake%5f%20-%20Release%20i386%20(20060807.1)_dists_dapper_main_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1) dapper/restricted Packages (/var/lib/apt/lists/Ubuntu%206.06.1%20%5fDapper%20Drake%5f%20-%20Release%20i386%20(20060807.1)_dists_dapper_restricted_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

