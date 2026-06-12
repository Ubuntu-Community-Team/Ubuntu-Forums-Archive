---
title: "A thank you to the Ubuntu team and the commmunity that uses and supports Ubuntu"
date: 2008-11-12
forum: Testimonials &amp; Experiences
---

### Post by SteveHillier on 2008-11-12
I am going to heap praise on you guys.  All of you.  Guys of both genders and of every sort.
Those of you who have seen my posts in the past will know that I am not shy of having a rant if I want and ktubu's thread (978533) has inspired me to counteract his comments.
My set up.  On my desk I have two workstations, one Ubuntu (Hardy) and one Vista Business.  Both connect to my network domain based on Windows 2003 Server standard.  My Ubuntu machine connects all my mapped drives if I need them so can act as a domain workstation without problems.
I have recently been writing a few websites and needed a php server so I set up a LAMP server (based on Fedora 8 - sorry guys).  My Win 2003 server acts as the appropriate DNS server so I can load test sites onto the webserver and test them.  No problem with all of that.  Works OK.
So I have a situation.  My Vista machine (on which I do most of the creation, leaving my Ubuntu machine to show the webpages and hold other references) sometimes has problems connecting to the web server via FTP.  (I am using vsftpd server on the server and FileZilla client on both workstations.)
There are times when Vista works like a dream but other days such as today I could not get it to connect to the server.  I could get it to connect to a public server, just not the local one.  I could ping the web server IP address the get a response back but it would not respond to a ping on a hostname on that server.
One might suspect DNS problems on Win 2003, but using the ftp agent on Ubuntu connected straight away.  The problem here is that while I can connect I have not yet found out how I can get FileZilla to reference to the mount points of the mapped drives.  All the html, php, images, css etc are all stored on the Win 2003 server.
So how did I do it in the end.
Develop the html on the Vista machine (convenience of software).  Store the files on the Win 2003 server.  Connect to the server on the Ubuntu machine and drop the files on the desktop.  Pick up the files from the desktop with FileZilla and copy to the web server.
It works.  It is not pretty.  It is long winded.  But it is necessary.
Why is it necessary?  Because Vista networking is such a pig's ear, dog's breakfast or whatever.
It can't be the DNS server, that does not change.  I can't be the web server, that does not change.  I can't be the ftp client, that does not change (OK there may be some diferences).  The only difference is Vista and Ubuntu, and guess which one wins here.
So my thanks go to all of you who give of your time freely to develop and support this system.:lolflag:

---

