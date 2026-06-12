---
title: "Ubuntu 14.04 / Apache / Virtual Host Configuration"
date: 2016-02-17
forum: Server Platforms
---

### Post by Daniel_Clarke on 2016-02-17
Hey,

I am new to both Linux and Apache so I apologize if I am in the wrong place or if I do not know much regarding this topic, please bare with me.

My ultimate goal was to create a server to host multiple websites from, specifically Joomla (CMS) based websites. I was successful at setting up Ubuntu 14.04 LTS, LAMPP. I was able to get my first Joomla site without issue. Here is where I ran into issues. I have read about Virtual Host here:

[https://httpd.apache.org/docs/current/vhosts/examples.html](https://httpd.apache.org/docs/current/vhosts/examples.html)

However, I am not sure what files I am suppose to be editing with these settings. Can someone please walk me through configuring Apache to allow me to host multiple sites from a single IP? 

Thanks in advance

-daniel

---

### Post by sandyd on 2016-02-17
Moved to *server platforms*

---

### Post by darkod on 2016-02-17
I am no apache expert but basically here is how it goes:

The most important folders are /etc/apache2/sites-available which contains .conf files for each site you want to host, and the /etc/apache2/sites-enabled where you actually do not touch anything. Enabling a site creates the needed link between sites-enabled and sites-available. Having a site .conf file in sites-available does not make it work until it's enabled.

So, in the most basic turns you can copy the default 000-default.conf in sites-available into for example domain1.conf (or domain1.com.conf if you expect to have sites with identical domain name but different TLD). Then inside that file modify the most important parameters which are:
ServerName - for example domain1.com
ServerAlias - [www.domain1.com](www.domain1.com)
DocumentRoot - the location where you want to keep the files, for example /var/www/domain1

After that enable the site and restart apache:
```
sudo a2ensite domain1 (or domain1.com) (leave out the .conf part)
sudo service apache2 restart
```

That should get that site going. I don't know joomla and I don't know if it needs separate install for each site... But for simple enabling of sites the above is all you need. Of course, you also need to DNS handling that domain to have adequate A record directed at your server public IP.

---

### Post by Daniel_Clarke on 2016-02-18
Hey,

Thanks for the post, however this is exactly what I did to get the first site going. I now want to be able to host multiple sites from a single IP. It is my understanding I am suppose to add or edit a file to add the multiple domains. Either a vhost.conf or a httpd file for Apache, I cant seem to find either of those in my systems. Any additional suggestions would be appreciated.

Thanks

-Daniel

---

### Post by SeijiSensei on 2016-02-18
Create a file called hostname.conf, e.g., [www.example.com.conf](www.example.com.conf), in /etc/apache2/sites-available.  A basic file looks like this:
```

<VirtualHost    *:80>
ServerAdmin     webmaster@example.com
DocumentRoot    /path/to/the/website/root
ServerName      example.com
ServerAlias     www.example.com
ErrorLog        logs/error_log-example
TransferLog     logs/access_log-example

<Directory      "/path/to/the/website/root">
    Options All
</Directory>

</VirtualHost>

```

Replace "/path/to/the/website/root" with the current full path to the top of the website tree, in your case the directory where index.php is stored.  Replace "example" with the appropriate entries for you site.  The use the a2ensite command and restart server as darkod wrote above.

Virtual hosts in Apache depend on the names in the ServerName and ServerAlias fields.  It will try to match those names against the hostname in the requesting URL. If it finds a match, it will use that virtualhost definition.  If it doesn't find a match, it will use the default in 000-default.conf.

---

### Post by Daniel_Clarke on 2016-02-18
Ok, will "hostname.conf" contain all the information for each of my domains? Like this:

> 
# Ensure that Apache listens on port 80
Listen 80
<VirtualHost *:80>
    DocumentRoot "/www/example1"
    ServerName [www.example.com](www.example.com)
  
    # Other directives here
</VirtualHost>

<VirtualHost *:80>
    DocumentRoot "/www/example2"
    ServerName [www.example.org](www.example.org)

    # Other directives here
</VirtualHost>


Thanks

-Daniel

---

### Post by darkod on 2016-02-18
No, one file per site. Separate .conf file for each site/domain.

If you edited the 000-default.conf to serve for your first website, you can still copy it and make adequate modification in the new file. For example:
```
sudo -i
cd /etc/apache2/sites-available
cp 000-default.conf domain2.org.conf
nano domain2.org.conf
```

Change the ServerName, ServerAlias and DirectoryRoot parameters. Also others if needed. Then enable the new site/conf file and restart apache2:
```
a2ensite domain2.org
service apache2 restart
```

That should be it.

Or simply create a new file in sites-available with the content that Sensei posted, adjust it, save and close it. Then enable the site and restart apache2. It is up to you which way you do it, the important thing to remember is one file per site. Do not specify multiple domains in the same .conf file otherwise they will all open the same site/files. On the other hand, if you want multiple URLs to open the same site content, you can use the ServerAlias to specify them. In this case there is a single .conf file for multiple URLs but that is because you want to open same content. If you want different content, create different .conf files.

---

