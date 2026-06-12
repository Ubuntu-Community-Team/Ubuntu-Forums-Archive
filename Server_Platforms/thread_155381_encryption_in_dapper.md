---
title: "encryption in dapper"
date: 2006-04-04
forum: Server Platforms
---

### Post by Subnet on 2006-04-04
lately I have been reading about encryption and encfs. However, I noticed that apparently encfs and the dependencies are not in the repositories right now. Is there a way to maybe get them from the Breezy repositories, or maybe install them from the deb file? Any suggestions or comments would be of great help.:-D

---

### Post by Subnet on 2006-04-05
Found the answer I followed this guide [http://ubuntuforums.org/showthread.php?t=148359](http://ubuntuforums.org/showthread.php?t=148359) and added
 *deb [ftp://ftp.ubuntu.com/ubuntu](ftp://ftp.ubuntu.com/ubuntu) dapper main restricted universe* to my sources.list file and also uncommented
[I]deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe[/I] and now I can install encfs.....so apparently this was a user error](*,)

---

