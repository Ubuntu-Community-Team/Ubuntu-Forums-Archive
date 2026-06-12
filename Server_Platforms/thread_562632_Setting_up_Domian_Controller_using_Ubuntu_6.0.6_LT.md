---
title: "Setting up Domian Controller using Ubuntu 6.0.6 LTS"
date: 2007-09-29
forum: Server Platforms
---

### Post by s.s.swapnil on 2007-09-29
I'm very new to Ububtu environment. I've planned to setup Ubuntu 6.0.6 domain controller same as Windows 2000/2003 domain controller. I have both the installer CDs of Ubuntu 6.0.6 Server & Client as well. I have following questions regarding the Same ....

1. I have planned to install my server as File / Printer / Database server for all of my 15 clients, who are already running Ununtu 6.0.6 desktop edition. As I'm quite familier with Windows environment, & aware that windows member servers needs to promoted to domain controller manually by issuing DCPROMO command. Is the same kind of thing is required in case of Ubuntu servers as well ?

2. Are Open Directory Services could be considered as Active Directory Services under Windows environment ???

3. Is there any GUI tool for managing users / rights / security over my intra network ??

4. If LAMP is install, are there any chances of loosing GUI on ubuntu server (I came across it ling time). If yes what are the steps to setup the GUI on ubuntu server from command line ??

5. How to Create / Manage the Login Scripts and user profiles for client systems running Ubuntu 6.0.6 desktop edition ??


Expecting soom feedback AEAP [:)]

Thanks in advance,

S.S.Swapnil

---

### Post by koenn on 2007-09-29
A combination of Kerberos, (Open)LDAP and Samba can produce similar functionality  as Microsoft's Active DIrectory. 
The links in this thread should get you started.
[http://ubuntuforums.org/showthread.php?t=561597](http://ubuntuforums.org/showthread.php?t=561597)

For some AD features (GPO/User and Computer Configuration,  softwre deployment, ...) you'll have to add additional sollutions. 

Personally, I'm not a big fan of attempts to immitate MS sollutions on a Linux platform. It has the same flaws as expecting Linux desktop applications to be drop-in replacements for Windows apps.
IT soolutions should be based on an analysis of the problem at hand. If it turns out that Kerberos , LDAP and windows-compatible file sharing are the sollution, so be it, but in that case your analysis will help you to  set them up so that they actually solve a problem, rather than configure them to be behave the same as MS AD.

---

### Post by rennen01 on 2007-09-29
As far as installing a GUI on Server edition

```
sudo apt-get install ubuntu-desktop
```

---

