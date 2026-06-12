---
title: "Updating 16.04"
date: 2016-03-06
forum: Ubuntu Development Version
---

### Post by PsychedelicWonders on 2016-03-06
So I've been running 16.04 for a couple of weeks now and everything seems to be running just fine - but I haven't done any new updates/installs of it.

Is just doing updates sufficient, or should complete new installs be done every so often until LTS is out?

Also, the software updater had a bunch of stuff to install today, but it gave me an error upon download saying the internet connection isn't working right - but that can't be considering I've been on the internet this entire time and still am?  Any idea why or how to get around this so I can install the updates?

---

### Post by goofprog on 2016-03-06
The internet is a big monster for problem solving.  What I used to do is: 1) Used a LAN line and troubleshot my issues from there.

---

### Post by MikeMecanic on 2016-03-06
Was it a message like this one?
''Failed to download repository information''
Check your Internet connection.
Try Again
Not sure about the meaning of your second phrase?  Did you upgrade to 16.04 or you made fresh install?

---

### Post by v3.xx on 2016-03-06
Do an update in terminal and post any errors.

```
sudo apt update
```

If no errors, do a upgrade

```
sudo apt dist-upgrade
```

---

### Post by grahammechanical on 2016-03-06
Have we forgotten that there are repositories listed in the sources list file that are not active in a development version and do not become active until the new version is released?

For example, 

> deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse

Back ports are not needed until the version is released. So, we will get errors sometimes.

Sometimes, in fact often, we will see a dialog that offers us a partial upgrade. There are four reasons for this dialog appearing

1) A previous upgrade which did not complete
2) Problems with some installed software
3) Unofficial software repositories not provided by Ubuntu
4) Normal changes of a pre-release version of Ubuntu.

I just click Continue and the update/upgrade takes place as normal. It does not matter if we have installed the development version from the very first daily built ISO image or from the final release candidate ISO image. By Updating/upgrading the installed development OS will progress to become the released OS.

We can use Software Updater. Or we can run apt-get update & apt-get upgrade. It is up to us. But we should be aware that apt-get dist-upgrade will bring in packages that are being held back. And they are being held back for a reason. I have twice used dist-upgrade to bring in a new kernel that I was too impatient to wait for. And nothing was broken. But as with a partial upgrade there is always an element of risk when using dist-upgrade.

Of course, if we want to test the daily built ISO images then we would indeed download an new ISO image at intervals agreeable to ourselves and install it.

Here is the recommended action when getting an offer to do a partial upgrade

[http://ubuntuforums.org/showthread.php?t=2300151](http://ubuntuforums.org/showthread.php?t=2300151)

Regards.

---

### Post by vasa1 on 2016-03-06
> **grahammechanical said:**
> Have we forgotten that there are repositories listed in the sources list file that are not active in a development version and do not become active until the new version is released?
...

Here is the recommended action when getting an offer to do a partial upgrade

[http://ubuntuforums.org/showthread.php?t=2300151](http://ubuntuforums.org/showthread.php?t=2300151)
...
Bookmarking this answer!

Re. not all repos being active until release, does that apply to the RC as well?

---

### Post by Smask on 2016-03-06
> **grahammechanical said:**
> 1) A previous upgrade which did not complete
2) Problems with some installed software
3) Unofficial software repositories not provided by Ubuntu
4) Normal changes of a pre-release version of Ubuntu.
 
I've found that most times I get the Partial upgrades dialog, it boils down to:

5) The country specific mirror your installation selected didn't sync properly against the main server.

And as Graham wrote, just do a simple upgrade, never do a partial one. By making an partial upgrade. you risk ruining your system and the main reason why the update-manager is nicknamed update-mangler. Just upgrade those parts that update-manager have found OK to upgrade and then wait for the repos/mirrors to sort themselves out.

---

### Post by v3.xx on 2016-03-06
> **vasa1 said:**
> Bookmarking this answer!

Yes, me too.  But OP has not been offered a partial upgrade.  Maybe a terminal update will offer one or give other errors.  And update-manager also gives you a dist-upgrade when used, [this makes sense to me.]("https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands")

---

