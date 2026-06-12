---
title: "ubuntu server and ftp"
date: 2009-11-30
forum: Server Platforms
---

### Post by citronvodka on 2009-11-30
I have a disk from windows widht lots of film on

how should i do to have the disk in ubuntu and let friends to use ftp to login and so on

i have install vsftpd but how should i do to let them see the disk

---

### Post by pi4r0n on 2009-11-30
> **citronvodka said:**
> I have a disk from windows widht lots of film on
 
how should i do to have the disk in ubuntu and let friends to use ftp to login and so on
 
i have install vsftpd but how should i do to let them see the disk
 
I would start with some basics [here]("http://www.google.co.uk/search?hl=en&q=setup+ftp+server+in+ubuntu&meta=&aq=f&oq=")

---

### Post by citronvodka on 2009-11-30
the ftp works ,but when i´m logon i only see filefolders, think this is my home folders, but how should i do to see my new disk??

---

### Post by BkkBonanza on 2009-11-30
Are you aware that using ftp is very insecure? If you want to expose your whole disk via ftp you would be opening up you machine to many security problems. Users accessing your machine with ftp would be exposing userid/passwords in clear text across the internet making it easy for others sniffing traffic to capture these.

---

### Post by citronvodka on 2009-12-02
I´m going to secure widht ssh or something else, just now im trying to make so i can see my disk

---

