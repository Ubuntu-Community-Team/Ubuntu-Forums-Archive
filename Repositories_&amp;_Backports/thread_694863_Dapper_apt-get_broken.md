---
title: "Dapper apt-get broken"
date: 2008-02-12
forum: Repositories &amp; Backports
---

### Post by mattymonkey on 2008-02-12
Hi all,

I have been working on this for an hour or so now.. My net works fine and I can connect manually in Firefox to the source, I have tried many people's different suggestionson source.list and manually setting my DNS etc.. I am not sure what is wrong.. 

I have finally decided to go with my original sources.list, here is a paste of that:

#
# deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted


deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe


And here is the error I am getting running "sudo apt-get update"

admin@cbms-media1:/etc/apt$ sudo apt-get update
Ign cdrom://Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1) dapper Release.gpg
Ign cdrom://Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1) dapper Release
Ign cdrom://Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1) dapper/main Packages
Ign cdrom://Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1) dapper/restricted Packages
Err cdrom://Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1) dapper/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1) dapper/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg
  Connection failed [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg
  Connection failed [IP: 91.189.88.31 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
  Connection failed [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
  Connection failed [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
  Connection failed [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
  Connection failed [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
  Connection failed [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
  Connection failed [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
  Connection failed [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
  Connection failed [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
  Connection failed [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
  Connection failed [IP: 91.189.88.46 80]
50% [Connecting to security.ubuntu.com (91.189.88.37)]

And then stalls for awhile, eventually failing.

Any thouights? Again I can ping these repositories just fine. I can also connect to them threw firefox. Only apt and Synaptic seem broken

Thanks for any and all help.

---

### Post by ajgreeny on 2008-02-12
I'm not certain it will help, but I suggest you comment out the second line at the top referring to your cdrom.  Once the system is up and running, this really isn't needed or helpful.

---

### Post by mattymonkey on 2008-02-14
Thanks for the reply, I have tried that but it didn't help.

I am at the point now where I think Im going to try a different distrobution.. I tried 7.10 Desktop and Server, Alternate and Live, but nothing seems to work.. Incompatible hardware I guess.

The 7.10 gives me that "No Common CD-Rom drive detected error" during install.. Even though it booted from the cd drive and got to that point running off it.. Silly

---

