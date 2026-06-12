---
title: "LIO ISCSI Server Targetcli missing commands and files"
date: 2014-09-04
forum: Server Platforms
---

### Post by gorm-oppermann on 2014-09-04
Hi i have installet a LIO ISCSI Ubuntu 14.04 Server and iam using Targetcli to set iscsi up.

I cant find the file [COLOR=#545454][FONT=arial]/etc/target/[/FONT][/COLOR][COLOR=#545454][FONT=arial]**saveconfig**[/FONT][/COLOR][COLOR=#545454][FONT=arial].[/FONT][/COLOR][COLOR=#545454][FONT=arial][B]json ? 
typing [/B][/FONT][/COLOR]saveconfig in targetcli works but clearconfig do not work ?

Because clearconfig doesn't work i have tried to delete all entry's in targetcli but something must be hidden somewhere be-course now i cant create new portals.

/iscsi/iqn.20...tpgt1/portals> create
Using default IP port 3260
Automatically selected IP address 192.168.122.237.
Invalid argument
/iscsi/iqn.20...tpgt1/portals> ls
o- portals .................................................................................. [0 Portals]
/iscsi/iqn.20...tpgt1/portals> 


thanks in advance for any help

---

### Post by WattAJ on 2014-10-12
> **gorm-oppermann said:**
> ...
/iscsi/iqn.20...tpgt1/portals> create
Using default IP port 3260
Automatically selected IP address 192.168.122.237.
Invalid argument
/iscsi/iqn.20...tpgt1/portals> ls
o- portals .................................................................................. [0 Portals]
/iscsi/iqn.20...tpgt1/portals> 
...
I have the same problem, and I'm interested to see if there is a solution.
Good-luck.

---

### Post by WattAJ on 2014-10-12
Update...

I trashed my original set-up, and started from scratch with a clean installation of 14.04, and targetcli.
This has worked[sup]*[/sup] and I now have an iscsi connection to my home server from my windows 7 laptop.
No errors were encountered.

I *think* that the errors above *may* have been as a result of having iscsi-target already installed on the machine, and having tried to get this to work first, before trying targetcli. [Winfried Maus's blog]("http://www.wmaus.net/?p=1387") suggests that iscsi-target doesn't work, and I would still be bashing away with iscsi-target if I had not found his post; thanks Winfried, really very much appreciated.



[sup]* I say *worked*, but this is a little bit misleading. Yes, I can access cds and dvds on this remote drive, but the 'eject' instruction from the Windows 7 machine doesn't appear to have an effect on the server's DVD drive... I can live with this minor irritation whilst I investigate further. ;)[/sup]

---

### Post by WattAJ on 2014-10-21
> **WattAJ said:**
> ...
* I say *worked*, but this is a little bit misleading. Yes, I can access cds and dvds on this remote drive, but the 'eject' instruction from the Windows 7 machine doesn't appear to have an effect on the server's DVD drive... I can live with this minor irritation whilst I investigate further. ;)
Just a quick update to close off this path:

I was able to consistently access, and eject the drive tray, for my server's DVD drive from my Windows 7 laptop until the server had accessed the drive itself (e.g. mount, ls, unmount). The laptop was unable to eject the drive tray from that point onwards. Only rebooting the server would resolve this issue.

Having been able to access/use the drive as a pscsi backstore under targetcli I tried to set it up as an iblock backstore, but this failed. The guys over on the [targetcli development mail group]("http://www.spinics.net/lists/target-devel/msg07807.html") were incredibly helpful in identifying why this was happening (thanks guys; very much appreciated), but, sadly, it was not possible to set up the iblock backstore, and the pscsi backstore isn't going to be a long-term solution for me.

I have removed targetcli for the time being, and I no-longer have external access to this drive.

---

