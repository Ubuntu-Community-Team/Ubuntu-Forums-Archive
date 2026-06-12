---
title: "Setting up a Server help"
date: 2007-11-25
forum: Server Platforms
---

### Post by s3lnt0 on 2007-11-25
Hello,

I am somewhat new to linux and the other day tried to set up a server using Ubuntu 7.10 Server Edition. I followed the guide 

[URL="http://www.howtoforge.com/perfect_server_ubuntu7.10"]
http://www.howtoforge.com/perfect_server_ubuntu7.10[/URL]

which worked and then installed Webmin which also worked and I can log in. I concluded that I have php5 working and I can bring up phpMyAdmin. The problem is that I don't really know to much about servers and I would like to run a live website off of it. How exactly would I do this? I tried searching around for guides, etc. but can't seem to figure it out.

---

### Post by eggdeng on 2007-11-25
If you have installed everything properly, you are already serving a website. You can access it by typing your private IP in the the address bar of any box on your local network.
A good idea is to set up ssh access to the server from your production box. See for example [https://wiki.ubuntu.com/SSHHowto]("https://wiki.ubuntu.com/SSHHowto")
To put up content, basically just save your html or php documents to the /var/www directory of the server; your home page should be called index.html, or index.php.
If you want your site to be accessible from the web, you will need to forward port 80 on your router to the server. You can acquire & set up  a domain name at [www.domaindirect.com]("www.domaindirect.com") or any of hundreds of other sites.
These are very rough and ready tips as the range of questions raised is potentially huge but I hope they help to get you started. Good luck!

---

### Post by s3lnt0 on 2007-11-25
Thanks!

How would I set up a domain name though? Does have to do with the DNS?

---

### Post by prodezigner on 2007-11-25
It deals with your external IP (check out [www.ipchicken.com](www.ipchicken.com))

If you have a router just make sure you have port 80 forwarded to the machine your hosting on and when you setup a domain use your IP address and it'll sync up.

---

### Post by s3lnt0 on 2007-11-25
I got it working. I forwarded port 80 on the router to my internal ip and then used zoneedit.com to create name servers for my domain and added the external ip of my router. Thanks for the help.

---

### Post by mattc908 on 2007-11-25
Easy guide I created: [http://insightahoy.com/forum/viewtopic.php?t=5](http://insightahoy.com/forum/viewtopic.php?t=5)

---

