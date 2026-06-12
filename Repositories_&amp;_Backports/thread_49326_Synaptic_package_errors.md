---
title: "Synaptic package errors"
date: 2005-07-15
forum: Repositories &amp; Backports
---

### Post by joplass on 2005-07-15
I get these errors when Synaptic starts:
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_main_binary-i386_Packages) - stat (2 No such file or directory)

If click ok I get these:
[http://backports.ubuntuforums.org/ubp/dists/hoary-backports/Release.gpg:](http://backports.ubuntuforums.org/ubp/dists/hoary-backports/Release.gpg:) Could not connect to backports.ubuntuforums.org:80 (69.46.19.12). - connect (111 Connection refused)
[http://backports.ubuntuforums.org/ubp/dists/hoary-extras/Release.gpg:](http://backports.ubuntuforums.org/ubp/dists/hoary-extras/Release.gpg:) Could not connect to backports.ubuntuforums.org:80 (69.46.19.12). - connect (111 Connection refused)
[http://backports.ubuntuforums.org/ubp/dists/hoary-backports/main/binary-i386/Packages.gz:](http://backports.ubuntuforums.org/ubp/dists/hoary-backports/main/binary-i386/Packages.gz:) Could not connect to backports.ubuntuforums.org:80 (69.46.19.12). - connect (111 Connection refused)
[http://backports.ubuntuforums.org/ubp/dists/hoary-backports/universe/binary-i386/Packages.gz:](http://backports.ubuntuforums.org/ubp/dists/hoary-backports/universe/binary-i386/Packages.gz:) Could not connect to backports.ubuntuforums.org:80 (69.46.19.12). - connect (111 Connection refused)
[http://backports.ubuntuforums.org/ubp/dists/hoary-backports/multiverse/binary-i386/Packages.gz:](http://backports.ubuntuforums.org/ubp/dists/hoary-backports/multiverse/binary-i386/Packages.gz:) Could not connect to backports.ubuntuforums.org:80 (69.46.19.12). - connect (111 Connection refused)
[http://backports.ubuntuforums.org/ubp/dists/hoary-backports/restricted/binary-i386/Packages.gz:](http://backports.ubuntuforums.org/ubp/dists/hoary-backports/restricted/binary-i386/Packages.gz:) Could not connect to backports.ubuntuforums.org:80 (69.46.19.12). - connect (111 Connection refused)
[http://backports.ubuntuforums.org/ubp/dists/hoary-extras/main/binary-i386/Packages.gz:](http://backports.ubuntuforums.org/ubp/dists/hoary-extras/main/binary-i386/Packages.gz:) Could not connect to backports.ubuntuforums.org:80 (69.46.19.12). - connect (111 Connection refused)
[http://backports.ubuntuforums.org/ubp/dists/hoary-extras/universe/binary-i386/Packages.gz:](http://backports.ubuntuforums.org/ubp/dists/hoary-extras/universe/binary-i386/Packages.gz:) Could not connect to backports.ubuntuforums.org:80 (69.46.19.12). - connect (111 Connection refused)
[http://backports.ubuntuforums.org/ubp/dists/hoary-extras/multiverse/binary-i386/Packages.gz:](http://backports.ubuntuforums.org/ubp/dists/hoary-extras/multiverse/binary-i386/Packages.gz:) Could not connect to backports.ubuntuforums.org:80 (69.46.19.12). - connect (111 Connection refused)
[http://backports.ubuntuforums.org/ubp/dists/hoary-extras/restricted/binary-i386/Packages.gz:](http://backports.ubuntuforums.org/ubp/dists/hoary-extras/restricted/binary-i386/Packages.gz:) Could not connect to backports.ubuntuforums.org:80 (69.46.19.12). - connect (111 Connection refused)
[ftp://ftp.nerim.net/debian-marillat/dists/stable/main/binary-i386/Packages.gz:](ftp://ftp.nerim.net/debian-marillat/dists/stable/main/binary-i386/Packages.gz:) MD5Sum mismatch
[ftp://ftp.nerim.net/debian-marillat/dists/testing/main/binary-i386/Packages.gz:](ftp://ftp.nerim.net/debian-marillat/dists/testing/main/binary-i386/Packages.gz:) MD5Sum mismatch

How can I correct these errors?  I will say the best thing is for me to remove those repositories that give me errors but I am not too sure.



Thanks!

---

### Post by zeroK on 2005-07-16
The error is related with the > [ftp://ftp.nerim.net/debian-marillat...86/Packages.gz:](ftp://ftp.nerim.net/debian-marillat...86/Packages.gz:) MD5Sum mismatch-lines of the second problem. Since the package list appears to be broken doesn't create /var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-i386_Packages.

And the backports.ubuntuforums.org-lines are caused by the server seeming being disabled/locked/whatever. But the mirror still seems to work :-)

[http://mirror.brianpuccio.net/ubuntu-backports-repository/](http://mirror.brianpuccio.net/ubuntu-backports-repository/)

---

### Post by joplass on 2005-07-16
Do you or anyone else know how I can fix this problem?
Thanks,

---

