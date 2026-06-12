---
title: "Masking Website by IP"
date: 2009-03-07
forum: Server Platforms
---

### Post by armymil on 2009-03-07
This is harder to type out and harder to research in google because I dont know how to find the right key words.

My buddy runs a webserver. He runs it on port 8080 because he has residential internet. However, when you access IP:8080 it returns another website. He is running ubuntu server. When you go to example.com, it will resolve correctly. So I used Wireshark, and I am able to determine my packets are going to IP:8080 when going to example.com. I have asked him how he is doing this but claims "it is a secret." Jerk.

Is there actually a way to hide a webserver behind an IP and port number using another website as a front so people cant access IP:8080 and gather important information but can access through example.com? I want to try to do this with my server.

Thanks!

---

### Post by drubin on 2009-03-08
Hi 

This is called virtual hosting.
[http://www.debuntu.org/2006/02/22/7-virtual-hosting-using-apache-2](http://www.debuntu.org/2006/02/22/7-virtual-hosting-using-apache-2)

Basically when you send a request to a server it connects to a IP address but passes the host name you mention in the URL. Apache uses this host name to determine which site you would like to see and shows you that.

You can copy the host file in  /etc/apache2/sites-available/default to  /etc/apache2/sites-available/myserverhostname

and by simply changing  DocumentRoot /var/www/ to where you would like *these* documents/website to sit. 
then change ServerName localhost to ServerName YourServerNameYouWant


Hopefully this helps. You to search for what you are looking for. You will of course need dns to point to your IP.

---

### Post by armymil on 2009-03-09
Thank you! You answered my question. Of course DNS I understand and wont have any problems on that end.

---

### Post by snek on 2009-03-09
Might I suggest the wonderful, wonderful articles from SliceHost? :)
I run an Ubuntu VPS with them and configured my virtual domains myself thanks to their articles.
The articles you'd be most interrested in are these I think:
[http://articles.slicehost.com/2007/9/17/introduction-to-virtual-hosts](http://articles.slicehost.com/2007/9/17/introduction-to-virtual-hosts)
[http://articles.slicehost.com/2008/12/17/ubuntu-intrepid-apache-virtual-hosts-1](http://articles.slicehost.com/2008/12/17/ubuntu-intrepid-apache-virtual-hosts-1)
[http://articles.slicehost.com/2008/12/17/ubuntu-intrepid-apache-virtual-hosts-2](http://articles.slicehost.com/2008/12/17/ubuntu-intrepid-apache-virtual-hosts-2)

Good luck! :)

---

### Post by drubin on 2009-03-09
> **snek said:**
> Might I suggest the wonderful, wonderful articles from SliceHost? :)
I run an Ubuntu VPS with them and configured my virtual domains myself 

Thanks those are pretty nice how to's

---

### Post by daboroe on 2009-03-09
i like these articles. they are very very helpful.

---

