---
title: "Apache Virtual Hosts"
date: 2007-11-10
forum: Server Platforms
---

### Post by bullines on 2007-11-10
Hi!

I'm trying to set up a couple of development websites on my Gutsy machine.  The problem I'm having is as follows.

My paths are:

/home/me/web/site1.com
/home/me/web/site2.com

In /etc/apache2/sites-available I have:

```

# domain: site1.com
# public: /home/me/web/site1.com/

<VirtualHost *>

  # Admin email, Server Name (domain name) and any aliases
  ServerAdmin webmaster@site1.com
  ServerName  site1.com
  ServerAlias www.site1.com


  # Index file and Document Root (where the public files are located)
  DirectoryIndex index.php
  DocumentRoot /home/me/web/site1.com/


  # Custom log file locations
  LogLevel warn
  ErrorLog  /home/me/web/site1.com/logs/error.log
  CustomLog /home/me/web/site1.com/logs/access.log combined

</VirtualHost>

```

and:

```

# domain: site2.com
# public: /home/me/web/site2.com/

<VirtualHost *>
  # Admin email, Server Name (domain name) and any aliases
  ServerAdmin webmaster@site2.com
  ServerName  site2.com
  ServerAlias www.site2.com


  # Index file and Document Root (where the public files are located)
  DirectoryIndex index.php
  DocumentRoot /home/me/web/site2.com/


  # Custom log file locations
  LogLevel warn
  ErrorLog  /home/me/web/site2.com/logs/error.log
  CustomLog /home/me/web/site2.com/logs/access.log combined
</VirtualHost>

```

I run 'sudo a2ensite /etc/apache2/sites-available/site1.com' and  'sudo /etc/apache2/sites-available/site2.com'.  Then I run 'sudo /etc/init.d/apache2 reload'.  I update my /etc/hosts so that it contains:

```

127.0.0.1 localhost localdomain localhost ubuntu1 
127.0.0.1 www.site1.com
127.0.0.1 www.site2.com

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

I cannot browse to either [www.site1.com](www.site1.com) or [www.site2.com](www.site2.com).  Even weirder is that I can't even reach [http://127.0.0.1/phpmyadmin/](http://127.0.0.1/phpmyadmin/).  If I do a 'sudo /etc/init.d/apache2 restart', I get:

```

 * Restarting web server apache2                                                httpd (pid 6726?) not running

```

If I then do a2dissite for site1.com and site2.com and then run 'sudo /etc/init.d/apache2 reload' followed by 'sudo /etc/init.d/apache2 restart', I'm at least able to access [http://127.0.0.1/phpmyadmin/](http://127.0.0.1/phpmyadmin/) again.

What am I doing wrong?

Thanks in advance.

---

### Post by MJN on 2007-11-10
> **bullines said:**
> I run 'sudo a2ensite /etc/apache2/sites-available/site1.com' and  'sudo /etc/apache2/sites-available/site2.com'.

Did that not throw an error? a2ensite runs on site names[1], not paths, so I'm surprised it didn't tell you the site didn't exist and hence didn't add the symlinks into sites-enabled/.

It might also be worth checking the logs to see if there's any mention of something untoward.

Mathew

[1] At least this is the case for Dapper, perhaps the Gutsy scripts can accept either in which case ignore this red herring.

---

### Post by bullines on 2007-11-10
> **MJN said:**
> Did that not throw an error? a2ensite runs on site names[1], not paths, so I'm surprised it didn't tell you the site didn't exist and hence didn't add the symlinks into sites-enabled/.


Yes, sorry about that.  I meant to say that I ran 'sudo a2ensite site1.com' and 'sudo a2ensite site2.com'.

Which logs should I look in?

---

### Post by MJN on 2007-11-10
The ErrorLog's defined in your config.

Mathew

---

### Post by bullines on 2007-11-10
I'm not sure what happened, but I rebooted and all seems to be working now.  Not sure why, but I'm not complaining.  Thanks :)

---

### Post by hockey97 on 2007-11-10
How do you config apache to use  a bought domain name.

and how would I go about's setting it up in apahce2??

I have webmin, that's what I use to config or make changes to apache.

I am trying to get 2 vertiual hosts to work.

---

### Post by k_grdn on 2007-11-10
Hi hockey97,

You need to create an A record for your domain with whoever is hosting your domain.

Assuming your hosting machine has the address corresponding to the A record, configure apache vhosts for your domain.  Follow the default   template in /etc/apache2/sites-enabled.

Regards,

k_grdn

---

### Post by hockey97 on 2007-11-10
I have a couple of A records and also mx records.

the a records I have it to point my domain name to my server ip address.

I have followed online tutorials and done what they asked but didn't success I only see the defalut server stuff.

Dosen't an A record only points the domain name to the servers ip??

and do I have to  make a file in /etc/apache2/sites-enabled in order to have it to work.

I have my website folders under home/user/websites  ect 

I don't have anything on /etc/apache2/sites-enabled. to my knowledge.

I am using webmin to config apache and bind 9.

---

### Post by k_grdn on 2007-11-10
You need to create a DocumentRoot directive to "/home/user/websites" and ServerName Directive to your site in a vhosts file under /etc/apache2/sites-available and symlink it to !$:h/sites-enabled.

Regards,

k_grdn

---

### Post by hockey97 on 2007-11-10
ok... ?? I already done most of that but the last part the symlink thing.
What I have got so far, I got to type in my website name [www.myname.com](www.myname.com)  in the web browsers and apache comes on, and so I got the domain name working jut one problem, in apache2 I have virtual  hosts and one was supposed to respond to any request made by [www.myname.com](www.myname.com) ,  so instead when I type [www.myname.com](www.myname.com) in the web browsers I get the defualt apache server, config,  where it has a folder apache and a test site.

---

### Post by hockey97 on 2007-11-11
Do I need in apache2   state where the files are,   Well I am right now getting an error saying resource cannot be found on server [www.mydomain.com](www.mydomain.com) on port 80.

I do have to document root set up right,  /home/me/webpage/mysite.com  
but so I have to tell apache which files to host, I gave it the directory   but I didn't put anything of like /home/me/webpage/mysite.com/mainpage.html  

ect

also this domain name is registered and paid for,  so I tested the page using an proxy server, to test outside traffic,  and I get an error saying this website is experiencing  some problems please try again later.
is their a way I can transfer requestions on ww.mydomain.com  to my virtual server on apache2??

---

### Post by k_grdn on 2007-11-12
If the doc root is being called your vhosts file is not being read or doc root is not found, try the permissions.

Sorry about the symlink, thinking in bash!

should be ln -s /etc/apache2/sites-available/site-name /etc/apache2/sites-enabled/site-name 

Restart apache.

Any probs post your vhost file.

Regards,

k_grdn

---

### Post by MJN on 2007-11-12
> **k_grdn said:**
> should be ln -s /etc/apache2/sites-available/site-name /etc/apache2/sites-enabled/site-name
 
There are scripts to this now - a2ensite <sitename> and a2dissite <sitename> (to enable/disable respectively).
 
It's a good idea to get used to using them as they're likely to introduce further functionality in due course.
 
Mathew

---

### Post by hockey97 on 2007-11-13
I  had it working on on my computer any other computer on the network can't  get to the website that is virtuial hosted.

like on the computer running the server, I can type my [www.mydomain.com](www.mydomain.com) and get the website.
then I notices I have 7.04 ubuntu installed, so I  upgradded it to 7.10.

so before I upgrated it I restarted my computer, when I got back on ubuntu without any changes but the apache config stuff, it the now when I type ww.mydomain.com it now gives me an error saying cannot be found , gave tips saying the website would be busy or you typed in the wrong domain name ect..

well it worked before I restarted the computer.

and ya it is in the sites-available folder for apache..

but I never was able to have my paid domain name forword traffice from the outside to my computer to see the website when  they type in [www.mydomainname.com](www.mydomainname.com). 

I never even got it work to work on my internal network, like no computer could get to my website only my computer that is hosting it could get to it using the domain name.

but now I can't do it even on the computer that is hosting it.
I edited the  file  in /etc/hosts
I added the domain name.

that's how I got it to work before, for just the computer that is hosting it.

but never got it working so the computer on my network nor the outside network computers could get to my site using the domain name..

should I chmod the folder?? I think the folder is not blocked or anything.

do I also need to config bind 9??

I creade bind 9 records he A records and MX records.

---

### Post by hockey97 on 2007-11-15
here is my Vhost file for one domain.


# domain: [www.mdomain.com](www.mdomain.com)
# public: /home/aaron/WebPage/mdomains.com

<VirtualHost *:*>

  # Admin email, Server Name (domain name) and any aliases
ServerAdmin [email]webmaster@mdomain.com[/email]
ServerAlias  [www.mdomain.com](www.mdomain.com)[


  # Index file and Document Root (where the public files are located)
DirectoryIndex awaymessage.html
DocumentRoot /home/aaron/WebPages/mdomain.com


  # Custom log file locations
  LogLevel warn
  ErrorLog  /home/aaron/WebPages/mdomain.com/error.log
  CustomLog /home/aaron/WebPages/mdomain.com/access.log combined
<Directory "/home/aaron/WebPages/mdomain.com">

allow from all
Options +Indexes
</Directory>

ServerPath /home/aaron/WebPages/mdomain.com
ServerNamemdomain.com

</VirtualHost> 
all mdomain are the same name, that's where my real domain is.
I just replaced mdomain with my real domain name.

do you see anything wrong with it??

I want  to be able to type mdomain in my web browser so that it will take me to the website.

same with external trtaffic, I bought this domain name, and want to use it for people from the internet to be able to type my mdomain and get to my page.

---

### Post by hockey97 on 2007-11-15
Hi, I deleted the virtuial host to start all over.

I followed a tutorial online. on this website  [http://rimuhosting.com/howto/virtualhosting.jsp]("http://rimuhosting.com/howto/virtualhosting.jsp") 

and after that, I still can't get my virtuial host going, I have webmin, and commonly use that to config stuff.
I deleted the virtuial host I had and then created new ones using webmin and following that tutorial.

any ideas on how to get my virtuial host running???

I also want to point a paid domain name to one of my virtuial hosts.

---

