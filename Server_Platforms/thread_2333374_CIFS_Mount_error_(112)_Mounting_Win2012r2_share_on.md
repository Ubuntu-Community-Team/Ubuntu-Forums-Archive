---
title: "CIFS Mount error (112) Mounting Win2012r2 share on Ubuntu 16.04"
date: 2016-08-09
forum: Server Platforms
---

### Post by AshleyTayles on 2016-08-09
Hi guys!

I've spent the last 4 hours tearing my hair out over something I have done in some capacity over and over again for years: mounting windows shares.

I'm attempting to use fstab to do this, here is my fstab line:

```
//192.168.1.201/netstore  /netstore  cifs  guest,uid=1000,iocharset=utf8  0  0
```

So pretty simple right? I have a folder in root called "netstore", there's no password on the samba share.

The Windows 2012R2 box is a domain controller for a domain. A windows 7 box NOT on the domain can open the share with no problem.

Some troubleshooting now:

Both port 445 and 139 are open on the Windows 2012 box for the ubuntu box:

```
ashley@tayles-cs:~$ telnet 192.168.1.201 445
Trying 192.168.1.201...
Connected to 192.168.1.201.
Escape character is '^]'.

ashley@tayles-cs:~$ telnet 192.168.1.201 139
Trying 192.168.1.201...
Connected to 192.168.1.201.
Escape character is '^]'.


```

And to make doubly sure there is full connectivity:

```
ashley@tayles-cs:~$ ping 192.168.1.201
PING 192.168.1.201 (192.168.1.201) 56(84) bytes of data.
64 bytes from 192.168.1.201: icmp_seq=1 ttl=128 time=0.178 ms
64 bytes from 192.168.1.201: icmp_seq=2 ttl=128 time=0.181 ms
64 bytes from 192.168.1.201: icmp_seq=3 ttl=128 time=0.125 ms
64 bytes from 192.168.1.201: icmp_seq=4 ttl=128 time=0.173 ms
64 bytes from 192.168.1.201: icmp_seq=5 ttl=128 time=0.165 ms
64 bytes from 192.168.1.201: icmp_seq=6 ttl=128 time=0.141 ms
^C
--- 192.168.1.201 ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 4997ms
rtt min/avg/max/mdev = 0.125/0.160/0.181/0.024 ms

```

I've tried using the NETBIOS AND the FQDN in the FSTAB with exactly the same results.

Trying to connect using smbclient:

```
ashley@tayles-cs:~$ smbclient //192.168.1.201/netstore -U guest
WARNING: The "syslog" option is deprecated
Enter guest's password:
protocol negotiation failed: NT_STATUS_CONNECTION_RESET

ashley@tayles-cs:~$ smbclient //192.168.1.201/netstore -U ashley
WARNING: The "syslog" option is deprecated
Enter ashley's password:
protocol negotiation failed: NT_STATUS_CONNECTION_RESET

ashley@tayles-cs:~$ sudo smbclient //192.168.1.201/netstore -U ashley
WARNING: The "syslog" option is deprecated
Enter ashley's password:
protocol negotiation failed: NT_STATUS_CONNECTION_RESET



```

I've checked the Window Event Viewer and there are NO attempted connections from the Ubuntu box. If I use my windows 7 pc and try to connect using bad creds, I get failed attempted logs, so I would expect the same if Ubuntu was failing to connect?

Anyone got any ideas? I have run out of things to Google lol. If you want more output just shout! :)

Thanks,
Ashley

---

### Post by Graham_Willis on 2016-08-09
Why not to check the logs at the Ubuntu side? I think **/var/log/samba/log.smbd** is most likely to have useful information, but check everything what you have in this directory. Try using the option **-m** of **smbclient**. Try manipulating samba server log level (the variable **log level **in the section **global** of **/etc/samba/smb.conf**). Also useful might be the option **-d** of **smbclient.**

---

### Post by AshleyTayles on 2016-08-09
> **Graham_Willis said:**
> Why not to check the logs at the Ubuntu side? I think **/var/log/samba/log.smbd** is most likely to have useful information, but check everything what you have in this directory. Try using the option **-m** of **smbclient**. Try manipulating samba server log level (the variable **log level **in the section **global** of **/etc/samba/smb.conf**). Also useful might be the option **-d** of **smbclient.**

Perfection! Thanks :D

I'll list what I just did.


```
smbclient //192.168.1.201/netstore -d 6
```

This clearly showed that a TCP connection was being created but being almost instantly disconnected.

The "-m" handle for smbclient is not one I have heard of and the man page wasn't much help. I did some digging and this actually changes the version of SMB being used. I thought what the hell and whacked in "SMB2" after -m and BOOM it worked!

I added "vers=2.1" to my fstab arguments and a quick sudo mount -a later I had a mounted share!

Thanks @Graham_Willis !!!

Time to find out why the Windows server wasn't playing ball with SMB3 :(

---

### Post by gianluigi.zanettini on 2017-03-11
Hello Ashley,
I found this topic Googling for the same issue! I've a mixed Ubuntu+Win10+Android network and all the Linux-based clients were unable to access a specific Win10 PC (the same clients had no problem connecting to other Win10 PCs). -m SMB2 did the trick for me too! Thanks for suggesting it!

Have you found out the cause of the SMB3 failure?

---

### Post by gianluigi.zanettini on 2017-03-11
OK, found the cause. For me, the failing Win10 PC [had SMB1 removed]("https://support.microsoft.com/en-us/help/2696547/how-to-enable-and-disable-smbv1,-smbv2,-and-smbv3-in-windows-vista,-windows-server-2008,-windows-7,-windows-server-2008-r2,-windows-8,-and-windows-server-2012"):

[IMG]https://kbdevstorage1.blob.core.windows.net/asset-blobs/4014206_en_1[/IMG]

Reinstalling it fixed the problem.

---

### Post by Morbius1 on 2017-03-12
Windows 10 may be another issue regarding SMB3 since if I use a cifs mount instead of a nautilus / smbclient mount ( smb1 ) and specify smb3 ( vers=3.0 ) It registers it as a SMB3 access on the Windows side:
> PS C:\WINDOWS\system32> Get-SmbSession | Select Dialect,ClientComputerName,ClientUserName

[COLOR=#0000cd]**Dialect**[/COLOR] ClientComputerName ClientUserName
-------     ------------------                --------------
[COLOR=#0000cd]**3.0**[/COLOR]        ****192.168.0.4                         **********VWIN10\smbuser
The problem with altering smb.conf so that Nautilus or smbclient itself can access via SMB3 ( or even SMB2 ) ...
```
client max protocol = SMB3
```
... Is that will disable network browsing entirely in Linux which seems like a bug to me but .....

You can access the Windows share with that parameter in place in smb.conf but you have to address the share explicitly by name.

---

### Post by heman22union on 2018-02-12
> **gianluigi.zanettini said:**
> OK, found the cause. For me, the failing Win10 PC [had SMB1 removed]("https://support.microsoft.com/en-us/help/2696547/how-to-enable-and-disable-smbv1,-smbv2,-and-smbv3-in-windows-vista,-windows-server-2008,-windows-7,-windows-server-2008-r2,-windows-8,-and-windows-server-2012"):

[IMG]https://kbdevstorage1.blob.core.windows.net/asset-blobs/4014206_en_1[/IMG]

Reinstalling it fixed the problem.


You should remove the SMBv1 that you enabled on Windows 10 immediately. After removal use [this ]("https://support.microsoft.com/en-us/help/2696547/how-to-detect-enable-and-disable-smbv1-smbv2-and-smbv3-in-windows-and")resource to determine if your Windows Client/Server is using SMBv2 or SMBv3 now. SMBv1 is how the WannaCry ransomware was spread. It is not an appropriate fix and should not be posted for users to enable. 

[https://tech.slashdot.org/story/17/06/17/001209/microsoft-will-disable-wannacry-attack-vector-smbv1-starting-this-fall](https://tech.slashdot.org/story/17/06/17/001209/microsoft-will-disable-wannacry-attack-vector-smbv1-starting-this-fall)

You should make the suggested changes to the smb.conf file to use SMBv2 or SMBv3 as an appropriate fix.

Have a good day!

---

### Post by gianluigi.zanettini on 2018-03-14
@heman22union: I appreciate your concern, but please note that my post is ONE YEAR old. Since then I removed SMB1 and enabled SMB2 like this:

[IMG]https://turbolab.it/immagini/med/risolto-ubuntu-cartelle-condivise-rete-windows-10-errore-connessione-scaduta-argomento-non-valido-11142.img[/IMG]

---

### Post by Mythological on 2018-04-07
Just a quick note for anyone who stumbles across this thread because your "sudo mount.cifs ..." has stopped working (it returns "mount error(112): Host is down" even though you can ping the host with no problem).  In my case I was using a command of the form:

sudo mount.cifs //192.168.1.X/WindowsShare /home/myuser/Share/ -o user=*****,password=*****,uid=1000,gid=1000

The information in this thread helped me discover that what I needed to do was add **vers=3.0** to the options, like this

sudo mount.cifs //192.168.1.X/WindowsShare /home/myuser/Share/ -o user=*****,password=*****,**vers=3.0,**uid=1000,gid=1000

If 3.0 doesn't work, try 2.0.

---

### Post by wildmanne39 on 2018-04-07
Old thread back to sleep!

---

