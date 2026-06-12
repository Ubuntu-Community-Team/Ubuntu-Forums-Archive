---
title: "Edgy -&gt; Feisty : How?"
date: 2008-05-29
forum: Server Platforms
---

### Post by tamcy on 2008-05-29
Hello all,

I am too late to know that the community ceased the support of Edgy. The situation is that the edgy dist is now removed from the source servers, but I still want to upgrade my installation to Feisty (then Gutsy then Hardy). 

I first read the upgrade notes ([https://help.ubuntu.com/community/FeistyUpgrades#head-0aee739ab0dfe9702a69ee3d316f5926d5d31807](https://help.ubuntu.com/community/FeistyUpgrades#head-0aee739ab0dfe9702a69ee3d316f5926d5d31807)) but failed to follow as running "sudo do-release-upgrade" would only throws errors about files cannot be found because it attempts to read from the edgy dist. Below is some of the error logs:

[INDENT]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://hk.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz](http://hk.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://hk.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz](http://hk.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://hk.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz](http://hk.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz) 404 Not Found [IP: 91.189.88.46 80]
[/INDENT]

And I prefer not to upgrade via network because ubuntu server doesn't play well with my line, causing HTTP connection having more than 50% chance to stuck at the middle of a download. 

I also tried "Upgrading using the alternate CD/DVD" but my machine doesn't have gksu installed and I can no longer install it back (Install via network not an option, and I don't have the CD).

My question is what should I do now?

Is the advice from zvacet([http://ubuntuforums.org/showthread.php?t=436666](http://ubuntuforums.org/showthread.php?t=436666)) that changes source.list to point to feisty suits my situation? Or there's another way better?

Thanks in advance.

**EDIT: I managed to find a server still have those edgy files, but I am still hesitate doing an upgrade because of the network issue mentioned years ago ([http://ubuntuforums.org/showthread.php?t=491825](http://ubuntuforums.org/showthread.php?t=491825)) which still hasn't solved. So I really prefer the CD-ROM way. Is there any way I can make use of the alternative CD?**

Tamcy

---

### Post by gtdaqua on 2008-05-29
with alternate CD you shud be abe to upgrade without any probs.

Do not change your sources.list to point to Feisty - You will have problems in dependencies. They are obviosuly mainted specifically for Feisty.

---

