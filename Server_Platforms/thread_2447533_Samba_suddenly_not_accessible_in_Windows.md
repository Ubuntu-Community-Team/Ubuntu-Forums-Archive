---
title: "Samba suddenly not accessible in Windows"
date: 2020-07-20
forum: Server Platforms
---

### Post by jrmymllr on 2020-07-20
SOLVED. My /tmp permissions got changed. Glad that's done.

I'm using Ubuntu Server 16.04 and Samba 4.3.11. I've had Samba set up for years and haven't had a problem...until today. 

I'm not sure what happened as I didn't change anything I'm aware of. No Samba changes for sure. It started out with one share not working on Windows 7. 
 I disconnected the 3 shares on my Windows computer and tried to remap them by going to "\\192.168.0.3", the server's IP, and it says:

[B]Windows cannot access \\192.168.0.3

You do not have permission to access \\192.168.0.3. Contact your network administrator to request access.

[/B]It won't even show me the shares. Just this error box.

This is where it gets weird. I can access all 3 shares just fine on two Fire TVs running Kodi, a music player connected to the LAN, and another Windows 7 computer.

If I try smbclient on the server itself, as root:

```

root@SERVERNAME:/# smbclient -L 192.168.0.3 -U myusername
WARNING: The "syslog" option is deprecated
Enter myusernames's password:
Domain=[WORKGROUP] OS=[Windows 6.1] Server=[Samba 4.3.11-Ubuntu]


        Sharename       Type      Comment
        ---------       ----      -------
Error returning browse list: NT_STATUS_ACCESS_DENIED
Domain=[WORKGROUP] OS=[Windows 6.1] Server=[Samba 4.3.11-Ubuntu]


        Server               Comment
        ---------            -------


        Workgroup            Master
        ---------            -------




```


This is driving me totally bonkers. I'm not a Samba expert, but WTF is going on? Why everything but this one Windows 7 computer can access this? 

 EDIT: I now see a Windows 10 computer also can't access.

I've tried restarting smbd and nmbd, and of course Windows 7. Restarting Ubuntu actually fixed it for a day, but now the problem is back again. I set Samba log level = 3, but there was nothing interesting in the /var/log/samba log file.


Share section of smb.conf:

```

[RW]
path = /NetworkShare/backup
browseable = yes
valid users = myusername
read only = no
hide unreadable = yes
veto files = AV/Camera/
veto files = AV/mp3/


[R]
path = /NetworkShare/backup/AV
browsable = yes
read only = yes
hide unreadable = yes
guest ok = yes
guest only = yes


[ADMIN]
path = /NetworkShare/backup/AV
browseable = yes
valid users = myusername
read only = no
hide unreadable = yes


[TEMP]
path = /X_data/TempShare
browseable = yes
valid users = myusername
read only = no
hide unreadable = yes

```

Relevant directories at /
```

drwxr-xr-x   4 myusername root  4096 Feb  1 10:54 NetworkShare
drwxr-xr-x  10 myusername root   205 Jul 20 15:56 X_data

```

Relevant directory at /X_data
```

drwxr-xr-x  6 myusername myusername       4096 Jul 20 15:30 TempShare

```

---

### Post by TheFu on 2020-07-21
> **jrmymllr said:**
> 
Rebooted machine. Solved. <shrug>

"Have you tried turning it off and on again?"

I've been having a similar issue from a Windows box the last few weeks after cleaning up a few old unused interfaces in Windows.  Only that 1 client wasn't working. Other systems worked - both Windows and Linux clients all worked.  I'd checked firewalls, drivers, networking and watched logs. The connection request from that single client wasn't getting to the samba server.  
Finally, asked for help from my LUG on Sunday. All of them asked "Have you tried turning it off and on again?" - which I had not and laughed.  I just don't think that way.  Rebooted - what a pain - had to wait about 5 minutes for Windows to come up and all the stupid add-on drivers for scanners, printers, video cards, to finally finish. Tried to open Exploder, nothing. Tried again.  About 2 minutes after that, 8 Explorer windows opened ... 

and the Samba connection that had been working for 10+ yrs worked again.  Maddening.

---

