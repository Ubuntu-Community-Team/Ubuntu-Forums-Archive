---
title: "Repository software updates"
date: 2007-03-31
forum: Repositories &amp; Backports
---

### Post by Richard Carlson on 2007-03-31
This is my question:  Why do the repositories seem to take forever to get up to speed with the latest apps being developed? Also what are the chances of getting  some additional apps that are being developed by 3rd parties?

 For example. . ..I'd like to get 'Lazarus' fpc  on my system but I'm running into various file dependency problems. Hugin is in the developmental stage but can also be installed (as long as you get all of the compiled dependencies from your repositories. . .) You've completely dropped this app. . . 

I'm an avid amateur astronomer. Kstars is ok, but other packages are out there such as 'Cartes du Ciel' i.e. Sky Charts. .(Works well) .

As far as updated versions of applications. . . 
 Stellarium is now version 8.2, Celestia is 1.4.1.  but your repositories are still behind the developmental curve. (Still using Stellarium 7.1 and Celestia 1.3.2. . .Celestia can easily be installed with its autopackage program.  Stellarium  will work if you've got all of the dependencies. .. 

 What does it take to get the newest versions into your repositories and the apps up to speed? It seems you are behind on the developmental curve
with applications. .  .

Mind you this is not a complaint. .. just wondering why it seems to take forever for the apps to catch up with the development that they are seeing. 

Another question: what about apps such as 'Google-earth', 'Picasa' ? 

These are just a few of my questions. . . .:KS

---

### Post by WW on 2007-03-31
In general, once a version of Ubuntu is released, the packages in it are "frozen", and will never be updated except for security or critical bug fixes.

*Some* updated packages are available from the backports project.

---

### Post by 23meg on 2007-03-31
[QUOTE=Richard Carlson]What does it take to get the newest versions into your repositories and the apps up to speed? It seems you are behind on the developmental curve
with applications. . .[/QUOTE]

Ubuntu freezes the repositories after each stable release, until the next one. If you're dissatisfied with this, you should use a distro that uses a rolling release system instead of a freeze system, where new packages become available between releases.

[QUOTE=WW]In general, once a version of Ubuntu is released, the packages in it are "frozen", and will never be updated except for security or critical bug fixes.[/QUOTE]

Not in general; that's valid for all releases at all times.

---

### Post by WW on 2007-03-31
Well, the backports are more than just bug fixes.  Since the backports are an "official Ubuntu project" [1], they *could* be considered part of a release (e.g. dapper-backports is part of dapper).  But this is just a matter of semantics. :)


[1] [http://ubuntuforums.org/showthread.php?t=40291](http://ubuntuforums.org/showthread.php?t=40291)

---

