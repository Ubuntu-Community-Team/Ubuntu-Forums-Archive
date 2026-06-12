---
title: "[SOLVED] Apache access log and document root"
date: 2008-07-17
forum: Server Platforms
---

### Post by f37u5g0d on 2008-07-17
I am using the default configurations of apache and my website is working but I have 2 problems. One is that the access log is completely blank and 2 is that apache insists that my website be located in /htdocs even though there is no mention in any of the config files about /htdocs. I figuered out it need to be there from the error log which is fully functional (unlike access log). Here is the url to my website

novak.homelinux.net

---

### Post by windependence on 2008-07-17
Ed, didn't we have a thread on this just a bit ago?

Apache 1.3 uses /var/www/htdocs as the web root by default. What makes you think this is what Apache thinks? Do you have your files in that directory? What is in /var/log?

-Tim

---

### Post by f37u5g0d on 2008-07-17
First off I am using apache 2.2 secondly I don't have anything in /var/www.  It is literally empty.  My website in it's entirety is located in /htdocs.  (which btw is a link to a folder in my home dir).

I do remember that thread but I though I'd make a new thread to try and solve these two problems because the old thread seemed to have fell by the wayside.

What I can't figure out is why my sites-enabled folder in /etc/apache2 has a configuration file that says the document root is /var/www.  If I place files there they don't show up and the error log at /var/log/apache2/error.log starts telling me that /htdocs is not found?  My website will only work if I put the files for it in /htdocs.

---

### Post by zachtib on 2008-07-17
have you tried reloading apache? that just fixed the logging issue for me

---

### Post by f37u5g0d on 2008-07-17
I have tried sudo /etc/init.d/apache2 reload several times yes.  Doesn't solve the problem for me :(  Thanks for trying though!

---

### Post by zipperback on 2008-07-17
You need to configure your apache server configuration file to store the access logs for your domain name.

Example:

<VirtualHost 192.0.0.1>
ServerName domain.com
DocumentRoot "/home/username/html/"
ErrorLog /home/username/logs/error.log
</VirtualHost> 


This would specify your document root to be:
/home/username/html/

And your error logs would be stored in:
/home/username/logs/error.log


Here are two links which can answer more of your questions regarding log files and apache.

[http://httpd.apache.org/docs/2.2/logs.html](http://httpd.apache.org/docs/2.2/logs.html)
[http://httpd.apache.org/docs/2.2/mod/mod_log_config.html#customlog](http://httpd.apache.org/docs/2.2/mod/mod_log_config.html#customlog)


- zipperback
:popcorn:

---

### Post by dmizer on 2008-07-17
please post:
```
ls /etc/apache2/sites-enabled
```
and post the contents of:
```
/etc/apache2/sites-available/default
```

---

### Post by f37u5g0d on 2008-07-18
Hi dmizer (thank you for all of your help!!)

ls /etc/apache2/sites-enabled
000-default  000-default~

**sudo** **gedit** /etc/apache2/sites-availabe/**000-**default
NameVirtualHost novak.homelinux.com
<VirtualHost novak.homelinux.com>
	ServerAdmin [email]enovak@monm.edu[/email]
	
	DocumentRoot /var/www/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
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
	ServerSignature On

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

### Post by mbeach on 2008-07-19
something must be pointing to htdocs.  try something like
```
cd /etc/apache2/
grep -iR htdocs *
```
which should list files with any mention of htdocs.  Perhaps there's a directive dangling around somewhere.

---

### Post by mbeach on 2008-07-19
and could you post the lines from your error log indicating that its looking in htdocs?

---

### Post by mbeach on 2008-07-19
and just for fun, after reading a bit more of your issue at
[http://ubuntuforums.org/showthread.php?t=853867](http://ubuntuforums.org/showthread.php?t=853867)
try removing the trailing slash on DocumentRoot so that it reads
DocumentRoot /var/www
but leave the 
<Directory /var/www/>
line.

do a 
sudo /etc/init.d/apache2 reload

after changing the /etc/apache2/sites-available/default file

then try hitting your server from another pc on your own network.

---

### Post by f37u5g0d on 2008-07-19
cd /etc/apache2/
grep -iR htdocs *
Returned nothing

Excerpt from /var/apache2/log/error.log.1
[Thu Jul 10 17:46:27 2008] [error] [client 192.168.1.1] File does not exist: /htdocs
[Thu Jul 10 17:46:27 2008] [error] [client 192.168.1.1] File does not exist: /htdocs
[Thu Jul 10 17:46:30 2008] [error] [client 192.168.1.1] File does not exist: /htdocs
[Thu Jul 10 17:54:35 2008] [error] [client 192.168.1.1] File does not exist: /htdocs
[Thu Jul 10 17:54:35 2008] [error] [client 192.168.1.1] File does not exist: /htdocs
[Thu Jul 10 17:54:39 2008] [error] [client 192.168.1.1] File does not exist: /htdocs
[Thu Jul 10 17:54:39 2008] [error] [client 192.168.1.1] File does not exist: /htdocs
[Thu Jul 10 17:54:56 2008] [error] [client 192.168.1.1] File does not exist: /htdocs
[Thu Jul 10 18:12:05 2008] [notice] caught SIGWINCH, shutting down gracefully
[Thu Jul 10 18:13:19 2008] [notice] Apache/2.2.8 (Ubuntu) configured -- resuming normal operations
[Thu Jul 10 18:14:49 2008] [error] [client 192.168.1.1] File does not exist: /htdocs
[Thu Jul 10 18:14:49 2008] [error] [client 192.168.1.1] File does not exist: /htdocs
[Thu Jul 10 18:14:52 2008] [error] [client 192.168.1.1] File does not exist: /htdocs
[Thu Jul 10 18:15:13 2008] [error] [client 192.168.1.1] File does not exist: /htdocs
[Thu Jul 10 18:15:14 2008] [error] [client 192.168.1.1] File does not exist: /htdocs

Do I need quotes around /var/www/ on the document root line in 000-default?
I will try your trick of removing the trailing slash and I will try my idea of removing the quotes and get back to you I only have time to post this real quick before I go to work.  Thanks again for all of your help!

---

### Post by f37u5g0d on 2008-07-19
I tried every combination of adding/removing the slash and add/removing the quotes.  After each change I reloaded apache and accessed the site.  None of the changes made a difference.  After the entire test I looked at the access-log which was still blank.  

I thought maybe I needed quotes or no trailing slash or something was wrong with the syntax of that line and it is defaulting to /htdocs without any implication from any conf files but that doesn't seem to be the case.  I switched /var/www/ to "/filedoesnotexist" to both the Directory line and the Document root line.  When I reload apache it yells at me.
"Warning: DocumentRoot [/filedoesnotexist] does not exist
[Sat Jul 19 10:40:02 2008] [warn] NameVirtualHost novak.homelinux.com:0 has no VirtualHosts"
So clearly the 000-default has no syntax error and recognizes that /var/www is a valid file so why doesn't it need my website there?
My 000-default file is now back to how it started with /var/www/ on the document root line and on the directory line.  My website is now up.

---

### Post by mbeach on 2008-07-19
certainly perplexing.

to review:
/var/www is completely empty, 
your /etc/apache2/sites-available/default file points to /var/www/ as your documentRoot, 
yet files in /htdocs are being served.  
/htdocs is a symlink to a folder in your home folder

your site will work locally but not from another machine on the same network?  Is it possible you are accessing your files from the server's browser not using apache at all?  What are you using for a url:  [http://localhost/index.html](http://localhost/index.html) or something like /htdocs?  Sorry if thats an offensive question - just ruling it out.

If you put a simple index.html in /var/www/ and browse to [http://localhost](http://localhost) your access.log doesn't register anything, but the error.log shows a file not found?  I think I'd ignore the error.log as its my gut feeling that perhaps thats a red herring (some html file with a bad link).

---

### Post by f37u5g0d on 2008-07-19
I'm not offended by anything you've said so don't worry about that  :).  To review:

/var/www is completely empty : true
/etc/apache2/sites-available/default point to /var/www/ as document root : true
files in htdocs are being served : true
/htdocs is a symlink to a folder in /home : true

My site works locally and long distance.  It worked when I accessed it at work on a different machine on a different network with a different ISP.  You can see it right now if you go to [http://novak.homelinux.net](http://novak.homelinux.net) .  Again not offended at all by this question or anything else you've said.

I'm confused about the last question.  I put a dummy index.html in /var/www specifically what should I browse to?  [http://*my](http://*my) ip address*? or [http://*novak.homelinux.net](http://*novak.homelinux.net)*?  My error file is working and I don't think it is a red herring.  I have used it to fix other problems like my favicon for example and to figure out permission problems.  My access log is blank and has always been that way.

---

### Post by mbeach on 2008-07-20
I'm out of ideas. There has to be a setting somewhere pointing Apache to /htdocs instead of /var/www 

I can see your website so you've obviously got stuff set up but as to why its not using what you've got in the conf files is interesting. 

I didn't mean completely ignore the error.log - just in this situation it is finding htdocs since your website is up and running but saying that it cannot - which is a bit misleading. It assisted in finding where apache was looking for your files, so that's good, but not giving much info as to why its looking to /htdocs in the first place. 

good luck, I'm sure you'll find the reason why as you continue. 
mb.

---

### Post by f37u5g0d on 2008-07-20
Ok.  Thank you for your help mbeach.  Just so you know my error log only says /htdocs does not exist (like in the example I posted) when that file truely doesn't exist.  Otherwise it doesn't mention it.  I should have been more clear but the error log is accurate as far as I can tell.  Although while it does tell me that my site needs to be in /htdocs you're right and it sucks that it won't tell me why they need to be there.  Hopefully someone else will read this and have some sort of solution.  I consider myself to be pretty good with computers and this totally baffles me.  Is there a good apache forum out there anybody?

(o and btw, bump)

---

### Post by windependence on 2008-07-20
Can you post your httpd.conf?

-Tim

---

### Post by f37u5g0d on 2008-07-20
All that my httpd.conf holds is two lines.

ServerName novak.homelinux.com
ServerName novak.homelinux.net

I am using a webhop url from dyndns from .homelinux.net to .homelinux.com:75 so that you don't have to type the :75 and the website can be viewed from ie.  I left the .homelinux.com in case for some reason I want/need to access the site from .homelinux.com:75.

---

### Post by windependence on 2008-07-21
You should remove one of these, in fact, you should remove all of these from here and put ONE in your main conf file. httpd.conf is deprecated and is only there to support upgrades from 1.3. Your server only has one FQDN so two directives are probably not good. If you want the .net to go to the .com, just point it at the .com in your domain DNS with your registrar and mask the domain. Also, I don't know what dynamis DNS service you use, but with no-ip, I can point my domain to their servers, and then point their servers at my server, including the port. They support masking so you won't see the port.

-Tim

---

### Post by f37u5g0d on 2008-07-21
I use dyndns and they allow me to do the same thing as you to specify a port and hide it in the url.  I am assuming that FQDN is my ServerName but what does FQDN stand for?  Also any suggestions on my no access log / website in mysterious folder problems?  Thank you!

Edit: And yes I moved the contents of httpd.conf into apache2.conf and I only specified one ServerName.

---

### Post by windependence on 2008-07-21
FQDN is fully qualified domain name. It's done like this:

server.yourdomain.tld

Example:

server1.example.com

At the command line do this:

```
hostname -f
```

and tell me what you get.

-Tim

---

### Post by dmizer on 2008-07-21
actually, i have a suggestion for you.

instead of trying to tweak apache to do your will, try using [lighttpd](http://www.lighttpd.net/) instead.  it's in the repositories. more information on configuration here: [http://ubuntuforums.org/showthread.php?t=245932](http://ubuntuforums.org/showthread.php?t=245932)

most of the documentation for lighttpd works just fine in ubuntu.  everything i needed to do, i learned here: [http://trac.lighttpd.net/trac/wiki/Docs](http://trac.lighttpd.net/trac/wiki/Docs)

fast, simple, scalable, and reports indicate that it's more secure than apache2.

not really "fixing" your problem exactly, but i think you'll be much more satisfied with lighttpd.  i know i am.

---

### Post by f37u5g0d on 2008-07-29
Hi dmizer.  I took your suggestion and tried to install lighttpd as my webserver software.  I am having some trouble getting startes though.  I understand the syntax mostly but I just don't know specifically what I need to put in a file and where that file needs to go in order to start serving my site.  I need a simplified explanation and all I can find on the web are sites that explaim how to use lighttpd and php or cgi scripts.  That would be nice but how do you get your site online first?

---

### Post by f37u5g0d on 2008-07-30
I'm going to start a new thread as this next post I'm going to make is quite off topic from the original title.  Basically I have switched to lighttpd and never did fix my problems with apache.

---

### Post by Blackneto on 2008-08-04
I realize the OP has moved on but I had the same problem and found the solution here:
[http://ubuntuforums.org/showthread.php?t=668979](http://ubuntuforums.org/showthread.php?t=668979)

```
 Re: '[error] [client ::1] File does not exist: /htdocs'
Ok, I've figured it out...

The "[client ::1]" represents the loopback connection, so this is invoked from some internal process, and "::1" = the loopback address 127.0.blah blah.

Now all the virtualhosts I have are defined by explicit IP addresses. There is no virtualhost defined for the loopback IP. Furthemore, there was no default DocumentRoot defined in /etc/apache2.conf.

So I added:

DocumentRoot "/home/www"

in /etc/apache2.conf & the problem appears to be solved.
```

I changed **/home/www** to **/var/www** but it worked.

---

### Post by f37u5g0d on 2008-08-05
Thanks now I can mark this as sloved :)

-The OP

---

