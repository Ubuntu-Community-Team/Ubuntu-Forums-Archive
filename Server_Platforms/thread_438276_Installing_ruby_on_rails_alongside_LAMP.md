---
title: "Installing ruby on rails alongside LAMP"
date: 2007-05-09
forum: Server Platforms
---

### Post by siefkencp on 2007-05-09
I was wondering if any one has installed apache and ruby on rails on the same box by using different ports or through some other means. Any help would be appreciated.

Thanks!
Chris

---

### Post by mazirian on 2007-05-09
Yes, of course. Rails may be called by a cgi, fastcgi or mod_ruby handler through apache2.  In fact, I've never used ROR through any other means.  I think the answer to the question you may be asking is apache2 + mod_proxy!

---

### Post by siefkencp on 2007-05-09
So just fire up mod_ruby and install?

I'm trying to check out [http://www.redmine.org/index.php?s=home](http://www.redmine.org/index.php?s=home)

The server it's on is live production so I'm a little nervous about breaking apache especially after I've gotten it working just the way I like it.

---

### Post by mazirian on 2007-05-09
mod_ruby and ror tend not be the best pair.  I think ror and fastcgi are a better pairing.  You really shouldn't be able to break apache that easily playing with this rails app.  It will have its own databases and it's own location on apache, so at worst you restart or reload apache and redmine doesn't work; but that really shouldn't hose the other web applications you're hosting or other vhosts your serving up.  I often set up a separate vhost just for playing with these sorts of things.  So you could add a testingrails.yourdomain.com to /etc/apache2/sites-available and then enable that site and then reload apache2 and your off and running.

The webrick server is really meant more for testing than actually serving the rails.  When you unpack the source there should be a "public" directory, and that's where you should point apache.  Let me know what specific questions you have and I'll try to provide some more detailed answers

---

### Post by siefkencp on 2007-05-09
Very informative -- thanks. I'll try it with an additional Vhost... 

I don't suppose you've ever tried running a tomcat server with apache on ubuntu?

---

