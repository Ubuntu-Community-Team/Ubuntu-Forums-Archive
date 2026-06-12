---
title: "Odd vsftpd issue"
date: 2011-10-19
forum: Server Platforms
---

### Post by Vadtec on 2011-10-19
Greetings all,

I'm running 10.04LTS on a VPS, and I'm having the most odd issue with vsftpd. I also noticed this on a Debian VPS, but thought it was just cause that VPS was overloaded.

Quick stats:

Ubuntu 10.04LTS 64-bit (Linux vps 2.6.32-28-server #55-Ubuntu SMP Mon Jan 10 23:57:16 UTC 2011 x86_64 GNU/Linux) running on a Xen host

vsftpd 2.2.2
Package: vsftpd
Versions: 
2.2.2-3ubuntu6.2 (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_lucid-updates_main_binary-amd64_Packages) (/var/lib/dpkg/status)

I've run vsftpd on CentOS in the past, and never encountered what I'm about to describe.

Basically, when I connect to the ftp server and start uploading, 10-15 files will transfer in proper order (quickly, little delay between each, etc). Then, all of a sudden, things grind to a halt. A random transfer will all of a sudden appear to "hang" and it takes exactly two minutes for it to time out, at which point it skips the file.

Here is an example of what is happening:
```

[15:57:35] [R] SIZE drink.png
[15:57:35] [R] 550 Could not get file size.
[15:57:35] [R] PASV
[15:57:36] [R] 227 Entering Passive Mode (255,255,255,255,4,0).
[15:57:36] [R] Opening data connection IP: 255.255.255.255 PORT: 1024
[15:57:36] [R] STOR drink.png
[15:57:36] [R] 150 Ok to send data.
[15:59:36] [R] Transfer Failed!
[15:59:36] [R] Connection lost: the.remote.server
[15:59:36] Transferred 0 Files (0 bytes) in 2 minutes 5 seconds (0.0 KB/s)
[15:59:36] 1 File Skipped
[15:59:38] [R] Attempting to Reconnect.
[15:59:38] [R] Connecting to the.remote.server -> DNS=the.remote.server IP=255.255.255.255 PORT=21 (attempt # 1)
[15:59:39] [R] Connected to the.remote.server
[15:59:39] [R] 220 (vsFTPd 2.2.2)
[15:59:39] [R] USER vadtec
[15:59:39] [R] 331 Please specify the password.
[15:59:39] [R] PASS (hidden)
[15:59:40] [R] 230 Login successful.
[15:59:40] [R] SYST
[15:59:41] [R] 215 UNIX Type: L8
[15:59:41] [R] FEAT
[15:59:41] [R] 211-Features:
[15:59:41] [R]  EPRT
[15:59:41] [R]  EPSV
[15:59:41] [R]  MDTM
[15:59:41] [R]  PASV
[15:59:42] [R]  REST STREAM
[15:59:42] [R]  SIZE
[15:59:42] [R]  TVFS
[15:59:42] [R]  UTF8
[15:59:42] [R] 211 End
[15:59:42] [R] PWD
[15:59:42] [R] 257 "/the/path"
[15:59:42] [R] CWD /the/path/the_project_files/media/pinax/silk/icons
[15:59:43] [R] 250 Directory successfully changed.
[15:59:43] [R] PWD
[15:59:43] [R] 257 "/the/path/the_project_files/media/pinax/silk/icons"
[15:59:43] [R] TYPE A
[15:59:43] [R] 200 Switching to ASCII mode.
[15:59:43] [R] PASV
[15:59:44] [R] 227 Entering Passive Mode (255,255,255,255,4,6).
[15:59:44] [R] Opening data connection IP: 255.255.255.255 PORT: 1030
[15:59:44] [R] LIST -al
[15:59:45] [R] 150 Here comes the directory listing.
[15:59:46] [R] 226 Directory send OK.
[15:59:46] [R] List Complete: 24 KB in 2.55 seconds (9.5 KB/s)
[15:59:46] [R] TYPE I
[15:59:46] [R] 200 Switching to Binary mode.
[15:59:46] [R] SIZE drink.png
[15:59:46] [R] 213 692
[15:59:46] [R] MDTM drink.png
[15:59:46] [R] 213 20111019165722
[15:59:46] [R] Skip [equal]: B:\the_project_django\the_project_files\media\pinax\silk\icons\drink.png
[15:59:46] [R] SIZE drink_empty.png
[15:59:46] [R] 550 Could not get file size.
[15:59:46] [R] PASV

```If you look about 8 lines down in that, you will see where it randomly fails and has to reconnect.

I've checked conntrack. I've checked the firewall. I've checked my local firewall. I've checked with the DC. I've made sure the config is correct. All I get is *poof, its gone* for no apparent reason.

Has anyone noticed this before, or am I just SOL?

- Vadtec

---

### Post by kevinthecomputerguy on 2011-10-19
Are those files your uploading maybe corrupted? Can you make 15 new txt files and upload them OK?

My guess is the source files are maybe corrupt, or something about the file name is doesn't like.

---

### Post by Vadtec on 2011-10-19
No, they are not corrupt. They are jpegs and pngs. I can upload them just fine to any other server I run, some of which are running vsftpd as well. The file names are simple XYZ_ABC.jpeg and xyz_abc.png style file names.

It almost acts like its not acknowledging the file size, so when its done transferring it simply keeps waiting for more data. Just one of the many thoughts I've had about what could be wrong.

- Vadtec

---

