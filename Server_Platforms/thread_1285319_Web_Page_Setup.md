---
title: "Web Page Setup"
date: 2009-10-07
forum: Server Platforms
---

### Post by gfagel on 2009-10-07
We had a person develop a web page  using Apache2 Php5 and Mysql. The files were given to us and the person has vanished. I have setup a Ubuntu server with Php5 and Mysql. All done with excellent  help for documents found within Ubuntu. So my problem now is trying to figure out where to place the files and folders given to us to get it all working. Is ther any documentation to guide me through this process????

Thanks in Advance
Gary

---

### Post by Iowan on 2009-10-07
The default location is */var/www*, but you can put them elsewhere - as long as Apache knows where to look. [Here]("https://help.ubuntu.com/community/ApacheMySQLPHP") is a place to start.

---

### Post by Lars Noodén on 2009-10-08
If php and mysql are involved, then it was not web pages he set up but some other service using the web.  If you have Apache2 you can see the active sites in this directory, each site has it's own configuration file: 
/etc/apache2/sites-enabled

Look for lines with 'DocumentRoot' and 'Directory' in the configuration file for each site.  


The available, but maybe inactive sites can be found here:
/etc/apache2/sites-available

---

### Post by gfagel on 2009-10-16
Thanks much for the replies. Gives me a place to start.

---

