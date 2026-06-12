---
title: "The Basics"
date: 2006-04-03
forum: Server Platforms
---

### Post by Nrbelex on 2006-04-03
Hi there - I'm new to all this Linux stuff so go easy :rolleyes:. I plan to use my new Ubuntu box as a web server but wanted to do a regular install so I can still check out Ubuntu as a desktop OS. So I tried to follow the directions at [http://thehiddengrotto.com/server.php](http://thehiddengrotto.com/server.php) and I registered at [http://www.dyndns.com/](http://www.dyndns.com/) but I'm a little bit stuck. When I installed the Apache 2.0 package, I looked through all the menus and couldn't find it and I don't yet know what files to explore for these types of things in Linux. Also, at the DNS site, I'm not sure what exactly I need to enter to correctly set this up. I know I need to use their dynamic ip service and I tried entering my current ip but when I tried going to the link it created, it brought me to my router setup page :shock: so I immediately deleted everything I had done. Any and all help is greatly appreciated!

~ Brett

---

### Post by Zeroangel on 2006-04-03
Well for one thing, your apache server will run automatically as a system servive (System > Administration > Services) . Any configs you do on them must generally be done to the config files (except for mySQL which can be admistrated by both the command line and through various utilities like the web frontend phpMyAdmin or the linux gui utility mysql-admin), however if you installed the PHP and MySQL packages as well then they should work straight away without you having to do any more configuration.

You web root folder is located at /var/www/ if you have trouble writing to it, then set the permissions on the folder and contents to your username by using the terminal command:```
sudo chown -R $USER /var/www
```
and even symlink it to your liking by using a command such as```
ln -s /var/www /home/$USER
```

I apologize if this seems overwhelming to you. I assume that you want a fully featured webserver with PHP and MySQL, so ignore the parts that don't apply to you.

---

### Post by Nrbelex on 2006-04-03
Thanks - that got me past those issues - here I am now...

I'm learning through experimentation so I've registered a domain name from godaddy and created a tiny test website in my www folder. I registered at Zoneedit and am waiting for a response. I installed the ez-ipupdate package (but can't find it, if there is something to find in order to configure it). I opened port 80 on my router and can access the site from my IP address in the address bar. I don't understand how I do binding or if I need to and how to use a name server or anything. At this point, I'm thoroughly lost. Any help would be greatly appreciated. 

~ Brett

---

