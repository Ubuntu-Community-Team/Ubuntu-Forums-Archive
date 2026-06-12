---
title: "Dynamically configured mass virtual hosting"
date: 2009-09-21
forum: Server Platforms
---

### Post by krraleigh on 2009-09-21
Working with the wiki on Dynamically configured mass virtual hosting over at [apache.org]("http://httpd.apache.org/docs/2.2/vhosts/mass.html"). Now I would like to dynamically configure a file path name based on the subdomain that the user types in so I can serve the correct files. I have create a separate vhosts file just for subdomains on the site and my wildcard is working for the one file path that I have setup. So far so good. But, now I need to extract the subdomain name so that I can include it in the file path so that I can serve up one vhosts file for all my 125 camps.
 
looking at the info below from the website:
> [FONT=Courier New]# get the server name from the Host: header[/FONT]
[FONT=Courier New]UseCanonicalName Off[/FONT]
 
[FONT=Courier New]# this log format can be split per-virtual-host based on the first field[/FONT]
[FONT=Courier New]LogFormat "%V %h %l %u %t \"%r\" %s %b" vcommon[/FONT]
[FONT=Courier New]CustomLog logs/access_log vcommon[/FONT]
 
[FONT=Courier New]# include the server name in the filenames used to satisfy requests[/FONT]
[FONT=Courier New]VirtualDocumentRoot /www/hosts/%0/docs[/FONT]
[FONT=Courier New]VirtualScriptAlias /www/hosts/%0/cgi-bin [/FONT]
 
Now I tried to work with this info but the first error that I ran into was that I couldn't use VirtualDocumentRoot in my vhost file.
 
I am also not sure where all this information is supposed to go. I read that httpd.conf was just there for older systems and isn't to be used anymore. I am to use apache2.conf instead.
 
So can someone give my a hand by telling what info I need to put into my vhosts file and where the rest of the information is supposed to go. Rather new to this section, and not fully understanding what I need to do.
 
 
Just a thought that I just came across. Do I need to install mod_vhost_alias to use the virtualdocumentroot? If so How do I install it? I can't find any docs. And when I checked to see what what mods were available I found a mod called alias.conf. Is that the same thing that I want? 
 
Using the intrepid version of ubuntu 8.10
insight appreciated
thanx
kevin:popcorn:

---

### Post by krraleigh on 2009-09-21
problem solved
 
thanx anyway
 
use the apache website for your answers
may time a little time to wrap your head around the info but it works great
 
Kevin

---

