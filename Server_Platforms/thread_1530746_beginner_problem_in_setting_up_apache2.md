---
title: "beginner problem in setting up apache2"
date: 2010-07-14
forum: Server Platforms
---

### Post by tapas_mishra on 2010-07-14
I am having different websites in a folder
/var/www/
as
/var/www/atutor
/var/www/dokeos
/var/www/docebolms
.
.
.
/var/www/efront

When  I am on lan trying to access these sites as

[http://192.168.1.5/dokeos](http://192.168.1.5/dokeos) or [http://192.168.1.5/docebolms](http://192.168.1.5/docebolms) 

 I am getting a 404 not found page.
The requested URL /dokeos was not found on this server.

here are the response headers to the above said request
[http://pastebin.com/g1XDtu1R](http://pastebin.com/g1XDtu1R)



another application is dokeos
and response headers which I captured in FireFox when trying to access it

as [http://192.168.1.5/docebolms](http://192.168.1.5/docebolms)

[http://pastebin.com/tiFTRh0A](http://pastebin.com/tiFTRh0A)




When I type [http://192.168.1.5/](http://192.168.1.5/)
I expect to get a directory listing of different websites which are present in my /var/www

as per this page [http://httpd.apache.org/docs/2.0/mod/core.html#options](http://httpd.apache.org/docs/2.0/mod/core.html#options)
where it said if there is no index.html page in that directory 
mod_autoindex  will generate a directory index.

instead of getting a directory listing I am getting a response from a vhost 
atutor

which I should get when I type [http://192.168.1.5/atutor](http://192.168.1.5/atutor)
(because apache serves vhosts in alpha numeric order)

in /etc/apache2/sites-available/atutor
I do have a 
<Directory /var/www>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
  </Directory>


the complete configuration is here

[http://pastebin.com/VpvHdkSP](http://pastebin.com/VpvHdkSP)



on lan when ever I am typing [http://192.168.1.5/](http://192.168.1.5/)
I am getting response or website which I should get when I type
i.e. [http://192.168.1.5/atutor](http://192.168.1.5/atutor)
and if I am typing [http://192.168.1.5/docebolms](http://192.168.1.5/docebolms) or http;//192.168.1.5/dokes
then URL not found error.

---

### Post by slooksterpsv on 2010-07-14
The directories themselves are lowercase, if they even have just 1 uppercase letter and you type in all lowercase, it will fail to find that directory. Make sure that if its DoKeOS - you type in: [http://192.168.56.1/DoKeOS](http://192.168.56.1/DoKeOS) cause it won't go to [http://192.168.56.1/dokeos](http://192.168.56.1/dokeos) - I've had this trouble before in the past.

See screenshot attached:

EDIT: This may help [http://keystoneit.wordpress.com/2007/02/19/making-apache-case-insensitive/](http://keystoneit.wordpress.com/2007/02/19/making-apache-case-insensitive/)

---

### Post by tapas_mishra on 2010-07-14
I checked your blog and my directory structure also I am having all the directories in lower case letter thanks for this information.
But I am having the problem which I reported in above question.

---

### Post by slooksterpsv on 2010-07-14
> **tapas_mishra said:**
> I checked your blog and my directory structure also I am having all the directories in lower case letter thanks for this information.
But I am having the problem which I reported in above question.

Are you able to reproduce the same results with 127.0.0.1 or localhost on that machine or is this a different machine on the same lan?

---

### Post by tapas_mishra on 2010-07-14
Yes same results with localhost also.

---

### Post by tyleruk on 2010-07-14
Have your actually tried adding a index.html file to the folder, just to see if it worked.

Also try adding
> Options +Indexes
to each directory in the sites-available file.

---

### Post by tapas_mishra on 2010-07-14
Yes I have tried both the things you mentioned.

---

### Post by slooksterpsv on 2010-07-14
Change your DocumentRoot back to /var/www instead of /var/www/atutor - that is looking for the other folders like dokeos in atutor EDIT: Sorry I keep missing information, the dokeos is its own vhost file same with atutor etc. ok so you can ignore this then.

I didn't catch that earlier, also is there a link from sites-available to sites-enabled for the vhost you created? If its not make a link, I believe its just ln -s /path/to/vhost /path/to/link/vhost
e.g.
sudo ln -s /etc/apache2/sites-available/mysite101 /etc/apache2/sites-enabled/mysite101

---

### Post by tapas_mishra on 2010-07-14
Man thanks a lot for replying.I have been able to nail this problem finally.
I am mentioning so that if some one else comes across this thread should help them.
We need to understand if there are many websites running on same server which is using a name based Virtual Hosting.
On Ubuntu based system and Red Hat based systems it is different.
I was using Ubuntu 10.04 I will mention what was happening


on a webserver if some one is using Name Based Virtual hosting and have a lot of websites then how does apache decided which vhost to serve I asked this question on apache forum also
[here is a link]("http://www.spinics.net/lists/apache-users/msg95701.html") on apache forum where I asked
another link
[http://httpd.apache.org/docs/2.2/vhosts/details.html](http://httpd.apache.org/docs/2.2/vhosts/details.html)
but you may not find it easy for the first time if you are a having this problem.So I am explaining.
In my /etc/apache2/sites-available I had following files
```

root@someserver:/etc/apache2/sites-available# ls

 atutor  claroline    docebolms  dokeos  efront  olat  mydomain.com    sakai 
```

the vhost file atutor is coming alphabetically first so even if I was typing [http://localhost](http://localhost) it was being served.
You can verify this by following
apache2ctl -S
```

VirtualHost configuration:
wildcard NameVirtualHosts and _default_ servers:
*:80                   is a NameVirtualHost
         **default server atutor (/etc/apache2/sites-enabled/atutor:1)**
         port 80 namevhost atutor (/etc/apache2/sites-enabled/atutor:1)
         port 80 namevhost claroline (/etc/apache2/sites-enabled/claroline:1)
         port 80 namevhost docebolms (/etc/apache2/sites-enabled/docebolms:1)
         port 80 namevhost dokeos (/etc/apache2/sites-enabled/dokeos:1)
         port 80 namevhost efront (/etc/apache2/sites-enabled/efront:1)
         port 80 namevhost olat (/etc/apache2/sites-enabled/olat:1)
         port 80 namevhost mydomain.com(/etc/apache2/sites-enabled/mydomain.com:1)
         port 80 namevhost sakai (/etc/apache2/sites-enabled/sakai:1)
Syntax OK


```
Note above output also shows atutor as default.

And as you correctly said


> **slooksterpsv said:**
> Change your DocumentRoot back to /var/www instead of /var/www/atutor - that is looking for the other folders like dokeos in atutor EDIT: Sorry I keep missing information, the dokeos is its own vhost file same with atutor etc. ok so you can ignore this then.

I didn't catch that earlier, also is there a link from sites-available to sites-enabled for the vhost you created? If its not make a link, I believe its just ln -s /path/to/vhost /path/to/link/vhost
e.g.
sudo ln -s /etc/apache2/sites-available/mysite101 /etc/apache2/sites-enabled/mysite101

I need to have one more vhost which should be default vhost to be served having /var/www as its document root.
To do so I need to create a file as 000-tapas in /etc/apache2/sites-available/000-tapas
and then a2ensite 000-tapas
the name 000-tapas preceding 0's are important since this gives priority to vhost 000-tapas over atutor.

the content of 
/etc/apache2/sites-available/000-tapas
should be 
```

<VirtualHost *:80>
        ServerAdmin webmaster@localhost
#        ServerName (what ever you want default)
**        DocumentRoot /var/www/**

        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
**        <Directory /var/www/>**
                Options +Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>


</VirtualHost>


```
Note /var/www in above so now restart apache2 and then do an 
```

apache2ctl -S 

```
the output is 


```

VirtualHost configuration:
wildcard NameVirtualHosts and _default_ servers:
*:80                   is a NameVirtualHost
         **default server 000-tapas (/etc/apache2/sites-enabled/000-tapas:1)**
         port 80 namevhost 000-tapas (/etc/apache2/sites-enabled/000-tapas:1)
port 80 namevhost atutor (/etc/apache2/sites-enabled/atutor:1)
         port 80 namevhost claroline (/etc/apache2/sites-enabled/claroline:1)
         port 80 namevhost docebolms (/etc/apache2/sites-enabled/docebolms:1)
         port 80 namevhost dokeos (/etc/apache2/sites-enabled/dokeos:1)
         port 80 namevhost efront (/etc/apache2/sites-enabled/efront:1)
         port 80 namevhost olat (/etc/apache2/sites-enabled/olat:1)
         port 80 namevhost mydomain.com(/etc/apache2/sites-enabled/mydomain.com:1)
         port 80 namevhost sakai (/etc/apache2/sites-enabled/sakai:1)
Syntax OK


```
Now in above output 000-tapas is default
and that solved the entire thing.

---

