---
title: "Most apt-get package installs fail"
date: 2010-10-12
forum: Server Platforms
---

### Post by pthurmond on 2010-10-12
I am running Ubuntu Server 10.04. It is a fresh install, reinstalled it tonight in fact. And I am having a lot of problem getting packages to install. I added a few more sources to my "/etc/apt/sources.list" and that helped with a few items.

However on almost everything I try to install I am getting a "E: Broken packages" message which usually follows the listing of some package dependency that it says is not going to be installed.

For example, I tried to install php5-dev, but I get a message about libssl-dev and libtool. When I try to install those I get more of the same but with different packages. I followed the rabbit hole for awhile, but it is getting tiresome and pointless.

Does anyone have any idea what is going on? I have already run "sudo apt-get update" and "sudo apt-get upgrade" with nothing changing.

Thanks for your help in advance!

-Patrick

---

### Post by sikander3786 on 2010-10-12
Hi.

First of all try to install missing dependencies

```
sudo apt-get install -f
```

If it doesn't work

```
sudo dpkg --configure -a
```

And then,

```
sudo apt-get update
```

Post back the errors encountered, if any.

---

