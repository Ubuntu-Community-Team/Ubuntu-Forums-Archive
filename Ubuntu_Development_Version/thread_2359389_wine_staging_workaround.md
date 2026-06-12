---
title: "wine staging workaround"
date: 2017-04-23
forum: Ubuntu Development Version
---

### Post by rrnbtter on 2017-04-23
Greetings,
I had to do a new install of Artful to get rid of some WIFI problems left over from zenial.  After the upgrade I needed Wine-Staging in order to setup Kompozer.exe since the Kompozert.deb has been deprecated since Trusty. However the Artful packages aren't released yet. 

Solution was to install the ppa and then change the ppa to Xenial in Software & Updates and updating prior to the last step of installing the recommends. The xenial packages work fine in Artful. 

I suggest removing wine-stable and or wine-dev prior to installing wine staging but you don't absolutely have to because they install in different directories. 
FYI

---

