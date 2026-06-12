---
title: "Trusty now offers upgrade to Wily"
date: 2016-02-05
forum: Ubuntu, Linux and OS Chat
---

### Post by kansasnoob on 2016-02-05
Those users who've changed the release upgrade settings from "LTS only" to "any release" will now be offered the upgrade to Wily:

[ATTACH=CONFIG]267125[/ATTACH]

That is intentional (and was also the case for Trusty -> Vivid):

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1497024](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1497024)

I haven't yet had time to test the upgrade path, and there was no QA testing that I'm aware of, so this will almost certainly be interesting (in a bad way). If nothing else many nVidia users will find that the proprietary drivers no longer work:

[http://ubuntuforums.org/showthread.php?t=2311759&p=13432574#post13432574](http://ubuntuforums.org/showthread.php?t=2311759&p=13432574#post13432574)

And many Intel graphics users will find badly garbled graphics:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1507255](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1507255)

Of course smart users will have left the settings as Canonical intended but we all know how that goes.

---

### Post by grahammechanical on 2016-02-05
At least changing the notification to any new release does not now inform the user that there are no new releases available or that the upgrade cannot take place because the upgrade scripts are looking for the next release in line instead of jumping a release.

A further thought. It might avoid some users trying to upgrade using do-release-upgrade with the -d switch and ending up on the next development version.

Regards.

---

### Post by vasa1 on 2016-02-05
> **kansasnoob said:**
> ...
Of course smart users will have left the settings as Canonical intended but we all know how that goes.
Please mention where these settings are. I can't remember where :( :( :(

Found it! It's in *Software & Updates* in the *Updates* tab ...

But just out of curiosity, where is this information stored? IOW, is there a file in */etc/apt* perhaps that has it?

---

### Post by kansasnoob on 2016-02-05
> **grahammechanical said:**
> At least changing the notification to any new release does not now inform the user that there are no new releases available or that the upgrade cannot take place because the upgrade scripts are looking for the next release in line instead of jumping a release.

Regards.

If I had my druthers we'd make it a bit harder to change that setting by either (a) hiding it (maybe it shouldn't even have a GUI) or (b) having a pop-up warning appear when you change that setting with basic EOL info - eg; "***The change you have selected will upgrade you to 15.10 which will reach EOL July 2016, whereas you're currently running 14.04.* which is supported until April 2019", do you still wish to proceed?***".

---

### Post by kansasnoob on 2016-02-05
> **vasa1 said:**
> Please mention where these settings are. I can't remember where :( :( :(

Found it! It's in *Software & Updates* in the *Updates* tab ...

But just out of curiosity, where is this information stored? IOW, is there a file in */etc/apt* perhaps that has it?

```
grep Prompt= **/etc/update-manager/release-upgrades**
```

Options = normal or lts

---

### Post by vasa1 on 2016-02-05
> **kansasnoob said:**
> ```
grep Prompt= **/etc/update-manager/release-upgrades**
```

Options = normal or ltsThank you :)

There's also "never".

---

