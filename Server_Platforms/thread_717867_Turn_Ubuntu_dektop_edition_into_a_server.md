---
title: "Turn Ubuntu dektop edition into a server"
date: 2008-03-07
forum: Server Platforms
---

### Post by ftpvk on 2008-03-07
I have the latest ubuntu desktop version on my laptop and I want to use my computer as a server for a very simple website and log the people who view it. 

Please suggest what I can do

---

### Post by insineratehymn on 2008-03-07
Install Apache2, find a dynamic IP thingy (like no-ip), and then place your website in /var/www.

---

### Post by HermanAB on 2008-03-07
You don't have to do anything.  There is no real difference between Linux as a desktop and Linux as a server. 

Simply use synaptic and install whatever services you want.

If your server is installed in a dark corner of a dank data centre, then you may choose to stop Xorg with 'init 3', since there won't be a keyboard, mouse or screen attached to it, but before you do that, ensure that you have sshd installed and working.

Cheers,

Herman

---

