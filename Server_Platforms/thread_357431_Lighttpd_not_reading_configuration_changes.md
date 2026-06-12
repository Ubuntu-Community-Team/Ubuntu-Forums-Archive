---
title: "Lighttpd not reading configuration changes"
date: 2007-02-09
forum: Server Platforms
---

### Post by Barleyman on 2007-02-09
Hi, I have a VPS server running lighttpd.  It works fine, but no matter what I do, I can't get it to recognize the fact that I have changed the following.

index-file.names = ( "index.php", "index.html", "index.htm" )
server.dir-listing = "enable"

I have a script that restarts lighttpd and I have even rebooted with no luck.

ps. I can add a new website with no problems and it is recognized by restarting.  It just won't recognize index.html or index.htm as a valid index-file

---

### Post by Barleyman on 2007-02-09
Solved my own problem.  I just [used this default config file ]("http://www.debianhelp.co.uk/manpages/samplelighttpd.txt") and rebuilt my config piece by piece, until I ran into the problem.

This was the problem 

$HTTP["host"] =~ 

on one of my sites.

---

