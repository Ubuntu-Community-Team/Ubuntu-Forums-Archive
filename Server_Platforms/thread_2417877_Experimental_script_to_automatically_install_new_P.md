---
title: "Experimental script to automatically install new PHPMyAdmin"
date: 2019-04-28
forum: Server Platforms
---

### Post by direc85 on 2019-04-28
Hello everybody!

I had some serious frustrations trying to use [PHPMyAdmin on Ubuntu 18.04.6 with PHP 7.2]("https://bugs.launchpad.net/ubuntu/+source/phpmyadmin/+bug/1767361"), and noticed that [the package]("https://packages.ubuntu.com/bionic/phpmyadmin") is rather old. Actually it has been last updated in [July 2017]("http://changelogs.ubuntu.com/changelogs/pool/universe/p/phpmyadmin/phpmyadmin_4.6.6-5/changelog")! It looks like the original maintainer doesn't update the package anymore, so there is little to gain in making noise in the bug tracker until someone new jumps in :(

Since I don't know a thing about Debian/Ubuntu packaging, I decided to create a bash script instead. **It is highly experimental at the moment**, but it has reached a point where I could share it...

Newcomers, please stay away from this for now. Seriously.

Experienced users, please take backups or snapshot your VM!

The script can be downloaded from my [GitHub repository]("https://github.com/direc85/phpmyadmin-installer"). Please go through readme and the script before firing it up. Testing, feedback and pull requests are most welcome! Let's make this script something more fool-proof, shall we :)

Thanks!

---

