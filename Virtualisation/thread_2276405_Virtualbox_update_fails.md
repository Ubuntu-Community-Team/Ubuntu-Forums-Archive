---
title: "Virtualbox update fails"
date: 2015-05-02
forum: Virtualisation
---

### Post by x-terry on 2015-05-02
Section of install log showing errors:

(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 544960 files and directories currently installed.)
Preparing to unpack .../virtualbox-4.3_4.3.26-98988-Ubuntu-raring_amd64 (2).deb ...
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
dpkg: error processing archive /home/terry/Downloads/virtualbox-4.3_4.3.26-98988-Ubuntu-raring_amd64 (2).deb (--install):
 subprocess new pre-removal script returned error exit status 1
Errors were encountered while processing:
 /home/terry/Downloads/virtualbox-4.3_4.3.26-98988-Ubuntu-raring_amd64 (2).deb

Any ideas?

---

### Post by Elfy on 2015-05-02
Appears you are trying to install something in 13.04 - this release went End of Life January 2014.

Think about either trying to upgrade [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

or installing a supported version.

---

### Post by x-terry on 2015-05-02
Thanks for that, After running several attempts to uninstall the old version, I finally got it sorted then reinstalled the latest.

---

