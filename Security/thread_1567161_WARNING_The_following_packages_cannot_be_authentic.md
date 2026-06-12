---
title: "WARNING: The following packages cannot be authenticated!"
date: 2010-09-03
forum: Security
---

### Post by iamqiuhui on 2010-09-03
how to pass thought the authentication?
if not authentication ,why advise me to install this software?

i want security ,not the unknown factor

---

### Post by uRock on 2010-09-03
I didn't get those warnings for the bogofilter updates. Do you get this warning with everything you try to install of just these?

---

### Post by movieman on 2010-09-03
I didn't get it either, so they could be bogus files or they could have been corrupted in the download, or there could be a missing authentication key on that machine.

---

### Post by uRock on 2010-09-03
There could be something wrong in software.sources.

---

### Post by bodhi.zazen on 2010-09-03
> **movieman said:**
> I didn't get it either, so they could be bogus files or they could have been corrupted in the download, or there could be a missing authentication key on that machine.

The OP probably added software sources, likely ppa, without adding the key.

```
sudo add-apt-repository ppa:chromium-daily
```

Change "chromium-daily" to the name of the ppa you are adding.

See also :

[https://help.launchpad.net/Packaging/PPA](https://help.launchpad.net/Packaging/PPA)

[http://www.ubuntugeek.com/ubuntu-tip-simplified-way-to-add-ppa-repositories-in-karmic.html](http://www.ubuntugeek.com/ubuntu-tip-simplified-way-to-add-ppa-repositories-in-karmic.html)

---

### Post by uRock on 2010-09-03
> **bodhi.zazen said:**
> The OP probably added software sources, likely ppa, without adding the key.

```
sudo add-apt-repository ppa:chromium-daily
```Change "chromium-daily" to the name of the ppa you are adding.

See also :

[https://help.launchpad.net/Packaging/PPA](https://help.launchpad.net/Packaging/PPA)

[http://www.ubuntugeek.com/ubuntu-tip-simplified-way-to-add-ppa-repositories-in-karmic.html](http://www.ubuntugeek.com/ubuntu-tip-simplified-way-to-add-ppa-repositories-in-karmic.html)
That sounds very plausible. The update showing in the window was from the ubuntu security server, which seems odd, unless the warning list all of the updates instead of just the problem updates.

---

### Post by OpSecShellshock on 2010-09-03
In the screen capture, it does not appear that the network connection is enabled. Would that be required in order for the authentication of the packages to take place?

---

### Post by mjulius on 2010-09-04
I just got the same thing .......   ?????

---

### Post by rompe on 2010-09-30
This message seems to occure if something went wrong at the time you ran "apt-get update". Maybe the archives have been synced or your network connection went down.
Just try running "apt-get update && apt-get dist-upgrade" again a little later and see if you still get the warning.

---

### Post by Silvertones on 2010-09-30
I just got it as well. Received notice of updates & went to install and it came up. Will reboot and redownload the update info.

---

### Post by rompe on 2010-09-30
There should be no need for a reboot. "apt-get update" ought to be enough.

---

### Post by Silvertones on 2010-09-30
Was fine this time. Must have been a global issue though don't you think?

---

