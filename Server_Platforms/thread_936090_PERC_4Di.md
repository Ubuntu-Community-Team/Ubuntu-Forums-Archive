---
title: "PERC 4/Di"
date: 2008-10-02
forum: Server Platforms
---

### Post by csb1227 on 2008-10-02
Has anybody had success installing Ubuntu Server on a Dell PowerEdge 2600 with the PERC 4/Di controller card?  I want to make sure it will work before I buy a computer with that card in it for my office.

Thanks

---

### Post by oneloveamaru on 2008-10-06
It will install/work with no problems. I have installed Ubuntu and Debian on a range of Dell servers from Perc 2 to to Perc 5 with no problems, ever. From 2650's to 2950's.

The only time I see people having a problem installing linux, is on a new RAID card, that needs newer drivers and the installation does not have it. Perc 4's have been around for a few years now, there shouldn't be a distro out there that doesn't support it.

---

### Post by tlianza on 2012-05-02
> **oneloveamaru said:**
> It will install/work with no problems. I have installed Ubuntu and Debian on a range of Dell servers from Perc 2 to to Perc 5 with no problems, ever. From 2650's to 2950's.

The only time I see people having a problem installing linux, is on a new RAID card, that needs newer drivers and the installation does not have it. Perc 4's have been around for a few years now, there shouldn't be a distro out there that doesn't support it.

I can't get it to install on the latest version of Ubuntu... though I'd love to believe it installs with no problems, the forums indicate otherwise, mostly with stranded people who give up:

[http://ubuntuforums.org/showthread.php?t=1912901](http://ubuntuforums.org/showthread.php?t=1912901)
[http://ubuntuforums.org/showthread.php?t=1699199](http://ubuntuforums.org/showthread.php?t=1699199)

---

### Post by LHammonds on 2012-05-02
Well, if you cannot get the drivers to work with Ubuntu, you could try to virtualize it.

See if you can get VMware's ESXi to install on the Dell Server.  If so, you can then create a virtual server for Ubuntu and configure it in such a way that it consumes all the resources...like a single OS server.

LHammonds

---

### Post by SeijiSensei on 2012-05-03
Another alternative is to try [CentOS 6]("http://www.centos.org/modules/tinycontent/index.php?id=30") instead.

---

