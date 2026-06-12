---
title: "Ubuntu Server"
date: 2007-08-08
forum: Server Platforms
---

### Post by scorpiox on 2007-08-08
Hi
I have just got a VPS server, with Ubuntu 6 LTS installed on it, and am trying to set it up as a webserver for a single domain.
SO far, i have got APACHE2 installed, and operating, PHP5 installed and working, but now im stuck. I need MYSQL and a mailer of some sort, but i dont know how to do it. 
The other big thing, is once i have them installed, how do i configure them, ie email and so on?
Im googling it now, but if anyone can make any suggestoins, i would really appreciate it. 
BIND is installed, but i have no idea what to do with it. I just want to configure the server to show a single domain, in the /var/www folder.

Thanks in advance

---

### Post by scorpiox on 2007-08-08
Update - installed SQL5, but now i cant seem to make databases. I entered the right stuff, but it either gives a syntax error or jsut doesnt respond :(

---

### Post by foxholeunder on 2007-08-08
> **scorpiox said:**
> Hi
I have just got a VPS server, with Ubuntu 6 LTS installed on it, and am trying to set it up as a webserver for a single domain.
SO far, i have got APACHE2 installed, and operating, PHP5 installed and working, but now im stuck. I need MYSQL and a mailer of some sort, but i dont know how to do it. 
The other big thing, is once i have them installed, how do i configure them, ie email and so on?
Im googling it now, but if anyone can make any suggestoins, i would really appreciate it. 
BIND is installed, but i have no idea what to do with it. I just want to configure the server to show a single domain, in the /var/www folder.

Thanks in advance

scorpiox,

For mysql with php support - from a terminal type:

```

sudo apt-get install libapache2-mod-auth-mysql mysql-server php5-mysql

```

Once you have mysql installed you will want to give mysql a password for 'root' - This is important as by default no password is set for 'root'.

To add a password for root type:
```

mysql -u root

```

Your prompt should change from '$' to 'mysql>' The next few lines will include this new prompt so only type in whats after the '>'
```

mysql> USE mysql;
mysql> UPDATE user SET Password=PASSWORD('new-password') WHERE user='root';
mysql> FLUSH PRIVILEGES;
mysql> exit

```

It is also important to not configure mysql with the root account especially if this is a real-world accessible server. You can easily add a user but first we are going to install phpmyadmin so we can configure mysql with a nicer web interface rather than from the command line... This is especially useful if you are new to configuring databases.

To add easy configuration using phpmyadmin make sure the universe repository is available in your /etc/apt/sources.list

If not fire up vim or nano and uncomment the universe repository I will be assuming you are familiar with doing this. If not do this

```

sudo nano /etc/apt/sources.list

```

You should see a commented out section stating "Uncomment the following two lines to add software from the 'universe' repository." - Remove the # comment from the lines starting with deb [http://....universe](http://....universe) and deb-src http:...universe

Save and exit - with nano press 'ctrl-x' then press 'y' and then 'enter'


Once universe is enabled make sure to update
```

sudo apt-get update

```

To install phpmyadmin:
```

sudo apt-get install phpmyadmin

```

phpmyadmin is now available at [http://ip-address/phpmyadmin](http://ip-address/phpmyadmin) 

Once inside the startup page for phpmyadmin you should see a link entitled 'Privileges' - click this link and you will be prompted to insert info about your new user. Once your done log out and log back in as the newly created user to ensure your new account works.

As far as advice on what you need to do from here will rather depend on what you are wishing to do. However, on the main phpmyadmin page you will see another link entitled "phpMyAdmin Documentation" - click this to get a good idea of where you need to start. 

Hope this helps!

---

### Post by foxholeunder on 2007-08-08
Just read your syntax error you posted while I was composing my post and Thought I should mention that phpMyAdmin is rather nice especially when it comes to debugging syntax errors.

Everything is displayed as highlighted code making it easy to see if you have an error before submitting it to the database. If submitted with errors it will give you  fairly reasonable suggestions on where and how to fix the syntax error.

---

### Post by scorpiox on 2007-08-08
Ok. Because i didnt follow that, ill most likely reformat the server and restart, but quick (and important ) question - how do i load phpmyadmin after its installed?

---

### Post by scorpiox on 2007-08-08
Oh, stupid me. Didnt read it. Thanks, following now.

---

### Post by scorpiox on 2007-08-08
Its all working great, last thing - i now need to install and configure a mail program, can anyone help with that?

---

### Post by foxholeunder on 2007-08-08
I can not really help you in the Mail department, sorry :( 

I was going to install one a few weeks ago but got side tracked clustering three apache servers with two load balancers. It has taken me several attempts but I finally have everything fail-proof (knock on wood).

I will say that I am going to be installing Postfix with POP and IMAP services.
I will also be installing a program called Postgrey to help reduce spam and a mail activity monitor called Mailgraph.

As to how to configure them once installed I can not help you yet... at least not till I tackle the project myself.

I can however tell you what you need to type in in order to install them.

So here it goes:

For the Mail server itself:
```

sudo apt-get install postfix

```

For POP and IMAP services:
```

sudo apt-get install courier-imap courier-imap-ssl courier-pop courier-pop-ssl

```

For spam reduction:
```

sudo apt-get install postgrey

```

And finally for monitoring activity:
```

sudo apt-get install mailgraph

```

Otherwise Sorry I can not help with fine tuning the basics after installation.
This should get you going though.

I assume you have set up your server to have a static ip... If not you will want to make sure you do that. Otherwise everything will break terribly with an ip change on the server.

---

### Post by foxholeunder on 2007-08-08
Best of luck by the way! I will follow this thread to see how you come out!

---

### Post by scorpiox on 2007-08-09
Thanks. I have got everything installed , and DNS functioning, its just mail that is defeating me at the moment. I have enlisted the assistance of another guy though, ill keep this place updated :)

---

