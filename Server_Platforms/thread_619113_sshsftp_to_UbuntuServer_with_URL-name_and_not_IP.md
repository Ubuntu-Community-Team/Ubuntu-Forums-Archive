---
title: "ssh/sftp to UbuntuServer with URL-name and not IP"
date: 2007-11-21
forum: Server Platforms
---

### Post by dqsis on 2007-11-21
Hello all! 

I have recently installed an Ubuntu Server and everything works fine. 

I would like to connect to the server (from any computer) by SSH or SFTP. When I try:
ssh [email]username@129.XX.XX.XX[/email] I have no problems what so ever. 

Nevertheless, instead of using the IP, I would like to use a different (alias) name, f.e. dqsis.net. How can I do that? This is my /etc/hosts file:

127.0.0.1       localhost
129.XX.XXX.XX   dqsis.net   dqsis
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

BUT when I try ssh [email]username@dqsis.net[/email] it doesn't work :(

Any ideas on how to proceed?

---

### Post by 1/0 on 2007-11-21
Well the computer you are using to ssh from needs to have the ip. Another approach is to use dyndns or noip. It updates a url with your IP.

---

