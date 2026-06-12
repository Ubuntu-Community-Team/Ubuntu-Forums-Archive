---
title: "Hardy Upgrade Docs"
date: 2008-05-20
forum: Server Platforms
---

### Post by prem1er on 2008-05-20
I am trying to upgrade my headless Gutsy server over ssh.  Can anyone send me a link to the documentation for a command line upgrade?  Thanks.

---

### Post by prem1er on 2008-05-20
I just feel like I have tried all the online HowTo's.  I have expanded my repositories and used the command 

```
sudo apt-get upgrade && sudo apt-get dist-upgrade
```

And it just installed a couple of packages, but didn't upgrade the system.

---

### Post by kustomjs on 2008-05-20
do this

sudo apt-get install update-manager-core

then

sudo do-release-upgrade

---

