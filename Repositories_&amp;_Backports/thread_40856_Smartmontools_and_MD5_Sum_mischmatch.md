---
title: "Smartmontools and MD5 Sum mischmatch"
date: 2005-06-10
forum: Repositories &amp; Backports
---

### Post by Teo on 2005-06-10
Hi,
I can't install smartmontools (I'm using Synaptic) - I've got this error message:

```
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/smartmontools/smartmontools_5.32-2ubuntu1_i386.deb
  MD5Sum mismatch
```
I've used this link to configure my sources.list
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
What should I do?  :?

---

### Post by Seth on 2005-06-10
[QUOTE=Teo]Hi,
I can't install smartmontools (I'm using Synaptic) - I've got this error message:

```
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/smartmontools/smartmontools_5.32-2ubuntu1_i386.deb
  MD5Sum mismatch
```
I've used this link to configure my sources.list
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
What should I do?  :?[/QUOTE]
 A lot of packages including gedit and kdeartwork are showing mismatches. Something has gone wrong after the US archive went down.

---

### Post by Teo on 2005-06-10
[QUOTE=Seth]A lot of packages including gedit and kdeartwork are showing mismatches. Something has gone wrong after the US archive went down.[/QUOTE]
So there's only one way: wait in peace :)

---

### Post by psoleko on 2005-06-10
Getting md5sum mismatch errors on alot of packages xfce and kde stuff included. Bleh, figures as I had no plans tongiht. :(

---

### Post by rcmn on 2005-06-10
i guess i won't install firefox tonight .But i thought kunbuntu and ubuntu had it by default ??!!

---

### Post by psoleko on 2005-06-10
Firefox is in both by default, if you are looking for Firefox 1.04 it is only in backports, although the security updates have been patched into the default 1.02 by the Ubuntu Devs.

---

### Post by Kazriko on 2005-07-10
I fixed the MD5Sum problem on my system by switching to the ca repositories instead of the us ones.

---

