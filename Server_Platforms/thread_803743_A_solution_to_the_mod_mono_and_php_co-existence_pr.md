---
title: "A solution to the mod_mono and php co-existence problem on Ubuntu 8.04 (Hardy)"
date: 2008-05-22
forum: Server Platforms
---

### Post by kingherc on 2008-05-22
I've also published this in [my blog]("http://www.studentguru.gr/blogs/kingherc/archive/2008/05/22/how-to-mono-1-9-1-and-php-5-on-ubuntu-8-04-hardy.aspx"):

It got me a few days to find out how to solve this problem. And it was rather frustrating. But finally I got to run mod_mono on apache, and get some asp.net 2.0 working on Ubuntu 8.04! I searched around the internet, and many have the same problem: It's annoying that Ubuntu Hardy doesn't let you install mod_mono on apache 2 without uninstalling PHP, though it was possible on Ubuntu 7.10.


We'll assume a new Ubuntu 8.04 installation, with an apache 2 and php 5 installed and working fine. It's annoying that Ubuntu Hardy doesn't let you install libapache2-mod-mono without uninstalling libapache2-mod-php5 (which will then not serve php pages, and will only serve them as downloadable files), though it was possible on Ubuntu 7.10. It's further annoying that it's all too complicated to get mod_mono working! Let's solve the problem. I'm assuming you know a bit about linux commands, just enough to edit a file at least. I'll not explain all commands, but you can find some explanations about what we're doing in the referenced pages i've written in the bottom of the post.

 
**First steps:** 


[LIST]
[*]sudo apt-get remove mono-common
 That will remove all the extra packages that are installed with mono as they all depend on it. Be aware that it will also remove applications like f-spot and beagle, which will have to be re-installed after the mono upgrade if you wish to use them.
[*]cd ~
[*]mkdir src
[*]cd src
This is where we'll download the mono source files and work with them.
[*]sudo vi /etc/apt/sources.list
 Remove the # characters from the universe and multiverse entries and save the file. That will allow the apt-get command to install packages from the universe and multiverse repositories.
[*]sudo apt-get update
[*]sudo apt-get install build-essential pkg-config libglib2.0-dev bison libcairo2-dev libungif4-dev libjpeg62-dev libtiff4-dev
 This will install required and optional packages for compiling and installing mono.
[/LIST]
 [B]Installing libgdiplus:
 [/B] 
[LIST]
[*]Go to [http://go-mono.com/sources-stable/](http://go-mono.com/sources-stable/) to see the links for the files we'll be downloading and we'll compile and install. Note the version (if it's not 1.9.1 which we'll be using), and do something like the following to get the latest version from the links:
[*]wget [http://ftp.novell.com/pub/mono/sources/libgdiplus/libgdiplus-1.9.tar.bz2](http://ftp.novell.com/pub/mono/sources/libgdiplus/libgdiplus-1.9.tar.bz2)
[*]tar -xvf libgdiplus-1.9.tar.bz2
[*]cd libgdiplus-1.9/
[*]sudo ./configure --prefix=/usr/local
[*]sudo make
[*]sudo make install
[*]sudo sh -c "echo /usr/local/lib >> /etc/ld.so.conf"
[*]sudo /sbin/ldconfig
[/LIST]
 [B]Installing mono:
 [/B] 
[LIST]
[*]cd ~/src/
[*]wget [http://ftp.novell.com/pub/mono/sources/mono/mono-1.9.1.tar.bz2](http://ftp.novell.com/pub/mono/sources/mono/mono-1.9.1.tar.bz2)
[*]tar -xvf mono-1.9.1.tar.bz2
[*]cd mono-1.9.1
[*]sudo ./configure --prefix=/usr/local
[*]sudo make
[*]sudo make install
[*]We'll now add mono to the bash path. Edit the following file:
 vi ~/.bashrc
 And add the following lines at the end of the file:
 PATH=/usr/local/bin:$PATH 
 LD_LIBRARY_PATH=/usr/local/lib/:$LD_LIBRARY_PATH 
 PKG_CONFIG_PATH=/usr/local/lib/pkgconfig:$PKG_CONFIG_PATH
[*]bash
This command will reload bash, so that the mono command is available.
[/LIST]
 [B]Installing XSP (required, even if you'll only use mod_mono):
 [/B] 
[LIST]
[*]cd ~/src/
[*]wget [http://ftp.novell.com/pub/mono/sources/xsp/xsp-1.9.1.tar.bz2](http://ftp.novell.com/pub/mono/sources/xsp/xsp-1.9.1.tar.bz2)
[*]tar -xvf xsp-1.9.1.tar.bz2
[*]cd xsp-1.9.1/
[*]sudo ./configure --prefix=/usr/local
[*]sudo make
[*]sudo make install
[/LIST]
 [B]Let's test XSP and see if everything works until now:
 [/B]  
[LIST]
[*]cd /usr/local/lib/xsp/test
[*]xsp2
 This command will start the xsp web server which will most probably listen on port 8080. Because the command is run from this directory, this directory will serve as the root of the web server. Open up a browser and go to [http://localhost:8080/](http://localhost:8080/). You should see the XSP test asp.net pages. If you see them, everything works fine until now, cheers!
 Note: XSP is a great way to test and develop mono websites.
[/LIST]
 [B]Installing mod_mono module for apache 2:
 [/B] 
[LIST]
[*]sudo apt-get install apache2 apache2-threaded-dev
apache2-threaded-dev will be needed for apxs, which automates the loading of apache modules.
[*]cd ~/src/
[*]wget [http://ftp.novell.com/pub/mono/sources/mod_mono/mod_mono-1.9.tar.bz2](http://ftp.novell.com/pub/mono/sources/mod_mono/mod_mono-1.9.tar.bz2)
[*]tar -xvf mod_mono-1.9.tar.bz2
[*]cd mod_mono-1.9
[*]sudo ./configure --prefix=/usr --with-apxs=/usr/bin/apxs2
[*]sudo make
[*]sudo make install
[*]cp -r /usr/local/lib/xsp/test /var/www/test
 This will copy the XSP test site to Apache's default root website (/var/www), so that we may later test mod_mono and see if everything works fine.
[*]sudo a2enmod mod_mono
sudo vi /etc/apache2/mods-enabled/mod_mono.conf
 and uncomment the asp.net version of mono server you want (I uncommented the 2.0 and commented the 1.0).

EDIT: If the a2enmod command complains about not finding the module, then you'll have to activate mod_mono on apache manually:
Visit my first reference page at [http://blog.ruski.co.za/page/Install-Mono-126-on-Ubuntu-710.aspx](http://blog.ruski.co.za/page/Install-Mono-126-on-Ubuntu-710.aspx), and follow the steps of the section "Installing Mod_Mono" just after the "make install" command. Be careful to check the paths you write in those steps, because at some steps the paths should be /usr/lib/... and not /usr/local/lib/..., according to our guide. These steps are equivalent with the "a2enmod" step of my guide, and after you'll be able to continue to our next bullet point. I'm reproducing these steps for further assistance, but I've not tested them, if you have an error, please make a comment:
[LIST]
[*]sudo vi /etc/apache2/apache2.conf
Add the following line at the end:
Include /etc/apache2/mod_mono.conf
[*]sudo vi /etc/apache2/mods-available/mod_mono.load
Add the following line to the file:
LoadModule mono_module /usr/lib/apache2/modules/mod_mono.so[]("http://ftp.novell.com/pub/mono/sources/libgdiplus/libgdiplus-1.9.tar.bz2")
[*]sudo vi /etc/apache2/mods-available/mod_mono.conf
Add the following to the file:
AddType application/x-asp-net .aspx .ashx .asmx .ascx .asax .config .ascx
DirectoryIndex index.aspx
include /usr/local/lib/mono/2.0/mono-server2-hosts.conf
[*]sudo vi /usr/local/lib/mono/2.0/mono-server2-hosts.conf
Add the following to the file:
<IfModule mod_mono.c>
  MonoUnixSocket default /tmp/.mod_mono_server2
  MonoServerPath default /usr/local/lib/mono/2.0/mod-mono-server2.exe
  AddType application/x-asp-net .aspx .ashx .asmx .ascx .asax .config .ascx
  MonoApplicationsConfigDir default /usr/local/lib/mono/2.0
  MonoPath default /usr/local/lib/mono/2.0:/usr/local/lib
</IfModule>
Note: Be sure that /usr/local/lib/mono/2.0/mod-mono-server2.exe exists, else use /usr/bin/mod-mono-server2 instead (thanks tiger2004 for this).
[/LIST]
[*]sudo vi /etc/apache2/sites-enabled/000-default
 and add the following at the end of the virtual host:
     
 MonoServerPath "/usr/local/bin/mod-mono-server2"
 MonoApplications "/test:/var/www/test"
 <Directory /var/www/test>
     SetHandler mono
     AddHandler mod_mono .aspx .ascx .asax .ashx .config .cs .asmx
     DirectoryIndex index.html index.aspx default.aspx Default.aspx
     Options Indexes FollowSymLinks MultiViews
     AllowOverride None
     Order allow,deny
     allow from all
 </Directory>
[*]sudo /etc/init.d/apache2 restart
[*]Now, go to [http://localhost/test/](http://localhost/test/). If you see the XSP test pages, then everything works fine! Maybe you'll see the XSP test site without graphics and images, but it's not an error (it's because paths in the source shouldn't start with a /)!
 You can also test PHP pages, they should work fine too.
[/LIST]
 References:

[LIST]
[*][http://blog.ruski.co.za/page/Install-Mono-126-on-Ubuntu-710.aspx](http://blog.ruski.co.za/page/Install-Mono-126-on-Ubuntu-710.aspx)
[*][http://www.mono-project.com/Mod_mono](http://www.mono-project.com/Mod_mono)
[*][https://help.ubuntu.com/community/MonoFromSource](https://help.ubuntu.com/community/MonoFromSource)
[/LIST]

---

### Post by mattpd on 2008-07-11
thanks, worked perfectly (with your edit)!

---

### Post by tiger2004 on 2008-07-26
Hi
I think there is a problem with the following:

<IfModule mod_mono.c>
MonoUnixSocket default /tmp/.mod_mono_server2
MonoServerPath default [COLOR="Red"]/usr/local/lib/mono/2.0/mod-mono-server2.exe[/COLOR]
AddType application/x-asp-net .aspx .ashx .asmx .ascx .asax .config .ascx
MonoApplicationsConfigDir default /usr/local/lib/mono/2.0
MonoPath default /usr/local/lib/mono/2.0:/usr/local/lib
</IfModule>

The monoServerPath is currently (/usr/local/lib/mono/w.0/mod-monoserver.exe) which it doesn't work. However when I changed the monoServerPath to /usr/bin/mod-mono-server2, The mono server works fine. I have a question over this. Is the path ends in red with exe extension only for windows and it is here as a bug, or I have to install wine in order for this path to work correctly?

kind regards

---

### Post by aeolustw on 2008-09-08
[COLOR="Red"]Sorry , i canceled the asp function.[/COLOR]

Hi , kingherc

It works fine by your edit.

But when i browser the test page >> [http://yes168.tw/test/1.1/asp.net/browsercaps.aspx](http://yes168.tw/test/1.1/asp.net/browsercaps.aspx)

There are five error messages with red color >>

Item >> [COLOR="Red"]Error: Number of parameter does not match expected count.[/COLOR]

HtmlTextWriter >> [COLOR="Red"]Error: Number of parameter does not match expected count.[/COLOR]

RequiresContentTypeMetaTag >> [COLOR="Red"]Error: Number of parameter does not match expected count.[/COLOR]

RequiresControlStateInSession >> [COLOR="Red"]Error: Number of parameter does not match expected count.[/COLOR]

UseOptimizedCacheKey >> [COLOR="Red"]Error: Number of parameter does not match expected count.[/COLOR]

What do they means?

How to fix them?

Thanks.:KS

---

### Post by roeltje.com on 2009-01-19
A quick fix to make the HOWTO complete.

To get the css-styles / graphics working, run the following command
$find /var/www/test -print0 | xargs -0 perl -pi -e 's/mono-xsp.css/test\/mono-xsp.css/g'

---

### Post by kingherc on 2009-02-01
> **aeolustw said:**
> [COLOR="Red"]Sorry , i canceled the asp function.[/COLOR]

Hi , kingherc

It works fine by your edit.

But when i browser the test page >> [http://yes168.tw/test/1.1/asp.net/browsercaps.aspx](http://yes168.tw/test/1.1/asp.net/browsercaps.aspx)

There are five error messages with red color >>

Item >> [COLOR="Red"]Error: Number of parameter does not match expected count.[/COLOR]

HtmlTextWriter >> [COLOR="Red"]Error: Number of parameter does not match expected count.[/COLOR]

RequiresContentTypeMetaTag >> [COLOR="Red"]Error: Number of parameter does not match expected count.[/COLOR]

RequiresControlStateInSession >> [COLOR="Red"]Error: Number of parameter does not match expected count.[/COLOR]

UseOptimizedCacheKey >> [COLOR="Red"]Error: Number of parameter does not match expected count.[/COLOR]

What do they means?

How to fix them?

Thanks.:KS

I have no idea :)
Is it an asp.net error?

> **roeltje.com said:**
> A quick fix to make the HOWTO complete.

To get the css-styles / graphics working, run the following command
$find /var/www/test -print0 | xargs -0 perl -pi -e 's/mono-xsp.css/test\/mono-xsp.css/g'

Thanks for the add!

---

### Post by kingherc on 2009-02-01
> **tiger2004 said:**
> Hi
I think there is a problem with the following:

<IfModule mod_mono.c>
MonoUnixSocket default /tmp/.mod_mono_server2
MonoServerPath default [COLOR="Red"]/usr/local/lib/mono/2.0/mod-mono-server2.exe[/COLOR]
AddType application/x-asp-net .aspx .ashx .asmx .ascx .asax .config .ascx
MonoApplicationsConfigDir default /usr/local/lib/mono/2.0
MonoPath default /usr/local/lib/mono/2.0:/usr/local/lib
</IfModule>

The monoServerPath is currently (/usr/local/lib/mono/w.0/mod-monoserver.exe) which it doesn't work. However when I changed the monoServerPath to /usr/bin/mod-mono-server2, The mono server works fine. I have a question over this. Is the path ends in red with exe extension only for windows and it is here as a bug, or I have to install wine in order for this path to work correctly?

kind regards

The EDIT section of the guide was taken from the reference website I mentioned at the end of the guide. It's peculiar to see an .exe file, but my only guess is that the mono server app is written in pure .NET, and thus can be run on linux by Mono. I have to stress there's no need for Wine. 
Anyways, the shortcut you mentioned does make sense and seems like it'd work!

---

### Post by noninoni on 2009-02-19
Hi kingherc,
Thanks for the detailed steps for installing and running Mono on ubuntu and the same is working fine. But my original problem is not solved i.e when i click on .php a dialog box appears for downloading. Please let me know any other setting needs to be done. I exactly followed the steps what u have given. 

Secondly I wanted to host a asp.net application where the data is kept in SQL SERVER on another machine. The application refers to web.config for database connection. When I host the application the Login page is appearing but it is not moving further. I suspect the DB is not getting connected. I checked in apache log nothing is given in that. Any one please let me know if I have to do some tweaks to make it work.

Rajshekar

---

### Post by kingherc on 2009-02-19
Well, if .php files come as downloadable files, then the handler for php files on apache doesn't work. Possibly, your libapache2-mod-php5 wasn't installed when you started the whole guide. Or it got removed in the process. Or you're trying to run .php files in the same directory as your asp.net website. I can't think of any other reasons.
Do check that before starting the guide, PHP was working correctly.

As for the SQL Server, I haven't tested any database connections because I didn't get the chance to go further with mono, I switched back to Windows Server :)
But if you're having a connection problem, there should be an asp.net error page, stating the error details. Didn't one popup?

---

### Post by noninoni on 2009-02-19
Hi Kingherc,
Earlier .php was working fine then I installed mono. Then the problem started. I had installed libapache2-mod-php5 before this. All the applications are hosted in different directories under var/www/.
As for as SQL SERVER connection i am also exploring the connection possibilities. I will update you once I get through. I need to deploy web services also in mono.

---

### Post by kingherc on 2009-02-21
> **noninoni said:**
> Hi Kingherc,
Earlier .php was working fine then I installed mono. Then the problem started. I had installed libapache2-mod-php5 before this. All the applications are hosted in different directories under var/www/.
As for as SQL SERVER connection i am also exploring the connection possibilities. I will update you once I get through. I need to deploy web services also in mono.

Well my guess is that libapache2-mod-php5 got removed somewhere in the steps. Can you check that libapache2-mod-php5 is not installed after completing the guide? If it's not, then you could try running again the guide from scratch on a virtual machine, and check where the libapache2-mod-php5 gets removed.
I can't take a guess, because the point of the guide was to keep both packets. Something which worked for me.

If libapache2-mod-php5 is still installed, then you must have a problem with your apache configuration. Try switching back to default configuration files, and see if .php files work.

---

### Post by Xolamee on 2009-04-13
If the php module was not uninstalled during the process of following this guide, but php files still try to download rather than open in the browser, you might try erasing/emptying your cache on your browser. This has been reported to cause problems in the past.

---

### Post by tang214 on 2009-08-20
Is it possible to run both .asmx (or any .NET page) and php pages from the /var/www directory? 

PHP was working from the beginning and I ran through this how to only modifying the part where mono applications are served from and now mono works but php does not.

---

### Post by directhex on 2009-08-20
> **tang214 said:**
> Is it possible to run both .asmx (or any .NET page) and php pages from the /var/www directory? 

PHP was working from the beginning and I ran through this how to only modifying the part where mono applications are served from and now mono works but php does not.

if you use mod-mono-auto rather than mod-mono as the apache module, it ought to work

---

### Post by GoodLuckyBoy on 2010-11-06
Thank you for [kingherc&#65281;]("http://ubuntuforums.org/member.php?u=580031")

---

