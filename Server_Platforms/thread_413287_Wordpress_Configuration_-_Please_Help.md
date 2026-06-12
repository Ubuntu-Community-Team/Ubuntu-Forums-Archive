---
title: "Wordpress Configuration - Please Help"
date: 2007-04-19
forum: Server Platforms
---

### Post by Xarok on 2007-04-19
I'm trying to set up a set up a site for my friend and he wants a bloggin section.

I got wordpress set up on my Ubuntu Server 6.06 and I can login and view the site just fine from my laptop on the same LAN as the Ubuntu Server. It works if I go to the domain blessedbyheart.com or if I directly go to my router's IP. It's strange though that when I navigate through the blog the domain name "blessedbyheart.com" changes to the server's LAN ip (192.168.1.111)

But if I try accesing from outside my LAN (ie: from my school) I cannot acces my wordpress section blessedbyheart.com/wp/.

Sometimes the HTML page loads, but the CSS and images do not.

If the HTML loads and I try to click on "login" for example the url changes from [http://blessedbyheart.com/wp/](http://blessedbyheart.com/wp/) to [http://192.168.1.111/wp/wp-login.php](http://192.168.1.111/wp/wp-login.php)

At the time of installing wordpress I had not given apache a ServerName in etc/apache2/apache2.conf
Could this be the problem?

Right now I've added the line 'ServerName blessedbyheart.com' within the apache2.conf but nothing changed.

I also read somewhere about changing the /etc/hosts file by adding the domain to the line
127.0.0.1 localhost
so that it would look like:
127.0.0.1 localhost blessedbyheart.com
This also didn't help though...

Do you suggest that I just re-install the Ubuntu Server and make sure to add the ServerName before the installation of wordpress?

Thanks very much if you can help.

Xarok
Edit/Delete Message

---

