---
title: "apache2 &amp; dynamic IP &amp; blocked port 80"
date: 2006-03-13
forum: Server Platforms
---

### Post by ephman on 2006-03-13
hi,

i've setup jinzora (a media streaming server) so that i can listen to my collection at my office, and apache2, and i can only for now stream locally (which was a feat so i'm proud).  i'm really new to webservers and the such (never set one up before), and could use a little help with the next step, i've googled around and can't make sense of what i'm reading.  i bought a domain, my port 80 is blocked, with a dynamic ip, and would like to setup an apache2 server.  any help on what i need to do to setup my webserver would be so appreciated.

thank you very much,

ephman

---

### Post by DarthMandeep on 2006-03-13
I also have an ISP that blocks incoming port 80. I've also got a dynamic IP.

I setup Lighttpd, a small web server, on my primary Linux server, then set my router to redirect incoming port 81 to port 80 on that computer.

This way I can type in my public IP in a web browser, and as long as I add :81 to the end of it, I'll get to my web page. 

Then I got a dyndns.org free account and set it up to forward mandeep.webhop.org to my public IP. My router has a DDNS client built in that tells dyndns what my IP is every time it changes, but you can also use ddclient on the server to do that.

This way I don't have to remember the public IP, I just type the name in and away it goes.

It's something similar to what you're doing, streaming my media to anywhere using just a web browser.  Works fine for music and video.

The best part is it doesn't cost anything other than time and the ISP bill I'm already paying.

Hope that helps a little. You just need to setup a dynamic dns account with dyndns or a similar provider for free, and forward a port other than 80 through your router to be accessible on the Internet.

---

### Post by ephman on 2006-03-14
hi,

ok thanks for the info.  i'm hoping now that somebody can show me an example of how i should setup the apache server with the posting's above description.  i'm pretty lost when it comes to this, eventhough i've read some of the apache documentation.  any help would be so appreciated.

thanks,
ephman

---

### Post by smarchini on 2006-03-14
edit ports.conf under /etc/apache2

add line listen 81

then restart apache2

---

### Post by ephman on 2006-03-14
really?  that's all.  i don't have to configure anything to anything else in apache?  life should be good after that?  ok cool.  so the url will be [www.website.com:81](www.website.com:81)  that'll be great thanks so much, i know these are basic questions so thank you.

be well,
ephman

---

