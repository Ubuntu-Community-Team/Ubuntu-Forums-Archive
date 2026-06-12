---
title: "Upgrading to 16.04(.2) from an EOL version"
date: 2017-02-24
forum: Server Platforms
---

### Post by johnlocke2342 on 2017-02-24
Hi.
I will soon be a Windows Technician while being a Linux (more particularily Ubuntu) enthusiast for the past 10 years (my first Linux ever was Ubuntu 7.04).
In order to get my diploma I am currently in an internship at my hometown's city hall IT department.

I know Ubuntu pretty well and my boss wants me to help him upgrade the city's servers running Ubuntu to a "recent, updateable" Ubuntu version. The problem is I'm not sure what version they're on (neither does my boss), all I know is it reached EOL status a while ago (it's between 14.10-15.10). 

[I found a workaround on the wiki]("https://help.ubuntu.com/community/EOLUpgrades") to update an EOL version of Ubuntu to a newer one, but my boss doesn't believe it'd be enough. Is he right? I can't tell for sure, I'm sure it'd work on a desktop Ubuntu but the only servers I worked on so far are running Windows Server.

If it's not enough, could someone please tell me the steps to perform the upgrade (I think 16.04.2 would be perfect for the time being, since it's a LTS). 

Thanks in advance.

---

### Post by howefield on 2017-02-24
> **johnlocke2342 said:**
> The problem is I'm not sure what version they're on (neither does my boss), all I know is it reached EOL status a while ago (it's between 14.10-15.10).

Find out where you are starting from..

```
cat /etc/*-release
```

Probably

```
echo $XDG_CURRENT_DESKTOP
```

as well.

---

### Post by johnlocke2342 on 2017-02-24
Thanks for the reply, now he says it's 15.10. I'll check anyway.

---

### Post by howefield on 2017-02-24
> **johnlocke2342 said:**
> Thanks for the reply, now he says it's 15.10. I'll check anyway.

That would be the best chance of a successful upgrade given that it is only one step away from 16.04.2.

The wiki that you link to should work. I've fired up a machine with a default Ubuntu 15.10 on it, upgrade was flawless with the upgrader taking care of sorting out the sources ect,..

```
do-release-upgrade -c
Checking for a new Ubuntu release
Your Ubuntu release is not supported anymore.
For upgrade information, please visit:
http://www.ubuntu.com/releaseendoflife

New release '16.04.2 LTS' available.
Run 'do-release-upgrade' to upgrade to it.
```
to check for new release availability and then..

```
sudo do-release-upgrade
[sudo] password for hugh: 
Checking for a new Ubuntu release
Your Ubuntu release is not supported anymore.
For upgrade information, please visit:
http://www.ubuntu.com/releaseendoflife

Get:1 Upgrade tool signature [836 B]                                           
Get:2 Upgrade tool [1,265 kB]                                                  
Fetched 1,266 kB in 0s (0 B/s)                                                 
authenticate 'xenial.tar.gz
```

and on it continued to a successful 16.04.2

```
cat /etc/*-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.2 LTS"
NAME="Ubuntu"
VERSION="16.04.2 LTS (Xenial Xerus)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 16.04.2 LTS"
VERSION_ID="16.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"
VERSION_CODENAME=xenial
UBUNTU_CODENAME=xenial
```

Goes without saying that all important data should be backed up before hand of course.

---

### Post by johnlocke2342 on 2017-02-27
Oh I was sure I answered your reply this weekend! Thanks for it, then.
Is the process the same as on a desktop version? I wanted to try on my "testing" PC this weekend but didn't see the point if not.
Anyway, back to work, will see when the boss wants to do the upgrade.

---

### Post by howefield on 2017-02-27
> **johnlocke2342 said:**
> Is the process the same as on a desktop version? I wanted to try on my "testing" PC this weekend but didn't see the point if not.

Yes, it was actually a desktop that I gave the above example for. Point being that the upgrade manager took care of all the changes to the sources.

If you are upgrading a desktop then you should remove all proprietary drivers and  return the system to as much of a default position as possible, ie removing software installed from PPAs.. (although the upgrade manager should disable any ppa's as a matter of course), Again, the point is that the further away from a stock install that you are the higher the risk of something going wrong.

Also worth noting that early in the process (before anything destructive takes place) you will be given the opportunity to check the packages that will be affected by the upgrade, ensure that you view the details and possibly also again at the end of the process if packages are to be removed. It's more obvious when you use the graphical update manager but that won't be the case on the server ?

---

### Post by johnlocke2342 on 2017-02-27
Thanks. I'll try later this week with a 15.10 desktop vm as that "testing" PC is at my mom's, where I don't live anymore except on weekends. I know it's not exactly the same as on a "real" computer but I think the process is the same. I already upgraded an Ubuntu release, but I never updated (nor used) a server version, let alone one that reached EOL status (let that be a desktop or a server).

---

### Post by howefield on 2017-02-27
> **johnlocke2342 said:**
> ..... let alone one that reached EOL status (let that be a desktop or a server).

The good news is that the process was seamless even though the 15.10 that I upgraded was of course, EOL. You'd never have known the install was "unsupported" with regards to upgrading it.

Good luck and keep us updated :)

---

### Post by johnlocke2342 on 2017-03-03
OK. I had a talk with the boss this morning, it's a 15.04, not 15.10 (he also has another VM which is up to date to 16.04). What I don't understand is he updated it in front of me, and the update process worked without switching servers. But the version upgrade doesn't work. Can we upgrade directly to 16.04.2? Or do we have to upgrade to EOL 15.10 beforehand?
He told me he knew it's the official procedure but that when he did it it messed up the mysql database which suddenly became blank! I think you can understand why I'm gathering as much info as I can.

---

