---
title: "vsftpd error"
date: 2011-08-03
forum: Server Platforms
---

### Post by fingerslip on 2011-08-03
Hello!

I am running ubuntu 11.04 x64  with vsftp v3.2.2

log:
```
[T] Connecting to ftp://fingerslip:***@94.23.254.218
[T] Connecting to ftp://fingerslip:***@pony.feralhosting.com
[T] Resolving pony.feralhosting.com...
[T] pony.feralhosting.com => 85.17.27.67
[T] Connecting to 94.23.254.218:21
[T] Connecting to 85.17.27.67:21
[T] 220 (vsFTPd 2.3.2)
[T] USER fingerslip
[T] 220 ProFTPD 1.3.1 Server (FTP) [::ffff:85.17.27.67]
[T] USER fingerslip
[T] 331 Please specify the password.
[T] PASS (hidden)
[T] 331 Password required for fingerslip
[T] PASS (hidden)
[T] 230 User fingerslip logged in
[T] 230 Login successful.
[T] SYST
[T] SYST
[T] 215 UNIX Type: L8
[T] TYPE A
[T] 215 UNIX Type: L8
[T] TYPE A
[T] 200 Type set to A
[T] 200 Switching to ASCII mode.
[T] REST 1
[T] REST 1
[T] 501 REST: Resuming transfers not allowed in ASCII mode
[T] REST 0
[T] 350 Restart position accepted (1).
[T] REST 0
[T] 350 Restarting at 0. Send STORE or RETRIEVE to initiate transfer
[T] 350 Restart position accepted (0).
[T] FEAT
[T] FEAT
[T] 211-Features:
[T]  LANG en
[T] 211-Features:
[T]  MDTM
[T]  EPRT
[T]  UTF8
[T]  EPSV
[T]  REST STREAM
[T]  MDTM
[T]  SIZE
[T]  PASV
[T] 211 End
[T] OPTS UTF8 ON
[T]  REST STREAM
[T]  SIZE
[T]  TVFS
[T]  UTF8
[T] 211 End
[T] OPTS UTF8 ON
[T] 200 UTF8 set to on
[T] PWD
[T] 200 Always in UTF8 mode.
[T] PWD
[T] 257 "/media/sdk1/home/fingerslip" is the current directory
[T] 257 "/home/fingerslip"
[T] CWD /media/sdk1/home/fingerslip/
[T] 250 CWD command successful
[T] PWD
[T] 257 "/media/sdk1/home/fingerslip/" is the current directory
[T] PASV
[T] 227 Entering Passive Mode (85,17,27,67,165,180).
[T] Opening data connection IP: 85.17.27.67 PORT: 42420
[T] LIST
[T] 150 Opening ASCII mode data connection for file list
[T] 226 Transfer complete
[T] List Complete: 311 bytes in 0,05 seconds (6,62KB/s)
[T] CWD /home/fingerslip/downloads/
[T] 250 Directory successfully changed.
[T] PWD
[T] 257 "/home/fingerslip/downloads"
[T] PASV
[T] 227 Entering Passive Mode (94,23,254,218,7,209).
[T] Opening data connection IP: 94.23.254.218 PORT: 2001
[T] LIST
[T] 150 Here comes the directory listing.
[T] 226 Directory send OK.
[T] List Complete: 229 bytes in 0,05 seconds (4,87KB/s)
[T] TYPE I
[T] 200 Type set to I
[T] TYPE I
[T] 200 Switching to Binary mode.
[T] PASV
[T] 227 Entering Passive Mode (85,17,27,67,183,180).
[T] PORT 85,17,27,67,183,180
[T] 200 PORT command successful. Consider using PASV.
[T] STOR file_to_transfer.mp4
[COLOR=Red][T] 500 OOPS: vsf_sysutil_bind[/COLOR]
[i] Transfer Failed: file_to_transfer.mp4
[i] Failed 1 file(s) and Skipped 0 file(s)
[2] PASV
[1] PASV
[1] 227 Entering Passive Mode (85,17,27,67,149,47).
[1] Opening data connection IP: 85.17.27.67 PORT: 38191
[2] 227 Entering Passive Mode (94,23,254,218,7,208).
[2] Opening data connection IP: 94.23.254.218 PORT: 2000
[1] LIST
[2] LIST
[2] 150 Here comes the directory listing.
[1] 150 Opening ASCII mode data connection for file list
[2] 226 Directory send OK.
[2] List Complete: 329 bytes in 0,05 seconds (7,00KB/s)
[1] 226 Transfer complete
[1] List Complete: 311 bytes in 0,05 seconds (6,62KB/s)
[COLOR=Red][T] 500 OOPS: 500 OOPS: child died[/COLOR]
[T] Connecting to ftp://fingerslip:***@94.23.254.218
[T] Connecting to 94.23.254.218:21
[T] 220 (vsFTPd 2.3.2)
[T] USER fingerslip
[T] 331 Please specify the password.
[T] PASS (hidden)
[T] 230 Login successful.
[T] SYST
[T] 215 UNIX Type: L8
[T] TYPE A
[T] 200 Switching to ASCII mode.
[T] FEAT
[T] 211-Features:
[T]  EPRT
[T]  EPSV
[T]  MDTM
[T]  PASV
[T]  REST STREAM
[T]  SIZE
[T]  TVFS
[T]  UTF8
[T] 211 End
[T] OPTS UTF8 ON
[T] 200 Always in UTF8 mode.
[T] PWD
[T] 257 "/home/fingerslip"
```I get tese errors: [COLOR=Red][T] 500 OOPS: vsf_sysutil_bind and [/COLOR][COLOR=Red][T] 500 OOPS: 500 OOPS: child died

Edit: Solved installed another ftp server and worked..well
[/COLOR]

---

