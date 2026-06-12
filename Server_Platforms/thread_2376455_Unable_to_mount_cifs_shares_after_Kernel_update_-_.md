---
title: "Unable to mount cifs shares after Kernel update - [Work Around]"
date: 2017-11-02
forum: Server Platforms
---

### Post by prrawls2 on 2017-11-02
I updated my Ubuntu 16.04.3 LTS Server this morning with the new kernel (**4.4.0-98-generic #121-Ubuntu SMP**) and discovered that I could not mount my cifs Windows 2012 SMB share, stating an **Input/Output error** at the command line.


This was my /etc/fstab mount command.
```
//WindowsServer/share /mnt/share cifs vers=3.0,credentials=/root/.smbauth,iocharset=utf8,sec=ntlmssp,gid=0,uid=0,file_mode=0700,dir_mode=0600 0 0
```


It was throwing this error every time I tried to do a manual mount in my /var/log/syslog 
```
[  491.511144] CIFS VFS: validate protocol negotiate failed: -11
[  491.511369] CIFS VFS: cifs_mount failed w/return code = -5
```

On the Windows Server side it recorded the following.

**From: SMBServer Event Log** on my Windows 2012 R2 Server. (had been using SMB=3 tried SMB=3.02 in this example nither 3.0 or 3.02 worked.)
```
The server rejected an invalid negotiation request. Connection was terminated.


Client Name: \\192.168.0.32
Client Address: 192.168.0.32:39964
User Name: REMOVED
Session ID: 0x40055C000049
Expected Dialect: 0x302
Expected Capabilities: 0x57
Expected Security Mode: 0x1
Received Dialect: 0x0
Received Capabilities: 0x57
Received Security Mode: 0x1


Guidance:


This event indicates that a client is attempting to negotiate a second connection using a mismatched dialect or capabilities.
```

After seeing that it was not receiving the **Expected Dialect: 0x302**, instead it was getting **Received Dialect: 0x0**. I was surprised for sure, then I downgraded the command as show below to **SMB=2.1**, and it allowed the mount to work. Is there a bug somewhere on this? I've looked everywhere to see if anyone else is seeing this. Why is 3.02 or even 3.0 not being recognized? 


The "fix" was a downgrade in SMB version in the connection string.

```
//WindowsServer/share /mnt/share cifs vers=2.1,credentials=/root/.smbauth,iocharset=utf8,sec=ntlmssp,gid=0,uid=0,file_mode=0700,dir_mode=0600 0 0
```

---

### Post by LHammonds on 2017-11-02
Hmm....All of my Ubuntu Servers were recently updated to that version but I'm not getting errors when I mount my Win2012 backup share.

```
uname -a
4.4.0-98-generic #121-Ubuntu SMP Tue Oct 10 14:24:03 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
```

```
apt search samba
samba/xenial-updates,xenial-security,now 2:4.3.11+dfsg-0ubuntu0.16.04.11 amd64 [installed]
```

```
winver
Microsoft Windows Server 2012 R2 Datacenter, version 6.3 (Build 9600)
```

My scripts mount the server with a function call similar to this:
```
mount -t cifs //srv-backup/linux /mnt/srv-backup --options nouser,rw,nofail,noexec,credentials=/etc/cifspw
```

I just issued the command manually and verified it worked for me.

LHammonds

---

### Post by prrawls2 on 2017-11-02
Thanks man, yah I'm seriously scratching my head here on what happened... The Windows 2012 R2 server is unchanged, I patched it last week way before this... Glad to see it's just me, I have two Ubuntu servers that this occurred to. Weird!

I'm runnning...
samba-common/xenial-updates,xenial-updates,xenial-security,xenial-security,now 2:4.3.11+dfsg-0ubuntu0.16.04.11 all [installed,automatic]

---

### Post by jdjonsson on 2017-11-03
Well, I discovered this bug yesterday too, when my bacula server lost all access to the target volumes. I lost a night of backups figuring this out, and it took finding this thread. I changed fstab to explicitly define "vers=2.1" instead of "vers=3.0" which had been working. Without explicit definition, it defaults to version 1. 

I think this could become a big deal fairly soon, given that a lot of admins will have the same experience as me, and this is quite a breakdown in functionality. wonder if this has been reported to the cifs-utils devs?

---

### Post by yuljk2 on 2017-11-03
Exacltly the same issue here too - Ubuntu 16.04.03 with all updates connecting to 2012 R2 CIFS share via fstab.  Changing SMB version to 2.1 restores functionality, 3.0 no longer works

---

### Post by Morbius1 on 2017-11-04
@         prrawls2, when you have nothing else to do could you try an experiment:

Change **sec=****ntlmssp **to** sec=****ntlmsspi**
> //WindowsServer/share /mnt/share cifs vers=3.0,credentials=/root/.smbauth,iocharset=utf8,[COLOR=#0000cd]**sec=ntlmsspi**[/COLOR],gid=0,uid=0,file_mode=0700,dir_mode=0600 0 0
Source: [https://www.mail-archive.com/kernel-packages@lists.launchpad.net/msg256243.html](https://www.mail-archive.com/kernel-packages@lists.launchpad.net/msg256243.html)

*Side note: Version 4.13 of the Linux Kernel changed the default smb dialect from smb1 to smb3 for cifs so you should be able to drop the vers=3.0 entirely from your fstab statement.*
[COLOR=#0000cd]**Edit**: I have no idea why I added that "Side note" at the end. Clearly kernel 4.13 > kernel 4.4. Sorry about that.[/COLOR]

---

### Post by yuljk2 on 2017-11-04
I tried adding **sec=[B]ntlmsspi**[/B] in my fstab - however I received '[FONT=arial, sans-serif][SIZE=2][COLOR=#6a6a6a]Unknown error 524' when issuing mount -a.  If I include vers=3.0 the drive mounts successfully.[/COLOR][/SIZE][/FONT]

---

### Post by prrawls2 on 2017-11-09
i was able to add the sec=ntlmsspi and dropped the ver out of the connection string, and all is working as expected!  Thanks Morbius1 for pointing me in the right direction!

---

### Post by zohaskins on 2017-11-12
I was knocking my head against the wall, but adding [COLOR=#292F34][FONT=verdana]sec=ntlmsspi seems to have done the trick.[/FONT][/COLOR]

---

