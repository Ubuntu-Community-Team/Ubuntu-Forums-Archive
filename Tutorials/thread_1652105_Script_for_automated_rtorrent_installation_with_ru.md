---
title: "Script for automated rtorrent installation with rutorrent for Ubuntu 10.04!"
date: 2010-12-24
forum: Tutorials
---

### Post by CyberAngel on 2010-12-24
Hello,

I was trying to install rtorrent lately with a good web interface in my Ubuntu 10.04 server but I found it to be a quite challenging task.
After I succesfully managed to install rtorrent with rutorrent as a web ui, I created a bash script to do everything automatically and thought that someone else might find it useful so I am posting it here.

**My demands were the following so the script accomplishes them too:**
```
* rtorrent had to be able to run as a service automatically upon boot.
* No GUI with any gnome or kde dependencies! Only a web interface as this installation was targeting a headless server.
* No source compilation
* Single user use and authorization
```

You can read also more info in the beginning of the script.
Some quoted text of what this script will do in your computer..

```
# The script will do the following changes in your computer:
#       1) Download rtorrent 3.2
#       2) Download rtorrent plugins 3.2
#       3) Download a startup script for rtorrent
#       4) Download a working .rtorrent.rc
#       5) Check the md5sum of the downloaded files.
#       6) Add a PPA repository for rtorrent compiled against the latest xmlrpc libraries.
#       7) Download any extra dependencies using apt-get such as apache, screen and some more.
#       8) Create all necessary directories
#       9) Set all necessary permissions
#       10) Ask for a password (using htpasswd) for the given username to be able to access the web page of rutorrent
#       11) Install the startup script for automatic startup of rtorrent on boot.
```

To run the script download the attachment, make it executable and run it:

```

chmod +x rtorrent_server.sh

sudo ./rtorrent_server.sh <username>

```

The <username> has to be a valid system user with an id of 1000 or more. The default one created during ubuntu installation will do fine ;)
This user will be used to run the rtorrent instance.

Enjoy!

[COLOR="Red"]Update 2011-07-22 :[/COLOR]
[COLOR="Orange"]A much requested feature[/COLOR] has been implemented by user [rocker2344]("http://ubuntuforums.org/member.php?u=865866"). The feature is multi user support and ISPConfig integration as a bonus ;)
I haven't tested the script myself, but you can test and report success back here.
Follow this link for more information: [http://ubuntuforums.org/showpost.php?p=11072942&postcount=47](http://ubuntuforums.org/showpost.php?p=11072942&postcount=47)


[COLOR="Red"]Update 2011-01-20 :[/COLOR] Script was not installing one very important package! Now fixed (libapache2-mod-php5 and unzip).

---

### Post by nilsja on 2011-01-17
Hi CyberAngel,

thank you very much for your work on this. The installation worked great. But i get these errors under the tab "logger":

"ratio: plugin can't start for unknown reason."
and
"Bad response from server: (500),[Error.setsettings]) Warning: XMLRPCcall is failed."

And torrent adding works fine but downloads don't start. 

Do you have a idea how to solve this?

---

### Post by CyberAngel on 2011-01-17
> **nilsja said:**
> Hi CyberAngel,

thank you very much for your work on this. The installation worked great. But i get these errors under the tab "logger":

"ratio: plugin can't start for unknown reason."
and
"Bad response from server: (500),[Error.setsettings]) Warning: XMLRPCcall is failed."

And torrent adding works fine but downloads don't start. 

Do you have a idea how to solve this?

Hello there,

Did you try to install in ubuntu 10.10?

This script will not work with it!
If you read in the beginning of the script I have a notification about it.
```
# The script will not work for Ubuntu 10.10 as the repository used contains packages 
# only for Ubuntu 10.04.
```

That's because rutorrent must be compiled against the latest xmlrpc libraries and the ppa repository I use only works for ubuntu 10.04.

If that's the case, then you need to compile xmlrpc and rutorrent yourself!

Try this link that it has information on how to compile it yourself ;)
[http://chrispenner.info/blog/2010/07/20/installing-rtorrent-rutorrent-on-ubuntu-server-10-04-lts/](http://chrispenner.info/blog/2010/07/20/installing-rtorrent-rutorrent-on-ubuntu-server-10-04-lts/)

---

### Post by nilsja on 2011-01-17
no, it is on Ubuntu 10.04

---

### Post by CoolHandSE on 2011-01-18
I uninstalled standard rtorrent from my 10.04 ubuntu server and ran your script in order to get web access to rtorrent. It appeared to work.

rtorrent runs and the web interface is accessable although it does not show me the status of any torrents, this is the error message in Firefox...


[18.01.2011 11:09:38] WebUI started.
[18.01.2011 11:09:38] JS error: [[http://192.168.2.2/rutorrent/](http://192.168.2.2/rutorrent/) : 403] XML cannot be the whole program

the error message in Internet Explorer is...

[18.01.2011 11:36:03] WebUI started.
 [18.01.2011 11:36:03] JS error: [[http://192.168.2.2/rutorrent/](http://192.168.2.2/rutorrent/) :  121987285] Syntax error
 [18.01.2011 11:36:04] Bad response from server: (200  [parsererror,getuisettings]) <?phprequire_once( 'util.php' );$fname =  getSettingsPath()."/uisettings.json";$s = @file_get_contents($fname); if($s==false)    $s = '{}';cachedEcho($s,"application/json",true);?>

The problem is with rutorrent because ntorrent can connect to rtorrent.

Any ideas on how to fix this?

---

### Post by nilsja on 2011-01-18
now i got another error: "rTorrent is compiled with incorrect version of xmlrpc-c library, without i8 support. Version must be >= 1.11. Some functionality will be unavailable."

i think i'll have to try wtorrent again...

---

### Post by CyberAngel on 2011-01-20
Hey!

I forgot to make the script installing a very important package as I had a LAMP already installed....

Try to run this line:

```
sudo apt-get install libapache2-mod-php5 unzip
```

I created a fresh 10.04.1 virtual machine, ran the script with this change and now it looks like working fine ;)

---

### Post by nilsja on 2011-01-20
already had this installed too. but still tried it again. this time i recognized an error right from the install script: "cannot find rtorrent binary in PATH /usr/bin:/usr/local/bin:/usr/local/sbin:/sbin:/bin:/usr/sbin"

---

### Post by CyberAngel on 2011-01-20
> **nilsja said:**
> already had this installed too. but still tried it again. this time i recognized an error right from the install script: "cannot find rtorrent binary in PATH /usr/bin:/usr/local/bin:/usr/local/sbin:/sbin:/bin:/usr/sbin"

Try to run the following command and give me the output here...

```
apt-cache policy rtorrent
```

---

### Post by nilsja on 2011-01-21
```
apt-cache policy rtorrent
rtorrent:
  Installiert: (keine)
  Kandidat: 0.8.6-1
  Versions-Tabelle:
     0.8.6-1 0
        500 http://de.archive.ubuntu.com/ubuntu/ lucid/universe Packages

```
(keine) means none...

---

### Post by CyberAngel on 2011-01-21
> **nilsja said:**
> ```
apt-cache policy rtorrent
rtorrent:
  Installiert: (keine)
  Kandidat: 0.8.6-1
  Versions-Tabelle:
     0.8.6-1 0
        500 http://de.archive.ubuntu.com/ubuntu/ lucid/universe Packages

```
(keine) means none...

Did you run the script as root?

You should have rtorrent installed from another ppa repository there!

Try to download and re-run the script once more!

If this is not working again, run this command: 
```
apt-get update && apt-get -y install python-software-properties && add-apt-repository ppa:patricksissons/rtorrent && apt-get install rtorrent
```

and the run the apt-cache policy one again to make sure that it is installed from the correct repository.

---

### Post by nilsja on 2011-01-21
```
sudo apt-cache policy rtorrent
rtorrent:
  Installiert: 0.8.6-3~patricksissons0
  Kandidat: 0.8.6-3~patricksissons0
  Versions-Tabelle:
 *** 0.8.6-3~patricksissons0 0
        500 http://ppa.launchpad.net/patricksissons/rtorrent/ubuntu/ lucid/main Packages
        100 /var/lib/dpkg/status
     0.8.6-1 0
        500 http://de.archive.ubuntu.com/ubuntu/ lucid/universe Packages

```

but the messages in the rutorrent gui still are: ```
[21.01.2011 20:53:48] WebUI started.
[21.01.2011 20:53:48] Bad link to rTorrent. Check if it is really running. Check $scgi_port and $scgi_host settings in config.php and scgi_port in rTorrent configuration file.
[21.01.2011 20:53:48] rssurlrewrite: Plugin will not work. It require existence of plugin(s) rss
```

---

### Post by CyberAngel on 2011-01-21
> **nilsja said:**
> ```
sudo apt-cache policy rtorrent
rtorrent:
  Installiert: 0.8.6-3~patricksissons0
  Kandidat: 0.8.6-3~patricksissons0
  Versions-Tabelle:
 *** 0.8.6-3~patricksissons0 0
        500 http://ppa.launchpad.net/patricksissons/rtorrent/ubuntu/ lucid/main Packages
        100 /var/lib/dpkg/status
     0.8.6-1 0
        500 http://de.archive.ubuntu.com/ubuntu/ lucid/universe Packages

```

but the messages in the rutorrent gui still are: ```
[21.01.2011 20:53:48] WebUI started.
[21.01.2011 20:53:48] Bad link to rTorrent. Check if it is really running. Check $scgi_port and $scgi_host settings in config.php and scgi_port in rTorrent configuration file.
[21.01.2011 20:53:48] rssurlrewrite: Plugin will not work. It require existence of plugin(s) rss
```

From the errors I see, it means that the script didn't ran correctly.

Please re-download it, make it executable and then run it again:

```
chmod +x rtorrent_server.sh
sudo ./rtorrent_server.sh <add-your-username-here>
```

---

### Post by Vrutin on 2011-01-27
Its working had no problems installed in 2 minutes...
=====================================================
Though, How Would I Add another user?

---

### Post by CyberAngel on 2011-01-27
> **Vrutin said:**
> Its working had no problems installed in 2 minutes...
=====================================================
Though, How Would I Add another user?

rutorrent does not support many users.
You can make it work (search for "rutorrent multi user" in google) but it's not easy so I didn't bother as a single user is enough for my needs.

---

### Post by pendhu on 2011-02-01
Hi CyberAngel, 

Great work my friend, I ran the script as per your instructions, it installed within a couple of minutes and I'm up and running already, I definately recommend this brilliant script for a painless install of rutorrent on Ubuntu 10.04, just make sure you follow the instructions and you can't go wrong.

Keep up the good work mate!

Rgds
pendhu  

;)

---

### Post by kevinamadeus2 on 2011-02-07
OMG! Thank you soo much for this script!
I am a Linux noob and all the guides setting up rtorrent with rutorrent cause so many errors. You can't image how much time I wasted for failures. And now I used 2 mins for all things set up!

---

### Post by CyberAngel on 2011-02-07
I am glad that this script helped more people :)

Thank you for you kind comments!

---

### Post by DpGonzo on 2011-02-11
After 4 hours of frustration in trying to get rtorrent to work with rpc plugin on my Mythbuntu 10.04, your script was a desk-saver (the desk survived the continuing blows of frustrastion...)

Thanx a lot CyberAngel!

---

### Post by CyberAngel on 2011-02-11
> **DpGonzo said:**
> ....your script was a desk-saver...

:D
I can add it to the feature list!!
hahahaha

---

### Post by ChriZathens on 2011-02-15
Thanks a lot for your script!
I already have rtorrent installed (ubuntu 10.10), but I have thought many times about changing to a different app (like e.g. deluge) just because it is not e&#945;sy to install rtorrent+rutorrent again in case of a failure where a new installation will be needed..
I trust that you will update the script as long as the reps for 10.10 are available? If this is the case then this will be a rare diamond :)

---

### Post by CyberAngel on 2011-02-15
> **ChriZathens said:**
> Thanks a lot for your script!
I already have rtorrent installed (ubuntu 10.10), but I have thought many times about changing to a different app (like e.g. deluge) just because it is not e&#945;sy to install rtorrent+rutorrent again in case of a failure where a new installation will be needed..
I trust that you will update the script as long as the reps for 10.10 are available? If this is the case then this will be a rare diamond :)

I guess that this won't be a problem :)

---

### Post by stbunny on 2011-02-18
Works like a charm!

Thanks a lot!

---

### Post by Deamos on 2011-02-25
Script worked great! Quite a lifesaver!

---

### Post by mcmn on 2011-02-26
looks great, seems to have worked aswell. Thanks alot mate.

---

### Post by kis2a on 2011-03-05
thanks for this ,


You are not possible to mod this for multiple user please ?

Work perfectly for one user , 

one solution for add multiple user ?

;)

---

### Post by jesth on 2011-03-05
I just spent 5 hours trying to manually do what your script is doing, I had alot of errors, but then I googled, and found your script, will test it in a few.

*EDIT* Flawlessly installation and working with the WebGui, thanks alot for this great script.

---

### Post by Magneto on 2011-03-10
Thank you very much! Fantastic script!

Remember to change permissions on any directories you use for watch, downloads or sessions. Set them to 775 and www-data for the group. Without those changes your torrents will pause (be "pausing" - key search word for rutorrent forums) forever.

---

### Post by CyberAngel on 2011-03-10
> **Magneto said:**
> Thank you very much! Fantastic script!

Remember to change permissions on any directories you use for watch, downloads or sessions. Set them to 775 and www-data for the group. Without those changes your torrents will pause (be "pausing" - key search word for rutorrent forums) forever.

You're welcome! :)

What do you mean by changing permissions? Which folders are you talking about?
I didn't have any problems.
rtorrent runs as a simple user (the one you provide in the script), so the folders for the default download location are created under the user's home directory and rtorrent has full access on them.

---

### Post by conkyrc on 2011-03-11
OS: Ubuntu v10.04 32bits

I´ve followed the next steps:

- Uploaded through FTP "rtorrent_server.sh" to /home/myusername
- chmod +x /home/myusername/rtorrent_server.sh
- sudo /home/myusername/rtorrent_server.sh myusername

The install goes well but i see the next error msg: 

```
cannot find readable config /home/myusername/.rtorrent.rc. check that it is there and permissions a     re appropriate
```

After that i done:

```
sudo apt-cache policy rtorrent
rtorrent:
  Installiert: 0.8.6-3~patricksissons0
  Kandidat: 0.8.6-3~patricksissons0
  Versions-Tabelle:
 *** 0.8.6-3~patricksissons0 0
        500 http://ppa.launchpad.net/patricksissons/rtorrent/ubuntu/ lucid/main Packages
        100 /var/lib/dpkg/status
     0.8.6-1 0
        500 http://de.archive.ubuntu.com/ubuntu/ lucid/universe Packages
```

But when i log in the WebUI rTorrent doesn´t work:

```
[21.01.2011 20:53:48] WebUI started.
[21.01.2011 20:53:48] Bad link to rTorrent. Check if it is really running. Check $scgi_port and $scgi_host settings in config.php and scgi_port in rTorrent configuration file.
[21.01.2011 20:53:48] rssurlrewrite: Plugin will not work. It require existence of plugin(s) rss
```

As you told us before, i tried to re-download & re-upload the script from this thread but i have always the same problem so i cannot use rTorrent properly...

I would like to know how to fix this problem or at least know how to unistall the whole script for do a manual setup of rTorrent + ruTorrent

Thanks for all!

---

### Post by CyberAngel on 2011-03-11
> **conkyrc said:**
> OS: Ubuntu v10.04 32bits

I´ve followed the next steps:

- Uploaded through FTP "rtorrent_server.sh" to /home/myusername
- chmod +x /home/myusername/rtorrent_server.sh
- sudo /home/myusername/rtorrent_server.sh myusername

The install goes well but i see the next error msg: 

```
cannot find readable config /home/myusername/.rtorrent.rc. check that it is there and permissions a     re appropriate
```

After that i done:

```
sudo apt-cache policy rtorrent
rtorrent:
  Installiert: 0.8.6-3~patricksissons0
  Kandidat: 0.8.6-3~patricksissons0
  Versions-Tabelle:
 *** 0.8.6-3~patricksissons0 0
        500 http://ppa.launchpad.net/patricksissons/rtorrent/ubuntu/ lucid/main Packages
        100 /var/lib/dpkg/status
     0.8.6-1 0
        500 http://de.archive.ubuntu.com/ubuntu/ lucid/universe Packages
```

But when i log in the WebUI rTorrent doesn´t work:

```
[21.01.2011 20:53:48] WebUI started.
[21.01.2011 20:53:48] Bad link to rTorrent. Check if it is really running. Check $scgi_port and $scgi_host settings in config.php and scgi_port in rTorrent configuration file.
[21.01.2011 20:53:48] rssurlrewrite: Plugin will not work. It require existence of plugin(s) rss
```

As you told us before, i tried to re-download & re-upload the script from this thred but i have always the same problem so i cannot use rTorrent properly...

I would like to know how to fix this problem or at least know how to unistall the whole script for do a manual setup of rTorrent + ruTorrent

Thanks for all!


Run the following commands and every change related to rtorrent and rutorrent will be wiped out ;)
Well, to be more exact, the repository added will not be removed and apache will not be removed too (someone might had apache installed before running this script).

```
sudo apt-get --purge autoremove rtorrent
sudo rm -f /home/<user-you-used-install>/.rtorrent.rc
sudo rm -rf /home/<user-you-used-install>/rtorrent
sudo update-rc.d -f rtorrentInit.sh remove
sudo rm /etc/init.d/rtorrentInit.sh
sudo rm -rf /var/www/rutorrent
sudo a2dissite rutorrent
sudo rm -f /etc/apache2/sites-available/rutorrent

Reboot your computer.
```

---

### Post by conkyrc on 2011-03-11
> **CyberAngel said:**
> Run the following commands and every change related to rtorrent and rutorrent will be wiped out ;)
Well, to be more exact, the repository added will not be removed and apache will not be removed too (someone might had apache installed before running this script).

```
sudo apt-get --purge autoremove rtorrent
sudo rm -f /home/<user-you-used-install>/.rtorrent.rc
sudo rm -rf /home/<user-you-used-install>/rtorrent
sudo update-rc.d -f rtorrentInit.sh remove
sudo rm /etc/init.d/rtorrentInit.sh
sudo rm -rf /var/www/rutorrent
sudo a2dissite rutorrent
sudo rm -f /etc/apache2/sites-available/rutorrent

Reboot your computer.
```
Ok, all rtorrent paths & configs are now removed, again thanks for your fast anwser & useful information.

Now i would like to offer you a custom quote, as a linux user i always try to learn and fix all the problems i usually have with it. All we know that are a lot of nice how-to around Internet for install this manually, anyway i will love to know why i can´t install and run properly this script under my box.

About the box, i will be glad of share my dedicated (Will be used as plain seedbox rTorrent+FTP without GNOME/KDE or any kind of graphical interface, it has 500GB of HDD @ 100Mbps [5TB Bandwitdh per month] and i haven´t used it a lot during the last days. It has a default Ubuntu v10.04 x32 OS.

Before start the installation process, i create a new user called rt, after that i put them into the sudoers file. I uploaded the rtorrent_server.sh script and type:

```
chmod +x /home/rt/rtorrent_server.sh
sudo /home/rt/rtorrent_server.sh rt
```

I have to mention that i use the repositories of HostNoc (UK), could it cause my installation problems? It´s hard to understand that when other users over this thread run & install all without any problem, ):P

Thanks for your help bro

---

### Post by CyberAngel on 2011-03-11
> **conkyrc said:**
> Ok, all rtorrent paths & configs are now removed, again thanks for your fast anwser & useful information.

Now i would like to offer you a custom quote, as a linux user i always try to learn and fix all the problems i usually have with it. All we know that are a lot of nice how-to around Internet for install this manually, anyway i will love to know why i can´t install and run properly this script under my box.

About the box, i will be glad of share my dedicated (Will be used as plain seedbox rTorrent+FTP without GNOME/KDE or any kind of graphical interface, it has 500GB of HDD @ 100Mbps [5TB Bandwitdh per month] and i haven´t used it a lot during the last days. It has a default Ubuntu v10.04 x32 OS.

Before start the installation process, i create a new user called rt, after that i put them into the sudoers file. I uploaded the rtorrent_server.sh script and type:

```
chmod +x /home/rt/rtorrent_server.sh
sudo /home/rt/rtorrent_server.sh rt
```

I have to mention that i use the repositories of HostNoc (UK), could it cause my installation problems? It´s hard to understand that when other users over this thread run & install all without any problem, ):P

Thanks for your help bro

Now it's weird to say....
Do you see any step failing in the script?
Any error in the output when the script runs?

A good way to debug this is to go step by step and do everything the script does by hand just by copy/paste commands from within the script.

---

### Post by gu3 on 2011-04-12
fresh ubuntu server 10.10 amd64

installed basic SSH and LAMP

> **[13.04.2011 04:58:24] WebUI started.**
**[13.04.2011  04:58:24] Bad link to rTorrent. Check if it is really running. Check  $scgi_port and $scgi_host settings in config.php and scgi_port in  rTorrent configuration file.**
**[13.04.2011 04:58:24] rssurlrewrite: Plugin will not work. It require existence of plugin(s) rs**cant see the whole output in putty but almost at the end of the script:
> Syntax error on line 1 of /etc/apache2/sites-enabled/rutorrent:
Invalid command 'SCGIMount', perhaps misspelled or defined by a module not included in the server configuration
Action 'configtest' failed.
The Apache error log may have more information.
   ...fail!
cannot find rtorrent binary in PATH /usr/bin:/usr/local/bin:/usr/local/sbin:/sbi n:/bin:/usr/sbinapache error log:
> [Wed Apr 13 04:56:37 2011] [notice] Apache/2.2.16 (Ubuntu) configured -- resuming normal operations
[Wed Apr 13 04:57:07 2011] [notice] caught SIGTERM, shutting down
[Wed Apr 13 04:57:13 2011] [notice] Apache/2.2.16 (Ubuntu) configured -- resuming normal operations
[Wed Apr 13 04:57:21 2011] [notice] Graceful restart requested, doing restart
[Wed Apr 13 04:57:21 2011] [notice] Apache/2.2.16 (Ubuntu) configured -- resuming normal operations
[Wed Apr 13 04:57:27 2011] [notice] caught SIGTERM, shutting down
[Wed Apr 13 04:57:28 2011] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.3 with Suhosin-Patch configured -- resuming normal operations


---

### Post by gu3 on 2011-04-12
and i found this 

[http://forums.rutorrent.org/index.php?topic=95.0](http://forums.rutorrent.org/index.php?topic=95.0)

after [FONT=monospace]: [/FONT]apt-get install libapache2-mod-scgi
> 
root@user:/var/log/apache2# /etc/init.d/apache2 restart
Syntax error on line 1 of /etc/apache2/sites-enabled/rutorrent:
Invalid command 'SCGIMount', perhaps misspelled or defined by a module not included in the server configuration
Action 'configtest' failed.
The Apache error log may have more information.
   ...fail!
going to test more on a fresh install with lighttpd tomorrow

---

### Post by gu3 on 2011-04-13
with lighttpd i get this error

> ./rtorrent_server.sh: line 171: /etc/apache2/sites-available/rutorrent: No such file or directory
./rtorrent_server.sh: line 174: a2ensite: command not found

Please enter a password for user "user" to access the web ui
./rtorrent_server.sh: line 177: htpasswd: command not found
apache2: unrecognized service
cannot find rtorrent binary in PATH /usr/bin:/usr/local/bin:/usr/local/sbin:/sbin:/bin:/usr/sbin

it works in the browser but i still get 
> [13.04.2011 17:39:14] WebUI started.
[13.04.2011  17:39:14] Bad link to rTorrent. Check if it is really running. Check  $scgi_port and $scgi_host settings in config.php and scgi_port in  rTorrent configuration file.
[13.04.2011 17:39:14] rssurlrewrite: Plugin will not work. It require existence of plugin(s) rss

im just going to compile it manually now, ty for the script anyway

---

### Post by CyberAngel on 2011-04-13
> **gu3 said:**
> with lighttpd i get this error

it works in the browser but i still get 
im just going to compile it manually now, ty for the script anyway

The script won't work with Ubuntu 10.10....
Only 10.04.

Check the first post once more ;)

---

### Post by kufra on 2011-04-29
i bumped into some problems with this script.

i ran it with my mainuser and almost everything worked out of the box, except trafic plugin. the plugin does not show any graphs. is there something you are aware of?

wooh? all of a sudden it's working... sorry guys having same problem i have no clue what i did change. i did some chmod but eventually changed it back, ohh i actually tried

```
http://server/rutorrent/php/initplugins.php
```
but if this made the trick alot of other plugins should not work aswell?

---

### Post by CyberAngel on 2011-04-29
> **kufra said:**
> i bumped into some problems with this script.

i ran it with my mainuser and almost everything worked out of the box, except trafic plugin. the plugin does not show any graphs. is there something you are aware of?

wooh? all of a sudden it's working... sorry guys having same problem i have no clue what i did change. i did some chmod but eventually changed it back, ohh i actually tried

```
http://server/rutorrent/php/initplugins.php
```
but if this made the trick alot of other plugins should not work aswell?

Sorry....
I don't have a clue about it :(

---

### Post by kufra on 2011-04-29
no problem then it's probably nothing wrong with your script. :D

it's actually working right now, so something i did fixed the problem. thx for awsome script btw!

---

### Post by belkira on 2011-05-17
> **gu3 said:**
> and i found this 

[http://forums.rutorrent.org/index.php?topic=95.0](http://forums.rutorrent.org/index.php?topic=95.0)

after [FONT=monospace]: [/FONT]apt-get install libapache2-mod-scgi
going to test more on a fresh install with lighttpd tomorrow

After you have installed it you still need to enable it:

```
sudo a2enmod scgi
```

then reload apache

```
sudo service apache2 reload
```

---

### Post by binkles on 2011-05-27
> **CyberAngel said:**
> The <username> has to be [SIZE=2]**a valid system user with an id of 1000 or more. **[/SIZE]The default one created during ubuntu installation will do fine ;)


I'm not sure what this means, im running 10.04 server and am logged in as root in putty

---------------------------------------------------------------------------------------------------------
[COLOR=Red][B]
EDIT:[/B][/COLOR]

adduser fixed that, then i found out wget wasnt installed..lol..fixed that now too.

---------------------------------------------------------------------------------------------------------

---

### Post by binkles on 2011-05-30
what would happen if i run [COLOR=Sienna]**sudo do-release-upgrade** [COLOR=Black]?

would it break rtorrent?
[/COLOR][/COLOR]

---

### Post by CyberAngel on 2011-05-30
> **binkles said:**
> what would happen if i run [COLOR=Sienna]**sudo do-release-upgrade** [COLOR=Black]?

would it break rtorrent?
[/COLOR][/COLOR]

Haven't tried it but I am pretty sure it would, as rtorrent in the official repositories is not compiled against the xmlrpc libraries.

---

### Post by mizifih on 2011-06-23
[B][CyberAngel]("http://ubuntuforums.org/member.php?u=56029"),
[/B]
First I want to thank you for this awesome script. It really make our  (at least mine) life easier. My only problem... I mean, it's not  actually a problem, but the only feature that I miss is the possibility  to access remotely with my android phone. I was used to use Transdroid,  but at the config it asks me some info that I don't have a clue where  I'm supposed to get it. do you know any Android App that supports/access  ruTorrent?

Thanks for everything. Keep being awesome ;)

---

### Post by tjy on 2011-07-10
I can't get this to work :(

I get the old

```
[21.01.2011 20:53:48] WebUI started.
[21.01.2011 20:53:48] Bad link to rTorrent. Check if it is really running. Check $scgi_port and $scgi_host settings in config.php and scgi_port in rTorrent configuration file.
[21.01.2011 20:53:48] rssurlrewrite: Plugin will not work. It require existence of plugin(s) rss
```

...it looks like the script is not able to do the chowns and the chmods, though I did run it as root.

Que pasa?

---

### Post by rocker2344 on 2011-07-21
> **kis2a said:**
> thanks for this ,


You are not possible to mod this for multiple user please ?

Work perfectly for one user , 

one solution for add multiple user ?

;)

I have gone ahead and done this with CyberAngel's script but made to work with ispconfig aswell (this was my goal) i can work on one that works with out is (a base ubuntu install). 

it has been modded only run the install script once

but for now 
```
./rtorrent_server
```
let it install
then
```
addrtoruser <user> <port> <client> <web>
```
to start/stop a user run
```
/etc/init.d/rtorrentInit.sh <start|stop|restart> <user>
```
Get it here
[http://www.aditlfai.com/rtorrent.html]("http://www.aditlfai.com/rtorrent.html")
It will not break an ubuntu system.
rtorrent just might not work like some other people who are unlucky

***UPDATE!!!****
added
```
removertoruser
```
***1.9 update****
This is not done, it works but does not have the ui i said i would put.
added a ```
--upgrade
```
flag
it will now install on ubuntu 10.04+ servers, if a deiban user wants to test, they are free too.
links located at [http://aditlfai.com/beta.html](http://aditlfai.com/beta.html)

---

### Post by newbiefly on 2011-07-22
i like it!  i also found this:
[http://surfnet.dl.sourceforge.net/project/autodl-irssi/readme.txt]("http://surfnet.dl.sourceforge.net/project/autodl-irssi/readme.txt")
```
cd
wget --no-check-certificate -O autodl-setup http://sourceforge.net/projects/autodl-irssi/files/autodl-setup/download
sudo sh autodl-setup
```
and now i have rutorrent with rss and autodl-irssi plugins a great fall back in case usenet gets too weird or costly.:guitar:

---

### Post by CyberAngel on 2011-07-22
> **rocker2344 said:**
> I have gone ahead and done this with CyberAngel's script but made to work with ispconfig aswell (this was my goal) i can work on one that works with out is (a base ubuntu install). 

it has been modded only run the install script once

but for now 
```
./rtorrent_server
```
let it install
then
```
addrtoruser <user> <port> <client> <web>
```
to start/stop a user run
```
/etc/init.d/rtorrentInit.sh <start|stop|restart> <user>
```
Get it here
[http://www.aditlfai.com/rtorrent.html]("http://www.aditlfai.com/rtorrent.html")
It will not break an ubuntu 10.04 system.
rtorrent just might not work like some other people who are unlucky

Nice job man :)
That was a much requested feature that I did not have time to invest at the moment. I will update the first post and refer you.

---

### Post by rocker2344 on 2011-07-22
I have updated it
Now includes a 
```
removertoruser
```
command
also there are two versions, the ISPconfig (still working on webui intergration)
and the Stock ubuntu (will make a web ui for that one but it is at the very end of my list)
You can get either or at [http://aditlfai.com/rtorrent.html]("http://aditlfai.com/rtorrent.html")

---

### Post by rocker2344 on 2011-08-06
Added an update to the script
[HERE]("http://ubuntuforums.org/showpost.php?p=11072942&postcount=47")
and 
[HERE]("http://aditlfai.com") as always it will update there first!

---

### Post by rocker2344 on 2011-08-24
I will make a SVN so people can join and make and commit changes to the rtorrent install script/project. expect it to be up in about 3 days
I BLAME SCHOOL!!!!!!!! speaking of school IGTG
Head over to [http://aditlfai.com]("http://aditlfai.com") to read up on info about this svn
another reason for this svn while browsing through networking/wireless i ran into this 
[http://ubuntuforums.org/announcement.php?f=336]("http://ubuntuforums.org/announcement.php?f=336")

---

### Post by rocker2344 on 2011-08-26
Most likely my last reply on this thread.
Started GIT repo (not svn) and want to change the name to RUadmin
(since it does more the the first script by cyberangel)
Check [http://aditlfai.com](http://aditlfai.com) to get in on all the info

---

### Post by FannyMae on 2011-09-09
hi.
the script saved my time. really appreciated.
so, as i have plenty of time now to test things, i re-install all with these modifications.
nothing important as you did but just to try and it works too so ... i'm just happy right now.

```
MD5SUM_RUTORRENT_ORIG="ef678b8209e68a036ebf82c7a982aad6"
MD5SUM_PLUGINS_ORIG="b17f17f535c7e86ede404913f6fd3fbb"
```and this too, as well :

```
$WGET http://rutorrent.googlecode.com/files/rutorrent-3.3.tar.gz -O /tmp/rutorrent.tar.gz
$WGET http://rutorrent.googlecode.com/files/plugins-3.3.tar.gz -O /tmp/plugins.tar.gz
```and i tried all of this with a fresh install (Ubuntu Server 10.04.2 LTS 64).

i wonder now howto get on my seedbox as before (via ssh).
could it be something you may implement on your script ?

anyway, thanks for your work.
--
Fanny

---

### Post by mizifih on 2011-09-29
Thank you so very much! I'm  a newbe and this script saves my life! Thank you, thank you, thank you....

---

### Post by rocker2344 on 2011-09-29
> **FannyMae said:**
> hi.
the script saved my time. really appreciated.
so, as i have plenty of time now to test things, i re-install all with these modifications.
nothing important as you did but just to try and it works too so ... i'm just happy right now.

```
MD5SUM_RUTORRENT_ORIG="ef678b8209e68a036ebf82c7a982aad6"
MD5SUM_PLUGINS_ORIG="b17f17f535c7e86ede404913f6fd3fbb"
```and this too, as well :

```
$WGET http://rutorrent.googlecode.com/files/rutorrent-3.3.tar.gz -O /tmp/rutorrent.tar.gz
$WGET http://rutorrent.googlecode.com/files/plugins-3.3.tar.gz -O /tmp/plugins.tar.gz
```and i tried all of this with a fresh install (Ubuntu Server 10.04.2 LTS 64).

i wonder now howto get on my seedbox as before (via ssh).
could it be something you may implement on your script ?

anyway, thanks for your work.
--
Fanny

To get on the Cli version simply ssh to the user started with the command /etc/init.d/rtorrentInit.sh
so 
```
ssh user@host
screen -x
```

You might need to change the password of the user
so ```
sudo passwd user
```
in the command prompt

to exit the screen with out killing rtorrent
```
ctrl a+d
```

---

### Post by mizifih on 2011-10-24
Hi there! I've been using this script for a log time, never had any problem. I had to make some changes on my computer and now I'm having this issue, not a problem per say.

since my HDD is not handling the amount of downloaded data, I had to plug a External USB HDD. No problem doing that, same as Windows (I'm mostly a Windows user). I have changed some folders/directories on rutorrent configuration, rtorrent+rutorrent are still downloading and seeding my files but now I can't use the 'get data' function when I right click a file on a selected torrent from the list. It says 'Web server user can't access the data on this torrent.

I tried changing permission with chown and chmod but I didn't had any success. I have restarted apache service but I keep getting this message, doesn't matter what I do.

Could you help me with that? Giving me the command I should use to effectively change the permissions (what and where)?

Thanks a bunch for this script ;)

Keep :guitar: !

---

### Post by CyberAngel on 2011-10-24
> **mizifih said:**
> Hi there! I've been using this script for a log time, never had any problem. I had to make some changes on my computer and now I'm having this issue, not a problem per say.

since my HDD is not handling the amount of downloaded data, I had to plug a External USB HDD. No problem doing that, same as Windows (I'm mostly a Windows user). I have changed some folders/directories on rutorrent configuration, rtorrent+rutorrent are still downloading and seeding my files but now I can't use the 'get data' function when I right click a file on a selected torrent from the list. It says 'Web server user can't access the data on this torrent.

I tried changing permission with chown and chmod but I didn't had any success. I have restarted apache service but I keep getting this message, doesn't matter what I do.

Could you help me with that? Giving me the command I should use to effectively change the permissions (what and where)?

Thanks a bunch for this script ;)

Keep :guitar: !

Well... To tell the truth, I haven't played a lot with rtorrent and rutorrent. I just made this script back then to automate the installation cause I wanted to use it. Other than that I don't have a clue on how rtorrent and rutorrent works :P

I guess for something like this it would be better if you ask rtorrent forums. The only thing comes to my mind is the disk file system. I guess your external hard drive uses the NTFS filesystem.... I have seen some weird behaviour sometimes with NTFS disks and permissions under Linux.

---

### Post by mizifih on 2011-10-24
> **CyberAngel said:**
> Well... To tell the truth, I haven't played a lot with rtorrent and rutorrent. I just made this script back then to automate the installation cause I wanted to use it. Other than that I don't have a clue on how rtorrent and rutorrent works :P

I guess for something like this it would be better if you ask rtorrent forums. The only thing comes to my mind is the disk file system. I guess your external hard drive uses the NTFS filesystem.... I have seen some weird behaviour sometimes with NTFS disks and permissions under Linux.

Yeah, it's NTFS. I'll try hooking up this USB HDD on my Windows computer and see if I can change the permissions somehow.

Thanks for the heads up!

---

### Post by bruckwine on 2011-11-30
Thanks a lot Cyber Angel - you saved me hours (days?) of headaches :D

---

### Post by CyberAngel on 2011-12-01
> **bruckwine said:**
> Thanks a lot Cyber Angel - you saved me hours (days?) of headaches :D

Happy to know :D

---

### Post by DroidVPN on 2011-12-01
> **rocker2344 said:**
> Added an update to the script
[HERE]("http://ubuntuforums.org/showpost.php?p=11072942&postcount=47")
and 
[HERE]("http://aditlfai.com") as always it will update there first!

Wow! Thanks for sharing your script.

---

### Post by baz1337 on 2012-01-27
This is simply awsome!

---

### Post by FuuYuu on 2012-02-08
installations was flawless and painless.

---

### Post by mushroomblue on 2012-03-24
all script links are not working as of 3/24/2012 at least.

---

### Post by CyberAngel on 2012-03-25
> **mushroomblue said:**
> all script links are not working as of 3/24/2012 at least.

I guess you are talking about rocker2344's scripts, right?
Because the attached script in the first post, must be working fine.

---

### Post by FuuYuu on 2012-03-25
OK I have a VPS with 10.4.3 LTS installed Apache2 is installed. 
Will this script try and re-install Apache2 or will it just proceed if it sees it.

Sorry I am such a nube with such a question.

---

### Post by CyberAngel on 2012-03-25
> **FuuYuu said:**
> OK I have a VPS with 10.4.3 LTS installed Apache2 is installed. 
Will this script try and re-install Apache2 or will it just proceed if it sees it.

Sorry I am such a nube with such a question.

It will issue the apt-get install command and if it is already installed, it will just go on. This is the behaviour of apt-get.

---

### Post by FuuYuu on 2012-03-25
> **CyberAngel said:**
> It will issue the apt-get install command and if it is already installed, it will just go on. This is the behavious of apt-get.

OK this server came as a default with only a root log in. I created a user but haven't managed to add them to the sudoers list yet.
Can I run this script as su and have it set up rutorrent with the proper directories in that users space?

---

### Post by FuuYuu on 2012-03-25
I got the following at the end of the install. 

```
Adding password for user flamebait
 * Restarting web server apache2                                                                                                       * We failed to correctly shutdown apache, so we're now killing all running apache processes. This is almost certainly suboptimal, so please make sure your system is working as you'd expect now!
 ... waiting Syntax error on line 1 of /etc/apache2/sites-enabled/rutorrent:
Invalid command 'SCGIMount', perhaps misspelled or defined by a module not included in the server configuration
                                                                                                                               [fail]
cannot find rtorrent binary in PATH /usr/bin:/usr/local/bin:/usr/local/sbin:/sbin:/bin:/usr/sbin

Installation was succesful
You can now navigate to http://127.0.0.1/rutorrent and login using user: flamebait and the password you provided.

``` 

Can't connect via htpp:/remote-server-ipdddress/rutorrent. Not sure how to proceed.
Can't start rutorrent "command not found"

---

### Post by CyberAngel on 2012-03-26
> **FuuYuu said:**
> I got the following at the end of the install. 

```
Adding password for user flamebait
 * Restarting web server apache2                                                                                                       * We failed to correctly shutdown apache, so we're now killing all running apache processes. This is almost certainly suboptimal, so please make sure your system is working as you'd expect now!
 ... waiting Syntax error on line 1 of /etc/apache2/sites-enabled/rutorrent:
Invalid command 'SCGIMount', perhaps misspelled or defined by a module not included in the server configuration
                                                                                                                               [fail]
cannot find rtorrent binary in PATH /usr/bin:/usr/local/bin:/usr/local/sbin:/sbin:/bin:/usr/sbin

Installation was succesful
You can now navigate to http://127.0.0.1/rutorrent and login using user: flamebait and the password you provided.

``` 

Can't connect via htpp:/remote-server-ipdddress/rutorrent. Not sure how to proceed.
Can't start rutorrent "command not found"

How have you ran the script?
Using sudo?
Are you sure that all of the packages got installed during the installation process?
Have you seen any errors before reaching the end of the script?

I see two obvious errors there:

```
Invalid command 'SCGIMount', perhaps misspelled or defined by a module not included in the server configuration
                                                                                                                               [fail]
cannot find rtorrent binary in PATH /usr/bin:/usr/local/bin:/usr/local/sbin:/sbin:/bin:/usr/sbin
```

This means that something most probably went wront with the installation of the packages.

---

### Post by swcrazyfan on 2012-04-14
> **CyberAngel said:**
> How have you ran the script?
Using sudo?
Are you sure that all of the packages got installed during the installation process?
Have you seen any errors before reaching the end of the script?

I see two obvious errors there:

```
Invalid command 'SCGIMount', perhaps misspelled or defined by a module not included in the server configuration
                                                                                                                               [fail]
cannot find rtorrent binary in PATH /usr/bin:/usr/local/bin:/usr/local/sbin:/sbin:/bin:/usr/sbin
```

This means that something most probably went wront with the installation of the packages.

I got this same issue. I can't figure out how to get past this.

---

### Post by CyberAngel on 2012-04-14
> **swcrazyfan said:**
> I got this same issue. I can't figure out how to get past this.

Have you ran the script in am Ubuntu 10.04? I haven't tried it in any other version of Ubuntu and I am pretty sure that it will not work, because as I see the ppa repository I used for rtorrent supports only Karmic and Lucid ([https://launchpad.net/~patricksissons/+archive/rtorrent](https://launchpad.net/~patricksissons/+archive/rtorrent)).

Have you ran the script with sudo like this?: 
```
sudo ./rtorrent_server.sh <your_user_name>
```

Run this command in the command line and try to run the script again:
```
sudo add-apt-repository -y ppa:patricksissons/rtorrent
```

---

### Post by imasickboy on 2012-07-19
```

cannot find rtorrent binary in PATH /usr/bin:/usr/local/bin:/usr/local/sbin:/sbin:/bin:/usr/sbin
```

I have not used this script, however, that problem should be easily remedied:

```
sudo nano /etc/ld.so.conf
```

add line:
```
include /usr/local/lib
```

then:
```
sudo ldconfig
```

Now rtorrent should start.

---

### Post by mizifih on 2012-10-09
> **rocker2344 said:**
> I have gone ahead and done this with CyberAngel's script but made to work with ispconfig aswell (this was my goal) i can work on one that works with out is (a base ubuntu install). 

it has been modded only run the install script once

but for now 
```
./rtorrent_server
```
let it install
then
```
addrtoruser <user> <port> <client> <web>
```
to start/stop a user run
```
/etc/init.d/rtorrentInit.sh <start|stop|restart> <user>
```
Get it here
[http://www.aditlfai.com/rtorrent.html]("http://www.aditlfai.com/rtorrent.html")
It will not break an ubuntu system.
rtorrent just might not work like some other people who are unlucky

***UPDATE!!!****
added
```
removertoruser
```
***1.9 update****
This is not done, it works but does not have the ui i said i would put.
added a ```
--upgrade
```
flag
it will now install on ubuntu 10.04+ servers, if a deiban user wants to test, they are free too.
links located at [http://aditlfai.com/beta.html](http://aditlfai.com/beta.html)

Where can we download your script? Is it working yet?

---

### Post by mizifih on 2012-10-09
It's not working here. It says "Installation was succesful", told me to restart apache2, I did, but it´s not working, "bad link to rtorrent" message.

Installed using
```
chmod +x rtorrent_server.sh
sudo ./rtorrent_server.sh <username>
```

Running Ubuntu **10.04.4** LTS

**apt-cache policy rtorrent**
```
rtorrent:
  Installed: 0.8.9-0ubuntu0
  Candidate: 0.8.9-0ubuntu0
  Version table:
 *** 0.8.9-0ubuntu0 0
        500 http://ppa.launchpad.net/patricksissons/rtorrent/ubuntu/ lucid/main Packages
        100 /var/lib/dpkg/status
     0.8.6-1 0
        500 http://ubuntu.mirrors.ovh.net/ftp.ubuntu.com/ubuntu/ lucid/universe Packages
```

It's also acusing a "rssurlrewrite: plugin will not work. It require existence of plugin(s) rss".

---

### Post by CyberAngel on 2012-10-11
> **mizifih said:**
> ...It's also acusing a "rssurlrewrite: plugin will not work. It require existence of plugin(s) rss".

Does this mean that you can see the web interface of rutorrent?

---

### Post by mizifih on 2012-10-11
> **CyberAngel said:**
> Does this mean that you can see the web interface of rutorrent?

I can see it, but it's very limited, with option button (with very limite options avaliable) and also says that rtorrent was not running or not responding. I could see some tabs on the bottom part of the screen, not only registry tab, but that's pretty much all I could see.

So, I could see the WebUI, was asked for password to access it, but it was not working with rtorrent at all.

But I found another script, and it's been working, so far. So don't get bothered with this ;)

We're cool ;)

I really appretiate your time and effort. I used your script a lot in the past, A LOT! I mean, past... wrong choice of word, I was using it 'til day before yesterday ;)

Thank you.

---

### Post by Nice boy on 2013-03-11
hey guys where i can find the script ?!! is it the rtorrent_server.sh ?!! in the attatch

---

### Post by reitak on 2013-11-05
when i run .sh i got error

./rtorrent_server.sh: line 51: syntax error near unexpected token `fi'
./rtorrent_server.sh: line 51: `        fi fi WGET=$(whereis wget | cut -d" " -f2) MD5SUM=$(whereis md5sum | cut -d" " -f2) USER=$1 USER_HOME=$(cat /etc/passwd '

---

### Post by CyberAngel on 2013-11-05
> **reitak said:**
> when i run .sh i got error

./rtorrent_server.sh: line 51: syntax error near unexpected token `fi'
./rtorrent_server.sh: line 51: `        fi fi WGET=$(whereis wget | cut -d" " -f2) MD5SUM=$(whereis md5sum | cut -d" " -f2) USER=$1 USER_HOME=$(cat /etc/passwd '

It looks like you have modified the script?

This line should be 65 and not 51.

Try to re-download and run it again.

---

