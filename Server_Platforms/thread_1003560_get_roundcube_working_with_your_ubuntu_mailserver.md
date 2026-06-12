---
title: "get roundcube working with your ubuntu mailserver"
date: 2008-12-06
forum: Server Platforms
---

### Post by joenieburg on 2008-12-06
I wanted to have a mail server at home.
And the nice thing about that is with a webmail based portal I can access my email from everywhere.

I Am a newby for Ubuntu so I was needing a lot off these forums.

At first a started out just to get the mail server up and running with Postfix and courier imap server. Here is the link.

[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts]("http://www.howtoforge.com/perfect-server-ubuntu8.04-lts")

After that I head to figure out how to use Maildir.
This is done automaticly for the first email. Only I wanted to have a sent box and a Draft box.
Here are the commands.
First stand in the users dir where u wants this.
maildirmake -f Drafts Maildir
maildirmake -f Sent Maildir

When u want to connect from outlook express be sure to set your outlook express imap settings to an empty root folder map. Also set outlook to use a secure connection (SSL)

When your ready with receiving and sending mail . This is the point where it gets realy easy.

Install roundcube. U can go to the website and all. But the easiest way is like this.
On your server type.
> sudo apt-get install roundcube
Follow the on screen questions.
> Database voor roundcube via dbconfig-common instellen?  YES 
 Use the MYSQL db (because off the Perfect server setup)

after that You only have to get thw webiste running through apache. This was my trouble. Because the installation put all roundcube files in /usr/share/roundcube I was not able to start a website. so this is what I did.

sudo cp -R /usr/share/roundcube /var/www

after this I open the browser to [http://Localhost/roundcube](http://Localhost/roundcube) 
login with my username and password and it worked.

Now some people will say u also good create een virtual directory on your apache server. But I don't know how. But this is working now.

---

### Post by GJB on 2008-12-09
Hi Joenieburg , 
 nice !

You can create a virtual directory in Apache by making a symbolic link from /var/www to the /usr/share/roundcube directory 

 for instance :  ln -s /var/www/roundcube /usr/share/roundcube 

 creates the symbolic link 'roundcube' in the root of your Apache-server but it actually reads from /usr/share/roundcube

):P

---

### Post by joenieburg on 2008-12-14
Thanxs GJB, for that ln.


 I only changed the target with the link. 
so I went to the /var/www 
there I did 
ln -s /usr/share/roundcube roundcube 
But If u dont want a link called [http://localhost/roundcube](http://localhost/roundcube) but webmail then change the last word (roundcube) to what ever u want.


But does anybody knows how to make a virtual dir in Apache?

---

### Post by joenieburg on 2008-12-22
To get Roundcube working in your apache virtual server.

This can be done in two ways. Through webmin which I prefer.
> webmin => apache Webserver => virtual server => alias and redirects.
How to get webmin go to this site
[http://www.webmin.com]("http://www.webmin.com")

But u can also edit the sites file by hand. To do this go to the file;

/etc/apache2/sites-available/default

and past this within the VirtualHost section
> Alias /webmail "/usr/share/roundcube/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>


Some troubles I have been having along the way.

>  extension not found in /usr/share/roundcube/program/include/rcube_db.inc

I installed the minimal ubuntu server version. (because off performanche) 
Than roundcube can not connect to the SQL DB. U have to install php5-mysql and sqlite3 on your server.

also I had trouble with the maildirmake command which I run at a users home dir under root. Then the owner rights are set to root. this is wrong.

to get it right go to the users home dir in the users acoount and then set the owner rights ok again.

sudo chown [user]:[user] Maildir 
and all file inside Maildir.

But it is better to create a user, and then send an mail to that users. Postfix will create the Maildir box.
And in the main.inc.php found in usr/share/roundcube set the rmail_config['create_default_folders'] = TRUE (Default is false) Then roundcube will create those folders for that users when she/he logs in.  
Also remember that roundcube will not make the Maildir folder so first send an email to a new users than let the new user log in through roundcube.

---

