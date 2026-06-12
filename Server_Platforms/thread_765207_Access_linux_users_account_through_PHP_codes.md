---
title: "Access linux users account through PHP codes"
date: 2008-04-24
forum: Server Platforms
---

### Post by haryoh on 2008-04-24
I found this [LINK]("http://www.mysql-apache-php.com/") while I was looking for different information on how to install web servers.
I'll be testing this and fixing the problems as well so it can work with Ubuntu. 
Any question let me know please.

---

### Post by dmizer on 2008-04-25
it is WAY easier than that to install a webserver on ubuntu: 
```
sudo aptitude install lamp-server
```
done.

postfix - comes pre-installed from what i remember.
webmin - is not available in ubuntu repos, and has a history of security problems.
clamav - is really only needed if your server is hosting file shares to windows clients, or if you have a functional, external email server.
iptables - also comes pre-installed with ubuntu.

edit:
actually, upon reading that some more ... it's suggesting some configurations that i would consider fool hardy for live servers, not the least of which is changing the /var/www directory to 755 permissions in order to accommodate an ftp server.  see this thread for why that's a real problem: [http://ubuntuforums.org/showthread.php?t=688979](http://ubuntuforums.org/showthread.php?t=688979)

---

### Post by haryoh on 2008-04-28
That's really cool..

I have a question: Is it good to make windows the main web server and use linux as back up for files and virus scans for emails?

---

### Post by Dr Small on 2008-04-28
dmizer, could you please provide some further information as to why Webmin would be insecure?

---

### Post by dmizer on 2008-04-28
> **haryoh said:**
> That's really cool..

I have a question: Is it good to make windows the main web server and use linux as back up for files and virus scans for emails?
i suppose it depends on what your goals are, and what you need.  if windows does what you need it to do, and you can make it safe there's no reason not to.  especially if you are more familiar with it.

> **Dr Small said:**
> dmizer, could you please provide some further information as to why Webmin would be insecure?

here's the debian security information on webmin: [http://www.debian.org/security/2006/dsa-1199](http://www.debian.org/security/2006/dsa-1199) (debian security announcement)
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=343897](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=343897) (debian bug report indicating why webmin is dropped)

to be fair, the above reports are old and it does look as though webmin has been picked up again and is actively being developed: [http://www.webmin.com/changes.html](http://www.webmin.com/changes.html) this is something i was not aware of when i made the post.  though (as far as i know) the package is still not available in debian.

i have updated my post with a more accurate description.  thanks for keeping me honest.

---

