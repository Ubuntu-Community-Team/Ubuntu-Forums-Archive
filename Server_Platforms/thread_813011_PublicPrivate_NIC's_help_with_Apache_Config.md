---
title: "Public/Private NIC's help with Apache Config"
date: 2008-05-30
forum: Server Platforms
---

### Post by e30drift on 2008-05-30
Greetings!

I got shafted at work with building a new Linux web server. I say shafted because I am the only one using Ubuntu and they assume that I am a Linux GOD!  I was actually quite excited to the do the project, but I have only been using the desktop side of Linux for about 6 months.

So far I have ran through the setup from HowtoForge.com on how to setup a "Perfect Server" with 8.04.
[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts]("http://www.howtoforge.com/perfect-server-ubuntu8.04-lts")

I have the base install done, but I am having severe issues getting the web modules (ISPConfig, WebMin, Webalizer, and phymyadmin) to be setup to run on either both or one NIC interface.

I have a public interface for ISPConfig, client websites and phpmyadmin. The private IP is for only WebMin and Webalizer for administrative purposes.

Is there a way to separate these web services/modules?

---

### Post by Fire_Chief on 2008-05-30
You can typically configure multiple sites in Apache where each site is bound to a specific IP address thereby allowing you to bind some sites to the private IP range and some to the public IP range.   You could also separate the modules by port address if they are not already doing so. Some packages (such as webmin run their own web server instead of using Apache so the configuration for it will be separate also (own config files typically).

---

### Post by e30drift on 2008-05-30
> **Fire_Chief said:**
> You can typically configure multiple sites in Apache where each site is bound to a specific IP address thereby allowing you to bind some sites to the private IP range and some to the public IP range.   You could also separate the modules by port address if they are not already doing so. Some packages (such as webmin run their own web server instead of using Apache so the configuration for it will be separate also (own config files typically).


I noticed that ISPConfig and Webmin create their own Apache instance with is nice, but coming from a company that handles Window's only network, i need to shed my knowledge of IIS real quick.

Sorry to be a pain, but can I get specific instructions on how to do this?

---

### Post by Fire_Chief on 2008-05-30
Have a look at these guides to get an idea of how to setup virtual hosts in Apache.
[http://www.techmongrel.com/05/setting-up-a-virtual-host-using-apache-2-on-ubuntu-710/]("http://www.techmongrel.com/05/setting-up-a-virtual-host-using-apache-2-on-ubuntu-710/")

[http://www.debianhelp.co.uk/virtualhosts.htm]("http://www.debianhelp.co.uk/virtualhosts.htm")

Cheers!

---

### Post by e30drift on 2008-05-31
> **Fire_Chief said:**
> Have a look at these guides to get an idea of how to setup virtual hosts in Apache.
[http://www.techmongrel.com/05/setting-up-a-virtual-host-using-apache-2-on-ubuntu-710/]("http://www.techmongrel.com/05/setting-up-a-virtual-host-using-apache-2-on-ubuntu-710/")

[http://www.debianhelp.co.uk/virtualhosts.htm]("http://www.debianhelp.co.uk/virtualhosts.htm")

Cheers!


Sweeeet!!

I finally got the install done and showed the interface to my managers and they are very impressed.  Now of course I have to configure it to work with 2 very bitchy web hosts.

The interface seems quite intuitive, but I'm lost on how to even get a client on there for webhosting.

The docs for ISPConfig doesn't really tell you how to setup a web client...

Anyone know of some good step-by-step tutorials?

---

### Post by Fire_Chief on 2008-06-01
> **e30drift said:**
> 
The docs for ISPConfig doesn't really tell you how to setup a web client...

Anyone know of some good step-by-step tutorials?

Sorry...I've not worked with ISPConfig before. I do hope you find some good information on it though.

Cheers!

---

