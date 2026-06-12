---
title: "Synaptic got all messed up, help!"
date: 2007-06-07
forum: Repositories &amp; Backports
---

### Post by alex2035 on 2007-06-07
My Synaptic is messed up and I cant get it to update any more. I made a system upgrade (Ubuntu 5.10) and installed several packages OK. Then I added some repositories and the problem begin, it started to show errors readind sources.list and the /var/lib/apt/ area where it reported dozens of errors. I removed the files there in an attempt to fix the problem. Now I have a synaptic showing only the contents of the cdrom and it would not let me add any repositories whatsoever. It keeps showing errors all over. any idea how I can clean this mess? thank you

---

### Post by 5-HT on 2007-06-07
Could you please post the error messages so that someone can take a look to see what's going on?

---

### Post by alex2035 on 2007-06-08
This is what appears upon launching Synaptic:

-----------------------------------------------------------------------------------
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
-----------------------------------------------------------------------------------------------------
This happens when I do a Reload Packages:
It starts to scan and stops with this:
-----------------------------------------------------------------------------------------------------
cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/dists/breezy/main/binary-i386/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/dists/breezy/restricted/binary-i386/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
[http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz:) 404 Not Found
[http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.89.8 80]
[http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.89.8 80]
[http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz:) 404 Not Found
[http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.89.8 80]
[http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.89.8 80]
[http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.89.8 80]
[http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.89.8 80]
[http://security.ubuntu.com/ubuntu/dists/breezy-security/multiverse/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/multiverse/binary-i386/Packages.gz:) 404 Not Found
[http://archive.ubuntu.com/ubuntu/dists/breezy-updates/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.89.8 80]
[http://archive.ubuntu.com/ubuntu/dists/breezy-updates/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/multiverse/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.89.8 80]
----------------------------------------------------------------------------------------------------------------------------
And finally shows an error box where it repeats the messages from the first dump above.

Hope this helps

---

### Post by alex2035 on 2007-06-10
SOLVED.
Just to  let you know. I got to a point where it broke the xserver and everything became a mess. Started a fresh installation, this time version 6.06 LTS . I got my system running OK now, with all the updates. Despite  this is an old laptop (PII300) surprisingly it moves faster than with 5.10 :D

---

