---
title: "proFTPd ls -lR"
date: 2006-04-04
forum: Server Platforms
---

### Post by jhop on 2006-04-04
I have proFTPd set up and running.  I am trying to set up an indexer program that will allow me to search it (and others)

However, it uses ls -lR to get a list of all the files.  O have seen this work on other ftp servers, but on mine I just get:

ftp> ls -lR
200 PORT command successful
150 Opening ASCII mode data connection for file list
download
upload
ftp
226 Transfer complete.
ftp: 23 bytes received in 0.00Seconds 23000.00Kbytes/sec.

there are lots of files and subdirectories in download, but they arnt shown.  
Any idea why?

---

### Post by jhop on 2006-04-05
well, I havent fixed the problem, but I did ...something... to the indexer, and it seems to work anyway...

so not to worry

---

