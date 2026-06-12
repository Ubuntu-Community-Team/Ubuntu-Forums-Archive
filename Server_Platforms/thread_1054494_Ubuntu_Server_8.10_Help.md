---
title: "Ubuntu Server 8.10 Help"
date: 2009-01-29
forum: Server Platforms
---

### Post by angel120 on 2009-01-29
I just finished installing Ubuntu Server 8.10 on my new hardware.
First off, some quick specs:
Intel Atom 330 CPU embedded on ITX motherboard
1.5TB Hard drive
90W Pico ATX PSU
The server is connected via a single on-board NIC, directly to my WRT54G Tomato router, which is connected to my cable modem.

I know you guys probably get bombarded with a bunch of noob questions like these, but I haven't the slightest knowledge of servers, networking, or anything of the sort.  I am, however, very proficient in computer hardware, and a moderately skilled computer programmer (Java, C++, and MIPS Assembler).

Anyway, the main features I want are:[list]
[*]Multiple users able to access their files from any computer.  When a user logs in, the user should be brought to their personal home folder, and be unable to view anyone else's home folder.  However, I'd like everyone to be able to access the same "share" folder, so we can all post files in that folder for others to view
[*]Able to host a small webpage for my cell phone.  The page will simply contain icons and links to websites I'd like to view (traffic, maps, Google, etc).  Writing the HTML code is not a problem, just being able to do so seems difficult.
[*]This one is a bit iffy..  I would like it to also act as a print server, however I have a printer/scanner/copier, and would like to be able to scan documents to be saved on the server as well.
[/list]

So far, I've only been able to get my server to run locally.  On my laptop w/ Intrepid, I'm able to connect via PuTTY, SFTP, and I'm able to access the files anywhere on my network via [FTP://AngelServer/](FTP://AngelServer/) but my main focus is to get this thing global (with user authentication, of course).

Any help I can possibly get will be GREATLY appreciated :)

Thanks in advance,
-Angel.

---

### Post by Iowan on 2009-01-30
All *should* be do-able.  Samba server for filesharing (in particular, if users have Windows boxes), LAMP server for webserver, and Samba may be able to print serve, too, but CUPS May be easier option.  Stop by [http://help.ubuntu.com](http://help.ubuntu.com) and search for SAMBA and LAMP (or Apache).

Here are some links:
[Samba]("https://help.ubuntu.com/community/SettingUpSamba")
[LAMP]("https://help.ubuntu.com/community/ApacheMySQLPHP")
[CUPS]("https://help.ubuntu.com/8.04/serverguide/C/cups.html")

---

### Post by volkswagner on 2009-01-31
[Webmin]("http://www.webmin.com/") can also be helpful with server admin.

---

