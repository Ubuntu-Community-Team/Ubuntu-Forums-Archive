---
title: "What I just learned about installing packages"
date: 2021-10-20
forum: Ubuntu, Linux and OS Chat
---

### Post by sofasurfer on 2021-10-20
I'm not a newie but I'm always learning. Might be nothing new to you but its an eye opener to me. I found that to install a .deb package all I need to do is download it and the run apt install command, Bing, bang simple. So I guess all that the package installer does is to run the same command, right? Now if I could find a similar magic bullet for installing rpms I would be one of those rocket scientists.

---

### Post by QIII on 2021-10-20
Not a support request.  Moved to Ubuntu, Linux and OS Chat.

---

### Post by The Cog on 2021-10-21
RPMs are for Red Hat, and their package system is yum. "sudo yum install cool-package". 
Installing RPM packages on Ubuntu is not quite so easy - there is a possibility of incompatibilities, but there is a utility to convert RPM to DEB - it's called **alien**. I only ever used it once, some years ago so I don't remember the fine detail, but it did the trick for me.

---

### Post by vo-nguyen on 2021-10-30
I first learned this trick in Debian. I was in a hot mess with dependencies with dpkg -i instead of sudo apt install ./package.deb.

---

### Post by monkeybrain20122 on 2021-10-31
Actually all you need to do is to right click it. The softwarestore will open and install it. It will pull in the dependencies. Or you can install gdebi. It does the same.

For rpm if you are on Fedora (yum is deprecated) 
```

sudo dnf install ./xxx.rpm
```

As said above, you can install .rpm packages on Debian based distros like Ubuntu with alien, but it doesn't always work, depends on the package you try to install.  alien also works in reverse, it lets you install .deb packages on rpm based OSes. I used it for something years ago. On Ubuntu it creates a .deb file then you have to install either via apt, dpkg or by right click. On Fedora it converts the deb to rpm and automatically installs it as well. There may be some settings or options one could play with, but I didn't bother.

---

