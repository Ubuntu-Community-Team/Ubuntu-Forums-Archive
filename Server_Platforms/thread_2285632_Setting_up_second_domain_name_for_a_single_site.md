---
title: "Setting up second domain name for a single site"
date: 2015-07-07
forum: Server Platforms
---

### Post by dprichard on 2015-07-07
I am currently running Apache on Ubuntu 14.04.  I tried adding an alias, but it doesn't do exactly what I need.  I have a single site and I need to point two domain names to it.  The thing is, if someone types in [www.site1.com](www.site1.com) I want it to show the url as [www.site1.com](www.site1.com) and if someone types in [www.site2.com](www.site2.com) I want it to continue to show [www.site2.com](www.site2.com) in the URL.  Right now if they type in [www.site1.com](www.site1.com) it shows the first site name as the URL, but if they type in [www.site2.com](www.site2.com) it changes the URL to [www.site1.com](www.site1.com).  Below is what I have as my virtual host in my conf file currently. Thanks for any help on this.  

```

ServerAdmin webmaster@localhost
ServerName site1.com
ServerAlias site1.com site2.com

```

---

### Post by dprichard on 2015-07-07
Figured it out.  Setup a second .conf file and changed the domain names and pointed it to the same directory.  :D

---

