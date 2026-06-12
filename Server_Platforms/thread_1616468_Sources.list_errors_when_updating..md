---
title: "Sources.list errors when updating."
date: 2010-11-08
forum: Server Platforms
---

### Post by grey580 on 2010-11-08
Hello all. When trying to update I'm getting some errors.
 
```
albert@PresMiamiUbuntu00:/etc/apt$ sudo apt-get update
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages
404 Not Found [IP: 91.189.88.37 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages
404 Not Found [IP: 91.189.88.37 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources
404 Not Found [IP: 91.189.88.37 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages
404 Not Found [IP: 91.189.92.172 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages
404 Not Found [IP: 91.189.92.172 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Sources
404 Not Found [IP: 91.189.92.172 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources
404 Not Found [IP: 91.189.88.37 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages
404 Not Found [IP: 91.189.88.37 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Sources
404 Not Found [IP: 91.189.92.172 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources
404 Not Found [IP: 91.189.88.37 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages
404 Not Found [IP: 91.189.92.172 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources
404 Not Found [IP: 91.189.92.172 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages
404 Not Found [IP: 91.189.92.172 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages
404 Not Found [IP: 91.189.88.37 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources
404 Not Found [IP: 91.189.88.37 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources
404 Not Found [IP: 91.189.92.172 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages
404 Not Found [IP: 91.189.92.172 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages
404 Not Found [IP: 91.189.92.172 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources
404 Not Found [IP: 91.189.92.172 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Sources
404 Not Found [IP: 91.189.92.172 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages
404 Not Found [IP: 91.189.92.172 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources
404 Not Found [IP: 91.189.92.172 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages
404 Not Found [IP: 91.189.92.172 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources
404 Not Found [IP: 91.189.92.172 80]
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.37 80]
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.172 80]
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.172 80]
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz) 404 Not Found [IP: 91.189.92.172 80]
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz) 404 Not Found [IP: 91.189.92.172 80]
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.172 80]
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.gz) 404 Not Found [IP: 91.189.92.172 80]
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.172 80]
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.37 80]
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/source/Sources.gz) 404 Not Found [IP: 91.189.88.37 80]
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/source/Sources.gz) 404 Not Found [IP: 91.189.88.37 80]
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.37 80]
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/source/Sources.gz) 404 Not Found [IP: 91.189.92.172 80]
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.172 80]
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.172 80]
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Sources.gz) 404 Not Found [IP: 91.189.92.172 80]
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz) 404 Not Found [IP: 91.189.92.172 80]
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.172 80]
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz) 404 Not Found [IP: 91.189.92.172 80]
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/source/Sources.gz) 404 Not Found [IP: 91.189.88.37 80]
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.37 80]
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/source/Sources.gz) 404 Not Found [IP: 91.189.88.37 80]
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.172 80]
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz) 404 Not Found [IP: 91.189.92.172 80]
[/QUOTE]
 
When looking at the links. It seems that the intrepid repositories have been removed.
So I need to update my sources.list. Can anyone help me with that?
 
[QUOTE]
#
# deb cdrom:[Ubuntu-Server 8.10 _Intrepid Ibex_ - Release i386 (20081028.1)]/ intrepid main restricted
#deb cdrom:[Ubuntu-Server 8.10 _Intrepid Ibex_ - Release i386 (20081028.1)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
 

```
 
Thanks.

---

### Post by howefield on 2010-11-08
Intrepid went end of life, April 2010, hence your issues.

Given that the next upgrade to that, Jaunty 9.04 is also end of life, you might be better considering backing up your data and installing 10.04.1 which is the current Long Term Support release supported till April 2013 on the desktop, or 10.10 which is the current non LTS release supported till April 2012.

---

### Post by Sef on 2010-11-08
You are correct that the updates have been removed. Intrepid was updated for 18 months which is time normal time for nonLTS Ubuntu distros. There are no more updates for it. If you want to update, then I suggest either using the latest nonLTS - [Marverik Meerkat]("http://www.ubuntu.com/desktop/get-ubuntu/download") or the latest LTS - [Lucid Lynx]("http://www.ubuntu.com/desktop/get-ubuntu/download"). (To get Lucid, change Meerkat to Koala.)

There is an archive where you can get the updates,but I would have to look for it. The updates are for the 18 months, it was being patched.

---

### Post by grey580 on 2010-11-08
> **howefield said:**
> Intrepid went end of life, April 2010, hence your issues.
 
Given that the next upgrade to that, Jaunty 9.04 is also end of life, you might be better considering backing up your data and installing 10.04.1 which is the current Long Term Support release supported till April 2013 on the desktop, or 10.10 which is the current non LTS release supported till April 2012.
 
well that makes sense. i'm going to upgrade to Jaunty so that I can at least be somewhat secure. And then look into 10.
 
thanks.

---

### Post by Sef on 2010-11-08
> well that makes sense. i'm going to upgrade to Jaunty so that I can at least be somewhat secure. And then look into 10.

Jaunty has also reached its end of life, so any current security holes will not get patched. You can update from Intrepid to Jaunty to Lucid, which will be patched for 5 years instead of 18 months since it is a Long Term Supported (LTS.)

---

### Post by tomerzz on 2010-11-11
i'm also facing the same problem with 8.10 ,
but as i've installed 10.04 before and had issues (like many others) with ipw2200 driver , i downgraded back to 8.10 as for some reason it is much more stable wireless wise for me. 

i'm quite happy the way things are right now with 8.10 , is there anyway to solve this issue?

UPDATE: changed main repository server in sources.list to 
[http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/)
seems to be working.

---

