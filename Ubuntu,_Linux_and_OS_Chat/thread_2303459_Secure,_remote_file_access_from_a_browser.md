---
title: "Secure, remote file access from a browser"
date: 2015-11-18
forum: Ubuntu, Linux and OS Chat
---

### Post by Sezmeralda on 2015-11-18
This is more a request for guidance than a specific issue to be resolved.

Is there a way to set up a linux computer so that a directory can be accessed securely, over the internet, and without a dedicated client program at the remote end?

For example, I want to be able to download reports and academic files which are on my home (linux) desktop onto a university network computer (which I cannot install software into); and I want to be able to change that file, save a copy to my university home drive, then upload the changed file back to my desktop at home. Or I might be holidaying at friend's place in another city, and want to grab some photos which I promised to give her but forgot... etc.

Online tutorials seem to assume I can just use putty at the remote end, can I do it through a browser instead?

Thanks in advance.

---

### Post by influencedchaos on 2015-11-18
For your case I would recommend using Owncloud which is basically a self-hosted cloud storage. It allows you to upload and download files through a web browser. This does however require that you run a LAMP (Linux, Apache, MySQL, PHP) suite on your home computer. If your interested, more info is over at [Owncloud's Website]("https://owncloud.org/").

Again this is more of a preference and can have multiple answers.

EDIT: You might also want to move the thread to [COLOR=#000000]Ubuntu, Linux and OS Chat since its not a direct issue with Ubuntu itself.[/COLOR]

---

### Post by Sezmeralda on 2015-11-19
> For your case I would recommend using Owncloud
Thank you, I'll definitely look into it - it's great to have a place to start!

> You might also want to move the thread to [COLOR=#000000]Ubuntu, Linux and OS Chat[/COLOR]
Agreed (my bad). Am now working out how to do so!

---

### Post by lisati on 2015-11-19
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by Sezmeralda on 2015-11-19
Thanks Lisati.

I am interested to hear more views on a good way to go about accessing files securely from afar.

---

### Post by Lars Noodén on 2015-11-19
A fast, easy way is to just put up a web server running HTTPS and then putting the pictures behind a password.  It's no frills but can be done safely in minutes.  That would be a prerequisite for a lot of other things anyway.  HTTPS is easy to do nowadays with either Apache2 or nginx.

---

### Post by jeffjohn2 on 2015-11-19
As a more general observation, I use FTPS via Filezilla to access a specific directory ; secure and rock solid.

---

### Post by Lars Noodén on 2015-11-19
> **jeffjohn2 said:**
> As a more general observation, I use FTPS via Filezilla to access a specific directory ; secure and rock solid.

FileZilla also supports SFTP, which is safer and easier to set up.  (FTPS is complicated to set up and, at the end of the day, still FTP).  But speaking of SFTP, it does not even need FileZilla as the file managers now support SFTP out of the box.  Just open Nautilus and choose "Connect to Server" and enter the URI like sftp://user@somesite.example.com/ and it will connect.

---

### Post by mastablasta on 2015-11-19
yet all these sftp options require a client instaolled. unless one uses a portable app.

---

### Post by jeffjohn2 on 2015-11-19
Quote extracted from [www.eldos.com:](www.eldos.com:) It&#8217;s a good idea to use FTPS when you have a server that needs to be  accessed from personal devices (smartphones, PDAs etc.) or from some  specific operating systems which have FTP support but don&#8217;t have SSH /  SFTP clients. If you are building a custom security solution, SFTP is  probably the better option.   As for the client side, the requirements are defined by the server(s)  that you plan to connect to. When connecting to Internet servers, SFTP  is more popular because it&#8217;s supported by Linux and UNIX servers by  default.

---

### Post by Sezmeralda on 2015-11-19
Thanks everyone, but It wonder if I can *Connect to server* from the WinExplorer program at uni... something I would have to try and see for myself.

What about [Weaved]("https://www.weaved.com")?

---

### Post by mastablasta on 2015-11-20
on owncloud or seafile you can connect to the cloud file sharing service via explorer.

if you want to administrate the server via browser then try Zentyal or Ajenti.

---

