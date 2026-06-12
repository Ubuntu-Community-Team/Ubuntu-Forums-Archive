---
title: "web server keeps redirecting to 192.xxx,xx/ outside of the home network"
date: 2013-01-27
forum: Server Platforms
---

### Post by Ki6465 on 2013-01-27
I use Ubuntu 12.04.1 LTS webserver with apache. When I access my webserver on my home network using [http://192.xx.x/wordpress](http://192.xx.x/wordpress) I can access wordpress and all its links on the page without any problem. But when I access the server outside of my network [http://mypublicip/WordPress](http://mypublicip/WordPress) the page loads fine but all the links on the website point to [http://192.xx.x/WordPress/example](http://192.xx.x/WordPress/example). It gives me an error 504:gateway time-out. 

Is there any way to fix this ? 
I have DMZ enabled on the router.

---

### Post by thnewguy on 2013-01-27
Sounds to me like you need to update the hostname settings in your Wordpress installation. Login to your Wordpress site with your admin account. Go to the Settings tab and bring up General Settings. There are two boxes there containing URLs, "Wordpress address" and "Site address". To make your website accessible to the outside world, change these to your public address.

This may have the site effect of preventing you from accessing your website from your local network, depending on how your router handles internal requests. If you need to access your website from the local network and your router redirects local requests then you can access your local web server using a web proxy.

---

### Post by chrisguk on 2013-01-27
> **Ki6465 said:**
> I use Ubuntu 12.04.1 LTS webserver with apache. When I access my webserver on my home network using [http://192.xx.x/wordpress](http://192.xx.x/wordpress) I can access wordpress and all its links on the page without any problem. But when I access the server outside of my network [http://mypublicip/WordPress](http://mypublicip/WordPress) the page loads fine but all the links on the website point to [http://192.xx.x/WordPress/example](http://192.xx.x/WordPress/example). It gives me an error 504:gateway time-out. 

Is there any way to fix this ? 
I have DMZ enabled on the router.

This would be a hard question to answer without seeing the contents of the following:

Your /etc/hosts file
The file where you have declared your Virtual host block
and the .htaccess file in the root of the /wordpress on your webserver.

I am assuming you don't have the machine setup with DNS?

---

### Post by Ki6465 on 2013-01-27
> **chrisguk said:**
> This would be a hard question to answer without seeing the contents of the following:

Your /etc/hosts file
The file where you have declared your Virtual host block
and the .htaccess file in the root of the /wordpress on your webserver.

I am assuming you don't have the machine setup with DNS? 

No i don't have it set up with DNS. But here is whats inside the host file 

127.0.0.1      Localhost
127.0.1.1      WebServer-DELL

# the following lines are desirable for IPv6 cable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ffo2::2 ip6-allrouters


How do i access the .htacces file ?

---

### Post by chrisguk on 2013-01-27
If you are using the standard out of the box apache2 server setup then you need the following:

in the hosts file:

```


127.0.0.1 Localhost
127.0.1.1 WebServer-DELL
172.0.1.2 wordpress


```


In the /etc/apache2/sites-available create a file called wordpress:

```
sudo nano /etc/apache2/sites-available/wordpress
```

Place this code inside it and save:
```


<VirtualHost 127.0.1.2:80>
        ServerName wordpress
        ServerAlias www.wordpress
        ServerAdmin admin@wordpress
        DocumentRoot /var/www/wordpress
        <Directory /var/www/wordpress>
                Options FollowSymLinks
                AllowOverride All                                                                                             
        </Directory>                                                                                                          
                                                                                                                              
</VirtualHost>       


```

Ensure you have MOD rewrite enabled which worpress relies on:

```


sudo a2enmod rewrite


```

Ensure that you have put all of the web for wordpress in the following folder:

```


/var/www/wordpress


```

Enable the site

```


sudo a2ensite wordpress


```

The restart the apache server:

```


sudo service apache2 restart


```

You should now be able to navigate to the wordpress installation using this:

```


http://wordpress


```

Make sure you adjust the .htaccess file inside the wordpress root folder and look for a line like:

```


RewriteBase /


```

You can follow this procedure for any other website you want to install.

---

### Post by Ki6465 on 2013-01-27
> **chrisguk said:**
> If you are using the standard out of the box apache2 server setup then you need the following:

in the hosts file:

```


127.0.0.1 Localhost
127.0.1.1 WebServer-DELL
172.0.1.2 wordpress


```


In the /etc/apache2/sites-available create a file called wordpress:

```
sudo nano /etc/apache2/sites-available/wordpress
```

Place this code inside it and save:
```


<VirtualHost 127.0.1.2:80>
        ServerName wordpress
        ServerAlias www.wordpress
        ServerAdmin admin@wordpress
        DocumentRoot /var/www/wordpress
        <Directory /var/www/wordpress>
                Options FollowSymLinks
                AllowOverride All                                                                                             
        </Directory>                                                                                                          
                                                                                                                              
</VirtualHost>       


```

Ensure you have MOD rewrite enabled which worpress relies on:

```


sudo a2enmod rewrite


```

Ensure that you have put all of the web for wordpress in the following folder:

```


/var/www/wordpress


```

Enable the site

```


sudo a2ensite wordpress


```

The restart the apache server:

```


sudo service apache2 restart


```

You should now be able to navigate to the wordpress installation using this:

```


http://wordpress


```

Make sure you adjust the .htaccess file inside the wordpress root folder and look for a line like:

```


RewriteBase /


```

You can follow this procedure for any other website you want to install.

I did all of what you told me to do but I could not find the .htaccess file.

---

### Post by chrisguk on 2013-01-27
In Ubuntu and any debian type distro any file or folder that is proceeded by a "." for example ".htaccess" suggests its a hidden file or folder.

If you are using a GUI interface then navigate to the folder, assuming you placed the installation in:

/var/www/wordpress

Then use ctrl+h on your keyboard.  This will reveal any hidden files or folders.

This is commonly used when trying to find a package from within you home folder.

If you are using command line then us the following command:

```
ls -al /var/www/wordpress
```

It will not only reveal the file but its permissions too.

**Just one quick side note:  Did you follow the steps by thnewguy too? **

---

### Post by Ki6465 on 2013-01-27
> **chrisguk said:**
> In Ubuntu and any debian type distro any file or folder that is proceeded by a "." for example ".htaccess" suggests its a hidden file or folder.

If you are using a GUI interface then navigate to the folder, assuming you placed the installation in:

/var/www/wordpress

Then use ctrl+h on your keyboard.  This will reveal any hidden files or folders.

This is commonly used when trying to find a package from within you home folder.

If you are using command line then us the following command:

```
ls -al /var/www/wordpress
```It will not only reveal the file but its permissions too.

**Just one quick side note:  Did you follow the steps by thnewguy too? **

No i haven't yet but do i do his too ? 

Here is what i got (screenshot) from the cmdline since i dont have any gui installed.

---

### Post by chrisguk on 2013-01-27
okay thats probably because you havent selected user friendly URLs in the WP admin panel.

But providing you have the LAMP stack fully installed it should work.

LAMP =

apache2 server
mysql server and client
php5
phpmyadmin as an extra if you need it

The wordpress installation needs to be in the /var/www/wordpress folder as declared in the virtual host block.

Just out of interest if you dont have a GUI application how are you seeing the website in a browser?

---

### Post by Ki6465 on 2013-01-27
> **thnewguy said:**
> Sounds to me like you need to update the hostname settings in your Wordpress installation. Login to your Wordpress site with your admin account. Go to the Settings tab and bring up General Settings. There are two boxes there containing URLs, "Wordpress address" and "Site address". To make your website accessible to the outside world, change these to your public address.

This may have the site effect of preventing you from accessing your website from your local network, depending on how your router handles internal requests. If you need to access your website from the local network and your router redirects local requests then you can access your local web server using a web proxy.

It worked but is there a way to access the website with out using a proxy?

---

### Post by chrisguk on 2013-01-27
> **Ki6465 said:**
> It worked but is there a way to access the website with out using a proxy?

Is the site accessed on a LAN?

If so then you can add the IP to the webserver to the hosts file I believe but dont quote me.

Or you could go all out and make it a DNS server.  Ive just made a tutorial about that here:

[http://ubuntuforums.org/showthread.php?p=12477143#post12477143]("http://ubuntuforums.org/showthread.php?p=12477143#post12477143")

---

### Post by Ki6465 on 2013-01-27
> **chrisguk said:**
> okay thats probably because you havent selected user friendly URLs in the WP admin panel.

But providing you have the LAMP stack fully installed it should work.

LAMP =

apache2 server
mysql server and client
php5
phpmyadmin as an extra if you need it

The wordpress installation needs to be in the /var/www/wordpress folder as declared in the virtual host block.

Just out of interest if you dont have a GUI application how are you seeing the website in a browser?

I'm using my other computer with win xp on my local network.

---

### Post by Ki6465 on 2013-01-27
Alright thank you for the help though. I'll make a DNS server then.

---

### Post by anonymouschief on 2013-01-31
Try replacing the IP address with an asterisk in the virtual host section of your Wordpress site's apache config file. The config file I am referring to is located at \etc\apache2\sites-available. Reload apache after making the change. Make a backup of the file b4 making changes, just in case.

This will get all the URLs to be relative to which ever ip address owas used to access the WordPress site since the asterisk tells the wordpress site to listen on all interfaces, that is, loopback, local IP, and public IP.

---

