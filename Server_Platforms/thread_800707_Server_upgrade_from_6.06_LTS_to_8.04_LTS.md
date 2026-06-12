---
title: "Server upgrade from 6.06 LTS to 8.04 LTS"
date: 2008-05-20
forum: Server Platforms
---

### Post by riverty on 2008-05-20
I do:
**lsb_release -a**

I get:
[B]No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 6.06.2 LTS
Release:        6.06
Codename:       dapper[/B]

I want to upgrade to the new 8.04 LTS.

I do:
**do-release-upgrade**

I get:
[B]Checking for a new ubuntu release
No new release found[/B]

I check /etc/apt/sources.list:
[B]## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted[/B]

Looks good. The system **is** fully updated to the dapper repositories.

So, am I updated or not? Nothing has happened "upgrade like" to make me think the system is. If my system is updated, why doesn't it say that running 'lsb_release -a'?

---

### Post by ephmanjmm on 2008-05-20
I followed these instructions for four different servers and it worked each time. The server instructions are near the bottom of the page. [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by cdtech on 2008-05-20
I had the same problem with my 6.06 upgrade, here's what I did:

I copied this list to my sources.list:
```
deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu dapper-proposed main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
```
Don't ask me why my old locations didn't work, they just didn't.

I verified that my current install was completely up to date:
```
sudo aptitude update
sudo aptitude upgrade
sudo aptitude dist-upgrade
```

Install the server-based update utility (This is the core of update-manager and the release upgrade utility):

```
sudo aptitude install update-manager
``` worked for me.
start the upgrade using:
```
sudo do-release-upgrade
```

My results:

/etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION=”Ubuntu 8.04&#8243;

---

### Post by riverty on 2008-05-21
After doing your suggestions:

lsb_release -a:
[B]No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.04
Release:        8.04
Codename:       hardy[/B]

Thank you for your time and response!

---

### Post by vrillusions on 2008-05-22
How have 6.06 LTS server to 8.04 LTS server upgrades been?  It said in the release notes to wait until the first point release, but obviously upgrades are working for people.  Just don't want to do the upgrade and then find out nothing is working :)

Also has anyone done upgrades just over ssh?  The datacenter is like a 30 mile drive, so if I can save the gas, I'm a happy person :)

(edit)I was going to find the link to where it said to wait for point release in june and I can't seem to find it now.  Perhaps that was just an initial suggestion and was removed now that it IS safe to upgrade?(/edit)

---

### Post by cdtech on 2008-05-22
> **riverty said:**
> After doing your suggestions:

lsb_release -a:
[B]No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.04
Release:        8.04
Codename:       hardy[/B]

Thank you for your time and response!

welcome...

---

### Post by wxman on 2008-05-28
I've gone through all the same steps shown above, but mine still shows 6.06.

I'm doing it using PUTTY and a SSH connection if that matters.

---

### Post by K_V_B on 2008-06-01
> **cdtech said:**
> 

```
sudo do-release-upgrade
```




I did exactly what you suggested, as you suggested, But still I get the following:

```
root@aare:/etc/apt# do-release-upgrade 
Checking for a new ubuntu release
No new release found

```

What should I do?

---

### Post by freebullets on 2008-06-01
Ubuntu CD?

---

### Post by wxman on 2008-06-02
> **freebullets said:**
> Ubuntu CD?

Is the CD install smart enough not to overwrite the old installation?

---

### Post by freebullets on 2008-06-02
> **wxman said:**
> Is the CD install smart enough not to overwrite the old installation?

yeah, if you skip around.  experiment with the cd, and theres a step that installs the programs.  Hint: use the go back button

You are using the text based installer right?

---

### Post by Eladon on 2008-06-18
This link says you can use "do-release-upgrade":

[https://help.ubuntu.com/community/HardyUpgrades#head-e059d5452a24b50d09c64df48058ef2d834eb197-2](https://help.ubuntu.com/community/HardyUpgrades#head-e059d5452a24b50d09c64df48058ef2d834eb197-2)

But after trying all the suggestions in this thread, I was never able to get it to work.  This link says you use "do-release-upgrade -d":

[http://www.ubuntu.com/getubuntu/upgrading#head-e059d5452a24b50d09c64df48058ef2d834eb197-2](http://www.ubuntu.com/getubuntu/upgrading#head-e059d5452a24b50d09c64df48058ef2d834eb197-2)

As soon as I added the "-d", away things went, worked great.

I did need to change the contents of the sources.list as mentioned above.  I found the "us.archive.ubuntu.com" entries in sources.list (which were the default for me) didn't work, they gave an error, even when I did apt-get update.  But changing those entries to "archive.ubuntu.com" fixed it.

---

### Post by wxman on 2008-06-18
After trying everything, including threatening the computer by dangling it out the window - in a thunderstorm, I've given up. 

I made the best backup I could for now of the one web site I was testing, then started a reinstall of the whole thing. This time I'm partitioning it so this won't happen again. I would think upgrading the server software should be as easy as upgrading the desktop. I'm using the "Perfect Server" guide again, and of course the reinstall is giving me grief. I can't seem to get past the point where I can start to connect using the SSH terminal. It's probably just my firewall needing adjusting. At least this time I hope to be more prepared to do updates, upgrades, etc. of the server without loosing the whole thing.

---

