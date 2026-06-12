---
title: "How to install Ubuntu 17.04 (Zesty Zapus) Daily Build"
date: 2017-03-13
forum: Ubuntu Development Version
---

### Post by gayanv2 on 2017-03-13
Hello Friends !

I'm looking foward to try new Ubuntu 17.04 version.So i downloaded "[zesty-desktop-amd64.iso]("http://cdimage.ubuntu.com/daily-live/current/zesty-desktop-amd64.iso")" and installed it in vmware.But after i install it says version no is 16.10 ! So how to install Ubuntu 17.04 Beta or whatever ? :confused:

---

### Post by Irihapeti on 2017-03-13
*Thread moved to **Ubuntu Development Version**.*

Very likely, that file hasn't been updated yet. You have the most recent iso file.

---

### Post by dino99 on 2017-03-13
the version number has still not been updated yet :confused: Dont worry, you really have 17.04 installed.  :P
You will see 17.04 when Zesty will have been released next month.

---

### Post by gayanv2 on 2017-03-13
> **dino99 said:**
> the version number has still not been updated yet :confused: Dont worry, you really have 17.04 installed.  :P

hmm.actually my main intention is to try new UI :p i believe it really looks like this -> [http://i1-news.softpedia-static.com/images/news2/ubuntu-17-04-zesty-zapus-is-open-for-development-gcc-linaro-used-for-arm-port-509589-2.jpg](http://i1-news.softpedia-static.com/images/news2/ubuntu-17-04-zesty-zapus-is-open-for-development-gcc-linaro-used-for-arm-port-509589-2.jpg)

but i'm stuck with old UI :-k

---

### Post by cariboo on 2017-03-13
> **gayanv2 said:**
> hmm.actually my main intention is to try new UI :p i believe it really looks like this -> [http://i1-news.softpedia-static.com/images/news2/ubuntu-17-04-zesty-zapus-is-open-for-development-gcc-linaro-used-for-arm-port-509589-2.jpg](http://i1-news.softpedia-static.com/images/news2/ubuntu-17-04-zesty-zapus-is-open-for-development-gcc-linaro-used-for-arm-port-509589-2.jpg)

but i'm stuck with old UI :-k

That's what Unity 7 looks like with a different icon set, running on an arm, based system.

To check your release, open a terminal and type the following command.

```
cat /etc/lsb-release
```

The output should look like this:

```
cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=17.04
DISTRIB_CODENAME=zesty
DISTRIB_DESCRIPTION="Ubuntu Zesty Zapus (development branch)"
```

---

### Post by gayanv2 on 2017-03-13
> **cariboo said:**
> That's what Unity 7 looks like with a different icon set, running on an arm, based system.



any plans to add those icons set to new release ?

---

### Post by jbicha on 2017-03-13
This works too:
```
cat /etc/os-release
```

---

### Post by jbicha on 2017-03-13
> **gayanv2 said:**
> hmm.actually my main intention is to try new UI :p i believe it really looks like this -> [http://i1-news.softpedia-static.com/images/news2/ubuntu-17-04-zesty-zapus-is-open-for-development-gcc-linaro-used-for-arm-port-509589-2.jpg](http://i1-news.softpedia-static.com/images/news2/ubuntu-17-04-zesty-zapus-is-open-for-development-gcc-linaro-used-for-arm-port-509589-2.jpg)

but i'm stuck with old UI :-k

Ubuntu with Unity 17.04 looks about the same as 16.04 LTS. It does not look like that screenshot unless you install and apply a different icon theme and tweak some other settings.

---

### Post by lysander6662 on 2017-03-14
> **jbicha said:**
> Ubuntu with Unity 17.04 looks about the same as 16.04 LTS. It does not look like that screenshot unless you install and apply a different icon theme and tweak some other settings.

So Unity 8 is not installed by default [not that I will be using it]?

---

### Post by howefield on 2017-03-14
> **lysander6662 said:**
> So Unity 8 is not installed by default [not that I will be using it]?

Yes, it is installed by default however it will not be the default desktop environment. It can be chosen from the login screen.

---

### Post by lysander6662 on 2017-03-14
Ah, I see. Thanks for that. I will probably be going the way of Budgie anyway. If I were to, can I update from 17.04 [to 17.10] and then to 18.04 [is that how it works?]

---

### Post by howefield on 2017-03-14
> **lysander6662 said:**
> Ah, I see. Thanks for that. I will probably be going the way of Budgie anyway. If I were to, can I update from 17.04 [to 17.10] and then to 18.04 [is that how it works?]

Indeed, ensure that Software & Updates > Updates tab is set to notify you of any new release (which I think is the default) and you'll be offered each upgrade as it is ready.

---

### Post by lysander6662 on 2017-03-14
OK thank you. I imagine it best to back up important files before doing so just in case. It is better to do a fresh install or are upgrades thought of as running as smoothly as a fresh install?

---

### Post by howefield on 2017-03-14
> **lysander6662 said:**
> OK thank you. I imagine it best to back up important files before doing so just in case. It is better to do a fresh install or are upgrades thought of as running as smoothly as a fresh install?

The thread is drifting away from the OP, so will make this my past post in it.

Yes, of course, important data not sufficiently backed up is simply an accident waiting to happen.

My preference is always for a clean install, then there is no doubt that you have what the developers intended. Having said that I have never had an issue upgrading a default installation, heck these days even end of life releases upgrade perfectly in my humble experience. Having said that the further away you go from the default install the higher the risk of experiencing issues, eg injudiciously adding PPA repositories, proprietary drivers and so on.

At one time I would separate the /home folder to another partition/disk from the root folder to make reinstalling easier, however these days I keep /home within the same partition as / and symlink user folders to a separate disk/partition. A bundle of config files tar.gz'ed backed up makes my most used applications a doddle to set up too. 

The choice is yours, upgrading is generally painless imho, providing that you haven't fundamentally altered/corrupted the packaging system.

---

### Post by lysander6662 on 2017-03-14
I have three hard drives. I think when I do a fresh install I won't partition my main disk. Thanks for that. very good idea. I need to tidy up the other two drives anyway. 

Sorry to hijack the thread, I didn't mean to. I'll bow out now as well.

---

