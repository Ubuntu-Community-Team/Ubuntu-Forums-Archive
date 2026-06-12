---
title: "Samba"
date: 2010-09-16
forum: Server Platforms
---

### Post by WhiteElephant on 2010-09-16
I am wanting to setup an office network consisting of three computers and one server. We already have the equipment ready with Vista Business pre-installed on the computers. I want to be able to create a network which allows users to use any machine as this will reduce downtime should a machine break. Also I would like user's files to be held centrally on the server which makes backups easier.
 
The most important element here is data backup. As like most businesses we are moving away from paper and using the computers to store important records such as customer information. If this data were to be lost, the business would come to a complete halt.
 
I have been looking at the idea of installing a Microsoft Small Business Server as it would be nice to have centralised control of the machines. However the cost would be over £800 which can not be justified for three machines and five users. Therefore I am turning to Linux for a alternative solution. I have previously used CentOS and Ubuntu for home use but never really gained much knowledge or experience of either.
 
It is my understanding that Samba can act as a Primary Domain Controller, which if I'm not mistaken is where it handles the network logins and profiles. Is this correct?
 
I have come across many samba tutorials online but whats confusing is they are all different. Some of the tutorials involve using Kerberos and OpenLDAP. Do I need to learn about either of these? What do they do and what benefit will they bring?
 
Finally, I see Samba 4 is in development and is likely to bring a lot of new features which aren't available in Samba 3. Is this worth waiting for because I don't want to be upgrading everything again 6 months down the road?
 
Thanks for your support.

---

### Post by HermanAB on 2010-09-16
Howdy,

Yes you can use Samba, but you could save yourself a heckofalot of trouble by installing Windows Services for UNIX (free download from MS) on the Windows machines and then use a NFS server instead of Samba.

A NFS server has one, yes *one* line of configuration in one file.  Samba has hundreds of lines of configuration and the book is 2 inches thick.  You do the math.

---

### Post by dtech on 2010-09-16
I would not wait for samba 4. It is still under development and even when it is released I'd wait at least a year before using it in a production environment.

Samba can indeed act as a domain controller, OpenLDAP is the equivalent of Active-Directory (keeping information about your computers and/or users) and Kerberos provides authentication.

The suggestion from HermanAB isn't a bad one, but with NFS you will *only* be able to set up file shares for files/backups. You cannot store complete profiles as e.g. Samba can. You can even provide both to the same shares (because NFS is usually faster). But personally I'd view samba as neccesairy and NFS as supplementary.

As for your backups: I'd suggest a RAID-1 configuration for / and /home (seperate partitions). This is easy using linux software-raid. For backups you can use an external HD or extra internal HD.

---

### Post by WhiteElephant on 2010-09-16
Thanks for the advice up there.

The server has two 500gb drives but does not have a raid controller. I already have a backup script which will copy /home into /backup every week, and it will keep the last six weeks worth backups. Therefore I was thinking about having one whole drive just for /backup and leave the primary drive for /.

I will have a look into the NFS and the Windows Services for Unix. Im not exactly sure what the OpenLDAP does or even if I need it but Ill try to find "OpenLDAP for Dummies".

---

### Post by R.Bucky on 2010-09-16
If you have the option, install Ubuntu Server with soft RAID and a hot spare and then use an external backup. Call it extra insurance, but RAID is a much happier circumstance, especially for a business.

---

### Post by WhiteElephant on 2010-09-16
I have been having a think about the setup. If the server goes down then all the network will be offline for a few days until someone comes to repair it. Given that we only have a few computers and users would it be better to have these setup as stand-alone machines? Then I can use Samba or NFS for setting up some shared storage. Then the computers could be setup to backup weekly onto the server.

What would you recommend?

---

### Post by dtech on 2010-09-16
A (linux) server is quite stable once setup, only kernel-upgrades and distribution upgrades can cause serious problems. In my experience hardware failure, especially hard disk failure, is a much greater concern. As such, I would really advise software-raid-1.

---

### Post by WhiteElephant on 2010-09-16
I think I will setup Samba as a Primary Domain Controller to handle network logins & roaming profiles.
 
I have also looked into DropBox and its highly likely that I will be going down this route. I will share the /home/user's folder with the individual users so they can gain access to their files from home.
 
I will install Avast for Linux which I can setup on a cron job to do a daily scan on the /home/ directory.
 
The backup script I have would run weekly and copy the /home/ directory into /backup/, which is on a secondary drive. This script is also set to keep the last six previous backups just incase something is deleted or becomes corrupt. However if I use the software RAID 1 as you have suggested then there would be no need to use this script. What would happen if all the files on drive one became deleted, damaged or corrupt, wouldn't this means the backups files are also affected?

---

### Post by dtech on 2010-09-17
I don't see how all files on the primary drive would become corrupt at once. The only likely cause for this would be a RAID-0 setup in which one of the drives fails. Or a stolen root password and a malicious "hacker". In any case, I wouldn't worry about it.

---

### Post by WhiteElephant on 2010-09-17
Lets suppose a user edits a file or deletes it, that would also affect the backup. I think my idea of copying A to B once a week would be a better solution.
 
In regards to setting up a proxy server to filter bad content, I am thinking of using Squid with filters from URLBlacklist.com. There is also DansGuardian, SquidGuard. What would you recommend?

---

### Post by dtech on 2010-09-17
> **WhiteElephant said:**
> Lets suppose a user edits a file or deletes it, that would also affect the backup. I think my idea of copying A to B once a week would be a better solution.
 


Uhm, yes. That is the whole idea of a backup... What was your origional plan then?

> 
In regards to setting up a proxy server to filter bad content, I am thinking of using Squid with filters from URLBlacklist.com. There is also DansGuardian, SquidGuard. What would you recommend?


Squidguard is a static filtering that can use filters from e.g. URLBlacklist (it is much more advanced than the blacklisting in squid, which is too slow to implement a large set). I don't have experience with Dansguardian, but it seems to be a dynamic content filtering (e.g. like a virus scanner does)

---

### Post by WhiteElephant on 2010-09-17
I have a script which creates a backup of /home/ into /backup (on drive b). It will run on a weekly basis and keep the last six previous backups before overwriting them.

---

### Post by WhiteElephant on 2010-09-17
The endpoints will have their own security protection so the proxy will only be there as an extra layer of protection. I believe DansGuardian can filter MIME types and file types which will be useful for stoping executables from being downloaded.
 
Do you know if there is a cheap commercial alternative?

---

### Post by dtech on 2010-09-17
Why would you want a full-commercial alternative? DansGuardian only asks for a donation for commercial use, even though it is GPL. According to the GPL they are obliged to provide a download to the source, so they cannot force you too. Even so, they cannot force you to unless they include non-GPL (e.g. artwork) material.

---

### Post by WhiteElephant on 2010-09-17
The server will be using Comodo's Secure DNS which blocks malware at DNS level. If this fails, I would like to proxy to block malware by blocking potentially malicious file types. Plus, I believe DansGuardian can scan downloads using ClamAV?
 
I will be blocking:
```

.exe
.dll
.com
.bat
.scr
.vbs

```
This should prevent most malware unless its compressed, right? I can't block zip because most of our downloads are in zip format.
 
If the proxy fails to block malware it will then come down to the browser, which will have McAfee SiteAdvisor, or WOT. After that it comes down to McAfee Anti-Malware's scanning.

---

### Post by HermanAB on 2010-09-18
Howdy,

Note that you really don't need the LDAP crap (whichever brand) for less than 20 PCs.

---

### Post by dtech on 2010-09-18
> **WhiteElephant said:**
> The server will be using Comodo's Secure DNS which blocks malware at DNS level. If this fails, I would like to proxy to block malware by blocking potentially malicious file types. Plus, I believe DansGuardian can scan downloads using ClamAV?
 
I will be blocking:
```

.exe
.dll
.com
.bat
.scr
.vbs

```
This should prevent most malware unless its compressed, right? I can't block zip because most of our downloads are in zip format.
 

I would advise against blocking exe. exe is so common (heck, it is used for every windows program) that blocking it also blocks a lot of valid programs (e.g. installers)

---

### Post by WhiteElephant on 2010-09-18
All valid programs will already be installed.

I dont want people to be downloading installers, thats where it starts to go wrong.

---

### Post by dtech on 2010-09-18
Well its your call, but I personally think blocking exe's is not a good idea, especially since it can easily be circumvented by malware by downloading e.g. a zip file instead of an exe file; and thus blocks more valid downloads than malware downloads.

---

