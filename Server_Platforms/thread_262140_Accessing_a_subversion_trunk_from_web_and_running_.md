---
title: "Accessing a subversion trunk from web and running PHP"
date: 2006-09-21
forum: Server Platforms
---

### Post by marlun on 2006-09-21
Hello!

Quick:
I want to be able to go to [http://myserverip/myproject](http://myserverip/myproject) which will run the php code that is inside the trunk of a subversion repository.

Description: 
My repository is in /var/svn/myproject and my web server uses /var/www. I want to be able to go to [http://myserverip/myproject](http://myserverip/myproject) which will run the php code that is in /var/svn/myproject/trunk. I don't want to access the code, I want it to run as a normal php site.

Is this possible with a <Location /myproject></Location>? Or do I have to use VirtualHosts? I would like to not use VirtualHosts since I don't understand them and I've only got a server with dynamic ip and a no-ip account.

Thanks in advance!

-Marlun

---

### Post by marlun on 2006-09-22
I'm told it should be possible with apache dav_svn but I don't know how. No one who knows how to do this?

---

### Post by Miademora on 2006-09-24
I dont think thats possible. You can however setup a svn script wich checks your repository everytime out or at least updates it into the webserverdirectory.

Copy **repository/hooks/post-commit.tpl** to **repository/hooks/post-commit** and make it executable.

Edit **repository/hooks/post-commit** and ad the following to the end:

```
cd /var/www/website
svn update --username=test --password=test
```

I checked my repository out 1 time in /var/www/website before this worked

---

### Post by marlun on 2006-09-24
Thank you very much, I havn't tested it yet but I will and I hope it works =)

---

