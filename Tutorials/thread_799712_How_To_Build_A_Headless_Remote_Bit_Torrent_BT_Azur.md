---
title: "How To Build A Headless Remote Bit Torrent BT Azureus NAS Samba Webserver With FTP"
date: 2008-05-19
forum: Tutorials
---

### Post by cackles on 2008-05-19
**Updated for 10.10**

OK, totally upgraded after nearly three years. This is now a SAMBA sharing, Bit Torrent, NAS, Webserving, remote access headless server. You can start torrents downloading from your smart phone and download them to a device via a simple webpage or use the mapped drive from your LAN.

Things have changed since I first wrote this and I've only ran this install 4 or 5 times, if something is typed up wrong, lemme know. I know I need to overhaul the Azureus Daemon. This works with XP, Vista and Win7.

The machine I have attached now is a P4 2.4 with 2GB RAM, 300GB system disk and 2 x 1.5TB storage.

Old post with updated 

Your guide to a DIY BT NAS SAMBA server remote controlled by Windows XP / Web browser.

 

Seems I'll need to format it better at a later date.

 

[COLOR="Red"]Updated again, I had to remove about 5000 words to get it into another forum lol. I will add the ftp via 

vsftp for samba users and webserver, though you shouldnt really need since I can access my samba as a network drive from 

anywhere and the tuts are clear enough for ftp usage. The ftp part, once its refined will cover users having home 

directories and being able to access the torrents, or whichever way you want it. I also added 5 beeps on startup, since 

this is headless and you may want to know when its finished booting.

I also use rc.local which I havent seen any of in any tuts, being a newb I dunno if its the done thing but as far as Im 

concerned its there to be used.

[/COLOR]


This has auto resume, ssh and anything else you might need for a full setup. This is how I have setup a shared resource 

for torrents and files. Basically you can tell it to download, everyone can access it and you can switch any other 

computers on your network off and leave it to download. Its a NAS, Bit Torrent client, webserver and if you add it in 

RAID/backup. Theres also all the other possibilities that go with Ubuntu but heres the quick 'n' dirty NAS BT client 

version. If you add in a dynamic IP redirect service you could queue your torrents from anywhere in the world, even using 

a mobile phone.

You can use any old rubbish and fire a couple of big drives in there, even go as far as getting an IDE to SATA to get the 

best. This is what I used, since I cant afford £250 for just an enclosure that actually does less that this old junk. 

Duron 900
Old iWill RAID mobo
512MB RAM
64MB something ancient AGP video card
30GB HDD thats actually 9 years old and I remember buying it 9 years ago and I have no idea how it turned up
[Ubuntu 8.04 LTS Server Edition]("http://www.ubuntu.com/getubuntu/download") which is free anyway

Now all I need are a couple of big disks :) Right now Im thinking 2 x 1TB and I wonder, if this is archived and read in 2 

years how 2TB total sounds lol.

This 'guide' assumes your network is already setup correctly, your client machines are XP and you, like me, have little 

experience with any of this. This is my 2nd day (less than 20hrs) with Ubuntu, so difficulty level is set to easy.

You may run into trouble and need to open up ports on your router, generally the ports you are working on are the ones 

that need opened/forwarded/virtual servered. Your gonna need the instruction manual for that if you havent done it before 

:)

If running Windows 7 you will need to right click and 'Run as administrator' putty and xming (OK John?).

I wont go into the basic obvious setup stuff unless its referred to later.

```
Hostname: The name you want to call your box (I sometimes refer to it as yourboxname).

Guided - Use entire partition.

Username and password: This will be your main account for logging on and doing 'stuff'.


```

Now go download [PuTTY]("http://www.chiark.greenend.org.uk/~sgtatham/putty/") for windows while waiting and after 

reboot login using the Username and password from setup like this.

Start PuTTY and in the Hostname/IP box type the name you gave your box earlier, dont hit return yet though.
Click SSH > X11 > Tick Enable X11 forwarding and in X display location put 127.0.0.1

Go back to the sessions page and under Saved Sessions put in your box name and then hit SAVE. Now you can hit open and 

connect.

When using putty you can copy from text in Windows and just a right click in PuTTY will paste it. If you highlight in 

PuTTY it automatically copies.

Any code for commands you should enter one line at a time. If its a config file you can copy and paste it all in.

Make your servers IP static (optional but necessary if you want to access webpages and torrent client from the internet):

Check your current IP and settings:

```
ifconfig]
/CODE

From this you will get your current IP. For example 'inet addr:192.168.1.4'. When you set a static IP you are as well to 

use the one assigned if you are unsure. Just copy the '192.168.1.4' part from your ifconfig. The gateway is your routers 

IP. If you dont know it, check the manual. It is the same as the login page for your routers configs.

[CODE]sudo cp /etc/network/interfaces /etc/network/interfaces.bak
sudo nano /etc/network/interfaces

```

You want the file to look like the one below. DHCP is edited to STATIC and a few lines are added. It is IMPORTANT you 

keep the eth# the same as it is, it is your network adapter.

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet static
address 192.168.1.4
netmask 255.255.255.0
gateway 192.168.1.1

```

Reboot your machine and make sure you can still connect:

```
sudo reboot -h now

```

Still works? 

Put these commands in:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install openssh-server
sudo apt-get install mysql-server mysql-client
sudo apt-get apache2
sudo apt-get php5 libapache2-mod-php5
sudo /etc/init.d/apache2 restart
sudo apt-get install xauth
sudo apt-get install azureus
sudo apt-get install screen
sudo apt-get install beep
sudo apt-get install samba smbfs
sudo apt-get install mediatomb


```

Let's check the webserver is running. In your browser go to [http://yourboxname](http://yourboxname)

In PuTTY lets make a shared folder called shared that everyone can eventually use:

```
sudo mkdir /shared
sudo chmod 0777 /shared
```

Now lets backup and remake the config file for samba:

```
sudo mv /etc/samba/smb.conf /etc/samba/smb.conf.bak
sudo nano /etc/samba/smb.conf
```

Paste this in:

```
[global]
; General server settings
netbios name = hostname
server string = ishare
workgroup = MSHOME
announce version = 5.0
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_$

passdb backend = tdbsam
security = user
null passwords = true
username map = /etc/samba/smbusers
name resolve order = hosts wins bcast

wins support = yes

printing = CUPS
printcap name = CUPS

syslog = 1
syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
; valid users = %S
; create mode = 0600
; directory mode = 0755
; browseable = no
; read only = no
; veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
;path = /var/lib/samba/netlogon
;admin users = Administrator
;valid users = %U
;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
;path = /var/lib/samba/profiles
;valid users = %U
;create mode = 0600
;directory mode = 0700
;writeable = yes
;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
path = /var/lib/samba/printers
browseable = yes
guest ok = yes
read only = yes
write list = root
create mask = 0664
directory mask = 0775

[printers]
path = /tmp
printable = yes
guest ok = yes

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
;path = /media/cdrom
;browseable = yes
;read only = yes
;guest ok = yes

[Share Name]
path = /shared
browseable = yes
read only = no
guest ok = no
create mask = 0644
directory mask = 0755
; force user = yourlogin
; force group = yourlogin
```


Parts to change

```
[global]
; General server settings
netbios name = hostname <- The Hostname of your box
server string = ishare <- A description for your box
workgroup = MSHOME <- The workgroup your computers are on, this is the most common XP

[Share Name] <------------------------- This is what it will be called on the network 
path = /shared <- The shared folder you made
browseable = yes
read only = no
guest ok = no
create mask = 0644
directory mask = 0755
; force user = yourlogin <- I have these commented out, if at the end yours doesnt work 
; force group = yourlogin <- delete both the ; and put your PuTTY/root login name there
```

Press ```
control + x
``` to save then yes etc. to exit.

Restart Samba:

```
sudo restart smbd
```

Add a pass to your own samba logon details, the pass can be different from Windows or your box:

```
sudo smbpasswd -L -a yourlogin
sudo smbpasswd -L -e yourlogin
```

Add user logons so everyone/all the computers can get access to the share, replace newuser with the username you desire 

and the new smb password thats requested with one you want:

```
sudo useradd -s /bin/true newuser
sudo smbpasswd -L -a newuser
sudo smbpasswd -L -e newuser
```

Done this way so that Windows isnt storing my boxes root user details. 

Back to XP and in 'My Computer' goto Tools > Map Network Drive
Pick a letter
Click on Connect using a dofferent username. Now in there put in one of the logins you just created under samba, ok it 

and then for the folder enter \\boxhostname\Share Name hit finish and it should take you right in. Remember the share 

name is the one in [brackets] from earlier.

And thats your shared space.

You actually probably need to give your box a sudo reboot about now, youve essentially just changed what network it is on 

etc. The default it is installed with is workgroup and xp go for MSHOME.


Now get the torrent client up and running, for this we need [URL="http://sourceforge.net/projects/xming/"]XMing and its 

fonts[/URL]so our windows machine can connect for a quick log on to do some setting up before we put it to bed. Remember the fonts, they are on the 'Files' page.

Basically install them and then launch XMing, leave it running in the background and then its back to PuTTY. This is 

where the extra setting up and saving comes in handy from earlier. Close any PuTTY session you have and then restart one. 

After your logged on type ```
azureus
``` and up should come an Azureus GUI. This will be the only time you see 

this. Get the updates and setup your speeds, also in tools/options setup your folder in transfers so its pointing to your 

shared folder and tell it to automatically download (or is it upload)/no confirmation needed, theres only the one anyway. 

Goto the plugin installation wizard and download autostopper and azhtmlwebui. Once its installed go to tools > options > 

plugins, click on its box and configure your settings. Youll want to put a pass on it since right now anyone can log one 

and probably change to https. Once its done and settings are saved its time to close it down and make a daemon for it. 

Before we do though lets get our browsers and go to [https://yourboxname:6886/](https://yourboxname:6886/) and the Azureus webgui should 

appear and you will be able to log on, if not you have to check port settings on your router or anything that maybe 

blocking. If you get your external IP then you should be able to access it from anywhere on the planet, youll need a 

dynamic ip account at somewhere like dynip, explained later.

I couldnt find a startup feature or anything that worked so I went right ahead to try and rip off, I mean use, someone 

elses great one and that never went well at all so I made a basic one and its all you really need. This also uses a 

method I couldnt see anywhere so any and all improvements welcome, if someone could show me how to do if statements in 

this then that would be a result.

In PuTTY:

```
sudo nano /usr/share/java/azureus_daemon
```

Now in there paste:

```
#! /bin/sh

#The user that will run Azureus
AZ_USER=anybody

#Name of the screen-session
NAME=cackles_azureus_daemon

#executable files in the following paths that are perhaps needed by the script
PATH=/bin:/usr/bin:/sbin:/usr/sbin:/usr/share/java

#your path to the azureus directory, where Azureus2.jar is located
DIR=/usr/share/java/

#Description
DESC="Azureus Daemon"


set -e


case "$1" in
start)
echo "Starting $DESC: $NAME"
su $AZ_USER -c "cd $DIR; screen -dmS $NAME java -jar ./Azureus2.jar --ui=console"
su $AZ_USER -c "screen -S $NAME -X start all"
echo "Azureus Daemon Started"
;;
stop)
su $AZ_USER -c "screen -S $NAME -X quit"
echo " Daemon Has Been Stopped"
;;
check)
su $AZ_USER -c "screen -S $NAME -X show torrents all"
;;
daemons)
su $AZ_USER -c "screen -list"
;;
esac

exit 0
```

Then change anybody to your root logon name, no need for pass or anything.

```
AZ_USER=anybody
```
Control + X to get out and save that and then:

```
sudo chmod a+x /usr/share/java/azureus_daemon
```

Ok so I used the wiki one only made it run on my machine and mines also automatically resumes your torrents :)

Lets see if it works. I'm pretty sure some of its broken because the code is three years old. but we only need stop and 

start. Make sure you are in /usr/share/java/ and type:

```
sudo ./azureus_daemon start
```

That should start the server. Use your browser and goto [http://yourboxname:6886](http://yourboxname:6886) and make sure its working.

```
sudo ./azureus_daemon daemons 
```

will let you see your daemon running.

```
sudo ./azureus_daemon check
``` 

will let you see any torrents that are downloading.

```
sudo ./azureus_daemon stop
```

Stops ... There are no safeties built into this but if you play with and rack up too many daemons theres always reboot 

with no harm done :)

Now we need to get it to run at startup.

```
sudo nano /etc/rc.local
```
And make sure yours is like this:

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

sudo /usr/share/java/azureus_daemon start
beep -r 5

exit 0
```

You should have only needed to add one line for azureus, but we added two so that our headless machine beeps 5 times when 

its has started up and loaded everything. Remove the beep line if you dont want it. You can also add log on messages here 

with echo "message including the quotes". exit 0 should always be the last thing.

Reboot:

```
sudo reboot -h now

```

But you want to stream media as well?

Mediatomb time!

```
sudo cp /etc/mediatomb/config.xml /etc/mediatomb/config.xml.bak
sudo nano /etc/mediatomb/config.xml

```

There are only 3 parts of this that need changed to get it to run on the PS3 and basically anything else.

Part 1 change no to yes:

```
<ui enabled="yes"

```

Part 2 in the first yellow blob below that change no to yes:
```
<protocolInfo extend="yes"/>

```

Part 3 remove the <!-- -->:
```
<map from="avi" to="video/divx"/>

```

Now you can go to [http://yourboxname:49152](http://yourboxname:49152). Go to Filesystem. Click on shared. Click the + with the arrows around it. 

Select Inotify, Full, Recursive. Set.

But you said I can access this from anywhere! OK. Go to dyndns.com and setup a free account. Make a URL. Activate it. 

Update the IP, click on the link for the URL and update using 'my IP'.

Install this Gizmo, selecting dyndns and 'from list along with your dyndns username and pass.

```
sudo apt-get install ddclient

```

Now go into your router settings. Forward ports 80, 49152, 6886.

Cool but you can't download, meh, thats easily solved. 

```
sudo mkdir /var/www/test
sudo nano /var/www/test/.htaccess


```
In nano paste this in:

AuthUserFile  /etc/apache2/.htpasswd
AuthGroupFile /dev/null
AuthName  YouKnowWhere
AuthType Basic
require user test

```

sudo htpasswd -c /etc/apache2/.htpasswd test
sudo nano /etc/apache2/sites-available/default

```

Add this to the file after ServerAdmin webmaster@yourboxname (If you use a virtual, covered later, then you wont need 

this):

```
       <Directory /var/www/test>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
                Order allow,deny
                allow from all
        </Directory>

```

Restart Apache:

```
sudo /etc/init.d/apache2 restart

```

Make a simple webpage:
```
sudo nano /var/www/index.html

```

Remember, this is to test only and show you. Make your page look like this:
```
Test 1
<p><A HREF="test/">Test</A>

```

Time to add shared to it:

```
sudo mount -o bind /shared /var/www/test
sudo nano /etc/fstab

```

Add this line to fstab to make it 'stick':

```
/shared /var/www/test auto bind 0 0

```


```
sudo reboot -h now
```

You now have a webpage to download files from.

And that should be that!

I will a bit later about hosting multiple websites from the one machine as well as FTP, RAID and mounting another drive.

---

### Post by ndoggac on 2008-05-21
Thanks a lot for this!!  Already had Samba setup and knew what I was doing there, but the Azureus setup was just what I needed and spot on easy to follow directions.  Took about 15 minutes to setup and another 15 to migrate over my torrents/data from another machine.  Note to anyone migrating data and torrents from another machine, you will have to load up the GUI using SSH/XMing and force a recheck of all torrents (right-click menu).  Then you can daemonize the process using the included script.

Also installed safepeer and speed scheduler azureus plugins using the GUI.  Daemon script works perfectly as well...I used Webmin to create the startup script...very easy!  Web interface is great for day to day maintenance, but if you want to change any detailed settings, you have to stop the daemon process, start azureus using Xming and Putty so you can use the GUI to change options, install plugins, etc....a little bit of a pain, but won't have to do that very often.

Cackles...you rule!

---

### Post by cackles on 2008-05-27
> **ndoggac said:**
> Thanks a lot for this!!  Already had Samba setup and knew what I was doing there, but the Azureus setup was just what I needed and spot on easy to follow directions.  Took about 15 minutes to setup and another 15 to migrate over my torrents/data from another machine.  Note to anyone migrating data and torrents from another machine, you will have to load up the GUI using SSH/XMing and force a recheck of all torrents (right-click menu).  Then you can daemonize the process using the included script.

Also installed safepeer and speed scheduler azureus plugins using the GUI.  Daemon script works perfectly as well...I used Webmin to create the startup script...very easy!  Web interface is great for day to day maintenance, but if you want to change any detailed settings, you have to stop the daemon process, start azureus using Xming and Putty so you can use the GUI to change options, install plugins, etc....a little bit of a pain, but won't have to do that very often.

Cackles...you rule!




Your welcome, I wasnt sure if I was just spewing newbie rubbish but there didnt seem to be one covering this particular setup. I should go more into the detailed setup of azureus via the gui next time I update this and I'll look up the plugins you installed and add them in as well along with vsftpd that I learned about. Im also going to refine the azureus daemon script and define more clearly about stopping the daemon to install.

---

### Post by ndoggac on 2008-05-29
Cackles, I got a question for you and anyone else that may be able to help....Trying to run the speedscheduler plugin in console mode but cannot get it to startup.  I've been searching around and found this command...

set Plugin.SpeedScheduler.speedscheduler.Enabled 1

I've tried many variations of this including setEnabled with true/false, 1/0, speedschedulerPlugin., etc with no success.

if you start azureus manually in console mode (ie not a startup script), and type "set", it will give you a list of options.  You can type "set Plugin.*" and so on to see sublists.  I don't see this option or any other option to enable speedscheduler upon startup like the command I found.

I started up the GUI through Putty/Xming and the plugin starts successfully, but never starts in console mode.

Any help would be appreciated.  Thanks in advance.

---

### Post by cackles on 2008-05-30
According to the FAQ theres a problem with some versions of Azureus.

Do you have the latest version of Azureus?

---

### Post by ndoggac on 2008-05-30
<Solved>

Finally got it working....originally I had used the CVS snapshot JAR file along with the two jar files needed to run it in console mode...this always failed to load the plugins.  So I went to the regular azureus download section and downloaded the official release tarball and used that version of the Azureus2.jar file with the 2 additional jar files needed for console mode.  Worked great, loaded up my plugins successfully (Safepeer & SpeedScheduler).  Thanks for the help.

---

### Post by cackles on 2008-05-30
No probs, if you 

```
sudo apt-get install azureus
```

Azureus you get the latest version too, least I think it is. Thats what I used and it loaded my plugins so I take it does.

---

### Post by drsox1899 on 2008-06-17
I followed the sequence and it worked beautifully. Thanks.

Some questions :

If I only want to run a NAS, then I can uninstall

 xauth
 azureus
 screen
 beep

? or not ?

How do I monitor the temps of the discs etc on this ?  I can install sensors etc but how do I look at the results ?

How do I set up the box to start up and shut down on a fixed schedule - I don't want to run it 24/7 but only when I'm awake/active !  i/e 8am to 11pm

Is there a GUI alternative to working with PuTTY ?

If this is going to be a real server then how do I get it to listen to a UPS ?

Great Job  - and so easy !!

---

### Post by tvds on 2008-07-11
This tutorial ROCKS !! :guitar:

But....

There is a small error in your tutorial.

When the azereus webgui is ready you point out to go to
[https://localhost:6886/](https://localhost:6886/) 

This is wrong. As the webgui is not running on the windows machine but on the ubuntu server.
So it should be the servername or servers ip address to go to.

In my case

[https://192.168.1.175:6886/](https://192.168.1.175:6886/)

Secondly I really miss more info about the LAMP part.
No Offence but, I think this is more a bittorrent tutorial then a "Remote Bit Torrent BT Azureus NAS Samba Webserver With FTP" tutorial.

---

### Post by masuta on 2008-07-26
> **ndoggac said:**
> Cackles, I got a question for you and anyone else that may be able to help....Trying to run the speedscheduler plugin in console mode but cannot get it to startup.  I've been searching around and found this command...

set Plugin.SpeedScheduler.speedscheduler.Enabled 1

I've tried many variations of this including setEnabled with true/false, 1/0, speedschedulerPlugin., etc with no success.



I also had this problem with speedscheduler.  You were close.
Try to use:

set Plugin.SpeedScheduler.speedscheduler.enabled 1 int

Thats what worked for me.  Also note that for me is was case sens.  You will still need to either manually type out the SavedSchedule.xml or copy it from a machine with a GUI.

Cheers.

---

### Post by ejcdke on 2008-08-10
This how-to was exactly what I needed.  Thank you.  Is there a way to made the azureus_daeon executable from any location in the terminal?  I wouldn't mind being able to run it without having go to /usr/share/java/.  Thanks.

Eric

---

### Post by fox_cream on 2008-10-07
Great tutorial, but unless you are using a socks5 proxy to anonymise your downloading, there really is no point in using azureus over torrentflux on your NAS now that torrentflux 2.4 support encryption.  It's much more resource hungry and the webui for torrentflux is far superior.  However, as i am using a socks5 proxy now, I will definitely be using azureus!

@ Eric, 

make a symlink for the /usr/share/azureus folder to /usr/bin and you can run it from anywhere.

---

### Post by ndoggac on 2008-10-11
Thought maybe webmin would be a good addition to this thread.  It makes it very easy to create a startup script, and edit samba settings very quickly.

[http://www.webmin.com/deb.html](http://www.webmin.com/deb.html)

add the repository to /etc/apt/sources.list
then sudo apt-get update
then sudo apt-get install webmin

then the web interface is available at [https://hostip_or_name:10000](https://hostip_or_name:10000)

if you install new packages, make sure you refresh the modules to make their respective interfaces appear.

This has been one of the best additions to my headless server setup.

---

### Post by PHiRe2008 on 2008-10-28
WOW!!!!! Cackles all i can say is this post is legendary just helped me with my headless set up so much!!!!

---

### Post by oaxacamatt1 on 2008-12-10
hey cakles,
Is there a free alternative to Xming?  

Cheers,
Matt

---

### Post by oaxacamatt1 on 2008-12-15
Hey Cackles,
I have been plugging through the post you put up for the headless torrent server.  For the most part I have been able to duplicate your work.  But when it comes to the portion where I check the Azureus HTML gui I am unable to do so.  I have check to see if it is being affected by my firewall setup, Comodo Firewall Software, and my router.  I dont think either are the problem.  Do you have any suggestions?
Cheers,
Matt

---

### Post by ElectricBlue on 2008-12-21
@ oaxacamatt1

Xming is free.

---

### Post by ElectricBlue on 2008-12-22
My torrents never seem to start downloading. They show up in the WebUI and the GUI when I launch it but they do not start downloading. There is more than enough peers and seeds and I have forwarded the port in my router. Also, when I use"./azureus_daemon check" nothing is returned. 

What could it could be?

EDIT: I was testing the build of Azureus with the GUI and had a JRE error. I had forgotten that Java on PPC is unsupported by Sun. I will post back when/if I can resolve the Java issue.

---

### Post by Rickster888 on 2009-04-25
Hmmm I've used screen for a while and browsing this page there seems to be a mistaken understanding of what -X does.

-X is used to send "SCREEN" commands to a screen session (attached or detached), the author seems to believe it sends output to the console, it does not. 

E.g.

screen -S $NAME -X start all
screen -S $NAME -X show torrents all

Will NOT work, as start and show are not screen options/commands.

screen -S $NAME -X quit

This will work, but not because it sent the command "quit", this will work with ANY screen session. This is because this tells screen to kill window and terminate the screen session.

You probably want to do this: (stuff is a SCREEN command to send input to the input queue of the screen).

screen -S $NAME -X stuff $'start all\n'
screen -S $NAME -X stuff $'show torrents\n'

You need the $'  ' to be able to send newline across.

Other bugs bug.

1. You're check won't show you anything. It just sends the command to the detached window, nothing is shown to you.

2. Azuerus doesn't do start all without 'show torrents first', so if 
you have stopped any torrents prior to starting up azuerus you need to issue this instead.

screen -S $NAME -X stuff $'show torrents\nstart all\n'


Ricky

---

### Post by Rickster888 on 2009-04-25
See my reply to the previous post, I have explained why check doesn't work and also a work around for starting all torrents.

If you want a working check, there probably is a few ways to do it but the simplest way I can think off from the top of my head is:

# Do this as part of the start of you service.
screen -S $NAME -X logile /tmp/somelog
screen -S $NAME -X logfile flush 1

Now for the check part.
screen -S $NAME -X log
screen -S $NAME -X stuff $'show torrents\n'
sleep 5
screen -S $NAME -X log

You should now get output to a file called /tmp/somelog, which you can look at and delete as you feel like. You may need to wait more than 5 seconds, depending on how faster azuerus console responds. (without flush 1, you would have had to wait much longer).

screen is a excellent piece of software.


Ricky

> **ElectricBlue said:**
> My torrents never seem to start downloading. They show up in the WebUI and the GUI when I launch it but they do not start downloading. There is more than enough peers and seeds and I have forwarded the port in my router. Also, when I use"./azureus_daemon check" nothing is returned. 

What could it could be?

EDIT: I was testing the build of Azureus with the GUI and had a JRE error. I had forgotten that Java on PPC is unsupported by Sun. I will post back when/if I can resolve the Java issue.

---

### Post by cackles on 2009-04-26
This worked perfectly under 8.04/8.10 and until they updated to 9.04 and screen ... also azureus ... why do they need to change things? :)

I honestly appreciate any help with changing it and getting it updated, thanks Ricky.

Right now its past 5am though and Im in the middle of a wee drinky.

screen -S $NAME -X start all

still works, along with stop and daemons command, check is the only one broken with the update, but Im thinking thats down to azureus/vuze command change.

screen -S $NAME -X start all
screen 
-S shockname
$name name of screen session 
-x execute
start all command



My biggest problem is getting screen to start in -dmS / daemon mode, for some reason under 9.04 it wants a profile, which it shouldnt be asking for seeing as it is being started as a daemon. Must be a new ubuntu config. Worst case scenario is I wrtite a config file for it. I have been playing with it for a couple of days now and might tell it to 'do anything' to start a screen session. I also need to workaround for the 'show all torrents'. It did all work flawlessly though. The show all torrents isnt required anyway, I just done that for testing purposes so I suppose I can remove it. After initial setup the torrents are controlled through the web interface.

This tut will be updated by the start of next month, well Friday...ish. This is to allow for any bugs in 9.04 to be ironed out. I currently went back to 8.10. I'll also be adding the ftp dump in.

After the weekend Im going to set it up using 8.04, again, then 9.04 again, but if I remember corectly it had some issues with 8.10 to start with.

---

### Post by cackles on 2011-02-22
OK, I updated it for 10.10

---

### Post by JasonMarquez on 2012-04-23
The domain website you suggest to get a domain from no longer has a free service. I got No-IP instead. How should I adjust the settings to make it work?

---

