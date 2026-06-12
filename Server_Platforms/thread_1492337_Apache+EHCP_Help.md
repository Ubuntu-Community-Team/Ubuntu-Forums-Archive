---
title: "Apache+EHCP Help"
date: 2010-05-24
forum: Server Platforms
---

### Post by SirKonstantine on 2010-05-24
I know that the answer to this problem is something really easy but this is my first server and I'm a little confused at how Apache + Ubuntu + Cloud computing works together.

Right now, I have 'elliesdev.com' set up to go from my DNS to the cloud server. httpd.conf currently looks like this:
```

NameVirtualHost 173.203.100.72:80

<VirtualHost *:80>
        ServerName elliesdev.com
        ServerAlias www.elliesdev.com *.elliesdev.com
        DocumentRoot /var/www/
</VirtualHost>

```But when you go to 'elliesdev.com' it shows you the EHCP page. I have [followed this thread to uninstall EHCP]("http://ubuntuforums.org/showthread.php?t=481418") as well as deleting the index.php and its image files from /var/www but I still see the "default web site page" by EHCP.  So I'm pretty sure its something with Apache that is causing the site to display that page? [B]What should I do to get ride of it the EHCP default page?
[/B]
I also have a magento ecommerce running at elliesdev.com/magento and I would like to have Apache display it as the default page that you see when you go to elliesdev.com. I have tried changing the DocumentRoot in Apache to /var/www/magento but it makes magento display wrong. **How do I make Apache referre to /var/ww/magento as the default for elliesdev.com without displaying wrong? **

Also, when you go to elliesdev.com/magento, the URL will turn into IP-ADDRESS/magento. **How do you make Apache keep my domain name in the URL and not change it to my IP address?**

I have a feeling that what I am doing is correct, but there is some config file from EHCP that I have not deleted yet that is causing all of this. Thanks in advance.

---

### Post by SirKonstantine on 2010-05-25
bump.

---

### Post by karesmakro on 2010-05-25
Hi!
This is a very basic configuration for apache, you posted! Why no log section, where you can search for, if something went wrong?
for example:
```
NameVirtualHost 173.203.100.72:80

<VirtualHost *:80>
        ServerName elliesdev.com
        ServerAlias www.elliesdev.com *.elliesdev.com
        DocumentRoot /var/www/
        ErrorLog /var/log/apache2/apache-error.log
        TransferLog /var/log/apache2/apache-access.log
</VirtualHost>
```

Try to make a nslookup for 173.203.100.72, what is your server speaking? It should show something like elliesdev.com and same should be vice versa, if you are asking for ip address!

---

### Post by SirKonstantine on 2010-05-25
Ok I added the logs to the apache config, but I still do not know why it changes from elliesdev.com to my IP address when I  go to elliesdev.com/magento

BUT

if you go to elliesdev.com/phpmyadmin, the URL does not change to my IP address! This is really frustrating me. Someone help. =[.

---

### Post by karesmakro on 2010-05-25
Did you tried this:
> Try to make a nslookup for 173.203.100.72, what is your server speaking? It should show something like elliesdev.com and same should be vice versa, if you are asking for ip address!
```
nslookup 173.203.100.72
```
I think, thats the reason! You can also try
```
NameVirtualHost elliesdev.com:80
```
but if your reverse named lookup do not work, you'll have problems like you reported.

---

