---
title: "Basic Apche configuration for multiple websites"
date: 2010-06-22
forum: Server Platforms
---

### Post by leegold on 2010-06-22
Hi, 

Have a newbie question about setting up Apache for users who would want to make their own websites. I would like each person to have their own index.html. I have a default LAMP install on 9.04 sever and it works OK. 

One way to give access I see documented is to configure /var/www to make it editable by making a www-data group which has permission to edit the document root and then adding people to that group...

I also see virtual hosts...

What I want is to have the ability to add people who want their own websites. It doesn't have to be user1.org, user2.org which I assume virtual hosts would be able to do. It could just be, mydomain.org/user1, mydomain.org/user2 were uach user can only edit their own page only.

So I'm not sure how to securely config this. Do I add dirs per each user under www/var and give permissions/authentication per each dir per user. Or do I do it from each user's /home?

I expect I'll have to edit Apache config file(s) too.

If there's a tutorial you know or you could give me some idea it would be appreciated. This is a test server behind my local firewall and is a test, only local.

There may be some DNS to make it better but I'd like to defer that right now and just get the functionality cited above, Seems like a very common (but not necessarily easy) thing to do. Help appreciated.

Lee G.

---

### Post by Ryan Dwyer on 2010-06-22
Enable Apache's userdir module: sudo a2enmod userdir
Restart Apache: sudo /etc/init.d/apache2 restart
Create public_html for your user: sudo mkdir /home/username/public_html
Create an index file for your user: sudo echo "Here's the index" > /home/username/public_html/index.htm
Fix up permissions: sudo chown -R username:username /home/username/public_html

Browse to [http://servername/~username](http://servername/~username)

---

### Post by kevinthecomputerguy on 2010-06-22
Leegold-
I think this is what you are looking for
[http://woodel.com](http://woodel.com) 
Its Debian based, but still applies to Ubuntu for the most part

---

