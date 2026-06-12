---
title: "gzip trouble with apt-get update"
date: 2005-01-03
forum: Repositories &amp; Backports
---

### Post by nikopol on 2005-01-03
haven't managed to find a solution to this one. 

I enter the sources.list file correctly (I've done this on many computers before so it's not a problem wtih that) but I get some rather bizarre output from the ubuntu servers:


# sudo apt-get update
Err cdrom://Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020) unstable/main Packages
  Please use apt-cdrom to make this CD recognized by APT. apt-get update cannot be used to add new CDs
Ign cdrom://Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020) unstable/main Release
Err cdrom://Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020) unstable/restricted Packages
  Please use apt-cdrom to make this CD recognized by APT. apt-get update cannot be used to add new CDs
Ign cdrom://Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020) unstable/restricted Release
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/main Packages [315kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main Packages [2145kB]
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Release
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable/main Packages
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable/main Release
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/main Packages
  Error reading from server - read (104 Connection reset by peer) [IP: 82.211.81.138 80]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/main Release
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/restricted Packages [19.6kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/restricted Release
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/main Sources [37.6kB]
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/main Release
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/restricted Sources [1551B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/restricted Release
20% [3 Packages gzip 0] [2 Packages 466872/2145kB 21%]
gzip: stdin: not in gzip format
Err [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/restricted Packages
  Sub-process gzip returned an error code (1)
25% [4 Sources gzip 0] [2 Packages 583672/2145kB 27%]
gzip: stdin: not in gzip format
Err [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/main Sources
  Sub-process gzip returned an error code (1)
34% [5 Sources gzip 0] [2 Packages 818732/2145kB 38%]
gzip: stdin: not in gzip format
Err [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/restricted Sources
  Sub-process gzip returned an error code (1)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main Packages
  Error reading from server - read (104 Connection reset by peer)
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main Release
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/restricted Packages [21.3kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/restricted Release
3% [6 Packages gzip 0] [Waiting for headers]
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/restricted Packages
  Sub-process gzip returned an error code (1)
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main Sources [686kB]
23% [7 Sources gzip 0] [Connecting to archive.ubuntu.com (82.211.81.138)]
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main Sources
  Sub-process gzip returned an error code (1)
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main Release
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/restricted Sources [3159B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/restricted Release
23% [8 Sources gzip 0] [Connecting to archive.ubuntu.com (82.211.81.138)]
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/restricted Sources
  Sub-process gzip returned an error code (1)
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/universe Packages [10.5MB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/universe Release
82% [9 Packages gzip 0] [Connecting to archive.ubuntu.com (82.211.81.138)]
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/universe Packages
  Sub-process gzip returned an error code (1)
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/universe Sources [3862kB]
85% [Connecting to archive.ubuntu.com (82.211.81.138)]               464kB/s 5s
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/universe Sources
  Sub-process gzip returned an error code (1)
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/universe Release
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/multiverse Packages [275kB]
86% [Connecting to archive.ubuntu.com (82.211.81.138)]               464kB/s 5s
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/multiverse Packages
  Sub-process gzip returned an error code (1)
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/multiverse Release
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/multiverse Sources [223kB]
86% [Working]                                                        464kB/s 5s
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/multiverse Sources
  Sub-process gzip returned an error code (1)
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/multiverse Release
Fetched 15.6MB in 40s (381kB/s)
Failed to fetch cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/dists/unstable/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD recognized by APT. apt-get update cannot be used to add new CDs
Failed to fetch cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/dists/unstable/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD recognized by APT. apt-get update cannot be used to add new CDs
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/warty/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/warty/main/binary-i386/Packages.gz)  Error reading from server - read (104 Connection reset by peer)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/warty/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/warty/restricted/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/warty/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/warty/main/source/Sources.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/warty/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/warty/restricted/source/Sources.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/warty/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/warty/universe/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/warty/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/warty/universe/source/Sources.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/warty-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/warty-security/main/binary-i386/Packages.gz)  Error reading from server - read (104 Connection reset by peer) [IP: 82.211.81.138 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/warty-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/warty-security/restricted/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/warty-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/warty-security/main/source/Sources.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/warty-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/warty-security/restricted/source/Sources.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/warty/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/warty/multiverse/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/warty/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/warty/multiverse/source/Sources.gz)  Sub-process gzip returned an error code (1)
Reading Package Lists... Done
W: Couldn't stat source package list cdrom://Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020) unstable/main Packages (/var/lib/apt/lists/Ubuntu%204.10%20%5fWarty%20Warthog%5f%20-%20Preview%20i386%20Binary-1%20(20041020)_dists_unstable_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020) unstable/restricted Packages (/var/lib/apt/lists/Ubuntu%204.10%20%5fWarty%20Warthog%5f%20-%20Preview%20i386%20Binary-1%20(20041020)_dists_unstable_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_warty_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_warty_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_warty_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_warty-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_warty-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_warty_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.


Basically, is it something on my ubuntu install that's faulty or is there some trouble at mill with the ubuntu servers? 

Cheers

N

---

### Post by hazza96 on 2005-01-03
[QUOTE=nikopol]Basically, is it something on my ubuntu install that's faulty or is there some trouble at mill with the ubuntu servers?[/QUOTE]
I had no problems with the Ubuntu servers 5 minutes ago, it must be your end.

My suggestion, re-install gzip.

---

### Post by nikopol on 2005-01-03
Thanks for the tip :) The weird thing is that it has no trouble with the nerim repository which had me thinking that the gzip isn't a problem. 

Well I still tried a reinstall of gzip but still no go :(

I'll have a look if I can find any nearby mirrors but I assume that if the problem is with faulty gzip files, they would also have copied over the version that was on the ubuntu servers? 

Strange problem though! :)

---

### Post by nikopol on 2005-01-03
Success! Changed to a german repository (couldn't find a French one) and it's all working fine. 

My sources.list now looks like this:```

## Uncomment the following two lines to fetch updated software from the network

deb http://ftp.inf.tu-dresden.de/os/linux/dists/ubuntu warty main restricted universe multiverse
deb-src http://ftp.inf.tu-dresden.de/os/linux/dists/ubuntu warty main restricted universe multiverse

deb http://ftp.inf.tu-dresden.de/os/linux/dists/ubuntu warty-security main restricted
deb-src http://ftp.inf.tu-dresden.de/os/linux/dists/ubuntu warty-security main restricted

deb ftp://ftp.nerim.net/debian-marillat/ stable main
deb ftp://ftp.nerim.net/debian-marillat/ unstable main
deb ftp://ftp.nerim.net/debian-marillat/ testing main
```

And no more error messages. I'm curious why I was getting them though given that the ubuntu servers didn't seem to be at fault nor did gzip... If anyone needs me to see if I can replicate it again, I'd be glad to test...

---

### Post by hazza96 on 2005-01-03
Are you in England? Are you having any network issues? In your post I noticed the line
> Error reading from server - read (104 Connection reset by peer) [IP: 82.211.81.138 80]
According to [http://www.domainwhitepages.com/](http://www.domainwhitepages.com/) the IP **82.211.81.138** is in England.

Try again tomorrow, see if it sorts itself out. If it does then my guess would be you had connection issues, if it doesn't then start looking at your machine.

---

### Post by nikopol on 2005-01-03
Nope - am currently located in France though will be back in Scotland next week!  8-)

---

### Post by fago on 2005-04-16
i've the same troubles with the austrian debian mirror:
> OK   [http://ubuntu.inode.at](http://ubuntu.inode.at) hoary-security/multiverse Packages
Hole:11 [http://ftp.at.debian.org](http://ftp.at.debian.org) sarge/main Packages [59,4kB]
98% [7 Packages gzip 0] [11 Packages 3571/59,4kB 6%]                76,2kB/s 0s
gzip: stdin: not in gzip format
Fehl [http://ftp.at.debian.org](http://ftp.at.debian.org) unstable/non-US/main Packages
  Unterprozess gzip ist mit einem Fehlercode zurückgekehrt (1)
99% [Warte auf Kopfzeilen (header)]                                 76,2kB/s 0s
gzip: stdin: not in gzip format
Fehl [http://ftp.at.debian.org](http://ftp.at.debian.org) sarge/main Packages
  Unterprozess gzip ist mit einem Fehlercode zurückgekehrt (1)
Hole:12 [http://ftp.at.debian.org](http://ftp.at.debian.org) sarge/contrib Packages [56,3kB]
Hole:13 [http://ftp.at.debian.org](http://ftp.at.debian.org) sarge/non-free Packages [5116B]
99% [12 Packages gzip 0] [13 Packages 123/5116B 2%]                 76,2kB/s 0s
gzip: stdin: not in gzip format
Fehl [http://ftp.at.debian.org](http://ftp.at.debian.org) sarge/contrib Packages
  Unterprozess gzip ist mit einem Fehlercode zurückgekehrt (1)
....

perhaps this a problem with a new feature in ubuntu's apt. afair it has now support for bzip2 compressed files.

---

### Post by xurizaemon on 2005-10-18
Same issue here - fresh 5.10 with network updates enabled thru funky GUI in menu, then it faithfully downloads each Packages.gz file and spits the dummy about not being able to un-bzip2 said .gz file.

gzip and bzip2 both seem to work fine on this machine. But apt-get retrieves one file, then tries to use the other decompressor on it. Silly!

Dead keen for feedback on this. Also mentioned in Debian as [Bug#316337]("http://lists.debian.org/deity/2005/06/msg00262.html"). But not solved (except, "it's intermittent").

---

### Post by xurizaemon on 2005-10-18
<< Removing double post >>

Short answer: no, it's not your apt, and it's not the repositories either :)

Well, not for me. See below.

---

### Post by xurizaemon on 2005-10-18
Ok, I feel a BIT silly spending so long to work this one out, maybe I can help someone else too. After trying LOTS and LOTS of mirrors, and satisfying myself that bzip2 and gzip worked Just Fine on this box, I finally tried ... downloading the Packages.gz file (with wget) and having a gander at it.

(Actually downloading it on the box that was having trouble, not from my remote workstation.)

```
$ wget -nv http://mirror.optusnet.com.au/ubuntu/dists/breezy-updates/main/binary-i386/Packages.bz2
10:51:38 URL:http://mirror.optusnet.com.au/ubuntu/dists/breezy-updates/main/binary-i386/Packages.bz2 [2244] -> "Packages.bz2" [1]
$ file Packages.bz2
Packages.bz2: HTML document text

```

Turned out that the client's proxy content filter (Dan's Firewall) was swapping in a pretty page that says "Access has been restricted, we don't recognise the extension .bz2". But (in deference to Microsoft's cleverness in implementing 'friendly error messages') the firewall doesn't return a 404 or other appropriate HTTP error code, it just serves up the exchanged content in place. BOO to that.

So, if you're getting inexplicably unable-to-be-decompressed files, try yanking the file and see if it looks like you're assuming it does. It might just be that the repositories, APT and all are fine, and something in between you and the repository is hosing things ...

Luckily, on account of their Incredible Firewall Setup, the simple fix was to switch to ftp:// URLs in the /etc/apt/sources.list file - bingo, no more silly proxy content filter.

---

### Post by matrix3D on 2006-05-03
> Luckily, on account of their Incredible Firewall Setup, the simple fix was to switch to ftp:// URLs in the /etc/apt/sources.list file - bingo, no more silly proxy content filter.

Thanks for the suggestion. I was just getting a similar error on one of the US repositories and changing it from http:// to ftp:// in sources.list fixed the problem for me. I really wish people would stop breaking the server configs!

---

### Post by infoseeker on 2006-08-06
> Get:12 [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) dapper/universe Sources [1312kB]
99% [12 Sources gzip 0]
gzip: stdin: not in gzip format
Err [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) dapper/universe Sources
  Sub-process gzip returned an error code (1)
Fetched 106kB in 4m57s (355B/s)
Reading package lists... Done


Seems very much 'on-topic' :)
Maybe I should try another country ?

EDIT: changed all the 'za' entries to 'uk' and all well again :confused:

---

### Post by digeratess on 2006-12-02
> **xurizaemon said:**
> Luckily, on account of their Incredible Firewall Setup, the simple fix was to switch to ftp:// URLs in the /etc/apt/sources.list file - bingo, no more silly proxy content filter.

This solved a big problem for me today. Thanks!

---

### Post by Forceflow on 2006-12-03
Yep, very similar to my problem:
[http://ubuntuforums.org/showthread.php?t=311093](http://ubuntuforums.org/showthread.php?t=311093)

Also fixed it by switching to FTP. I did disable my router's firewall, though.

---

### Post by Koppie on 2007-03-19
Switching to ftp worked for me too!

It's odd, the repos worked for weeks.  And only one of them failed with http; the rest still work.  And I did this from various locations so I don't think it was the firewall either.  Anyway, the problem is solved, so I can worry about something else now!

---

### Post by Thomas Barregren on 2007-08-17
As described at [http://www.barregren.se/node/10]("http://www.barregren.se/blog/sub-process-gzip-returned-error-code-1")   just do following:

```

sudo rm /var/lib/apt/lists/partial/*

```

---

