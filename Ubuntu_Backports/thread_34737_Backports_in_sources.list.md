---
title: "Backports in sources.list"
date: 2005-05-16
forum: Ubuntu Backports
---

### Post by daenney on 2005-05-16
Hey
I'm new to the whole bacport idea but I find it really amazing what you people do...
I added the backports from ubuntuguide.org to my apt sources but it can't find anything, basically, u get an error.
I surfed around a bit and I assume it's because the backport takes up so much bandwith that the mirrors are down or have the mirror address been updated?

---

### Post by lao_V on 2005-05-16
what sort of error are you getting and what's in your sources.list?

---

### Post by Dax0r on 2005-05-16
I get this error:

> Err [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/main Packages
  500 Internal Server Error
Err [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/universe Packages
  500 Internal Server Error
Err [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/multiverse Packages
  500 Internal Server Error
Err [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/restricted Packages
  500 Internal Server Error
Err [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/main Packages
  500 Internal Server Error
Err [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/universe Packages
  500 Internal Server Error
Err [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/multiverse Packages
  500 Internal Server Error
Err [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/restricted Packages
  500 Internal Server Error

---

### Post by jdong on 2005-05-16
Sorry, repository is down. I have a backup access location at : "http://backports.ubuntuforums.org/ubp/"


It may be a bit less up-to-date, but at least it works!

---

### Post by XDevHald on 2005-05-16
[QUOTE=Dax0r]I get this error:[/QUOTE]
 [http://www.ubuntuforums.org/showthread.php?p=174215#post174215]("http://www.ubuntuforums.org/showthread.php?p=174215#post174215")

The link above will give you some info on this, and yes the backports are down at the moment, they were up yesterday.

---

### Post by artAlexion on 2005-05-16
I did not get any errors regarding the servers, but ```
apt-get upgrade
``` didn't. (e.g. firefox did not upgrade)  

Is there a special order for the respositories in my sources.list?

---

### Post by XDevHald on 2005-05-16
Hmm, try doing it from the Update Package Manager but hit **Refresh **after it's done initializing. That will grab all of the new udates/upgrades from the backports.

---

### Post by artAlexion on 2005-05-16
[QUOTE=BB]Hmm, try doing it from the Update Package Manager but hit **Refresh **after it's done initializing. That will grab all of the new udates/upgrades from the backports.[/QUOTE]

No Update Package Manager in Warty (that I know of)  Sorry, I should have mentioned that I am using Warty, still.

---

### Post by daenney on 2005-05-16
I had the same errors as DaXor

Apparently the backports are back up again but I do get this in apt:

Ign [http://backports.ubuntuforums.org]("http://backports.ubuntuforums.org") hoary-backports Release.gpg
Ign [http://backports.ubuntuforums.org]("http://backports.ubuntuforums.org") hoary-extras Release.gpg

What does the Ign mean? Ignoring or something else?

---

### Post by jdong on 2005-05-16
Ign means "Ignored". I do not GPG-sign my packages, so they don't have a Release.gpg file. It's normal.

---

### Post by ubuntu-geek on 2005-05-16
We now have a new mirror that will improve the speeds and hopefully take over some of the main site's bandwidth issues :) Check here:

[http://backports.ubuntuforums.org/url.php](http://backports.ubuntuforums.org/url.php)

---

