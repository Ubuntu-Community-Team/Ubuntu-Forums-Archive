---
title: "XP Delayed Write Failed"
date: 2010-02-02
forum: Server Platforms
---

### Post by Pioden on 2010-02-02
Hi folks,

We have six file servers, all virtualised on OpenVZ, all identical in set-up. Even the hardware of the host servers are pretty much identical. Host kernels are 2.6.18-12-fza-amd64 (all hosts) and the fileserver OS is Ubuntu 8.04 (all fileservers).

The problem is that the users of one of the fileservers are reporting Windows 'Delayed Write Failed' messages. Windows (XP Pro) is almost certainly not the issue - every user in our college is using identical 'imaged' Windows installations. 

Can anyone suggest what might be wrong? User_beancounters for OpenVZ checks out fine - no reported resource shortages.  I checked MTU size -  a suggestion on another thread - they're all identical on all hosts. The affected fileserver is in many ways one of our 'quieter' ones - which confuses the issue even more!!

All suggestions appreciated.
 
TIA

Huw

---

### Post by Pioden on 2010-02-03
Any suggestions?

---

### Post by capscrew on 2010-02-03
> **Pioden said:**
> Hi folks,

We have six file servers, all virtualised on OpenVZ, all identical in set-up. Even the hardware of the host servers are pretty much identical. Host kernels are 2.6.18-12-fza-amd64 (all hosts) and the fileserver OS is Ubuntu 8.04 (all fileservers).

*"...pretty much identical"* But not **exactly identical**.  See [**_[COLOR="Navy"]here[/COLOR]_**]("http://support.microsoft.com/kb/330174").  In this instance it could be as simple as a bad or incorrect HDD cable.

> 

The problem is that the users of one of the fileservers are reporting Windows 'Delayed Write Failed' messages. Windows (XP Pro) is almost certainly not the issue - every user in our college is using identical 'imaged' Windows installations.
So are you saying that only a few XP hosts are reporting this error or are all XP hosts using a particular fileserver?  It would be nice to know the ENTIRE error code (including the status number) as there is more that one Delayed Write error.> 

Can anyone suggest what might be wrong? User_beancounters for OpenVZ checks out fine - no reported resource shortages.  I checked MTU size -  a suggestion on another thread - they're all identical on all hosts. The affected fileserver is in many ways one of our 'quieter' ones - which confuses the issue even more!!
...
The root problem seems to be timing delays interacting with the XP OS.  It would seem to me that this could be either the hardware of the server or XP itself.  See [**_[COLOR="Navy"]here (needs an MS Patch) [/COLOR]_**]("http://support.microsoft.com/kb/321733")and [**_[COLOR="Navy"]here (at the bottom)[/COLOR]_**]("http://www.itags.org/msdn/803433/") for other thoughts.

---

