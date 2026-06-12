---
title: "Help! DansGuardian uninstall nightmare -- Internet Conncetion Dead"
date: 2007-01-02
forum: Ubuntu Christian Edition
---

### Post by chaplanger on 2007-01-02
I had noticed that since installing Ubuntu CE -- my internet browsing was slower.  After seeing in another thread how to uninstall Dansguardian I tried this.  Now I can not connect to the internet in any browser (Firefox thinks proxy settings are wrong, but its set to "Direct connection to the internet).  Mozilla will not browse either.  

In the past when Dansguardian was first installed, Mozilla operated fine, then Firefox came back up when I changed the proxy settings through Dansguardian.

Dansguardian GUI still appears in the administrator settings area, but it has no data list for its various categories.

How can I fix this?

Is there a way to reinstall Dansguardian?
 Should I simply reinstall Ubuntu CE with a clean install on the HD devoted to Ubuntu?

How do I reinstall Ubuntu when it is currently installed as the only OS on the HD -- I would want all of the current settings wiped off (with a reformat of the HD) so that no apeck of the current system remained to confuse the installation process.

](*,)

---

### Post by mhancoc7 on 2007-01-02
Hi,
The dansguardian setup on Ubuntu CE is configured to be difficult to remove on purpose.

I would suggest that you use the the Dansguardian setup script on the Ubuntu CE Download page for Edgy/Dapper CE.

Once you have completed that I would install the latest Dansguardian GUI.
[http://www.ubuntuforums.org/attachment.php?attachmentid=20528&d=1165221070](http://www.ubuntuforums.org/attachment.php?attachmentid=20528&d=1165221070)

This version of the Dansguardian GUI will be in the next release of Ubuntu CE and gives you the ability to Enable/Disable Dansguardian more easily but still needing root access.

I hope that helps. I will be on holiday for the next few weeks so I will be away from the forums.

God Bless, Jereme

---

### Post by chaplanger on 2007-01-03
This did take care of it!  Thanks!

---

### Post by paddy2706 on 2007-01-12
actually it's quite easy:

apt-get --reinstall --purge firefox
apt-get remove dansguardian firehol tinyproxy


that's how it worked for me :)

---

