---
title: "http, https, XAMPP and kittens."
date: 2009-12-04
forum: Server Platforms
---

### Post by christhegoth on 2009-12-04
The kittens bit is optional, but can be fun.

Tested on Ubuntu Hardy 64 bit, and Debian Lenny text only 32-bit.  Any urls that are mine are on a home server, so it may be rebooted on occasion as it is a test rig.  My switches also reboot twice per week to keep them fresh.

Ok, XAMPP by Apachefriends is lovely.  And works so very well for Ubuntu.  So...

How do you get the https bit working with full virtual hosting activated as well.  It's actually very simple ( ah XAMPP, how I love thee... ) so I'll run through it here.  I cracked it yesterday so thought I'd put this how-to together as my formal write-up shall we say.

Right, the test subject is a 9 year old laptop called Bumblebee who actually runs Debian Lenny.  But due to Ubuntu being gorgeous this works on Ubuntu as well.  Debian Lenny is a much smaller install though, so suitable for the old 'bucket of bolts' I've been playing with.  And yes it is fully patchable and very responsive.

Right, my base assumption is that you are text only on an ssh connnection, and have sudo rights for your log-in.  Use the command 'visudo' and add your login to the list if you cannot sudo normally.   I doubt it'll be an issue in Ubuntu, but Debian Lenny can be iffy here.

I'm also assuming you are using Gnome-RDP as an ssh client, as it has a nice copy and paste set-up with a web-browser like firefox.  I found putty wasn't great for this bit, but Gnome-RDP works well as long as your sshd lives on port 22.  Gnome-RDP only works on port 22 servers.

And here we go...



Ok, download and install XAMPP. The website can tell you how to do that.  Once installed you need to make a decision.  Developer, or Production machine.  Developer is already thought of, but if you want to make a machine to actually use for real ( and not play with ) run this command.

sudo /opt/lampp/lampp security

I generally do not password lock the http docs, but you definitely need that sql server not accessible from the network.  Once done you are ready to rock really.  Well, for a basic install.  But you need more than a basic install to run a happy https site that is always https.  And this is the bit I'm really gonna write up.


Ok, go to /opt/lampp/etc and find the httpd.conf.  Open it, and make some adjustments.  Leave it listening on port 80 or virtual hosting WILL NOT WORK.  This is fine though, as virtual hosting means loads of websites on one server on the same port.  Port 80.  You'll also need to find the list of indexes and make sure the filetypes index.htm and index.htm.var are also there.  That's about half way down.  I find this is good practice due to Dreamweaver and stuff like that using .htm commonly.

Also set the document root to a folder which has a basic testpage for the server in.  /var/www/testpage for example if it lives there.  the /var folder is for variable data that users fiddle with.  So creating /var/www and the setting up sub-folders for each website works fine.

[http://bumblebee.gothfiles.org.uk](http://bumblebee.gothfiles.org.uk) 

...is my testpage.  The link goes to a subfolder in the website file-tree.  This is purely for safety, so there is a 'default if you accidentally bust vhosting'.  An 'oops! page' you could say.

Then head down to the bottom and you'll get the hashed out 'include this doobrey' posts.  Remove the hash at the start of the line which says to include httpd-vhosts.conf .  What this does is that the server will now ignore the filetree entry above and use only the virtual host configuration file.  The filetree entry above is purely for if you accidentally break vhosting.  The default is to a 'safe' site, and not your document root for all sites...

Save that and move on.  The next file you need is in /opt/lampp/etc/extra and is httpd-vhosts.conf.  Crack it open and have a look, as this is the heart of your server now.

The frist vhost is the default.  It will have a server alias entry where as others don't.  Set that to localhost.  And change the servername url bit to the url for your testpage.   In my case bumblebee BLAH.  Don't forget to add that url to the prenames for the log files as well.

My entry looks like this:

<VirtualHost *:80>
    ServerAdmin [email]christhegoth@yahoo.com[/email]
    DocumentRoot /var/www/test
    ServerName bumblebee.gothfiles.org.uk
    ServerAlias localhost
    ErrorLog logs/bumblebee.gothfiles.org.uk-error_log
    CustomLog logs/bumblebee.gothfiles.org.uk-access_log common
</VirtualHost>

<VirtualHost *:80>
    ServerAdmin [email]christhegoth@yahoo.com[/email]
    DocumentRoot /var/www/bumblebeesecure
    ServerName bumblebeesecure.gothfiles.org.uk
    ErrorLog logs/bumblebeesecure.gothfiles.org.uk-error_log
    CustomLog logs/bumblebeesecure.gothfiles.org.uk-access_log common
</VirtualHost>


The first has the alias, and is the testpage and anchor point to localhost.  After that add as many as you want/ need to add.  This is all http protocol though.

The https bit does also activate when you start the server up, but you need to do some adjustments to it.  bumblebeesecure is part of my https site by the way, but I'll get to that.  It's there in the http bit as you need to bump the connection to https for safety sake, as the users won't always remember to use https:// instead of [http://.](http://.)  So you rig the website to do it for them.

I'll get to that bit later.

In the httpd-vhosts.conf you'll see this line:

NameVirtualHost *:80

That sets up named based virtual-hosting, which is obviously what you want.  Copy that and paste it to a separate notepad program, and then change the 80 to 443.

Save that lot and head to httpd-ssl.conf , which is still in /opt/lampp/etc/extra .  This is the conf file for the https bit and has it all in one place, including the virtual hosting.  It is set up so that 1 virtualhost only will work for https, which is useful but too basic if your server is beefy as you like.  We want moar dammit!!!  Moar https sites supported !!!  *froth froth* *types like a maniac*.

*ahem*  Yes, full virtual-hosting and https is the ideal, so we need to adjust this file a little.  Read down until you reach the first virtualhost.   Starting <virtualhost...

Just before it add:

NameVirtualHost *:443

This activates name based virtual-hosting, as in the basic install only 1 https set is supported as I said.

And then adjust it's start id from:

<VirtualHost _default_:443>

to

<VirtualHost *:443>

That's it, full virtual-hosting unlocked for the https server.

After that add as many virtual-hosts you need, as the ServerAlias bit is looked after by the http bit mentioned previously.  Just make sure the doc root is set to the correct folder and it'll do the rest.  Mine is:

<VirtualHost *:443>

DocumentRoot "/var/www/httpssites/bumblebeesecure"
ServerName bumblebeesecure.gothfiles.org.uk:443
ServerAdmin [email]christhegoth@yahoo.com[/email]
ErrorLog /opt/lampp/logs/error_log
TransferLog /opt/lampp/logs/access_log

Followed by a load of presets you do not actually have to touch, and then eventually down the bottom the final </virtualhost>

To add another virtual-host simply copy, paste, and adjust doc-roots accordingly.

To start the server the command is as follows:

sudo /opt/lampp/lampp start

'sudo /opt/lampp/lampp stop' also works, as does putting 'restart' on the end if you've added a host and need to restart the server to add it in.


With my confs you'll see bumblebeesecure is the site.  There are 2 parts to it really.  The full site, which lives on the https v-host, and the load page which lives on http vhosts as well as being the first page in the full site.

The first page is a 'loading page'.  'Please wait' or some message like that, a little pretty icon, and a meta-tag redirect.  The meta-tag redirect is the key here, as you set the url to https there.  Remember what I said about the user not reliably typing https:// every time?  This bit forces it.

In the site tree it's index.htm ( so is loaded first as default ), and the redirect is to...

[https://bumblebeesecure.gothfiles.org.uk/testsecure.htm](https://bumblebeesecure.gothfiles.org.uk/testsecure.htm)

...after 2 seconds.  In the metatags.  You only see this loading page before the main site loads.  Right, where do you put it in your server?

The loading page, and associated images, goes in both the http and https folders you've set up, and the rest of the site is ONLY in the https section.  That way if some twerp tries to access sub-pages by url and only uses the http:// prefix there is nothing to load as they are all in the https side only.  

The 'loading page' is in both so that that https:// redirect happens to make sure the https:// protocol is activated.  And as I said if the prefix is http:// only the index.htm url will load.  As that is the only bit in the http:// side of the virtual host.

You really do need that by the way, but it is very easy to make.  You have to think of the http version and the https version as different, even though the rest of the url is the same.  2 separate sites under the same name.

[http://bumblebeesecure.gothfiles.org.uk](http://bumblebeesecure.gothfiles.org.uk)  now works.
[https://bumblebeesecure.gothfiles.org.uk](https://bumblebeesecure.gothfiles.org.uk)  also works.

[https://bumblebeesecure.gothfiles.org.uk/testsecure.htm](https://bumblebeesecure.gothfiles.org.uk/testsecure.htm)  also works for the redirect on https ONLY

but if you type in

[http://bumblebeesecure.gothfiles.org.uk/testsecure.htm](http://bumblebeesecure.gothfiles.org.uk/testsecure.htm) there is nothing to load.  So the twerp is stopped from busting his own security IYSWIM.

The server I have hosts these:

[http://ctgsecure.gothfiles.org.uk](http://ctgsecure.gothfiles.org.uk)
[http://bumblebeesecure.gothfiles.org.uk](http://bumblebeesecure.gothfiles.org.uk)

Both go https, and both live on the same physical 'bucket of bolts'.  Nice :D


Further add-ons:

FTP support works fine here for ftp'ing in to update your site.  Even on debian lenny this guide...

[http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)

...is still good with proftpd.  Including the TLS bit, which I do advise if you're gonna do it properly.

Also, Truecrypt.  If you set up Truecrypt and create ext3 filevaults you can ftp into them and host websites out of them.  As long as they're mounted obviously.  In the event of a powerdown the filevault closes and won't open without the usual password.  So the website inside is locked in.  Protects any sensitive data.  This will not work with FAT format, so don't try it with that.  Text only Debian Lenny only gives you the option for fat, but Ubuntu on GUI ( how I normally do this ) works like a dream.

After that it's simply a big-*** lock on the server room door, various big slightly rusty chains fixing the servers to the wall, and some spring-loaded rottweilers or an Aliens sentry gun.

*click!*  *boing!*  *growl snarl* etc etc.

Mad Scientists do have their uses :D

---

