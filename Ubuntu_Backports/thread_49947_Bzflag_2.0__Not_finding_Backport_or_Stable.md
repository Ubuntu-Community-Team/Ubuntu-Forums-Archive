---
title: "Bzflag 2.0  Not finding Backport or Stable"
date: 2005-07-18
forum: Ubuntu Backports
---

### Post by ep_ on 2005-07-18
I've been on a quest to install Bzflag version 2.0, so far I've only found it here:  [warty-backport](http://mirror.brianpuccio.net/ubuntu-backports-repository/dists/warty-backports/universe/binary-i386/) 
 
I have Hoary and bzflag 2.0 is not listed in the equivalent Hoary-universe section.  Also, I've been researching here on the forums and I've found a couple of postings stating that Bzflag 2.0 has been released to the stable tree.
 
[http://ubuntuforums.org/showthread.php?t=11847](http://ubuntuforums.org/showthread.php?t=11847) 

However, as far as I can determine the only thing thats in universe is Bzflag version 1.10, not version 2.0.  So my quesion is, how in the world do I install Bzflag version 2.0?

Addendum:  I'm fairly new but I also tried to  Install the debian bzflag 2.0 package.   It needs libcurl3 version greater than all versions that are available for Ubuntu.  I tried to install that but it was over my head, ran into dependency hell.  Looking for another solution,  I  had a  bzflag developer help me compile from scratch -- no luck needed a newer libcurl3-dev package (more dependency hell).  She recommended I switch to Debian -- but i REALLY like ubuntu.

TIA -- ep

---

### Post by redlabour on 2005-07-19
[QUOTE=ep_]I've been on a quest to install Bzflag version 2.0, so far I've only found it here:  [warty-backport](http://mirror.brianpuccio.net/ubuntu-backports-repository/dists/warty-backports/universe/binary-i386/) 
 
I have Hoary and bzflag 2.0 is not listed in the equivalent Hoary-universe section.  Also, I've been researching here on the forums and I've found a couple of postings stating that Bzflag 2.0 has been released to the stable tree.
 
[http://ubuntuforums.org/showthread.php?t=11847](http://ubuntuforums.org/showthread.php?t=11847) 

However, as far as I can determine the only thing thats in universe is Bzflag version 1.10, not version 2.0.  So my quesion is, how in the world do I install Bzflag version 2.0?

Addendum:  I'm fairly new but I also tried to  Install the debian bzflag 2.0 package.   It needs libcurl3 version greater than all versions that are available for Ubuntu.  I tried to install that but it was over my head, ran into dependency hell.  Looking for another solution,  I  had a  bzflag developer help me compile from scratch -- no luck needed a newer libcurl3-dev package (more dependency hell).  She recommended I switch to Debian -- but i REALLY like ubuntu.

TIA -- ep[/QUOTE]
 It is in the Backports.

---

### Post by ep_ on 2005-07-19
Your reply, "It's in the backports", wasn' helpfull. Which backport? Where?  As I explained, I've already seached.   For instance, I added the following two lines to /etc/apt/sources.list:

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

Then sudo apt-get update.  Then apt-cache search bzflag.   apt-cache show bzblag 
Uninstall 1.10 then apt-get install bzfag.

Not there.

---

### Post by redlabour on 2005-07-19
[QUOTE=ep_]Your reply, "It's in the backports", wasn' helpfull. Which backport? Where?  As I explained, I've already seached.   For instance, I added the following two lines to /etc/apt/sources.list:

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

Then sudo apt-get update.  Then apt-cache search bzflag.   apt-cache show bzblag 
Uninstall 1.10 then apt-get install bzfag.

Not there.[/QUOTE]
 Oh Shit .... sorry i don´t know that there is 1.10 and not 2.0 in it. I mean 1.10. :(

But i make a Request : [http://www.ubuntuforums.org/showthread.php?t=50208](http://www.ubuntuforums.org/showthread.php?t=50208)

---

