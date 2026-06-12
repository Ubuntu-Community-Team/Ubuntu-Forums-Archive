---
title: "Dell Open Manage"
date: 2010-06-25
forum: Server Platforms
---

### Post by KLStringer on 2010-06-25
I have a Dell R610 PowerEdge and installed the Open Manage software but can't find any information on how to use it with Ubuntu. Anyone have any good links on how to use it with Ubuntu? 

Thanks in advance.:-k

---

### Post by KLStringer on 2010-06-28
I found this page, figured I'd link it here in case anyone else needed it.

[http://support.dell.com/support/edocs/software/svradmin/](http://support.dell.com/support/edocs/software/svradmin/)

---

### Post by KLStringer on 2010-06-28
Quick simple question, off said R610 PE I've hung a MD1000 that  currently only has 2 2TB HDD's in RAID 1. When I add more dives into the  MD1000 can I expand the array without having to destroy it and  rebuilding? If I can how would I go about it?

Thanks in advance.

---

### Post by KLStringer on 2010-07-02
Found the answer below if anyone else is looking

[http://en.community.dell.com/support-forums/storage/f/1216/t/19304321.aspx#19590406](http://en.community.dell.com/support-forums/storage/f/1216/t/19304321.aspx#19590406)

[http://en.community.dell.com/support-forums/servers/f/906/t/18745664.aspx](http://en.community.dell.com/support-forums/servers/f/906/t/18745664.aspx)

---

### Post by KLStringer on 2010-07-02
Following 

[https://subtrac.sara.nl/oss/omsa_2_deb/wiki/FAQ](https://subtrac.sara.nl/oss/omsa_2_deb/wiki/FAQ)

[http://sadsoftware.blogspot.com/2008/08/installing-dell-omsa-and-snmp-in-ubuntu.html](http://sadsoftware.blogspot.com/2008/08/installing-dell-omsa-and-snmp-in-ubuntu.html)

and 

[http://www.ubergeek.co.uk/blog/2008/05/dell-openmanage-on-linux-debian/](http://www.ubergeek.co.uk/blog/2008/05/dell-openmanage-on-linux-debian/)

I've got OMSA installed and running, when I log into the webserver it says that the 6/iR RAID controller driver is out of date. I found

[http://support.dell.com/support/downloads/download.aspx?c=us&cs=08&l=en&s=bsdr&releaseid=R211003&SystemID=pwe_r610&servicetag=5VTKRL1&os=RH52&osl=en&deviceid=13856&devlib=0&typecnt=0&vercnt=2&catid=-1&impid=-1&formatcnt=0&libid=46&typeid=-1&dateid=-1&formatid=-1&source=-1&fileid=296683](http://support.dell.com/support/downloads/download.aspx?c=us&cs=08&l=en&s=bsdr&releaseid=R211003&SystemID=pwe_r610&servicetag=5VTKRL1&os=RH52&osl=en&deviceid=13856&devlib=0&typecnt=0&vercnt=2&catid=-1&impid=-1&formatcnt=0&libid=46&typeid=-1&dateid=-1&formatid=-1&source=-1&fileid=296683)

that is a newer version. I used alien to convert it, then installed, and rebooted. Now when I log into OMSA it's still saying that the driver is out of data. When I do a modinfo megaraid_sas it shows that the version is the newer version.

I'm a little confused why they both report different versions and how do I tell which one is correct, OMSA or modinfo.

---

### Post by Vegan on 2010-07-02
I use Webmin which is fine for my needs, its easier to use too. And its free.

---

### Post by tgalati4 on 2010-07-02
It's probably a bug in OMSA.  When you boot your server, go into the RAID BIOS, (probably Control-S) and see what version number shows up.  Write it down and compare it to what OMSA says.  I would guess the version in your firmware is what you are running regardless of what OMSA says.  There's probably an OMSA or RAID config file in /etc or in /opt/omsa where the firmware values are copied.  You can probably decipher the OMSA PHP code to determine where it gets the version numbers from.  If you know PHP, you can fix it as well.

OMSA is nice because it can drill down into the BIOS NVRAM (all 200 MB worth in my Poweredge 1750) to capture server health data and other events not captured by the kernel or syslogd.  I'm surprised that it works out-of-the-box being ported from Red Hat rpm to deb package with little modification.

---

