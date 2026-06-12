---
title: "Internet Encryption"
date: 2009-01-18
forum: Security
---

### Post by Black Razor on 2009-01-18
I was thinking.  I know its possible, but I don't have the know how to set it up.  What I would like to do is funnel all of my network traffic into a single packet stream which is encrypted using a common used encryption method so that ALL of my internet traffic is encrypted and hidden from my ISP.  I know it works in theory but how do I do this?

---

### Post by Dr Small on 2009-01-18
The destination server must support and provide the encryption method, such as SSL. This is basically what is happening when you connect to a site via HTTPS (SSL), but the server must initate the encrypted handshake in order to be able to send encrypted packets to it.

---

### Post by kevdog on 2009-01-18
Could you be more specific?  Somewhere along the chain communication is going to have to become unencrypted.  There is SSH tunneling.

---

### Post by HermanAB on 2009-01-19
You need to read the Snail Book:
[http://www.snailbook.com/](http://www.snailbook.com/)

Cheers,

Herman

---

### Post by pdtpatrick on 2009-01-19
Are you trying to use the internet while being anonymous ?? if so then try Tor which is good. I believe it masquerades your IP so people cant trace where the IP is coming from.

---

### Post by Tubes6al4v on 2009-01-19
I am sure you could get an encrypted proxy server if you don't want to put up with the slow Tor times.

If it is single use, you could use Anonym.OS It is a live CD based on BSD with tor and a bunch of other security stuff loaded on there. So you use it, and the only trace is if they could grab you ram within a few seconds of shutting down, freeze it and try to read the data. That or you get caught with your pants down, so to speak.

---

### Post by stefangr1 on 2009-01-19
The sort answer: no, it's not possible in a workable manner.

You could set it up like this:
- on the server side install openssh-server and the squid proxyserver
- on the client side configure Firefox to use remote DNS (otherwise they can still see what sites you're visiting), and configure it to connect to a localhost proxyserver.
- login with putty or another ssh client on the server, and forward the traffic from localhost to the proxy server.

In this manner, you are probably as secure as you can be. There's however one little but... You need control over the server...

Then there are tons of other means to hide internet traffic, but they are usually slow and not really secure (e.g. they provide a false sense of security). Lets think about the anonymous proxy servers in China etc.: why would some vague government agency in China (or basically anyone) devote costly bandwith and server capacity to allow YOU access trough their servers?

---

### Post by pdtpatrick on 2009-01-19
Very good point :)

---

