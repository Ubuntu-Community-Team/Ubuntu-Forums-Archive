---
title: "Samba failing to start"
date: 2010-09-07
forum: Server Platforms
---

### Post by pspkiller91 on 2010-09-07
I've recently rebuilt and revamped my file/web/streaming music server at home. Basically it was a case of back up all files, format all hard drives, install Ubuntu on a new drive as the SMART status on the old one suggested it might die soon, accidentaly destroy the new drive by dropping a multitool on it (lots of smoke), find another drive, install Ubuntu on that, get all the other drives mounted and ready, install a load of software and fiddle with configuration files and hope for the best. So far it's worked out pretty well. I have access to everything I need over FTP and HTTP. I've set up SSH and VNC for fiddling with settings and whathaveyou and I also have Jinzora installed on the HTTP webserver for the streaming of MP3's over the internet to wherever I may be. It's all great except for the single most important function.

I need access to my files from within my network. The natural choice for this is Samba to set up Windows shares. So, I installed it, configured it and voila. All was well until the the server was rebooted. Samba doesn't want to start up. So, I unintstalled it, cleared the configuration files and started again. Same problem again. I'm on the 3rd install now and it's beginning to annoy me.

The log of Samba attempting to start goes as follows:

```

[2010/09/07 15:20:36,  0] smbd/server.c:1069(main)
  smbd version 3.4.7 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2010/09/07 15:20:37,  0] printing/print_cups.c:103(cups_connect)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2010/09/07 15:20:37,  0] printing/print_cups.c:103(cups_connect)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2010/09/07 15:20:37,  0] smbd/server.c:1115(main)
  standard input is not a socket, assuming -D option

```

Now, I know that CUPS is to do with printing and that Samba can be used to work as a print server as well as a file server or domain controller but the printing and domain functions are all disabled.

I can post smb.conf if needed. I've left it out for now because of it's size.

Thanks.

---

