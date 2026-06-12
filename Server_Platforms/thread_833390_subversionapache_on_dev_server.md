---
title: "subversion/apache on dev server"
date: 2008-06-18
forum: Server Platforms
---

### Post by nullspace on 2008-06-18
I having issues with an existing apache web server I use for development work. I want to install subversion and trac. I found a howto [http://www.howtoforge.com/subversion-trac-virtual-hosts-on-ubuntu-server]("http://www.howtoforge.com/subversion-trac-virtual-hosts-on-ubuntu-server")
I followed it and got stuck when I restarted my apache server. 
I just added the the apache site configuration info into my existing sites config file. The existing site is a subdomain so I figured I would just make this a svn.subdomain.com.

When I restart the apache server the server shutsdown gracefully and I get a bunch of client connection errors. 

the site config file is here: [http://paste.ubuntu.com/21205/](http://paste.ubuntu.com/21205/)

---

