---
title: "webmin configuration  help"
date: 2008-03-24
forum: Server Platforms
---

### Post by psychobeauty on 2008-03-24
hello i have gutsy gibbon server and i want to configure an ftp server in the webmin do anyone know a good tutorial or can anyone help me,,,im new


thanx

---

### Post by Viruk on 2008-03-25
I started posting a reply then realised I was not answering your question!

I have a guide for setting up webmin, but not specifically for setting up an ftp server in webmin. 

Is Webmin set up and running for you? I can post information on that if you need it. 

Maybe one of the following will help you...
[http://whitepapers.zdnet.co.uk/0,1000000651,260280066p-39000684q,00.htm](http://whitepapers.zdnet.co.uk/0,1000000651,260280066p-39000684q,00.htm)
[http://articles.techrepublic.com.com/5100-6345-1046898.html](http://articles.techrepublic.com.com/5100-6345-1046898.html)

---

### Post by psychobeauty on 2008-03-25
web min is install and working..i want to make an ftp or an apache web server

---

### Post by Viruk on 2008-03-26
You can get a good working base setup by just using the LAMP option when installing the server software - I don't know if that's an option for you, or if you're using webmin on someone else's server where you don't have access to the machine itself. 

Most of the recent servers I have set up simply use the LAMP option and do the job I need really well. 

These links may be useful to you for Webmin: 
[For FTP]("http://doxfer.com/Webmin/ProFTPDServer") or [for Apache]("http://doxfer.com/Webmin/ApacheWebserver")

---

### Post by psychobeauty on 2008-03-26
i used the lamp option when i install the ubuntu 7.10 server edition...but now what???:) i dont know what to do next.....i can see throught http//localhost the default page of apache saying it works! but   i dont know how to put my files in there...



thanxxxx

---

### Post by Viruk on 2008-03-27
try adding files to /var/www/your-folder-here

For example, I run a wiki on one of our webservers, I put the wiki files in /var/www/wiki

then to access it i use:
[http://server-address-here/wiki](http://server-address-here/wiki)

Adding the files can be done any way you like. At work we use Windows machines, so I use [WinSCP]("http://winscp.net/eng/index.php") to add files to the linux servers where necessary. I'd reccomend using the stable version not the beta (go for version 4.0.7 as the latest non-beta version at time of writing)

HTH :)

---

