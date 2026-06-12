---
title: "Apache error: 404 Not Found, why?"
date: 2006-08-14
forum: Server Platforms
---

### Post by cocotu on 2006-08-14
Hello friends, some time ago I was told that if I place a file at /var/www/"anything" at the DocumentRoot it will be as my index file. Now, I installed the MediaWiki and I place the DocumentRoot like this and I restarted Apache: 

/var/www/mwiki1.7.1

And I get this error:

Not Found
The requested URL /mwiki1.7.1/index.php/Main_Page was not found on this server.
--------------------------------------------------------------------------------

Apache/2.0.55 (Ubuntu) PHP/5.1.2 Server at 10.0.3.107 Port 80

I tried this with a CMS called Jupiter and it worked fine. I not sure if this error has to do with MediaWiki.

Thanks...

---

### Post by lvanderree on 2006-08-14
I think this is because

/mwiki1.7.1/index.php/Main_Page 

does not exist and 
index.php is a file and not a directory.

How you can solve this is by enabling the mod-rewrite plugin for php and apache. mod-rewrite can rewrite urls so for example the look like directories while they actually are php-arguments.

this can be done from the command prompt if you have apache2 (might work the same for apache1) with:

```
a2enmod rewrite
```

this creates a symlink in the etc/apache2/mods-enabled directory for the rewrite module

Ps. it might be possible that you again need to restart apache to let this change be applied

---

### Post by cocotu on 2006-08-14
Ivanderree, I typed the command above, but I with no success.  I went to DocumentRoot and did this:

DocumentRoot var/www/mwiki1.7.1
then I tried this:

DocumentRoot var/www/mwiki1.7.1/index.php
then I tried this:

DocumentRoot var/www/mwiki1.7.1/index.php/Main_Page

Nothing happened, and I did restart Apache after every change. Every time I restarted Apache I got:

"Warning: DocumentRoot [/var/www.mwiki1.7.1/index.php] does not exist" this also happened when I included the /Main_Page folder. And when I leave just "DocumentRooot /var/www" I get:

Index of /
 Name                    Last modified      Size  Description-------------------------------------------------------------------------------- ControlYourTime.mht     15-May-2006 17:42   21K  
 Joomla1-0/              01-Aug-2006 18:05    -   
 Jupiter1.5/             27-Apr-2006 17:37    -   
 apache2-default/        01-Aug-2006 12:42    -   
 http.doc                17-Jan-2006 17:53   19K  
 mwiki1.7.1/             09-Jul-2006 04:45    -   
--------------------------------------------------------------------------------
Apache/2.0.55 (Ubuntu) PHP/5.1.2 Server at 10.0.3.107 Port 80

Before I was able to just type the IP number of the server and get the contents of the Jupiter1.5 CMS, I just included in "DocumentRoot /var/www/Jupiter1.5" and it took me directly into the index.php of Jupiter.  I don't know what is the difference now?? Please help!!!!

---

### Post by lvanderree on 2006-08-14
OK I'll try to be a little more specific.

First you where supposed to enter the line:
a2enmod rewrite
at the console of ubuntu (not in a browser as URL, but I suppose you have done that)

Then I think you want
/var/www/mwiki1.7.1
as your DocumentRoot 

But please also make sure that you have index.php as one of the files at DirectoryIndex in /etc/apache2/apache2.conf

If you have that and then restart apache by using the command
sudo /etc/init.d/apache2 force-reload

It is supposed to be working, or else please reply with the error you see in your browser when you go to your server.

---

### Post by cocotu on 2006-08-14
Ok Ivanderree, this is what I have in the 
etc/apache2/apache2.conf:

DirectoryIndex index.html index.cgi index.pl index.php index.xhtml

I follow all your steps and this is what I get at the browser:

The page cannot be found 
The page you are looking for might have been removed, had its name changed, or is temporarily unavailable. 

--------------------------------------------------------------------------------

Please try the following:

If you typed the page address in the Address bar, make sure that it is spelled correctly.

Open the 10.0.3.107 home page, and then look for links to the information you want. 
Click the  Back button to try another link. 
Click  Search to look for information on the Internet. 

HTTP 404 - File not found
Internet Explorer 

Thanks for your help..

---

### Post by lvanderree on 2006-08-14
Can it be that apache hasn't got the rights to open the mywiki directory?

A simple fix for this should be

```
sudo chown www-data -R /var/www/mwiki1.7.1
```

otherwise try to install the mediawiki from the ubuntu archive:
[http://meta.wikimedia.org/wiki/Help:Running_MediaWiki_on_Ubuntu_GNU/Linux](http://meta.wikimedia.org/wiki/Help:Running_MediaWiki_on_Ubuntu_GNU/Linux)

But I think that changing the owner of the mywiki folder (and all its subfolders with -R) could be the solution...

---

### Post by cocotu on 2006-08-14
Ivan, I got the same error message above

Not Found
The requested URL /mwiki1.7.1/index.php/Main_Page was not found on this server.

I'm going nuts, because with other CMS everything worked fine. But here at work they decided to use MediaWiki. 

Thanks for the help Ivan. So you think installing mediawiki from the ubuntu archive is an easier way? Would it work the same?
Ivan why are there so many commands to restart Apache?:

sudo apachectl restart
sudo /etc/init.d/apache2
sudo invoke-rc.d apache2 restart

Why? Is there a diff.? Well thanks again and if you think of something please let me know!!

---

### Post by lvanderree on 2006-08-14
First of all I was a little confused about the name Ivan, my name is Leon ;-) So I was searching in the messages above for an Ivan. But I can imagine why you thought lvanderree stands for Ivan (but the first letter is an L the rest is my surname).

But I really think it is strange that it still isn't working.

I will show you most of my config files, maybe we then can find the cause of the problem.

Because your web-browser says that it can't find the document, and you changed the owner of the mywiki directory I think that there still is some config file of apache not setup correctly.

When you go with your browser to the address of your server (I think 10.0.3.107), Do you then still see:
```

Index of /
Name Last modified Size Description-------------------------------------------------------------------------------- ControlYourTime.mht 15-May-2006 17:42 21K 
Joomla1-0/ 01-Aug-2006 18:05 - 
Jupiter1.5/ 27-Apr-2006 17:37 - 
apache2-default/ 01-Aug-2006 12:42 - 
http.doc 17-Jan-2006 17:53 19K 
mwiki1.7.1/ 09-Jul-2006 04:45 - 
--------------------------------------------------------------------------------
Apache/2.0.55 (Ubuntu) PHP/5.1.2 Server at 10.0.3.107 Port 80

```

Because if so, you probably didn't set the DocumentRoot correctly, maybe misspelled it, or more probably at an wrong location.
It looks like the DocumentRoot in this case still points to /var/www and that's why you see mywiki1.7.1/ as one of the files/directories at the page.

If you click on this folder mywiki1.7.1 do you then see your wiki or yet an other error?

If this link to the folder does work, which probably is [http://10.0.3.107/mywiki1.7.1/](http://10.0.3.107/mywiki1.7.1/) in your browser, then the only thing which needs to be done is find the correct location of the DocumentRoot.

I don't know where you changed this setting, but I think it should be done in
/etc/apache2/sites-available/default
there you see the settings of the default website which apache will show when you go to [http://10.0.3.107](http://10.0.3.107) 
And if I'm correctly you can find the DocumentRoot on the 5th line, edit this 
from /var/www 
to /var/www/mywiki1.7.1 

save it and restart apache again with 
/etc/init.d/apache restart (the default way of doing it in Ubuntu/Debian)

In debian and Ubuntu all initialization scripts are located at /etc/init.d so if you ever need to start/stop/reload/restart a service look at that folder for a file matching your application.

Tell me what your findings are this time, one day we will tackle the problem ;-)

---

### Post by cocotu on 2006-08-15
Ok Lvanderree, sorry for the confusion. So I see that you are in the Netherlands, how everything there? Well, I was told to make the changes in the /etc/apache2/sites-enabled/000-default, this worked for the other CMS that I was using. For some reason when I make changes let say DocumentRoot /var/www/mwiki1.7.1 in the 000-default it also changes in the /etc/apache2/sites-available/default file. Is this OK? Here is the file 000-default:

NameVirtualHost *
<VirtualHost *>
	ServerAdmin 
	
	DocumentRoot /var/www/mwiki1.7.1[COLOR="Red"]This is where you make the changes, right?[/COLOR]
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
		# Uncomment this directive is you want to see apache2's
		# default start page (in /apache2-default) when you go to /
		#RedirectMatch ^/$ /apache2-default/
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

When I make the changes to /var/www/mwiki1.7.1 I get:

Not Found
The requested URL /mwiki1.7.1/index.php/Main_Page was not found on this server.

-----------------------------------------------------------------
Apache/2.0.55 (Ubuntu) PHP/5.1.2 Server at 10.0.3.107 Port 80

So is there any diff. between /etc/apache2/sites-available and /etc/apache2/sites-enabled. I see that any changes I make in sites-enabled reflects in sites-available. So why having these two files if they "look" they same?

Thanks Lvanderree...

---

### Post by lvanderree on 2006-08-15
You have correctly noticed that 
/etc/apache2/sites-available/default is the same as /etc/apache2/sites-enabled/000-default

when you go to the directory etc/apache2/sites-enabled and run 
```
ls -l
```
(with the l from Leon ;-) )
you can see that 000-default is a link to the default file located at sites-available/default (it's a little like a shortcut in windows)
(the application a2ensite ca do this for you).

Now that you have changed the DocumentRoot correctly to /var/www/mwiki1.7.1 apache is going directly to your wiki when your browser goes to the address of your server (still asuming: 10.0.3.107 )

So I guess you went to 
[http://10.0.3.107](http://10.0.3.107)
and then the error:
The requested URL /mwiki1.7.1/index.php/Main_Page was not found on this server.
Shows up

This means that apache has loaded index.php, but this file has a assignment to redirect your browser to /mywiki1.7.1/index.php/Main_Page

this can brake because of two things:
**1.** [http://10.0.3.107/mwiki1.7.1/](http://10.0.3.107/mwiki1.7.1/) does not exists. This is the case if your current DocumentRoot now is /var/www/mwiki1.7.1 
I expected the error to be: The requested URL /index.php/Main_Page was not found on this server, without the mywiki1.7.1 part.

So please tell me if you changed the documentroot to /var/www/mywiki1.7.1, restarted apache and went to [http://10.0.3.107](http://10.0.3.107) with your browser and saw: The requested URL /index.php/Main_Page was not found on this server, or The requested URL /mywiki1.7.1/index.php/Main_Page was not found on this server.

**2.** The other problem can be that index.php/Main_Page is not found. This actually is the case, because index.php isn't is a directory and as I said before, you need the mod-rewrite plugin for this to let it work.
So please take a look in the directory /etc/apache2/mods-enabled and look if there is a file rewrite.load
If not rewrites aren't enabled. You can enable these by entering the following line:
```
sudo a2enmod rewrite
```
or if this isn't working, by adding a link to it yourself with the following lines:
```

sudo ln -s /etc/apache2/mods-available/rewrite.load /etc/apache2/mods-enabled/rewrite.load

```
of course restart apache after this and lets try it again...

Otherwise we can also change this url-style, but first see if this works!Good luck.

(Ps. It's rainy here in Holland ;-))

---

### Post by cocotu on 2006-08-15
Thanks Lvanderree, these are the results:

1. I went to /etc/apache2/mods-enabled and there is a file rewrite.load.
2. I made the changes in /var/www/mwiki1.7.1 and I got:

Not Found
The requested URL /mwiki1.7.1/index.php/Main_Page was not found on this server.
-----------------------------------------------------------------

Apache/2.0.55 (Ubuntu) PHP/5.1.2 Server at 10.0.3.107 Port 80

No luck! Here in New York is also raining, Holland must be a great place to live, and I have noticed a lot of people from Holland in the forums. So what should we do next Lvanderree? Thanks..

---

### Post by lvanderree on 2006-08-15
OK, I think the problem has to be in mediaWiki then.
The problem I see is that you get a message about "/mwiki1.7.1/index.php/Main_Page", which in my opinion should be "/index.php/Main_Page" (without the mywiki part) and then your problem should be dissapeared.

So what I have done is downloaded mediaWiki1.7.1 myself and installed it. Follow me:

(I already have 1.6.5 running, but that was some time ago)

1. in the console type
```

sudo su

cd /var/www
wget http://surfnet.dl.sourceforge.net/sourceforge/wikipedia/mediawiki-1.7.1.tar.gz
tar -xvzf mediawiki-1.7.1.tar.gz
mv mediawiki-1.7.1 mwiki1.7.1 [COLOR="Red"](pay attention to first remove your old mwiki1.7.1 directory if you do this)[/COLOR]
cd mwiki1.7.1/
chmod a+w config

exit

```

When you now use your browser to go to your server (10.0.3.107) you should see the mediawiki setup.

Please tell me this works... Otherwise I think there is something wrong with your apache setup, but I'm afraid I can't tell you where. Of course we can again try to solve this, but I think we then have to reinstall apache2 from ubuntu-archive so I know your apache2 config is clean.

---

### Post by cocotu on 2006-08-15
I think there should be no problem with the apache2 installation. I installed the LAMP server in which everything comes ready to use. I think also a MediaWiki thing. The problem is that right now others are playing around with this installation here at work so I need to ask them if they want to leave the current path or just type the IP address (which I think is the best idea). Another issue is the HD space. I installed this LAMP together with Win (bual-boot) and for the LAMP partition there is only around 5GB. Having said this I might have to re-install the LAMP again in order to take the whole HD for linux. I'm not sure if I can resize the HD and take over the Win98 partition for linux. Thanks for your help, I will try to re-install Wiki again and see what happens. I saw that some changes where made to the Wiki page here, do you know if there is a way to make a backup of these changes and put them in the new installation?

Thanks a lot...

---

### Post by cocotu on 2006-08-16
Hey Lvanderree, the guys decided to keep what they have, so now I don't think I will be able to re-install everything again because they made a lot of changes already. I was reading the doc for Wiki and I'm trying a few things to see what happens, I will be here for 3 more hours if you have any suggestions I will be happy to "read" them.

Thanks for your help..

---

### Post by lvanderree on 2006-08-16
Sorry I am a little too late this time.

Still willing to help, but yesterday I wanted to wait till you knew what your colleagues have done.

I said that when you now browse to your server's IP, you can see the directory of your wiki, but you didn't say if the Wiki was working when you click on this directory in your browser.

If this works out OK or not, I know where to search for, because I didn't have this problem myself and because I can't see everything you see I have to imagine it all to see what goes wrong where.

I changed the DocumentRoot in my Apache default-config to my freshly unpacked(as I described the previous time) wiki-root directory and this worked out OK.

So if you have a (second) newly unpacked wiki installation and things still go wrong it has to be an Apache configuration, or a disabled apache/php-plugin.

Also when things work out OK when you browse to this <ip-address>/folder path, I assume this can be the case, but then it can also be a setting in the wiki config.

---

### Post by cocotu on 2006-08-17
Hi Lvan, there is a setting in the wiki config, but I still have not figured it out, I was playing with it yesterday and it took me to the /mwiki folder showing me all the contents of it. When I clicked on index.php I got, "Page not found". So what we decided to do is to place all the contents of the wiki folder into the /var/www (the root) and eliminite the mwiki folder. Now we just need to type the IP address and we are in the wiki page. I didn't want to do it this way, but they needed this thing as soon as possible. The file to configure in wiki is the "LocalSettings.php" and I was following these instructions: [http://meta.wikimedia.org/wiki/Rewrite_rules]("http://meta.wikimedia.org/wiki/Rewrite_rules"). Now the next task is to set the Server name so instead of typing the IP address we want to be able to type "intranet" or something else and go to the page, this task I think might be easier than the previous. Any suggestions? Thanks for your help Lvanderree!!

---

### Post by lvanderree on 2006-08-17
I can't think of anything why placing the wiki in /var/www/wiki isn't working and when placed in /var/www it is, when changing the DocumentRoot and the mediawiki is "freshly" unpacked.

But if this is a workable solutione, then I think it's OK to leave it this way.

To change the address from IP to a name, typing in the hostname of your server in your browser should do the trick. 

at your server type:
```

hostname -s

```
to see your short hostname. This should work when entered in your browser.

changing the hostname of your server is possible too.
see 
```
man hostname
``` for that


at your workstation you can also check with
```

ping <hostname>

```
to see if the correct IP can be found.

otherwise you can also set the hostname you desire in all workstations manually.
If you have Windows XP, there is the file "c:\WINDOWS\system32\drivers\etc\hosts" in which you can add the ip and the name of your server like
```

10.0.0.1	intranet

```

in linux this can be done the same in 
/etc/hosts

---

### Post by cocotu on 2006-08-18
Thanks Lvanderree, this is my /etc/hosts, could you let me know if its ok:

10.0.3.107	localhost.localdomain	localhost	gtwiki
#127.0.0.1	localhost ORIGINAL
127.0.1.1	UbuntuLinux

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

And this is my hostname: gtwiki

When I go to the browser and type gtwiki I get:

The page cannot be displayed 
There is a problem with the page you are trying to reach and it cannot be displayed. 

-----------------------------------------------------------------

Please try the following:

Click the Refresh button, or try again later.

Open the Web site home page, and then look for links to the information you want. 
If you believe you should be able to view this directory or page, please contact the Web site administrator by using the e-mail address or phone number listed on the Web site home page. 
10061 - Connection refused
Internet Security and Acceleration Server

-----------------------------------------------------------------

Technical Information (for support personnel)

Background:
The server you are attempting to access has refused the connection with the gateway. This usually results from trying to connect to a service that is inactive on the server.

ISA Server: goodtemps-web.exchange.goodwillny.org
Via: 

Time: 8/18/2006 1:47:25 PM GMT 

Thanks...

---

### Post by lvanderree on 2006-08-18
I don't think your hostfile is correct.

I think it should be like this:

```

10.0.3.107 UbuntuLinux 
10.0.3.107 gtwiki
#127.0.0.1 localhost ORIGINAL
127.0.0.1 localhost.localdomain localhost 

```

As far as I know localhost (in all its forms) should always point to 127.0.0.1
10.0.3.107 can have multiple instances (like above) and now UbuntuLinux and gtkwiki both are resolving to it ON YOUR SERVER ITSELF.

so when you are at the console of your server, and type
```

ping ubuntulinux

```
or 
```

ping GtkWIKI

```

you should see something like
```

leon@gtkwiki:~$ ping gtkwiki
PING gtkwiki (10.0.3.107) 56(84) bytes of data.
**64 bytes from gtkwiki (10.0.3.107): icmp_seq=1 ttl=64 time=0.130 ms**
etc...

```
press ctrl+c to stop this

when you see unknown host then your hosts file is not OK
when you an IP but don't see a reply time, and something like destination unreachable there is something else wrong, but I don't think that this will be the case.

now when your try to do the same (ping) on a workstation, you also should see a result with an IP and an response time.

If you don't see a IP in this case (unknown host) this is because the DNS at your location didn't or couldn't translate the name gtkwiki OR ubuntulinux (depending on which you are ping-ing) to an IP-address. Try both to see if one is working. The one who is working, should also work in your internet browser.

When you want to change this name, you have two options I think.
Change the hostname of your server. Or at EVERY workstation change the hosts file (see previous mail for location of it on windows) and add 
```

10.0.3.107 gtwiki

```
to it, (or an other name you like to use for it. You can even say it is [www.google.com](www.google.com) and on that workstation [www.google.com](www.google.com) will resolve in 10.0.3.107)

Good luck and if things go wrong again, tell me all you have done and all you have seen.

---

### Post by cocotu on 2006-08-18
This is how I change the hosts file:

127.0.0.1	localhost.localdomain	localhost
10.0.3.7	intranet
#127.0.0.1	localhost ORIGINAL

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

As you can see I just want to name it "intranet". I follow your instructions and I added "10.0.3.107 intranet" to one of the computers here (they all use WinXP) and it worked just fine, from that machine I can type intranet and it takes me to the default page. But Lvanderree, is there another way of doing this? If not I will have to sit down at 30 different computers in order to add this IP.

Thanks for your help, you are the best!

---

### Post by lvanderree on 2006-08-18
To let intranet be known on all other computers automaticly it is important that no other computer is called 'intranet' on the network. 

So first go to one of your workstations with an unedited hosts file and look what ping tells you:
```

goto Start\Run
enter 'cmd' and press OK
in the console type:
**ping intranet**<enter>

```
now look at the output.

can the hostname intranet be resolved? and if so to which IP or full-hostname? Tell me the output if you don't understand it.

If not, it is safe to use the name 'intranet' for this server on your network. You should be able to change the hostname of your server with the hostname command.

I think it should be as easy as something like
```

sudo hostname intranet

```
on your server

but after this please check the content of /etc/hostname
to see if it's changed accordingly, otherwise change this manually as well, and you should be set.
Otherwise also try to reboot the server, to see if it is changed.

if it is changed, again go to a workstation and try to ping intranet.

---

### Post by cocotu on 2006-08-18
Ok, these are the results:

1. I went to a PC with unedited hosts file and I "ping intranet" and got: "Ping request could not find host intranet. Please check the name and try again." (Which means the hostname was not resolved)

2. When I did "sudo hostname intranet" I got:
   sudo: unable to lookup UbuntuLinux via gethostbyname()

3. I changed the hostname at etc/hostname to intranet, but when I type at the terminal the command hostname I get UbuntuLinux. This is crazy! and when I type cat hostname I get: intranet. To restart the server the command is: shutdown -r now?

I did these steps and I'm able to ping intranet, but when I go to the browser I get:


The page cannot be displayed 
There is a problem with the page you are trying to reach and it cannot be displayed. 

-----------------------------------------------------------------

Please try the following:

Click the Refresh button, or try again later.

Open the Web site home page, and then look for links to the information you want. 
If you believe you should be able to view this directory or page, please contact the Web site administrator by using the e-mail address or phone number listed on the Web site home page. 
10061 - Connection refused
Internet Security and Acceleration Server

-----------------------------------------------------------------

Technical Information (for support personnel)

Background:
The server you are attempting to access has refused the connection with the gateway. This usually results from trying to connect to a service that is inactive on the server.

ISA Server: goodtemps-web.exchange.goodwillny.org
Via: 

Time: 8/18/2006 7:19:39 PM GMT

---

### Post by lvanderree on 2006-08-18
so when you look at the console of your server (after the reboot), you see:

username@**intranet**:~$

and when you type:
```
hostname -s
```
you also see **intranet** I hope.

So you succesfully changed the hostname.

the error at 2. is probably because UbuntuLinux wasn't in your /etc/hosts anymore.


And the problem now is that when you go to a workstation, and use a browser, you can't go to [http://intranet](http://intranet), while you can ping intranet on this same workstation from its command prompt (cmd)?

That is really strange...

at the workstation, what is the ip which now is resolved when you type ping? is it the ip of your server? if so then try to restart your browser, or restart your entire workstation. Or install firefox or opera and look if this has the same problem.

---

### Post by cocotu on 2006-08-18
Amazing! I'm my workstation using firefox it work fine when I type "intranet" in IE does NOT. From my machine I'm able to ping intranet and get the correct IP, but that's because I already made the change to the host file in Windows. From other machines that I haven't change the host file I'm not able to ping intranet and I get "ping request could not find host intranet". 
So you think is a browser problem with IE? (Yes, at my console I have user@intranet)

Thanks

---

### Post by lvanderree on 2006-08-18
I can't tell why IE isn't working correctly.

But the problem at the other computers is because they can't resolve intranet to your servers ip address. That has nothing to do with the browser. It's probably because the name server at your location didn't "adopt" your servers name with its ip address. Or your workstations can't find intranet as a hostname on the network.

This partly has to do with your network setup.

I think you has to ask in a new post how this can be solved, because this I cannot tell you.

---

### Post by cocotu on 2006-08-18
Thanks Lvanderree you have done enough!! You must be tired of reading my questions. Thanks a lot!! For now I will use the first method you told me.

Thanks again, if you come to New York one day I will be glad to help you.

---

