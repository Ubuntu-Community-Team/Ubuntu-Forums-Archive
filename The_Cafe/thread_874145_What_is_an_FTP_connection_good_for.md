---
title: "What is an FTP connection good for?"
date: 2008-07-29
forum: The Cafe
---

### Post by Lateforgym on 2008-07-29
I know that sounds stupid. I understand you can transfer files between computers, but I usually just use a USB between my desktop and my laptop. I also have an HDD adapter for major transfers and its more secure since Im not putting personal files on some strange internet website. So, What is an FTP good for then? Am I missing something here? If there is another reason that the community frowns upon, like for transfering pirated stuff between friends (like all you ipod stuff to your mates), you can email me that answer. I just got curious on this one since I keep seeing more and more people with FTP connection through widgets or other applications, yet USB drive are huge these days and everyone seems to have one.

---

### Post by 50words on 2008-07-29
Uploading files to my websites.

---

### Post by tom66 on 2008-07-29
Backup & uploading.

Say you have a backup HDD sitting next to your computer - it's not going to work too well after a fire, or something drastic.

---

### Post by Lateforgym on 2008-07-29
Thanks. Do you trust these website to keep your data secure? Also, how large of a free account can you get and can you friends access it?

---

### Post by LaRoza on 2008-07-29
[http://en.wikipedia.org/wiki/File_Transfer_Protocol](http://en.wikipedia.org/wiki/File_Transfer_Protocol)

---

### Post by Lateforgym on 2008-07-29
"No integrity check on the receiver side. If a transfer is interrupted, the receiver has no way to know if the received file is complete or not."

Interesting. Thats good to know for people who back up their stuff to FTP.

---

### Post by wootah on 2008-07-29
SSH using SCP or rsync.

Check them out :)

EDIT: Should have read your question. Wow... sorry!

---

### Post by tom66 on 2008-07-29
Yes, but the TCP/IP protocol itself integrates checksums so any 'frames' which are corrupt are discarded. I believe this applies to FTP as well. Plus, if you're paranoid, like me, you use SFTP which is encrypted.

I trust my web host, DreamHost, to keep my information secure. Nonetheless, there could be a leak, but that's the same for any system - if it has access to the outside world, there's probably a way you can get into it. FTP on web servers is almost always password-protected, except with anonymous FTP.

---

### Post by original_jamingrit on 2008-07-30
FTP is just one way of doing things, it's something that's very old and very common.  You may have even used it without realizing it, through your web browser.  It's not particularly sophisticated, [COLOR="Gray"]it doesn't even support globbing[/COLOR](EDIT: nevermind, i guess it does).  But it's simple and quite useful for low-bandwidth connections to a server you trust, including possibly your own.

---

### Post by Corfy on 2008-07-31
This may not be the answer you are looking for, but...

My office would pretty much shut down if it weren't for FTP. Among other things, we are a commercial printing operation, with our customers sending us their files to print via FTP (we have our own FTP server in house). These are files that can easily reach 50 MB each, with up to 60 files per product. (OK, that is a tad misleading... I don't know of any products that have 60 50MB files, but you get the idea). These are files that are too big to email, and with our customers being miles away, physically transferring the files is inconvenient to say the least.

---

### Post by DownTown22 on 2008-07-31
I have an NAS drive with a built in FTP server which I and my fiance (and my family from elsewhere) use to access files when we're away from home.  Just the other day I put some more music on the drive, my fiance wasn't home and wanted some different music, so she just FTP'd it her computer - and this was much faster than trying to email it or send it via skype/pidgin/msn.

---

### Post by arvevans on 2008-08-01
Open a terminal screen (the dreaded CLI - Command Line Interface) and enter "man ftp".  Use your keyboard arrow keys to scroll up or down in the man page for ftp.  When done reading, you should have a pretty good grasp on the function and possibilities of ftp.  It is used for many things, some in the background that you may already be doing and don't realize it.
_._

---

### Post by phaed on 2008-08-01
"What is an FTP connection good for?"

Wow, that question makes me feel old.

Here's another one for 10 bonus points:  what is a gopher connection used for?  (And I'm not talking about an animal :)

---

### Post by arvevans on 2008-08-01
For answer to your "Gopher" question, go here: 

[INDENT]<http://www.codeghost.com/gopher_history.html> [/INDENT]

Although the dates given for emergence of the Gopher are a bit wrong.  I was using it at Bell Labs at an earlier date (probably a code leak from the University of Michigan or University of Wisconsin).

Think you feel old...I have met and talked with Richey, Kernigan, Aho, etc. when they were writing original UNIX code.  I feel positively ancient, and some of the questions encountered on this forum make it even worse.  What I do find amazing is that so much of that original UNIX operating system has survived to become significant parts of the Linux OS, and the applications that run on it.

Arv
_._

---

### Post by hubie on 2008-08-02
It has always been the way to transfer very large files, where large is defined to be too big for email.  Even though many places such as gmail are letting you deal with emails up to 20MB (my company will let me receive 15MB and send 10MB), you may be surprised the size of files you may want to send if you deal with lots of data, or work with people who load up their PowerPoint files with tons and tons of very large pictures.

---

### Post by xss500 on 2008-08-23
It is very nice if you need to download heavy files from internet.
[Missouri Drug Addiction](http://www.drugaddiction.net/missouri)

---

