---
title: "Cannot connect to Samba share (4.1.11) from Windows 10"
date: 2015-09-06
forum: Server Platforms
---

### Post by pangel on 2015-09-06
Hi! 

I have a Samba server version 4.1.11 running on Ubuntu Server 14.04. I cannot connect from Windows 10 (but I can from Windows 7).

The server and the clients are not on the same LAN.

The error message given by Windows is that the server is online but not responding. However the Samba logs say otherwise.

I have attached the logs for a failed connection attempt from Windows 10, and those for a successful attempt from Windows 7 (for comparison).

Briefly, unlike the successful attempt, the failed one starts with:

```
switch message SMBnegprot (pid 2855) conn 0x0
```

then it requests a number of different protocols before selecting [FONT=Courier New]SMB2_FF[/FONT]. Then, after some security negotiations, it switches to protocol [FONT=Courier New]SMB 2.???[/FONT], then [FONT=Courier New]SMB3_00[/FONT], followed by:

```
Server exit (NT_STATUS_END_OF_FILE).
```

The successful attempt selects protocol [FONT=Courier New]SMB2_10[/FONT] from the start, but this protocol is not even requested by Windows 10.

Here are the logs :

Failed attempt (from Windows 10)
[http://pastebin.com/M0xmBuY3](http://pastebin.com/M0xmBuY3)

Successful attempt (from Windows 7)
[http://pastebin.com/jF8VzaiA](http://pastebin.com/jF8VzaiA)

smb.conf
[http://pastebin.com/CWYqGuBa](http://pastebin.com/CWYqGuBa)

---

### Post by volkswagner on 2015-09-06
I see some unconventional share configuration.

What is "<user>" accomplishing? Is this to force samba to accept any username?

I suggest setting up a simple share without "<user>" to see if you can connect? 

Are you trying to connect to a specific share, or the root of the server?

You say the Window's 10 machine is on a separate LAN. Do windows 7 machines also connect from the same separate LAN?

---

### Post by pangel on 2015-09-06
Hi, thanks for your answer! <user> is just a stand-in for the actual user name. The configuration file has some username where <user> is written here.

I am trying to connect to a specific share (I think). I write \\<url>\<folder> when I try to connect from Windows.

Yes, Windows 7 and Windows 10 are on the same LAN.

This solved my problem:

> Windows 10 will try to negotiate SMB3_11, which Samba4 doesn't yet support
except in the current 4.3 release candidate. I suspect for now disabling
SMB2/3 on the Windows 10 client is your best, if not ideal, option.

Instructions for doing.this can be found
here: [https://support.microsoft.com/en-us/kb/2696547](https://support.microsoft.com/en-us/kb/2696547)

[https://lists.samba.org/archive/samba/2015-September/193886.html](https://lists.samba.org/archive/samba/2015-September/193886.html)

---

### Post by Morbius1 on 2015-09-12
> Windows 10 will try to negotiate SMB3_11, which Samba4 doesn't yet support
except in the current 4.3 release candidate. I suspect for now disabling
SMB2/3 on the Windows 10 client is your best, if not ideal, option.
Hm......

If I connect to my Xubuntu machine from Windows 10:
[ATTACH=CONFIG]264376[/ATTACH]
I can get access to it's samba shares without any adjustment to Windows:
[ATTACH=CONFIG]264377[/ATTACH]
It even works using the legacy netbios mechanism:
[ATTACH=CONFIG]264378[/ATTACH]
Now I'm running samba 4.1.6 in Xubuntu. And this is a home lan where everyone is in the same network. But if there was an incompatibility in SMB levels I would think it would impact me as well. Maybe it's a Samba 4.1.11 issue.

---

### Post by LeeJaeJun on 2016-01-28
How did you solve it?
I tried the link you mentioned but ended up fail.

I disabled SMB2/3 according to the instruction.

1. Open the **PowerShell** with admin authority and type

```
[COLOR=#000000][FONT=Segoe UI]Set-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters" SMB2 -Type DWORD -Value 0 -Force
[/FONT][/COLOR]
```

2. Open the **command line window** with admin authority and type

```
[COLOR=#000000][FONT=Segoe UI]sc.exe config lanmanworkstation depend= bowser/mrxsmb10/nsi[/FONT][/COLOR]
[COLOR=#000000][FONT=Segoe UI]sc.exe config mrxsmb20 start= disabled[/FONT][/COLOR]
```

Every command did not show any errors. 
So I restarted my PC to see nothing changed.
It still doesn't work.

Can you explain more details what you have done?

Thanks.

ps.
I'm using **Windows10** and **Ubuntu14.04** with **samba 4.1.6**.

---

### Post by Morbius1 on 2016-01-28
>  I'm using **Windows10** and **Ubuntu14.04** with **samba 4.1.6**.         
I suspect that you should probably start a new topic since it has nothing to do with this one.

And you might want to describe the issue you are having. The Win10 machine can't see the Ubuntu machine or you can't connect to the Ubuntu machine? There&#8217;s a problem with Win10 "discovering" the Linux machine. It has no problem connecting to one - you just have to ask for it by name.

Besides the whole premise of this doesn't make sense to me:
> Windows 10 will try to negotiate SMB3_11, which Samba4 doesn't yet support
except in the current 4.3 release candidate. I suspect for now disabling
SMB2/3 on the Windows 10 client is your best, if not ideal, option.

I just connected to a Xubuntu 14.04 samba share from WIn10. If I look at the connection parameters on WIn10 this is what I see:
```
Windows PowerShell
Copyright (C) 2015 Microsoft Corporation. All rights reserved.

PS C:\WINDOWS\system32> Get-SmbConnection | Select ServerName,ShareName,Dialect

ServerName ShareName Dialect
----------   ---------  -------
xub1404.local  Downloads   3.0

```

There&#8217;s no doubt that Win10 starts with SMB3_11 but both it and the samba server can auto-negotiate this.

---

