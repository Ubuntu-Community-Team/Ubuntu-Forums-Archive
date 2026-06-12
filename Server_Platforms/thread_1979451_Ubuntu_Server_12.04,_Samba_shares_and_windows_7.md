---
title: "Ubuntu Server 12.04, Samba shares and windows 7"
date: 2012-05-13
forum: Server Platforms
---

### Post by adwsys on 2012-05-13
Hi All,

I have a Windows 7 (64 bit) development machine, on which I set up a new Ubuntu 12.04 Server (32-bit) installation in a VirtualBox VM & included LAMP, SSH & Samba in the installation.  When complete I configured Samba and shared the /var/www folder for read/write access.  However I could not access the Ubuntu 12 server from my windows 7 PC, but I had full read/write access from a Windows XP system on the same network.

I searched the internet for a solution, but couldn't find anything conclusive, however I did find some posts where others had similar problems, and one reference which said that the version of Samba in 12.04 was different than in earlier Ubuntu releases.

I was getting nowhere with 12.04, so I set up another VM and installed Ubuntu Server 11.10, this time from a pre-built VB image and configured it the same way as the previous 12.04 server.  Same user, same passwords, same shares, same everything as far as possibel, and it works swimmingly.  I have full R/W access from both Windows 7 and Windows XP, and can map drives and copy files to & from the sahres without any problems.

I'm fairly new to Linux/Ubuntu, and I don't know how to troubleshoot this type of problem, so I'd be grateful for anyones comments & help.

ADW

---

### Post by nikozzzzzz on 2012-05-13
Could you post your /etc/samba/smb.conf files  both from 12.04 and 11.10 ? 
You can do this with 
cat /etc/samba/smb.conf
--------------------------------
[http://ubuntuforums.org/showthread.php?t=1979297](http://ubuntuforums.org/showthread.php?t=1979297)

This looks like a similar problem. There is access to Samba shares from XP , but there is none from windows 7.
---------------------------------
Ive got an idea. Maybe it will solve your problem. Find out , what samba version is installed on your 11.10 and install exactly this version on 12.04 ( dont forget to backup+remove your config file from newer Samba before installing the old version) . You can use the command to find out currently installed smb version:  smbstatus
----------------------------------
Looks like MS changed the way W7 connects to external shares after WinXP. And looks like the Samba dev team did something wrong in their new release.Or maybe we are just missing something.)
--
Sorry for my bad english

---

### Post by ian dobson on 2012-05-13
Hi,

Windows7 uses smb2 which samba doesn't support. Thare's a registry option in windows that allows you to accept/send smb packets. When I find the link I'll post it here.

Regards
Ian Dobson

---

### Post by CharlesA on 2012-05-13
> **ian dobson said:**
> Hi,

Windows7 uses smb2 which samba doesn't support. Thare's a registry option in windows that allows you to accept/send smb packets. When I find the link I'll post it here.

Regards
Ian Dobson
You shouldn't have to make any changes to the registry.

I'm using 12.04 with the default smb.conf file and I can connect fine from my Win7 box.

Posting the smb.conf file would be the first step to see why it isn't working.

---

### Post by ian dobson on 2012-05-14
Hi,

Have a look here [http://www.sevenforums.com/network-sharing/213344-samba-share-not-accessible-windows-7-client.html](http://www.sevenforums.com/network-sharing/213344-samba-share-not-accessible-windows-7-client.html)

Regards
Ian Dobson

---

### Post by Morbius1 on 2012-05-14
> In the Local Group Policy Editor, go to:
 
 [COLOR=red]Local  Computer Policy->Computer Configuration->Windows  Settings->Security Settings->Local Policies->Security Options[/COLOR]
 
Find the policy:
 
 [COLOR=red]Microsoft network client: Digitally sign communications (always)[/COLOR]
 
If this is enabled, change it to **Disabled**. Be sure and restart  your machine for the change to take effect! Pressing the "Apply" button  in the Policy Editor after the change is made is not sufficient...Under no circumstances should anyone sober even think about messing with any Windows7 default security setting. This isn't Win98. Win7 is Windows2000 on steroids with a goofy DE. Whatever the issue is with samba it can be resolved another way.

---

### Post by LHammonds on 2012-05-14
Actually, the very 1st place I would look is at your VirtualBox settings.  Your Network Adapter needs to be set to Bridged Adapter if you want communication between your guest and host to go both ways.

---

### Post by CharlesA on 2012-05-14
> **Morbius1 said:**
> Under no circumstances should anyone sober even think about messing with any Windows7 default security setting. This isn't Win98. Win7 is Windows2000 on steroids with a goofy DE. Whatever the issue is with samba it can be resolved another way.

Agreed. Of the 5 machines I have Win7 on at home, I have had no issues connecting to Samba when I was using 10.04 or 12.04. The only thing I needed to do was set up a local DNS server to resolve hostnames to ip addresses. Broadcasts would work fine though.

> **LHammonds said:**
> Actually, the very 1st place I would look is at your VirtualBox settings.  Your Network Adapter needs to be set to Bridged Adapter if you want communication between your guest and host to go both ways.

That would be my bet too - if it is a prebuilt VM, it might have to have it's settings tweaked before it will work.

---

### Post by adwsys on 2012-05-14
Hi All,

Thanks for the swift replies.

The versions of Samba are:
 - 11.10 : Samba version 3.5.11
 - 12.04 : Samba version 3.6.3

Both /etc/samba/smb.conf files are identical (attached)

The configuration of the VM's are identical & the network is set to Bridged mode.

I can quite happily ping both servers using either their IP addresses or their machine hostnames (imaginatively 'ubuntu11' & 'ubuntu12').

I think that this is definately a Samba issue, so I'll maybe try downgrading the version to 3.5.11 in the 12.o4 server & see what happens.

ADW

---

### Post by Morbius1 on 2012-05-15
Any chance that /var/www is set to 0750 or 770? 

You might want to see if the samba client on the 12.04 machine can see the samba server on the same machine by running the following command:
```
smbtree
```If your lucky it will throw an error message if it finds something wrong.

---

### Post by arturmodz on 2012-05-23
Try this:
[http://ask.brothersoft.com/how-to-fix-windows-7-system-error-1231-network-location-problem-208243.html](http://ask.brothersoft.com/how-to-fix-windows-7-system-error-1231-network-location-problem-208243.html)

---

### Post by LHammonds on 2012-05-23
@adwsys, this is [how I have configured my 12.04 servers]("http://ubuntuforums.org/showpost.php?p=11951847&postcount=5") so my Windows 7 PC can write files to the server.

The differences between yours and my config files are the following:

```
username map = /etc/samba/smbusers
public = yes
guest ok = no
writable = yes
directory mask = 0777

```

Comment out those lines and see if you can access (and create files).

If not, then check your /var/www ownership and permissions for discrepancies....or create a /srv/samba/share folder and test there to avoid messing with your www files-n-folders.

Once you have it working, then move on from there.

It will work, you just have to figure out what you are doing that is preventing from working.

---

