---
title: "Want a Nagios 2.5 on a 6.06 OS How To?"
date: 2006-07-26
forum: Server Platforms
---

### Post by cavern on 2006-07-26
***Updated for Ubuntu 6.10 and Nagios 2.6***

**Introduction:**
I’m assuming you have a base Ubuntu 6.10 with GUI interface for this how to.  I wrote this guide from a fresh install of Ubuntu 6.10, but you can follow this if you have an already operational OS install with some basic editing.

** System Requirements:**
Apache2
GD Library
Nagios *(currently 2.6 as of 12/28/06)*
Nagios Plugins *(currently 1.4.5 as of 12/28/06)*
Basic Compilers

** Access Requirements:**
Root Password
[B]
Special Commands:[/B]
Sudo *(run root commands)*
Sudo –s *(root login)*

** Preinstall)**
Open a terminal window by selecting Applications, Accessories, and Terminal.  Type ‘sudo –s’ and the root password.

** Step 1) Install Basic Compilers**
Type ‘sudo apt-get install build-essential’.

** Step 2) Install GD Libraries**
Type ‘sudo apt-get install libgd2-dev’.

** Step 3) Install Apache2**
Type ‘sudo apt-get install apache2’.
[B]
Step 4) Download Nagios 2.6[/B]
This can be acquired at [http://www.nagios.org](http://www.nagios.org) and download the newest tarball *(at time of writing is 2.6 on 12/28/2006)* to the desktop.

** Step 5) Download Nagios 1.4.5 Plug-ins**
Also available at [http://www.nagios.org](http://www.nagios.org) and download the newest tarball of the Nagios Plugins to the desktop.

** Step 6) Nagios Install**
* Within the terminal window type the following commands:*
cd ~/Desktop
tar xzf nagios-2.6.tar.gz
cd nagios-2.6
adduser nagios *(this is default, change for your usage if needed)*[INDENT]fill in information as needed *(password, user information)*[/INDENT]mkdir /etc/nagios *(change for your usage if needed, take note of change this will be the install url)*
chown nagios.nagios /etc/nagios
grep “^User” /etc/apache2/httpd.conf
/usr/sbin/groupadd nagcmd *(default, change for your usage, take note of change)*[INDENT]Adds a group named nagcmd to Ubuntu for allowing external commands from the Web UI.[/INDENT]/usr/sbin/usermod –G nagcmd www-data *(user for apache)*
/usr/sbin/usermod –G nagcmd nagios *(user for nagios)*[INDENT]Adds the apache username and nagios into the nagcmd group.[/INDENT]./configure --prefix=prefix --with-cgiurl=cgiurl --with-htmurl=htmurl --with-nagios-user=someuser --with-nagios-group=somegroup --with-command-group=cmdgroup[INDENT]Replace prefix with /etc/nagios *(unless urlschanged)*
Replace cgiurl with /nagios/cgi-bin
Replace htmurl with /nagios *(default)*
Replace someuser with nagios *(unless otherwise changed)*
Replace somegroup with nagios *(unless otherwise changed)*
Replace cmdgroup with nagcmd *(unless otherwise changed)*
Verify general options look accurate[/INDENT]make all
make install
make install-init *(creates /etc/init.d/nagios functionality)*
make install-commandmode *(creates permissions for folders)*
make install-config *(creates sample config files)*

** Step 7) Install Nagios Plugins**
* Within the terminal window type the following commands:*
cd ..
tar xzf nagios-plugins-1.4.5.tar.gz
cd nagios-plugins-1.4.5
./configure –prefix=prefix –with-cgiurl=someurl[INDENT] Replace prefix with /etc/nagios *(unless urls changed)*
Replace cgiurl with /nagios/cgi-bin
[/INDENT]make
make install
make install-root

** Step 8 ) Configure Apache**
* Within the terminal window type the following commands:*
sudo gedit /etc/apache2/httpd.conf[INDENT] Once file opens, paste in the following lines:
[/INDENT]ScriptAlias /nagios/cgi-bin /etc/nagios/sbin

<Directory "/etc/nagios/sbin">
    Options ExecCGI
    AllowOverride None
    Order allow,deny
    Allow from all
    AuthName "Nagios Access"
    AuthType Basic
    AuthUserFile /etc/nagios/etc/htpasswd.users
    Require valid-user
</Directory>

Alias /nagios /etc/nagios/share

<Directory "/etc/nagios/share">
    Options None
    AllowOverride None
    Order allow,deny
    Allow from all
    AuthName "Nagios Access"
    AuthType Basic
    AuthUserFile /etc/nagios/etc/htpasswd.users
    Require valid-user
</Directory>[INDENT] Change the folder urls with information used above if changed, save and close.
[/INDENT]/etc/init.d/apache2 restart
htpasswd –c /etc/nagios/etc/htpasswd.users nagiosadmin (if this does not work, use cd /etc/nagios/etc; htpasswd -c htpasswd.users nagiosadmin)[INDENT]     Replace nagiosadmin if required.
    Enter in a password which will be used for Web UI.
[/INDENT]** Step 9) Setup User Access in Nagios**
* Within the terminal window type the following commands:*
sudo nautilus[INDENT]navigate to /etc/nagios/etc/ *(unless urls changed)*
rename all files and remove –sample
open cgi.cfg
go to line 116, remove # and add your user as created for Web UI
go to line 128, remove # and add your user as created for Web UI
go to line 141, remove # and add your user as created for Web UI
go to line 154, remove # and add your user as created for Web UI
go to line 155, remove # and add your user as created for Web UI
go to line 168, remove # and add your user as created for Web UI
go to line 169, remove # and add your user as created for Web UI
close cgi.cfg
open localhost.cfg
go to line 98, change contact_name to your user as created for Web UI
go to line 106, change email to valid email for your notifications
go to line 125, change members list to include your user as created for Web UI
close localhost.cfg
close browser
[/INDENT]/etc/nagios/bin/nagios –v /etc/nagios/etc/nagios.cfg *(unless urls changed)*[INDENT]This should return clean at this point.
[/INDENT]/etc/init.d/nagios restart
* Close the terminal window.*

** Step 10) Verify Web UI Usability**
Open your web browser and enter the url: [http://localhost/nagios/](http://localhost/nagios/)
Verify that the status map page loads properly.
[B]
Step 11) Enjoy![/B]
This HOW TO will walk you through the basics of setting up Nagios with one user access to everything within Nagios.  Personally I would go back into the minimal.cfg and tear out the sections into separate files.  Look in the nagios.cfg file on line 46 for the breakout of file names it requires.

I’ve done the digging for the correct and fewest packages needed to get this running properly, if you have any comments, please post them!

** Credits)**
Nagios:
[http://www.nagios.org](http://www.nagios.org)

Nagios Documentation:
[http://nagios.sourceforge.net/docs/2_0/](http://nagios.sourceforge.net/docs/2_0/)

Ubuntu Guide:
[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

Onlamp:
[http://www.onlamp.com/pub/a/onlamp/2002/09/26/nagios.html?page=3](http://www.onlamp.com/pub/a/onlamp/2002/09/26/nagios.html?page=3)

Ubuntu OS:
[http://www.ubuntu.com/](http://www.ubuntu.com/)

Debian:
[http://www.debian.org/](http://www.debian.org/)

Gnome:
[http://www.gnome.org/](http://www.gnome.org/)

- Jon

---

### Post by jordilin on 2006-07-26
Well, installing nagios in ubuntu should be nearly the same as installing it in a Debian machine. So, take a look at:
[http://wiki.tryphon.org/How_to_install_Nagios_under_Debian](http://wiki.tryphon.org/How_to_install_Nagios_under_Debian) with some interesting links at the bottom. Specially,
[http://www.onlamp.com/pub/a/onlamp/2002/09/05/nagios.html](http://www.onlamp.com/pub/a/onlamp/2002/09/05/nagios.html)
Hope that helps :D

---

### Post by BakCompat on 2006-07-26
absolutely. I've been playing around with VMWware Server and some of the posted network appliances. There is a NMS VMapp that has Nagios in addition to *many* other quite useful apps in it.. But hey, i would prefer to run Nagios natively.. So absolutely, let's see your guide.

Jordilin, thanks for those links. If and when i get the time, i will certainly be looking into them. Currently, my duties have prevented me from messing much with our Nagios test server since we are going through so many tests and have all sorts of other company shenanigans happening in the background. Sadly, it is one more thing on my todo list. Sadly, that list is rather long..

But thanks for the post.

---

### Post by cavern on 2006-07-26
> **jordilin said:**
> Well, installing nagios in ubuntu should be nearly the same as installing it in a Debian machine. So, take a look at:
[http://wiki.tryphon.org/How_to_install_Nagios_under_Debian](http://wiki.tryphon.org/How_to_install_Nagios_under_Debian) with some interesting links at the bottom. Specially,
[http://www.onlamp.com/pub/a/onlamp/2002/09/05/nagios.html](http://www.onlamp.com/pub/a/onlamp/2002/09/05/nagios.html)
Hope that helps :D

I agree, it wasn't that hard since knowing its close to installing on Debain, and those have helped alot actually, specificly the onlamp one.  But I know for alot of people finding these can be tricky/navigating linux, I just thought if anyone was interested it would be just as easy to do a step by step guide.

> **BakCompat said:**
> absolutely. I've been playing around with VMWware Server and some of the posted network appliances. There is a NMS VMapp that has Nagios in addition to *many* other quite useful apps in it.. But hey, i would prefer to run Nagios natively.. So absolutely, let's see your guide.

Jordilin, thanks for those links. If and when i get the time, i will certainly be looking into them. Currently, my duties have prevented me from messing much with our Nagios test server since we are going through so many tests and have all sorts of other company shenanigans happening in the background. Sadly, it is one more thing on my todo list. Sadly, that list is rather long..

But thanks for the post.

Will do a little editing on my part and post it up shortly..

- Jon

---

### Post by juicybananahead on 2006-07-26
Yup, Jon, I've been thinking about tinkering with Nagios for a while now so a howto would certainly help to get it up and running.

Cheers,
// Dave

---

### Post by cavern on 2006-07-27
Updated, see first post.

---

### Post by etank on 2006-08-02
I can not seem to get Ubuntu to send mail from nagios. I have installed mailx. What am I missing? When I run ```
mail -s "test" user@email.com
```the server just sits there.

---

### Post by etank on 2006-08-04
Ok, I got it working. I installed ssmtp and mailx because we already have a mail server and I want it to relay messages for me. Once they were installed I had to configure ssmtp.conf with the mail server that I wanted to use and then add an alias for the nagios user in revaliases so that it would look like it was coming from the helpdesk email account.

---

### Post by chrisfay on 2006-08-05
Anyone know of a good howto regarding adding hosts, servers, services etc. to Nagios? I got this up and running on localhost a while back and would like to add monitoring for a couple other on/offsite terminals. I haven't looked to hard but if anyone has any references or ideas it would be nice.

---

### Post by wuhaa on 2006-08-06
Wow

This is nice man, vary nice :) 

I like that status map.

Thanks for the HOW-TO

---

### Post by etank on 2006-08-07
It is still in the works but [http://nagiosbook.org](http://nagiosbook.org) has some good info.

---

### Post by cavern on 2006-08-07
> **etank said:**
> Ok, I got it working. I installed ssmtp and mailx because we already have a mail server and I want it to relay messages for me. Once they were installed I had to configure ssmtp.conf with the mail server that I wanted to use and then add an alias for the nagios user in revaliases so that it would look like it was coming from the helpdesk email account.

Good to know, thanks for the information, I'm still writing a process for a simple mail setup.

> **chrisfay said:**
> Anyone know of a good howto regarding adding hosts, servers, services etc. to Nagios? I got this up and running on localhost a while back and would like to add monitoring for a couple other on/offsite terminals. I haven't looked to hard but if anyone has any references or ideas it would be nice.

All the ones I've tried with Mysql/php5/apache2 installed always fail, I've gone ahead and figured out most of the toggles and such, if you like I can send you some of my configs as samples to pull from, besides the ones built into nagios of course.

> **wuhaa said:**
> Wow

This is nice man, vary nice :) 

I like that status map.

Thanks for the HOW-TO

No problem, I hope to get more HOW-TO's rolling of some other projects I'm working on.

> **etank said:**
> It is still in the works but [http://nagiosbook.org](http://nagiosbook.org) has some good info.

Great link, I've got it bookmarked and will be reading through it.

- Jon

---

### Post by chrisfay on 2006-08-07
> All the ones I've tried with Mysql/php5/apache2 installed always fail, I've gone ahead and figured out most of the toggles and such, if you like I can send you some of my configs as samples to pull from, besides the ones built into nagios of course.

That would be great...It would help to have some sample configs for things other than the generic single file. I want to setup more services on different machines and would like to seperate out all the files.

---

### Post by cavern on 2006-08-08
> **chrisfay said:**
> That would be great...It would help to have some sample configs for things other than the generic single file. I want to setup more services on different machines and would like to seperate out all the files.

Sure, send me a PM with an email address and I'll get some files over to ya (or, more so a link since I don't send files over email :p)

- Jon

---

### Post by AdrianOC on 2006-08-09
First off thank you for the guide.

Ive very green here but I thought you might like some feedback.

I found the whole guide to be very well laid out. It would help tremendously though if perhaps between steps you could add in little commands that we could type (Or screenshots)to test if what we have done so far is correct. This of course mightn't be possible at all, I don't know to be honest but I certainly think it would help.

Currently im on my third install because I made mess of the first two and I had no idea where things went astray so I thought a reinstall was best. I was also using Kubuntu which although similar is still very different.

Another idea might be to show what the commands do what we should be seeing when we enter stuff like "grep “^User” /etc/apache2/httpd.conf" 

or if you could show what we should be typing not the generic command one. Like this "./configure --prefix=prefix --with-cgiurl=cgiurl --with-htmurl=htmurl --with-nagios-user=someuser --with-nagios-group=somegroup --with-command-group=cmdgroup"
But with the actual stuff inserted (On my first two attempts I entered the above exactly as it written... untill I learned the error my ways ;)

Please dont take my suggestions as any form of criticism, I am VERY gratefull for your guide and all the work you put into it, without it I would still be lost in a world of ubuntu and nagios while now at least a have a road to follow :) They are simply some suggestions. GL

---

### Post by etank on 2006-08-09
The one thing that I do differently on my install is create a nagios.conf file to hold all of the apache directives. I put it in /usr/local/nagios/etc/ and then create a symbolic link for it in /etc/apache2/mods-enabled. That way if it keeps the httpd.conf file clean.

I also try to seperate my config files. I create different directories like ```
/usr/local/nagios/etc/routers
/usr/local/nagios/etc/servers
```and in them I place a single text file for each device that I want to monitor. That way if I add a new server I just copy the config for one of the others and change the name and IP.

---

### Post by cavern on 2006-08-09
> **AdrianOC said:**
> First off thank you for the guide.

Ive very green here but I thought you might like some feedback.

I found the whole guide to be very well laid out. It would help tremendously though if perhaps between steps you could add in little commands that we could type (Or screenshots)to test if what we have done so far is correct. This of course mightn't be possible at all, I don't know to be honest but I certainly think it would help.

Currently im on my third install because I made mess of the first two and I had no idea where things went astray so I thought a reinstall was best. I was also using Kubuntu which although similar is still very different.

Another idea might be to show what the commands do what we should be seeing when we enter stuff like "grep “^User” /etc/apache2/httpd.conf" 

or if you could show what we should be typing not the generic command one. Like this "./configure --prefix=prefix --with-cgiurl=cgiurl --with-htmurl=htmurl --with-nagios-user=someuser --with-nagios-group=somegroup --with-command-group=cmdgroup"
But with the actual stuff inserted (On my first two attempts I entered the above exactly as it written... untill I learned the error my ways ;)

Please dont take my suggestions as any form of criticism, I am VERY gratefull for your guide and all the work you put into it, without it I would still be lost in a world of ubuntu and nagios while now at least a have a road to follow :) They are simply some suggestions. GL

This won't be a problem at all, actually I'll try and get some screesn taken here in the next day or so.

And now that you asked about the examples (little comments) I actually had them written in but I thought they might be a little confusing, but I'll certainly add them.


> **etank said:**
> The one thing that I do differently on my install is create a nagios.conf file to hold all of the apache directives. I put it in /usr/local/nagios/etc/ and then create a symbolic link for it in /etc/apache2/mods-enabled. That way if it keeps the httpd.conf file clean.

I also try to seperate my config files. I create different directories like ```
/usr/local/nagios/etc/routers
/usr/local/nagios/etc/servers
```and in them I place a single text file for each device that I want to monitor. That way if I add a new server I just copy the config for one of the others and change the name and IP.

I do like these ideas, I have already split the config files, but  I didn't think about the nagios.conf holding the apache directives, I'll have to try this with my setup.

- Jon

---

### Post by khilari on 2006-08-14
This was simply awesome

Last few time, it took me a whole day to configure nagios, this time was sooo much easier... thanks to this "how to"

Thank you

---

### Post by Bugrit on 2006-08-18
Hi all
I am new to Linux and Ubuntu, so please accept my apologies for obvious errors. I am starting to look at replacing some of my server apps with Linux equivalents. Nagios looks to provide a lot features I would like but my colleague has been having trouble getting it working. I thought I could try it myself and tied to use your instructions to get er up and working :-)

First hurdle...I came unstuck at the add user command.
It didn't work as typed (all the previous ones were typed in a terminal window and worked fine. So I trolled thru the menus and found the Add users and groups app. Seemed to go okay.
Then I looked at the next command "mkdir /nagios".
Even if I assume that you needed to "sudo" all of these commands, it would still be creating me a directory in where ever I happened to be, is that ok?
In this case it would be /media/sda7/downloads/nagios-2.5/  
I thought that sounded wrong, so I created a new directory at the root "/" called it /nagios. 
The next few commands went ok, but when I got to./configure, it all blew up again. 
my command was :

sudo ./configure --prefix=/nagios --with-cgiurl=/nagios/cgi-bin --with-htmurl=/nagios/ --with-nagios-user=nagios --with-nagios-group=nagios --with-command-group=nagcmd

and the answer was:

bash: ./configure: No such file or directory

Sounds like it doesnt understand the ./configure command?
I have seen my colleague use it a few times, but I have not yet been educated as to its usage. So far (2 weeks) everything is apt-get installed without any other commands, or package updated automatically.
I will or course wander off and surf for the problem, but you get my drift.
A little more explanation of where you should be doing stuff, or the full path names required would be handy for "noobs" like me ;-)

Thanks for listening

Buggy

---

### Post by Bugrit on 2006-08-18
ok, so I'm a divot.
The ./configure command should run in the current directory.
I was in root, and the untar'd files are in /media/sda7/downloads/nagios-2.5/
Any chance of a visual guide to the proposed directory layout?
I would like to install the nagios application under /nagios if possible.
BTW What does the "sudo -s" command do?
:-)
Sorry for being a pain.
It will only get better I promise!

Buggy

---

### Post by briseida on 2006-09-07
how i can install nagat................

---

### Post by cavern on 2006-09-07
I apologize, been out of the office for some time, will be working on these additions shortly..


And working to see about getting Nagat installed.

- Jon

---

### Post by jjasghar on 2006-09-08
i'm with wuhaa here, thank you soo much, hell this is going to be so vital for me soon that i even subscribed to it so i can keep an eye on it!

---

### Post by chrisfay on 2006-09-08
Does anyone have experience monitoring remote Windows/Unix terminals using Nagios? I have configured all the services I want monitored locally and everything works great. I even added the SMTP,IMAP,POP3 and mailQ monitoring features as well.

My question is how to monitor local services like CPU load and harddrive space on pc's remotely. I know you can't just add those terminals the same way since that info is protected. So has anyone configured SNMP to transfer requests to the nagios server? Or possibly some of the Nagios plugins like NSCA? 

I would like to have all my pc's on my network reporting to Nagios but as of now I can only ping them. 

Any info would be great...

---

### Post by chrisfay on 2006-09-08
..duplicate

---

### Post by etank on 2006-09-08
I use NSClient [http://www.nagiosexchange.org/Windows.49.0.html?&tx_netnagext_pi1[p_view]=65&tx_netnagext_pi1[page]=10%3A10 ](http://www.nagiosexchange.org/Windows.49.0.html?&tx_netnagext_pi1[p_view]=65&tx_netnagext_pi1[page]=10%3A10 )and it works great. You have to install it on all of the windows machines and it should monitor the stuff that you are wanting once you set the check commands correctly on the nagios server. It runs as a service too. [http://nagiosexchange.org](http://nagiosexchange.org) has a lot of cool stuff like this. If you use nagios you need to check it out. Also look at [http://nagiosbook.org](http://nagiosbook.org).

I hope that it helps.

---

### Post by chrisfay on 2006-09-08
> I use NSClient [http://www.nagiosexchange.org/Window...;page]=10%3A10and](http://www.nagiosexchange.org/Window...;page]=10%3A10and) it works great.

Thanks, that looks like what I need. I did some quick googling and didn't find much info on configuring NSClient with Nagios. Any ideas on a good resource for setting this up or is it fairly straight forward? Do I need to install any Nagios pluggins to receive the info sent from NSClient?

---

### Post by chrisfay on 2006-09-08
Nevermind...Looks like NSClient has good documentation in the README. Thanks again...

---

### Post by chrisfay on 2006-09-09
If anyone is interested, these are unedited config files from my Nagios setup. I was having some confusion on seperating out the files so thought this might help someone else with the same problem.....

(obviously edit them to fit your needs)

[http://cjfay.com/nag_files/nagios.cfg](http://cjfay.com/nag_files/nagios.cfg)
[http://cjfay.com/nag_files/hosts.cfg](http://cjfay.com/nag_files/hosts.cfg)
[http://cjfay.com/nag_files/hostgroups.cfg](http://cjfay.com/nag_files/hostgroups.cfg)
[http://cjfay.com/nag_files/services.cfg](http://cjfay.com/nag_files/services.cfg)
[http://cjfay.com/nag_files/checkcommands.cfg](http://cjfay.com/nag_files/checkcommands.cfg)
[http://cjfay.com/nag_files/contacts.cfg](http://cjfay.com/nag_files/contacts.cfg)
[http://cjfay.com/nag_files/contactgroups.cfg](http://cjfay.com/nag_files/contactgroups.cfg)

---

### Post by OHardBodyO on 2006-09-09
I got the following message "usermod: unknown group nagcmd" when I ran the following command "/usr/sbin/usermod -G nagcmd www-data" what did I do wrong?

Thanks for the guide.

---

### Post by cavern on 2006-09-11
> **OHardBodyO said:**
> I got the following message "usermod: unknown group nagcmd" when I ran the following command "/usr/sbin/usermod -G nagcmd www-data" what did I do wrong?

Thanks for the guide.

Verify step 6, line:

/usr/sbin/groupadd nagcmd (default, change for your usage, take note of change)

that will create the nagcmd group, which then you can run usermod -g nagcmd www-data.

- Jon

---

### Post by bsalt on 2006-11-01
> **cavern said:**
> Good to know, thanks for the information, I'm still writing a process for a simple mail setup.



All the ones I've tried with Mysql/php5/apache2 installed always fail, I've gone ahead and figured out most of the toggles and such, if you like I can send you some of my configs as samples to pull from, besides the ones built into nagios of course.


- Jon

Hey Jon, could I request a copy of your config's as well? I am reading all the docs on how to do this, but I am just completely lost. I am looking to set up Nagios for a business that will monitor some 300 client computers, and I'll need any help possible ;P. 

Thanks for an EXCELLENT install guide. I just wish everyone else could make one that didn't have errors result in it.

-Jonathan

---

### Post by OHardBodyO on 2006-11-02
Jon, I had to start over again and start clean.  You never mentioned what should be the output when you the this command? grep "^User" /etc/apache2/httpd.conf.  Also since we unpackage the nagios tar on the desktop, does that mean the nagios core files are on the desktop? does it need to be moved?  thanks for your help. 

Lecorps

---

### Post by bsalt on 2006-11-02
> **bsalt said:**
> Hey Jon, could I request a copy of your config's as well? I am reading all the docs on how to do this, but I am just completely lost. I am looking to set up Nagios for a business that will monitor some 300 client computers, and I'll need any help possible ;P. 

Thanks for an EXCELLENT install guide. I just wish everyone else could make one that didn't have errors result in it.

-Jonathan

Never mind, I saw an earlier thread with thier cfg's on it. Without those, I wouldn't have been able to do this. Thank you! 

I am also in the process of setting up NSCA to monitor Windows computers that are behind firewalls, so if you'd like, I could post what I did to get that up and running.

---

### Post by cavern on 2006-11-02
> **bsalt said:**
> Never mind, I saw an earlier thread with thier cfg's on it. Without those, I wouldn't have been able to do this. Thank you! 

I am also in the process of setting up NSCA to monitor Windows computers that are behind firewalls, so if you'd like, I could post what I did to get that up and running.

Sure!  I'd like to see what you have come up with.

I appologize for not checking this more often, my email notifications are not working, I'm adjusting them as I type this.


Lecorps,
It appears in a folder on your desktop, and should be named the same as the tar minus the extention.  There shouldn't be any output that I can recall, it just enteres it into the httpd.conf file, no return information is displayed.

Of course I'm basing this install on a fresh default copy of Ubuntu, if you edit the installations at all you can fill in the different folder names, etc.

- Jon

---

### Post by iwalmsley on 2006-11-10
I just used this HOWTO to install Nagious and wanted to say thank you.

This is why I love the internet.

Thanks again! I am up and running perfectly.

---

### Post by cavern on 2006-11-10
> **iwalmsley said:**
> I just used this HOWTO to install Nagious and wanted to say thank you.

This is why I love the internet.

Thanks again! I am up and running perfectly.

Good deal! :-D

---

### Post by hypnoticspectar on 2006-11-20
Hi, 
This is a great how to! I am running into a problem though. When I try to install the plugins I run into this issue. 

./configure -prefix=/usr/local/nagios -with-nagios-user=nagios -with-nagios-group=nagios -with-cgiurl=/nagios/cgi-bin

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
configure: error: --with-nagios-user is a deprecated option

does anyone have any ideas for me?

---

### Post by cavern on 2006-11-20
I'll see if I can recreate the error, is it a fresh nagios/ubuntu setup have you been using this install for awhile?

---

### Post by hypnoticspectar on 2006-11-21
Hello, 

This is a fresh install. I downloaded everything last night (ubuntu and nagios). I wonder if this might have something to do with my version of complier? I am not able to access the machine right now, but if needed later on I can provide some system information. If there is something specific that you need please let me know. 

Thank you for your help in advance.

---

### Post by hypnoticspectar on 2006-11-28
I was able to get it to work by omitting the --with-nagios-user entry.

---

### Post by dregern on 2006-12-12
Hi,:D  im new in nagios here.
after following all the steps provided, on the first page,
till step 9, which is to open the minimal.cfg file, i coulnt find the file. and for ur information, im using nagios 2.6. Is nagios 2.6 doesnt have that file :confused: .Pls help, Ur a.s.a.p response is very appreciated.

Thanks

---

### Post by cavern on 2006-12-12
I appologize for the late response, my email notifications are not working properly still.

What .CFG files are listed within your nagios installation?

---

### Post by dregern on 2006-12-13
I have cgi.cfg, commands.cfg, resource.cfg, localhost.cfg, and nagios.cfg.

When i run the [Http://localhost/nagios/](Http://localhost/nagios/), i do get the front page, but i cant click the links. (e.g tactical overview, service detailed). It appears the login windows, and using the default authentication(username: nagiosadmin password:xxxxx) didnt works. Help again.!! :mrgreen:

---

### Post by hariste on 2006-12-28
Hi.. I'm new to Nagios..

Just finished install n configure it, what a hard way and took a lot of time.. :p

Need help with how to define service..

What do i need is how to configure the localhost.cfg to check PDC, dns, samba, web server, squid and microsoft sharing service..

If using ping we could use this
define service{
        use                             generic-service         ; Name of service template to use
        host_name                       newton, nobel, galileo, copernicus
        service_description             PING
	is_volatile			0
	check_period			24x7
	max_check_attempts		4
	normal_check_interval		5
	retry_check_interval		1
	notification_interval		960
	notification_period		24x7
	contact_groups			admins
	check_command			check_ping!100.0,20%!500.0,60%
        }

how bout the others..

thanx.

---

### Post by cavern on 2006-12-29
Hello All!  I've gone ahead and updated the first post with a new edition of this tutorial.  This now includes Ubuntu 6.10 and Nagios 2.6, with the new installation features, and a newer logical directory structure.

Changelog:
Removed nagios from root directory and placed in /etc/
Removed installation commands (user/group) from nagios plugins (no longer needed)
Updated configuration file names and line numbers.

Can a moderator update the title of this thread with "Want a Nagios 2.6 on a 6.06 OS How To?".





Hariste, I will come back and answer your question soon.

Happy new year all!

- Jon

---

### Post by OHardBodyO on 2007-01-07
Me again :-) hope you had a good new year.  I'm back again this time with an edgy but I'm stuck.  Can you help?  Please see below

mathelus@lecorps-desktop:~/Desktop/nagios-2.6$ /usr/sbin/usermod –G nagcmd www-data
usermod: no flags given
mathelus@lecorps-desktop:~/Desktop/nagios-2.6$ /usr/sbin/groupadd nagcmd
groupadd: group nagcmd exists
mathelus@lecorps-desktop:~/Desktop/nagios-2.6$ /usr/sbin/usermod –G nagcmd www-data
usermod: no flags given
mathelus@lecorps-desktop:~/Desktop/nagios-2.6$

---

### Post by OHardBodyO on 2007-01-07
nevermind! i figured it out.  I also had to allow all access to apache cuz nagiosadmin password wasn't working

---

### Post by cavern on 2007-01-08
Glad you got it working! :-D

---

### Post by OHardBodyO on 2007-01-08
Yeah, I did.  It wouldn't be possible without your how-to....YOU DA MAN!

Have you ever used Oreon? Now that I have nagios? how the hell do I add hosts? LOL

---

### Post by cavern on 2007-01-08
No problem, glad I could help.

I haven't used Oreon but I'm reading up on it.

I add hosts using the localhost.cfg, with my how to the sample files are created, take a peak in there and it describes how to add hosts.  Otherwise I can send you a temp config file I created to get you started.

---

### Post by OHardBodyO on 2007-01-08
I just finished installing oreon (2 hr work).  I recommend it for new nagios users.  Make it easier to add host, services, and users.  I followed the how-to located here [http://www.debianhelp.co.uk/oreon1.3.htm](http://www.debianhelp.co.uk/oreon1.3.htm)

---

### Post by wjgeorge on 2007-01-09
Great post! Got it up and running without too many probelms. I'm a Ubuntu/Linux nubie, but have nearly 30 years of Unix experience. I'll tell you right now, it doesn't help!

Anyway I found 2 small giltches in the install (on Ubuntu 6.06), mainly due to failures when I tried to "cut-and-paste".

> **cavern said:**
> 

./configure &#8211;prefix=prefix &#8211;with-cgiurl=someurl[INDENT] Replace prefix with /etc/nagios *(unless urls changed)*

[INDENT]**Shouldn't this be "--prefix" and "--with-cgiurl"**[/INDENT]


htpasswd &#8211;c /etc/nagios/etc/htpasswd.users nagiosadmin[INDENT] 

[INDENT]**Doesn't work, change to: (cd /etc/nagios/etc; htpasswd -c htpasswd.users nagiosadm)**[/INDENT]



Thanks again for the help in the install

Regards,

Bill George
Vonage

---

### Post by cavern on 2007-01-11
> **wjgeorge said:**
> Great post! Got it up and running without too many probelms. I'm a Ubuntu/Linux nubie, but have nearly 30 years of Unix experience. I'll tell you right now, it doesn't help!

Anyway I found 2 small giltches in the install (on Ubuntu 6.06), mainly due to failures when I tried to "cut-and-paste".



Thanks again for the help in the install

Regards,

Bill George
Vonage

Glad I could help!  I also just built a nagios fedora core box using the same installation tutorial :)  The -prefix command is actually different than the nagios 2.6 install.  The -prefix command was written for the nagios-plugins setup, while --prefix is for the nagios 2.6 install, I pulled that information directly from nagios.org, and verified it works properly.

As for the htpasswd -c, that line works fine on both my 6.06 and 6.10 versions of ubuntu?  I can add yours in there as an optional line, are you running server edition or desktop?

- Jon

---

### Post by OHardBodyO on 2007-01-14
> **cavern said:**
> Glad I could help!  I also just built a nagios fedora core box using the same installation tutorial :)  The -prefix command is actually different than the nagios 2.6 install.  The -prefix command was written for the nagios-plugins setup, while --prefix is for the nagios 2.6 install, I pulled that information directly from nagios.org, and verified it works properly.

As for the htpasswd -c, that line works fine on both my 6.06 and 6.10 versions of ubuntu?  I can add yours in there as an optional line, are you running server edition or desktop?

- Jon

Jon - you should modify the tutorial to reflect George's mods.  Once I did his way I was able to login without any problem using nagios admin.

Now that I have nagios monitoring my localhost....how the hell do i add another host and services?

---

### Post by cavern on 2007-01-14
> **OHardBodyO said:**
> Jon - you should modify the tutorial to reflect George's mods.  Once I did his way I was able to login without any problem using nagios admin.

Now that I have nagios monitoring my localhost....how the hell do i add another host and services?

I will try out his suggestions, I'm just not sure the difference between the two, my writeup works fine on my standard 6.06 and 6.10 installs.

I'll add it in as optional fields if others have issues?

OhardBodyO, you edit the localhost.cfg and create additional hosts and services for each host.  If it helps I can send you a sample file of my hosts and services files I've built.  Just let me know.

---

### Post by OHardBodyO on 2007-01-16
I made a change to nagios and now i'm unable to start nagios.  Here are the error messages im getting when i check the config

mathelus@lecorps-desktop:~$ /etc/nagios/bin/nagios –v /etc/nagios/etc/nagios.cfg 
Nagios 2.6
Copyright (c) 1999-2006 Ethan Galstad ([http://www.nagios.org](http://www.nagios.org))
Last Modified: 11-27-2006
License: GPL

Error: Cannot open main configuration file '/home/mathelus/–v' for reading!
Nagios 2.6 starting... (PID=8115)
Bailing out due to one or more errors encountered in the configuration files.  Run Nagios from the command line with the -v option to verify your config before restarting. (PID=8115)


Any help is appreciated.

---

### Post by OHardBodyO on 2007-01-17
I was able to resolve the problem by reinstall nagios as root and all was well.  I am currently monitoring 2 hosts :-) Thanks guys!

Jon - where you able to get oreon working?

---

### Post by cavern on 2007-01-18
HardBody, I haven't had time to try and install it yet.

For everyone who is asking, its hard to provide steps how to add hosts because each persons configuration will be different.  Some people use 1 file to list all hosts and services, I personally split the files into 3 files, localhost.cfg for administration purposes, hosts.cfg for hosts, and services.cfg for services.

I also go further and break them into folders /domain1/ and /domain2/ etc, (i have 2 nic cards configured differently).

Please visit: [click here](http://files.cavernprojects.com/nagios/) for sample config files.

If you plan on using these, PLEASE edit the localhost.cfg, host.cfg and services.cfg files.

---

### Post by dregern on 2007-01-25
Anyone know any simple configuration to let Nagios sent mail notification in Ubuntu.

Any respond is very appreciated..TQ~

---

### Post by rickyjones on 2007-01-25
Hey everyone,

I've got Nagios 2.6 running great - but it won't start up automatically when the monitoring server reboots. I have "nagios" in the /etc/init.d/ folder, and I can start/stop/restart it using that (sudo /etc/init.d/nagios start|stop|restart). Could it be a permissions problems, or do I need to update something else?

Any help would be appreciated.

Thanks!

-Richard

---

### Post by cavern on 2007-01-25
> **rickyjones said:**
> Hey everyone,

I've got Nagios 2.6 running great - but it won't start up automatically when the monitoring server reboots. I have "nagios" in the /etc/init.d/ folder, and I can start/stop/restart it using that (sudo /etc/init.d/nagios start|stop|restart). Could it be a permissions problems, or do I need to update something else?

Any help would be appreciated.

Thanks!

-Richard

I would look at:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Boot-Up_Manager_.28BUM.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Boot-Up_Manager_.28BUM.29)

By default, it is not included in the bootup services, you manually have to add it as a service.

---

### Post by rickyjones on 2007-01-25
> **cavern said:**
> I would look at:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Boot-Up_Manager_.28BUM.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Boot-Up_Manager_.28BUM.29)

By default, it is not included in the bootup services, you manually have to add it as a service.

Would install a new bootup manager fix this? Also - this is a server install, so no GUI. Do you need a GUI to configure this?

I also have webmin installed - would I be able to configure this behavior from webmin?

Thanks!

-Richard

---

### Post by rickyjones on 2007-01-25
Update - apparently I can change this behavior w/ Webmin. I'll know if it works the next time the office loses power.

:)
EDIT:

I changed the behavior, but Webmin still says that it is NOT set to boot at startup? Any ideas?

Thanks guys!

-Richard

---

### Post by cavern on 2007-01-25
> **rickyjones said:**
> Update - apparently I can change this behavior w/ Webmin. I'll know if it works the next time the office loses power.

:)
EDIT:

I changed the behavior, but Webmin still says that it is NOT set to boot at startup? Any ideas?

Thanks guys!

-Richard

Ah see you didn't mention it was a server install, not GUI based :)

[http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html](http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html)

That link should provide you with all the information on how to add programs to run on startup, based on their run level.

- Jon

---

### Post by Koybe on 2007-02-15
Hello,

I just compile nagios 2.7 on ubuntu 6.06 LTS server. Everything was fine until i try to get to the web interface. Here's what I get :
[[IMG]http://img113.imageshack.us/img113/9119/clipboard1pu1.th.png[/IMG]]("http://img113.imageshack.us/my.php?image=clipboard1pu1.png")

Thank you for any help.

EDIT : Figure it out myself. I confired apache2 with Alias instead of ScriptAlias for the cgi directory.
Tanx anyway! ;-)

---

### Post by cavern on 2007-02-15
I have yet to use 2.7, I will install it shortly and see..

---

### Post by JonRohan on 2007-02-19
Thanks for this. I've managed to get Nagios 2.7 up and running (from what I can see). :)

---

### Post by cavern on 2007-02-19
> **JonRohan said:**
> Thanks for this. I've managed to get Nagios 2.7 up and running (from what I can see). :)

\\:D/ My pleasure!.

---

### Post by JonRohan on 2007-02-21
Has anyone got a good howto or resource on how to setup email alerts with Nagios?

---

### Post by cavern on 2007-02-21
> **JonRohan said:**
> Has anyone got a good howto or resource on how to setup email alerts with Nagios?

As in setting up an MTA (Postfix) within Ubuntu so the emails will be sent out?

---

### Post by JonRohan on 2007-02-21
I have setup Postfix and sent a test email sucessfully. Do I have to tell Nagios to use postfix or will it just try and use the detault MTA for the system? 

I'm a bit of a linux noob. :(. 

Hopefully this nagios system I'm trying to setup will monitor over 200 nodes on our network :).

---

### Post by cavern on 2007-02-21
> **JonRohan said:**
> I have setup Postfix and sent a test email sucessfully. Do I have to tell Nagios to use postfix or will it just try and use the detault MTA for the system? 

I'm a bit of a linux noob. :(. 

Hopefully this nagios system I'm trying to setup will monitor over 200 nodes on our network :).

Do you know how to send an email out through the terminal?  If you can do that modifying the email script is very easy.

---

### Post by JonRohan on 2007-02-24
> **cavern said:**
> Do you know how to send an email out through the terminal?  If you can do that modifying the email script is very easy.

I have successfully sent an email to myself via the terminal. I'll take a look at the nagios documentation and see if I can get nagios to email me :). 

Thanks for your help. 

Regards, 

Jon

---

### Post by ScottTFrazer on 2007-02-26
If you are using a server install of Ubuntu, these instructions still seem to work, but your "check_http" plugin will not be able to use SSL connections and cannot tell you useful things like how soon your cert will expire.  

To get SSL support, add or change the following steps:


[I]**Step 3a) Install libssl-dev**
type `sudo apt-get install libssl-dev`[/I]
...

** Step 7) Install Nagios Plugins**
Within the terminal window type the following commands:
cd ..
tar xzf nagios-plugins-1.4.5.tar.gz
cd nagios-plugins-1.4.5
./configure &#8211;prefix=prefix &#8211;with-cgiurl=someurl ***--with-openssl=/usr/include/openssl*** 

[INDENT] Replace prefix with /etc/nagios *(unless urls changed)*
Replace cgiurl with /nagios/cgi-bin
*Check the status and look for "--with-openssl: yes"*
[/INDENT]

---

### Post by chrisfay on 2007-03-03
How do I change the notification timing for a host that goes down and comes back up within seconds?

I am monitoring a server and the ping will fail, send out a critical notification, then come back up in under a few seconds, and send out a recovery email. 

I've looked into the <notification_interval> option, but from what I understand, that only deals with the time delay between two seperate critical or unreachable events; not the time between down and up staus.

I'm not sure that this happens enough to be considered 'flapping', but I get maybe two or three down/up notifications per day from this service/host. Has anyone configured flapping successfully and is this what I'm looking for? I would like Nagios to only send out notifications if the time between the initial critical warning and the recovery warning is larger than a specified ammount.  I'm basically getting a bunch of false positives...

**EDIT:**

I may have found the solution to this actually, tell me if this makes sense. I changed the <max_check_attempts> from 10 to 20 and increased the <retry_check_interval> from 1 to 10. I'm assuming this means that instead of going from soft to HARD status (and generating a notification) after 10 failed attempts, this will space it out to 20 attempts and increase the timing between each of those checks from 1 to 10.

EDIT2:

...changing the <retry_check_interval> from 1 to 3 allowed enough time for the host to come back up without generating a notification.

---

### Post by chrisfay on 2007-03-04
Ok, apparently my problem is not from the PING 'service' check, but rather the host-check-alive command ran on the host 'after' a service SOFT fails. When a service fails for the first time (SOFT), nagios runs the check-host-alive command for that host to make sure it's even alive. My problem is that the host is considered down after 10 attempts, all of which are run within a milisecond of each other. So this means that if there's no response from the host within roughly 10 miliseconds, I get a critical notification; even if the host is really up, but couldn't respond in time. 

How do I set a <retry_check_interval> for a host, not a service? I've only seen directives for <check_interval> on a host, which is only used if active checks is enabled.....

 I've never used this before, but I think it's time: ](*,)

---

### Post by GoBieN on 2007-03-04
I run in to a problem when executing **make install **for the plugins:

>  ... 
make[1]: Leaving directory `/tmp/nagios-plugins-1.4.6/plugins-scripts'
Making install in plugins-root
make[1]: Entering directory `/tmp/nagios-plugins-1.4.6/plugins-root'
make[2]: Entering directory `/tmp/nagios-plugins-1.4.6/plugins-root'
 /usr/bin/install -c check_dhcp /etc/nagios/libexec/check_dhcp
 chown root /etc/nagios/libexec/check_dhcp
 chmod 4550 /etc/nagios/libexec/check_dhcp
 /usr/bin/install -c check_icmp /etc/nagios/libexec/check_icmp
 chown root /etc/nagios/libexec/check_icmp
 chmod 4550 /etc/nagios/libexec/check_icmp
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/tmp/nagios-plugins-1.4.6/plugins-root'
make[1]: Leaving directory `/tmp/nagios-plugins-1.4.6/plugins-root'
Making install in po
make[1]: Entering directory `/tmp/nagios-plugins-1.4.6/po'
/bin/sh @MKINSTALLDIRS@ /etc/nagios/share
/bin/sh: Can't open @MKINSTALLDIRS@
make[1]: *** [install-data-yes] Error 2
make[1]: Leaving directory `/tmp/nagios-plugins-1.4.6/po'
make: *** [install-recursive] Error 1
root@ARES:/tmp/nagios-plugins-1.4.6#


Any ideas ?

---

### Post by GoBieN on 2007-03-05
I tried the 1.4.5 plugins and they install fine, only 1.4.6 didnt go for me.

---

### Post by cavern on 2007-03-08
Sorry everyone, works been busy, I'll have more time this evening to go through the last 4-5 messages, but I haven't forgotten about anyone! :)

---

### Post by ScottTFrazer on 2007-03-16
> **GoBieN said:**
> I tried the 1.4.5 plugins and they install fine, only 1.4.6 didnt go for me.

The error generated from the 1.4.6 plugins install doesn't seem very critical.  all the plugins I've tried work fine.

---

### Post by GoBieN on 2007-03-20
> **ScottTFrazer said:**
> The error generated from the 1.4.6 plugins install doesn't seem very critical.  all the plugins I've tried work fine.

Since it stops the make install process with an error its not just fine i guess

---

### Post by teamchachi on 2007-03-22
Any updates on this issue?  I'm getting there error with 1.4.6 as well.

---

### Post by blakegrover on 2007-03-23
Same here the exact error mesasge I get is:

> make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/root/nagios-plugins-1.4.6/plugins-root'
make[1]: Leaving directory `/root/nagios-plugins-1.4.6/plugins-root'
Making install in po
make[1]: Entering directory `/root/nagios-plugins-1.4.6/po'
/bin/sh @MKINSTALLDIRS@ /etc/nagios/share
/bin/sh: @MKINSTALLDIRS@: No such file or directory
make[1]: *** [install-data-yes] Error 127
make[1]: Leaving directory `/root/nagios-plugins-1.4.6/po'
make: *** [install-recursive] Error 1


---

### Post by Wasca on 2007-03-29
Hi Guys

I found that after compiling the plugins that I was missing check_mysql and check_mysql_query. 

To fix this I needed to do an apt-get install libmysqlclient15-dev and then recompile the plugins as outlined in the first post of the thread.

Hope this helps some one.

---

### Post by acoustix on 2007-04-03
Thanks for the great instructions Jon.  I went through the steps yesterday and everything seemed to work well.  However, when I go to the nagios website I cannot login.  I've tried resetting the password on the nagiosadmin account, but that doesn't seem to help.  Does anyone have any ideas?

Thanks again!

Nick

---

### Post by saulecker on 2007-04-16
Hi there and thanks for the awesome HOWTO.  It has helped me immensly.

I am having a problem installing Nagios 2.9 on a machine running 6.06.  I follow all the instructions and I don't see any errors (I installed a second time looking very carfully, but that doesn't mean I didn't miss anything) but when I get to the point where I need to restart apache I get an error "grep: /etc/apache/conf.d/nagios: No such file or directory ...fail!"  I looked at /etc/apache/conf.d and "nagios" is a symlink pointing at /nagios/apache.conf.  Well, to my amazement there is no /nagios directory on the system.  I started the install from acratch again and paid very close attention to the out put from all configure and make commands and saw no errors.  Am I missing something?  is 2.9 really that different?

Thanks

---

### Post by saulecker on 2007-04-16
> **saulecker said:**
> Hi there and thanks for the awesome HOWTO.  It has helped me immensly.

I am having a problem installing Nagios 2.9 on a machine running 6.06. 
Thanks

Well after tinkering around I got it working, although I really don't know 100% what the problem was.  My fix for it was a complete manual removal of all things nagios on the machine.  I had un-tarred the source files to a temp directory at the root.  After removing everything nagios on the machine I moved everything to ~ and followed your directions to the letter.  It now works.  Thinking on it, I think the key thing I may have mised in my first 5 installs was changing owner/group on the /etc/nagios directory.  It helped undoing everything and starting over because that was one of a couple of steps that I thought "no need to do that because it's been done already".  With a true fresh install I had to re-do that step (or do it for the first time :D ) and now everything works.

so again, thanks again for the wonderful walk thru.  The steps worked fine on nagios 2.9 with the 1.4.8 plugins.

---

### Post by acoustix on 2007-04-18
I'm seeing some weird things happening here.  I've got Nagios configured to monitor 24 Windows servers and at first it was working great.  But it seems that every few days Nagios shows a server that is "down" but it's not down.  I'm up to 8 servers now that Nagios is reporting as "down".  It gives me this statement: "Usage:check_nt -H host -v variable [-p port] [-w warning] [-c critical][-l params] [-d SHOWALL] [-t timeout] "

I have all of my config files for the servers setup up exactly the same.  Here's a sample of my server config:
define host{
       use                     windows-server-critical
       host_name               mailnode1.xxxxxx.com
       alias                   Exchange Server - Mail Node 1
       address                 192.168.0.26
       check_command           check_nt_process
       check_command           check_nt_clientversion
       check_command           check_nt_uptime
       check_command           check_nt_memuse
       check_command           check_nt_disk
       check_command           check_nt_cpuload
       }

Any ideas?  I tried posting over at meulie.net, but that place is dead.

Nick

---

### Post by Horbert on 2007-04-27
Just wanted to say I followed the directions on a clean install of 7.04 and everything worked perfectly.
I am using nagios-2.9 and nagios-plugins-1.4.8.  Only thing I want to add is if you are installing nrpe make sure you grab the libssl-dev package. I know you did not have nrpe on the how to but I thought I would mention it for others. Thanks again!

---

### Post by uicsux on 2007-05-08
./configure --prefix=prefix --with-cgiurl=cgiurl --with-htmurl=htmurl --with-nagios-user=someuser --with-nagios-group=somegroup --with-command-group=cmdgroup

    Replace prefix with /etc/nagios (unless urlschanged)
    Replace cgiurl with /nagios/cgi-bin
    Replace htmurl with /nagios (default)
    Replace someuser with nagios (unless otherwise changed)
    Replace somegroup with nagios (unless otherwise changed)
    Replace cmdgroup with nagcmd (unless otherwise changed)
    Verify general options look accurate

im stuck here. i am still in root  /Desktop/nagios2.9  when i try to run this command, i get unrecognized options --/etc/nagios=/etc/nagios

any ideas? pardon my noobish questions

---

### Post by rgiskard01 on 2007-05-18
I'm running Nagios v3 on 6.06 Server, so far no problems. Already picked up some good pointers from this thread!  Very nice work.

I am currently setting up notifications, and just installed SSMTP via apt.

It setup the revaliases and ssmtp.conf files in /etc/ssmtp/

After configuring them as per nagiosbook, I tried to run the test mail commeand, but get a:
-bash: mail: command not found

Can some tell me what I'm missing and what I need to do to get nagios notifications working?

Thx!

(this box would be setup at a business setting, sending out alerts to specific email addresses)

---

### Post by rgiskard01 on 2007-05-19
I have now gotten sSMTP to work via command line on my home cable line, sending it the authentication credentials, and I receive an email.

The line I send is:

/usr/sbin/sendmail -s "test" root
blah blah
<ctrl-d>

And I receive an email; however, it is from root@<my domain> not the hostname of the machine like I expected,  and there is no subject or from address, and blah blah is in the body.  

However, I am not receiving any notifications from Nagios when I should.

I have edited the email commands in commands.cfg, so now the notify_host_by_email looks like:

/usr/bin/printf "%b" "***** Nagios *****\n\nNotification Type: $NOTIFICATIONTYPE$\nHost: $HOSTNAME$\nState: $HOSTSTATE$\nAddress: $HOSTADDRESS$\nInfo: $HOSTOUTPUT$\n\nDate/Time: $LONGDATETIME$\n" | /usr/sbin/sendmail -s "** $NOTIFICATIONTYPE$ Host Alert: $HOSTNAME$ is $HOSTSTATE$ **" $CONTACTEMAIL$

and notify_service_by_email:
/usr/bin/printf "%b" "***** Nagios *****\n\nNotification Type: $NOTIFICATIONTYPE$\n\nService: $SERVICEDESC$\nHost: $HOSTALIAS$\nAddress: $HOSTADDRESS$\nState: $SERVICESTATE$\n\nDate/Time: $LONGDATETIME$\n\nAdditional Info:\n\n$SERVICEOUTPUT$" | /usr/sbin/sendmail -s "** $NOTIFICATIONTYPE$ Service Alert: $HOSTALIAS$/$SERVICEDESC$ is $SERVICESTATE$ **" $CONTACTEMAIL$

Since I can send email via command line through my earthlink line, I presume Nagios should be able to as well.

I've check all the setting in Nagios again, and all appear correct, most are default from the samples.

---

### Post by rgiskard01 on 2007-05-20
:) 

OK - I have now got it working!

I had the change the commands in commands.cfg to the following:

notify_service_by_host:

/usr/bin/printf "%b" "***** Nagios *****\n\nNotification Type: $NOTIFICATIONTYPE$\nHost: $HOSTNAME$\nState: $HOSTSTATE$\nAddress: $HOSTADDRESS$\nInfo: $HOSTOUTPUT$\n\nDate/Time: $LONGDATETIME$\n" | [COLOR="Navy"]**echo Subject: **[/COLOR]"** $NOTIFICATIONTYPE$ Host Alert: $HOSTNAME$ is $HOSTSTATE$ **" **[COLOR="Navy"]| /usr/sbin/sendmail [/COLOR]**$CONTACTEMAIL$

and notify_service_by_email:

/usr/bin/printf "%b" "***** Nagios *****\n\nNotification Type: $NOTIFICATIONTYPE$\n\nService: $SERVICEDESC$\nHost: $HOSTALIAS$\nAddress: $HOSTADDRESS$\nState: $SERVICESTATE$\n\nDate/Time: $LONGDATETIME$\n\nAdditional Info:\n\n$SERVICEOUTPUT$" |**[COLOR="Navy"] echo Subject: [/COLOR]**"** $NOTIFICATIONTYPE$ Service Alert: $HOSTALIAS$/$SERVICEDESC$ is $SERVICESTATE$ **"**[COLOR="Navy"] | /usr/sbin/sendmail [/COLOR]**$CONTACTEMAIL$

So this is using Nagios 3, Ubuntu 6.06 (LAMP Server), and only sSMTP and is sending notifications to external emails. 

Only last question is if there are any issues or concerns using the echo command in this way....?

---

### Post by cavern on 2007-05-20
> **uicsux said:**
> ./configure --prefix=prefix --with-cgiurl=cgiurl --with-htmurl=htmurl --with-nagios-user=someuser --with-nagios-group=somegroup --with-command-group=cmdgroup

    Replace prefix with /etc/nagios (unless urlschanged)
    Replace cgiurl with /nagios/cgi-bin
    Replace htmurl with /nagios (default)
    Replace someuser with nagios (unless otherwise changed)
    Replace somegroup with nagios (unless otherwise changed)
    Replace cmdgroup with nagcmd (unless otherwise changed)
    Verify general options look accurate

im stuck here. i am still in root  /Desktop/nagios2.9  when i try to run this command, i get unrecognized options --/etc/nagios=/etc/nagios

any ideas? pardon my noobish questions

the example would be like:

./configure --prefix=/etc/nagios --with-cgiurl=/nagios/cgi-bin --with-htmurl=/nagios --with-nagios-user=nagios --with-nagios-group=nagcmd

---

### Post by cavern on 2007-05-20
> **rgiskard01 said:**
> :) 

OK - I have now got it working!

I had the change the commands in commands.cfg to the following:

notify_service_by_host:

/usr/bin/printf "%b" "***** Nagios *****\n\nNotification Type: $NOTIFICATIONTYPE$\nHost: $HOSTNAME$\nState: $HOSTSTATE$\nAddress: $HOSTADDRESS$\nInfo: $HOSTOUTPUT$\n\nDate/Time: $LONGDATETIME$\n" | [COLOR="Navy"]**echo Subject: **[/COLOR]"** $NOTIFICATIONTYPE$ Host Alert: $HOSTNAME$ is $HOSTSTATE$ **" **[COLOR="Navy"]| /usr/sbin/sendmail [/COLOR]**$CONTACTEMAIL$

and notify_service_by_email:

/usr/bin/printf "%b" "***** Nagios *****\n\nNotification Type: $NOTIFICATIONTYPE$\n\nService: $SERVICEDESC$\nHost: $HOSTALIAS$\nAddress: $HOSTADDRESS$\nState: $SERVICESTATE$\n\nDate/Time: $LONGDATETIME$\n\nAdditional Info:\n\n$SERVICEOUTPUT$" |**[COLOR="Navy"] echo Subject: [/COLOR]**"** $NOTIFICATIONTYPE$ Service Alert: $HOSTALIAS$/$SERVICEDESC$ is $SERVICESTATE$ **"**[COLOR="Navy"] | /usr/sbin/sendmail [/COLOR]**$CONTACTEMAIL$

So this is using Nagios 3, Ubuntu 6.06 (LAMP Server), and only sSMTP and is sending notifications to external emails. 

Only last question is if there are any issues or concerns using the echo command in this way....?

Not that I'm aware of, I actually had setup mine very similar to this at first.

When I get back into the office I'll hunt down my config files and pull what I was using :)

Sorry all for the absense, but I'm back now, and I have a fresh install of 7.04 installed, I'll be setting up my nagios here soon to verify everything.

---

### Post by joeyoung25 on 2007-06-14
I have a question for anyone. 
Im fairly new to configuring nagios. I have ubuntu 7.04 and nagios 2.9 I cant figure out how to configure nagios to send email to an address when a host is down. 
I have sendmail installed but not sure why nagios isnt using it to notify us but nagios is logging notifications we just arent receiving any emails.

---

### Post by bodhi.zazen on 2007-06-15
Nice How-to

This thread has been added to the UDSF wiki.

[Nagios](http://doc.gwos.org/index.php/Nagios)

---

### Post by cavern on 2007-06-18
> **bodhi.zazen said:**
> Nice How-to

This thread has been added to the UDSF wiki.

[Nagios](http://doc.gwos.org/index.php/Nagios)

THANKS! Thats awesome!  I'm honored, a few sites have linked to this thread now.  Anyway I can get the topic updated for Ubuntu 7.04 Nagios 2.9?  When I update the original post should I contact anyone for the title to be updated and the wiki to be updated or is there a way I can go in and update it?

> **joeyoung25 said:**
> I have a question for anyone. 
Im fairly new to configuring nagios. I have ubuntu 7.04 and nagios 2.9 I cant figure out how to configure nagios to send email to an address when a host is down. 
I have sendmail installed but not sure why nagios isnt using it to notify us but nagios is logging notifications we just arent receiving any emails.

My box is currently off but if I can recall, I use something similar to:

```
/usr/bin/mail -s "$HOSTNAME$ - $HOSTSTATE$ - Host Alert" $CONTACTEMAIL -- -f user@domain.com -F "Nagios Alerts"
```

Which is found in the commands.cfg using 'host-notify-by-email'.

---

### Post by bodhi.zazen on 2007-06-18
> **cavern said:**
> THANKS! Thats awesome!  I'm honored, a few sites have linked to this thread now.  Anyway I can get the topic updated for Ubuntu 7.04 Nagios 2.9?  When I update the original post should I contact anyone for the title to be updated and the wiki to be updated or is there a way I can go in and update it?

I tried to update the wiki page for 7.10 and 2.9.

Feel free to edit the page as you wish, that is what is awesome about wiki :)

Otherwise PM me on the Ubuntu Forums and I will modify the wiki as time allows.

---

### Post by cavern on 2007-06-18
> **bodhi.zazen said:**
> I tried to update the wiki page for 7.10 and 2.9.

Feel free to edit the page as you wish, that is what is awesome about wiki :)

Otherwise PM me on the Ubuntu Forums and I will modify the wiki as time allows.


Perfect! Thanks a bunch, got it bookmarked, I'm surprised how well this has taken off.

---

### Post by slimjim83 on 2007-07-25
First off, thank you for this amazing How-To; it turned what was looking like a two or three day project with a lot of reading into a few easy hours of work.  Now that the install is done, the real fun begins.

I would like to comment on one small thing.  My application is Ubuntu 6.10 (server) w/ Nagios 2.9 & Plugins 1.4.9.  When installing the libgd2-dev package, I got an error message saying that it was a virtual package and there were no installation candidates.  It looks to me like this package has been split into 2 seperate ones, one with xpm support and one without.  I used libgd2-xpm-dev and it seems to work okay, though I haven't had much time to test it.  I thought maybe the instructions could be updated to reflect which package is a better choice.

Once again, thanks for this great tutorial!!

slim

---

### Post by kchang on 2007-08-20
> **slimjim83 said:**
> I would like to comment on one small thing.  My application is Ubuntu 6.10 (server) w/ Nagios 2.9 & Plugins 1.4.9.  When installing the libgd2-dev package, I got an error message saying that it was a virtual package and there were no installation candidates.  It looks to me like this package has been split into 2 seperate ones, one with xpm support and one without.  I used libgd2-xpm-dev and it seems to work okay, though I haven't had much time to test it.  I thought maybe the instructions could be updated to reflect which package is a better choice.

I have to agree with slim. This How-To certainly made the nagios install much easier, and everything works fine except for the libgd2-dev package. Thank you for taking the time to create the How-To!

---

### Post by rodent on 2007-11-02
Hello all

I've got a new Ubuntu LAMP Server running on Fiesta Fawn :-) (7.04) and have downloaded nagios 2.10 and plugins.  I've run all the installs given here but  get the following when I try to install  libgd2-dev :

root@s-decc-ubuntu:/etc/postfix# apt-get install libgd2-dev

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package libgd2-dev

I've gotten the php5 GD Library support to run as per phpinfo() page :

GD Support  enabled  
GD Version  2.0 or higher  
FreeType Support  enabled  
FreeType Linkage  with freetype  
FreeType Version  2.2.1  
T1Lib Support  enabled  
GIF Read Support  enabled  
GIF Create Support  enabled  
JPG Support  enabled  
PNG Support  enabled  
WBMP Support  enabled  

When I configure nagios with the following string :

./configure --prefix=/etc/nagios --with-cgiurl=/nagios/cgi-bin --with-htmurl=/nagios --with-nagios-user=nagios --with-nagios-group=nagios --with-command-group=nagcmd --with-gd-lib=/usr/lib --with-gd-inc=/usr/include

I get no statusmap.cgi and or histogram.cgi.  In short all the nice graphic bits don't work while the rest works fine.  I have it monitoring everything I need but would like to have a complete installation.

Any help or suggestions would be appreciated.

Cheers

---

### Post by rfmug on 2007-12-01
I used the HOW TO to install Nagios 2.10 on Ubuntu 7.04. The instructions worked for me without alteration.

Thanks!

---

### Post by narinderpaul on 2008-01-09
very good instructions......Great stuff..

Cheers

---

### Post by Wyld on 2008-03-27
YMMV but I managed to get my Nagios installation (Nagios 3.0 sitting in Ubuntu 7.10) to function fully once I hunted down a missing dependency.

```
apt-get install libglib2.0-dev
```

After that, I use the following configure command:

```
./configure --prefix=/opt/nagios-3.0 --enable-nanosleep --enable-event-broker --with-nagios-user=nagios --with-nagios-group=nagios --with-command-user=nagcmd --with-command-group=nagcmd --with-gd-lib=/usr/lib
```

Now, you should alter your configure to suit your needs.  In my case, I place my compiled apps in /opt/whatever-version.x and create symlinks to point to the version I'm using.  Makes life a heap easier.  Thought I'd document my configure in case it helps.

G'luck mate :)

Edit: Did find an issue with the *order* of configuration options ... updated as I've done on my dev server, and I'm enjoying the Nagios world with VRML, just like it's 1998 :P

---

### Post by cb03BoilerUp on 2008-04-01
I agree with everyone else, this was one of the most straight-forward HOW-TOs that I´ve come across.  THANK YOU!

I am able to see windows machines with no problems, but cannot get routers to work out at all.  I have Nagios 3.0 on 7.10.  Whenever I add a router to the switch.cfg template, it gives the following error when I try to restart Nagios:

¨Running configuration check... CONFIG ERROR!  Restart aborted.  Check your Nagios configuration.¨

Does anyone have any sample configs from 3.0 that you have had success with?

Thanks,

---

### Post by Wyld on 2008-04-09
Best thing to start with is to verify your installation and look at where the issue actually is.

/path/bin/nagios -v /path/etc/nagios.cfg

This will tell you what line the issue is.

If you can see other machines, then you should be fine interacting with the switch.

---

### Post by cb03BoilerUp on 2008-04-10
Thanks Wyld, but after some further research, I had some other issues that forced me to completely start over.  I used the following link and it's working like a charm now.

[http://nagios.sourceforge.net/docs/3_0/quickstart-ubuntu.html](http://nagios.sourceforge.net/docs/3_0/quickstart-ubuntu.html)


:)

---

### Post by ajeetraina on 2008-05-15
Thanks for the Great Instructions for installing Nagios.
Can anyone provide me with the post-installation stuff..I mean How can I add the hosts plus the respective services monitoring??
Pls Help

---

