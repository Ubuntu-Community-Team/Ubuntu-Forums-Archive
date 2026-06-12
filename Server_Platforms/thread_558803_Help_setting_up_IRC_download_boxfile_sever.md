---
title: "Help setting up IRC download box/file sever"
date: 2007-09-24
forum: Server Platforms
---

### Post by kipman725 on 2007-09-24
Basicly setting up a box that downloads files from IRC bots via fast internet connection and puts them in an FTP folder to be sent around the lan and to freinds over the web.
  The FTP is working fine(proftpd)  and has a shared folder /home/FTP-shared I have also set up SSH as the box in an effort to save power is running with no graphics card.
  So far I have tried BitchX and ircII (prefered ircII) dcc worked in ircII there are a number of problems before it's usable:

dcc dosn't auto accept files resulting in having to type a massive 120odd character file name to download anything.

I can't find a way to set the download directory which needs to be /home/FTP-shared/irc and the files need to have read/write permisions for everyone (at the moment the FTP user can't delete them or move).

how do you set up a list of servers/chan's to connect on startup?

other issue is how do I add another user account with the same level of permisions as the default user?

---

