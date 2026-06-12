---
title: "Qt Creator Installation Issues"
date: 2018-02-06
forum: Ubuntu Dev Link Forum
---

### Post by dickett on 2018-02-06
I am installing qtcreator according to the following procedure.
```
sudo add-apt-repository ppa:ubuntu-sdk-team/ppa
sudo apt-get update 
sudo apt-get upgrade
sudo apt-get install ubuntu-sdk-ide
```

```
source /opt/fslc-x11/2.4.1/environment-setup-armv7at2hf-neon-fslc-linux-gnueabi
qtcreator
```
The first thing qtcreator does is run usdk-target autosetup but it is failing with the following error message:
```
Stopping containers: All containers stopped.

Creating default network bridge ..... FAILED
error: Creating the bridge failed with : not implemented
```
I have tried running through sudo lxd init several ways but the results are the same.
Any ideas?
Thanks in advance,
Tim

---

