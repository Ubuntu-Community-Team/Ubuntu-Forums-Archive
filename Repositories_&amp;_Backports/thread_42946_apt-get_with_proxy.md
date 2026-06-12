---
title: "apt-get with proxy?"
date: 2005-06-20
forum: Repositories &amp; Backports
---

### Post by interaktiv on 2005-06-20
Hello!

I have a proxy. How may I setup a apt-get to use it?

Thank you for replies.
regards,
interaktiv

---

### Post by blind0wl on 2005-06-20
A work around I use is by editing the ~/.bashrc file, try:

```
sudo nano ~/.bashrc
```

and add this to the bottom of the file

```
http_proxy='http://username:password@yourproxy.com:80'
export http_proxy

```

Ctrl-X and save over the top, reopen a terminal and you should be good.  If its a web based proxy, you might need to authenticate first by opening firefox (with your proxy settings).  If its not an authenticated proxy omit the username and password bit and just have the [http://yourproxy.com:80](http://yourproxy.com:80). Remeber to replace the 80 with whatever port you use.  Reopen a terminal and try apt-getting from there.

HTH

Blindy

---

### Post by lorenzo on 2005-06-20
The easiest way (for me) is using synaptic. Under preferences you have network settings where you can set proxy, username, password.

Otherwise you have to set environment variables in bashrc files (something like that, sorry but don't know exactly). There are some posts in this forum with the details.

However, I think using synaptic is far easier (especially if you change environment/proxy frequently).


Ciao,
Lorenzo

---

