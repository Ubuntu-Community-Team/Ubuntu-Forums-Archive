---
title: "404 Error when use Public IP or Domain Name"
date: 2010-05-26
forum: Server Platforms
---

### Post by macmike on 2010-05-26
Ok, when I type in wilmingtoncoc.com or type in 192.168.123.101 I get this error message.

**Not Found**

 The requested URL / was not found on this server.
  Apache/2.2.14 (Ubuntu) Server at 69.246.231.58 Port 80

When I type in 127.0.0.1 

I get a screen that says it works. 

I installed the ddclient and configured it. Porting in the router is working. I am trying to get 3 sites hosted on this Web Server. Any help appreciated. Also I have installed ftp, Webmin and want to install wordPress for the [www.wilmingtoncoc.com](www.wilmingtoncoc.com) site. What commands do I use and how do I configure them? All help welcomed. Definitely a green horn with Linux.

Mike Hughes

---

### Post by macmike on 2010-05-26
Ok, when I type in wilmingtoncoc.com or type in 192.168.123.101 I get this error message.

**Not Found**

 The requested URL / was not found on this server.
  Apache/2.2.14 (Ubuntu) Server at 69.246.231.58 Port 80

When I type in 127.0.0.1 

I get a screen that says it works. 

The $64,000 question is why can I get into the server locally with 127.0.0.1 and can't get to the file at Wilmingtoncoc.com or the Public IP or my 192.168.123.101 address?

Someone on the phone told me apparently a configuration file for apache is not set right. The files are at /SERVER. How do I get to the config file to see what is set in the Document root? I typed in sudo nano /etc/apache2/httpd.conf and got a blank document. Don't know which one I need to look at to make sure it is all set right.

I installed the ddclient and configured it. Porting in the router is working. I am trying to get 3 sites hosted on this Web Server. Any help appreciated. Also I have installed ftp, Webmin and want to install wordPress for the [www.wilmingtoncoc.com]("http://www.wilmingtoncoc.com/") site. What commands do I use and how do I configure them? All help welcomed. Definitely a green horn with Linux.

Mike Hughes

---

### Post by cariboo on 2010-05-26
Have you registered the ip address with your registrars dns servers, I tried pinging the address and get no response.

---

### Post by cariboo on 2010-05-26
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by macmike on 2010-05-26
I thought I did. I use Dydns. I have the Domain names through Go Daddy and have them forwarded to DynDNS.com.  Sorry for the multi-posting. How do I make sure?

Mike

---

### Post by halitech on 2010-05-26
check out the section here on virtual hosts: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by macmike on 2010-05-26
Question: I have started searching through .conf files and see what I can find out. At the bottom of the apache2.conf file I have the following.

NameVirtualHost 69.246.231.58:80
<ifModule mod_ssl.c>
NameVirtualHost 69.246.231.58.443

Do these need to come out will this keep the sites from being found? Coming to the box is not the Public IP which these are. They are not static IP's either.

Mike

---

### Post by Vegan on 2010-05-26
You should move the namedvirtual host to the HTTPD.CONF file at the top. You should also change the IP address to *:80 so that if you IP address changes you do not need to change any settings at all.

---

### Post by macmike on 2010-05-26
Is there anyway to do a copy and paste? I have an httpd.conf file now that is void of content.

Mike

---

### Post by macmike on 2010-05-26
When I restart apache2 Sever I still gt NameVirtualHost *:0 has no VirtualHosts
NameVirtualHost *:80 has no VirtualHosts
NameVirtualHost *:443 has no VirutalHosts

Then repeats the warnings again. Still can't get to the Domain outside of doing it locally by 127.0.0.1

I just did an nslookup 69.246.231.58 and got
Server 68.87.72.134
Address: 68.87.72#53

Non-authoritative answer:
58.231.246.69.in-addr.arpa  name = c-69-246-231-58.hsdq.il.comcast.net

What do I need to do to fix that?

Thanks,

Mike Hughes

---

### Post by Vegan on 2010-05-26
Are you behind a firewall or a NAT box?

---

### Post by macmike on 2010-05-26
I have been trying for weeks to get my virtual name hosting going. I want to host three of my sites myself. Is this not possible using Comcast as your ISP? When I do a nslookup of my wilmingtoncoc.com I get some comcast ip numbers. I am having trouble resolving to my server files as well.

Mike Hughes

---

### Post by -humanaut- on 2010-05-26
Comcast shouldn't be blocking it do you own the website in question the /block? Comcast will just throttle your connection.

---

### Post by halitech on 2010-05-26
> **macmike said:**
> Question: I have started searching through .conf files and see what I can find out. At the bottom of the apache2.conf file I have the following.

NameVirtualHost 69.246.231.58:80
<ifModule mod_ssl.c>
NameVirtualHost 69.246.231.58.443

Do these need to come out will this keep the sites from being found? Coming to the box is not the Public IP which these are. They are not static IP's either.

Mike

remove the virtual host stuff from the apache2.conf file.

what file(s) do you have listed in /etc/apache2/sites-available? Have you created files for the virtual hosts you want to host? have you enabled them? (as per the virtual hosts section on the link I gave you earlier?)

---

### Post by sylvester_0 on 2010-05-26
Looks fine to me:

```
Not Found

The requested URL / was not found on this server.
Apache/2.2.14 (Ubuntu) Server at www.wilmingtoncoc.com Port 80
```

You probably just don't have your vhosts set up correctly. You could drop a stock index.html into /var/www/ to see that it's working :)

---

### Post by halitech on 2010-05-26
don't start multiple threads

[http://ubuntuforums.org/showthread.php?t=1493981](http://ubuntuforums.org/showthread.php?t=1493981)

did you follow the instructions as per the link I gave you in post 6?

---

### Post by macmike on 2010-05-26
You probably just don't have your vhosts set up correctly. You could  drop a stock index.html into /var/www/ to see that it's working :smile:

How do I do that?

my DocumentRoot is /SERVER/wilmingtoncoc there is an index.html inside the wilmingtoncoc folder. It works I see it when I go locally.

Mike

---

### Post by lisati on 2010-05-26
> **halitech said:**
> don't start multiple threads
Agreed: Threads merged
> **macmike said:**
> You probably just don't have your vhosts set up correctly. You could  drop a stock index.html into /var/www/ to see that it's working :smile:

How do I do that?

my DocumentRoot is /SERVER/wilmingtoncoc there is an index.html inside the wilmingtoncoc folder. It works I see it when I go locally.

Mike
If you want to quote someone else's reply, you should use the [noparse]>  and [/noparse] tags, otherwise it could get confusing. The easiest way is to use the "quote" button: [IMG]http://ubuntuforums.org/images/buttons/quote.gif[/IMG]

---

### Post by macmike on 2010-05-26
> **Vegan said:**
> Are you behind a firewall or a NAT box?

Firewall in my router and in the Ubuntu Server.

Cool on the quote business, I wondered how they did that!

---

### Post by macmike on 2010-05-27
This morning. I can't get to the site at all. In my httpd.conf file I have

NameVirtualHost *:80
<VirtualHost *:80>
ServerName [www.wilmingtoncoc.com](www.wilmingtoncoc.com)
ServerAlias wilmingtoncoc.com *.wilmingtoncoc.com
DocumentRoot /SERVER/wilmingtoncoc
</VirtualHost>

<VirtualHost *:80>
ServerName [www.mikealrhughes.com](www.mikealrhughes.com)
ServerAlias mikealrhughes.com *.mikealrhughes.com
DocumentRoot /SERVER/wilmingtoncoc
</VirtualHost>

<VirtualHost *:80>
ServerName [www.biblematters.net](www.biblematters.net)
ServerAlias biblematters.net *biblematters.net
DocumentRoot /SERVER/biblematters
</VirtualHost>

When I restart apache2 I get an error that says VirtualHost *:80 -- mixing * ports and non-*ports with a NameVirtualHost is not supported, proceeding with undefined results
[Warn] NameVirtualHost *:80 has no VirtualHosts

Always any help appreciated.

---

### Post by halitech on 2010-05-27
remove the virtual host stuff from the httpd.conf file, it shouldn't be there as I've said twice. You need to use the virtual host files

> Virtual Hosts

Apache2 has the concept of sites, which are separate configuration files that Apache2 will read. These are available in /etc/apache2/sites-available. By default, there is one site available called default this is what you will see when you browse to [http://localhost](http://localhost) or [http://127.0.0.1](http://127.0.0.1). You can have many different site configurations available, and activate only those that you need.

As an example, we want the default site to be /home/user/public_html/. To do this, we must create a new site and then enable it in Apache2.

To create a new site:

    *

      Copy the default website as a starting point. sudo cp /etc/apache2/sites-available/default /etc/apache2/sites-available/mysite 
    *

      Edit the new configuration file in a text editor "sudo nano" on the command line or "gksudo gedit", for example: gksudo gedit /etc/apache2/sites-available/mysite
    *

      Change the DocumentRoot to point to the new location. For example, /home/user/public_html/
    *

      Change the Directory directive, replace <Directory /var/www/> to <Directory /home/user/public_html/>
    *

      You can also set separate logs for each site. To do this, change the ErrorLog and CustomLog directives. This is optional, but handy if you have many sites
    * Save the file 

Now, we must deactivate the old site, and activate our new one. Ubuntu provides two small utilities that take care of this: a2ensite (apache2enable site) and a2dissite (apache2disable site).

sudo a2dissite default && sudo a2ensite mysite

Finally, we restart Apache2:

sudo /etc/init.d/apache2 restart

If you have not created /home/user/public_html/, you will receive an warning message

To test the new site, create a file in /home/user/public_html/:

echo '<b>Hello! It is working!</b>' > /home/user/public_html/index.html

Finally, browse to [http://localhost/](http://localhost/)

normally I use the site names when I create the new virtual hosts files.

---

### Post by macmike on 2010-05-27
Ok I have done that. One thing I noticed when I ran ifconfig. The Web Server was no longer on 192.168.123.101 but had moved to 104. How do I set the box so that it has a static IP of 192.168.123.101? I went into my DynDNS service and set that IP address in the service and am now back to the error message

Not Found

The requested URL / was not found on this server.

Apache/2.2.14 (Ubuntu) Server at wilmingtoncoc.com Port 80

So I think this tells me it is getting to the box but for some reason, unbeknown to me is not getting to my /SERVER/wilmingtoncoc/index.html file. So what now.

Again, I appreciate all the help I can get. I am determined to get this going. So I can next figure out how to FTP into this and also put the site up using WordPress.

I am wondering if there is something missing out of one of my conf files that would direct it to the directory where my index.html file is. I don't know the chain of command from the time a command enters the webserver to finally getting to the index.html file.

Mike Hughes

---

### Post by halitech on 2010-05-27
you don't want to enter an IP of 192.168.x.x into DynDNS service, its a non-routable IP address and is only good on your local network, not the internet. You need to use the IP address that your router is getting from your ISP.

if your router supports it, you can assign IPs based on MAC addresses and leave the computer on DHCP

what do you have for files in /etc/apache2/sites-available now?

---

### Post by macmike on 2010-05-27
I have biblematters
default
default-ssl
michaelrhughes (needs to be renamed to mikealrhughes) how do I do that?
wilmingtoncoc

A fellow in Washington state was able to get in I think by way of SSH and set this up for me. Just spelled the directory for the mikealrhughes site wrong. My mother didn't know how Michael was suppose to be spelled she asked the nurse and she said spell it like it sounded so they came up with Mikeal. Anyway appreciate your help.

I am not attempting to move the other 2 sites until I see the wilmingtoncoc site going and able to get content into it through Wordpress. I know this is a big learning curve.

When I type into my browser on my iMac - 192.168.123.104 I get my index.html file from the wilmingtoncoc directory.
When I type in wilmingtoncoc.com I get the 404 error back from the Web Server.



Mike

---

### Post by halitech on 2010-05-27
after you created the sites-available, did you run
```
sudo a2ensite wilmingtoncoc
```
and 
```
sudo /etc/init.d/apache2 restart
```

---

### Post by macmike on 2010-05-27
I just ran the command again to make sure.  It returned a message 
Site wilmingtoncoc already enabled

The restart returns the warnings again
[warn] NameVirtualHost *:0 has no VirtualHost
[warn] NameVirtualHost *:80 has no VirtualHost

---

### Post by halitech on 2010-05-27
can you post the contents of the wilmingtoncoc file in sites-available

---

### Post by macmike on 2010-05-27
Just index.html
is listed.
When I did a sudo nano for the index.html it just says wilmingtoncoc.com
I believe for some reason the wilmingtoncoc.com is not resolving to that file. But can't figure out why. That is why I was checking my Dyndns stuff and my router settings. I now believe they are ok that it has to be something in the configuration of the Web Server. Some configuration file is not pointed in the right direction. I am green on the operation of Linux that I don't know what files to check. Macintosh, or Windows I would have no problem it is just like learning a new language. I have had that experience 6 times. It is a challenge until one day it clicks and you can think in that language. I have to get to where I can think in Linux but have to learn it before I can think it. Anyway, thanks for your patience with me in this endeavor.

Why is it I can type in 192.168.123.104 in a URL and get the index.html. But can't when I type in wilmingtoncoc.com. Does sound like a DNS issue somewhere to me I just can't put my finger on where in the Server box that problem would be. Does it go back to the site-enable/wilmingtoncoc file not accepting the NameServer *:80 line?


Mike

---

### Post by halitech on 2010-05-27
I'm not looking for the index file, I'm looking for the contents of the file /etc/apache2/sites-available/wilmingtoncoc.com

it should look like this:
```
<VirtualHost *:80>
	ServerAdmin joe@aol.com <change to correct email>
	ServerName wilmingtoncoc.com
	ServerAlias wilmingtoncoc.com *.wilmingtoncoc.com
	DocumentRoot <where ever you have the document root>
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory <where ever you have the document root>>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```

---

### Post by macmike on 2010-05-27
Ok here is what is in there

<VirtualHost *:80>
ServerName wilmingtoncoc.com
ServerAlias [www.wilmingtoncoc.com](www.wilmingtoncoc.com)
DocumentRoot /SERVER/wilmingtoncoc/
</VirtualHost>
<Directory /SERVERwilmingtoncoc/>
Options - Indexes FollowSymlinks MultiViews
AllowOverride All
Order allow, deny
Allow from all
</directory>

---

### Post by halitech on 2010-05-27
change it to this and enter the correct email address in the ServerAdmin line
> 
<VirtualHost *:80>
	ServerAdmin [email]joe@aol.com[/email] <change to correct email>
	ServerName wilmingtoncoc.com
	ServerAlias wilmingtoncoc.com *.wilmingtoncoc.com
	DocumentRoot /SERVER/wilmingtoncoc/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory <where ever you have the document root>>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>


---

### Post by macmike on 2010-05-27
Still get

**Not Found**

 The requested URL / was not found on this server.
  Apache/2.2.14 (Ubuntu) Server at wilmingtoncoc.com Port 80

---

### Post by halitech on 2010-05-27
is the DocumentRoot /SERVER/wilmingtoncoc/ correct? Linux is case sensative and SERVER is not the same as Server or server.

also did you change this line: <Directory <where ever you have the document root>>

---

### Post by macmike on 2010-05-27
> **halitech said:**
> is the DocumentRoot /SERVER/wilmingtoncoc/ correct? Linux is case sensative and SERVER is not the same as Server or server.

also did you change this line: <Directory <where ever you have the document root>>
  Yes the DocumentRoot is /SERVER/wilmingtoncoc

Yes I changed the line <Directory <where ever you have the document root>> to
<Directory </SERVER/wilmingtoncoc>> or should it just be /SERVER there?

---

### Post by macmike on 2010-05-27
Where do I need to put the line 
NameVirtualHost *:80 or do I need that line. It was in my apache2.conf file. Someone told me to put it in the httpd.conf file. Is that why it is not resolving my 192.168.123.104 over to my wilmingtoncoc directory?

I looked in /etc/apache2/conf.d there is a file called virtual.conf

It has inside 

#
# We're running multitude virtual hosts.
#
NameVirtualHost *:80

Is that file needed? 

Mike

---

### Post by halitech on 2010-05-27
change <Directory </SERVER/wilmingtoncoc>> to <Directory /SERVER/wilmingtoncoc>

the only place you need to put NameVirtualHost *:80 is in the sites-available file

make sure the last line in your apache2.conf file has is this:
```
# Include the virtual host configurations:
Include sites-enabled/

```

---

### Post by macmike on 2010-05-27
Question for anyone:

I have a resolv.conf file that was created I guess by the server.

Right now it has this

nameserver 68.87.72.134
nameserver 68.87.72.134
domain hsd1.il.comcast.net.
search hsd1.il.comcast.net.

Can I change that to an open DNS to see if this is my resolving problem? Does anyone know of a good open DNS ip to change it too? 

Mike Hughes

---

### Post by halitech on 2010-05-27
its not your DNS servers that are the issue as I can hit the server but apache doesn't know where to direct things to.

> 
Not Found

The requested URL / was not found on this server.
Apache/2.2.14 (Ubuntu) Server at wilmingtoncoc.com Port 80

---

### Post by macmike on 2010-05-27
So the $64,000 question is what is keeping Apache from knowing where to direct things? What keeps the Web Server from Resolving?

---

### Post by halitech on 2010-05-27
the server is resolving, thats why you get an error code, there is something going on with the sites-available file

can you post the contents of /etc/apache2/sites-available/wilmingtoncoc.com now

---

### Post by macmike on 2010-05-27
Question how can I get to that from this computer without having to be at the server and no way to get it over here with out retyping all the lines?

the file is named wilmingtoncoc not wilmingtoncoc.com does that make a difference?


Mike

---

### Post by halitech on 2010-05-27
how are you making changes to files now?

---

### Post by macmike on 2010-05-27
How can I save the file to a flash drive and then bring it over here and copy and paste?

---

### Post by halitech on 2010-05-27
try this
```
sudo apt-get install pastebinit
```
```
pastebinit /etc/apache2/sites-available/wilmingtoncoc
```
that will give you a URL that you can open on your desktop and then copy and paste the info here

as far as the name of the file, no it doesn't as long as you are getting the info from the right file

---

### Post by macmike on 2010-05-27
At least I am getting my typing practice in today.

NameVirtualHost *:80

<VirtualHost *:80>
ServerAdmin [email]mail@mikealrhughes.com[/email]
ServerName wilmingtoncoc.com
ServerAlias [www.wilmingtoncoc.com](www.wilmingtoncoc.com) *.wilmingtoncoc.com
Document Root /SERVER/wilmingtoncoc/
<Directory />
Options -FollowSymLinks MultiViews
AllowOverride none
</Directory>
<Directory <SERVER/>>
Options Indexes FollowSymLinks MultiViews
Allow Override None
Order allow, deny
Allow from all
</Directory>

ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
<Directory "usr/lib/cgi-bin">
AllowOverride None
Options +excecCGI -MultiViews +SymlinksIfOwnerMatch
Order allow,deny
Allow from all
</Directory>

ErrorLog /var/log/apache2/error.log

#possible values include: debug, info, notice, warn, error, crit,
# alert, emerg.
LogLevel warn

CustomLog /var/log/apache2/access.log combined

Alias /doc/"user/share/doc/"
<Directory "usr/share/doc/">
Options Indexes MultiViews FollowSymLinks
AllowOverride None
Order deny, allow
Deny from all
Allow from 127.0.0.0/255.0.0.0 ::1/128
</Directory>
</VirtualHost>

---

### Post by halitech on 2010-05-27
change the line in red

```

<VirtualHost *:80>
ServerAdmin xxxxxx@mikealrhughes.com
ServerName wilmingtoncoc.com
[color="red"]ServerAlias wilmingtoncoc.com *.wilmingtoncoc.com[/color]
Document Root /SERVER/wilmingtoncoc/
<Directory />
Options -FollowSymLinks MultiViews
AllowOverride none
</Directory>
[color="red"]<Directory /SERVER/wilmingtoncoc/>[/color]
Options Indexes FollowSymLinks MultiViews
Allow Override None
Order allow, deny
Allow from all
</Directory>

ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
<Directory "usr/lib/cgi-bin">
AllowOverride None
Options +excecCGI -MultiViews +SymlinksIfOwnerMatch
Order allow,deny
Allow from all
</Directory>

ErrorLog /var/log/apache2/error.log

#possible values include: debug, info, notice, warn, error, crit,
# alert, emerg.
LogLevel warn

CustomLog /var/log/apache2/access.log combined

Alias /doc/"user/share/doc/"
<Directory "usr/share/doc/">
Options Indexes MultiViews FollowSymLinks
AllowOverride None
Order deny, allow
Deny from all
Allow from 127.0.0.0/255.0.0.0 ::1/128
</Directory>
</VirtualHost>
```

one other question, is /SERVER in your root directory or is it a folder inside /var/www/ ?

---

### Post by macmike on 2010-05-27
SERVER is in the root directory

---

### Post by halitech on 2010-05-27
ok, did you make those 2 changes and restart apache yet?

---

### Post by macmike on 2010-05-27
Yes I did. No difference. The 192.168.123.104 is giving me the NOT Found message now.

Mike

---

### Post by halitech on 2010-05-27
what does
```
sudo ls -l /SERVER
```
give for output?

---

### Post by macmike on 2010-05-27
Output is
biblematters
ip
mikealrhughes
wilmingtoncoc

---

### Post by halitech on 2010-05-27
what is your external IP address?
go to [www.ipchicken.com](www.ipchicken.com) if you aren't sure

---

### Post by macmike on 2010-05-27
*.*.*.*

---

### Post by macmike on 2010-05-27
Is there a config file that would be running that would keep it from getting to site-enabled?

---

### Post by halitech on 2010-05-27
try disabling the default
```
sudo a2dissite default
```

also, go back and edit the IP address now, I wrote it down in case I need it again. wilmingtoncoc.com is resolving to the correct ip address.

---

### Post by macmike on 2010-05-27
It says already disabled.

---

### Post by macmike on 2010-05-27
> **halitech said:**
> try disabling the default
```
sudo a2dissite default
```also, go back and edit the IP address now, I wrote it down in case I need it again. wilmingtoncoc.com is resolving to the correct ip address.


How do I go back and edit the IP address

Duh! I did it.

---

### Post by halitech on 2010-05-27
the only thing I can think of would be in /etc/apache2/apache2.conf not having this line

# Include the virtual host configurations:
Include sites-enabled/

---

### Post by halitech on 2010-05-27
> **macmike said:**
> How do I go back and edit the IP address

on the post where you listed it here, you should see a button called edit, click that and you can edit the number

---

### Post by macmike on 2010-05-27
Ok I put that line and restarted apache2.

I now get Warning: DocumentRoot [/WEBSERVER/biblematters/] does not exist.
Syntax error on line 14 of /etc/apache2/sites-enabled/wilmingtoncoc:
allow and deny must be followed by 'from'

I know the first problem but not sure about the from.

Mike

---

### Post by halitech on 2010-05-27
first warning you can resolve by creating the folder

second one, edit line 14

change it from
Allow Override None
to
AllowOverride None

and then restart apache again

---

### Post by halitech on 2010-05-27
just thought of something. you say /SERVER is in the root directory, what are the permissions on the folder?

```
ls -l /
```

---

### Post by macmike on 2010-05-27
Ok, have a Syntax error on like 35 of /etc/apache2/sites-enable/wilmingtoncoc
Alias takes two arguments, a fakename and a realname

Looked in my Apache book after much searching found out left out some " and that solved the problems. I don't know how to mark this thread solved. 

Thanks halitech appreciate your patience. Now on to posting to see how to get into the programs and get content on this Server

Mike Hughes

---

