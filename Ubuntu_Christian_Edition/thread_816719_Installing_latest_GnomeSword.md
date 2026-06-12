---
title: "Installing latest GnomeSword"
date: 2008-06-03
forum: Ubuntu Christian Edition
---

### Post by mjpatey on 2008-06-03
Hi, I'm trying to install the latest version of GnomeSword from a .deb installer found here:

[http://dominique.corbex.net/gnomesword/](http://dominique.corbex.net/gnomesword/)

 My reason for using this version rather than the one in the Ubuntu repo is that the newer version supposedly allows you to change the font size of the Bible text.  I'm installing on an EeePC (small 8.9" screen) so this is important to me.

Unfortunately, installing the .deb results in an "unsatisfiable dependency": libcairo2.  I have libcairo2 installed, and it's the latest version, according to Ubuntu.

Any idea how to get this to work?

Thanks in advance for any insight!

-Mark

---

### Post by Matthew Wiebelhaus on 2008-06-03
Ok try doing this and tell me if anything happens. If you have GnomeSword installed go to apt-get use complete uninstall. Then go and reinstall libcario2 and try to install the .deb again.

---

