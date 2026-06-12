---
title: "LAMP Server Major Permission Issue (I think)"
date: 2014-08-23
forum: Server Platforms
---

### Post by robert_boutin2 on 2014-08-23
Hoping somebody may be able to help me.

I set up a web server and it has been working well.  However...

Earlier this year I installed Pydio in a subdirectory of my website.  I recall having to modify several permissions as a site security precaution.  Well I went to upload some updated html pages in my main site directory via Filezilla and all my site files and directories were hidden.  I connected to another site I created on the same server and all the files were visible.  So I can only guess that somehow it was caused when I revised the permissions for Pydio.  I tried to revise permissions for all files and directories in /var/www to 755 but something went horribly awry.  As I was in ispconfig3 deleting a couple webDAV usernames that were not in use, my screen jumped to an Internal Server Error screen.  When I tried to browse to my website using my external ip address, I get a 443 Internal Server Error.  When I try to open ispconfig, I get the error again.  Also, my SSL seems to be involved in this this issue.  If I browse to [http://X.X.X.X]("http://64.233.215.72") and [http://192.168.1.3](http://192.168.1.3), I get the Apache "Welcome to Your Website".  But if I try either ip with https:// which worked fine before this issue, I get errors.

From what I've been able to find, it sounds like I changed permissions in a way that somebody external trying to browse to my site doesn't have permission to get into the server to access web files.  I'm an engineer, not a programmer so sorry if I'm explaining this in a ridiculous manner.  Any thoughts?  Appreciate any and all advice.  Thanks.

****update.  So I did an update to ispconfig.  Now I can connect to ispconfig.  But I still get an error trying to browse to my sites.  I am forcing https, that seems to be a big part of the problem.

****update.  I ended up just going into ispconfig, deleting my websites, creating new sites, and then reuploading the html files.  That seems to have everything back to normal.

---

