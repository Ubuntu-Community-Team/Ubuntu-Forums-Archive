---
title: "Official Ubuntu repository issues"
date: 2005-06-10
forum: Repositories &amp; Backports
---

### Post by Farhad on 2005-06-10
I'm getting these errors when reloading in synaptic:

[http://us.archive.ubuntu.com/ubuntu/dists/hoary/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/hoary/main/binary-i386/Packages.gz:) 404 Not Found
[http://us.archive.ubuntu.com/ubuntu/dists/hoary/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/hoary/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://us.archive.ubuntu.com/ubuntu/dists/hoary/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/hoary/main/source/Sources.gz:) 404 Not Found
[http://us.archive.ubuntu.com/ubuntu/dists/hoary/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/hoary/restricted/source/Sources.gz:) 404 Not Found
[http://us.archive.ubuntu.com/ubuntu/dists/hoary/universe/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/hoary/universe/binary-i386/Packages.gz:) 404 Not Found
[http://us.archive.ubuntu.com/ubuntu/dists/hoary/universe/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/hoary/universe/source/Sources.gz:) 404 Not Found
[http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/main/binary-i386/Packages.gz:) 404 Not Found
[http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/main/source/Sources.gz:) 404 Not Found
[http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/source/Sources.gz:) 404 Not Found
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)

Whats wrong?  This never happened before.

---

### Post by Seth on 2005-06-10
[QUOTE=Farhad]I'm getting these errors when reloading in synaptic:

[http://us.archive.ubuntu.com/ubuntu/dists/hoary/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/hoary/main/binary-i386/Packages.gz:) 404 Not Found
[http://us.archive.ubuntu.com/ubuntu/dists/hoary/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/hoary/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://us.archive.ubuntu.com/ubuntu/dists/hoary/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/hoary/main/source/Sources.gz:) 404 Not Found
[http://us.archive.ubuntu.com/ubuntu/dists/hoary/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/hoary/restricted/source/Sources.gz:) 404 Not Found
[http://us.archive.ubuntu.com/ubuntu/dists/hoary/universe/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/hoary/universe/binary-i386/Packages.gz:) 404 Not Found
[http://us.archive.ubuntu.com/ubuntu/dists/hoary/universe/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/hoary/universe/source/Sources.gz:) 404 Not Found
[http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/main/binary-i386/Packages.gz:) 404 Not Found
[http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/main/source/Sources.gz:) 404 Not Found
[http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/source/Sources.gz:) 404 Not Found
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)

Whats wrong?  This never happened before.[/QUOTE]
 Repo's down; I get it too. Give it an hour and it'll be back.

---

### Post by rider343 on 2005-06-10
:(

---

### Post by Kyral on 2005-06-10
whew, so its not just me :P

---

### Post by dabear on 2005-06-10
[QUOTE=Kyral]whew, so its not just me :P[/QUOTE]
Yepp, confirmed here too. I can access the servers, but the packages at
[http://us.archive.ubuntu.com/](http://us.archive.ubuntu.com/) (noEmptySpacesHere) ubuntu/dists/hoary-updates/restricted/ (main | source etc.) /Sources.gz
cannot be found (404-ing)

---

### Post by willrea on 2005-06-11
is it still down for you just because i get this when trying to install libimlib2:

0 upgraded, 1 newly installed, 0 to remove and 49 not upgraded.
Need to get 185kB of archives.
After unpacking 545kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main libimlib2 1.1.2-2.1 [185kB]
Fetched 185kB in 0s (212kB/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/i/imlib2/libimlib2_1.1.2-2.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/i/imlib2/libimlib2_1.1.2-2.1_i386.deb)  MD5Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by kai on 2005-06-11
I'm getting a similar problem when I try to download certain packages (abiword, firefox), some parts cannot be retrieved.

These are the messages I'm getting:

Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/p/pango1.0/libpango1.0-0_1.8.1-0ubuntu2_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/p/pango1.0/libpango1.0-0_1.8.1-0ubuntu2_i386.deb)  MD5Sum mismatch
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/libg/libgnomecanvas/libgnomecanvas2-0_2.10.0-0ubuntu1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/libg/libgnomecanvas/libgnomecanvas2-0_2.10.0-0ubuntu1_i386.deb)  MD5Sum mismatch


It's been like this since yesterday afternoon!

---

### Post by Reb on 2005-06-11
*SNIP*
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libp/libpng/libpng10-0_1.0.18-1ubuntu1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libp/libpng/libpng10-0_1.0.18-1ubuntu1_amd64.deb)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/x/xscreensaver/xscreensaver_4.21-4ubuntu4_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/x/xscreensaver/xscreensaver_4.21-4ubuntu4_amd64.deb)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/w/wireless-tools/wireless-tools_27-3ubuntu2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/w/wireless-tools/wireless-tools_27-3ubuntu2_amd64.deb)  MD5Sum mismatch
*SNIP*
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

etc etc... there are many, many more MD5sum mismatches. I was dist-upgrading.

---

### Post by Seth on 2005-06-11
[QUOTE=Reb]*SNIP*
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libp/libpng/libpng10-0_1.0.18-1ubuntu1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libp/libpng/libpng10-0_1.0.18-1ubuntu1_amd64.deb)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/x/xscreensaver/xscreensaver_4.21-4ubuntu4_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/x/xscreensaver/xscreensaver_4.21-4ubuntu4_amd64.deb)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/w/wireless-tools/wireless-tools_27-3ubuntu2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/w/wireless-tools/wireless-tools_27-3ubuntu2_amd64.deb)  MD5Sum mismatch
*SNIP*
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

etc etc... there are many, many more MD5sum mismatches. I was dist-upgrading.[/QUOTE]
 You can switch your sources.list to use [http://archive.ubuntu.com](http://archive.ubuntu.com) for now. Might be slower, but seems to not be affected.

---

### Post by kai on 2005-06-13
Thanks a bunch, Seth!  That fixed the problem.

Does anybody know what's up with the other repositories?

---

### Post by Magneto on 2005-06-13
thanks for posting the problem

---

