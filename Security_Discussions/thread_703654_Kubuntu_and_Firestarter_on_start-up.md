---
title: "Kubuntu and Firestarter on start-up"
date: 2008-02-21
forum: Security Discussions
---

### Post by TWO on 2008-02-21
I've recently just switched from Ubuntu to Kubuntu, just to give it try for a while.

I've installed Firestarter, on each system start-up I am prompted for a password in order for the program to start. 

I'd rather not have to keep entering a password each time, so I'm just wondering if anyone knows how to set the program so that it starts with the necessary permissions so that I don't have to keep entering in the password.

Thanks in advance,

TWO

---

### Post by stooshbunutu on 2008-02-21
yeah I wanna know that two

---

### Post by bodhi.zazen on 2008-02-21
First, if you are running Kubuntu you might prefer guarddog. Just a thought.

==========

Second you should NOT run firestarter all the time. Firestarter is a gui front end for your firewall, iptables. Once it is configured it remains configured even if you close firestarter or reboot.

Firestarter runs as root and is thus a security risk. Firestarter should NOT be used to monitor your network traffic.

==========

OK, if you want to run firestarter anyway, you need to configure sudo to allow you to run firestarter with no password. Sorry to be a pain about this, but I believe if you are going to configure sudo you should read and fully understand what you are doing.

See these links : 

[http://www.debian-administration.org/articles/33](http://www.debian-administration.org/articles/33)

	[http://www.gratisoft.us/sudo/man/sudoers.html](http://www.gratisoft.us/sudo/man/sudoers.html)

	[http://www.unixcities.com/sudo/index.html](http://www.unixcities.com/sudo/index.html)

If after looking at those links you have specific questions, feel free to ask.

One last thing, be sure to use visudo (which will call nano) to make changes.

---

