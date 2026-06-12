---
title: "Repository for acroread"
date: 2006-10-05
forum: Repositories &amp; Backports
---

### Post by textguru on 2006-10-05
I have posted inquiry yesterday: [http://ubuntuforums.org/showthread.php?t=271668](http://ubuntuforums.org/showthread.php?t=271668)

But it seems that I cant install acroread plugin for mozilla firefox. Can you point me to the right repository? :confused:

---

### Post by guysmiley25 on 2006-10-06
I have it, I dont know what one it is but this is where I got my repository file from

[http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories)

Hope that helps.

---

### Post by Jussi Kukkonen on 2006-10-06
You need *multiverse*.

---

### Post by textguru on 2006-10-06
> **Jussi Kukkonen said:**
> You need *multiverse*.

are you pertaining to these:

 deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
 deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

If yes, both are uncommented. I have done the following after editing the sources.list

sudo apt-get update
sudo apt-get upgrade

Hope you might help.

---

### Post by textguru on 2006-10-06
> **guysmiley25 said:**
> I have it, I dont know what one it is but this is where I got my repository file from

[http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories)

Hope that helps.

I have tried to uncomment all and found no luck. Btw, I am using Xubuntu desktop.

---

### Post by aysiu on 2006-10-06
Follow these instructions:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by textguru on 2006-10-06
> **aysiu said:**
> Follow these instructions:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Thanks. It really helps. I am now downloading the update.

---

