---
title: "Securely expose machine to the internet (for someone familiar with ubuntu)"
date: 2018-11-28
forum: Security
---

### Post by schwarcu on 2018-11-28
Hi, 
I am familiar with ubuntu and networking but I never did something like this so please be understanding.

I am looking for places to start, some information about technologies and guides how can I achieve the following:

- expose my Ubuntu 18.04 machine so that I can log in to the terminal from the internet using secure connection and pefrorm normal work
- expose my web server (like Apache) to the internet in a way that it can't be used to take control over my machine (like closing all ports and ubuntu features/services that would allow someone from outside to hack into my machine)

I have no idea what Ubuntu features and services are that have to be disabled or enabled to configure such machine for a secure hosting. Can someone point me to some trusted guides?

In general I would like to be able to host my own webapp/service so that I can access it from the internet and still be able to remotely log in to the Ubuntu and perform some maintenance or setup of that webapp/service.

Thanks for the patience ;)

---

### Post by TheFu on 2018-11-28
There are at least 100,000 different web server configurations. Nobody can possibly tell you how to secure them all and some cannot be secured.

ssh access is much easier to make reasonably secure, though nothing is 100%. There are many guides for setting up ssh on Ubuntu. Pick one.  That will get it working, but that isn't the same as being secured.  [http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures) tries to explain the configuration.

BTW, none of this is Ubuntu specific.  Ubuntu is 90% Linux and 95% Debian, so the differences between Ubuntu, Debian and all other Linux systems are pretty tiny.

The quickest way to reasonably secure any service is to enable authentication and never use passwords, always use keys, for authentication.  If you want cleaner log files, don't listen on standard ports and don't allow the entire world access to your service when only 1 country needs it.

Security is about layers of protections.  Network design, firewalls (router and proxy and on the server), authentication (use strong solutions, not weak ones), and being consistent.  Make a script (written, program, or tool) for the setup and configuration, then follow it.  If you find issues with it, update the script. Continuously get better.  

Some other articles that I wrote:
* [http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server](http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server)
* [http://blog.jdpfu.com/2016/10/04/lamp-server-security](http://blog.jdpfu.com/2016/10/04/lamp-server-security)
Here's one from LHammonds, a respected forum member here - [http://hammondslegacy.com/forum/viewtopic.php?f=40&t=220](http://hammondslegacy.com/forum/viewtopic.php?f=40&t=220)

And stay patched.

---

### Post by wyliecoyoteuk on 2018-11-28
1. use a VPN
[https://www.digitalocean.com/community/tutorials/how-to-set-up-an-openvpn-server-on-ubuntu-18-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-an-openvpn-server-on-ubuntu-18-04)

2. set up a webserver using https
add a certificate (you will need a domain name) [https://letsencrypt.org/](https://letsencrypt.org/)
read all about hardening your server, there are lots of things to consider.
Sudo apt install Lynis is a good place to start

---

### Post by schwarcu on 2018-11-28
Thanks a lot, I have something to start with :)

---

