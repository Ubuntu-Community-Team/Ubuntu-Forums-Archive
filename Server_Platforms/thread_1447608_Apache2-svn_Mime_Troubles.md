---
title: "Apache2-svn Mime Troubles"
date: 2010-04-05
forum: Server Platforms
---

### Post by Thund3rstruck on 2010-04-05
Hi guys, 

I've got an apache-svn server up and running fine but I'm struggling with an irritating problem. I need the apache server to display .vbs, .cs., vb., .sh, .pl., .c, .h, .cpp, etc, etc files in the browser. Whenever our users click on a script they get a download dialog instead of the script being displayed in the browser as plain/text. 

I have added: 
```

AddType text/plain .vbs

``` 

Into /etc/apache2/mods-enabled/mime.conf but it seems to be getting ignored. 

Anyone have any ideas how I can tell apache to treat script files as plain-text?

Cheers!

---

### Post by Thund3rstruck on 2010-04-05
Resolved... have to set each svn:mime-type property on every file in the repository for this to work. 

For additional detail, [here's my writeup]("http://www.nealosis.com/blog/post/Create-a-Subversion-Repository-for-Windows-Clients.aspx") of how to get apache to serve code files as plain/text in the browser.

---

