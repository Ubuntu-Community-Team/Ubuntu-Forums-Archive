---
title: "default location of Apache web page..."
date: 2007-03-26
forum: Server Platforms
---

### Post by Mia_tech on 2007-03-26
I installed Apache2, on my ubuntu-box, but I'm kind of new to apache webserver, does anybody knows where by default apache puts your webpages? I know it is up and working because nmap port 80 is open and i'm able to access my [http://localhost](http://localhost) homepage

thanks

---

### Post by Stemp on 2007-03-26
/var/www/

---

### Post by Mia_tech on 2007-03-26
> **Stemp said:**
> /var/www/

so once I'm done with desing of webpage putting them there should be enough?
and do you know if webpages created with front page would work under apache and ubuntu?

---

### Post by Stemp on 2007-03-26
> so once I'm done with desing of webpage putting them there should be enough?
yes
> and do you know if webpages created with front page would work under apache and ubuntu?
I don't know, but if it's just html pages it should work.

---

### Post by huggy77 on 2007-03-26
front page has some .net or ISS add ins... keep it straight vanilla html it should work....  Apache2 rocks... Very easy to get up and running.... Good luck

---

### Post by Mia_tech on 2007-03-27
> **huggy77 said:**
> front page has some .net or ISS add ins... keep it straight vanilla html it should work....  Apache2 rocks... Very easy to get up and running.... Good luck

I knwo for IIS in windows the default homepage usually have the "default.htm" or "index.htm", how about with apache in linux is there any name that default homepage should have in order for apache to make it the homepage.........new to apache!!

any suggestions on any good reading on apache?

---

### Post by kostkon on 2007-03-27
Apache should accept* index.html*, *index.htm*, *index.php* and so on as the start page of your site. But, if you edit the **apache.conf** (i.e. the apache configuration file) you can add your own accepted forms of index pages, like the *default.htm* you said.

Thus, if you open the file as administrator priviledges:

```
sudo gedit /etc/apache2/apache2.conf
```

and find this line in this file:

```
DirectoryIndex index.html index.cgi index.pl index.php index.xhtml
```

you will be able to add your own version of index files, like *default.htm*, next to the current ones, as you can see is easy.

Furthermore, instead of using the **/var/www** folder you can search this lines in the **apache2.conf** file and uncommented them (remove the #'s), like shown here:

```
# UserDir is now a module
#UserDir public_html
#UserDir disabled root

<Directory /home/*/public_html>
	AllowOverride FileInfo AuthConfig Limit
	Options Indexes SymLinksIfOwnerMatch IncludesNoExec
</Directory>
```

then create a folder named** public_html** in your home space and you will be able to put your webpages there. You will be able to access your pages by going to

```
http://localhost/~username/
```

where *username* is your user name. I think this is a cleaner solution where every user has it's own folder for webpages, the way it is used in real world environments. It's safer and simpler that to have to access **/var/www** which belongs to *root*.

I hope I helped you...:)

---

### Post by Mia_tech on 2007-03-27
thanks for the quick intro

---

### Post by TheTux on 2007-04-09
I tried to enable UserDir by editing apache2.conf as you said but it still does not work. I got this

**Forbidden**

 You don't have permission to access /~zul on this server.
 Additionally, a 403 Forbidden error was encountered while trying to use an ErrorDocument to handle the request.
  Apache/2.0.55 (Ubuntu) PHP/5.1.2 Server at localhost Port 80

anyone?

---

