---
title: "Problem installing new kernel"
date: 2013-03-09
forum: Ubuntu Development Version
---

### Post by chenriques on 2013-03-09
Hi

I'm getting this:

```
sudo apt-get install linux-source linux-headers-generic

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 linux-headers-generic : Depends: linux-headers-3.8.0-12-generic but it is not installable
E: Unable to correct problems, you have held broken packages.

```

Any ideas?
I had some packages that were not upgrade, essentially linux-image\linux-headers and libreoffice.
I've removed all the packages, but I can't install any of them:

```
sudo apt-get install libreoffice-base-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 libreoffice-base-core : Depends: libreoffice-core (= 1:4.0.1-0ubuntu1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

What can I do to fix this?

Thanks

---

### Post by dino99 on 2013-03-09
3.8.0.12 is not out yet, so be patient. Same for LO

---

### Post by serdotlinecho on 2013-03-09
LO [4.0.1]("https://lists.ubuntu.com/archives/raring-changes/2013-March/007352.html") is available in raring proposed :)

---

### Post by dino99 on 2013-03-09
only sources are published; still waiting the debs.

[https://launchpad.net/ubuntu/+source/libreoffice/1:4.0.1-0ubuntu1](https://launchpad.net/ubuntu/+source/libreoffice/1:4.0.1-0ubuntu1)

---

### Post by chenriques on 2013-03-09
If they are not out yet, why are they already available to install (although they fail)?

[IMG]http://i.imgur.com/4MDRy5S.png[/IMG]

---

### Post by jppr on 2013-03-09
Install Synaptic... sudo apt-get install synaptic, and learn how to use it so all the updates are much easier to make

---

### Post by chenriques on 2013-03-09
I already have synaptic.
today I started my laptop and run software update. It said that it couldnt install everything and asked if I wanted a partial upgrade. I said yes.
then I get this errors..
if I ran "apt-get dist-upgrade" it listed libre office and the new kernel, but it couldn't install them, giving the unmet depencies errors.
my question is, if they are nit yet ready for upgrade, why does apr lists them?

---

### Post by ptn107 on 2013-03-09
Not all the dependencies are uploaded yet that's why you get errors.  The raring archive is live so sometimes you get partial upgrades and sometimes you get updates that don't install until their dependencies are available.

---

### Post by chenriques on 2013-03-09
Thanks ptn107.
I'll wait then, without Libre Office until then :(

---

### Post by zika on 2013-03-09
Turn off proposed in Raring and You will be OK, if You did not start dist-upgrade at some time in the near past...

---

### Post by JonPaul on 2013-03-09
Install Libreoffice4.01 from their website - instructions are in the readme downloaded with the tar files. It is not difficult.....

[http://www.libreoffice.org/download/?type=deb-x86&lang=en-GB&version=4.0.1](http://www.libreoffice.org/download/?type=deb-x86&lang=en-GB&version=4.0.1)

this is for the english version of 32bit 

I did have to remove 3.6 completely first (using synaptics as software center didn't get rid of everything) or else it will not compile. 

It's good \\:D/

---

### Post by Budovi on 2013-03-09
Kernel updates works like this: (I think this is new way, it did not work like this in precise at least, I did not use quantal so I do not know. Also I do not know if this is "final way", use your brain as always (: )

* Packages "linux-image-generic" and "linux-headers-generic" are just sort of dummy packages that depends on actual kernel and header packages of certain (newest, same as actual package) version.

* Package "linux-generic" depends on corresponding versions of "linux-image-generic" and "linux-headers-generic", that means you can only upgrade this package, if you have both kernel and headers in newest version installed.

* apt-get upgrade is updating packages only, there is new version of these 3 packages, but they have unmet dependencies because you do not have new kernel and it WON'T be installed for you.

* apt-get dist-upgrade ("partial upgrade" in software updater) is able to install and remove packages too, so you HAVE TO PAY ATTENTION what it wants to do. But this is only possible automated way, how to update kernel. Because it allows installing new kernel and met dependencies of "linux-generic", "linux-headers-generic" and "linux-image-generic" so they are then upgradable. There is also safer possibility that you search and install new kernel and headers from repositories manually.

* If there are old versions of kernel installed (sort of 4 versions old), they are now proposed to be "autoremoved" as they are no longer needed.


Edit: and also for libreoffice there was update where one particular package (some sort of libreoffice impress remote control? I do not remember) was in conflict, so maybe try running "dist-upgrade", analyze situation yourself (Do not allow removing packages that are obviously needed or you do not know what they do! You can uninstall literally half of your system!) and consider fixing some dependencies (: at your risk of course :D

---

### Post by chenriques on 2013-03-10
I disabled the proposed packages and now everything works great ;)

Thanks.

---

