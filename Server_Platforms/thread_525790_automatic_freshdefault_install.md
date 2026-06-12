---
title: "automatic fresh/default install"
date: 2007-08-14
forum: Server Platforms
---

### Post by honeydew on 2007-08-14
We use ubuntu 6.06 as our server platform at work.  As a systems admin I am constantly developing new goodies for the network.   I have recently found myself setting up some more advance servers.. I am trying to get a development machine just right.. sometimes I feel its quicker to reinstall then to go back and reverse all the configuration steps I have taken.   Now what I am wondering, is there a quick and painless way to revert to a default server install? that will remove all edited configurations and make the server fresh and clean?

thanks in advance

---

### Post by netlogic on 2007-08-15
Why don't you have separate partitions for /home /boot and /etc? Also, if the configs are the issue. You can always create a crontab to make a backup of your /etc every four hours. There is a beauty in a flat file and everything is a directory OS. If this is a test machine that has to be quickly changed, run it under VM, and use a snapshot feature. If this a test machine and can't function that way in your environment, why not have three /etc partitions and remount to different partitions as you go? The best rule to follow is just copy your configs to different files before you start. I never had to reinstall Linux if I am using standard packages. It isn't like Windows.

---

### Post by honeydew on 2007-08-15
mm maybe I am just still cary my bad habbits from windows years ago.  I believe I am going to take the snapshot aproach.. w/ either Xen or VMware.. both appear to be rather nice.  Anyways thanks for the tips.

---

