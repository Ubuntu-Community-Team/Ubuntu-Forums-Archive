---
title: "Apache2 mime types"
date: 2008-07-17
forum: Server Platforms
---

### Post by yahn on 2008-07-17
Can anyone tell me how to set up Apache2 to serve application/xhtml+xml?  There is supposed to be a mime-type file in the apache2 home folder, but it's not there.

---

### Post by cdenley on 2008-07-17
> **yahn said:**
> Can anyone tell me how to set up Apache2 to serve application/xhtml+xml?  There is supposed to be a mime-type file in the apache2 home folder, but it's not there.

Maybe you need to edit this file.
/etc/apache2/mods-available/mime.conf

---

### Post by srv42 on 2013-04-05
I was looking for the same information, here is my findings:
 
In the file: [B]/etc/apache2/mods-available/mime.conf
[/B]you can add/override MIME types in the section "**AddType**"
however by default it tells Apache to load the mime types from **/etc/mime.types**

In Ubuntu server version 12.04 those mime types are already listed in **/etc/mime.types** as 
[I]application/xhtml+xml     xhtml xht
application/xml              xml xsl xsd[/I]
so they should be loaded by default.

fyi: I was looking for this information to add .dat and .pac, but they are also already in there.
*application/x-ns-proxy-autoconfig      pac dat*


The problem that I had was the file permissions on the wpad.dat file in the apache directory **/var/www**
When I pointed my web browser at the file ( [http://apachewebserver/wpad.dat](http://apachewebserver/wpad.dat) ) it could not read it and got an error "Permission Denied".
Once I fixed the permissions on the file the browser was then able to read the file and prompted me to download or open with application.

---

