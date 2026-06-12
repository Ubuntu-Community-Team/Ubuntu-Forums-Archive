---
title: "Problems with apache webdav server on ubuntu 11.10"
date: 2012-01-07
forum: Server Platforms
---

### Post by boots.xiv on 2012-01-07
Hey everyone.  I'm new to linux and I'm trying to set up a webdav server using the tutorial on unixmen.com:
[http://unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1207-how-to-install-and-configure-webdav-ubuntu-1104](http://unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1207-how-to-install-and-configure-webdav-ubuntu-1104)

Everything looked ok as I was running through the tutorial, but I am having the following problems:

Anytime I restart apache I see the following:
/etc/init.d/apache2 restart
 *Restarting web server apache2               apache2: Could not  reliably determine the server's fully qualified domain name, using  127.0.1.1 for ServerName
 ... waiting .apache2: Could not reliably determine the server's fully  qualified domain name, using 127.0.1.1 for ServerName   [ OK ]
 Should the server have a fully qualified domain name, and if so how would it be determined?




 When I access the server from firefox using [http://127.0.1.1](http://127.0.1.1) I get: 
 "It works! This is the default web page for this server. The web server software is running but no content has been added, yet."
 I am not prompted to enter a username and password.  When I use [http://127.0.1.1/webdav](http://127.0.1.1/webdav) I get:
 "Forbidden. You don't have permission to access /webdav/ on this server."
 I am able to access the server through Home Folder -> File ->  Connect to Server and add content to the server from there, but as of  yet I am unable to connect to the server from any other location.
 

Any advice?

---

### Post by druhboruch on 2012-01-07
You may define your location in /etc/apache2/mods_enabled/dav_fs.conf

Mine looks like this:

```
DAVLockDB ${APACHE_LOCK_DIR}/DAVLock

<Location /webdav/>
	DAV On
	AuthType Kerberos
	AuthName "Kerberos Login"
	Krb5Keytab /etc/apache2/krb5_server.tab
        # KrbMethodNegotiate On
	# KrbMethodK5Passwd Off
      	KrbAuthRealms MYREALM.NET
	KrbServiceName HTTP
	Require valid-user
	DavMinTimeout 600
	<LimitExcept GET PUT HEAD OPTIONS POST>
		Require valid-user
	</LimitExcept>
</Location>

```
Just setup your own authentication method as per your tutorial.

---

### Post by boots.xiv on 2012-01-07
Wow! I knew I was a newbie, but its becoming painfully apparent just how true that is.  I hope this isn't redundant but I'm going to post the command lines I used to set up my webdav server:

Installation of apache and encoding modules
```
sudo apt-get install apache2 libapache2-mod-encoding

```Enable webdav modules
```
a2enmod dav_fsa2enmod dav
```Create webdav directory and add permissions
```
mkdir -p /var/www/webdav
chown www.data. /var/www/webdav
chmod 770 /var/www/webdav
```Restarted apache then configured webdav server
```
vi /etc/apache2/conf.d/webdav.conf
``````
Alias /webdav /var/www/webdav
<Location /webdav>
DAV On
#SSLRequireSSL
Options None
AuthType Basic
AuthName WebDAV
AuthUserFile /etc/apache2.conf.d/.htpasswd
<LimitExcept GET OPTIONS>
Order allow,deny
Allow from all
# IP address you allow
Require valid-user
</LimitExcept>
</Location>
```Apply webdav encoding
```
a2enmod dav* encoding
```Make access to webdav server for user admin
```
htpasswd -c /etc/apache2/conf.d/.htpasswd admin
New password:
# set password:
Re-type new password:
# confirm
Adding password for user admin
```Opened webdav with cadaver tool
```
cadaver http://localhost/webdav
Authentication required for WebDAV on server 'localhost':
Username: admin
Password:
dav:/webdav/>
```[SIZE=1][COLOR=Black]

Everything seems to work fine up to this point, except that I then have the issues I mentioned in my first post.

As you can see I defined my location in [/COLOR][/SIZE]/etc/apache2/conf.d/webdav.conf whereas you did in /etc/apache2/mods_enabled/dav_fs.conf.  As well I don't have the DAVLockDB ${APACHE_LOCK_DIR}/DAVLock ahead of the <Location> tag.

Is this my problem?

---

### Post by druhboruch on 2012-01-07
When I was configuring my webdav I was unable to cleanly restart apache until I moved the location configuration to dav_fs.conf...

---

### Post by boots.xiv on 2012-01-08
Ok I'll try that. Thank you very much! Do you know if I need to remove the configuration from the original file: etc/apache2/conf.d/WebDAV.conf?

---

### Post by boots.xiv on 2012-01-08
I really appreciate your assistance but I'm giving up on this specific issue.  I'm becoming frustrated and I'd like to start over.  I've already removed apache2 from my system, just to give myself a fresh start.  Any chance you could point me to a configuration that actually works?

---

### Post by druhboruch on 2012-01-08
I don't know of any webdav howto created for 11.10.

During my setup I used this howto as a base:

[http://www.howtoforge.com/how-to-set-up-webdav-with-apache2-on-ubuntu-9.10](http://www.howtoforge.com/how-to-set-up-webdav-with-apache2-on-ubuntu-9.10) since it worked OK on previous versions of Ubuntu.

In Oneiric I just had to define the location in dav_fs.conf instead.

Later I also changed the authenticaion method to meet my requirements, but only after I tested it with the plain one.

I hope it helps.

---

### Post by boots.xiv on 2012-01-09
Yes that helps me a lot! If I understand correctly, I can go through the howto exactly as posted except to place

        Alias /webdav /var/www/web1/web

        <Location /webdav>
           DAV On
           AuthType Basic
           AuthName "webdav"
           AuthUserFile /var/www/web1/passwd.dav
           Require valid-user
       </Location>

in dav_fs.conf instead of where specified in the howto.

I'll give that a try and post my results. Again, thanks for your help!

---

### Post by druhboruch on 2012-01-09
Please, see the second post of this tread.
Only location section belongs in dav_fs.conf

---

### Post by boots.xiv on 2012-01-09
Right... so the "Alias..." line still goes where specified in the howto? I'd assumed it went hand in hand with the <Location> code, just with the way it was put together in the tutorial.

---

### Post by boots.xiv on 2012-01-11
It worked!!

Many thanks druhboruch!!! I ran through the tutorial you pointed me to, putting the alias part where directed, but the location section in dav_fs.conf.

A few interesting things came up.  I have no idea what they mean.  If you don't have the time or inclination to comment, no worries.  I'm already quite satisfied and appreciative of your assistance.

First thing I noticed was: "[warn] NameVirtualHost *:80 has no VirtualHosts"

This was after restarting apache2. I have absolutely no idea what that means.  I don't even know if that means something is wrong, but it kinda sounds like it.

Also, I still get this message: "Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName"

I am able to access the webdav server using [http://127.0.1.1:80/webdav](http://127.0.1.1:80/webdav).  But I am also able to connect using my computer's ip on my local wifi network: [http://111.111.1.11(false](http://111.111.1.11(false), obviously):80/webdav.

In any case, it seems my webdav server is up and running.  Thanks again!

---

### Post by druhboruch on 2012-01-11
Most likely you have more then one definition of NameVirtualHost

Try grep NameVirt * -R in /etc/apache2.

---

### Post by boots.xiv on 2012-01-12
I haven't tried that yet, but a thought came to me.  How could I have more than one definition of NameVirtualHost if I've never set up a virtual host before? Could it have something to do with my earlier failed attempt at setting up the webdav server? Although, that tutorial never mentioned a virtual host.
 
In any case, the webdav server works great, so I can live with the error message. I'll try the command you gave me tonight and see what happens.

---

### Post by boots.xiv on 2012-01-13
Alright! So after some additional research, I finally caught on to exactly what you meant in your last post. And indeed, I did have more than one definition of NameVirtualHost.  Turns out the file /etc/apache2/ports.conf has a NameVirtualHost line by default.  All I did was delete that line from /etc/apache2/sites-available/default configuration and the error went away. So my final configuration of /etc/apache2/sites-available/default looks like this:

```

<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/web1/web/
        <Directory /var/www/web1/web/>
                Options Indexes MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        Alias /webdav /var/www/web1/web

</VirtualHost>

```Pretty much exactly the same, except the NameVirtualHost *:80 line is gone from the top.  The error disappeared and my server is still working great.  Now if only I could figure out what ".apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName" means...

---

### Post by boots.xiv on 2012-01-13
Ok...so thats done! The fix for ".apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName" can be found here:

[http://aslamnajeebdeen.com/blog/how-to-fix-apache-could-not-reliably-determine-the-servers-fully-qualified-domain-name-using-127011-for-servername-error-on-ubuntu](http://aslamnajeebdeen.com/blog/how-to-fix-apache-could-not-reliably-determine-the-servers-fully-qualified-domain-name-using-127011-for-servername-error-on-ubuntu)

---

### Post by Len2012 on 2012-03-25
Thanks so much for posting this info. I had followed a couple of other tutorials and they did not work. I had to back up on my own steps and delete/modify everything that I had done and reinstall/install apache2 to start from scratch. It took me some hours but I went though the whole thing and my webdav server is running (I guess) thanks to the post.

I followed  all steps indicated by boots.xiv and druhboruch, and like I said, the webdav server is working. However, I noticed that when I access: [http://localhost/webdav](http://localhost/webdav) the browser asks me for a username/password (which is obviously what it's supposed to do), but when I access "http://localhost/" no username/password is asked, and I can see all the contents of /var/www/web1/web in the browser.

Any help will be greatly appreciated.

Thanks in advance,

L.

---

### Post by boots.xiv on 2012-03-29
I have the same problem.  I vaguely remember coming across this issue in my research when I was setting up my webdav server, but I never discovered a solution.  Honestly I didn't give it much thought until you mentioned it now.  I can actually access the server from a different device on my local network without getting prompted for a username and password.  Kind of defeats the purpose...

---

### Post by parisv on 2012-04-07
I'm having issues with the same guide also.

First of all I'm installing it on a headless server. So say the ip is 192.168.1.2

I added "ServerName localhost" to /etc/apache2/httpd.conf


/etc/apache2/mods-enabled/dav_fs.conf looks like this:

```
DAVLockDB ${APACHE_LOCK_DIR}/DAVLock
<Location /webdav>
DAV On
#SSLRequireSSL
Options None
AuthType Basic
AuthName WebDAV
AuthUserFile /etc/apache2.conf.d/.htpasswd
<LimitExcept GET OPTIONS>
Order allow,deny
Allow from all
# IP address you allow
Require valid-user
</LimitExcept>
</Location>
```


/etc/apache2/conf.d/webdav.conf just has the 1 line in:

```
Alias /webdav /var/www/webdav
```

When I browse to [http://192.168.1.2/webdav](http://192.168.1.2/webdav) it does not work. I've created a rule for port 80 in ufw and tried disabling ufw altogether.

What am I doing wrong?

Thanks

---

