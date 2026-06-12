---
title: "Trouble getting updates and locating netIP with my Ubuntu 7.10 Server"
date: 2013-11-15
forum: Server Platforms
---

### Post by jonathanbojilov on 2013-11-15
Recently I decided to build a Web Server and got a tutorial from this site: 

[http://www.techsupportalert.com/how-to-set-up-your-own-web-server.htm](http://www.techsupportalert.com/how-to-set-up-your-own-web-server.htm)

However it asked for me to download US 7.10 which according to its release is (EOL) which I think doesn't matter. I installed it with my CD-ROM. 
I established an internet connection within my server and proceeded to delete from the vi file all the [COLOR=#333333][FONT=Verdana]"deb cdrom" lines. I then exited the file and when
I typed:

[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]*apt-get update*    [nothing happened]
[/FONT][/COLOR]*[COLOR=#333333][FONT=Verdana]apt-get upgrade   [/FONT][/COLOR]*[COLOR=#333333][FONT=Verdana][nothing to upgrade][/FONT][/COLOR][COLOR=#333333][FONT=Verdana]
[/FONT][/COLOR]*[COLOR=#333333][FONT=Verdana]apt-get install telnetd  [/FONT][/COLOR]*[COLOR=#333333][FONT=Verdana]["error - telnetd not found"]
[/FONT][/COLOR]
[FONT=Verdana, Tahoma, Arial, Helvetica, sans-serif][COLOR=#333333]I honestly don't know what the issue is - there is a connection. Also I cannot test my Web Server via locating its IP. I would type 192.168.x.xxx on a browser at home but nothing would happen...[/COLOR][/FONT]

---

### Post by SeijiSensei on 2013-11-15
Of course it matters.  A release that reaches end of life will usually no longer have active repositories.

Install 12.04LTS.  No one will be able to help you with a version as old as 7.10.

---

### Post by Doug S on 2013-11-15
additionally, toss out that reference you were using (updated June 2012, but still says to use 7.10, therefore not updated, really) and use the [ubutu serverguide]("https://help.ubuntu.com/12.04/serverguide/index.html") ([the PDF]("https://help.ubuntu.com/12.04/serverguide/serverguide.pdf")).

---

