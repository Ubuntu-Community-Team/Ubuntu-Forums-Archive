---
title: "SSH to web server to view web pages"
date: 2009-09-24
forum: Security
---

### Post by frrobert on 2009-09-24
I am working on 3 websites that currently can not be viewed from the net but access is only set to view locally


One site is set to the address 127.0.0.100

I can ssh with the following command 

ssh -L 50000:127.0.0.100:80 [email]username@server.xxx[/email]

If I try to view the web pages 

with

[http://127.0.0.100:50000/](http://127.0.0.100:50000/)

I get a page load error.

Other developers on the team can see the pages in the browser but they are not running ubuntu.  I am running Ubuntu 8.10

I am figuring it is a configuration issue on my machine, any ideas would be appreciated

Thanks

---

### Post by wojox on 2009-09-24
What happens when you go to: [http://127.0.0.100](http://127.0.0.100)

---

### Post by frrobert on 2009-09-24
I figured it out the problem it was operator error even though you type in 
ssh -L 50000:127.0.0.100:80 [email]username@server.xxx[/email]
for the ssh command you type  127.0.0.1:50000 in the browser or localhost:50000

---

### Post by Sarmacid on 2009-09-24
Maybe it's a problem with the proxy, try adding an exception for the site you want to access.

---

### Post by staffgs1102 on 2009-09-29
Thanks for your sharing. Thanks for sharing this useful information. It's great.

---

