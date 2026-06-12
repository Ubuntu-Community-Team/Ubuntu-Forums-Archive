---
title: "Rdiff-backup release sensitive"
date: 2023-04-07
forum: Server Platforms
---

### Post by aljames2 on 2023-04-07
Focal 20.04 uses rdiff-backup version 2.0.0, while Jammy 22.04 uses 2.0.5.  I have a server running 20.04 & a client with 22.04.  I am getting warnings about the versions being different & failure to work.

Looking at this compatibility list, it appears that systems intending to use rdiff-backup accross a network need to run the same ubuntu release for things to work, unless there is a backport available.

[https://repology.org/project/rdiff-backup/versions](https://repology.org/project/rdiff-backup/versions)

I have not found a way to downgrade the rdiff-backup version on 22.04.

This has happened before, when my server was running 18.04 and my desktop was running 20.04.  The incompatibility here was due to rdiff-backup upgrading to Python 3.0.  There was a backport available in this case.  I have not found a way to downgrade the rdiff-back version on 22.04.

I suppose I will need to upgrade my server release soon.  Has anyone else ran into this?

---

### Post by mikodo on 2023-04-07
Hello, what worked for me with a different application, was to comment out the present  /etc/apt/sources.list and add the same list for the release you are wanting. In this case 20.04. Then purge the 22.04 application of rdiff-backup and then install the 20.04 application with apt install. After the install, change back your sources list to reflect Jammy.

Example if your 22.04 /etc/apt/sources.list  looks like this:  

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) Jammy main  

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) Jammy partner  

deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) Jammy partner

  deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) Jammy-security main    

Change it to look like this:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal main  

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal partner  

deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal partner  

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-security main  

I hope this works for you.

---

### Post by aljames2 on 2023-04-08
Thank you for the suggestion. I tried your method on a MATE 22.04 VM and it failed for me.  I made a backup of the sources.list file first, then made the edits as you suggested.  After so, I ran sudo apt update which pointed me to all the focal repos.  On sudo apt install rdiff-backup, the following was returned:
```

The following information may help to resolve the situation:

The following packages have unmet dependencies:
 rdiff-backup : Depends: python3 (< 3.9) but 3.10.6-1~22.04 is to be installed
                Recommends: python3-pylibacl but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

Jammy runs on Python 3.10.x, whereas Focal runs on a lower version with different dependencies. Not sure these can be overcome in this case.

---

### Post by mikodo on 2023-04-10
> **aljames2 said:**
>  Jammy runs on Python 3.10.x, whereas Focal runs on a lower version with different dependencies. Not sure these can be overcome in this case.
If you still want to explore this, possibly the solution lies in apt pinning . Here are a couple of links about this:

Ubuntu Community Help Wiki:

[https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)

Debian Wiki AptConfiguration:

[https://wiki.debian.org/AptConfiguration](https://wiki.debian.org/AptConfiguration)

Apt pinning

*Force installation of a package from a repository

[URL="https://wiki.debian.org/AptConfiguration#apt_preferences_.28APT_pinning.29"]
[/URL]

---

### Post by TheFu on 2023-04-10
Have you checked that the resulting rdiff-backup areas aren't correct?  A 3rd level change shouldn't impact the stored formats.  Even between v1.x and v2.x rdiff-backup versions, the storage format was compatible enough. It was just the network serialization that broke.

I'm backing up 22.04 systems (via pull) with the default rdiff-backup on 20.04 backup server.  The backup directories all seem fine. I moved to a Linux Mint v21.1 desktop in late Feb.  This is based on Ubuntu 22.04.
```
$ more inc-sizes-deneb-2023-04-09 
        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Sun Apr  9 00:04:24 2023         11.0 GB           11.0 GB   (current mirror)
Sat Apr  8 00:04:26 2023         1.98 MB           11.0 GB
Fri Apr  7 00:04:34 2023         1.50 MB           11.0 GB
Thu Apr  6 00:04:38 2023         2.83 MB           11.0 GB
...
Fri Mar  3 00:04:13 2023         9.06 MB           13.9 GB
Thu Mar  2 00:04:16 2023         5.11 MB           13.9 GB
Wed Mar  1 08:30:58 2023          445 KB           13.9 GB
```
That seems reasonable.  Just looked at the rdiff/ subdir. Seems fine. The desktop has v2.0.5-3build1. The server is running v2.0.5 too. Odd.   Perhaps your 20.04 systems just need a patch?
```
$ lsb_release -d
Description:    Linux Mint 21.1

$ lsb_release -d
Description:    Ubuntu 20.04.6 LTS

```

---

### Post by aljames2 on 2023-04-11
> **TheFu said:**
> That seems reasonable.  Just looked at the rdiff/ subdir. Seems fine. The desktop has v2.0.5-3build1. The server is running v2.0.5 too. Odd.   Perhaps your 20.04 systems just need a patch?


Hmm, I see. This should work then.  I will check in to this more, must be something else going on.

Thank you both!

---

### Post by aljames2 on 2023-04-12
Success!  works as usual.

I guess having my backups scripted for some time has made me a bit rusty using rdiff-backup at the command line.  Flawed use of my --include --exclude  options in my test.

I do get this warning thrown each time, but I suppose it is just for awareness purposes.
```
Warning: Local version 2.0.0 does not match remote version 2.0.5.
```

Thanks again :smile:

---

### Post by mIk3_08 on 2023-04-13
> **aljames2 said:**
> Success!  works as usual.

I guess having my backups scripted for some time has made me a bit rusty using rdiff-backup at the command line.  Flawed use of my --include --exclude  options in my test.

I do get this warning thrown each time, but I suppose it is just for awareness purposes.
```
Warning: Local version 2.0.0 does not match remote version 2.0.5.
```

Thanks again :smile:
On how to mark this thread as solve,
Please Click the "Solve thread" link below. Regards and cheers.

---

### Post by TheFu on 2023-04-13
> **aljames2 said:**
> Success!  works as usual.

I guess having my backups scripted for some time has made me a bit rusty using rdiff-backup at the command line.  Flawed use of my --include --exclude  options in my test.

I do get this warning thrown each time, but I suppose it is just for awareness purposes.
```
Warning: Local version 2.0.0 does not match remote version 2.0.5.
```

Thanks again :smile:

Be careful saying "thrown", since that usually means an exception and exceptions generally kill a program.
It is a warning ... and I don't understand why your 20.04 system isn't running rdiff-backup 2.0.5 when mine do. Ah ... I see. I have the rdiff-backup "backports" for focal PPA installed.

---

### Post by aljames2 on 2023-04-15
> **TheFu said:**
> Be careful saying "thrown", since that usually means an exception and exceptions generally kill a program.
It is a warning
Got it, that makes sense.

> **TheFu said:**
>  ... and I don't understand why your 20.04 system isn't running rdiff-backup 2.0.5 when mine do. Ah ... I see. I have the rdiff-backup "backports" for focal PPA installed.

I just updated my focal server, now it has rdiff-backup version 2.0.5. :)

I had not tried the backports.  In reading this resource I did not think the backport applied here since my server already had 2.0.0 on it.  I thought the backports were only for updating older debian/ubuntu releases from rdiff-backup 1.x.x to 2.x.x.
[https://launchpad.net/~rdiff-backup/+archive/ubuntu/rdiff-backup-backports](https://launchpad.net/~rdiff-backup/+archive/ubuntu/rdiff-backup-backports)

All set now, and thanks again for the extra post :D

---

