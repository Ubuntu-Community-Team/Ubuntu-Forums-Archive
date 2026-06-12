---
title: "How do I host a web site?"
date: 2007-05-31
forum: Server Platforms
---

### Post by victory2007 on 2007-05-31
I would like to host my web site on my ubuntu server.  I have no idea how to do this.  Does any one have some pointers.  Thanks

---

### Post by snoop on 2007-05-31
You can install webserver software like apache or lighttpd. Lighttpd will work for static pages on an old computer, for everything else, you can use apache. ubuntuguide also has instructions on how to set up apache.

---

### Post by capn_hector on 2007-06-01
i believe the server install disk has a LAMP set up (Linux Apache Mysql Php).  all you need to host a web site as snoop stated is a webserver, i would suggest apache.  then you also need to have a way for people to find it, i use dyndns for this task.  then you need content and that is some thing for you to develop using html php or any other language you wish. (you can do a pure java site if you realy want.)

---

### Post by coxy on 2007-06-01
Take a look at some dynamic DNS providers; [http://www.dyndns.org](http://www.dyndns.org) and [http://www.no-ip.com](http://www.no-ip.com) are two good ones. You can sign up for a free account that will let you choose a domain name with them. You then use either their software or a tool from the Ubuntu repos to connect to your account and update your IP address with their server. This points your domain to your server. It is a very simple task, some routers also support dynamic DNS which means you don't even need software, you just add your user details to the relevant section on your router.

Somebody mentioned above that you can build a LAMP server with the Ubuntu server CD. I would suggest you do that. Your web pages will then need to be placed into the /var/www/ folder on your server where apache will serve them from.

You will also need to foward port 80 on your router/firewall to your servers IP address.

---

