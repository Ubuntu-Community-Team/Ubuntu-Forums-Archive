---
title: "How to verify ubuntu-14.04.1-desktop-amd64, I can not find the checksum"
date: 2014-09-04
forum: Security
---

### Post by varunaub on 2014-09-04
How to verify ubuntu-14.04.1-desktop-amd64, The below information was obtained through Kaspersky Internet Security 2014's Application Advisor option
 **File**

   Name:[ubuntu-14.04.1-desktop-amd64.iso]("http://whitelisting.kaspersky.com/advisor#search/119CB63B48C9A18F31F417F09655EFBD") Type:ISO: Disk imageSize:981 MBVersion:— MD5:[119CB63B48C9A18F31F417F09655EFBD]("http://whitelisting.kaspersky.com/advisor#search/119CB63B48C9A18F31F417F09655EFBD")SHA1:[096DBA6EE83D784009EDDEC7F28287AB66091F66]("http://whitelisting.kaspersky.com/advisor#search/096DBA6EE83D784009EDDEC7F28287AB66091F66")Added:7/30/2014 4:07:00 AM

---

### Post by sammiev on 2014-09-04
The program [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") is designed to verify data integrity using the MD5.

---

### Post by varunaub on 2014-09-04
I have not installed Ubuntu yet, I have Windows, 
I have calculated md5 checksum using Kaspersky But I am not able to find the checksum at the Ubuntu download page.Where can I find it wellnot here [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes), not for [SIZE=2]**[B]ubuntu-14.04.1-desktop-amd64**[/B][/SIZE]

---

### Post by sammiev on 2014-09-04
The checksums are [here]("http://releases.ubuntu.com/14.04.1/").

119cb63b48c9a18f31f417f09655efbd *ubuntu-14.04.1-desktop-amd64.iso

---

### Post by varunaub on 2014-09-04
thanks sammiev

---

### Post by varunaub on 2014-09-04
Whay is the the link [http://releases.ubuntu.com/14.04.1/](http://releases.ubuntu.com/14.04.1/) you listed is not displayed in the main download page?

---

### Post by sammiev on 2014-09-04
Yes it seems it hasn't been updated.

---

### Post by Doug S on 2014-09-05
> **varunaub said:**
> Where can I find it wellnot here [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes), not for [SIZE=2]**[B]ubuntu-14.04.1-desktop-amd64**[/B][/SIZE]That page is rarely up to date, and this time there are 8 bug reports, so far, about it.

For obvious reasons that page is restricted from the normal anybody can edit it scenario. The proposal is to delete the contents and just point to the real location to get the Hashes.

Reference:
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/1349715](https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/1349715)

---

