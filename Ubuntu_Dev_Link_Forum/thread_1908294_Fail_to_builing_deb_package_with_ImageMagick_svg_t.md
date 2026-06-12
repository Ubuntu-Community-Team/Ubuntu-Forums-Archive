---
title: "Fail to builing deb package with ImageMagick svg to png"
date: 2012-01-13
forum: Ubuntu Dev Link Forum
---

### Post by __jcubic__ on 2012-01-13
I've created deb a package that use imagemagick to convert svg icons to png, and lauchpad throw an error

[https://launchpadlibrarian.net/89825671/buildlog_ubuntu-maverick-i386.clarity-icon-theme_0.3.2~maverick1_FAILEDTOBUILD.txt.gz]("https://launchpadlibrarian.net/89825671/buildlog_ubuntu-maverick-i386.clarity-icon-theme_0.3.2~maverick1_FAILEDTOBUILD.txt.gz")

I have this in debian/control

Build-Depends: debhelper (>= 7), imagemagick (>= 6)

What package I need to include in deps it build it?

---

