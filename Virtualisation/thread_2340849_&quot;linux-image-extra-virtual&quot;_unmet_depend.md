---
title: "&quot;linux-image-extra-virtual&quot; unmet dependency while installing docker"
date: 2016-10-22
forum: Virtualisation
---

### Post by ubudabi on 2016-10-22
Hi all,
I want to install docker on Ubuntu 16.04 and I am following the instructions from here:
[https://docs.docker.com/engine/installation/linux/ubuntulinux/]("https://docs.docker.com/engine/installation/linux/ubuntulinux/")
everything goes well until I get to the step > Prerequisites by Ubuntu Version where I have to install the package **linux-image-extra-virtual** with:
```
 $ sudo apt-get install linux-image-extra-$(uname -r) linux-image-extra-virtual
```
then it complains about **linux-image-extra-virtual** and unmet dependencies, namely:
```
ubudabi@pc ~ $ sudo apt-get install linux-image-extra-virtual
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 linux-image-extra-virtual : Depends: linux-image-generic (= 4.4.0.45.48) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```
So what does that mean? I have to update my kernel, or can I somehow fix it or can leave it like this? Is this package necessary to run docker?
My kernel is **4.4.0-21-generic** and I actually I don't want to upgrade for stability reasons.

Any ideas?

---

### Post by Habitual on 2016-10-22
Does
```
sudo apt-mark showhold
```
provide any clue?

---

### Post by ubudabi on 2016-10-22
[COLOR=#000000]Habitual thanks for the quick response!
[/COLOR]```
[COLOR=#000000]$ sudo apt-mark showhold[/COLOR]
```
returns nothing...

Another idea?

---------------------------------------------------------------------
[EDIT]
It seems to be OK after I have used **aptitude** instead of apt-get:

```
$ sudo **aptitude** install linux-image-extra-virtual
```

---

