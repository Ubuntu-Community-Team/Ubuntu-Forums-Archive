---
title: "Apache virtualhost issues"
date: 2011-02-14
forum: Server Platforms
---

### Post by Sewerraccoon on 2011-02-14
I've been working on a server to prepare it for more than one website It will be hosting. I've got one domain name for the site that's already on it, and the domain name assigned to every machine in the school. Both of those names are forwarded to the machines single IP. When a new site is added, they'll take out another appropriate domain name for the site for us. I set one virtual host to host the page we already have set up, and to test the configuration out I made a simple HTML test page and assigned another virtual host to it. After a little bit of tweaking, I thought I had everything sussed out, but something strange started to happen. When I type in the name for the test site, I get the test site, that all works fine, but when I type in the name for the site we're already hosting, I get the proper title for the site (up in the browser title and the tab), but the content in the main window is that of the test site. I'm stumped. I checked all the sites files, i made sure that the virtual host was pointing to the correct document root, but couldn't find anything. Any input would be most appreciated. I don't have access to the machine right now, but I'll throw my virtual hosts config up in a post after this.

---

### Post by Sewerraccoon on 2011-02-14
Here's my virtualhosts file
```
NameVirtualHost [Correct IP]:80
###SEHS Robotics virtual host file###
<VirtualHost [Correct IP]:80>
        ServerAdmin webmaster@localhost
        ServerName [Domain1].org
        ServerAlias [Domain1].org
        #DocumentRoot /var/www/       
        DocumentRoot /home/sehsadmin/www/robotics
        CustomLog /var/log/apache2/southroboticsorg.log combined
</VirtualHost>
<VirtualHost [Correct IP]:80>
       ServerAdmin webmaster@localhost
        ServerName [Domain2].edu
        ServerAlias test.org
        DocumentRoot /home/sehsadmin/www/test/
        CustomLog /var/log/apache2/testorg.log combined
</VirtualHost> 
```

And for good measure, I've attached my apache2.conf to this post (I had to swap the .conf for .txt to appease the attachment system).

---

### Post by volkswagner on 2011-02-14
The sticky section of this forum has excellent [links]("http://ubuntuforums.org/showthread.php?t=1046738") to resources.

Did you restart apache2 after making the change?  Did you get any errors, or any pertinent info in /var/log/apache2/error.log?

I know there is usually more than one way to skin a cat.

My setup consists of the following.

Each virtual host gets a unique file in /etc/apache2/sites-available.  I then enable with 

```
sudo a2ensite newfilename
```

```
sudo /etc/init.d/apache2 reload
```

Along with the above I have in /etc/apache2/httpd.conf

```
NameVirtualHost *

```

If all your sites will be placed on this one machine and all running on port 80 this will work.  You will also not need the reference in your individual host file.

Each of your host files should look like this.


/etc/apache2/sites-available/domain1
```
###SEHS Robotics virtual host file###
<VirtualHost *>
        ServerAdmin webmaster@localhost
        ServerName Domain1.org
        ServerAlias www.Domain1.org
        #DocumentRoot /var/www/       
        DocumentRoot /home/sehsadmin/www/robotics
        CustomLog /var/log/apache2/southroboticsorg.log combined
</VirtualHost>

```


/etc/apache2/sites-available/test1
```
<VirtualHost *>
       ServerAdmin webmaster@localhost
        ServerName Domain2.edu
        ServerAlias test.org
        DocumentRoot /home/sehsadmin/www/test/
        CustomLog /var/log/apache2/testorg.log combined
</VirtualHost>
```


Again if you need custom reference to network interfaces or ip address, this setup will need more work.

---

### Post by Sewerraccoon on 2011-02-16
I have restarted the service several times, and the machine has been restarted at least once since I've started this endeavor. I'm still not entirely sure what the "NameVirtualHost" directive does, but I will try moving it to "httpd.conf" as opposed to my VirtualHosts file, and change it from the IP to wildcard. My VirtualHosts file is inside the "site-enabled" so there shouldn't be an issue there. Let me know if any other additional config files could give me clues. I should've mentioned this before, but for the test site i'm using the domain name assigned by the school, "[hostname].sehs.lane.edu". I'm not entirely sure how it would differ from the domain name they're actually paying for, admittedly, I know very little about their network. 

PS: Thanks for the reply :)

---

### Post by rudelgurke on 2011-02-16
Did you run "apache2 -STD DUMP_VHOSTS" on the command line to verify your configuration ?

---

### Post by James78 on 2011-02-16
> **Sewerraccoon said:**
> I have restarted the service several times, and the machine has been restarted at least once since I've started this endeavor. **I'm still not entirely sure what the "NameVirtualHost" directive does**, but I will try moving it to "httpd.conf" as opposed to my VirtualHosts file, and change it from the IP to wildcard. My VirtualHosts file is inside the "site-enabled" so there shouldn't be an issue there. Let me know if any other additional config files could give me clues. I should've mentioned this before, but for the test site i'm using the domain name assigned by the school, "[hostname].sehs.lane.edu". I'm not entirely sure how it would differ from the domain name they're actually paying for, admittedly, I know very little about their network. 

PS: Thanks for the reply :)
[http://httpd.apache.org/docs/2.2/mod/core.html#namevirtualhost](http://httpd.apache.org/docs/2.2/mod/core.html#namevirtualhost)

---

