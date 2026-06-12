---
title: "apache2 .asp rendering"
date: 2008-03-19
forum: Server Platforms
---

### Post by sreilly on 2008-03-19
Hi,
I'm running an Apache2 LAMP on Gutsy with what I believe to be all the bells and whistles turned on.
The web server runs fine with all the code I throw at it.
However, I have a large number of .asp extension pages that I would like to server but all I get is unrendered source code.
I've installed Tomcat, Mono, Apache::ASP etc etc and been through loads of howto's but can't seem to get it to work.
As a work-around, if I replace the .asp extension of each file with .php and sed each file to replace each .asp hyperlink with .php it works. But  I'd like to know the correct way of doing it.
If install Apache2 under XP and use the .asp files it has no problems at all.

TIA,
Steve

---

### Post by twistedtwig on 2008-03-19
Hi,

Are you saying if you server default.asp as default.php it parses the asp page and serves it correctly but will not serve it if it has the asp extension?

if that is the case then I would presune you just need to add a handler or soemthing of that nature so it knows that it is a valid extension.

in the apache.conf file it says .html .htm files are extensions.  I htink it is where it does the .php as well.  I would try addign .asp where the others are added to see if that fixes it (force-reload would probably be needed).

GL

---

