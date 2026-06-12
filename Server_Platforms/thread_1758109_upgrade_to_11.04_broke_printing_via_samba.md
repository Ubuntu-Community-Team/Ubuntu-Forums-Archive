---
title: "upgrade to 11.04 broke printing via samba"
date: 2011-05-14
forum: Server Platforms
---

### Post by odi1984 on 2011-05-14
Hi,

I use my server running 64-bit Ubuntu server as a printer server for several Windows clients. Ever since the upgrade to 11.04 printing does not work any more.
The printer works fine locally, but printing via samba doesn't.
The samba configuration was not changed during the upgrade and has always worked, and I see no reason why it shouldn't work any more. 

The problem is really strange. There aren't any errors or warnings in the log files (cups or samba) and the printer shows up in the network and the Windows machines can connect to it. However, when trying to print something, nothing happens. The job never shows up in the cups job queue. 
The Windows machines seem to send the job correctly, no error messages there either. 

Global and printer section of smb.conf:
```

[global]
        server string = server
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        username map = /etc/samba/users.map
        unix password sync = Yes
        log level = 3
        syslog = 2
        log file = /var/log/samba/log.%m
        max log size = 1000
        smb ports = 139
        name resolve order = lmhosts host wins bcast
        printcap name = cups
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
        printcap = cups
        printing = cups

[printers]
        comment = All Printers
        path = /var/spool/samba
        guest ok = Yes
        printable = Yes
        use client driver = Yes
        browseable = No

[HP_DESKJET_990C]
        comment = HP DESKJET 990C
        path = /var/spool/samba
        read only = No
        guest ok = Yes
        printable = Yes
        printer name = HP_DESKJET_990C
        oplocks = No
        share modes = No

```

I'm not posting the log files since they only contain the "started" lines. 

I'm really stuck and any help would be appreciated!

btw: I read about the bug that cups and samba start in the wrong order - that's not it.

---

### Post by eggi-j on 2011-05-16
Hi,

I've got a similar problem after upgrade from 10.10 to 11.04. Samba and cups worked before, and none of the config files were changed. However, after the upgrade none of them worked. I can print test page from cups admin, but the shared Samba printer doesn't list on Windows. The cups printer is listed both on Mac and Ubuntu clients, but when I print to the cups printer the printer "goes offline". The jobs never arrive to cups, it seems. Printing from lpr works.

I'm totally stuck on this one...

Hoping that it's a matter of updating to a fixed version. :)

---

### Post by Leena Mulye on 2011-05-20
Hi all,

Any updates/solutions for above problem? I am also facing similar issues after upgrading our Ubuntu server from version 8.04 to 10.04 (Lucid).

I did upgrade SAMBA, CUPS, printer drivers. BTW we are using Canon MF4100. Before upgrade it was working fine.
After upgrade shared drives are working fine(files are shared over network), but network printer does not print. It is connected to server using USB and from server it prints (no problems with printer) but doesnot print from other machines on network (which also are on Ubuntu 10.04).

when I send document for printing from client computer, it sends but I cannot find it in cups and nothing happens after that no error msg and no printing....
how to troubleshoot such issues? any clues....


Thanks,
Leena

---

### Post by kpholmes on 2011-05-24
ya this seems to be happening to quite a bit of people. me including. if i find any info or get it working ill post it here but im thinking of downgrading just for this.

---

### Post by eggi-j on 2011-05-27
I found out that the printer was available through samba if you specified the url manually. Even though the printer was set to browsable = yes it actually loads as browsable = no. I can't set it to "yes" although for me it's not that important.

I also learned that I must specify the printer on the local CUPS server as well, in order for CUPS to work...

Does anyone else have the problem with browsable = yes (but actually "no")?

---

### Post by capscrew on 2011-05-27
> **eggi-j said:**
> I found out that the printer was available through samba if you specified the url manually. Even though the printer was set to browsable = yes it actually loads as browsable = no. I can't set it to "yes" although for me it's not that important.

I also learned that I must specify the printer on the local CUPS server as well, in order for CUPS to work...

Does anyone else have the problem with browsable = yes (but actually "no")?

I do not use Samba for printing in my network.  All my printers are networked.  But I have a theory as to what is happening. I think this is a nameservices problem.  Either the daemon ***nmbd ***is not running or you don't have local LAN DNS configured.

The daemon *nbmd * converts hostnames to NetBIOS names and is the critical component in network browsing.  Without it running the parameter *browseable = yes* dosn't work because you can't find any shares by the Browse List created by the Local Master Browser.  What do you get when you use this command in the terminal```
smbtree
```Post the output back here. 

To see if the *nmbd and smbd *daemons are running try this at the terminal```
ps -ef | grep mbd
```

Post the this output back here too.

---

