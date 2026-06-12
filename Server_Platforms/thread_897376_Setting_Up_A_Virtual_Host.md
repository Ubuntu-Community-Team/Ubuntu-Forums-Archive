---
title: "Setting Up A Virtual Host"
date: 2008-08-22
forum: Server Platforms
---

### Post by Ken Iovino on 2008-08-22
Hey everyone, I've been reading and searching how to do this and I understand the basics, but I'm missing some fundamentals on how to set this up. I've never really worked inside the command line like this before, so please go easy on me. :)

I downloaded and setup Ubuntu Server on a box I had laying around. I installed Apache, PHP5, and MySQL and what I would like to do is point a few domains to this box so outsiders can view the content. After reading a bunch of post, I have a pretty good idea on how to do this, but I'm a little stuck.

I'm told that each domain should have a vhost file created within the "/etc/apache2/sites-available/" folder. Problem is, I don't know how to create that file, or which command to use to create it and when ever I try to edit the default file, I get this:

```
ken@ubuntu:/etc/apache2/sites-available$ edit Default
Warning: unknown mime-type for "Default" -- using "application/*"
Error: no write permission for file "Default"
```

I feel dumb for even asking, but can someone show me how I create the file? Once I figure that out, this should probably be the contents of the file right? Just want to make sure I'm doing this right.

```

 <VirtualHost *:80>
         ServerName example.com
         ServerAlias www.example.com *.example.com
         DocumentRoot /var/example/www
 </VirtualHost>

```

Then I should run this and restart apache.

```

cd /etc/apache2/sites-enabled/
ln -s ../sites-available/example.com 

```

Am I on the right track and how do I physical create the file. :)

Thanks for reading!

Ken

---

### Post by windependence on 2008-08-22
To edit the file use nano:

```
sudo nano etc/apache2/sites-available
```


When you are done, type ctl O (the letter O) and hit enter to save, then ctl X to exit, it's all there on a menu at the bottom.

Don't forget to restart Apache when you're done.

-Tim

---

### Post by Ken Iovino on 2008-08-22
Thanks Tim, but everytime I try that I get this error:

[ Error writing etc/apache2/sites-available/default: No such file or directory ]

**Edit:** I think I got it.

---

