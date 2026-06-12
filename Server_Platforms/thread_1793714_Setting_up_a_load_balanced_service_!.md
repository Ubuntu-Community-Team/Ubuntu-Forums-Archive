---
title: "Setting up a load balanced service !"
date: 2011-06-29
forum: Server Platforms
---

### Post by MyWorld on 2011-06-29
Hello everyone
 
Im very new to linux, Im used to Win Server so Im not very familiar with ubuntu server, I want to setup a load balanced service
I have three server , one as a load balancer and the other two as my web servers, now my questions is that what are the steps I need to do to setup my cluster, I dont mean the requirements, not the actual detailed configuration.
 
My other questions is that, Im gonna have my Mail server on these servers, how am I gonna setup the mail server to work with the load balancer, I mean is it possible to load balance the mail server like web server on ubuntu?
 
Thanks

---

### Post by rubylaser on 2011-06-30
Google is your friend :)  Here's a year old guide, that shows some of the steps to setup a high availability web cluster like you'd like.
[http://library.linode.com/linux-ha/highly-available-load-balancer-ubuntu-10.04](http://library.linode.com/linux-ha/highly-available-load-balancer-ubuntu-10.04)

---

### Post by MyWorld on 2011-06-30
Thanks
My main question was basically the requirements and different methods to do that and also I wanted to know what shoudl I do about the mail server when its located on the web servers ?
 
Thanks again

---

### Post by MyWorld on 2011-06-30
What about DNS, Im goin to use BIND and its located on each web server, I want to know what would happened if I wanted to sync the records int eh DNS in frist webserver with the second one , the same thing about mail server !

---

### Post by klono on 2011-06-30
Hi!
 
[COLOR=black][FONT=Verdana]Like you, I'm searching for a robust balance method. Recently I have been trying Pound with Ubuntu Server 10.4, and works great for me. I found useful this site [[COLOR=#0000ff]http://www.linuxvirtualserver.org/whatis.html[/COLOR]]("http://www.linuxvirtualserver.org/whatis.html") because you get an idea about balancing matter. But now, I have a problem with the sessions (PHP) handle :(.[/FONT][/COLOR]

---

### Post by MyWorld on 2011-06-30
Webserver is Okay, I dont undertstand in this case what would happen to Mail adn DNS server which are located on the same servers !?

---

