---
title: "Ubuntu server 14.04 Unable to locate package"
date: 2014-05-20
forum: Server Platforms
---

### Post by liz3 on 2014-05-20
I have just installed ubuntu server 14.04 and am now trying to install java.
I have tried 
```
sudo apt-get install openjdk-7-jdk
```

And I get the error:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package openjdk-7-jdk
```

I have tried running 
```
sudo apt-get update
```
but that doesn't change anything (everything seems up to date).

When I checked whether java was installed already by using java -version it tells me it isn't installed but can be installed using the package openjdk-7-jre-headless, which leads to the same error.

I have recently successfully installed ubuntu server 14.04 on a different machine so I copied over /etc/apt/sources.list from there but that doesn't change anything.
This is what it looks like:

```
# deb cdrom:[Xubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140416.2)]/ trusty main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ trusty main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ trusty universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty universe
deb http://gb.archive.ubuntu.com/ubuntu/ trusty-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ trusty multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
deb http://security.ubuntu.com/ubuntu trusty-security universe
deb-src http://security.ubuntu.com/ubuntu trusty-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse
deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu trusty partner
# deb-src http://archive.canonical.com/ubuntu trusty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
deb-src http://extras.ubuntu.com/ubuntu trusty main

```

If this question has been answered a million times already could you please point me at the right thread? For most people the update seems to solve things but it doesn't for me.

---

### Post by bapoumba on 2014-05-20
```
bapoumba@SonyBlue:~$ apt-cache policy openjdk-7-jre-headless
openjdk-7-jre-headless:
  Installed: 7u55-2.4.7-1ubuntu1
  Candidate: 7u55-2.4.7-1ubuntu1
  Version table:
 *** 7u55-2.4.7-1ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ trusty-updates/main i386 Packages
        500 http://archive.ubuntu.com/ubuntu/ trusty-security/main i386 Packages
        100 /var/lib/dpkg/status
     7u51-2.4.6-1ubuntu4 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/main i386 Packages

```
The package is in main, so you should get it. please try using the another mirror or even the main ubuntu repos (remove the **gb.** from your repos url in the source.list and **sudo apt-get update** again).

---

### Post by liz3 on 2014-05-21
I tried switching to archive.ubuntu.com (instead of gb.archive.ubuntu.com) and ran update but it still gives me the unable to locate package error.

I can ping both gb.archive as well as archive without a problem, so I think it is not the connection. Any ideas what this could be?

---

### Post by bapoumba on 2014-05-21
Ah.. As you have both -updates and -security in your sources.list, that will need some investigation, and I am not with my ubuntu computer for now :)

What is the output to 
```
sudo apt-get update
apt-cache policy openjdk-7-jdk

```

---

### Post by liz3 on 2014-05-21
Thanks for the quick reply![B]

sudo apt-get update[/B]
```
Ign http://security.ubuntu.com trusty-security InRelease
Ign http://security.ubuntu.com trusty-security Release.gpg
Ign http://security.ubuntu.com trusty-security Release
Ign http://security.ubuntu.com trusty-security/universe Translation-en
Reading package lists... Done

```

**apt-cache policy openjdk-7-jdk**
```
N: Unable to locate package openjdk-7-jdk
```

On a different machine I managed to install openjdk-7-jdk without a problem, both machines are running ubuntu server 14.04.

---

### Post by bapoumba on 2014-05-21
Is there anything else to the ```
sudo apt-get update
``` command ? There should be a lot more. On the other hand, if apt-get does not read the whole sources.list, it can explain why you cannot install the package. Now the question would be why does apt-get not hit all the repos in the sources.list..

Edit : 
Idea n° 1 : if you are using the same sources.list on a working computer, please rename the current one sources.list_bak (or whatever you use for backups) and copy over a working one. Then run again sudo apt-get update and sudo apt-get upgrade.
Idea n°2 : move the var/lib/apt/archive.ubuntu.com.blabla and var/lib/apt/extras.ubuntu.com.blabla (if you have them) somewhere to empty /var/lib/apt and run sudo apt-get update and sudo apt-get upgrade again
1 & 2 _should_ lead to the same result.
Idea n°3 : and may be stupid one, is the machine connected to the internet ?

---

### Post by liz3 on 2014-05-21
I copied over the file from the working setup (that's the one with the gb in it): 
and I get:
**sudo apt-get update**```

Ign http://extras.ubuntu.com trusty InRelease 
Ign http://extras.ubuntu.com trusty Release.gpg
Ign http://extras.ubuntu.com trusty Release
Err http://extras.ubuntu.com trusty/main Sources
  
Err http://extras.ubuntu.com trusty/main Sources
  
Err http://extras.ubuntu.com trusty/main Sources
  
Err http://extras.ubuntu.com trusty/main Sources
  
Err http://extras.ubuntu.com trusty/main Sources
  gnutls_handshake() warning: The server name sent was not recognized
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/trusty/main/source/Sources  gnutls_handshake() warning: The server name sent was not recognized

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

Running it a second time gives me:
```
Ign http://security.ubuntu.com trusty-security InRelease
Ign http://security.ubuntu.com trusty-security Release.gpg
Ign http://security.ubuntu.com trusty-security Release
Ign http://security.ubuntu.com trusty-security/universe Translation-en
Reading package lists... Done
```

**sudo apt-get upgrade**
says
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

If I try idea 2 then I only get the update output without the errors (the second one).

I can ping gb.archive.ubuntu.com so I guess that means that the computer is connected to the internet (I can access it from the local network as well).
I really don't understand what is going on here...

---

### Post by bapoumba on 2014-05-21
OK, I wont be able to help you that much here as I am completely illiterate when it comes to servers, I'll move your thread to the server section so that others can help you.

That said and for now, I think the error to look at is this one :
```
gnutls_handshake() warning: The server name sent was not recognized
```
The sudo apt-get update should be a lot more talkative that it is now. So I think, from what I have read running that error into a web search, that your server does not update or hit the repos when you run update or upgrade commands.
Here are a few of the links I found, the ones that look the most appropriate to me (and again, my perspective may be wrong here picking them up) :
[https://bugs.launchpad.net/ubuntu/+source/pycurl/+bug/926548](https://bugs.launchpad.net/ubuntu/+source/pycurl/+bug/926548)
[https://stackoverflow.com/questions/7766961/git-trouble-via-https-routinesssl23-get-server-hello](https://stackoverflow.com/questions/7766961/git-trouble-via-https-routinesssl23-get-server-hello)
[http://osdir.com/ml/debian-bugs-dist/2010-01/msg02576.html](http://osdir.com/ml/debian-bugs-dist/2010-01/msg02576.html)
[https://groups.google.com/forum/#!topic/git-users/nE5eXzN74uo](https://groups.google.com/forum/#!topic/git-users/nE5eXzN74uo)

Other question, would you happen to be behind a proxy ?

Edit : Moved to Server Platforms.

---

### Post by steeldriver on 2014-05-21
I agree with bapoumba - there should be a lot more output from the 'update' command - it should either '**Hit**', '**Err**or', or '**Ign**ore' each repository listed in your /etc/sources.list file - it's almost like it's not even *trying *to hit most of the repos

I also wondered about proxying - however I would think that a working proxy should result in a 'Hit' and a bad proxy in an 'Err' (possibly accompanied by the proxy's IP). Nevertheless you could try

```

sudo apt-get -o **Acquire::http::Proxy=DIRECT** update

```

I also wondered about possible corruption of the /var/lib/apt/lists files - you could also try removing and recreating them

```

sudo rm -rf /var/lib/apt/lists/*

sudo apt-get update

```

Finally (and this is uncharted territory for me) there are some debug options for apt-get e.g.

```

sudo apt-get **-o Debug::Acquire::http=1** update

```

---

### Post by bapoumba on 2014-05-21
Thanks steeldriver :)

In my post #6, I *think* that making a new sources.list is, in the end, equivalent to removing everything from /var/lib/apt/lists/, as the archive lists *should be* recreated in both cases. liz3 should try removing everything as you suggested or at least moving everything out from the file so we can rule that option out if it still does not work.

I really am not able to help with the gnutls error.

---

### Post by liz3 on 2014-05-27
I've now tried a new install (from a new CD with a newly downloaded image) and I can install packages during install but not later...
Installing ubuntu desktop works and I can install packages so I might just leave desktop running on it even though I don't need the GUI.

I'm still quite puzzled by this and have no idea what could have caused the problem...

---

