---
title: "apache2 problem....."
date: 2008-07-01
forum: Security
---

### Post by hockey97 on 2008-07-01
Hi ok, I first lost all my websites and even the configs, because my particians were damanged so I am starting all over again.

I am having trouble with apache2, I am using webmin, all are latest stuff, since I just install a new slate of ubuntu with the latest version out their.

So so far I got apache up and running just not able to see my virtuial hosts.

I have 2 domain names I bought and plan to host 2 websites.

so far I get a 404 error, well a 404 not found error.

I did a while back config apache2 right and I remeber I had to switch in the config files an area I had to turn off the test mode or something along the lines but I forgot what file has this.

Could someone help me?? I made virtuial hosts by using webmin but didn't get anything to work. I did declared an index file.

any ideas how I can fix this 404 not found error??

---

### Post by elithrar on 2008-07-01
It's hard to say what to help without seeing error logs or your vhost/apache configs - but if you've just set things up I'd suggest wiping the slate clean & following [these articles](http://articles.slicehost.com/ubuntu-hardy) over at Slicehost to get Apache up & running with a few virtual hosts ;)

---

### Post by hockey97 on 2008-07-01
well I am using webmin to add virtuial hosts.

I can show you the logs.

here is the log

never mind fixed it...

but now how would you get rid of index, and could just assign the main website file??

---

### Post by hockey97 on 2008-07-01
So now I just am trying to get out of the default indexing.

when I type my domain name I get a Index of /  with a emtpy Index.

How can I  assign my main html file so when I type in the domain name it would grab the main website file???

---

### Post by hockey97 on 2008-07-01
I still get a empty index list how can I point apache2 to my website files??

I am also using webmin, and tried assinging the dirctory where my files are at.

---

### Post by elithrar on 2008-07-01
Can you post your virtual host config? You should have the following line, though:
```

  DirectoryIndex index.html

```

---

### Post by hockey97 on 2008-07-01
Removed!!!!

---

### Post by LaRoza on 2008-07-01
Not a programming question, moved to servers.

---

### Post by elithrar on 2008-07-01
Yes, it will - unless your actual default page is called **I**ndex.html, it won't work. Configurations & files are case-sensitive.

---

### Post by hockey97 on 2008-07-01
it is my main file. That Index file is my  main webpage where I want people to go when they type in my domain name.

---

### Post by hockey97 on 2008-07-01
I now renamed my main website file to index.html and have it matched like above and yet still dosen't have  my website showing I also disabled the indexing in the httpd for security reasons.

any idea how to go around this??

---

### Post by elithrar on 2008-07-02
Is it called **index.html** or **Index.html**, though? (note the capitalised latter version).

---

### Post by hockey97 on 2008-07-02
it was  Index.html  first and now I just changed it to index.html

that is the html file.

so the config I shown you eailer the file was called Index.html that is the main website file where I want the users to be.

I also now turned off indexing by using the http.conf file adding option -indexing ect

so now I get a forbidden if I put indexing on I then get an empty listing.

I just want my website to appear and don't want to let unauthorized people getting access to see what's in each folder otherwise it will allow a hacker to read my php files by downloading them and looking at source code to understand and break into my website.

So how could I fix this??

I have it currently set to no indexing and has the index file set to  index.html

to me it looks fine I just can't understand what's going wrong why it's listing an emtpy list and why my file is not being runned by apache2.


Also I have the folders and files not in  /www  folder which is default . I have the files in my home folder a folder I made for my websites is in the home area.

---

### Post by elithrar on 2008-07-02
If you have called the file **index.html**, it should work - but why do you have ns.chillenvillen.com as your ServerName? Here's my vhosts file with your domain & paths instead of mine. This should work - I'd suggest creating a [FONT="Lucida Console"]log/[/FONT] directory as well inside [FONT="Lucida Console"]/home/aaron/websites[/FONT].
```



<VirtualHost *:80>

  # Admin email, Server Name (domain name) and any aliases
  ServerAdmin youremail@yourdomain.com
  ServerName  chillenvillen.com
  ServerAlias www.chillenvillen.com

  # Index file and Document Root (where the public files are located)
  DirectoryIndex index.html Index.html
  DocumentRoot /home/aaron/websites/Chillenvillen.com/ 

  # Custom log file locations
  LogLevel warn
  ErrorLog  /home/aaron/websites/log/error.log
  CustomLog /home/aaron/websites/log/access.log combined

  # Error Document Locations
  ErrorDocument 404 /404.html
  ErrorDocument 403 /403.html

  # Additional Configuration Options
  Options -Indexes

  <Directory "/">
    AllowOverride FileInfo
   <Files ~ "^\.htaccess">
      Order allow,deny
      Deny from all
      Satisfy All
    </Files>
  </Directory>

</VirtualHost>


```

---

### Post by hockey97 on 2008-07-02
ok I just copied and pasted it and just deleted the Index.html and just kept the index.html.

So far I tested it and I get a   403 forbidden error.

---

### Post by elithrar on 2008-07-02
What are the permissions on the files in your web-directory? Can you also post your apache2.conf file?

---

### Post by hockey97 on 2008-07-02
Removed!!!!

---

### Post by elithrar on 2008-07-02
Make sure you have the user as www-data in /etc/apache2/envvars - this should be set as such by default, though.

Ensure that your DocumentRoot is accessible by Apache - do a [FONT="Lucida Console"]chown -R aaron:www-data /home/aaron/websites/Chillenvillen.com/[/FONT]

---

### Post by hockey97 on 2008-07-02
ok it works now, thanks, it was the permissions and also my other vir domain which conflicted.

Thanks for the help so much.

---

