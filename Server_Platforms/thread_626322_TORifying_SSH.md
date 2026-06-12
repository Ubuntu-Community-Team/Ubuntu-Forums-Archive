---
title: "TORifying SSH"
date: 2007-11-28
forum: Server Platforms
---

### Post by The Tronyx on 2007-11-28
Hello everyone, I have been using this link as a reference for TORifying SSH but not having a lot of luck as this is my first time working with TOR.

[http://itnomad.wordpress.com/2006/09/28/tor-howto-using-tor-through-a-ssh-tunnel/](http://itnomad.wordpress.com/2006/09/28/tor-howto-using-tor-through-a-ssh-tunnel/)

> 
Next, check if TOR uses the default port and listen-address, open /etc/tor/torrc (or where your torrc is):
SocksPort 9050
SocksBindAddress 127.0.0.1

After doing that I have confirmed that those settings are correct.  I run into problems with the next part and I think it might be the lack of sleep causing me to read this incorrectly.

> 
Now it all depends on if you&#8217;re using openssh or putty. With openssh it&#8217;s very simple. Open a terminal and log in to the remote-host:
host2$ ssh -L 9050:127.0.0.1:9050 user@host

If I run  "ssh -L 9050:127.0.0.1:9050 user@host" to a machine, successfully log in and run the who command, it displays my actual IP address.

What is it about this document that I am reading incorrectly?  Any help is greatly appreciated so thanks in advance!

---

### Post by The Tronyx on 2007-11-29
Bump.

---

### Post by bodhi.zazen on 2007-11-30
solved over irc.

For the benefit of others :

SSH : [http://www.antagonism.org/anon/ssh-tor.shtml](http://www.antagonism.org/anon/ssh-tor.shtml)

download connect.c :

			[http://www.meadowy.org/~gotoh/ssh/connect.c](http://www.meadowy.org/~gotoh/ssh/connect.c)

---

