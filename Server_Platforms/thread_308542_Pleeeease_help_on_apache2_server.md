---
title: "Pleeeease help on apache2 server"
date: 2006-11-28
forum: Server Platforms
---

### Post by jbtito03 on 2006-11-28
Hi guys and girls. I really need help with my apache 2 server. It suddenly crashed (actually not so suddenly). I installed the lamp server 6.06 and then php4(because of egroupware) and then php5 and now....

Failed to start apache : Apache does not appear to be running :

 * Starting apache 2.0 web server...
   ...done.

That is my webmin output. Please be gentle with me as i am new to this. 

HELP please. I need this server runnin for my project group in my NGO.


Thx

JB

---

### Post by hernan43 on 2006-11-28
The first thing I would do is check out your log files. In /var/log/apache2/ there should be ome logs. I think error.log includes any errors that occur on start up.

---

### Post by jbtito03 on 2006-11-28
Okey.. i got it....

Thx..

---

### Post by dumbbeatnix on 2006-11-28
I am relatively new to this, at the moment I am having trouble sorting out what looks like firewall probs. ](*,)

In your /etc/apache2 directory there should be a file called apache2.conf

Do this at terminal:

sudo gedit /etc/apache2/apache2.conf

Now there are some lines in this that mention public_html.  Uncomment these lines.

Create a directory in your home folder called public_html

Do this at terminal in your home folder:

chmod 744 public_html

Put your web files in the public_html directory.  Now simply type in your browser:

localhost

It should come up with your files.

Also a little tip that might help, when you put your files into the public_html folder ensure that everyone can read and execute them.  So use the chmod command above, only:

chmod 744 public_html/*

I hope this helps. :-k 

Cheers
dumbbeatnix

---

### Post by jbtito03 on 2006-11-28
Okey... i did all this before...

But the actual problem is that the server does not start...


You can read the error log above.


Thx in fwd


JB

---

### Post by stickboy2642 on 2006-11-29
```

PHP Warning:  cl_loaddbdir: Unable to open file or directory\n in Unknown on line 0
PHP Fatal error:  Unable to start clamav module in Unknown on line 0
LibClamAV Error: cl_loaddbdir(): Can't open directory /var/lib/clamav


```

I am guessing that this is your problem.  Do you have clamav installed on your server?  It looks as though it is trying to start  the PHP clamav module, but either doesn't have permissions to the directory /var/lib/clamav or the directory doesn't exist.  If the directory does exist, you may have to grant the www-data user or group the ability to access it.

```

chgrp www-data /var/lib/clamav
chmod g+rx /var/lib/clamav

```

The above commands will change the group on the directory to the group that apache runs under, and will grant read and execute access to the directory.

---

### Post by jbtito03 on 2006-11-29
Oi... thhx... now the apache is working and the PHP is working...

But my program says:

JDatabase::getInstance: Could not connect to database
The MySQL adapter "mysql" is not available.

but my mysql base is running

What can i do here?

---

### Post by fatbastard spice on 2006-11-29
Have you checked to see if the mysql module (libapache2-mod-auth-mysql) is installed? 

```
dpkg-query -l libapache2-mod-auth-mysql
```

Then just enable it (it may already be enabled, but it won't hurt to do it again).

```
sudo a2enmod
auth_mysql
```

Did that fix anything?

---

### Post by jbtito03 on 2006-11-29
Well i did this but still no mysql...

any other suggestions?

I really need thisone

Thx


Jb

---

### Post by jbtito03 on 2006-11-30
Anyone... pleease... urgently need thisone running.

Thx

JB

---

### Post by fatbastard spice on 2006-11-30
Could you give a bit more info on what you're trying to display? Sounds like you've got apache displaying php and html files, so the error is possibly with the web app that you're trying to run. Googling your error message pointed me to Joomla a couple of times, but there wasn't much with that syntax. If it is a web app, you might get more traction with a forum aimed at the particular application.

---

### Post by jbtito03 on 2006-11-30
Okey... i have double checked my joomla and my groupware suite... they both dont have acces to the mysql database and both say that it does not run or something....

Apache2 however is saying that it is OK - no problems in the error log.


Still, the sites do not run and i need them really badly - they did run before i have messed with the server (clean LAMP installation) so something has to be fixed but i have no clue what.

Any suggestions?


Thx...


JB

---

### Post by jbtito03 on 2006-11-30
Helllooooo... i beg you people using this and having experience to heeelp.

I am desperate...


JB

---

### Post by gnaunited on 2006-11-30
It is a php error, not apache.
Do an apt-cache search php5 mysql

It will bring up a module. Install it. Sit back and watch it work. Probably. You might want to search install the php4 version too.

---

### Post by jbtito03 on 2006-12-01
Nope...:-k 

all modules installed...

also did set the php.ini to find the extensions...

no go..](*,) 


I am really getting desperate.:( 


Cheers

JB

---

### Post by jbtito03 on 2006-12-01
Anyone? still did not have any luck...


JB

---

### Post by adamkane on 2006-12-01
This happens to EVERY new would-be LAMP sys admin.

First, keep it simple. Pick ONE version of Apache/MySQL/PHP, and don't deviate.

Second, if LAMP breaks, you may need to COMPLETELY re-install Ubuntu. No-one knows how to un-install/re-install LAMP. I've been watching Ubuntu Forums for a year, and NO ONE has come up with a solution.

The only thing you can do is try a LAMP re-install. If that doesn't work, try an Ubuntu re-install to clean your system.

This is how you install/re-install LAMP:

Apache2/PHP4/MySQL4:
```

sudo apt-get install apache2 php4 mysql-client mysql-server phpmyadmin libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql

```Apache2/PHP5/MySQL4:
```

sudo apt-get install apache2 php5 mysql-client mysql-server phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```Apache2/PHP5/MySQL5:
```

sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```Reboot (or start mysql manually).

Open phpmyadmin:
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

Name: root
Pass: [blank]

---

### Post by jbtito03 on 2006-12-02
Thanx... that solved the problems.. i owe you one :D

Cheers

JB


P.S. You saved my life.... thx...

---

