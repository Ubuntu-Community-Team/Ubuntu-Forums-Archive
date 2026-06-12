---
title: "No SSH in 10.10"
date: 2010-11-29
forum: Security
---

### Post by TheFr00n on 2010-11-29
I recently did a clean install of 10.10 on my serverbox at home. All of a sardine, SSH, which had worked perfectly under 10.04, was no longer available.

After far too much researching (I am not a guru), I was able to establish that there was no SSH server installed. Shouldn't be a problem, you would think - just install one.

But there's no openssh in the Ubuntu Software Center. You can't get it via the package manager either. When I tried to manually install via apt-get, I got an error telling me that openssh-server has no install candidate.

Can anyone shed some light on why Ubuntu would dump such a standard security tool? Thankfully I still have the 10.04 iso (which came with SSH working out of the box), but what gives?

---

### Post by squaregoldfish on 2010-11-29
The package you're looking for is openssh-server.

Steve.

---

### Post by TheFr00n on 2010-11-29
Oh, I'm well aware of that. It's just not available in 10.10.

> :~$ sudo apt-get install openssh-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package openssh-server is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'openssh-server' has no installation candidate
:~$ 

---

### Post by surfer on 2010-11-29
could you post the output of
```
$ cat /etc/apt/sources.list
```
and
```
sudo apt-get update
```
openssh-server is in the reporitories! trust me.

---

### Post by squaregoldfish on 2010-11-29
Hmm. It's on my clean install (64bit alternate). No idea why it's not on your setup.

---

### Post by TheFr00n on 2010-11-29
OK here's my output of cat /etc/apt/sources.list:

> #deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick universe
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick multiverse
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse


And then, here's my output of sudo apt-get update:

> Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick Release.gpg                                                                        
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick/main Translation-en                                                        
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_ZA                                                     
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_ZA
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_ZA
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_ZA
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick-updates Release.gpg
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg [316B]           
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en    
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_ZA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg         
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_ZA
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_ZA
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_ZA
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick Release                    
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick-updates Release                                  
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_ZA                       
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release [57.3kB]             
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_ZA
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_ZA
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick/main Sources                 
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_ZA
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_ZA
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                          
  
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick/restricted Sources           
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick/universe Sources
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick/multiverse Sources
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick/main i386 Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick/restricted i386 Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick/multiverse i386 Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick-updates/main Sources
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick-updates/restricted Sources
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick-updates/universe Sources
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick-updates/multiverse Sources
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick-updates/main i386 Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick-updates/restricted i386 Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick-updates/universe i386 Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick-updates/multiverse i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages
Fetched 317B in 2s (149B/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DB141E2302FDF932

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/Release](http://extras.ubuntu.com/ubuntu/dists/maverick/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.


I'm noticing an error on the end there, but I'm not sure what it means or how to fix it.

---

### Post by wojox on 2010-11-29
Run:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192
```

---

### Post by surfer on 2010-11-29
this is strange; the package is here: [http://za.archive.ubuntu.com/ubuntu/pool/main/o/openssh/]("http://za.archive.ubuntu.com/ubuntu/pool/main/o/openssh/") .

the problem remains after the apt-get update? there is no openssh-server in synaptic?

to fix the key:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys DB141E2302FDF932

```

---

### Post by TheFr00n on 2010-11-29
Quick request for clarity: both you and wojox are asking me to run this apt-key adv command, but with different arguments on the end.

What's the difference between the two?

EDIT: I'm impatient, so I ran them both. Wojox's one resulted in no change, but surfer's did the trick. OpenSSH is installing as we speak.

THANKS!

---

### Post by surfer on 2010-11-29
yes, i just took wojox's command and added the public key you're missing.

glad to hear things work out!

---

