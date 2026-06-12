---
title: "You don't have permission to access / on this server."
date: 2009-07-05
forum: Server Platforms
---

### Post by ltwinner on 2009-07-05
Well, I have apache, php and mysql set up on my laptop and they are working fine as I've created some test web pages and instalelled drupal. 

However the index.html file at [http://localhost/index.html](http://localhost/index.html) wasn't loading automatically when I went to [http://localhost](http://localhost), although it did work if I specified the full path [http://localhost/index.html](http://localhost/index.html). In my attempts to fix this though I have now locked myself out of all files/folders in [http://localhost](http://localhost). I get a 403 Forbidden message "You don't have permission to access / on this server."

I'm logged into linux as root. Can someone tell me how to configure my /var/ww/ folder so I have permission to access all these files on [http://localhost?](http://localhost?) Or do I have to configure apache? Really at a loss here as I've only been using linux 3 days.

---

### Post by Kareeser on 2009-07-05
Can you guide us through the steps you took to get you in this situation? Knowing that, we can reverse the steps.

---

### Post by kustomjs on 2009-07-05
it sounds like he got deny from sit some where in his apache file some where.

check your apache 2 available sites under default maybe you got deny inside of that when it needs to be changed to Allow from all.

look at this file setup /etc/apache2/sites-available/default

---

### Post by ndxtg on 2009-07-06
> **ltwinner said:**
> 
However the index.html file at [http://localhost/index.html](http://localhost/index.html) wasn't loading automatically when I went to [http://localhost](http://localhost), although it did work if I specified the full path [http://localhost/index.html](http://localhost/index.html). In my attempts to fix this though I have now locked myself out of all files/folders in [http://localhost](http://localhost). I get a 403 Forbidden message "You don't have permission to access / on this server."

It's seem like Diretory Index is turned off.

Go to your apache config file (usually /etc/apache2/site-avaialble/default)

Look for the part:
```

<Directory /public_html/mysite>
...
</Directory>

```
where /public_html/mysite is your web directory 

Inside it, look for AllowOverride None and change it 
to AllowOverride All

Then make a file .htaccess in your web directory
with content

```

DirectoryIndex index.html index.htm default.htm index.php index.php3 index.phtml index.php5 index.shtml mwindex.phtml

```

Restart your Apache /etc/init.d/apache restart
then it should work :lolflag:

---

### Post by webtechquery on 2010-02-27
Hi there.
This could be the rights problem as mentioned by you. Try giving the rights on the folder /var/www or subfolder in it through chmod. Try the following on terminal:

**chmod ****a+rwx**** */var/www/****

For further information regarding this error or chmod, check the URL below:
[http://www.webtechquery.com/index.php/2010/02/you-dont-have-permission-to-access-httplocalhost-files-or-folders-on-this-server-in-ubuntu-linux/](http://www.webtechquery.com/index.php/2010/02/you-dont-have-permission-to-access-httplocalhost-files-or-folders-on-this-server-in-ubuntu-linux/)

For any other queries, contact me.

Thanx.

---

### Post by koenn on 2010-02-27
> **webtechquery said:**
> Hi there.
This could be the rights problem as mentioned by you. Try giving the rights on the folder /var/www or subfolder in it through chmod. Try the following on terminal:

**chmod ****a+rwx**** */var/www/****
"just give everyone full controll" is not the right answer. 
besides, this thread is 8 months old. 
trying to collect hits for your blog ?

---

### Post by webtechquery on 2010-02-28
> **koenn said:**
> "just give everyone full controll" is not the right answer. 
besides, this thread is 8 months old. 
trying to collect hits for your blog ?

well, I just mentioned the problem to be solved easily. and for other details, I've asked to access the web where chmod details are there, where one can give rights to owner, group as well as users only.

yes the blog is months older but, is only hitting on the blog is required? what if someone takes advantage of this problem while finding such error, and be helped by me ?

---

### Post by Arsic on 2010-09-23
This thread is a few months old, but I kept running into this problem and this thread keeps popping up in the Google searches, so I'll reply with how I fixed it.

Recursively change permissions to **-rwxr-xr-x**.
```
sudo chmod -R 755 /var/www  
```

You should end up with the following permissions on all of the files in the directory.
[B]Root: read, write, execute
Group: read, execute
Others: read, execute[/B]

Remove read permissions on the folders you don't want users in the group or other to access (**chmod 744 *folder*** or **chmod 700 *folder***). Just add the -R option to do it recursively. For more information on file and folder permissions, please read [http://catcode.com/teachmod/summary.html]("http://catcode.com/teachmod/summary.html"). There are 3 pages to read through there.

---

### Post by koenn on 2010-09-23
cool

---

### Post by SeijiSensei on 2010-09-23
It may be a problem at the OS level, but more common is the situation where directory indexes are disabled as nsdtx suggested.

Make sure you have "Indexes +On" in the <Directory> stanza that defines your website.  That's not the same as the DirectoryIndex directive that nsdtx talks about; that one tells Apache what filenames constitute a valid directory list or home page like index.html.  However if "Indexes" are turned off, and there is no recognized home page, Apache will refuse to list the directory and complain with "You don't have permission to access / on this server."

Take a look at /etc/apache2/sites-enabled/000-default and the definition it contains for /var/www for guidance.

---

### Post by stephanvaningen on 2011-09-13
I had this problem because the higher-level folders did not have group or all permissions set (700 i.o. 755 or 744). In error.log I got this message "(13)Permission denied: /home/developer/sources/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable"

So when my DocumentRoot was i.e:
/home/developer/sources/www
I had to make sure all 3 levels (/home, /home/developer and /home/developmer/sources had u+rx and a+rx permissions set and after that I could immediately access the web site.

---

### Post by nothingspecial on 2011-09-13
Thank you for expanding on the information in this thread :)

However, it is two years old.

Thread closed.

---

