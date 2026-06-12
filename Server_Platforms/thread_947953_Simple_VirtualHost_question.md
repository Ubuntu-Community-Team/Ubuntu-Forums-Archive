---
title: "Simple VirtualHost question"
date: 2008-10-14
forum: Server Platforms
---

### Post by adam35413 on 2008-10-14
I am trying to setup two sites on the same server using virtual hosts.  I have read several different posts and guides, and I set up two sites in the sites-available folder, each with different DocumentRoots and Directories.  I enabled both, but when I got to the first site I get directed to the second, and I get directed to the second site if I go to the second address.  I disabled the second site and then I was able to go to the first site again:

Before:
server1.com ---> First site

After:
server1.com ---> Second site
server2.com ---> Second site

Any thoughts?

---

### Post by mbeach on 2008-10-14
double check everything (ServerName, documentRoot).  How are you testing this - are you browsing to the ip on your local lan or using the domain names?  Take a look in your access log. 

I'll add (and you probably know this already) that you need to :
sudo /etc/init.d/apache2 reload
after configuration changes.

---

### Post by mbeach on 2008-10-14
post the output from ```

 grep -i -e virtualhost -e ServerName -e documentroot /etc/apache2/sites-enabled/*

```

---

### Post by adam35413 on 2008-10-14
Wow.  The issue I had was that I did not have any server name.  I had server alias, but not name so either way it resolved to server2, even if I went to server1.  Putting in the ServerName has fixed my issue.  Thanks guys.

See, I told you it was easy ;-).

---

