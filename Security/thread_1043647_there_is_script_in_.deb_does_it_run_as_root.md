---
title: "there is script in .deb? does it run as root?"
date: 2009-01-18
forum: Security
---

### Post by q.dinar on 2009-01-18
there is script in .deb, is not it? does it run as root?
then there is some debs not from ubuntu repositories, for example of flash player. to install it installation runs with root privileges. can script in .deb file harm system?

---

### Post by Nepherte on 2009-01-18
it is correct deb packages need root privileges to install. That is the very reason you should only install packages from trustworthy sources, the ubuntu repositories for instance.

---

### Post by q.dinar on 2009-01-19
when i installed flash player from ubuntu repository i have seen in terminal in synaptic's window that it redirected to other site (adobe or macromedia) and downloaded the package from there.

---

### Post by hyper_ch on 2009-01-19
this happened because that software is proprietary and may not be distributed by third parties without permission.

---

### Post by q.dinar on 2009-01-19
does ubuntu team check every new version and provide checksum to synaptic/apt/aptitude ?

---

### Post by cdenley on 2009-01-19
> **q.dinar said:**
> does ubuntu team check every new version and provide checksum to synaptic/apt/aptitude ?

Whenever an ubuntu package downloads software from a third party, it does use checksums to verify the downloaded file(s), as far as I know. This was a problem with flash when adobe decided to provide a newer version in the same location as the previous version. The newer version did not match the checksum in the ubuntu package, and flash became impossible to install.

---

### Post by q.dinar on 2009-01-19
that is good.
are deb's installer script of them checked, does anybody know?
> This was a problem ...
what is now? no more they check or repository do not redirect to new version until new version is checked?

---

### Post by cdenley on 2009-01-19
> **q.dinar said:**
> that is good.
are deb's installer script of them checked, does anybody know?

what is now? no more they check or repository do not redirect to new version until new version is checked?

The problem was of course fixed when ubuntu released a new package for flash with the checksum of the new version of flash. When the checksum doesn't match, the installer will give an error, and the third-party software will not be installed.

How other packages may react to third parties releasing new versions depends how the third party maintains their download links. Assuming all the packages work the same, an invalid package will never be installed, though.

If you're concerned about the ubuntu packaging being corrupted, there is no need to worry.
[https://help.ubuntu.com/community/SecureApt](https://help.ubuntu.com/community/SecureApt)
[http://wiki.debian.org/SecureApt](http://wiki.debian.org/SecureApt)

---

### Post by q.dinar on 2009-01-23
if i download a new version deb package like flash, opera, wine, how can i look through (see) installer script? as i remember i opened deb file by clicking and did not see where is that script.

---

### Post by cdenley on 2009-01-23
Open the deb with the "Archive Manager", open control.tar.gz, open "./postinst".

---

