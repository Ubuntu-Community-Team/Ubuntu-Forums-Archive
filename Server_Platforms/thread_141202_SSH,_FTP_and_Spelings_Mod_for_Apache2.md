---
title: "SSH, FTP and Spelings Mod for Apache2"
date: 2006-03-07
forum: Server Platforms
---

### Post by CyanFOX on 2006-03-07
Okay, HiHi I am having a really great time with Ubuntu (Server) on my iMac, finally i have something productive to do with it...

Okay, when using MacOS it was farily easy for me to Enable FTP, SSH and Edit my Httpd.conf file (because it was mac os) because there were friendly little check boxes for enabling services, with Ubuntu i have had to rely on my UN*X experience and knowing what files to edit et al..

my question is, i finally have my web server part of my server up, but am uncertain as how to get spelings mod enabled in apache2, i was checking the config and i dont believe it was mentioned there but i dont want to waste this question for something i could goto apache.org to figure out so here is my next two real questions:

QUESTION ONE) okay how do i enable SSH so i can "telnet" to my server so i can remote login into my server ( what files do i need to edit and what do i need to edit in these files )

QUESTION TWO) how do i enable FTP on said server so i can do all sorts of FTP'y goodness ( just point me to a config file or a man page or tell me how to start the service [ commands are fine thankyou ] ) with my server?

thanks so much in advance!

CyanFOX ~7~

---

### Post by pete on 2006-03-07
Neither ssh or ftp servers are built into Ubuntu, so you'd need to install them via either Synaptic or apt.

Personally, I canned FTP on my boxes a while back and do all my file transfer via SFTP/SCP over the ssh connection.  However, lots of folks around here seem to like vsftp as an ftp server.

---

