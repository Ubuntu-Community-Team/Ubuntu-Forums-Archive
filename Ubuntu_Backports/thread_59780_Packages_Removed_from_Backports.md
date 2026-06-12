---
title: "Packages Removed from Backports"
date: 2005-08-25
forum: Ubuntu Backports
---

### Post by acascianelli on 2005-08-25
Has anyone else noticed the packages that have been removed from backports...

firefox
gaim
gimp
samba
xchat
java

There are a bunch more but those are some of the major ones.  Does anybody have any idea why they're gone and when they're coming back?

---

### Post by sbassett on 2005-08-25
acascianelli -

It appears that there is some problem with apt versus hoary-extras. None of them are being read for some reason. Have you noticed an Ign prefix in front of the hoary-extras entries when running apt-get update?

---

### Post by GoA on 2005-08-25
This is actually quite a problem if users cannot install their software. I wish there were more information about this problem. Because of this I cannot even install azureus.  :???:

---

### Post by tzutolin on 2005-08-25
[QUOTE=GoA]This is actually quite a problem if users cannot install their software. I wish there were more information about this problem. Because of this I cannot even install azureus.  :???:[/QUOTE]

I think we have to wait for the backports dev team come back to solve this problem. Be patient :-) !

---

### Post by acascianelli on 2005-08-25
[QUOTE=sbassett]acascianelli - 

It appears that there is some problem with apt versus hoary-extras. None of them are being read for some reason. Have you noticed an Ign prefix in front of the hoary-extras entries when running apt-get update?[/QUOTE]

Yes, I do see some Ign in my update log.  What does that mean?

```
acascianelli@ubuntu:~$ sudo apt-get update
Password:
Ign http://ubuntu-backports.mirrormax.net hoary-backports-staging Release.gpg
Ign http://ubuntu-backports.mirrormax.net hoary-backports Release.gpg
Ign http://ubuntu-backports.mirrormax.net hoary-extras Release.gpg
Ign http://ubuntu-backports.mirrormax.net hoary-backports-staging Release
Ign http://ubuntu-backports.mirrormax.net hoary-backports Release
Ign http://ubuntu-backports.mirrormax.net hoary-extras Release
Ign http://ubuntu-backports.mirrormax.net hoary-backports-staging/main Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports-staging/universe Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports-staging/multiverse Packages
...
Ign http://ubuntu-backports.mirrormax.net hoary-backports-staging/restricted Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports/main Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports/universe Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports/multiverse Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports/restricted Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/main Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/universe Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/multiverse Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/restricted Packages
...
Fetched 51.1kB in 2s (24.8kB/s)
Reading package lists... Done
acascianelli@ubuntu:~$
```

Edited to save space.

---

### Post by Velvet Elvis on 2005-08-25
You might have better luck getting answers by adressing the backports mailing list.


[http://lists.ubuntu.com/mailman/listinfo/ubuntu-backports](http://lists.ubuntu.com/mailman/listinfo/ubuntu-backports)

---

### Post by sbassett on 2005-08-25
The Ign prefix, to the best of my knowledge, signifies that apt is ignoring this request. Apparently, this has been going on for 5 days now.

[http://lists.ubuntu.com/archives/ubuntu-backports/2005-August/000069.html](http://lists.ubuntu.com/archives/ubuntu-backports/2005-August/000069.html) 

I guess the best we can do is wait. Though I still I would still like to build a local repo, as the packages can be d'led from extras.

---

### Post by acascianelli on 2005-08-25
[QUOTE=sbassett]The Ign prefix, to the best of my knowledge, signifies that apt is ignoring this request. Apparently, this has been going on for 5 days now.

[http://lists.ubuntu.com/archives/ubuntu-backports/2005-August/000069.html](http://lists.ubuntu.com/archives/ubuntu-backports/2005-August/000069.html) 

I guess the best we can do is wait. Though I still I would still like to build a local repo, as the packages can be d'led from extras.[/QUOTE]

That explains why if I hit the repo with a browser I can see the packages that apt is saying are installed localy or obsolete.

Wait I shall :(

---

### Post by Errorist on 2005-08-25
Lol... Was wondering if I was the only one having this problem.

It's my first day.
Now we play the waiting game.  :)

---

### Post by ShaneAu on 2005-08-26
I've always had the "Ign" message. I don't think it causes any problems.

---

### Post by rpgcyco on 2005-08-26
I think the ign thing has something to do with the packages not being authenticated.

- Rpg Cyco

---

### Post by acascianelli on 2005-08-26
I have some packages that are unupgradable at the moment.  'mozilla-firefox' says its now a transitional upgrade file that requires 'firefox'.  'firefox' is not available thru apt at the moment.  But I noticed that in my Breezy box, the Firefox package is not called 'mozilla-firefox' but its called 'firefox'.  Maybe there are having some compatability issues with package naming between Hoary and Breezy.

EDIT:

I added the official Ubuntu backports repo to my sources.list file...

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main universe multiverse restricted

...and it seems to have resolved alot of the packages in the local/obsolete category, but there are still some packages missing. Firefox, totem, samba, and a few others are still not available.

Here is my sources.list file...

```
## Default
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

deb http://us.archive.ubuntu.com/ubuntu hoary main universe multiverse restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main universe multiverse restricted

deb http://us.archive.ubuntu.com/ubuntu hoary-updates main universe multiverse restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main universe multiverse restricted

deb http://us.archive.ubuntu.com/ubuntu hoary-security main universe multiverse restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-security main universe multiverse restricted

deb http://security.ubuntu.com/ubuntu hoary-security main universe multiverse restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main universe multiverse restricted

## Backports
deb http://archive.ubuntu.com/ubuntu hoary-backports main universe multiverse restricted

deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-backports-staging main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras-staging main universe multiverse restricted

## Wine
# deb http://wine.sourceforge.net/apt/ binary/
# deb-src http://wine.sourceforge.net/apt/ source/
```

---

### Post by chiefofthejojos on 2005-08-26
see [http://ubuntuforums.org/showpost.php?p=318414&postcount=16](http://ubuntuforums.org/showpost.php?p=318414&postcount=16)

in the meantime you should be able to download the .deb files for those packages directly from the repository using your web browser.  java is here:
[http://ubuntu-backports.mirrormax.net/dists/hoary-extras/restricted/binary-i386/](http://ubuntu-backports.mirrormax.net/dists/hoary-extras/restricted/binary-i386/)
but I'm not sure where where those other packages are.
Then you you can install them using "dpkg -i"

---

### Post by acascianelli on 2005-08-28
Everything seems to be fixed now for me.  Anybody else want to confirm this also?

---

### Post by ShaneAu on 2005-08-28
Seems so. :).

The MirrorMAX ubuntu-backports server's bandwidth increased at 5 PM (1600) according to MRTG graphs.

And considering the java packages are 29M and  62M in size, they would cause a fluctuation in outgoing bandwidth when available for download via apt-get again.

Everyone should run this command now:
```

sudo apt-get update

```

---

### Post by chiefofthejojos on 2005-08-28
yes, it is working again.  My computer automatically upgraded the java sdk this morning. :D

---

### Post by tzutolin on 2005-08-29
[QUOTE=acascianelli]Everything seems to be fixed now for me.  Anybody else want to confirm this also?[/QUOTE]
Yeah!!
Everything is working fine now. Thanks to the developers of backports very much!!  :smile:

---

### Post by loon on 2005-08-29
I really dont want to sound like a downer....


but that took WAY to long to fix... esp if they have schools and workers using Ubuntu.  Doesn't help to fix a problem weeks after it happens.


Thanks for the fix though.

---

