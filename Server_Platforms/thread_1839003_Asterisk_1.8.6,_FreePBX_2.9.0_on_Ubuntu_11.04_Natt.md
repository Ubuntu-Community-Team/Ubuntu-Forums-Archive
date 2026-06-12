---
title: "Asterisk 1.8.6, FreePBX 2.9.0 on Ubuntu 11.04 Natty"
date: 2011-09-04
forum: Server Platforms
---

### Post by tomage on 2011-09-04
Made reference to 
[http://www.pedro.kiefer.com.br/2011/02/asterisk-and-freepbx-on-ubuntu-server-10-10]("http://www.pedro.kiefer.com.br/2011/02/asterisk-and-freepbx-on-ubuntu-server-10-10")
[http://ubuntuforums.org/showthread.php?t=1753143]("http://ubuntuforums.org/showthread.php?t=1753143")

FreePBX MySQL database: asterisk
FreePBX MySQL database: asteriskcdrdb
FreePBX MySQL user: dbuser
FreePBX MySQL password: dbpassword
FreePBX Apache Virtual Host: pabx.local
Asterisk Manager interface user: admin
Asterisk Manager interface password: amp111   

Add the following two lines to your sources.list
> deb [http://packages.asterisk.org/deb](http://packages.asterisk.org/deb) natty main
deb-src [http://packages.asterisk.org/deb](http://packages.asterisk.org/deb) natty main
```
sudo vi /etc/apt/sources.list.d/asterisk.list
```
Update gpg key
```
sudo apt-key adv --keyserver pgp.mit.edu --recv-keys 175E41DF
```
Update package repository
```
sudo apt-get update
```
Install software and required dependencies
```
sudo apt-get install apache2 apache2-mpm-prefork apache2-utils asterisk asterisk-dahdi asterisk-mp3 asterisk-mysql asterisk-sounds-extra build-essential curl libapache2-mod-php5 libaprutil1-dbd-sqlite3 libaprutil1-ldap libhtml-template-perl libnet-daemon-perl linux-headers-`uname -r` mysql-server php5 php5-cli php5-gd php5-mysql php-db phpmyadmin postfix sox ssl-cert
```
[SIZE="3"]Apache[/SIZE]
Before running the install command, you have to configure your apache server. In this connfiguration we are using a virtual host because I couldn't find out how to have a seperate log file for a directiory.
We also use these directories for FreePBX 
/etc/freepbx
/var/log/freepbx
/usr/share/freepbx
In the /etc/freepbx I store the necessary vhost configuration, in /usr/share/freepbx lives the public accessible files, and /var/log/freepbx hosts the logging files.
Create the needed directories:
```
sudo mkdir /etc/freepbx
sudo mkdir /var/log/freepbx
sudo mkdir /usr/share/freepbx
```
Create the FreePBX Apache configuration file with the following contents
> <VirtualHost *:80>
    ServerName pabx.local
    ServerAlias pabx.local
    ServerAdmin [email]admin@pabx.local[/email]
    ErrorLog /var/log/freepbx/error.log
    CustomLog /var/log/freepbx/access.log combined
    DocumentRoot /usr/share/freepbx
    <Directory /usr/share/freepbx>
        Options Indexes FollowSymLinks MultiViews
        Order allow,deny
        AllowOverride All
        Allow from all
    </Directory>
</VirtualHost>
```
sudo vi /etc/freepbx/apache.conf
```
With the file created, add the vhost to the sites-enabled directory, with:
```
sudo ln -s /etc/freepbx/apache.conf /etc/apache2/sites-available/freepbx
```
```
sudo a2ensite freepbx
```
```
sudo service apache2 reload
```
Grab the FreePBX tarball
```
wget http://mirror.freepbx.org/freepbx-2.9.0.tar.gz
```
Extract the tarball and move into the directory
```
tar zxf freepbx-2.9.0.tar.gz
cd freepbx-2.9.0
```
Now it&#8217;s time to create the database, the user used to access it, and populate the basic tables. This will create and import the basic tables to asterisk and asterisk cdr database, run this from the recently extracted directory.
```
mysqladmin create asterisk -u root -p
mysqladmin create asteriskcdrdb -u root -p
mysql -u root -p asterisk < SQL/newinstall.sql
mysql -u root -p asteriskcdrdb < SQL/cdr_mysql_table.sql
```
With the tables in-place, it's time to create the user with privileges to access and edit those tables. Open a mysql prompt with:
```
mysql -u root -p
```
On the prompt run the following queries:
```
GRANT ALL PRIVILEGES ON asterisk.* TO dbuser@localhost IDENTIFIED BY 'dbpassword';
GRANT ALL PRIVILEGES ON asterisk.* TO dbuser@127.0.0.1 IDENTIFIED BY 'dbpassword';
GRANT ALL PRIVILEGES ON asteriskcdrdb.* TO  dbuser@localhost IDENTIFIED BY 'dbpassword';
GRANT ALL PRIVILEGES ON asteriskcdrdb.* TO  dbuser@127.0.0.1 IDENTIFIED BY 'dbpassword';
flush privileges;
quit;
```
Don't forget to change the password!
Before running the install command, make a copy of /etc/asterisk/modules.conf. FreePBX rewrites the file and trashes Asterisk installation. If you restart Asterisk after installing FreePBX Asterisk dies with no message.
```
sudo cp /etc/asterisk/modules.conf ~/asterisk-modules.conf
```
Ok, we are ready to install freepbx to /usr/share/freepbx:
```
sudo ./install_amp
```
The install script will ask for some configuration data, eg. were to install freepbx (/usr/share/freepbx), sql password, asterisk password, etc. Take note of the passwords you used, you might need them later.
The output from the install script is somewhat like this:
> ...
Enter your USERNAME to connect to the 'asterisk' database:
 [asteriskuser] dbuser
Enter your PASSWORD to connect to the 'asterisk' database:
 [amp109] dbpassword
Enter the hostname of the 'asterisk' database:
 [localhost]
Enter a USERNAME to connect to the Asterisk Manager interface:
 [admin]
Enter a PASSWORD to connect to the Asterisk Manager interface:
 [amp111]   
Enter the path to use for your AMP web root:
 [/var/www/html]
/var/www/pabx.domain/public
Enter the IP ADDRESS or hostname used to access the AMP web-admin:
 [xx.xx.xx.xx] pabx.domain
Enter a PASSWORD to perform call transfers with the Flash Operator Panel:
 [passw0rd] password
Use simple Extensions [extensions] admin or separate Devices and Users [deviceanduser]?
 [extensions]
Enter directory in which to store AMP executable scripts:
 [/var/lib/asterisk/bin]
...
Restore asterisk-modules.conf file, which you backed up before installing FreePBX:
```
sudo cp ~/asterisk-modules.conf /etc/asterisk/modules.conf
```
Apache runs as www-data, Asterisk as user asterisk, so we have to change some permission to make both programs work together. First, add www-data to asterisk group:
```
sudo adduser www-data asterisk
```
Fix the permissions from amportal, add these lines to the end of /etc/amportal.conf:
> AMPASTERISKUSER=www-data
AMPASTERISKGROUP=asterisk
AMPASTERISKWEBUSER=www-data
AMPASTERISKWEBGROUP=asterisk
```
sudo vi + /etc/amportal.conf
```
At this point, after issuing the following command
```
sudo amportal start
```
I was not able to login using the admin user name and password I chose during the amportal install, at [http://pabx.local/admin](http://pabx.local/admin) 
It seemed to be a mismatched password hash in the mysql database.
The solution for me was to just recreate the hash for the password I chose and poke it into the database
I also found I couldnt enable Hidden settings and Read Only Settings from the gui, so I changed them directly from the database as well
We need to get the password hash for the password we put for the Asterisk Manager interface (amp111)
```
echo -n 'amp111' | openssl sha1
```
We will poke this into the database plus a couple of other variables. Could not login to the manager interface without it
```
mysql -u root -p dbname
```
change f4cf50302526d3ebc5726f27479a4801691359e9 to the hash you generated in the previous step
```
update ampusers set password_sha1 = 'f4cf50302526d3ebc5726f27479a4801691359e9' where username = 'admin' limit 1 ;
```
Enable some administrative features
```
update freepbx_settings set value=1 where keyword="AS_DISPLAY_HIDDEN_SETTINGS";
update freepbx_settings set value=1 where keyword="AS_DISPLAY_READONLY_SETTINGS";
update freepbx_settings set value=1 where keyword="AS_OVERRIDE_READONLY";
quit;
```
Now edit safe_asterisk, to make sure it runs on background, edit the variable BACKGROUND to zero: You need to do this everytime asterisk gets updated. It seems updates overwrite the changes you make to this file
```
sudo sed -e s/BACKGROUND=0/BACKGROUND=1/ -i /usr/sbin/safe_asterisk
```
Everything in place, time to start amportal:
```
sudo amportal start
```
We have to start amportal after booting, so call amportal start in /etc/rc.local. Edit your /etc/rc.local and add the following line before the exit 0 line.
> /usr/local/sbin/amportal start
```
sudo vi /etc/rc.local
```
Reboot your machine, and check that everything is still working. Have fun!

---

### Post by fattsammy on 2011-09-09
The install got interrupted during the ./install_amp phase and now it is totally broken.  I tried going back to the beginning with no luck.  Here is the error output:

laptop:~/freepbx-2.9.0$ sudo ./install_amp 
Checking for PEAR DB..OK
Checking for PEAR Console::Getopt..OK
Checking user..OK
Checking if Asterisk is running..running with PID: 13280..OK
Checking for /etc/amportal.conf..OK
Reading /etc/amportal.conf..OK
Checking for /etc/asterisk/asterisk.conf..OK
Reading /etc/asterisk/asterisk.conf..OK
Using asterisk as PBX Engine
Checking for Asterisk version..1.8.6.0
Checking for selinux..PHP Notice:  Undefined offset: 0 in /home/liam/freepbx-2.9.0/install_amp on line 902
OK
Connecting to database..FAILED
Try running ./install_amp --username=user --password=pass  (using your own user and pass)
[FATAL] Cannot connect to database



I then tried with the ./install_amp --username= etc., and got the same failure.

Is there any way to repair this or do I have to dump everything (mysql, apache, etc.) and start over?

Thanks for any suggestions.

---

### Post by tomage on 2011-09-12
> **fattsammy said:**
> The install got interrupted during the ./install_amp phase and now it is totally broken.  I tried going back to the beginning with no luck.  Here is the error output:

laptop:~/freepbx-2.9.0$ sudo ./install_amp 
Checking for PEAR DB..OK
Checking for PEAR Console::Getopt..OK
Checking user..OK
Checking if Asterisk is running..running with PID: 13280..OK
Checking for /etc/amportal.conf..OK
Reading /etc/amportal.conf..OK
Checking for /etc/asterisk/asterisk.conf..OK
Reading /etc/asterisk/asterisk.conf..OK
Using asterisk as PBX Engine
Checking for Asterisk version..1.8.6.0
Checking for selinux..PHP Notice:  Undefined offset: 0 in /home/liam/freepbx-2.9.0/install_amp on line 902
OK
Connecting to database..FAILED
Try running ./install_amp --username=user --password=pass  (using your own user and pass)
[FATAL] Cannot connect to database



I then tried with the ./install_amp --username= etc., and got the same failure.

Is there any way to repair this or do I have to dump everything (mysql, apache, etc.) and start over?

Thanks for any suggestions.

It seems you did not use the same mysql username and password in this step

> GRANT ALL PRIVILEGES ON asterisk.* TO dbuser@localhost IDENTIFIED BY 'dbpassword';
GRANT ALL PRIVILEGES ON asterisk.* TO dbuser@127.0.0.1 IDENTIFIED BY 'dbpassword';
GRANT ALL PRIVILEGES ON asteriskcdrdb.* TO  dbuser@localhost IDENTIFIED BY 'dbpassword';
GRANT ALL PRIVILEGES ON asteriskcdrdb.* TO  dbuser@127.0.0.1 IDENTIFIED BY 'dbpassword';
as you you did when asked during the sudo ./install_amp > Enter your USERNAME to connect to the 'asterisk' database:
[asteriskuser] dbuser
Enter your PASSWORD to connect to the 'asterisk' database:
[amp109] dbpassword

---

### Post by Rascayu67 on 2011-09-13
I've got the same problem with ./install_amp phasethe first time i put the users and passwords of the first post

Thanks

---

### Post by rubylaser on 2011-09-13
I'm all for creating your own solution and I ran my own self-rolled Deb based Asterisk PBX for years.  Since [PBXinaFlash]("http://pbxinaflash.net/") has come along, I find it hard to justify all the time to get it working, when I can have a functioning system in 10 minutes.  I need my VOIP system working, so I like having a rock solid platform to work from.  This is well tested and just works. They even have an OpenVZ image for Proxmox and a VMWare image. Just a thought :)

---

### Post by pmowry911 on 2011-09-13
> **tomage said:**
> It seems you did not use the same mysql username and password in this step


as you you did when asked during the sudo ./install_amp

My guess is they (like me) did not use the same database name.  Your sample code creates DB dbname, but the scripts reference asterisk.

---

### Post by tomage on 2011-09-14
> **pmowry911 said:**
> My guess is they (like me) did not use the same database name.  Your sample code creates DB dbname, but the scripts reference asterisk.

Yep I think you're right.

I'll change the database now in the scripts to asterisk

---

### Post by tomage on 2011-09-14
> **rubylaser said:**
> I'm all for creating your own solution and I ran my own self-rolled Deb based Asterisk PBX for years.  Since [PBXinaFlash]("http://pbxinaflash.net/") has come along, I find it hard to justify all the time to get it working, when I can have a functioning system in 10 minutes.  I need my VOIP system working, so I like having a rock solid platform to work from.  This is well tested and just works. They even have an OpenVZ image for Proxmox and a VMWare image. Just a thought :)

This makes sense, I'll check it out. Thanks

---

### Post by atka on 2011-09-18
Ok I've followed all the steps but when I get to ./install_amp I get this error
```
PHP Fatal error:  Class 'Console_Getopt' not found in /home/todd/freepbx-2.9.0/install_amp on line 546
```
any idea ho to fix it?

---

### Post by AdamH1996 on 2012-07-14
I followed all the steps which seem to be in success however once the amportal is started why can't I access [http://pabx.local/admin](http://pabx.local/admin)

It fails to load in multiple browsers which leads me to believe there is a larger underlying problem.

---

### Post by volkswagner on 2012-07-15
> **AdamH1996 said:**
> I followed all the steps which seem to be in success however once the amportal is started why can't I access [http://pabx.local/admin](http://pabx.local/admin)

It fails to load in multiple browsers which leads me to believe there is a larger underlying problem.


I believe pabx.local is specific to the machine.

Did you create the same hostname for your install?

```
hostname -f
```

Perhaps you don't have local DNS working.  Can you ssh into the machine using the hostname?
If not replace the hostname with the ip address >> [http://192.168.1.xxx/admin](http://192.168.1.xxx/admin)

The path may not match your vhost file in Apache2.  Check the DocumentRoot directive in the related vhost file.

---

### Post by darkod on 2012-07-15
I am currently in the middle of a project like this, only on Debian 6.0.5. I never managed to find any recent tutorials, so I am working on a compilation of various websites and getting close.

My installation is still only inside VBox, no phones connected etc, but I finally managed to get it done.

Few pointers I noticed:
1. Create the asterisk use like:
adduser asterisk --disabled-password --gecos "Asterisk PBX" --home /var/lib/asterisk

2. Inside /etc/apache2/envvars replace the www-data user and group with asterisk.

3. During the freepbx installation with ./install_amp DO NOT change the default login details for Asterisk Manager, leave them as admin/amp111. Many tutorials say not to leave default logins, and I support that, but my test install got confused when I changed them. Since the PBX will not be public anyway, I don't mind leaving them. In case you want to start over the install process for freepbx, you can delete the /etc/amportal.conf file and run the ./install_amp again.

4. During the freepbx install change the location of the web files from the default /var/www/html into /var/www which I believe is the apache2 default under debian. I think that should work out.

I am preparing a bash script (my first one :) ) based on an older script I found online, which can help at least with the needed packages when starting from base core debian system.

Another note, I didn't install asterisk from apt, I compiled the latest version .tar.gz.

EDIT PS: Concerning the apache2 user, there are few options. Some decide to just add the asterisk user to the www-data group, and not sure if you need to make any changes in /etc/apache2/envvars in that case. I decided to replace www-data both user and group in that file. I think it probably works better.

---

### Post by volkswagner on 2012-07-15
For a dead simple Asterisk 1.8 setup on Ubuntu or Debian check out [freedoh.net]("http://www.freedoh.net/freedoh.html") for a great install script which will get Asterisk and Freepbx up and running in about 20 minutes.

---

### Post by khemyst on 2012-10-26
This worked awesome. Thanks.

---

### Post by pbxfan on 2013-01-04
Hi all please i've just finished the setup everything is going well fixed some errors i have one problem virtual host as i can't access [http://pabx.local](http://pabx.local)

please find here my main conf files

/etc/hosts
```

127.0.0.1 localhost
127.0.1.1 ubuntu

```

latest lines of /etc/apache2/apache2.conf i didn't make include of the freepbx/apache.conf but pasted the content into /etc/apache2/apache2.conf
```


<VirtualHost 127.0.0.1>

    DocumentRoot /var/www/
    ServerName 127.0.0.1
    ScriptAlias /cgi-bin/ /var/www/cgi-bin/
    <Directory *>
    Options +ExecCGI
    AddHandler cgi-script .cgi .pl
    </Directory>

</VirtualHost>


<VirtualHost *:80>
ServerName pabx.local
ServerAlias pabx.local
ServerAdmin admin@pabx.local
ErrorLog /var/log/freepbx/error.log
CustomLog /var/log/freepbx/access.log combined
DocumentRoot /var/www/pabx.domain/public
<Directory /var/www/pabx.domain/public>
Options Indexes FollowSymLinks MultiViews
Order allow,deny
AllowOverride All
Allow from all
</Directory>
</VirtualHost> 

```


/etc/amportal.conf
```

#;--------------------------------------------------------------------------------
#; Do NOT edit this file as it is auto-generated by FreePBX. All modifications to
#; this file must be done via the Web GUI. There are alternative files to make
#; custom modifications, details at: http://freepbx.org/configuration_files
#;--------------------------------------------------------------------------------


#;--------------------------------------------------------------------------------
#; All settings can be set from the Advanced Settings page accessible in FreePBX
#;--------------------------------------------------------------------------------



#
# --- CATEGORY: Advanced Settings Details ---
#

# Display Friendly Name
# Default Value: TRUE
AS_DISPLAY_FRIENDLY_NAME=TRUE

# Display Hidden Settings
# Default Value: FALSE
AS_DISPLAY_HIDDEN_SETTINGS=TRUE

# Display Readonly Settings
# Default Value: FALSE
AS_DISPLAY_READONLY_SETTINGS=TRUE

# Override Readonly Settings
# Default Value: FALSE
AS_OVERRIDE_READONLY=TRUE

#
# --- CATEGORY: Asterisk Manager ---
#

# Asterisk Manager Host
# Default Value: localhost
ASTMANAGERHOST=localhost

# Asterisk Manager Password
# Default Value: amp111
AMPMGRPASS=amp111

# Asterisk Manager Port
# Default Value: 5038
ASTMANAGERPORT=5038

# Asterisk Manager Proxy Port
# Default Value: 
ASTMANAGERPROXYPORT=

# Asterisk Manager User
# Default Value: admin
AMPMGRUSER=admin

#
# --- CATEGORY: Developer and Customization ---
#

# Always Download Web Assets
# Default Value: FALSE
FORCE_JS_CSS_IMG_DOWNLOAD=FALSE

# AMPLOCALBIN Dir for retrieve_conf
# Default Value: 
AMPLOCALBIN=

# Debug File
# Default Value: /tmp/freepbx_debug.log
FPBXDBUGFILE=/tmp/freepbx_debug.log

# Developer Mode
# Default Value: FALSE
DEVEL=FALSE

# Disable FreePBX dbug Logging
# Default Value: TRUE
FPBXDBUGDISABLE=TRUE

# Disable Mainstyle CSS Compression
# Default Value: FALSE
DISABLE_CSS_AUTOGEN=FALSE

# Disable Module Admin Caching
# Default Value: FALSE
MODULEADMIN_SKIP_CACHE=FALSE

# Leave Reload Bar Up
# Default Value: FALSE
DEVELRELOAD=FALSE

# POST_RELOAD Debug Mode
# Default Value: FALSE
POST_RELOAD_DEBUG=FALSE

# POST_RELOAD Script
# Default Value: 
POST_RELOAD=

# PRE_RELOAD Script
# Default Value: 
PRE_RELOAD=

# Provide Verbose Tracebacks
# Default Value: FALSE
DIE_FREEPBX_VERBOSE=FALSE

# Use Packaged Javascript Library 
# Default Value: TRUE
USE_PACKAGED_JS=TRUE

# Post Call Recording Script
# Default Value: 
MIXMON_POST=

#
# --- CATEGORY: Device Settings ---
#

# Show all Device Setting on Add
# Default Value: FALSE
ALWAYS_SHOW_DEVICE_DETAILS=FALSE

# Require Strong Secrets
# Default Value: TRUE
DEVICE_STRONG_SECRETS=TRUE

# SIP canrenivite (directmedia)
# Default Value: no
DEVICE_SIP_CANREINVITE=no

# SIP trustrpid
# Default Value: yes
DEVICE_SIP_TRUSTRPID=yes

# SIP sendrpid
# Default Value: no
DEVICE_SIP_SENDRPID=no

# SIP nat
# Default Value: no
DEVICE_SIP_NAT=no

# SIP encryption
# Default Value: no
DEVICE_SIP_ENCRYPTION=no

# SIP qualifyfreq
# Default Value: 60
DEVICE_SIP_QUALIFYFREQ=60

# SIP and IAX qualify
# Default Value: yes
DEVICE_QUALIFY=yes

# SIP and IAX allow
# Default Value: 
DEVICE_ALLOW=

# SIP and IAX disallow
# Default Value: 
DEVICE_DISALLOW=

# SIP and DAHDi callgroup
# Default Value: 
DEVICE_CALLGROUP=

# SIP and DAHDi pickupgroup
# Default Value: 
DEVICE_PICKUPGROUP=

#
# --- CATEGORY: Dialplan and Operational ---
#

# Block CNAM on External Trunks
# Default Value: FALSE
BLOCK_OUTBOUND_TRUNK_CNAM=FALSE

# Call Forward Ringtimer Default
# Default Value: 0
CFRINGTIMERDEFAULT=0

# Convert ZAP Settings to DAHDi
# Default Value: FALSE
ZAP2DAHDICOMPAT=FALSE

# CW Enabled by Default
# Default Value: TRUE
ENABLECW=TRUE

# Disable -custom Context Includes
# Default Value: FALSE
DISABLECUSTOMCONTEXTS=FALSE

# Ditech VQA Inbound Setting
# Default Value: 7
DITECH_VQA_INBOUND=7

# Ditech VQA Outbound Setting
# Default Value: 7
DITECH_VQA_OUTBOUND=7

# Dynamically Generate Hints
# Default Value: FALSE
DYNAMICHINTS=FALSE

# Enable Custom Device States
# Default Value: FALSE
USEDEVSTATE=FALSE

# Extension Concurrency Limit
# Default Value: 0
CONCURRENCYLIMITDEFAULT=0

# Feature Codes Beep Only
# Default Value: FALSE
FCBEEPONLY=FALSE

# Force All Internal Auto Answer
# Default Value: FALSE
FORCE_INTERNAL_AUTO_ANSWER_ALL=FALSE

# Generate Diversion Headers
# Default Value: FALSE
DIVERSIONHEADER=FALSE

# Internal Auto Answer Default
# Default Value: disabled
DEFAULT_INTERNAL_AUTO_ANSWER=disabled

# NoOp Traces in Dialplan
# Default Value: 0
NOOPTRACE=0

# Occupied Lines CW Busy
# Default Value: TRUE
CWINUSEBUSY=TRUE

# Only Use Last CID Prepend
# Default Value: TRUE
CID_PREPEND_REPLACE=TRUE

# Polling Interval for Stopping Asterisk
# Default Value: 2
ASTSTOPPOLLINT=2

# Use bad-number Context
# Default Value: TRUE
AMPBADNUMBER=TRUE

# Use Google DNS for Enum
# Default Value: FALSE
USEGOOGLEDNSFORENUM=FALSE

# Waiting Period to Stop Asterisk
# Default Value: 120
ASTSTOPTIMEOUT=120

# Use Automixmon for One-Touch Recording
# Default Value: FALSE
AUTOMIXMON=FALSE

#
# --- CATEGORY: Directory Layout ---
#

# Asterisk AGI Dir
# Default Value: /var/lib/asterisk/agi-bin
ASTAGIDIR=/usr/share/asterisk/agi-bin

# Asterisk bin Dir
# Default Value: /var/lib/asterisk
ASTVARLIBDIR=/var/lib/asterisk

# Asterisk etc Dir
# Default Value: /etc/asterisk
ASTETCDIR=/etc/asterisk

# Asterisk Log Dir
# Default Value: /var/log/asterisk
ASTLOGDIR=/var/log/asterisk

# Asterisk Modules Dir
# Default Value: /usr/lib/asterisk/modules
ASTMODDIR=/usr/lib/asterisk/modules

# Asterisk Run Dir
# Default Value: /var/run/asterisk
ASTRUNDIR=/var/run/asterisk

# Asterisk Spool Dir
# Default Value: /var/spool/asterisk
ASTSPOOLDIR=/var/spool/asterisk

# CGI Dir
# Default Value: /var/www/cgi-bin 
AMPCGIBIN=/var/www/cgi-bin 

# FreePBX bin Dir
# Default Value: /var/lib/asterisk/bin
AMPBIN=/var/lib/asterisk/bin

# FreePBX sbin Dir
# Default Value: /usr/sbin
AMPSBIN=/usr/local/sbin

# FreePBX Web Root Dir
# Default Value: /var/www/html
AMPWEBROOT=/var/www/pabx.domain/public

# MoH Subdirectory
# Default Value: moh
MOHDIR=mohmp3

# Override Call Recording Location
# Default Value: 
MIXMON_DIR=

#
# --- CATEGORY: Flash Operator Panel ---
#

# Disable FOP
# Default Value: FALSE
FOPDISABLE=FALSE

# FOP Password
# Default Value: passw0rd
FOPPASSWORD=password

# FOP Sort Mode
# Default Value: extension
FOPSORT=extension

# FOP Web Root Dir
# Default Value: /var/www/html/panel
FOPWEBROOT=/var/www/pabx.domain/public/panel

# Start FOP with amportal
# Default Value: TRUE
FOPRUN=TRUE

#
# --- CATEGORY: GUI Behavior ---
#

# Abort Config Gen on Bad Dest
# Default Value: FALSE
BADDESTABORT=FALSE

# Abort Config Gen on Exten Conflict
# Default Value: FALSE
XTNCONFLICTABORT=FALSE

# Check Server Referrer
# Default Value: TRUE
CHECKREFERER=TRUE

# Include Server Name in Browser
# Default Value: FALSE
SERVERINTITLE=FALSE

# Report Unknown Dest as Error
# Default Value: TRUE
CUSTOMASERROR=TRUE

# Require Confirm with Apply Changes
# Default Value: TRUE
RELOADCONFIRM=TRUE

# Show Categories in Nav Menu
# Default Value: TRUE
USECATEGORIES=TRUE

# Use wget For Module Admin
# Default Value: FALSE
MODULEADMINWGET=FALSE

# Dashboard Info Update Frequency
# Default Value: 30
DASHBOARD_INFO_UPDATE_TIME=30

# Dashboard Max Calls Initial Scale
# Default Value: 
MAXCALLS=

# Dashboard Stats Update Frequency
# Default Value: 6
DASHBOARD_STATS_UPDATE_TIME=6

#
# --- CATEGORY: Remote CDR Database ---
#

# Remote CDR DB Host
# Default Value: 
CDRDBHOST=

# Remote CDR DB Name
# Default Value: 
CDRDBNAME=

# Remote CDR DB Password
# Default Value: 
CDRDBPASS=

# Remote CDR DB Port
# Default Value: 
CDRDBPORT=

# Remote CDR DB Table
# Default Value: 
CDRDBTABLENAME=

# Remote CDR DB Type
# Default Value: 
CDRDBTYPE=

# Remote CDR DB User
# Default Value: 
CDRDBUSER=

#
# --- CATEGORY: Styling and Logos ---
#

# Legacy Right Logo
# Default Value: 
AMPADMINLOGO=

# Hide Nav Background
# Default Value: FALSE
BRAND_IMAGE_HIDE_NAV_BACKGROUND=FALSE

# Image: shadow-side-background.png
# Default Value: images/shadow-side-background.png
BRAND_IMAGE_SHADOW_SIDE_BACKGROUND=images/shadow-side-background.png

# Image: Right Upper
# Default Value: images/logo.png
BRAND_IMAGE_FREEPBX_RIGHT=images/logo.png

# Image: Left Upper
# Default Value: images/freepbx_large.png
BRAND_IMAGE_FREEPBX_LEFT=images/freepbx_large.png

# Image: Footer
# Default Value: images/freepbx_small.png
BRAND_IMAGE_FREEPBX_FOOT=images/freepbx_small.png

# Image: Reload Screen
# Default Value: images/loading.gif
BRAND_IMAGE_RELOAD_LOADING=images/loading.gif

# Alt for Left Logo
# Default Value: 
BRAND_FREEPBX_ALT_LEFT=

# Alt for Right Logo
# Default Value: 
BRAND_FREEPBX_ALT_RIGHT=

# Alt for Footer Logo
# Default Value: 
BRAND_FREEPBX_ALT_FOOT=

# Link for Left Logo
# Default Value: 
BRAND_IMAGE_FREEPBX_LINK_LEFT=

# Link for Right Logo
# Default Value: 
BRAND_IMAGE_FREEPBX_LINK_RIGHT=

# Link for Footer Logo
# Default Value: 
BRAND_IMAGE_FREEPBX_LINK_FOOT=

# Hide Right Logo
# Default Value: FALSE
BRAND_HIDE_LOGO_RIGHT=FALSE

# Hide Left FreePBX Version
# Default Value: FALSE
BRAND_HIDE_HEADER_VERSION=FALSE

# Hide Header Menus
# Default Value: FALSE
BRAND_HIDE_HEADER_MENUS=FALSE

# Primary CSS Stylesheet
# Default Value: 
BRAND_CSS_ALT_MAINSTYLE=

# Optional Additional CSS Stylesheet
# Default Value: 
BRAND_CSS_CUSTOM=

#
# --- CATEGORY: System Setup ---
#

# FreePBX Log Routing
# Default Value: FILE
AMPSYSLOGLEVEL=FILE

# Disable FreePBX Log
# Default Value: FALSE
AMPDISABLELOG=FALSE

# Log Verbose Messages
# Default Value: TRUE
LOG_OUT_MESSAGES=TRUE

# Send Dashboard Notifications to Log
# Default Value: TRUE
LOG_NOTIFICATIONS=TRUE

# FreePBX Log File
# Default Value: /var/log/asterisk/freepbx.log
FPBX_LOG_FILE=/var/log/asterisk/freepbx.log

# PHP Error Log Output
# Default Value: dbug
PHP_ERROR_HANDLER_OUTPUT=dbug

# User & Devices Mode
# Default Value: extensions
AMPEXTENSIONS=extensions

# Authorization Type
# Default Value: database
AUTHTYPE=database

# Allow Login With DB Credentials
# Default Value: FALSE
AMP_ACCESS_DB_CREDS=FALSE

# User Portal Admin Username
# Default Value: 
ARI_ADMIN_USERNAME=admin

# User Portal Admin Password
# Default Value: ari_password
ARI_ADMIN_PASSWORD=ari_password

# Asterisk VMU Mask
# Default Value: 007
AMPVMUMASK=007

# Force Asterisk Version
# Default Value: 
FORCED_ASTVERSION=

# FreePBX Web Address
# Default Value: 
AMPWEBADDRESS=127.0.0.1

# System Asterisk Group
# Default Value: asterisk
AMPASTERISKGROUP=asterisk

# System Asterisk User
# Default Value: asterisk
AMPASTERISKUSER=www-data

# System Device Group
# Default Value: asterisk
AMPDEVGROUP=asterisk

# System Device User
# Default Value: asterisk
AMPDEVUSER=asterisk

# System Web Group
# Default Value: asterisk
AMPASTERISKWEBGROUP=asterisk 

# System Web User
# Default Value: asterisk
AMPASTERISKWEBUSER=www-data

# Telephony Engine
# Default Value: asterisk
AMPENGINE=asterisk

# Convert Music Files to WAV
# Default Value: TRUE
AMPMPG123=TRUE

# Dashboard Non-Std SSH Port
# Default Value: 
SSHPORT=

# Recordings Crypt Key
# Default Value: 
AMPPLAYKEY=

#
# --- CATEGORY: VmX Locater ---
#

# VMX Default Context
# Default Value: from-internal
VMX_CONTEXT=from-internal

# VMX Default Loop Exceed Context
# Default Value: 
VMX_LOOPDEST_CONTEXT=

# VMX Default Loop Exceed Extension
# Default Value: dovm
VMX_LOOPDEST_EXT=dovm

# VMX Default Loop Exceed Priority
# Default Value: 1
VMX_LOOPDEST_PRI=1

# VMX Default Priority
# Default Value: 1
VMX_PRI=1

# VMX Default Timeout Context
# Default Value: 
VMX_TIMEDEST_CONTEXT=

# VMX Default Timeout Extension
# Default Value: dovm
VMX_TIMEDEST_EXT=dovm

# VMX Default Timeout Priority
# Default Value: 1
VMX_TIMEDEST_PRI=1

#
# --- CATEGORY: Voicemail Module ---
#

# Provide IMAP Voicemail Fields
# Default Value: FALSE
VM_SHOW_IMAP=FALSE

#
# --- CATEGORY: Bootstrapped or Legacy Settings ---
#

#
AMPDBUSER=dbuser

#
AMPDBPASS=dbpassword

#
AMPDBHOST=localhost

#
AMPDBNAME=asterisk

#
AMPDBENGINE=mysql

#
datasource=

#
AMPENABLEDEVELDEBUG=

#
TCINTERVAL=60

#
TCMAINT=1

#
DAYNIGHTTCHOOK=


```

thanks in advance

---

### Post by volkswagner on 2013-01-05
Are you trying to access [http://pabx.local](http://pabx.local) from a remote machine or from the pbx itself (gui installed on server)?  

This is a DNS issue.  Simple work around would be to add an entry to /etc/hosts on the machine you are trying _from_.

You'll need the ip of the pbx machine, and change the following to reflect such.

```
sudo nano /etc/hosts
```

add:

```
pabx.local     192.168.xxx.xxx
```

To reach machines by name you will need a local DNS server.  Some routers have DNSmasq which is great if you are using hostnames.

What is the hostname of your pbx?

```
hostname
```
```
hostname -f
```
```
cat /etc/hostname
```

---

### Post by pbxfan on 2013-01-07
Hi, thank you for you answer, i have added the pabx.local to my /etc/hosts but the problem is that 

to access amportal i use this link [http://pabx.local/pabx.domain/public/admin](http://pabx.local/pabx.domain/public/admin)
and not only [http://pabx.local/admin](http://pabx.local/admin)

this is the path of 127.0.0.1 ( /var/www/)

while amportal is here /var/www/pabx.domain/public/admin

thank you for your help

my hostname is "ubuntu"

and i'm trying to acess the portal from the same ip

---

### Post by volkswagner on 2013-01-07
I can't say for sure if your NameVirtualHost method will work or not.  My theory is you may not even have namevirtualhosts enabled.

[Here is the traditional way]("https://help.ubuntu.com/10.04/serverguide/httpd.html") to make vhost using separate host files. 

To prove my theory simply move your 127.0.0.1 virtual host below <VirtualHost *:80>

Apache may actually be reading from /etc/apache2/sites-enabled/000-default.

/etc/apache2/ports.conf should contain the following as a minimum:
```
NameVirtualHost *:80
Listen 80

```

---

