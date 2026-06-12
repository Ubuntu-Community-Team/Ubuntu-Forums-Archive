---
title: "Updating server from 7.10 to 8,04"
date: 2008-08-16
forum: Server Platforms
---

### Post by Sir Jake on 2008-08-16
Hello there, I would like to know if many people have had issues upgrading from 7.10 to 8.04  I wish to upgrade my server if I will not have many issues doing so.  This server is at a colocation so I would have to install via ssh how would I do that?
 Thanks for the help.
Jake,

---

### Post by windependence on 2008-08-16
```
sudo aptitude install update-manager-core

sudo do-release-upgrade
```

HTH

-Tim

---

### Post by Sir Jake on 2008-08-18
Hello there after running this command and it doing alot of things it's stuck on en_US.UTF-8...


Last few lines show 
"Setting up librpc-xml-perl (0.59-2) ...
Setting up lubotr2 (3.1.0-2) ...

Setting up libavahi-ui0 (0.6.22-2ubuntu4) ...

Setting up locales (2.7.9-4) ...
Generating locales...
  en_US.UTF-8...


It's been stuck on this for a few hours how. :(  Please help.

---

### Post by Girya on 2008-08-18
I had the same problem as your describing. you need to enter grub and boot into the choice with the earlier kernal version Maybe .14 or .15
then run the upgrade when I did this the upgrade ran without a hitch. 

you can search the forum for this issue.

here is the link to the thread

[http:// http://ubuntuforums.org/showthread.php?t=865679]("http://ubuntuforums.org/showthread.php?t=865679")

---

### Post by Sir Jake on 2008-08-18
I'll read some of the things on that post, server is at a colcation though so loggin into grub is not really an option for me here. :(

---

