---
title: "Support confusion with LTS"
date: 2014-05-02
forum: Ubuntu, Linux and OS Chat
---

### Post by sagsaw-sawant on 2014-05-02
whats this about support ... someone told me if i installed  lubuntu-desktop on ubuntu14.04 LTS ... lubuntu-desktop package will get 5  years support.

see lubuntu is 3 year support for LTS so how will a lubuntu package be supported for 5 years thats the question?

also if i install minimal ubuntu using the 14.04 LTS mini iso,  and then i install lubuntu-core ... will the distro become lubuntu or  will it be ubuntu? so will there 5 years support or 3 years support?
very important 



this is a fundamental but very important confusion.

---

### Post by sagsaw-sawant on 2014-05-02
whats this about support ... someone told me if i installed  lubuntu-desktop on ubuntu14.04 LTS ... lubuntu-desktop package will get 5  years support.

see lubuntu is 3 year support for LTS so how will a lubuntu package be supported for 5 years thats the question?

also if i install minimal ubuntu using the 14.04 LTS mini iso,  and then i install lubuntu-core ... will the distro become lubuntu or  will it be ubuntu? so will there 5 years support or 3 years support?
very important 



this is a fundamental but very important confusion.

---

### Post by deadflowr on 2014-05-02
Thread Moved to Ubuntu, Linux, and OS Chat

not support about support.:)

---

### Post by sudodus on 2014-05-02
The common program packages of Ubuntu and Lubuntu (many packages under the hood) are supported for 5 years. But the Lubuntu specific packages are only supported for 3 years.

Lubuntu Core is a smaller version (with fewer program packages) compared to standard Lubuntu. If you start from the mini.iso and install Lubuntu Desktop you'll get standard Lubuntu.

```
sudo apt-get install lubuntu-desktop
```

Lubuntu and Lubuntu Core have LTS for 3 years. See this link

[https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)

---

### Post by coffeecat on 2014-05-02
Threads merged. Please do not post duplicates.

---

### Post by sagsaw-sawant on 2014-05-02
ok but if i start from mini iso and install lubuntu-core ... still will i get Lubuntu or Ubuntu with lubuntu-core package and thus 5 years support?

---

### Post by Warren Hill on 2014-05-02
Support is on a package by package basis.

Most of the packages are common to Lubuntu and Ubuntu (and for that matter Xubuntu and Kubuntu as well) and will be supported for 5 years.  The ones that are specific to Lubuntu will stop being maintained after 3 years and if you want full support you will need to upgrade.

Lubuntu and Ubuntu are both free so you will be able to upgrade to 16.04LTS once it's released.

---

### Post by verymadpip on 2014-05-02
Hi there.
It's a bit of a minefield isn't it?
have a look at this, see if it helps at all
[http://ubuntuforums.org/showthread.php?t=2175646](http://ubuntuforums.org/showthread.php?t=2175646)

---

### Post by grahammechanical on 2014-05-02
I would not describe this matter as a minefield. Here are the facts.

Until the release of Ubuntu 12.04 LTS support was 5 years for a server edition LTS and 3 years for a desktop edition LTS. But things changed with 12.04. Both server edition and desktop editions of Ubuntu LTS releases get 5 years support.

Because Ubuntu is open source other developers are able to take Ubuntu and modify it to change the desktop environment. We call these modified versions of Ubuntu "flavours." Those developers have limited resources. They still follow the same 6 monthly release pattern as the Ubuntu developers but they cannot give the same length of support. It would be wrong to claim that they can give a certain length of support when they know they cannot.

So, the choice is this, spend a lot of effort maintaining support for a release and fall behind with releasing the next version of their flavour, or keep up to date with releases but limit the support period.

According to the old definition, 3 years support is Long Term Support. Just think of this matter as Ubuntu developers being a bit more generous with their time and skills then they were previously. And be thankful that we have such a thing as Free and Open Source Software.

An alternative comes to mind. Ubuntu developers could revert to the old ways of only having 3 years support for desktop LTS releases. Then no one should complain. But then secretly provide 5 year support for the desktop to commercial enterprises (companies) registered as using Ubuntu.  Of course, there will have to be a fee for this service. 

Happy with that? We get something very good for nothing and still people complain. I remember a post back in 2012. Someone had heard that Ubuntu 12.04 was going to get 5 year support and they were complaining that Ubuntu 10.04 was only getting 3 year support. Why couldn't 10.04 be given 5 years support. They demanded. Releases reach end of life. It is a fact. Life moves on. 

Regards.

---

### Post by sagsaw-sawant on 2014-05-02
[ 						 							[IMG]http://ubuntuforums.org/customavatars/avatar1087323_2.gif[/IMG] 						 					]("http://ubuntuforums.org/member.php?u=1087323") 				 				 					 						 	[**[COLOR=#000000]grahammechanical[/COLOR]**]("http://ubuntuforums.org/member.php?u=1087323") ... I am not complaining about the 3 year or 5 year thing ... i am just trying to get the confusion I have corrected ... One thing I came to know is that support is per package basis ... which means if its an ubuntu package it will be supported for 5 years and if its lubuntu it will be supported for 3 years ... which means that if I want lxde and 5 year support then I will have to use lxde package ...

almost clear the confusion ...

---

### Post by lykwydchykyn on 2014-05-02
> **sagsaw-sawant said:**
>  which means that if I want lxde and 5 year support then I will have to use lxde package ...

almost clear the confusion ...

No.

There is no way for you to have 5 years of support with Ubuntu + LXDE.  No matter how you go about installing it, the result is the same.

All flavors (ubuntu, lubuntu,  kubuntu, xubuntu, server, edubuntu) pull packages from the same set of repositories.  Each flavor maintains a certain set of packages in the repositories.  If flavor A is a 5-year LTS, its maintainers are going to keep up with supporting their packages for 5 years.  If flavor B is a 3-year LTS, its maintainers are going to be supporting those packages for 3 years.

If flavor A and B both use a package, it's going to be maintained for 5 years, because the flavor A developers will still be supporting it.
If only flavor B uses the package, and flavor A doesn't, it's only getting 3 years of support.

LXDE (unless I'm wrong) is packaged and maintained in the repos by the Lubuntu project developers.  When they stop maintaining it, it's unsupported.

The kernel, on the other hand, is going to be maintained for 5 years no matter what flavor you're using, because all flavors are using the kernel.

Then of course there are packages maintained by the community (the Universe repos).  I don't know if LTS guarantees any amount of support for those packages. It's probably just up to the individual maintainer.

---

### Post by sudodus on 2014-05-02
But ***lxde*** is not part of Ubuntu, so do not expect more than 3 years support. At least not from Canonical or the Ubuntu community (including Lubuntu).

The important thing here is that 3 years a good enough. It means one year overlap between the long time support versions.

***LXLE***, a re-spin based on Ubuntu 12.04 LTS, is promising 5 years support for a system using lxde. LXLE is developed and maintained by a separate organisation.

---

