---
title: "Do I have to reinstall snort again if clamav db is upgraded?"
date: 2007-02-22
forum: Server Platforms
---

### Post by johnnydepp74 on 2007-02-22
Hi, 

a newbie question. I have installed snort 2.6.0.2 patched with clamav preprocessor and the installed clamav version is 0.88.7 on my production ids box. 

Recently, I just upgraded my clamav version to 0.90 by uninstalling the previous 0.88.7 version (make uninstall) and installing the new version (configure; make; make install). 

Question: do I have to reinstall the previously installed snort and if yes, what commands do I have to run ?? 
I do not want to break any existing links here and there becoz this is a production box.  

fyi I had installed snort using the following command: 

./configure --enable-clamav --with-clamav-includes=/usr/local/include 
--with-clamav-defdir=/usr/local/share/clamav --with-mysql=/usr/local/mysql --enable-dynamicplugin 

Any help from those gurus will be appreciated. Thanks 

Rgds 
John

---

