---
title: "GPG errors and backport problems on multiple boxes"
date: 2005-06-08
forum: Repositories &amp; Backports
---

### Post by hotspoons on 2005-06-08
I did a fresh install of hoary on my Athlon 64 box (32 bit install though after a less-than impressive run with the 64 bit versions of both ubuntu and winXP x64) yesterday and started the unofficial add-on cd install so I could fully use the linux install.  During installation, it overwrites /etc/apt/sources.list with its own that contains universe, multiverse, malirat, and backport repos.  I've gone through this add-on CD on a few other boxes, and never had a problem, besides sometimes needing to update the GPG key for malirat.

This time, I was getting lots of errors (below) about bad keys and bad repositories.  Thinking it was just related to my fresh install, I went ahead and apt-get updated my "screaming" 500 MHz PIII ubuntu box, and got the same errors.  I added the repositories from the ubuntu add-on cd to my KnoppMyth HD PVR box, did apt-get update, and had the same thing happen.

Is something broken?  Is comcast sassing me?  The rest of the internet works.  Any ideas?  Thnx.


```
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[i]http://backports.ubuntuforums.org/backports/dists/hoary-backports/Release.gpg: Could not connect to backports.ubuntuforums.org:80 (69.46.19.12). - connect (111 Connection refused)
http://backports.ubuntuforums.org/backports/dists/hoary-extras/Release.gpg: Could not connect to backports.ubuntuforums.org:80 (69.46.19.12). - connect (111 Connection refused)
http://backports.ubuntuforums.org/backports/dists/hoary-backports/main/binary-i386/Packages.gz: Could not connect to backports.ubuntuforums.org:80 (69.46.19.12). - connect (111 Connection refused)
http://backports.ubuntuforums.org/backports/dists/hoary-backports/universe/binary-i386/Packages.gz: Could not connect to backports.ubuntuforums.org:80 (69.46.19.12). - connect (111 Connection refused)
http://backports.ubuntuforums.org/backports/dists/hoary-backports/multiverse/binary-i386/Packages.gz: Could not connect to backports.ubuntuforums.org:80 (69.46.19.12). - connect (111 Connection refused)
http://backports.ubuntuforums.org/backports/dists/hoary-backports/restricted/binary-i386/Packages.gz: Could not connect to backports.ubuntuforums.org:80 (69.46.19.12). - connect (111 Connection refused)
http://backports.ubuntuforums.org/backports/dists/hoary-extras/main/binary-i386/Packages.gz: Could not connect to backports.ubuntuforums.org:80 (69.46.19.12). - connect (111 Connection refused)
http://backports.ubuntuforums.org/backports/dists/hoary-extras/universe/binary-i386/Packages.gz: Could not connect to backports.ubuntuforums.org:80 (69.46.19.12). - connect (111 Connection refused)
http://backports.ubuntuforums.org/backports/dists/hoary-extras/multiverse/binary-i386/Packages.gz: Could not connect to backports.ubuntuforums.org:80 (69.46.19.12). - connect (111 Connection refused)
http://backports.ubuntuforums.org/backports/dists/hoary-extras/restricted/binary-i386/Packages.gz: Could not connect to backports.ubuntuforums.org:80 (69.46.19.12). - connect (111 Connection refused)
[/i]
```

the following problems...

```
W: GPG error: http://archive.ubuntu.com hoary Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://us.archive.ubuntu.com hoary Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
```

```
W: Couldn't stat source package list http://backports.ubuntuforums.org hoary-backports/main Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://backports.ubuntuforums.org hoary-backports/universe Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://backports.ubuntuforums.org hoary-backports/multiverse Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://backports.ubuntuforums.org hoary-backports/restricted Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://backports.ubuntuforums.org hoary-extras/main Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://backports.ubuntuforums.org hoary-extras/universe Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://backports.ubuntuforums.org hoary-extras/multiverse Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://backports.ubuntuforums.org hoary-extras/restricted Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)

```

-rich

---

### Post by jdong on 2005-06-08
You shouldn't be using backports.ubuntuforums.org anymore; that's the master repository that keeps all the mirrors up-to-date.

See [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

---

### Post by simple on 2005-06-10
> http://us.archive.ubuntu.com/*..: Could not connect to us.archive.ubuntu.com:80 (216.165.129.138). - connect (111 Connection refused) 
same with this backport?

   1. You have included too many images in your signature or in your previous post. Please go back and correct the problem and then continue again.

      Images include use of smilies, the vB code [img] tag and HTML <img> tags. The use of these is all subject to them being enabled by the administrator. <-- lame, i couldn't post like http://us.archive.ubuntu.com/ubuntu/dists/hoary/Release.gpg: Could not connect to us.archive.ubuntu.com:80 (216.165.129.138). - connect (111 Connection refused) all twelve of those errors for the various backports

---

