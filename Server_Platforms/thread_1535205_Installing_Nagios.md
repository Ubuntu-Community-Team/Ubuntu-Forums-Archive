---
title: "Installing Nagios"
date: 2010-07-20
forum: Server Platforms
---

### Post by MacGoose on 2010-07-20
Hi!

I have been running a webserver for a time now.  And for fun I thought I would use Nagios for monitoring it.  But the installation instruction says install this on webserver01 and that on webserver02.  I only have one server and want to monitor it remotely from a simple browser.  Is this possible or does Nagios need at least two separate servers?  Can't it just run it on my one server?

TIA!

, MacGoose

---

### Post by richardjh on 2010-07-20
It can monitor the same server that it is running on yes.

Once you learn Nagios you will be glad you did. It is not a simple thing to get started with.
However it is very powerful and almost the standard monitoring application. 

It is also often mentioned as a requirement in vacancies for system administration jobs so to have at least a basic understanding will put you in good stead in the long term.

There is a quick start guide specifically for Ubuntu at 

[http://nagios.sourceforge.net/docs/3_0/quickstart-ubuntu.html](http://nagios.sourceforge.net/docs/3_0/quickstart-ubuntu.html)

This is probably not the best way to go, as you can install nagios from the repos.

It does guide you on sample configuration files though and how to get started quickly.

---

