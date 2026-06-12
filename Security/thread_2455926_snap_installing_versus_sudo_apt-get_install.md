---
title: "snap installing versus sudo apt-get install"
date: 2020-12-30
forum: Security
---

### Post by jedi123 on 2020-12-30
Hello folks, I would like to know  the security of  snap installing something like sudo apt-get   vis a vis  pgp signed verifcation.

I know that say **sudo apt-get install VLC d**oes verify the package 's signature before installation, but what about ** sudo snap install VLC ?** In regards to verification. 

Thank you .

---

### Post by TheFu on 2020-12-31
They both are cryptographically signed and validated.
However, the deb package from APT would likely have a stronger parentage that is traceable than a snap package version. Anyone can make a snap package and submit to Canonical's snap store.

```
$ snap search vlc
Name             Version                 Publisher  Notes  Summary
vlc              3.0.11                  videolan&#10003;  -      The ultimate media player
dav1d            0.7.0                   videolan&#10003;  -      AV1 decoder from VideoLAN

```
The "videolan" above does imply that the same team doing the deb packages and snap for vlc is the same.
```
$ snap search videolan
Name   Version  Publisher  Notes  Summary
vlc    3.0.11   videolan&#10003;  -      The ultimate media player
dav1d  0.7.0    videolan&#10003;  -      AV1 decoder from VideoLAN
```
seems a handy search as well.

As for application security post-install, that's a huge question that has been gone over many times in many different places. Snap packages run inside a sandbox/container restricted environment. This causes problems for many users and for less popular integrations to the program.

---

### Post by deadflowr on 2020-12-31
Afaik snaps use a system called assertions where all packages are signed.
Interesting read here on the differences between snap and apt: 
[https://snapcraft.io/blog/a-technical-comparison-between-snaps-and-debs]("https://snapcraft.io/blog/a-technical-comparison-between-snaps-and-debs")
About assertions here:
[https://snapcraft.io/docs/assertions]("https://snapcraft.io/docs/assertions")

---

