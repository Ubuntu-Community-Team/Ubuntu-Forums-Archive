---
title: "Please help ubuntu 12.04 upgrade gone wrong"
date: 2012-04-13
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by joeg2324 on 2012-04-13
I've been using ubuntu 12.04 for about a month and everything has been going great until ten minutes ago when I dowloaded some updates. After rebooting, the launcher is completely gone and I have only the desktop. Is anyone else experiencing this? Is there a way to get it back?

---

### Post by JRV on 2012-04-13
Welcome aboard,

Try:```
unity --reset
```

From now on please post questions about 12.04 in the Ubuntu +1 (Precise Pangolin) forum.

---

### Post by joeg2324 on 2012-04-13
Thanks, I'm getting a message that says: 
The program 'unity' is currently not installed.  You can install it by typing:
sudo apt-get install unity

I guess I should re install it?

---

### Post by joeg2324 on 2012-04-13
It's working now. I re installed unity and did a unity --reset like you said and everything is working now. Not sure what happened, but the update I did must have uninstalled unity some how. Thanks!

---

### Post by raja.genupula on 2012-04-13
ok now please mark the thread as solved from thread tools . that can help us to look for other unsolved threads .

Thank you .

---

### Post by JRV on 2012-04-13
Did you do a partial upgrade?
They should usually be avoided because they often mess things up.
To upgrade a pre-release version I use:
```

sudo apt-get update
sudo apt-get install aptitude
sudo sudo aptitude safe-upgrade

```

Read this thread for more details:

[http://ubuntuforums.org/showthread.php?t=1859240](http://ubuntuforums.org/showthread.php?t=1859240)

Then look through the "Ubuntu +1 (Precise Pangolin)" forum.  
There are always problems with upgrades in pre-release versions.

---

### Post by nothingspecial on 2012-04-13
*Thread moved to **Ubuntu +1 (Precise Pangolin)**.*

---

### Post by buzzmandt on 2012-04-13
> **JRV said:**
> Did you do a partial upgrade?
They should usually be avoided because they often mess things up.
To upgrade a pre-release version I use:
```

sudo apt-get update
sudo apt-get install aptitude
sudo sudo aptitude safe-upgrade

```

Read this thread for more details:

[http://ubuntuforums.org/showthread.php?t=1859240](http://ubuntuforums.org/showthread.php?t=1859240)

Then look through the "Ubuntu +1 (Precise Pangolin)" forum.  
There are always problems with upgrades in pre-release versions. 
isn't apt-get upgrade the same as aptitude safe-upgrade?

---

### Post by zombifier25 on 2012-04-13
aptitude is smarter than apt-get at handling dependencies... I think. I have a few cases in which apt-get will not upgrade fully, while aptitude will do it just fine.

---

### Post by bluenova on 2012-04-13
Or just 'apt-get dist-upgrade' and check if anything important is going to be removed before entering Y.

---

### Post by raja.genupula on 2012-04-13
[http://askubuntu.com/questions/117088/aptitude-safe-upgrade-equivalence-with-apt-get](http://askubuntu.com/questions/117088/aptitude-safe-upgrade-equivalence-with-apt-get)

---

### Post by buzzmandt on 2012-04-13
Oh that's quite nice actually. Thank you

---

### Post by joeg2324 on 2012-04-13
I had done a Apt-get dist-upgrade 
Should I have not done this?

---

### Post by raja.genupula on 2012-04-13
> **joeg2324 said:**
> I had done a Apt-get dist-upgrade 
Should I have not done this?

you have to do that , you should . its also important one .

---

### Post by buzzmandt on 2012-04-13
Just be watchful on the packages it might want to remove

---

