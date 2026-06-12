---
title: "Can't Install Nano"
date: 2009-05-12
forum: Server Platforms
---

### Post by techdude2008 on 2009-05-12
Trying to get my Ubuntu Server 8 up and running and I'm having problems.    It appears that Nano is not installed (when I type in nano I get: bash: nano: command not found) and the package dependanceies are not working (or not updated)...if I type in sudo apt-get install nano, I get:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nano

So I am guessing the package sources needs to be updated?  Is there a manual way to install nano...or a way to update the package sources without using nano?

---

### Post by _Purple_ on 2009-05-12
Try
```
sudo apt-get update
sudo apt-get install nano
```

---

