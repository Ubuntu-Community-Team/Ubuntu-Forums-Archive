---
title: "vsftp compatability question"
date: 2009-04-09
forum: Server Platforms
---

### Post by CodeMonkeyX on 2009-04-09
Hello,
I have a vsftp server up and running on a Ubuntu 8.04 machine. The server works fine when connecting from ftp clients, but I am trying to get it to work with an old Xerox Docutech 135 ftp archive program.

The Xerox machine copies files fine, but will not list any files. I turned on debugging saw this in the log:

```
Thu Apr  9 15:36:49 2009 [pid 15929] CONNECT: Client "192.168.0.16"
Thu Apr  9 15:36:49 2009 [pid 15929] FTP response: Client "192.168.0.16", "220 (vsFTPd 2.0.6)"
Thu Apr  9 15:36:49 2009 [pid 15929] FTP command: Client "192.168.0.16", "USER docutec3"
Thu Apr  9 15:36:49 2009 [pid 15929] [docutec3] FTP response: Client "192.168.0.16", "331 Please specify the password."
Thu Apr  9 15:36:49 2009 [pid 15929] [docutec3] FTP command: Client "192.168.0.16", "PASS <password>"
Thu Apr  9 15:36:49 2009 [pid 15928] [docutec3] OK LOGIN: Client "192.168.0.16"
Thu Apr  9 15:36:49 2009 [pid 15930] [docutec3] FTP response: Client "192.168.0.16", "230 Login successful."
Thu Apr  9 15:36:49 2009 [pid 15930] [docutec3] FTP command: Client "192.168.0.16", "CWD /mnt/data/docarchive/docback1"
Thu Apr  9 15:36:49 2009 [pid 15930] [docutec3] FTP response: Client "192.168.0.16", "250 Directory successfully changed."
Thu Apr  9 15:36:49 2009 [pid 15930] [docutec3] FTP command: Client "192.168.0.16", "PORT 192,168,0,16,125,127"
Thu Apr  9 15:36:49 2009 [pid 15930] [docutec3] FTP response: Client "192.168.0.16", "200 PORT command successful. Consider using PASV."
Thu Apr  9 15:36:49 2009 [pid 15930] [docutec3] FTP command: Client "192.168.0.16", "LIST /mnt/data/docarchive/docback1/*/*Job.type"
Thu Apr  9 15:36:49 2009 [pid 15930] [docutec3] FTP response: Client "192.168.0.16", "150 Here comes the directory listing."
Thu Apr  9 15:36:49 2009 [pid 15930] [docutec3] FTP response: Client "192.168.0.16", "226 Transfer done (but failed to open directory)."
Thu Apr  9 15:36:49 2009 [pid 15930] [docutec3] FTP command: Client "192.168.0.16", "QUIT"
Thu Apr  9 15:36:49 2009 [pid 15930] [docutec3] FTP response: Client "192.168.0.16", "221 Goodbye."

```

It seems that "LIST /mnt/data/docarchive/docback1/*/*Job.type" is the command that is causing the problem. If I do a ls from the terminal and type in the same command it works file and lists several files that I put there.

But it just will not list from the FTP program.

Is this a problem with vsftp? Is it possible that using another server program might work?

The current setup is using WSFTP on a windows machine currently without issue.

---

