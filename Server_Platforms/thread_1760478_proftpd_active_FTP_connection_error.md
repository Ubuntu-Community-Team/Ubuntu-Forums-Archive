---
title: "proftpd active FTP connection error"
date: 2011-05-17
forum: Server Platforms
---

### Post by TBhX£2760R8@nK7§r on 2011-05-17
I'm trying to set up a FTP server so Team Fortress 2(a game) can upload replay files to a FTP server and the clients can download them automatically.

I installed proftpd, then uninstalled at error messages and followed this guide: [http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)
This is the full from an attempted connection with WinSCP.

```
 2011-05-17 00:17:41.892 --------------------------------------------------------------------------
. 2011-05-17 00:17:41.892 WinSCP Version 4.2.9 (Build 938) (OS 6.1.7601 Service Pack 1)
. 2011-05-17 00:17:41.893 Login time: Tuesday, May 17, 2011 00:17:41
. 2011-05-17 00:17:41.893 --------------------------------------------------------------------------
. 2011-05-17 00:17:41.893 Session name: replay@scuzzball.serveftp.com
. 2011-05-17 00:17:41.893 Host name: scuzzball.serveftp.com (Port: 65521)
. 2011-05-17 00:17:41.893 User name: replay (Password: Yes, Key file: No)
. 2011-05-17 00:17:41.893 Tunnel: No
. 2011-05-17 00:17:41.893 Transfer Protocol: FTP
. 2011-05-17 00:17:41.893 Ping type: C, Ping interval: 30 sec; Timeout: 15 sec
. 2011-05-17 00:17:41.893 Proxy: none
. 2011-05-17 00:17:41.893 FTP: FTPS: None; Passive: No [Force IP: No]
. 2011-05-17 00:17:41.893 Local directory: default, Remote directory: home, Update: No, Cache: Yes
. 2011-05-17 00:17:41.894 Cache directory changes: Yes, Permanent: Yes
. 2011-05-17 00:17:41.894 DST mode: 1
. 2011-05-17 00:17:41.894 --------------------------------------------------------------------------
. 2011-05-17 00:17:41.993 Connecting to scuzzball.serveftp.com:65521 ...
. 2011-05-17 00:17:42.063 Connected with scuzzball.serveftp.com:65521. Waiting for welcome message...
< 2011-05-17 00:17:42.378 220 ProFTPD 1.3.2c Server (TF2Replay) [192.168.1.5]
> 2011-05-17 00:17:42.378 USER replay
< 2011-05-17 00:17:42.416 331 Password required for replay
> 2011-05-17 00:17:42.416 PASS ******
< 2011-05-17 00:17:42.561 230 User replay logged in
> 2011-05-17 00:17:42.561 SYST
< 2011-05-17 00:17:42.602 215 UNIX Type: L8
> 2011-05-17 00:17:42.602 FEAT
< 2011-05-17 00:17:42.642 211-Features:
< 2011-05-17 00:17:42.642  MDTM
< 2011-05-17 00:17:42.642  MFMT
< 2011-05-17 00:17:42.642  UTF8
< 2011-05-17 00:17:42.642  MFF modify;UNIX.group;UNIX.mode;
< 2011-05-17 00:17:42.642  MLST modify*;perm*;size*;type*;unique*;UNIX.group*;UNIX.mode*;UNIX.owner*;
< 2011-05-17 00:17:42.642  REST STREAM
< 2011-05-17 00:17:42.642  LANG en-US.UTF-8*
< 2011-05-17 00:17:42.642  SIZE
< 2011-05-17 00:17:42.643 211 End
> 2011-05-17 00:17:42.643 OPTS UTF8 ON
< 2011-05-17 00:17:42.688 200 UTF8 set to on
. 2011-05-17 00:17:42.693 Connected
. 2011-05-17 00:17:42.694 --------------------------------------------------------------------------
. 2011-05-17 00:17:42.694 Using FTP protocol.
. 2011-05-17 00:17:42.694 Doing startup conversation with host.
> 2011-05-17 00:17:42.698 PWD
< 2011-05-17 00:17:42.741 257 "/" is the current directory
. 2011-05-17 00:17:42.744 Getting current directory name.
. 2011-05-17 00:17:42.746 Retrieving directory listing...
> 2011-05-17 00:17:42.746 TYPE A
< 2011-05-17 00:17:42.781 200 Type set to A
> 2011-05-17 00:17:42.786 PORT 192,168,1,2,126,234
< 2011-05-17 00:17:42.861 500 Illegal PORT command
. 2011-05-17 00:17:42.862 Could not retrieve directory listing
. 2011-05-17 00:17:42.864 Retrieving directory listing...
> 2011-05-17 00:17:42.864 TYPE A
< 2011-05-17 00:17:42.904 200 Type set to A
> 2011-05-17 00:17:42.909 PORT 192,168,1,2,126,236
< 2011-05-17 00:17:42.948 500 Illegal PORT command
. 2011-05-17 00:17:42.949 Could not retrieve directory listing
* 2011-05-17 00:17:42.949 (ECommand) Error listing directory '/'.
* 2011-05-17 00:17:42.949 Could not retrieve directory listing
* 2011-05-17 00:17:42.949 Illegal PORT command
. 2011-05-17 00:17:44.844 Startup conversation with host finished.
. 2011-05-17 00:17:48.111 Disconnected from server

```


I would prefer to use SFTP, as that already works, but sadly TF2 does not support any connection other than FTP.

Most people how have the problem with "Illegal PORT command" just switch to passive connections, but it's hard for me to open more ports as it's a friend running the server.

Thank you for any and all help, especially if I'm just missing some small thing(again).

Scuzzball.

---

