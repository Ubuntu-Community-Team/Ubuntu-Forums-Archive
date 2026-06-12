---
title: "UW IMAPD help!"
date: 2007-11-24
forum: Server Platforms
---

### Post by DaturaX on 2007-11-24
I am trying to get install the UW IMAPD package. My aim is to have the pop3 package working.

I have downloaded the imap.tar.Z file and managed to tarball it.

I have also compile it using the following argument 

make LNP SSLTYPE=NONE

Attached is the link to the screenshot of the error message during the compilation.

[[IMG]http://img259.imageshack.us/img259/3490/imap2006ecompileerrorij0.th.jpg[/IMG]](http://img259.imageshack.us/my.php?image=imap2006ecompileerrorij0.jpg)

Nonetheless, I managed to see the ipopd packages in the folder.

[[IMG]http://img516.imageshack.us/img516/496/imap2006ecompileerror02we6.th.jpg[/IMG]](http://img516.imageshack.us/my.php?image=imap2006ecompileerror02we6.jpg)



Now my next task is to get the ipop3d binary produced after the compile into the directory /usr/local/bin and have the pop3 service started. But in the ipopd folder, I see that the files are ipop2d.c and ipop3d.c and MAKEFILE.

How do I compile the ipop3d.c into a a daemon and have ithe service automatically started?

---

### Post by MJN on 2007-11-24
Whilst not a direct answer to your question, is there any particular reason your want to use UWIMAP? (and why not from the repositories?)? Try Dovecot instead - you will likely find it works out of the box as required.

(I'd also recommend using IMAP instead of POP3 if you've got the choice)

Mathew

---

### Post by DaturaX on 2007-11-26
This is a requirement for my coursework. I have figured out that the UW-imapd port for make is ldb 

Attached is the log of the make.

It seems that the make is not successful and I dont know how to make out the errors.

Anyone have done UW-Imapd before? I tried googling the web but doesnt look very successful.

---

### Post by DaturaX on 2007-11-26
Managed to get it up and running. The error was telling me that I am missing the c compiler. Fixed it by installing the build-essentials.

---

