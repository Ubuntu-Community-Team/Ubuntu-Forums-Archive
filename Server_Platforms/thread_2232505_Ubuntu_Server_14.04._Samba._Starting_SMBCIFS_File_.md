---
title: "Ubuntu Server 14.04. Samba. Starting SMB/CIFS File Server [fail]"
date: 2014-07-02
forum: Server Platforms
---

### Post by Roswebnet on 2014-07-02
[FONT=Calibri][SIZE=3][COLOR=#000000]Hieveryone,[/COLOR][/SIZE][/FONT]
[FONT=Calibri][SIZE=3][COLOR=#000000]I am facingstrange problem with Samba AD on Ubuntu Server 14.04. On system reboot, I amgetting at the end of boot this message:[/COLOR][/SIZE][/FONT]
[FONT=Calibri][SIZE=3][COLOR=#000000] ```
 * Starting SMB/CIFS File Server[74G[[31mfail[39;49m]
```[/COLOR][/SIZE][/FONT]
[FONT=Calibri][SIZE=3][COLOR=#000000]However,tests shows that everything works fine:[/COLOR][/SIZE][/FONT]
[FONT=Calibri][SIZE=3][COLOR=#000000]```

root@srv01:~# kinit [EMAIL="administrator@DOT.LAN"]administrator@DOT.LAN[/EMAIL]
Password for [EMAIL="administrator@DOT.LAN"]administrator@DOT.LAN[/EMAIL]:
Warning: Your password will expire in 41 days on Wed 13 Aug 2014 04:22:38 PM CEST
root@srv01:~# klist -e
Ticket cache: FILE:/tmp/krb5cc_0
Default principal: [EMAIL="administrator@DOT.LAN"]administrator@DOT.LAN[/EMAIL]
Valid starting       Expires              Service principal
07/02/2014 16:45:36  07/03/2014 02:45:36  [EMAIL="krbtgt/DOT.LAN@DOT.LAN"]krbtgt/DOT.LAN@DOT.LAN[/EMAIL]
        renew until 07/03/2014 16:45:32, Etype (skey, tkt): aes256-cts-hmac-sha1-96, aes256-cts-hmac-sha1-96
root@srv01:~# smbclient -L localhost -U%
Domain=[DOT] OS=[Unix] Server=[Samba 4.1.6-Ubuntu]
        Sharename       Type      Comment
        ---------       ----      -------
        netlogon        Disk
        sysvol          Disk
        Profiles        Disk      Users Profile Directories
        Home            Disk      Users Homes Directories
        printers        Printer   All Printers
        print$          Disk      Printer Drivers
        ODMPrinter      Printer
        shares          Disk      Global share for all users
        IPC$            IPC       IPC Service
Domain=[DOT] OS=[Unix] Server=[Samba 4.1.6-Ubuntu]
        Server               Comment
        ---------            -------
        Workgroup            Master
        ---------            -------
root@srv01:~# smbclient //localhost/netlogon -UAdministrator%'Pa77w0rd' -c 'ls'
Domain=[DOT] OS=[Unix] Server=[Samba 4.1.6-Ubuntu]
  .                                   D        0  Wed Jul  2 16:22:33 2014
  ..                                  D        0  Wed Jul  2 16:22:40 2014
                48643 blocks of size 524288. 42365 blocks available
root@srv01:~# samba-tool domain level show
Domain and forest function level for domain 'DC=dot,DC=lan'
Forest function level: (Windows) 2008 R2
Domain function level: (Windows) 2008 R2
Lowest function level of a DC: (Windows) 2008 R2


``` 
[/COLOR][/SIZE][/FONT] 
[FONT=Calibri][SIZE=3][COLOR=#000000]Moreover,Windows 8.1 client can join domain without any problems.

My provision: 
```
samba-tool domain provision \--realm=DOT.LAN \--domain=DOT \--adminpass='Pa77w0rd' \--dns-backend=BIND9_DLZ \--server-role=dc \--use-xattr=yes \--use-rfc2307  \--function-level=2008_R2 \--use-ntvfs
```
[/COLOR][/SIZE][/FONT][FONT=Calibri][SIZE=3][COLOR=#000000]
All requested operations with bind9.9.5 and samba 4.1.6, I did according this wiki:
[https://wiki.samba.org/index.php/DNS_Backend_BIND](https://wiki.samba.org/index.php/DNS_Backend_BIND)[/COLOR][/SIZE][/FONT]
[FONT=Calibri][SIZE=3][COLOR=#000000]See mylogs in attachments.[/COLOR][/SIZE][/FONT]
[FONT=Calibri][SIZE=3][COLOR=#000000] [ATTACH]254396[/ATTACH][/COLOR][/SIZE][/FONT]
[FONT=Calibri][SIZE=3][COLOR=#000000]Is there any problem? How to solve such strange boot behaviour?[/COLOR][/SIZE][/FONT]
[FONT=Calibri][SIZE=3][COLOR=#000000]Thank you.[/COLOR][/SIZE][/FONT]

---

