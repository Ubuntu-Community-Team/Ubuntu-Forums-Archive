---
title: "Unmet dependency hell"
date: 2011-04-05
forum: Server Platforms
---

### Post by puremetal on 2011-04-05
Hi all,

I'm trying to get remastersys working on my Dapper 6.06.2 LTS server, but keep running into dependency issues. I have added the remastersys repository to my sources.list.

This is what happens after apt-get update

> # apt-get install remastersys


Reading package lists... Done
Building dependency tree... Done

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  remastersys: Depends: xresprobe but it is not going to be installed
E: Broken packages


So then I try to install xeresprobe and get this:

> # apt-get install xresprobe

Reading package lists... Done
Building dependency tree... Done

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  xresprobe: Depends: libc6 (>= 2.5-0ubuntu1) but 2.3.6-0ubuntu20.6 is to be installed
E: Broken packages



What's going on here and what can I do to fix it? I don't understand that last bit about libc6. Should I install libc6 and keep going until I don't have any unmet dependencies left? :confused:

Thanks :)


PS: I'm trying to get remastersys working because I want to make a LiveCD of my system so that I can install and test it on another (local) machine before I make some changes to my production server. If anyone knows of a better way than remastersys to do this, I'm all ears!

---

### Post by volkswagner on 2011-04-05
> The following packages have unmet dependencies.
xresprobe: Depends: libc6 (>= 2.5-0ubuntu1) but 2.3.6-0ubuntu20.6 is to be installed
E: Broken packages 



I think you will get this sort of thing often with an older system with mismatched sources.list.

If your not sue what the above means... xresprobe needs libc6 version to be greater than 2.5, but with your sources list 2.3.6 is the latest version.

Did you run apt-get update first?

I think you could end up breaking your working system if you continue.

Why not try cloning the system with Clonezilla and try restoring it to a second system that has a hard drive you won't mind overwriting.  Proving the hardware is not drastically different you may have a great success, as on boot Ubuntu will load proper drivers for the system.

---

### Post by puremetal on 2011-04-05
I did run apt-get update, yeah. I read elsewhere about this being an issue with a mismatched sources list, but I don't see what is mismatched - everything is Dapper, except for repositories that didn't seem to have a specific Dapper version. That said I've had other issues with unmet dependencies on this system before, so I must indeed have a problem!

> 
# deb cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted

deb [http://213.171.201.6/dapper/](http://213.171.201.6/dapper/) dapper main
#deb [http://213.171.201.6/dapper-test/](http://213.171.201.6/dapper-test/) dapper main

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://apt-mirror.sourceforge.net/](http://apt-mirror.sourceforge.net/) apt-mirror/
deb [http://ubuntu.blueyonder.co.uk/archive/](http://ubuntu.blueyonder.co.uk/archive/) blueyonder archive
deb [http://mirrors.kernel.org/ubuntu/](http://mirrors.kernel.org/ubuntu/) kernelorg mirror
##deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) remastersys/
##deb [http://live.debian.net/debian/](http://live.debian.net/debian/) etch main

# Remastersys
deb [http://www.remastersys.klikit-linux.com/repository](http://www.remastersys.klikit-linux.com/repository) remastersys/



Thanks for the warning though - I'll try clonezilla instead and see if that'll work. Thanks :)

---

