---
title: "Beginner Uploading webpages"
date: 2008-02-11
forum: Server Platforms
---

### Post by stock1232 on 2008-02-11
I have just installed LAMP, vsftpd. What is the easiest way to upload html files from a remote computer? i know Samba is the best on the LAN from windows to linux.

If I use or have FTP does my user need a client to log into my file server? How do I use vsftpd to let the user download to a specific directory or folder/

Basically, I want developers to be able to upload webpages/ ect to my webserver. I might need a step by step process because of my lack of knowledge.

Thanks in advance.

---

### Post by crouton on 2008-02-13
You really should do some Googling on these subjects.  You will learn a lot more reading and testing it yourself than somebody giving you the answers.

There are some excellent guides on [www.howtoforge.com](www.howtoforge.com) that may help you get started.

---

### Post by faulkes on 2008-02-13
Server specific information can be found at:

[https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)

Faulkes

---

### Post by jonabyte on 2008-02-14
you can use winscp from a windows machine.

---

### Post by johnnybirdman on 2008-02-14
> **stock1232 said:**
> I have just installed LAMP, vsftpd. What is the easiest way to upload html files from a remote computer? i know Samba is the best on the LAN from windows to linux.

If I use or have FTP does my user need a client to log into my file server? How do I use vsftpd to let the user download to a specific directory or folder/

Basically, I want developers to be able to upload webpages/ ect to my webserver. I might need a step by step process because of my lack of knowledge.

Thanks in advance.

on the client side check out Filezilla.
Hope you have better luck than me setting things up on the server side, I'ved tried a few different how-to's and programs with no luck.

---

### Post by Holmes89 on 2008-02-15
I spent a lot of time trying to figure this out and I dissagree with the comment of going to a website to figure it out by yourself. Yes it is important to learn how to do these things but it is also important for the community to help. My question is do you have a thumbdrive? because that is the easiest way I figured out how to upload a website.

---

### Post by crouton on 2008-02-15
The community does help - this post could have easily been ignored but wasn't. "How do I ride a bike" can be answered by the community, but unless you've jumped on a bike you won't necessarily understand all the advice.  Reading tutorials and then trying them out for yourself is (IMHO) more effective than giving out a working solution that only works for one situation.

---

### Post by faulkes on 2008-02-15
Ok, lets return to trying to help the poster out, rather than arguing over "read" or "don't read".

In regards to the thumb drive idea, while this does work, the poster specifically mentions a requirement for multiple users, which negates the uses of such a device, especially in a development environment.

Faulkes

---

### Post by Brazen on 2008-02-15
You'll probably want to use ftp.  That is the standard way that hosting companies provide for users to upload their content and every web authoring program I know of (Komposer, Dreamweaver, Frontpage) include a built in FTP client.  Windows also has built-in functionality as an ftp client which your users may already be familiar with, but I strong encourage users to use Filezilla client and they have a much better experience with that.

I followed this guide for setting up my ftp server: [https://help.ubuntu.com/6.06/ubuntu/serverguide/C/ftp-server.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/ftp-server.html)
I hope you are sticking with the LTS release of Ubuntu on your server (it is really much better for a production server).  I would read through that page, try it out and then ask here if you need any help.

Another option is scp.  Scp is included with ssh, but you'll probably want to use scponly so your users can't get a shell and are chrooted into the website directory.  I have not set up scponly, so you are on your own there.  Scp is more secure over ftp, and that is it's only advantage.  By more secure though, I mean much much MUCH more secure.  But security usually isn't much of an issue with websites since the webpages will probably be publicly viewable anyway.

---

