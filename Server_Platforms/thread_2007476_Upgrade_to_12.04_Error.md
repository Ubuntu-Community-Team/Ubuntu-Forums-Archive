---
title: "Upgrade to 12.04 Error"
date: 2012-06-20
forum: Server Platforms
---

### Post by shibby4555 on 2012-06-20
Keep getting the same issue. I would prefer to just upgrade via cd b/c console always gives me trouble on updates.
I've tried the following
```
 do-release-upgrade
apt-get dist-upgrade
aptitude full-upgrade
```All come with an error on exit status 1.
The aptitude upgrade gave me:
```
 E: Could not perform immediate configuration on 'libjpeg-dev'. Please see man 5 apt.conf upder APT::Immediate Configure for details. (2) 
```What that file is:
"The libjpeg-devel package includes the header files and static libraries necessary for developing programs which will manipulate JPEG files using the libjpeg library.  If you are going to develop programs which will manipulate JPEG images, you should install libjpeg-devel.  You'll also need to have the libjpeg package installed."

So perhaps, just remove it and problem solved. Don't see the need for it on a simple ftp server that I'm running.

On a side, trying to create boot disk to update my Desktop OS to 12.04, tried it on a cd and usb and keeps hanging on a black screen. Put in my old 11.10 live cd and worked fine. As always, thanks for your help and input.
-shibby

---

