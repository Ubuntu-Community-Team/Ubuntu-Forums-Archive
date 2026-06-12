---
title: "How can I upgrade from 12.04 lts to raring?"
date: 2012-12-23
forum: Ubuntu Development Version
---

### Post by sonnet on 2012-12-23
as per title I have installed 12.04 lts (only a cli system).
I'd like to know if there's a command or a method that would allow me to upgrade to Raring (raring daily cd do not seem to work on my pc)

---

### Post by wojox on 2012-12-23
Not directly, but if you upgrade to 12.10 you can easily upgrade to 13.04.

---

### Post by ibjsb4 on 2012-12-23
[http://ubuntuforums.org/showthread.php?p=12416435#post12416435](http://ubuntuforums.org/showthread.php?p=12416435#post12416435)

---

### Post by blackbird34 on 2012-12-23
You will have to upgrade to Quantal first.

```
 sudo apt-get install update-manager-core && sudo do-release-upgrade
```[Source ]("https://help.ubuntu.com/community/Upgrades#Network_upgrades")

Raring Ringtail is a develpment release, so the command is slightly different. You need to already be running Quantal.

```
 sudo apt-get install update-manager-core && sudo do-release-upgrade -d
```[SOurce]("https://help.ubuntu.com/community/Upgrades#Upgrading_to_development_releases"), same page as before.[ ]("https://help.ubuntu.com/community/Upgrades#Upgrading_to_development_releases")

---

### Post by sonnet on 2012-12-23
Sorry to be a pain in the chest,but i tried the command with a fresh installation(just to be safe) of Quantal (only the second part) and I got the bug illustrated here:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1077676](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1077676)

Any idea?

---

### Post by kansasnoob on 2012-12-23
> **sonnet said:**
> Sorry to be a pain in the chest,but i tried the command with a fresh installation(just to be safe) of Quantal (only the second part) and I got the bug illustrated here:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1077676](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1077676)

Any idea?

Since you're open to fresh installs why not grab a fresh image here:

[http://iso.qa.ubuntu.com/qatracker/milestones/243/builds](http://iso.qa.ubuntu.com/qatracker/milestones/243/builds)

No doubt it's always a crap shoot because they're testing iso's but what the hay :lolflag:

---

### Post by sonnet on 2012-12-23
> **kansasnoob said:**
> Since you're open to fresh installs why not grab a fresh image here:

[http://iso.qa.ubuntu.com/qatracker/milestones/243/builds](http://iso.qa.ubuntu.com/qatracker/milestones/243/builds)

No doubt it's always a crap shoot because they're testing iso's but what the hay :lolflag:

That was the initial plan, unfortunately I'm experiencing a nasty bug :
[http://ubuntuforums.org/showthread.php?t=2097429](http://ubuntuforums.org/showthread.php?t=2097429)

So I thought as alternative to install quantal and upgrade from there.
But again I 'm experiencing another bug again in upgrading.
It's all so depressing.

---

### Post by kansasnoob on 2012-12-23
> **sonnet said:**
> That was the initial plan, unfortunately I'm experiencing a nasty bug :
[http://ubuntuforums.org/showthread.php?t=2097429](http://ubuntuforums.org/showthread.php?t=2097429)

So I thought as alternative to install quantal and upgrade from there.
But again I 'm experiencing another bug again in upgrading.
It's all so depressing.

Yeah, I hear ya' ;)

I'm trying to figure out the depends and recommends for the gnome remix:

[http://ubuntuforums.org/showpost.php?p=12418948&postcount=13](http://ubuntuforums.org/showpost.php?p=12418948&postcount=13)

Everything is rough right now. But that mini.iso does work if you're familiar with it.

---

### Post by grahammechanical on 2012-12-24
There is a standard method that we used when the new development cycle started. We took an updated Quantal and changed the software sources/repositories to Raring.

This is how I got my Raring install in the first place back in November. and being unable to get a Raring ISO image to work I converted a second Quantal just the other day. A lot of updates need to be done but it will still work.

```
sudo sed -i 's/quantal/raring/g' /etc/apt/sources.list
```

That changes the repositories. Follow it with the usual 

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

I am planning later today to install Gnome Remix. That will be Quantal and then use this method to convert it to Raring. If it does not work in this case I can easily re-install the 12.10 Remix.

Regards.

---

### Post by sonnet on 2012-12-24
Followed that and it worked: though I needed dist-upgrade to pull in the kernel upgrade

---

### Post by jinjorge on 2012-12-27
> **grahammechanical said:**
> There is a standard method that we used when the new development cycle started. We took an updated Quantal and changed the software sources/repositories to Raring.

This is how I got my Raring install in the first place back in November. and being unable to get a Raring ISO image to work I converted a second Quantal just the other day. A lot of updates need to be done but it will still work.

```
sudo sed -i 's/quantal/raring/g' /etc/apt/sources.list
```

That changes the repositories. Follow it with the usual 

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

I am planning later today to install Gnome Remix. That will be Quantal and then use this method to convert it to Raring. If it does not work in this case I can easily re-install the 12.10 Remix.

Regards.

This is pretty awesome!!! Used it to go from quantal to raring. 

Thanks for sharing.

J

---

### Post by Curtis6767 on 2013-01-06
> **grahammechanical said:**
> There is a standard method that we used when the new development cycle started. We took an updated Quantal and changed the software sources/repositories to Raring.

This is how I got my Raring install in the first place back in November. and being unable to get a Raring ISO image to work I converted a second Quantal just the other day. A lot of updates need to be done but it will still work.

```
sudo sed -i 's/quantal/raring/g' /etc/apt/sources.list
```That changes the repositories. Follow it with the usual 

```
sudo apt-get update
``````
sudo apt-get upgrade
```I am planning later today to install Gnome Remix. That will be Quantal and then use this method to convert it to Raring. If it does not work in this case I can easily re-install the 12.10 Remix.

Regards.

Downloaded a fresh copy of 12.10 and installed it in VB. Then, using the above sources list line, I changed sources list to raring.

Ran into problems with broken dependencies after running all regular updates, including dist-upgrade.

ran the following two lines:

                               ```
   sudo dpkg --configure -a        
```                           ```
  sudo apt-get -f install  
```These fixed dependency problems and allowed for the installation of the 3.7 kernel and the remaining upgrades.

I already had Raring running in VB but wanted to give this upgrade method a try and was frustrated until I stumbled upon the 'dpkg' line above.

Thanks, Graham, for providing the sources list info.

---

### Post by engenilk on 2013-04-23
Graphical way (bypass the bug):

```
do-release-upgrade -d -f DistUpgradeViewGtk3
```

---

