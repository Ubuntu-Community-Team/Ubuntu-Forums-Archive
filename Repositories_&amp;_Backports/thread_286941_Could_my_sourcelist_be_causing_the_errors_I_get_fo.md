---
title: "Could my sourcelist be causing the errors I get for mplayer install?"
date: 2006-10-28
forum: Repositories &amp; Backports
---

### Post by maddbaron on 2006-10-28
I am trying to install mplayer and its plugin

But I keep getting errors such as

> Fetched 18.4kB in 6s (2744B/s)
Failed to fetch [http://asher256-repository.tuxfamily...86/Packages.gz](http://asher256-repository.tuxfamily...86/Packages.gz) 404 Not Found
Failed to fetch [http://asher256-repository.tuxfamily...86/Packages.gz](http://asher256-repository.tuxfamily...86/Packages.gz) 404 Not Found
Failed to fetch [http://asher256-repository.tuxfamily...86/Packages.gz](http://asher256-repository.tuxfamily...86/Packages.gz) 404 Not Found
Reading package lists... Done
W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 18B52FE3521A9C7C
W: GPG error: [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9
W: GPG error: [http://mrpouit.tuxfamily.org](http://mrpouit.tuxfamily.org) edgy-pouit Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

and

> maddbaron@baronworks:~$ sudo apt-get install mplayer
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
mplayer: Depends: libdirectfb-0.9-22 but it is not installable
E: Broken packages

Here is my sourcelist

> deb-src [http://mrpouit.tuxfamily.org](http://mrpouit.tuxfamily.org) edgy-pouit extra 
deb [http://mrpouit.tuxfamily.org](http://mrpouit.tuxfamily.org) edgy-pouit extra 
deb-src [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) dapper 3v1n0 
deb [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) dapper 3v1n0 
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main 
deb [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) ubuntu main dupdate french 
deb [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) edgy main dupdate french 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main 


deb cdrom:[Kubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted 

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe 

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse 

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe 

#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) dapper main

deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
#AUTOMATIX REPOS END


Can someone point me in right direction please? I am also getting errors when I try to install other programs in adept and I have 3 updates that won't update because all of it says Broken in bright red letters. I ran apt-get update and still get the errors.

---

### Post by Qrk on 2006-10-28
> Failed to fetch [http://asher256-repository.tuxfamily...86/Packages.gz](http://asher256-repository.tuxfamily...86/Packages.gz) 404 Not Found
Failed to fetch [http://asher256-repository.tuxfamily...86/Packages.gz](http://asher256-repository.tuxfamily...86/Packages.gz) 404 Not Found
Failed to fetch [http://asher256-repository.tuxfamily...86/Packages.gz](http://asher256-repository.tuxfamily...86/Packages.gz) 404 Not Found
Reading package lists... Done
W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 18B52FE3521A9C7C
W: GPG error: [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9
W: GPG error: [http://mrpouit.tuxfamily.org](http://mrpouit.tuxfamily.org) edgy-pouit Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718

I'd start by removing these repositories. 

Also, it seems you are using a dapper repository for wine. Its a bad idea, so I'd remove this repository as well.


deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) dapper main


You may also want to remove the google repository, I'm not sure what its for, but I assume something like google-earth.

Its a bad idea to get too creative with your sources.list.

---

### Post by maddbaron on 2006-10-28
Thank You It Worked!

---

