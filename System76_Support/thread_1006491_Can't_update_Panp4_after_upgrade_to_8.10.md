---
title: "Can't update Panp4 after upgrade to 8.10"
date: 2008-12-09
forum: System76 Support
---

### Post by carpecatfish on 2008-12-09
First off, I am a total noob who has had his Pangolin Performance running 8.04 since August with few problems. So here goes...

After uprgading to 8.10 (I followed the instructions to the letter including installing the new System 76 driver). So far so good. Everything is fine, except that when I log in, I have to enter my password twice. Also, when I try to install updates, absolutely nothing happens after I enter password. The machine thinks for 5 seconds and I am returned to package manager with all available updates still seemingly available for installation. I was able to change my password.

Thanks in advance,

M.F. Huntington

---

### Post by thomasaaron on 2008-12-09
Please go to a terminal and enter these commands...

```
sudo apt-get update

sudo apt-get --assume-yes dist-upgrade
```

Do they throw any errors?

Not sure about you having to enter your password twice. Could be a hosed upgrade.

---

### Post by carpecatfish on 2008-12-09
Ok! Updates installed with no errors. Have to enter pw twice in terminal too.

---

### Post by thomasaaron on 2008-12-09
Check out these two posts. See if either of them helps.

[http://ubuntuforums.org/archive/index.php/t-503976.html](http://ubuntuforums.org/archive/index.php/t-503976.html)
[http://ubuntuforums.org/archive/index.php/t-98205.html](http://ubuntuforums.org/archive/index.php/t-98205.html)

---

