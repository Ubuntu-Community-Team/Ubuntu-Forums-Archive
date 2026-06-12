---
title: "possible issues with apache configs"
date: 2011-01-07
forum: Server Platforms
---

### Post by Gashi on 2011-01-07
hey everyone I'm thinking I am having issues with apache or php configurations. I didn't know where to post so mods please feel free to move if need be :) 

i have LAMP setup through the lamp-server task in aptitude don't know enought to trust myself to do a custom configuration :(
I also have proftp setup to the /var/www directory and have my vhosts setup to be a subdomain of my domainname and am able to access it from the interwebs after many hours of digging and scratching lol :D

i have the web directories set to be chown'd by my main user we'll call it gashi. as that was the only way i seemed to get proftp to work...(i know major security no-no just didnt know what to do...) ](*,) postscript: i dont know hardly anything about permissions of groups and users just the standard basic stuff... :( 

but my issue is i have a php document that i have in a private directory protected by .htaccess(deny from all) and it seems that apache2(or somthing else) can't access that file...any help provided is greatly appreciated..

i am using to get the document the php server variable DOCUMENT_ROOT and have checked the path with echo and it is right its comming from the /(root) directory (or is this my problem?)

---

