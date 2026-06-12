---
title: "Unity won't install anymore (precise beta)"
date: 2012-03-12
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by robwilkens on 2012-03-12
I did a partial upgrade from update-manager and....

well. I wound up without a working desktop environment..

So- I install kubuntu-desktop.  Now I have something i'm not very happy with.  Is there a quick fix for this?

The problem is apparently unity is not installable...

Here's what i get on apt-get install unity:

The following packages have unmet dependencies:
 unity : Depends: compiz but it is not going to be installed
         Depends: compiz-core-abiversion-20120216 but it is not installable
         Depends: libnux-abiversion-20120212.01 but it is not installable
         Depends: compiz-plugins-main-default but it is not going to be installed

I'm going to assume this is a temporary fix, but if it's not can someone get back to me on how to fix this?  Yes, i understand this is beta software (precise).

-Rob

UPDATE: It was my fault for doing a partial upgrade, that's apparently a bad thing, sorry didn't know.

---

### Post by nasos on 2012-03-12
Yes, something broke.

I completely removed ubuntu desktop, compiz and unity and than manually downloaded compiz-plugins-main-default, libcompizconfig0  and unity, removed the compiz-core-abiversion-20120216 and libnux-abiversion-20120212.01 dependencies and installed the three packages.

Also take a look at: [https://bugs.launchpad.net/utouch-compiz/+bug/879782](https://bugs.launchpad.net/utouch-compiz/+bug/879782)

Then I installed compiz and ubuntu-desktop and it seems it works.

I would STRONGLY encourage you though to wait for a fix in the repos.


Best,
Nasos

---

### Post by nothingspecial on 2012-03-12
*Thread moved to **Ubuntu +1 (Precise Pangolin)**.*

---

### Post by grahammechanical on 2012-03-12
Hi

Synaptic Package Manager is not installed by default. You should install it. One update a few months ago remove Software Centre. One library was not ready for 12.04 and so it was held back and software centre was removed because it would be upset by the libraries already downloaded.

You need an alternate method of updating.

And with Synaptic you can install specific packages. You can also unmark packages for removal. I had to do this a few weeks ago to stop ubuntu-desktop being removed.

Try using synaptic to re-install Compiz and Ubuntu-desktop and Unity etc.

Do it one at a time and read what it says it is replacing and removing. If you do not like it find the package and uncheck it.

with Synaptic you can search for packages that need to be upgraded. They have a grey icon alongside the name. Then you can mark these for upgrade.

Regards.

---

### Post by robwilkens on 2012-03-12
> **grahammechanical said:**
> Hi

Synaptic Package Manager is not installed by default. You should install it. One update a few months ago remove Software Centre. One library was not ready for 12.04 and so it was held back and software centre was removed because it would be upset by the libraries already downloaded.



I used to use synaptic on debian i believe, but i am a perpetual newbie in that historically i use linux for short bursts at a time.  I was very happy with the precise gnome desktop environment though, even install virtualbox for those few windows apps i might need.

Anyway, enough history : Synaptic said to fix broken packages first.  But when i fix broken packages, it tells me packages are being 'held' and can't be fixed.. So I guess i just have to wait which i will.

-Rob

---

### Post by grahammechanical on 2012-03-12
They usually come through a day or two later. I had to wait 3 days before I could re-install Software Centre. Not that I had a great need for it. Daily updates is the way to go.

Regards.

---

### Post by jymbob on 2012-03-12
> **grahammechanical said:**
> Hi

...

Try using synaptic to re-install Compiz and Ubuntu-desktop and Unity etc.

Do it one at a time and read what it says it is replacing and removing. If you do not like it find the package and uncheck it.


I actually came at this from a Synaptic route, however the issue here is that there is not only an unmet dependency, but an unmeetable one. Namely the update of compiz-core from 1:0.9.7.0~bzr2995-0ubuntu5 to 1:0.9.7.0+bzr3035-0ubuntu1 which in turn provides the compiz-core-abiversion virtual package. This update has changed the package number so that unity, compiz-plugins-main-default and libcompizconfig0 cannot satisfy their dependencies. This causes all manner of problems, as the only way to meet all dependencies of an upgrade are to remove compiz, unity, and everything that depends on them, which is rather a lot.

Removing the dependencies mentioned above from those three packages has led me to a workable system again.

EDIT: Actually, upon further investigation, while forcing the packages through leads to a system whereby all dependencies can be met for the purposes of upgrading a system, compiz will fail to initialise as it's expecting a different version of the core library. I'll be 2D until this is fixed.

---

### Post by robwilkens on 2012-03-12
> **grahammechanical said:**
> They usually come through a day or two later. I had to wait 3 days before I could re-install Software Centre. Not that I had a great need for it. Daily updates is the way to go.

Regards.

Thank you for the info, i can wait a few days if i have to...

FYI - some of the packages i reported as missing in my original message are no longer listed as missing but now others are missing..  I wrote myself a note in a todo file on my desktop so i don't forget to fix this even if, as you say, it takes 3 days or more..

-Rob

---

### Post by ernestj on 2012-03-12
I did a dist-upgrade and lost Unity also. I have Cinnamon as a alternative desktop when this happens (second time). I do not like Cinnamon. I want my Unity back! Most likely it will be back by the end of the day or in the morning. But, its gonna be a great day:mad:
Ernie

---

### Post by robwilkens on 2012-03-12
For anyone following - It's now fixed (the packages needed are there):

apt-get install ubuntu-desktop unity

and a reboot

Seem to fix it.

-Rob

---

### Post by ernestj on 2012-03-12
didn't work for me! said I was missing something.
anyways, updates included Unity 2d, but nothing for 3d. It won't even show up on log in. i am getting sick of Cinnamon quick. I hope this gets fixed soon.

ernie

---

### Post by rtalcott on 2012-03-12
2 machines....100% success....Thank You!

---

### Post by anti_microsoft on 2012-03-12
> **ernestj said:**
> didn't work for me! said I was missing something.
anyways, updates included Unity 2d, but nothing for 3d. It won't even show up on log in. i am getting sick of Cinnamon quick. I hope this gets fixed soon.

ernie

I had the same problem, didn't work.

What I had to do was CTRL+ALT+F2. Sudo su and cd /etc/apt. The problem was I upgraded my sources to a mirror closer to me. So it was not using official Ubuntu mirrors.

There should be a sources.list.save file there with the original sources setup you started with. 

```
mv sources.list sources.list.2
mv sources.list.save sources.list
```

Then do apt-get clean, apt-get update, apt-get install ubuntu-desktop unity and it should work.

Hope this helps.

---

### Post by ernestj on 2012-03-12
should this work itself out with updates in the next day or so?

I am not sure what to do, that you mentioned. 

ernie

---

### Post by jymbob on 2012-03-13
> **ernestj said:**
> should this work itself out with updates in the next day or so?

I am not sure what to do, that you mentioned. 

ernie

Ernie: What worked for me here was the following two commands from a terminal:
```
sudo apt-get update
sudo apt-get upgrade
```
The first one checks your package list is up-to-date; the second finds anything that can be upgraded and does it. It will list what's about to be upgraded so just check unity is in the list.

---

