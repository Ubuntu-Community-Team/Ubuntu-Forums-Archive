---
title: "Apache2/Virtual Hosts"
date: 2005-04-25
forum: Server Platforms
---

### Post by Eningo Montoya on 2005-04-25
I'm trying to figure out how to add multiple virtual hosts to the apache2 configuration.  Here's what I understand...

1.) There is no more httpd.conf.  It exists, but is empty.  Everything is done in apache2.conf.

2.) Virtual sites are added in /etc/apache2/sites-available/virtual_site_file. Then, a symbolic link is added to /etc/apache2/sites-enabled/virtual_site_file to enable the virtual site. 

However, I'm not able to get more then one website working. So far, I have the default virtual site modified with one of my domain websites. I've tried adding other websites for other domains, but I don't understand what I have to do. Is it just a matter of adding another file to /etc/apache2/sites-available/another_virtual_site_file and then symbolically linking that to /etc/apache2/sites-enabled/another_virtual_site_file?

---

### Post by chapterthree on 2005-04-25
Yep, that's all I do, create a new virtual host file in sites-available, then symlink it in sites-enabled.

---

### Post by jdonnell on 2005-04-25
you could add it to the  /etc/apache2/sites-available/default to see if that works. It's not as clean as the other way, but see if it works. 

Stupid question, did you restart apache after you made the changes?

Paste one of your virtual host directives if your still stuck.

---

### Post by Eningo Montoya on 2005-04-25
Not a stupid question - I've done it before, but this time, I did restart apache.  I also did copy my virtual host into the default and that worked.  What is the last line (the include line) for in the apache.conf file?  Am I supposed to add an include line for every virtual host file I have - by the looks of it, I shouldn't have to.  I'll try simply adding the files to sites-available and linking them to sites-enabled and see what happens.

---

### Post by MJWhiteDerm on 2007-09-23
I have a similar problem.  That is, I have followed the instructions in the Ubuntu HTTPD - Apache2 Web Server documentation and I still can't get the virtual hosting to work.

Apache2 is working fine.  I have 6.06 running on another machine.  It has several web pages.  My fixed IP address is 64.91.78.105  and all of my  multiple DNS entries point to that address.  (I actually own a whole range of addresses, but I kept it simple for the moment because of a possible router issue.)

[www.cthia.com](www.cthia.com) points to 64.91.78.105 and is now the default web page.  It comes up fine.  That is, I call up  my friend and say, look at the web site _______ (there are several), and apache shows the web site.  The DEFAULT web site is now cthia, and it shows up fine out on the external world.

[www.laxlinux.com](www.laxlinux.com) also points to the same external IP and my router successfully sends a port 80 request to the same internal machine.  But ... cthia comes up.  [www.laxlinux.com/laxlinux](www.laxlinux.com/laxlinux) loads the correct page.  Ditto for /mikhailbadenov  or /primumnonnocere  which are two other web pages.

I copied the file /etc/apache2/sites-available/default file and made modifications.  The default file now points to cthia.  I modified the copies and have one for laxlinux and one for mikhailbadenov and one for primumnonnocere.

I enabled laxlinux and mikhailbadenov, as per the instructions in the ubuntu documentation with sudo a2ensite laxlinux (etc) for each site.  Each site's file in /sites-available is appropriately copied over to sites-enabled and I restarted apache2.  There is a ServerName statement in each file and a DirectoryRoot statement in each file, pointing to the respective directories.  The RedirectMatch statement in each file is modified to reflect the appropriate virtual host.

When I reboot apache2, I get a statement:
Name or service not known: Cannot resolve host name laxlinux (or [www.laxlinux](www.laxlinux)) -- Ignoring!

If I try to put these directives in apache2.conf, it chokes and gives me a FAIL message.

I'm missing something, somewhere.

Anyone have any clue what I might be forgetting?

also: [email]michael.white@gemair.com[/email]

Thanks, in advance.

Michael

---

### Post by lifewithryan on 2007-09-24
Any chance I could see the site config files....

Just from hitting the site, its looks as if the rewrite rule could be messed up.
do you "need" a rewrite rule?

so for Servername on laxlinux you've got : [www.laxlinux.com](www.laxlinux.com) and DocumentRoot is pointing to /path/to/laxlinux/files?

If you have all that setup, my first guess is that your rewrite rule is taking everything and passing to /cthia.  HOWEVER, if it were only the rewrite rule, I would think that would fail unless you have a /cthia directory under laxlinux as well...

I setup my sites in "home" directories for my servers...so:
/home/laxlinux
/home/cthia
/home/whatever

and then my site file for laxlinux would be:
ServerName [www.laxlinux.com](www.laxlinux.com)
DocumentRoot /home/laxlinux

and for cthia would be:
ServerName [www.cthia.com](www.cthia.com)
DocumentRoot /home/cthia

I wouldn't even be using a rewrite rule unless I put it in a .htaccess at the root of one of those sites...that way they don't stomp on the other virtual sites you are running.

---

### Post by MJWhiteDerm on 2007-09-25
I can't answer the question about rewrite rule, until I get home and revisit the files.  However, there is one other potential issue, pointed out by someone else .. .I uncommented the RedirectMatch line in the default configuration file ... so instead of pointing to

/etc/apache2/apache2-default

for the other sites, it points to

/etc/apache2/laxlinux      or
/etc/apache2/mikhailbadenov
/etc/apache2/primumnonnocere     and so on.

Someone else suggested commenting those lines out.  I realize, as I look at them, that those directories are not found in /etc/apache2  but are only found in /var/www  .... so clearly that move (done on autopilot) is not helping things.

My email is [email]michael.white@gemair.com[/email]   ... if you drop me a line I will email the files to you.  First, I'm going to comment those lines in the config files  back out (except for the default).

Michael

---

### Post by clw3388 on 2008-04-13
I too HAD the same problem with only my default site showing...
i read 
[http://www.debianhelp.co.uk/virtualhosts.htm](http://www.debianhelp.co.uk/virtualhosts.htm)
and it indicates:
A   VirtualHost entry must also be configured for the domain originally hosted on the server ([www.example.com](www.example.com)).

So in other words you have 2 sites. example1.com and example2.com
with what i gather you copied example1.com directives and put it in the default file located at /etc/apache2/sites-available.. this dont work..
(at least it didnt mine)..
You must (according to document) create 2 separate files and setup symlinks to both..

so in /etc/apache2/sites-available you create files called example1 and example2 then edit directives using default as a guide.. once all directive are set for document root etc,ect, you create symlinks to /etc/apache2/sites-enabled by running the sudo a2ensite example1 and again run it for example2. sudo a2ensite example2. then force a reload of apache (sudo /etc/init.d/apache2 force-reload) (or restart)

Worked for me and my dynamic ip address using dnsexit :):guitar:

---

