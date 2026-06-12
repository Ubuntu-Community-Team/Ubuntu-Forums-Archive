---
title: "Location of Web HTML pages for Localhost to see"
date: 2008-09-06
forum: Server Platforms
---

### Post by JKHinton CPBD on 2008-09-06
Hello ya'll,

I am trying to move my existing web pages that I have been working on from a Windows XP Testing Server to a Ubuntu Server edition w/Kubuntu desktop. I have the Apache server running and have found the /root/var/www/ folder with the test Index.Html and testing with my browser running Localhost I get the It Works HTML page so this far we're OK.  I then create a folder called it ADWeb and placed it in the root/var/www/ADWeb I then copied my
existing Web pages and data into this folder.  If I put these in the root/var/www folder and delete the test Index.Html I can see my web pages starting with my Index.HTML when I run Localhost in the browser.  

Now to the question how do I make the LocalHost look inside the new ADWeb folder rather than the www folder? I know I have to change something in the Apache2.conf but I don't know what? Do we need to add a Modules if so which one? or just change some of the wording in the config file?

Any Help will be appreciated Thanks in advance

---

### Post by lazyart on 2008-09-07
Quick answer - [http://localhost/ADWeb](http://localhost/ADWeb)

You should create a Virtual Host configuration in the /etc/apache2/sites-available directory, then create a link back to it in /etc/apache2/sites-enabled

The virtual host config will tell apache what port the page should be served on, what directory it should work from (called the DocumentRoot-- what you're looking for here) the name, location of error log.... a bunch of info. [It's documented pretty well]("http://httpd.apache.org/docs/2.2/vhosts/").

---

