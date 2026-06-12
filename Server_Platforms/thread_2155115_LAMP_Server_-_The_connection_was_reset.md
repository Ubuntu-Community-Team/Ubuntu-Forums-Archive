---
title: "LAMP Server - The connection was reset"
date: 2013-06-17
forum: Server Platforms
---

### Post by gazfocus on 2013-06-17
We are using a LAMP server for development before making changes to our live site and the LAMP server has been working fine for the past year or so, since setting it up. However, a couple of weeks ago, it stopped working in that whenever I go to [http://ipaddress](http://ipaddress) in any browser, I get 'The connection was reset'.

I'm still able to ssh/ftp to the server and can still ping the server but just cannot load anything in the browser. I have tried restarting Apache2 but get an error saying Access is denied.

Any help would be much appreciated.

---

### Post by SeijiSensei on 2013-06-17
What do you see in /var/log/apache2/error.log?

Is there an SQL server involved in this sitez?  Is it running?

---

### Post by romeroc24 on 2013-06-17
Try

Remove:

sudo apt-get --purge remove apache2
sudo apt-get autoremove

Reinstall:

sudo apt-get install apache2
sudo /etc/init.d/apache2 restart

good luck

---

