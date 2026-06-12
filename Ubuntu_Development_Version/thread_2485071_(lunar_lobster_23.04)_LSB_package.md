---
title: "(lunar lobster 23.04) LSB package ?"
date: 2023-03-19
forum: Ubuntu Development Version
---

### Post by csae2608 on 2023-03-19
Hello ,

have upgraded the linux on computer to 23.04 Kubuntu.
to get the printer fully functional, it needs package "lsb",

it should be present in Ubuntu repository, however, when i try to install it, getting error

```
[FONT=monospace][COLOR=#ff5454]**E: **[/COLOR][COLOR=#000000]Package 'lsb' has no installation candidate[/COLOR]


[/FONT]
```

---

### Post by howefield on 2023-03-19
THread moved to the "*Ubuntu Development Version*" forum.

---

### Post by MAFoElffen on 2023-03-19
<< Lunar Lobster, 23.04 is still a Dev version, who's release is set for April 20th, 2023. Until then, all posts for it should be posted in: [https://ubuntuforums.org/forumdisplay.php?f=427](https://ubuntuforums.org/forumdisplay.php?f=427) >>

What printer (make and model) is it?

If, for some reason, you meant that you are looking for package "lsb-printing"... That package does not exist in the Lunar Repo's. The newest version I see that package for is for Kinetic (22.10)...
RE: [https://packages.ubuntu.com/kinetic/lsb-printing](https://packages.ubuntu.com/kinetic/lsb-printing)

---

### Post by #&amp;thj^% on 2023-03-19
How odd, it shows and should be there:
```
lsb | 4.1+Debian11ubuntu6   | trusty           | source, all
 lsb | 4.1+Debian11ubuntu6.2 | trusty-updates   | source, all
 lsb | 9.20160110            | xenial           | source
 lsb | 9.20160110ubuntu0.2   | xenial-updates   | source, all
 lsb | 9.20170808ubuntu1     | bionic           | source
 lsb | 9.20170808ubuntu1     | bionic/universe  | all
 lsb | 11.1.0ubuntu2         | focal            | source
 lsb | 11.1.0ubuntu2         | focal/universe   | all
 lsb | 11.1.0ubuntu4         | jammy            | source
 lsb | 11.1.0ubuntu4         | jammy/universe   | all
 lsb | 11.2ubuntu1           | kinetic          | source
 lsb | 11.2ubuntu1           | kinetic/universe | all
**[COLOR="#FF0000"] lsb | 11.6                  | lunar            | source[/COLOR]**


``` 
See this: [https://launchpad.net/ubuntu/+source/lsb](https://launchpad.net/ubuntu/+source/lsb)

---

### Post by deadflowr on 2023-03-19
That's shows it's source only.
No packages have been built for it, as least not directly as package name lsb.

---

### Post by #&amp;thj^% on 2023-03-19
> **deadflowr said:**
> That's shows it's source only.
No packages have been built for it, as least not directly as package name lsb.

I'm aware of that....that's why included the link.
```

Publishing details

    Published on 2023-03-06
    Copied from Primary Archive for Ubuntu by Ubuntu Archive Auto-Sync (sponsored by Ubuntu Archive Robot)
    Originally uploaded to debian sid in Primary Archive for Debian GNU/Linux

Changelog

lsb (11.6) unstable; urgency=medium

  * Team upload.
  [ Adam Borowski ]
  * Update README.Debian wrt lsb-base dematerialization; closes: #1030597.
  [ Jelmer Vernoo&#307; ]
  * Move transitional package lsb-base to oldlibs/optional.
  * Bump debhelper from old 12 to 13.

 -- Adam Borowski <email address hidden>  Sun, 05 Feb 2023 18:12:07 +0100

Available diffs

    diff from 11.5 to 11.6 (1.4 KiB)

Builds

    [FULLYBUILT] amd64

Built packages

    lsb-base transitional package for Linux Standard Base init script functionality

Package files

    lsb-base_11.6_all.deb (4.5 KiB)
    lsb_11.6.dsc (1.6 KiB)
    lsb_11.6.tar.xz (38.1 KiB)


```

---

### Post by #&amp;thj^% on 2023-03-20
FWIW:
```
 apt policy lsb-base
lsb-base:
  Installed: 11.6
  Candidate: 11.6
  Version table:
 *** 11.6 1001
       1001 http://us.archive.ubuntu.com/ubuntu lunar/main amd64 Packages
       1001 http://us.archive.ubuntu.com/ubuntu lunar/main i386 Packages
        100 /var/lib/dpkg/status

```

---

### Post by Tramontana on 2023-06-30
I'm also having this problem, with an Epson ET-2710. Installation (with the latest drivers) fails because lsb is not present. I see a reference below to a source package, which I've downloaded, but I lack the knowledge of how to use it. I have some limited familiarity with 'make' but this file doesn't resemble anything I've seen before. Assuming it results in a module acceptable to the Epson driver, are there any beginner-level instructions on how to build and install?

---

