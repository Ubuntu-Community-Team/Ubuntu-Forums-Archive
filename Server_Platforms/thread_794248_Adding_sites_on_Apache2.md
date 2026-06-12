---
title: "Adding sites on Apache2"
date: 2008-05-14
forum: Server Platforms
---

### Post by chris1991 on 2008-05-14
Hello there. I have experience with IIS on Windows but have switched to Ubuntu and Apache. I have my default site running in /var/www on port 80 but I would like to add another site on a separate port number. In IIS all I used to do was 'Add Site > Port xxxx'. Can anyone help me with setting this up on Apache please.

Cheers,

Chris

---

### Post by cdenley on 2008-05-14
-add the new port you want apache to listen to by editing /etc/apache2/ports.conf
```

sudo -s
echo "Listen 8080">>/etc/apache2/ports.conf
exit

```

-create a new site(vhost) configuration at /etc/apache2/sites-available/<site name>
(replace <site name> with whatever you want besides default)
something like this should work
```

NameVirtualHost *:8080

<VirtualHost *:8080>
DocumentRoot /path/to/new/site
ServerName www.example.com
</VirtualHost>

```

-enable your new site
```

sudo a2ensite <site name>

```

-restart apache to listen on your new port and load your new site
```

sudo /etc/init.d/apache2 restart

```

---

### Post by chris1991 on 2008-05-14
cdenley, thanks for the walk through. It's worked perfectly :D

Cheers,

Chris

---

### Post by jbaileypro on 2008-05-14
I use a program called Webmin which helps! Check it out!

---

### Post by bossy22 on 2008-05-17
Hi, 

concerning your Posts, I was unable to get my vhosts up and running. I can remember that it was very easy on apache1.x. But now it's just a drag..

I've got the following: 

I am running apache2 on Hardy Heron.

In my /etc/apache/apache.conf, I've got the following:

```
# Include generic snippets of statements
Include /etc/apache2/conf.d/

# Include the virtual host configurations:
#Include /etc/apache2/sites-enabled/vhost.conf

```

As u see, I've disabled the vhost.conf in the sites-enabled Folder. So it can do no harm :)

In the

/etc/apache2/sites-available

Path, I have two config-files: 

digitalearbeit  localhost

In these, I have the following: 

```

NameVirtualHost *:80

<VirtualHost *:80>
ServerAdmin webmaster@localhost

DocumentRoot /home/dantooine/webdev/sites/digi
ServerName   digitalearbeit.local
<Directory />
Options FollowSymLinks
AllowOverride None
</Directory>
</VirtualHost>

```

and 

```

NameVirtualHost *:80

<VirtualHost *:80>
ServerAdmin webmaster@localhost

DocumentRoot /var/www
ServerName   localhost
<Directory />
Options FollowSymLinks
AllowOverride None
</Directory>
</VirtualHost>

```


I was able to activate digitalearbeit by the following:

```

sudo a2ensite

```

and localhost too, without an error message. 

The Problem is now, that when I type digitalearbeit OR localhost Or 127.0.0.1, I only get to the first dir>digitalearbeit!

Which tells me, that the vhosts are not working properly. 

Oh and before anyone asks: my /etc/hosts is:

```

127.0.0.1 	localhost 
192.168.2.10	hendrikmartz.local
127.0.1.1 	dantooine

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

Can anybody help? I really want to work and not configure....

Thanx for ur help and regards

bossy

---

### Post by cdenley on 2008-05-17
The last line of /etc/apache2/apache2.conf should be
```

Include /etc/apache2/sites-enabled/

```
This will load all your vhost configurations from that directory. That directory should contain links to the vhost files in /etc/apache2/sites-available. The links get created when you enable a site with a2ensite.

Where did this come from?
```

#Include /etc/apache2/sites-enabled/vhost.conf

```

---

### Post by bossy22 on 2008-05-18
> **cdenley said:**
> 

Where did this come from?
```

#Include /etc/apache2/sites-enabled/vhost.conf

```

This comes from me. An old habit from apache 1.x. 

I did as you told. 

Inside /etc/apache/sites-available$ is
digitalearbeit  localhost

doing 

```

sudo a2ensite 
```

tells me:

```
Your choices are: digitalearbeit localhost
Site name? digitalearbeit
This site is already enabled!

```

Inside the .conf of /etc/apache2/sites-available$ 

is the following: 

```

NameVirtualHost *:80

<VirtualHost *:80>
ServerAdmin webmaster@localhost

DocumentRoot /home/dantooine/webdev/sites
ServerName   digitalearbeit.local
<Directory />
Options FollowSymLinks
AllowOverride None
</Directory>
</VirtualHost>

```

Typing digitalearbeit.local into a browser, brings up:

```
Address Not Found!
```

typing

```
http://localhost/
```

into browser brings up: 

```
It works!
```

which needs no explanation..

I think there's something wrong with this: 


```
NameVirtualHost *:80

<VirtualHost *:80>
ServerAdmin webmaster@localhost

```

do I have to put my IP-Address somewhere in here, and if yes, where?

```
NameVirtualHost 192.168.2.10:80

<VirtualHost *:80>
ServerAdmin webmaster@localhost
```

or

```
NameVirtualHost *:80

<VirtualHost 192.168.2.10:80>
ServerAdmin webmaster@localhost
```

or

```
NameVirtualHost *:80

<VirtualHost digitalearbeit.local>
ServerAdmin webmaster@localhost
```

????

Thanx in advance

Bossy

---

### Post by RWells on 2008-05-18
Im not sure because I dont really understand all this all that well, but I I have not had any reall problems getting my vhosts to work,

I think you need to add digitalearbeit to your hosts file.

something like this I think

127.0.0.1 localhost digitalearbeit

Hopefully someone that knows better will point Out my error if Im wrong.

Rusty

---

### Post by cdenley on 2008-05-18
Any hostname you look up in a browser has to resolve to an IP address. If you want digitalearbeit.local to resolve to 127.0.0.1, you need this line in /etc/hosts
> 
127.0.0.1 digitalearbeit.local


```

NameVirtualHost *:80
<VirtualHost *:80>

```
There is nothing wrong with this unless you want the server to listen on a specific interface. An asterisk means you can connect through any interface.

---

### Post by bossy22 on 2008-05-18
U two were absolutely right...

Everything works now.. Thanx


Bossy

---

### Post by golferjcd on 2013-04-25
Hi,
I am very new to apache2 and LAMP environments in general.  I have set up an EC2 instance with aws and installed apache2.  I pointed a domain name at my elastic ip address and setup phpmyadmin, mysql and joomla and it all seems to work fine.  I am not trying to add another domain name.  So I have pointed the second domain name at my elastic ip address and am now trying to configure the vhosts in apache2.  So I added a site to /etc/apache2/sites-available and i edited the file to so it says ServerName (my website) instead of ServerAdmin webmaster@localhost and also changed the DocumentRoot, I did this same process with "default" and changed default to my other domain name.  I also went into the /etc/hosts file and added the two websites to the local ip addresses.  I enabled both websites and it says both are enabled.  The problem is when i try to restart apache2 it says "Syntax Error on line 262 Invalid Command '=====================' maybe and misspelled word or command.  Ive gone back in using the command vi /etc/apache2/apache2.conf and tried several different things but nothing seems to work.  Any suggestions? 

Thank you in advance for any help

---

### Post by wildmanne39 on 2013-04-27
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

