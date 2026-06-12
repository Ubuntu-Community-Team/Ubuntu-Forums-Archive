---
title: "I REALLY need help setting up a wordpress server."
date: 2007-06-11
forum: Server Platforms
---

### Post by tdrusk on 2007-06-11
I am running Ubuntu Feisty 7.04. I installed apache1.3 php5-mysql libapache2-mod-php5 mysql-server

First of all, I was having a hard time setting up a mysql database. I installed mysql-admin in hopes of making things easier. I can't figure out how to connect.

Previously, I tried to use the commandline to make a root password and database. I got
I am at this part. I am kind of confused on what to enter. Let's say I want my password for mysql to be "chicken". Would I do
mysqladmin -u root -p password chicken
?

It keeps telling me
Quote:
mysqladmin: connect to server at 'localhost' failed.
error: 'Access denied for user 'tyler'@localhost' (using password: YES)'

I have a Dynamic ip, so I set this up.
[http://techaspect.blogdns.com](http://techaspect.blogdns.com)

It works and connects to the server, but I still need to fix those other things.

After I get those working I need to install Wordpress. I feel stupid because so many people have done this successfully, but I guess it's all in the learning process.

Any help is greatly appreciated.

---

### Post by jakobfriis on 2007-06-12
First of all you must have a working LAMP - the rest is piece of cake, and you will see why. 

cd <full-path-to-your-webserver-docroot> (typically /var/www)
sudo wget [http://wordpress.org/latest.tar.gz](http://wordpress.org/latest.tar.gz)
sudo gunzip latest.tar.gz
sudo tar xvf latest.tar

start a browser and load [http://yourserver/wordpress](http://yourserver/wordpress)

It will open an installation page and from here on you just have to follow the instructions.

If you need more help feel free to contact me via messenger on [email]friis_jakob@hotmail.com[/email] (emails are not read)

---

### Post by silverglade00 on 2007-06-12
> **fuzzyhair said:**
> 
 Let's say I want my password for mysql to be "chicken". Would I do
mysqladmin -u root -p password chicken
?


That should be mysqladmin -u root -p chicken
Leave out the word password. You might also want to try phpMyAdmin. It's a web based gui thing for administration of mysql. Not sure if it's in the repos, I just installed a couple hours ago.

I can tell you got something wrong. I clicked on your link and it took me to my test Wordpress server on my local network :)

---

### Post by Wardazo on 2007-06-12
> **fuzzyhair said:**
> I am running Ubuntu Feisty 7.04. I installed apache**1.3 **php5-mysql libapache2-mod-php**5** mysql-server

Looks like you are tring to install apache 1.3 with php mod for apache 2. I'm not sure if Ubuntu could resolve this automatically via the synaptic package manager. I would uninstall the LAMP software. 

Then... the following will give you a functional LAMP server complete with email (for php mail() function) and working phpmyadmin:

> sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql postfix

But the default instalations ARE NOT SECURE! For example phpmyadmin is run as root, phpmyadmin is not password protected, the php.ini file is not for a production sever (not php.ini-recommended). The list goes on an on.

Before setting up a server I really suggest you read up about security. People will try and break into you server.

If you want any help, post back on the forum:p

---

### Post by tdrusk on 2007-06-12
okay. i've gotten pretty far, but when I go to phpmyadmin to make a new database it asks me for my username and password. What do I put in for these?

---

### Post by Wardazo on 2007-06-12
Hi

I think the default is either

username: root
password: [empty]

or

username: root
password: root

I'm pretty certain it's the first one... unless you've changed the root password

---

### Post by tdrusk on 2007-06-12
> **Wardazo said:**
> Hi

I think the default is either

username: root
password: [empty]

or

username: root
password: root

I'm pretty certain it's the first one... unless you've changed the root password
Wahoo it worked! 

I set a password for it, but I had to restart mysql. Thanks

---

### Post by Wardazo on 2007-06-12
Cool.

Please don't forget forget about security. The default instalations are not ready to be put online. Sorry I can't recommend a recent primer on the subject. I learn this stuf some time ago.

If you want any help, post back here. I'll get an email that way. 

Goog luck.

---

### Post by tdrusk on 2007-06-12
Now I'm having trouble setting up a mysql database for wordpress. I have no idea how to do it. I would like to do it using phpmyadmin. any ideas?

---

### Post by Wardazo on 2007-06-12
At [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) there should be a box which says create database. If you can't see it press the  refresh button on your browser. That will take you to the default page.

In the box write "wordpress", although I believe with wordpress you can asign any name. The press the button "create". All the defaults should be sufficient for wordpress if it's english you want.

That's the database part done (but not secured). If you go to your wordpress directory you should be able to set up an insecure wordpress instalation using the wordpress instalation wizard.

---

### Post by tdrusk on 2007-06-12
Okay, I'm doing better but....
It says it can connect to the database, whcih means my username and password is right, but it was unable to select the wordpress database.

so close!

---

### Post by tdrusk on 2007-06-12
Nevermind i got it to work. I forgot the capital in wordpress. Thanks for all your help. I really appreciate it.

---

### Post by tdrusk on 2007-06-12
How can I get this secured and on the web?

---

### Post by Wardazo on 2007-06-12
Great! Please don't forget what I said about securing your server. 

The set up you have now is great for devoloping or exploring a functioning server, but it is not secure. 

Just consider the opeing lines of the php.ini file:

> 
;;;;;;;;;;;
; WARNING ;
;;;;;;;;;;;
; This is the default settings file for new PHP installations.
; By default, PHP installs itself with a configuration suitable for
; development purposes, and *NOT* for production purposes.

---

### Post by tdrusk on 2007-06-12
> **Wardazo said:**
> Great! Please don't forget what I said about securing your server. 

The set up you have now is great for devoloping or exploring a functioning server, but it is not secure. 

Just consider the opeing lines of the php.ini file:

Okay. I guess I should secure it then. I also want to make it so someone from anywhere can type [http://techaspect.wordpress.com](http://techaspect.wordpress.com) and it will connect to my computer. How can I do this?

---

### Post by Wardazo on 2007-06-12
Hi

Not sure if you can use [http://techaspect.wordpress.com](http://techaspect.wordpress.com) as this belongs to wordpress. You could put a link on this page or erhaps a meta redirect... not sure what wordpress.com allows.

You'll need a the ip of your computer, but you've probably got a dynamic one so I'd look at dyndns.com.

I've never used dyndns so can't offer you much help there.

---

### Post by tdrusk on 2007-06-12
Okay, so with dyndns i set up an account and directed it to my dynamic ip. 
I came out with this link [http://techaspect.dnsalias.net//](http://techaspect.dnsalias.net//)
but I am sure that whenever someone clicks it it will take them to THEIR ip, not mine... :(

---

### Post by Wardazo on 2007-06-12
Hi

I'm sorry I can't help you with this. I've never used dnydns. I've always had a fixed ip to work with. However, I'm sure there are thousands of people on this forum that know dyndns.

You should start a new post titled "dyndns help" in the beginners section.

I'm sure someone will help.

good luck

---

### Post by tdrusk on 2007-06-12
> **Wardazo said:**
> Hi

I'm sorry I can't help you with this. I've never used dnydns. I've always had a fixed ip to work with. However, I'm sure there are thousands of people on this forum that know dyndns.

You should start a new post titled "dyndns help" in the beginners section.

I'm sure someone will help.

good luck

Okay thank you so much.

---

### Post by Wardazo on 2007-06-12
No problem. Good luck

---

