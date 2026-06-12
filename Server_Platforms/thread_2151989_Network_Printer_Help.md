---
title: "Network Printer Help"
date: 2013-06-06
forum: Server Platforms
---

### Post by chrisavfc93 on 2013-06-06
Hi,
I've been trying to get a network printer set up using my linux server running Ubuntu 12.04 and my HP Deskjet 1050 printer.
The drivers are installed and I can print a test page if I print from the server itself, so I know that works.
I'm using a samba share and the printer shows up on my windows laptop and the option is there to use it as a printer, however when I do choose it nothing happens. 
I checked to see if there were ant pending printing jobs and there were not, guessing it must be due to permissions, but I'm a bit lost now.

Here is the relevant part of my smb.conf (well at least what I think is the relevant part.)

```
[printers]
        create mask = 0700
        comment = All Printers
        printable = yes
        writeable = yes
        public = yes
        path = /var/spool/samba


# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
        guest ok = yes
        comment = Printer Drivers
        writable = yes
        path = /var/lib/samba/printers

```


Thanks,

Chris

---

### Post by SeijiSensei on 2013-06-06
Have you checked the logs in /var/log/samba?

---

### Post by chrisavfc93 on 2013-06-06
> **SeijiSensei said:**
> Have you checked the logs in /var/log/samba?

This is the only relevant log I can see in there but not a clue what it means.

```
[2013/06/06 15:57:23,  0] smbd/server.c:1051(main)
  smbd version 3.6.3 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2011
[2013/06/06 15:57:23.427714,  0] smbd/server.c:1107(main)
  standard input is not a socket, assuming -D option
[2013/06/06 16:09:21,  0] smbd/server.c:1051(main)
  smbd version 3.6.3 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2011
[2013/06/06 16:09:21.279512,  0] smbd/server.c:1107(main)
  standard input is not a socket, assuming -D option
[2013/06/06 16:14:29,  0] smbd/server.c:1051(main)
  smbd version 3.6.3 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2011
[2013/06/06 16:14:29.900369,  0] smbd/server.c:1107(main)
  standard input is not a socket, assuming -D option



```

---

### Post by SeijiSensei on 2013-06-07
Not much there, I'm afraid, though it seems like the server keeps restarting.  Those timestamps are awfully close together. 

How about trying "smbclient -L localhost" on the server?  Does it show the print share as available?  If so, try connecting to it with "smbclient //localhost/print_share_name".  You should get an "smb: \>" prompt.

---

### Post by gordintoronto on 2013-06-07
Do you actually need Ubuntu Server for some reason? Ubuntu Desktop runs almost as well, and it provides many useful GUI tools. Everything you can do in Server, you can do in Desktop, if you have enough RAM. (1 GB)

---

