---
title: "fsftpd broken"
date: 2009-11-26
forum: Server Platforms
---

### Post by johnh10000 on 2009-11-26
Now I run 2 ftp servers on my network.   tux on the usual ports 20-21
and tux2 on 90-91.  This has been working for months.

When I TRY to log into tux, from tux2 (I get clues that way) I get

johnh10000@tux2:~$ ftp tux.isa-geek.org
Connected to tux.isa-geek.org.
220 Welcome to blah FTP service.
Name (tux.isa-geek.org:johnh10000): johnh10000
331 Please specify the password.
Password:
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> ls
500 Illegal PORT command.
ftp: bind: Address already in use
ftp> quit
221 Goodbye.
johnh10000@tux2:~$ 

ANd of course no dir list.

Now I haven't changed the confog, so I am a tad confused.

Any kind soul will help me?

in addition from tux2 which is on the loacl net I get this now:
[2]+  Stopped                 ftp -p tux.isa-geek.org 21
johnh10000@tux2:~$ ftp -p tux.isa-geek.org 21
Connected to tux.isa-geek.org.
220 Welcome to Tux's FTP service.
Name (tux.isa-geek.org:johnh10000): johnh10000
331 Please specify the password.
Password:
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> ls
227 Entering Passive Mode (82,6,134,175,197,142)
ftp: connect: Connection refused
ftp> 

Oh it works just fine on tux, just know where else

---

### Post by johnh10000 on 2009-11-26
An update gang

When I change tux ftp port to 90-91 it works.  It just don't work at 20-21
Plain weird.

---

