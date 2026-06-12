---
title: "Can't remove seamonkey-mozilla-build"
date: 2011-02-24
forum: Ubuntuzilla
---

### Post by GnuSense on 2011-02-24
I recently updated from Hardy to Lucid (and changed the ubuntuzilla repositories, as per the installation page at Sourceforge). I'd used ubuntuzilla to give me the latest version of seamonkey, but these days it seems like the repository version is current. I'd rather use the repository version because I have multiple Ubuntu installs on various machines and use the approx proxy on a low-powered home server to avoid downloading the same programs several times. But when I try to remove seamonkey-mozilla-build or install seamonkey-browser I get errors.

```
# apt-get remove seamonkey-mozilla-build
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  seamonkey-mozilla-build
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 413968 files and directories currently installed.)
Removing seamonkey-mozilla-build ...
dpkg-divert: mismatch on package
  when removing `diversion of /usr/bin/seamonkey to /usr/bin/seamonkey.ubuntu by seamonkey-mozilla-build'
  found `local diversion of /usr/bin/seamonkey to /usr/bin/seamonkey.ubuntu'
dpkg: error processing seamonkey-mozilla-build (--remove):
 subprocess installed post-removal script returned error exit status 2
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Errors were encountered while processing:
 seamonkey-mozilla-build
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
Purging or adding THE FORCE doesn't help.  
[INDENT]
dpkg-divert --list |grep seamonkey
local diversion of /usr/bin/seamonkey to /usr/bin/seamonkey.ubuntu[/INDENT]

I guess a diversion is missing or damaged, I'm not wise in the ways of such things, what can I do to remove the mozilla-build version?

---

### Post by witeshark17 on 2011-03-03
Is this not the same issue interfering with removing Ubuntuzilla build of Firefox so that the new repo versions can install rightly?

---

### Post by Karlchen on 2011-03-07
Hello, GnuSense.

Based on what nanotube's instructions are [in a similar Firefox related (un)installation issue](http://ubuntuforums.org/showpost.php?p=10055289&postcount=23), I assume that removing the interfering diversion before launching the uninstallation might help. > sudo rm -rf /usr/bin/seamonkey
sudo dpkg-divert --package seamonkey-mozilla-build --remove --divert /usr/bin/seamonkey.ubuntu --rename /usr/bin/seamonkey Next launch the uninstallation of Ubuntuzilla SeaMonkey > sudo apt-get check
sudo apt-get remove seamonkey-mozilla-build If the uninstallation is successfull rename seamonkey.ubuntu back to its original name provided the original Ubuntu SeaMonkey software is present on your system. > sudo mv /usr/bin/seamonkey.ubuntu /usr/bin/seamonkeyHTH,
Karl

---

### Post by GnuSense on 2011-03-08
Thanks, I'll give it a try the next time I boot the system.

---

