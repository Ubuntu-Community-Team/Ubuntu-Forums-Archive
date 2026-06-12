---
title: "Name Based Virtual Hosting Apache"
date: 2009-06-24
forum: Server Platforms
---

### Post by R.Bucky on 2009-06-24
I use Name Based Virtual Hosting on my home web server to host 3 web sites. I would like to have a sort of index page if someone types in my ip address - 24.18.97.111. I tried creating a Virtual Host using my ip, but after thinking about it, that route does not make sense.

The code below is what I use for VirtualHost config

```
<VirtualHost *:80>
ServerName domain.com
DocumentRoot /server/directory/
</VirtualHost>
```

Does anyone have suggestions? My current configuration is a standard LAMP stack using 8.04 Ubuntu.

---

### Post by dzcowart on 2009-06-24
The info you want is documented here:

[http://httpd.apache.org/docs/2.2/vhosts/name-based.html](http://httpd.apache.org/docs/2.2/vhosts/name-based.html)

exec. summary:  If you use the ip address, apache will serve up the pages that are handled by the default host on your web server.  So if you have myhost.com, domain1.com and domain2.com, and the server name (locally and in dns) is myhost.com, then the vhost for myhost.com will be the one to serve up pages...  

To do what you want setup myhost.com to provide links to domain1.com & domain2.com, or change the server name to something different (myrealserver.com) with it's requisite vhost, and then 3 other vhosts for each of your domains (This is what I typically do).

I hope this helps,

--Donald

---

### Post by CptPhillips on 2009-07-01
I couldn't find a complete tutorial in the forums so I cobbled together information I found in a few different tutorials and got vhosts working for myself. Here is what I did;

First I had to tell Apache2 that I wanted to used name based addressing with this line added to /etc/apache2/apache2.conf

```
NameVirtualHost *:80
```

Now, you can also add the virtual hosts to the same file if you want but that's not very clean and it could get hard to manage if you plan on having several vhosts. So I changed directories to /etc/apache2/sites-available and created a seperate file for each vhost. Use your favorite text editor and create a file with the following format;

```
<VirtualHost *:80>
ServerName yourhostnamehere.com
ServerAlias any_other_hostname_it_might_be_known_as.com
ServerAdmin yourname@yourhostname.com
DocumentRoot /var/www
</VirtualHost>
```

Don't change the first or last line unless you're using a port other than 80, or you have a multi-homed server and you want your trafic to come in on a specific interface. Then it might be something like this;

```
<Virtualhost 192.168.1.10:443>
```

I saved the file with the servername (yourhostnamehere.com) and then made another one for a friend who hosts his site on my box. I don't trust this guy so I made his site located in his home directory by changing the DocumentRoot atribute; That way I don't have to give him write access to the /var/www directory. This is the kind of stuff vhosts was made for!

```
<VirtualHost *:80>
ServerName mybuddyshostname.com
ServerAlias any_other_hostname_it_might_be_known_as.com
ServerAdmin mybuddysname@mybuddyshostname.com
DocumentRoot /home/mybuddy/www
</VirtualHost>
```

OK, now we've created the vhost files, but we have to enable them. The easiest way to do this is to create symbolic links in the sites-enabled directory. You could copy the files over there but again, using links makes management easier.

```
cd ../sites-enabled
sudo ln -s ../sites-available/yourhostnamehere.com
sudo ln -s ../sites-available/mybuddyshostname.com
```

All that's left now is to restart apache2 to put our changes into effect;

```
sudo /etc/init.d/apache2 restart
```

OK, now when you pop open your favorite web browser and enter yourhostnamehere.com it should go to your site in /var/www/ and when you go to mybuddyshostname.com it will go to your buddy's site located in /home/mybuddy/www/. Then if he ticks you off you can deactivate his site by deleteing the symlink and restarting apache2. You should try to forgive him though, he is your friend you know.

I hope this was helpful. Please correct me if I've done anything improperly.

---

