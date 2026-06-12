---
title: "'installers' fail to work in wine"
date: 2010-12-23
forum: Wine
---

### Post by 0jciec on 2010-12-23
Hello!
I have a problem with installing software like: java, silverlight, or chrome in Wine.
They seem to start correctly but eventually** they all use their own 'installers' that suppose to download additional  data, but instead the error message appears ('installation failed') **
 I think that maybe  ubuntu/wine dosen't allow them to connect to the internet. 
 For example Java  installs without any problems with 'offline installer'.  
Please help.
Oh, and sorry for my english:)

---

### Post by sikander3786 on 2010-12-23
Welcome to the forums :-)

Wine is just a compatibility layer and most of the Windows software might not run exactly as it was intended to. Check the Wine database.

[http://appdb.winehq.org/](http://appdb.winehq.org/)

And why do you want to install Java and Chrome in Wine? They are natively available for Linux and you can install them from Applications > Software Center.

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by 0jciec on 2010-12-23
> **sikander3786 said:**
> 

And why do you want to install Java and Chrome in Wine? They are natively available for Linux

I want to watch videos on some site which requires both silverlight and java. Moonshine does'nt work there (it's officially confirmed).Chrome was only for test couse it also uses its own installer.
I've searched WineHQ already but  guess i will give another try. 
Thanks for reply.

---

### Post by cogadh on 2010-12-24
Wine probably isn't going to work for that. I'm assuming that you are trying to access a site like Netflix, which uses Silverlight for its DRM stack. Since Wine does not include the necessary OS components for the DRM stack to actually work, Netflix and most other sites like that are not going to work, no matter what you do.

---

### Post by 0jciec on 2010-12-26
Oh, thanks for info Cogadh, i will try virtualbox then.
But the problem with soft, that connects to to internet during installation, on Wine is still valid.
Best Regards !

---

