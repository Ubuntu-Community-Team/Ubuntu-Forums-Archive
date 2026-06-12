---
title: "I am a bit lost.."
date: 2006-11-26
forum: Server Platforms
---

### Post by thamarok on 2006-11-26
Hello!

About two hours ago I made a new installation of the Ubuntu Server Edition 6.10 Edgy Eft. I chose "LAMP Server" in the installation, so I should have Apache now.

I installed the K Desktop Environment (because this server is just for testing so I wanted a graphical interface) and I was so much busy with configuring my desktop that I forgot that I have a LAMP Server.

And now I am lost: Where should I put my php files and how can I access them?

Thanks!

---

### Post by tturrisi on 2006-11-26
/var/www/
access it by [http://address/](http://address/)
OR
/home/user/public_html/ (public_html dir must be created)
access it by [http://address/~username/](http://address/~username/)

---

### Post by thamarok on 2006-11-26
Thank you!
I was a little unsure if the php scripts should go to /var/www/ but now as I copied them there, they work :mrgreen: 

Also, I found another way to access my server: [http://*Hostname](http://*Hostname)*.home.net/
(replace *Hostname* with your hostname)

Ubuntu is so much fun to use :p 
I have never installed a LAMP Server this easily :KS

---

