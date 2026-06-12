---
title: "New to Linux and web administration"
date: 2014-05-20
forum: Server Platforms
---

### Post by Zachary_Thomas on 2014-05-20
Hello Ubuntu community!

I am new to using ubuntu as well as trying to setup a website. I am trying to setup owncloud and my understanding is I need a domain to access it from anywhere. My concern is how do I link the domain to my owncloud service? I have already installed it on ubunu server 14.04 LTS and now need help with the linking of the domain to the owncloud service. I'm braving the world of open source and hope it becomes a huge success for me!

Thanks everyone!

---

### Post by dudumomo on 2014-05-21
Hi Thomas,

If you have installed Owncould on your server, you should be able to access it directly using its IP (If on your local network, something like 192.168.x.x/owncloud should work, depending on how you install it)
You don't necessary need a domain name...but it's much more friendly than remembering your IP (Especially if you want access from outsite your local network)

You need to buy one (Like on OVH, Gandi, GoDaddy, etc..) and configure it to do a A redirection to your public IP (Not your local IP). After few hours (The time the DNS replicate) you should be able to access to your website.

Welcome in the world of Open Source! It's great and bright! Learning and discovering things everyday!

---

### Post by CharlesA on 2014-05-21
> **Zachary_Thomas said:**
> Hello Ubuntu community!

I am new to using ubuntu as well as trying to setup a website. I am trying to setup owncloud and my understanding is I need a domain to access it from anywhere. My concern is how do I link the domain to my owncloud service? I have already installed it on ubunu server 14.04 LTS and now need help with the linking of the domain to the owncloud service. I'm braving the world of open source and hope it becomes a huge success for me!

Thanks everyone!

You should be able to just create a virtualhost with whatever web server you are using and set it up that way.

[http://httpd.apache.org/docs/current/vhosts/examples.html](http://httpd.apache.org/docs/current/vhosts/examples.html)
[http://wiki.nginx.org/ServerBlockExample](http://wiki.nginx.org/ServerBlockExample)

---

### Post by kosmokramer314 on 2014-05-22
[http://ubuntuserverguide.com/2013/04/how-to-setup-owncloud-server-5-with-ssl-connection.html](http://ubuntuserverguide.com/2013/04/how-to-setup-owncloud-server-5-with-ssl-connection.html)

---

