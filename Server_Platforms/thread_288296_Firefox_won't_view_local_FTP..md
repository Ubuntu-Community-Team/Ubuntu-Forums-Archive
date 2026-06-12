---
title: "Firefox won't view local FTP."
date: 2006-10-29
forum: Server Platforms
---

### Post by Rashid584 on 2006-10-29
Hey,

Basically, I spent about the last 4 hours (oh my God...I just realised...its been 4 hours!! I need a life!) getting an FTP server to work onmy system. I have pure-ftpd installed.

Now, if I try to connect using Konqueror, I can log in fine with a username and password of an existing user. And access files, copy, delete, download, upload etc

The problem is, I want people to be able to do that from internet explorer/firefox from a computer in any internet cafe. When I enter [ftp://my.ip.add.ress](ftp://my.ip.add.ress) it just says loading forever, and never loads.

If I install the fireFTP extension for firefox, it works fine, again. But that won't be possible in a net cafe with internet explorer.

Does it refuse to connect just because its my local computer...or will it not work at all?

This is really odd behavior...not expected. Also, viewing any other ftp site, e.g. ftp.kde.org, works fine.

Thanks for your help :)

Oh, another question; when I log in, it defaults to /. I want it to default to /home/username not /. Is there any way I can configure pure-ftpd to do that?

-Rashid

---

### Post by bache on 2006-11-01
You need a ftp client to access your ftp server. Internet Explorer and Firefox are only browsers (not talking about the Firefox extension). 

You can install a web server Apache and in that way to access your files through a web page from every place you have an interenet connection and a browser.

---

### Post by Rashid584 on 2006-11-01
Oops, actually, I found a solution to the problem...forgot to post it here.

Internet explorer is actually capable of being an ftp client (i think its the window explorer component...like my documents uses windows explorer so can manage files)

instead of using [ftp://my.ip.add.ress](ftp://my.ip.add.ress) if I use [ftp://username@my.ip.add.ress](ftp://username@my.ip.add.ress) both firefox and internet explorer prompt for a password. When entered, it successfully views that users home folder on my computer :D In firefox it only views, can't upload. Internet explorer can upload as well, by dragging and dropping files into the window.

Also, you can use a colon to seperate the username and password e.g. [ftp://user:pass@xx.xx.xxx.xxx](ftp://user:pass@xx.xx.xxx.xxx) logs them straight in without prompting for a password

Hope thats useful reference for someone in the future who has the same problem (btw for firefox, there are numerous web based java applet ftp clients that will do the job without installing anything. [net2ftp](http://www.net2ftp.com) is one)

-Rashid

---

