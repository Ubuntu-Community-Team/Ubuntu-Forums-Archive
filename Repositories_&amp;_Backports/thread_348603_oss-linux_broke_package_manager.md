---
title: "oss-linux broke package manager"
date: 2007-01-29
forum: Repositories &amp; Backports
---

### Post by stevemazdaspeed on 2007-01-29
ok, I rushed into trying to get some games to work, and now all has gone to hell. It all started with getting oss installed on my system. I went to their site and download the .deb package and used package installer to install it. All was good for a while, untill I tried to install some updates. Apperently the oss files weren't in the proper space. Couldn't re-install, uninstall, anything. Then I used the installation program for oss to try to fix things. Well, that was a bad idea since it killed the volume manager and all sound on the system. Now synaptic is dead, gives the following errors:

E: The package oss-linux needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

E: I wasn't able to locate file for the oss-linux package. This might mean you need to manually fix this package.

And I can't seam to fix anything :mad: :mad: :mad: 

Please someone help......

---

### Post by Marvil on 2007-02-04
Hi Stevemazdaspeed, 
Help is here ;-) , I'm a bit new in Linux, but i don't give up. I used to old copy and paste approach. 

You still have the *.deb package you downloaded? if not download it again. 

Open the package with Archive manager, exctract the files to your home folder. 
Copy them to their right place in the filesystem it was /etc/  and /usr/
Then try to reinstall the Oss once again with sudo dpkg -i oss.*

This should be working. 

Cheers and god luck
Marvil

---

### Post by canelle on 2007-02-19
Hi Stevemazdaspeed,
I had the same problem. try the following command:
sudo dpkg --remove --force-depends --force-remove-reinstreq oss-linux

Let me know how it goes.
Good luck.

---

### Post by akwatve on 2008-01-23
I had a broken oss-linux which I was not able to remove or reinstall. Suggestion by Marvil worked for me...
Thanks Marvil

---

