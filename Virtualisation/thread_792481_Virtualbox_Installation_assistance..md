---
title: "Virtualbox Installation assistance."
date: 2008-05-13
forum: Virtualisation
---

### Post by ThatGuyThere on 2008-05-13
Hi, thanks in advance for your help...

I downloaded the Sun xVM VirtualBox 1.6
virtualbox_1.6.0-30421_Ubuntu_hardy_i386.deb file from the virtualbox website, and after the dl finished, i started the install. I get the error message displayed in the attached jpg. Anybody know what's wrong?

---

### Post by jcbray on 2008-05-13
Did you install Virtual Box OSE from the repo? Remove that if you have and retry the installation.

---

### Post by ThatGuyThere on 2008-05-13
> **jcbray said:**
> Did you install Virtual Box OSE from the repo? Remove that if you have and retry the installation.

I have already removed it. This is what i get when I run sudo apt-get remove virtualbox-ose:
```
max@mxg-linbook:~$ sudo apt-get remove virtualbox-ose
[sudo] password for max:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package virtualbox-ose is not installed, so not removed

```

---

### Post by ironwolfe on 2008-05-13
Weird...

you may need to remove the dependencies one by one.

You could try (after backing up your virtual machines directory - VDI's

```
sudo apt-get purge virtualbox-ose
```

did you do a fresh hardy install or an upgrade?

You could also just remove the .ko file - you shouldn't need it as the 1.6 will install it's own.

---

### Post by ThatGuyThere on 2008-05-13
> **ironwolfe said:**
> Weird...

you may need to remove the dependencies one by one.

You could try (after backing up your virtual machines directory - VDI's

```
sudo apt-get purge virtualbox-ose
```

did you do a fresh hardy install or an upgrade?

You could also just remove the .ko file - you shouldn't need it as the 1.6 will install it's own.

I did a fresh hardy install. Purge gives me the same output as the sudo apt-get remove virtualbox-ose.


EDIT: Where can i find the .ko file?

EDIT2: Sorry about being vague in the last edit; I looked in the /lib/modules/2.6.24-16-generic/misc , but there isn't a vboxdrv.ko file in that directory.

EDIT3: Seems to be working now. I crawled around in syntapic to see if i had missed anything, and i had a modules or something other there. Thanks for taking the time anyways :)

---

