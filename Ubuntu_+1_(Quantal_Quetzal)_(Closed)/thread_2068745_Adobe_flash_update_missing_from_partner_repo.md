---
title: "Adobe flash update missing from partner repo"
date: 2012-10-09
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by alphacrucis2 on 2012-10-09
E```
rr http://archive.canonical.com/ quantal/partner adobe-flash-properties-gtk amd64 11.2.202.243-0quantal1
  404  Not Found [IP: 91.189.92.191 80]
Err http://archive.canonical.com/ quantal/partner adobe-flashplugin amd64 11.2.202.243-0quantal1
  404  Not Found [IP: 91.189.92.191 80]
Failed to fetch http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flash-properties-gtk_11.2.202.243-0quantal1_amd64.deb  404  Not Found [IP: 91.189.92.191 80]

```

The latest batch of updates included the above but it appears the specified deb file doesn't exist. I disabled the partner repo and reran updates to install the other stuff in the meantime.


Edit. Just noticed FF 16 landed. I wondered if it would make it before QQ release.

---

### Post by exploder on 2012-10-09
I enabled the partner source repo and got the updated flash. Weird but it worked.

---

### Post by alphacrucis2 on 2012-10-09
> **exploder said:**
> I enabled the partner source repo and got the updated flash. Weird but it worked.

Maybe it landed in between time. I can't try again right now but I will in an hour or two.

---

### Post by cariboo on 2012-10-09
I had the same problem this morning, flash won't install, but doing updates this evening, flash installed with no problem.

---

### Post by sammiev on 2012-10-09
> **exploder said:**
> I enabled the partner source repo and got the updated flash. Weird but it worked.

Tried that no luck here yet. Guess I will try in the morning.

---

### Post by pqwoerituytrueiwoq on 2012-10-09
if we are all using the flashplugin-installer package i had it fail 2 times for me
1st time i ran my update manager and i was notified the same way i and for crashes but a different icon
it said it failed to download something and to check my net connection and gave my a button to try it again, it worked just fine
later i installed updates on my moms system
i installed updates over ssh with apt-get i noticed the libflashplayer.so was missing later
i ran sudo apt-get install  flashplugin-installer it said it was upto date so i purged it and ran installed it and it worked just fine

---

### Post by alphacrucis2 on 2012-10-10
Well I tried the update again and it worked this time

---

### Post by sammiev on 2012-10-10
Purged all and tried again fresh and this is what I get. At this point I'm a little lost.

> Preconfiguring packages ...
Selecting previously unselected package flashplugin-installer.
(Reading database ... 193948 files and directories currently installed.)
Unpacking flashplugin-installer (from .../flashplugin-installer_11.2.202.243ubuntu1_amd64.deb) ...
Processing triggers for update-notifier-common ...
flashplugin-installer: downloading [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.243.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.243.orig.tar.gz)
Installing from local file /tmp/tmpdQ2Elq.gz
Flash Plugin installed.
Setting up flashplugin-installer (11.2.202.243ubuntu1) ...
W: Waited for dpkg --assert-multi-arch but it wasn't there - dpkgGo (10: No child processes)


---

### Post by Frogs Hair on 2012-10-10
You could give this a try if using Firefox . I had no problem with the update from the repository.[https://addons.mozilla.org/en-us/firefox/addon/flash-aid/](https://addons.mozilla.org/en-us/firefox/addon/flash-aid/)

---

### Post by jfernyhough on 2012-10-10
Sometimes the packages are listed in the repository package list but the .deb file is not there. There are a few possible reasons. Firstly, it might not have uploaded yet, or correctly. Secondly, it may have been pulled due to a packaging error or omission. Third - I'm sure you can come up with more.

This sort of thing happens quite often. Just refresh the package lists and try again. If nothing, try later. It's not a big deal.

---

### Post by crichard on 2012-10-10
I've uninstalled and reinstalled the flashplugin. It is working now.
```
sudo apt-get remove flashplugin-installer
```
```
sudo apt-get install flashplugin-installer
```

---

### Post by sammiev on 2012-10-10
It seems when you check your add-ons in FF it shows you do not have the latest, when you go to Flash Players test site it tells you you have the latest. I guess a bug in FF. Thanks folks for your suggestions. :)

---

